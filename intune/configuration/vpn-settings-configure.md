---
title: Adicionar configurações de VPN a dispositivos no Microsoft Intune-Azure | Microsoft Docs
description: Para dispositivos Android, Android Enterprise, iOS, macOS e Windows, use configurações internas para criar conexões de rede virtual privada (VPN) no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9fab50e0aefd926b4dc7a2b3559576642d5d6b79
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059316"
---
# <a name="create-vpn-profiles-to-connect-to-vpn-servers-in-intune"></a>Criar perfis VPN para se conectar a servidores VPN no Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

As VPNs (redes virtuais privadas) oferecem aos usuários acesso remoto seguro à rede da sua organização. Os dispositivos usam um perfil de conexão VPN para iniciar uma conexão com o servidor VPN. **Perfis de VPN** no Microsoft Intune atribuir configurações de VPN a usuários e dispositivos na sua organização, para que eles possam se conectar com facilidade e segurança à sua rede organizacional.

Por exemplo, você deseja configurar todos os dispositivos iOS com as configurações necessárias para se conectar a um compartilhamento de arquivos na rede da organização. Você cria um perfil VPN que inclui essas configurações. Em seguida, atribua esse perfil a todos os usuários que têm dispositivos iOS. Os utilizadores veem a ligação VPN na lista de redes disponíveis e podem ligar-se sem esforço.

> [!NOTE]
> Você pode usar [as políticas de configuração personalizada do Intune](custom-settings-configure.md) para criar perfis de VPN para as seguintes plataformas:
>
> * Android 4 e posterior
> * Dispositivos inscritos com Windows 8.1 e posterior
> * Windows Phone 8.1 e posterior
> * Computadores inscritos com o Windows 10
> * Windows 10 Mobile
> * Windows Holographic for Business

## <a name="vpn-connection-types"></a>Tipos de ligação VPN

Pode criar perfis VPN com os seguintes tipos de ligação:

|Tipo de ligação|Platform|
|-|-|
|Automático|Windows 10|
|Check Point Capsule VPN|-Android<br/>-Perfis de trabalho do Android Enterprise<br/>-iOS<br/>-macOS<br/>-Windows 10<br/>-Windows 8.1<br/>-Windows Phone 8,1|
|Cisco AnyConnect|-Android<br/>-Perfis de trabalho do Android Enterprise<br/>-Proprietário do dispositivo Android Enterprise (totalmente gerenciado)<br/>-iOS<br/>-macOS|
|Cisco (IPSec)|iOS|
|Citrix SSO|-Android<br/>-Perfis de trabalho do Android Enterprise: usar [política de configuração de aplicativo](../apps/app-configuration-policies-use-android.md)<br/>-Proprietário do dispositivo Android Enterprise (totalmente gerenciado): usar [política de configuração de aplicativo](../apps/app-configuration-policies-use-android.md)<br/>-iOS<br/>-Windows 10|
|VPN Personalizada|-iOS<br/>-macOS|
|F5 Access|-Android<br/>-Perfis de trabalho do Android Enterprise<br/>-Proprietário do dispositivo Android Enterprise (totalmente gerenciado)<br/>-iOS<br/>-macOS<br/>-Windows 10<br/>-Windows 8.1<br/>-Windows Phone 8,1|
|IKEv2| -iOS<br/>-Windows 10|
|L2TP|Windows 10|
|Palo Alto Networks GlobalProtect|-Perfis de trabalho do Android Enterprise: usar [política de configuração de aplicativo](../apps/app-configuration-policies-use-android.md)<br/>-iOS<br/>-Windows 10|
|PPTP|Windows 10|
|Pulse Secure|-Android<br/>-Perfis de trabalho do Android Enterprise<br/>-Proprietário do dispositivo Android Enterprise (totalmente gerenciado)<br/>-iOS<br/>-macOS<br/>-Windows 10<br/>-Windows 8.1<br/>-Windows Phone 8,1|
|SonicWall Mobile Connect|-Android<br/>-Perfis de trabalho do Android Enterprise<br/>-iOS<br/>-macOS<br/>-Windows 10<br/>-Windows 8.1<br/>-Windows Phone 8,1|
|Zscaler|-Perfis de trabalho do Android Enterprise: usar [política de configuração de aplicativo](../apps/app-configuration-policies-use-android.md)<br/>-iOS|

> [!IMPORTANT]
> Para poder utilizar os perfis VPN atribuídos a um dispositivo, tem de instalar a aplicação VPN aplicável ao perfil. Pode utilizar as informações do artigo [O que é a gestão de aplicações do Microsoft Intune?](../apps/app-management.md) para ajudá-lo a atribuir a aplicação através do Intune.  

Saiba como criar perfis VPN personalizados com definições URI em [Criar um perfil com definições personalizadas](custom-settings-configure.md).

## <a name="create-a-device-profile"></a>Criar um perfil de dispositivo

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Insira um nome descritivo para o perfil. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. Por exemplo, um bom nome de perfil é o **perfil de VPN para toda a empresa**.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: escolha a plataforma dos seus dispositivos. As opções são:

      - **Android**
      - **Android Enterprise** > **somente proprietário do dispositivo**
      - **Android Enterprise** > **perfil de trabalho somente**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows Phone 8.1**
      - **Windows 8.1 e posterior**
      - **Windows 10 e posterior**

    - **Tipo de perfil**: selecione **VPN**.

4. Consoante a plataforma que escolheu, as definições que pode configurar variam. Consulte os seguintes artigos para obter configurações detalhadas em cada plataforma:

    - [Definições do Android](vpn-settings-android.md)
    - [Configurações do Android Enterprise](vpn-settings-android-enterprise.md)
    - [configurações do iOS/iPadOS](vpn-settings-ios.md)
    - [Definições do macOS](vpn-settings-macos.md)
    - [Definições do Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
    - [Definições do Windows 8.1](vpn-settings-windows-8-1.md)
    - [Definições do Windows 10](vpn-settings-windows-10.md) (incluindo o Windows Holographic for Business)

5. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações.

O perfil é criado e apresentado na lista de perfis. Para atribuir este perfil a grupos, veja [atribuir perfis de dispositivo](device-profile-assign.md).

## <a name="secure-your-vpn-profiles"></a>Proteger seus perfis de VPN

Os perfis da VPN podem utilizar vários tipos de ligação e protocolos diferentes de fabricantes diferentes. Essas conexões são normalmente protegidas por meio dos métodos a seguir.

### <a name="certificates"></a>Certificados

Quando cria o perfil da VPN, pode escolher um perfil de certificado SCEP ou PKCS que tenha criado anteriormente no Intune. Este perfil é conhecido como certificado de identidade. É utilizado para autenticação em relação a um certificado fidedigno (ou um *certificado de raiz*) que deve criar para permitir que o dispositivo do utilizador estabeleça ligação. O certificado fidedigno é atribuído ao computador que irá autenticar a ligação VPN (normalmente, o servidor VPN).

Para obter mais informações sobre como criar e utilizar perfis de certificado no Intune, veja [Como configurar certificados com o Microsoft Intune](../protect/certificates-configure.md).

### <a name="user-name-and-password"></a>Nome de utilizador e palavra-passe

O utilizador é autenticado no servidor VPN ao fornecer um nome de utilizador e uma palavra-passe.

## <a name="next-steps"></a>Próximos passos

O perfil não estará ativo assim que for criado. Em seguida, [atribua o perfil](device-profile-assign.md) a alguns dispositivos.

Você também pode criar e usar VPNs por aplicativo em dispositivos [Android](android-pulse-secure-per-app-vpn.md) e [Ios](vpn-setting-configure-per-app.md) .
