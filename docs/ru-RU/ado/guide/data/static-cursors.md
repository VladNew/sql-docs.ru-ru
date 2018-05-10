---
title: Статические курсоры | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], static
- static cursors [ADO]
ms.assetid: cce93ace-c4ed-4c6c-940c-28a50ff2fd12
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 04ef88ca992498194feb4772045c6ada60fc1ea5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="static-cursors"></a>Статические курсоры
Статический курсор всегда отображает результирующий набор, в котором он был при первом открытии курсора. В зависимости от реализации, статические курсоры имеют только для чтения или чтения и записи и предоставить прямой и обратной прокрутки. Статический курсор обычно не обнаруживает изменений в членство, порядок и значения из результирующего набора, после открытия курсора. Статические курсоры могут обнаруживать свои собственные обновления, удаления и вставки, несмотря на то, что они не требуются для этого.  
  
 Статические курсоры никогда не обнаружить другие обновляет, удаляет и вставляет. Например предположим, статический курсор извлекает строки и другое приложение, а затем обновляет этой строки. Если приложение refetches строку из статического курсора, значения, которые видит не изменяются, независимо от изменений, внесенных в других приложениях. Поддерживаются все типы прокрутки, но поставщики могут или не поддерживает закладки.  
  
 Если приложения не требуется для обнаружения изменения данных и требуется прокрутка, статический курсор является лучшим вариантом. Используйте **adOpenStatic CursorTypeEnum** для указания, что вы хотите использовать статический курсор в ADO.  
  
## <a name="see-also"></a>См. также  
 [Однопроходные курсоры](../../../ado/guide/data/forward-only-cursors.md)   
 [Управляемые набором ключей курсоры](../../../ado/guide/data/keyset-cursors.md)   
 [Динамические курсоры](../../../ado/guide/data/dynamic-cursors.md)