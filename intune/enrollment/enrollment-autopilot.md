---
title: Registrar dispositivos usando o piloto automático do Windows
titleSuffix: Microsoft Intune
description: Saiba como registrar dispositivos Windows 10 usando o piloto automático do Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2ebca165c067afbc3d830e5f75ac9f8e29effb2
ms.sourcegitcommit: a50a1ca123ecc2c5ac129f112f73838748f56476
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2019
ms.locfileid: "72237221"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Registrar dispositivos Windows no Intune usando o piloto automático do Windows  
O Windows AutoPilot simplifica o registro de dispositivos no Intune. Criar e manter imagens personalizadas do sistema operacional é um processo demorado. Você também pode gastar tempo aplicando essas imagens personalizadas do sistema operacional a novos dispositivos para prepará-las para uso antes de fornecê-las aos usuários finais. Com o Microsoft Intune e o AutoPilot, você pode fornecer novos dispositivos aos seus usuários finais sem a necessidade de criar, manter e aplicar imagens personalizadas do sistema operacional aos dispositivos. Ao usar o Intune para gerenciar dispositivos do AutoPilot, você pode gerenciar políticas, perfis, aplicativos e muito mais depois que eles são registrados. Para obter uma visão geral dos benefícios, cenários e pré-requisitos, consulte [visão geral do Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

Há quatro tipos de implantação do AutoPilot:
- [Modo de autoimplantação](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) para quiosques, pôsteres digitais ou um dispositivo compartilhado
- O [diferenciada branco](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) permite que os parceiros ou a equipe de ti pré-provisionar um PC com Windows 10 para que ele seja totalmente configurado e o[piloto automático pronto para os negócios para dispositivos existentes](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) permite que você implante facilmente a versão mais recente do Windows 10 em seus dispositivos existentes
- [Modo controlado pelo usuário](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) para usuários tradicionais. 


## <a name="prerequisites"></a>Pré-requisitos
- [Assinatura do Intune](../fundamentals/licenses.md)
- [Registro automático do Windows habilitado](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Assinatura Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>Como obter o CSV para importação no Intune

Para obter mais informações, consulte o cmdlet Understanding PowerShell.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo)

## <a name="add-devices"></a>Adicionar dispositivos

Você pode adicionar dispositivos do Windows AutoPilot importando um arquivo CSV com suas informações.

1. No [Intune na portal do Azure](https://aka.ms/intuneportal), escolha **registro de dispositivo** > **registro do Windows** > **dispositivos** > **importação**.

    ![Captura de tela de dispositivos do Windows AutoPilot](./media/enrollment-autopilot/autopilot-import-device.png)

2. Em **Adicionar dispositivos do Windows AutoPilot**, navegue até um arquivo CSV listando os dispositivos que você deseja adicionar. O arquivo CSV deve listar os números de série, as IDs de produto do Windows, os hashes de hardware, as marcas de grupo opcionais e o usuário atribuído opcional. Você pode ter até 500 linhas na lista. Use o cabeçalho e o formato de linha mostrados abaixo:

    `Device Serial Number,Windows Product ID,Hardware Hash,Group Tag,Assigned User`</br>
    `<serialNumber>,<ProductID>,<hardwareHash>,<optionalGroupTag>,<optionalAssignedUser>`

    ![Captura de tela da adição de dispositivos do Windows AutoPilot](./media/enrollment-autopilot/autopilot-import-device2.png)

    >[!IMPORTANT]
    > Ao usar o carregamento de CSV para atribuir um usuário, certifique-se de atribuir UPNs válidos. Se você atribuir um UPN inválido (nome de usuário incorreto), seu dispositivo poderá ficar inacessível até que você remova a atribuição inválida. Durante o CSV, carregue a única validação que executamos na coluna **usuário atribuído** é verificar se o nome de domínio é válido. Não podemos executar validação de UPN individual para garantir que você está atribuindo um usuário existente ou correto.

3. Escolha **importar** para começar a importar as informações do dispositivo. A importação pode levar vários minutos.

4. Após a conclusão da importação, **escolha registro de dispositivo** >  registro do**Windows** > **Windows AutoPilot** > **dispositivos** > **sincronização**. Uma mensagem exibe que a sincronização está em andamento. O processo pode levar alguns minutos para ser concluído, dependendo de quantos dispositivos estão sendo sincronizados.

5. Atualize a exibição para ver os novos dispositivos.

## <a name="create-an-autopilot-device-group"></a>Criar um grupo de dispositivos de piloto automático

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), escolha **grupos** > **novo grupo**.
2. Na folha do **grupo** :
    1. Para **tipo de grupo**, escolha **segurança**.
    2. Digite um **nome de grupo** e uma **Descrição de grupo**.
    3. Para **tipo de associação**, escolha dispositivo **atribuído** ou **dinâmico**.
3. Se você escolheu **atribuído** para o **tipo de associação** na etapa anterior, na folha **grupo** , escolha **Membros** e adicione dispositivos de piloto automático ao grupo.
    Os dispositivos de piloto automático que ainda não estão registrados são dispositivos em que o nome é igual ao número de série do dispositivo.
4. Se você escolher **dispositivos dinâmicos** para o **tipo de associação** acima, na folha **grupo** , escolha **membros do dispositivo dinâmico** e digite qualquer um dos códigos a seguir na caixa **regra avançada** . Somente os dispositivos AutoPilot são coletados por essas regras, pois eles direcionam atributos que são apenas possuía por dispositivos AutoPilot.
    - Se você quiser criar um grupo que inclui todos os seus dispositivos do AutoPilot, digite: `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - O campo de marca de grupo do Intune é mapeado para o atributo OrderID em dispositivos do Azure AD. Se você quiser criar um grupo que inclui todos os seus dispositivos do AutoPilot com uma marca de grupo específica (o dispositivo OrderID do Azure AD), deverá digitar: `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Se você quiser criar um grupo que inclui todos os seus dispositivos do AutoPilot com uma ID de ordem de compra específica, digite: `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Depois de adicionar o código de **regra avançada** , escolha **salvar**.
5. Escolha **Criar**.  

## <a name="create-an-autopilot-deployment-profile"></a>Criar um perfil de implantação do AutoPilot
Os perfis de implantação do AutoPilot são usados para configurar os dispositivos de piloto automático.
1. No [Intune no portal do Azure](https://aka.ms/intuneportal), escolha **registro de dispositivo** > **registro do Windows** >  perfis de**implantação** > **Criar perfil**.
2. Na página **noções básicas** , digite um **nome** e uma **Descrição**opcional.

    ![Captura de tela da página básico](./media/enrollment-autopilot/create-profile-basics.png)

3. Se você quiser que todos os dispositivos nos grupos atribuídos sejam convertidos automaticamente para o piloto automático, defina **converter todos os dispositivos de destino para o piloto automático** como **Sim**. Todos os dispositivos de propriedade corporativa, não autopiloto em grupos atribuídos serão registrados com o serviço de implantação do AutoPilot. Dispositivos de propriedade pessoal não serão convertidos para o piloto automático. Permitir 48 horas para o registro ser processado. Quando o registro do dispositivo for cancelado e redefinido, o AutoPilot o registrará. Depois que um dispositivo é registrado dessa forma, desabilitar essa opção ou remover a atribuição de perfil não removerá o dispositivo do serviço de implantação do AutoPilot. Em vez disso, você deve [remover o dispositivo diretamente](enrollment-autopilot.md#delete-autopilot-devices).
4. Selecione **Seguinte**.
5. Na página **OOBE (instalação inicial do uso)** , para o modo de **implantação**, escolha uma destas duas opções:
    - **Controlado pelo usuário**: dispositivos com esse perfil estão associados ao usuário que está registrando o dispositivo. As credenciais do usuário são necessárias para registrar o dispositivo.
    - **Autoimplantação (visualização)** : os dispositivos do Windows 10, versão 1809 ou posteriores com esse perfil não estão associados ao usuário que está registrando o dispositivo. As credenciais do usuário não são necessárias para registrar o dispositivo. Quando um dispositivo não tem nenhum usuário associado a ele, as políticas de conformidade baseadas no usuário não se aplicam a ele. Ao usar o modo de implantação automática, somente as políticas de conformidade direcionadas ao dispositivo serão aplicadas.

    ![Captura de tela da página OOBE](./media/enrollment-autopilot/create-profile-outofbox.png)

6. Na caixa **ingressar no Azure ad como** , escolha **ingressado no Azure ad**.
7. Configure as seguintes opções:
    - **Contrato de licença de usuário final (EULA)** : (Windows 10, versão 1709 ou posterior) escolha se deseja mostrar o EULA aos usuários.
    - **Configurações de privacidade**: escolha se deseja mostrar as configurações de privacidade para os usuários.
    >[!IMPORTANT]
    >O valor padrão para a configuração de dados de diagnóstico varia entre as versões do Windows. Para dispositivos que executam o Windows 10, versão 1903, o valor padrão é definido como completo durante a experiência inicial do uso. Para obter mais informações, consulte [dados de diagnóstico do Windows](https://docs.microsoft.com/windows/privacy/windows-diagnostic-data) <br>
    
    - **Ocultar opções de conta de alteração (requer o Windows 10, versão 1809 ou posterior)** : escolha **ocultar** para impedir que as opções alterar conta sejam exibidas nas páginas entrada da empresa e erro de domínio. Essa opção requer [que a identidade visual da empresa seja configurada no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Tipo de conta de usuário**: escolha o tipo de conta do usuário (**administrador** ou usuário **padrão** ). Permitimos que o usuário que está ingressando o dispositivo seja um administrador local adicionando-o ao grupo de Administradores local. Não habilitamos o usuário como o administrador padrão no dispositivo.
    - **Allow White diferenciada OOBE** (requer o Windows 10, versão 1903 ou posterior; [requisitos físicos adicionais](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove#prerequisites)): escolha **Sim** para permitir o suporte a diferenciada branco.
    - **Aplicar modelo de nome de dispositivo** (requer o Windows 10, versão 1809 ou posterior e tipo de junção do Azure AD): escolha **Sim** para criar um modelo a ser usado ao nomear um dispositivo durante o registro. Os nomes devem ter 15 caracteres ou menos e podem ter letras, números e hifens. Os nomes não podem ser todos os números. Use a [macro% serial%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) para adicionar um número de série específico de hardware. Ou use a [macro% Rand: x%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) para adicionar uma cadeia de caracteres aleatória de números, em que x é igual ao número de dígitos a serem adicionados. Você só pode fornecer uma correção prévia para dispositivos híbridos em um [perfil de ingresso no domínio](windows-autopilot-hybrid.md#create-and-assign-a-domain-join-profile). 
    - **Idioma (região)** \*: escolha o idioma a ser usado para o dispositivo. Essa opção só estará disponível se você escolher **autoimplantação** para o **modo de implantação**.
    - **Configurar automaticamente o teclado**\*: se um **idioma (região)** estiver selecionado, escolha **Sim** para ignorar a página de seleção de teclado. Essa opção só estará disponível se você escolher **autoimplantação** para o **modo de implantação**.
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
> O Intune verificará periodicamente se há novos dispositivos nos grupos atribuídos e, em seguida, iniciará o processo de atribuição de perfis a esses dispositivos. Esse processo pode levar vários minutos para ser concluído. Antes de implantar um dispositivo, verifique se esse processo foi concluído.  Você pode verificar em **registro de dispositivo** > **registro do Windows** > **dispositivos** em que você deve ver o status do perfil alterar de "não atribuído" para "atribuindo" e, por fim, a "atribuído".

## <a name="edit-an-autopilot-deployment-profile"></a>Editar um perfil de implantação do AutoPilot
Depois de criar um perfil de implantação do AutoPilot, você pode editar determinadas partes do perfil de implantação.   

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), escolha **registro de dispositivo**.
2. Em **registro do Windows**, na seção **piloto automático do Windows** , escolha perfis de **implantação**.
3. Selecione o perfil que você deseja editar.
4. Clique em **Propriedades** à esquerda para alterar o nome ou a descrição do perfil de implantação. Clique em **salvar** depois de fazer as alterações.
5. Clique em **configurações** para fazer alterações nas configurações do OOBE. Clique em **salvar** depois de fazer as alterações.

> [!NOTE]
> As alterações no perfil são aplicadas aos dispositivos atribuídos a esse perfil. No entanto, o perfil atualizado não será aplicado a um dispositivo que já esteja registrado no Intune até que o dispositivo seja redefinido e registrado novamente.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Alertas para dispositivos Windows AutoPilot não atribuídos  <!-- 163236 -->  

Os alertas mostrarão quantos dispositivos do programa AutoPilot não têm perfis de implantação do AutoPilot. Use as informações do alerta para criar perfis e atribuí-las aos dispositivos não atribuídos. Ao clicar no alerta, você verá uma lista completa de dispositivos do Windows AutoPilot e informações detalhadas sobre eles.

Para ver alertas para dispositivos não atribuídos, no [Intune na portal do Azure](https://aka.ms/intuneportal), escolha **registro de dispositivo** > **visão geral** > **dispositivos não atribuídos**.  

## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Atribuir um usuário a um dispositivo específico do AutoPilot

Você pode atribuir um usuário a um dispositivo específico de piloto automático. Essa atribuição preenche previamente um usuário de Azure Active Directory na página de entrada da [marca da empresa](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) durante a instalação do Windows. Ele também permite que você defina um nome de saudação personalizado. Ele não preenche nem modifica o logon do Windows. Somente usuários licenciados do Intune podem ser atribuídos dessa maneira.

Pré-requisitos: Azure Active Directory Portal da Empresa foi configurado e Windows 10, versão 1809 ou posterior.

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), escolha registro de **dispositivo** > **registro do Windows** > **dispositivos** > escolha o dispositivo > **atribuir usuário**.

    ![Captura de tela de atribuir usuário](./media/enrollment-autopilot/assign-user.png)

2. Escolha um usuário do Azure licenciado para usar o Intune e escolha **selecionar**.

    ![Captura de tela de selecionar usuário](./media/enrollment-autopilot/select-user.png)

3. Na caixa **nome amigável do usuário** , digite um nome amigável ou aceite apenas o padrão. Essa cadeia de caracteres é o nome amigável que é exibido quando o usuário faz logon durante a instalação do Windows.

    ![Captura de tela de nome amigável](./media/enrollment-autopilot/friendly-name.png)

4. Escolha **Ok**.


## <a name="delete-autopilot-devices"></a>Excluir dispositivos do AutoPilot

Você pode excluir dispositivos do Windows AutoPilot que não são registrados no Intune:

- Exclua os dispositivos do Windows AutoPilot no **registro de dispositivo** >  registro do**Windows** > **dispositivos**. Escolha os dispositivos que você deseja excluir e, em seguida, escolha **excluir**. A exclusão do dispositivo do Windows AutoPilot pode levar alguns minutos para ser concluída.

A remoção completa de um dispositivo do seu locatário exige que você exclua o dispositivo do Intune, o dispositivo Azure Active Directory e os registros do dispositivo do Windows AutoPilot. Isso pode ser feito no Intune:

1. Se os dispositivos estiverem registrados no Intune, você deverá primeiro [excluí-los da folha todos os dispositivos do Intune](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Exclua os dispositivos **em dispositivos Azure Active Directory em dispositivos @no__t-** 1**dispositivos do Azure ad**.

3. Exclua os dispositivos do Windows AutoPilot no **registro de dispositivo** >  registro do**Windows** > **dispositivos**. Escolha os dispositivos que você deseja excluir e, em seguida, escolha **excluir**. A exclusão do dispositivo do Windows AutoPilot pode levar alguns minutos para ser concluída.

## <a name="using-autopilot-in-other-portals"></a>Usando o piloto automático em outros portais
Se você não estiver interessado no gerenciamento de dispositivos móveis, poderá usar o AutoPilot em outros portais. Embora o uso de outros portais seja uma opção, recomendamos que você use o Intune apenas para gerenciar suas implantações do AutoPilot. Quando você usa o Intune e outro portal, o Intune não é capaz de:  

- Exibir alterações em perfis criados no Intune, mas editados em outro portal
- Sincronizar perfis criados em outro portal
- Exibir alterações para atribuições de perfil feitas em outro portal
- Sincronizar atribuições de perfil feitas em outro portal
- Exibir alterações na lista de dispositivos que foram feitas em outro portal

## <a name="windows-autopilot-for-existing-devices"></a>Piloto automático do Windows para dispositivos existentes

Você pode agrupar dispositivos Windows por uma ID de correlator ao registrar usando o [AutoPilot para dispositivos existentes](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) por meio de Configuration Manager. A ID do correlator é um parâmetro do arquivo de configuração do AutoPilot. O [atributo de dispositivo do Azure ad enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) é definido automaticamente como "OfflineAutopilotprofile-\<correlator ID @ no__t-2". Isso permite que grupos dinâmicos do Azure AD sejam criados com base na ID do correlator usando o atributo enrollmentprofileName.

>[!WARNING] 
> Como a ID do correlator não está previamente listada no Intune, o dispositivo pode relatar qualquer ID de correlator que desejarem. Se o usuário criar uma ID de correlator correspondente a um nome de perfil do Apple DEP ou do netpilot, o dispositivo será adicionado a qualquer grupo de dispositivos dinâmicos do Azure AD com base no atributo enrollmentProfileName. Para evitar esse conflito:
> - Sempre criar regras de grupo dinâmicos correspondentes ao valor enrollmentProfileName *inteiro*
> - Nunca Nomeie os perfis do piloto automático ou do Apple DEP começando com "OfflineAutopilotprofile-".

## <a name="next-steps"></a>Passos seguintes
Depois de configurar o piloto automático do Windows para dispositivos Windows 10 registrados, saiba como gerenciar esses dispositivos. Para obter mais informações, consulte [o que é Microsoft InTune gerenciamento de dispositivo?](../remote-actions/device-management.md)
