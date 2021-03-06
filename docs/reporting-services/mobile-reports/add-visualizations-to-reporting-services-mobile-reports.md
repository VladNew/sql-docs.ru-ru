---
title: Добавление визуализаций в мобильные отчеты Reporting Services | Документы Майкрософт
description: 'Сведения о трех основных типах диаграмм, которые можно использовать в мобильных отчетах Reporting Services: время, категория, итоги, а также соответствующие сравнительные диаграммы.'
ms.date: 09/26/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 3b220b74-9ecd-4084-93fb-545208d5d7a2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3379d5eb53bc255a09e255d4986eb924912e5eb3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "79447988"
---
# <a name="add-visualizations-to-reporting-services-mobile-reports"></a>Добавление визуализаций в мобильные отчеты Reporting Services
Диаграммы являются неотъемлемой частью визуализации данных. Здесь приведены сведения о диаграммах, которые можно использовать в мобильных отчетах [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] в разных ситуациях. 

[!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-long.md)] имеет три основных типа диаграмм: временная, диаграмма по категориям и диаграмма итоговых значений. Эти типы диаграмм имеют соответствующие сравнительные диаграммы, которые удобно использовать для сравнения двух различных наборов рядов.  

## <a name="shared-chart-properties"></a>Общие свойства диаграмм

Одни свойства применяются ко всем диаграммам, другие — только к некоторым из них. Ниже приведены некоторые общие свойства.

### <a name="number-format"></a>Формат чисел
Числам на диаграмме в [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] можно назначить различные форматы, например общий, валюта с десятичными знаками или без них, проценты с десятичными знаками или без них и т. д. На диаграмме форматирование чисел применяется как к меткам оси, так и к всплывающим окнам точек данных. Форматирование чисел задается для каждой диаграммы в отдельности, а не для всего мобильного отчета целиком. 

* Чтобы задать формат чисел, откройте вкладку **Макет** , выберите диаграмму в рабочей области конструирования, а затем в области **Свойства визуальных элементов** выберите **Формат чисел**. 
  
### <a name="legend"></a>Условные обозначения
* Чтобы показать условные обозначения для диаграммы, откройте вкладку **Макет** , выберите диаграмму в рабочей области конструирования, а затем в области **Свойства визуальных элементов** выберите для **Отображать условные обозначения** значение **Вкл**.
  
### <a name="series"></a>Series
Каждая отдельная метрика или значение, отображаемые на диаграмме, называются рядом. На диаграмме может быть несколько рядов, совместно использующих общую ось x и общую ось y. Ряды определяются на панели свойств данных в представлении данных путем выбора одной или нескольких таблиц данных и полей. При визуализации диаграммы каждое поле будет представлено отдельным рядом точек одного цвета.  

### <a name="change-aggregation"></a>Смена агрегата 
Для числовых полей на диаграммах агрегатом по умолчанию является суммирование. Его можно изменить на среднее, количество, минимум, максимум, первый или последний элемент.

* Откройте вкладку **Данные** и в области **Свойства данных** выберите **Параметры** рядом с числовым полем, а затем выберите другой агрегат.

### <a name="set-or-clear-filters"></a>Задание или очистка фильтров

При добавлении навигатора для фильтрации мобильного отчета можно выбрать фильтруемые диаграммы.

1. Откройте вкладку **Данные** и в области **Свойства данных**выберите **Параметры**.

2. В разделе **Фильтр по**отображаются навигаторы, которые можно выбрать или отменить.

Дополнительные сведения о [добавлении навигаторов для фильтрации мобильного отчета](../../reporting-services/mobile-reports/add-navigators-to-reporting-services-mobile-reports.md).
   
## <a name="time-charts"></a>Диаграммы времени  
  
Диаграмма времени является самой простой в [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)]. Для оси времени (и дат) на диаграмме автоматически назначается первое допустимое поле даты или времени в таблице данных.  

![mobile-report-time-chart](../../reporting-services/mobile-reports/media/mobile-report-time-chart.png)

1. Перетащите элемент **Диаграмма времени** с вкладки **Макет** в рабочую область конструирования и измените ее размер.

2. По умолчанию это линейчатая диаграмма с накоплением. Это можно изменить в разделе **Визуализация ряда**.

3. Если диаграмме требуются данные, которых еще нет в отчете, откройте вкладку **Данные** и выберите **Добавить данные** для [получения данных из Excel или общего набора данных](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md).

3. В области **Свойства данных** в поле **Основной ряд** выбран вариант **SimulatedTable**. Щелкните стрелку в поле и выберите таблицу.

5. Если для параметра **Структура данных** задано значение **По столбцам** (на вкладке **Макет** в области **Свойства визуальных элементов**), то в области **Свойства данных** можно выбрать несколько столбцов числовых значений.

   Если для параметра **Структура данных** задано значение **По строкам**, то в области **Свойства данных** можно выбрать **Поле имени ряда** и один столбец числовых значений.
   
Дополнительные сведения о [группировании данных по столбцам или строкам](../../reporting-services/mobile-reports/group-data-by-columns-or-rows-in-a-mobile-report-reporting-services.md).
  
## <a name="category-charts"></a>Диаграммы категорий  
  
В отличие от диаграмм времени, на диаграмме категорий группирование выполняется не по полю даты/времени на оси x. Такое группирование, называемое *координатой категорий*, должно находиться в строковом, а не числовом поле.

![mobile-report-category-chart](../../reporting-services/mobile-reports/media/mobile-report-category-chart.png)   

1. Перетащите элемент **Диаграмма категорий** с вкладки **Макет** в рабочую область конструирования и при необходимости [получите для него данные](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md).

2. Откройте вкладку **Данные** и в области **Свойства данных** в разделе **Category Coordinate**(Координата категорий) выберите таблицу и поле для группирования. Это поле будет находиться на оси x итоговой диаграммы.

3. В разделе **Основной ряд**выберите таблицу и числовые поля для статистической обработки по каждой категории. 
  
## <a name="totals-charts"></a>Диаграммы итоговых значений  

![mobile-report-totals-chart](../../reporting-services/mobile-reports/media/mobile-report-totals-chart.png)
  
Диаграмма итоговых значений выполняет две отдельные задачи: 
* На ней представлено не несколько, а всего один ряд, отражающий сумму (итог) определенного основного ряда. 
* Она позволяет группировать данные по столбцам или по строкам. Группирование по столбцам может быть полезно при работе с плоскими данными. При группировании по столбцам доступно только свойство основного ряда, так как столбец категории автоматически определяется по числу полей, выбранных для свойства основного ряда.  

Дополнительные сведения о [группировании данных по столбцам или строкам](../../reporting-services/mobile-reports/group-data-by-columns-or-rows-in-a-mobile-report-reporting-services.md). 
  
## <a name="comparison-charts"></a>Сравнительные диаграммы  
  
Диаграммы времени, категорий и итоговых значений также могут выступать в роли *сравнительных диаграмм*. На сравнительной диаграмме можно указать не только основной ряд, но второй ряд для сравнения. Основной ряд и ряд сравнения могут отображаться тремя различными способами.

![mobile-report-comparison-time-chart](../../reporting-services/mobile-reports/media/mobile-report-comparison-time-chart.png)

1. Перетащите один из элементов **Comparison charts** (Сравнительные диаграммы) (времени, категорий или итоговых значений) с вкладки **Макет** в рабочую область конструирования и при необходимости [получите для него данные](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md).

2. В области **Свойства визуальных элементов** в разделе **Визуализация ряда**выберите одно из следующих значений: 
   * Линейчатые и узкие линейчатые
   * График и линейчатая
   * Линейчатые и ступенчатые с областями 

На сравнительных диаграммах можно использовать одинаковые цвета для основных и сравниваемых значений ряда.

* В области **Свойства визуальных элементов** установите для параметра **Повторное использование цветов в ряде сравнений** значение **Вкл**.

   Если задано значение **Вкл.** , цветовая палитра переводится в исходное состояние между рисованием основных и сравнительных рядов, чтобы связанные значения этих рядов были одинаковыми. 

   Если задано значение **Выкл.** , цветовая палитра продолжает обычный перебор цветов при рисовании основных рядов после рисования сравнительных, благодаря чему исключается ложная цветовая координация между двумя наборами рядов.  
  
## <a name="pie-and-funnel-charts"></a>Круговые и воронкообразные диаграммы  
  
Круговые и воронкообразные диаграммы — самые простые способы визуализации данных. Данные можно структурировать по строкам или столбцам. 
* **Круговые диаграммы** в мобильных отчетах [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] могут иметь вид кругов, колец или колец итогом в центре. Круговые диаграммы хорошо подходят для отображения относительного размера различных частей целого. Слишком большое число сегментов затрудняет их восприятие.
* **Воронкообразные диаграммы** часто используются для отображения этапов процесса, таких как продажи.

![mobile-report-funnel-chart](../../reporting-services/mobile-reports/media/mobile-report-funnel-chart.png)

### <a name="structure-pie-and-funnel-chart-data-by-rows-or-by-columns"></a>Структурирование круговых и воронкообразных диаграмм по строкам или столбцам
1. Перетащите элемент **Круговая диаграмма** или **Воронкообразная диаграмма** с вкладки **Макет** в рабочую область конструирования и при необходимости [получите для него данные](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md).
2. В области **Свойства визуальных элементов** в разделе **Структура данных**выберите одно из значений:
   * **По столбцам**
   * **По строкам**
3. Если выбрано значение **По столбцам**, откройте вкладку **Данные** и в области **Свойства данных** в разделе **Основной ряд**выберите таблицу и все поля, предназначенные для статистической обработки в круговой на воронкообразной диаграмме. Имена полей будут использоваться для маркировки каждой области результирующей диаграммы.

   Если выбрано значение **По строкам**, откройте вкладку **Данные** и в области **Свойства данных** в разделе **Category Column**(Столбец категории) выберите таблицу и столбец со значениями для группирования и меток на круговой диаграмме. В поле колонки основного ряда выберите числовое поле для значений на диаграмме.

Дополнительные сведения о [группировании данных по столбцам или строкам](../../reporting-services/mobile-reports/group-data-by-columns-or-rows-in-a-mobile-report-reporting-services.md). 

## <a name="treemaps"></a>Диаграммы "дерево"  
  
Диаграммы "дерево" отображают значения метрик в виде плиток определенного размера и цвета в пределах прямоугольной сетки. 

![mobile-report-group-treemap](../../reporting-services/mobile-reports/media/mobile-report-group-treemap.png)

1. Перетащите элемент **Диаграмма дерева** с вкладки **Макет** в рабочую область конструирования и при необходимости [получите для него данные](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md).
2.  Откройте вкладку **Данные** и в области **Свойства данных** выполните следующее: 

     * В поле **Представления размера** выберите числовое поле для размера плиток.
     * В поле **Представления цветов** выберите числовое поле для цвета плиток. 
     * **Пользовательское значение центра** (необязательно). **Пользовательское значение центра** можно использовать только при типе визуализации HeatMapWithCustomCenterValue.
     
         Значение центра определяет цвет поля. Чем лучше метрика в сравнении со значением центра, тем она зеленее. Чем хуже метрика, тем она краснее.
     
     * Чтобы отобразить всплывающее окно, когда пользователи выбирают плитку в сетке, выберите поле или поля в разделе **Метки всплывающих окон** [необязательно]. Всплывающие окна диаграммы "дерево" могут отображать как текстовые, так и числовые поля.  

По умолчанию диаграммы "дерево" являются иерархическими, группируя плитки сначала по категориям, а затем по размеру и цвету.
* На вкладке **Данные** в разделе **Группировать** выберите таблицу и поле.

Можно отключить группирование, чтобы упорядочить плитки только по размеру и цвету. 

* Откройте вкладку **Макет** и задайте для параметра **Two-level treemap** (Двухуровневая диаграмма дерева) значение **Выкл**.   

## <a name="waterfall-charts"></a>Каскадные диаграммы

Каскадные диаграммы отображают нарастающий итог по мере добавления или вычитания значений. Это полезно для понимания того, как на исходное значение (например, чистый доход) влияет ряд положительных и отрицательных изменений.

Зеленым цветом обозначается увеличение значения, а красным — уменьшение. Это сделано, чтобы столбцы было легко различать. Столбцы с исходным и финальным значениями часто начинаются от нуля. Промежуточные значения представлены плавающими столбцами. Из-за своего вида такие диаграммы также называются мостом.

### <a name="when-to-use-a-waterfall-chart"></a>Использование каскадных диаграмм

Каскадные диаграммы обычно используются в следующих случаях.
* При изменяющихся значениях временных рядов или разных категорий для аудита основных изменений, влияющих на итоговое значение.
* Для создания графика годовой прибыли организации с отображением разных источников дохода и оценкой общей прибыли (или убытков).
* Для иллюстрации начального и конечного показателей учета сотрудников компании за год.
* Для визуализации количества затрат и прибыли в месяц, а также текущего баланса для вашей учетной записи. 

### <a name="create-a-waterfall-chart"></a>Создание каскадных диаграмм

1. Перетащите элемент **Каскадная диаграмма** с вкладки **Макет** в рабочую область конструирования и при необходимости [получите для него данные](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md).

    ![mobile-report-waterfall-chart-icon](../../reporting-services/mobile-reports/media/mobile-report-waterfall-chart-icon.png)
    
2.  Откройте вкладку **Данные** и в области **Свойства данных** выберите поле категории для элемента **Координаты категории**и числовое поле для элемента **Основной ряд**: 

    ![mobile-report-waterfall-data](../../reporting-services/mobile-reports/media/mobile-report-waterfall-data.png)
    
3. На вкладке **Макет** каскадная диаграмма доступна для предварительного просмотра.

   ![mobile-report-waterfall-chart](../../reporting-services/mobile-reports/media/mobile-report-waterfall-chart.png)
   
   Месяцы с убытками (например, февраль, июнь и июль) выделены красным цветом. 
   Месяцы с прибылью (например, сентябрь, октябрь и ноябрь) выделены зеленым цветом. 

## <a name="see-also"></a>См. также раздел 
* [Карты в мобильных отчетах служб Reporting Services](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)
* [Navigators in Reporting Services mobile reports (Навигаторы в мобильных отчетах служб Reporting Services)](../../reporting-services/mobile-reports/add-navigators-to-reporting-services-mobile-reports.md)
* [Data grids in Reporting Services mobile reports (Сетки данных в мобильных отчетах служб Reporting Services)](../../reporting-services/mobile-reports/add-data-grids-to-mobile-reports-reporting-services.md)
* [Gauges in Reporting Services mobile reports (Датчики в мобильных отчетах служб Reporting Services)](../../reporting-services/mobile-reports/add-gauges-to-mobile-reports-reporting-services.md)
  

