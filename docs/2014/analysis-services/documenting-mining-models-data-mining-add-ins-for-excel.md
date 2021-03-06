---
title: Документирование моделей интеллектуального анализа (надстройки интеллектуального анализа данных для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- documenting models
- mining structures, managing
- mining models, managing
- model properties
ms.assetid: 0a663e11-e40c-4708-ad18-fabb6c976fa4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: afe304e3fa76be805a64e9bd662bc21500ac2fa7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66081592"
---
# <a name="documenting-mining-models-data-mining-add-ins-for-excel"></a>Документирование моделей интеллектуального анализа данных (надстройки интеллектуального анализа данных для Excel)
  ![Кнопка «Документирование модели» на ленте «Интеллектуальный анализ данных»](media/dmc-docmodel.gif "Кнопка «Документирование модели» на ленте «Интеллектуальный анализ данных»")  
  
 Мастер **документирования модели** создает отчет, который предоставляет полезные сведения о созданных моделях интеллектуального анализа данных. При помощи документирования созданной модели можно отслеживать источник данных, используемых для формирования модели, получать дополнительные сведения о времени обработки модели и отслеживать изменения параметров, влияющие на результаты модели.  
  
## <a name="using-the-document-model-wizard"></a>Использование мастера документирования модели  
  
1.  Перейдите на вкладку **интеллектуальный анализ данных** .  
  
2.  В группе **Использование модели** щелкните **документ модель**.  
  
3.  В диалоговом окне **Выбор модели** выберите модель для отчета, а затем нажмите кнопку **Далее**. Мастер **документов** необходимо запускать отдельно для каждой модели, которую необходимо документировать.  
  
4.  В диалоговом окне **Выбор сведений о документации** выберите один из двух вариантов: **полные сведения** или **Сводные данные**.  
  
5.  Нажмите кнопку **Готово**.  
  
6.  Мастер автоматически создает новый лист, содержащий указанный отчет, озаглавленную **документацию по модели**.  
  
## <a name="understanding-the-report"></a>Основные сведения об отчете  
 Создавая отчет, документирующий модель интеллектуального анализа данных, можно создать как сводку, содержащую основные сведения — имя и описание модели, так и полный отчет, содержащий сведения о лежащей в основе структуре и расширенные сведения о модели интеллектуального анализа данных.  
  
 В зависимости от алгоритма, использованного для создания модели, предоставляются различные типы данных. Например, в модели взаимосвязей пользователи будут заинтересованы в сведениях о числе наборов элементов и о числе сформированных правил. В модели кластеризации больший интерес будет предоставлять число кластеров.  
  
 В следующей таблице перечисляются параметры и сведения, предоставляемые в отчете для каждого параметра.  
  
> [!NOTE]  
>  По умолчанию для столбцов в отчете устанавливается определенный размер. Следовательно, если имена столбцов или значения имеют слишком большую длину, то они могут быть скрыты или могут быть отображены в Excel как серия символов ###. Чтобы отобразить значения, следует изменить размер строки. Если ячейка выбрана, то для отображения полного значения или строки можно щелкнуть и перетащить двойные стрелки на правом крае строки формул.  
  
### <a name="summary-report"></a>Сводный отчет  
  
||||  
|-|-|-|  
|**Метаданные**|Имя модели<br /><br /> Описание модели<br /><br /> Имя алгоритма<br /><br /> Дата последней обработки||  
|**Результирующие данные модели**|Взаимосвязь|Число наборов элементов<br /><br /> Число правил|  
||Кластеризация|Число кластеров<br /><br /> Несущее множество каждого кластера|  
||Дерево решений|Количество деревьев<br /><br /> Количество узлов в каждом дереве|  
||Линейная регрессия|Количество деревьев (всегда 1)<br /><br /> Количество узлов (всегда 1)|  
||Упрощенный алгоритм Байеса|Важные атрибуты|  
||Нейронная сеть|Количество входных узлов<br /><br /> Количество выходных узлов<br /><br /> Количество скрытых узлов|  
||Кластеризация последовательностей|Число кластеров|  
  
### <a name="complete-report"></a>Полный отчет  
 В полный отчет включаются все данные, содержащиеся в сводном отчете, а также подробные сведения о столбцах данных, использованных в модели, и результаты анализа.  
  
||||  
|-|-|-|  
|**Метаданные**|Метаданные модели|Параметры и значения алгоритма|  
||Метаданные столбца|Имя столбца<br /><br /> Использование<br /><br /> Тип данных<br /><br /> Тип содержимого<br /><br /> Значения (список дискретных значений или диапазон значений)|  
|**Статистика модели**|Непрерывные столбцы|Среднее значение<br /><br /> Минимальное значение<br /><br /> Максимальное значение<br /><br /> Корень среднеквадратичной погрешности<br /><br /> Средняя абсолютная погрешность<br /><br /> Логарифмическая оценка<br /><br /> Формула регрессии (только для моделей с линейной регрессией)|  
||Дискретные столбцы|Число передач<br /><br /> Число сбоев<br /><br /> Логарифмическая оценка<br /><br /> Точность прогноза|  
  
> [!NOTE]  
>  Документировать можно любой тип модели, поддерживаемый службами SQL Server Analysis Services. Следовательно, в таблице перечисляются некоторые типы моделей, которые не могут быть созданы с помощью средств анализа таблиц или с помощью мастеров клиента интеллектуального анализа данных. Однако все типы моделей можно создать с помощью **расширенного редактора запросов интеллектуального анализа данных**. Дополнительные сведения см. в разделе [Query &#40;SQL Server надстроек интеллектуального анализа данных&#41;](query-sql-server-data-mining-add-ins.md).  
  
## <a name="see-also"></a>См. также  
 [Развертывание и масштабирование моделей интеллектуального анализа &#40;надстройки интеллектуального анализа данных для Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
