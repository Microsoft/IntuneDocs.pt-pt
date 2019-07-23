---
title: Adicionar definições personalizadas para dispositivos macOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Exporte definições do macOS com as ferramentas Apple Configurator ou Gestor de Perfis da Apple e, em seguida, importe estas definições para o Microsoft Intune. Essas configurações podem criar, usar e controlar configurações e recursos personalizados em dispositivos macOS. Em seguida, este perfil personalizado pode ser atribuído ou distribuído pelos dispositivos macOS na sua organização, para criar uma linha de base ou um padrão.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0309c5aa73dc8c03cabd69878d55ac51aa6d4f3
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375130"
---
# <a name="use-custom-settings-for-macos-devices-in-microsoft-intune"></a>Utilizar definições personalizadas para dispositivos macOS no Microsoft Intune

Ao utilizar o Microsoft Intune, pode adicionar ou criar definições personalizadas para os seus dispositivos macOS com um "perfil personalizado". Os perfis personalizados são uma funcionalidade do Intune. Foram concebidos para adicionar definições e funcionalidades de dispositivos que não estão incorporadas Intune.

Ao utilizar dispositivos macOS, existem duas formas de obter as definições personalizadas no Intune:

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Gestor de Perfis da Apple](https://support.apple.com/profile-manager)

Pode utilizar estas ferramentas para exportar definições para um perfil de configuração. No Intune, irá importar este ficheiro e, em seguida, atribuir o perfil aos seus utilizadores e dispositivos macOS. Depois de atribuídas, as configurações são distribuídas. Eles também criam uma linha de base ou padrão para macOS em sua organização.

Este artigo fornece algumas diretrizes sobre como usar o Apple Configurator e o Apple Profile Manager e descreve as propriedades que você pode configurar.

## <a name="before-you-begin"></a>Antes de começar

[Crie o perfil](device-profile-create.md).

## <a name="what-you-need-to-know"></a>O que tem de saber

- Ao usar o **Apple** Configurator para criar o perfil de configuração, certifique-se de que as configurações exportadas sejam compatíveis com a versão do MacOS nos dispositivos. Para obter informações sobre como resolver definições incompatíveis, procure **Configuration Profile Reference** (Referência de Perfil de Configuração) e **Mobile Device Management Protocol Reference** (Referência do Protocolo de Gestão de Dispositivos Móveis) no site [Apple Developer](https://developer.apple.com/).

- Ao utilizar o **Gestor de Perfis da Apple**, certifique-se de que:

  - Ativa a [gestão de dispositivos móveis](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) no Gestor de Perfis.
  - Adiciona os [dispositivos macOS](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) no Gestor de Perfis.
  - Depois de adicionar um dispositivo no Gestor de Perfis, aceda a **Under the Library** (Na Biblioteca) > **Devices** (Dispositivos) > selecione o seu dispositivo > **Settings** (Definições). Introduza as definições gerais e de segurança, privacidade, diretório e certificado do dispositivo.

    Transfira e guarde este ficheiro. Irá introduzi-lo no perfil do Intune. 

  - Certifique-se de que as configurações exportadas do Gerenciador de perfis da Apple sejam compatíveis com a versão do macOS nos dispositivos. Para obter informações sobre como resolver definições incompatíveis, procure **Configuration Profile Reference** (Referência de Perfil de Configuração) e **Mobile Device Management Protocol Reference** (Referência do Protocolo de Gestão de Dispositivos Móveis) no site [Apple Developer](https://developer.apple.com/).

## <a name="custom-configuration-profile-settings"></a>Configurações de perfil de configuração personalizadas

- **Nome do perfil de configuração personalizado**: Introduza um nome para a política. Este nome é apresentado no dispositivo e no estado do Intune.
- **Arquivo de perfil de configuração**: Navegue até o perfil de configuração criado usando o Apple Configurator ou o Apple Profile Manager. O ficheiro que importou é apresentado na área **Conteúdos do ficheiro**.

  Você também pode adicionar tokens de dispositivo `.mobileconfig` aos seus arquivos. Os tokens de dispositivo são usados para adicionar informações específicas do dispositivo. Por exemplo, para mostrar o número de série, `{{serialnumber}}`digite. No dispositivo, o texto é exibido de forma `123456789ABC`semelhante a, que é exclusivo para cada dispositivo. Ao inserir variáveis, certifique-se de usar chaves `{{ }}`. Os tokens de [configuração de aplicativo](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) incluem uma lista de variáveis que podem ser usadas. Você também pode usar `deviceid` ou qualquer outro valor específico do dispositivo.

  > [!NOTE]
  > As variáveis não são validadas na interface do usuário e diferenciam maiúsculas de minúsculas. Como resultado, você poderá ver os perfis salvos com entrada incorreta. Por exemplo, se você inserir `{{DeviceID}}` em vez `{{deviceid}}`de, a cadeia de caracteres literal será mostrada em vez da ID exclusiva do dispositivo. Certifique-se de inserir as informações corretas.

Selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e mostrado na lista de perfis.

## <a name="next-steps"></a>Passos seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md).

Saiba como [criar o perfil em dispositivos iOS](custom-settings-ios.md).
