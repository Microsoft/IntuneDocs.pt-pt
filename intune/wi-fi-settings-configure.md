---
title: Como configurar as definições de Wi-Fi do Intune
titleSuffix: Microsoft Intune
description: Saiba como utilizar o Microsoft Intune para configurar ligações Wi-Fi em dispositivos que gere.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e2dba6e0d1c50790c8c2c2bf287695ab67fdb972
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905337"
---
# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>Como configurar definições de Wi-Fi no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilize os perfis Wi-Fi do Microsoft Intune para atribuir definições de rede sem fios a utilizadores e dispositivos na sua organização. Quando atribuir um perfil Wi-Fi, os utilizadores terão acesso à sua rede Wi-Fi empresarial sem terem de o configurar.

Por exemplo, instala uma nova rede Wi-Fi chamada Contoso Wi-Fi e quer configurar todos os dispositivos iOS para se ligarem a esta rede. Eis o processo:

1. Crie um perfil de Wi-Fi que contenha as definições que são precisas para ligar à rede sem fios Contoso Wi-Fi.
2. Atribua o perfil a um grupo que contém todos os utilizadores de dispositivos iOS.
3. Os utilizadores encontrarão a rede nova Contoso Wi-Fi na lista de redes sem fios do dispositivo deles e conseguirão ligar-se facilmente à mesma.

## <a name="supported-device-platforms"></a>Plataformas de dispositivos suportadas

Os perfis de Wi-Fi suportam as seguintes plataformas de dispositivos:

- Android 4 e posterior
- Perfis de trabalho do Android
- iOS 8.0 e posterior
- macOS (Mac OS X 10.11 e posterior)

Para dispositivos com o Windows 8.1, Windows 10, Windows 10 Mobile e Windows Holographic for Business, pode importar uma configuração de Wi-Fi que tenha sido anteriormente exportada de outro dispositivo.

Utilize as informações deste tópico para conhecer as noções básicas sobre como configurar um perfil de Wi-Fi e, em seguida, leia os tópicos de cada plataforma para saber mais sobre as especificações dos dispositivos.

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>Criar um perfil de dispositivo com as definições de Wi-Fi

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Configuração do dispositivo**.
2. No painel **Configuração do dispositivo**, na secção **Gerir**, selecione **Perfis**.
3. No painel de perfis, selecione **Criar perfil**.
4. No painel **Criar perfil**, introduza um **Nome** e uma **Descrição** para o perfil de Wi-Fi.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições de Wi-Fi. Atualmente, pode escolher uma das seguintes plataformas para definições de Wi-Fi:
    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e posterior**
    - **Windows 10 e posterior**

   > [!IMPORTANT]
   > Se estiver a criar um perfil para dispositivos com o Windows 10, incluindo o Windows Holographic for Business, tem de selecionar a plataforma **Windows 8.1 e versões posteriores**. A plataforma **Windows 10 e posterior** não incluo um tipo de perfil Wi-Fi. 

6. Para dispositivos Apple ou Android, na lista pendente **Tipo de Wi-Fi**, selecione **Básica** ou **Enterprise**. Pode utilizar a opção **Básica** para disponibilizar funcionalidades básicas, como o nome da rede e o SSID. A opção **Empresarial** permite disponibilizar informações mais avançadas, como o Protocolo de Autenticação Extensível (EAP), se a sua rede Wi-Fi o utilizar. 

   O perfil **Wi-Fi importado** (para Windows 8.1 e versões posteriores) permite-lhe importar definições de Wi-Fi como um ficheiro XML que exportou anteriormente a partir de um dispositivo diferente.
1. As definições que pode configurar diferem consoante a plataforma que escolher. Aceda a um dos seguintes tópicos para definições detalhadas para cada plataforma:
    - [Definições de perfil de trabalho do Android e Android](wi-fi-settings-android.md)
    - [Definições do iOS](wi-fi-settings-ios.md)
    - [Definições do macOS](wi-fi-settings-macos.md)
    - [Windows 8.1 e definições posteriores](wi-fi-settings-import-windows-8-1.md) (incluindo o Windows Holographic for Business)
1. Quando tiver terminado, regresse ao painel **Criar perfil** e clique em **Criar**.

O perfil será criado e apresentado no painel Lista de perfis.

## <a name="next-steps"></a>Próximos passos

Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).
