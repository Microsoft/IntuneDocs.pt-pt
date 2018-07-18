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
ms.openlocfilehash: a233c62b76901d9bad00aa6d8b2a8a4dd45dea96
ms.sourcegitcommit: 024cce10a99b12a13f32d3995b69c290743cafb8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/14/2018
ms.locfileid: "39039306"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Repor ou remover um código de acesso do dispositivo no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para criar um novo código de acesso para um dispositivo, utilize a ação **Remover código de acesso**. Esta ação pede uma reposição do PIN apenas do perfil de trabalho. As reposições de PIN dos dispositivos não são suportadas para perfis de trabalho do Android.

## <a name="work-profile-pin-reset-supported-platforms"></a>Plataformas que suportam a reposição de PIN do perfil de trabalho

- Dispositivos Android inscritos com um perfil de trabalho com a versão 8.0 e posterior 
- Dispositivos Android com a versão 6.0 ou anterior
- Dispositivos de quiosque Android Enterprise
- iOS 
     
## <a name="unsupported-platforms"></a>Plataformas não suportadas

- Dispositivos Android inscritos com um Perfil de Trabalho com a versão 7.0 e anterior
- Dispositivos Android com a versão 7.0 ou posterior
- macOS
- Windows

## <a name="reset-a-passcode"></a>Repor um código de acesso

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e, em seguida, selecione **Microsoft Intune**.
3. Selecione **Dispositivos** e, em seguida, selecione **Todos os dispositivos**.
4. Na lista de dispositivos que gere, selecione um dispositivo e selecione **…Mais**. Em seguida, selecione a ação remota **Remover código de acesso** do dispositivo.

## <a name="resetting-android-work-profile-passcodes"></a>Repor códigos de acesso do perfil de trabalho do Android

Os dispositivos com perfil de trabalho do Android suportados recebem uma nova palavra-passe de desbloqueio do perfil gerido ou um desafio de perfil gerido para o utilizador final. 

Para os dispositivos com perfil de trabalho do Android 8.0, os utilizadores finais são notificados para ativar o respetivo código de acesso após a conclusão da inscrição. A notificação é apresentada se for necessário definir uma palavra-passe de Perfil de Trabalho. Depois de introduzir o respetivo código de acesso, a notificação é dispensada.

## <a name="resetting-ios-passcodes"></a>Repor códigos de acesso em iOS

Os códigos de acesso são removidos dos dispositivos iOS. Se estiver definida uma política de conformidade de código de acesso, o dispositivo pedirá ao utilizador para definir um novo código de acesso nas Definições. 

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, em **Dispositivos**, selecione **Ações do dispositivo**.
