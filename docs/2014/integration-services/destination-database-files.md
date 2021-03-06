---
title: Файлы целевой базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.destdbfiles.f1
ms.assetid: f6f90417-86fb-4b8c-a790-0b215c344ef6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2cfee31b4167625b4f868d7312abd752a215652c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66059548"
---
# <a name="destination-database-files"></a>Файлы базы данных-назначения
  Используйте диалоговое окно **Файлы целевой базы данных** для просмотра или изменения имен файлов базы данных и местоположений на целевом сервере, или для определения положения в сети файла для задачи «Передача базы данных». Дополнительные сведения об этой задаче см. в разделе [Задача "Передача базы данных"](control-flow/transfer-database-task.md).  
  
 Для автоматического заполнения этого диалогового окна именами файлов базы данных и положений на исходном сервере сначала укажите **SourceConnection**, **SourceDatabaseName**и **SourceDatabaseFiles** на странице **Базы данных** диалогового окна **Редактор задачи «Передача базы данных»** .  
  
## <a name="options"></a>Параметры  
 **Целевой файл**  
 Имена переданных файлов базы данных на целевом сервере.  
  
 Введите имя файла или нажмите имя файла для редактирования.  
  
 **Целевая папка**  
 Папка на целевом сервере, куда должны быть переданы файлы базы данных.  
  
 Введите путь к папке, нажмите путь к папке для редактирования или нажмите кнопку обзора для указания папки, куда необходимо передать файлы базы данных на целевом сервере.  
  
 **Сетевая общая папка**  
 Общая сетевая папка на целевом сервере, куда должны быть переданы файлы базы данных. Используйте **сетевую общую папку** при переносе базы данных в автономном режиме, указав **значение DatabaseOffline параметра** для **метода** на странице **базы данных** диалогового окна **Редактор задачи «перемещение базы данных** ».  
  
 Введите размещение сетевой общей папки или нажмите кнопку обзора для ее указания.  
  
 При передаче базы данных в режиме вне сети файлы базы данных копируются в **Сетевую общую папку** перед тем, как они переданы в расположение **Целевая папка** .  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Перемещение базы данных" &#40;общие&#41;страницы](general-page-of-integration-services-designers-options.md)   
 [Редактор задачи "Передача базы данных" (страница "Базы данных")](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  
