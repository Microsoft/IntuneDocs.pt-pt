---
title: Gestão de Aplicações Móveis (MAM)
titleSuffix: Microsoft Intune
description: Tópico de referência para a categoria Mobile App Management das coleções de entidades na API do Armazém de Dados do Intune.
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
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: eb1833a6a54fe0a7f78958e653468921df952b4d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72505691"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Referência para as entidades de gestão de aplicações móveis (MAM)

A categoria **Mobile App Management** contém entidades para aplicações móveis como:

- Apps
- de Instâncias
- Estado de entrada
- Estado de funcionamento
- Estado de política
- Estado de inscrição
- Tipos de plataforma

## <a name="mamapplications"></a>mamApplications

A entidade **mamApplication** lista os aplicativos de linha de negócios (LOB) que são gerenciados por meio do MAM (gerenciamento de aplicativo móvel) sem registro em sua empresa.

| Propriedade | Description | Exemplo |
|---------|------------|--------|
| mamApplicationKey |Identificador exclusivo do aplicativo MAM. | 432 |
| mamApplicationName |Nome do aplicativo MAM. |Nome de exemplo do aplicativo MAM |
| mamApplicationId |ID do aplicativo de MAM. | 123 |
| isDeleted |Indica se este registo da aplicação MAM foi atualizado. <br>True: a aplicação MAM tem um novo registo com campos atualizados nesta tabela. <br>False: o registo mais recente desta aplicação MAM. |True/False |
| startDateInclusiveUTC |Data e hora em UTC em que esta aplicação MAM foi criada no armazém de dados. |11/23/2016 12:00:00 AM |
| deletedDateUTC |Data e hora em UTC em que a propriedade IsDeleted foi alterada para True. |11/23/2016 12:00:00 AM |
| rowLastModifiedDateTimeUTC |Data e hora em UTC em que esta aplicação MAM foi modificada pela última vez no armazém de dados. |11/23/2016 12:00:00 AM |


## <a name="mamapplicationinstances"></a>mamApplicationInstances

A entidade **mamApplicationInstance** lista aplicativos gerenciados de MAM (gerenciamento de aplicativo móvel) como instâncias singulares por usuário por dispositivo. Todos os utilizadores e dispositivos listados na entidade estão protegidos, ou seja, têm pelo menos uma Política de MAM atribuída.


|          Propriedade          |                                                                                                  Description                                                                                                  |               Exemplo                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   applicationInstanceKey   |                                                               Identificador exclusivo de instância da aplicação MAM no armazém de dados – chave de substituição.                                                                |                 123                  |
|           userId           |                                                                              ID de usuário do usuário que tem esse aplicativo de MAM instalado.                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   applicationInstanceId    |                                              Identificador exclusivo de instância da aplicação MAM, semelhante à propriedade ApplicationInstanceKey, apesar de o identificador ser uma chave natural.                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | ID do aplicativo do aplicativo Mam para o qual esta instância do aplicativo Mam foi criada.   | 11/23/2016 12:00:00 AM   |
|     applicationVersion     |                                                                                     Versão desta aplicação MAM.                                                                                      |                  2                   |
|        createdDate         |                                                                 Data em que este registo da instância da aplicação MAM foi criado. O valor pode ser nulo.                                                                 |        11/23/2016 12:00:00 AM        |
|          Plataforma          |                                                                          Plataforma do dispositivo no qual esta aplicação MAM está instalada.                                                                           |                  2                   |
|      platformVersion       |                                                                      Versão de plataforma do dispositivo no qual esta aplicação MAM está instalada.                                                                       |                 2.2                  |
|         sdkVersion         |                                                                            A versão de SDK MAM com a qual esta aplicação MAM foi encapsulada.                                                                            |                 3.2                  |
| mamDeviceId | ID do dispositivo ao qual a instância do aplicativo MAM está associada.   | 11/23/2016 12:00:00 AM   |
| mamDeviceType | Tipo de dispositivo do dispositivo ao qual a instância do aplicativo MAM está associada.   | 11/23/2016 12:00:00 AM   |
| mamDeviceName | Nome do dispositivo ao qual a instância do aplicativo MAM está associada.   | 11/23/2016 12:00:00 AM   |
|         isDeleted          | Indica se este registo de instância da aplicação MAM foi atualizado. <br>True: esta instância de aplicação MAM tem um novo registo com campos atualizados nesta tabela. <br>False: o registo mais recente desta instância da aplicação MAM. |              True/False              |
|   startDateInclusiveUtc    |                                                              Data e hora em UTC em que esta instância da aplicação MAM foi criada no armazém de dados.                                                               |        11/23/2016 12:00:00 AM        |
|       deletedDateUtc       |                                                                             Data e hora em UTC em que a propriedade IsDeleted foi alterada para True.                                                                              |        11/23/2016 12:00:00 AM        |
| rowLastModifiedDateTimeUtc |                                                           Data e hora em UTC em que esta instância da aplicação MAM foi modificada pela última vez no armazém de dados.                                                            |        11/23/2016 12:00:00 AM        |


## <a name="mamcheckins"></a>mamCheckins

A entidade **mamCheckin** representa os dados coletados quando uma instância de aplicativo de gerenciamento de aplicativo móvel (MAM) tiver feito check-in com o serviço do Intune. 

> [!Note]  
> Quando uma instância de aplicação dá entrada várias vezes por dia, o armazém de dados armazena-a como uma entrada única.

| Propriedade | Description | Exemplo |
|---------|------------|--------|
| dateKey |Chave da data quando a entrada da aplicação MAM foi registada no armazém de dados. | 20160703 |
| applicationInstanceKey |Chave da instância da aplicação associada a esta entrada da aplicação MAM. | 123 |
| userKey |Chave do utilizador associado a esta entrada da aplicação MAM. | 4323 |
| mamApplicationKey |Chave de aplicativo do aplicativo associado ao check-in do aplicativo MAM. | 432 |
| deviceHealthKey |Chave de DeviceHealth associada a esta entrada da aplicação MAM. | 321 |
| platformKey |Representa a plataforma do dispositivo associado a esta entrada da aplicação MAM. |123 |
| effectiveAppliedPolicyKey |Representa a política aplicada em vigor associada à aplicação MAM que deu entrada. Uma política aplicada em vigor resulta da união de todas as políticas relevantes para um utilizador e uma aplicação específicos. | 322 |
| pastCheckInDate |Data e hora em que esta aplicação MAM deu entrada pela última vez. O valor pode ser nulo. |11/23/2016 12:00:00 AM |


## <a name="mamdevicehealth"></a>mamDeviceHealth

A entidade **mamDeviceHealth** representa dispositivos que têm políticas de gerenciamento de aplicativo móvel (MAM) implantadas para eles mesmo se estiverem desbloqueados.

| Propriedade | Description | Exemplo |
|---------|------------|--------|
| deviceHealthKey |Identificador exclusivo do dispositivo e respetivo estado de funcionamento associado no armazém de dados – chave de substituição. |123 |
| deviceHealth |Identificador exclusivo do dispositivo e respetivo estado de funcionamento associado, semelhante a DeviceHealthKey, mas o identificador é uma chave natural. |b66bc706-ffff-7777-0340-032819502773 |
| deviceHealthName |Representa o estado do dispositivo. <br>Not available: não existem informações sobre este dispositivo. <br>Healthy: o dispositivo não foi desbloqueado por jailbreak. <br>Unhealthy: o dispositivo foi desbloqueado por jailbreak. |Not Available Healthy Unhealthy |
| rowLastModifiedDateTimeUtc |Data e hora em UTC em que o Estado de Funcionamento deste Dispositivo MAM específico foi modificado pela última vez no armazém de dados. |11/23/2016 12:00:00 AM |

## <a name="mameffectivepolicies"></a>mamEffectivePolicies

A entidade **mamEffectivePolicy** lista todas as políticas efetivas de MAM (gerenciamento de aplicativo móvel) aplicadas em sua organização. Uma política aplicada em vigor resulta da união de todas as políticas relevantes para um utilizador e uma aplicação específicos.

| Propriedade | Description | Exemplo |
|---------|------------|--------|
| effectivePolicyKey |Identificador exclusivo da política em vigor de MAM no armazém de dados. |2 |
| realPolicyKey |Identificador exclusivo da política de MAM criada pelo Profissional de TI. |1 |
| rowCreatedDateTimeUtc |Data e hora em UTC em que esta política em vigor de MAM foi criada no armazém de dados. |11/23/2016 12:00:00 AM |

## <a name="mamplatforms"></a>mamPlatforms

A entidade **mamPlatform** lista os nomes de plataforma e os tipos nos quais um aplicativo de gerenciamento de aplicativo móvel (MAM) foi instalado.


|          Propriedade          |                                    Description                                    |                         Exemplo                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        platformKey         |     Identificador exclusivo da plataforma no armazém de dados – chave de substituição.      |                           123                           |
|          Plataforma          | Identificador exclusivo da plataforma, semelhante a PlatformKey, mas é uma chave natural. |                           123                           |
|        platformName        |                                   Nome da plataforma                                   | Não disponível <br>Nenhum <br>Windows <br>iOS <br>Android. |
| rowLastModifiedDateTimeUtc | Data e hora em UTC em que esta plataforma foi modificada pela última vez no armazém de dados.  |                 11/23/2016 12:00:00 AM                  |

