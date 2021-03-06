---
title: Установка компонентов ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC]
- installing ODBC components [ODBC], about installing
- ODBC [ODBC], component installation
ms.assetid: b7e48e9c-8912-4003-b4ef-30aa44de06a7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbd0a6aeba8073ce14b08b8635396b1f231895fb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298984"
---
# <a name="installing-odbc-components"></a>Установка компонентов ODBC
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC входит в операционную систему Windows. Следует явно устанавливать ODBC только в более ранних версиях Windows.  
  
 В этом разделе описывается, как устанавливаются и удаляются компоненты ODBC. Поскольку разработчики драйверов всегда устанавливают компонент ODBC (драйвер), им нужно прочитать этот раздел. Разработчикам приложений необходимо прочитать этот раздел только в том случае, если они поставляют компоненты ODBC с приложениями. Компоненты ODBC включают диспетчер драйверов, драйверы, переводчики, библиотеку DLL установщика, библиотеку курсоров и все связанные файлы. В этом разделе приложения ODBC не считаются компонентами ODBC.  
  
> [!NOTE]  
>  Этот раздел относится только к платформам Microsoft Windows. Установка компонентов ODBC на других платформах зависит от платформы.  
  
 Компоненты ODBC устанавливаются и удаляются отдельно для каждого компонента, а не для каждого файла. Например, если транслятор состоит из самого транслятора и нескольких файлов данных, эти файлы устанавливаются и удаляются в виде группы. они не должны устанавливаться и удаляться отдельно для каждого файла. Причина этого заключается в том, чтобы убедиться в том, что в системе существует только полный компонент.  
  
 В целях установки и удаления компонентов определены следующие компоненты ODBC:  
  
-   **Основные компоненты.** Диспетчер драйверов, Библиотека курсоров, Библиотека DLL установщика и другие связанные файлы составляют основные компоненты и должны быть установлены и удалены в виде группы.  
  
-   **Поставщиков.** Каждый драйвер является отдельным компонентом.  
  
-   **Преобразователей.** Каждый переводчик является отдельным компонентом.  
  
 Благодаря поддержке Юникода в ODBC 3,5 и более поздних версиях следует учитывать некоторые факторы, которые следует учесть при использовании компонентов OLE DB с ODBC. Версия 1,1 поставщика OLE DB для ODBC была записана в конкретные спецификации Юникода в ODBC 3,0. Поскольку эти спецификации изменились в ODBC 3,5, необходимо иметь поставщик версии 1,5 или более поздней при использовании ODBC 3,5 и более поздних версий. Этот раздел содержит следующие подразделы.  
  
-   [Компоненты установки](../../../odbc/reference/install/installation-components.md)  
  
-   [Подсчет использования](../../../odbc/reference/install/usage-counting.md)
