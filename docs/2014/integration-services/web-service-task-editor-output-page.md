---
title: Редактор задачи «веб-служба» (страница «выходные данные») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7924570253bf2f805d91c4dfabc3d5facf44cccc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054473"
---
# <a name="web-service-task-editor-output-page"></a>Редактор задачи «Веб-служба» (страница «Вывод»)
  Используйте страницу **Вывод** диалогового окна **Редактор задачи «Веб-служба»** , чтобы указать, где следует хранить результаты, возвращенные веб-методом.  
  
 Дополнительные сведения об этой задаче см. в разделе [Задача "Веб-служба"](control-flow/web-service-task.md).  
  
## <a name="static-options"></a>Статические параметры  
 **OutputType**  
 Выберите тип хранения, используемый для хранения результатов. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**Соединение с файлом**|Хранить результаты в файле. При выборе этого значения отображается динамический параметр **Файл**.|  
|**Переменная**|Хранить результаты в переменной. При выборе этого значения отображается динамический параметр **Переменная**.|  
  
## <a name="outputtype-dynamic-options"></a>Динамические параметры OutputType  
  
### <a name="outputtype--file-connection"></a>OutputType = Соединение с файлом  
 **Файл**  
 Выберите Диспетчер подключения файлов в списке или нажмите кнопку \< **создать соединение...**>, чтобы создать новый диспетчер соединений.  
  
 **См. также:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="outputtype--variable"></a>OutputType = Переменная  
 **Переменная**  
 Выберите переменную из списка или нажмите кнопку \< **создать переменную...**>, чтобы создать новую переменную.  
  
 **См. также:**  [Integration Services &#40;переменные&#41; SSIS](integration-services-ssis-variables.md), [Добавить переменную](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "веб-служба" &#40;страница "Общие"&#41;](general-page-of-integration-services-designers-options.md)   
 [Редактор задачи "веб-служба" &#40;"входная страница"&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Страница «Выражения»](expressions/expressions-page.md)  
  
  
