---
title: Использование динамических административных представлений для определения статистики использования и производительности представлений
description: Использование динамических административных представлений для определения статистики использования и производительности представлений
manager: craigg
author: MashaMSFT
ms.author: mathoma
ms.date: 09/27/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.openlocfilehash: 1ac9c72ecee9beee66ea190b3acf233a0e4bc753
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47618412"
---
# <a name="use-dmvs-to-determine-usage-statistics-and-performance-of-views"></a>Использование динамических административных представлений для определения статистики использования и производительности представлений

В этой статье рассматриваются методы и скрипты, используемые для получения информации о **производительности запросов, которые используют представления** в объекте базы данных. Цель этих скриптов — предоставить показатели использования и производительности различных представлений, найденных в базе данных. 

## <a name="sysdmexecqueryoptimizerinfo"></a>Sys.dm_exec_query_optimizer_info

Динамическое административное представление [sys.dm_exec_query_optimizer_info](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-optimizer-info-transact-sql) предоставляет статистику об оптимизации, выполняемой оптимизатором запросов SQL Server. Эти значения являются накопительными. Их запись начинается при запуске SQL Server.  

Приведенное ниже обобщенное табличное выражение (CTE) common_table_expression использует это динамическое административное представление, чтобы предоставить сведения о рабочей нагрузке, например, процент запросов, которые ссылаются на представление. Результаты, возвращенные этим запросом, сами по себе не указывают на проблему производительности, но помогают выявлять исходные проблемы в сочетании с жалобами пользователей на запросы с низкой производительностью. 


```SQL
WITH CTE_QO AS
(
  SELECT
    occurrence
  FROM
    sys.dm_exec_query_optimizer_info
  WHERE
    ([counter] = 'optimizations')
),
QOInfo AS
(
  SELECT
    [counter]
    ,[%] = CAST((occurrence * 100.00)/(SELECT occurrence FROM CTE_QO) AS DECIMAL(5, 2))
  FROM
    sys.dm_exec_query_optimizer_info
  WHERE
    [counter] IN ('optimizations'
                  ,'trivial plan'
                  ,'no plan'
                  ,'search 0'
                  ,'search 1'
                  ,'search 2'
                  ,'timeout'
                  ,'memory limit exceeded'
                  ,'insert stmt'
                  ,'delete stmt'
                  ,'update stmt'
                  ,'merge stmt'
                  ,'contains subquery'
                  ,'view reference'
                  ,'remote query'
                  ,'dynamic cursor request'
                  ,'fast forward cursor request'
             )
)
SELECT
  [optimizations] AS [optimizations %]
  ,[trivial plan] AS [trivial plan %]
  ,[no plan] AS [no plan %]
  ,[search 0] AS [search 0 %]
  ,[search 1] AS [search 1 %]
  ,[search 2] AS [search 2 %]
  ,[timeout] AS [timeout %]
  ,[memory limit exceeded] AS [memory limit exceeded %]
  ,[insert stmt] AS [insert stmt %]
  ,[delete stmt] AS [delete stmt]
  ,[update stmt] AS [update stmt]
  ,[merge stmt] AS [merge stmt]
  ,[contains subquery] AS [contains subquery %]
  ,[view reference] AS [view reference %]
  ,[remote query] AS [remote query %]
  ,[dynamic cursor request] AS [dynamic cursor request %]
  ,[fast forward cursor request] AS [fast forward cursor request %]
FROM
  QOInfo
PIVOT (MAX([%]) FOR [counter] 
  IN ([optimizations]
      ,[trivial plan]
      ,[no plan]
      ,[search 0]
      ,[search 1]
      ,[search 2]
      ,[timeout]
      ,[memory limit exceeded]
      ,[insert stmt]
      ,[delete stmt]
      ,[update stmt]
      ,[merge stmt]
      ,[contains subquery]
      ,[view reference]
      ,[remote query]
      ,[dynamic cursor request]
      ,[fast forward cursor request])) AS p;
GO
```
Объедините результаты этого запроса с результатами системного представления [sys.views](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-views-transact-sql), чтобы определить статистику запросов, текст запроса и кэшированный план выполнения. 

## <a name="sysviews"></a>Sys.views

В приведенном ниже обобщенном табличном выражении предоставляются сведения о количестве выполнений, общем времени работы и количестве прочитанных страниц из памяти. На основе результатов можно определить запросы, требующие оптимизации. 
  
  >[!NOTE]
  > Результаты этого запроса могут различаться в зависимости от используемой версии SQL Server.  


```SQL
WITH CTE_VW_STATS AS
(
  SELECT
    SCHEMA_NAME(vw.schema_id) AS schemaname
    ,vw.name AS viewname
    ,vw.object_id AS viewid
  FROM
    sys.views AS vw
  WHERE
    (vw.is_ms_shipped = 0)
  INTERSECT
  SELECT
    SCHEMA_NAME(o.schema_id) AS schemaname
    ,o.Name AS name
    ,st.objectid AS viewid
  FROM
    sys.dm_exec_cached_plans cp
  CROSS APPLY
    sys.dm_exec_sql_text(cp.plan_handle) st
  INNER JOIN
    sys.objects o ON st.[objectid] = o.[object_id]
  WHERE
    st.dbid = DB_ID()
)
SELECT
  vw.schemaname
  ,vw.viewname
  ,vw.viewid
  ,DB_NAME(t.databaseid) AS databasename
  ,t.databaseid
  ,t.*
FROM
  CTE_VW_STATS AS vw
CROSS APPLY
  (
    SELECT
      st.dbid AS databaseid
      ,st.text
      ,qp.query_plan
      ,qs.*
    FROM
      sys.dm_exec_query_stats AS qs
    CROSS APPLY
      sys.dm_exec_sql_text(qs.plan_handle) AS st
    CROSS APPLY
      sys.dm_exec_query_plan(qs.plan_handle) AS qp
    WHERE
      (CHARINDEX(vw.schemaname, st.text, 1) > 0)
      AND (st.dbid = DB_ID())
  ) AS t;
GO
```

## <a name="sysdmvexeccachedplans"></a>Sys.dmv_exec_cached_plans

Окончательный запрос предоставляет сведения о неиспользуемых представлениях при помощи динамического административного представления [sys.dmv_exec_cached_plans](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql). Однако кэшированный план выполнения динамический и результаты могут различаться. Таким образом, необходимо использовать этот запрос через какое-то время, чтобы определить, используется ли представление. 


```SQL
SELECT
  SCHEMA_NAME(vw.schema_id) AS schemaname
  ,vw.name AS name
  ,vw.object_id AS viewid
FROM
  sys.views AS vw
WHERE
  (vw.is_ms_shipped = 0)
EXCEPT
SELECT
  SCHEMA_NAME(o.schema_id) AS schemaname
  ,o.name AS name
  ,st.objectid AS viewid
FROM
  sys.dm_exec_cached_plans cp
CROSS APPLY
  sys.dm_exec_sql_text(cp.plan_handle) st
INNER JOIN
  sys.objects o ON st.[objectid] = o.[object_id]
WHERE
  st.dbid = DB_ID();
GO
```

## <a name="related-external-resources"></a>Связанные внешние ресурсы

- [Динамические административные представления для настройки производительности (видео — SQL Saturday Pordenone)](https://www.youtube.com/watch?v=9FQaFwpt3-k)
- [Динамические административные представления для настройки производительности (слайды и демоверсия — SQL Saturday Pordenone)](http://www.sqlsaturday.com/589/Sessions/Details.aspx?sid=57409)
- [Видео о настройке SQL Server в форме капсулы (SQL Saturday Parma)](https://vimeo.com/200980883)
- [Настройка SQL Server в двух словах (слайды и демоверсия — SQL Saturday Parma)](http://www.sqlsaturday.com/566/Sessions/Details.aspx?sid=53988)
- [Книга о настройке производительности с помощью динамических административных представлений SQL Server](https://www.red-gate.com/library/performance-tuning-with-sql-server-dynamic-management-views)
- [Видео о важнейших типах ожидания в SQL Server 2016](https://channel9.msdn.com/Blogs/MVP-Data-Platform/The-Most-Prominent-Wait-Types-of-your-SQL-Server-2016)