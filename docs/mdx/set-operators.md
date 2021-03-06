---
title: Операторы SET | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6ad0b92a970c3618584365d9ad6e99420daef05d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68037012"
---
# <a name="set-operators"></a>Операторы наборов


  В многомерных выражениях операторы наборов служат для выполнения операций над элементами и наборами, возвращающими набор. Операторы наборов часто используются в многомерных выражениях вместо нескольких функций наборов.  
  
 В многомерных выражениях поддерживаются операторы наборов, перечисленные в следующей таблице.  
  
|Оператор|Описание|  
|--------------|-----------------|  
|[- (исключение)](../mdx/except-mdx-operator.md)|Возвращает разность двух наборов, удаляя повторяющиеся элементы.<br /><br /> Этот оператор функционально эквивалентен функции [except](../mdx/except-mdx-function.md) .|  
|[* (перекрестное соединение)](../mdx/crossjoin-mdx-operator-reference.md)|Возвращает перекрестное произведение двух наборов.<br /><br /> Этот оператор функционально эквивалентен функции [перекрестного](../mdx/crossjoin-mdx.md) соединения.|  
|[, перечислены ниже. (Range)](../mdx/range-mdx.md)|Возвращает естественно упорядоченный набор, ограниченный двумя указанными элементами. Набор содержит все элементы между ними и сами конечные элементы.|  
|[+ (объединение множеств)](../mdx/union-mdx-operator-reference.md)|Возвращает объединение двух наборов, исключая повторяющиеся элементы.<br /><br /> Этот оператор функционально эквивалентен функции [Union &#40;многомерные выражения&#41;](../mdx/union-mdx.md) .|  
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)   
 [Справочник по операторам многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-operator-reference-mdx.md)   
 [Операторы &#40;синтаксиса многомерных выражений&#41;](../mdx/operators-mdx-syntax.md)  
  
  
