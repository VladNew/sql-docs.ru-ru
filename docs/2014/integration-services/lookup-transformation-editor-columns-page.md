---
title: Редактор преобразования "Уточняющий запрос" (страница "столбцы") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.columns.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: 690ffef5-fd59-4e95-a27d-4fcf0d6b1c0b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e1a32dcbcee6704cb4fecef7b58cbff8354b910a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66057899"
---
# <a name="lookup-transformation-editor-columns-page"></a>Редактор преобразования «Уточняющий запрос» (страница «Столбцы»)
  Используйте страницу **Столбцы** диалогового окна **Редактор преобразования «Уточняющий запрос»** , чтобы указать соединение между исходной и ссылочной таблицами и выбрать уточняющие столбцы из ссылочной таблицы.  
  
 Дополнительные сведения о преобразовании «Уточняющий запрос» см. в разделе [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Доступные входные столбцы**  
 Просмотрите список доступных входных столбцов. Входные столбцы — это столбцы в потоке данных из подключенного источника. Входной и уточняющий столбец должны иметь одинаковый тип данных.  
  
 Чтобы сопоставить доступные входные столбцы с уточняющими столбцами, воспользуйтесь операцией перетаскивания.  
  
 Также можно сопоставить входные и уточняющие столбцы с помощью клавиатуры, выделив цветом столбец в таблице **Доступные входные столбцы** , нажав клавишу «Приложение» и выбрав пункт **Изменить сопоставления**.  
  
 **Доступные уточняющие столбцы**  
 Просмотр списка уточняющих столбцов. Уточняющие столбцы представляют собой столбцы в ссылочной таблице, в которых должен производиться поиск значений, совпадающих с входными столбцами.  
  
 Чтобы сопоставить доступные уточняющие столбцы с входными столбцами, воспользуйтесь операцией перетаскивания.  
  
 С помощью флажков выберите уточняющие столбцы в ссылочной таблице, по которым будет выполняться уточняющий запрос.  
  
 Также можно сопоставить входные и уточняющие столбцы с помощью клавиатуры, выделив цветом столбец в таблице **Доступные уточняющие столбцы** , нажав клавишу «Приложение» и выбрав пункт **Изменить сопоставления**.  
  
 **Уточняющий столбец**  
 Просмотр выбранных уточняющих столбцов. Выбор отражается установкой флажков в таблице **Доступные уточняющие столбцы** .  
  
 **Операция уточняющего запроса**  
 Выберите из списка операцию уточняющего запроса, которую нужно выполнить для уточняющего столбца.  
  
 **Псевдоним вывода**  
 Введите псевдоним выхода для каждого уточняющего столбца. По умолчанию используется имя уточняющего столбца, однако можно выбрать любое уникальное описательное имя.  
  
## <a name="see-also"></a>См. также  
 [Редактор преобразования "Уточняющий запрос" &#40;общие&#41;страницы](general-page-of-integration-services-designers-options.md)   
 [Редактор преобразования "Уточняющий запрос" &#40;страница подключения&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [Редактор преобразования "Уточняющий запрос" &#40;страница "Дополнительно"&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)   
 [Редактор преобразования "Уточняющий запрос" &#40;страница "вывод ошибок"&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [преобразование «Нечеткий уточняющий запрос»](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
