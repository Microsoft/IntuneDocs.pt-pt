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
ms.openlocfilehash: 4f97c4c56073044e79b5251dc83c54decb5c9c55
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124848"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Inscrever dispositivos Windows no Intune com o Windows Autopilot  
O Windows Autopilot simplifica a inscrição de dispositivos no Intune. A criação e manutenção de imagens personalizadas do sistema operativo são um processo moroso. Também poderá demorar a aplicar estas imagens personalizadas do sistema operativo a novos dispositivos para as preparar para utilização antes de as disponibilizar aos seus utilizadores finais. Com o Microsoft Intune e o Autopilot, pode fornecer novos dispositivos aos seus utilizadores finais sem ter de criar, manter e aplicar imagens de sistema operativo personalizadas aos dispositivos. Ao utilizar o Intune para gerir dispositivos do Autopilot, pode gerir políticas, perfis, aplicações, entre outros, após estes serem inscritos. Para uma descrição geral das vantagens, cenários e pré-requisitos, veja [Descrição geral do Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

Existem quatro tipos de implantação do Piloto Automático:
- [Modo de Implantação Autónoma](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) para quiosques, sinalização digital ou um dispositivo partilhado
- [A White Glove](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) permite aos parceiros ou funcionários de TI pré-fornecer um PC Windows 10 para que esteja totalmente configurado e pronto para o negócio -[O Autopilot para dispositivos existentes](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) permite-lhe implementar facilmente a versão mais recente do Windows 10 para os seus dispositivos existentes
- [Modo acionado pelo utilizador](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) para utilizadores tradicionais. 


## <a name="prerequisites"></a>Pré-requisitos
- [Subscrição intonizada](../fundamentals/licenses.md)
- [A Inscrição automática no Windows tem de estar ativada](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Assinatura Azure Ative Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](https://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>Como obter o CSV para importação em Intune

Para mais informações, consulte a compreensão da powershell cmdlet.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo)

## <a name="add-devices"></a>Adicionar dispositivos

Pode adicionar dispositivos Windows Autopilot ao importar um ficheiro CSV com as informações dos dispositivos.

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **dispositivos** > Windows > **dispositivos** de ** > de inscrição do** **Windows** (no âmbito do Programa de **Implementação do Piloto Automático do Windows** > **Import**.

    ![Captura de ecrã dos dispositivos Windows Autopilot](./media/enrollment-autopilot/autopilot-import-device.png)

2. Em **Adicionar Dispositivos do Windows Autopilot**, procure um ficheiro CSV que liste os dispositivos que pretende adicionar. O ficheiro CSV deve listar os números de série, iDs do produto Windows, hashes de hardware, etiquetas de grupo opcionais e utilizador opcional atribuído. Pode ter até 500 filas na lista. Para obter informações sobre como obter informações sobre o dispositivo, consulte [adicionar dispositivos ao Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/add-devices#device-identification). Utilize o formato cabeçalho e de linha abaixo indicado:

    `Device Serial Number,Windows Product ID,Hardware Hash,Group Tag,Assigned User`</br>
    `<serialNumber>,<ProductID>,<hardwareHash>,<optionalGroupTag>,<optionalAssignedUser>`

    ![Captura de ecrã de Adicionar dispositivos Windows Autopilot](./media/enrollment-autopilot/autopilot-import-device2.png)

    >[!IMPORTANT]
    > Quando utilizar o upload do CSV para atribuir um utilizador, certifique-se de que atribui NS UPNs válidos. Se atribuir uma UPN inválida (nome de utilizador incorreto), o seu dispositivo pode ficar inacessível até remover a atribuição inválida. Durante o upload do CSV, a única validação que executamos na coluna **utilizador atítulo** é verificar se o nome de domínio é válido. Não conseguimos realizar validação individual da UPN para garantir que está a atribuir um utilizador existente ou correto.

3. Escolha **Importar** para iniciar a importação das informações do dispositivo. A importação poderá demorar alguns minutos.

4. Depois de concluída a importação, escolha **dispositivos** > Windows > **Dispositivos** de > **de inscrição do Windows** (no âmbito do Programa de **Implementação do Piloto Automático do Windows** > **Sync**. Uma mensagem mostra que a sincronização está em andamento. O processo poderá demorar alguns minutos a concluir, consoante o número de dispositivos em sincronização.

5. Atualize a vista para ver os novos dispositivos.

## <a name="create-an-autopilot-device-group"></a>Criar um grupo de dispositivos do Autopilot

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **Grupos** > **Novo grupo**.
2. No painel **Grupo**:
    1. Para **Tipo de grupo**, selecione **Segurança**.
    2. Introduza um **Nome do grupo** e uma **Descrição do grupo**.
    3. Para **Tipo de associação**, selecione **Atribuído** ou **Dispositivo Dinâmico**.
3. Se optou por **Atribuído** para o **Tipo de associação** no passo anterior, no painel **Grupo**, selecione **Membros** e adicione dispositivos do Autopilot ao grupo.
    Os dispositivos Autopilot que ainda não estão inscritos são dispositivos em que o nome é igual ao número de série do dispositivo.
4. Se acima optou por **Dispositivo Dinâmico** para o **Tipo de associação**, no painel **Grupo**, selecione **Membros de dispositivo dinâmicos** e escreva o seguinte código na caixa **Regra avançada**. Apenas os dispositivos Autopilot são recolhidos por estas regras, porque visam atributos que só são possuídos por dispositivos Autopilot. A criação de um grupo baseado em atributos não piloto automático não garante que os dispositivos incluídos no grupo estejam registados no Autopilot.
    - Se quiser criar um grupo que inclua todos os seus dispositivos Autopilot, escreva: `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Os mapas de campo de etiquetas de grupo intune para o atributo OrderID em dispositivos AD Azure. Se pretender criar um grupo que inclua todos os seus dispositivos Autopilot com uma etiqueta de grupo específica (o dispositivo AD Azure OrderID), deve escrever: `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Se quiser criar um grupo que inclua todos os seus dispositivos do Autopilot com um ID de Nota de Encomenda específico, escreva `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Depois de adicionar o código da **Regra avançada**, selecione **Guardar**.
5. Selecione **Criar**.  

## <a name="create-an-autopilot-deployment-profile"></a>Criar um perfil de implementação do Autopilot
Os perfis de implementação do Autopilot são utilizados para configurar os dispositivos do Autopilot. Você pode criar até 350 perfis por locatário.
1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **dispositivos** > **Windows** > **windows > ** perfis de **implementação** > **Criar perfil**.
2. Na página **Basics,** digite um **nome** e **descrição**opcional.

    ![Screenshot da página Basics](./media/enrollment-autopilot/create-profile-basics.png)

3. Se pretender que todos os dispositivos nos grupos atribuídos sejam convertidos automaticamente no Autopilot, defina **Converter todos os dispositivos visados para o Piloto Automático** para **Sim**. Todos os dispositivos corporativos e não autopilotos em grupos designados registar-se-ão no serviço de implementação do Autopilot. Os dispositivos pessoais não serão convertidos para Piloto Automático. O processo de registo demora até 48 horas, pelo que deverá aguardar. Quando a inscrição do dispositivo for anulada e o dispositivo for reposto, o Autopilot irá inscrevê-lo. Após registar um dispositivo desta forma, desativar esta opção ou remover a atribuição de perfil não irá remover o dispositivo do serviço de implementação do Autopilot. Em alternativa, tem de [remover o dispositivo diretamente](enrollment-autopilot.md#delete-autopilot-devices).
4. Selecione **Seguinte**.
5. Na página **Out-of-box (OOBE),** para modo de **implantação,** escolha uma destas duas opções:
    - **Orientado pelo utilizador**: os dispositivos com este perfil são associados ao utilizador que inscreve o dispositivo. Precisa de credenciais de utilizador para inscrever o dispositivo.
    - **Auto-implantação (pré-visualização)** : (requer o Windows 10, versão 1809 ou mais tarde) Os dispositivos com este perfil não estão associados ao utilizador que está a inscrever o dispositivo. Não são necessárias credenciais de utilizador para inscrever o dispositivo. Quando um dispositivo não tem utilizador associado a ele, as políticas de conformidade baseadas no utilizador não se aplicam ao mesmo. Ao utilizar o modo de auto-implantação, apenas serão aplicadas as políticas de conformidade direcionadas para o dispositivo.

    ![Screenshot da página OOBE](./media/enrollment-autopilot/create-profile-outofbox.png)

   > [!NOTE]
   > As opções que parecem escurecidas ou sombreadas não são atualmente suportadas pelo modo de implementação selecionado.

6. Na caixa **Aderir ao Azure AD como**, selecione **Associado ao Azure AD**.
7. Configure as seguintes opções:
    - **Contrato de licença do utilizador final (EULA)** : (Versão 1709 ou posterior do Windows 10) selecione se pretende ou não apresentar o EULA aos utilizadores.
    - **Definições de privacidade**: selecione se pretende apresentar definições de privacidade aos utilizadores.
    >[!IMPORTANT]
    >O valor predefinido para a definição de Dados de Diagnóstico varia entre as versões do Windows. Para dispositivos que executam o Windows 10, versão 1903, o valor predefinido é definido para Full durante a experiência fora da caixa. Para mais informações, consulte dados [de diagnóstico do Windows](https://docs.microsoft.com/windows/privacy/windows-diagnostic-data) <br>
    
    - **Ocultar opções de conta de alteração (requer o Windows 10, versão 1809 ou mais tarde)** : Escolha **ocultar** para evitar que as opções de conta de alteração sejam exibidas nas páginas de erro de sessão e erro de domínio da empresa. Esta opção requer a [configuração da imagem corporativa da empresa no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Tipo de conta de utilizador**: selecione o tipo de conta de utilizador (**Administrador** ou utilizador **Padrão**). Permitimos que o utilizador que se junte ao dispositivo seja um Administrador local, adicionando-o ao grupo de administração local. Não ativamos o utilizador como administrador predefinido no dispositivo.
    - **Permitir luva branca OOBE** (requer o Windows 10, versão 1903 ou mais tarde; [requisitos físicos adicionais):](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove#prerequisites)Escolha **Sim** para permitir suporte à luva branca.
    - **Aplicar o modelo** de nome do dispositivo (requer o Windows 10, a versão 1809 ou mais tarde, e o tipo de adesão do Azure AD): Escolha **Sim** para criar um modelo para usar ao nomear um dispositivo durante a inscrição. Os nomes têm de ter 15 carateres ou menos e podem conter letras, números e hífenes. Não podem conter apenas números. Utilize a [macro %SERIAL%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) para adicionar um número de série específico de hardware. Em alternativa, utilize a [macro %RAND:x%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) para adicionar uma cadeia de números aleatória na qual x corresponde ao número de dígitos a adicionar. Só é possível fornecer uma pré-correcção para dispositivos híbridos num perfil de [adesão](windows-autopilot-hybrid.md#create-and-assign-a-domain-join-profile)de domínio . 
    - **Idioma (Região)** \*: selecione o idioma a utilizar para o dispositivo. Esta opção só está disponível se tiver optado pela **Implementação personalizada** no **Modo de implementação**.
    - **Configure automaticamente o teclado**\*: Se for selecionada uma **Língua (Região),** escolha **Sim** para saltar a página de seleção do teclado. Esta opção só está disponível se tiver optado pela **Implementação personalizada** no **Modo de implementação**.
8. Selecione **Seguinte**.
9. Na página scope **tags,** adicione opcionalmente as etiquetas de âmbito que pretende aplicar a este perfil. Para obter mais informações sobre etiquetas de âmbito, consulte [Utilize o controlo de acesso baseado em papéis e as etiquetas](../fundamentals/scope-tags.md)de âmbito para TI distribuídos .
10. Selecione **Seguinte**.
11. Na página **de Atribuição,** escolha **grupos Selecionados** para **Atribuir a**.

    ![Screenshot da página de Atribuições](./media/enrollment-autopilot/create-profile-assignments.png)

12. Escolha **selecione grupos para incluir**, e escolha os grupos que pretende incluir neste perfil.
13. Se quiser excluir quaisquer grupos, escolha **Grupos Select para excluir**e escolha os grupos que pretende excluir.
14. Selecione **Seguinte**.
15. Na página **Review + Criar,** escolha **Criar** para criar o perfil.

    ![Screenshot da página de revisão](./media/enrollment-autopilot/create-profile-review.png)

> [!NOTE]
> Intune verificará periodicamente se há novos dispositivos nos grupos designados e, em seguida, iniciará o processo de atribuição de perfis a esses dispositivos. Este processo pode levar vários minutos para ser concluído. Antes de implementar um dispositivo, certifique-se de que este processo está concluído.  Pode verificar em **dispositivos** > **Windows** > **dispositivos** de > de **inscrição do Windows** (no âmbito do Programa de Implementação do **Piloto Automático windows,** onde deverá ver a mudança de estado do perfil de "Não atribuído" para "Atribuição" e, finalmente, para "Designado".

## <a name="edit-an-autopilot-deployment-profile"></a>Editar um perfil de implementação do Autopilot
Após ter criado um perfil de implementação do Autopilot, poderá editar determinadas partes do perfil de implementação.   

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **dispositivos** > **Windows** > **windows > ** perfis de **implementação**.
2. Selecione o perfil que pretende editar.
3. Selecione **Propriedades** à esquerda para alterar o nome ou descrição do perfil de implementação. Após ter efetuado as alterações, clique em **Guardar**.
5. Clique em **Definições** para efetuar alterações às definições da OOBE. Após ter efetuado as alterações, clique em **Guardar**.

> [!NOTE]
> As alterações ao perfil são aplicadas aos dispositivos atribuídos a esse perfil. No entanto, o perfil atualizado não será aplicado a um dispositivo já inscrito no Intune até que o dispositivo tenha sido reposto e reinscrito.

## <a name="edit-autopilot-device-attributes"></a>Editar atributos do dispositivo Autopilot
Depois de ter carregado um dispositivo Autopilot, pode editar certos atributos do dispositivo.

1. No [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431),selecione **Dispositivos** > Windows > **Dispositivos** de ** > de inscrição do** **Windows** (no âmbito do Programa de **Implementação do Piloto Automático windows**.
2. Selecione o dispositivo que pretende editar.
3. No painel à direita do ecrã, pode editar o nome do dispositivo, etiqueta de grupo ou Nome Amigável do Utilizador (se tiver atribuído um utilizador).
4. Selecione **Guardar**.

> [!NOTE]
> Os nomes do dispositivo podem ser configurados para todos os dispositivos, mas são ignorados em implementações adessimas a Hybrid Azure AD. O nome do dispositivo ainda vem do perfil de adesão do domínio para dispositivos AD Hybrid Azure.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Alertas para dispositivos não atribuídos do Windows Autopilot  <!-- 163236 -->  

Os alertas irão indicar quantos dispositivos do programa Autopilot não têm perfis de implementação do Autopilot. Utilize as informações no alerta para criar perfis e atribui-los aos dispositivos não atribuídos. Quando clica no alerta, é-lhe apresentada uma lista completa dos dispositivos Windows Autopilot e informações detalhadas sobre os mesmos.

Para ver alertas para dispositivos não atribuídos, no [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **dispositivos** > **visão geral** > Alertas de **inscrição** > **dispositivos não atribuídos**.  

## <a name="autopilot-deployments-report"></a>Relatório de implementações de piloto automático
Pode ver detalhes em cada dispositivo implementado através do Windows Autopilot.
Para ver o relatório, vá ao [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **Monitor** > **implementações do Autopilot**.
Os dados estão disponíveis durante 30 dias após a implantação.

Este relatório está em pré-visualização. Os registos de implantação do dispositivo são atualmente apenas desencadeados por novos eventos de inscrição intune. Isto significa que qualquer implantação que não desencadeie uma nova inscrição intune não será captada por este relatório. Isto inclui qualquer tipo de reset que mantenha a inscrição e a parte do utilizador da luva Branca Autopilot.

## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Atribuir um utilizador a um dispositivo do Autopilot específico

Pode atribuir um utilizador a um dispositivo do Autopilot específico. Esta atribuição preenche previamente um utilizador do Azure Active Directory na página de início de sessão [empresarial](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) durante a configuração do Windows. Também permite definir um nome de saudação personalizado. Esta ação não preenche previamente nem modifica o início de sessão do Windows. Os utilizadores licenciados do Intune são os únicos que podem ser atribuídos desta forma.

Pré-requisitos: O Portal da Empresa de DirectórioActivo Azure foi configurado e o Windows 10, versão 1809 ou posterior.

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **dispositivos** > **Windows** > **Windows de inscrição** > **Dispositivos** (no âmbito do Programa de **Implementação** do Piloto Automático do Windows > escolha o utilizador do dispositivo > **Atribuir**.

    ![Captura de ecrã de Atribuir utilizador](./media/enrollment-autopilot/assign-user.png)

2. Selecione um utilizador licenciado do Azure para utilizar o Intune e selecione **Selecionar**.

    ![Captura de ecrã da seleção do utilizador](./media/enrollment-autopilot/select-user.png)

3. Na caixa **Nome amigável de utilizador**, escreva um nome amigável ou aceite simplesmente o nome predefinido. Esta cadeia é o nome amigável que é apresentado quando o utilizador inicia sessão durante a configuração do Windows.

    ![Captura de ecrã do nome amigável](./media/enrollment-autopilot/friendly-name.png)

4. Selecione **OK**.


## <a name="delete-autopilot-devices"></a>Eliminar dispositivos Autopilot

Pode eliminar dispositivos do Windows Autopilot que não estão inscritos no Intune:

- Elimine os dispositivos do Windows Autopilot em **Dispositivos** > Windows > **Dispositivos** de > **de matrícula do Windows** (no âmbito do Programa de **Implementação do Piloto Automático do Windows**. Escolha os dispositivos que pretende eliminar e, em seguida, escolha **Apagar**. A eliminação do dispositivo Do Piloto Automático do Windows pode demorar alguns minutos a ser concluída.

A remoção completa de um dispositivo do seu inquilino requer que você elimine o dispositivo Intune, o dispositivo De Diretório Ativo Azure e os registos do dispositivo Do Maautopilot do Windows. Tudo isto pode ser feito a partir de Intune:

1. Se os dispositivos estiverem matriculados no Intune, tem primeiro de [os eliminar da lâmina Intune All.](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)

2. Elimine os dispositivos em dispositivos de Diretório Ativo Azure em **Dispositivos** > **dispositivos AD Azure**.

3. Elimine os dispositivos do Windows Autopilot em **Dispositivos** > Windows > **Dispositivos** de ** > de inscrição do Windows** (no âmbito do Programa de **Implementação** do Piloto Automático do Windows >. Escolha os dispositivos que pretende eliminar e, em seguida, escolha **Apagar**. A eliminação do dispositivo Do Piloto Automático do Windows pode demorar alguns minutos a ser concluída.

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

## <a name="next-steps"></a>Passos Seguintes
Após ter configurado o Windows Autopilot para dispositivos Windows 10 registados, saiba como gerir esses dispositivos. Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](../remote-actions/device-management.md)
