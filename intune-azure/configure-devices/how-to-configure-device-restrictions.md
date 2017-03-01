---
title: "Configurar definições de restrições de dispositivos do Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como utilizar o Intune para configurar definições e funcionalidades nos dispositivos que gere."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 67e3481f9cf01bd1b298cfb26f25d1a3205e0f29
ms.openlocfilehash: 0c22d8a85d90139b3ac17c54668890d5b4c0afe6


---

# <a name="how-to-configure-device-restriction-settings-in-intune-azure-preview"></a>Como configurar definições de restrições de dispositivos na pré-visualização do Azure no Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

As restrições de dispositivos permitem-lhe controlar uma grande variedade de definições e funcionalidades que gere através de um intervalo de categorias, incluindo segurança, browser, hardware e definições de partilha de dados. Por exemplo, pode criar um perfil de restrição de dispositivo para impedir que os utilizadores dos dispositivos iOS de acedam à câmara do dispositivo.

Utilize as informações deste tópico para conhecer as noções básicas sobre como configurar perfis de restrição de dispositivos e, em seguida, leia os tópicos de cada plataforma para saber mais sobre as especificações dos dispositivos.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Criar um perfil de dispositivo com as definições de restrição de dispositivos

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
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
    - [Definições do Android](device-restrictions-for-android.md)
    - [Definições do iOS](device-restrictions-for-ios.md)
    - [Definições do macOS](device-restrictions-for-macos.md)
    - [Definições do Windows Phone 8.1](device-restrictions-for-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-for-windows-8-1.md)
    - [Definições do Windows 10](device-restrictions-for-windows-10.md)
    - [Definições do Windows 10 Team](device-restrictions-for-windows-10-team.md)
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](how-to-assign-device-profiles.md).

## <a name="example-of-device-restriction-settings"></a>Exemplo de definições de restrição de dispositivos

Neste exemplo de alto nível, vai criar uma política de restrição de dispositivos que bloqueia a utilização da aplicação da câmara incorporada em dispositivos Android.

![Como desativar a câmara em dispositivos Android](./media/disable-android-camera.png)




<!--HONumber=Feb17_HO1-->

