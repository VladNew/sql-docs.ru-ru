---
title: Демонстрация повышения производительности для выполняющейся в памяти OLTP | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c6def45d-d2d4-4d24-8068-fab4cd94d8cc
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 8c9477a318d2cb4f9886d67da8a4f8b5967cc180
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63071789"
---
# <a name="demonstration-performance-improvement-of-in-memory-oltp"></a>Демонстрация. Улучшение производительности выполняющейся в памяти OLTP
  Это пример демонстрирует улучшение производительности при использовании In-Memory OLTP путем сравнения различий времени ответа при выполнении идентичного запроса Transact-SQL или таблиц, оптимизированных для памяти, и таблиц на диске. Кроме того, в нем также создается (на основе того же запроса) и выполняется компилированная в собственном коде хранимая процедура для демонстрации того, что наилучшего времени ответа, как правило, можно добиться при запросе таблицы, оптимизированной для памяти, с помощью компилированной в собственном коде хранимой процедуры. Это пример показывает лишь один аспект улучшений производительности при доступе к данным в таблицах, оптимизированных для памяти: эффективность доступа к данным при выполнении вставки. В этом примере реализован только один поток, который не позволяет воспользоваться преимуществами параллелизма In-Memory OLTP. Рабочая нагрузка, которая использует параллелизм, получит более заметное повышение производительности.  
  
> [!NOTE]  
>  Другой пример, демонстрирующий оптимизированные для памяти таблицы см. в разделе [Пример SQL Server 2014 In-Memory OLTP](https://msftdbprodsamples.codeplex.com/releases/view/114491).  
  
 Для завершения этого примера потребуется выполнить следующие действия.  
  
1.  Создание базы данных с именем **imoltp** и изменение сведений о ее файлах, чтобы настроить ее для использования In-Memory OLTP.  
  
2.  Создание объектов базы данных для нашего примера: три таблицы и компилированная в собственном коде хранимая процедура.  
  
3.  Выполнение различных запросов и отображение времени ответа по каждому запросу.  
  
 Чтобы установить базу данных **imoltp** для нашего примера, сначала создайте пустую папку **c:\imoltp_data**, а затем выполните следующий код:  
  
```sql  
USE master  
GO  
  
-- Create a new database.  
CREATE DATABASE imoltp  
GO  
  
-- Prepare the database for In-Memory OLTP by  
-- adding a memory-optimized filegroup to the database.  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_file_group  
    CONTAINS MEMORY_OPTIMIZED_DATA;  
  
-- Add a file (to hold the memory-optimized data) to the new filegroup.  
ALTER DATABASE imoltp ADD FILE (name='imoltp_file', filename='c:\imoltp_data\imoltp_file')  
    TO FILEGROUP imoltp_file_group;  
GO  
  
```  
  
 Затем выполните следующий код, чтобы создать таблицу на диске, две (2) таблицы, оптимизированные для памяти, и компилированную в собственном коде хранимую процедуру для демонстрации различных методов доступа к данным:  
  
```sql  
USE imoltp  
GO  
  
-- If the tables or stored procedure already exist, drop them to start clean.  
IF EXISTS (SELECT NAME FROM sys.objects WHERE NAME = 'DiskBasedTable')  
   DROP TABLE [dbo].[DiskBasedTable]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects WHERE NAME = 'InMemTable')  
   DROP TABLE [dbo].[InMemTable]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects  WHERE NAME = 'InMemTable2')  
   DROP TABLE [dbo].[InMemTable2]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects  WHERE NAME = 'usp_InsertData')  
   DROP PROCEDURE [dbo].[usp_InsertData]  
GO  
  
-- Create a traditional disk-based table.  
CREATE TABLE [dbo].[DiskBasedTable] (  
  c1 INT NOT NULL PRIMARY KEY,  
  c2 NCHAR(48) NOT NULL  
)  
GO  
  
-- Create a memory-optimized table.  
CREATE TABLE [dbo].[InMemTable] (  
  c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),  
  c2 NCHAR(48) NOT NULL  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY = SCHEMA_AND_DATA);  
GO  
  
-- Create a 2nd memory-optimized table.  
CREATE TABLE [dbo].[InMemTable2] (  
  c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),  
  c2 NCHAR(48) NOT NULL  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY = SCHEMA_AND_DATA);  
GO  
  
-- Create a natively-compiled stored procedure.  
CREATE PROCEDURE [dbo].[usp_InsertData]   
  @rowcount INT,  
  @c NCHAR(48)  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
  AS   
  BEGIN ATOMIC   
  WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  DECLARE @i INT = 1;  
  WHILE @i <= @rowcount  
  BEGIN  
    INSERT INTO [dbo].[inMemTable2](c1,c2) VALUES (@i, @c);  
    SET @i += 1;  
  END  
END  
GO  
  
```  
  
 Настройка завершена, и мы готовы к выполнению запросов, отображающих время ответа для сравнения производительности различных методов доступа к данным.  
  
 Чтобы завершить пример, выполните следующий код несколько раз. Не обращайте внимания на результаты первого выполнения, на которое отрицательно влияет начальное выделение памяти.  
  
```sql  
SET STATISTICS TIME OFF;  
SET NOCOUNT ON;  
  
-- Delete data from all tables to reset the example.  
DELETE FROM [dbo].[DiskBasedTable]   
    WHERE [c1]>0  
GO  
DELETE FROM [dbo].[inMemTable]   
    WHERE [c1]>0  
GO  
DELETE FROM [dbo].[InMemTable2]   
    WHERE [c1]>0  
GO  
  
-- Declare parameters for the test queries.  
DECLARE @i INT = 1;  
DECLARE @rowcount INT = 100000;  
DECLARE @c NCHAR(48) = N'12345678901234567890123456789012345678';  
DECLARE @timems INT;  
DECLARE @starttime datetime2 = sysdatetime();  
  
-- Disk-based table queried with interpreted Transact-SQL.  
BEGIN TRAN  
  WHILE @I <= @rowcount  
  BEGIN  
    INSERT INTO [dbo].[DiskBasedTable](c1,c2) VALUES (@i, @c);  
    SET @i += 1;  
  END  
COMMIT  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (disk-based table with interpreted Transact-SQL).';  
  
-- Memory-optimized table queried with interpreted Transact-SQL.  
SET @i = 1;  
SET @starttime = sysdatetime();  
  
BEGIN TRAN  
  WHILE @i <= @rowcount  
    BEGIN  
      INSERT INTO [dbo].[InMemTable](c1,c2) VALUES (@i, @c);  
      SET @i += 1;  
    END  
COMMIT  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (memory-optimized table with interpreted Transact-SQL).';  
  
-- Memory-optimized table queried with a natively-compiled stored procedure.  
SET @starttime = sysdatetime();  
  
EXEC usp_InsertData @rowcount, @c;  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (memory-optimized table with natively-compiled stored procedure).';  
  
```  
  
 Ожидаемые результаты содержат фактическое время ответа и подтверждают тот факт, что использование таблиц, оптимизированных для памяти, и компилированных в собственном коде хранимых процедур, как правило, стабильно обеспечивает более быстрое время ответа по сравнению с аналогичными нагрузками, выполняемыми на основе традиционных таблиц на диске.  
  
## <a name="see-also"></a>См. также  
 [Расширения в AdventureWorks для демонстрации выполняющейся в памяти OLTP](../../database-engine/extensions-to-adventureworks-to-demonstrate-in-memory-oltp.md)   
 [Выполняющаяся в памяти OLTP &#40;оптимизации в памяти&#41;](in-memory-oltp-in-memory-optimization.md)   
 [Оптимизированные для памяти таблицы](memory-optimized-tables.md)   
 [Скомпилированные в собственном код хранимые процедуры](natively-compiled-stored-procedures.md)   
 [Требования к использованию таблиц, оптимизированных для памяти](requirements-for-using-memory-optimized-tables.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Параметры ALTER DATABASE File и FILEGROUP &#40;&#41;Transact-SQL](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)   
 [СОЗДАНИЕ процедур и таблиц, оптимизированных для памяти](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
