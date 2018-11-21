---
title: Configurar políticas de proteção de aplicações durante a migração do Intune
titlesuffix: Microsoft Intune
description: Este artigo fornece os passos necessários para configurar as políticas de proteção de aplicações durante uma migração do Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: 7f108af829cd24e3aeff7f6a8210e0be3669b82f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183559"
---
# <a name="configure-app-protection-policies-optional"></a>Configurar políticas de proteção de aplicações (opcional)


As políticas de proteção de aplicações permitem-lhe:
* Encriptar aplicações
* Definir um PIN quando a aplicação for acedida
* Impedir que as aplicações sejam executadas em dispositivos desbloqueados por jailbreak ou por rooting e muitas outras proteções.

Se o telemóvel do utilizador for perdido ou roubado, pode apagar remotamente os dados empresariais de forma seletiva e manter os dados pessoais intactos.

As políticas de proteção de aplicações aplicam a segurança ao nível da aplicação e não precisam da inscrição de dispositivos. Pode utilizá-las com dispositivos que estejam ou não inscritos no Intune. Além disso, pode aplicar estas políticas a dispositivos inscritos num fornecedor de MDM de terceiros.

## <a name="app-protection-policies-with-lob-apps"></a>Políticas de proteção de aplicações com aplicações LOB

Também pode expandir as políticas de proteção de aplicações móveis para as suas aplicações de linha de negócio (LOB) ao utilizar o [SDK da Aplicação Microsoft Intune](app-sdk-get-started.md) ou a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para as plataformas iOS e Android. Para obter mais informações, veja [Ferramenta de Encapsulamento de Aplicações para iOS](app-wrapper-prepare-ios.md) e [Ferramenta de Encapsulamento de Aplicações para Android](app-wrapper-prepare-android.md). Além disso, veja [Preparar aplicações LOB para a proteção de aplicações](apps-prepare-mobile-application-management.md).

## <a name="how-do-app-protection-policies-help-during-migration"></a>Como é que as políticas de proteção de aplicações ajudam durante a migração?

Numa migração, tem de remover dispositivos do fornecedor de MDM antigo e inscrevê-los no Intune. Deve planear esta situação e incentivar os utilizadores finais a deixarem o fornecedor de MDM antigo e a inscreverem-se imediatamente no Intune. No entanto, durante a migração podem existir utilizadores que atrasam a conclusão do processo de inscrição e cujos dispositivos não são geridos por qualquer fornecedor de MDM.

Este período pode deixar a sua organização mais vulnerável a roubos de dispositivos e perda de dados empresariais caso o acesso a recursos empresariais ainda seja permitido. Também poderá levar à redução de produtividade do utilizador caso o acesso a recursos empresariais esteja impedido.

O Intune pode oferecer proteções de dados empresariais durante a migração para que continue a ter cobertura de segurança para os seus dados empresariais quando não existir qualquer gestão ao nível do dispositivo.

À medida que desativa o acesso condicional no fornecedor de MDM antigo, os utilizadores podem continuar a ser produtivos enquanto os incorpora no Intune.

## <a name="task-list-for-app-protection-policies"></a>Lista de tarefas das políticas de proteção de aplicações

1. [Criar uma política de proteção de aplicações](app-protection-policies.md#create-an-app-protection-policy)
2. [Implementar uma política](app-protection-policies.md#deploy-a-policy-to-users)


## <a name="next-steps"></a>Passos Seguintes

[Considerações especiais sobre a migração](migration-guide-considerations.md)
