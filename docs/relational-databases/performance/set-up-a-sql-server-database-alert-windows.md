---
title: Настройка предупреждения базы данных SQL Server (Windows) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
ms.assetid: 65d2c5c1-921f-4eff-9ef7-149170ab61e8
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: f76c6f4f4d65273c35dffb1cb17e664fceac0328
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68113337"
---
# <a name="set-up-a-sql-server-database-alert-windows"></a>Настройка предупреждения базы данных SQL Server (Windows)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Вы можете использовать системный монитор для создания предупреждения, которое будет выводиться, когда счетчик системного монитора достигает порогового значения. В ответ на оповещение системный монитор может запустить то или иное приложение — скажем, приложение, решающее связанную с оповещением проблему. Например, можно создать предупреждение, которое будет выводиться, когда число взаимоблокировок превысит заданное значение. 
  
 Оповещения можно также определять c помощью среды Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Оповещения](../../ssms/agent/alerts.md).  
  
## <a name="set-up-a-sql-server-database-alert"></a>Настройка оповещения базы данных SQL Server  
  
1. В дереве навигации окна **Производительность** разверните узел **Журналы и оповещения производительности**.  
  
2. Щелкните правой кнопкой мыши элемент **Оповещения** и выберите пункт **Новые параметры оповещений**.
  
3. В диалоговом окне **Новые параметры оповещений** введите имя нового оповещения и нажмите кнопку **ОК**.  
  
4. На вкладке **Общие** диалогового окна нового оповещения введите **Комментарий**. Нажмите кнопку **Добавить**, чтобы добавить к оповещению счетчик.  
  
     Каждое оповещение должно быть связано хотя бы с одним счетчиком.  
  
5. В диалоговом окне **Добавить счетчики** выберите объект SQL Server в списке **Объект производительности**. Выберите нужный счетчик в области **Выбрать счетчики из списка**.  
  
6. Чтобы связать счетчик с оповещением, нажмите кнопку **Добавить**. Далее можно продолжить добавление счетчиков или щелкнуть кнопку **Закрыть**, чтобы вернуться к диалоговому окну нового оповещения.  
  
7. В диалоговом окне нового предупреждения выберите в списке **Оповещать, когда значение** вариант **Больше** или **Меньше**. После этого введите пороговое значение в поле **Предел**.  
  
     Предупреждение будет выводиться, когда значение счетчика станет больше или меньше порогового значения (это зависит от того, что было выбрано: **Больше** или **Меньше**).  
  
8. В поле **Снимать показания каждые** укажите частоту считывания показаний счетчика.  
  
9. На вкладке **Действие** укажите действия, которые будут выполняться в ответ на оповещение.  
  
10. На вкладке **Расписание** укажите время начала и прекращения наблюдения за оповещениями.  
  
## <a name="see-also"></a>См. также раздел  
 [Создание предупреждения для базы данных SQL Server](../../relational-databases/performance-monitor/create-a-sql-server-database-alert.md)  
  
  
