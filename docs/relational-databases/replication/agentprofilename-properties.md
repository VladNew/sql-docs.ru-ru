---
title: Свойства &lt;AgentProfileName&gt; | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.profiles.perfprofileprops.f1
helpviewer_keywords:
- Agent Profile Properties dialog box
ms.assetid: 01a992d2-e4ff-417c-93f0-dc43ab2d1624
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 7d7607d8749f99452d58374eb2a83c6a31f640d3
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "76288260"
---
# <a name="ltagentprofilenamegt-properties"></a>Свойства &lt;AgentProfileName&gt;
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Диалоговое окно **Свойства профиля агента** позволяет просматривать значения всех параметров агента, указанных в профиле, и изменять эти значения для пользовательских профилей.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Имя профиля.  
  
 **Описание**  
 Описание профиля.  
  
 **Параметр**  
 Параметры агента, включенные в профиль. Профили не должны задавать значения для каждого параметра. Для просмотра всех допустимых для данного агента параметров снимите флажок **Показывать только параметры, используемые в этом профиле** . Описание каждого параметра см. в разделах:  
  
-   [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
-   [Агент чтения журнала репликации](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
-   [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
-   [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md)  
  
-   [Replication Queue Reader Agent](../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
 **Значение по умолчанию**  
 Значение по умолчанию для каждого параметра агента.  
  
 **Value**  
 Значение, заданное для данного параметра в профиле. Для пользовательских профилей это поле можно изменять.  
  
 **Показывать только параметры, используемые в этом профиле**  
 Снимите флажок, чтобы отобразить все корректные параметры для данного агента.  
  
## <a name="see-also"></a>См. также:  
 [Работа с профилями агента репликации](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Обзор агентов репликации](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Профили агента репликации](../../relational-databases/replication/agents/replication-agent-profiles.md)  
  
  
