---
title: Criar um perfil Wi-Fi para os dispositivos no Microsoft Intune – Azure | Microsoft Docs
description: Veja os passos para criar um perfil de configuração dos dispositivos de Wi-Fi no Microsoft Intune. Crie perfis para Android, Android Enterprise, Quiosque do Android, iOS, macOS, Windows 10 e posterior e Windows Holographic for Business. Utilize estes perfis para criar uma ligação Wi-Fi para utilizar certificados, escolher um tipo de EAP, selecionar um método de autenticação, ativar um proxy e mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a338cce6249cc7c5214a9d69a897cad3eaa09e93
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188403"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Adicionar e utilizar definições de Wi-Fi nos seus dispositivos no Microsoft Intune

Utilize os perfis Wi-Fi do Microsoft Intune para atribuir definições de rede sem fios a utilizadores e dispositivos na sua organização. Quando atribui um perfil Wi-Fi, os utilizadores podem aceder à rede de Wi-Fi da sua organização sem precisarem de a configurar.

Por exemplo, instale uma nova rede Wi-Fi com o nome Contoso Wi-Fi. Em seguida, configure todos os dispositivos iOS para se ligarem a esta rede. Eis o processo:

1. Crie um perfil de Wi-Fi que inclua as definições que são precisas para ligar à rede sem fios Contoso Wi-Fi.
2. Atribua o perfil a um grupo que contém todos os utilizadores de dispositivos iOS.
3. Os utilizadores encontrarão a nova rede Contoso Wi-Fi na lista de redes sem fios do dispositivo deles. Podem, em seguida, ligar-se à rede através do método de autenticação à sua escolha.

Utilize os passos neste artigo para criar um perfil Wi-Fi. Em seguida, reveja tópicos sobre detalhes e definições específicos da plataforma.

## <a name="supported-device-platforms"></a>Plataformas de dispositivos suportadas

Os perfis de Wi-Fi suportam as seguintes plataformas de dispositivos:

- Android 4 e posterior
- Android Enterprise e quiosque
- iOS 8.0 e posterior
- macOS (Mac OS X 10.11 e posterior)
- Windows 10 e posterior, Windows 10 Mobile e Windows Holographic for Business

> [!NOTE]
> Nos dispositivos que executam o Windows 8.1, pode importar uma configuração de Wi-Fi que tenha sido exportada anteriormente a partir de outro dispositivo.

## <a name="create-a-wi-fi-device-profile"></a>Criar um perfil Wi-FI do dispositivo

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços** > filtre o **Intune** e selecione **Microsoft Intune**. 
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza um **Nome** e uma **Descrição** para o perfil Wi-Fi.
4. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições de Wi-Fi. As opções são:

    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e posterior**
    - **Windows 10 e posterior**

5. Em **Tipo de Perfil**, escolha **Wi-Fi**.

    - Para os dispositivos **Android Enterprise** em execução como um quiosque, pode escolher **Proprietário do dispositivo apenas** > **Wi-Fi**.
    - Para **Windows 8.1 e posterior**, pode escolher **Importação de Wi-Fi**. Esta opção permite-lhe importar definições de Wi-Fi como um ficheiro XML que exportou anteriormente a partir de um dispositivo diferente.

6. Algumas das definições de Wi-Fi são diferentes para cada plataforma. Para ver as definições de uma plataforma específica, escolha:

    - [Android](wi-fi-settings-android.md)
    - [Android Enterprise e quiosque](wi-fi-settings-android-enterprise.md)
    - [iOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 e posterior](wi-fi-settings-windows.md)
    - [Windows 8.1 e posterior](wi-fi-settings-import-windows-8-1.md), incluindo o Windows Holographic for Business

    A maioria das plataformas têm as definições **Básica** e **Empresarial**. **Básica** inclui funcionalidades como o nome da rede e o SSID. **Empresarial** permite disponibilizar informações mais avançadas, como o Protocolo de Autenticação Extensível (EAP).

7. Quando terminar de adicionar as definições de Wi-Fi, selecione **Criar Perfil** > **Criar** para adicionar o perfil de configuração. O perfil é criado e é apresentado na lista de perfis (**Configuração do dispositivo** > **Perfis**).

## <a name="next-steps"></a>Passos Seguintes

O perfil é criado, mas não faz nada. Em seguida, [atribua este perfil](device-profile-assign.md).
