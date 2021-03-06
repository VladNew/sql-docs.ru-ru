---
title: Объект CubeDef (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CubeDef
helpviewer_keywords:
- CubeDef object [ADO MD]
ms.assetid: feb2581c-fc41-471c-bb69-29f8a55fda70
author: rothja
ms.author: jroth
ms.openlocfilehash: 25dd4d6a9c8a5518c8c2b637af63b39e7b992557
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764355"
---
# <a name="cubedef-object-ado-md"></a>Объект CubeDef (многомерные объекты ADO)
Представляет куб из многомерной схемы, содержащий набор связанных измерений.  
  
## <a name="remarks"></a>Примечания  
 С помощью коллекций и свойств объекта **CubeDef** можно выполнять следующие действия.  
  
-   Найдите **CubeDef** с помощью свойства [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) .  
  
-   Возвращает строку, описывающую куб со свойством [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) .  
  
-   Возвращает измерения, которые составляют куб, с помощью коллекции [измерений](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md) .  
  
-   Получите дополнительные сведения о **CubeDef** со стандартной коллекцией [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) ADO.  
  
 Коллекция **Properties** содержит свойства, предоставляемые поставщиком. В следующей таблице перечислены свойства, которые могут быть доступны. Фактический список свойств может отличаться в зависимости от реализации поставщика. Более полный список доступных свойств см. в документации поставщика.  
  
|name|Описание|  
|----------|-----------------|  
|CatalogName|Имя каталога, которому принадлежит куб.|  
|CreatedOn|Дата и время создания куба.|  
|кубегуид|GUID Куба.|  
|CubeName|Имя куба.|  
|кубетипе|Тип куба.|  
|датаупдатедби|Идентификатор пользователя, выполняющего Последнее обновление данных.|  
|Описание|Понятное описание Куба.|  
|LastSchemaUpdate|Дата и время последнего обновления схемы.|  
|SchemaName|Имя схемы, к которой принадлежит куб.|  
|счемаупдатедби|Идентификатор пользователя, выполняющего Последнее обновление схемы.|  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/cubedef-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Объект каталога (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)   
 [Коллекция Кубедефс (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)   
 [Коллекция Dimensions (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
