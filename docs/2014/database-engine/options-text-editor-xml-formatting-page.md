---
title: Параметры (текстовый редактор — страница «форматирование XML») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97373178-d288-4127-af37-d9f5fe1b8607
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e0d36c5a92dba9f3f92943b65107e7eedb178554
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000636"
---
# <a name="options-text-editor---xml---formatting-page"></a>Параметры ("Текстовый редактор" — "XML" — страница "Форматирование")

При помощи этого диалогового окна можно задать настройки форматирования для XML-редактора. Диалоговое окно **Параметры** можно открыть из меню **Сервис**.  
  
> [!NOTE]  
> Эти настройки доступны при выборе папки **Текстовый редактор**, папки **XML** и параметра **Форматирование** в диалоговом окне **Параметры**.  
  
## <a name="attributes"></a>Атрибуты  
 **Сохранить ручное форматирование атрибутов**  
 Не переформатировать атрибуты. Это значение по умолчанию.  
  
> [!NOTE]  
>  Если атрибуты расположены на нескольких строках, редактор смещает каждую строку атрибутов, чтобы соответствовать структурированию родительского элемента.  
  
 **Выравнивать атрибуты, чтобы каждый был на отдельной строке**  
 Расположить второй и последующий атрибуты вертикально, в соответствии со структурированием первого атрибута. Следующий XML-текст является примером расположения атрибутов.  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95"  
</item>  
```  
  
## <a name="auto-reformat"></a>Автоматическое переформатирование  
 **При вставке из буфера обмена**  
 Переформатировать XML-текст, вставленный из буфера обмена.  
  
 **По завершении закрывающего тега**  
 Переформатировать элемент по завершении закрывающего тега.  
  
## <a name="mixed-content"></a>Смешанное содержимое  
 **Форматировать смешанное содержимое по умолчанию**  
 Произвести попытку переформатировать смешанное содержимое, за исключением тех случаев, когда содержание находится в области `xml:space="preserve"`. Это значение по умолчанию.  
  
 Содержимое элемента считается смешанным, если он состоит из текста и разметки. Далее приводится пример элемента со смешанным содержимым.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
```  
  
 \</dir>  
  
## <a name="see-also"></a>См. также  
 [Редактор XML (среда SQL Server Management Studio)](../ssms/sql-server-management-studio-ssms.md)  
