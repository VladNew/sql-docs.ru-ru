---
title: sysreplicationalerts (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysreplicationalerts_TSQL
- sysreplicationalerts
dev_langs:
- TSQL
helpviewer_keywords:
- sysreplicationalerts system table
ms.assetid: 6ed15828-8cca-4cf0-b2ff-1ecd0d8db11a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 163b5aba5f676f14afd26b962c856b325ccc4dc4
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82819994"
---
# <a name="sysreplicationalerts-transact-sql"></a>sysreplicationalerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения об условиях срабатывания оповещения о репликации. Эта таблица хранится в базе данных **msdb** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|Идентификатор предупреждения.|  
|**status**|**int**|Определяемое пользователем значение:<br /><br /> **0** = не обслуживается.<br /><br /> **1** = обслуживается.|  
|**agent_type**|**int**|Тип агента:<br /><br /> **1** = агент моментальных снимков.<br /><br /> **2** = агент чтения журнала.<br /><br /> **3** = агент распространения.<br /><br /> **4** = агент слияния.|  
|**agent_id**|**int**|Идентификатор агента из таблиц **MSsnapshot_agents**, **MSlogreader_agents**, **MSdistribution_agents**или **MSmerge_agents**.|  
|**error_id**|**int**|Идентификатор ошибки, хранящейся в **MSrepl_errors**.|  
|**alert_error_code**|**int**|Идентификатор предупреждения, сработавшего при регистрации данной записи.|  
|**time**|**datetime**|Время добавления записи.|  
|**publisher**|**sysname**|Имя издателя, связанного с запустившим данное предупреждение агентом.|  
|**publisher_db**|**sysname**|Имя базы данных издателя, связанной с запустившим данное предупреждение агентом.|  
|**публикации**|**sysname**|Имя публикации, связанной с запустившим данное предупреждение агентом.|  
|**publication_type**|**int**|Тип публикации:<br /><br /> **0** = моментальный снимок.<br /><br /> **1** = транзакционная.<br /><br /> **2** = слияние.|  
|**абонент**|**sysname**|Имя подписчика, связанного с запустившим данное предупреждение агентом.|  
|**subscriber_db**|**sysname**|Имя базы данных подписчика, связанного с запустившим данное предупреждение агентом.|  
|**статья**|**sysname**|Имя статьи, связанной с агентом, запустившим данное предупреждение.|  
|**destination_object**|**sysname**|Имя таблицы подписки, связанной с предупреждением.|  
|**source_object**|**sysname**|Имя опубликованной таблицы, связанной с предупреждением.|  
|**alert_error_text**|**ntext**|Текст предупреждения.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
