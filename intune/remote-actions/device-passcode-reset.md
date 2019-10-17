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
ms.openlocfilehash: d7ca53786d372f53d63388fef1179ca271fdb9d9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508584"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Repor ou remover um código de acesso do dispositivo no Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este documento discute a redefinição de senha no nível do dispositivo e a redefinição de senha do perfil de trabalho no Android Enterprise (anteriormente chamado de dispositivos Android for Work ou AfW). É importante observar essa distinção, pois os requisitos de cada um podem variar. Uma reposição de código de acesso ao nível do dispositivo repõe o código de acesso de todo o dispositivo. Uma reposição de código de acesso do perfil de trabalho repõe apenas o código de acesso do perfil de trabalho do utilizador em dispositivos Android Enterprise.

## <a name="supported-platforms-for-device-level-passcode-reset"></a>Plataformas suportadas para reposição de códigos de acesso ao nível do dispositivo

| Platform | Suportado? |
| ---- | ---- |
| Dispositivos Android com a versão 6.X ou anterior | Sim |
| Dispositivos Android Enterprise no modo de quiosque | Sim |
| Dispositivos iOS | Sim |
| dispositivos iOS registrados com o registro de usuário | Não |
| Dispositivos Android registrados com um perfil de trabalho | Não |
| Dispositivos Android com a versão 7.0 ou posterior | Não |
| macOS | Não |
| Windows | Não |

Para dispositivos Android, isso significa que a redefinição de senha no nível do dispositivo só tem suporte em dispositivos que executam o 6. x ou anterior, ou em dispositivos Android Enterprise em execução no modo de quiosque. Isto acontece porque a Google removeu o suporte da reposição de códigos de acesso/palavras-passe para dispositivos Android 7 a partir de uma aplicação concedida ao Administrador de Dispositivos e aplica-se a todos os fornecedores MDM.

## <a name="supported-platforms-for-android-enterprise-work-profile-passcode-reset"></a>Plataformas suportadas para reposição de códigos de acesso do perfil de trabalho do Android Enterprise

| Platform | Suportado? |
| ---- | ---- |
| Dispositivos Android Enterprise inscritos com um perfil de trabalho e com a versão 8.0 e posterior | Sim |
| Dispositivos Android Enterprise inscritos com um perfil de trabalho e com a versão 7.X e anterior | Não |
| Dispositivos Android com a versão 7.X e anterior | Não |

Para criar um novo código de acesso de perfil de trabalho, utilize a ação Repor Código de Acesso. Esta ação solicita uma reposição do código de acesso e cria um código de acesso novo e temporário apenas para o perfil de trabalho. 

## <a name="reset-a-passcode"></a>Repor um código de acesso


1. Entre no [portal do Azure](https://portal.azure.com) com qualquer uma das seguintes funções: Azure Active Directory Administrador Global, Azure Active Directory administrador de serviços do Intune, operador de assistência técnica ou administrador de função.
2. Selecione **Todos os serviços**, filtre por **Intune** e, em seguida, selecione **Microsoft Intune**.
3. Selecione **Dispositivos** e, em seguida, selecione **Todos os dispositivos**.
4. Na lista de dispositivos que gere, selecione um dispositivo e selecione **…Mais**. Em seguida, selecione a ação remota **Remover código de acesso** do dispositivo.

## <a name="reset-android-work-profile-passcodes"></a>Repor códigos de acesso do perfil de trabalho do Android

Os dispositivos Android Enterprise inscritos suportados com um perfil de trabalho recebem uma nova palavra-passe de desbloqueio do perfil gerido ou um desafio de perfil gerido para o utilizador final.

Para dispositivos Android Enterprise com a versão 8.X ou posterior e inscritos com um perfil de trabalho, os utilizadores finais são notificados para ativar o código de acesso de reposição logo após a inscrição estar concluída. A notificação é apresentada se for necessário definir uma palavra-passe de perfil de trabalho. Depois de introduzir o respetivo código de acesso, a notificação é dispensada.


## <a name="remove-ios-passcodes"></a>Remover códigos de acesso do iOS

Em vez de serem repostos, os códigos de acesso são removidos dos dispositivos iOS. Se estiver definida uma política de conformidade de código de acesso, o dispositivo pedirá ao utilizador para definir um novo código de acesso nas Definições.

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, em **Dispositivos**, selecione **Ações do dispositivo**.
