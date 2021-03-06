---
title: Изменение учетной записи для ведения журнала развертывания служб SSIS с горизонтальным увеличением масштаба | Документы Майкрософт
description: В этой статье описывается, как изменять настройки учетной записи пользователя для развертывания SSIS с горизонтальным увеличением масштаба.
ms.custom: performance
ms.date: 12/13/2017
ms.prod: sql
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
ms.reviewer: maghan
ms.openlocfilehash: 81c1770da78d1d469d1b6ad3a01100abaa9ec829
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82748608"
---
# <a name="change-the-account-for-scale-out-logging"></a>Изменение учетной записи для ведения журнала развертывания служб SSIS с горизонтальным увеличением масштаба

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


При выполнении пакетов SSIS в развертывании с горизонтальным увеличением масштаба сообщения о событиях записываются в базу данных SSISDB с помощью создаваемой автоматически учетной записи пользователя **##MS_SSISLogDBWorkerAgentLogin##** . Для входа этого пользователя в систему применяется проверка подлинности SQL Server.

Чтобы сменить учетную запись, используемую для ведения журнала горизонтального увеличения масштаба, выполните указанные ниже действия.

> [!NOTE]
> Если для ведения журналов применяется учетная запись пользователя Windows, используйте ту же учетную запись, что и для выполнения службы рабочей роли горизонтального увеличения масштаба. В противном случае произойдет ошибка входа в SQL Server.

## <a name="1-create-a-user-for-ssisdb"></a>1. Создание пользователя SSISDB
Инструкции по созданию пользователя базы данных см. в разделе [Создание пользователя базы данных](../../relational-databases/security/authentication-access/create-a-database-user.md).

## <a name="2-add-the-user-to-the-database-role-ssis_cluster_worker"></a>2. Добавление пользователя в роль базы данных ssis_cluster_worker

Инструкции по присоединению роли базы данных см. в разделе [Присоединение к роли](../../relational-databases/security/authentication-access/join-a-role.md).

## <a name="3-update-the-logging-information-in-ssisdb"></a>3. Обновление сведений о ведении журнала в SSISDB
Вызовите хранимую процедуру `[catalog].[update_logdb_info]` с именем SQL Server и строкой подключения в качестве параметров, как показано в следующем примере:

    ```sql
    SET @serverName = CONVERT(sysname, SERVERPROPERTY('servername'))
    SET @connectionString = 'Data Source=' + @serverName + ';Initial Catalog=SSISDB;Integrated Security=SSPI;'
    EXEC [internal].[update_logdb_info] @serverName, @connectionString
    GO
    ```

## <a name="4-restart-the-scale-out-worker-service"></a>4. Перезапуск службы рабочей роли горизонтального увеличения масштаба
Перезапустите службу рабочей роли горизонтального увеличения масштаба, чтобы изменение вступило в силу.

## <a name="next-steps"></a>Дальнейшие действия
-   [Диспетчер горизонтального увеличения масштаба Integration Services](integration-services-ssis-scale-out-manager.md)
