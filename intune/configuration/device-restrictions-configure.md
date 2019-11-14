---
title: Restringir recursos de dispositivos usando a política no Microsoft Intune-Azure | Microsoft Docs
description: Adicionar um perfil de dispositivo para restringir recursos em dispositivos Android, macOS, iOS, iPadOS, Windows Phone e Windows 10 no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 704da2ee4f0f2e6dce222c89704c83a35368c02c
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059526"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Configurar definições de restrição de dispositivos no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Intune inclui políticas de restrição de dispositivo que ajudam os administradores a controlar dispositivos Android, iOS, macOS e Windows. Essas restrições permitem controlar uma ampla gama de configurações e recursos para proteger os recursos da sua organização. Por exemplo, os administradores podem:

- Permitir ou bloquear a câmera do dispositivo
- Controlar o acesso a Google Play, lojas de aplicativos, exibição de documentos e jogos
- Bloquear aplicativos internos ou criar uma lista de aplicativos que são permitidos ou proibidos
- Permitir ou impedir o backup de arquivos em contas de armazenamento e nuvem
- Definir um comprimento mínimo da senha e bloquear senhas simples

Esses recursos estão disponíveis no Intune e podem ser configurados pelo administrador. O Intune usa "perfis de configuração" para criar e personalizar essas configurações para as necessidades da sua organização. Depois de adicionar esses recursos em um perfil, você pode enviar por Push ou implantar o perfil em dispositivos na sua organização.

Este artigo mostra como criar um perfil de restrições de dispositivo. Você também pode ver todas as configurações disponíveis para as diferentes plataformas.

## <a name="create-the-profile"></a>Criar o perfil

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Insira um nome descritivo para a política. Atribua nomes às políticas de forma que possa identificá-las facilmente mais tarde. Por exemplo, um bom nome de política é **Ios: bloquear câmera em dispositivos**.
    - **Descrição**: Insira uma descrição para a política. Esta definição é opcional, mas recomendada.
    - **Plataforma**: escolha a plataforma dos seus dispositivos. As opções são:  

        - **Android**
        - **Android Enterprise**
        - **iOS/iPadOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 e posterior**
        - **Windows 10 e posterior**

    - **Tipo de perfil**: selecione **restrições de dispositivo**.

        Para criar um perfil de restrições de dispositivo para dispositivos Windows 10 Team, como Surface Hub, escolha **restrições de dispositivo (Windows 10 Team)** .

4. Consoante a plataforma que escolheu, as definições que pode configurar variam. Escolha sua plataforma para configurações detalhadas:

    - [Definições do Android](../device-restrictions-android.md)
    - [Configurações do Android Enterprise](../device-restrictions-android-for-work.md)
    - [configurações do iOS/iPadOS](device-restrictions-ios.md)
    - [Definições do macOS](device-restrictions-macos.md)
    - [Definições do Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Definições do Windows 10](device-restrictions-windows-10.md)
    - [Definições do Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Definições do Windows Holographic for Business](device-restrictions-windows-holographic.md)

5. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações.

O perfil é criado e mostrado na lista de perfis.

## <a name="next-steps"></a>Próximos passos

Depois que o perfil é criado, ele está pronto para ser atribuído. Em seguida, [atribua o perfil](../device-profile-assign.md) e [monitorize o estado](../device-profile-monitor.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/device-restrictions-configure/disable-android-camera.png)

-->
