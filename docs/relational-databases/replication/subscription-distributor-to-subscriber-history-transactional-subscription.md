---
title: Журнал операций от распространителя к подписчику
description: Здесь описываются параметры на вкладке "Журнал операций от распространителя к подписчику" в SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.subscription.disttosub.f1
ms.assetid: 1aad5b82-592e-4907-92f7-b90794175be5
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 420e659988abb4292a1653261034361f9d5f6055
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "76287107"
---
# <a name="subscription-distributor-to-subscriber-history-transactional-subscription"></a>Подписка, журнал от распространителя к подписчику (подписка на публикацию транзакций)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Вкладка **Журнал операций от распространителя к подписчику** отображает подробные сведения об агенте распространителя, включая состояние, журнал, информационные сообщения и любые сообщения об ошибках.  
  
## <a name="options"></a>Параметры  
 В меню **Вид** выберите сеансы, какого агента распространителя необходимо просмотреть, а затем в сетке **Сеансы агента распространителя**выберите определенный сеанс. Подробные сведения об этом сеансе отображаются в сетке, помеченной как **Действия в выбранном сеансе**. Если выбранный сеанс закончен с ошибкой, также выводится на экран текстовое поле, помеченное как **Описание ошибки или сообщение выбранного сеанса** .  
  
 **View** (Вид)  
 Выберите агента распространителя, сеансы которого необходимо просмотреть. Как правило, агент распространителя работает постоянно, поэтому просмотреть можно только один сеанс.  
  
 **Состояние**  
 Состояние агента распространителя. Возможные значения состояния показаны в следующем списке:  
  
-   Ошибка  
  
-   Завершено  
  
-   Повтор  
  
-   Запущен  
  
 **Start Time**  
 Время начала сеанса.  
  
 **Время окончания**  
 Время окончания сеанса. Если агент не остановлен, это поле остается пустым.  
  
 **Длительность**  
 Длительность работы агента распространителя в этом сеансе. Если в данный момент агент работает, отображается время его работы, после завершения сеанса агента отображается общая длительность сеанса.  
  
 **Сообщение об ошибке**  
 Если сеанс завершился ошибкой, в данном поле отображается последнее сообщение об ошибке, зарегистрированное агентом распространителя. Если сеанс завершился без ошибки, это поле остается пустым.  
  
 **Сообщение действия**  
 Все информационные сообщения и сообщения об ошибках, зарегистрированные агентом распространителя в течение выбранного сеанса.  
  
 **Время действия**  
 Время, когда было выполнено действие, описанное в столбце **Сообщение действия** .  
  
 **Описание ошибки или сообщение выбранного сеанса**  
 Выводится, только если выбранный сеанс отображает значение **Ошибка** в столбце **Состояние** . Это текстовое поле отображает подробные данные об ошибке и о выполняемой во время возникновения ошибки команде. Также содержит ссылки на дополнительные данные, имеющие отношение к ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Запуск монитора репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Просмотр сведений и выполнение задач с помощью монитора репликации](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Наблюдение за репликацией](../../relational-databases/replication/monitor/monitoring-replication.md)   
 [Replication Agents Overview](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
