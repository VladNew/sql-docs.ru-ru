---
title: sys. dm_hadr_cluster_networks (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_hadr_cluster_networks
- sys.dm_hadr_cluster_networks_TSQL
- sys.dm_hadr_cluster_networks
- dm_hadr_cluster_networks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_cluster_networks dynamic management view
ms.assetid: ece32b15-d63f-4f93-92b7-e2930333e97a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dd37e1f39291e12bd313b03b556506eb51eb131d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829387"
---
# <a name="sysdm_hadr_cluster_networks-transact-sql"></a>sys.dm_hadr_cluster_networks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает по строке для каждого из элементов кластера WSFC, участвующего в конфигурации подсети группы доступности. Это динамическое административное представление можно использовать для проверки виртуального сетевого IP-адреса, настроенного для каждой из реплик доступности.  
  
 Первичный ключ: **MEMBER_NAME**  +  **network_subnet_IP**  +  **network_subnet_prefix_length**  
  
 > [!TIP]
 > Начиная с версии [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] , это динамическое административное представление поддерживает Always on экземпляры отказоустойчивого кластера в дополнение к группам доступности Always on.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**member_name**|**nvarchar(128)**|Имя компьютера, принадлежащее узлу в кластере WSFC.|  
|**network_subnet_ip**|**nvarchar (48)**|IP-адрес подсети, к которой принадлежит компьютер. Это может быть адрес IPv4 или IPv6.|  
|**network_subnet_ipv4_mask**|**nvarchar (45)**|Маска подсети, задающая подсеть, к которой принадлежит IP-адрес. **network_subnet_ipv4_mask** , чтобы указать параметры dhcp-<network_subnet_option> в предложении WITH DHCP инструкции [CREATE Availability Group](../../t-sql/statements/create-availability-group-transact-sql.md) или [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] .<br /><br /> NULL = подсеть IPv6.|  
||||  
|**network_subnet_prefix_length**|**int**|Длина префикса сетевого IP-адреса, задающего подсеть, к которой принадлежит компьютер.|  
|**is_public**|**bit**|Является ли сеть в кластере WSFC общедоступной или закрытой, одно из следующих значений:<br /><br /> 0 = закрытая<br /><br /> 1 = общедоступная|  
|**is_ipv4**|**bit**|Тип подсети, одно из следующих значений:<br /><br /> 1 = IPv4<br /><br /> 0 = IPv6|  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Отказоустойчивая кластеризация и Always On группы доступности &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Мониторинг групп доступности &#40;&#41;Transact-SQL](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [sys. dm_os_cluster_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [Запросы к системному каталогу SQL Server вопросы и ответы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
