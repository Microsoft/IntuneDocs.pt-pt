---
title: Inscrição para híbrido do Azure AD associado dispositivos - Windows Autopilot
titleSuffix: ''
description: Utilizar o Windows Autopilot para inscrever híbrido do Azure AD associado dispositivos no Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: be0598d09f10403892fa6a82e109ecc90015ccf9
ms.sourcegitcommit: 47d8ca144ea4e8b8817e95ac4b8c6bd8591fcc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/14/2019
ms.locfileid: "65619442"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-by-using-intune-and-windows-autopilot"></a>Implementação híbrida do Azure AD associado dispositivos com o Intune e o Windows Autopilot
Pode utilizar o Intune e o Windows Autopilot para configurar híbrida do Azure Active Directory (Azure AD)-dispositivos associados a um. Para tal, siga os passos neste artigo.

## <a name="prerequisites"></a>Pré-requisitos

Configurar com êxito a sua [híbrido do Azure dispositivos associados ao AD](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan). Não se esqueça [Verifique se o registo do dispositivo]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration) utilizando o cmdlet Get-MsolDevice.

Os dispositivos a ser inscritos também têm de:
- Executar o Windows 10 com a [atualização de outubro de 2018](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/).
- Ter acesso à Internet.
- Terá acesso ao seu Active Directory (ligação de VPN não é suportada neste momento).
- São submetidos a experiência de out-of-box (OOBE).
- Ser capaz de enviar pings para o controlador de domínio do domínio que está a tentar associar.

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurar a inscrição automática de dispositivos Windows 10

1. Inicie sessão para o [portal do Azure](https://portal.azure.com) e, no painel esquerdo, selecione **Azure Active Directory**.

   ![O portal do Azure](./media/auto-enroll-azure-main.png)

1. Selecione **Mobilidade (MDM e MAM)**.

   ![O painel Azure Active Directory](./media/auto-enroll-mdm.png)

1. Selecione **Microsoft Intune**.

   ![O painel de mobilidade (MDM e MAM)](./media/auto-enroll-intune.png)

1. Certifique-se de que os utilizadores que implementar dispositivos associados ao AD Azure com o Intune e Windows são membros de um grupo que está incluído no seu **âmbito do utilizador MDM**.

   ![O painel de configuração de mobilidade (MDM e MAM)](./media/auto-enroll-scope.png)

1. Utilize os valores predefinidos no **MDM dos termos de utilização URL**, **URL de deteção de MDM**, e **URL de conformidade de MDM** caixas e, em seguida, selecione **guardar**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Aumentar o limite de contas de computador na Unidade Organizacional

O conector do Intune para o Active Directory cria inscritos autopilot computadores no domínio do Active Directory no local. O computador que aloja o conector do Intune tem de ter os direitos para criar os objetos de computador no domínio. 

Em alguns domínios, computadores não são concedidos os direitos para criar computadores. Além disso, domínios têm um limite interno (predefinição de 10) que se aplica a todos os utilizadores e computadores que não são delegados direitos para criar objetos de computador. Por conseguinte, os direitos tem de ser delegado a computadores que alojam o conector do Intune na unidade organizacional onde híbrido do Azure são criados dispositivos associados ao AD.

A unidade organizacional tem direitos para criar computadores tem de corresponder ao:
- A unidade organizacional que é introduzida no perfil de associação a um domínio.
- Não se for selecionado nenhum perfil, nome de domínio do computador para o seu domínio.

1. Open **utilizadores do Active Directory e computadores (DSA. msc)**.

1. A unidade organizacional que irá utilizar para criar híbrido do Azure com o botão direito computadores associados ao AD e, em seguida, selecione **delegar controlo**.

    ![O comando de delegar controlo](media/windows-autopilot-hybrid/delegate-control.png)

1. Na **delegação do controle** assistente, selecione **próxima** > **adicionar** > **tipos de objeto**.

1. Na **tipos de objeto** painel, selecione a **computadores** caixa de verificação e, em seguida, selecione **OK**.

    ![O painel de tipos de objeto](media/windows-autopilot-hybrid/object-types-computers.png)

1. Na **selecionar utilizadores, computadores ou grupos** painel, na **introduza os nomes de objeto a selecionar** , introduza o nome do computador em que o conector é instalado.

    ![O painel selecionar utilizadores, computadores ou grupos](media/windows-autopilot-hybrid/enter-object-names.png)

1. Selecione **verificar nomes** para validar a sua participação, selecione **OK**e, em seguida, selecione **seguinte**.

1. Selecione **criar uma tarefa personalizada para delegar** > **seguinte**.

1. Selecione o **apenas os seguintes objetos na pasta** caixa de verificação e, em seguida, selecione a **objetos de computador**, **criar objetos selecionados nesta pasta**, e  **Eliminar objetos selecionados nesta pasta** caixas de verificação.

    ![O painel de tipo de objeto do Active Directory](media/windows-autopilot-hybrid/only-following-objects.png)
    
1. Selecione **Seguinte**.

1. Sob **permissões**, selecione a **controlo total** caixa de verificação.  
    Esta ação seleciona todas as outras opções.

    ![O painel de permissões](media/windows-autopilot-hybrid/full-control.png)

1. Selecione **próxima**e, em seguida, selecione **concluir**.

## <a name="install-the-intune-connector"></a>Instalar o Conector do Intune

O conector do Intune para o Active Directory tem de ser instalados num computador que está a executar o Windows Server 2016 ou posterior. O computador também tem de ter acesso à internet e o Active Directory. Para aumentar o dimensionamento e a disponibilidade ou suportar múltiplos domínios do Azure Active Directory, pode instalar múltiplos conectores no seu ambiente. Recomendamos que instale o conector num servidor que não está em execução quaisquer outros conectores do Intune.

1. Certifique-se de que tem um pacote de idiomas instalado e configurado conforme descrito em [os requisitos de idioma do conector do Intune (pré-visualização)](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector).
2. Na [Intune](https://aka.ms/intuneportal), selecione **inscrição de dispositivos** > **inscrição Windows** > **conector do Intune para o Active Directory ( Pré-visualização)** > **adicionar conector**. 
3. Siga as instruções para transferir o conector.
4. Abra o ficheiro de configuração para o conector transferido *ODJConnectorBootstrapper.exe*, para instalar o conector.
5. No final da configuração, selecione **configurar**.
6. Selecione **iniciar sessão**.
7. Introduza as credenciais de função de Administrador Global ou administrador do Intune de utilizador.  
   A conta de utilizador tem de ter uma licença do Intune atribuída.
8. Aceda a **inscrição de dispositivos** > **inscrição Windows** > **conector do Intune para o Active Directory (pré-visualização)** e, em seguida, confirme que o Estado da ligação é **Active Directory**.

> [!NOTE]
> Depois de iniciar sessão para o conector, poderá demorar alguns minutos a aparecer na [Intune](https://aka.ms/intuneportal). Ele só será apresentada se consegue comunicar com êxito com o serviço Intune.

### <a name="configure-web-proxy-settings"></a>Configurar definições de proxy Web

Se tiver um proxy web no seu ambiente de rede, certifique-se de que o conector do Intune para o Active Directory funciona corretamente por consultar [funcionam com o existente no local servidores proxy](autopilot-hybrid-connector-proxy.md).


## <a name="create-a-device-group"></a>Criar um grupo de dispositivos
1. Na [Intune](https://aka.ms/intuneportal), selecione **grupos** > **novo grupo**.

1. Na **grupo** painel, faça o seguinte:

    a. Para **tipo de grupo**, selecione **segurança**.

    b. Introduza um **nome do grupo** e **descrição do grupo**.

    c. Selecione um **tipo de associação**.

1. Se tiver selecionado **dispositivos dinâmica** para o tipo de associação, no **grupo** painel, selecione **membros de dispositivo dinâmicos** e, em seguida, no **regra avançada** caixa, efetue um dos seguintes procedimentos:
    - Para criar um grupo que inclua todos os seus dispositivos Autopilot, introduza `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`.
    - Para criar um grupo que inclua todos os seus dispositivos Autopilot com um ID de ordem específica, introduza `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`.
    - Para criar um grupo que inclua todos os seus dispositivos Autopilot com um ID de ordem de compra específico, introduza `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`.
    
1. Selecione **Guardar**.

1. Selecione **Criar**.  

## <a name="register-your-autopilot-devices"></a>Registar os seus dispositivos do Autopilot

Selecione uma das seguintes formas de inscrever os dispositivos Autopilot.

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Registar dispositivos do Autopilot que já estejam inscritos

1. Crie um perfil de implementação do Autopilot com a opção **Autopilot** definida para **Sim**. 
2. Atribua o perfil a um grupo que contém os membros que pretende registar automaticamente com o Autopilot.

Para obter mais informações, veja [Criar um perfil de implementação do Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Registar dispositivos do Autopilot que não estão inscritos

Se os seus dispositivos ainda não estiverem inscritos, pode registá-los. Para obter mais informações, veja [Adicionar dispositivos](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Registar dispositivos de um OEM

Se comprar novos dispositivos, alguns OEMs podem registar os dispositivos por si. Para obter mais informações, veja a [página do Windows Autopilot](http://aka.ms/WindowsAutopilot).

Quando os seus dispositivos Autopilot estão *registado*, antes de serem inscritos no Intune, estes são apresentados em três locais (com nomes de definir seus números de série):
- O **dispositivos Autopilot** painel do Intune no portal do Azure. Selecione **inscrição de dispositivos** > **inscrição Windows** > **dispositivos**.
- O **dispositivos do Azure AD** painel do Intune no portal do Azure. Selecione **dispositivos** > **dispositivos do Azure AD**.
- O **do Azure AD todos os dispositivos** painel no Azure Active Directory no portal do Azure ao selecionar **dispositivos** > **todos os dispositivos**.

Depois do Autopilot dispositivos estão *inscritos*, estes são apresentados em quatro locais:
- O **dispositivos Autopilot** painel do Intune no portal do Azure. Selecione **inscrição de dispositivos** > **inscrição Windows** > **dispositivos**.
- O **dispositivos do Azure AD** painel do Intune no portal do Azure. Selecione **dispositivos** > **dispositivos do Azure AD**.
- O **do Azure AD todos os dispositivos** painel no Azure Active Directory no portal do Azure. Selecione **dispositivos** > **todos os dispositivos**.
- O **todos os dispositivos** painel do Intune no portal do Azure. Selecione **dispositivos** > **todos os dispositivos**.

Após a inscrição dos seus dispositivos Autopilot, seus nomes tornam-se o nome de anfitrião do dispositivo. Por predefinição, o nome de anfitrião começa com *DESKTOP -*.


## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Criar e atribuir um perfil de implementação do Autopilot
Os perfis de implementação do Autopilot são utilizados para configurar os dispositivos do Autopilot.

1. Na [Intune](https://aka.ms/intuneportal), selecione **inscrição de dispositivos** > **inscrição Windows** > **perfis de implementação**  >  **Criar perfil**.
1. Introduza um **Name** e, opcionalmente, uma **Descrição**.
1. Para **modo de implementação**, selecione **controlada pelo usuário**.
1. Na **aderir ao Azure AD como** caixa, selecione **Azure AD híbrido associou (pré-visualização)**.
1. Selecione **experiência de Out-of-box (OOBE)**, configure as opções, conforme necessário e, em seguida, selecione **guardar**.
1. Selecione **Criar** para criar o perfil. 
1. No painel de perfil, selecione **atribuições**.
1. Selecione **selecionar grupos**.
1. Na **selecionar grupos** painel, selecione o grupo de dispositivos e, em seguida, clique em **selecione**.

Demora cerca de 15 minutos para que o estado do perfil de dispositivo a alterar no *não atribuído* ao *atribuir* e, por fim, para *atribuído*.

## <a name="optional-turn-on-the-enrollment-status-page"></a>(Opcional) Ativar a página de estado de inscrição

1. Na [Intune](https://aka.ms/intuneportal), selecione **inscrição de dispositivos** > **inscrição Windows** > **página de estado de inscrição (pré-visualização)**.
1. Na **página de estado de inscrição** painel, selecione **predefinido** > **definições**.
1. Na **Mostrar o progresso de instalação da aplicação e o perfil** caixa, selecione **Sim**.
1. Configure as outras opções conforme seja necessário.
1. Selecione **Guardar**.

## <a name="create-and-assign-a-domain-join-profile"></a>Criar e atribuir um perfil de Associação a um Domínio

1. Na [Intune](https://aka.ms/intuneportal), selecione **configuração do dispositivo** > **perfis** > **criar perfil**.
1. Introduza as seguintes propriedades:
   - **Nome**: Introduza um nome descritivo para o novo perfil.
   - **Descrição**: Introduza uma descrição para o perfil.
   - **Plataforma**: Selecione **Windows 10 e posterior**.
   - **Tipo de perfil**: Selecione **ingresso no domínio (pré-visualização)**.
1. Selecione **configurações**e, em seguida, forneça um **prefixo do nome do computador**, **nome de domínio**e (opcional) **unidade organizacional** no [Formato de DN](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name). 
1. Selecione **OK** > **criar**.  
    O perfil é criado e apresentado na lista.
1. Para atribuir o perfil, siga os passos em [atribuir um perfil de dispositivo](device-profile-assign.md#assign-a-device-profile) e atribuir o perfil ao mesmo grupo utilizado nesta etapa [criar um grupo de dispositivos](windows-autopilot-hybrid.md#create-a-device-group)
   - Implementar vários perfis de associação a um domínio
   
     a. Criar um grupo dinâmico que inclui todos os seus dispositivos Autopilot com um perfil de implementação do Autopilot específico, introduza (device.enrollmentProfileName - eq "Nome do perfil Autopilot"). 
     
     b. Substitua o "Nome do perfil Autopilot" com o nome a apresentar do perfil criado sob [criar e atribuir um perfil de implementação do Autopilot](windows-autopilot-hybrid.md#create-and-assign-an-autopilot-deployment-profile). 
     
     c. Crie múltiplos perfis de implementação do Autopilot e atribua esse dispositivo para o perfil especificado neste grupo dinâmico.

> [!NOTE]
> As capacidades de nomenclatura para Windows Autopilot híbrida associação do Azure AD não suportam variáveis como % SERIAL % e apenas suportam prefixos para o nome do computador.

## <a name="next-steps"></a>Passos Seguintes

Após configurar o Windows Autopilot, saiba como gerir os seus dispositivos. Para obter mais informações, consulte [o que é a gestão de dispositivos do Microsoft Intune?](device-management.md).
