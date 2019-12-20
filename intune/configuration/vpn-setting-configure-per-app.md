---
title: Configurar a VPN por aplicação para dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
description: Veja os pré-requisitos, crie um grupo para os utilizadores da rede privada virtual (VPN), adicione um perfil de certificado SCEP, configure um perfil VPN por aplicação e atribua algumas aplicações ao perfil VPN no Microsoft Intune em dispositivos iOS. Também indica os passos para verificar a ligação VPN no dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1c9f6dbfb8d6ee4b766abef04595ffca7df4c9dc
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206385"
---
# <a name="set-up-per-app-virtual-private-network-vpn-for-ios-devices-in-intune"></a>Configurar a VPN (rede virtual privada) por aplicativo para dispositivos iOS no Intune

No Microsoft Intune, você pode criar e usar redes virtuais privadas (VPNs) atribuídas a um aplicativo. Esse recurso é chamado de "VPN por aplicativo". Você escolhe os aplicativos gerenciados que podem usar sua VPN em dispositivos gerenciados pelo Intune. Ao usar as VPNs por aplicativo, os usuários finais se conectam automaticamente por meio da VPN e obtêm acesso a recursos organizacionais, como documentos.

Esta funcionalidade aplica-se a:

- iOS 9 e posterior

Verifique a documentação do seu provedor de VPN para ver se sua VPN dá suporte a VPN por aplicativo.

Este artigo mostra como criar um perfil de VPN por aplicativo e atribuir esse perfil aos seus aplicativos. Use estas etapas para criar uma experiência de VPN por aplicativo sem interrupções para seus usuários finais. Para a maioria das VPNs que dão suporte a VPN por aplicativo, o usuário abre um aplicativo e se conecta automaticamente à VPN.

Algumas VPNs permitem a autenticação de nome de usuário e senha com VPN por aplicativo. Ou seja, os usuários precisam inserir um nome de usuário e senha para se conectar à VPN.

> [!IMPORTANT]
> A VPN por aplicativo não tem suporte para perfis VPN IKEv2 para iOS.

## <a name="per-app-vpn-with-zscaler"></a>VPN por aplicativo com Zscaler

O ZPA (Zscaler Private Access) integra-se com o Azure Active Directory (Azure AD) para autenticação. Ao usar o ZPA, você não precisa do [certificado confiável](#create-a-trusted-certificate-profile) ou dos perfis de [certificado SCEP ou PKCS](#create-a-scep-or-pkcs-certificate-profile) (descritos neste artigo). Se você tiver um perfil de VPN por aplicativo configurado para Zscaler, a abertura de um dos aplicativos associados não se conectará automaticamente ao ZPA. Em vez disso, o usuário precisa entrar no aplicativo Zscaler primeiro. Em seguida, o acesso remoto é limitado aos aplicativos associados.

## <a name="prerequisites-for-per-app-vpn"></a>Pré-requisitos para a VPN por aplicação

> [!IMPORTANT]
> Seu fornecedor de VPN pode ter outros requisitos para VPN por aplicativo, como um hardware ou licenciamento específico. Certifique-se de que consulta a documentação do fornecedor e de que cumpre os pré-requisitos antes de configurar a VPN por aplicação no Intune.

Para provar a identidade, o servidor VPN apresenta o certificado que tem de ser aceite sem um pedido pelo dispositivo. Para confirmar a aprovação automática do certificado, crie um perfil de certificado confiável que contenha o certificado raiz do servidor VPN emitido pela autoridade de certificação (CA). 

### <a name="export-the-certificate-and-add-the-ca"></a>Exportar o certificado e adicionar a autoridade de certificação

1. No servidor VPN, abra o console de administração.
2. Confirme se o servidor VPN usa autenticação baseada em certificado. 
3. Exporte o ficheiro de certificado de raiz fidedigno. Tem uma extensão .cer e tem de adicioná-la ao criar um perfil de certificado fidedigno.
4. Adicione o nome da AC que emitiu o certificado para autenticação ao servidor VPN.

    Se a AC apresentada pelo dispositivo corresponder a uma AC na lista de autoridades de certificação confiáveis no servidor VPN, o servidor VPN autenticará o dispositivo com êxito.

## <a name="create-a-group-for-your-vpn-users"></a>Criar um grupo para os utilizadores de VPN

Crie ou escolha um grupo existente no Azure Active Directory (Azure AD) para os usuários ou dispositivos que usam VPN por aplicativo. Para criar um novo grupo, consulte [Adicionar grupos para organizar usuários e dispositivos](../fundamentals/groups-add.md).

## <a name="create-a-trusted-certificate-profile"></a>Criar um perfil de certificado fidedigno

Importe o certificado de raiz do servidor VPN emitido pela AC para um perfil criado no Intune. O perfil de certificado fidedigno indica ao dispositivo iOS para confiar automaticamente na AC que o servidor VPN apresenta.

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:
    - **Nome**: Insira um nome descritivo para o perfil. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. Por exemplo, um bom nome de perfil é o **perfil de VPN de certificado confiável do IOS para toda a empresa**.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: selecione **Ios**.
    - **Tipo de perfil**: selecione **certificado confiável**.
4. Selecione o ícone de pasta e navegue até o certificado de VPN (arquivo. cer) que você exportou do console de administração de VPN. 
5. Selecione **OK** > **criar**.

    ![Criar um perfil de certificado confiável para dispositivos iOS no Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-or-pkcs-certificate-profile"></a>Criar um perfil de certificado SCEP ou PKCS

O perfil de certificado raiz confiável permite que o dispositivo confie automaticamente no servidor VPN. O certificado SCEP ou PKCS fornece credenciais do cliente VPN iOS para o servidor VPN. O certificado permite que o dispositivo autentique silenciosamente sem solicitar um nome de usuário e uma senha. 

Para configurar e atribuir o certificado de autenticação de cliente, consulte um dos seguintes artigos:

- [Configurar a infraestrutura para dar suporte ao SCEP com o Intune](../protect/certificates-scep-configure.md)
- [Configurar e gerir certificados PKCS com o Intune](../protect/certficates-pfx-configure.md)

Certifique-se de configurar o certificado para autenticação de cliente. Você pode definir isso diretamente nos perfis de certificado SCEP (lista de**uso estendido de chave** > **autenticação de cliente**). Para PKCS, defina autenticação de cliente no modelo de certificado na autoridade de certificação (CA).

![Criar um perfil de certificado SCEP em Microsoft Intune, incluindo formato de nome de entidade, uso de chave, uso estendido de chave e muito mais](./media/vpn-setting-configure-per-app/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>Criar um perfil de VPN por aplicação

O perfil VPN contém o certificado SCEP ou PKCS com as credenciais do cliente, as informações de conexão para a VPN e o sinalizador VPN por aplicativo para habilitar o recurso VPN por aplicativo usado pelo aplicativo iOS.

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
2. Introduza as seguintes propriedades:
    - **Nome**: Insira um nome descritivo para o perfil personalizado. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. Por exemplo, um bom nome de perfil é o **perfil de VPN por aplicativo IOS para toda a empresa**.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: selecione **Ios**.
    - **Tipo de perfil**: selecione **VPN**.
3. Em **tipo de conexão**, selecione seu aplicativo cliente VPN.
4. Selecione **VPN Base**. [configurações de VPN do IOS](vpn-settings-ios.md) lista e descreve todas as configurações. Ao usar a VPN por aplicativo, certifique-se de definir as seguintes propriedades como listadas:

    - **Método de autenticação**: selecione **certificados**. 
    - **Certificado de autenticação**: selecione um certificado SCEP ou PKCS existente > **OK**.      
    - **Túnel dividido**: selecione **desabilitar** para forçar todo o tráfego a usar o túnel VPN quando a conexão VPN estiver ativa. 

      ![Em um perfil VPN por aplicativo, insira uma conexão, um endereço IP ou FQDN, o método de autenticação e o túnel dividido no Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-create-vpn-profile.png)

    Para obter informações sobre as outras configurações, consulte [configurações de VPN do IOS](vpn-settings-ios.md).

5. Selecione o **tipo de** > **VPN automática** de VPN automática > **VPN por aplicativo**

    ![No Intune, defina VPN automática para VPN por aplicativo em dispositivos iOS](./media/vpn-setting-configure-per-app/vpn-per-app-automatic.png)

6. Selecione **ok** > **OK** > **criar**.

## <a name="associate-an-app-with-the-vpn-profile"></a>Associar uma aplicação ao perfil VPN

Depois de adicionar o perfil VPN, associe a aplicação e o grupo do Azure AD ao perfil.

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), selecione **aplicativos** > **todos os aplicativos**.
2. Selecione um aplicativo na lista > **atribuições** > **Adicionar grupo**.
3. Em **tipo de atribuição**, selecione **necessário** ou **disponível para dispositivos registrados**.
4. Selecione **grupos incluídos** > **Selecione os grupos a serem incluídos** > selecione o grupo [que você criou](#create-a-group-for-your-vpn-users) (neste artigo) > **selecione**.
5. Em **VPNs**, selecione o perfil VPN por aplicativo [que você criou](#create-a-per-app-vpn-profile) (neste artigo).

    ![Atribuir um aplicativo ao perfil VPN por aplicativo no Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-app-to-vpn.png)

6. Selecione **OK** > **salvar**.

Uma associação entre um aplicativo e um perfil é removida durante o próximo check-in do dispositivo, quando todas as condições a seguir existem:

- A aplicação foi direcionada com a intenção "Instalação obrigatória".
- O perfil e a aplicação foram direcionados para o mesmo grupo.
- Removeu a configuração da VPN por aplicação da atribuição de aplicações.

Uma associação entre um aplicativo e um perfil persiste até que o usuário solicite uma reinstalação do Portal da Empresa, quando todas as seguintes condições existirem:

- A aplicação foi direcionada com a intenção "Instalação disponível".
- O perfil e a aplicação foram direcionados para o mesmo grupo.
- O usuário final solicitou a instalação do aplicativo de Portal da Empresa, que resulta no aplicativo e no perfil que estão sendo instalados no dispositivo.
- Removeu ou alterou a configuração da VPN por aplicação da atribuição de aplicações.

## <a name="verify-the-connection-on-the-ios-device"></a>Verificar a ligação no dispositivo iOS

Com a configuração de VPN por aplicação associada à sua aplicação, verifique se a ligação funciona a partir de um dispositivo.

### <a name="before-you-attempt-to-connect"></a>Antes de tentar estabelecer ligação

- Certifique-se de implantar todas as políticas mencionadas acima no mesmo grupo. Caso contrário, a experiência de VPN por aplicativo não funcionará.
- Se você estiver usando o aplicativo VPN Pulse Secure ou um aplicativo cliente VPN personalizado, poderá optar por usar a camada de aplicativo ou o túnel de camada de pacote. Defina o valor **ProviderType** para **proxy-da-aplicação**, para o túnel de camada de aplicação ou para **pacote-túnel**, para o túnel de camada de pacote. Verifique a documentação do seu provedor de VPN para certificar-se de que você está usando o valor correto.

### <a name="connect-using-the-per-app-vpn"></a>Estabelecer ligação com a VPN por aplicação

Verifique a experiência sem contacto ao estabelecer ligação sem ter de selecionar a VPN ou escrever as suas credenciais. A experiência sem contacto significa que:

- O dispositivo não solicita que você confie no servidor VPN. Ou seja, o usuário não vê a caixa de diálogo de **confiança dinâmica** .
- O usuário não precisa digitar credenciais.
- O dispositivo do usuário é conectado à VPN quando o usuário abre um dos aplicativos associados.

## <a name="next-steps"></a>Próximos passos

- Para rever as definições do iOS, veja [VPN settings for iOS devices in Microsoft Intune (Definições de VPN para dispositivos iOS no Microsoft Intune)](vpn-settings-ios.md).
- Para saber mais sobre a configuração de VPN e o Intune, consulte [definir configurações de VPN no Microsoft Intune](vpn-settings-configure.md).
