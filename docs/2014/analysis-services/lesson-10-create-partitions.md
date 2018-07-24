---
title: 'Занятие 11: Создание секций | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8e2f9ab8d98ae4ffbb8be67c4b64f5022b0f7f8e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261376"
---
# <a name="lesson-11-create-partitions"></a>Занятие 11. Создание секций
  На этом занятии мы создадим секции для разделения таблицы интернет-продаж на более мелкие логические части, которые могут быть обработаны (обновлены) независимо от других секций. По умолчанию каждая таблица, включенная в модель, имеет одну секцию, включающую все столбцы и строки таблицы. Для таблицы интернет-продаж нам необходимо разделить данные по годам — по одной секции на каждые пять лет.  После этого каждую секцию можно обработать независимо. Дополнительные сведения см. в разделе [Секции (табличные службы SSAS)](tabular-models/partitions-ssas-tabular.md).  
  
 Предполагаемое время выполнения этого занятия: **15 минут**  
  
## <a name="prerequisites"></a>предварительные требования  
 Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Прежде чем выполнять задания в этом занятии, необходимо завершить предыдущее занятие: [Занятие 10. Создание иерархий](lesson-9-create-hierarchies.md).  
  
## <a name="create-partitions"></a>Создание секций  
  
#### <a name="to-create-partitions-in-the-internet-sales-table"></a>Создание секций в таблице интернет-продаж  
  
1.  В конструкторе моделей щелкните таблицу **Интернет-продажи** , а затем откройте меню **Таблица** и выберите пункт **Секции**.  
  
     Откроется диалоговое окно **Диспетчер секций** .  
  
2.  В **диспетчер секций** отображаемое в диалоговом окне **секций**, нажмите кнопку **Интернет-продажи** секции.  
  
3.  В **имя секции**, измените имя на `Internet Sales 2005`.  
  
    > [!TIP]  
    >  Прежде чем переходить к следующему шагу, обратите внимание, что имена столбцов в окне «Предварительный просмотр таблицы» отображают столбцы, включенные в таблицу модели (которая отмечена флажком) с именами столбцов из источника. Это происходит, потому что окно «Предварительный просмотр таблицы» отображает столбцы из исходной таблицы, а не из таблицы модели.  
  
4.  Нажмите кнопку **Редактор запросов** чуть выше в правой части окна предварительного просмотра.  
  
     Поскольку необходимо, чтобы секция включала только строки из определенного периода, используйте предложение WHERE. Предложение WHERE можно создать только с помощью инструкции SQL.  
  
5.  В поле **Инструкция SQL** замените существующую инструкцию, вставив следующее:  
  
    ```  
    SELECT   
    [dbo].[FactInternetSales].[ProductKey],  
    [dbo].[FactInternetSales].[CustomerKey],  
    [dbo].[FactInternetSales].[PromotionKey],  
    [dbo].[FactInternetSales].[CurrencyKey],  
    [dbo].[FactInternetSales].[SalesTerritoryKey],  
    [dbo].[FactInternetSales].[SalesOrderNumber],  
    [dbo].[FactInternetSales].[SalesOrderLineNumber],  
    [dbo].[FactInternetSales].[RevisionNumber],  
    [dbo].[FactInternetSales].[OrderQuantity],  
    [dbo].[FactInternetSales].[UnitPrice],  
    [dbo].[FactInternetSales].[ExtendedAmount],  
    [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
    [dbo].[FactInternetSales].[DiscountAmount],  
    [dbo].[FactInternetSales].[ProductStandardCost],  
    [dbo].[FactInternetSales].[TotalProductCost],  
    [dbo].[FactInternetSales].[SalesAmount],  
    [dbo].[FactInternetSales].[TaxAmt],  
    [dbo].[FactInternetSales].[Freight],  
    [dbo].[FactInternetSales].[CarrierTrackingNumber],  
    [dbo].[FactInternetSales].[CustomerPONumber],  
    [dbo].[FactInternetSales].[OrderDate],  
    [dbo].[FactInternetSales].[DueDate],  
    [dbo].[FactInternetSales].[ShipDate]   
    FROM [dbo].[FactInternetSales]  
    WHERE (([OrderDate] >= N'2005-01-01 00:00:00') AND ([OrderDate] < N'2006-01-01 00:00:00'))  
    ```  
  
     Эта инструкция указывает, что секция должна включать все данные из строк, в которых OrderDate относится к календарному 2005 году, согласно предложению WHERE.  
  
6.  Нажмите кнопку **Проверить**.  
  
     Обратите внимание на предупреждение о том, что некоторые столбцы не присутствуют в источнике. Это обусловлено в [занятия 3: переименование столбцов](rename-columns.md), переименовать эти столбцы в таблице Интернет-продаж в модели, чтобы отличаться от тех же столбцов в источнике.  
  
#### <a name="to-create-a-partition-for-the-2006-year-in-the-internet-sales-table"></a>Создание секции для 2006 года в таблице продаж через Интернет  
  
1.  В **диспетчер секций** отображаемое в диалоговом окне **секций**, нажмите кнопку `Internet Sales 2005` секции, вы только что создали, а затем **копирования**.  
  
2.  В **имя секции**, тип `Internet Sales 2006`.  
  
3.  В инструкции SQL, для того чтобы секция включала только строки для 2006 года, замените предложение WHERE следующим:  
  
    ```  
    WHERE (([OrderDate] >= N'2006-01-01 00:00:00') AND ([OrderDate] < N'2007-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2007-year-in-the-internet-sales-table"></a>Создание секции для 2007 года в таблице продаж через Интернет  
  
1.  В диалоговом окне **Диспетчер секций** выберите команду **Копировать**.  
  
2.  В **имя секции**, тип `Internet Sales 2007`.  
  
3.  В **переключиться в**выберите **редактора запросов**.  
  
4.  В инструкции SQL, для того чтобы секция включала только строки для 2007 года, замените предложение WHERE следующим:  
  
    ```  
    WHERE (([OrderDate] >= N'2007-01-01 00:00:00') AND ([OrderDate] < N'2008-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2008-year-in-the-internet-sales-table"></a>Чтобы создать раздел за 2008 год в таблице Интернет-продаж  
  
1.  В диалоговом окне **Диспетчер секций** выберите команду **Создать**.  
  
2.  В **имя секции**, тип `Internet Sales 2008`.  
  
3.  В **переключиться в**выберите **редактора запросов**.  
  
4.  В инструкции SQL, для того чтобы секция включала только строки за 2008 год, замените предложение WHERE следующим:  
  
    ```  
    WHERE (([OrderDate] >= N'2008-01-01 00:00:00') AND ([OrderDate] < N'2009-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2009-year-in-the-internet-sales-table"></a>Создание секции для 2009 года в таблице «Интернет-продажи»  
  
1.  В диалоговом окне **Диспетчер секций** выберите команду **Создать**.  
  
2.  В **имя секции**, тип `Internet Sales 2009`.  
  
3.  В **переключиться в**выберите **редактора запросов**.  
  
4.  Для того чтобы секция включала только строки для 2009 года, замените предложение WHERE в инструкции SQL на следующее:  
  
    ```  
    WHERE (([OrderDate] >= N'2009-01-01 00:00:00') AND ([OrderDate] < N'2010-01-01 00:00:00'))  
    ```  
  
## <a name="process-partitions"></a>Обработка секций  
 В диалоговом окне **Диспетчер секций** обратите внимание на звездочку (**\***) рядом с именем каждой из только что созданных секций. Это означает, что секция не была обработана (обновлена). Во время создания новых секций нужно запустить операцию обработки секций или обработки таблиц для обновления данных в этих секциях.  
  
#### <a name="to-process-internet-sales-partitions"></a>Обработка секций интернет-продаж  
  
1.  Нажмите кнопку **OK** , чтобы закрыть диалоговое окно **Диспетчер секций** .  
  
2.  В конструкторе моделей щелкните таблицу **Интернет-продажи** , откройте меню **Модель** , наведите указатель на пункт **Обработка** (обновление) и выберите команду **Обработать секции**.  
  
3.  Убедитесь в том, что в диалоговом окне **Обработать секции** свойство **Режим** имеет значение **Обработка по умолчанию**.  
  
4.  Установите флажок в столбце **Обработка** для каждой из пяти созданных секций и нажмите кнопку **OK**.  
  
     Если появится окно для ввода учетных данных олицетворения, введите имя пользователя и пароль в системе Windows, которые были указаны в занятии 2, шаге 6.  
  
     **Процесс данных** диалоговое окно, затем появляется и отображает сведения о процессе для каждой секции. Обратите внимание, что для каждой секции передается различное количество строк. Это происходит, потому что каждая секция включает только строки для года, указанного с помощью предложения WHERE в инструкции SQL. Нет данных за 2010 год.  
  
## <a name="next-steps"></a>Следующие шаги  
 Чтобы продолжить изучение этого учебника, перейдите к следующему занятию: [Занятие 12. Создание ролей](lesson-11-create-roles.md).  
  
  