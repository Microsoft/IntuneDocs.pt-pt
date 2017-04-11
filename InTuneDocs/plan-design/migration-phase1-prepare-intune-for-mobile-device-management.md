---
title: "Preparar o Intune para a gestão de dispositivos móveis | Documentos da Microsoft"
description: "O objetivo deste artigo é ajudar os leitores a avaliarem os seus requisitos técnicos e empresariais antes de migrarem para o Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8da2695c4c6dc8b45559323b83a4bb77167303b7
ms.openlocfilehash: 2e7bcedebdf777db64a9ec90aa758822634ed435
ms.lasthandoff: 03/28/2017


---

# <a name="phase-1-prepare-intune-for-mobile-device-management-mdm"></a>Fase 1: Preparar o Intune para a gestão de dispositivos móveis (MDM)

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Antes de explorar os detalhes da configuração do Intune, vamos rever os requisitos da gestão de dispositivos móveis da sua organização. Poderá ser útil executar relatórios de utilizadores ativos no seu fornecedor de MDM atual para identificar os grupos de utilizadores críticos e, em seguida, pode começar a tratar das questões da secção [Avaliar requisitos de MDM](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements).

## <a name="assess-mdm-requirements"></a>Avaliar requisitos de MDM

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>Que tipos de dispositivos precisa de gerir?

-   Que [plataformas](https://docs.microsoft.com/intune/get-started/supported-mobile-devices-and-computers) precisa de suportar?

-   Os dispositivos que precisa de suportar são empresariais ou BYOD?

-   Que tipo de conetividade é utilizada? Wi-Fi, rede móvel, VPN?

### <a name="what-do-your-users-need-to-do-on-managed-devices"></a>O que é que os seus utilizadores precisam de fazer em dispositivos geridos?

-   Precisa de aprovisionar aplicações para os utilizadores finais?

-   Utiliza aplicações de linha de negócio personalizadas? Ou só precisa de aplicações do arquivo público?

-   Precisa de aprovisionar contas de e-mail?

### <a name="what-kinds-of-users"></a>Que tipos de utilizadores?

-   Quantos utilizadores irão utilizar um único dispositivo?

-   Que Termos de Utilização precisa?

    -   Envolva o departamento jurídico neste aspeto desde o início.

    -   Qual é a localização necessária?

-   Os utilizadores estão familiarizados com a tecnologia e a TI em geral?

### <a name="what-is-your-device-security-policy"></a>Qual é a sua política de segurança de dispositivos? 

-   Precisa de encriptação ao nível do dispositivo?

-   Quais são os comprimentos de código de acsesso/PIN do dispositivo?

-   Precisa de desativar funcionalidades do dispositivo ou restringir determinados comportamentos do dispositivo?

    -   Pode controlar uma variedade de definições específicas da plataforma com perfis de configuração de dispositivos, por exemplo: Desativar a câmara, Bloquear no modo de aplicação única.
<br></br>
-   Que tipos de autenticação tem de suportar?

    -   Se precisar de uma autenticação baseada em certificados, que tipos de certificados têm de ser aprovisionados?

        -   O Intune pode aprovisionar certificados com perfis de acesso a recursos para os dispositivos inscritos.
<br></br>
    -   Que tipo de Infraestrutura de Chaves Públicas (PKI) precisa de suportar?
<br></br>
-   Precisa de suportar a Rede Privada Virtual (VPN) ao nível do dispositivo ou da aplicação?

    -   O Intune pode aprovisionar configurações de VPN para fornecedores de VPN de terceiros.
<br></br>
-   Podem ser feitas exceções temporárias para determinados requisitos para evitar o período de indisponibilidade? Ou os dispositivos com acesso cumprem sempre todos os requisitos de segurança?

## <a name="additional-information"></a>Informações adicionais

-   Para obter exemplos mais detalhados, reveja estes [casos práticos](https://customers.microsoft.com/en-US/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune) de setores da indústria diferentes para ver como as organizações avaliaram os respetivos requisitos para a gestão de dispositivos móveis.

## <a name="next-steps"></a>Próximos passos

[Fase 1: Configuração Básica](https://docs.microsoft.com/intune/plan-design/migration-phase1-basic-setup)

