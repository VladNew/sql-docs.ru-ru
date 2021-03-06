---
title: Поля дескриптора возвращающего табличное значение параметра | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), descriptor fields
ms.assetid: 4e009eff-c156-4d63-abcf-082ddd304de2
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7a2d4b96d837edc1fa0fcb2ce2c9d48449eb59e7
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82698194"
---
# <a name="table-valued-parameter-descriptor-fields"></a>Поля дескрипторов возвращающего табличное значение параметра
  Поддержка возвращающих табличное значение параметров включает новые поля в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-дескрипторах параметра ODBC-приложения и дескрипторах параметра реализации.  
  
## <a name="remarks"></a>Remarks  
  
|name|Расположение|Type|Описание|  
|----------|--------------|----------|-----------------|  
|SQL_CA_SS_TYPE_NAME|IPD|SQLTCHAR*|Имя серверного типа возвращающего табличное значение параметра.<br /><br /> Если в вызове SQLBindParameter указано имя типа возвращающего табличное значение параметра, оно всегда должно быть указано в Юникоде даже в приложениях, созданных как приложения ANSI. Значение, используемое для параметра *StrLen_or_IndPtr* , должно быть либо SQL_NTS, либо строковой длины имени, умноженной на sizeof (WChar).<br /><br /> Если имя типа возвращающего табличное значение параметра указывается через SQLSetDescField, его можно указать с помощью литерала, который соответствует способу построения приложения. Диспетчер драйвера ODBC выполнит все необходимые преобразования данных в Юникод.|  
|SQL_CA_SS_TYPE_CATALOG_NAME (только для чтения)|IPD|SQLTCHAR*|Каталог, в котором определен тип.|  
|SQL_CA_SS_TYPE_SCHEMA_NAME|IPD|SQLTCHAR*|Схема, в которой определен тип.|  
  
 Приложения не должны устанавливать SQL_CA_SS_TYPE_CATALOG_NAME для возвращающих табличное значение параметров. Иначе будет возвращена ошибка SQL_ERROR и зарегистрирована диагностическая запись с SQLSTATE = HY091 и сообщением «Недопустимый идентификатор поля дескриптора».  
  
 Если фокус параметра установлен на возвращающий табличное значение параметр, то к возвращающим табличное значение параметрам применяются следующие атрибуты инструкций и поля заголовка дескриптора:  
  
|name|Расположение|Type|Описание|  
|----------|--------------|----------|-----------------|  
|SQL_ATTR_PARAMSET_SIZE<br /><br /> (эквивалентен SQL_DESC_ARRAY_SIZE в дескрипторе параметра приложения)|APD|SQLUINTEGER|Размер массива для массивов буфера для возвращающего табличное значение параметра. Это максимальное количество строк, которое может быть размещено в буферах, или размер буферов в строках. Возвращающий табличное значение параметр может иметь больше или меньше строк, чем помещается в буфер. Значение по умолчанию: 1. **Примечание.**  Если для SQL_SOPT_SS_PARAM_FOCUS задано значение по умолчанию 0, SQL_ATTR_PARAMSET_SIZE ссылается на инструкцию и указывает количество наборов параметров. Если для SQL_SOPT_SS_PARAM_FOCUS задан порядковый номер возвращающего табличное значение параметра, то он ссылается на возвращающий табличное значение параметр и указывает число строк для набора параметров для возвращающего табличное значение параметра.|  
|SQL_ATTR_PARAM _BIND_TYPE|APD|SQLINTEGER|По умолчанию имеет значение SQL_PARAM_BIND_BY_COLUMN.<br /><br /> Чтобы выбрать привязку на уровне строки, это поле имеет значение длины структуры или экземпляра буфера, который будет привязан к набору строк возвращающего табличное значение параметра. Эта длина должна включать пробел для всех связанных столбцов и все заполнения структуры или буфера. Это гарантирует, что если адрес связанного столбца увеличивается на указанную длину, результат будет указывать на начало того же столбца в следующей строке. При использовании оператора `sizeof` в ANSI C, такое поведение гарантируется.|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|APD|SQLINTEGER*|Значение по умолчанию — указатель NULL.<br /><br /> Если это поле имеет значение, отличное от NULL, драйвер разыменовывает указатель, добавляет разыменованное значение к каждому из отложенных полей в записи дескриптора (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR и SQL_DESC_OCTET_LENGTH_PTR), и использует новые значения указателя, чтобы получить значения данных.|  
  
 Эти поля допустимы только для возвращающих табличное значение параметров и не учитываются для всех остальных типов данных.  
  
 Поле SQL_CA_SS_TYPE_NAME не является обязательным для вызовов хранимых процедур. Оно должно быть указано для инструкций SQL, не являющихся вызовами процедур, чтобы разрешить серверу определять тип возвращающего табличное значение параметра.  
  
 Если необходимо имя типа и тип таблицы для возвращающего табличное значение параметра определяется в схеме, отличной от этой хранимой процедуры, то значение SQL_CA_SS_TYPE_SCHEMA_NAME должно быть задано в дескрипторе параметра реализации. Иначе сервер не сможет определить тип возвращающего табличное значение параметра. Это приведет к ошибке при вызове SQLExecute или SQLExecDirect. Ошибка будет иметь статус SQLSTATE= 07006 и сообщение «Нарушение атрибута ограниченного типа данных».  
  
 Столбцы возвращающего табличное значение параметра могут использовать привязки на уровне столбца или строки. По умолчанию используется привязка на уровне столбца. Установив параметр SQL_ATTR_PARAM_BIND_TYPE и SQL_ATTR_ PARAM_BIND_OFFSET_PTR, можно указать привязку на уровне строки. Это аналогично привязке на уровне строки столбцов и параметров.  
  
 Атрибуты SQL_CA_SS_TYPE_CATALOG_NAME и SQL_CA_SS_TYPE_SCHEMA_NAME могут также использоваться для получения каталога и схемы, связанных с параметрами определяемых пользователем типов данных CLR. Это альтернатива для существующих атрибутов схемы каталога, зависящих от типа, для этих типов.  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличное значение параметры &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
