---
title: sys. dm_exec_function_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/30/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_function_stats
- sys.dm_exec_function_stats_tsql
- dm_exec_function_stats
- dm_exec_function_stats_tsql
helpviewer_keywords:
- sys.dm_exec_function_stats dynamic management view
ms.assetid: 4c3d6a02-08e4-414b-90be-36b89a0e5a3a
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 02cff18af9c0824d7f28e5685f5fc63a0bf45128
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82821257"
---
# <a name="sysdm_exec_function_stats-transact-sql"></a>sys. dm_exec_function_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Возвращает статистическую статистику производительности для кэшированных функций. Представление возвращает одну строку для каждого кэшированного плана функции, а время существования строки — до тех пор, пока функция остается в кэше. При удалении функции из кэша соответствующая строка удаляется из этого представления. В этот момент возникает событие трассировки SQL статистики производительности аналогично **sys.dm_exec_query_stats**. Возвращает сведения о скалярных функциях, включая функции в памяти и скалярные функции CLR. Не возвращает сведения о функциях, возвращающих табличное значение.  
  
 Динамические административные представления в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] не могут предоставлять информацию, которая может повлиять на автономность базы данных, или информацию о других базах данных, к которым имеет доступ пользователь. Во избежание раскрытия этой информации все строки, содержащие данные, не принадлежащие подключенному клиенту, отфильтровываются.  
  
> [!NOTE]
> Результаты **sys. dm_exec_function_stats** могут различаться при каждом выполнении, так как данные отражают только завершенные запросы, а не по-прежнему в полете. 

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, в которой находится функция.|  
|**object_id**|**int**|Идентификационный номер объекта функции.|  
|**type**|**char (2)**|Тип объекта: FN = скалярные функции|  
|**type_desc**|**nvarchar(60)**|Описание типа объекта: SQL_SCALAR_FUNCTION|  
|**sql_handle**|**varbinary (64)**|Это можно использовать для сопоставления с запросами в **представлении sys. dm_exec_query_stats** , которые были выполнены в этой функции.|  
|**plan_handle**|**varbinary (64)**|Идентификатор плана в оперативной памяти. Этот идентификатор является временным и константным, только пока план сохраняется в кэше. Это значение можно использовать с динамическим административным представлением **sys. dm_exec_cached_plans** .<br /><br /> Всегда будет 0x000, когда скомпилированная в собственном режиме функция запрашивает оптимизированную для памяти таблицу.|  
|**cached_time**|**datetime**|Время добавления функции в кэш.|  
|**last_execution_time**|**datetime**|Время последнего выполнения функции.|  
|**execution_count**|**bigint**|Количество раз, когда функция была выполнена с момента последней компиляции.|  
|**total_worker_time**|**bigint**|Общее количество времени ЦП, затраченное на выполнение этой функции с момента компиляции, в микросекундах.<br /><br /> Для функций, скомпилированных в собственном режиме, **total_worker_time** может быть неточным, если количество выполнений меньше 1 миллисекунды.|  
|**last_worker_time**|**bigint**|Время ЦП, затраченное на время последнего выполнения функции, в микросекундах. <sup>1</sup>|  
|**min_worker_time**|**bigint**|Минимальное время ЦП в микросекундах, которое эта функция когда-либо использовала во время одного выполнения. <sup>1</sup>|  
|**max_worker_time**|**bigint**|Максимальное время ЦП (в микросекундах), которое эта функция когда-либо использовала во время одного выполнения. <sup>1</sup>|  
|**total_physical_reads**|**bigint**|Общее число операций физического считывания, выполненных с момента компиляции этой функции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**last_physical_reads**|**bigint**|Число операций физического считывания, выполненных при последнем выполнении функции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**min_physical_reads**|**bigint**|Минимальное число физических операций чтения, которые эта функция когда-либо выполняла во время одного выполнения.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**max_physical_reads**|**bigint**|Максимальное число физических операций чтения, которые эта функция когда-либо выполняла во время одного выполнения.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**total_logical_writes**|**bigint**|Общее число логических операций записи, выполненных выполнением этой функции с момента ее компиляции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**last_logical_writes**|**bigint**|Количество страниц в буферном пуле, загрязненных во время последнего выполнения плана. Если страница уже является «грязной» (т. е. измененной), операции записи не учитываются.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**min_logical_writes**|**bigint**|Минимальное число операций логической записи, которые эта функция когда-либо выполняла во время одного выполнения.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**max_logical_writes**|**bigint**|Максимальное число операций логической записи, которые эта функция когда-либо выполняла во время одного выполнения.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**total_logical_reads**|**bigint**|Общее число операций логического считывания, выполненных с момента компиляции этой функции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**last_logical_reads**|**bigint**|Число логических операций чтения, выполненных при последнем выполнении функции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**min_logical_reads**|**bigint**|Минимальное число операций логического считывания, которые эта функция когда-либо выполняла во время одного выполнения.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**max_logical_reads**|**bigint**|Максимальное число операций логического считывания, которые эта функция когда-либо выполняла во время одного выполнения.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**total_elapsed_time**|**bigint**|Общее затраченное время в микросекундах для выполнения этой функции.|  
|**last_elapsed_time**|**bigint**|Затраченное время в микросекундах для последнего выполненного выполнения этой функции.|  
|**min_elapsed_time**|**bigint**|Минимальное затраченное время в микросекундах для любого завершенного выполнения этой функции.|  
|**max_elapsed_time**|**bigint**|Максимальное затраченное время в микросекундах для любого завершенного выполнения этой функции.|  
|**total_page_server_reads**|**bigint**|Общее число операций чтения сервера страниц, выполненных с момента компиляции этой функции.<br /><br /> **Применимо к:** Масштабирование базы данных SQL Azure.|  
|**last_page_server_reads**|**bigint**|Число операций чтения сервера страниц, выполненных при последнем выполнении функции.<br /><br /> **Применимо к:** Масштабирование базы данных SQL Azure.|  
|**min_page_server_reads**|**bigint**|Минимальное количество операций чтения сервером страниц, которые эта функция когда-либо выполняла во время одного выполнения.<br /><br /> **Применимо к:** Масштабирование базы данных SQL Azure.|  
|**max_page_server_reads**|**bigint**|Максимальное количество операций чтения на сервере страниц, которые эта функция когда-либо выполняла во время одного выполнения.<br /><br /> **Применимо к:** Масштабирование базы данных SQL Azure.|
  
## <a name="permissions"></a>Разрешения  

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения о первых десяти функциях, идентифицируемых по среднему затраченному времени.  
  
```  
SELECT TOP 10 d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'function name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time,  
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],  
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_function_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys. dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_query_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 
 [sys. dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)   
 [sys. dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  
  
  
