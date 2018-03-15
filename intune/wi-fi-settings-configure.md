---
title: "Como configurar as definições de Wi-Fi do Intune"
titleSuffix: Microsoft Intune
description: "Saiba como utilizar o Microsoft Intune para configurar ligações Wi-Fi em dispositivos que gere."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/25/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 21bc79d3440e57ec91f7e4482112d77cf233575f
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>Como configurar definições de Wi-Fi no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize os perfis Wi-Fi do Microsoft Intune para atribuir definições de rede sem fios a utilizadores e dispositivos na sua organização. Quando atribuir um perfil Wi-Fi, os utilizadores terão acesso à sua rede Wi-Fi empresarial sem terem de o configurar.

Por exemplo, instala uma nova rede Wi-Fi chamada Contoso Wi-Fi e quer configurar todos os dispositivos iOS para se ligarem a esta rede. Eis o processo:

1. Crie um perfil de Wi-Fi que contenha as definições que são precisas para ligar à rede sem fios Contoso Wi-Fi.
2. Atribua o perfil a um grupo que contém todos os utilizadores de dispositivos iOS.
3. Os utilizadores encontrarão a rede nova Contoso Wi-Fi na lista de redes sem fios do dispositivo deles e conseguirão ligar-se facilmente à mesma.

## <a name="supported-device-platforms"></a>Plataformas de dispositivos suportadas

Os perfis de Wi-Fi suportam as seguintes plataformas de dispositivos:

- Android 4 e posterior
- Android for Work
- iOS 8.0 e posterior
- macOS (Mac OS X 10.9 e posterior)

Para dispositivos com o Windows 8.1, Windows 10, Windows 10 Mobile e Windows Holographic for Business, pode importar uma configuração de Wi-Fi que tenha sido anteriormente exportada de outro dispositivo.

Utilize as informações deste tópico para conhecer as noções básicas sobre como configurar um perfil de Wi-Fi e, em seguida, leia os tópicos de cada plataforma para saber mais sobre as especificações dos dispositivos.

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>Criar um perfil de dispositivo com as definições de Wi-Fi

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de Wi-Fi.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições de Wi-Fi. Atualmente, pode escolher uma das seguintes plataformas para definições de Wi-Fi:
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows 8.1 e posterior (importar um perfil)**

   > [!IMPORTANT]
   > Se estiver a criar um perfil para dispositivos com o Windows 10, incluindo o Windows Holographic for Business, tem de selecionar a plataforma **Windows 8.1 e versões posteriores**. A plataforma **Windows 10 e posterior** não incluo um tipo de perfil Wi-Fi. 

6. Para dispositivos Apple ou Android, na lista pendente **Tipo de Wi-Fi**, selecione **Básica** ou **Enterprise**. Pode utilizar a opção **Básica** para disponibilizar funcionalidades básicas, como o nome da rede e o SSID. A opção **Empresarial** permite disponibilizar informações mais avançadas, como o Protocolo de Autenticação Extensível (EAP), se a sua rede Wi-Fi o utilizar. 

   O perfil **Wi-Fi importado** (para Windows 8.1 e versões posteriores) permite-lhe importar definições de Wi-Fi como um ficheiro XML que exportou anteriormente a partir de um dispositivo diferente.
1. As definições que pode configurar diferem consoante a plataforma que escolher. Aceda a um dos seguintes tópicos para definições detalhadas para cada plataforma:
    - [Definições do Android e Android for Work](wi-fi-settings-android.md)
    - [Definições do iOS](wi-fi-settings-ios.md)
    - [Definições do macOS](wi-fi-settings-macos.md)
    - [Windows 8.1 e definições posteriores](wi-fi-settings-import-windows-8-1.md) (incluindo o Windows Holographic for Business)
1. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil é criado e apresentado no painel da lista de perfis.

## <a name="next-steps"></a>Passos seguintes

Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).
