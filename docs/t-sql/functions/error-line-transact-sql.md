---
title: ERROR_LINE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ERROR_LINE
- ERROR_LINE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], line number
- messages [SQL Server], line number
- TRY...CATCH [SQL Server]
- line number of error [SQL Server]
- ERROR_LINE function
- CATCH block
ms.assetid: 47335734-0baf-45a6-8b3b-6c4fd80d2cb8
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 247cb52aefba41df8a4d0becc1428e12acd4d377
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82804583"
---
# <a name="error_line-transact-sql"></a>ERROR_LINE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эта функция возвращает номер строки, в которой произошла ошибка, вызвавшая выполнение блока CATCH конструкции TRY…CATCH.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ERROR_LINE ( )  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
**int**  
  
## <a name="return-value"></a>Возвращаемое значение  
При вызове в блоке CATCH функция `ERROR_LINE` возвращает:  
  
-   номер строки, где произошла ошибка;    
-   номер строки в подпрограмме, если ошибка возникла в хранимой процедуре или триггере;  
-   значение NULL в случае вызова вне блока CATCH.  
  
## <a name="remarks"></a>Remarks  
Функцию `ERROR_LINE` можно вызывать в любом месте области действия блока CATCH.  
  
Функция `ERROR_LINE` возвращает номер строки, в которой возникла ошибка. Это происходит вне зависимости от места вызова `ERROR_LINE` в пределах блока CATCH от числа вызовов `ERROR_LINE`. В этом отличие данной функции от таких функций, как @@ERROR. Функция @@ERROR возвращает номер ошибки в той инструкции, которая непосредственно следует за инструкцией, вызвавшей ошибку, или же в первой инструкции блока CATCH.  
  
Во вложенных блоках CATCH функция `ERROR_LINE` возвращает номер строки ошибки, связанной с тем блоком CATCH, в котором она была вызвана. Например, блок CATCH конструкции TRY…CATCH может содержать вложенную конструкцию TRY…CATCH. Внутри вложенного блока CATCH функция `ERROR_LINE` возвращает номер строки ошибки, вызвавшей вложенный блок CATCH. Если функция `ERROR_LINE` выполняется во внешнем блоке CATCH, она возвращает номер строки ошибки, вызвавшей этот блок CATCH.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-error_line-in-a-catch-block"></a>A. Использование функции ERROR_LINE в блоке CATCH  
В приведенном ниже примере кода показана инструкция `SELECT`, вызывающая ошибку деления на ноль. Функция `ERROR_LINE` возвращает номер строки, где произошла ошибка.  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_LINE() AS ErrorLine;  
END CATCH;  
GO  
```  
  
### <a name="b-using-error_line-in-a-catch-block-with-a-stored-procedure"></a>Б. Использование функции ERROR_LINE в блоке CATCH с хранимой процедурой  
В приведенном ниже примере показана хранимая процедура, которая создает ошибку деления на 0. Функция `ERROR_LINE` возвращает номер строки, где произошла ошибка.  
  
```  
-- Verify that the stored procedure does not already exist.  
IF OBJECT_ID ( 'usp_ExampleProc', 'P' ) IS NOT NULL   
    DROP PROCEDURE usp_ExampleProc;  
GO  
  
-- Create a stored procedure that  
-- generates a divide-by-zero error.  
CREATE PROCEDURE usp_ExampleProc  
AS  
    SELECT 1/0;  
GO  
  
BEGIN TRY  
    -- Execute the stored procedure inside the TRY block.  
    EXECUTE usp_ExampleProc;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_LINE() AS ErrorLine;  
END CATCH;  
GO  
``` 


### <a name="c-using-error_line-in-a-catch-block-with-other-error-handling-tools"></a>В. Использование функции ERROR_LINE в блоке CATCH с другими средствами обработки ошибок  
В приведенном ниже примере кода показана инструкция `SELECT`, вызывающая ошибку деления на ноль. Функция `ERROR_LINE` возвращает номер строки, где произошла ошибка, и сведения, связанные с этой ошибкой.  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_LINE() AS ErrorLine,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
``` 
  
## <a name="see-also"></a>См. также:  
 [TRY...CATCH (Transact-SQL)](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [sys.messages (Transact-SQL)](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [ERROR_NUMBER (Transact-SQL)](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_MESSAGE (Transact-SQL)](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_PROCEDURE (Transact-SQL)](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY (Transact-SQL)](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE (Transact-SQL)](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  
