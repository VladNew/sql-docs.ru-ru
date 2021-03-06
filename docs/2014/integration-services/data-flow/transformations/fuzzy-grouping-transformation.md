---
title: Преобразование "Нечеткое группирование" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtrans.f1
helpviewer_keywords:
- cleaning data
- comparing data
- token delimiters [Integration Services]
- temporary indexes [Integration Services]
- Fuzzy Grouping transformation
- temporary tables [Integration Services]
- grouping data
- standardizing data [Integration Services]
- columns [Integration Services], standardizing
- similarity thresholds [Integration Services]
- data cleaning [Integration Services]
- duplicate data [Integration Services]
ms.assetid: e43f17bd-9d13-4a8f-9f29-cce44cac1025
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 41ac7c11824457bd6d93a062344eb3b411c95b3e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62900573"
---
# <a name="fuzzy-grouping-transformation"></a>преобразование «Нечеткое группирование»
  Преобразование «Нечеткое группирование» выполняет задачи очистки данных путем идентификации строк данных, которые похожи на дубликаты, и выбора канонической строки данных для использования в стандартизации данных.  
  
> [!NOTE]  
>  Дополнительные сведения о преобразовании "Нечеткое группирование", в том числе сведения об ограничениях производительности и памяти, см. в техническом документе [Преобразования "Нечеткий уточняющий запрос" и "Нечеткое группирование" в службах SQL Server Integration Services 2005](https://go.microsoft.com/fwlink/?LinkId=96604).  
  
 Преобразованию «Нечеткое группирование» необходимо соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , чтобы создать временные таблицы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , необходимые алгоритму преобразования для выполнения этой работы. Соединение должно преобразоваться в пользователя, имеющего разрешение создавать таблицы в базе данных.  
  
 Чтобы настроить преобразование, необходимо выбрать входные столбцы для поиска дубликатов, а также выбрать тип соответствия — нечеткое или точное — для каждого столбца. Точное совпадение гарантирует, что только строки, имеющие идентичные значения в этом столбце, будут сгруппированы. Точное соответствие может быть применено к столбцам любых типов данных служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , кроме DT_TEXT, DT_NTEXT и DT_IMAGE. Нечеткое соответствие группирует строки, имеющие приблизительно похожие значения. Метод приблизительного совпадения данных основан на указанном пользователем показателе подобия. В нечетком соответствии могут использоваться только столбцы с типами данных DT_WSTR и DT_STR. Дополнительные сведения см. в разделе [Integration Services Data Types](../integration-services-data-types.md).  
  
 Выход преобразования включает все входные столбцы, один или больше столбцов со стандартизованными данными и столбец, содержащий показатель подобия. Показатель является десятичным значением между 0 и 1. Каноническая строка имеет показатель 1. Другие строки в нечеткой группе имеют показатели, отображающие, насколько строка соответствует канонической строке. Чем ближе к 1 коэффициент, тем более строка соответствует канонической. Если в нечеткое группирование включаются строки, которые являются точными дубликатами канонической строки, эти строки также имеют показатель 1. Преобразование не удаляет дублирующиеся строки; оно группирует их, создавая ключ, связывающий каноническую строку со сходной строкой.  
  
 Преобразование формирует одну выходную строку для каждой входной строки со следующими дополнительными столбцами:  
  
-   **_key_in**— столбец, который уникально идентифицирует каждую строку.  
  
-   **_key_out**— столбец, который идентифицирует группу дублирующихся строк. Столбец **_key_out** имеет значение столбца **_key_in** в канонической строке данных. Строки с одинаковым значением в **_key_out** — члены одной и той же группы. Значение **_key_out**для группы соответствует значению **_key_in** в канонической строке данных.  
  
-   **_score**— значение между 0 и 1, отображающее подобие входной строки по отношению к канонической строке.  
  
 Эти названия столбцов заданы по умолчанию. Можно настроить преобразование «Нечеткое группирование» для использования других названий. Выход также обеспечивает показатель подобия для каждого столбца, участвующего в нечетком группировании.  
  
 Преобразование «Нечеткое группирование» предоставляет два параметра для настройки выполняемого группирования: разделители токенов и порог подобия. Преобразование обеспечивает заданный по умолчанию набор разделителей, используемых для разметки данных, но можно добавить новые разделители, которые улучшат разметку данных.  
  
 Порог подобия отображает, как строго преобразование идентифицирует дубликаты. Пороги подобия могут быть установлены на уровнях компонента и столбца. Порог подобия столбца доступен только для столбцов, участвующих в нечетком соответствии. Диапазон подобия охватывает значения от 0 до 1. Чем ближе порог к 1, тем более сходными должны быть строки и столбцы, чтобы называться дубликатами. Порог подобия среди строк и столбцов указывается установкой свойства MinSimilarity на уровнях компонента и столбца. Для соответствия подобию, которое указано на уровне компонента, все строки должны иметь подобие во всех столбцах, которое больше порога подобия, определенного на уровне компонента, или равно ему.  
  
 Преобразование "Нечеткое группирование" вычисляет внутреннюю меру подобия и не группирует строки с меньшим значением подобия, чем определено в MinSimilarity.  
  
 Чтобы определить порог подобия, который будет работать для реальных данных, возможно, придется применить преобразование «Нечеткое группирование» несколько раз, используя различные минимальные пороги подобия. Во время выполнения столбцы показателя на выходе преобразования содержат показатели подобия для каждой строки в группе. Можно использовать эти значения, чтобы определить порог подобия, который соответствует этим данным. Если необходимо увеличить подобие, нужно присвоить свойству MinSimilarity значение больше, чем значение в столбцах показателей.  
  
 Можно настроить группирование, выполняемое преобразованием, устанавливая свойства столбцов на входе преобразования «Нечеткое группирование». Например, свойство FuzzyComparisonFlags определяет, как преобразование сравнивает строковые данные в столбце, а свойство ExactFuzzy определяет, выполняет ли преобразование нечеткое или точное соответствие.  
  
 Объем памяти, используемой преобразованием "Нечеткое группирование", можно задать в пользовательском свойстве MaxMemoryUsage. Можно указать число мегабайтов (МБ) или значение 0, которое позволяет преобразованию использовать динамический объем памяти в зависимости от своих потребностей и наличия доступной физической памяти. Пользовательское свойство MaxMemoryUsage можно обновить с помощью выражения свойства при загрузке пакета. Дополнительные сведения см. в разделах [Выражения служб Integration Services (SSIS)](../../expressions/integration-services-ssis-expressions.md), [Использование выражений свойств в пакетах](../../expressions/use-property-expressions-in-packages.md) и [Пользовательские свойства преобразований](transformation-custom-properties.md).  
  
 Это преобразование имеет один вход и один выход. Вывод ошибок не поддерживается.  
  
## <a name="row-comparison"></a>Сравнение строк  
 При настройке преобразования «Нечеткое группирование» можно определить алгоритм сравнения, который преобразование применяет для сравнения строк на входе преобразования. Если для `true`Свойства Exhaustive задано значение, то преобразование сравнивает каждую строку во входных данных с каждой другой строкой во входных данных. Этот алгоритм сравнения может выдать более точные результаты, но это может сделаеть работу преобразования более медленной при большом количестве строк на входе. Чтобы избежать проблем с производительностью, рекомендуется задать для свойства Exhaustive значение `true` только во время разработки пакета.  
  
## <a name="temporary-tables-and-indexes"></a>Временные таблицы и индексы  
 Во время выполнения преобразование «Нечеткое группирование» создает временные объекты, такие как таблицы и индексы, потенциально существенного размера в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , к которой преобразование подключается. Размер таблиц и индексов пропорционален количеству строк на входе преобразования и количеству разделителей токенов, созданных преобразованием «Нечеткое группирование».  
  
 Преобразование также делает запросы к временным таблицам. Поэтому необходимо рассмотреть подключение преобразования "Нечеткое группирование" к непроизводственному экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], особенно если рабочий сервер имеет ограничения по доступному месту на диске.  
  
 Производительность этого преобразования может повышаться путем размещения используемых им таблиц и индексов на локальном компьютере.  
  
## <a name="configuration-of-the-fuzzy-grouping-transformation"></a>Настройка преобразования «Нечеткое группирование»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно установить в диалоговом окне **Редактор преобразования «Нечеткое группирование»** , см. в следующих разделах:  
  
-   [Редактор преобразования "Нечеткое группирование" (вкладка "Диспетчер соединений")](../../fuzzy-grouping-transformation-editor-connection-manager-tab.md)  
  
-   [Редактор преобразования "Нечеткое группирование" (вкладка "Столбцы")](../../fuzzy-grouping-transformation-editor-columns-tab.md)  
  
-   [Редактор преобразования "Нечеткое группирование" (вкладка "Дополнительно")](../../fuzzy-grouping-transformation-editor-advanced-tab.md)  
  
 Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](../../common-properties.md)  
  
-   [Transformation Custom Properties](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения об установке свойств этой задачи см. в следующих разделах:  
  
-   [Определение подобных строк данных с помощью преобразования «Нечеткое группирование»](fuzzy-grouping-transformation.md)  
  
-   [Установление свойств компонента потока данных](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a>См. также  
 [Преобразование "Нечеткий уточняющий запрос"](lookup-transformation.md)   
 [Преобразования служб Integration Services](integration-services-transformations.md)  
  
  
