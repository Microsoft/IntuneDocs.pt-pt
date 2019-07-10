---
title: Referência para as entidades de políticas
titleSuffix: Microsoft Intune
description: Tópico de referência para a categoria Policy das coleções de entidades na API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4f66cc3a10711b137e081fab98445d73108748a9
ms.sourcegitcommit: 63b55e81122e5c15893302b109ae137c30855b55
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67713163"
---
# <a name="reference-for-policy-entities"></a>Referência para as entidades de políticas

A categoria **Policy** contém entidades para dispositivos móveis que registam informações como:

  - Inventário de perfis de configuração de dispositivos, perfis de configuração de aplicações e políticas de conformidade  
  - Número de dispositivos no estado com êxito, pendente, com falhas ou com erros por dia  
  - Número de utilizadores no estado com êxito, pendente, com falhas ou com erros por dia  
  - Número cumulativo de dispositivos no estado com êxito, pendente, com falhas ou com erros por dia  

## <a name="policy"></a>Policy

A entidade **Policy** apresenta uma lista de perfis de configuração de dispositivos, perfis de configuração de aplicações e políticas de conformidade. Pode atribuir as políticas com a Gestão de Dispositivos Móveis (MDM) a um grupo na sua empresa.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| PolicyKey |Chave exclusiva para representar a política no armazém de dados. |123 |
| PolicyId |Identificador exclusivo da Política no armazém de dados. |b66bc706-ffff-7437-0340-032819502773 |
| PolicyName |Nome da Política. |"Linha de Base do Windows 10" |
| PolicyVersion |Versão da Política. Quando a política é editada ou alterada, é criada uma versão mais recente. |1, 2, 3 |
| IsDeleted |Indica se o registo da Política foi atualizado.  <br>True – a política tem um novo registo com campos atualizados. <br>False – o registo mais recente da política. |True/False |
| StartDateInclusiveUTC |Data e hora em UTC em que a política foi criada no armazém de dados. |11/23/2016 12:00:00 AM |
| DeletedDateUTC |Data e hora em UTC em que a propriedade IsDeleted foi alterada para True. |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Data e hora em UTC em que a política foi modificada pela última vez no armazém de dados. |11/23/2016 12:00:00 AM |

## <a name="policytype"></a>PolicyType

A entidade **PolicyType** apresenta uma lista dos tipos de perfis de configuração de dispositivos, perfis de configuração de aplicações e políticas de conformidade. Pode atribuir as políticas com a Gestão de Dispositivos Móveis (MDM) a um grupo na sua empresa.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| PolicyTypeId |Identificador exclusivo da política no sistema de origem. |123 |
| PolicyTypeKey |Identificador exclusivo da política no armazém de dados. |1 |
| PolicyTypeName |Nome do tipo de política. |Política de Conformidade do Windows 10. |

## <a name="deviceconfiguration"></a>DeviceConfiguration

O **DeviceConfigurationProfileDeviceActivity** entidade apresenta uma lista o número de **dispositivos** com êxito, pendente, com falhas ou Estado com erros por dia. O número reflete os Perfis de configuração de dispositivos atribuídos à entidade. Por exemplo, se um **dispositivo** está no Estado com êxito para todas as políticas atribuídas, ele incrementa o contador com êxito um para esse dia. Se um dispositivo tiver dois perfis atribuídos, um no estado com êxito e outro num estado com erros, a entidade incrementa o contador do estado com êxito (Succeeded) e coloca o dispositivo no estado com erros. A entidade apresenta uma lista de quantos dispositivos estão em cada um dos estados num determinado dia nos últimos 30 dias.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| DateKey |Data-chave de quando a entrada do Perfil de Configuração do Dispositivo foi registada no armazém de dados. |20160703 |
| Pendente |Número de Dispositivos exclusivos no estado pendente. |123 |
| Succeeded |Número de Dispositivos exclusivos no estado com êxito. |12 |
| Erro |Número de Dispositivos exclusivos no estado com erros. |10 |
| Falhou |Número de Dispositivos exclusivos no estado com falhas. |2 |

O **DeviceConfigurationProfileUserActivity** entidade apresenta uma lista o número de **utilizadores** com êxito, pendente, com falhas ou Estado com erros por dia. O número reflete os Perfis de configuração de dispositivos atribuídos à entidade. Por exemplo, se um **utilizador** está no Estado com êxito para todas as políticas atribuídas, sobe o contador com êxito por um para esse dia. Se um utilizador tiver dois perfis atribuídos, um no estado com êxito e outro no estado com erros, é contado o utilizador no estado com erros.  A entidade **DeviceConfigurationProfileUserActivity** apresenta uma lista de quantos utilizadores estão em que estado num determinado dia nos últimos 30 dias.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| DateKey |Data-chave de quando a entrada do Perfil de Configuração do Dispositivo foi registada no armazém de dados. |20160703 |
| Pendente |Número de Utilizadores exclusivos no estado pendente. |123 |
| Succeeded |Número de Utilizadores exclusivos no estado com êxito. |12 |
| Erro |Número de Utilizadores exclusivos no estado com erros. |10 |
| Falhou |Número de Utilizadores exclusivos no estado com falhas. |2 |

## <a name="policytypeactivity"></a>PolicyTypeActivity

A entidade **PolicyTypeActivity** apresenta uma lista do número cumulativo de dispositivos no estado com êxito, pendente, com falhas ou com erros por dia. Apresenta uma lista destes estados relativamente a um perfil de configuração de dispositivo, perfil de configuração de aplicação ou política de conformidade por dia.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| DateKey |Data-chave de quando a entrada do Perfil de configuração do dispositivo foi registada no armazém de dados. |20160703 |
| PolicyKey |A chave de política pode ser acompanhada pela Política para obter o policyName. |Linha de base do Windows 10 |
| PolicyTypeKey |O tipo de Chave de Política pode ser acompanhado do Tipo de Política para obter o nome do tipo de política. |Política de Compatibilidade do Windows 10 |
| Pendente |Número de dispositivos exclusivos no estado pendente. |123 |
| Succeeded |Número de dispositivos exclusivos no estado com êxito. |12 |
| Erro |Número de dispositivos exclusivos no estado com erros. |10 |
| Falhou |Número de dispositivos exclusivos no estado com falhas. |2 |

## <a name="compliance-policy"></a>Política de Conformidade

A Referência da API de Políticas de Conformidade contém entidades que fornecem informações de estado sobre as políticas de conformidade atribuídas a dispositivos.

### <a name="compliancepolicystatusdeviceactivities"></a>CompliancePolicyStatusDeviceActivities

A tabela seguinte apresenta um resumo dos estados de atribuição de políticas de conformidade a dispositivos. Esta tabela indica a contagem de dispositivos detetados em cada estado de conformidade.


|Propriedade     |Descrição  |Exemplo  |
|---------|---------|---------|
|DateKey  |Chave da data em que o resumo da política de conformidade foi criado.|20161204 |
|Unknown  |Número de dispositivos que estão offline ou que não conseguiram comunicar com o Intune ou o Azure AD por outros motivos. |5|
|NotApplicable      |Número de dispositivos em que as políticas de conformidade visadas pelo administrador não são aplicáveis.|201 |
|Compatível      |Número de dispositivos que aplicaram com êxito uma ou mais políticas de conformidade do dispositivo visadas pelo administrador. |4083 |
|InGracePeriod      |Número de dispositivos que não estão em conformidade, embora se encontrem no período de tolerância definido pelo administrador. |57|
|NonCompliant      |Número de dispositivos que não conseguiram aplicar uma ou mais definições de políticas de conformidade do dispositivo visadas pelo administrador ou nos quais o utilizador ainda não está a cumprir as políticas visadas pelo administrador.|43 |
|Erro      |Número de dispositivos que não conseguiram comunicar com o Intune ou o Azure AD e devolveram uma mensagem de erro. |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>CompliancePolicyStatusDevicePerPolicyActivities 

A tabela seguinte apresenta um resumo dos estados de atribuição de políticas de conformidade a dispositivos por política e por tipo de política. Esta tabela indica a contagem de dispositivos detetados em cada estado de conformidade para todas as políticas de conformidade atribuídas.



|Propriedade  |Descrição  |Exemplo  |
|---------|---------|---------|
|DateKey  |Chave da data em que o resumo da política de conformidade foi criado.|20161219|
|PolicyKey     |Chave da política de conformidade para a qual o resumo foi criado. |10178 |
|PolicyPlatformKey      |Chave do tipo de plataforma da política de conformidade para a qual o resumo foi criado.|5|
|Unknown     |Número de dispositivos que estão offline ou que não conseguiram comunicar com o Intune ou o Azure AD por outros motivos.|13|
|NotApplicable     |Número de dispositivos em que as políticas de conformidade visadas pelo administrador não são aplicáveis.|3|
|Compatível      |Número de dispositivos que aplicaram com êxito uma ou mais políticas de conformidade do dispositivo visadas pelo administrador. |45|
|InGracePeriod      |Número de dispositivos que não estão em conformidade, embora se encontrem no período de tolerância definido pelo administrador. |3|
|NonCompliant      |Número de dispositivos que não conseguiram aplicar uma ou mais definições de políticas de conformidade do dispositivo visadas pelo administrador ou nos quais o utilizador ainda não está a cumprir as políticas visadas pelo administrador.|7|
|Erro      |Número de dispositivos que não conseguiram comunicar com o Intune ou o Azure AD e devolveram uma mensagem de erro. |3|

### <a name="policyplatformtypes"></a>PolicyPlatformTypes

A tabela seguinte contém os tipos de plataforma de todas as políticas atribuídas. Os tipos de plataforma das políticas que nunca foram atribuídos a um dispositivo não são apresentados nesta tabela.


|Propriedade  |Descrição  |Exemplo  |
|---------|---------|---------|
|PolicyPlatformTypeKey      |A chave exclusiva do tipo de plataforma da política. |20170519 |
|PolicyPlatformTypeId      |O identificador exclusivo do tipo de plataforma da política.|1|
|PolicyPlatformTypeName      |O nome do tipo de plataforma da política.|AndroidForWork |

### <a name="policydeviceactivity"></a>PolicyDeviceActivity

A tabela seguinte mostra o número de dispositivos no estado com êxito, pendente, com falhas ou com erros por dia. O número apresentado reflete os perfis de dados por Tipo de Política. Por exemplo, se um dispositivo estiver no estado com êxito em todas as políticas atribuídas, o contador de casos com êxito tem um incremento de um para esse dia. Se um dispositivo tiver dois perfis atribuídos, um no estado com êxito e outro num estado com erros, a entidade incrementa o contador do estado com êxito (Succeeded) e coloca o dispositivo no estado com erros. A entidade PolicyDeviceActivity apresenta uma lista de quantos dispositivos estão em cada um dos estados num determinado dia nos últimos 30 dias.

|Propriedade  |Descrição  |Exemplo  |
|---------|---------|---------|
|DateKey|Data-chave de quando a entrada do Perfil de Configuração do Dispositivo foi registada no armazém de dados.|20160703|
|Pendente|Número de Dispositivos exclusivos no estado pendente.|123|
|Succeeded|Número de Dispositivos exclusivos no estado com êxito.|12|
PolicyKey|A chave de política pode ser acompanhada pela Política para obter o policyName.|Linha de base do Windows 10|
|Erro|Número de Dispositivos exclusivos no estado com erros.|10|
|Falhou|Número de Dispositivos exclusivos no estado com falhas.|2|

### <a name="policyuseractivity"></a>PolicyUserActivity 

A tabela seguinte mostra o número de utilizadores no estado com êxito, pendente, com falhas ou com erros por dia. O número apresentado reflete os perfis de dados por Tipo de Política. Por exemplo, se um utilizador estiver no estado com êxito em todas as políticas atribuídas, sobe o contador com êxito em um para esse dia. Se um utilizador tiver dois perfis atribuídos, um no estado com êxito e outro no estado com erros, é contado o utilizador no estado com erros. A entidade PolicyUserActivity apresenta uma lista de quantos utilizadores estão em cada um dos estados num determinado dia nos últimos 30 dias.


| Propriedade  |                                         Descrição                                         |       Exemplo       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  DateKey  | Data-chave de quando a entrada do Perfil de Configuração do Dispositivo foi registada no armazém de dados. |      20160703       |
|  Pendente  |                         Número de Dispositivos exclusivos no estado pendente.                          |         123         |
| Succeeded |                         Número de Dispositivos exclusivos no estado com êxito.                          |         12          |
| PolicyKey |                A chave de política pode ser acompanhada pela Política para obter o policyName.                 | Linha de base do Windows 10 |
|   Erro   |                          Número de Dispositivos exclusivos no estado com erros.                           |         10          |

