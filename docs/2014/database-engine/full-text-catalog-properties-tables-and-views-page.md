---
title: Свойства полнотекстового каталога (страница представлений и таблиц) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.tablesviews.f1
ms.assetid: 2d45fcd2-0f0f-4167-9027-316d6696c106
caps.latest.revision: 25
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: e0e73607bf54d066c0328ae45785151ceaa2cca1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37298920"
---
# <a name="full-text-catalog-properties-tables-and-views-page"></a>Свойства полнотекстового каталога (страница "Таблицы и представления")
  Используйте это диалоговое окно для просмотра и редактирования таблиц и представлений, назначенных полнотекстовому каталогу.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Все объекты соответствующих таблиц и представлений в этой базе данных**  
 Перечисляет таблицы и представления, для которых задан уникальный индекс, но они еще не входят в полнотекстовый каталог. Чтобы выбрать таблицу или представление и назначить их каталогу, выберите элементы в поле со списком и нажмите кнопку «->».  
  
 **Объекты таблиц и представлений, назначенных каталогу**  
 Перечисляет таблицы и представления, назначенные полнотекстовому каталогу  
  
## <a name="selected-object-properties"></a>Свойства выбранного объекта  
 **Свойства выбранного объекта**  
 Отображает свойства выбранного объекта в поле со списком объектов, назначенных каталогу.  
  
 **Уникальный индекс**  
 Перечисляет доступные уникальные индексы таблицы или представления.  
  
 **Таблица является полнотекстовый поиск**  
 Установите этот флажок, чтобы включить полнотекстовый индекс для таблицы. Снимите этот флажок, чтобы отключить полнотекстовый индекс.  
  
## <a name="eligible-columns-grid"></a>Сетка подходящих столбцов  
  
|||  
|-|-|  
|**Доступные столбцы**|Отображает все столбцы, поддерживающие полнотекстовый индекс. Установите этот флажок, чтобы добавить столбец в полнотекстовый индекс.|  
|**Язык для разбиения по словам**|Отображает язык средства разбиения по словам.|  
|**Столбец типа данных**|Содержит имя столбца в таблице, который хранит тип документа столбца, перечисленного в списке **доступные столбцы** Если столбец является `varbinary(max)` или `image` столбца.|  
|**Статистическая семантика**|Укажите, следует ли включить статистическое семантическое индексирование для выбранного столбца. Дополнительные сведения см. в разделе [Семантический поиск (SQL Server)](../relational-databases/search/semantic-search-sql-server.md).<br /><br /> Если **Язык** выбран до выбора режима **Статистическая семантика**и выбранный язык не имеет связанной семантической модели языка, флажок **Статистическая семантика** будет недоступным. Если режим **Статистическая семантика** выбран до выбора **Языка**, в раскрывающемся поле со списком будут доступны только языки, имеющие семантическую модель языка.|  
  
## <a name="track-changes"></a>Отслеживать изменения  
  
|||  
|-|-|  
|**Автоматически**|Полнотекстовый индекс обновляется автоматически при редактировании, добавлении или удалении данных в базовой таблице.|  
|**Вручную**|Когда данные изменяются, добавлена или удалена в индексированных данных, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] отслеживает изменения. Если активировано отслеживание изменений по параметру **Вручную** , индекс автоматически не обновляется этими изменениями. Вместо этого администратор может применить изменения вручную с помощью [ALTER FULLTEXT INDEX... START UPDATE POPULATION](/sql/t-sql/statements/alter-fulltext-index-transact-sql) инструкции.|  
|**Не отслеживать изменения**|Если этот параметр включен, изменения в индексированные данные каталога не регистрируются. Администратор должен построить индекс с помощью инструкции ALTER FULLTEXT INDEX с параметром FULL POPULATION или INCREMENTAL POPULATION.|  
  
## <a name="see-also"></a>См. также  
 [CREATE FULLTEXT CATALOG (Transact-SQL)](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)   
 [ALTER FULLTEXT CATALOG (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql)   
 [Заполнение полнотекстовых индексов](../relational-databases/indexes/indexes.md)  
  
  