---
title: "Iniciar uma campanha de migração do Intune"
description: "O objetivo deste artigo é proporcionar uma orientação sobre como iniciar uma campanha de migração."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f781b029-50f2-46ee-8ff7-03b4a6719e80
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9690572fd5f17fece0de7b533c98bfc52d77615b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="phase-2-migration-campaign"></a>Fase 2: Campanha de Migração

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

As organizações devem adotar as abordagens de migração mais adequadas às suas necessidades e ajustar as táticas de implementação com base nos seus requisitos específicos. O resto deste guia proporciona as ferramentas de que precisa para alcançar o objetivo de inscrever os dispositivos do utilizador no Intune.

## <a name="keys-to-a-successful-migration"></a>Aspetos essenciais para uma migração com êxito

Estas são as lições essenciais aprendidas ao migrar de um fornecedor de MDM de terceiros para o Intune:

-   A comunicação é fundamental para minimizar o tempo de inatividade do utilizador final e a satisfação.

-   Confirme se tem instruções de migração específicas e concretas.

-   A inscrição de todos os dispositivos geridos tem de ser anulada a partir do seu fornecedor de MDM existente antes da inscrição no Intune.

-   Proporciona uma orientação do fornecedor de MDM existente para os utilizadores finais sobre como anular a inscrição dos respetivos dispositivos.

-   Utilize uma abordagem faseada. Comece com um pequeno grupo de utilizadores piloto e adicione de forma incremental mais grupos de utilizadores até chegar à implementação de escala completa.

-   Monitorize o êxito das inscrições e dos carregamentos do Suporte técnico de cada ciclo. Deixe tempo na agenda para garantir que os critérios de êxito podem ser avaliados para cada grupo antes de migrar a próxima. A implementação piloto deve validar o seguinte:

    -   Se as taxas de êxito e de falha da inscrição estão dentro das expectativas.

    -   Produtividade do utilizador:

        -   Se os recursos da empresa, tais como VPN, Wi-Fi, e-mail e certificados, estão a trabalhar.

        -   Se as Aplicações aprovisionadas estão acessíveis.

    -   Segurança de dados:

        -   Relatórios de conformidade

        -   Proteções de aplicações móveis impostas

-   Quando estiver satisfeito com a primeira fase de migrações, repita o Ciclo de Migração (descrito abaixo em Ciclo de Migração Típico) para a fase seguinte.

-   Repita os ciclos faseados até todos os utilizadores terem migrado para o Intune.

-   Confirme se a equipa de Suporte técnico está pronta para suportar os utilizadores finais ao longo da campanha de migração. Execute uma migração voluntária até poder fazer uma estimativa da carga de trabalho de chamadas de suporte.

-   Não estabeleça prazos para a inscrição enquanto a população restante não puder ser processada pelo Suporte técnico

> [!IMPORTANT] 
> Não configure o Intune e a sua solução de MDM de terceiros existente para aplicar controlos de acesso a recursos, tais como o Exchange ou o SharePoint Online. Além disso, só deve inscrever os dispositivos numa solução de cada vez.

## <a name="next-steps"></a>Próximos passos

[Plano de comunicação](migration-guide-communication-plan.md)
