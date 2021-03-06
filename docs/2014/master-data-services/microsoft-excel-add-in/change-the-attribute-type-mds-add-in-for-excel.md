---
title: Изменение типа атрибута (надстройка MDS для Excel) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9d3001d9-8d0f-4e4a-8e04-4f666bf0df69
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 4406eb225002bbf5df93f8c67385694922d7d2c7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "65482767"
---
# <a name="change-the-attribute-type-mds-add-in-for-excel"></a>Изменение типа атрибута (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]администраторы могут изменить тип атрибута, если тип данных или количество допустимых символов являются неверными.  
  
 Если необходимо изменить тип атрибута для создания ограниченного списка (атрибут на основе домена), см. раздел [Создание атрибута на основе домена (надстройка MDS для Excel)](create-a-domain-based-attribute-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  Нельзя изменить тип или длину столбцов **Имя** или **Код**.  
  
## <a name="prerequisites"></a>Предварительные условия  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональным областям **Администрирование системы** и **Обозреватель** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).  
  
-   должны быть существующие модель, сущность и атрибут.  
  
### <a name="to-change-the-attribute-type"></a>Изменение типа атрибута  
  
1.  В Excel загрузите сущность, содержащую столбец (атрибут), который необходимо изменить. Дополнительные сведения см. [в статье Загрузка данных из MDS в Excel](export-data-to-excel-from-master-data-services.md).  
  
2.  Щелкните любую ячейку в столбце, который подлежит изменению.  
  
3.  В группе **Построить модель** нажмите кнопку **Свойства атрибута**.  
  
4.  В диалоговом окне **Свойства атрибута** при необходимости обновите параметры.  
  
5.  Нажмите кнопку **ОК**.  
  
## <a name="what-happens-when-you-change-the-attribute-type"></a>Что происходит при изменении типа атрибута  
 Если есть какая-либо зависимость от атрибута, например на атрибут ссылается бизнес-правило MDS или он включен в представление подписки, то MDS при изменении типа данных атрибута выполняет следующие операции.  
  
-   Изменение типа данных атрибута.  
  
-   Создать копию атрибута с суффиксом "_old", который не содержит значения. Это называется **устаревшим** атрибутом.  
  
 Однако все существующие элементы, которые зависят от исходного атрибута, будут указывать на устаревший атрибут, а не на измененный.  
  
 Это означает следующее.  
  
-   Необходимо обновить бизнес-правила так, чтобы они указывали на измененный атрибут, поскольку логика может измениться с учетом того, что у атрибута теперь новый тип данных. Необходимо изменить все затронутые правила, а затем переработать выражения, чтобы удалить ссылки на устаревший атрибут (_old) и установить ссылки на обновленный атрибут.  
  
-   Необходимо открыть все представления подписки в разделе Управление интеграцией, выбрать строку представления, открыть ее для редактирования, щелкнув значок карандаша, а затем щелкнув значок **сохранить диск** , чтобы обновить определение представления. Для повторного формирования синтаксиса представления больше никаких изменений не требуется.  
  
-   К промежуточным таблицам, в которых есть этот атрибут, будет добавлен столбец с устаревшим атрибутом, а это означает, что промежуточный код также будет затронут. Устаревший атрибут после обновления бизнес-правил и представлений подписки можно удалить.  
  
 **Удаление устаревшего атрибута**  
  
 Прежде чем удалить какой-либо устаревший атрибут, необходимо удалить все ссылки на этот атрибут, например зафиксировать бизнес-правила и повторно сформировать представления подписки, как описано выше. В противном случае при попытке удалить устаревший атрибут на веб-странице «Системное администрирование» возникнет ошибка, указывающая, что атрибут нельзя удалить, так как на него ссылается объект.  
  
 Чтобы удалить атрибут, см. раздел [Delete a attribute &#40;Master Data Services&#41;](../delete-an-attribute-master-data-services.md)  
  
> [!TIP]  
>  Изменять тип данных атрибутов MDS, которые имеют данные и связанные сущности, неудобно, особенно если объявлено бизнес-правило или представление подписки, которое ссылается на сущность. Рекомендуется для начала выбрать тип данных, который достаточно гибок и позволяет указывать все необходимые значения. Например, вначале строки могут быть небольшими, но со временем становиться все длиннее, поэтому следует исходить из самого худшего варианта развития событий. Очень длинные текстовые строки могут быть неудобными в работе (например, широкие текстовые поля для пользовательского интерфейса сложно уместить на экране), поэтому следует избегать слишком длинных строк.  
  
## <a name="see-also"></a>См. также  
 [Master Data Services &#40;атрибутов&#41;](../attributes-master-data-services.md)   
 [Построение модели (надстройка MDS для Excel)](building-a-model-mds-add-in-for-excel.md)  
  
  
