---
title: Отсоединение базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.detachdatabase.f1
helpviewer_keywords:
- database detaching [SQL Server]
- detaching databases [SQL Server]
ms.assetid: f63d4107-13e4-4bfe-922d-5e4f712e472d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35a118575be4ac15cb44588f1773ea1bb4fbc257
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68006192"
---
# <a name="detach-a-database"></a>Отсоединение базы данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается отсоединение базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Отсоединенные файлы останутся на диске и могут быть повторно подсоединены с помощью инструкции CREATE DATABASE с параметрами FOR ATTACH или FOR ATTACH_REBUILD_LOG. Файлы можно также переместить на другой сервер и подсоединить там.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Отсоединение базы данных с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 Список ограничений см. в статье [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо членство в предопределенной роли базы данных db_owner.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-detach-a-database"></a>Отсоединение базы данных  
  
1.  В обозревателе объектов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , а затем раскройте его.  
  
2.  Раскройте список **Базы данных**и выберите имя пользовательской базы данных, которую необходимо отсоединить.  
  
3.  Щелкните правой кнопкой мыши имя базы данных, укажите пункт **Задачи**, а затем выберите команду **Отсоединить**. Появится диалоговое окно **Отсоединение базы данных** .  
  
     **Базы данных для отсоединения**  
     Перечисляет базы данных для отсоединения.  
  
     **Имя базы данных**  
     Отображает имя базы данных для отсоединения.  
  
     **Удалить соединения**  
     Завершить соединения с указанной базой данных.  
  
    > [!NOTE]  
    >  Невозможно отсоединить базу данных с активными соединениями.  
  
     **Обновить статистику**  
     По умолчанию операция отсоединения сохраняет устаревшую статистику оптимизации. Для ее обновления установите этот флажок.  
  
     **Сохранять полнотекстовые каталоги**  
     По умолчанию операция отсоединения сохраняет связанные с базой данных полнотекстовые каталоги. Для удаления этих каталогов сбросьте флажок **Сохранять полнотекстовые каталоги** . Этот параметр доступен только при обновлении базы данных с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
     **Состояние**  
     Отображает одно из следующих состояний: **Готово** или **Не готово**.  
  
     **Сообщение**  
     Столбец **Сообщение** может отображать сведения о базе данных следующим образом:  
  
    -   Если база данных участвует в репликации, то ее **Состояние** имеет значение **Не готово** , а в столбце **Сообщение** отображается строка **База данных реплицирована**.  
  
    -   Если имеется одно или несколько активных соединений с базой данных, то ее **Состояние** имеет значение **Не готово**, а в столбце **Сообщение** отображается **Активных соединений: _<число_активных_соединений>_**, например **Активных соединений: 1**. Прежде чем можно будет отсоединить базу данных, необходимо отключить активные соединений, выбрав команду **Удалить соединения**.  
  
     Чтобы получить сведения о сообщении, откройте монитор активности, щелкнув текст с гиперссылкой.  
  
4.  Если для отсоединения базы данных все готово, нажмите кнопку **ОК**.  
  
> [!NOTE]  
>  Отсоединенная база данных отображается в узле **Базы данных** обозревателя объектов до тех пор, пока не будет обновлено представление. Обновить его можно в любой момент. Щелкните область обозревателя объектов и в меню выберите пункт **Представление**, а затем пункт **Обновить**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-detach-a-database"></a>Отсоединение базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере отсоединяется база данных AdventureWorks2012 с параметром SKIPCHECKS, установленным в значение TRUE.  
  
```  
EXEC sp_detach_db 'AdventureWorks2012', 'true';  
```  
  
## <a name="see-also"></a>См. также:  
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_detach_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
  
