---
title: Referência para entidades de política
titleSuffix: Microsoft Intune
description: Tópico de referência para a categoria Policy das coleções de entidades na API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 64fc1bab596715be80fd3a91c003cac1176fe787
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490271"
---
# <a name="reference-for-policy-entities"></a>Referência para entidades de política

A categoria de **políticas** contém entidades para dispositivos móveis que rastreiam informações como:

- Inventário de perfis de configuração de dispositivos, perfis de configuração de aplicações e políticas de conformidade  
- Número de dispositivos no estado com êxito, pendente, com falhas ou com erros por dia  
- Número de utilizadores no estado com êxito, pendente, com falhas ou com erros por dia  
- Número cumulativo de dispositivos no estado com êxito, pendente, com falhas ou com erros por dia  

## <a name="policies"></a>políticas

A entidade **política** lista perfis de configuração de dispositivo, perfis de configuração de aplicativo e políticas de conformidade. Pode atribuir as políticas com a Gestão de Dispositivos Móveis (MDM) a um grupo na sua empresa.

| Propriedade  | Description | Exemplo |
|---------|------------|--------|
| policyKey |Chave exclusiva para representar a política no armazém de dados. |123 |
| policyId |Identificador exclusivo da Política no armazém de dados. |b66bc706-ffff-7437-0340-032819502773 |
| policyName |Nome da Política. |"Linha de Base do Windows 10" |
| policyVersion |Versão da Política. Quando a política é editada ou alterada, é criada uma versão mais recente. |1, 2, 3 |
| isDeleted |Indica se o registo da Política foi atualizado.  <br>True – a política tem um novo registo com campos atualizados. <br>False – o registo mais recente da política. |True/False |
| startDateInclusiveUTC |Data e hora em UTC em que a política foi criada no armazém de dados. |11/23/2016 12:00:00 AM |
| deletedDateUTC |Data e hora em UTC em que a propriedade IsDeleted foi alterada para True. |11/23/2016 12:00:00 AM |
| rowLastModifiedDateTimeUTC |Data e hora em UTC em que a política foi modificada pela última vez no armazém de dados. |11/23/2016 12:00:00 AM |

## <a name="policytypes"></a>policyTypes

A entidade **PolicyType** lista os tipos de perfis de configuração de dispositivo, perfis de configuração de aplicativo e políticas de conformidade. Pode atribuir as políticas com a Gestão de Dispositivos Móveis (MDM) a um grupo na sua empresa.

| Propriedade  | Description | Exemplo |
|---------|------------|--------|
| policyTypeId |Identificador exclusivo da política no sistema de origem. |123 |
| policyTypeKey |Identificador exclusivo da política no armazém de dados. |1 |
| policyTypeName |Nome do tipo de política. |Política de Conformidade do Windows 10. |

## <a name="device-configuration"></a>Configuração do Dispositivo

A entidade **deviceConfigurationProfileDeviceActivity** lista o número de **dispositivos** com êxito, pendente, com falha ou estado de erro por dia. O número reflete os Perfis de configuração de dispositivos atribuídos à entidade. Por exemplo, se um **dispositivo** estiver no estado de êxito para todas as suas políticas atribuídas, ele incrementará o contador bem-sucedido, um para esse dia. Se um dispositivo tiver dois perfis atribuídos, um no estado com êxito e outro num estado com erros, a entidade incrementa o contador do estado com êxito (Succeeded) e coloca o dispositivo no estado com erros. A entidade apresenta uma lista de quantos dispositivos estão em cada um dos estados num determinado dia nos últimos 30 dias.

| Propriedade  | Description | Exemplo |
|---------|------------|--------|
| dateKey |Data-chave de quando a entrada do Perfil de Configuração do Dispositivo foi registada no armazém de dados. |20160703 |
| Pendente |Número de Dispositivos exclusivos no estado pendente. |123 |
| com êxito |Número de Dispositivos exclusivos no estado com êxito. |12 |
| erro |Número de Dispositivos exclusivos no estado com erros. |10 |
| Falha ao |Número de Dispositivos exclusivos no estado com falhas. |2 |

A entidade **deviceConfigurationProfileUserActivity** lista o número de **usuários** com êxito, pendente, com falha ou estado de erro por dia. O número reflete os Perfis de configuração de dispositivos atribuídos à entidade. Por exemplo, se um **usuário** estiver no estado com êxito para todas as suas políticas atribuídas, ele moverá o contador bem-sucedido em um para esse dia. Se um utilizador tiver dois perfis atribuídos, um no estado com êxito e outro no estado com erros, é contado o utilizador no estado com erros.  A entidade **deviceConfigurationProfileUserActivity** lista quantos usuários estão em qual estado em um determinado dia nos últimos 30 dias.

| Propriedade  | Description | Exemplo |
|---------|------------|--------|
| dateKey |Data-chave de quando a entrada do Perfil de Configuração do Dispositivo foi registada no armazém de dados. |20160703 |
| Pendente |Número de Utilizadores exclusivos no estado pendente. |123 |
| com êxito |Número de Utilizadores exclusivos no estado com êxito. |12 |
| erro |Número de Utilizadores exclusivos no estado com erros. |10 |
| Falha ao |Número de Utilizadores exclusivos no estado com falhas. |2 |

## <a name="policytypeactivities"></a>policyTypeActivities

A entidade **policyTypeActivity** lista o número cumulativo de dispositivos no estado com êxito, pendente, com falha ou erro. Apresenta uma lista destes estados relativamente a um perfil de configuração de dispositivo, perfil de configuração de aplicação ou política de conformidade por dia.

| Propriedade  | Description | Exemplo |
|---------|------------|--------|
| dateKey |dateKey quando o check-in do perfil de configuração do dispositivo foi registrado no data warehouse. |20160703 |
| policyKey |policyKey, pode ser Unido com a política para obter o PolicyName. |Linha de base do Windows 10 |
| policyTypeKey |O tipo de Chave de Política pode ser acompanhado do Tipo de Política para obter o nome do tipo de política. |Política de Compatibilidade do Windows 10 |
| Pendente |Número de dispositivos exclusivos no estado pendente. |123 |
| com êxito |Número de dispositivos exclusivos no estado com êxito. |12 |
| erro |Número de dispositivos exclusivos no estado com erros. |10 |
| Falha ao |Número de dispositivos exclusivos no estado com falhas. |2 |

## <a name="compliance-policy"></a>Política de Conformidade

A Referência da API de Políticas de Conformidade contém entidades que fornecem informações de estado sobre as políticas de conformidade atribuídas a dispositivos.

### <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities

A tabela seguinte apresenta um resumo dos estados de atribuição de políticas de conformidade a dispositivos. Esta tabela indica a contagem de dispositivos detetados em cada estado de conformidade.


|Propriedade     |Description  |Exemplo  |
|---------|---------|---------|
|dateKey  |Chave da data em que o resumo da política de conformidade foi criado.|20161204 |
|Conhecidos  |Número de dispositivos que estão offline ou que não conseguiram comunicar com o Intune ou o Azure AD por outros motivos. |5|
|NotApplicable      |Número de dispositivos em que as políticas de conformidade visadas pelo administrador não são aplicáveis.|201 |
|em conformidade      |Número de dispositivos que aplicaram com êxito uma ou mais políticas de conformidade do dispositivo visadas pelo administrador. |4083 |
|InGracePeriod      |Número de dispositivos que não estão em conformidade, embora se encontrem no período de tolerância definido pelo administrador. |57|
|Não compatíveis      |Número de dispositivos que não conseguiram aplicar uma ou mais definições de políticas de conformidade do dispositivo visadas pelo administrador ou nos quais o utilizador ainda não está a cumprir as políticas visadas pelo administrador.|43 |
|erro      |Número de dispositivos que não conseguiram comunicar com o Intune ou o Azure AD e devolveram uma mensagem de erro. |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities 

A tabela seguinte apresenta um resumo dos estados de atribuição de políticas de conformidade a dispositivos por política e por tipo de política. Esta tabela indica a contagem de dispositivos detetados em cada estado de conformidade para todas as políticas de conformidade atribuídas.



|Propriedade  |Description  |Exemplo  |
|---------|---------|---------|
|dateKey  |Chave da data em que o resumo da política de conformidade foi criado.|20161219|
|policyKey     |Chave da política de conformidade para a qual o resumo foi criado. |10178 |
|policyPlatformKey      |Chave do tipo de plataforma da política de conformidade para a qual o resumo foi criado.|5|
|Conhecidos     |Número de dispositivos que estão offline ou que não conseguiram comunicar com o Intune ou o Azure AD por outros motivos.|13|
|NotApplicable     |Número de dispositivos em que as políticas de conformidade visadas pelo administrador não são aplicáveis.|3|
|em conformidade      |Número de dispositivos que aplicaram com êxito uma ou mais políticas de conformidade do dispositivo visadas pelo administrador. |45|
|InGracePeriod      |Número de dispositivos que não estão em conformidade, embora se encontrem no período de tolerância definido pelo administrador. |3|
|Não compatíveis      |Número de dispositivos que não conseguiram aplicar uma ou mais definições de políticas de conformidade do dispositivo visadas pelo administrador ou nos quais o utilizador ainda não está a cumprir as políticas visadas pelo administrador.|7|
|erro      |Número de dispositivos que não conseguiram comunicar com o Intune ou o Azure AD e devolveram uma mensagem de erro. |3|

### <a name="policyplatformtypes"></a>policyPlatformTypes

A tabela seguinte contém os tipos de plataforma de todas as políticas atribuídas. Os tipos de plataforma das políticas que nunca foram atribuídos a um dispositivo não são apresentados nesta tabela.


|Propriedade  |Description  |Exemplo  |
|---------|---------|---------|
|policyPlatformTypeKey      |A chave exclusiva do tipo de plataforma da política. |20170519 |
|policyPlatformTypeId      |O identificador exclusivo do tipo de plataforma da política.|1|
|policyPlatformTypeName      |O nome do tipo de plataforma da política.|AndroidForWork |

### <a name="policydeviceactivities"></a>policyDeviceActivities

A tabela seguinte mostra o número de dispositivos no estado com êxito, pendente, com falhas ou com erros por dia. O número apresentado reflete os perfis de dados por Tipo de Política. Por exemplo, se um dispositivo estiver no estado com êxito em todas as políticas atribuídas, o contador de casos com êxito tem um incremento de um para esse dia. Se um dispositivo tiver dois perfis atribuídos, um no estado com êxito e outro num estado com erros, a entidade incrementa o contador do estado com êxito (Succeeded) e coloca o dispositivo no estado com erros. A entidade policyDeviceActivity lista quantos dispositivos estão em qual estado em um determinado dia nos últimos 30 dias.

|Propriedade  |Description  |Exemplo  |
|---------|---------|---------|
|dateKey|Data-chave de quando a entrada do Perfil de Configuração do Dispositivo foi registada no armazém de dados.|20160703|
|Pendente|Número de Dispositivos exclusivos no estado pendente.|123|
|Succeeded|Número de Dispositivos exclusivos no estado com êxito.|12|
|policyKey|policyKey, pode ser Unido com a política para obter o PolicyName.|Linha de base do Windows 10|
|erro|Número de Dispositivos exclusivos no estado com erros.|10|
|Falha ao|Número de Dispositivos exclusivos no estado com falhas.|2|

### <a name="policyuseractivities"></a>policyUserActivities

A tabela seguinte mostra o número de utilizadores no estado com êxito, pendente, com falhas ou com erros por dia. O número apresentado reflete os perfis de dados por Tipo de Política. Por exemplo, se um utilizador estiver no estado com êxito em todas as políticas atribuídas, sobe o contador com êxito em um para esse dia. Se um utilizador tiver dois perfis atribuídos, um no estado com êxito e outro no estado com erros, é contado o utilizador no estado com erros. A entidade PolicyUserActivity apresenta uma lista de quantos utilizadores estão em cada um dos estados num determinado dia nos últimos 30 dias.


| Propriedade  |                                         Description                                         |       Exemplo       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  dateKey  | Data-chave de quando a entrada do Perfil de Configuração do Dispositivo foi registada no armazém de dados. |      20160703       |
|  Pendente  |                         Número de Dispositivos exclusivos no estado pendente.                          |         123         |
| com êxito |                         Número de Dispositivos exclusivos no estado com êxito.                          |         12          |
| policyKey |                 policyKey, pode ser Unido com a política para obter o PolicyName.                 | Linha de base do Windows 10 |
|   erro   |                          Número de Dispositivos exclusivos no estado com erros.                           |         10          |

