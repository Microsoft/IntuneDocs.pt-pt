---
title: "Identificar cenários de casos de utilização do Intune | Documentos da Microsoft"
description: "Este artigo ajuda a identificar cenários de casos de utilização e casos de subutilização para uma implementação do Microsoft Intune apenas na cloud."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f807d6e4b20b98ecf622d1ebdd9db33b132a2e6a
ms.openlocfilehash: c834b0282b8f9b47566ab1da2125d993ba8febdf


---

# <a name="identify-intune-use-case-scenarios"></a>Identificar cenários de casos de utilização do Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Os cenários de casos de utilização de gestão de dispositivos móveis descrevem o tipo ou a função do utilizador e a propriedade do respetivo dispositivo (por exemplo, pessoal ou da empresa). Os cenários de casos de utilização são úteis porque permitem dividir os seus utilizadores em grupos mais fáceis de gerir. Identificar os seus cenários de casos de utilização é uma parte importante do processo de planeamento numa implementação bem-sucedida do Intune.

Vamos abordar alguns exemplos que ajudam a sua organização a identificar cenários de casos de utilização do Intune, bem como grupos organizacionais e plataformas de dispositivos móveis associadas a cada caso de utilização.

## <a name="use-case-scenarios"></a>Cenários de casos de utilização

Pode começar por consultar os objetivos e metas da implementação do Intune da sua organização para o ajudar a identificar os principais cenários de casos de utilização da sua implementação. No âmbito do seu plano de implementação do Intune, terá de responder às seguintes perguntas:

-   Planeia suportar dispositivos pertencentes à empresa?

-   Planeia suportar dispositivos pertencentes a pessoas (BYOD)?

### <a name="sub-use-case-scenarios"></a>Cenários de casos de subutilização

Após identificar os seus principais cenários de casos de utilização, terá de determinar se cada cenário de caso de utilização também inclui casos de subutilização. Por exemplo, uma organização pode ter identificado requisitos para suportar um cenário de caso de utilização empresarial que inclua casos de subutilização adicionais:

-   Técnico de informação

-   Executivos

-   Kiosk

Eis alguns exemplos de cenários de casos de utilização e casos de subutilização. Pode utilizar a tabela abaixo para introduzir o caso de utilização e os cenários de casos de subutilização da sua organização:

| **Casos de utilização** | **Casos de subutilização** |
|:---:|:---:|
| Empresarial | Técnico de informação |              
| Empresarial | Executivos |           
| Empresarial | Kiosk |
| BYOD | Técnico de informação |           
| BYOD | Executivos |

## <a name="identify-organizational-groups-associated-with-use-case-scenarios"></a>Identificar grupos organizacionais associados a cenários de casos de utilização

Agora precisa de identificar os grupos organizacionais associados a cada cenário de caso de utilização e caso de subutilização. Eis alguns exemplos de grupos organizacionais associados a cenários de casos de utilização e casos de subutilização que podem ser utilizados como modelo para introduzir as informações da sua organização:

| **Casos de utilização** | **Casos de subutilização** | **Grupos organizacionais** |
|:---:|:---:|:---:|
| Empresarial | Técnico de informação | RH, Finanças |               
| Empresarial | Executivo | RH, Finanças |            
| Empresarial | Kiosk | Revenda |
| BYOD | Técnico de informação | Marketing, Vendas |            
| BYOD | Executivo | Marketing, Vendas |

## <a name="identify-mobile-device-platforms-for-use-case-scenarios"></a>Identificar plataformas de dispositivos móveis para cenários de casos de utilização

Aqui, irá identificar as plataformas de dispositivos móveis associados a cada cenário de caso de utilização. Por exemplo, o seu cenário de caso de utilização empresarial poderá suportar plataformas de dispositivos iOS e Android Samsung KNOX e a sua política BYOD poderá incluir suporte para plataformas de dispositivos móveis adicionais como o Android (que NÃO seja Samsung KNOX) e o Windows 10 Mobile. Eis um exemplo de plataformas de dispositivos móveis associadas a cada cenário de caso de utilização. Pode utilizar a tabela abaixo para introduzir as plataformas de dispositivos da sua organização associadas aos respetivos cenários de casos de utilização:

| **Casos de utilização** | **Casos de subutilização** | **Grupos** | **Plataformas de dispositivos** |   
|:---:|:---:|:---:|:---:|
| Empresarial | Técnico de informação | RH, Finanças | iOS |                                                           
| Empresarial | Executivos | RH, Finanças | iOS |                                                           
| Empresarial | Kiosk | Revenda | Android |
| BYOD | Técnico de informação | Marketing, Vendas | iOS |                                                           
| BYOD | Executivos | Marketing, Vendas | iOS |

## <a name="next-section"></a>Secção Seguinte

A secção seguinte fornece orientações sobre como [identificar os requisitos do Intune para cada cenário de caso de utilização](section-3-determine-use-case-requirements.md).



<!--HONumber=Dec16_HO5-->


