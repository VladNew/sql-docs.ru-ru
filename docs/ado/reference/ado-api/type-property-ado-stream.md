---
title: Свойство Type (поток ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Type
- _Stream::get_Type
- _Stream::put_Type
helpviewer_keywords:
- Type property [ADO Stream]
ms.assetid: f6a17e8c-7a28-48d0-bded-76b9e0cf7639
author: rothja
ms.author: jroth
ms.openlocfilehash: de61f4877dc6adcdfaa9644f5f266cd827a1d096
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765345"
---
# <a name="type-property-ado-stream"></a>Свойство Type (объект Stream ADO)
Указывает тип данных, содержащихся в [потоке](../../../ado/reference/ado-api/stream-object-ado.md) (двоичный или текстовый).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение [стреамтипинум](../../../ado/reference/ado-api/streamtypeenum.md) , указывающее тип данных, содержащихся в объекте **потока** . Значение по умолчанию — **адтипетекст**. Однако, если двоичные данные изначально записываются в новый пустой **поток**, **Тип** изменится на **адтипебинари**.  
  
## <a name="remarks"></a>Примечания  
 Свойство **Type** доступно только для чтения и записи, если текущая координата находится в начале **потока** (значение[позиции](../../../ado/reference/ado-api/position-property-ado.md) равно 0), а в любой другой позиции — только для чтения.  
  
 Свойство**Type** определяет, какие методы следует использовать для чтения и записи **потока**. Для текстовых **потоков**используйте [ReadText](../../../ado/reference/ado-api/readtext-method.md) и [WriteText](../../../ado/reference/ado-api/writetext-method.md). Для двоичных **потоков**используйте [Чтение](../../../ado/reference/ado-api/read-method.md) и [запись](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство RecordType (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Свойство Type (ADO)](../../../ado/reference/ado-api/type-property-ado.md)
