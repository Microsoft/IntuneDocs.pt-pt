---
title: Guia de migração da gestão de dispositivos móveis do Intune
titleSuffix: Microsoft Intune
description: Este guia irá orientá-lo ao longo dos vários detalhes relacionados com a migração de um fornecedor de MDM de terceiros para o Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 492b5c0b75bf47f6fbf784939f18964663556315
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505262"
---
# <a name="intune-migration-guide"></a>Guia de migração do Intune

![Imagem do guia de migração da MDM do Microsoft Intune](./media/migration-guide/MDM-migration-guide-art.PNG)

Para efetuar uma migração com êxito para o Microsoft Intune, deverá começar com um plano sólido que tenha em consideração o seu ambiente, os objetivos empresariais e os requisitos técnicos atuais da gestão de dispositivos móveis (MDM). Além disso, tem de incluir os principais intervenientes que irão apoiar e colaborar com o seu plano de migração.

Este guia irá orientá-lo ao longo dos vários detalhes relacionados com a migração de um fornecedor de MDM de terceiros para o Intune.

## <a name="whats-included-in-this-guide"></a>O que está incluído neste guia?

Este guia divide o processo de migração em duas fases, que incluem tarefas, estratégias e orientações táticas que irão ajudar a orientá-lo ao longo do processo completo de migração para o Intune MDM.

- [Fase 1: Preparar o Intune para a gestão de dispositivos móveis](migration-guide-prepare.md)

  - [Avaliar os requisitos de migração da MDM](migration-guide-prepare.md#assess-mdm-requirements)

  - [Configuração básica](migration-guide-setup.md)

  - [Configurar políticas de gestão de aplicações e dispositivos](migration-guide-configure-policies.md)

  - [Configurar políticas de proteção de aplicações](../apps/app-protection-policies.md)

  - [Considerações especiais sobre a migração](migration-guide-considerations.md)

- [Fase 2: campanha de migração](migration-guide-campaign.md)

  - [Plano de comunicação](migration-guide-communication-plan.md)

  - [Conduzir a adoção do usuário final com acesso condicional](migration-guide-drive-adoption.md)

  - [Ciclo de migração típico](migration-guide-cycle.md)
    - [Monitorização da migração](migration-guide-cycle.md#monitoring-migration)
    - [Pós-migração](migration-guide-cycle.md#post-migration)

## <a name="assumptions"></a>Pressupostos

- Já avaliou o Intune num ambiente de prova de conceito (PoC) e decidiu utilizá-lo como a solução de MDM na sua organização.

- Já se familiarizou com o Intune e as respetivas políticas.

## <a name="before-you-begin"></a>Antes de começar

É importante reconhecer que a nova implementação do Intune poderá ser diferente da implementação da MDM antiga. Ao contrário dos serviços de MDM tradicionais, o Intune centra-se no controlo de acesso condicionado por identidade e, por isso, não precisa de um dispositivo de proxy de rede para controlar o acesso a dados empresariais a partir de dispositivos móveis fora perímetro da rede da sua organização. A Microsoft oferece soluções para proteger os serviços de dados na própria cloud através de um conjunto de aplicações de serviços cloud profundamente integrados, coletivamente designado como a oferta Enterprise Client + Security.

- Consulte as [formas comuns de utilizar o Intune](common-scenarios.md).

## <a name="next-steps"></a>Próximos passos

[Fase 1: Preparar o Intune para a gestão de dispositivos móveis](migration-guide-prepare.md)
