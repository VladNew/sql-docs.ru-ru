---
title: Класс событий Broker:Activation | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Activation event class
ms.assetid: 481d5b13-657e-4b51-8783-ccac3595bd45
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f95424242f62c946dc5d0787e54c8095e2f71a1f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250204"
---
# <a name="brokeractivation-event-class"></a>Broker:Activation, класс событий
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует событие **Broker:Activation** , если монитор очереди запускает хранимую процедуру активации, отправляет уведомление QUEUE_ACTIVATION или если существует хранимая процедура активации, запущенная монитором очереди.  
  
## <a name="brokeractivation-event-class-data-columns"></a>Столбцы данных класса событий Broker:Activation  
  
|Столбец данных|Тип|Описание|Номер столбца|Фильтруемый|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ClientProcessID**|`int`|Идентификатор, присвоенный компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|`int`|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database*не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**EventClass**|`int`|Тип захваченного класса событий. Всегда **163** для **Broker:Activation**.|27|Нет|  
|**EventSequence**|`int`|Порядковый номер этого события.|51|Нет|  
|**EventSubClass**|`nvarchar`|Конкретное действие, о котором сообщает это событие. Одно из следующих значений:<br /><br /> **Запуск**: <br />                [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запустил хранимую процедуру активации.<br /><br /> **завершено**: Активация хранимой процедуры, завершила работу нормально.<br /><br /> **прервано**: Активация хранимой процедуры, завершился с ошибкой.|21|Нет|  
|**HostName**|`nvarchar`|Имя компьютера, на котором выполняется клиентская программа. Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**IntegerData**|`int`|Число активных задач в этой очереди.|25|Нет|  
|**IsSystem**|`int`|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Нет|  
|**LoginSid**|`image`|Идентификатор безопасности вошедшего в систему пользователя. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|`nvarchar`|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|`nvarchar`|Имя пользователя, которому принадлежит соединение, создавшее это событие.|6|Да|  
|**ObjectID**|`int`|Очередь, связанная с этим событием.|22|Нет|  
|**ServerName**|`nvarchar`|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , подвергаемого трассировке.|26|Нет|  
|**SPID**|`int`|Идентификатор процесса сервера, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присвоил процессу, связанному с клиентом.|12|Да|  
|**StartTime**|`datetime`|Время начала события, если доступно.|14|Да|  
|**TransactionID**|`bigint`|Назначенный системой идентификатор транзакции.|4|Нет|  
  
  