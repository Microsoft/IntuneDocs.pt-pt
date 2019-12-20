---
title: Inscrever dispositivos através do Windows Autopilot
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos com o Windows 10 através do Windows Autopilot.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f15ddae79cdfec5635afff08abaee181e0517cc8
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207235"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Inscrever dispositivos Windows no Intune com o Windows Autopilot  
O Windows Autopilot simplifica a inscrição de dispositivos no Intune. A criação e manutenção de imagens personalizadas do sistema operativo são um processo moroso. Também poderá demorar a aplicar estas imagens personalizadas do sistema operativo a novos dispositivos para as preparar para utilização antes de as disponibilizar aos seus utilizadores finais. Com o Microsoft Intune e o Autopilot, pode fornecer novos dispositivos aos seus utilizadores finais sem ter de criar, manter e aplicar imagens de sistema operativo personalizadas aos dispositivos. Ao utilizar o Intune para gerir dispositivos do Autopilot, pode gerir políticas, perfis, aplicações, entre outros, após estes serem inscritos. Para uma descrição geral das vantagens, cenários e pré-requisitos, veja [Descrição geral do Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

Há quatro tipos de implantação do AutoPilot:
- [Modo de autoimplantação](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) para quiosques, pôsteres digitais ou um dispositivo compartilhado
- O [diferenciada branco](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) permite que os parceiros ou a equipe de ti pré-provisionar um PC com Windows 10 para que ele seja totalmente configurado e o[piloto automático pronto para os negócios para dispositivos existentes](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) permite que você implante facilmente a versão mais recente do Windows 10 em seus dispositivos existentes
- [Modo controlado pelo usuário](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) para usuários tradicionais. 


## <a name="prerequisites"></a>Pré-requisitos
- [Assinatura do Intune](../fundamentals/licenses.md)
- [A Inscrição automática no Windows tem de estar ativada](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Assinatura Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>Como obter o CSV para importação no Intune

Para obter mais informações, consulte o cmdlet Understanding PowerShell.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo)

## <a name="add-devices"></a>Adicionar dispositivos

Pode adicionar dispositivos Windows Autopilot ao importar um ficheiro CSV com as informações dos dispositivos.

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **windows** > **registro do Windows** > **dispositivos** (no programa de **implantação do Windows AutoPilot** > **importar**.

    ![Captura de ecrã dos dispositivos Windows Autopilot](./media/enrollment-autopilot/autopilot-import-device.png)

2. Em **Adicionar Dispositivos do Windows Autopilot**, procure um ficheiro CSV que liste os dispositivos que pretende adicionar. O arquivo CSV deve listar os números de série, as IDs de produto do Windows, os hashes de hardware, as marcas de grupo opcionais e o usuário atribuído opcional. Você pode ter até 500 linhas na lista. Use o cabeçalho e o formato de linha mostrados abaixo:

    `Device Serial Number,Windows Product ID,Hardware Hash,Group Tag,Assigned User`</br>
    `<serialNumber>,<ProductID>,<hardwareHash>,<optionalGroupTag>,<optionalAssignedUser>`

    ![Captura de ecrã de Adicionar dispositivos Windows Autopilot](./media/enrollment-autopilot/autopilot-import-device2.png)

    >[!IMPORTANT]
    > Ao usar o carregamento de CSV para atribuir um usuário, certifique-se de atribuir UPNs válidos. Se você atribuir um UPN inválido (nome de usuário incorreto), seu dispositivo poderá ficar inacessível até que você remova a atribuição inválida. Durante o CSV, carregue a única validação que executamos na coluna **usuário atribuído** é verificar se o nome de domínio é válido. Não podemos executar validação de UPN individual para garantir que você está atribuindo um usuário existente ou correto.

3. Escolha **Importar** para iniciar a importação das informações do dispositivo. A importação poderá demorar alguns minutos.

4. Após a conclusão da importação, escolha **dispositivos** > **Windows** > **registro do Windows** > **dispositivos** (no programa de **implantação do Windows AutoPilot** > **sincronizar**. Uma mensagem exibe que a sincronização está em andamento. O processo poderá demorar alguns minutos a concluir, consoante o número de dispositivos em sincronização.

5. Atualize a vista para ver os novos dispositivos.

## <a name="create-an-autopilot-device-group"></a>Criar um grupo de dispositivos do Autopilot

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **grupos** > **novo grupo**.
2. No painel **Grupo**:
    1. Para **Tipo de grupo**, selecione **Segurança**.
    2. Introduza um **Nome do grupo** e uma **Descrição do grupo**.
    3. Para **Tipo de associação**, selecione **Atribuído** ou **Dispositivo Dinâmico**.
3. Se optou por **Atribuído** para o **Tipo de associação** no passo anterior, no painel **Grupo**, selecione **Membros** e adicione dispositivos do Autopilot ao grupo.
    Os dispositivos Autopilot que ainda não estão inscritos são dispositivos em que o nome é igual ao número de série do dispositivo.
4. Se acima optou por **Dispositivo Dinâmico** para o **Tipo de associação**, no painel **Grupo**, selecione **Membros de dispositivo dinâmicos** e escreva o seguinte código na caixa **Regra avançada**. Somente os dispositivos AutoPilot são coletados por essas regras, pois eles direcionam atributos que são apenas possuía por dispositivos AutoPilot. A criação de um grupo com base em atributos não AutoPilot não garantirá que os dispositivos incluídos no grupo estejam realmente registrados no piloto automático.
    - Se você quiser criar um grupo que inclui todos os seus dispositivos do AutoPilot, digite: `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - O campo de marca de grupo do Intune é mapeado para o atributo OrderID em dispositivos do Azure AD. Se você quiser criar um grupo que inclua todos os seus dispositivos de piloto automático com uma marca de grupo específica (o dispositivo OrderID do Azure AD), você deve digitar: `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Se quiser criar um grupo que inclua todos os seus dispositivos do Autopilot com um ID de Nota de Encomenda específico, escreva `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Depois de adicionar o código da **Regra avançada**, selecione **Guardar**.
5. Selecione **Criar**.  

## <a name="create-an-autopilot-deployment-profile"></a>Criar um perfil de implementação do Autopilot
Os perfis de implementação do Autopilot são utilizados para configurar os dispositivos do Autopilot. Você pode criar até 350 perfis por locatário.
1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **windows** > **registro do Windows** > perfis de **implantação** > **Criar perfil**.
2. Na página **noções básicas** , digite um **nome** e uma **Descrição**opcional.

    ![Captura de tela da página básico](./media/enrollment-autopilot/create-profile-basics.png)

3. Se pretender que todos os dispositivos nos grupos atribuídos sejam convertidos automaticamente no Autopilot, defina **Converter todos os dispositivos visados para o Piloto Automático** para **Sim**. Todos os dispositivos de propriedade corporativa, não autopiloto em grupos atribuídos serão registrados com o serviço de implantação do AutoPilot. Dispositivos de propriedade pessoal não serão convertidos para o piloto automático. O processo de registo demora até 48 horas, pelo que deverá aguardar. Quando a inscrição do dispositivo for anulada e o dispositivo for reposto, o Autopilot irá inscrevê-lo. Após registar um dispositivo desta forma, desativar esta opção ou remover a atribuição de perfil não irá remover o dispositivo do serviço de implementação do Autopilot. Em alternativa, tem de [remover o dispositivo diretamente](enrollment-autopilot.md#delete-autopilot-devices).
4. Selecione **Seguinte**.
5. Na página **OOBE (instalação inicial do uso)** , para o modo de **implantação**, escolha uma destas duas opções:
    - **Orientado pelo utilizador**: os dispositivos com este perfil são associados ao utilizador que inscreve o dispositivo. Precisa de credenciais de utilizador para inscrever o dispositivo.
    - **Autoimplantação (visualização)**: os dispositivos do Windows 10, versão 1809 ou posteriores com esse perfil não estão associados ao usuário que está registrando o dispositivo. Não são necessárias credenciais de utilizador para inscrever o dispositivo. Quando um dispositivo não tem nenhum usuário associado a ele, as políticas de conformidade baseadas no usuário não se aplicam a ele. Ao usar o modo de implantação automática, somente as políticas de conformidade direcionadas ao dispositivo serão aplicadas.

    ![Captura de tela da página OOBE](./media/enrollment-autopilot/create-profile-outofbox.png)

6. Na caixa **Aderir ao Azure AD como**, selecione **Associado ao Azure AD**.
7. Configure as seguintes opções:
    - **Contrato de licença do utilizador final (EULA)**: (Versão 1709 ou posterior do Windows 10) selecione se pretende ou não apresentar o EULA aos utilizadores.
    - **Definições de privacidade**: selecione se pretende apresentar definições de privacidade aos utilizadores.
    >[!IMPORTANT]
    >O valor padrão para a configuração de dados de diagnóstico varia entre as versões do Windows. Para dispositivos que executam o Windows 10, versão 1903, o valor padrão é definido como completo durante a experiência inicial do uso. Para obter mais informações, consulte [dados de diagnóstico do Windows](https://docs.microsoft.com/windows/privacy/windows-diagnostic-data) <br>
    
    - **Ocultar opções de conta de alteração (requer o Windows 10, versão 1809 ou posterior)**: escolha **ocultar** para impedir que as opções alterar conta sejam exibidas nas páginas entrada da empresa e erro de domínio. Esta opção requer a [configuração da imagem corporativa da empresa no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Tipo de conta de utilizador**: selecione o tipo de conta de utilizador (**Administrador** ou utilizador **Padrão**). Permitimos que o usuário que está ingressando o dispositivo seja um administrador local adicionando-o ao grupo de Administradores local. Não habilitamos o usuário como o administrador padrão no dispositivo.
    - **Allow White diferenciada OOBE** (requer o Windows 10, versão 1903 ou posterior; [requisitos físicos adicionais](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove#prerequisites)): escolha **Sim** para permitir o suporte a diferenciada branco.
    - **Aplicar modelo de nome de dispositivo** (requer o Windows 10, versão 1809 ou posterior e tipo de junção do Azure AD): escolha **Sim** para criar um modelo a ser usado ao nomear um dispositivo durante o registro. Os nomes têm de ter 15 carateres ou menos e podem conter letras, números e hífenes. Não podem conter apenas números. Utilize a [macro %SERIAL%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) para adicionar um número de série específico de hardware. Em alternativa, utilize a [macro %RAND:x%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) para adicionar uma cadeia de números aleatória na qual x corresponde ao número de dígitos a adicionar. Você só pode fornecer uma correção prévia para dispositivos híbridos em um [perfil de ingresso no domínio](windows-autopilot-hybrid.md#create-and-assign-a-domain-join-profile). 
    - **Idioma (Região)**\*: selecione o idioma a utilizar para o dispositivo. Esta opção só está disponível se tiver optado pela **Implementação personalizada** no **Modo de implementação**.
    - **Configurar automaticamente o teclado**\*: se um **idioma (região)** está selecionado, escolha **Sim** para ignorar a página de seleção do teclado. Esta opção só está disponível se tiver optado pela **Implementação personalizada** no **Modo de implementação**.
8. Selecione **Seguinte**.
9. Na página **marcas de escopo** , adicione opcionalmente as marcas de escopo que você deseja aplicar a esse perfil. Para obter mais informações sobre marcas de escopo, consulte [usar o controle de acesso baseado em função e marcas de escopo para distribuí-lo](../fundamentals/scope-tags.md).
10. Selecione **Seguinte**.
11. Na página **atribuições** , escolha **grupos selecionados** para **atribuir a**.

    ![Captura de tela da página atribuições](./media/enrollment-autopilot/create-profile-assignments.png)

12. Escolha **Selecionar grupos para incluir**e escolha os grupos que você deseja incluir neste perfil.
13. Se você quiser excluir todos os grupos, escolha **Selecionar grupos a serem excluídos**e escolha os grupos que deseja excluir.
14. Selecione **Seguinte**.
15. Na página **revisar + criar** , escolha **criar** para criar o perfil.

    ![Captura de tela da página de revisão](./media/enrollment-autopilot/create-profile-review.png)

> [!NOTE]
> O Intune verificará periodicamente se há novos dispositivos nos grupos atribuídos e, em seguida, iniciará o processo de atribuição de perfis a esses dispositivos. Esse processo pode levar vários minutos para ser concluído. Antes de implantar um dispositivo, verifique se esse processo foi concluído.  Você pode verificar em **dispositivos** > **Windows** > **registro do Windows** > **dispositivos** (no programa de implantação do Windows **AutoPilot** , em que você deve ver o status do perfil alterado de "não atribuído" para "atribuindo" e, por fim, a "atribuído".

## <a name="edit-an-autopilot-deployment-profile"></a>Editar um perfil de implementação do Autopilot
Após ter criado um perfil de implementação do Autopilot, poderá editar determinadas partes do perfil de implementação.   

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **windows** > **registro do Windows** > perfis de **implantação**.
2. Selecione o perfil que pretende editar.
3. Selecione **Propriedades** à esquerda para alterar o nome ou a descrição do perfil de implantação. Após ter efetuado as alterações, clique em **Guardar**.
5. Clique em **Definições** para efetuar alterações às definições da OOBE. Após ter efetuado as alterações, clique em **Guardar**.

> [!NOTE]
> As alterações ao perfil são aplicadas aos dispositivos atribuídos a esse perfil. No entanto, o perfil atualizado não será aplicado a um dispositivo já inscrito no Intune até que o dispositivo tenha sido reposto e reinscrito.

## <a name="edit-autopilot-device-attributes"></a>Editar atributos de dispositivo de piloto automático
Depois de carregar um dispositivo de piloto automático, você poderá editar determinados atributos do dispositivo.

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), selecione **dispositivos** > **windows** > **registro do Windows** > **dispositivos** (no programa de **implantação do Windows AutoPilot**.
2. Selecione o dispositivo que você deseja editar.
3. No painel à direita da tela, você pode editar o nome do dispositivo, a marca do grupo ou o nome amigável do usuário (se você tiver atribuído um usuário).
4. Selecione **Guardar**.

> [!NOTE]
> Os nomes de dispositivo podem ser configurados para todos os dispositivos, mas são ignorados em implantações Unidas do Azure AD híbridos. O nome do dispositivo ainda vem do perfil de ingresso no domínio para dispositivos híbridos do Azure AD.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Alertas para dispositivos Windows AutoPilot não atribuídos  <!-- 163236 -->  

Os alertas irão indicar quantos dispositivos do programa Autopilot não têm perfis de implementação do Autopilot. Utilize as informações no alerta para criar perfis e atribui-los aos dispositivos não atribuídos. Quando clica no alerta, é-lhe apresentada uma lista completa dos dispositivos Windows Autopilot e informações detalhadas sobre os mesmos.

Para ver alertas para dispositivos não atribuídos, no [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **visão geral** > **alertas de registro** > **dispositivos não atribuídos**.  

## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Atribuir um utilizador a um dispositivo do Autopilot específico

Pode atribuir um utilizador a um dispositivo do Autopilot específico. Esta atribuição preenche previamente um utilizador do Azure Active Directory na página de início de sessão [empresarial](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) durante a configuração do Windows. Também permite definir um nome de saudação personalizado. Esta ação não preenche previamente nem modifica o início de sessão do Windows. Os utilizadores licenciados do Intune são os únicos que podem ser atribuídos desta forma.

Pré-requisitos: Azure Active Directory Portal da Empresa foi configurado e Windows 10, versão 1809 ou posterior.

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **windows** > **registro do Windows** > **dispositivos** (em programa de **implantação do Windows AutoPilot** > escolha o dispositivo > **atribuir usuário**.

    ![Captura de ecrã de Atribuir utilizador](./media/enrollment-autopilot/assign-user.png)

2. Selecione um utilizador licenciado do Azure para utilizar o Intune e selecione **Selecionar**.

    ![Captura de ecrã da seleção do utilizador](./media/enrollment-autopilot/select-user.png)

3. Na caixa **Nome amigável de utilizador**, escreva um nome amigável ou aceite simplesmente o nome predefinido. Esta cadeia é o nome amigável que é apresentado quando o utilizador inicia sessão durante a configuração do Windows.

    ![Captura de ecrã do nome amigável](./media/enrollment-autopilot/friendly-name.png)

4. Selecione **OK**.

## <a name="autopilot-deployments-report"></a>Relatório de implantações do AutoPilot
Você pode ver detalhes em cada dispositivo implantado por meio do piloto automático do Windows.
Para ver o relatório, vá para o [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **monitorar** > **implantações do AutoPilot**.
Os dados ficam disponíveis por 30 dias após a implantação.


## <a name="delete-autopilot-devices"></a>Eliminar dispositivos Autopilot

Você pode excluir dispositivos do Windows AutoPilot que não são registrados no Intune:

- Exclua os dispositivos do Windows AutoPilot em **dispositivos** > **Windows** > **registro do Windows** > **dispositivos** (no programa de implantação do Windows **AutoPilot**. Escolha os dispositivos que você deseja excluir e, em seguida, escolha **excluir**. A exclusão do dispositivo do Windows AutoPilot pode levar alguns minutos para ser concluída.

A remoção completa de um dispositivo do seu locatário exige que você exclua o dispositivo do Intune, o dispositivo Azure Active Directory e os registros do dispositivo do Windows AutoPilot. Isso pode ser feito no Intune:

1. Se os dispositivos estiverem registrados no Intune, você deverá primeiro [excluí-los da folha todos os dispositivos do Intune](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Exclua os dispositivos **em dispositivos Azure Active Directory em dispositivos > ** **dispositivos do Azure ad**.

3. Exclua os dispositivos do Windows AutoPilot em **dispositivos** > **Windows** > **registro do Windows** > **dispositivos** (sob o programa de **implantação do Windows AutoPilot** >. Escolha os dispositivos que você deseja excluir e, em seguida, escolha **excluir**. A exclusão do dispositivo do Windows AutoPilot pode levar alguns minutos para ser concluída.

## <a name="using-autopilot-in-other-portals"></a>Utilizar o Autopilot noutros portais
Se não estiver interessado na gestão de dispositivos móveis, pode utilizar o Autopilot noutros portais. Embora a utilização de outros portais seja uma opção, recomendamos-lhe que apenas utilize o Intune para gerir as suas implementações do Autopilot. Se utilizar o Intune e outro portal, o Intune não será capaz de:  

- Apresentar alterações aos perfis criados no Intune que tenham sido editados noutro portal
- Sincronizar perfis criados noutro portal
- Apresentar alterações a atribuições de perfil efetuadas noutro portal
- Sincronizar atribuições de perfil efetuadas noutro portal
- Apresentar as alterações à lista de dispositivos que foram feitas noutro portal

## <a name="windows-autopilot-for-existing-devices"></a>Windows Autopilot para dispositivos existentes

Pode agrupar dispositivos Windows por um ID de correlacionador ao inscrevê-los com o [Autopilot para dispositivos existentes](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430), através do Configuration Manager. O ID de correlacionador é um parâmetro do ficheiro de configuração do Autopilot. O [atributo enrollmentProfileName de dispositivos do Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) é automaticamente definido para ser igual a "OfflineAutopilotprofile-\<correlator ID\>". Isto permite que sejam criados grupos dinâmicos do Azure AD arbitrários com base no ID de correlacionador ao utilizar o atributo enrollmentprofileName.

>[!WARNING] 
> Como o ID de correlacionador não está listado previamente no Intune, o dispositivo pode comunicar qualquer ID de correlacionador. Se o utilizador criar um ID de correlacionador que corresponda a um nome de perfil do Autopilot ou DEP da Apple, o dispositivo será adicionado a qualquer grupo de dispositivos dinâmico do Azure Active Directory com base no atributo enrollmentProfileName. Para impedir este conflito:
> - Crie sempre regras de grupos dinâmico que correspondam a *todo* o valor enrollmentProfileName
> - Nunca crie um nome para perfis de Autopilot ou DEP da Apple começado por "OfflineAutopilotprofile-".

## <a name="next-steps"></a>Próximos passos
Após ter configurado o Windows Autopilot para dispositivos Windows 10 registados, saiba como gerir esses dispositivos. Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](../remote-actions/device-management.md)
