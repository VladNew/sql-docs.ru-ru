---
title: Числовые функции (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC numeric functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], numeric functions
- numeric functions [ODBC]
- FoxPro ODBC driver [ODBC], numeric functions
ms.assetid: 7caab48e-cbb5-4bbc-a09b-5cf902e5bc45
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3993a9a1b2412cb15229f2763c7c3b38f6b7862
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298164"
---
# <a name="numeric-functions-visual-foxpro-odbc-driver"></a>Числовые функции (драйвер ODBC для Visual FoxPro)
В следующей таблице описаны числовые функции ODBC, поддерживаемые драйвером ODBC для Visual FoxPro. Если грамматика Visual FoxPro для той же функции отличается от синтаксиса ODBC, в списке отображается эквивалент Visual FoxPro.  
  
|Грамматика ODBC|Грамматика Visual FoxPro|  
|------------------|---------------------------|  
|ABS *(numeric_exp)*||  
|ACOS *(float_exp)*||  
|ASIN *(float_exp)*||  
|ATAN *(float_exp)*||  
|ATAN2 *(float_exp1, float_exp2)*|ATN2 (*float_exp1, float_exp2*)|  
|CEILING *(numeric_exp)*||  
|COS *(float_exp)*||  
|COT *(float_exp)*||  
|ГРАДУСы *(numeric_exp)*|РТОД *(numeric_exp)*|  
|EXP *(float_exp)*||  
|ЭТАЖ *(numeric_exp)*||  
|Журнал *(float_exp)*||  
|LOG10 *(float_exp)*||  
|MOD *(integer_exp1, integer_exp2)*||  
|PI *()*||  
|РАДИАНы *(numeric_exp)*|DTOR *(numeric_exp)*|  
|RAND *([integer_exp])*||  
|ROUND *(numeric_exp, integer_exp)*||  
|ЗНАК *(numeric_exp)*||  
|SIN *(float_exp)*||  
|SQRT *(float_exp)*||  
|TAN *(float_exp)*||  
  
 Следующие числовые функции не поддерживаются:  
  
 МОЩНОСТЬ *(numeric_exp, integer_exp)*  
  
 TRUNCATE *(numeric_exp, integer_exp)*
