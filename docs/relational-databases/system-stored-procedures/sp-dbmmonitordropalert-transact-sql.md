---
title: sp_dbmmonitordropalert (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitordropalert_TSQL
- sp_dbmmonitordropalert
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], monitoring
- sp_dbmmonitordropalert
ms.assetid: fe4a134b-25bf-464e-a5c4-358de215b65a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 37877860454612e6ebc9b623b47a42606abe4646
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828405"
---
# <a name="sp_dbmmonitordropalert-transact-sql"></a>sp_dbmmonitordropalert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет предупреждения для указанной метрики производительности с помощью установки порогового значения NULL.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dbmmonitordropalert database_name   
    [ , alert_id ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Указывает базу данных, для которой исключаются указанные пороговые значения предупреждений.  
  
 *alert_id*  
 Целочисленное значение, которое определяет исключаемое предупреждение. Если этот аргумент не указан, исключаются все предупреждения в базе данных. Чтобы исключить предупреждение для указанной метрики производительности, укажите одно из следующих значений.  
  
|Значение|Метрика производительности|Пороговое значение предупреждения|  
|-----------|------------------------|-----------------------|  
|1|Самая старая неотправленная транзакция|Указывает количество транзакций за минуту, которые могут накопиться в очереди передачи перед тем, как будет сформировано предупреждение в экземпляре основного сервера. Это предупреждение помогает измерять возможную потерю данных за период времени. Это особенно уместно в режиме высокой производительности. Однако это предупреждение также уместно в режиме высокой безопасности, когда зеркальное отображение приостановлено или прекращено, потому что участники были разъединены.|  
|2|Неотправленный журнал|Указывает, какое количество килобайтов (КБ) неотправленного журнала формирует предупреждение в экземпляре основного сервера. Это предупреждение помогает измерять возможную потерю данных в КБ. Это особенно уместно в режиме высокой производительности. Однако это предупреждение также уместно в режиме высокой безопасности, когда зеркальное отображение приостановлено или прекращено, потому что участники были разъединены.|  
|3|Невосстановленный журнал|Указывает, какое количество килобайтов (КБ) невосстановленного журнала формирует предупреждение в экземпляре зеркального сервера. Это предупреждение помогает вычислить время отработки отказа. *Время отработки отказа* в основном состоит из времени, необходимого бывшему зеркальному серверу для наката всех журналов, оставшихся в его очереди повторов, и небольшого дополнительного времени.|  
|4|Затраты на фиксирование изменений на зеркальном сервере|Указывает количество миллисекунд средней задержки транзакции, которая допустима перед формированием предупреждения на основном сервере. Задержка — это объем дополнительной нагрузки во время ожидания экземпляром основного сервера экземпляра зеркального сервера для добавления записи журнала транзакции в очередь повтора. Это значение уместно только в режиме высокой безопасности.|  
|5|Срок хранения|Метаданные, управляющие длительностью хранения строк в таблице состояния зеркального отображения базы данных.|  
  
> [!NOTE]  
>  Эта процедура удаляет пороговые значения предупреждений независимо от того, были ли они указаны с помощью **sp_dbmmonitorchangealert** или монитора зеркального отображения баз данных.  
  
 Сведения о кодах событий, соответствующих предупреждениям, см. [в разделе Использование пороговых значений предупреждений и предупреждений в метриках производительности зеркального отображения &#40;SQL Server&#41;](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется настройка срока хранения базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_dbmmonitordropalert AdventureWorks2012, 5;  
```  
  
 В следующем примере удаляются все пороговые значения предупреждений и срок хранения базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_dbmmonitordropalert AdventureWorks2012 ;  
```  
  
## <a name="see-also"></a>См. также  
 [Мониторинг &#40;SQL Server зеркального отображения базы данных&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangealert (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql.md)  
  
  
