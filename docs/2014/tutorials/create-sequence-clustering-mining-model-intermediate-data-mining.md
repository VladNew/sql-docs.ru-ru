---
title: Создание структуры модели интеллектуального анализа данных (учебник по интеллектуальному анализу интеллектуальному анализу данных) кластеризации последовательностей | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e9339227-6c2e-4c4b-8be2-8c1960bc4a8d
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c18097b6851bc23522882227158b5aad390570e3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37189571"
---
# <a name="creating-a-sequence-clustering-mining-model-structure-intermediate-data-mining-tutorial"></a>Создание структуры модели интеллектуального анализа данных кластеризации последовательностей (учебник по интеллектуальному анализу данных — средний уровень)
  Первым шагом создания последовательности, модели кластеризации интеллектуального анализа данных является использование мастера интеллектуального анализа данных для создания новой структуры интеллектуального анализа данных и модели интеллектуального анализа данных на основе [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритм кластеризации последовательностей.  
  
 Для этой цели будет использоваться представление источника данных, которое использовалось для анализа покупательского поведения, к которому добавляется столбец, содержащий идентификатор `sequence`. В данном сценарии «sequence» означает порядок, в котором покупатели добавляют элементы в свою корзину во время покупок.  
  
 Также будут добавлены несколько столбцов, которые используются в одной из моделей для группировки покупателей по демографическому признаку.  
  
### <a name="to-create-a-sequence-clustering-structure-and-model"></a>Создание структуры кластеризации последовательностей и модели  
  
1.  В обозревателе решений в [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], щелкните правой кнопкой мыши **структуры интеллектуального анализа данных** и выберите **создать структуру интеллектуального анализа**.  
  
2.  На странице **Вас приветствует мастер интеллектуального анализа данных** нажмите кнопку **Далее**.  
  
3.  На **Выбор метода определения** странице, убедитесь, что **из существующей реляционной базы данных или хранилища данных** выбран, а затем нажмите кнопку **Далее**.  
  
4.  На **создать структуру интеллектуального анализа данных** странице, убедитесь, что параметр **Создание структуры интеллектуального анализа данных с моделью интеллектуального анализа данных** выбран. Затем щелкните раскрывающийся список для параметра **какой метод интеллектуального анализа данных вы хотите использовать?** и выберите **кластеризации последовательностей Майкрософт**. Нажмите кнопку **Далее**.  
  
     **Выбор представления источников данных** появится страница. В разделе **доступные представления источников данных**выберите `Orders`.  
  
     Заказы — это то представление источника данных, которое использовалось для сценария потребительской корзины. Если вы не создали это представление источника данных, см. в разделе [Добавление представления источников данных с вложенными таблицами &#40;данных учебник по интеллектуальному анализу&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md).  
  
5.  Нажмите кнопку **Далее**.  
  
6.  На **определение типов таблиц** выберите **случай** флажок рядом с полем **vAssocSeqOrders** таблицу и команду **Nested** "флажок" рядом с полем **vAssocSeqLineItems** таблицы. Нажмите кнопку **Далее**.  
  
    > [!NOTE]  
    >  Если произошла ошибка при выборе **случай** или **Nested** флажки, возможно, что соединение в представлении источника данных не верен. Вложенная таблица, **vAssocSeqLineItems**, должны быть подключены к таблице вариантов, **vAssocSeqOrders,** с помощью соединения многие к одному. Можно изменить эту связь, щелкнув правой кнопкой мыши на линии соединения и затем изменив направление соединения на обратное. Дополнительные сведения см. в разделе [создать или изменить окно связи &#40;службы Analysis Services — многомерные данные&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md).  
  
7.  На **Определение обучающих данных** выберите столбцы для использования в модели, установив флажок следующим образом:  
  
    -   **IncomeGroup** выберите **ввода** "флажок".  
  
         Данный столбец содержит полезную информацию о покупателях, которую можно использовать для кластеризации. Такая информация будет использоваться в первой модели и не будет учитываться во второй.  
  
    -   **OrderNumber** выберите `Key` "флажок".  
  
         Данное поле будет использоваться в качестве идентификатора таблицы вариантов либо значения `Key`. В целом ключевое поле таблицы вариантов никогда не используется в качестве входных данных, поскольку ключ содержит уникальные значения, не представляющие интереса для кластеризации.  
  
    -   **Регион** выберите **ввода** "флажок".  
  
         Данный столбец содержит полезную информацию о покупателях, которую можно использовать для кластеризации. Такая информация будет использоваться в первой модели и не будет учитываться во второй.  
  
    -   **LineNumber** выберите `Key` и **ввода** флажки.  
  
         **LineNumber** поле будет использоваться в качестве идентификатора для вложенной таблицы, или `Sequence Key`. Ключ для вложенной таблицы всегда должен использоваться для ввода.  
  
    -   **Модель** выберите **ввода** и **прогнозируемый** флажки.  
  
     Убедитесь, что выбранные параметры указаны правильно и нажмите кнопку **Далее**.  
  
8.  На **содержимого и типа данных столбцов укажите** странице, убедитесь, что в сетке содержатся столбцы, типы содержимого и типы данных, приведенные в следующей таблице и нажмите кнопку **Далее**.  
  
    |Таблицы и столбцы|Тип содержимого|Тип данных|  
    |---------------------|------------------|---------------|  
    |IncomeGroup|Discrete|Текст|  
    |OrderNumber|Key|Текст|  
    |Region|Discrete|Текст|  
    |vAssocSeqLineItems|||  
    |Line Number|Ключевая последовательность|Long|  
    |Модель|Discrete|Текст|  
  
9. На **создание проверочного набора** странице **процент проверочных данных** 20, а затем нажмите кнопку **Далее**.  
  
10. На **завершение работы мастера** странице для **имя структуры интеллектуального анализа данных**, тип `Sequence Clustering with Region`.  
  
11. Для **имя модели интеллектуального анализа данных**, тип `Sequence Clustering with Region`.  
  
12. Проверьте **разрешить детализацию** , а затем щелкните **Готово**.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Обработка модели кластеризации последовательностей](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
## <a name="see-also"></a>См. также  
 [Конструктор интеллектуального анализа данных](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Алгоритм кластеризации последовательностей (Майкрософт)](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)  
  
  