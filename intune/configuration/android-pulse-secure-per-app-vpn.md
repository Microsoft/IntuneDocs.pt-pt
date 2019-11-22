---
title: Personalizar um perfil VPN por aplicação para Android
titleSuffix: Microsoft Intune
description: Saiba como criar um perfil VPN por aplicação para dispositivos Android geridos pelo Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 62f418e396c5030a47ea0bcb31914cd4e1069c40
ms.sourcegitcommit: eb2e420b304c7da9d3be5ef49a676cba66766d2b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74319848"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Utilizar um perfil personalizado do Microsoft Intune para criar um perfil VPN por aplicação para dispositivos Android

Pode criar um perfil VPN por aplicação para dispositivos Android 5.0 e posteriores geridos pelo Intune. Em primeiro lugar, crie um perfil VPN que utilize o tipo de ligação Pulse Secure ou Citrix. Em seguida, crie uma política de configuração personalizada que associe o perfil de VPN a aplicações específicas.

> [!NOTE]
> To use per-app VPN on Android Enterprise devices, you can also use these steps. But, it's recommended to use an [app configuration policy](../apps/app-configuration-policies-use-android.md) for your VPN client app.

Depois de atribuir a política ao seu dispositivo Android ou grupos de utilizadores, os utilizadores devem iniciar o cliente de VPN do Pulse Secure ou Citrix. O cliente de VPN permite apenas tráfego das aplicações especificadas para utilizar a ligação VPN aberta.

> [!NOTE]
>
> Apenas os tipos de ligação Pulse Secure e Citrix são suportados para este perfil.

## <a name="step-1-create-a-vpn-profile"></a>Passo 1: criar um perfil de VPN

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles** > **Create profile**.
3. Introduza as seguintes propriedades:

    - **Name**: Enter a descriptive name for the profile. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. For example, a good profile name is **Android per-app VPN profile for entire company**.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Platform**: Select **Android**.
    - **Profile type**: Select **VPN**.

4. Escolha **Definições** > **Configurar**. Then, configure the VPN profile. For more information, see [How to configure VPN settings](vpn-settings-configure.md) and [Intune VPN settings for Android devices](vpn-settings-android.md).

Tome nota do valor **Nome da Ligação** que especificar ao criar o perfil de VPN. Esse nome será necessário no próximo passo. Por exemplo, **MyAppVpnProfile**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Passo 2: criar uma política de configuração personalizada

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles** > **Create profile**.
3. Introduza as seguintes propriedades:

    - **Name**: Enter a descriptive name for the custom profile. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. For example, a good profile name is **Custom OMA-URI Android VPN profile for entire company**.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Platform**: Select **Android**.
    - **Profile type**: Select **Custom**.

4. Escolha **Definições** > **Configurar**.
5. No painel **Definições OMA-URI personalizadas**, selecione **Adicionar**.
    - **Name**: Enter a name for your setting.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **OMA-URI**: Enter `./Vendor/MSFT/VPN/Profile/*Name*/PackageList`, where *Name* is the connection name you noted in Step 1. In this example, the string is `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList`.
    - **Data type**: Enter **String**.
    - **Value**: Enter a semicolon-separated list of packages to associate with the profile. For example, if you want Excel and the Google Chrome browser to use the VPN connection, enter `com.microsoft.office.excel;com.android.chrome`.

![Exemplo de política personalizada de VPN por aplicação Android](./media/android-pulse-secure-per-app-vpn/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Definir a lista de aplicações como lista de bloqueados ou lista de permitidos (opcional)

Use the **BLACKLIST** value to enter a list of apps that *cannot* use the VPN connection. Todas as outras aplicações são ligadas através da VPN. Or, use the **WHITELIST** value to enter a list of apps that *can* use the VPN connection. Apps that aren't on the list don't connect through the VPN.

1. No painel **Definições OMA-URI personalizadas**, selecione **Adicionar**.
2. Introduza um nome para a definição.
3. In **OMA-URI**, enter `./Vendor/MSFT/VPN/Profile/*Name*/Mode`, where *Name* is the VPN profile name you noted in Step 1. In our example, the string is `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode`.
4. In **Data type**, enter **String**.
5. Em **Valor**, introduza **BLACKLIST** ou **WHITELIST**.

## <a name="step-3-assign-both-policies"></a>Passo 3: atribuir ambas as políticas

[Assign both device profiles](device-profile-assign.md) to the required users or devices.
