---
title: Создание главного ключа базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: jaszymas
ms.author: jaszymas
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bb8730a00c09b57fdabf3465b290cd2df63b1bc4
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "79510035"
---
# <a name="create-a-database-master-key"></a>Создание главного ключа базы данных

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
В этом разделе описывается создание главного ключа базы данных в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи [!INCLUDE[tsql](../../../includes/tsql-md.md)].

## <a name="security"></a>безопасность

### <a name="permissions"></a>Разрешения

Требует разрешения CONTROL для базы данных.

## <a name="using-transact-sql"></a>Использование Transact-SQL

### <a name="to-create-a-database-master-key"></a>Создание главного ключа базы данных

1. Выберите пароль для шифрования копии главного ключа базы данных, которая будет храниться в базе данных.
2. В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].
3. Разверните узел **Системные базы данных**, щелкните правой кнопкой мыши базу данных `master` и выберите пункт **Создать запрос**.
4. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.

   ```sql
     -- Creates the master key.
     -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe".  
     CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';  

   ```

Дополнительные сведения см. в разделе [CREATE MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-master-key-transact-sql.md).
