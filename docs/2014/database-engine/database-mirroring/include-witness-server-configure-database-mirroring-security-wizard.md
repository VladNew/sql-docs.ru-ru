---
title: Включение следящего сервера (мастер настройки безопасности зеркального отображения баз данных) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.inclwitness.f1
ms.assetid: f04b38a4-f4e2-4d4c-bdac-7cc70e5a5684
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9f588b8a4305f44eceb8a8f6ab351bc940fbfef5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62754939"
---
# <a name="include-witness-server-configure-database-mirroring-security-wizard"></a>Включить следящий сервер (мастер настройки безопасности зеркального отображения баз данных)
  Используйте эту страницу, чтобы указать, включать ли следящий сервер в конфигурацию безопасности для зеркального отображения базы данных.  
  
 **Настройка зеркального отображения базы данных в среде SQL Server Management Studio**  
  
-   [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (среда SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Запуск мастера настройки безопасности зеркального отображения баз данных (среда SQL Server Management Studio)](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Параметры  
 **Да**  
 Нажмите, чтобы включить экземпляр следящего сервера в конфигурацию безопасности. Следящий сервер необходим для режима высокого уровня безопасности с автоматической отработкой отказа, который дает возможность автоматического перехода на экземпляр зеркального сервера при сбое в работе экземпляра основного сервера.  
  
 **Нет**  
 Нажмите, чтобы настроить безопасность без следящего сервера.  
  
## <a name="see-also"></a>См. также  
 [Свойства базы данных &#40;страница зеркального отображения&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [SQL Server &#40;зеркального отображения базы данных&#41;](database-mirroring-sql-server.md)   
 [Database Mirroring Witness](database-mirroring-witness.md)  
  
  
