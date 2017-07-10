---
title: "Guia de migração da gestão de dispositivos móveis do Intune"
description: "O objetivo deste guia é orientar os clientes ao longo dos vários detalhes relacionados com a migração de um fornecedor de MDM de terceiros para o Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9e86f342413a0f31c51d7a56f862986c433309eb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="intune-migration-guide"></a>Guia de migração do Intune

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

![Imagem do guia de migração da MDM do Intune](./media/MDM-migration-guide-art.PNG)

Para obter uma migração com êxito para o Intune deverá começar com um plano sólido que tenha em consideração o ambiente, os objetivos empresariais e os requisitos técnicos atuais da gestão de dispositivos móveis (MDM). Além disso, tem de ter as principais partes interessadas que irão apoiar e colaborar com o seu plano de migração.

O objetivo deste guia é orientá-lo ao longo dos vários detalhes relacionados com a migração de um fornecedor de MDM de terceiros para o Intune.

## <a name="whats-included-in-this-guide"></a>O que está incluído neste guia?

Este guia inclui duas fases, que incluem tarefas, estratégias e orientações táticas que irão ajudar a orientá-lo ao longo do processo de ponto a ponto de migração para o Intune MDM.

-   [Fase 1: Preparar o Intune para a Gestão de dispositivos móveis] (migration-guide-prepare.md)

    -   [Avaliar os requisitos de migração da MDM](migration-guide-prepare.md#assess-mdm-requirements)

    -   [Configuração básica](migration-guide-setup.md)

    -   [Configurar políticas de gestão de aplicações e dispositivos](migration-guide-configure-policies.md)

    -   [Configurar políticas de proteção de aplicações] (migration-guide-app-protection-policies.md)

    -   [Considerações especiais sobre a migração](migration-guide-considerations.md)

-   [Fase 2: Campanha de migração](migration-guide-campaign.md)

    -   [Plano de Comunicação](migration-guide-communication-plan.md)

    -   [Promover a adoção por parte de utilizadores finais de unidades com acesso condicional](migration-guide-drive-adoption.md)
    
    -   [Ciclo de Migração Típico](migration-guide-cycle.md)
        -   [Monitorização da migração](migration-guide-cycle.md#monitoring-migration)
        -   [Pós-migração](migration-guide-cycle.md#post-migration)

## <a name="assumptions"></a>Pressupostos

-   Já avaliou o Intune num ambiente de prova de conceito (PoC) e decidiu utilizá-lo como a solução de MDM na sua organização.

-   Já se familiarizou com o Intune e as respetivas políticas. 

> [!NOTE]
> Veja o [Guia de avaliação do Intune](/intune-classic/understand-explore/sign-up-for-30-day-trial-microsoft-intune) se quiser conhecer melhor o Intune antes da migração.

## <a name="before-you-begin"></a>Antes de começar

É importante reconhecer que a nova implementação do Intune poderá ser diferente da implementação da MDM antiga. Ao contrário dos serviços de MDM tradicionais, o Intune centra-se no controlo de acesso condicionado por identidade e, por isso, não precisa de um dispositivo de proxy de rede para controlar o acesso a dados empresariais a partir de dispositivos móveis fora perímetro da rede da sua organização. A Microsoft oferece soluções para proteger os serviços de dados na própria cloud através de um conjunto de aplicações de serviços cloud estreitamente integrados, coletivamente designado como a oferta Enterprise Client + Security.

-   Consulte as [formas comuns de utilizar o Intune](migration-guide-prepare.md#assess-mdm-requirements).

## <a name="next-steps"></a>Próximos passos

[Fase 1: Preparar o Intune para a gestão de dispositivos móveis] (migration-guide-prepare.md)
