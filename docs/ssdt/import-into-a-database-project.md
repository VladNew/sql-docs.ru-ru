---
title: Импорт в проект базы данных | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL.DATA.TOOLS.SQLPROJECTIMPORTSNAPSHOTSUMMARYDIALOG.DIALOG
- SQL.DATA.TOOLS.SQLPROJECTIMPORTDATABASESUMMARYDIALOG.DIALOG
- SQL.DATA.TOOLS.IMPORTSCRIPTWIZARD.SUMMARY
ms.assetid: d0a0a394-6cb6-416a-a25f-9babf8ba294a
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: af8ee2d569c44d19e518c1dafacddb958c66cc88
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087746"
---
# <a name="import-into-a-database-project"></a>Импорт в проект базы данных
Функцию импорта можно использовать для заполнения проекта новыми объектами из активной базы данных или файла DACPAC либо для обновления имеющихся объектов в проекте новым определением из скрипта. Следует отметить некоторые приведенные ниже различия в поведении между этими тремя действиями.  
  
**Меню "Импорт"**  
  
![Меню "Импорт" в SSDT](../ssdt/media/ssdt-import.gif "SSDT Import Menu")  
  
**Подразделы этого раздела**  
  
[Источник импорта: база данных или приложение уровня данных (*.dacpac)](#bkmk_import_source_db)  
  
[Источник импорта: скрипт (*.sql)](#bkmk_import_source_script)  
  
[Импорт зашифрованных объектов](#bkmk_import_encrypted)  
  
## <a name="bkmk_import_source_db"></a>Источник импорта: база данных или приложение уровня данных (*.dacpac)  
Возможность импорта схемы из базы данных или файла DACPAC доступна только в том случае, если в проекте еще не определены никакие объекты схемы. Это не относится к журналам рефакторинга или скриптам, выполняемым до и после развертывания.  
  
При импорте определения объектов записываются в файлы проекта с использованием параметров организации по умолчанию SSDT для новых объектов: новых файлов объектов верхнего уровня, иерархических потомков, определенных в том же файле в качестве родительского элемента, ограничений таблицы или столбца, определенных встроенным образом, где это возможно. Чтобы обеспечить более целенаправленную видимость и управление для каждого объекта, воспользуйтесь не импортом, а функцией «Сравнение схемы».  
  
Если источник импорта содержит скрипты, выполняемые до и после развертывания, журналы рефакторинга или определения переменных SQLCMD, то они будут импортированы в проект. Если проект уже содержит любой из этих объектов, импортированные файлы будут добавлены в папку проекта **Пропущенное при импорте**.  
  
**Пропущенное при импорте**  
  
![Папка SSDT "Пропущенное при импорте"](../ssdt/media/ssdt-ignoredonimport.gif "SSDT Ignored on Import Folder")  
  
## <a name="bkmk_import_source_script"></a>Источник импорта: скрипт (*.sql)  
Все объекты из источника импорта, которые *отсутствуют* в проекте, будут добавлены, а все объекты в источнике импорта, которые *присутствуют* в проекте, перезапишут соответствующие определения в проекте.  
  
> [!NOTE]  
> Известны две ошибки данного метода, которые будут исправлены в следующем выпуске:  
>   
> -   Если ограничения таблицы или столбца определены за пределами инструкции CREATE TABLE в определении таблицы проекта, то при импорте определение таблицы будет перезаписано, так что ограничение будет встроенным. Однако внешнее ограничение останется, в результате чего в проекте будут повторяющиеся ограничения.  
> -   Главные ключи или ключи шифрования базы данных из скрипта-источника, уже имеющиеся в проекте, будут дублированы при импорте. Для сборки проекта удалите повторяющиеся элементы.  
  
Процесс «Импорт из скрипта» не обрабатывает сценарии, выполняемые до или после развертывания, переменные SQLCMD и файлы журналов рефакторинга. Эти и другие неподдерживаемые конструкции, обнаруженные во время импорта, будут помещены в файл **ScriptsIgnoredOnImport.sql** в папке **Скрипты** проекта.  
  
Дополнительные сведения см. на форуме SSDT по адресу [http://social.msdn.microsoft.com/Forums/en-US/ssdt/threads](http://social.msdn.microsoft.com/Forums/en-US/ssdt/threads).  
  
## <a name="bkmk_import_encrypted"></a>Импорт зашифрованных объектов  
При импорте зашифрованных объектов в проект базы данных полный текст определения объекта не всегда может быть получен с сервера. Таким образом, поведение при импорте может быть различным при работе с данным классом объектов.  
  
Если полный текст определения получить не удается, то в скрипт помещается верхний и нижний колонтитул объекта с фиктивным текстом. Такое поведение может возникнуть при импорте или сравнении схемы, когда источником является активная база данных или файл DACPAC, извлеченный из базы данных.  
  
**Скрипт с фиктивным текстом**  
  
![Скрипт с фиктивным текстом](../ssdt/media/ssdt-procwithencryption.gif "Script with a Dummy Body")  
  
Если доступно и может быть получено полное определение объекта, операция импорта или сравнения схемы поместит его в проект полностью. Это происходит при обновлении проекта из скрипта, файла DACPAC, построенного на основе проекта базы данных, или другого проекта базы данных.  
  