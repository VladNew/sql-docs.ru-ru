---
title: Мссубскриптионс (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscriptions_TSQL
- MSsubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriptions system table
ms.assetid: b7e8301d-d115-41f6-8d4f-e0d25f453b25
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b4ed943e0768e031c07fa1748961e311373af8ad
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82812264"
---
# <a name="mssubscriptions-transact-sql"></a>MSsubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **мссубскриптионс** содержит по одной строке для каждой опубликованной статьи в подписке, обслуживаемой локальным распространителем. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|Идентификатор базы данных издателя.|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**publication_id**|**int**|Идентификатор публикации.|  
|**article_id**|**int**|Идентификатор статьи.|  
|**subscriber_id**|**smallint**|Идентификатор подписчика.|  
|**subscriber_db**|**sysname**|Имя базы данных подписки.|  
|**subscription_type**|**int**|Тип подписки.<br /><br /> **0** = принудительная отправка.<br /><br /> **1** = по запросу.<br /><br /> **2** = анонимный.|  
|**sync_type**|**tinyint**|Тип синхронизации:<br /><br /> **1** = автоматический.<br /><br /> **2** = нет синхронизации.|  
|**status**|**tinyint**|Состояние подписки.<br /><br /> **0** = неактивно.<br /><br /> **1** = подписка выполнена.<br /><br /> **2** = активно.|  
|**subscription_seqno**|**varbinary (16)**|Порядковый номер транзакции моментального снимка памяти.|  
|**snapshot_seqno_flag**|**bit**|Указывает источник порядкового номера транзакции моментального снимка, где значение **1** означает, что **subscription_seqno** является порядковым номером моментального снимка.|  
|**independent_agent**|**bit**|Указывает, имеется ли для данной публикации изолированный агент распространителя.|  
|**subscription_time**|**datetime**|Только для внутреннего использования.|  
|**loopback_detection**|**bit**|Применяется к подпискам, которые являются частью двунаправленной топологии репликации транзакций. Механизм распознавания обратной связи определяет, отправляет ли агент распространителя транзакции, созданные в подписчике, обратно подписчику:<br /><br /> **1** = не отправляет обратно.<br /><br /> **0** = отправляет обратно.<br /><br />|  
|**agent_id**|**int**|Идентификатор агента.|  
|**update_mode**|**tinyint**|Тип обновления.|  
|**publisher_seqno**|**varbinary (16)**|Последовательный номер транзакции на издателе для этой подписки.|  
|**ss_cplt_seqno**|**varbinary (16)**|Последовательный номер, используемый для обозначения завершения одновременной обработки моментальных снимков.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
