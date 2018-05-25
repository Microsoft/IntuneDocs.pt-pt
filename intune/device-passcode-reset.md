---
title: Repor códigos de acesso de dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Remova ou reponha o código de acesso com a ação Remover código de acesso nos dispositivos dos quais faça a gestão ou monitorização com o Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5783558a768e1d58087168f81ad27e5acf9aae09
ms.sourcegitcommit: 91802e78cd5014d20a828ca25a54a381d452f0f8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Repor ou remover um código de acesso do dispositivo no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para criar um novo código de acesso para um dispositivo, utilize a ação **Remover código de acesso**.

## <a name="supported-platforms"></a>Plataformas suportadas

- Dispositivos Android inscritos com um Perfil de Trabalho com a versão 7.0 e posterior
- Dispositivos Android com a versão 6.0 ou anterior
- iOS 
     
## <a name="unsupported-platforms"></a>Plataformas não suportadas

- Dispositivos Android inscritos com um Perfil de Trabalho com a versão 6.0 e anterior
- Dispositivos Android com a versão 7.0 ou posterior
- macOS
- Windows

## <a name="reset-a-passcode"></a>Repor um código de acesso

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e, em seguida, selecione **Microsoft Intune**.
3. Selecione **Dispositivos** e, em seguida, selecione **Todos os dispositivos**.
4. Na lista de dispositivos que gere, selecione um dispositivo e selecione **…Mais**. Em seguida, selecione a ação remota **Remover código de acesso** do dispositivo.

## <a name="resetting-android-for-work-passcodes"></a>Repor códigos de acesso do Android for Work

Os dispositivos Android for Work suportados recebem uma nova palavra-passe de desbloqueio do perfil gerido ou um desafio de perfil gerido para o utilizador final. Para dispositivos Android 7.0 ou posterior com Perfis de Trabalho, os utilizadores finais receberão notificações para ativar o respetivo token de reposição de código de acesso imediatamente após a inscrição estar concluída. A notificação é apresentada se for necessário definir uma palavra-passe de Perfil de Trabalho. Depois de introduzir o respetivo código de acesso, a notificação é dispensada.

## <a name="resetting-ios-passcodes"></a>Repor códigos de acesso em iOS

Os códigos de acesso são removidos dos dispositivos iOS. Se estiver definida uma política de conformidade de código de acesso, o dispositivo pedirá ao utilizador para definir um novo código de acesso nas Definições. 

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, em **Dispositivos**, selecione **Ações do dispositivo**.
