---
title: Реализация заданий
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 9770382558af7e77090235775c133dbeaeabff51
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75242348"
---
# <a name="implement-jobs"></a>Реализация заданий
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяют автоматизировать задачи администрирования и сделать их выполнение более эффективным.  
  
Задание — это определенная цепочка действий, последовательно выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Задание может выполнять различные действия, включая запуск скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] , приложений командной строки, скриптов Microsoft ActiveX, пакетов служб Integration Services, запросов и команд служб Analysis Services или задач репликации. Задание может выполнять повторяющиеся задачи или задачи, запуск которых определяется расписанием; кроме того, оно может автоматически уведомлять пользователей о своем состоянии, значительно упрощая администрирование сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Задания можно запускать вручную, по расписанию или в ответ на оповещения.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|||  
|-|-|  
|**Описание**|**Раздел**|  
|Содержит сведения о создании заданий и назначении владельца.|[Создание заданий](../../ssms/agent/create-jobs.md)|  
|Содержит сведения об организации заданий по категориям.|[Упорядочивание заданий](../../ssms/agent/organize-jobs.md)|  
|Содержит сведения о различных видах шагов заданий, их создании и управлении ими.|[Управление шагами задания](../../ssms/agent/manage-job-steps.md)|  
|Содержит сведения о том, как определить время запуска и частоту выполнения заданий.|[Создание и присоединение расписаний к заданиям](../../ssms/agent/create-and-attach-schedules-to-jobs.md)|  
|Содержит сведения о заданиях, запускаемых вручную (не по расписанию).|[Запуск заданий](../../ssms/agent/run-jobs.md)|  
|Содержит сведения о том, как настроить реакцию агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на задания. Например агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может уведомлять администраторов о завершении заданий.|[Определение ответов заданий](../../ssms/agent/specify-job-responses.md)|  
|Содержит сведения о том, как просмотреть или изменить существующие задания и просмотреть историю их выполнения.|[Просмотр или изменение заданий](../../ssms/agent/view-or-modify-jobs.md)|  
|Содержит сведения об удалении заданий.|[Удаление заданий](../../ssms/agent/delete-jobs.md)|  
  
## <a name="see-also"></a>См. также:  
[Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md)  
  
