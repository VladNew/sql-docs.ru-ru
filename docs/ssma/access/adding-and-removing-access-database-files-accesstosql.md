---
title: Добавление и удаление файлов базы данных Access (Акцесстоскл) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases
- adding Access files
- adding and removing Access databases
- browsing Access metadata
- browsing metadata, Access databases
- connecting, Access databases
- databases
- files, adding and removing
- finding Access databases
- finding database files
- locating database files
- metadata
- metadata, browsing
- metadata, refreshing
- refreshing metadata
- removing Access files
- scanning for database files
- searching for database files
ms.assetid: e944c740-4c8a-4bc1-b0ed-be57bc06dced
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 39df13a3cab2d842a313ca37fc4a98d0c331ba83
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68104215"
---
# <a name="adding-and-removing-access-database-files-accesstosql"></a>Добавление и удаление файлов базы данных Access (Акцесстоскл)
Чтобы перенести данные доступа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, необходимо добавить одну или несколько баз данных Access в проект SSMA. Эти базы данных должны иметь доступ к 97 или более поздним версиям. При наличии баз данных из более ранней версии Access необходимо преобразовать базы данных в более новую версию. Это можно сделать, открыв и сохранив базы данных в Access 97 или более поздней версии, прежде чем добавлять их в SSMA.  
  
## <a name="what-happens-when-you-add-access-database-files"></a>Что происходит при добавлении файлов базы данных Access?  
При добавлении базы данных Access в проект SSMA SSMA считывает метаданные базы данных, а затем добавляет эти метаданные в файл проекта. Эти метаданные описывают базу данных и ее объекты. SSMA использует метаданные при преобразовании объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис или SQL Azure, а также при переносе данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Эти метаданные можно просмотреть в обозревателе метаданных Access и просмотреть свойства отдельных объектов базы данных.  
  
> [!NOTE]  
> Базу данных Access можно разделить на несколько файлов: серверную базу данных, содержащую таблицы, и клиентские базы данных, содержащие запросы, формы, отчеты, макросы, модули и ярлыки. Если вы хотите перенести базу данных с разделением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на или SQL Azure, добавьте базу данных переднего плана в SSMA.  
  
## <a name="permissions-that-are-required-by-ssma"></a>Разрешения, необходимые для SSMA  
Чтобы перенести базу данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, группа пользователей и пользователь с правами администратора должны иметь разрешения администратора. Сведения о переносе баз данных с помощью защиты рабочих групп см. в разделе [Подготовка баз данных Access к миграции](preparing-access-databases-for-migration-accesstosql.md).  
  
## <a name="selecting-databases-to-add"></a>Выбор баз данных для добавления  
Если вы хотите добавить одну или несколько баз данных в проект SSMA и все файлы находятся в одном известном расположении, их можно добавить с помощью следующей процедуры.  
  
**Добавление отдельных файлов базы данных**  
  
1.  В меню **файл** выберите команду **Добавить базы данных**.  
  
2.  В диалоговом окне **Открыть** выберите папку, содержащую файл или файлы базы данных.  
  
3.  Выберите файлы, которые требуется добавить, и нажмите кнопку **Открыть**.  
  
## <a name="finding-databases-to-add"></a>Поиск баз данных для добавления  
Если требуется добавить несколько баз данных Access из разных папок в проект SSMA или вы хотите добавить один файл, но нужно найти файл, то можно выполнить следующие действия, чтобы найти один или несколько файлов и добавить их в проект.  
  
**Поиск и Добавление баз данных**  
  
1.  В меню **файл** выберите пункт **найти базы данных**.  
  
2.  В мастере поиска баз данных введите имя диска, путь к файлу или UNC-путь, который требуется найти. Также можно нажать кнопку **Обзор** , чтобы найти диск или сетевую папку.  
  
3.  Нажмите кнопку **Добавить** , чтобы добавить расположение в список.  
  
    Повторите предыдущие два шага, чтобы добавить дополнительные расположения для поиска.  
  
4.  При необходимости добавьте условие поиска для уточнения списка возвращаемых баз данных.  
  
    > [!IMPORTANT]  
    > В текстовом поле **все или часть имени файла** не поддерживаются подстановочные знаки.  
  
5.  Нажмите кнопку **Проверить**.  
  
    Откроется страница Scan (сканирование). Отобразятся найденные базы данных и ход выполнения поиска. Чтобы прерывать Поиск, нажмите кнопку " **Закрыть**".  
  
6.  На странице Выбор файлов выберите базы данных, которые необходимо добавить в проект.  
  
    Можно использовать кнопки **выбрать все** и **Очистить все** в верхней части списка, чтобы выбрать или очистить все базы данных. Удерживая нажатой клавишу CTRL, можно выбрать несколько баз данных или нажать клавишу SHIFT, чтобы выбрать диапазон баз данных.  
  
7.  Щелкните **Далее**.  
  
8.  На странице Проверка нажмите кнопку **Готово**.  
  
## <a name="browsing-access-metadata"></a>Просмотр метаданных доступа  
После добавления базы данных Access в проект метаданные проекта отображаются в обозревателе метаданных Access. В обозревателе можно просматривать иерархию баз данных и объектов базы данных.  
  
**Просмотр метаданных**  
  
1.  В обозревателе метаданных Access разверните узел **доступ — метабаза**, а затем узел **базы данных**.  
  
2.  Разверните базу данных, которую необходимо проверить, а затем разверните узел **запросы**.  
  
    Обратите внимание на список запросов. Если выбрать запрос, на правой панели появится вкладка **SQL** и вкладка **свойства** .  
  
3.  Разверните узел **таблицы** и выберите таблицу.  
  
    Обратите внимание, что отображаются четыре вкладки: **Таблица**, **Сопоставление типов**, **Свойства**и **данные**.  
  
4.  Разверните таблицу, разверните **раздел ключи**, а затем выберите ключ.  
  
    Ключевые свойства отображаются на правой панели.  
  
5.  Разверните узел **индексы**и выберите индекс.  
  
    Свойства индекса отображаются на правой панели.  
  
## <a name="refreshing-databases"></a>Обновление баз данных  
Если база данных Access изменяется после добавления ее файла, можно обновить метаданные из базы данных Access.  
  
**Обновление метаданных доступа**  
  
-   В обозревателе метаданных Access щелкните правой кнопкой мыши базу данных и выберите пункт **Обновить из базы данных**.  
  
## <a name="removing-databases"></a>Удаление баз данных  
Чтобы удалить базу данных Access из проекта, выполните следующие действия.  
  
**Удаление базы данных из проекта**  
  
1.  В обозревателе метаданных Access разверните узел **доступ — метабаза**, а затем узел **базы данных**.  
  
2.  Щелкните правой кнопкой мыши базу данных и выберите пункт **Удалить базу данных**.  
  
## <a name="next-step"></a>Следующий шаг  
Следующим шагом процесса миграции является [Подключение к SQL Server](https://msdn.microsoft.com/bb8c4bde-cfc2-4636-92ae-5dd24abe9536).  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[создание проектов и управление ими](creating-and-managing-projects-accesstosql.md)  
  
