---
title: Выполнение распределенных транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2baaa43fdf638dcd1f6794eaa9f5cf76df424c06
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707084"
---
# <a name="performing-distributed-transactions"></a>Выполнение распределенных транзакций
  С помощью координатора распределенных транзакций (Майкрософт) (MS DTC) приложения могут распространять транзакции на два или более экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Он также позволяет приложениям участвовать в транзакциях, выполняющихся под управлением диспетчеров транзакций, которые соответствуют стандарту Open Group DTP XA.  
  
 Обычно все команды управления транзакциями отправляются на сервер через драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Приложение запускает транзакцию, вызывая [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) с отключенным режимом автоматической фиксации. Затем приложение выполняет обновления, составляющие транзакцию, и вызывает [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) с параметром SQL_COMMIT или SQL_ROLLBACK.  
  
 Однако при использовании MS DTC диспетчер транзакций координатор MS DTC перестает использовать **SQLEndTran**.  
  
 В случае прикрепления к одной распределенной транзакции, а затем ко второй драйвер ODBC Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] покидает исходную распределенную транзакцию и прикрепляется к новой транзакции. Дополнительные сведения см. в [справочнике программиста по DTC](https://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).  
  
## <a name="see-also"></a>См. также  
 [Выполнение транзакций &#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
