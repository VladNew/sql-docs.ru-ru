---
title: Автоматическое заполнение IPD | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- automatically populating ipd [ODBC]
- descriptors [ODBC], automatically populating ipd
- descriptors [ODBC], allocating and freeing
- ipd [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1184a7d8-d557-4140-843b-6633ae6deacc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1998ea1992ee7f14d87d01e348d955b017166088
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81285074"
---
# <a name="automatic-population-of-the-ipd"></a>Автоматическое заполнение IPD
Некоторые драйверы могут задавать поля IPD после подготовки параметризованного запроса. Поля дескриптора автоматически заполняются сведениями о параметре, включая тип данных, точность, масштаб и другие характеристики. Это эквивалентно поддержке **SQLDescribeParam**. Эта информация может быть особенно полезной для приложения, если у него нет другого способа обнаружить его, например при выполнении нерегламентированного запроса с параметрами, о которых приложение не знает.  
  
 Приложение определяет, поддерживает ли драйвер автоматическое заполнение, вызывая **SQLGetConnectAttr** с *атрибутом* SQL_ATTR_AUTO_IPD. Если возвращается SQL_TRUE, драйвер поддерживает его, и приложение может включить его, задав для атрибута инструкции SQL_ATTR_ENABLE_AUTO_IPD значение SQL_TRUE.  
  
 Если автоматическое заполнение поддерживается и включено, драйвер заполняет поля функции IPD после того, как инструкция SQL, содержащая маркеры параметров, была подготовлена вызовом **SQLPrepare**. Приложение может получить эти сведения, вызвав **SQLGetDescField** или **SQLGetDescRec**или **SQLDescribeParam**. Приложение может использовать эти сведения для привязки наиболее подходящего буфера приложения для параметра или для указания преобразования данных для него.  
  
 Автоматическое заполнение IPD может привести к снижению производительности. Приложение может отключить его путем сброса атрибута SQL_ATTR_ENABLE_AUTO_IPD инструкции в SQL_FALSE (значение по умолчанию).
