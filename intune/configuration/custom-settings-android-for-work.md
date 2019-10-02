---
title: Adicionar definições personalizadas a dispositivos Android Enterprise no Microsoft Intune – Azure | Microsoft Docs
description: Adicionar ou criar um perfil personalizado para dispositivos Android Enterprise, para criar definições personalizadas no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/01/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: baa202ba5fdb554af56724279456cf43961ff82d
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730916"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Utilizar definições personalizadas para dispositivos Android Enterprise no Microsoft Intune

Usando Microsoft Intune, você pode adicionar ou criar configurações personalizadas para seus dispositivos de perfil de trabalho do Android Enterprise usando um "perfil personalizado". Os perfis personalizados são uma funcionalidade do Intune. Foram concebidos para adicionar definições e funcionalidades de dispositivos que não estão incorporadas Intune.

Os perfis personalizados do Android Enterprise utilizam as definições Open Mobile Alliance Uniform Resource Identifier (OMA-URI) para controlar funcionalidades em dispositivos Android Enterprise. Estas definições são normalmente utilizadas por fabricantes de dispositivos móveis para controlar essas funcionalidades.

O Intune dá suporte a um número limitado de perfis personalizados do Android Enterprise, incluindo:

- ./Vendor/MSFT/WiFi/Profile/SSID/Settings: [Criar um perfil de Wi-Fi com uma chave pré-compartilhada](wi-fi-profile-shared-key.md) tem alguns exemplos.
- ./Vendor/MSFT/VPN/Profile/Name/PackageList: [Criar um perfil de VPN por aplicativo](android-pulse-secure-per-app-vpn.md) tem alguns exemplos.
- ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste: Consulte o [exemplo](#example) (neste artigo).

Se você precisar de configurações adicionais, consulte [OEMConfig para Android Enterprise](android-oem-configuration-overview.md).

Este artigo mostra-lhe como criar um perfil personalizado para dispositivos Android Enterprise. Fornece também um exemplo de um perfil personalizado que bloqueia a funcionalidade de copiar e colar.

## <a name="create-the-profile"></a>Criar o perfil

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: Insira um nome para o perfil, como `android enterprise custom profile`
    - **Descrição**: Insira uma descrição para o perfil
    - **Plataforma**: Escolher **Android Enterprise**
    - **Tipo de perfil**: Escolher **personalizado**

4. Em **Definições OMA-URI Personalizadas**, selecione **Adicionar**. Introduza as seguintes definições:

    - **Nome**: Insira um nome exclusivo para a configuração de OMA-URI para que você possa encontrá-la facilmente.
    - **Descrição**: Insira uma descrição que dê uma visão geral da configuração e quaisquer outros detalhes importantes.
    - **OMA-URI**: Insira o OMA-URI que você deseja usar como uma configuração.
    - **Tipo de dados**: Escolha o tipo de dados que você usará para essa configuração de OMA-URI. As opções são:

      - Cadeia
      - Cadeia (ficheiro XML)
      - Data e Hora
      - Número inteiro
      - Vírgula flutuante
      - Booleano
      - Base64 (ficheiro)

    - **Valor**: Insira o valor de dados que você deseja associar ao OMA-URI que você inseriu. O valor depende do tipo de dados que selecionou. Por exemplo, se optar por **Data e hora**, selecione o valor num seletor de datas.

    Depois de adicionar algumas definições, pode selecionar **Exportar**. A opção **Exportar** cria uma lista de todos os valores que adicionou num ficheiro de valores separados por vírgulas (.csv).

5. Selecione **OK** para guardar as alterações. Continue a adicionar mais definições conforme necessário.
6. Quanto terminar, selecione **OK** > **Criar** para criar o perfil do Intune. Depois de criado, o perfil é apresentado na lista **Configuração do dispositivo – Perfis**.

## <a name="example"></a>Exemplo

Neste exemplo, irá criar um perfil personalizado que restringe as ações de copiar e colar entre aplicações de trabalho e pessoais em dispositivos Android Enterprise.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: Insira um nome para o perfil, como `android ent block copy paste custom profile`.
    - **Descrição**: introduza uma descrição para o perfil.
    - **Plataforma**: Escolha **Android Enterprise**.
    - **Tipo de perfil**: Escolha **personalizado**.

4. Em **Definições OMA-URI Personalizadas**, selecione **Adicionar**. Introduza as seguintes definições:

    - **Nome**: Insira algo como `Block copy and paste`.
    - **Descrição**: Insira algo como `Blocks copy/paste between work and personal apps`.
    - **OMA-URI**: Insira `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`.
    - **Tipo de dados**: Escolha **booliano** para que o valor para esse OMA-URI seja **true** ou **false**.
    - **Valor**: Escolha **verdadeiro**.

5. Depois de introduzir as definições, o seu ambiente deverá ter um aspeto semelhante à imagem seguinte:

    ![Bloquear a funcionalidade Copiar e Colar para perfis de trabalho do Android.](./media/custom-settings-android-for-work/custom-policy-afw-copy-paste.png)

Ao atribuir este perfil aos dispositivos Android Enterprise que gere, a funcionalidade Copiar e Colar é bloqueada entre aplicações nos perfis de trabalho e pessoais.

## <a name="next-steps"></a>Passos seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md).

Saiba como [criar o perfil em dispositivos Android](../custom-settings-android.md).
