---
title: "Como configurar as definições de Wi-Fi do Intune"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como utilizar o Intune para configurar ligações Wi-Fi nos dispositivos que gere."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1fadb488-9c6c-43c1-ba23-8c69db633b96
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: aea6d9868d91260dd7a3a4c3b1426f12fcc9f47d
ms.lasthandoff: 02/18/2017


---

# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>Como configurar definições de Wi-Fi no Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Utilize os perfis de Wi-Fi do Microsoft Intune para implementar definições de rede sem fios para utilizadores e dispositivos na sua organização. Quando implementa um perfil Wi-Fi, os utilizadores terão acesso à sua rede Wi-Fi empresarial sem ser preciso que eles o configurem.

Por exemplo, instala uma nova rede Wi-Fi chamada Contoso Wi-Fi e quer configurar todos os dispositivos iOS para se ligarem a esta rede. Eis o processo:

1. Crie um perfil de Wi-Fi que contenha as definições que são precisas para ligar à rede sem fios Contoso Wi-Fi.
2. Atribua o perfil a um grupo que contém todos os utilizadores de dispositivos iOS.
3. Os utilizadores encontrarão a rede nova Contoso Wi-Fi na lista de redes sem fios do dispositivo deles e conseguirão ligar-se facilmente à mesma.

Os perfis de Wi-Fi suportam as seguintes plataformas de dispositivos:

- Android 4 e posterior
- iOS 8.0 e posterior
- macOS (Mac OS X 10.9 e posterior)

Nos dispositivos que executam o Windows 8.1, Windows 10 e Windows 10 Mobile, pode importar uma configuração de Wi-Fi que tenha sido exportada anteriormente a partir de outro dispositivo.

Utilize as informações deste tópico para conhecer as noções básicas sobre como configurar um perfil de Wi-Fi e, em seguida, leia os tópicos de cada plataforma para saber mais sobre as especificações dos dispositivos.

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>Criar um perfil de dispositivo com as definições de Wi-Fi

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configurar dispositivos**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de Wi-Fi.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições de Wi-Fi. Atualmente, pode escolher uma das seguintes plataformas para definições de Wi-Fi:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows 8.1 e posterior (importar um perfil)**
6. Na lista pendente **Tipo de perfil**, escolha **Wi-Fi básico** ou **Wi-Fi empresarial**.
    >[!TIP]
    >Utilize **Wi-Fi básico** para disponibilizar funcionalidades básicas, como o nome da rede e o SSID. O **Wi-Fi empresarial** permite disponibilizar informações mais avançadas, como o Protocolo de Autenticação Extensível (EAP), se a sua rede Wi-Fi o utilizar. A **Importação de Wi-Fi** (para Windows 8.1 e Windows 10) permite-lhe importar definições de Wi-Fi como um ficheiro XML que exportou anteriormente a partir de um dispositivo diferente.
7. As definições que pode configurar diferem consoante a plataforma que escolheu. Aceda a um dos seguintes tópicos para definições detalhadas para cada plataforma:
    - [Definições do Android](wi-fi-for-android.md)
    - [Definições do iOS](wi-fi-for-ios.md)
    - [Definições do macOS](wi-fi-for-macos.md)
    - [Definições do Windows Phone 8.1](wi-fi-import-for-windows-8-1.md)
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](how-to-assign-device-profiles.md).


