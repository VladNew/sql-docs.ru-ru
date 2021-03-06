---
title: sp_changemergepublication (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergepublication_TSQL
- sp_changemergepublication
helpviewer_keywords:
- sp_changemergepublication
ms.assetid: 81fe1994-7678-4852-980b-e02fedf1e796
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3cc0e6bb77c49b7eefc17e5d1f16a185834f2061
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829614"
---
# <a name="sp_changemergepublication-transact-sql"></a>sp_changemergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства публикации слиянием. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changemergepublication [ @publication= ] 'publication'  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @property = ] 'property'`Свойство, которое необходимо изменить для данной публикации. *свойство* имеет тип **sysname**и может быть одним из значений, перечисленных в следующей таблице.  
  
`[ @value = ] 'value'`Новое значение для указанного свойства. *value* имеет тип **nvarchar (255)** и может быть одним из значений, перечисленных в следующей таблице.  
  
 В данной таблице описаны свойства публикации, доступные для изменения, а также ограничения на значения этих свойств.  
  
|Свойство|Значение|Описание|  
|--------------|-----------|-----------------|  
|**allow_anonymous**|**true**|Анонимные подписки разрешены.|  
||**false**|Анонимные подписки запрещены.|  
|**allow_partition_realignment**|**true**|Операции удаления отправляются на подписчик для отражения результатов изменений секции путем удаления данных, которые больше не являются частью секции подписчика. Это поведение по умолчанию.|  
||**false**|Данные из старой секции остаются на подписчике, а изменения данных, произведенные на издателе, на этот подписчик не реплицируются. Вместо этого изменения в подписчике реплицируются на издатель. Такой метод применяется для сохранения в подписке данных из старой секции, чтобы обеспечить доступ к архивным данным.|  
|**allow_pull**|**true**|Подписки по запросу на данную публикацию разрешены.|  
||**false**|Подписки по запросу на данную публикацию не разрешены.|  
|**allow_push**|**true**|Принудительные подписки на данную публикацию разрешены.|  
||**false**|Принудительные подписки на данную публикацию не разрешены.|  
|**allow_subscriber_initiated_snapshot**|**true**|Подписчик может инициировать процесс получения моментального снимка.|  
||**false**|Подписчик не может инициировать процесс получения моментального снимка.|  
|**allow_subscription_copy**|**true**|Можно копировать базы данных, подписанные на эту публикацию.|  
||**false**|Нельзя копировать базы данных, подписанные на эту публикацию.|  
|**allow_synctoalternate**|**true**|Разрешает альтернативному участнику синхронизации выполнять синхронизацию с этим издателем.|  
||**false**|Не разрешает альтернативному участнику синхронизации выполнять синхронизацию с этим издателем.|  
|**allow_web_synchronization**|**true**|Подписки можно синхронизировать через HTTPS.|  
||**false**|Подписки нельзя синхронизировать через HTTPS.|  
|**alt_snapshot_folder**||Указывает местоположение альтернативной папки для моментального снимка.|  
|**automatic_reinitialization_policy**|**1**|Перед повторной инициализацией подписки передаются изменения из подписчика.|  
||**0**;|Перед повторной инициализацией подписки изменения из подписчика не передаются.|  
|**centralized_conflicts**|**true**|Все конфликтующие записи хранятся на издателе. После изменения этого свойства необходимо выполнить повторную инициализацию существующих подписчиков.|  
||**false**|Конфликтующие записи хранятся на сервере, который был выбран в качестве проигравшего при устранении конфликта. После изменения этого свойства необходимо выполнить повторную инициализацию существующих подписчиков.|  
|**compress_snapshot**|**true**|Моментальный снимок в альтернативной папке снимков сжимается в формате CAB. Сжатие моментального снимка в папке моментальных снимков по умолчанию невозможно. Изменение этого свойства потребует создания нового моментального снимка.|  
||**false**|По умолчанию моментальный снимок не сжимается. Изменение этого свойства потребует создания нового моментального снимка.|  
|**conflict_logging**|**publisher**|Конфликтующие записи хранятся на издателе.|  
||**абонент**|Конфликтующие записи хранятся на подписчике, вызвавшем конфликт. Не поддерживается для [!INCLUDE[ssEW](../../includes/ssew-md.md)] подписчиков *.*|  
||**как**|Конфликтующие записи хранятся одновременно на издателе и на подписчике.|  
|**conflict_retention**||Значение **типа int** , указывающее срок хранения (в днях), в течение которого сохраняются конфликты. Если задать для параметра *conflict_retention* значение **0** , очистка конфликтов не требуется.|  
|**nописание**||Описание публикации.|  
|**dynamic_filters**|**true**|Публикация фильтруется на основе динамического предложения.|  
||**false**|Публикация не фильтруется динамически.|  
|**enabled_for_internet**|**true**|Публикация через Интернет разрешена. Для передачи файлов моментальных снимков на подписчик можно использовать протокол FTP. Файлы синхронизации для публикации размещаются в каталоге «C:\Program Files\Microsoft SQL Server\MSSQL\Repldata\ftp».|  
||**false**|Публикация через Интернет не разрешена.|  
|**ftp_address**||Сетевой адрес службы FTP для распространителя. Указывает место хранения файлов моментальных снимков публикации.|  
|**ftp_login**||Пароль пользователя для подключения к службе FTP.|  
|**ftp_password**||Пароль пользователя для подключения к службе FTP.|  
|**ftp_port**||Номер порта службы FTP для распространителя. Указывает номер порта TCP FTP-сайта, на котором хранятся файлы моментальных снимков публикации.|  
|**ftp_subdirectory**||Указывает, где создаются файлы моментальных снимков, если публикация поддерживает распространение моментальных снимков по протоколу FTP.|  
|**generation_leveling_threshold**|**int**|Задает число изменений, которые содержатся в поколении. Поколение — это набор изменений, переданных издателю или подписчику.|  
|**keep_partition_changes**|**true**|Синхронизация оптимизирована и влияет только на подписчиков, чьи строки принадлежат измененным секциям. Изменение этого свойства потребует создания нового моментального снимка.|  
||**false**|Синхронизация не оптимизирована, и при изменении данных в секции проверяются секции, переданные на подписчики. Изменение этого свойства потребует создания нового моментального снимка.|  
|**max_concurrent_merge**||Это **целое число,** представляющее максимальное количество одновременных процессов слияния, которые могут выполняться для публикации. Если это значение равно 0, то число процессов неограниченно. Если на одно и то же время запланировано большее число процессов слияния, то лишние задания помещаются в очередь и ожидают завершения текущих.|  
|**max_concurrent_dynamic_snapshots**||Это **целое число,** представляющее максимальное количество сеансов моментальных снимков для создания моментального снимка отфильтрованных данных, который может одновременно выполняться в публикации слиянием, использующей параметризованные фильтры строк. Если значение **равно 0**, ограничение отсутствует. Если на одно и то же время запланировано выполнение большего числа процессов создания моментальных снимков, то лишние задания помещаются в очередь и ожидают завершения текущих.|  
|**post_snapshot_script**||Задает указатель на расположение файла **SQL** . Агент распространителя или агент слияния выполняет заключительный скрипт создания моментального снимка после того, как скрипты и данные всех реплицируемых объектов используются во время начальной синхронизации. Изменение этого свойства потребует создания нового моментального снимка.|  
|**pre_snapshot_script**||Задает указатель на расположение файла **SQL** . Агент слияния выполняет предварительный скрипт моментального снимка до выполнения скриптов реплицируемых объектов, если моментальный снимок делается для подписчика. Изменение этого свойства потребует создания нового моментального снимка.|  
|**publication_compatibility_level**|**100RTM**|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
||**90RTM**|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|  
|**publish_to_activedirectory**|**true**|Этот аргумент устарел и поддерживается только для обратной совместимости скриптов. Сведения о публикации больше не могут быть добавлены в Active Directory.|  
||**false**|Удаляет сведения о публикации из службы Active Directory.|  
|**replicate_ddl**|**1**|Производится репликация инструкций DDL, выполняемых на издателе.|  
||**0**;|Репликация инструкций DDL не производится.|  
|**хранения**||Это целое **число,** представляющее количество единиц *retention_period_unit* , для которых необходимо сохранить изменения для данной публикации. Если подписка не синхронизирована в течение срока хранения, а ожидающие обработки изменения, которые были бы получены, удалены операцией очистки на стороне распространителя, срок действия подписки истекает, и подписка должна быть создана заново. Максимальный допустимый срок хранения равен числу дней между 31 декабря 9999 года и текущей датой.<br /><br /> Примечание. срок хранения для публикаций слиянием составляет 24-часовой льготный период для размещения подписчиков в разных часовых поясах.|  
|**retention_period_unit**|**day**|Срок хранения указан в днях.|  
||**week**|Срок хранения указан в неделях.|  
||**month**|Срок хранения указан в месяцах.|  
||**year**|Срок хранения указан в годах.|  
|**snapshot_in_defaultfolder**|**true**|Файлы моментального снимка сохранены в папке для моментальных снимков по умолчанию.|  
||**false**|Файлы моментальных снимков хранятся в альтернативном расположении, заданном *alt_snapshot_folder*. Такое сочетание позволяет размещать файлы моментальных снимков одновременно и в каталоге по умолчанию, и в альтернативном каталоге.|  
|**snapshot_ready**|**true**|Моментальный снимок доступен для публикации.|  
||**false**|Моментальный снимок для публикации не доступен.|  
|**status**|**active**|Публикация находится в активном состоянии.|  
||**Активный**|Публикация находится в неактивном состоянии.|  
|**sync_mode**|**native** или<br /><br /> **машинный код bcp**|Для исходного моментального снимка используются результаты вывода всех таблиц в собственном режиме программы массового копирования.|  
||**символов**<br /><br /> или **символ bcp**|Для исходного моментального снимка используются результаты вывода всех таблиц в символьном режиме программы массового копирования, что требуется подписчикам, отличным от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**use_partition_groups**<br /><br /> Примечание. После использования partition_groups, если вы хотите вернуться к использованию **сетупбелонгс**и установить **use_partition_groups = false** в **чанжемержеартикле**, это может быть неправильно отражено после создания моментального снимка. Триггеры, формируемые моментальным снимком, совместимы с группами секций.<br /><br /> Чтобы решить эту проблему, можно установить состояние неактивно, изменить **use_partition_groups**, а затем задать для параметра Состояние значение активно.|**true**|Публикация использует предварительно вычисляемые секции.|  
||**false**|Публикация не использует предварительно вычисляемые секции.|  
|**validate_subscriber_info**||Содержит список функций для получения сведений о подписчике. Затем проверяет условие динамического фильтра, которое используется для подписчика при проверке правильности секционирования данных.|  
|**web_synchronization_url**||Значение по умолчанию URL-адреса в Интернете для веб-синхронизации.|  
|NULL (по умолчанию)||Возвращает список поддерживаемых значений для *Свойства*.|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Подтверждает, что действие, выполняемое этой хранимой процедурой, может сделать недействительным существующий моментальный снимок. *force_invalidate_snapshot* является **битом**и имеет значение по умолчанию **0**.  
  
 **0** указывает, что изменение публикации не сделает моментальный снимок недействительным. Если хранимая процедура определяет, что изменение требует создания нового моментального снимка, возникает ошибка и изменения не выполняются.  
  
 значение **1** указывает, что изменение публикации может инввалидате моментальный снимок. Если существуют подписки, которым требуется новый моментальный снимок, то это значение дает разрешение пометить существующий моментальный снимок как устаревший и сформировать новый.  
  
 Сведения о свойствах, которые при их изменении требуют создания нового моментального снимка, см. в разделе «Примечания».  
  
`[ @force_reinit_subscription = ] force_reinit_subscription`Подтверждает, что действие, выполняемое этой хранимой процедурой, может потребовать повторной инициализации существующих подписок. *force_reinit_subscription* является **битом** со значением по умолчанию **0**.  
  
 значение **0** указывает, что изменение публикации не требует повторной инициализации подписок. Если хранимая процедура определяет, что изменения потребуют повторной инициализации подписок, возникает ошибка, и изменения не выполняются.  
  
 **1** указывает, что изменение публикации приводит к повторной инициализации существующих подписок и предоставляет разрешение на повторную инициализацию подписки.  
  
 Свойства, которые при изменении потребуют повторной инициализации всех текущих подписок, см. в разделе «Примечания».  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_changemergepublication** используется в репликации слиянием.  
  
 Изменение следующих свойств требует создания нового моментального снимка. Для параметра *force_invalidate_snapshot* необходимо указать значение **1** .  
  
-   **alt_snapshot_folder**  
  
-   **compress_snapshot**  
  
-   **dynamic_filters**  
  
-   **ftp_address**  
  
-   **ftp_login**  
  
-   **ftp_password**  
  
-   **ftp_port**  
  
-   **ftp_subdirectory**  
  
-   **post_snapshot_script**  
  
-   **publication_compatibility_level** (только для **80SP3** )  
  
-   **pre_snapshot_script**  
  
-   **snapshot_in_defaultfolder**  
  
-   **sync_mode**  
  
-   **use_partition_groups**  
  
 Изменение этих свойств потребует повторной инициализации существующих подписок. Для параметра *force_reinit_subscription* необходимо указать значение **1** .  
  
-   **dynamic_filters**  
  
-   **validate_subscriber_info**  
  
 Чтобы составить список объектов публикации для Active Directory с помощью *publish_to_active_directory*, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объект уже должен быть создан в Active Directory.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_changemergepublication](../../relational-databases/replication/codesnippet/tsql/sp-changemergepublicatio_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_changemergepublication**.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_dropmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
