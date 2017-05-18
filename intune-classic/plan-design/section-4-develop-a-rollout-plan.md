---
title: "Determinar os intervalos de tempo e os grupos visados para a implementação do Intune | Documentos da Microsoft"
description: "Este artigo ajuda a determinar os intervalos de tempo e os grupos visados para a implementação para uma implementação apenas na cloud do Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 2a970badf5ac18a05115a72dc267ee455ba4628d
ms.lasthandoff: 04/25/2017


---

# <a name="develop-an-intune-rollout-plan"></a>Desenvolver um plano de implementação do Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Esta secção ajudá-lo-á a determinar os grupos organizacionais visados para a sua implementação do Intune, bem como o intervalo de tempo de implementação para cada grupo e as abordagens de inscrição que serão utilizadas.

## <a name="determine-intune-rollout-targeted-groups-and-timeframes"></a>Determinar os intervalos de tempo e os grupos visados para a implementação do Intune

É importante começar por identificar os grupos que serão visados para a sua implementação do Intune. Os grupos visados foram anteriormente abordados na secção relativa à identificação de cenários de casos de utilização do Intune deste guia.

Em segundo lugar, terá de determinar o intervalo de tempo para o qual cada grupo será visado para a implementação do Intune. Normalmente, isto exige que a equipa de implementação do Intune comunique entre si e com os grupos visados para determinar o intervalo de tempo de implementação mais adequado a cada grupo.

Por exemplo, a equipa de implementação do Intune poderá abordar fatores, tais como a disposição do grupo para mudar, o número de utilizadores e dispositivos, os tipos de plataformas de dispositivos, os requisitos, a localização geográfica e o risco comercial, para determinar o intervalo de tempo da implementação.

Geralmente, as organizações optam por começar a implementação do Intune com um piloto inicial que visa um pequeno grupo de utilizadores do departamento de TI. Em seguida, o piloto pode ser expandido para incluir um conjunto mais amplo de utilizadores de TI, bem como a participação de outros grupos organizacionais. Após o êxito do piloto, as organizações estão preparadas para iniciar uma implementação de produção total ao visar os restantes grupos da organização. Abaixo encontram-se alguns exemplos de diferentes fases e grupos de implementação:

-   **Piloto:** a primeira fase da implementação deve visar utilizadores piloto. Os utilizadores piloto devem compreender que são as primeiras pessoas a utilizar uma nova solução e devem estar dispostos a fornecer feedback para ajudar a melhorar a configuração, a documentação e as notificações, bem como para facilitar o processo para todos os outros utilizadores nas fases posteriores de implementação. Estes utilizadores não devem ser Executivos ou VIPs.

-   **Departamentos:** cada departamento pode ser uma fase de implementação. Neste cenário, visará um departamento inteiro de uma só vez. Neste tipo de implementação, é muito provável que cada fase utilize o dispositivo móvel da mesma forma e aceda às mesmas aplicações. É muito provável que os utilizadores também tenham os mesmos tipos de política.

-   **Geografia:** este tipo de implementação consiste na implementação para todos os utilizadores de uma determinada localização geográfica que pode ser o mesmo continente, país, região ou edifício da empresa. Este tipo de implementação faseada permite incidir sobre uma localização específica de utilizadores. Isto poderia permitir uma abordagem mais [meticulosa](#user-assisted-enrollment) devido ao número reduzido de localizações que implementam o Intune em simultâneo. Como é provável que haja departamentos ou casos de utilização no mesmo local, poderão ser implementados casos de utilização diferentes em simultâneo.

-   **Plataforma:** este tipo de implementação consiste na implementação simultânea em plataformas semelhantes. Por exemplo, poderá implementar o Intune em todos os dispositivos iOS durante o primeiro mês. Em seguida, poderá fazê-lo nos dispositivos Android e, por fim, nos dispositivos Windows. Este tipo de implementação faseada ajuda a simplificar o suporte técnico. O suporte técnico apenas teria de fornecer suporte relativo a uma única plataforma de cada vez.

Eis um exemplo de um plano de implementação do Intune que inclui os grupos visados e as linhas cronológicas:

| **Fase de implementação** | **Julho** | **Agosto** | **Setembro** | **Outubro** |
|:---:|:---:|:---:|:---:|:---:|
| Piloto Limitado | TI (50 utilizadores) |  |  |  |                                                         
| Piloto Expandido | TI (200 utilizadores), Executivos de TI (10 utilizadores) |  |  |  |                                                         
| Primeira fase de implementação de produção |  | Departamento de Vendas e Marketing (2000 utilizadores) |  |  |
| Segunda fase de implementação de produção |  |  | Revenda (1000 utilizadores) |  |
| Terceira fase de implementação de produção |  |  |  | RH (50 utilizadores), Finanças (40 utilizadores), Executivos (30 utilizadores) |

## <a name="determine-the-intune-enrollment-approach"></a>Determinar a abordagem de inscrição no Intune

Agora que já determinou os grupos visados e os intervalos de tempo para a sua implementação do Intune, tem de escolher a abordagem de inscrição no Intune mais adequada a cada grupo. Existem diferentes abordagens de inscrição que as organizações podem utilizar para implementar o Intune. Algumas das abordagens de inscrição comuns incluem a inscrição self-service do utilizador, a inscrição do utilizador assistida e a feira técnica de TI.

### <a name="user-self-service"></a>Inscrição self-service do utilizador

Nesta abordagem, o utilizador é responsável pela inscrição do seu próprio dispositivo, normalmente através de instruções de inscrição fornecidas pela sua organização de TI. Esta abordagem é geralmente utilizada em organizações e é mais escalável do que a inscrição do utilizador assistida.

### <a name="user-assisted-enrollment"></a>Inscrição do utilizador assistida

Esta é conhecida como a abordagem "meticulosa". Neste caso, um membro da equipa de TI prestaria assistência ao utilizador, presencialmente ou através do Skype, durante o processo de inscrição. Geralmente, esta abordagem é utilizada com a equipa de executivos e com outros grupos que poderão necessitar de assistência adicional durante o processo de inscrição.

### <a name="it-tech-fair"></a>Feira técnica de TI

Em alternativa, pode organizar uma feira técnica de TI para inscrever utilizadores no Intune. Neste evento, o grupo de TI montaria um stand de assistência à inscrição no Intune, onde os utilizadores poderiam receber informações sobre a inscrição no Intune, colocar questões e obter assistência relativa ao processo de inscrição. Esta opção pode ser vantajosa tanto para o grupo de TI como para o utilizador, especialmente durante as fases iniciais da implementação do Intune.

Eis um exemplo de um plano de implementação do Intune com grupos visados, linhas cronológicas e abordagens de inscrição:

| **Fase de implementação** | **Julho** | **Agosto** | **Setembro** | **Outubro** |
|:---:|:---:|:---:|:---:|:---:|
| Piloto Limitado |  |  |  |  |                                                         
| Self-service | TI |  |  |  |
| Piloto Expandido |  |  |  |  |                                                         
| Self-service | TI |  |  |  |
| Abordagem meticulosa | Executivos de TI |  |  |  |
| Primeira fase de implementação de produção |  | Departamento de Vendas e Marketing |  |  |
| Self-service |  | Departamento de Vendas e Marketing |  |  |
| Segunda fase de implementação de produção |  |  | Revenda |  |
| Self-service |  |  |  |  |
| Terceira fase de implementação de produção |  |  | Revenda |  |
| Self-service |  |  |  | RH, Finanças |
| Abordagem meticulosa |  |  |  | Executivos |

## <a name="next-section"></a>Secção Seguinte

A secção seguinte fornece orientações relativas ao [desenvolvimento de um plano de comunicação de implementação do Intune](section-5-develop-a-rollout-communication-plan.md).

