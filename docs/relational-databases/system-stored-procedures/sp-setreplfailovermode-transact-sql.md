---
title: sp_setreplfailovermode (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setreplfailovermode
- sp_setreplfailovermode_TSQL
helpviewer_keywords:
- sp_setreplfailovermode
ms.assetid: ca98a4c3-bea4-4130-88d7-79e0fd1e85f6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9baab3745fde8249e5143b025dd4094c6f4a9133
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824317"
---
# <a name="sp_setreplfailovermode-transact-sql"></a>Хранимая процедура sp_setreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Позволяет установить режим отработки отказа для подписок, включенных для немедленного обновления с отработкой отказа с обновлением посредством очередей. Эта хранимая процедура выполняется на подписчике в базе данных подписки. Дополнительные сведения о режимах отработки отказа см. в разделе [обновляемые подписки для репликации транзакций](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_setreplfailovermode [ @publisher= ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication= ] 'publication' ]  
    [ , [ @failover_mode= ] 'failover_mode' ]  
    [ , [ @override = ] override ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию. Публикация уже должна существовать.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных публикации. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @failover_mode = ] 'failover_mode'`Режим отработки отказа для подписки. *FAILOVER_MODE* имеет тип **nvarchar (10)** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Интерпретация** или **Синхронизация**|Изменения данных на подписчике массово копируются на издатель по мере их возникновения.|  
|**в очереди**|Изменения данных хранятся в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] очереди.|  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)]Очередь сообщений устарела и больше не поддерживается.  
  
`[ @override = ] override`Только для внутреннего использования.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_setreplfailovermode** используется в репликации моментальных снимков или репликации транзакций, для которой включены подписки, либо для обновления посредством очередей с отработкой отказа, либо для немедленного обновления с отработкой отказа на обновление посредством очередей.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_setreplfailovermode**.  
  
## <a name="see-also"></a>См. также  
 [Переключение между режимами обновления для обновляемой подписки на публикацию транзакций](../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
