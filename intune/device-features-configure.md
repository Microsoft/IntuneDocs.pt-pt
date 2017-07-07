---
title: "Configurar as definições das funcionalidades dos dispositivos no Intune"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como utilizar o Intune para configurar funcionalidades nos dispositivos que gere."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: f584d76a498264f8ab1cf883f5ee95d52d3446d3
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-configure-device-feature-settings-in-microsoft-intune"></a>Como configurar as definições das funcionalidades dos dispositivos no Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

As restrições do dispositivo permitem-lhe controlar as funcionalidades nos dispositivos iOS e macOS como configurações de dispositivos partilhados, notificações e AirPrint.

Utilize as informações deste tópico para conhecer as noções básicas sobre como configurar perfis de funcionalidades de dispositivos e, em seguida, leia os tópicos de cada plataforma para saber mais sobre as especificações dos dispositivos.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Criar um perfil de dispositivo com as definições de restrição de dispositivos

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de funcionalidades de dispositivos.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições. Atualmente, pode escolher uma das seguintes plataformas para as funcionalidades de dispositivos:
    - **iOS**
    - **macOS**
6. Na lista pendente **Tipo de perfil**, escolha **Funcionalidades de dispositivos**. 
7. As definições que pode configurar diferem consoante a plataforma que escolheu. Aceda a um dos seguintes tópicos para definições detalhadas para cada plataforma:
    - [Definições do AirPrint para iOS e MacOS](air-print-settings-ios-macos.md)
     - [Definições do AirPlay para iOS](airplay-settings-ios.md)
    - [Definições de esquema do ecrã principal para iOS](home-screen-settings-ios.md)
    - [Definições de notificação das aplicações para iOS](app-notification-settings-ios.md)
    - [Definições de configuração de dispositivos partilhados para iOS](shared-device-settings-ios.md)

8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).



