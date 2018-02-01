---
title: "Configurar políticas de proteção de aplicações durante a migração do Intune"
description: "Este artigo fornece os passos necessários para configurar as políticas de proteção de aplicações durante uma migração do Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: d3c176b84a8555de245a1f4014c39885e50ab21d
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="configure-app-protection-policies-optional"></a>Configurar políticas de proteção de aplicações (opcional)


As políticas de proteção de aplicações permitem-lhe:
* Encriptar aplicações
* Definir um PIN quando a aplicação for acedida
* Impedir que as aplicações sejam executadas em dispositivos desbloqueados por jailbreak ou por rooting e muitas outras proteções.

Se o telemóvel do utilizador for perdido ou roubado, pode apagar remotamente os dados empresariais de forma seletiva e manter os dados pessoais intactos.

As políticas de proteção de aplicações aplicam a segurança ao nível da aplicação e não precisam da inscrição de dispositivos. Pode utilizá-las com dispositivos que estejam ou não inscritos no Intune. Além disso, pode aplicar estas políticas a dispositivos inscritos num fornecedor de MDM de terceiros.

## <a name="app-protection-policies-with-lob-apps"></a>Políticas de proteção de aplicações com aplicações LOB

Também pode expandir as políticas de proteção de aplicações móveis para as suas aplicações de linha de negócio (LOB) ao utilizar o [SDK da Aplicação Microsoft Intune](app-sdk-get-started.md) ou da Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para as plataformas [iOS](https://www.microsoft.com/download/details.aspx?id=45218&751be11f-ede8-5a0c-058c-2ee190a24fa6=True) e [Android](https://www.microsoft.com/download/details.aspx?id=47267).

## <a name="how-do-app-protection-policies-help-during-migration"></a>Como é que as políticas de proteção de aplicações ajudam durante a migração?

Numa migração, tem de remover dispositivos do fornecedor de MDM antigo e inscrevê-los no Intune. Deve planear esta situação e incentivar os utilizadores finais a deixarem o fornecedor de MDM antigo e a inscreverem-se imediatamente no Intune. No entanto, durante a migração podem existir utilizadores que atrasam a conclusão do processo de inscrição e cujos dispositivos não são geridos por qualquer fornecedor de MDM.

Este período pode deixar a sua organização mais vulnerável a roubos de dispositivos e perda de dados empresariais caso o acesso a recursos empresariais ainda seja permitido. Também poderá levar à redução de produtividade do utilizador caso o acesso a recursos empresariais esteja impedido.

O Intune pode oferecer proteções de dados empresariais durante a migração para que continue a ter cobertura de segurança para os seus dados empresariais quando não existir qualquer gestão ao nível do dispositivo.

À medida que desativa o acesso condicional no fornecedor de MDM antigo, os utilizadores podem continuar a ser produtivos enquanto os incorpora no Intune.

## <a name="task-list-for-app-protection-policies"></a>Lista de tarefas das políticas de proteção de aplicações

1. [Criar uma política de proteção de aplicações](app-protection-policies.md#create-an-app-protection-policy)
2. [Implementar uma política](app-protection-policies.md#deploy-a-policy-to-users)


## <a name="next-steps"></a>Próximos passos

[Considerações especiais sobre a migração](migration-guide-considerations.md)
