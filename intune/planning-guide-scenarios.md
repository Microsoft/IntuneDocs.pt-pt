---
title: Identificar cenários de casos de utilização
titlesuffix: Microsoft Intune
description: Este artigo ajuda-o a identificar cenários de casos de utilização e casos de subutilização para uma implementação do Microsoft Intune apenas na cloud.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: de72bc56bf1ec0e7f1555d889ae0684c1162fdb9
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841407"
---
# <a name="identify-mobile-device-management-use-case-scenarios"></a>Identificar cenários de casos de utilização da gestão de dispositivos móveis

Identificar os cenários de casos de utilização é uma parte importante do processo de planeamento numa implementação bem-sucedida do Intune. Os cenários de casos de utilização são úteis, pois permitem que segmente os utilizadores em grupos que podem ser geridos por função ou tipo de utilizador e a propriedade do dispositivo do utilizador (por exemplo, empresarial ou pessoal).

Vamos abordar alguns exemplos que ajudam a sua organização a identificar cenários de casos de utilização do Intune, bem como grupos organizacionais e plataformas de dispositivos móveis associadas a cada caso de utilização.

## <a name="device-ownership"></a>Propriedade dos dispositivos
Pode começar por consultar os objetivos e as metas da implementação do Intune da sua organização para o ajudar a identificar os principais cenários de casos de utilização da implementação. No âmbito do seu plano de implementação do Intune, responda às seguintes perguntas:

-   Planeia suportar dispositivos pertencentes à empresa?

-   Planeia suportar dispositivos pertencentes a pessoas (BYOD)?

Estas não são opções e/ou. Pode considerar que é necessário suportar ambas as formas de propriedade do dispositivo para satisfazer os seus objetivos organizacionais. Os casos de subutilização ajudarão a esclarecer onde aplicar as diferentes políticas de gestão de dispositivos.

### <a name="user-type-or-device-role"></a>Tipo de utilizador ou função do dispositivo

Determine se cada cenário de casos de utilização também inclui casos de subutilização. Por exemplo, a sua organização pode ter identificado requisitos para suportar um cenário de caso de utilização empresarial que inclua casos de subutilização adicionais com base no tipo de utilizador ou na função do dispositivo, tais como:

-   Técnico de informação

-   Executivo

-   Modo de Local Público

Veja a seguir alguns exemplos de cenários de casos de utilização e casos de subutilização:

| **Casos de utilização** | **Casos de subutilização** |
|:---:|:---:|
| Empresarial | Técnico de informação |              
| Empresarial | Executivos |           
| Empresarial | Modo de Local Público |
| BYOD | Técnico de informação |           
| BYOD | Executivos |

Pode [transferir um modelo da tabela acima](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para introduzir os cenários de casos de utilização e de casos de subutilização da sua organização.

## <a name="organizational-groups-for-your-scenarios"></a>Grupos organizacionais para os seus cenários

Agora precisa de identificar os grupos organizacionais associados a cada cenário de caso de utilização e caso de subutilização. Por exemplo:

| **Casos de utilização** | **Casos de subutilização** | **Grupos organizacionais** |
|:---:|:---:|:---:|
| Empresarial | Técnico de informação | RH, Finanças |               
| Empresarial | Executivo | RH, Finanças |            
| Empresarial | Modo de Local Público | Revenda |
| BYOD | Técnico de informação | Marketing, Vendas |            
| BYOD | Executivo | Marketing, Vendas |


## <a name="mobile-device-platforms-for-your-scenarios"></a>Plataformas de dispositivos móveis para os seus cenários

O próximo passo consiste em identificar as plataformas de dispositivos móveis associados a cada cenário de caso de utilização. Poderá existir mais de uma plataforma.

Por exemplo, o seu cenário de casos de utilização empresarial poderá suportar plataformas de dispositivos Samsung Knox Android e iOS. A política de BYOD poderá incluir suporte para plataformas de dispositivos móveis adicionais como Android (não Samsung Knox) e Windows 10 Mobile. Com base nos exemplos anteriores, associámos plataformas de dispositivos móveis a cada cenário de casos de utilização.

| **Casos de utilização** | **Casos de subutilização** | **Grupos** | **Plataformas de dispositivos** |   
|:---:|:---:|:---:|:---:|
| Empresarial | Técnico de informação | RH, Finanças | iOS |                                                           
| Empresarial | Executivos | RH, Finanças | iOS |                                                           
| Empresarial | Modo de Local Público | Revenda | Android |
| BYOD | Técnico de informação | Marketing, Vendas | iOS |                                                           
| BYOD | Executivos | Marketing, Vendas | iOS |

## <a name="next-steps"></a>Passos Seguintes

A secção seguinte fornece orientações sobre como [identificar os requisitos do Intune para cada cenário de caso de utilização](planning-guide-requirements.md).
