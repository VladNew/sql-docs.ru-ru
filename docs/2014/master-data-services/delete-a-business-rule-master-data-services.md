---
title: Удаление бизнес-правила (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting business rules [Master Data Services]
- business rules [Master Data Services], deleting
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d294bb2d07d87216fb40fb93267518970fdf4c9d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "65479739"
---
# <a name="delete-a-business-rule-master-data-services"></a>Удаление бизнес-правила (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно удалить бизнес-правило, которое больше не нужно.  
  
> [!NOTE]  
>  Чтобы предотвратить выполнение проверки данных на соответствие бизнес-правилу, можно исключить эти данные, а не удалить их. Дополнительные сведения см. в разделе [Исключение бизнес-правила (службы Master Data Services)](exclude-a-business-rule-master-data-services.md).  
  
## <a name="prerequisites"></a>Предварительные условия  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** .  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
### <a name="to-delete-a-business-rule"></a>Удаление бизнес-правила  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  В строке меню выберите **Управление** и щелкните **Бизнес-правила**.  
  
3.  На странице **Обслуживание бизнес-правил** выберите модель из списка **Модель** .  
  
4.  Выберите сущность из списка **Сущность** .  
  
5.  В списке **Тип элемента** выберите тип элемента, к которому будет применяться бизнес-правило.  
  
6.  Выберите из списка **Атрибут** атрибут или оставьте **Все**по умолчанию.  
  
7.  В сетке щелкните строку бизнес-правила, которое необходимо удалить.  
  
8.  Щелкните **Удалить выбранное бизнес-правило**.  
  
9. В диалоговом окне подтверждения нажмите кнопку **ОК**. Значение в столбце **состояние** — **Ожидание удаления**.  
  
10. Нажмите кнопку **Опубликовать бизнес-правила**.  
  
11. В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Исключить &#40;бизнес-правила Master Data Services&#41;](exclude-a-business-rule-master-data-services.md)   
 [Создание и публикация бизнес-правила &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [Бизнес-правила (службы Master Data Services)](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
