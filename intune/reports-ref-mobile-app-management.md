---
title: Gestão de Aplicações Móveis (MAM)
titleSuffix: Microsoft Intune
description: Tópico de referência para a categoria Mobile App Management das coleções de entidades na API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c549a7063883f637ac7b5316e767b159d2328d0b
ms.sourcegitcommit: c3ac858bbadb63d248ed54069e48160d703bbaf2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313665"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Referência para as entidades de gestão de aplicações móveis (MAM)

A categoria **Mobile App Management** contém entidades para aplicações móveis como:

- Aplicações
- de Instâncias
- Estado de entrada
- Estado de funcionamento
- Estado de política
- Estado de inscrição
- Tipos de plataforma

## <a name="mamapplications"></a>mamApplications

A entidade **mamApplication** lista os aplicativos de linha de negócios (LOB) que são gerenciados por meio do MAM (gerenciamento de aplicativo móvel) sem registro em sua empresa.

| Propriedade | Descrição | Exemplo |
|---------|------------|--------|
| mamApplicationKey |Identificador exclusivo do aplicativo MAM. | 432 |
| mamApplicationName |Nome do aplicativo MAM. |Nome de exemplo do aplicativo MAM |
| mamApplicationId |ID do aplicativo de MAM. | 123 |
| IsDeleted |Indica se este registo da aplicação MAM foi atualizado. <br>True: a aplicação MAM tem um novo registo com campos atualizados nesta tabela. <br>False: o registo mais recente desta aplicação MAM. |Verdadeiro/Falso |
| startDateInclusiveUTC |Data e hora em UTC em que esta aplicação MAM foi criada no armazém de dados. |11/23/2016 12:00:00 AM |
| DeletedDateUTC |Data e hora em UTC em que a propriedade IsDeleted foi alterada para True. |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Data e hora em UTC em que esta aplicação MAM foi modificada pela última vez no armazém de dados. |11/23/2016 12:00:00 AM |


## <a name="mamapplicationinstances"></a>mamApplicationInstances

A entidade **mamApplicationInstance** lista aplicativos gerenciados de MAM (gerenciamento de aplicativo móvel) como instâncias singulares por usuário por dispositivo. Todos os utilizadores e dispositivos listados na entidade estão protegidos, ou seja, têm pelo menos uma Política de MAM atribuída.


|          Propriedade          |                                                                                                  Descrição                                                                                                  |               Exemplo                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   ApplicationInstanceKey   |                                                               Identificador exclusivo de instância da aplicação MAM no armazém de dados – chave de substituição.                                                                |                 123                  |
|           userId           |                                                                              ID de usuário do usuário que tem esse aplicativo de MAM instalado.                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   ApplicationInstanceId    |                                              Identificador exclusivo de instância da aplicação MAM, semelhante à propriedade ApplicationInstanceKey, apesar de o identificador ser uma chave natural.                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | ID do aplicativo do aplicativo Mam para o qual esta instância do aplicativo Mam foi criada.   | 11/23/2016 12:00:00 AM   |
|     applicationVersion     |                                                                                     Versão desta aplicação MAM.                                                                                      |                  2                   |
|        CreatedDate         |                                                                 Data em que este registo da instância da aplicação MAM foi criado. O valor pode ser nulo.                                                                 |        11/23/2016 12:00:00 AM        |
|          Plataforma          |                                                                          Plataforma do dispositivo no qual esta aplicação MAM está instalada.                                                                           |                  2                   |
|      PlatformVersion       |                                                                      Versão de plataforma do dispositivo no qual esta aplicação MAM está instalada.                                                                       |                 2.2                  |
|         SdkVersion         |                                                                            A versão de SDK MAM com a qual esta aplicação MAM foi encapsulada.                                                                            |                 3.2                  |
| mamDeviceId | ID do dispositivo ao qual a instância do aplicativo MAM está associada.   | 11/23/2016 12:00:00 AM   |
| mamDeviceType | Tipo de dispositivo do dispositivo ao qual a instância do aplicativo MAM está associada.   | 11/23/2016 12:00:00 AM   |
| mamDeviceName | Nome do dispositivo ao qual a instância do aplicativo MAM está associada.   | 11/23/2016 12:00:00 AM   |
|         IsDeleted          | Indica se este registo de instância da aplicação MAM foi atualizado. <br>True: esta instância de aplicação MAM tem um novo registo com campos atualizados nesta tabela. <br>False: o registo mais recente desta instância da aplicação MAM. |              Verdadeiro/Falso              |
|   startDateInclusiveUtc    |                                                              Data e hora em UTC em que esta instância da aplicação MAM foi criada no armazém de dados.                                                               |        11/23/2016 12:00:00 AM        |
|       DeletedDateUtc       |                                                                             Data e hora em UTC em que a propriedade IsDeleted foi alterada para True.                                                                              |        11/23/2016 12:00:00 AM        |
| RowLastModifiedDateTimeUtc |                                                           Data e hora em UTC em que esta instância da aplicação MAM foi modificada pela última vez no armazém de dados.                                                            |        11/23/2016 12:00:00 AM        |


## <a name="mamcheckins"></a>mamCheckins

A entidade **mamCheckin** representa os dados coletados quando uma instância de aplicativo de gerenciamento de aplicativo móvel (MAM) tiver feito check-in com o serviço do Intune. 

> [!Note]  
> Quando uma instância de aplicação dá entrada várias vezes por dia, o armazém de dados armazena-a como uma entrada única.

| Propriedade | Descrição | Exemplo |
|---------|------------|--------|
| dateKey |Chave da data quando a entrada da aplicação MAM foi registada no armazém de dados. | 20160703 |
| ApplicationInstanceKey |Chave da instância da aplicação associada a esta entrada da aplicação MAM. | 123 |
| userKey |Chave do utilizador associado a esta entrada da aplicação MAM. | 4323 |
| mamApplicationKey |Chave de aplicativo do aplicativo associado ao check-in do aplicativo MAM. | 432 |
| DeviceHealthKey |Chave de DeviceHealth associada a esta entrada da aplicação MAM. | 321 |
| PlatformKey |Representa a plataforma do dispositivo associado a esta entrada da aplicação MAM. |123 |
| EffectiveAppliedPolicyKey |Representa a política aplicada em vigor associada à aplicação MAM que deu entrada. Uma política aplicada em vigor resulta da união de todas as políticas relevantes para um utilizador e uma aplicação específicos. | 322 |
| pastCheckInDate |Data e hora em que esta aplicação MAM deu entrada pela última vez. O valor pode ser nulo. |11/23/2016 12:00:00 AM |


## <a name="mamdevicehealth"></a>MamDeviceHealth

A entidade **mamDeviceHealth** representa dispositivos que têm políticas de gerenciamento de aplicativo móvel (MAM) implantadas para eles mesmo se estiverem desbloqueados.

| Propriedade | Descrição | Exemplo |
|---------|------------|--------|
| DeviceHealthKey |Identificador exclusivo do dispositivo e respetivo estado de funcionamento associado no armazém de dados – chave de substituição. |123 |
| deviceHealth |Identificador exclusivo do dispositivo e respetivo estado de funcionamento associado, semelhante a DeviceHealthKey, mas o identificador é uma chave natural. |b66bc706-ffff-7777-0340-032819502773 |
| DeviceHealthName |Representa o estado do dispositivo. <br>Not available: não existem informações sobre este dispositivo. <br>Healthy: o dispositivo não foi desbloqueado por jailbreak. <br>Unhealthy: o dispositivo foi desbloqueado por jailbreak. |Not Available Healthy Unhealthy |
| RowLastModifiedDateTimeUtc |Data e hora em UTC em que o Estado de Funcionamento deste Dispositivo MAM específico foi modificado pela última vez no armazém de dados. |11/23/2016 12:00:00 AM |

## <a name="mameffectivepolicies"></a>mamEffectivePolicies

A entidade **mamEffectivePolicy** lista todas as políticas efetivas de MAM (gerenciamento de aplicativo móvel) aplicadas em sua organização. Uma política aplicada em vigor resulta da união de todas as políticas relevantes para um utilizador e uma aplicação específicos.

| Propriedade | Descrição | Exemplo |
|---------|------------|--------|
| EffectivePolicyKey |Identificador exclusivo da política em vigor de MAM no armazém de dados. |2 |
| RealPolicyKey |Identificador exclusivo da política de MAM criada pelo Profissional de TI. |1 |
| RowCreatedDateTimeUtc |Data e hora em UTC em que esta política em vigor de MAM foi criada no armazém de dados. |11/23/2016 12:00:00 AM |

## <a name="mamplatforms"></a>mamPlatforms

A entidade **mamPlatform** lista os nomes de plataforma e os tipos nos quais um aplicativo de gerenciamento de aplicativo móvel (MAM) foi instalado.


|          Propriedade          |                                    Descrição                                    |                         Exemplo                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        PlatformKey         |     Identificador exclusivo da plataforma no armazém de dados – chave de substituição.      |                           123                           |
|          Plataforma          | Identificador exclusivo da plataforma, semelhante a PlatformKey, mas é uma chave natural. |                           123                           |
|        PlatformName        |                                   Nome da plataforma                                   | Não disponível <br>Nenhum <br>Windows <br>IOS <br>Android. |
| RowLastModifiedDateTimeUtc | Data e hora em UTC em que esta plataforma foi modificada pela última vez no armazém de dados.  |                 11/23/2016 12:00:00 AM                  |

