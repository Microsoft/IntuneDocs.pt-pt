---
title: Inscrever dispositivos através do Windows Autopilot
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos com o Windows 10 através do Windows Autopilot.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7b6355724a0c518cba59f70167adbcf4208fa18a
ms.sourcegitcommit: ef4bc7318449129af3dc8c0154e54a264b7bf4e5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65197617"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Inscrever dispositivos Windows no Intune com o Windows Autopilot  
O Windows Autopilot simplifica a inscrição de dispositivos no Intune. A criação e manutenção de imagens personalizadas do sistema operativo são um processo moroso. Também poderá demorar a aplicar estas imagens personalizadas do sistema operativo a novos dispositivos para as preparar para utilização antes de as disponibilizar aos seus utilizadores finais. Com o Microsoft Intune e o Autopilot, pode fornecer novos dispositivos aos seus utilizadores finais sem ter de criar, manter e aplicar imagens de sistema operativo personalizadas aos dispositivos. Ao utilizar o Intune para gerir dispositivos do Autopilot, pode gerir políticas, perfis, aplicações, entre outros, após estes serem inscritos. Para uma descrição geral das vantagens, cenários e pré-requisitos, veja [Descrição geral do Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).


## <a name="prerequisites"></a>Pré-requisitos
- [Subscrição do Intune](licenses.md)
- [A Inscrição automática no Windows tem de estar ativada](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Subscrição do Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>Como obter o CSV para importar no Intune

Veja Understanding powershell cmdlet (Compreender o cmdlet do Powershell) para obter mais informações sobre como utilizá-lo.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo/1.3/Content/Get-WindowsAutoPilotInfo.ps1)

## <a name="add-devices"></a>Adicionar dispositivos

Pode adicionar dispositivos Windows Autopilot ao importar um ficheiro CSV com as informações dos dispositivos.

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Dispositivos** > **Importar**.

    ![Captura de ecrã dos dispositivos Windows Autopilot](media/enrollment-autopilot/autopilot-import-device.png)

2. Em **Adicionar Dispositivos do Windows Autopilot**, procure um ficheiro CSV que liste os dispositivos que pretende adicionar. O ficheiro deve apresentar os números de série, os IDs dos produtos Windows, os hashes de hardware e os IDs dos pedidos opcionais dos dispositivos.

    ![Captura de ecrã de Adicionar dispositivos Windows Autopilot](media/enrollment-autopilot/autopilot-import-device2.png)

3. Escolha **Importar** para iniciar a importação das informações do dispositivo. A importação poderá demorar alguns minutos.

4. Depois de a importação estar concluída, escolha **Inscrição de dispositivos** > **Inscrição no Windows** > **Windows Autopilot** > **Dispositivos** > **Sincronizar**. Uma mensagem indica que a sincronização está em curso. O processo poderá demorar alguns minutos a concluir, consoante o número de dispositivos em sincronização.

5. Atualize a vista para ver os novos dispositivos.

## <a name="create-an-autopilot-device-group"></a>Criar um grupo de dispositivos do Autopilot

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), escolha **Grupos** > **Novo grupo**.
2. No painel **Grupo**:
    1. Para **Tipo de grupo**, selecione **Segurança**.
    2. Introduza um **Nome do grupo** e uma **Descrição do grupo**.
    3. Para **Tipo de associação**, selecione **Atribuído** ou **Dispositivo Dinâmico**.
3. Se optou por **Atribuído** para o **Tipo de associação** no passo anterior, no painel **Grupo**, selecione **Membros** e adicione dispositivos do Autopilot ao grupo.
    Os dispositivos Autopilot que ainda não estão inscritos são dispositivos em que o nome é igual ao número de série do dispositivo.
4. Se acima optou por **Dispositivo Dinâmico** para o **Tipo de associação**, no painel **Grupo**, selecione **Membros de dispositivo dinâmicos** e escreva o seguinte código na caixa **Regra avançada**.
    - Se quiser criar um grupo que inclua todos os seus dispositivos do Autopilot, escreva `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Se quiser criar um grupo que inclua todos os seus dispositivos do Autopilot com um ID do pedido específico, escreva `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - Se quiser criar um grupo que inclua todos os seus dispositivos do Autopilot com um ID de Nota de Encomenda específico, escreva `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Depois de adicionar o código da **Regra avançada**, selecione **Guardar**.
5. Selecione **Criar**.  

## <a name="create-an-autopilot-deployment-profile"></a>Criar um perfil de implementação do Autopilot
Os perfis de implementação do Autopilot são utilizados para configurar os dispositivos do Autopilot.
1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Dispositivos** > **Importar**.
2. Escreva um **Nome** e uma **Descrição** opcional.
3. Se pretender que todos os dispositivos nos grupos atribuídos sejam convertidos automaticamente no Autopilot, defina **Converter todos os dispositivos visados para o Piloto Automático** para **Sim**. Todos os dispositivos fora do Autopilot em grupos atribuídos serão registados com o serviço de implementação do Autopilot. O processo de registo demora até 48 horas, pelo que deverá aguardar. Quando a inscrição do dispositivo for anulada e o dispositivo for reposto, o Autopilot irá inscrevê-lo. Após registar um dispositivo desta forma, desativar esta opção ou remover a atribuição de perfil não irá remover o dispositivo do serviço de implementação do Autopilot. Em alternativa, tem de [remover o dispositivo diretamente](enrollment-autopilot.md#delete-autopilot-devices).
4. Para **Modo de implementação**, selecione uma destas duas opções:
    - **Controlada pelo usuário**: Os dispositivos com este perfil estão associados ao utilizador que inscreve o dispositivo. Precisa de credenciais de utilizador para inscrever o dispositivo.
    - **Implantação automática (pré-visualização)**: (requer o Windows 10, versão 1809 ou posterior) dispositivos com este perfil não estão associados com o utilizador a inscrição do dispositivo. Não são necessárias credenciais de utilizador para inscrever o dispositivo.
5. Na caixa **Aderir ao Azure AD como**, selecione **Associado ao Azure AD**.
6. Selecione **Experiência de configuração inicial (OOBE)**, configure as seguintes opções e, em seguida, selecione**Guardar**:
    - **Idioma (região)**\*: Escolha o idioma a utilizar para o dispositivo. Esta opção só está disponível se tiver optado pela **Implementação personalizada** no **Modo de implementação**.
    - **Configurar automaticamente o teclado**\*: Se um **idioma (região)** é selecionado, escolha **Sim** para ignorar a página de seleção do teclado. Esta opção só está disponível se tiver optado pela **Implementação personalizada** no **Modo de implementação**.
    - **O contrato de licença de utilizador final (EULA)**: (Windows 10, versão 1709 ou posterior) Escolha se pretende mostrar o EULA aos utilizadores.
    - **As definições de privacidade**: Escolha se pretende mostrar as definições de privacidade aos utilizadores.
    - **Ocultar alterar as opções de conta (requer o Windows 10, versão 1809 ou posterior)**: Escolher **ocultar** para impedir que alterar as opções de conta de ser apresentado nas páginas de erro de início de sessão e o domínio de empresa. Esta opção requer a [configuração da imagem corporativa da empresa no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Tipo de conta de utilizador**: Escolha o tipo de conta do usuário (**administrador** ou **padrão** utilizador).
    - **Aplicar modelo de nome de computador (requer o Windows 10, versão 1809 ou posterior)**: Escolher **Sim** para criar um modelo a utilizar quando um dispositivo de nomenclatura durante a inscrição. Os nomes têm de ter 15 carateres ou menos e podem conter letras, números e hífenes. Não podem conter apenas números. Utilize a [macro %SERIAL%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) para adicionar um número de série específico de hardware. Em alternativa, utilize a [macro %RAND:x%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) para adicionar uma cadeia de números aleatória na qual x corresponde ao número de dígitos a adicionar. 

6. Selecione **Criar** para criar o perfil. O perfil de implementação do Autopilot está agora disponível para atribuir a dispositivos.

* Ambos **idioma (região)** e **configurar automaticamente o teclado** só estão disponíveis se tiver escolhido **Self-implantação (pré-visualização)** para **modo de implementação**  (requer o Windows 10, versão 1809 ou posterior).


## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>Atribuir um perfil de implementação do Autopilot a um grupo de dispositivos

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Perfis de implementação** e selecione um perfil.
2. No painel do perfil específico, selecione **Atribuições**. 
3. Escolha **Selecionar Grupos** e, em seguida, no painel **Selecionar grupos**, escolha os grupos aos quais pretende atribuir o perfil. Em seguida, clique em **Selecionar**.


> [!NOTE]
> O Intune irá verificar periodicamente a existência de novos dispositivos nos grupos atribuídos e, em seguida, iniciar o processo de atribuição de perfis a esses dispositivos. Este processo pode demorar vários minutos a concluir. Antes de implementar um dispositivo, certifique-se de que concluiu este processo.  Pode verificar sob **inscrição de dispositivos** > * * a inscrição de Windows * * > **dispositivos** onde deverá ver o estado do perfil alterar de "Não atribuído" para "Atribuir" e, finalmente, para "Atribuído."

## <a name="edit-an-autopilot-deployment-profile"></a>Editar um perfil de implementação do Autopilot
Após ter criado um perfil de implementação do Autopilot, poderá editar determinadas partes do perfil de implementação.   

1. No [Intune, no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos**.
2. Em **Inscrição no Windows**, na secção **Windows Autopilot**, selecione **Perfis de Implementação**.
3. Selecione o perfil que pretende editar.
4. À esquerda, clique em **Propriedades** para alterar o nome ou a descrição do perfil de implementação. Após ter efetuado as alterações, clique em **Guardar**.
5. Clique em **Definições** para efetuar alterações às definições da OOBE. Após ter efetuado as alterações, clique em **Guardar**.

> [!NOTE]
> As alterações ao perfil são aplicadas aos dispositivos atribuídos a esse perfil. No entanto, o perfil atualizado não será aplicado a um dispositivo já inscrito no Intune até que o dispositivo tenha sido reposto e reinscrito.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Dispositivos de alertas para o Windows Autopilot não atribuídos  <!-- 163236 -->  

Os alertas irão indicar quantos dispositivos do programa Autopilot não têm perfis de implementação do Autopilot. Utilize as informações no alerta para criar perfis e atribui-los aos dispositivos não atribuídos. Quando clica no alerta, é-lhe apresentada uma lista completa dos dispositivos Windows Autopilot e informações detalhadas sobre os mesmos.


Para ver alertas de dispositivos não atribuídos, no [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Descrição geral** > **Dispositivos não atribuídos**.  


## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Atribuir um utilizador a um dispositivo do Autopilot específico

Pode atribuir um utilizador a um dispositivo do Autopilot específico. Esta atribuição preenche previamente um utilizador do Azure Active Directory na página de início de sessão [empresarial](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) durante a configuração do Windows. Também permite definir um nome de saudação personalizado. Esta ação não preenche previamente nem modifica o início de sessão do Windows. Os utilizadores licenciados do Intune são os únicos que podem ser atribuídos desta forma.

Pré-requisitos: Portal do Azure da empresa do Active Directory foi configurado e o Windows 10, versão 1809 ou posterior.

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Dispositivos** > selecione o dispositivo > **Atribuir utilizador**.

    ![Captura de ecrã de Atribuir utilizador](media/enrollment-autopilot/assign-user.png)

2. Selecione um utilizador licenciado do Azure para utilizar o Intune e selecione **Selecionar**.

    ![Captura de ecrã da seleção do utilizador](media/enrollment-autopilot/select-user.png)

3. Na caixa **Nome amigável de utilizador**, escreva um nome amigável ou aceite simplesmente o nome predefinido. Esta cadeia é o nome amigável que é apresentado quando o utilizador inicia sessão durante a configuração do Windows.

    ![Captura de ecrã do nome amigável](media/enrollment-autopilot/friendly-name.png)

4. Selecione **OK**.


## <a name="delete-autopilot-devices"></a>Eliminar dispositivos Autopilot

Pode eliminar dispositivos do Windows Autopilot que não estejam inscritos.

1. Se os dispositivos estiverem inscritos no Intune, primeiro tem de [eliminá-los do portal do Azure Active Directory](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. No [Intune no portal do Azure](https://aka.ms/intuneportal), escolha **Inscrição de dispositivos** > **Inscrição do Windows** > **Dispositivos**.

3. Em **Dispositivos Windows Autopilot**, escolha os dispositivos que quer eliminar e, em seguida, **Eliminar**.

4. Confirme a eliminação ao escolher **Sim**. A eliminação pode demorar alguns minutos.

## <a name="using-autopilot-in-other-portals"></a>Utilizar o Autopilot noutros portais
Se não estiver interessado na gestão de dispositivos móveis, pode utilizar o Autopilot noutros portais. Embora a utilização de outros portais seja uma opção, recomendamos-lhe que apenas utilize o Intune para gerir as suas implementações do Autopilot. Se utilizar o Intune e outro portal, o Intune não será capaz de:  

- Apresentar alterações aos perfis criados no Intune que tenham sido editados noutro portal
- Sincronizar perfis criados noutro portal
- Apresentar alterações a atribuições de perfil efetuadas noutro portal
- Sincronizar atribuições de perfil efetuadas noutro portal
- Apresentar as alterações à lista de dispositivos que foram feitas noutro portal

## <a name="windows-autopilot-for-existing-devices"></a>Windows Autopilot para dispositivos existentes

Pode agrupar dispositivos Windows por um ID de correlacionador ao inscrevê-los com o [Autopilot para dispositivos existentes](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430), através do Configuration Manager. O ID de correlacionador é um parâmetro do ficheiro de configuração do Autopilot. O [atributo enrollmentProfileName de dispositivos do Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) é automaticamente definido para ser igual a "OfflineAutopilotprofile-\<correlator ID\>". Isto permite que sejam criados grupos dinâmicos do Azure AD arbitrários com base no ID de correlacionador ao utilizar o atributo enrollmentprofileName.

>[!WARNING] 
> Como o ID de correlacionador não está listado previamente no Intune, o dispositivo pode comunicar qualquer ID de correlacionador. Se o utilizador criar um ID de correlacionador que corresponda a um nome de perfil do Autopilot ou DEP da Apple, o dispositivo será adicionado a qualquer grupo de dispositivos dinâmico do Azure Active Directory com base no atributo enrollmentProfileName. Para impedir este conflito:
> - Crie sempre regras de grupos dinâmico que correspondam a *todo* o valor enrollmentProfileName
> - Nunca crie um nome para perfis de Autopilot ou DEP da Apple começado por "OfflineAutopilotprofile-".

## <a name="next-steps"></a>Passos Seguintes
Após ter configurado o Windows Autopilot para dispositivos Windows 10 registados, saiba como gerir esses dispositivos. Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](https://docs.microsoft.com/intune/device-management)
