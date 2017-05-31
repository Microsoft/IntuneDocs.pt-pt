---
title: "Guia de Migração da gestão de dispositivos móveis (MDM) do Intune | Documentos da Microsoft"
description: "O objetivo deste guia é orientar os clientes ao longo dos vários detalhes relacionados com a migração de um fornecedor de MDM de terceiros para o Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: cce6d997c1aad73819b8cfcf31a1505f0ce75923
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="intune-migration-guide"></a>Guia de migração do Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

![Imagem do guia de migração da MDM do Intune](../media/MDM-migration-guide-art.PNG)

Para obter uma migração com êxito para o Intune deverá começar com um plano sólido que tenha em consideração o ambiente, os objetivos empresariais e os requisitos técnicos atuais da MDM. Além disso, tem de ter as principais partes interessadas que irão apoiar e colaborar com o seu plano de migração.

O objetivo deste guia é orientá-lo ao longo dos vários detalhes relacionados com a migração de um fornecedor de MDM de terceiros para o Intune.

## <a name="whats-included-in-this-guide"></a>O que está incluído neste guia?

Este guia inclui duas fases, que incluem tarefas, estratégias e orientações táticas que irão ajudar a orientá-lo ao longo do processo de ponto a ponto de migração para o Intune MDM.

-   [Fase 1: preparar o Intune para a gestão de dispositivos móveis] (/intune-classic/plan-design/migration-phase1-prepare-intune-for-mobile-device-management)

    -   [Avaliar os requisitos de migração da MDM](/intune-classic/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements)

    -   [Configuração básica](/intune-classic/plan-design/migration-phase1-basic-setup)

    -   [Configurar políticas de gestão de aplicações e dispositivos](/intune-classic/plan-design/migration-phase1-configure-device-and-app-management-policies)

    -   [Configurar políticas de proteção de aplicações] (/intune-classic/plan-design/migration-phase1-configure-app-protection-policies)

    -   [Considerações especiais sobre a migração](/intune-classic/plan-design/migration-phase1-special-migration-considerations)

-   [Fase 2: Campanha de migração](/intune-classic/plan-design/migration-phase2-migration-campaign)

    -   [Plano de Comunicação](/intune-classic/plan-design/migration-phase2-communication-plan)

    -   [Promover a adoção por parte de utilizadores finais de unidades com acesso condicional](/intune-classic/plan-design/migration-phase2-drive-end-user-adoption-with-conditional-access)
    
    -   [Ciclo de Migração Típico](/intune-classic/plan-design/migration-phase2-typical-migration-cycle)
        -   [Monitorização da migração](/intune-classic/plan-design/migration-phase2-typical-migration-cycle#monitoring-migration)
        -   [Pós-migração](/intune-classic/plan-design/migration-phase2-typical-migration-cycle#post-migration)

## <a name="assumptions"></a>Pressupostos

-   Já avaliou o Intune num ambiente de prova de conceito (PoC) e decidiu utilizá-lo como a solução de MDM na sua organização.

-   Já se familiarizou com o Intune e as respetivas políticas. 

> [!NOTE]
> Veja o [Guia de avaliação do Intune](/intune-classic/understand-explore/sign-up-for-30-day-trial-microsoft-intune) se quiser conhecer melhor o Intune antes da migração.

## <a name="before-you-begin"></a>Antes de começar

É importante reconhecer que a nova implementação do Intune poderá ser diferente da implementação da MDM antiga. Ao contrário dos serviços de MDM tradicionais, o Intune centra-se no controlo de acesso condicionado por identidade e, por isso, não precisa de um dispositivo de proxy de rede para controlar o acesso a dados empresariais a partir de dispositivos móveis fora perímetro da rede da sua organização. A Microsoft oferece soluções para proteger os serviços de dados na própria cloud através de um conjunto de aplicações de serviços cloud estreitamente integrados, coletivamente designado como a oferta Enterprise Client + Security.

-   Consulte as [formas comuns de utilizar o Intune](/intune-classic/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements).

## <a name="next-steps"></a>Passos seguintes

[Fase 1: preparar o Intune para a gestão de dispositivos móveis] (/intune-classic/plan-design/migration-phase1-prepare-intune-for-mobile-device-management)

