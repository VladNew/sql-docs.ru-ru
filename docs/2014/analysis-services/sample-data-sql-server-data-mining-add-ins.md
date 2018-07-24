---
title: Образец данных (SQL Server Data Mining Add-ins) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- holdout
- testing cases
- training cases
- partitioning data [data mining]
- mining models, testing
ms.assetid: 35907ae6-887f-4cb3-a750-cff3d7683d90
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5984bbbaa3dc2bb55ce8f20a59dd5132de0ca72a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178971"
---
# <a name="sample-data-sql-server-data-mining-add-ins"></a>Образец данных (надстройки интеллектуального анализа данных SQL Server)
  ![Мастер секционирования данных на ленте «Интеллектуальный анализ данных»](media/dmc-partition.gif "мастер секционирования данных на ленте «Интеллектуальный анализ данных»")  
  
 **Демонстрационные данные** мастер позволяет легко разделить исходные данные на два набора: один для построения (обучения) модели, а второй для проверки модели. Этот мастер предоставляет также возможность повторной выборки данных для построения нового набора данных, который лучше представляет решение.  
  
 Создание нужного вида данных для обучения и проверки моделей является важной частью интеллектуального анализа данных, но без использования соответствующих средств оно может быть довольно утомительным. Мастер выполняет стратифицированную выборку, чтобы убедиться, что обучающие и проверочные наборы хорошо сбалансированы.  
  
## <a name="random-sampling-and-oversampling"></a>Случайная и избыточная выборка  
 , и делает это по-другому. Случайная выборка является оптимальным способом обеспечения того, что данные, используемые для проверки модели, объективно представляют данные, используемые для создания модели. Можно произвести случайную выборку данных, хранимых в Excel или во внешнем источнике данных.  
  
 При использовании параметра случайной выборки **демонстрационные данные** мастер автоматически создает обучающий и проверочный наборы данных и выдает их в отдельных листах Excel для последующего просмотра.  
  
 Если данные хранятся в книге Excel, а не с внешним источником данных, у вас также есть вариант использования *Избыточная выборка*. При использовании этого параметра указывается целевое значение, которое может редко встречаться в данных, а мастер начинает сбор сбалансированного набора, содержащего целевое значение. Можно дать мастеру задание выбрать целевую процентную долю или определенное количество строк.  
  
 При использовании параметра избыточной выборки, **демонстрационные данные** мастер создаст новый лист, содержащий вновь Сбалансированные данные образца.  
  
## <a name="using-the-sample-data-wizard"></a>Использование мастера образцов данных  
  
#### <a name="to-separate-data-into-training-and-testing-sets"></a>Разбиение данных на обучающий и проверочный наборы данных  
  
1.  В **интеллектуального анализа данных** ленты, нажмите кнопку **демонстрационные данные**.  
  
2.  На **Выбор источника данных** , определите ли **данных** требуется секционировать находится в таблице или диапазоне Excel, или во внешнем источнике данных.  
  
3.  На **Выбор типа выборки** , определите, хотите ли вы создать обучающий и проверочный набор данных при помощи случайной выборки или создайте новый набор данных, избыточную выборку.  
  
    > [!NOTE]  
    >  При использовании внешнего источника данных доступен только параметр случайной выборки. Если для внешних данных требуется использовать избыточную выборку, данные можно импортировать в книгу Excel при помощи подключения к источнику данных Excel, а затем воспользоваться мастером образцов данных.  
  
4.  Параметры настройки зависят от выбранного метода выборки.  
  
    -   Для случайной выборки укажите либо долю исходных данных, которую нужно использовать для проверки, или общее число строк, используемых в проверочном наборе данных.  
  
    -   Для избыточной выборки выберите столбец и значение, которое нужно особо выделить. Затем задайте общее число строк в новом наборе данных и долю строк в этом наборе, которые должны включать целевое значение.  
  
         Целевое значение для избыточной выборки должно быть дискретным значением; нельзя выполнять избыточную выборку непрерывных числовых данных.  
  
5.  На **страницу завершения**Примите имена по умолчанию для новых наборов данных, или введите новое имя.  
  
     Мастер создает новый лист для каждого набора данных.  
  
 Большинство мастеров в клиенте интеллектуального анализа данных для Excel предоставляют также возможность случайно разделить данные на обучающий и проверочный наборы. Но при использовании мастеров данные остаются в том же листе или в другом источнике данных, а сведения о том, относится конкретная строка к проверочному или обучающему варианту, сохраняются внутренне. Напротив, при использовании **демонстрационные данные** мастер проверочные и обучающие данные выводятся в отдельные листы для справки.  
  
## <a name="related-options"></a>Связанные параметры  
 При работе с мастером вам будут доступны следующие параметры.  
  
|Параметры|Комментарии|  
|-------------|--------------|  
|Диалоговое окно «Выбор источника данных» (клиент интеллектуального анализа данных для Excel)|Выберите диапазон или таблицу Excel, которая содержит данные. Если необходимо использовать внешние данные, это могут быть реляционные данные, но их следует включить в источник данных [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. T|  
|Страница «Выбор типа выборки» (клиент интеллектуального анализа данных для Excel)|При использовании внешнего источника данных доступен только режим случайной выборки. Кроме того, необходимо указать число строк для создания в конечном наборе данных, с помощью **число строк** параметр. Процент от исходных данных указать нельзя.|  
|Страница «Случайная выборка» (клиент интеллектуального анализа данных для Excel)|Можно скопировать выраженную в процентах часть строк из источника или определенное количество строк.|  
|Страница «Избыточная выборка» (клиент интеллектуального анализа данных для Excel)|**Целевое состояние**<br /><br /> Выберите из списка значение, недостаточно представленное в исходном наборе данных. Избыточная выборка увеличит пропорцию строк данных, включающих это состояние.<br /><br /> **Размер выборки**<br /><br /> Выберите общее количество извлекаемых строк. Это значение представляет размер окончательного набора данных.|  
  
## <a name="other-sampling-options"></a>Другие параметры выборки  
 Если параметры выборки этого мастера не соответствуют конкретным потребностям, то можно с помощью преобразования выборки в службах SQL Server Integration Services (SSIS) произвести выборку строк из нескольких источников данных.  
  
 Дополнительные сведения см. в разделе [Row Sampling Transformation](../integration-services/data-flow/transformations/row-sampling-transformation.md) и [преобразование «Процентная выборка»](../integration-services/data-flow/transformations/percentage-sampling-transformation.md).  
  
## <a name="see-also"></a>См. также  
 [Контрольный список для подготовки к интеллектуальному анализу данных](checklist-of-preparation-for-data-mining.md)  
  
  