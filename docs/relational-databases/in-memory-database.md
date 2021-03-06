---
title: Функции и технологии систем баз данных в памяти
ms.date: 10/30/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- in-memory systems
- in-memory technologies
- in-memory features
- database, in-memory database
- system, in-memory system
- features, in-memory features
- in-memory
ms.assetid: 11f8017e-5bc3-4bab-8060-c16282cfbac1
author: briancarrig
ms.author: brcarrig
manager: amitban
ms.openlocfilehash: df8bb9e603d5455a2e42393df4c40956000cb037
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "76831595"
---
# <a name="in-memory-database-systems-and-technologies"></a>Системы и технологии баз данных в памяти

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Это справочная страница по функциям и технологиям систем баз данных в памяти в SQL Server. Понятие системы баз данных в памяти означает систему, предназначенную для использования преимуществ большего объема памяти, доступного для современных баз данных. База данных в памяти по своей природе может быть реляционной или нереляционной.

Предполагается, что производительность системы баз данных, находящихся в памяти, в основном повышается за счет ускорения (достигающего нескольких порядков) доступа к данным, находящимся в памяти, по сравнению с данными, которые находятся даже в самой быстрой дисковой подсистеме по своей природе. Многие рабочие нагрузки SQL Server, однако, позволяют разместить весь рабочий набор в доступной памяти. Многие системы баз данных в памяти могут сохранять данные на диск и не всегда могут разместить весь набор данных в доступной памяти.

Быстрый непостоянный кэш, который стоит перед существенно медленным, но постоянным носителем, превалирует среди рабочих нагрузок реляционных баз данных. Это требует определенного подхода к управлению рабочей нагрузкой. Возможности, представленные более быстрой передачей данных в памяти, большей емкостью или даже энергонезависимой памятью, упрощают разработку новых функций и технологий, которые позволят найти новые подходы к управлению рабочей нагрузкой реляционной базы данных.

## <a name="hybrid-buffer-pool"></a>Гибридный буферный пул

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[Гибридный буферный пул](../database-engine/configure-windows/hybrid-buffer-pool.md) расширяет буферный пул для файлов базы данных, размещенных на устройствах хранения энергонезависимой памяти с байтовой адресацией для платформ Windows и Linux с [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

## <a name="memory-optimized-tempdb-metadata"></a>Оптимизированные для памяти метаданные `tempdb`

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] появилась новая функция — [оптимизированные для памяти метаданные tempdb](./databases/tempdb-database.md#memory-optimized-tempdb-metadata), которая эффективно устраняет некоторые узкие места состязаний и открывает новый уровень масштабируемости для рабочих нагрузок, активно использующих tempdb.

## <a name="in-memory-oltp"></a>Выполняющаяся в памяти OLTP

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[Выполняющаяся в памяти OLTP](./in-memory-oltp/in-memory-oltp-in-memory-optimization.md) — технология баз данных, доступная в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDS](../includes/sssds-md.md)] и предназначенная для оптимизации производительности обработки транзакций, приема и загрузки данных, а также сценариев с временными данными.

## <a name="configuring-persistent-memory-support-for-linux"></a>Настройка поддержки энергонезависимой памяти для Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В статье [!INCLUDE[sqlv15](../includes/sssqlv15-md.md)] описано, как настроить энергонезависимую память (PMEM) с помощью служебной программы `ndctl` [энергонезависимая память](../linux/sql-server-linux-configure-pmem.md).

## <a name="persisted-log-buffer"></a>Буфер сохраненного журнала

В пакете обновления 1 (SP1) [!INCLUDE[ssSQL16](../includes/sssql16-md.md)] появилась оптимизация производительности для ресурсоемких операций записи, которые вызывались ожиданием WRITELOG. Энергонезависимая память используется для хранения буфера журнала. Этот небольшой буфер (20 МБ на одну пользовательскую базу данных) должен быть записан на диск, чтобы транзакции, записываемые в журнал транзакций, были зафиксированы. Для ресурсоемких рабочих нагрузок OLTP такой механизм записи на диск может стать узким местом. При хранении буфера журнала в энергонезависимой памяти уменьшается количество операций, необходимых для фиксации журнала, что позволяет повысить общую скорость транзакций и производительность рабочей нагрузки. Этот процесс был введен для [кэширования заключительного фрагмента журнала]( https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/). Однако выяснилось, что существует конфликт с [резервными копиями заключительного фрагмента журнала](./backup-restore/tail-log-backups-sql-server.md) и традиционным пониманием того, что заключительный фрагмент журнала транзакций — это его зафиксированная, но не зарезервированная часть. Так как официальное название функции — буфер сохраненного журнала, это имя используется здесь.

См. статью [Добавление буфера сохраненного журнала в базу данных](./databases/add-persisted-log-buffer.md).
