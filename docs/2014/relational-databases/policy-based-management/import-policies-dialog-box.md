---
title: Диалоговое окно "Импорт политик" | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.importpolicy.f1
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
caps.latest.revision: 21
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 06ba646fdd03aa577d9f04df009b0b494d558668
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37292564"
---
# <a name="import-policies-dialog-box"></a>Диалоговое окно «Импорт политик»
  Это диалоговое окно используется для импорта одной или нескольких политик (и упоминаемого в них условия), сохраненных в виде XML-файлов, в текущий экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] .  
  
## <a name="options"></a>Параметры  
 **Файлы, подлежащие импорту**  
 Чтобы выполнить импорт политики из XML-файла, введите путь и имя файла или нажмите кнопку "Обзор" (**...**).  
  
 **Заменять дубликаты импортируемыми элементами**  
 Выберите, чтобы перезаписать любую существующую политику или условие с тем же именем, если они уже существуют в экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Перезаписать условие с зависимой политикой можно только в том случае, если зависимая политика также переписывается. Если данный параметр не выбран, то наличие условия с таким же выражением не вызовет ошибку.  
  
 **Состояние политики**  
 Выберите требуемое состояние для импортированной политики:  
  
-   **Сохранить состояние политики при импорте**  
  
-   **Включить все политики при импорте**  
  
-   **Выключить все политики при импорте**  
  
## <a name="see-also"></a>См. также  
 [Администрирование серверов с помощью управления на основе политик](administer-servers-by-using-policy-based-management.md)   
 [Импорт политики управления на основе политик](import-a-policy-based-management-policy.md)   
 [Экспорт политики управления на основе политик](export-a-policy-based-management-policy.md)  
  
  