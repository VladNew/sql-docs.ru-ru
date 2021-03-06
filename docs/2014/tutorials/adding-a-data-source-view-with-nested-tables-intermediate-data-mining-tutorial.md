---
title: Добавление представления источников данных с вложенными таблицами (учебник по интеллектуальному анализу данных — средний уровень) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a14cd7f1-7a10-4ec6-af6a-f5f0676a0308
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 648b9d561ae340b67ed5e2d1aa878969e5a3bc47
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62822785"
---
# <a name="adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial"></a>Добавление представления источников данных с вложенными таблицами (учебник по интеллектуальному анализу данных — средний уровень)
  Для создания модели потребительской корзины необходимо использовать представление источника данных, поддерживающее ассоциативных данные. Это представление также будет использоваться в сценарии кластеризации последовательностей.  
  
 Это представление источника данных отличается от других, с которыми вы могли работать, так как содержит *вложенную таблицу*. *Вложенная таблица* содержит несколько строк сведений о одной строке в таблице вариантов. Например, если модель анализирует поведение клиентов в процессе покупки, обычно в качестве таблицы вариантов используется таблица, содержащая уникальную строку для каждого клиента. Однако каждый клиент может выполнить несколько покупок, и может понадобиться проанализировать последовательность покупок или продукты, часто приобретаемые совместно. Для логического представления данных покупок в модели необходимо добавить в представление источника данных еще одну таблицу, в которой будут перечисляться покупки каждого клиента.  
  
 Вложенная таблица покупок связана с таблицей клиентов связью «многие к одному». Вложенная таблица может содержать множество строк для каждого клиента, а каждая строка содержит один купленный продукт, иногда с дополнительными сведениями о заказах, на основании которых были сделаны покупки, о цене на момент заказа или любых действовавших акциях. Сведения вложенной таблицы можно использовать в качестве входных данных для модели или прогнозируемого атрибута.  
  
 На этом занятии будут выполнены следующие действия.  
  
-   В источник [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] данных добавляется представление источника данных.  
  
-   В данное представление будут добавлены таблица вариантов и вложенные таблицы.  
  
-   Будет задана связь «многие к одному» между таблицей вариантов и вложенной таблицей.  
  
    > [!NOTE]  
    >  . Очень важно точно следовать описанной процедуре и правильно задать связь между таблицей вариантов и вложенной таблицей, иначе при попытке обработки модели могут появиться ошибки.  
  
-   Затем задается способ использования столбцов данных в модели.  
  
 Дополнительные сведения о работе с вариантами и вложенными таблицами, а также о выборе ключа вложенной таблицы см. в разделе [вложенные таблицы &#40;Analysis Services-&#41;интеллектуального анализа данных ](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).  
  
### <a name="to-add-a-data-source-view"></a>Добавление представления источников данных  
  
1.  В обозреватель решений щелкните правой кнопкой мыши элемент **представления источников данных**и выберите пункт **создать представление источника данных**.  
  
     Будет открыт мастер представлений источников данных.  
  
2.  На странице **Мастер представления источника данных** нажмите кнопку **Далее**.  
  
3.  На странице **Выбор источника данных** в разделе **реляционные источники данных**выберите источник [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] данных, созданный в учебнике по основам интеллектуального анализа данных. Нажмите кнопку **Далее**.  
  
4.  На странице **Выбор таблиц и представлений** выберите следующие таблицы, а затем щелкните стрелку вправо, чтобы включить их в новое представление источника данных:  
  
    -   `vAssocSeqOrders`  
  
    -   `vAssocSeqLineItems`  
  
5.  Нажмите кнопку **Далее**.  
  
6.  На странице **Завершение работы мастера** по умолчанию представление источника данных имеет имя [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. Измените имя на `Orders`, а затем нажмите кнопку **Готово**.  
  
     Откроется конструктор представлений источников данных, и `Orders` появится представление источника данных.  
  
### <a name="to-create-a-relationship-between-tables"></a>Создание связи между таблицами  
  
1.  В конструкторе представлений источников данных расположите две таблицы горизонтально друг напротив друга, поместив таблицу vAssocSeqLineItems слева, а vAssocSeqOrders — справа.  
  
2.  Выберите столбец **OrderNumber** в таблице vAssocSeqLineItems.  
  
3.  Перетащите столбец в таблицу vAssocSeqOrders и вставьте его в столбец **OrderNumber** .  
  
    > [!IMPORTANT]  
    >  Не забудьте перетащить столбец **OrderNumber** из вложенной таблицы vAssocSeqLineItems, которая представляет собой множество сторон объединения, в таблицу вариантов vAssocSeqOrders, которая представляет одну сторону объединения.  
  
     Теперь между таблицами vAssocSeqLineItems и vAssocSeqOrders существует новая *связь "многие к одному* ". Если соединение таблиц выполнено правильно, должно появиться следующее представление источника данных:  
  
     ![ожидаемое соединение «многие к одному» вложенной таблицы и таблицы вариантов](../../2014/tutorials/media/dsv-nestedjoin-illustration.gif "ожидаемое соединение «многие к одному» вложенной таблицы и таблицы вариантов")  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Руководство по созданию структуры потребительской корзины и модели &#40;промежуточного интеллектуального анализа данных&#41;](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Учебник по интеллектуальному анализу данных &#40;Analysis Services — интеллектуальный анализ данных&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Структуры интеллектуального анализа данных &#40;Analysis Services — интеллектуальный анализ&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Модели интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
