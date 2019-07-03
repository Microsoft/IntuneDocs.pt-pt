---
title: Adicionar definições personalizadas para dispositivos macOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Exporte definições do macOS com as ferramentas Apple Configurator ou Gestor de Perfis da Apple e, em seguida, importe estas definições para o Microsoft Intune. Estas definições podem criar, utilizar e controlar as definições personalizadas e funcionalidades em dispositivos macOS. Em seguida, este perfil personalizado pode ser atribuído ou distribuído pelos dispositivos macOS na sua organização, para criar uma linha de base ou um padrão.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04671df820fee96d4090b13f6fa8f6c4f983a1ac
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530225"
---
# <a name="use-custom-settings-for-macos-devices-in-microsoft-intune"></a>Utilizar definições personalizadas para dispositivos macOS no Microsoft Intune

Ao utilizar o Microsoft Intune, pode adicionar ou criar definições personalizadas para os seus dispositivos macOS com um "perfil personalizado". Os perfis personalizados são uma funcionalidade do Intune. Foram concebidos para adicionar definições e funcionalidades de dispositivos que não estão incorporadas Intune.

Ao utilizar dispositivos macOS, existem duas formas de obter as definições personalizadas no Intune:

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Gestor de Perfis da Apple](https://support.apple.com/profile-manager)

Pode utilizar estas ferramentas para exportar definições para um perfil de configuração. No Intune, irá importar este ficheiro e, em seguida, atribuir o perfil aos seus utilizadores e dispositivos macOS. Uma vez atribuídas, as definições são distribuídas e criam também uma linha de base ou um padrão para o macOS na sua organização.

Este artigo mostra-lhe como criar um perfil personalizado para dispositivos macOS. Também fornece algumas orientações sobre como utilizar o Apple Configurator e o Gestor de Perfis da Apple.

## <a name="before-you-begin"></a>Antes de começar

- Ao utilizar o **Apple Configurator** para criar o perfil de configuração, certifique-se de que as definições exportadas são compatíveis com a versão do macOS nos dispositivos que está a utilizar. Para obter informações sobre como resolver definições incompatíveis, procure **Configuration Profile Reference** (Referência de Perfil de Configuração) e **Mobile Device Management Protocol Reference** (Referência do Protocolo de Gestão de Dispositivos Móveis) no site [Apple Developer](https://developer.apple.com/).

- Ao utilizar o **Gestor de Perfis da Apple**, certifique-se de que:

  - Ativa a [gestão de dispositivos móveis](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) no Gestor de Perfis.
  - Adiciona os [dispositivos macOS](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) no Gestor de Perfis.
  - Depois de adicionar um dispositivo no Gestor de Perfis, aceda a **Under the Library** (Na Biblioteca) > **Devices** (Dispositivos) > selecione o seu dispositivo > **Settings** (Definições). Introduza as definições gerais e de segurança, privacidade, diretório e certificado do dispositivo.

    Transfira e guarde este ficheiro. Irá introduzi-lo no perfil do Intune. 

  - Certifique-se de que as definições exportadas do Gestor de Perfis da Apple são compatíveis com a versão do macOS nos dispositivos que está a utilizar. Para obter informações sobre como resolver definições incompatíveis, procure **Configuration Profile Reference** (Referência de Perfil de Configuração) e **Mobile Device Management Protocol Reference** (Referência do Protocolo de Gestão de Dispositivos Móveis) no site [Apple Developer](https://developer.apple.com/).

## <a name="create-the-profile"></a>Criar o perfil

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: Introduza um nome para o perfil, como `macos custom profile`.
    - **Descrição**: introduza uma descrição para o perfil.
    - **Plataforma**: Escolher **macOS**.
    - **Tipo de perfil**: Escolher **personalizado**.

4. Em **Configuração personalizada**, introduza as seguintes definições:

    - **Nome do perfil de configuração personalizada**: Introduza um nome para a política. Este nome é apresentado no dispositivo e no estado do Intune.
    - **Ficheiro de perfil de configuração**: Navegue até ao perfil de configuração que criou com o Apple Configurator nem o Gerenciador de perfis do Apple. O ficheiro que importou é apresentado na área **Conteúdos do ficheiro**.

5. Selecione **OK** > **Criar** para criar o perfil do Intune. Depois de criado, o perfil é apresentado na lista **Configuração do dispositivo – Perfis**.

## <a name="next-steps"></a>Passos Seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md).

Saiba como [criar o perfil em dispositivos iOS](custom-settings-ios.md).
