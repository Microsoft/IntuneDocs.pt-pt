---
title: "Configurar as definições de restrição de dispositivos no Intune"
titleSuffix: Azure portal
description: "Saiba como utilizar o Intune para configurar definições e funcionalidades nos dispositivos que gere.\""
keywords: 
author: lleonard-msft
ms.author: alleonar
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
ms.openlocfilehash: b61ad1c0a114c8a66c174fa34c4520e2f6c6244a
ms.sourcegitcommit: af958afce3070a3044aafea490c8afc55301d9df
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-configure-device-restriction-settings-in-microsoft-intune"></a>Como configurar definições de restrições de dispositivos no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

As restrições de dispositivos permitem-lhe controlar uma grande variedade de definições e funcionalidades que gere através de um intervalo de categorias, incluindo segurança, browser, hardware e definições de partilha de dados. Por exemplo, pode criar um perfil de restrição de dispositivo para impedir que os utilizadores dos dispositivos iOS de acedam à câmara do dispositivo.

Utilize as informações deste tópico para conhecer as noções básicas sobre como configurar perfis de restrição de dispositivos e, em seguida, leia os tópicos de cada plataforma para saber mais sobre as especificações dos dispositivos.

Para criar um perfil de dispositivo com as definições de restrição de dispositivos:

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Configurar dispositivos**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de restrição de dispositivos.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições personalizadas. Atualmente, pode escolher uma das seguintes plataformas para definições de restrição de dispositivos:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e posterior**
    - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, escolha **Restrições de dispositivos**. Se quiser criar um perfil de restrições de dispositivos para dispositivos Windows 10 Team, como um Surface Hub, escolha **Restrições de dispositivos (Windows 10 Team)**.
7. As definições que pode configurar diferem consoante a plataforma que escolheu. Aceda a um dos seguintes tópicos para definições detalhadas para cada plataforma:
    - [Definições do Android](device-restrictions-android.md)
    - [Definições do iOS](device-restrictions-ios.md)
    - [Definições do macOS](device-restrictions-macos.md)
    - [Definições do Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Definições do Windows 10](device-restrictions-windows-10.md)
    - [Definições do Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Definições do Android for Work](device-restrictions-android-for-work.md)
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->