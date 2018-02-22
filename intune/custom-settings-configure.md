---
title: "Como configurar definições de dispositivos personalizadas no Intune"
titleSuffix: Azure portal
description: "Saiba como utilizar o Intune para configurar as definições personalizadas nos dispositivos que gere.\""
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cafcf95cc9025872ce0fbb9605c9d820aa7a19c0
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-configure-custom-device-settings-in-microsoft-intune"></a>Como configurar as definições personalizadas dos dispositivos no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="when-to-use-custom-settings"></a>Quando utilizar as definições personalizadas

As definições personalizadas dos dispositivos podem ser úteis quando o Intune não tem as definições que pretende configurar incorporadas e estão disponíveis a partir de outros perfis de dispositivo.
As definições personalizadas são configuradas de forma diferente para cada plataforma. Por exemplo, com dispositivos Android e Windows, pode especificar valores Open Mobile Alliance Uniform Resource Identifier (OMA-URI) para controlar as funcionalidades nos dispositivos. Para dispositivos Apple, pode importar um ficheiro que criou no [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

Utilize as informações deste tópico para conhecer as noções básicas sobre como configurar perfis com definições personalizadas e, em seguida, leia os tópicos de cada plataforma para saber mais sobre as especificações dos dispositivos.

## <a name="create-a-device-profile-containing-custom-settings"></a>Criar um perfil de dispositivo com as definições personalizadas

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil personalizado.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições personalizadas. Atualmente, pode escolher uma das seguintes plataformas para as definições personalizadas dos dispositivos:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, escolha **Personalizado**.
7. As definições que pode configurar diferem consoante a plataforma que escolher. Aceda a um dos seguintes tópicos para definições detalhadas para cada plataforma:
    - [Definições do Android](custom-settings-android.md)
    - [Definições do iOS](custom-settings-ios.md)
    - [Definições do macOS](custom-settings-macos.md)
    - [Definições do Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
    - [Definições do Windows 10](custom-settings-windows-10.md)
    - [Definições do Windows Holographic for Business](custom-settings-windows-holographic.md)
    - [Definições do Android for Work](custom-settings-android-for-work.md)
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil é criado e apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).
