---
title: Registro de dispositivos ingressados no Azure AD híbrido-piloto automático do Windows
titleSuffix: ''
description: Use o Windows AutoPilot para registrar dispositivos ingressados no Azure AD híbridos no Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0cf62d3f16951170a826528e94fcb50691be9fc7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731876"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-by-using-intune-and-windows-autopilot"></a>Implantar dispositivos ingressados no Azure AD híbrido usando o Intune e o piloto automático do Windows
Você pode usar o Intune e o piloto automático do Windows para configurar dispositivos ingressados no Azure Active Directory híbrido (Azure AD). Para fazer isso, siga as etapas neste artigo.

## <a name="prerequisites"></a>Pré-requisitos

Configurar com êxito seus [dispositivos ingressados no Azure ad híbrido](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan). Certifique-se de [verificar o registro do dispositivo](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration) usando o cmdlet Get-MsolDevice.

Os dispositivos a ser inscritos também têm de:
- Estar executando o Windows 10 v1809 ou superior.
- Ter acesso à Internet [seguindo os requisitos de rede do Windows AutoPilot documentados](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements#networking-requirements).
- Ter acesso a um controlador de domínio Active Directory, portanto, ele deve estar conectado à rede da organização (onde pode resolver os registros DNS para o domínio do AD e o controlador de domínio do AD e se comunicar com o controlador de domínio para autenticar o usuário. A conexão VPN não tem suporte no momento).
- Ser capaz de executar ping no controlador de domínio do domínio que você está tentando ingressar.
- Se estiver usando proxy, a opção de configurações de proxy WPAD deverá ser habilitada e configurada.
- Passam pela experiência inicial (OOBE).

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurar a inscrição automática de dispositivos Windows 10

1. Entre no [portal do Azure](https://portal.azure.com) e, no painel esquerdo, selecione **Azure Active Directory**.

   ![O portal do Azure](./media/windows-autopilot-hybrid/auto-enroll-azure-main.png)

1. Selecione **Mobilidade (MDM e MAM)** .

   ![O painel de Azure Active Directory](./media/windows-autopilot-hybrid/auto-enroll-mdm.png)

1. Selecione **Microsoft Intune**.

   ![O painel mobilidade (MDM e MAM)](./media/windows-autopilot-hybrid/auto-enroll-intune.png)

1. Certifique-se de que os usuários que implantam dispositivos ingressados no Azure AD usando o Intune e o Windows sejam membros de um grupo que está incluído no seu **escopo de usuário do MDM**.

   ![O painel de configuração de mobilidade (MDM e MAM)](./media/windows-autopilot-hybrid/auto-enroll-scope.png)

1. Use os valores padrão nas caixas **URL de termos de uso do MDM**, **URL de descoberta do MDM**e URL de conformidade do **MDM** e, em seguida, selecione **salvar**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Aumentar o limite de contas de computador na Unidade Organizacional

O conector do Intune para seu Active Directory cria computadores inscritos no AutoPilot no domínio Active Directory local. O computador que hospeda o conector do Intune deve ter os direitos para criar os objetos de computador dentro do domínio. 

Em alguns domínios, os computadores não recebem os direitos de criar computadores. Além disso, os domínios têm um limite interno (padrão de 10) que se aplica a todos os usuários e computadores que não são direitos delegados para criar objetos de computador. Portanto, os direitos precisam ser delegados a computadores que hospedam o conector do Intune na unidade organizacional em que os dispositivos ingressados no Azure AD híbrido são criados.

A unidade organizacional que recebe os direitos para criar computadores deve corresponder:
- A unidade organizacional que é inserida no perfil de ingresso no domínio.
- Se nenhum perfil for selecionado, o nome de domínio do computador para seu domínio.

1. Abra **Active Directory usuários e computadores (DSA. msc)** .

1. Clique com o botão direito do mouse na unidade organizacional que você usará para criar computadores ingressados no Azure AD híbrido e selecione **delegar controle**.

    ![O comando de controle de representante](./media/windows-autopilot-hybrid/delegate-control.png)

1. No assistente **de delegação de controle** , selecione **Avançar** > **Adicionar** > **tipos de objeto**.

1. No painel **tipos de objeto** , marque a caixa de seleção **computadores** e, em seguida, selecione **OK**.

    ![O painel tipos de objeto](./media/windows-autopilot-hybrid/object-types-computers.png)

1. No painel **Selecionar usuários, computadores ou grupos** , na caixa **Inserir os nomes de objeto a serem selecionados** , digite o nome do computador onde o conector está instalado.

    ![O painel Selecionar usuários, computadores ou grupos](./media/windows-autopilot-hybrid/enter-object-names.png)

1. Selecione **verificar nomes** para validar sua entrada, selecione **OK**e, em seguida, selecione **Avançar**.

1. Selecione **criar uma tarefa personalizada para delegar** > a**próxima**.

1. Marque a caixa de seleção **apenas os seguintes objetos na pasta** e, em seguida, marque as caixas de seleção **objetos de computador**, **criar objetos selecionados nesta pasta**e **excluir objetos selecionados nesta pasta** .

    ![O painel tipo de objeto de Active Directory](./media/windows-autopilot-hybrid/only-following-objects.png)
    
1. Selecione **Seguinte**.

1. Em **permissões**, marque a caixa de seleção **controle total** .  
    Essa ação seleciona todas as outras opções.

    ![O painel permissões](./media/windows-autopilot-hybrid/full-control.png)

1. Selecione **Avançar**e, em seguida, selecione **concluir**.

## <a name="install-the-intune-connector"></a>Instalar o Conector do Intune

O conector do Intune para Active Directory deve ser instalado em um computador que esteja executando o Windows Server 2016 ou posterior. O computador também deve ter acesso à Internet e à sua Active Directory. Para aumentar o dimensionamento e a disponibilidade ou suportar múltiplos domínios do Azure Active Directory, pode instalar múltiplos conectores no seu ambiente. É recomendável instalar o conector em um servidor que não esteja executando nenhum outro conector do Intune.

1. No [Intune](https://aka.ms/intuneportal), selecione **registro** > do dispositivo registro do**Windows** > **conector do Intune para Active Directory** > **Adicionar**. 
2. Siga as instruções para baixar o conector.
3. Abra o arquivo de instalação do conector baixado, *ODJConnectorBootstrapper. exe*, para instalar o conector.
4. No final da instalação, selecione **Configurar**.
5. Selecione **entrar**.
6. Insira as credenciais de administrador global do usuário ou da função de administrador do Intune.  
   A conta de usuário deve ter uma licença do Intune atribuída.
7. Acesse **dispositivo registro** > **Windows registro** > **Intune conector para Active Directory**e, em seguida, confirme se o status da conexão está **ativo**.

> [!NOTE]
> Depois de entrar no conector, pode levar alguns minutos para aparecer no [Intune](https://aka.ms/intuneportal). Ele só aparecerá se ele puder se comunicar com êxito com o serviço do Intune.

### <a name="turn-off-ie-enhanced-security-configuration"></a>Desligar a configuração de segurança reforçada do IE
Por padrão, o Windows Server tem a configuração de segurança reforçada do Internet Explorer ativada. Se não for possível entrar no conector do Intune para Active Directory desative a configuração de segurança avançada do IE para o administrador. [Como desativar a configuração de segurança reforçada do Internet Explorer](https://blogs.technet.microsoft.com/chenley/2011/03/10/how-to-turn-off-internet-explorer-enhanced-security-configuration)

### <a name="configure-web-proxy-settings"></a>Configurar definições de proxy Web

Se você tiver um proxy Web no seu ambiente de rede, verifique se o conector do Intune para Active Directory funciona corretamente consultando o [trabalho com os servidores proxy locais existentes](autopilot-hybrid-connector-proxy.md).


## <a name="create-a-device-group"></a>Criar um grupo de dispositivos
1. No [Intune](https://aka.ms/intuneportal), selecione **grupos** > **novo grupo**.

1. No painel **grupo** , faça o seguinte:

    a. Para **tipo de grupo**, selecione **segurança**.

    b. Insira um **nome de grupo** e uma **Descrição de grupo**.

    c. Selecione um **tipo de associação**.

1. Se você selecionou **dispositivos dinâmicos** para o tipo de associação, no painel **grupo** , selecione **membros do dispositivo dinâmico** e, na caixa **regra avançada** , siga um destes procedimentos:
    - Para criar um grupo que inclui todos os seus dispositivos do AutoPilot `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`, digite.
    - O campo de marca de grupo do Intune é mapeado para o atributo OrderID em dispositivos do Azure AD. Se você quiser criar um grupo que inclui todos os seus dispositivos de piloto automático com uma marca de grupo específica (OrderID), digite:`(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Para criar um grupo que inclui todos os dispositivos do AutoPilot com uma ID de ordem de compra `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`específica, insira.
    
1. Selecione **Guardar**.

1. Selecione **Criar**.  

## <a name="register-your-autopilot-devices"></a>Registar os seus dispositivos do Autopilot

Selecione uma das maneiras a seguir para registrar seus dispositivos de piloto automático.

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Registar dispositivos do Autopilot que já estejam inscritos

1. Crie um perfil de implementação do Autopilot com a opção **Autopilot** definida para **Sim**. 
2. Atribua o perfil a um grupo que contém os membros que você deseja registrar automaticamente com o piloto automático.

Para obter mais informações, veja [Criar um perfil de implementação do Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Registar dispositivos do Autopilot que não estão inscritos

Se os seus dispositivos ainda não estiverem inscritos, pode registá-los. Para obter mais informações, veja [Adicionar dispositivos](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Registar dispositivos de um OEM

Se comprar novos dispositivos, alguns OEMs podem registar os dispositivos por si. Para obter mais informações, veja a [página do Windows Autopilot](https://aka.ms/WindowsAutopilot).

Quando os dispositivos do AutoPilot são *registrados*, antes de serem inscritos no Intune, eles são exibidos em três locais (com nomes definidos para seus números de série):
- O painel de **dispositivos do piloto automático** no Intune no portal do Azure. Selecione **registro** > de dispositivo**dispositivos**de**registro** > do Windows.
- O painel **dispositivos do Azure ad** no Intune no portal do Azure. Escolha **dispositivos** > dispositivos**do Azure ad**.
- O painel **todos os dispositivos do Azure ad** no Azure Active Directory no portal do Azure selecionando **dispositivos** > **todos os dispositivos**.

Depois que os dispositivos do AutoPilot são *registrados*, eles são exibidos em quatro locais:
- O painel de **dispositivos do piloto automático** no Intune no portal do Azure. Selecione **registro** > de dispositivo**dispositivos**de**registro** > do Windows.
- O painel **dispositivos do Azure ad** no Intune no portal do Azure. Escolha **dispositivos** > dispositivos**do Azure ad**.
- O painel **todos os dispositivos do Azure ad** no Azure Active Directory no portal do Azure. Selecione **dispositivos** > **todos os dispositivos**.
- O painel **todos os dispositivos** no Intune no portal do Azure. Selecione **dispositivos** > **todos os dispositivos**.

Depois que os dispositivos do AutoPilot forem registrados, seus nomes se tornarão o nome do host do dispositivo. Por padrão, o nome do host começa com *Desktop-* .


## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Criar e atribuir um perfil de implementação do Autopilot
Os perfis de implementação do Autopilot são utilizados para configurar os dispositivos do Autopilot.

1. No [Intune](https://aka.ms/intuneportal), selecione **registro** > de dispositivo**Windows registro** > **perfis** > de implantação**Criar perfil**.
2. Na página **noções básicas** , digite um **nome** e uma **Descrição**opcional.
3. Se pretender que todos os dispositivos nos grupos atribuídos sejam convertidos automaticamente no Autopilot, defina **Converter todos os dispositivos visados para o Piloto Automático** para **Sim**. Todos os dispositivos de propriedade corporativa, não autopiloto em grupos atribuídos serão registrados com o serviço de implantação do AutoPilot. Dispositivos de propriedade pessoal não serão convertidos para o piloto automático. O processo de registo demora até 48 horas, pelo que deverá aguardar. Quando a inscrição do dispositivo for anulada e o dispositivo for reposto, o Autopilot irá inscrevê-lo. Após registar um dispositivo desta forma, desativar esta opção ou remover a atribuição de perfil não irá remover o dispositivo do serviço de implementação do Autopilot. Em alternativa, tem de [remover o dispositivo diretamente](enrollment-autopilot.md#delete-autopilot-devices).
4. Selecione **Seguinte**.
5. Na página de **OOBE (experiência do usuário)** , para o modo de **implantação**, selecione **controlado por usuários**.
6. Na caixa **ingressar no Azure ad como** , selecione **ingressado no Azure ad híbrido**.
7. Configure as opções restantes na página de **configuração inicial do uso (OOBE)** , conforme necessário.
8. Selecione **Seguinte**.
9. Na página **marcas de escopo** , selecione [marcas de escopo](../fundamentals/scope-tags.md) para este perfil.
10. Selecione **Seguinte**.
11. Na página **atribuições** , selecione **Selecionar grupos para incluir** > Pesquisar e selecione o grupo de dispositivos > **selecione**.
12. Selecione **Avançar** > **criar**.

Demora cerca de 15 minutos para que o status do perfil do dispositivo seja alterado de *não atribuído* para *atribuição* e, por fim, para *atribuído*.

## <a name="optional-turn-on-the-enrollment-status-page"></a>Adicional Ativar a página de status de registro

1. No [Intune](https://aka.ms/intuneportal), selecione **registro** > de dispositivo inscrição no registro do**Windows** > **página status**.
1. No painel de **página status do registro** , selecione**configurações** **padrão** > .
1. Na caixa de **progresso mostrar o aplicativo e a instalação do perfil** , selecione **Sim**.
1. Configure as outras opções conforme seja necessário.
1. Selecione **Guardar**.

## <a name="create-and-assign-a-domain-join-profile"></a>Criar e atribuir um perfil de Associação a um Domínio

1. No [Intune](https://aka.ms/intuneportal), selecione **dispositivo** > **perfis** > de configuração**Criar perfil**.
1. Introduza as seguintes propriedades:
   - **Nome**: introduza um nome descritivo para o novo perfil.
   - **Descrição**: introduza uma descrição para o perfil.
   - **Plataforma**: Selecione **Windows 10 e posterior**.
   - **Tipo de perfil**: Selecione **ingresso no domínio (versão prévia)** .
1. Selecione **configurações**e, em seguida, forneça um **prefixo de nome de computador**, nome de **domínio**e (opcional) **unidade organizacional** no [formato DN](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name). 
1. Selecione **OK** > **criar**.  
    O perfil é criado e exibido na lista.
1. Para atribuir o perfil, siga as etapas em [atribuir um perfil de dispositivo](../configuration/device-profile-assign.md#assign-a-device-profile) e atribua o perfil ao mesmo grupo usado nesta etapa [criar um grupo de dispositivos](windows-autopilot-hybrid.md#create-a-device-group)
   - Implantando vários perfis de ingresso no domínio
   
     a. Crie um grupo dinâmico que inclua todos os seus dispositivos de piloto automático com um perfil de implantação do AutoPilot específico, digite (Device. enrollmentProfileName-EQ "nome do perfil do AutoPilot"). 
     
     b. Substitua ' nome do perfil do AutoPilot ' pelo nome de exibição do perfil criado em [criar e atribua um perfil de implantação do AutoPilot](windows-autopilot-hybrid.md#create-and-assign-an-autopilot-deployment-profile). 
     
     c. Crie vários perfis de implantação do AutoPilot e atribua esse dispositivo ao perfil especificado nesse grupo dinâmico.

> [!NOTE]
> Os recursos de nomenclatura do Windows AutoPilot para o ingresso no Azure AD híbrido não dão suporte a variáveis como% SERIAL% e apenas prefixos de suporte para o nome do computador.

## <a name="next-steps"></a>Passos seguintes

Após configurar o Windows Autopilot, saiba como gerir os seus dispositivos. Para obter mais informações, consulte [o que é Microsoft InTune gerenciamento de dispositivo?](../remote-actions/device-management.md).
