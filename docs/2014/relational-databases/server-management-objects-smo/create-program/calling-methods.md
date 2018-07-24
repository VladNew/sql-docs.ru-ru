---
title: Вызов методов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- methods [SMO]
- calling methods
- SQL Server Management Objects, method calling
- SMO [SQL Server], method calling
ms.assetid: c88d5c5f-9ff0-4f84-b2b6-24c6b90fa15e
caps.latest.revision: 44
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b2d2cce4fa8bf38e8403af1a783c9b1d85eb14aa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37264310"
---
# <a name="calling-methods"></a>Вызов методов
  Методы выполняют специальные задачи, связанные с объектом, например устанавливают `Checkpoint` в базу данных или запрашивают перечисляемый список имен входа для экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Методы выполняют операции с объектом. Они могут принимать параметры и часто возвращают значение. Возвращаемое значение может быть простым типом данных, сложным объектом или структурой, содержащей большое число членов.  
  
 Для проверки успешного выполнения метода используется обработка исключений. Дополнительные сведения см. в разделе [Handling SMO Exceptions](handling-smo-exceptions.md).  
  
## <a name="examples"></a>Примеры  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="using-a-simple-smo-method-in-visual-basic"></a>Использование простого метода SMO на языке Visual Basic  
 В этом примере метод <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> не принимает параметры и не возвращает значение.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods1](SMO How to#SMO_VBMethods1)]  -->  
  
## <a name="using-a-simple-smo-method-in-visual-c"></a>Использование простого метода SMO на языке Visual C#  
 В этом примере метод <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> не принимает параметры и не возвращает значение.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define a Database object variable by supplying the parent server and the database name arguments in the constructor.   
Database db;   
db = new Database(srv, "Test_SMO_Database");   
//Call the Create method to create the database on the instance of SQL Server.   
db.Create();   
```  
  
 }  
  
## <a name="using-an-smo-method-with-a-parameter-in-visual-basic"></a>Использование метода SMO с параметром на языке Visual Basic  
 <xref:Microsoft.SqlServer.Management.Smo.Table> Объект имеет метод под названием <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>. Этому методу требуется числовой параметр, задающий `FillFactor`.  
  
```  
Dim srv As Server  
srv = New Server  
Dim tb As Table  
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources")  
tb.RebuildIndexes(70)  
```  
  
## <a name="using-an-smo-method-with-a-parameter-in-visual-c"></a>Использование метода SMO с параметром на языке Visual C#  
 <xref:Microsoft.SqlServer.Management.Smo.Table> Объект имеет метод под названием <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>. Этому методу требуется числовой параметр, задающий `FillFactor`.  
  
```  
{   
Server srv = default(Server);   
srv = new Server();   
Table tb = default(Table);   
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources");   
tb.RebuildIndexes(70);   
}   
```  
  
## <a name="using-an-enumeration-method-that-returns-a-datatable-object-in-visual-basic"></a>Использование метода перечисления, который возвращает объект DataTable, на языке Visual Basic  
 В этом разделе описывается способ вызова метода перечисления и способ обработки данных в возвращаемом <xref:System.Data.DataTable> объекта.  
  
 Метод <xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> возвращает объект <xref:System.Data.DataTable>, который требует дальнейшего перехода для доступа ко всем имеющимся сведениям о параметрах сортировки в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
'Connect to the local, default instance of SQL Server.  
Dim srv As Server  
srv = New Server  
'Call the EnumCollations method and return collation information to DataTable variable.  
Dim d As DataTable  
'Select the returned data into an array of DataRow.  
d = srv.EnumCollations  
'Iterate through the rows and display collation details for the instance of SQL Server.  
Dim r As DataRow  
Dim c As DataColumn  
For Each r In d.Rows  
    Console.WriteLine("==")  
    For Each c In r.Table.Columns  
        Console.WriteLine(c.ColumnName + " = " + r(c).ToString)  
    Next  
Next  
```  
  
## <a name="using-an-enumeration-method-that-returns-a-datatable-object-in-visual-c"></a>Использование метода перечисления, который возвращает объект DataTable, на языке Visual C#  
 В этом разделе описывается способ вызова метода перечисления и способ обработки данных в возвращаемом <xref:System.Data.DataTable> объекта.  
  
 <xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> Метод возвращает системный <xref:System.Data.DataTable> объекта. <xref:System.Data.DataTable> Объект требует дальнейшего перехода для доступа ко все сведения о доступных параметрах сортировки об экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Call the EnumCollations method and return collation information to DataTable variable.   
DataTable d = default(DataTable);   
//Select the returned data into an array of DataRow.   
d = srv.EnumCollations;   
//Iterate through the rows and display collation details for the instance of SQL Server.   
DataRow r = default(DataRow);   
DataColumn c = default(DataColumn);   
foreach ( r in d.Rows) {   
  Console.WriteLine("=========");   
  foreach ( c in r.Table.Columns) {   
    Console.WriteLine(c.ColumnName + " = " + r(c).ToString);   
  }   
}   
}   
```  
  
## <a name="constructing-an-object-in-visual-basic"></a>Создание объекта на языке Visual Basic  
 Конструктор любого объекта можно вызвать с помощью оператора `New`. Конструктор объектов <xref:Microsoft.SqlServer.Management.Smo.Database> перегружен, и версия конструктора объектов <xref:Microsoft.SqlServer.Management.Smo.Database>, приведенная в этом образце, принимает два параметра: родительский объект <xref:Microsoft.SqlServer.Management.Smo.Server>, которому принадлежит база данных, и строку, представляющую имя новой базы данных.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods4](SMO How to#SMO_VBMethods4)]  -->  
  
## <a name="constructing-an-object-in-visual-c"></a>Создание объекта на языке Visual C#  
 Конструктор любого объекта можно вызвать с помощью оператора `New`. Конструктор объектов <xref:Microsoft.SqlServer.Management.Smo.Database> перегружен, и версия конструктора объектов <xref:Microsoft.SqlServer.Management.Smo.Database>, приведенная в этом образце, принимает два параметра: родительский объект <xref:Microsoft.SqlServer.Management.Smo.Server>, которому принадлежит база данных, и строку, представляющую имя новой базы данных.  
  
```  
{   
Server srv;   
srv = new Server();   
Table tb;   
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources");   
tb.RebuildIndexes(70);   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Declare and define a Database object by supplying the parent server and the database name arguments in the constructor.   
Database d;   
d = new Database(srv, "Test_SMO_Database");   
//Create the database on the instance of SQL Server.   
d.Create();   
Console.WriteLine(d.Name);   
}  
```  
  
## <a name="copying-an-smo-object-in-visual-basic"></a>Копирование объекта SMO на языке Visual Basic  
 Данный пример кода использует <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> метод, чтобы создать копию <xref:Microsoft.SqlServer.Management.Smo.Server> объекта. <xref:Microsoft.SqlServer.Management.Smo.Server> Представляет подключение к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VCMethods6](SMO How to#SMO_VCMethods6)]  -->  
  
## <a name="copying-an-smo-object-in-visual-c"></a>Копирование объекта SMO на языке Visual C#  
 Данный пример кода использует <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> метод, чтобы создать копию <xref:Microsoft.SqlServer.Management.Smo.Server> объекта. <xref:Microsoft.SqlServer.Management.Smo.Server> Представляет подключение к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv1;   
srv1 = new Server();   
//Modify the default database and the timeout period for the connection.   
srv1.ConnectionContext.DatabaseName = "AdventureWorks2012";   
srv1.ConnectionContext.ConnectTimeout = 30;   
//Make a second connection using a copy of the ConnectionContext property and verify settings.   
Server srv2;   
srv2 = new Server(srv1.ConnectionContext.Copy);   
Console.WriteLine(srv2.ConnectionContext.ConnectTimeout.ToString);   
}  
```  
  
## <a name="monitoring-server-processes-in-visual-basic"></a>Наблюдение за процессами сервера на языке Visual Basic  
 Можно получить текущий тип сведения о состоянии об экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] через методы перечисления. В этом примере кода метод <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> используется для получения сведений о текущих процессах. В нем также показана работа со столбцами и строками в возвращаемом объекте <xref:System.Data.DataTable>.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods5](SMO How to#SMO_VBMethods5)]  -->  
  
## <a name="monitoring-server-processes-in-visual-c"></a>Наблюдение за процессами сервера на языке Visual C#  
 Можно получить текущий тип сведения о состоянии об экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] через методы перечисления. В этом примере кода метод <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> используется для получения сведений о текущих процессах. В нем также показана работа со столбцами и строками в возвращаемом объекте <xref:System.Data.DataTable>.  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Call the EnumCollations method and return collation information to DataTable variable.   
DataTable d = default(DataTable);   
//Select the returned data into an array of DataRow.   
d = srv.EnumProcesses;   
//Iterate through the rows and display collation details for the instance of SQL Server.   
DataRow r = default(DataRow);   
DataColumn c = default(DataColumn);   
foreach ( r in d.Rows) {   
  Console.WriteLine("=====");   
  foreach ( c in r.Table.Columns) {   
    Console.WriteLine(c.ColumnName + " = " + r(c).ToString);   
  }   
}   
}   
```  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  