---
title: Свойство InternetTimeout (RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- InternetTimeout property [ADO]
ms.assetid: 4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549
author: rothja
ms.author: jroth
ms.openlocfilehash: 8862cc58889c4446c23e994a9c8e0f6a54a50d38
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82751970"
---
# <a name="internettimeout-property-rds"></a>Свойство InternetTimeout (служба удаленных рабочих столов)
Указывает количество миллисекунд ожидания перед истечением времени ожидания запроса.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Long** , представляющее количество миллисекунд до истечения времени ожидания запроса.  
  
## <a name="remarks"></a>Примечания  
 Это свойство применяется только к запросам, отправленным с помощью протоколов HTTP или HTTPS.  
  
 Выполнение запросов в трехуровневой среде может занять несколько минут. Используйте это свойство, чтобы указать дополнительное время для долго выполняющихся запросов.  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[Объект DataSpace (служба удаленных рабочих столов)](../../../ado/reference/rds-api/dataspace-object-rds.md)|  
  
## <a name="see-also"></a>См. также  
 [Пример свойства InternetTimeout (Visual Basic)](../../../ado/reference/rds-api/internettimeout-property-example-vb.md)   
 [Пример свойства InternetTimeout (Visual C++)](../../../ado/reference/rds-api/internettimeout-property-example-vc.md)   
 

