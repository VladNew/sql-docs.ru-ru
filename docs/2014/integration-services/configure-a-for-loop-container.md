---
title: Настройка контейнера «цикл по каждому элементу» | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: b9cd7ea7-b198-4a35-8b16-6acf09611ca5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 766a82c975b607687f79a696ce587422b93322bf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81487002"
---
# <a name="configure-a-for-loop-container"></a>Настройка контейнера «цикл по элементам»
  В процедуре описывается, как настроить контейнер «цикл по элементам» с помощью диалогового окна **Редактор циклов по элементам** .  
  
### <a name="to-configure-the-for-loop-container"></a>Настройка контейнера «цикл по элементам»  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]дважды щелкните контейнер "цикл по элементам", чтобы открыть **Редактор циклов по элементам**.  
  
2.  При необходимости измените имя и описание контейнера «цикл по элементам».  
  
3.  При необходимости введите выражение инициализации в текстовое поле **InitExpression** .  
  
4.  Введите выражение в текстовое поле **EvalExpression** .  
  
    > [!NOTE]  
    >  Выражение должно иметь логическое значение. Если значением этого выражения будет `false`, выполнение цикла останавливается.  
  
5.  При необходимости введите выражение присвоения в текстовое поле **AssignExpression** .  
  
6.  При необходимости щелкните **Выражения** и на странице **Выражения** создайте выражения свойств для свойств контейнера «цикл по элементам». Дополнительные сведения см. в разделе [Добавление или изменение выражение свойства](expressions/add-or-change-a-property-expression.md).  
  
7.  Щелкните **ОК** , чтобы закрыть **Редактор циклов For**.  
  
## <a name="see-also"></a>См. также:  
 [Контейнер «цикл по каждому»](control-flow/for-loop-container.md)   
 [Выражения&#41; Integration Services &#40;SSIS](expressions/integration-services-ssis-expressions.md)   
 [Использование выражений свойств в пакетах](expressions/use-property-expressions-in-packages.md)  
  
  
