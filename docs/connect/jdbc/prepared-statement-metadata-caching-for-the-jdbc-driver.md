---
title: Кэширование метаданных подготовленной инструкции для JDBC Driver | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8918be02b5dbb0e6decf49bc315b0ebd8c83e369
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923768"
---
# <a name="prepared-statement-metadata-caching-for-the-jdbc-driver"></a>Кэширование метаданных подготовленной инструкции для JDBC Driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этой статье содержатся сведения об этих двух изменениях, реализованных для повышения производительности драйвера.

## <a name="batching-of-unprepare-for-prepared-statements"></a>Пакетная обработка аннулирования подготовленных инструкций
Начиная с версии 6.1.6-preview, повышение производительности реализовано за счет минимизации круговых путей к SQL Server. Ранее для каждого запроса prepareStatement также отправлялся вызов аннулирования. Теперь драйвер выполняет пакетную обработку запросов вплоть до порогового значения ServerPreparedStatementDiscardThreshold, которое по умолчанию равно 10.

> [!NOTE]  
>  Пользователи могут изменить значение по умолчанию с помощью следующего метода: setServerPreparedStatementDiscardThreshold(int value).

Еще одно изменение, представленное в версии 6.1.6-preview, заключается в том, что драйвер всегда вызывает хранимую процедуру sp_prepexec. Теперь для первого выполнения подготовленной инструкции драйвер вызывает хранимую процедуру sp_executesql, а в остальных случаях он выполняет процедуру sp_prepexec и назначает ей обработчик. Дополнительные сведения можно найти [здесь](https://github.com/Microsoft/mssql-jdbc/wiki/PreparedStatement-metadata-caching).

> [!NOTE]  
>  Пользователи могут изменить поведение по умолчанию в предыдущих версиях, которые всегда вызывают процедуру sp_prepexec, установив для параметра enablePrepareOnFirstPreparedStatementCall значение **true** с помощью следующего метода: setEnablePrepareOnFirstPreparedStatementCall(boolean value).

### <a name="list-of-the-new-apis-introduced-with-this-change-for-batching-of-unprepare-for-prepared-statements"></a>Список представленных в этом изменении новых API-интерфейсов для пакетной обработки аннулирования подготовленных инструкций

 **SQLServerConnection**
 
|Новый метод|Description|  
|-----------|-----------------|  
|int getDiscardedServerPreparedStatementCount()|Возвращает количество невыполненных на текущий момент действий отмены подготовки для подготовленных инструкции.|
|void closeUnreferencedPreparedStatementHandles()|Вызывает принудительное выполнение всех запросов отмены подготовки для необработанных и отброшенных подготовленных инструкций.|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|Возвращает поведение для конкретного экземпляра подключения. Если значение равно false, первое выполнение вызывает процедуру sp_executesql и не подготавливает инструкцию, а второе выполнение вызывает процедуру sp_prepexec и фактически настраивает обработчик подготовленной инструкции. Следующие выполнения вызывают хранимую процедуру sp_execute. Это избавляет от необходимости аннулировать закрываемую подготовленную инструкцию вызовом sp_unprepare, если эта инструкция выполнялась лишь один раз. Значение по умолчанию для этого параметра можно изменить, вызвав setDefaultEnablePrepareOnFirstPreparedStatementCall().|
|void setEnablePrepareOnFirstPreparedStatementCall(boolean value)|Указывает поведение для конкретного экземпляра соединения. Если значение равно false, первое выполнение вызывает sp_executesql и не подготавливает инструкцию, а второе выполнение вызывает sp_prepexec и фактически настраивает обработчик подготовленной инструкции. Следующие выполнения вызывают хранимую процедуру sp_execute. Это избавляет от необходимости аннулировать закрываемую подготовленную инструкцию вызовом sp_unprepare, если эта инструкция выполнялась лишь один раз.|
|int getServerPreparedStatementDiscardThreshold()|Возвращает поведение для конкретного экземпляра подключения. Этот параметр определяет, сколько невыполненных операций отмены для подготовленных инструкций (sp_unprepare) допускается для каждого соединения, прежде чем на сервере будет выполнен вызов очистки необработанных дескрипторов. Если этот параметр имеет значение не более 1, то действия аннулирования выполняются немедленно после завершения подготовленной инструкции. Если задано значение {@literal >} 1, эти вызовы объединяются в пакет, чтобы снизить накладные расходы на частый вызов sp_unprepare. Значение по умолчанию для этого параметра можно изменить, вызывая метод getDefaultServerPreparedStatementDiscardThreshold().|
|void setServerPreparedStatementDiscardThreshold(int value)|Указывает поведение для конкретного экземпляра соединения. Этот параметр определяет, сколько невыполненных операций отмены для подготовленных инструкций (sp_unprepare) допускается для каждого соединения, прежде чем на сервере будет выполнен вызов очистки необработанных дескрипторов. Если этот параметр имеет значение <= 1, то действия аннулирования выполняются немедленно после завершения подготовленной инструкции. Если задано значение > 1, эти вызовы объединяются в пакет, чтобы снизить накладные расходы на частый вызов sp_unprepare.|

 **SQLServerDataSource**
 
|Новый метод|Description|  
|-----------|-----------------|  
|void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall)|Если значение равно false, первое выполнение подготовленной инструкции вызовет sp_executesql без подготовки инструкции, а после второго выполнения будет вызвана процедура sp_prepexec и фактически настроен обработчик подготовленной инструкции. Следующие выполнения вызывают хранимую процедуру sp_execute. Это избавляет от необходимости аннулировать закрываемую подготовленную инструкцию вызовом sp_unprepare, если эта инструкция выполнялась лишь один раз.|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|Если значение равно false, первое выполнение подготовленной инструкции вызовет sp_executesql без подготовки инструкции, а после второго выполнения будет вызвана процедура sp_prepexec и фактически настроен обработчик подготовленной инструкции. Следующие выполнения вызывают хранимую процедуру sp_execute. Это избавляет от необходимости аннулировать закрываемую подготовленную инструкцию вызовом sp_unprepare, если эта инструкция выполнялась лишь один раз.|
|void setServerPreparedStatementDiscardThreshold(int serverPreparedStatementDiscardThreshold)|Этот параметр определяет, сколько невыполненных операций отмены для подготовленных инструкций (sp_unprepare) допускается для каждого соединения, прежде чем на сервере будет выполнен вызов очистки необработанных дескрипторов. Если этот параметр имеет значение <= 1, то действия аннулирования выполняются немедленно после завершения подготовленной инструкции. Если задано значение {@literal >} 1, эти вызовы объединяются в пакет, чтобы снизить накладные расходы на частый вызов sp_unprepare.|
|int getServerPreparedStatementDiscardThreshold()|Этот параметр определяет, сколько невыполненных операций отмены для подготовленных инструкций (sp_unprepare) допускается для каждого соединения, прежде чем на сервере будет выполнен вызов очистки необработанных дескрипторов. Если этот параметр имеет значение <= 1, то действия аннулирования выполняются немедленно после завершения подготовленной инструкции. Если задано значение {@literal >} 1, такие вызовы объединяются в пакет, чтобы снизить накладные расходы на частый вызов sp_unprepare.|

## <a name="prepared-statement-metatada-caching"></a>Кэширование метаданных подготовленных инструкций
Начиная с версии 6.3.0-preview, драйвер Microsoft JDBC Driver for SQL Server поддерживает кэширование подготовленных инструкций. До версии 6.3.0-preview, если выполняется запрос, который уже был подготовлен и сохранен в кэше, повторный вызов того же запроса не приведет к его подготовке. Теперь драйвер ищет запрос в кэше, находит обработчик и выполняет запрос с помощью sp_execute.
Кэширование метаданных подготовленных инструкций **отключено** по умолчанию. Чтобы включить его, необходимо вызвать следующий метод для объекта подключения:

`setStatementPoolingCacheSize(int value)   //value is the desired cache size (any value bigger than 0)`
`setDisableStatementPooling(boolean value) //false allows the caching to take place`

Например: `connection.setStatementPoolingCacheSize(10)`
`connection.setDisableStatementPooling(false)`

### <a name="list-of-the-new-apis-introduced-with-this-change-for-prepared-statement-metadata-caching"></a>Список представленных в этом изменении новых API-интерфейсов для кэширования метаданных подготовленных инструкций

 **SQLServerConnection**
 
|Новый метод|Description|  
|-----------|-----------------|  
|void setDisableStatementPooling(boolean value)|Задает значение true или false для параметра создания пула инструкций.|
|boolean getDisableStatementPooling()|Возвращает значение true, если создание пула инструкций отключено.|
|void setStatementPoolingCacheSize(int value)|Задает размер кэша подготовленных инструкций для этого подключения. Значение меньше 1 означает отсутствие кэша.|
|int getStatementPoolingCacheSize()|Возвращает размер кэша подготовленных инструкций для этого подключения. Значение меньше 1 означает отсутствие кэша.|
|int getStatementHandleCacheEntryCount()|Возвращает текущее число обработчиков подготовленных инструкций в составе пула.|
|boolean isPreparedStatementCachingEnabled()|Возвращает сведения о том, включено ли создание пула инструкций для этого подключения.|

 **SQLServerDataSource**
 
|Новый метод|Description|  
|-----------|-----------------|  
|void setDisableStatementPooling(boolean disableStatementPooling)|Задает значение true или false для параметра создания пула инструкций.|
|boolean getDisableStatementPooling()|Возвращает значение true, если создание пула инструкций отключено.|
|void setStatementPoolingCacheSize(int statementPoolingCacheSize)|Задает размер кэша подготовленных инструкций для этого подключения. Значение меньше 1 означает отсутствие кэша.|
|int getStatementPoolingCacheSize()|Возвращает размер кэша подготовленных инструкций для этого подключения. Значение меньше 1 означает отсутствие кэша.|

## <a name="see-also"></a>См. также раздел  
 [Повышение производительности и надежности с помощью JDBC Driver](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
