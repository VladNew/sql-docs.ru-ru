---
title: Подключение к источнику данных (клиент интеллектуального анализа данных для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections
ms.assetid: 548672ce-e403-4aca-b67a-c2c797f053dd
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5e750ec50aff2d4d69b90a974b28ddb77c54b068
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163605"
---
# <a name="connect-to-source-data-data-mining-client-for-excel"></a>Подключение к источнику данных (клиент интеллектуального анализа данных для Excel)
  В этом разделе описано, как создавать и использовать новые соединения, используемые для хранения моделей интеллектуального анализа данных, а также для доступа к внешним данным, хранящимся в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 **Подключения интеллектуального анализа данных.** Созданное при запуске надстроек первоначальное соединение используется для доступа к алгоритмам, анализа данных и сохранения моделей и структур интеллектуального анализа данных.  
  
 Требуется подключение к экземпляру [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] для использования средств визуализации и моделирования в надстройках, поскольку надстройки зависят от алгоритмов и структур данных, предоставляемых службами [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 **Соединения с внешними источниками данных.** Можно также создавать подключения к внешним источникам данных при построении моделей или сохранении результатов. Например, можно создать модель интеллектуального анализа данных на одном сервере, а затем выполнить прогнозирующий запрос к этой модели интеллектуального анализа данных, используя данные, хранимые на другом экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], в таблице Excel или во внешнем источнике данных, таком как [!INCLUDE[msCoName](../includes/msconame-md.md)] Access. Каждый раз при обращении к новому источнику данных будет появляться диалоговое окно с предложением создать соединение.  
  
##  <a name="bkmk_prereq2"></a> Предварительные требования  
 Эта версия надстройки требует, чтобы ваш экземпляр [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] был на основе SQL Server 2012. Если требуется подключиться к более ранней версии служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], имеется отдельная версия этих надстроек. Существуют версии надстроек, которые поддерживают SQL Server 2005, SQL Server 2008 и SQL Server 2008 R2.  
  
 Чтобы установить соединение с базой данных [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], необходимо наличие разрешений на доступ к серверу баз данных. Кроме того, необходимо включить сеансы интеллектуального анализа данных и иметь разрешения на чтение или чтение и запись объектов базы данных, сохраненных на сервере.  
  
##  <a name="bkmk_connect"></a> Создание подключения к серверу интеллектуального анализа данных  
 **Подключений** группе в клиенте интеллектуального анализа данных для Excel и средств анализа таблиц для Excel предоставляет средства для управления соединениями с экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   Можно создать соединение при установке надстройки или добавить его позже.  
  
-   Можно создать несколько соединений и менять их в любое время, кроме случаев, когда запущен процесс создания или отправки запросов к модели.  
  
     Не изменяйте и не закрывайте подключение во время обработки модели интеллектуального анализа данных. Модель интеллектуального анализа данных может потерять данные или стать непригодной для использования.  
  
-   Только одно соединение может быть активно одновременно.  
  
### <a name="connections-in-the-excel-add-ins"></a>Соединения в надстройках Excel  
 **Подключений** группе в клиенте интеллектуального анализа данных для Excel и средств анализа таблиц для Excel — управления соединениями с экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
##### <a name="create-a-new-server-connection-in-the-excel-add-ins"></a>Создание нового соединения с сервером в надстройках Excel  
  
1.  Нажмите кнопку **подключения** кнопку **анализ** или **интеллектуального анализа данных** ленты.  
  
    > [!NOTE]  
    >  Надпись на кнопке указывает наличие соединения. Если нет соединение будет установлено на листе, кнопка содержит текст "\<нет соединения >.» Если соединение было предварительно установлено в книге, на кнопке появляется его имя.  
  
2.  В **соединения со службами Analysis Services** диалоговом окне щелкните **New**.  
  
3.  В **нового соединения служб Analysis Services** диалогового окна введите имя сервера.  
  
4.  Выберите метод проверки подлинности.  
  
5.  Выберите базу данных из **имя каталога** стрелку раскрывающегося списка. Если база данных не существует на экземпляре, выберите **(по умолчанию)**.  
  
6.  Введите понятное имя для соединения.  
  
7.  Нажмите кнопку **проверить подключение** Чтобы проверить доступность сервера и базы данных.  
  
8.  Нажмите кнопку **ОК**, затем кнопку **Закрыть**.  
  
### <a name="connections-using-a-web-service"></a>Соединения с использованием веб-службы  
 При использовании архитектуры тонкого клиента, разрешающей просмотр кубов и данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], можно также настроить соединение с сервером служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] с помощью веб-служб. Дополнительные сведения об определении веб-клиента см. в электронной документации по [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 При наличии доступа к серверу, настроенному для веб-служб, тип соединения можно указать при первом создании соединения.  
  
##### <a name="create-an-http-connection-to-analysis-services"></a>Создание HTTP-соединения со службами Analysis Services  
  
1.  Откройте **нового соединения служб Analysis Services** диалоговое окно.  
  
2.  В качестве имени введите http:// и URL-адрес сервера служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
3.  Введите имя пользователя и пароль, необходимые для доступа к веб-службе.  
  
### <a name="connections-in-the-visio-add-in"></a>Соединения в надстройке Visio  
 В отличие от Excel, программа Visio не содержит ленты средств и кнопок, специально предназначенных для создания и наблюдения за соединением. Вместо этого подключение к данным создается при первоначальном выборе фигуры интеллектуального анализа данных и перетаскивании ее на страницу Visio. Мастер предложит выбрать модель для фигуры и задать другие параметры.  
  
 Если ранее использовались соединения с источниками данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в Excel, эти соединения будут перечислены в списке источников данных для выбора.  
  
##### <a name="create-a-connection-for-a-visio-shape"></a>Создание соединения для фигуры Visio  
  
1.  Откройте шаблон интеллектуального анализа данных и выберите одну из фигур интеллектуального анализа данных.  
  
2.  Перетащите эту фигуру на пустую страницу.  
  
3.  В **выбрать источник данных** диалоговом окне выберите источник из списка данных, или нажмите кнопку **New**.  
  
4.  При выборе **New**, выполните процедуру, описанную ранее для указания сервера и имя каталога или для подключения через веб-службу.  
  
##  <a name="bkmk_change"></a> Изменение подключений  
 Можно создать несколько соединений на одном листе, но одновременно может быть активно только одно соединение. Имя текущего соединения отображается в **подключения** кнопки.  
  
 В клиенте интеллектуального анализа данных для Excel, можно также проверить строку соединения и состояние текущего соединения, нажав кнопку **трассировки** и выбрав **текущего соединения**.  
  
#### <a name="use-a-different-server-connection"></a>Используйте другое соединение с сервером  
  
1.  Нажмите кнопку **подключения**.  
  
2.  В **соединения со службами Analysis Services** области, выберите соединение из **другие соединения** списке и нажмите кнопку **сделать текущей**.  
  
3.  Нажмите кнопку **проверить подключение** чтобы убедиться, что соединение доступно.  
  
 После завершения обработки модели интеллектуального анализа данных результаты сохраняются на локальном компьютере и на них не повлияет завершение соединения с одним сервером и подключение к другому. Однако надо избегать смены или завершения соединения во время обработки модели интеллектуального анализа данных, так как это может повредить данные.  
  
#### <a name="modify-an-existing-server-connection"></a>Изменение существующего соединения с сервером.  
  
1.  Нельзя изменить существующее соединение. Если необходимо подключиться к другой базе данных или к другому серверу, необходимо создать новое соединение.  
  
2.  Если необходимо изменить строку подключения, чтобы увеличить время ожидания запроса или добавить другие параметры, относящиеся к экземпляру [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], одно из возможных решений — изменить DMC-файл, в котором хранится строка подключения.  
  
     \<диск: > \Users\\< myusername\>\AppData\Local\Microsoft\Data Mining Add-in  
  
##  <a name="bkmk_extconnections"></a> Подключение к внешним источникам данных  
 В то время как средства в **анализ** ленте работают только с данными в Excel, средства в **интеллектуального анализа данных** ленты позволяют подключаться непосредственно к внешним источникам данных для использования в качестве входных данных для модели, или выборка.  
  
 Следующие средства в этих надстройках поддерживают использование внешних данных для интеллектуального анализа.  
  
-   [Образец данных &#40;надстройки интеллектуального анализа данных SQL Server&#41;](sample-data-sql-server-data-mining-add-ins.md)  
  
-   [Мастер классификации &#40;интеллектуального анализа данных надстройки для Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Мастер оценки &#40;интеллектуального анализа данных надстройки для Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Мастер кластеризации &#40;интеллектуального анализа данных надстройки для Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Мастер прогнозов &#40;интеллектуального анализа данных надстройки для Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Создание структуры интеллектуального анализа данных &#40;надстройки интеллектуального анализа данных SQL Server&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
-   [Диаграмма точности &#40;надстройки интеллектуального анализа данных SQL Server&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
-   [Диаграмма роста прибыли &#40;надстройки интеллектуального анализа данных SQL Server&#41;](profit-chart-sql-server-data-mining-add-ins.md)  
  
-   [Матрица классификации &#40;надстройки интеллектуального анализа данных SQL Server&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
  
### <a name="using-analysis-services-as-a-data-source"></a>Использование служб Analysis Services в качестве источника данных  
 Нельзя напрямую получать доступ к данным, сохраненным в кубе или в табличной модели [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Вместо этого создайте соединение в Excel с сервером [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и используйте данные для создания модели.  
  
### <a name="relational-data-sources"></a>Реляционные источники данных  
 Если нужно использовать данные из реляционного источника в качестве вводных данных для модели, можно подключиться к следующим версиям SQL Server:  
  
-   SQL Server 2008  
  
-   SQL Server 2008 R2  
  
-   SQL Server 2012  
  
 Также можно получить данные из любого реляционного источника данных, которые поддерживается в качестве источника данных в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Сведения о поддерживаемых источниках данных см. в разделе [источников данных в многомерных моделях](multidimensional-models/data-sources-in-multidimensional-models.md)  
  
 Обратите внимание, что следующие типы данных нельзя использовать для интеллектуального анализа данных. При включении этих данных в процесс создания модели возникнет ошибка.  
  
-   ntext  
  
-   BINARY  
  
## <a name="see-also"></a>См. также  
 [Трассировки &#40;клиент интеллектуального анализа данных для Excel&#41;](trace-data-mining-client-for-excel.md)  
  
  