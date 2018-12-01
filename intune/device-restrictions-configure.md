---
title: Configurar definições de restrição de dispositivos no Microsoft Intune – Azure | Microsoft Docs
description: Adicionar um perfil de dispositivo para restringir funcionalidades em dispositivos Android, macOS, iOS, Windows Phone e com o Windows 10 no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 11b241a14ed70a2e999fa505449cd12cdd1e025e
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728791"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Configurar definições de restrição de dispositivos no Microsoft Intune

As restrições do dispositivo permitem-lhe controlar uma vasta gama de definições e funcionalidades que gere em várias categorias, tais como:
- Segurança
- Browser
- Hardware
- Definições de partilha de dados

Por exemplo, pode criar um perfil de restrição do dispositivo para impedir que os utilizadores dos dispositivos iOS acedam à câmara do dispositivo.

Obtenha mais noções básicas sobre perfis de restrição de dispositivos e leia mais artigos sobre cada plataforma para aprender sobre as especificações de cada dispositivo.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Criar um perfil de dispositivo com as definições de restrição de dispositivos

1. Para o [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza um **Nome** e uma **Descrição** para o perfil de restrição de dispositivos.
4. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições personalizadas. Atualmente, pode escolher uma das seguintes plataformas para definições de restrição de dispositivos:

    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e posterior**
    - **Windows 10 e posterior**

5. Na lista pendente **Tipo de perfil**, selecione **Restrições do dispositivo**. Para criar um dispositivo restrições de perfil para dispositivos Windows 10 Team, como o Surface Hub, em seguida, escolha **restrições de dispositivos (Windows 10 Team)**.
6. Consoante a plataforma que escolheu, as definições que pode configurar variam. Escolha a sua plataforma definições detalhadas:

    - [Definições do Android](device-restrictions-android.md)
    - [Definições do Android enterprise](device-restrictions-android-for-work.md)
    - [Definições do iOS](device-restrictions-ios.md)
    - [Definições do macOS](device-restrictions-macos.md)
    - [Definições do Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Definições do Windows 10](device-restrictions-windows-10.md)
    - [Definições do Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Definições do Windows Holographic for Business](device-restrictions-windows-holographic.md)

7. Quando tiver terminado, volte para o **criar perfil** página e selecione **criar**.

O perfil é criado e apresentado na página da lista de perfis. 

## <a name="next-step"></a>Passo seguinte

Depois do perfil é criado, está pronto para ser atribuído. Ver [atribuir perfis de dispositivo](device-profile-assign.md) para obter os passos. 

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
