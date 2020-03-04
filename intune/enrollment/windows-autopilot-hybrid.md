---
title: Inscrições para dispositivos híbridos azure ad - Windows Autopilot
titleSuffix: ''
description: Utilize o Windows Autopilot para inscrever dispositivos híbridos azure ad-join em Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d30c02e67579e7c4e2d577f8804189fec1c6110d
ms.sourcegitcommit: 6608dc70d01376e0cd90aa620a2fe01337f6a2f1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260253"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-by-using-intune-and-windows-autopilot"></a>Implemente dispositivos híbridos de AD com a utilização de Intune e Windows Autopilot
Pode utilizar dispositivos intune e Windows Autopilot para configurar dispositivos híbridos azure Ative Directory (Azure AD). Para tal, siga os passos deste artigo.

## <a name="prerequisites"></a>Pré-requisitos

Configure com sucesso os seus [dispositivos híbridos azure ad- joined](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan). Certifique-se de [verificar o registo do seu dispositivo](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration) utilizando o cmdlet Get-MsolDevice.

Os dispositivos a ser inscritos também têm de:
- Esteja a executar o Windows 10 v1809 ou superior.
- Tenha acesso à internet [seguindo os requisitos de rede do Windows Autopilot documentados](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements#networking-requirements).
- Tenha acesso a um controlador de domínio Ative Directy, por isso deve ser ligado à rede da organização (onde pode resolver os registos DNS para o domínio AD e o controlador de domínio AD, e comunicar com o controlador de domínio para autenticar o utilizador. Ligação VPN não suportada neste momento).
- Seja capaz de pingar o controlador de domínio do domínio que está a tentar aderir.
- Se utilizar o Proxy, a opção de definições de Proxy WPAD deve ser ativada e configurada.
- Sofra a experiência fora da caixa (OOBE).
- Utilize um tipo de autorização que o Azure Ative Directory suporta no OOBE.


## <a name="set-up-windows-10-automatic-enrollment"></a>Configurar a inscrição automática de dispositivos Windows 10

1. Inscreva-se no Azure, no painel esquerdo, selecione **Azure Ative Directory**.

   ![O portal Azure](./media/windows-autopilot-hybrid/auto-enroll-azure-main.png)

1. Selecione **Mobilidade (MDM e MAM)** .

   ![O painel de diretório ativo Azure](./media/windows-autopilot-hybrid/auto-enroll-mdm.png)

1. Selecione **Microsoft Intune**.

   ![O painel de Mobilidade (MDM e MAM)](./media/windows-autopilot-hybrid/auto-enroll-intune.png)

1. Certifique-se de que os utilizadores que implementam dispositivos azure ad-join ing using Intune e Windows são membros de um grupo que está incluído no seu âmbito de **utilizador DOMD**.

   ![O painel de configuração da Mobilidade (MDM e MAM)](./media/windows-autopilot-hybrid/auto-enroll-scope.png)

1. Utilize os valores predefinidos no **URL de utilização do MDM,** **URL de descoberta do MDM**e caixas URL de conformidade com o **MDM** e, em seguida, selecione **Guardar**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Aumentar o limite de contas de computador na Unidade Organizacional

O Conector Intune para o seu Diretório Ativo cria computadores matriculados em piloto automático no domínio ative directory no local. O computador que acolhe o Conector Intune deve ter o direito de criar os objetos do computador dentro do domínio. 

Em alguns domínios, os computadores não têm o direito de criar computadores. Além disso, os domínios têm um limite incorporado (padrão de 10) que se aplica a todos os utilizadores e computadores que não são direitos delegados para criar objetos informáticos. Por isso, os direitos devem ser delegados aos computadores que acolhem o Intune Connector na unidade organizacional onde são criados dispositivos híbridos azure ad.a.d.

A unidade organizacional que concedeu os direitos de criar computadores deve corresponder:
- A unidade organizacional que entrou no perfil de Domain Join.
- Se não for selecionado nenhum perfil, o nome de domínio do computador para o seu domínio.

1. Aberto **Utilizadores e Computadores de Diretório Ativo (DSA.msc)** .

1. Clique na unidade organizacional que utilizará para criar computadores híbridos ligados a AD e, em seguida, selecione **Controlo de Delegados**.

    ![O comando de Controlo de Delegados](./media/windows-autopilot-hybrid/delegate-control.png)

1. Na **delegação de controlo,** selecione **Next** > **Adicionar** tipos de **objetos** > .

1. No painel **'Tipos de Objectos',** selecione a caixa de verificação **de computadores** e, em seguida, selecione **OK**.

    ![O painel dos tipos de objetos](./media/windows-autopilot-hybrid/object-types-computers.png)

1. No painel **De Utilizadores, Computadores ou Grupos Selecionados,** no **painel De introduzir os nomes do objeto para selecionar** a caixa, introduza o nome do computador onde o Conector está instalado.

    ![O painel de Utilizadores, Computadores ou Grupos Selecionados](./media/windows-autopilot-hybrid/enter-object-names.png)

1. Selecione **'Verificar Nomes'** para validar a sua entrada, selecione **OK**, e depois selecione **Next**.

1. Selecione **Criar uma tarefa personalizada para delegar** > **Seguinte**.

1. Selecione os **seguintes objetos na** caixa de verificação da pasta e, em seguida, selecione os **objetos do Computador**, **Crie objetos selecionados nesta pasta**e **elimine os objetos selecionados nesta pasta** verifique as caixas de verificação.

    ![O painel do tipo de objeto de diretório ativo](./media/windows-autopilot-hybrid/only-following-objects.png)
    
1. Selecione **Seguinte**.

1. Em **Permissões,** selecione a caixa de verificação **De Controlo Completo.**  
    Esta ação seleciona todas as outras opções.

    ![O painel de Permissões](./media/windows-autopilot-hybrid/full-control.png)

1. Selecione **Seguinte**, e, em seguida, selecione **Terminar**.

## <a name="install-the-intune-connector"></a>Instalar o Conector do Intune

O Conector Intune para Diretório Ativo deve ser instalado num computador que esteja a executar o Windows Server 2016 ou mais tarde. O computador também deve ter acesso à internet e ao seu Diretório Ativo. Para aumentar o dimensionamento e a disponibilidade ou suportar múltiplos domínios do Azure Active Directory, pode instalar múltiplos conectores no seu ambiente. Recomendamos a instalação do Conector num servidor que não esteja a executar outros conectores Intune.

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)selecione **Dispositivos** > **Windows** > **windows inscrição** > **Intune Connector for Ative Directory** > **Add**. 
2. Siga as instruções para descarregar o Conector.
3. Abra o ficheiro de configuração do Connector descarregado, *ODJConnectorBootstrapper.exe,* para instalar o Conector.
4. No final da configuração, **selecione Configurar**.
5. Selecione **Iniciar sessão**.
6. Introduza as credenciais de função de Administrador Global do Utilizador ou Administrador Intune.  
   A conta de utilizador deve ter uma licença Intune atribuída.
7. Vá a **Dispositivos** > **Windows** > **inscrição no Windows** > **Intune Connector para Diretório Ativo**, e depois confirme que o estado de ligação está **Ativo**.

> [!NOTE]
> Depois de iniciar sessão no Connector, pode levar alguns minutos a aparecer no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431). Só aparece se conseguir comunicar com sucesso com o serviço Intune.

### <a name="turn-off-ie-enhanced-security-configuration"></a>Desligue a configuração de segurança melhorada do IE
Por padrão, o Windows Server tem configuração de segurança melhorada do Internet Explorer. Se não conseguir iniciar sessão no Conector Intune para diretório ativo, desligue a configuração de segurança melhorada do IE para o Administrador. [Como desligar a configuração de segurança melhorada do Internet Explorer](https://blogs.technet.microsoft.com/chenley/2011/03/10/how-to-turn-off-internet-explorer-enhanced-security-configuration)

### <a name="configure-web-proxy-settings"></a>Configurar definições de proxy Web

Se tiver um representante web no seu ambiente de networking, certifique-se de que o Conector Intune para Diretório Ativo funciona corretamente, referindo-se ao [Trabalho com servidores proxy existentes no local](autopilot-hybrid-connector-proxy.md).


## <a name="create-a-device-group"></a>Criar um grupo de dispositivos
1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)selecione **Grupos** > **Novo grupo**.

1. No painel do **Grupo,** faça o seguinte:

    a. Para **o tipo de grupo,** selecione **Security**.

    b. Introduza um nome de **grupo** e **descrição do grupo**.

    c. Selecione um **tipo de Membro**.

1. Se selecionou **Dispositivos Dinâmicos** para o tipo de membro, no painel **do Grupo,** selecione **membros** do dispositivo Dynamic e, em seguida, na caixa de **regras Avançada,** faça um dos seguintes:
    - Para criar um grupo que inclua todos os seus dispositivos Autopilot, introduza `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`.
    - Os mapas de campo do Grupo Tag intune para o atributo OrderID em dispositivos AD Azure. Se pretender criar um grupo que inclua todos os seus dispositivos Autopilot com uma etiqueta de grupo específica (OrderID) deve digitar: `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Para criar um grupo que inclua todos os seus dispositivos Autopilot com um ID de Encomenda de Compra específico, introduza `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`.
    
1. Selecione **Guardar**.

1. Selecione **Criar**.  

## <a name="register-your-autopilot-devices"></a>Registar os seus dispositivos do Autopilot

Selecione uma das seguintes formas de inscrever os seus dispositivos Autopilot.

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Registar dispositivos do Autopilot que já estejam inscritos

1. Crie um perfil de implementação do Autopilot com a opção **Autopilot** definida para **Sim**. 
2. Atribuir o perfil a um grupo que contenha os membros que pretende registar automaticamente com o Autopilot.

Para obter mais informações, veja [Criar um perfil de implementação do Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Registar dispositivos do Autopilot que não estão inscritos

Se os seus dispositivos ainda não estiverem inscritos, pode registá-los. Para obter mais informações, veja [Adicionar dispositivos](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Registar dispositivos de um OEM

Se comprar novos dispositivos, alguns OEMs podem registar os dispositivos por si. Para obter mais informações, veja a [página do Windows Autopilot](https://aka.ms/WindowsAutopilot).

Quando os seus dispositivos Autopilot estão *registados,* antes de serem matriculados em Intune, são apresentados em três locais (com nomes definidos para os seus números de série):
- O painel **de dispositivos autopiloto** no Intune no portal Azure. Selecione a **inscrição do Dispositivo** > dispositivos de **inscrição** do Windows > **Dispositivos**.
- Os **dispositivos Azure AD** painelam no Intune no portal Azure. Selecione **Dispositivos** > **Dispositivos AD Azure**.
- O **painel Azure AD All Devices** no Azure Ative Directory no portal Azure selecionando **Dispositivos** > **Todos os Dispositivos**.

Depois de *matriculados*os seus dispositivos Autopilot, são apresentados em quatro locais:
- O painel **de dispositivos autopiloto** no Intune no portal Azure. Selecione a **inscrição do Dispositivo** > dispositivos de **inscrição** do Windows > **Dispositivos**.
- Os **dispositivos Azure AD** painelam no Intune no portal Azure. Selecione **Dispositivos** > **Dispositivos AD Azure**.
- O **painel Azure AD All Devices** pane in Azure Ative Directory no portal Azure. Selecione **Dispositivos** > **Todos os Dispositivos**.
- O painel **All Devices** no Intune no portal Azure. Selecione **Dispositivos** > **Todos os Dispositivos**.

Depois de matriculados os seus dispositivos Autopilot, os seus nomes tornam-se o nome de anfitrião do dispositivo. Por predefinição, o nome de anfitrião começa com *DESKTOP-* .


## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Criar e atribuir um perfil de implementação do Autopilot
Os perfis de implementação do Autopilot são utilizados para configurar os dispositivos do Autopilot.

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)selecione **Dispositivos** > **Windows** > **Windows > ** Perfis de **implementação** > **Criar Perfil**.
2. Na página **Basics,** digite um **nome** e **descrição**opcional.
3. Se pretender que todos os dispositivos nos grupos atribuídos sejam convertidos automaticamente no Autopilot, defina **Converter todos os dispositivos visados para o Piloto Automático** para **Sim**. Todos os dispositivos corporativos e não autopilotos em grupos designados registar-se-ão no serviço de implementação do Autopilot. Os dispositivos pessoais não serão convertidos para Piloto Automático. O processo de registo demora até 48 horas, pelo que deverá aguardar. Quando a inscrição do dispositivo for anulada e o dispositivo for reposto, o Autopilot irá inscrevê-lo. Após registar um dispositivo desta forma, desativar esta opção ou remover a atribuição de perfil não irá remover o dispositivo do serviço de implementação do Autopilot. Em alternativa, tem de [remover o dispositivo diretamente](enrollment-autopilot.md#delete-autopilot-devices).
4. Selecione **Seguinte**.
5. Na página **Out-of-box (OOBE)** para modo de **implantação,** selecione **-driven User**.
6. No **Join to Azure AD como** caixa, selecione **Hybrid Azure AD juntou-se**.
7. Configure as opções restantes na página **de experiência Out-of-box (OOBE)** conforme necessário.
8. Selecione **Seguinte**.
9. Na página **scope tags,** selecione [etiquetas](../fundamentals/scope-tags.md) de âmbito para este perfil.
10. Selecione **Seguinte**.
11. Na página **de Atribuiçãos,** selecione **Select groups para incluir** > procure e selecione o grupo de dispositivos > **Selecione**.
12. Selecione **Next** > **Criar**.

Leva cerca de 15 minutos para que o estado do perfil do dispositivo mude de *Não atribuído* a *Atribuir* e, finalmente, para *Designado*.

## <a name="optional-turn-on-the-enrollment-status-page"></a>(Opcional) Ligue a página de estado da inscrição

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)selecione **Dispositivos** > **Windows** > Windows > página de estado de **inscrição** .
1. No painel da página de estado de **inscrição,** selecione **Definições** **predefinidas** > .
1. Na **app Show e** na caixa de progresso de instalação de perfil, selecione **Sim**.
1. Configure as outras opções conforme seja necessário.
1. Selecione **Guardar**.

## <a name="create-and-assign-a-domain-join-profile"></a>Criar e atribuir um perfil de Associação a um Domínio

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)selecione **Dispositivos** > perfis de **configuração** > **Criar Perfil**.
2. Introduza as seguintes propriedades:
   - **Nome**: introduza um nome descritivo para o novo perfil.
   - **Descrição:** introduza uma descrição para o perfil.
   - **Plataforma**: Selecione **o Windows 10 e mais tarde**.
   - **Tipo de perfil**: Selecione **A juntar domínio (Pré-visualização)** .
3. Selecione **Definições,** e, em seguida, forneça um prefixo de nome de **computador,** **nome de domínio**.
4. (Opcional) Fornecer uma **unidade organizacional** (OU) em [formato DN](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name). As suas opções são:
   - Forneça um OU no qual delegou o controlo para o seu dispositivo Windows 2016 que está a executar o Conector Intune.
   - Forneça um OU no qual delegou o controlo para os computadores radiculares no seu diretório ativo on-prem.
   - Se deixar isto em branco, o objeto de computador será criado no recipiente predefinido do Diretório Ativo (CN=Computadores se nunca o [tiver alterado).](https://support.microsoft.com/en-us/help/324949/redirecting-the-users-and-computers-containers-in-active-directory-dom)
   
   Aqui estão alguns exemplos válidos:
   - OU=Nível 1,OU=Nível2,DC=contoso,DC=com
   - OU=Mine,DC=contoso,DC=com
   
   Aqui estão alguns exemplos que não são válidos:
   - CN=Computadores,DC=contoso,DC=com (não pode especificar um recipiente, em vez disso, deixe o valor em branco para usar o padrão para o domínio)
   - OU=Mina (deve especificar o domínio através dos atributos DC=)
     
   > [!NOTE]
   > Não utilize aspas em torno do valor da **unidade organizacional**.
5. Selecione **OK** > **Criar**.  
    O perfil é criado e exibido na lista.
6. Para atribuir o perfil, siga os passos sob o [perfil de Atribuir um dispositivo](../configuration/device-profile-assign.md#assign-a-device-profile) e atribua o perfil ao mesmo grupo utilizado nesta fase Criar um grupo de [dispositivos](windows-autopilot-hybrid.md#create-a-device-group)
   - Implementação de múltiplos perfis de Adesão de Domínio
   
     a. Crie um grupo dinâmico que inclua todos os seus dispositivos Autopilot com um perfil de implementação de Piloto Automático específico, introduza (dispositivo.registrationProfileName -eq "Nome de perfil de piloto automático"). 
     
     b. Substitua o 'Nome do Perfil do Piloto Automático' com o nome de visualização do perfil criado no âmbito [create e atribua um perfil de implementação autopiloto](windows-autopilot-hybrid.md#create-and-assign-an-autopilot-deployment-profile). 
     
     c. Crie vários perfis de implementação do Autopilot e atribua esse dispositivo ao perfil especificado neste grupo dinâmico.

> [!NOTE]
> As capacidades de nomeação para o Windows Autopilot para Hybrid Azure AD Join não suportam variáveis como %SERIAL% e apenas suportam prefixos para o nome do computador.

## <a name="next-steps"></a>Próximos passos

Após configurar o Windows Autopilot, saiba como gerir os seus dispositivos. Para mais informações, consulte [o que é a gestão do dispositivo Microsoft Intune?](../remote-actions/device-management.md)
