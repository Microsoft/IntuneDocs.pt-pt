---
title: Gestão de Aplicações Móveis (MAM)
titlesuffix: Microsoft Intune
description: Tópico de referência para a categoria Mobile App Management das coleções de entidades na API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 43292efd55ff93c2c05f49a5e3e8ceaaf91c5f2e
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Referência para as entidades de gestão de aplicações móveis (MAM)

A categoria **Mobile App Management** contém entidades para aplicações móveis como:

  -  Aplicações
  -  de Instâncias
  -  Estado de entrada
  -  Estado de funcionamento
  -  Estado de política
  -  Estado de inscrição
  -  Tipos de plataforma

## <a name="mamapplication"></a>MamApplication

A entidade **MamApplication** lista aplicações Linha de Negócio (LOB) que são geridas através da Gestão de Aplicações Móveis (MAM) sem inscrição na sua empresa.

| Propriedade | Descrição | Exemplo |
|---------|------------|--------|
| ApplicationKey |Identificador exclusivo da aplicação MAM no armazém de dados. |123 |
| ApplicationName |Nome da aplicação MAM. |"Word" |
| ApplicationID |ID da Aplicação MAM. |b66bc706-ffff-7437-0340-032819502773 |
| IsDeleted |Indica se este registo da aplicação MAM foi atualizado. <br>True: a aplicação MAM tem um novo registo com campos atualizados nesta tabela. <br>False: o registo mais recente desta aplicação MAM. |True/False |
| StartDateInclusiveUTC |Data e hora em UTC em que esta aplicação MAM foi criada no armazém de dados. |11/23/2016 12:00:00 AM |
| DeletedDateUTC |Data e hora em UTC em que a propriedade IsDeleted foi alterada para True. |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Data e hora em UTC em que esta aplicação MAM foi modificada pela última vez no armazém de dados. |11/23/2016 12:00:00 AM |

## <a name="mamapplicationinstance"></a>MamApplicationInstance

A entidade **MamApplicationInstance** lista aplicações geridas da Gestão de Aplicações Móveis (MAM) como instâncias singulares por utilizador e dispositivo. Todos os utilizadores e dispositivos listados na entidade estão protegidos, ou seja, têm pelo menos uma Política de MAM atribuída.


|          Propriedade          |                                                                                                  Descrição                                                                                                  |               Exemplo                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   ApplicationInstanceKey   |                                                               Identificador exclusivo de instância da aplicação MAM no armazém de dados – chave de substituição.                                                                |                 123                  |
|           UserId           |                                                                              ID do utilizador que tem esta aplicação MAM instalada.                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   ApplicationInstanceId    |                                              Identificador exclusivo de instância da aplicação MAM, semelhante à propriedade ApplicationInstanceKey, apesar de o identificador ser uma chave natural.                                              | b66bc706-ffff-7437-0340-032819502773 |
|       ApplicationID        |                                                                                        ID desta aplicação MAM                                                                                         |  com.microsoft.groupies-daily.<IOS>  |
|     ApplicationVersion     |                                                                                     Versão desta aplicação MAM.                                                                                      |                  2                   |
|        CreatedDate         |                                                                 Data em que este registo da instância da aplicação MAM foi criado. O valor pode ser nulo.                                                                 |        11/23/2016 12:00:00 AM        |
|          Platform          |                                                                          Plataforma do dispositivo no qual esta aplicação MAM está instalada.                                                                           |                  2                   |
|      PlatformVersion       |                                                                      Versão de plataforma do dispositivo no qual esta aplicação MAM está instalada.                                                                       |                 2.2                  |
|         SdkVersion         |                                                                            A versão de SDK MAM com a qual esta aplicação MAM foi encapsulada.                                                                            |                 3.2                  |
|          DeviceId          |                                                                          ID do dispositivo no qual esta aplicação MAM está instalada.                                                                          | b66bc706-ffff-7437-0340-032819502773 |
|         DeviceName         |                                                                         Nome do dispositivo no qual esta aplicação MAM está instalada.                                                                         |              "OMeuDispositivo"              |
|         IsDeleted          | Indica se este registo de instância da aplicação MAM foi atualizado. <br>True: esta instância de aplicação MAM tem um novo registo com campos atualizados nesta tabela. <br>False: o registo mais recente desta instância da aplicação MAM. |              True/False              |
|   StartDateInclusiveUtc    |                                                              Data e hora em UTC em que esta instância da aplicação MAM foi criada no armazém de dados.                                                               |        11/23/2016 12:00:00 AM        |
|       DeletedDateUtc       |                                                                             Data e hora em UTC em que a propriedade IsDeleted foi alterada para True.                                                                              |        11/23/2016 12:00:00 AM        |
| RowLastModifiedDateTimeUtc |                                                           Data e hora em UTC em que esta instância da aplicação MAM foi modificada pela última vez no armazém de dados.                                                            |        11/23/2016 12:00:00 AM        |

## <a name="mamcheckin"></a>MamCheckin

A entidade **MamCheckin** representa dados recolhidos quando uma instância de Gestão de Aplicações Móveis (MAM) deu entrada no Serviço do Intune. 

> [!Note]  
> Quando uma instância de aplicação dá entrada várias vezes por dia, o armazém de dados armazena-a como uma entrada única.

| Propriedade | Descrição | Exemplo |
|---------|------------|--------|
| DateKey |Chave da data quando a entrada da aplicação MAM foi registada no armazém de dados. | 20160703 |
| ApplicationInstanceKey |Chave da instância da aplicação associada a esta entrada da aplicação MAM. |5/2/1900 12:00:00 AM |
| UserKey |Chave do utilizador associado a esta entrada da aplicação MAM. |1/12/1900 12:00:00 AM |
| ApplicationKey |Chave da aplicação MAM que deu entrada. |1/10/1900 12:00:00 AM |
| DeviceHealthKey |Chave de DeviceHealth associada a esta entrada da aplicação MAM. |1/2/1900 12:00:00 AM |
| PlatformKey |Representa a plataforma do dispositivo associado a esta entrada da aplicação MAM. |1/1/1900 12:00:00 AM |
| EffectiveAppliedPolicyKey |Representa a política aplicada em vigor associada à aplicação MAM que deu entrada. Uma política aplicada em vigor resulta da união de todas as políticas relevantes para um utilizador e uma aplicação específicos. |5/2/1900 12:00:00 AM |
| LastCheckInDate |Data e hora em que esta aplicação MAM deu entrada pela última vez. O valor pode ser nulo. |11/23/2016 12:00:00 AM |

## <a name="mamdevicehealth"></a>MamDeviceHealth

A entidade **MamDeviceHealth** representa dispositivos que têm políticas de Gestão de Aplicações Móveis (MAM) implementadas nos mesmos, mesmo que tenham sido desbloqueados por jailbreak.

| Propriedade | Descrição | Exemplo |
|---------|------------|--------|
| DeviceHealthKey |Identificador exclusivo do dispositivo e respetivo estado de funcionamento associado no armazém de dados – chave de substituição. |1/1/1900 12:00:00 AM |
| DeviceHealth |Identificador exclusivo do dispositivo e respetivo estado de funcionamento associado, semelhante a DeviceHealthKey, mas o identificador é uma chave natural. |1/1/1900 12:00:00 AM |
| DeviceHealthName |Representa o estado do dispositivo. <br>Not available: não existem informações sobre este dispositivo. <br>Healthy: o dispositivo não foi desbloqueado por jailbreak. <br>Unhealthy: o dispositivo foi desbloqueado por jailbreak. |Not Available Healthy Unhealthy |
| RowLastModifiedDateTimeUtc |Data e hora em UTC em que o Estado de Funcionamento deste Dispositivo MAM específico foi modificado pela última vez no armazém de dados. |11/23/2016 12:00:00 AM |

## <a name="mameffectivepolicy"></a>MamEffectivePolicy

A entidade **MamEffectivePolicy** lista todas as políticas de Gestão de Aplicações Móveis (MAM) em vigor aplicadas na sua organização. Uma política aplicada em vigor resulta da união de todas as políticas relevantes para um utilizador e uma aplicação específicos.

| Propriedade | Descrição | Exemplo |
|---------|------------|--------|
| EffectivePolicyKey |Identificador exclusivo da política em vigor de MAM no armazém de dados. |2 |
| RealPolicyKey |Identificador exclusivo da política de MAM criada pelo Profissional de TI. |1 |
| RowCreatedDateTimeUtc |Data e hora em UTC em que esta política em vigor de MAM foi criada no armazém de dados. |11/23/2016 12:00:00 AM |

## <a name="mamglobalapplication"></a>MamGlobalApplication

A entidade **MamGlobalApplication** lista aplicações de loja que são geridas através da Gestão de Aplicações Móveis (MAM) sem inscrição na sua empresa.


|          Propriedade          |                                               Descrição                                               |           Exemplo            |
|----------------------------|---------------------------------------------------------------------------------------------------------|------------------------------|
|       ApplicationKey       |          Identificador exclusivo da aplicação de loja no armazém de dados, conhecido como chave de substituição.          |             123              |
|       ApplicationID        | Identificador exclusivo da aplicação de loja. O identificador é semelhante a ApplicationKey, mas é uma chave natural.  | com.microsoft.skydrive.<ios> |
|      ApplicationName       |                                      Nome de Aplicação Global MAM.                                       |           Skydrive           |
| RowLastModifiedDateTimeUtc | Data e hora em UTC em que esta Aplicação Global MAM específica foi modificada pela última vez no armazém de dados. |    11/23/2016 12:00:00 AM    |

## <a name="mamplatform"></a>MamPlatform

A entidade **MamPlatform** lista os nomes e tipos de plataformas em que uma aplicação da Gestão de Aplicações Móveis (MAM) foi instalada.


|          Propriedade          |                                    Descrição                                    |                         Exemplo                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        PlatformKey         |     Identificador exclusivo da plataforma no armazém de dados – chave de substituição.      |                           123                           |
|          Platform          | Identificador exclusivo da plataforma, semelhante a PlatformKey, mas é uma chave natural. |                           123                           |
|        PlatformName        |                                   Nome da plataforma                                   | Não disponível <br>Nenhum <br>Windows <br>iOS <br>Android. |
| RowLastModifiedDateTimeUtc | Data e hora em UTC em que esta plataforma foi modificada pela última vez no armazém de dados.  |                 11/23/2016 12:00:00 AM                  |

