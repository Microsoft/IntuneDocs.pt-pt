---
title: Criar um perfil VPN no Microsoft Intune – Azure | Microsoft Docs
description: Para dispositivos iOS, veja os tipos de ligações de rede privada virtual (VPN), crie um perfil de dispositivo VPN no portal do Azure e veja as suas opções para proteger o perfil VPN com certificados ou o nome de utilizador e palavra-passe no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2d0bde56c6622648d47fe47458bdac62d7843ca
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838466"
---
# <a name="create-vpn-profiles-in-intune"></a>Criar perfis VPN no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

As Redes Virtuais Privadas (VPN) permitem-lhe conceder aos seus utilizadores acesso remoto protegido à rede da sua empresa. Os dispositivos utilizam um perfil de ligação VPN para iniciar uma ligação com o servidor VPN. Utilize os **Perfis VPN** no Microsoft Intune para atribuir definições de VPN a utilizadores e dispositivos na sua organização, para que possam ligar-se de forma fácil e segura à rede.

Por exemplo, suponha que pretende aprovisionar todos os dispositivos iOS com as definições necessárias para estabelecer uma ligação a uma partilha de ficheiros na rede da empresa. Crie um perfil VPN que contenha as definições para ligar à rede empresarial. Em seguida, atribua este perfil a todos os utilizadores com dispositivos iOS. Os utilizadores veem a ligação VPN na lista de redes disponíveis e podem ligar-se sem esforço.

Pode utilizar políticas de configuração personalizadas do Intune para criar perfis VPN para as seguintes plataformas:

* Android 4 e posterior
* Dispositivos inscritos com Windows 8.1 e posterior
* Windows Phone 8.1 e posterior
* Computadores inscritos com o Windows 10
* Windows 10 Mobile
* Windows Holographic for Business

## <a name="vpn-connection-types"></a>Tipos de ligação VPN

Pode criar perfis VPN com os seguintes tipos de ligação:

|Tipo de ligação|Android<br>Perfis de trabalho do Android|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|Automático|Não|Não|Não|Não|Não|Sim|
|Check Point Capsule VPN|Sim|Sim|Sim|Sim|Sim|Sim|
|Cisco AnyConnect|Sim|Sim|Sim|Não|Não|Não|
|SonicWall Mobile Connect|Sim|Sim|Sim|Sim|Sim|Sim|
|F5 Edge Client|Sim|Sim|Sim|Sim|Sim|Sim|
|Palo Alto Networks GlobalProtect|Não|Sim|Não|Não|Não|Sim|
|Pulse Secure|Sim|Sim|Sim|Sim|Sim|Sim|
|Cisco (IPSec)|Não|Sim|Não|Não|Não|Não|
|Citrix|Sim (apenas Android)|Sim|Não|Não|Não|Sim|
|IKEv2|Não|Não|Não|Não|Não|Sim|
|L2TP|Não|Não|Não|Não|Não|Sim|
|PPTP|Não|Não|Não|Não|Não|Sim|
|Zscaler|Não|Sim|Não|Não|Não|Não|
|VPN Personalizada|Não|Sim|Sim|Não|Não|Não|

> [!IMPORTANT]
> Para poder utilizar os perfis VPN atribuídos a um dispositivo, tem de instalar a aplicação VPN aplicável ao perfil. Pode utilizar as informações do artigo [O que é a gestão de aplicações do Microsoft Intune?](app-management.md) para ajudá-lo a atribuir a aplicação através do Intune.  

Saiba como criar perfis VPN personalizados com definições URI em [Criar um perfil com definições personalizadas](custom-settings-configure.md).

## <a name="create-a-device-profile-containing-vpn-settings"></a>Criar um perfil de dispositivo com as definições de VPN

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
4. Introduza um **Nome** e uma **Descrição** para o perfil VPN.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições de VPN. Atualmente, pode escolher uma das seguintes plataformas para as definições de dispositivos VPN:
   - **Android**
   - **Android Enterprise**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 e posterior**
   - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, escolha **VPN**.
7. Consoante a plataforma que escolheu, as definições que pode configurar variam. Aceda a um dos seguintes tópicos para definições detalhadas para cada plataforma:
   - [Definições de perfil de trabalho do Android e Android](vpn-settings-android.md)
   - [Definições do iOS](vpn-settings-ios.md)
   - [Definições do macOS](vpn-settings-macos.md)
   - [Definições do Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
   - [Definições do Windows 8.1](vpn-settings-windows-8-1.md)
   - [Definições do Windows 10](vpn-settings-windows-10.md) (incluindo o Windows Holographic for Business)
8. Quando tiver concluído, selecione **Criar** para criar o seu perfil

O perfil será criado e apresentado na lista de perfis. Para atribuir este perfil a grupos, veja [atribuir perfis de dispositivo](device-profile-assign.md).

## <a name="methods-of-securing-vpn-profiles"></a>Métodos para proteger perfis de VPN

Os perfis da VPN podem utilizar vários tipos de ligação e protocolos diferentes de fabricantes diferentes. Normalmente, estas ligações são protegidas através de um de dois métodos.

### <a name="certificates"></a>Certificados

Quando cria o perfil da VPN, pode escolher um perfil de certificado SCEP ou PKCS que tenha criado anteriormente no Intune. Este perfil é conhecido como certificado de identidade. É utilizado para autenticação em relação a um certificado fidedigno (ou um *certificado de raiz*) que deve criar para permitir que o dispositivo do utilizador estabeleça ligação. O certificado fidedigno é atribuído ao computador que irá autenticar a ligação VPN (normalmente, o servidor VPN).

Para obter mais informações sobre como criar e utilizar perfis de certificado no Intune, veja [Como configurar certificados com o Microsoft Intune](certificates-configure.md).

### <a name="user-name-and-password"></a>Nome de utilizador e palavra-passe

O utilizador é autenticado no servidor VPN ao fornecer um nome de utilizador e uma palavra-passe.
