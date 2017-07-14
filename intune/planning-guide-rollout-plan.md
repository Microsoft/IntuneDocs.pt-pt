---
title: "Determinar grupos de destino para implementação e períodos de tempo"
description: "Este artigo ajuda-o a decidir quais os grupos para implementar o Intune e os períodos de tempo para essas implementações."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9dda530be47b5449a9c1ed610d8e409fd62148d7
ms.sourcegitcommit: ce363409d1206e4a3d669709863ccc9eb22b7d5f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/11/2017
---
# Desenvolver um plano de implementação
<a id="develop-a-rollout-plan" class="xliff"></a>

O seu plano de implementação identifica os grupos organizacionais que pretende direcionar para a implementação do Intune, o período de tempo de implementação para cada grupo e as abordagens de inscrição que utilizará.

## Grupos de destino e períodos de tempo
<a id="targeted-groups-and-timeframes" class="xliff"></a>

Em primeiro lugar, analise os grupos de destino da sua implementação do Intune e identificados nos seus [cenários de casos de utilização](planning-guide-scenarios.md).

Em segundo lugar, determine o período de tempo para cada grupo de destino. Esta tarefa normalmente exige que uma comunicação entre a equipa de implementação do Intune e os grupos de destino para determinar o intervalo de tempo de implementação mais adequado a cada grupo. Os pontos a serem abordados nessa comunicação incluem:
* Disponibilidade do grupo para a alteração
* Número de utilizadores e dispositivos
* Tipos de plataformas de dispositivos
* Requisitos
* Localização geográfica
* Risco para os negócios

## Fases de implementação
<a id="rollout-phases" class="xliff"></a>
Geralmente, as organizações optam por começar a implementação do Intune com um piloto inicial que visa um pequeno grupo de utilizadores do departamento de TI. O piloto pode ser expandido para incluir um conjunto mais amplo de utilizadores de TI e poderá incluir a participação de outros grupos organizacionais.

### Piloto
<a id="pilot" class="xliff"></a>
A primeira fase da implementação deve visar utilizadores piloto. Os utilizadores piloto devem compreender que são os primeiros utilizadores numa nova solução. Aqueles devem estar dispostos a fornecer feedback para ajudar a melhorar a configuração, a documentação e as notificações, bem como para facilitar o processo para todos os outros utilizadores nas fases posteriores de implementação. Estes utilizadores não devem ser executivos ou VIPs.

O piloto é uma boa oportunidade para testar os [desafios](planning-guide-deployment-goals.md) e refinar os [requisitos](planning-guide-requirements.md) recolhidos anteriormente.

Inclua o plano de [comunicação](planning-guide-communication-plan.md), o plano de [suporte](planning-guide-support-plan.md) e o [teste e validação](planning-guide-test-validation.md) para resolver quaisquer problemas enquanto o impacto para os utilizadores ainda é reduzido.

### Implementação de produção
<a id="production-rollout" class="xliff"></a>
Após um piloto bem-sucedido, está pronto para iniciar uma implementação de produção completa, direcionada para os restantes grupos da sua organização. Alguns exemplos dos diferentes grupos e fases de implementação são:

-   **Departamentos** <br/>Cada departamento pode ser uma fase de implementação. Pode direcionar para um departamento inteiro de cada vez. Neste tipo de implementação, os utilizadores de cada departamento têm tendência para utilizar o dispositivo móvel da mesma forma e aceder às mesmas aplicações. Os utilizadores terão, provavelmente, os mesmos tipos de políticas.

-   **Geografia** <br/>Nesta abordagem, implementa para todos os utilizadores de uma determinada localização geográfica que pode ser o mesmo continente, país, região ou edifício da empresa. Este tipo de implementação faseada permite incidir na localização específica de utilizadores. Tal poderia permitir-lhe uma abordagem mais [meticulosa](#user-assisted-enrollment) devido ao número reduzido de localizações que implementam o Intune em simultâneo. Como é provável que haja departamentos ou casos de utilização no mesmo local, poderão ser implementados casos de utilização diferentes em simultâneo.

-   **Plataforma** <br/>Este tipo de implementação consiste na implementação simultânea em plataformas semelhantes. Por exemplo, poderá implementar o Intune em todos os dispositivos iOS durante o primeiro mês. Em seguida, poderá fazê-lo nos dispositivos Android e, por fim, nos dispositivos Windows. Este tipo de implementação faseada ajuda a simplificar o suporte técnico, pois este teria apenas de fornecer suporte a uma única plataforma de cada vez.

Eis um exemplo de um plano de implementação do Intune que inclui os grupos visados e as linhas cronológicas:

| **Fase de implementação** | **Julho** | **Agosto** | **Setembro** | **Outubro** |
|:---:|:---:|:---:|:---:|:---:|
| Piloto Limitado | TI (50 utilizadores) |  |  |  |                                                         
| Piloto Expandido | TI (200 utilizadores), Executivos de TI (10 utilizadores) |  |  |  |                                                         
| Primeira fase de implementação de produção |  | Departamento de Vendas e Marketing (2000 utilizadores) |  |  |
| Segunda fase de implementação de produção |  |  | Revenda (1000 utilizadores) |  |
| Terceira fase de implementação de produção |  |  |  | RH (50 utilizadores), Finanças (40 utilizadores), Executivos (30 utilizadores) |

Pode [transferir um modelo da tabela acima](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para introduzir as fases de implementação da sua organização.
## Corresponder os grupos de implementação aos métodos de inscrição
<a id="match-rollout-groups-to-enrollment-approaches" class="xliff"></a>

Agora que já determinou os grupos de destino e os intervalos de tempo para a sua implementação do Intune, tem de escolher a abordagem de inscrição no Intune mais adequada a cada grupo. Existem diferentes métodos de inscrição que pode utilizar, incluindo:
* Inscrição self-service do utilizador
* Inscrição do utilizador assistida
* Feira técnica de TI

### Inscrição self-service do utilizador
<a id="user-self-service" class="xliff"></a>

Neste caso, o utilizador é responsável pela inscrição do seu próprio dispositivo, normalmente através de instruções de inscrição fornecidas pela sua organização de TI. Esta abordagem é geralmente utilizada em organizações e é mais dimensionável do que a inscrição do utilizador assistida.

### Inscrição assistida pelo utilizador
<a id="user-assisted-enrollment" class="xliff"></a>

Esta abordagem é conhecido como uma abordagem “meticulosa”. Um membro da equipa de IT ajuda o utilizador ao longo do processo de inscrição, pessoalmente ou através do Skype. Geralmente, esta abordagem é utilizada com a equipa de executivos e com outros grupos que podem necessitar de assistência adicional durante o processo de inscrição.

### Feira técnica de TI
<a id="it-tech-fair" class="xliff"></a>

Em alternativa, pode organizar uma feira técnica de TI para inscrever utilizadores no Intune. Neste evento, o grupo de TI monta um stand de assistência à inscrição no Intune, onde os utilizadores poderiam receber informações sobre a inscrição no Intune, colocar questões e obter assistência relativa ao processo de inscrição. Esta opção pode ser vantajosa tanto para o grupo de TI como para os utilizadores, especialmente durante as fases iniciais da implementação do Intune.

Veja a seguir um exemplo atualizado do plano de implementação do Intune acima referido para incluir as abordagens de inscrição:

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

## Passos seguintes
<a id="next-steps" class="xliff"></a>

A secção seguinte fornece orientações relativas ao [desenvolvimento de um plano de comunicação de implementação do Intune](planning-guide-communication-plan.md).