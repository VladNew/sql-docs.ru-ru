---
title: Создание группы атрибутов (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], creating
- creating attribute groups [Master Data Services]
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: c832fe601eb7151e438d7f93c3e39e9b249ea246
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "65483324"
---
# <a name="create-an-attribute-group-master-data-services"></a>Создание группы атрибутов (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]группы атрибутов создаются, когда нужно отобразить атрибуты на отдельных вкладках сетки **обозревателя** .  
  
> [!NOTE]  
>  При создании группы атрибутов она автоматически скрыта от всех пользователей, кроме того, кто ее создал. Дополнительные сведения о назначении видимости группе см. в разделе [Превращение группы атрибутов в видимую для пользователей (службы Master Data Services)](make-an-attribute-group-visible-to-users-master-data-services.md).  
  
## <a name="prerequisites"></a>Предварительные условия  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** .  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
-   Требуется хотя бы один атрибут. Дополнительные сведения см. в статье [Создание текстового атрибута (службы Master Data Services)](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).  
  
### <a name="to-create-an-attribute-group"></a>Создание группы атрибутов  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **представление модели** в строке меню наведите указатель мыши на пункт **Управление** и щелкните **группы атрибутов**.  
  
3.  Выберите модель из списка **Модель** .  
  
4.  Выберите сущность из списка **Сущность** .  
  
5.  Выберите **Конечные группы**, **Консолидированные группы**или **Группы коллекций** , чтобы создать группу атрибутов для конечных элементов, объединенных элементов или коллекций соответственно.  
  
6.  Нажмите кнопку **Добавить группу атрибутов**.  
  
7.  В поле **имя конечной группы** введите имя группы. Это имя отображается на вкладке в **обозревателе**.  
  
    > [!NOTE]  
    >  Если в шаге 5 были выбраны **консолидированные группы** или **группы коллекций** , это поле будет **объединено в группу** или имя **группы коллекций**соответственно.  
  
8.  Нажмите кнопку **Сохранить группу**.  
  
9. Разверните папку группы.  
  
10. Нажмите **Атрибуты**.  
  
11. Нажмите кнопку **изменить выбранный элемент**.  
  
12. Щелкните атрибуты в поле **доступно** и щелкните стрелку **Добавить** . Чтобы добавить все, щелкните стрелку **Добавить все** .  
  
13. При необходимости можно нажать кнопки со стрелками **вверх** и **вниз** , чтобы изменить порядок атрибутов слева направо.  
  
14. Нажмите кнопку **Сохранить**.  
  
## <a name="next-steps"></a>Дальнейшие действия  
  
-   [Превращение группы атрибутов в видимую для пользователей (службы Master Data Services)](make-an-attribute-group-visible-to-users-master-data-services.md)  
  
## <a name="see-also"></a>См. также  
 [Группы атрибутов &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md)   
 [Master Data Services &#40;атрибутов&#41;](../../2014/master-data-services/attributes-master-data-services.md)   
 [Изменение имени группы атрибутов &#40;Master Data Services&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md)   
 [Удаление группы атрибутов &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md)   
 [Конечные разрешения &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [Объединенные разрешения &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  
