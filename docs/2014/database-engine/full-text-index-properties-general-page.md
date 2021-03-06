---
title: Свойства полнотекстового индекса (страница «Общие») | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.general.f1
ms.assetid: f4dff61c-8c2f-4ff9-abe4-70a34421448f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 187366d9f289804942ba6e7d331a47bfaae68232
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000944"
---
# <a name="full-text-index-properties-general-page"></a>Свойства полнотекстового индекса (страница «Общие»)
  **Просмотр или изменение изменяемых свойств полнотекстового индекса**  
  
-   [Управление полнотекстовыми индексами](../relational-databases/indexes/indexes.md)  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Полнотекстовый каталог**  
 Отображает имя полнотекстового каталога, с которым связан полнотекстовый индекс.  
  
 **База данных**  
 Отображает имя базы данных, в которой находится полнотекстовый индекс.  
  
 **Таблица**  
 Позволяет отобразить имя таблицы, для которой определен полнотекстовый индекс.  
  
 **Полнотекстовый ключ индекса**  
 Отображает имя полнотекстового ключа индекса, который является уникальным индексом для отдельного столбца таблицы.  
  
 **Состояние табличных заполнений полнотекстовых индексов**  
 Отображает состояние заполнения полнотекстовой индексированной таблицы.  
  
 Возможны следующие значения:  
  
 0 = Бездействует.  
  
 1 = Производится полное заполнение.  
  
 2 = Производится добавочное заполнение.  
  
 3 = Выполняется распространение отслеженных изменений.  
  
 4 = Выполняется индексирование фонового обновления (например, автоматическое отслеживание изменений).  
  
 5 = Полнотекстовое индексирование приостановлено, или не хватает ресурсов на его выполнение.  
  
 **Активный полнотекстовый индекс**  
 Указывает, содержит ли таблица активный полнотекстовый индекс.  
  
 1 = True  
  
 0 = False.  
  
 **Файловая группа полнотекстового индекса**  
 Файловая группа, к которой принадлежит полнотекстовый индекс.  
  
 **Список стоп-слов полнотекстового индекса**.  
 Указывает список стоп-слов, который в данный момент связан с полнотекстовым индексом. Список стоп-слов содержит [стоп-слова](../relational-databases/search/full-text-search.md). Связанный с полнотекстовым индексом список стоп-слов (если он существует) применяется к полнотекстовым запросам к данному индексу. Список стоп-слов можно удалить из индекса, выбрав ** \< выключить>** из списка, или можно выбрать другой список стоп-слов. ** \< Системный>** указывает на системный список стоп-слов.  
  
 **Создание списка стоп-слов**  
  
-   [Настройка и управление стоп-словами и списками стоп-слов для полнотекстового поиска](../relational-databases/search/full-text-search.md)  
  
 **Поиск в списке свойств**.  
 Список свойств поиска, в настоящее время связанный с полнотекстовым индексом, если он имеется. Список свойств поиска задает набор свойств документа, которые включаются в связанный полнотекстовый индекс при его заполнении. Дополнительные сведения см. в статье [Поиск свойств документа с использованием списков свойств поиска](../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
 ** \< Off>** указывает, что в настоящее время отсутствует список свойств поиска, связанный с индексом. Вы можете удалить текущий список свойств поиска из индекса, выбрав ** \< Off>** из списка или выбрав другой список свойств поиска из списка. Здесь указаны только списки поиска свойств в текущей базе данных.  
  
> [!NOTE]  
>  Один список свойств поиска может быть связан с несколькими полнотекстовыми индексами в той же базе данных.  
  
 **Создание списка свойств поиска**  
  
-   [Поиск свойств документа с помощью списков свойств поиска](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
 **Счетчик табличных полнотекстовых элементов**  
 Указывает число строк, которые были успешно проиндексированы.  
  
 Это свойство соответствует свойству `TableFulltextItemCount`, возвращаемому функцией OBJECTPROPERTYEX [!INCLUDE[tsql](../includes/tsql-md.md)].  
  
 **Обработанные табличные полнотекстовые документы**  
 Отображает число строк, обработанных с начала полнотекстового индексирования. В таблице, которая индексируется для полнотекстового поиска, все столбцы одной строки рассматриваются как часть единого индексируемого документа. Удаленные строки не считаются.  
  
|||  
|-|-|  
|0|Указывает, что полнотекстовое индексирование завершено и активное заполнение отсутствует.|  
|> 0|Для активного заполнения указывает число документов, обработанных операциями вставки или обновления со времени заполнения, включения отслеживания изменений при фоновом заполнении индекса (такого как автоматическое отслеживание изменений), изменения схемы полнотекстового индекса, повторного построения полнотекстового каталога, перезапуска экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]и т. д.|  
  
 **Ожидающие табличные полнотекстовые изменения**  
 Количество ожидающих отслеженных изменений к обработке.  
  
 0 = Отслеживание изменений не включено.  
  
 NULL = Таблица не содержит полнотекстового индекса.  
  
 **Счетчик отказов табличных полнотекстовых элементов**  
 Число строк, не проиндексированных для полнотекстового поиска.  
  
 0 = Заполнение завершено.  
  
 \>0 = одно из следующих:  
  
-   Количество документов, не индексированных с начала заполнения отслеженных изменений полного, добавочного или ручного обновления.  
  
-   Для отслеживания изменений с индексацией фонового обновления — число строк, которые не проиндексированы с начала или перезапуска заполнения. Это может быть вызвано изменением схемы, перестройкой каталога, перезапуском сервера и т. д.  
  
 **Полнотекстовое индексирование включено**.  
 Указывает, включено ли полнотекстовое индексирование.  
  
|||  
|-|-|  
|**Условия**|Активировано|  
|**IsFalse**|Выключено|  
  
 **Отслеживание изменений**  
 Указывает, включено ли для таблицы полнотекстовое отслеживание изменений и, если да, какого типа. Полнотекстовое отслеживание изменений поддерживает список всех измененных строк таблицы или индексированного представления, подлежащих полнотекстовому индексированию. Эти изменения распространяются на полнотекстовый индекс.  
  
 Параметр **Отслеживание изменений** имеет следующие значения.  
  
|||  
|-|-|  
|**Выключено**|Изменения базовых данных не отражаются в полнотекстовом индексе.|  
|**Вручную**|Изменения базовых данных не вызывают автоматического обновления полнотекстового индекса. При этом изменения базовых данных сохраняются, и их можно распространить на полнотекстовый индекс по расписанию с помощью агента SQL Server или вручную.|  
|**Automatic** (Автоматический)|Изменения базовых данных в базовой таблице не вызывают автоматического обновления полнотекстового индекса.|  
  
 **Повторить заполнение индекса**  
 Щелкните для запуска заполнения полнотекстового индекса при закрытии диалогового окна. Выберите один из следующих типов заполнения.  
  
|||  
|-|-|  
|**Полное**|Во время полного заполнения таблицы записи индекса создаются для всех строк.|  
|**Присоединен**|Операция добавочного заполнения обновляет полнотекстовый индекс для строк, добавленных, удаленных или измененных после или во время последнего заполнения. Для выполнения добавочного заполнения базовая таблица должна включать столбец с типом данных `timestamp`.|  
|**Обновление**|Полнотекстовый индекс обновляется при изменении данных в базовой таблице.|  
  
## <a name="see-also"></a>См. также  
 [Приступая к работе с компонентом Full-Text Search](../relational-databases/search/get-started-with-full-text-search.md)  
  
  
