---
title: Аналитические функции (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 60fbff84-673b-48ea-9254-6ecdad20e7fe
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 643bd6ffc4fb44319e3e7f4c59ffaa76213cd868
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832208"
---
# <a name="analytic-functions-transact-sql"></a>Функции аналитики (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

SQL Server поддерживает указанные ниже аналитические функции:
  
|||  
|-|-|  
|[CUME_DIST &#40; Transact-SQL &#41;](../../t-sql/functions/cume-dist-transact-sql.md)|[LEAD &#40; Transact-SQL &#41;](../../t-sql/functions/lead-transact-sql.md)|  
|[FIRST_VALUE (Transact-SQL)](../../t-sql/functions/first-value-transact-sql.md)|[PERCENTILE_CONT (Transact-SQL)](../../t-sql/functions/percentile-cont-transact-sql.md)|  
|[LAG &#40;Transact-SQL&#41;](../../t-sql/functions/lag-transact-sql.md)|[PERCENTILE_DISC (Transact-SQL)](../../t-sql/functions/percentile-disc-transact-sql.md)|  
|[LAST_VALUE (Transact-SQL)](../../t-sql/functions/last-value-transact-sql.md)|[PERCENT_RANK (Transact-SQL)](../../t-sql/functions/percent-rank-transact-sql.md)|  
  
Аналитические функции вычисляют статистическое значение на основе группы строк. В отличие от агрегатных функций, аналитические функции могут возвращать несколько строк для каждой группы. Аналитические функции можно использовать для вычисления скользящих средних, промежуточных итогов, процентных долей или первых N результатов в группе.
 
## <a name="see-also"></a>См. также раздел
[Предложение OVER (Transact-SQL)](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
