---
title: MSlogreader_agents (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSlogreader_agents_TSQL
- MSlogreader_agents
dev_langs:
- TSQL
helpviewer_keywords:
- MSlogreader_agents system table
ms.assetid: 8baa3c5a-cb40-42d0-b966-00e6d55368e8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 85afab7ff3183953da0a4655c98733dd66fb138a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827260"
---
# <a name="mslogreader_agents-transact-sql"></a>MSlogreader_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **MSlogreader_agents** содержит по одной строке для каждого агент чтения журнала, выполняемого на локальном распространителе. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор агента чтения журнала.|  
|**name**|**nvarchar (100)**|Имя агента чтения журнала.|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**публикации**|**sysname**|Имя публикации.|  
|**local_job**|**bit**|Показывает, есть ли задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на локальном распространителе.|  
|**job_id**|**двоичный (16)**|Идентификационный номер задания.|  
|**profile_id**|**int**|Идентификатор конфигурации из таблицы [MSagent_profiles](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) .|  
|**publisher_security_mode**|**smallint**|Режим безопасности, используемый агентом при подключении к издателю, может принимать одно из следующих значений:<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Проверка подлинности Windows.|  
|**publisher_login**|**sysname**|Имя входа, используемое для соединения с издателем.|  
|**publisher_password**|**nvarchar (524)**|Зашифрованное значение пароля, используемое для соединения с издателем.|  
|**job_step_uid**|**uniqueidentifier**|Уникальный идентификатор шага задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором запущен агент.|  
|**job_login**|**sysname**||  
|**job_password**|**nvarchar (524)**||  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
