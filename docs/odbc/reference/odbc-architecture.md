---
title: Архитектура ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], components
- ODBC architecture [ODBC]
ms.assetid: 2604f492-587b-4a51-9876-59a7870b3ef2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07435dc1a5fbe800f2260e914f315cfe93dd8d1b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305135"
---
# <a name="odbc-architecture"></a>Архитектура ODBC
Архитектура ODBC состоит из четырех компонентов:  
  
-   **Приложение** Выполняет обработку и вызывает функции ODBC для отправки инструкций SQL и получения результатов.  
  
-   **Диспетчер драйверов** Загрузка и выгрузка драйверов от имени приложения. Обрабатывает вызовы функции ODBC или передает их драйверу.  
  
-   **Драйвер** Обрабатывает вызовы функций ODBC, отправляет запросы SQL в конкретный источник данных и возвращает результаты приложению. При необходимости драйвер изменяет запрос приложения таким образом, что запрос соответствует синтаксису, поддерживаемому связанной СУБД.  
  
-   **Источник данных** Содержит данные, к которым пользователь хочет получить доступ, и связанную с ним операционную систему, СУБД и сетевую платформу (если есть), используемые для доступа к СУБД.  
  
 Обратите внимание на следующие моменты, связанные с архитектурой ODBC. Во первых, могут существовать несколько драйверов и источников данных, что позволяет приложению одновременно получать доступ к данным из нескольких источников данных. Во-вторых, API ODBC используется в двух местах: между приложением и диспетчером драйверов, а также между диспетчером драйверов и каждым драйвером. Интерфейс между диспетчером драйверов и драйверами иногда называют *интерфейсом поставщика услуг* или *SPI*. Для ODBC интерфейс прикладного программирования (API) и интерфейс поставщика услуг (SPI) одинаковы; то есть диспетчер драйверов и каждый драйвер имеют один и тот же интерфейс для одних и тех же функций.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Приложения](../../odbc/reference/applications.md)  
  
-   [Диспетчер драйверов](../../odbc/reference/the-driver-manager.md)  
  
-   [Драйверы](../../odbc/reference/drivers.md)  
  
-   [Источники данных](../../odbc/reference/data-sources.md)
