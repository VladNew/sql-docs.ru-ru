---
title: Выражения (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 76d3ac86-650c-46fe-8086-8b3edcea3882
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 669b5d6a8514dce55a2f5fadc0d1c239b5b3ab61
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37268590"
---
# <a name="expressions-report-builder-and-ssrs"></a>Выражения (построитель отчетов и службы SSRS)
  Выражения часто используются в отчетах для получения, вычисления, отображения, группирования, сортировки, параметризации и форматирования данных. Многие свойства элементов отчета могут быть заданы в виде выражений. С помощью выражений можно управлять содержимым, внешним видом и интерактивными возможностями отчета. Выражения записываются на [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], сохраняются в определении отчета и вычисляются обработчиком отчетов при запуске отчета.  
  
 В отличие от приложений вроде [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office Excel, где можно работать с данными напрямую на листе, в отчете, при работе с выражениями, которые являются заполнителями для данных. Чтобы просмотреть фактические данные из вычисленных выражений, необходимо просмотреть отчет. При запуске отчета обработчик отчета вычисляет каждое выражение, объединяя данные отчета и элементы макета отчета, такие как таблицы и диаграммы.  
  
 При конструировании отчета многие выражения для элементов отчета будут уже заданы. Например, если перетащить поле с панели данных в ячейку таблицы в области конструктора отчета, в качестве значения текстового поля будет задано простое выражение для поля. На следующем рисунке область данных отчета отображает такие поля наборов данных, как ID, Name, SalesTerritory, Code и Sales. В таблицу добавлено три поля: [Name], [Code] и [Sales]. Обозначение [Name] в области конструктора представляет базовое выражение `=Fields!Name.Value`.  
  
 ![rs_DataDesignandPreview](../media/rs-datadesignandpreview.gif "rs_DataDesignandPreview")  
  
 При предварительном просмотре отчета обработчик отчетов комбинирует табличную область данных с фактическими данными из подключения к данным и отображает строку в таблице для каждой строки в результирующем наборе.  
  
 Чтобы ввести выражения вручную, выберите элемент в области конструктора и с помощью контекстных меню и диалоговых окон задайте свойства этого элемента. Если присутствует кнопка ***(fx)*** или значение `<Expression>` в раскрывающемся списке, то для свойства можно задать выражение. Дополнительные сведения см. в разделе [Добавление выражения (построитель отчетов и службы SSRS)](add-an-expression-report-builder-and-ssrs.md).  
  
 Дополнительные сведения и примеры см. в следующих разделах:  
  
-   [Использование выражений в отчетах &#40;построитель отчетов и службы SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)  
  
-   [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)  
  
-   [Примеры уравнений фильтра &#40;построитель отчетов и службы SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)  
  
-   [Примеры выражений групп &#40;построитель отчетов и службы SSRS&#41;](group-expression-examples-report-builder-and-ssrs.md)  
  
-   [Учебники по &#40;построитель отчетов&#41;](../report-builder-tutorials.md)  
  
-   [Учебники по службам Reporting Services (SSRS)](../reporting-services-tutorials-ssrs.md)  
  
-   [Образцы отчетов (построитель отчетов и службы SSRS)](http://go.microsoft.com/fwlink/?LinkId=198283)  
  
 Для разработки сложных выражений или выражений, использующих пользовательский код или пользовательские сборки, рекомендуется использовать конструктор отчетов среды [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения см. в разделе [Пользовательский код и ссылки на сборки в выражениях в конструкторе отчетов (службы SSRS)](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="Types"></a> Основные сведения о простых и сложных выражениях  
 Выражения начинаются со знака равенства (=) и создаются на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]. Они могут включать сочетание констант, операторов и ссылок на встроенные значения (поля, коллекции и функции), а также на внешний и пользовательский код.  
  
 Выражения можно использовать, чтобы задавать значения различных свойств элементов отчета. Самыми распространенными свойствами являются значения для текстовых полей и текста заполнителя. Как правило, если текстовое поле содержит только одно выражение, это выражение является значением для свойства текстового поля. Если текстовое поле содержит несколько выражений, каждое выражение является значением текста заполнителя в текстовом поле.  
  
 По умолчанию выражения отображаются в области конструктора отчетов в виде *простых* или *сложных выражений*.  
  
-   **Простое.** Простое выражение содержит ссылку на единственный элемент во встроенной коллекции, например поле набора данных, параметр или встроенное поле. В области конструктора простое выражение отображается в скобках. Например, `[FieldName]` соответствует базовому выражению `=Fields!FieldName.Value`. Простые выражения создаются автоматически по мере создания макета отчета и перетаскивания элементов из панели данных отчета на панель конструктора. Дополнительные сведения о символах, представляющих различные встроенные коллекции, см. в разделе [Основные сведения о символах префиксов в простых выражениях](#DisplayText).  
  
-   **Сложные.** Сложные выражения содержат ссылки на несколько встроенных ссылок, операторов и вызовов функций. Сложное выражение отображается как <\<Выраж>>, если значение выражения включает больше, чем простую ссылку. Для просмотра выражения наведите на него курсор и воспользуйтесь подсказкой. Чтобы изменить выражение, откройте его в диалоговом окне **Выражение** .  
  
 На следующем рисунке показаны типичные простые и сложные выражения как для текстовых полей, так и для текста заполнителя.  
  
 ![rs_ExpressionDefaultFormat](../media/rs-expressiondefaultformat.gif "rs_ExpressionDefaultFormat")  
  
 Чтобы вместо текста выражений отобразить образцы значений, примените форматирование к текстовому полю или к тексту заполнителя. На следующем рисунке показана область конструктора отчетов с отображением образцов значений.  
  
 ![rs_ExpressionSampleValuesFormat](../media/rs-expressionsamplevaluesformat.gif "rs_ExpressionSampleValuesFormat")  
  
 Дополнительные сведения см. в разделе [Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md).  
  

  
### <a name="report-model-formulas"></a>Формулы моделей отчетов  
 При создании запроса для получения набора данных, в котором в качестве источника данных используется модель отчета, можно создать *формулы*. Формулы — это вычисления, производимые над значениями в отчете, основанные на данных модели отчета.  
  
 Дополнительные сведения см. в разделе [Формулы в запросах модели отчета (построитель отчетов и службы SSRS)](formulas-in-report-model-queries-report-builder-and-ssrs.md).  
  

  

  
##  <a name="DisplayText"></a> Основные сведения о символах префиксов в простых выражениях  
 В простых выражениях используются символы, чтобы указать, ссылается ли оно на поле, параметр, встроенную коллекцию или коллекцию ReportItems. В следующей таблице показаны примеры отображаемого текста и текста выражения.  
  
|Элемент|Пример отображаемого текста|Пример текста выражения|  
|----------|--------------------------|-----------------------------|  
|Поля набора данных|`[Sales]`<br /><br /> `[SUM(Sales)]`<br /><br /> `[FIRST(Store)]`|`=Fields!Sales.Value`<br /><br /> `=Sum(Fields!Sales.Value)`<br /><br /> `=First(Fields!Store.Value)`|  
|Параметры отчета|`[@Param]`<br /><br /> `[@Param.Label]`|`=Parameters!Param.Value`<br /><br /> `=Parameters!Param.Label`|  
|Встроенные поля|`[&ReportName]`|`=Globals!ReportName.Value`|  
|Литеральные символы для отображения текста|`\[Sales\]`|`[Sales]`|  
  

  
##  <a name="References"></a> Написание сложных выражений  
 Выражения могут включать ссылки на функции, операторы, константы, поля, параметры и элементы из встроенных коллекций, а также ссылки на внедренный пользовательский код или пользовательские сборки.  
  
> [!NOTE]  
>  Для разработки сложных выражений или выражений, использующих пользовательский код или пользовательские сборки, мы рекомендуем использовать конструктор отчетов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения см. в разделе [Пользовательский код и ссылки на сборки в выражениях в конструкторе отчетов (службы SSRS)](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
 В следующей таблице перечислены типы ссылок, которые можно включать в выражение.  
  
|Ссылки|Описание|Пример|  
|----------------|-----------------|-------------|  
|[Константы](expressions-report-builder-and-ssrs.md)|Описывает константы для свойств, требующих постоянных значений, таких как цвет шрифта; к этим константам можно получить доступ в диалоговом режиме.|`="Blue"`|  
|[Операторы](operators-in-expressions-report-builder-and-ssrs.md)|Описывает операторы, которые можно использовать для объединения ссылок в выражении. Например `&` оператор используется для объединения строк.|`="The report ran at: " & Globals!ExecutionTime & "."`|  
|[Встроенные коллекции](built-in-collections-in-expressions-report-builder.md)|Описывает встроенные коллекции, которые можно включить в выражение, например `Fields`, `Parameters`и `Variables`.|`=Fields!Sales.Value`<br /><br /> `=Parameters!Store.Value`<br /><br /> `=Variables!MyCalculation.Value`|  
|[Встроенные функции отчета и агрегатные функции](report-builder-functions-aggregate-functions-reference.md)|Описывает встроенные функции, такие как `Sum` и `Previous`, к которым можно получить доступ из выражения.|`=Previous(Sum(Fields!Sales.Value))`|  
|[Пользовательский код и ссылки на сборки в выражениях в конструкторе отчетов &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)|Описывает, как получить доступ к встроенным классам среды CLR из пространства имен <xref:System.Math> и <xref:System.Convert>, другим классам среды CLR, функциям библиотеки времени выполнения [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] или методам из внешней сборки.<br /><br /> Описывает, как получить доступ к пользовательскому коду, внедренному в отчет или скомпилированному и установленному в виде пользовательской сборки на клиент отчета и сервер отчетов.|`=Sum(Fields!Sales.Value)`<br /><br /> `=CDate(Fields!SalesDate.Value)`<br /><br /> `=DateAdd("d",3,Fields!BirthDate.Value)`<br /><br /> `=Code.ToUSD(Fields!StandardCost.Value)`|  
  

  
##  <a name="Valid"></a> Проверка выражений  
 При создании выражения для определенного свойства элемента отчета типы ссылок, которые могут быть включены в выражение, зависят от значений, которые может принимать свойство элемента отчета, и от области, в которой это свойство вычисляется. Например:  
  
-   По умолчанию выражение [Sum] вычисляет сумму данных, находящихся в области в момент вычисления выражения. Для табличной ячейки область зависит от членства групп строк и столбцов. Дополнительные сведения см. в разделе [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
-   Применительно к значению свойства Font это значение должно представлять название шрифта.  
  
-   Синтаксис выражения проверяется во время разработки. При публикации отчета происходит проверка области выражения. При проверке, зависящей от фактических данных, ошибки могут быть выявлены только в ходе выполнения. Некоторые из этих выражений выдают #Error в качестве сообщения об ошибке в подготовленном отчете. Чтобы определить причины для этого типа ошибки, необходимо воспользоваться конструктором отчетов в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. В конструкторе отчетов отображается окно вывода, содержащее дополнительные сведения об этих ошибках.  
  
 Дополнительные сведения см. в разделе [Справочник выражений (построитель отчетов и службы SSRS)](expression-reference-report-builder-and-ssrs.md).  
  

  
##  <a name="Section"></a> в этом разделе  
 [Добавление выражения (построитель отчетов и службы SSRS)](add-an-expression-report-builder-and-ssrs.md)  
  
 [Использование выражений в отчетах &#40;построитель отчетов и службы SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)  
  
 [Область выражения для суммирования, агрегатов и встроенных коллекций &#40;построитель отчетов и службы SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
 [Справочник по выражениям &#40;построитель отчетов и службы SSRS&#41;](expression-reference-report-builder-and-ssrs.md)  
  

  
## <a name="see-also"></a>См. также  
 [Диалоговое окно выражение](../expression-dialog-box.md)   
 [Диалоговое окно "Выражение" (построитель отчетов)](../expression-dialog-box-report-builder.md)  
  
  