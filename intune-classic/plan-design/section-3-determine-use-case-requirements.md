---
title: "Determinar requisitos de cenários de casos de utilização do Intune | Documentos da Microsoft"
description: "Este artigo ajuda a determinar requisitos de cenários de casos de utilização e de casos de subutilização para uma implementação apenas na cloud do Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: a56b683e57997171053f35414289d5b782c8fc2d
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="determine-intune-use-case-scenario-requirements"></a>Determinar requisitos de cenários de casos de utilização do Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Nesta secção, determinará os requisitos para cada grupo organizacional dentro de cada cenário de caso de utilização. Este processo ajudá-lo-á a preparar-se melhor para as outras áreas de planeamento de implementação do Intune, tais como a arquitetura e a estrutura, a integração e a implementação. Também pode ajudá-lo a identificar potenciais lacunas e desafios relacionados com o seu projeto de implementação do Intune.

Poderá ter diferentes conjuntos de requisitos para cada um dos seus cenários de casos de utilização e de casos de subutilização, bem como para os grupos organizacionais e as plataformas de dispositivos móveis associados. Por exemplo, os seus requisitos de cenário de caso de utilização empresarial podem exigir a inscrição de dispositivos no Intune com um conjunto mais restritivo de definições do dispositivo (por exemplo, PIN com 6 carateres e desativação da cópia de segurança na cloud), ao passo que o seu cenário de caso de utilização "Bring your own device" (BYOD) não exige definições tão restritivas (por exemplo, PIN com 4 carateres e permissão para criar cópias de segurança na cloud).

Também poderá ter grupos organizacionais para o cenário de caso de utilização empresarial com diferentes conjuntos de requisitos (por exemplo, definições de PIN, perfil de Wi-Fi ou VPN, aplicações implementadas). Além disso, os requisitos poderão ser determinados pelas capacidades da plataforma do dispositivo móvel (por exemplo, leitor de impressões digitais, perfil de e-mail).

Eis alguns exemplos de requisitos de casos de utilização de uma organização que apresentam diferentes conjuntos de requisitos para cada cenário de caso de utilização/caso de subutilização, grupo organizacional e plataforma de dispositivo móvel. Também pode utilizar a tabela abaixo para introduzir os requisitos de caso de utilização da sua organização.

| **Casos de utilização** | **Casos de subutilização** | **GRUPOS** | **Plataformas de SO de dispositivos** | **Requirements** |
|:---:|:---:|:---:|:---:|:---:|
| Empresarial | Técnico de Informação | RH, Finanças | iOS | E-mail seguro, definições do dispositivo, Perfis, Aplicações |                                                          
| Empresarial | Executivos | RH, Finanças | iOS | E-mail seguro, definições do dispositivo, Perfis, Aplicações |                                                         
| Empresarial | Kiosk | Revenda | Android | Definições do dispositivo, Perfis e Aplicações |
| BYOD | Técnico de Informação | Marketing, Vendas | iOS | E-mail seguro, definições do dispositivo, Perfis, Aplicações |                                                         
| BYOD | Executivos | Marketing, Vendas | iOS | E-mail seguro, definições do dispositivo, Perfis, Aplicações |

## <a name="examples-of-requirements"></a>Exemplos de requisitos

Eis mais alguns exemplos que podem ser utilizados na coluna "Requisitos" da tabela acima:

- **E-mail seguro**
    - Acesso condicional para o Exchange online/no local
    - Políticas de proteção de aplicações do Outlook
<br></br>
- **Definições do dispositivo**
    - PIN com quatro ou seis carateres
    - Restrição da cópia de segurança na cloud
<br></br>
- **Perfis**
    - Wi-Fi
    - VPN
    - E-mail (Windows 10 Mobile)
<br></br>
- **Aplicações**
    - Office 365 com políticas de proteção de aplicações
    - Linha de negócio (LOB) com políticas de proteção de aplicações

## <a name="next-section"></a>Secção seguinte

A secção seguinte fornece orientações relativas a [como pode desenvolver um plano de implementação do Intune](section-4-develop-a-rollout-plan.md).

