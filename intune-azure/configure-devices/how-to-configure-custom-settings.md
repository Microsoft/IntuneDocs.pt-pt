---
title: "Como configurar as definições personalizadas dos dispositivos do Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como utilizar o Intune para configurar as definições personalizadas nos dispositivos que gere."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/23/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 89afae81076d563f4ebba289f8fa82eaea6ab234
ms.openlocfilehash: b404df57e94afe7b80dd39163ed72a24d8b05508


---

# <a name="how-to-configure-custom-device-settings"></a>Como configurar as definições personalizadas dos dispositivos

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="when-to-use-custom-settings"></a>Quando utilizar as definições personalizadas

As definições personalizadas dos dispositivos podem ser úteis quando o Intune não tem as definições que pretende configurar incorporadas e estão disponíveis a partir de outros perfis de dispositivo.
As definições personalizadas são configuradas de forma diferente para cada plataforma. Por exemplo, com dispositivos Android e Windows, pode especificar valores Open Mobile Alliance Uniform Resource Identifier (OMA-URI) para controlar as funcionalidades nos dispositivos. Para dispositivos Apple, pode importar um ficheiro que criou no [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

Utilize as informações deste tópico para conhecer as noções básicas sobre como configurar perfis com definições personalizadas e, em seguida, leia os tópicos de cada plataforma para saber mais sobre as especificações dos dispositivos.

## <a name="create-a-device-profile-containing-custom-settings"></a>Criar um perfil de dispositivo com as definições personalizadas

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configurar dispositivos**.
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
7. As definições que pode configurar diferem consoante a plataforma que escolheu. Aceda a um dos seguintes tópicos para definições detalhadas para cada plataforma:
    - [Definições do Android](custom-for-android.md)
    - [Definições do iOS](custom-for-ios.md)
    - [Definições do macOS](custom-for-macos.md)
    - [Definições do Windows Phone 8.1](custom-for-windows-phone-8-1.md)
    - [Definições do Windows 10](custom-for-windows-10.md)
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](how-to-assign-device-profiles.md).




<!--HONumber=Feb17_HO1-->

