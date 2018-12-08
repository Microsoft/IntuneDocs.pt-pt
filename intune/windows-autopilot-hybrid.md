---
title: Inscrição para híbrida do Active Directory associados a um dispositivos com o Windows Autopilot
titleSuffix: Microsoft Intune
description: Utilizar o Windows Autopilot para inscrever dispositivos híbridos associados ao Azure Active Directory no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: ed404d97b2fe0ccf38a5d3946819fd8225127581
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032321"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-using-intune-and-windows-autopilot-preview"></a>Implementar dispositivos híbridos associados ao Azure Active Directory com o Intune e o Windows Autopilot (Pré-visualização)
Pode utilizar o Intune e o Windows Autopilot para configurar dispositivos híbridos associados ao Azure Active Directory. Para o fazer, siga os passos abaixo.

> [!NOTE]
> Esta funcionalidade será implementada na base de utilizadores nos próximos dias. Assim, poderá não conseguir seguir estes passos até que a mesma seja implementada na sua conta.

## <a name="prerequisites"></a>Pré-requisitos

- Configurar [dispositivos híbridos associados ao Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan) com êxito.
    - Garantir a [verificação do registo ao utilizar o cmdlet Get-MsolDevice]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration).

Os dispositivos a ser inscritos também têm de:
- Executar o Windows 10 com a [atualização de outubro de 2018](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/).
- Ter acesso à Internet.
- Ter acesso ao seu Active Directory (A ligação VPN não é suportada).
- Passar pela Experiência de Configuração Inicial (OOBE).

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurar a inscrição automática de dispositivos Windows 10

1. Inicie sessão no [portal do Azure](https://portal.azure.com) e selecione **Azure Active Directory**.

   ![Captura de ecrã do portal do Azure](./media/auto-enroll-azure-main.png)

2. Selecione **Mobilidade (MDM e MAM)**.

   ![Captura de ecrã do portal do Azure](./media/auto-enroll-mdm.png)

3. Selecione **Microsoft Intune**.

   ![Captura de ecrã do portal do Azure](./media/auto-enroll-intune.png)

4. Certifique-se de que os utilizadores que irão implementar dispositivos associados ao Azure Active Directory através do Intune e Windows são membros de um grupo incluído no seu **Âmbito de utilizadores de MDM**.

   ![Captura de ecrã do portal do Azure](./media/auto-enroll-scope.png)

5. Utilize os valores predefinidos para os seguintes URLs:
    - **URL dos Termos de utilização de MDM**
    - **URL de Deteção de MDM**
    - **URL de Conformidade de MDM**
6. Escolha **Guardar**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Aumentar o limite de contas de computador na Unidade Organizacional

O Conector do Intune para o Active Directory cria computadores inscritos com o Autopilot no domínio do Active Directory no local. O computador que aloja o Conector do Intune tem de ter os direitos para criar os objetos de computador no domínio. 

Em alguns domínios, não é concedido aos computadores o direito de criar computadores. Além disso, a domínios que têm um concebidos no limite (predefinição de 10), que se aplica a todos os utilizadores e computadores que não são delegados direitos para criar objetos de computador. Por conseguinte, são criados a necessidade de direitos sejam delegadas a computadores que alojam o conector do Intune na unidade organizacional em que dispositivos associados ao Azure AD híbrido.

A unidade organizacional com o direito de criar computadores tem de corresponder:
- à unidade organizacional introduzida no perfil Associação a um Domínio
- ou, se nenhum perfil estiver selecionado, ao nome de domínio do computador para o seu domínio.

1. Abra o **Active Directory Users and Computers** (DSA.msc).

2. Clique com o botão direito do rato na unidade organizacional que irá utilizar para criar computadores híbridos associados ao Azure Active Directory > **Delegate Control** (Delegar Controlo).

    ![Captura de ecrã a mostrar a opção Delegate Control (Delegar Controlo)](media/windows-autopilot-hybrid/delegate-control.png)

3. No assistente de **Delegation of Control** (Delegação de Controlo), selecione **Next** (Seguinte) > **Add...** (Adicionar...) > **Object Types** (Tipos de Objeto).

4. Na caixa de diálogo **Object Types** (Tipos de Objeto), selecione **Computers** (Computadores) e, em seguida, selecione **OK**.

    ![Captura de ecrã a mostrar a opção Delegate Control (Delegar Controlo)](media/windows-autopilot-hybrid/object-types-computers.png)

5. Na caixa de diálogo **Select Users, Computers, or Groups** (Selecionar Utilizadores, Computadores ou Grupos), na caixa **Enter the object names to select** (Introduza os nomes de objetos a selecionar), introduza o nome do computador em que o Conector está instalado.

    ![Captura de ecrã a mostrar a opção Delegate Control (Delegar Controlo)](media/windows-autopilot-hybrid/enter-object-names.png)

6. Selecione **Check Names** (Verificar Nomes) para validar a sua entrada e, em seguida, selecione **OK** > **Next** (Seguinte).

7. Selecione **Create a custom task to delegate** (Criar uma tarefa personalizada para delegar) > **Next** (Seguinte).

8. Selecione **Only the following objects in the folder** (Apenas os seguintes objetos na pasta) e, em seguida, selecione as seguintes opções:
    - **Computer objects** (Objetos de computador)
    - **Create selected objects in this folder** (Criar os objetos selecionados nesta pasta)
    - **Delete selected objects in this folder** (Eliminar os objetos selecionados nesta pasta)

    ![Captura de ecrã a mostrar a opção Delegate Control (Delegar Controlo)](media/windows-autopilot-hybrid/only-following-objects.png)
    
9. Selecione **Next**.

10. Em **Permissions** (Permissões), selecione **Full Control** (Controlo Total) (todas as outras opções serão selecionadas com esta ação) > **Next** (Seguinte) > **Finish** (Concluir).

    ![Captura de ecrã a mostrar a opção Delegate Control (Delegar Controlo)](media/windows-autopilot-hybrid/full-control.png)

## <a name="install-the-intune-connector"></a>Instalar o Conector do Intune

O Conector do Intune para o Azure Active Directory tem de ser instalado num computador com o Windows Server 2016 e acesso à Internet e ao Azure Active Directory. Para aumentar o dimensionamento e a disponibilidade ou suportar múltiplos domínios do Azure Active Directory, pode instalar múltiplos conectores no seu ambiente. Recomendamos a instalação do conector num servidor que não execute outros conectores do Intune.

1. Certifique-se de que tem um pacote de idiomas instalado e configurado conforme descrito em [os requisitos de idioma do conector do Intune (pré-visualização)](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector).
2. No [Intune](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Conector do Intune para o Active Directory (Pré-visualização)** > **Adicionar conector**. 
3. Siga as instruções para transferir o conector.
4. Abra o ficheiro de configuração do conector transferido para instalar o conector (ODJConnectorBootstrapper.exe).
5. No fim da configuração, selecione **Configurar**.
6. Selecione **Iniciar Sessão**.
7. Introduza credenciais de utilizador com a função Administrador Global ou Administrador do Intune.
8. Aceda a **Inscrição de dispositivos** > **Inscrição no Windows** > **Conector do Intune para o Active Directory (Pré-visualização)** e confirme que o estado de ligação é **Ativo**.

### <a name="configure-web-proxy-settings"></a>Configurar definições de proxy Web

Se tiver um proxy Web no seu ambiente de rede, siga as instruções aqui apresentadas, para que o Conector do Intune para o Active Directory funcione corretamente: [Trabalhar com servidores proxy no local existentes](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers).


## <a name="create-a-device-group"></a>Criar um grupo de dispositivos
1. No [Intune](https://aka.ms/intuneportal), selecione **Grupos** > **Novo grupo**.
2. No painel **Grupo**:
    1. Para **Tipo de grupo**, selecione **Segurança**.
    2. Introduza um **Nome do grupo** e uma **Descrição do grupo**.
    3. Selecione um **Tipo de associação**.
3. Se acima optou por **Dispositivo Dinâmico** para o **Tipo de associação**, no painel **Grupo**, selecione **Membros de dispositivo dinâmicos** e escreva o seguinte código na caixa **Regra avançada**.
    - Se quiser criar um grupo que inclua todos os seus dispositivos do Autopilot, escreva `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Se quiser criar um grupo que inclua todos os seus dispositivos do Autopilot com um ID do pedido específico, escreva `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - Se quiser criar um grupo que inclua todos os seus dispositivos do Autopilot com um ID de Nota de Encomenda específico, escreva `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Depois de adicionar o código da **Regra avançada**, selecione **Guardar**.
5. Selecione **Criar**.  

## <a name="register-your-autopilot-devices"></a>Registar os seus dispositivos do Autopilot

Selecione uma das seguintes formas de inscrever os seus dispositivos do Autopilot:

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Registar dispositivos do Autopilot que já estejam inscritos

1. Crie um perfil de implementação do Autopilot com a opção **Autopilot** definida para **Sim**. 
2. Atribua o perfil a um grupo com os membros que pretende registar automaticamente com o Autopilot.

Para obter mais informações, veja [Criar um perfil de implementação do Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Registar dispositivos do Autopilot que não estão inscritos

Se os seus dispositivos ainda não estiverem inscritos, pode registá-los. Para obter mais informações, veja [Adicionar dispositivos](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Registar dispositivos de um OEM

Se comprar novos dispositivos, alguns OEMs podem registar os dispositivos por si. Para obter mais informações, veja a [página do Windows Autopilot](http://aka.ms/WindowsAutopilot).

Quando os dispositivos do Autopilot estiverem registados (e antes de serem inscritos no Intune), poderá vê-los em três locais (com os nomes definidos para os seus números de série):
- No painel Dispositivos do Autopilot, no Intune, no portal do Azure (**Inscrição de dispositivos** > **Inscrição do Windows** > **Dispositivos**).
- No painel Dispositivos do Azure AD, no Intune, no portal do Azure (**Dispositivos** > **Dispositivos do Azure AD**).
- No painel Todos os Dispositivos do AAD, no Azure Active Directory, no portal do Azure (**Dispositivos** > **Todos os Dispositivos**).

Quando os dispositivos do Autopilot estiverem inscritos, poderá vê-los em quatro locais:
- No Painel Dispositivos do Autopilot, no Intune, no portal do Azure (**Inscrição de dispositivos** > **Inscrição do Windows** > **Dispositivos**).
- No painel Dispositivos do Azure AD, no Intune, no portal do Azure (**Dispositivos** > **Dispositivos do Azure AD**).
- No painel Todos os Dispositivos do AAD, no Azure Active Directory, no portal do Azure (**Dispositivos** > **Todos os Dispositivos**).
- No painel Todos os Dispositivos, no Intune, no portal do Azure (**Dispositivos** > **Todos os Dispositivos**).

Quando os dispositivos do Autopilot estiverem inscritos, os respetivos nomes serão alterados para o nome do anfitrião do dispositivo. Por predefinição, este começa por "DESKTOP-".




## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Criar e atribuir um perfil de implementação do Autopilot
Os perfis de implementação do Autopilot são utilizados para configurar os dispositivos do Autopilot.

1. No [Intune](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Perfis de Implementação** > **Criar Perfil**.
2. Escreva um **Nome** e uma **Descrição** opcional.
3. Em **Modo de implementação**, escolha **Controlado pelo utilizador**.
4. Na caixa **Aderir ao Azure AD como**, selecione **Associados ao Azure AD Híbrido (Pré-visualização)**.
5. Selecione **Experiência de configuração inicial (OOBE)**, configure as opções consoante necessário e, em seguida, selecione **Guardar**.
6. Selecione **Criar** para criar o perfil. 
7. No painel do perfil, selecione **Atribuições**.
8. Selecione **Selecionar grupos** > no painel **Selecionar grupos**, selecione o grupo de dispositivos > **Selecionar**.

O estado do perfil dos dispositivos irá demorar cerca de 15 minutos a mudar de **Não atribuído** para **A atribuir** e, por fim, para **Atribuído**.

## <a name="turn-on-the-enrollment-status-page-optional"></a>Ativar a página de estado de inscrição (opcional)

1. No [Intune](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Página de Estado de Inscrição (Pré-visualização)**.
2. No painel **Página de Estado de Inscrição**, selecione **Predefinição** > **Definições**.
3. Para **Mostrar progresso de instalação de aplicações e perfis**, selecione **Sim**.
4. Configure as outras opções conforme seja necessário.
5. Escolha **Guardar**.

## <a name="create-and-assign-a-domain-join-profile"></a>Criar e atribuir um perfil de Associação a um Domínio

1. No [Intune](https://aka.ms/intuneportal), selecione **Configuração do dispositivo** > **Perfis** > **Criar Perfil**.
2. Introduza as seguintes propriedades:
   - **Nome**: introduza um nome descritivo para o novo perfil.
   - **Descrição:** introduza uma descrição para o perfil.
   - **Plataforma**: selecione **Windows 10 e posterior**.
   - **Tipo de perfil**: selecione **Associação a um Domínio (Pré-visualização)**.
3. Selecione **Definições** e forneça um **Prefixo de nome do computador**, um **Nome de domínio** e uma **Unidade organizacional** (opcional). 
4. Selecione **OK** > **Criar**. O perfil é criado e apresentado na lista.
5. Para atribuir o perfil, siga os passos em [Atribuir um perfil do dispositivo](device-profile-assign.md#assign-a-device-profile). 

## <a name="next-steps"></a>Passos Seguintes

Após configurar o Windows Autopilot, saiba como gerir os seus dispositivos. Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](device-management.md)
