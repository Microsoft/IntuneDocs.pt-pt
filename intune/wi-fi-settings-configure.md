---
title: Criar um perfil Wi-Fi para os dispositivos no Microsoft Intune – Azure | Microsoft Docs
description: Veja os passos para criar um perfil de configuração dos dispositivos de Wi-Fi no Microsoft Intune. Crie perfis para Android, Android Enterprise, Android quiosque, iOS, macOS, Windows 10 e posterior e Windows Holographic for Business. Utilize estes perfis para criar uma ligação Wi-Fi para utilizar certificados, escolher um tipo de EAP, selecionar um método de autenticação, ativar um proxy e mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 75cdd958d9663d5b2d330a947a19963c219feaea
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545927"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Adicionar e utilizar definições de Wi-Fi nos seus dispositivos no Microsoft Intune

O Wi-Fi é uma rede sem fio usada por muitos dispositivos móveis para obter acesso à rede. O Microsoft Intune inclui configurações de Wi-Fi internas que podem ser implantadas para usuários e dispositivos na sua organização. Esse grupo de configurações é chamado de "perfil" e pode ser atribuído a usuários e grupos diferentes. Depois de atribuídas, os usuários obtêm acesso à rede Wi-Fi da sua organização sem configurá-la por conta própria.

Por exemplo, instale uma nova rede Wi-Fi com o nome Contoso Wi-Fi. Em seguida, configure todos os dispositivos iOS para se ligarem a esta rede. Eis o processo:

1. Crie um perfil de Wi-Fi que inclui as configurações que se conectam à rede sem fio contoso Wi-Fi.
2. Atribua o perfil a um grupo que inclui todos os usuários de dispositivos iOS.
3. Os utilizadores encontrarão a nova rede Contoso Wi-Fi na lista de redes sem fios do dispositivo deles. Podem, em seguida, ligar-se à rede através do método de autenticação à sua escolha.

Este artigo lista as etapas para criar um perfil de Wi-Fi. Ele também inclui links que descrevem as diferentes configurações para cada plataforma.

## <a name="supported-device-platforms"></a>Plataformas de dispositivos suportadas

Os perfis de Wi-Fi suportam as seguintes plataformas de dispositivos:

- Android 4 e posterior
- Android Enterprise e quiosque
- iOS 8.0 e posterior
- macOS X 10,11 e mais recente
- Windows 10 e posterior, Windows 10 Mobile e Windows Holographic for Business

> [!NOTE]
> Nos dispositivos que executam o Windows 8.1, pode importar uma configuração de Wi-Fi que tenha sido exportada anteriormente a partir de outro dispositivo.

## <a name="create-a-device-profile"></a>Criar um perfil de dispositivo

1. No [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), selecione **dispositivo** > **perfis** > de configuração**Criar perfil**.
2. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para o perfil. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. Por exemplo, um bom nome de perfil é o **perfil de WiFi para toda a empresa**.
    - **Descrição**: introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: escolha a plataforma dos dispositivos. As opções são:

      - **Android**
      - **Android Enterprise**
      - **iOS**
      - **macOS**
      - **Windows 8.1 e posterior**
      - **Windows 10 e posterior**

    - **Tipo de perfil**: Selecione **Wi-Fi**.

      > [!TIP]
      >
      > - Para dispositivos **Android Enterprise** em execução como um dispositivo dedicado (quiosque), escolha **somente** > proprietário do dispositivo**Wi-Fi**.
      > - Para **Windows 8.1 e posterior**, pode escolher **Importação de Wi-Fi**. Esta opção permite-lhe importar definições de Wi-Fi como um ficheiro XML que exportou anteriormente a partir de um dispositivo diferente.

3. Algumas das definições de Wi-Fi são diferentes para cada plataforma. Para ver as configurações de uma plataforma específica, escolha sua plataforma:

    - [Android](wi-fi-settings-android.md)
    - [Android Enterprise](wi-fi-settings-android-enterprise.md), incluindo dispositivos dedicados
    - [iOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 e posterior](wi-fi-settings-windows.md)
    - [Windows 8.1 e posterior](wi-fi-settings-import-windows-8-1.md), incluindo o Windows Holographic for Business

4. Quando terminar, selecione **Criar perfil** > **criar**.

O perfil é criado e mostrado na lista de perfis (**perfis**de**configuração** > de dispositivo).

## <a name="next-steps"></a>Passos Seguintes

O perfil é criado, mas não faz nada. Em seguida, [atribua esse perfil](device-profile-assign.md) e [monitore seu status.](device-profile-monitor.md)..
