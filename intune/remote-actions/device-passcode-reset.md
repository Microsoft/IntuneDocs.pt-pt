---
title: Repor códigos de acesso de dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Remova ou reponha o código de acesso com a ação Remover código de acesso nos dispositivos dos quais faça a gestão ou monitorização com o Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cd6e58efa096c006780c17d991a9ea5da26099d4
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415548"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Repor ou remover um código de acesso do dispositivo no Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este documento discute tanto o reset de código de acesso do dispositivo como o reset de código de código de perfil de trabalho em dispositivos Android enterprise (anteriormente chamados Android for Work, ou AfW). É importante notar esta distinção como requisitos para cada um pode variar. Uma reposição de código de acesso ao nível do dispositivo repõe o código de acesso de todo o dispositivo. Uma reposição de código de acesso do perfil de trabalho repõe apenas o código de acesso do perfil de trabalho do utilizador em dispositivos Android Enterprise.

## <a name="supported-platforms-for-device-level-passcode-reset"></a>Plataformas suportadas para reposição de códigos de acesso ao nível do dispositivo

| Platform | Suportado? |
| ---- | ---- |
| Dispositivos Android com a versão 6.X ou anterior | Sim |
| Dispositivos empresariais Android matriculados como Proprietário de Dispositivos | Sim |
| dispositivos iOS/iPadOS | Sim |
| dispositivos iOS/iPadOS matriculados com inscrição do utilizador | Não |
| Dispositivos Android matriculados com um perfil de trabalho | Não |
| Dispositivos Android com a versão 7.0 ou posterior | Não |
| macOS | Não |
| Windows | Não |

Para dispositivos Android, isto significa que o reset da código de acesso ao nível do dispositivo só é suportado em dispositivos com 6.x ou anteriores, ou em dispositivos empresariais Android que executam no modo Quiosque. Isto acontece porque a Google removeu o suporte da reposição de códigos de acesso/palavras-passe para dispositivos Android 7 a partir de uma aplicação concedida ao Administrador de Dispositivos e aplica-se a todos os fornecedores MDM.

## <a name="supported-platforms-for-android-enterprise-work-profile-passcode-reset"></a>Plataformas suportadas para reposição de códigos de acesso do perfil de trabalho do Android Enterprise

| Platform | Suportado? |
| ---- | ---- |
| Dispositivos Android Enterprise inscritos com um perfil de trabalho e com a versão 8.0 e posterior | Sim |
| Dispositivos Android Enterprise inscritos com um perfil de trabalho e com a versão 7.X e anterior | Não |
| Dispositivos Android com a versão 7.X e anterior | Não |

Para criar um novo código de acesso de perfil de trabalho, utilize a ação Repor Código de Acesso. Esta ação solicita uma reposição do código de acesso e cria um código de acesso novo e temporário apenas para o perfil de trabalho. 

## <a name="reset-a-passcode"></a>Repor um código de acesso


1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) com qualquer uma das seguintes funções: Azure Ative Directory Global Admin, Azure Ative Directory Intune Service Admin, Helpdesk Operator ou Role Administrator.
2. Selecione **Dispositivos** e, em seguida, selecione **Todos os dispositivos**.
3. Na lista de dispositivos que gere, selecione um dispositivo e selecione **…Mais**. Em seguida, selecione a ação remota **Remover código de acesso** do dispositivo.

## <a name="reset-android-work-profile-passcodes"></a>Repor códigos de acesso do perfil de trabalho do Android

Os dispositivos Android Enterprise inscritos suportados com um perfil de trabalho recebem uma nova palavra-passe de desbloqueio do perfil gerido ou um desafio de perfil gerido para o utilizador final.

Para dispositivos Android Enterprise com a versão 8.X ou posterior e inscritos com um perfil de trabalho, os utilizadores finais são notificados para ativar o código de acesso de reposição logo após a inscrição estar concluída. A notificação é apresentada se for necessário definir uma palavra-passe de perfil de trabalho. Depois de introduzir o respetivo código de acesso, a notificação é dispensada.


## <a name="remove-iosipados-passcodes"></a>Remova códigos de acesso iOS/iPadOS

Em vez de serem repostas, as códigos de acesso são removidas dos dispositivos iOS/iPadOS. Se estiver definida uma política de conformidade de código de acesso, o dispositivo pedirá ao utilizador para definir um novo código de acesso nas Definições.

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, em **Dispositivos**, selecione **Ações do dispositivo**.
