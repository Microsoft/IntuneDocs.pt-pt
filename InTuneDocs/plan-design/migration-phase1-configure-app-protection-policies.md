---
title: "Configurar políticas de proteção de aplicações durante a migração do Intune | Documentos da Microsoft"
description: "O objetivo deste artigo é proporcionar os passos necessários para configurar as políticas de proteção de aplicações durante a migração do Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: f30ab8799b2e049372139c7f9ee7213547736bb0
ms.lasthandoff: 04/14/2017


---

# <a name="phase-1-configure-app-protection-policies-optional"></a>Fase 1: Configurar políticas de proteção de aplicações (opcional)

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

As políticas de proteção de aplicações permitem-lhe encriptar aplicações, definir um PIN quando a aplicação é acedida, impedir que as aplicações sejam executadas em dispositivos com jailbreak ou root, bem como muitos outras proteções. Se o telefone do utilizador for perdido ou roubado, poderá eliminar remota e seletivamente os dados empresariais, mantendo os dados pessoais intactos ao aplicar políticas de proteção de aplicações móveis.

As políticas de proteção de aplicações aplicam a segurança ao nível da aplicação e não precisam da inscrição de dispositivos. Podem ser utilizadas com os dispositivos inscritos ou não no Intune. Além disso, podem ser utilizadas com os dispositivos inscritos num fornecedor de MDM de terceiros.

## <a name="app-protection-policies-with-lob-apps"></a>Políticas de proteção de aplicações com aplicações LOB

Pode também expandir as políticas de proteção de aplicações móveis para as suas aplicações de linha de negócio (LOB) ao tirar partido do [SDK da Aplicação Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management) ou da Microsoft Intune App Wrapping Tool para as plataformas [IOS](https://www.microsoft.com/download/details.aspx?id=45218&751be11f-ede8-5a0c-058c-2ee190a24fa6=True) e [Android](https://www.microsoft.com/download/details.aspx?id=47267).

## <a name="how-do-app-protection-policies-help-during-migration"></a>Como é que as políticas de proteção de aplicações ajudam durante a migração?

A migração precisa de remover dispositivos do fornecedor de MDM antigo e de os inscrever novamente no Intune. Deve planear esta situação e incentivar os utilizadores finais a deixarem o fornecedor de MDM antigo e a inscreverem-se imediatamente no Intune. No entanto, durante a migração podem existir utilizadores que atrasam a conclusão do processo de inscrição e cujos dispositivos não são geridos por qualquer fornecedor de MDM.

Este período poderá deixar a sua organização mais vulnerável ao roubo de dispositivos e à perda de dados empresariais se o acesso a recursos empresariais ainda for permitido e/ou à perda de produtividade do utilizador se o acesso aos recursos da empresa estiver bloqueado.

O Intune pode oferecer proteções de dados empresariais durante a migração para que continue a ter cobertura de segurança para os seus dados empresariais quando não existir qualquer gestão ao nível do dispositivo.

À medida que desativa o acesso condicional no fornecedor de MDM antigo, os utilizadores podem continuar a ser produtivos enquanto os incorpora no Intune.

## <a name="task-list-for-app-protection-policies"></a>Lista de tarefas das políticas de proteção de aplicações

-   Tarefa 1: Saiba [como se preparar para configurar políticas de proteção de aplicações](https://docs.microsoft.com/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

-   Tarefa 2: Saiba [como criar e implementar políticas de proteção de aplicações móveis](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)

## <a name="next-steps"></a>Próximos passos 

[Fase 1: Considerações especiais sobre a migração](https://docs.microsoft.com/intune/plan-design/migration-phase1-special-migration-considerations)

