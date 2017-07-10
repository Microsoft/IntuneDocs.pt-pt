---
title: "Como configurar as definições de VPN do Intune"
titleSuffix: Intune on Azure
description: "Saiba como utilizar o Intune para configurar ligações VPN nos dispositivos que gere.\""
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e6a59c1f5fcb94d427b6d12eef19d4d49ff930ce
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-vpn-settings-in-microsoft-intune"></a>Como configurar as definições de VPN no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

As Redes Virtuais Privadas (VPN) permitem-lhe conceder aos seus utilizadores acesso remoto protegido à rede da sua empresa. Os dispositivos utilizam um perfil de ligação VPN para iniciar uma ligação com o servidor VPN. Utilize os **Perfis VPN** no Microsoft Intune para atribuir definições de VPN a utilizadores e dispositivos na sua organização, para que possam ligar-se de forma fácil e segura à rede.

Por exemplo, suponha que pretende aprovisionar todos os dispositivos iOS com as definições necessárias para estabelecer uma ligação a uma partilha de ficheiros na rede da empresa. Pode criar um perfil de VPN com as definições obrigatórias para se ligar à rede da empresa e, em seguida, atribuir este perfil em todos os utilizadores com dispositivos iOS. Os utilizadores verão a ligação VPN na lista de redes disponíveis e poderão ligar-se sem qualquer esforço.

## <a name="vpn-connection-types"></a>Tipos de ligação VPN

Pode criar perfis VPN com os seguintes tipos de ligação:

|Tipo de ligação|Android<br>Android for Work|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|Pulse Secure|Sim|Sim|Sim|Sim|Sim|Sim|
|Cisco (IPSec)|Não|Sim|Não|Não|Não|Não|
|Citrix|Sim (apenas Android)|Sim|Não|Não|Não|Não|
|F5 Edge Client|Sim|Sim|Sim|Sim|Sim|Sim|
|Dell SonicWALL Mobile Connect|Sim|Sim|Sim|Sim|Sim|Sim|
|Check Point Capsule VPN|Sim|Sim|Sim|Sim|Sim|Sim|
|Cisco AnyConnect|Sim|Sim|Sim|Não|Não|Não|
|Automático|Não|Não|Não|Não|Não|Sim|
|IKEv2|Não|Não|Não|Não|Não|Sim|
|L2TP|Não|Não|Não|Não|Não|Sim|
|PPTP|Não|Não|Não|Não|Não|Sim|
|Personalizar|Não|Sim|Sim|Não|Não|Não|


> [!IMPORTANT]
> Para poder utilizar os perfis VPN atribuídos a um dispositivo, tem de instalar a aplicação VPN aplicável ao perfil. Pode utilizar as informações do tópico [O que é a gestão de aplicações no Microsoft Intune?](app-management.md), que o ajuda a atribuir a aplicação com o Intune.  

Saiba como criar perfis VPN personalizados com definições URI em [Criar perfis VPN personalizados](custom-vpn-profiles-create.md).     

## <a name="create-a-device-profile-containing-vpn-settings"></a>Criar um perfil de dispositivo com as definições de VPN

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de VPN.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições de VPN. Atualmente, pode escolher uma das seguintes plataformas para as definições de dispositivos VPN:
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e posterior**
    - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, escolha **VPN**.
7. As definições que pode configurar diferem consoante a plataforma que escolheu. Aceda a um dos seguintes tópicos para definições detalhadas para cada plataforma:
    - [Definições do Android e Android for Work](vpn-settings-android.md)
    - [Definições do iOS](vpn-settings-ios.md)
    - [Definições do macOS](vpn-settings-macos.md)
    - [Definições do Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
    - [Definições do Windows 8.1](vpn-settings-windows-8-1.md)
    - [Definições do Windows 10](vpn-settings-windows-10.md)
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).


## <a name="methods-of-securing-vpn-profiles"></a>Métodos para proteger perfis de VPN

Os perfis da VPN podem utilizar vários tipos de ligação e protocolos diferentes de fabricantes diferentes. Normalmente, estas ligações são protegidas através de um de dois métodos.

### <a name="certificates"></a>Certificados

Quando cria o perfil da VPN, pode escolher um perfil de certificado SCEP ou PKCS que tenha criado anteriormente no Intune. Este é conhecido como certificado de identidade. É utilizado para autenticação em relação a um certificado fidedigno (ou um *certificado de raiz*) que criou para estabelecer que o dispositivo do utilizador tem permissões para se ligar. O certificado fidedigno é atribuído ao computador que irá autenticar a ligação VPN (normalmente, o servidor VPN).

Para obter mais informações sobre como criar e utilizar perfis de certificado no Intune, veja [Como configurar certificados com o Microsoft Intune](certificates-configure.md).

### <a name="user-name-and-password"></a>Nome de utilizador e palavra-passe

O utilizador é autenticado no servidor VPN ao fornecer um nome de utilizador e uma palavra-passe.
