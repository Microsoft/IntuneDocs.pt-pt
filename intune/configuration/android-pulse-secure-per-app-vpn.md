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
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74319848"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Utilizar um perfil personalizado do Microsoft Intune para criar um perfil VPN por aplicação para dispositivos Android

Pode criar um perfil VPN por aplicação para dispositivos Android 5.0 e posteriores geridos pelo Intune. Em primeiro lugar, crie um perfil VPN que utilize o tipo de ligação Pulse Secure ou Citrix. Em seguida, crie uma política de configuração personalizada que associe o perfil de VPN a aplicações específicas.

> [!NOTE]
> Para usar a VPN por aplicativo em dispositivos Android Enterprise, você também pode usar estas etapas. Mas é recomendável usar uma política de [configuração de aplicativo](../apps/app-configuration-policies-use-android.md) para seu aplicativo cliente VPN.

Depois de atribuir a política ao seu dispositivo Android ou grupos de utilizadores, os utilizadores devem iniciar o cliente de VPN do Pulse Secure ou Citrix. O cliente de VPN permite apenas tráfego das aplicações especificadas para utilizar a ligação VPN aberta.

> [!NOTE]
>
> Apenas os tipos de ligação Pulse Secure e Citrix são suportados para este perfil.

## <a name="step-1-create-a-vpn-profile"></a>Passo 1: criar um perfil de VPN

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Insira um nome descritivo para o perfil. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. Por exemplo, um bom nome de perfil é o **perfil de VPN por aplicativo Android para toda a empresa**.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: selecione **Android**.
    - **Tipo de perfil**: selecione **VPN**.

4. Escolha **Definições** > **Configurar**. Em seguida, configure o perfil VPN. Para obter mais informações, consulte [como definir configurações de VPN](vpn-settings-configure.md) e [configurações de VPN do Intune para dispositivos Android](vpn-settings-android.md).

Tome nota do valor **Nome da Ligação** que especificar ao criar o perfil de VPN. Esse nome será necessário no próximo passo. Por exemplo, **MyAppVpnProfile**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Passo 2: criar uma política de configuração personalizada

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Insira um nome descritivo para o perfil personalizado. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. Por exemplo, um bom nome de perfil é o **perfil VPN do Android OMA-URI personalizado para toda a empresa**.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: selecione **Android**.
    - **Tipo de perfil**: selecione **personalizado**.

4. Escolha **Definições** > **Configurar**.
5. No painel **Definições OMA-URI personalizadas**, selecione **Adicionar**.
    - **Nome**: Insira um nome para a sua configuração.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **OMA-URI**: Insira `./Vendor/MSFT/VPN/Profile/*Name*/PackageList`, em que *nome* é o nome da conexão que você anotou na etapa 1. Neste exemplo, a cadeia de caracteres é `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList`.
    - **Tipo de dados**: Insira a **cadeia de caracteres**.
    - **Valor**: Insira uma lista de pacotes separados por ponto e vírgula para associar ao perfil. Por exemplo, se você quiser que o Excel e o navegador Google Chrome usem a conexão VPN, digite `com.microsoft.office.excel;com.android.chrome`.

![Exemplo de política personalizada de VPN por aplicação Android](./media/android-pulse-secure-per-app-vpn/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Definir a lista de aplicações como lista de bloqueados ou lista de permitidos (opcional)

Use o valor de lista de **bloqueios** para inserir uma listagem de aplicativos que *não podem* usar a conexão VPN. Todas as outras aplicações são ligadas através da VPN. Ou use **o valor da lista de** permissões para inserir uma lista de aplicativos que *podem* usar a conexão VPN. Os aplicativos que não estão na lista não se conectam por meio da VPN.

1. No painel **Definições OMA-URI personalizadas**, selecione **Adicionar**.
2. Introduza um nome para a definição.
3. Em **OMA-URI**, insira `./Vendor/MSFT/VPN/Profile/*Name*/Mode`, em que *nome* é o nome do perfil VPN que você anotou na etapa 1. Em nosso exemplo, a cadeia de caracteres é `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode`.
4. Em **tipo de dados**, insira **cadeia de caracteres**.
5. Em **Valor**, introduza **BLACKLIST** ou **WHITELIST**.

## <a name="step-3-assign-both-policies"></a>Passo 3: atribuir ambas as políticas

[Atribua ambos os perfis de dispositivo](device-profile-assign.md) aos usuários ou dispositivos necessários.
