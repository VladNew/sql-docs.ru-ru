---
title: sys. dm_pdw_wait_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cfb8d905-c34f-44de-9574-dde81e170916
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 2d5815783528b89716cc8bfb426ea7c1b274802e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68088723"
---
# <a name="sysdm_pdw_wait_stats-transact-sql"></a>sys. dm_pdw_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит информацию, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] относящуюся к состоянию ОС, связанному с экземплярами, работающими на разных узлах. Список типов ожидания и их описание см. в разделе [sys. dm_os_wait_stats](https://msdn.microsoft.com/library/ms179984\(v=sql.120\).aspx).  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|**pdw_node_id**|**int**|Идентификатор узла, на который ссылается эта запись.||  
|**wait_name**|**nvarchar(255)**|Имя типа ожидания.||  
|**max_wait_time**|**bigint**|Максимальное время ожидания этого типа ожидания.||  
|**request_count**|**bigint**|Число ожиданий данного ожидающего типа ожидания.||  
|**signal_time**|**bigint**|Разница между временем сигнализации ожидающего потока и временем начала его выполнения.||  
|**completed_count**|**bigint**|Общее число ожиданий этого типа, выполненных с момента последнего перезапуска сервера.||  
|**wait_time**|**bigint**|Общее время ожидания для этого типа ожидания в миллисеконс. Включительно signal_time.||  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys. dm_pdw_waits &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
  
