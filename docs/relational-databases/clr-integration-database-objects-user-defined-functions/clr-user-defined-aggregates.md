---
title: Определяемые пользователем статистические функции CLR | Документация Майкрософт
description: SQL Server интеграция со средой CLR позволяет создавать пользовательские агрегатные функции в управляемом коде, которые выполняют вычисления с набором значений и возвращают значение.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
author: rothja
ms.author: jroth
ms.openlocfilehash: 9267e1e1e0b051dbbd8581b694aafacd2e5ce8a9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488306"
---
# <a name="clr-user-defined-aggregates"></a>Пользовательские агрегатные функции среды CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Агрегатные функции выполняют вычисление на наборе значений и возвращают одиночное значение. Традиционно поддерживаются только встроенные агрегатные функции, такие как **Sum** или Max, которые работают с набором входных скалярных значений и создают одно статистическое значение из этого набора. **MAX** [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Но теперь интеграция [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] со средой [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR позволяет создавать в управляемом коде пользовательские агрегатные функции и предоставлять доступ к ним из [!INCLUDE[tsql](../../includes/tsql-md.md)] или другого управляемого кода.  
  
 В следующей таблице приводится список подразделов данного раздела.  
  
 [Требования для определяемых пользователем статистических функций CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates-requirements.md)  
 Содержит общие сведения о требованиях к реализации определяемых пользователем агрегатных функций среды CLR.  
  
 [Вызов определяемых пользователем агрегатных функций CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)  
 Рассказывает о способах вызова определяемой пользователем статистической функции.  
  
  
