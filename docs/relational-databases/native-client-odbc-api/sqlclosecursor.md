---
title: SQLCloseCursor | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLCloseCursor function
ms.assetid: e7134d65-5c1c-4ae2-b119-d9b4b9a42483
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fb20bfa7ca76b8156ef2400e6db3235c590680ba
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302639"
---
# <a name="sqlclosecursor"></a>SQLCloseCursor
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **SQLCloseCursor** заменяет [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) значением *параметра* SQL_CLOSE. По получении функции **SQLCloseCursor**драйвер собственного клиента ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отбрасывает строки ожидающих результирующих наборов. Обратите внимание, что содержащиеся в инструкции привязки параметров и столбцов (если они существуют) **SQLCloseCursor**оставляет без изменений.  
  
## <a name="see-also"></a>См. также:  
 [SQLCloseCursor](https://go.microsoft.com/fwlink/?LinkId=59331)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
