---
title: Связанные и несвязанные столбцы text и Image | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 306abff20146ec5004b515578f5c71b8cb574bba
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718862"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Привязанные и непривязанные столбцы text и image
  При использовании серверных курсоров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента оптимизирован для передачи данных для непривязанных столбцов типа **Text**, **ntext**или **Image** во время выполнения **SQLFetch** . Данные типа **Text**, **ntext**или **Image** на самом деле не извлекаются с сервера, пока приложение не выдаст [SQLGetData](../native-client-odbc-api/sqlgetdata.md) для столбца.  
  
 Многие приложения могут быть написаны таким образом, чтобы не отображались данные типа **Text**, **ntext**или **Image** , пока пользователь просто прокручивается вверх и вниз в курсоре. Когда пользователь выбирает строку для получения более подробной информации, приложение может вызвать **SQLGetData** для получения данных типа **Text**, **ntext**или **Image** . Это предотвратит передачу данных типа **Text**, **ntext**или **Image** для любых строк, которые пользователь не выбирает, и таким образом предотвращает передачу очень больших объемов данных.  
  
## <a name="see-also"></a>См. также  
 [Управление столбцами Text и Image](managing-text-and-image-columns.md)   
 [Режимы работы курсоров](../native-client-odbc-cursors/cursor-behaviors.md)  
  
  
