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
ms.openlocfilehash: aea4a3d6f8d28e4277435b1d9fc092e68adb9e55
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530314"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Utilizar definições personalizadas para dispositivos Android Enterprise no Microsoft Intune

Utilizar o Microsoft Intune, pode adicionar ou criar definições personalizadas para os seus dispositivos de perfil de trabalho do Android Enterprise com um "perfil personalizado". Os perfis personalizados são uma funcionalidade do Intune. Foram concebidos para adicionar definições e funcionalidades de dispositivos que não estão incorporadas Intune.

Os perfis personalizados do Android Enterprise utilizam as definições Open Mobile Alliance Uniform Resource Identifier (OMA-URI) para controlar funcionalidades em dispositivos Android Enterprise. Estas definições são normalmente utilizadas por fabricantes de dispositivos móveis para controlar essas funcionalidades.

O Intune suporta um número limitado de perfis personalizados do Android Enterprise, incluindo:

- ./Vendor/MSFT/WiFi/Profile/SSID/Settings: [Criar um perfil de Wi-Fi com uma chave pré-partilhada](wi-fi-profile-shared-key.md) tem alguns exemplos.
- ./Vendor/MSFT/VPN/Profile/Name/PackageList: [Criar um perfil VPN por aplicação](android-pulse-secure-per-app-vpn.md) tem alguns exemplos.
- ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste: Consulte a [exemplo](#example) (neste artigo).

Se forem necessárias definições adicionais, veja [OEMConfig do Android Enterprise](android-oem-configuration-overview.md).

Este artigo mostra-lhe como criar um perfil personalizado para dispositivos Android Enterprise. Fornece também um exemplo de um perfil personalizado que bloqueia a funcionalidade de copiar e colar.

## <a name="create-the-profile"></a>Criar o perfil

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: Introduza um nome para o perfil, como `android enterprise custom profile`
    - **Descrição**: Introduza uma descrição para o perfil
    - **Plataforma**: Escolha **Android Enterprise**
    - **Tipo de perfil**: Escolha **personalizado**

4. Em **Definições OMA-URI Personalizadas**, selecione **Adicionar**. Introduza as seguintes definições:

    - **Nome**: Introduza um nome exclusivo para a definição de OMA-URI para que pode encontrá-la facilmente.
    - **Descrição**: Introduza uma descrição que proporcione uma descrição geral da definição e outros detalhes importantes.
    - **OMA-URI**: Introduza o OMA-URI que pretende utilizar como uma definição.
    - **Tipo de dados**: Escolha o tipo de dados que irá utilizar para esta definição de OMA-URI. As opções são:

      - Cadeia
      - Cadeia (ficheiro XML)
      - Data e Hora
      - Número inteiro
      - Vírgula flutuante
      - Booleano
      - Base64 (ficheiro)

    - **Valor**: Introduza o valor de dados que pretende associar ao OMA-URI que introduziu. O valor depende do tipo de dados que selecionou. Por exemplo, se optar por **Data e hora**, selecione o valor num seletor de datas.

    Depois de adicionar algumas definições, pode selecionar **Exportar**. A opção **Exportar** cria uma lista de todos os valores que adicionou num ficheiro de valores separados por vírgulas (.csv).

5. Selecione **OK** para guardar as alterações. Continue a adicionar mais definições conforme necessário.
6. Quanto terminar, selecione **OK** > **Criar** para criar o perfil do Intune. Depois de criado, o perfil é apresentado na lista **Configuração do dispositivo – Perfis**.

## <a name="example"></a>Exemplo

Neste exemplo, irá criar um perfil personalizado que restringe as ações de copiar e colar entre aplicações de trabalho e pessoais em dispositivos Android Enterprise.

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: Introduza um nome para o perfil, como `android ent block copy paste custom profile`.
    - **Descrição**: introduza uma descrição para o perfil.
    - **Plataforma**: Escolher **Android Enterprise**.
    - **Tipo de perfil**: Escolher **personalizado**.

4. Em **Definições OMA-URI Personalizadas**, selecione **Adicionar**. Introduza as seguintes definições:

    - **Nome**: Introduza algo como `Block copy and paste`.
    - **Descrição**: Introduza algo como `Blocks copy/paste between work and personal apps`.
    - **OMA-URI**: Enter `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`.
    - **Tipo de dados**: Escolher **booleano** para que o valor deste OMA-URI é **True** ou **False**.
    - **Valor**: Escolher **True**.

5. Depois de introduzir as definições, o seu ambiente deverá ter um aspeto semelhante à imagem seguinte:

    ![Bloquear a funcionalidade Copiar e Colar para perfis de trabalho do Android.](./media/custom-policy-afw-copy-paste.png)

Ao atribuir este perfil aos dispositivos Android Enterprise que gere, a funcionalidade Copiar e Colar é bloqueada entre aplicações nos perfis de trabalho e pessoais.

## <a name="next-steps"></a>Passos Seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md).

Saiba como [criar o perfil em dispositivos Android](custom-settings-android.md).
