---
title: Configurar a VPN por aplicação para dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
description: Veja os pré-requisitos, crie um grupo para os utilizadores da rede privada virtual (VPN), adicione um perfil de certificado SCEP, configure um perfil VPN por aplicação e atribua algumas aplicações ao perfil VPN no Microsoft Intune em dispositivos iOS. Também indica os passos para verificar a ligação VPN no dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c7609b3a190cacc7b722f408133f6c5f10d96771
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233139"
---
# <a name="set-up-per-app-virtual-private-network-vpn-for-ios-devices-in-intune"></a>Definir a cópia de segurança por aplicação Virtual rede privada (VPN) para dispositivos iOS no Intune

No Microsoft Intune, pode criar e utilizar redes privadas virtuais (VPNs) atribuído a uma aplicação. Esse recurso é chamado de "VPN por aplicação". Escolha as aplicações geridas que podem utilizar a VPN em dispositivos geridos pelo Intune. Quando utilizar uma VPN por aplicação, os utilizadores finais automaticamente ligadas através da VPN e obtenha acesso aos recursos organizacionais, como documentos.

Esta funcionalidade aplica-se a:

- iOS 9 e posteriores

Verifique a documentação do seu fornecedor de VPN para ver se a VPN oferece suporte a VPN por aplicação.

Este artigo mostra-lhe como criar um perfil VPN por aplicação e atribuir este perfil para as suas aplicações. Utilize estes passos para criar uma experiência VPN por aplicação totalmente integrada para os utilizadores finais. Para a maioria das VPNs que suportam VPN por aplicação, o utilizador abre uma aplicação e liga-se automaticamente à VPN.

Alguns VPNs permitem a autenticação de nome de utilizador e palavra-passe com a VPN por aplicação. Ou seja, os utilizadores têm de introduzir um nome de utilizador e palavra-passe para ligar à VPN.

## <a name="per-app-vpn-with-zscaler"></a>VPN por aplicação com o Zscaler

Acesso privado Zscaler (ZPA) integra-se com o Azure Active Directory (Azure AD) para autenticação. Ao utilizar ZPA, não precisa da [certificado fidedigno](#create-a-trusted-certificate-profile) ou [certificado SCEP ou PKCS](#create-a-scep-or-pkcs-certificate-profile) perfis (descritos neste artigo). Se tiver um conjunto de perfis de VPN por aplicação se para obter o Zscaler, abrir uma das aplicações associadas não ligar automaticamente a ZPA. Em vez disso, o utilizador tem de iniciar sessão na aplicação Zscaler pela primeira vez. Em seguida, o acesso remoto é limitado para as aplicações associadas.

## <a name="prerequisites-for-per-app-vpn"></a>Pré-requisitos para a VPN por aplicação

> [!IMPORTANT]
> O fornecedor VPN pode ter outros requisitos para VPN por aplicação, como o hardware específico ou de licenciamento. Certifique-se de que consulta a documentação do fornecedor e de que cumpre os pré-requisitos antes de configurar a VPN por aplicação no Intune.

Para provar a identidade, o servidor VPN apresenta o certificado que tem de ser aceite sem um pedido pelo dispositivo. Para confirmar a aprovação automática do certificado, crie um perfil de certificado fidedigno que contém o certificado de raiz do servidor VPN emitido pela autoridade de certificação (AC). 

#### <a name="export-the-certificate-and-add-the-ca"></a>Exportar o certificado e adicione a AC

1. No seu servidor VPN, abra a consola de administração.
2. Confirme que o seu servidor VPN utiliza autenticação baseada em certificado. 
3. Exporte o ficheiro de certificado de raiz fidedigno. Tem uma extensão .cer e tem de adicioná-la ao criar um perfil de certificado fidedigno.
4. Adicione o nome da AC que emitiu o certificado para autenticação ao servidor VPN.

    Se a AC apresentada pelo dispositivo corresponder a uma AC na lista de AC fidedigna no servidor VPN, em seguida, o servidor VPN com êxito autentica o dispositivo.

## <a name="create-a-group-for-your-vpn-users"></a>Criar um grupo para os utilizadores de VPN

Crie ou selecione um grupo existente no Azure Active Directory (Azure AD) para os utilizadores ou dispositivos que utilizem a VPN por aplicação. Para criar um novo grupo, consulte [adicionar grupos para organizar utilizadores e dispositivos](groups-add.md).

## <a name="create-a-trusted-certificate-profile"></a>Criar um perfil de certificado fidedigno

Importe o certificado de raiz do servidor VPN emitido pela AC para um perfil criado no Intune. O perfil de certificado fidedigno indica ao dispositivo iOS para confiar automaticamente na AC que o servidor VPN apresenta.

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes propriedades:
    - **Nome**
    - **Descrição**
    - **Plataforma**: Selecione **iOS**.
    - **Tipo de perfil**: Selecione **certificado fidedigno**.
4. Selecione o ícone de pasta e navegue para o certificado VPN (ficheiro. cer) que exportou a partir da sua consola de administração de VPN. 
5. Selecione **OK** > **criar**.

    ![Criar um perfil de certificado fidedigno para dispositivos iOS no Microsoft Intune](./media/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-or-pkcs-certificate-profile"></a>Criar um perfil de certificado SCEP ou PKCS

O perfil de certificado de raiz fidedigna permite ao dispositivo confiar automaticamente no servidor VPN. O certificado SCEP ou PKCS fornece as credenciais do cliente VPN de iOS para o servidor VPN. O certificado permite que o dispositivo seja autenticado automaticamente sem pedir um nome de utilizador e palavra-passe. 

Para configurar e atribuir o cliente de certificado de autenticação, consulte um dos seguintes artigos:

- [Configurar e gerir certificados SCEP com o Intune](certificates-scep-configure.md)
- [Configurar e gerir certificados PKCS com o Intune](certficates-pfx-configure.md)

Certifique-se de que configurar o certificado para autenticação de cliente. Pode definir isso diretamente nos perfis de certificado SCEP (**utilização alargada da chave** lista > **autenticação de cliente**). Para PKCS, defina a autenticação de cliente no modelo de certificado na autoridade de certificação (AC).

![Criar um perfil de certificado SCEP no Microsoft Intune, incluindo o formato do nome do requerente, utilização de chave, utilização alargada da chave e muito mais](./media/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>Criar um perfil de VPN por aplicação

O perfil VPN contém o certificado SCEP ou PKCS com as credenciais de cliente, as informações de ligação à VPN, e o sinalizador VPN por aplicação para ativar a funcionalidade VPN por aplicação utiliza pela aplicação iOS.

1. Na **Intune**, selecione **configuração do dispositivo** > **perfis** > **criar perfil**. 
2. Introduza as seguintes propriedades: 
    - **Nome**
    - **Descrição**
    - **Plataforma**: Selecione **iOS**.
    - **Tipo de perfil**: Selecione **VPN**.
3. Na **tipo de ligação**, selecione a sua aplicação de cliente VPN.
4. Selecione **VPN Base**. [definições de VPN de iOS](vpn-settings-ios.md) apresenta e descreve todas as definições. Ao utilizar a VPN por aplicação, certifique-se de que defina as propriedades seguintes, conforme listado: 
    
    - **Método de autenticação**: Selecione **certificados**. 
    - **Certificado de autenticação**: Selecione um certificado SCEP ou PKCS existente > **OK**.      
    - **Divisão do túnel**: Selecione **desativar** para forçar todo o tráfego para utilizar o túnel VPN quando a ligação VPN está ativa. 

      ![Num perfil VPN por aplicação, introduza uma ligação, o endereço IP ou FQDN, o método de autenticação e dividir tunning no Microsoft Intune](./media/vpn-per-app-create-vpn-profile.png)

    Para obter informações sobre as outras definições, consulte [definições de VPN de iOS](vpn-settings-ios.md).

5. Selecione **VPN automática** > **tipo de VPN automática** > **VPN por aplicação**

    ![No Intune, defina VPN automática para VPN por aplicação em dispositivos iOS](./media/vpn-per-app-automatic.png)

6. Selecione **OK** > **OK** > **criar**.

## <a name="associate-an-app-with-the-vpn-profile"></a>Associar uma aplicação ao perfil VPN

Depois de adicionar o perfil VPN, associe a aplicação e o grupo do Azure AD ao perfil.

1. No **Intune**, selecione **Aplicações do cliente** > **Aplicações**.
2. Selecione uma aplicação na lista > **atribuições** > **adicionar grupo**.
3. Na **tipo de atribuição**, selecione **necessário** ou **disponível para dispositivos inscritos**.
4. Selecione **incluído grupos** > **selecionar grupos para incluir** > selecione o grupo [que criou](#create-a-group-for-your-vpn-users) (neste artigo) > **selecione**.
5. Na **VPNs**, selecione o perfil VPN por aplicação [que criou](#create-a-per-app-vpn-profile) (neste artigo).

    ![Atribuir uma aplicação para o perfil VPN por aplicação no Microsoft Intune](./media/vpn-per-app-app-to-vpn.png)

6. Selecione **OK** > **guardar**.

Uma associação entre uma aplicação e um perfil é removida durante a próxima entrada de dispositivo, quando todas as condições seguintes:

- A aplicação foi direcionada com a intenção "Instalação obrigatória".
- O perfil e a aplicação foram direcionados para o mesmo grupo.
- Removeu a configuração da VPN por aplicação da atribuição de aplicações.

Uma associação entre uma aplicação e um perfil de persiste até que o usuário solicite uma reinstalação do Portal da empresa, quando todas as condições seguintes:

- A aplicação foi direcionada com a intenção "Instalação disponível".
- O perfil e a aplicação foram direcionados para o mesmo grupo.
- O utilizador final pediu a instalação da aplicação do Portal da empresa, o que resulta na aplicação e o perfil que está a ser instalado no dispositivo.
- Removeu ou alterou a configuração da VPN por aplicação da atribuição de aplicações.

## <a name="verify-the-connection-on-the-ios-device"></a>Verificar a ligação no dispositivo iOS

Com a configuração de VPN por aplicação associada à sua aplicação, verifique se a ligação funciona a partir de um dispositivo.

### <a name="before-you-attempt-to-connect"></a>Antes de tentar estabelecer ligação

 - Certificar-se de que implementou ao mesmo grupo de todas as políticas acima mencionadas. Caso contrário, a experiência VPN por aplicação não funcionará.
 - Se estiver a utilizar a aplicação de VPN de proteger Pulse ou uma aplicação de cliente VPN personalizada, pode optar por utilizar o túnel de camada de pacote ou de camada de aplicação. Defina o valor **ProviderType** para **proxy-da-aplicação**, para o túnel de camada de aplicação ou para **pacote-túnel**, para o túnel de camada de pacote. Verifique a documentação do seu fornecedor de VPN para se certificar de que está a utilizar o valor correto.

### <a name="connect-using-the-per-app-vpn"></a>Estabelecer ligação com a VPN por aplicação

Verifique a experiência sem contacto ao estabelecer ligação sem ter de selecionar a VPN ou escrever as suas credenciais. A experiência sem contacto significa que:

 - O dispositivo não lhe pede para confiar no servidor VPN. Ou seja, o utilizador não vê o **confiança dinâmica** caixa de diálogo.
 - O utilizador não tem de escrever as credenciais.
 - O dispositivo do utilizador está ligado à VPN, quando o utilizador abre uma das aplicações associadas.

<!-- ## Troubleshooting the per-app VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>Passos Seguintes

- Para rever as definições do iOS, veja [VPN settings for iOS devices in Microsoft Intune (Definições de VPN para dispositivos iOS no Microsoft Intune)](vpn-settings-ios.md).
- Para saber mais sobre a definição de VPN e o Intune, veja [configurar definições de VPN no Microsoft Intune](vpn-settings-configure.md).
