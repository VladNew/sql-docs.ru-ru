---
title: Хранимые процедуры управления на основе политик (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Policy-Based Management, stored procedures
- stored procedures [Policy-Based Management]
ms.assetid: df64ab19-4e66-4702-96bd-32ad587d00f0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 623fee7a29b56e54a4621a11fcebad7bd4ff00fc
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827868"
---
# <a name="policy-based-management-stored-procedures-transact-sql"></a>Хранимые процедуры управления на основе политик (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]поддерживает следующие системные хранимые процедуры, используемые для управления на основе политик.  
  
> [!IMPORTANT]  
>  Поддерживаются только хранимые процедуры управления на основе политик, описанные в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Недокументированные хранимые процедуры используются внутренними компонентами управления на основе политик и не должны использоваться для администрирования на основе политик.  
  
|||  
|-|-|  
|[sp_syspolicy_add_policy_category](../../relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-transact-sql.md)|[sp_syspolicy_rename_policy_category](../../relational-databases/system-stored-procedures/sp-syspolicy-rename-policy-category-transact-sql.md)|  
|[sp_syspolicy_add_policy_category_subscription](../../relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql.md)|[sp_syspolicy_repair_policy_automation](../../relational-databases/system-stored-procedures/sp-syspolicy-repair-policy-automation-transact-sql.md)|  
|[sp_syspolicy_configure](../../relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql.md)|[sp_syspolicy_set_config_enabled](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-enabled-transact-sql.md)|  
|[sp_syspolicy_delete_policy_category](../../relational-databases/system-stored-procedures/sp-syspolicy-delete-policy-category-transact-sql.md)|[sp_syspolicy_set_config_history_retention](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)|  
|[sp_syspolicy_delete_policy_category_subscription](../../relational-databases/system-stored-procedures/sp-syspolicy-delete-policy-category-subscription-transact-sql.md)|[sp_syspolicy_set_log_on_success](../../relational-databases/system-stored-procedures/sp-syspolicy-set-log-on-success-transact-sql.md)|  
|[sp_syspolicy_delete_policy_execution_history](../../relational-databases/system-stored-procedures/sp-syspolicy-delete-policy-execution-history-transact-sql.md)|[sp_syspolicy_subscribe_to_policy_category](../../relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql.md)|  
|[sp_syspolicy_purge_health_state](../../relational-databases/system-stored-procedures/sp-syspolicy-purge-health-state-transact-sql.md)|[sp_syspolicy_unsubscribe_from_policy_category](../../relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql.md)|  
|[sp_syspolicy_purge_history](../../relational-databases/system-stored-procedures/sp-syspolicy-purge-history-transact-sql.md)|[sp_syspolicy_update_policy_category](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-transact-sql.md)|  
|[sp_syspolicy_rename_condition](../../relational-databases/system-stored-procedures/sp-syspolicy-rename-condition-transact-sql.md)|[sp_syspolicy_update_policy_category_subscription](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql.md)|  
|[sp_syspolicy_rename_policy](../../relational-databases/system-stored-procedures/sp-syspolicy-rename-policy-transact-sql.md)||  
  
## <a name="see-also"></a>См. также  
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
