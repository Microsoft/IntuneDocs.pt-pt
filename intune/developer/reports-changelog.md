---
title: Registo de Alterações do Armazém de Dados do Intune
titleSuffix: Microsoft Intune
description: Este tópico fornece uma lista de alterações para a API de data warehouse de Microsoft Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3a1e797f1ed7b0e60d0f9550eaa9e571b8701ca4
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730236"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Registo de alterações da API do Armazém de Dados do Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Mantenha-se a par das atualizações do Armazém de Dados do Intune.

## <a name="1903-part-2"></a>1903 (parte 2)
_Lançado em abril de 2019_

### <a name="beta-changes"></a>Alterações beta

A tabela a seguir lista as coleções removidas recentes e as coleções de substituições no data warehouse do Intune.

|    Collection                          |    Alterar     |    Informações adicionais                                                                                                                                                                                                                                                                                                                                                                 |
|----------------------------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    mobileAppDeviceUserInstallStatus    |    Removidas    |    Use [mobileAppInstallStatusCounts](intune-data-warehouse-collections.md#mobileappinstallstatuscounts) em vez disso.                                                                                                                                                                                                                                                                     |
|    enrollmentTypes                     |    Removidas    |    Use [deviceEnrollmentTypes](intune-data-warehouse-collections.md#deviceenrollmenttypes) em vez disso.                                                                                                                                                                                                                                                                                      |
|    mdmStatuses                         |    Removidas    |    Use [complianceStates](intune-data-warehouse-collections.md#compliancestates) em vez disso.                                                                                                                                                                                                                                                                                               |
|    workPlaceJoinStateTypes             |    Removidas    |    Em vez `azureAdRegistered` disso, use a propriedade nas coleções [Devices](intune-data-warehouse-collections.md#devices) e [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) .                                                                                                                                                                                                             |
|    clientRegistrationStateTypes        |    Removidas    |    Use [deviceRegistrationStates](intune-data-warehouse-collections.md#deviceregistrationstates) em vez disso.                                                                                                                                                                                                                                                                             |
|    currentUser                         |    Removidas    |    Em vez disso, use a coleção [Users](intune-data-warehouse-collections.md#users) .                                                                                                                                                                                                                                                                                                      |
|    mdmDeviceInventoryHistories         |    Removidas    |    Muitas das propriedades eram redundantes ou agora podem ser encontradas nas coleções [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) ou [Devices](intune-data-warehouse-collections.md#devices) . Todas as propriedades **mdmDeviceInventoryHistories** que ainda não estiverem listadas com essas duas coleções não estarão mais disponíveis. Veja os detalhes abaixo.    |

A tabela a seguir lista as propriedades antigas encontradas anteriormente na coleção **mdmDeviceInventoryHistories** e a alteração/substituição. Todas as propriedades que estavam em **mdmDeviceInventoryHistories** , mas que não estão listadas abaixo, foram removidas.

|    Propriedade antiga                |    Alteração/substituição                                                           |
|--------------------------------|---------------------------------------------------------------------------------|
|    CellularTechnology          |    cellularTechnology na coleção de dispositivos                                     |
|    deviceClientId              |    DeviceID na coleção de dispositivos                                               |
|    deviceManufacturer          |    fabricante na coleção de dispositivos                                           |
|    deviceModel                 |    modelo na coleção de dispositivos                                                  |
|    deviceName                  |    DeviceName na coleção de dispositivos                                             |
|    deviceOsPlatform            |    deviceTypeKey na coleção de dispositivos                                          |
|    deviceOsVersion             |    osVersion na coleção devicePropertyHistories                              |
|    deviceType                  |    deviceTypeKey na coleção de dispositivos, referenciando a coleção deviceTypes    |
|    encryptionState             |    Propriedade EncryptionState na coleção Devices                           |
|    exchangeActiveSyncId        |    Propriedade easDeviceId na coleção Devices                               |
|    exchangeDeviceId            |    easDeviceId na coleção de dispositivos                                            |
|    imei                        |    IMEI na coleção de dispositivos                                                   |
|    isSupervised                |    Propriedade issupervisionada na coleção de dispositivos                              |
|    Jailbreak                  |    desbloqueado na coleção devicePropertyHistories                             |
|    meid                        |    Propriedade MEID na coleção Devices                                      |
|    OEM                         |    fabricante na coleção de dispositivos                                           |
|    osName                      |    deviceTypeKey na coleção de dispositivos, referenciando a coleção deviceTypes    |
|    phoneNumber                 |    phoneNumber na coleção de dispositivos                                            |
|    platformType                |    modelo na coleção de dispositivos                                                  |
|    product                     |    deviceTypeKey na coleção de dispositivos                                          |
|    productVersion              |    osVersion na coleção devicePropertyHistories                              |
|    serialNumber                |    serialNumber na coleção de dispositivos                                           |
|    storageFree                 |    Propriedade freeStorageSpaceInBytes na coleção Devices                   |
|    storageTotal                |    Propriedade totalStorageSpaceInBytes na coleção Devices                |
|    subscriberCarrierNetwork    |    Propriedade subscriberCarrier na coleção Devices                         |
|    wifimac                     |    wiFiMacAddress na coleção de dispositivos                                         |

A tabela a seguir lista as alterações nas propriedades encontradas na coleção [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) : 

|    Propriedade antiga                  |    Alteração/substituição                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey, fazendo referência à coleção deviceCategories       |
|    certExpirationDate            |    Removidas                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    CreatedDate                   |    enrolledDateTime na coleção de dispositivos                           |
|    deviceTypeKey                 |    deviceTypeKey na coleção de dispositivos                              |
|    easID                         |    easDeviceId na coleção de dispositivos                                |
|    enrolledByUser                |    userId na coleção de dispositivos                                     |
|    enrollmentTypeKey             |    deviceEnrollmentTypeKey na coleção de dispositivos                    |
|    graphDeviceIsCompliant        |    Removidas                                                          |
|    graphDeviceIsManaged          |    Removidas                                                          |
|    lastContact                   |    lastSyncDateTime na coleção de dispositivos                           |
|    lastContactNotification       |    Removidas                                                          |
|    lastContactWorkplaceJoin      |    Removidas                                                          |
|    lastExchangeStatusUtc         |    Removidas                                                          |
|    lastModifiedDateTimeUTC       |    Removidas                                                          |
|    lastPolicyUpdateUtc           |    Removidas                                                          |
|    ManagementAgentKey            |    managementStateKey                                               |
|    fabricante                  |    fabricante na coleção de dispositivos                               |
|    mdmStatusKey                  |    complianceStateKey, fazendo referência à coleção complianceStates    |
|    modelo                         |    modelo na coleção de dispositivos                                      |
|    osFamily                      |    conjunto de operatingSystem na coleção de dispositivos                            |
|    osRevisionNumber              |    osVersion na coleção de dispositivos                                  |
|    processorArchitecture         |    Removidas                                                          |
|    referenceId                   |    azureAdDeviceId na coleção de dispositivos                            |
|    serialNumber                  |    serialNumber na coleção de dispositivos                               |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

A tabela a seguir lista as alterações nas propriedades encontradas na coleção de [dispositivos](intune-data-warehouse-collections.md#devices) : 

|    Propriedade antiga                  |    Alteração/substituição                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey, fazendo referência à coleção deviceCategories       |
|    certExpirationDate            |    Removidas                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    CreatedDate                   |    enrolledDateTime                                                 |
|    easId                         |    easDeviceId                                                      |
|    enrolledByUser                |    userId                                                           |
|    enrollmentTypeKey             |    deviceEnrollmentTypeKey                                          |
|    graphDeviceIsCompliant        |    Removidas                                                          |
|    graphDeviceIsManaged          |    Removidas                                                          |
|    lastContact                   |    lastSyncDateTime                                                 |
|    lastContactNotification       |    Removidas                                                          |
|    lastContactWorkplaceJoin      |    Removidas                                                          |
|    lastExchangeStatusUtc         |    Removidas                                                          |
|    lastPolicyUpdateUtc           |    Removidas                                                          |
|    mdmStatusKey                  |    complianceStateKey, fazendo referência à coleção complianceStates    |
|    osFamily                      |    operatingSystem                                                  |
|    processorArchitecture         |    Removidas                                                          |
|    referenceId                   |    azureAdDeviceId                                                  |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

A tabela a seguir lista as alterações nas propriedades encontradas na coleção [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities) : 

|    Propriedade antiga         |    Alteração/substituição         |
|-------------------------|-------------------------------|
|    enrollmentTypeKey    |    deviceEnrollmentTypeKey    |

A tabela a seguir lista as alterações nas propriedades encontradas na coleção [mamApplications](intune-data-warehouse-collections.md#mamapplications) : 

|    Propriedade antiga       |    Alteração/substituição    |
|-----------------------|--------------------------|
|    ApplicationKey     |    mamApplicationKey     |
|    applicationName    |    mamApplicationName    |
|    applicationId      |    mamApplicationId      |

A tabela a seguir lista as alterações nas propriedades encontradas na coleção [mamApplicationInstances](intune-data-warehouse-collections.md#mamapplicationinstances) : 

|    Propriedade antiga     |    Alteração/substituição    |
|---------------------|--------------------------|
|    applicationId    |    mamApplicationId      |
|    deviceId         |    mamDeviceId           |
|    deviceType       |    mamDeviceType         |
|    deviceName       |    mamDeviceName         |

A tabela a seguir lista as alterações nas propriedades encontradas na coleção [mamCheckins](intune-data-warehouse-collections.md#mamcheckins) : 

|    Propriedade antiga      |    Alteração/substituição    |
|----------------------|--------------------------|
|    ApplicationKey    |    mamApplicationKey     |

A tabela a seguir lista as alterações nas propriedades encontradas na coleção de [usuários](intune-data-warehouse-collections.md#users) : 

|    Propriedade antiga             |    Alteração/substituição    |
|-----------------------------|--------------------------|
|    startDateInclusiveUtc    |    Removidas               |
|    endDateInclusiveUtc      |    Removidas               |
|    IsCurrent                |    Removidas               |

## <a name="1903"></a>1903
_Lançado em março de 2019_

### <a name="v10-changes-reflecting-back-to-beta"></a>V 1.0 alterações que refletem de volta para beta
Quando o V 1.0 foi introduzido pela primeira vez em 1808, ele difere de algumas maneiras significativas da API beta. Em 1903, essas alterações serão refletidas de volta para a versão da API beta. Se você tiver relatórios importantes que usam a versão da API beta, é altamente recomendável trocar esses relatórios para V 1.0 para evitar alterações significativas. Consulte [as informações de versão da API](../reports-api-url.md) para obter mais informações sobre versões de api do data warehouse e compatibilidade retroativa. 

## <a name="1902"></a>1902 
_Lançado em fevereiro de 2019_

### <a name="power-bi-compliance-app"></a>Aplicativo de conformidade Power BI 

Acesse suas data warehouse do Intune no Power BI online usando o aplicativo de [conformidade do Intune (data warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) . Com este Power BI aplicativo, agora você pode acessar e compartilhar relatórios pré-criados sem nenhuma configuração e sem sair do navegador da Web. 

> [!NOTE]
> Há dois filtros adicionais que você pode aplicar ao aplicativo de conformidade do Intune.

#### <a name="add-additional-filters-to-the-intune-compliance-app"></a>Adicionar filtros adicionais ao aplicativo de conformidade do Intune
1. Abra o aplicativo de [conformidade do Intune (data warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) em seus navegadores da Web.
2. Clique em **dispositivos sem conformidade** e selecione **não compatível** no filtro **complianceStatus** . 
3. Clique em **dispositivos desconhecidos** e selecione **ainda não disponível** no filtro **complianceStatus** . 

## <a name="1812"></a>1812 
_Lançado em dezembro de 2018_

### <a name="enrollment-activities-collection-released-to-v10"></a>Coleta de atividades de registro liberada para v 1.0 

A coleção de atividades de registro agora está disponível em v 1.0. Você pode usar essa coleção para entender o volume de falha de registro e as tendências em seu ambiente. Para obter mais informações, consulte [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities), [enrollmentEventStatuses](intune-data-warehouse-collections.md#enrollmenteventstatuses), [enrollmentFailureCategories](intune-data-warehouse-collections.md#enrollmentfailurecategories)e [enrollmentFailureReasons](intune-data-warehouse-collections.md#enrollmentfailurereasons).

## <a name="1808"></a>1808
_Lançada em agosto de 2018_

### <a name="v10-collections"></a>Coleções v1.0  

Agora, pode utilizar a versão v1.0 do Armazém de Dados do Intune, ao definir o parâmetro de consulta `api-version=v1.0`. As atualizações para coleções no Armazém de Dados são acumulativas por natureza e não interrompem cenários existentes.

### <a name="enrollment-activities-collection-released-to-beta"></a>Coleta de atividades de registro liberada para beta

A nova coleção `Enrollment Activities` é lançada para beta. Pode utilizar esta coleção para entender como a inscrição está a decorrer ao visualizar as falhas mais comuns. 


## <a name="1805"></a>1805
_Lançado em maio de 2018_

### <a name="correction-to-device-count-in-devices-collection"></a>Correção na contagem de dispositivos na coleção **Dispositivos** 

Foi feita uma correção à coleção **Dispositivos** que pode diminuir o número total de dispositivos que filtram pelo atributo `isDeleted`. Esta lista é um resultado da correção e não é um erro. Para mais informações sobre a coleção **Dispositivos**, veja [Referência para entidades de dispositivos](reports-ref-devices.md). 


## <a name="1801"></a>1801
_Lançada em janeiro de 2018_

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>Autenticação apenas com a aplicação do Armazém de Dados do Intune <!-- 1867540 -->

Pode configurar uma aplicação com o Azure Active Directory (Azure AD) e autenticar para o Armazém de Dados do Intune. Para obter mais informações, veja [Autenticação apenas com a aplicação do Armazém de Dados do Intune](data-warehouse-app-only-auth.md).

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Requisitos de credenciais do Azure AD e do Intune <!-- 2077525 -->

- Já não é necessário atribuir uma licença do Intune ao utilizador ao aceder ao Armazém de Dados do Intune (incluindo a API).
- O nome da função do Intune foi alterado de **Relatórios** para **Armazém de dados do Intune**. 

    Para obter mais informações, veja [Requisitos de credenciais do Azure AD e do Intune](reports-api-url.md#azure-ad-and-intune-credential-requirements).

### <a name="odata-query-options----2077711---"></a>Opções de consulta de OData <!-- 2077711 -->

Pode utilizar <code>$select</code> como um parâmetro de consulta de OData. A versão atual suporta os seguintes parâmetros de consulta de OData: <code>$filter</code>, <code>$orderby</code>, <code>$select</code>, <code>$skip</code> e <code>$top</code>. Para obter mais informações, veja [Opções de consulta de OData](reports-api-url.md#odata-query-options).

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>Novas entidades no modelo de dados no data warehouse <!-- 2077804 -->

- A entidade [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md) foi adicionada. A entidade **MobileAppDeviceUserInstallStatus** representa um estado de instalação da aplicação móvel de um determinado dispositivo e utilizador.
- A entidade, [**MobileAppInstallStates**](reports-ref-application.md#mobileappinstallstates), foi adicionada. A entidade **MobileAppInstallState** representa o estado de instalação de uma aplicação móvel depois de ser atribuída a um grupo que contém dispositivos, utilizadores ou ambos. 

## <a name="1710"></a>1710
_Lançado em novembro de 2017_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>A nova coleção de entidades denominada Utilizador Atual está limitada aos dados dos utilizadores atualmente ativos <!-- 1544273 -->

A coleção de entidades **Utilizadores** contém todos os utilizadores do Azure Active Directory (Azure AD) com licenças atribuídas na empresa. Estes registos incluem estados do utilizador durante o período de recolha dos dados, mesmo que o utilizador tenha sido removido. Por exemplo, um utilizador pode ser adicionado ao Intune e, em seguida, removido no decorrer do mês anterior. Apesar de este utilizador não estar presente no momento do relatório, o utilizador e o estado estão presentes nos dados. Pode criar um relatório que mostrará a duração da presença no histórico do utilizador nos seus dados.

Em contrapartida, a nova coleção de entidades **Utilizador Atual** contém apenas os utilizadores que não foram removidos. A coleção de entidades **Utilizador Atual** contém apenas os utilizadores atualmente ativos. Para obter informações sobre a coleção de entidades **Utilizador Atual**, veja [Reference for current user entity (Referência para a entidade utilizador atual)](../reports-ref-current-user.md).

## <a name="1709"></a>1709
_Lançamento em outubro de 2017_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Coleção de entidades de associação de dispositivo de usuário adicionada ao Intune data warehouse modelo de dados <!-- 1187917 -->

Agora pode criar relatórios e visualizações de dados com as informações de associação de dispositivos do utilizador que associam o utilizador às coleções de dispositivos de entidades. Pode aceder ao modelo de dados através do ficheiro do Power BI (PBIX) obtido na página do Intune do Armazém de Dados, através do ponto final do OData ou ao desenvolver um cliente personalizado. Para obter mais informações, veja a [Associação de Dispositivos do Utilizador](reports-ref-user-device.md).

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>Novas entidades no modelo de dados no data warehouse <!-- 1479526 --><!-- -->

- A entidade [**UserDeviceAssociation**](reports-ref-user-device.md) foi adicionada. A entidade **UserDeviceAssociation** contém associações de dispositivos do utilizador na sua organização. Agora pode criar relatórios e visualizações de dados com as informações de associação de dispositivos do utilizador que associam o utilizador às coleções de dispositivos de entidades.  
- A entidade [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md) foi adicionada. **IntuneManagementExtension** contém entidades para dispositivos móveis que controlam informações como o estado da versão e da instalação.

## <a name="next-steps"></a>Passos seguintes
- Saiba mais sobre [as novidades todas as semanas no Intune](../fundamentals/whats-new.md). Também pode descobrir quais são as alterações futuras, os avisos importantes sobre o serviço e as informações sobre versões anteriores.
- Leia o [Blogue do Microsoft Intune](https://go.microsoft.com/fwlink/?LinkID=273882).
