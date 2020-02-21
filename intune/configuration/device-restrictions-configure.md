---
title: Restringir funcionalidades de dispositivos utilizando a política no Microsoft Intune - Azure  Microsoft Docs
description: Adicione um perfil de dispositivo para restringir funcionalidades nos dispositivos Android, macOS, iOS, iPadOS, Windows Phone e Windows 10 no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53985a9af523ecf60efda5c5c651161c132e326c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511226"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Configurar definições de restrição de dispositivos no Microsoft Intune



Intune inclui políticas de restrição de dispositivos que ajudam os administradores a controlar dispositivos Android, iOS/iPadOS, macOS e Windows. Estas restrições permitem controlar uma vasta gama de configurações e funcionalidades para proteger os recursos da sua organização. Por exemplo, os administradores podem:

- Permitir ou bloquear a câmara do dispositivo
- Controle o acesso ao Google Play, lojas de aplicações, documentos de visualização e jogos
- Bloqueie aplicações incorporadas ou crie uma lista de aplicações que permitissem ou proibissem
- Permitir ou impedir o backup de ficheiros para contas de cloud e armazenamento
- Detete um comprimento mínimo de senha e bloqueie senhas simples

Estas funcionalidades estão disponíveis em Intune e são configuráveis pelo administrador. Intune usa "perfis de configuração" para criar e personalizar estas configurações para as necessidades da sua organização. Depois de adicionar estas funcionalidades num perfil, pode então empurrar ou implementar o perfil para dispositivos da sua organização.

Este artigo mostra-lhe como criar um perfil de restrições de dispositivos. Também pode ver todas as definições disponíveis para as diferentes plataformas.

## <a name="create-the-profile"></a>Criar o perfil

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > Perfis de **Configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome descritivo para a apólice. Atribua nomes às políticas de forma que possa identificá-las facilmente mais tarde. Por exemplo, um bom nome de política é **iOS/iPadOS: Bloquear a câmara nos dispositivos**.
    - **Descrição**: Insira uma descrição para a apólice. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Escolha a plataforma dos seus dispositivos. As opções são:  

        - **Android**
        - **Android Enterprise**
        - **iOS/iPadOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 e posterior**
        - **Windows 10 e posterior**

    - **Tipo de perfil**: Selecione **restrições do dispositivo**.

        Para criar um perfil de restrições de dispositivos para dispositivos da Equipa Windows 10, como o Surface Hub, escolha as restrições do **Dispositivo (Windows 10 Team)** .

4. Consoante a plataforma que escolheu, as definições que pode configurar variam. Escolha a sua plataforma para configurações detalhadas:

    - [Definições do Android](../device-restrictions-android.md)
    - [Configurações empresariais android](../device-restrictions-android-for-work.md)
    - [definições iOS/iPadOS](device-restrictions-ios.md)
    - [Definições do macOS](device-restrictions-macos.md)
    - [Definições do Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Definições do Windows 10](device-restrictions-windows-10.md)
    - [Definições do Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Definições do Windows Holographic for Business](device-restrictions-windows-holographic.md)

5. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações.

O perfil é criado e mostrado na lista de perfis.

## <a name="next-steps"></a>Próximos passos

Depois que o perfil é criado, está pronto para ser atribuído. Em seguida, [atribua o perfil](../device-profile-assign.md) e [monitorize o estado](../device-profile-monitor.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/device-restrictions-configure/disable-android-camera.png)

-->
