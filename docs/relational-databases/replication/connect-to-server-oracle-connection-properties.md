---
title: Соединение с сервером Oracle (страница "Свойства соединения") | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.oracleconnection.connectionprops.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 44e7d219fefe3a4ffc10f1727738a549d2a1b630
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "67903085"
---
# <a name="connect-to-server-oracle-connection-properties"></a>Соединение с сервером (Oracle), свойства соединения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Вкладка **Свойства соединения** диалогового окна **Соединение с сервером** позволяет задать параметры публикации **Шлюз** или **Полный**. После идентификации издателя изменить данный параметр без удаления и перенастройки издателя невозможно. Дополнительные сведения см. в статье [Настройка издателя Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Параметры  
 **Тип издателя**  
 Выберите **Шлюз** или **Полный**. Параметр **Полный** обеспечивает публикации моментальных снимков и транзакций полным набором поддерживаемых функций, необходимых для публикаций Oracle. Параметр **Шлюз** оптимизирует работу системы для случаев, когда шлюзом между системами выступает репликация. Параметр **Шлюз** нельзя использовать, если одна и та же таблица будет публиковаться в нескольких публикациях транзакций. Если выбран параметр **Шлюз**, то таблица может использоваться только в одной публикации транзакций и в любом количестве публикаций моментальных снимков.  
  
 **Время ожидания**  
 Указывает, как долго распространитель [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен пытаться подключиться к издателю Oracle, прежде чем выдать ошибку времени ожидания.  
  
## <a name="see-also"></a>См. также:  
 [Глоссарий терминов по публикации Oracle](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Настройка производительности для издателей Oracle](../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
