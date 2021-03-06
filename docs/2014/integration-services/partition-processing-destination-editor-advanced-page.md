---
title: Редактор назначения обработки секций (страница "Дополнительно") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.advanced.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 2039ee0f-069d-479d-90b2-2a12481b1162
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: de7c84a463d15e3260cc64c53ba1f82c6808dd93
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66056778"
---
# <a name="partition-processing-destination-editor-advanced-page"></a>Редактор назначения обработки секций (страница «Дополнительно»)
  Страница **Дополнительно** диалогового окна **Редактор назначения обработки секций** позволяет настроить обработку ошибок.  
  
 Дополнительные сведения о назначении для обработки секции см. в разделе [Partition Processing Destination](data-flow/partition-processing-destination.md).  
  
> [!NOTE]  
>  Описанные здесь задачи не применимы к табличным моделям служб Analysis Services.  Нельзя связать входные столбцы со столбцами секционирования для табличных моделей. Вместо этого для обработки секции следует использовать задачу выполнения DDL [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) служб Analysis Services.  
  
## <a name="options"></a>Параметры  
 **Использовать конфигурацию ошибок по умолчанию**  
 Укажите, нужно ли использовать обработку ошибок в службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] по умолчанию. По умолчанию это значение равно `True`.  
  
 **Действие при возникновении ошибки ключа**  
 Укажите способ обработки записей с недопустимыми ключевыми значениями.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**ConvertToUnknown**|Преобразовать неприемлемое значение ключа в значение Unknown.|  
|**DiscardRecord**|Удаляет запись.|  
  
 **Пропускать ошибки**  
 Указывает, что ошибки должны пропускаться.  
  
 **Остановить при возникновении ошибки**  
 Указывает, что в случае ошибки обработка должна прерываться.  
  
 **Количество ошибок**  
 Выберите порог ошибок, при достижении которого обработка должна закончиться, если выбран режим **Остановить при возникновении ошибки**.  
  
 **Действие при возникновении ошибки**  
 Если был выбран режим **Остановить при возникновении ошибки**, укажите действие, которое нужно выполнить при достижении порога ошибок.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**StopProcessing**|Останавливает обработку.|  
|**StopLogging**|Останавливает ведение журнала ошибок.|  
  
 **Ключ не найден**  
 Укажите действие при ошибке «Ключ не найден». По умолчанию, присваивается значение **Сообщить и продолжить**.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**Пропустить ошибку**|Пропустить ошибку и продолжить обработку.|  
|**Сообщить и продолжить**|Сообщить об ошибке и продолжить обработку.|  
|**Сообщить и остановиться**|Сообщить об ошибке и остановить обработку.|  
  
 **Дублирующийся ключ**  
 Указывает действие при ошибке «Повторяющийся ключ». По умолчанию, присваивается значение **Пропустить ошибку**.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**Пропустить ошибку**|Пропустить ошибку и продолжить обработку.|  
|**Сообщить и продолжить**|Сообщить об ошибке и продолжить обработку.|  
|**Сообщить и остановиться**|Сообщить об ошибке и остановить обработку.|  
  
 **Ключ NULL преобразован в неизвестный**  
 Выберите действие для ситуации, когда ключ NULL был преобразован в значение Unknown. По умолчанию, присваивается значение **Пропустить ошибку**.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**Пропустить ошибку**|Пропустить ошибку и продолжить обработку.|  
|**Сообщить и продолжить**|Сообщить об ошибке и продолжить обработку.|  
|**Сообщить и остановиться**|Сообщить об ошибке и остановить обработку.|  
  
 **Ключ NULL не разрешен**  
 Указывает действие при обнаружении ключа NULL в случае запрета ключей NULL. По умолчанию, присваивается значение **Сообщить и продолжить**.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**Пропустить ошибку**|Пропустить ошибку и продолжить обработку.|  
|**Сообщить и продолжить**|Сообщить об ошибке и продолжить обработку.|  
|**Сообщить и остановиться**|Сообщить об ошибке и остановить обработку.|  
  
 **Путь к журналу ошибок**  
 Введите путь для журнала ошибок или выберите место назначения, нажав кнопку обзора **(...)** .  
  
 **Обзор (...)**  
 Укажите путь к журналу ошибок.  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор назначения "Обработка секций" (страница "Сопоставления")](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md)  
  
  
