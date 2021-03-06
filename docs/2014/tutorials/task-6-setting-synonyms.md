---
title: Задача 6. Настройка синонимов | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b7d35ee9-d1c9-41d9-bbc5-0ca7db93e54d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 4499a0a099c92a9b1802cc905da3d0a473808eeb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "78177232"
---
# <a name="task-6-setting-synonyms"></a>Задача 6. Задание синонимов
  В этой задаче вы зададите два значения, **USA** и **США**, домена **Страна** как синонимы, при этом **США** будет начальным значением. Поскольку параметр **Использовать начальные значения** был выбран при создании домена **Страна** , все значения **USA** для домена **Страна** будут выводиться как **США** (при этом «США» — начальное значение). Дополнительные сведения см. в разделе [Изменение значений домена](https://msdn.microsoft.com/library/hh510408.aspx) .

1.  Выберите **Страна** в списке доменов.

2.  Перейдите на вкладку **Значения домена** .

3.  Нажмите кнопку **Добавить новое значение домена** на панели инструментов.

4.  Введите **USA** и нажмите клавишу **ВВОД**.

5.  Выберите **США** и **USA** с помощью клавиш CTRL или SHIFT, щелкните правой кнопкой выделенные элементы и выберите пункт **Установить как синонимы**. Службы DQS сгруппируют эти значения и назначат одно из значений в качестве ведущего, которым будут заменяться другие.

     ![Меню «Задать как синонимы»](../../2014/tutorials/media/et-settingsynonyms-01.jpg "Меню «Задать как синонимы»")

6.  Обратите внимание, что значение **США** задано как начальное. Если вы хотите, чтобы «USA» было начальным значением, щелкните «USA» правой кнопкой мыши и выберите параметр **Установить в качестве ведущего** . В этом учебнике мы будем использовать значение **США** как начальное.

     ![«United States» и «USA» как синонимы](../../2014/tutorials/media/et-settingsynonyms-02.jpg "«United States» и «USA» как синонимы")

## <a name="next-step"></a>Следующий шаг
 [Задача 7. Создание составного домена](../../2014/tutorials/task-7-creating-a-composite-domain.md)


