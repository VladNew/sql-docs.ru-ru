---
title: Диспетчер подключений Azure Data Lake Analytics | Документация Майкрософт
description: Пакет SQL Server Integration Services (SSIS) может использовать диспетчер подключений Azure Data Lake Analytics для подключения к учетной записи Data Lake Analytics.
ms.custom: ''
ms.date: 05/18/2018
ms.prod: sql
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
author: yanancai
ms.author: yanacai
ms.reviewer: maghan
ms.openlocfilehash: fa388a47c6a7cfd4ecae15ea145ff358eb88232c
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765625"
---
# <a name="azure-data-lake-analytics-connection-manager"></a>Диспетчер подключений Azure Data Lake Analytics

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Пакет SQL Server Integration Services (SSIS) может использовать диспетчер подключений Azure Data Lake Analytics для подключения к учетной записи Data Lake Analytics с использованием одного из двух следующих типов проверки подлинности:
-   удостоверение пользователя Azure Active Directory (Azure AD);
-   удостоверение службы Azure AD. 

Диспетчер подключений Azure Data Lake Analytics включен в [пакет дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
 
## <a name="configure-the-connection-manager"></a>Настройка диспетчера подключений

1. В диалоговом окне **Добавление диспетчера подключений со службами SSIS** выберите **AzureDataLakeAnalytics** >  и щелкните **Добавить**. Откроется диалоговое окно **редактора диспетчера подключений Azure Data Lake Analytics**.
  
2. В диалоговом окне **Редактор диспетчера подключений Azure Data Lake Analytics** в поле **Имя учетной записи ADLA** введите соответствующее имя для учетной записи Data Lake Analytics. Например, myadlaaccountname.
  
3. В поле **Проверка подлинности** выберите подходящий тип проверки подлинности для получения доступа к данным в Data Lake Analytics.

   а. Если вы выбрали вариант **Удостоверение пользователя Azure AD**, сделайте следующее:
   
      i. Укажите значения в полях **Имя пользователя** и **Пароль**.    
      ii. Чтобы проверить подключение, нажмите кнопку **Проверить подключение**. Если вы или администратор клиента ранее не давали согласия на доступ к учетной записи Data Lake Analytics из SSIS,при появлении соответствующего запроса щелкните **Принять**. Дополнительные сведения о предоставлении согласия см. в разделе [Интеграция приложений с Azure Active Directory](https://docs.microsoft.com/azure/active-directory/manage-apps/plan-an-application-integration#integrating-applications-with-azure-ad).
    
   > [!NOTE] 
   > При выборе варианта проверки подлинности **Удостоверение пользователя Azure AD** многофакторная проверка подлинности и проверка подлинности учетной записи Майкрософт не поддерживаются.
    
   b. Если вы выбрали вариант **Удостоверение службы Azure AD**, сделайте следующее.
   
      i. Создайте приложение и субъект-службу Azure AD для получения доступа к учетной записи Data Lake Analytics. Дополнительные сведения об этом параметре проверки подлинности см. в разделе [Использовать портал для создания приложения и службы-участника, который имеет доступ к ресурсам Active Directory](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).    
      ii. Назначьте приложению Azure AD соответствующие разрешения на доступ к учетной записи Data Lake Analytics. Узнайте, как предоставить права доступа к учетной записи Data Lake Analytics с помощью [мастера добавления пользователей](https://docs.microsoft.com/azure/data-lake-analytics/data-lake-analytics-manage-use-portal#add-a-new-user).    
      iii. Укажите значения для полей **Идентификатор приложения**, **Ключ проверки подлинности** и **Идентификатор клиента**.    
      iv. Чтобы проверить подключение, нажмите кнопку **Проверить подключение**.  

4. Щелкните **ОК**, чтобы закрыть диалоговое окно **редактора диспетчера подключений Azure Data Lake Analytics**.  

## <a name="view-the-properties-of-the-connection-manager"></a>Просмотр свойств диспетчера подключений
Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .  
  
  
