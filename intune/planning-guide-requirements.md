---
title: "Determinar os requisitos de cenários de casos de utilização"
description: "Este artigo ajuda-o a determinar os requisitos de cenários de casos de utilização e de casos de subutilização para uma implementação apenas na cloud do Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 032427a9965f368d7be17339e3cbe5b426800347
ms.sourcegitcommit: ce363409d1206e4a3d669709863ccc9eb22b7d5f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/11/2017
---
# Determinar os requisitos de cenários de casos de utilização
<a id="determine-use-case-scenario-requirements" class="xliff"></a>

Nesta secção, determina os requisitos para cada grupo organizacional dentro de cada cenário de caso de utilização. Este processo ajuda-o a preparar-se para as outras áreas de planeamento de implementação do Intune, tais como a arquitetura e a estrutura, a integração e a implementação. Também pode ajudá-lo a identificar potenciais lacunas e desafios relacionados com o seu projeto de implementação do Intune.

Poderá ter diferentes conjuntos de requisitos para cada um dos seus cenários de casos de utilização e de casos de subutilização, bem como para os grupos organizacionais e as plataformas de dispositivos móveis associados. Por exemplo, os seus requisitos de cenários de casos de utilização empresarial podem exigir dispositivos para inscrição no Intune com um conjunto mais restritivo de definições do dispositivo, como um PIN de 6 carateres ou a cópia de segurança na cloud desativada. O seu cenário de casos de utilização “bring your own device” (BYOD) poderá ser menos restritivo e permitir um PIN de 4 carateres e a cópia de segurança na cloud.

Também poderá ter grupos organizacionais para o cenário de caso de utilização empresarial com diferentes conjuntos de requisitos (por exemplo, definições de PIN, perfil de Wi-Fi ou VPN, aplicações implementadas). Os seus requisitos poderão ser igualmente determinados pelas capacidades da plataforma do dispositivo móvel (por exemplo, leitor de impressões digitais, perfil de e-mail).

Veja alguns exemplos de requisitos de casos de utilização de uma organização que apresentam diferentes conjuntos de requisitos para cada cenário de casos de utilização e casos de subutilização, grupo organizacional e plataforma de dispositivo móvel. Também pode utilizar a tabela seguinte para introduzir os requisitos de caso de utilização da sua organização:

| **Casos de utilização** | **Casos de subutilização** | **Grupos** | **Plataformas de dispositivos** | **Requirements** |
|:---:|:---:|:---:|:---:|:---:|
| Empresarial | Técnico de informação | RH, Finanças | iOS | E-mail seguro, definições do dispositivo, perfis, aplicações |                                                          
| Empresarial | Executivos | RH, Finanças | iOS | E-mail seguro, definições do dispositivo, perfis, aplicações |                                                         
| Empresarial | Kiosk | Revenda | Android | Definições do dispositivo, perfis e aplicações |
| BYOD | Técnico de informação | Marketing, Vendas | iOS | E-mail seguro, definições do dispositivo, perfis, aplicações |                                                         
| BYOD | Executivos | Marketing, Vendas | iOS | E-mail seguro, definições do dispositivo, perfis, aplicações |

Pode [transferir um modelo da tabela acima](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para introduzir os requisitos de casos de utilização e de casos de subutilização da sua organização.


## Exemplos de requisitos
<a id="examples-of-requirements" class="xliff"></a>

Veja mais alguns exemplos que podem ser utilizados na coluna “Requisitos”:

- **E-mail seguro**
    - Acesso condicional do Exchange Online/no local
    - Políticas de proteção de aplicações do Outlook

- **Definições do dispositivo**
    - PIN com quatro ou seis carateres
    - Restrição da cópia de segurança na cloud

- **Perfis**
    - Wi-Fi
    - VPN
    - E-mail (Windows 10 Mobile)

- **Aplicações**
    - Office 365 com políticas de proteção de aplicações
    - Linha de negócio (LOB) com políticas de proteção de aplicações

## Passos seguintes
<a id="next-steps" class="xliff"></a>

A secção seguinte fornece orientações relativas a [como pode desenvolver um plano de implementação do Intune](planning-guide-rollout-plan.md).
