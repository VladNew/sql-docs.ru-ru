---
title: sys. dm_cdc_errors (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_cdc_errors_TSQL
- dm_cdc_errors
- sys.dm_cdc_errors
- sys.dm_cdc_errors_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cdc_errors dynamic management view
- change data capture [SQL Server], error reporting
ms.assetid: 898f2d76-9e63-45ef-94da-8034e86004ab
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 81908d815818c0274615e9bd2bd3bf40037e2b99
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833850"
---
# <a name="change-data-capture---sysdm_cdc_errors"></a>Система отслеживания измененных данных — sys. dm_cdc_errors
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает одну строку для каждой ошибки, встреченной во время сеанса просмотра журнала системы отслеживания измененных данных.  
 
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Идентификатор сеанса.<br /><br /> 0 = ошибка не происходила в течение сеанса просмотра журнала.|  
|**phase_number**|**int**|Номер, указывающий этап, в котором находился сеанс во время возникновения ошибки. Описание каждого этапа см. в разделе [sys. dm_cdc_log_scan_sessions &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md).|  
|**entry_time**|**datetime**|Дата и время регистрации ошибки. Это значение соответствует отметке времени в журнале ошибок SQL.|  
|**error_number**|**int**|Идентификатор сообщения об ошибке.|  
|**error_severity**|**int**|Степень серьезности сообщения, от 1 до 25.|  
|**error_state**|**int**|Номер состояния ошибки.|  
|**error_message**|**nvarchar(1024)**|Текст сообщения ошибки.|  
|**start_lsn**|**nvarchar (23)**|Начальное значение номера LSN для строк, которые обрабатывались во время возникновения ошибки.<br /><br /> 0 = ошибка не происходила в течение сеанса просмотра журнала.|  
|**begin_lsn**|**nvarchar (23)**|Начальное значение номера LSN для транзакции, которая обрабатывалась во время возникновения ошибки.<br /><br /> 0 = ошибка не происходила в течение сеанса просмотра журнала.|  
|**sequence_value**|**nvarchar (23)**|Номер LSN для строк, которые обрабатывались во время возникновения ошибки.<br /><br /> 0 = ошибка не происходила в течение сеанса просмотра журнала.|  
  
## <a name="remarks"></a>Remarks  
 **sys. dm_cdc_errors** содержит сведения об ошибке для предыдущих 32 сеансов.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение VIEW DATABASE STATE для запроса динамического административного представления **sys. dm_cdc_errors** . Дополнительные сведения о разрешениях для динамических административных представлений см. в разделе [динамические административные представления и функции &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="see-also"></a>См. также  
 [sys. dm_cdc_log_scan_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md)   
 [sys. dm_repl_traninfo &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-repl-traninfo-transact-sql.md)  
  
  

