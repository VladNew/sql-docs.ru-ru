---
title: sys.dm_db_objects_impacted_on_version_change
titleSuffix: Azure SQL Database
ms.date: 03/03/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_objects_impacted_on_version_change_TSQL
- dm_db_objects_impacted_on_version_change
- dm_db_objects_impacted_on_version_change_TSQL
- sys.dm_db_objects_impacted_on_version_change
dev_langs:
- TSQL
helpviewer_keywords:
- dm_db_objects_impacted_on_version_change
- sys.dm_db_objects_impacted_on_version_change
ms.assetid: b94af834-c4f6-4a27-80a6-e8e71fa8793a
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.custom: seo-dt-2019
ms.openlocfilehash: 482f64eff3c37aad08319e6ea8af348b014bd784
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828065"
---
# <a name="sysdm_db_objects_impacted_on_version_change-azure-sql-database"></a>sys.dm_db_objects_impacted_on_version_change (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Это системное представление уровня базы данных предназначено для отображения ранних предупреждений, позволяющих определить объекты, которые затрагиваются при обновлении выпуска в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Можно использовать это представление до или после обновления для получения полного перечисления затронутых объектов. Чтобы запросить полный отчет для всего сервера, потребуется запросить это представление в каждой базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|класс|**тип int** НЕ NULL|Класс объекта, который будет затронут:<br /><br /> **1** = ограничение<br /><br /> **7** = кучи и индексы|  
|class_desc|**nvarchar (60)** НЕ NULL|Описание класса:<br /><br /> **OBJECT_OR_COLUMN**<br /><br /> **INDEX**|  
|major_id|**тип int** НЕ NULL|Код объекта ограничения или код объекта таблицы, содержащей индекс или кучу.|  
|minor_id|**тип int** ЗАКАНЧИВАЮЩ|значение **NULL** для ограничений<br /><br /> Index_id для индексов и куч|  
|dependency|**nvarchar (60)** НЕ NULL|Описание зависимости, которая вызывает применение затрагиваемого ограничения или индекса. Такое же значение используется для предупреждений, созданных во время обновления.<br /><br /> Примеры<br /><br /> Значение **space** (для встроенной функции)<br /><br /> **geometry** (для системного, определяемого пользователем типа)<br /><br /> **geography::Parse** (для системного, определяемого пользователем метода)|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE.  
  
## <a name="example"></a>Пример  
 В следующем примере показан запрос к представлению **sys.dm_db_objects_impacted_on_version_change**, применяемый для поиска объектов, подверженных влиянию обновления с переходом на следующую основную версию сервера  
  
```  
SELECT * FROM sys.dm_db_objects_disabled_on_version_change;  
GO  
```  
  
```  
class  class_desc        major_id    minor_id    dependency                       
------ ----------------- ----------- ----------- ----------   
1      OBJECT_OR_COLUMN  181575685   NULL        geometry                        
7      INDEX             37575172    1           geometry                        
7      INDEX             2121058592  1           geometry                        
1      OBJECT_OR_COLUMN  101575400   NULL        geometry     
```  
  
## <a name="remarks"></a>Remarks  
  
### <a name="how-to-update-impacted-objects"></a>Обновление затрагиваемых объектов  
 Далее описывается порядок действий по исправлению после обновления набора исправлений, которое будет доступно в июне.  
  
|Номер|Затрагиваемый объект|Действие по исправлению|  
|-----------|---------------------|-----------------------|  
|1|**Индексы**|Перестройте любой индекс, идентифицируемый **sys. dm_db_objects_impacted_on_version_change** например:`ALTER INDEX ALL ON <table> REBUILD`<br />or<br />`ALTER TABLE <table> REBUILD`|  
|2|**Объектами**|Все ограничения, обозначенные как **sys.dm_db_objects_impacted_on_version_change**, должны быть еще раз проверены после повторного вычисления данных типа Geometry и Geography в базовой таблице. Для ограничений выполните проверку с помощью инструкции ALTER TABLE. <br />Пример: <br />`ALTER TABLE <tab> WITH CHECK CHECK CONSTRAINT <constraint name>`<br />or<br />`ALTER TABLE <tab> WITH CHECK CONSTRAINT ALL`|  
  
  
