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
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d85793dcf0ee6fa0186147606c9fd695a268e529
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506972"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Utilizar definições personalizadas para dispositivos Android Enterprise no Microsoft Intune

Usando Microsoft Intune, você pode adicionar ou criar configurações personalizadas para seus dispositivos de perfil de trabalho do Android Enterprise usando um "perfil personalizado". Os perfis personalizados são uma funcionalidade do Intune. Foram concebidos para adicionar definições e funcionalidades de dispositivos que não estão incorporadas Intune.

Os perfis personalizados do Android Enterprise utilizam as definições Open Mobile Alliance Uniform Resource Identifier (OMA-URI) para controlar funcionalidades em dispositivos Android Enterprise. Estas definições são normalmente utilizadas por fabricantes de dispositivos móveis para controlar essas funcionalidades.

O Intune dá suporte a um número limitado de perfis personalizados do Android Enterprise, incluindo:

- ./Vendor/MSFT/WiFi/Profile/SSID/Settings: [criar um perfil de Wi-Fi com uma chave pré-compartilhada](wi-fi-profile-shared-key.md) tem alguns exemplos.
- ./Vendor/MSFT/VPN/Profile/Name/PackageList: [criar um perfil de VPN por aplicativo](android-pulse-secure-per-app-vpn.md) tem alguns exemplos.
- ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste: consulte o [exemplo](#example) (neste artigo).

Se você precisar de configurações adicionais, consulte [OEMConfig para Android Enterprise](android-oem-configuration-overview.md).

Este artigo mostra-lhe como criar um perfil personalizado para dispositivos Android Enterprise. Fornece também um exemplo de um perfil personalizado que bloqueia a funcionalidade de copiar e colar.

## <a name="create-the-profile"></a>Criar o perfil

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: introduza um nome para o perfil, como `android enterprise custom profile`.
    - **Descrição:** introduza uma descrição para o perfil.
    - **Plataforma**: selecione **Android Enterprise**.
    - **Tipo de perfil**: selecione **Personalizado**.

4. Em **Definições OMA-URI Personalizadas**, selecione **Adicionar**. Introduza as seguintes definições:

    - **Nome**: introduza um nome exclusivo para a definição OMA-URI, para poder encontrá-la facilmente.
    - **Descrição**: introduza uma descrição que lhe permita obter uma descrição geral da definição e outros detalhes importantes.
    - **OMA-URI**: introduza o OMA-URI que quer utilizar como uma definição.
    - **Tipo de dados**: selecione o tipo de dados que irá utilizar para esta definição OMA-URI. As opções são:

      - Cadeia
      - Cadeia (ficheiro XML)
      - Data e Hora
      - Número inteiro
      - Vírgula flutuante
      - Booleano
      - Base64 (ficheiro)

    - **Valor**: introduza o valor de dados que pretende associar à definição OMA-URI que introduziu. O valor depende do tipo de dados que selecionou. Por exemplo, se optar por **Data e hora**, selecione o valor num seletor de datas.

    Depois de adicionar algumas definições, pode selecionar **Exportar**. A opção **Exportar** cria uma lista de todos os valores que adicionou num ficheiro de valores separados por vírgulas (.csv).

5. Selecione **OK** para guardar as alterações. Continue a adicionar mais definições conforme necessário.
6. Quanto terminar, selecione **OK** > **Criar** para criar o perfil do Intune. Depois de criado, o perfil é apresentado na lista **Configuração do dispositivo – Perfis**.

## <a name="example"></a>Exemplo

Neste exemplo, irá criar um perfil personalizado que restringe as ações de copiar e colar entre aplicações de trabalho e pessoais em dispositivos Android Enterprise.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: introduza um nome para o perfil, como `android ent block copy paste custom profile`.
    - **Descrição:** introduza uma descrição para o perfil.
    - **Plataforma**: selecione **Android Enterprise**.
    - **Tipo de perfil**: selecione **Personalizado**.

4. Em **Definições OMA-URI Personalizadas**, selecione **Adicionar**. Introduza as seguintes definições:

    - **Nome**: introduza algo como `Block copy and paste`.
    - **Descrição**: introduza algo como `Blocks copy/paste between work and personal apps`.
    - **OMA-URI**: introduza `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`.
    - **Tipo de dados**: selecione **Booleano** para que o valor deste OMA-URI seja **True** ou **False**.
    - **Valor**: selecione **True**.

5. Depois de introduzir as definições, o seu ambiente deverá ter um aspeto semelhante à imagem seguinte:

    ![Bloquear a funcionalidade Copiar e Colar para perfis de trabalho do Android.](./media/custom-settings-android-for-work/custom-policy-afw-copy-paste.png)

Ao atribuir este perfil aos dispositivos Android Enterprise que gere, a funcionalidade Copiar e Colar é bloqueada entre aplicações nos perfis de trabalho e pessoais.

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md).

Saiba como [criar o perfil em dispositivos Android](../custom-settings-android.md).
