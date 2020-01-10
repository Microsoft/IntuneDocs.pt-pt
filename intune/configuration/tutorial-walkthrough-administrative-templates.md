---
title: Walkthrough – criar modelo administrativo no Microsoft Intune – Azure | Microsoft Docs
description: Este tutorial ou explicação usa Microsoft Intune para configurar modelos ADMX do Office, Windows e Microsoft Edge no Windows 10 e em dispositivos mais recentes.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/07/2020
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 80f489bc91f6d2f51cf9ee378793043a49c4e949
ms.sourcegitcommit: e4602481a25a5e12379f673dfe801c611f51c35b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75735027"
---
# <a name="tutorial-use-the-cloud-to-configure-group-policy-on-windows-10-devices-with-admx-templates-and-microsoft-intune"></a>Tutorial: usar a nuvem para configurar a política de grupo em dispositivos Windows 10 com modelos ADMX e Microsoft Intune

> [!NOTE]
> Este tutorial foi criado como um workshop técnico para o Microsoft Ignite. Ele tem mais pré-requisitos do que os tutoriais típicos, pois ele compara o uso e a configuração de políticas do ADMX no Intune e no local.

Os modelos administrativos de diretiva de grupo, também conhecidos como modelos ADMX, incluem configurações que podem ser definidas em dispositivos Windows 10, incluindo PCs. As configurações de modelo ADMX estão disponíveis por serviços diferentes. Essas configurações são usadas pelos provedores de MDM (gerenciamento de dispositivo móvel), incluindo Microsoft Intune. Por exemplo, você pode ativar ideias de design no PowerPoint, definir um home page no Microsoft Edge, bloquear controles ActiveX no Internet Explorer e muito mais.

Os modelos ADMX estão disponíveis para os seguintes serviços:

- **Microsoft Edge**: baixar no [arquivo de política do Microsoft Edge](https://www.microsoftedgeinsider.com/en-us/enterprise).
- **Office**: Baixe no [Office 365 ProPlus, Office 2019 e Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).
- **Windows**: interno ao sistema operacional Windows 10.

Para obter mais informações sobre as políticas de ADMX, consulte [noções básicas sobre políticas com suporte a ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies).

No Microsoft Intune, esses modelos são internos ao serviço do Intune e estão disponíveis como perfis de **modelos administrativos** . Nesse perfil, você define as configurações que deseja incluir e, em seguida, "atribuir" esse perfil a seus dispositivos.

Neste tutorial, irá:

> [!div class="checklist"]
> * Seja apresentado ao [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
> * Crie grupos de usuários e crie grupos de dispositivos.
> * Compare as configurações no Intune com as configurações de ADMX locais.
> * Crie modelos administrativos diferentes e defina as configurações direcionadas a grupos diferentes.

Ao final deste laboratório, você terá as habilidades para começar a usar o Intune e Microsoft 365 para gerenciar seus usuários e implantar modelos administrativos.

Esta funcionalidade aplica-se a:

- Windows 10 versão 1703 e mais recente

## <a name="prerequisites"></a>Pré-requisitos

- Uma assinatura Microsoft 365 E3 ou e5, que inclui o Intune e o Azure Active Directory (AD) Premium. Se você não tiver uma assinatura E3 ou e5, [experimente gratuitamente](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365?view=o365-worldwide).

  Para obter mais informações sobre o que você obtém com as diferentes licenças de Microsoft 365, consulte [transformar sua empresa com Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans).

- Microsoft Intune está configurado como a **autoridade de MDM do Intune**. Para obter mais informações, consulte [definir a autoridade de gerenciamento de dispositivo móvel](../fundamentals/mdm-authority-set.md).

  > [!div class="mx-imgBorder"]
  > ![definir a autoridade de MDM como Microsoft Intune em seu status de locatário](./media/tutorial-walkthrough-administrative-templates/tenant-status.png)

- Em um DC (controlador de domínio) Active Directory local:

  1. Copie os seguintes modelos do Office e do Microsoft Edge para o [repositório central (pasta SYSVOL)](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra):

      - [Modelos administrativos do Office](https://www.microsoft.com/download/details.aspx?id=49030)
      - [Arquivo de política de > de modelos administrativos do Microsoft Edge](https://www.microsoftedgeinsider.com/en-us/enterprise)

  2. Crie uma política de grupo para enviar esses modelos por push a um computador administrador do Windows 10 Enterprise no mesmo domínio que o DC. Neste tutorial:

      - A política de grupo que criamos com esses modelos é chamada de **OfficeandEdge**. Você verá esse nome nas imagens.
      - O computador do administrador do Windows 10 Enterprise que usamos é chamado de **computador administrador**.

      Em algumas organizações, um administrador de domínio tem duas contas – uma conta de trabalho de domínio típica e uma conta de administrador de domínio diferente usada somente para tarefas de administrador de domínio, como a política de grupo.

      A finalidade desse **computador administrador** é que os administradores entrem com sua conta de administrador de domínio e acessem as ferramentas criadas para gerenciar a diretiva de grupo.

- Neste **computador administrador**:

  - Entre com uma conta de administrador de domínio.

  - Instale as **ferramentas de gerenciamento do RSAT: política de grupo**:

    1. Abra o aplicativo **configurações** > **aplicativos** > **recursos opcionais** > **Adicionar recurso**.
    2. Selecione **rsat: ferramentas de gerenciamento de Política de Grupo** > **instalar**.

        Aguarde enquanto o Windows instala o recurso. Quando concluído, ele eventualmente aparece no aplicativo **Ferramentas administrativas do Windows** .

        > [!div class="mx-imgBorder"]
        > ![aplicativos de ferramentas administrativas do Windows, incluindo Política de Grupo aplicativo de gerenciamento](./media/tutorial-walkthrough-administrative-templates/windows-administrative-tools-app.png)

  - Verifique se você tem direitos de acesso à Internet e de administrador para a assinatura Microsoft 365, que inclui o centro de administração do Endpoint Manager.

## <a name="open-the-endpoint-manager-admin-center"></a>Abrir o centro de administração do Endpoint Manager

1. Abra um navegador da Web Chromium, como o Microsoft Edge versão 77 e posterior.
2. Vá para o [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) (https://devicemanagement.microsoft.com). Entre com a seguinte conta:

    **Usuário**: Insira a conta de administrador de sua assinatura de locatário do Microsoft 365.  
    **Senha**: Insira sua senha.

Esse centro de administração concentra-se no gerenciamento de dispositivos e inclui serviços do Azure, como o Azure AD e o Intune. Talvez você não veja a identidade visual do **Azure Active Directory** e do **Intune** , mas você as está usando.

Você também pode abrir o centro de administração do Endpoint Manager no [centro de administração Microsoft 365](https://admin.microsoft.com):

1. Vá para [https://admin.microsoft.com](https://admin.microsoft.com).
2. Entre com sua conta de administrador de sua assinatura de locatário do Microsoft 365.
3. Em **centros de administração**, selecione **todos os centros de administração** > gerenciamento de ponto de **extremidade**. O centro de administração do Endpoint Manager é aberto.

    > [!div class="mx-imgBorder"]
    > ![ver todos os centros de administração no centro de administração Microsoft 365](./media/tutorial-walkthrough-administrative-templates/microsoft365-admin-centers.png)

## <a name="create-groups-and-add-users"></a>Criar grupos e adicionar usuários

As políticas locais são aplicadas em LSDOU ordem-local, site, domínio e unidade organizacional (UO). Nessa hierarquia, as políticas de UO substituem políticas locais, as políticas de domínio substituem políticas de site e assim por diante.

No Intune, as políticas são aplicadas aos usuários e grupos que você criar. Não há uma hierarquia. Se duas políticas atualizarem a mesma configuração, a configuração aparecerá como um conflito. Se duas políticas de conformidade estiverem em conflito, a política mais restritiva se aplicará. Se dois perfis de configuração estiverem em conflito, a configuração não será aplicada. Para obter mais informações, consulte [perguntas comuns, problemas e resoluções com perfis e políticas de dispositivo](device-profile-troubleshoot.md#if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied).

Nestas próximas etapas, você criará grupos de segurança e adicionará usuários aos grupos. Você pode adicionar um usuário a vários grupos. Por exemplo, é normal que um usuário tenha vários dispositivos, como uma superfície Pro for Work e um dispositivo móvel Android para pessoal. E é normal que uma pessoa acesse os recursos organizacionais desses vários dispositivos.

1. No centro de administração do Endpoint Manager, selecione **grupos** > **novo grupo**.

2. Introduza as seguintes definições:

    - **Tipo de grupo**: selecione **segurança**.
    - **Nome do grupo**: insira **todos os dispositivos dos alunos do Windows 10**.
    - **Tipo de associação**: selecione **atribuído**.

3. Selecione **Membros**e adicione alguns dispositivos.

    A adição de dispositivos é opcional. O objetivo é praticar a criação de grupos e saber como adicionar dispositivos. Se você estiver usando este tutorial em um ambiente de produção, lembre-se do que está fazendo.

4. **Selecione** > **criar** para salvar suas alterações.

    Não consegue ver seu grupo? Selecione **Atualizar**.

5. Selecione **novo grupo**e insira as seguintes configurações:

    - **Tipo de grupo**: selecione **segurança**.
    - **Nome do grupo**: insira **todos os dispositivos Windows**.
    - **Tipo de associação**: selecione **dispositivo dinâmico**.
    - **Membros do dispositivo dinâmico**: configure sua consulta:

        - **Propriedade**: selecione **deviceOSType**.
        - **Operador**: selecione **é igual a**.
        - **Valor**: Insira o **Windows**.

        1. Selecione **Adicionar expressão**. Sua expressão é mostrada na **sintaxe da regra**:

            > [!div class="mx-imgBorder"]
            > ![criar uma consulta dinâmica e adicionar a expressão no modelo administrativo Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/dynamic-group-query.png)

            Quando os usuários ou dispositivos atendem aos critérios inseridos, eles são automaticamente adicionados aos grupos dinâmicos. Neste exemplo, os dispositivos são adicionados automaticamente a esse grupo quando o sistema operacional é o Windows. Se você estiver usando este tutorial em um ambiente de produção, tenha cuidado. O objetivo é praticar a criação de grupos dinâmicos.

        2. **Salve** > **criar** para salvar suas alterações.

6. Crie o grupo **todos os professores** com as seguintes configurações:

    - **Tipo de grupo**: selecione **segurança**.
    - **Nome do grupo**: insira **todos os professores**.
    - **Tipo de associação**: selecione **usuário dinâmico**.
    - **Membros dinâmicos do usuário**: configure sua consulta:

      - **Propriedade**: selecione **Departamento**.
      - **Operador**: selecione **é igual a**.
      - **Valor**: insira **professores**.

        1. Selecione **Adicionar expressão**. Sua expressão é mostrada na **sintaxe da regra**.

            Quando os usuários ou dispositivos atendem aos critérios inseridos, eles são automaticamente adicionados aos grupos dinâmicos. Neste exemplo, os usuários são adicionados automaticamente a esse grupo quando seu departamento é professor. Você pode inserir o departamento e outras propriedades quando os usuários são adicionados à sua organização. Se você estiver usando este tutorial em um ambiente de produção, tenha cuidado. O objetivo é praticar a criação de grupos dinâmicos.

        2. **Salve** > **criar** para salvar suas alterações.

### <a name="talking-points"></a>Pontos de discussão

- Grupos dinâmicos são um recurso no Azure AD Premium. Se você não tiver Azure AD Premium, você estará licenciado para criar apenas grupos atribuídos. Para obter mais informações sobre grupos dinâmicos, consulte:

  - [Associação de grupo dinâmico no Azure Active Directory (parte 1)](https://blogs.technet.microsoft.com/pauljones/2017/08/28/dynamic-group-membership-in-azure-active-directory-part-1/)
  - [Associação de grupo dinâmico no Azure Active Directory (parte 2)](https://blogs.technet.microsoft.com/pauljones/2017/08/29/dynamic-group-membership-in-azure-active-directory-part-2/)

- O Azure AD Premium inclui outros serviços que são comumente usados ao gerenciar aplicativos e dispositivos, incluindo a [MFA (autenticação multifator)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) e o [acesso condicional](https://docs.microsoft.com/azure/active-directory/conditional-access/overview).

- Muitos administradores perguntam quando usar grupos de usuários e quando usar grupos de dispositivos. Para obter algumas diretrizes, consulte [grupos de usuários vs. grupos de dispositivos](device-profile-assign.md#user-groups-vs-device-groups).

- Lembre-se de que um usuário pode pertencer a vários grupos. Considere alguns dos outros grupos de usuários e dispositivos dinâmicos que você pode criar, como:

  - Todos os alunos
  - Todos os dispositivos Android
  - Todos os dispositivos iOS
  - Marketing
  - Recursos Humanos
  - Todos os funcionários do Charlotte
  - Todos os funcionários de Redmond
  - Administradores de ti da costa oeste
  - Administradores de ti da costa leste

Os usuários e grupos criados também são vistos no [centro de administração Microsoft 365](https://admin.microsoft.com), no Azure AD na portal do Azure e [Microsoft Intune no portal do Azure](https://go.microsoft.com/fwlink/?linkid=2090973). Você pode criar e gerenciar grupos em todas essas áreas para sua assinatura de locatário. **Se sua meta for o gerenciamento de dispositivos, use o [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)** .

### <a name="review-group-membership"></a>Rever associação ao grupo

1. No centro de administração do Endpoint Manager, selecione **usuários** > selecionar o nome de qualquer usuário existente.

    > [!div class="mx-imgBorder"]
    > ![no centro de administração do Endpoint Manager, selecione usuários](./media/tutorial-walkthrough-administrative-templates/select-users-endpoint-manager-admin-center.png)

2. Examine algumas das informações que você pode adicionar ou alterar. Por exemplo, examine as propriedades que você pode configurar, como cargo, departamento, cidade, local do escritório e muito mais. Você pode usar essas propriedades em suas consultas dinâmicas ao criar grupos dinâmicos.
3. Selecione **grupos** para ver a associação deste usuário. Você também pode remover o usuário de um grupo.
4. Selecione algumas das outras opções para ver mais informações e o que você pode fazer. Por exemplo, examine a licença atribuída, os dispositivos do usuário e muito mais.

### <a name="what-did-i-just-do"></a>O que eu acabei de fazer?

No centro de administração do Endpoint Manager, você criou novos grupos de segurança e adicionou usuários e dispositivos existentes a esses grupos. Usaremos esses grupos em etapas posteriores neste tutorial.

## <a name="create-a-template-in-intune"></a>Criar um modelo no Intune

Nesta seção, criamos um modelo administrativo no Intune, examinamos algumas configurações no **política de grupo Management**e comparamos a mesma configuração no Intune. O objetivo é mostrar uma configuração na diretiva de grupo e mostrar a mesma configuração no Intune.

1. No centro de administração do Endpoint Manager, selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
2. Introduza as seguintes propriedades:

    - **Nome**: Insira um nome descritivo para o perfil. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. Por exemplo, insira **modelo de administrador – dispositivos de aluno do Windows 10**.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: selecione **Windows 10 e posterior**.
    - **Tipo de perfil**: selecione **modelos administrativos**.

3. Selecione **Criar**. Na lista suspensa **selecionar uma categoria** , selecione **todos os produtos**. Todas as configurações são mostradas. Nessas configurações, observe as seguintes propriedades:

    - O **caminho** para a política é o mesmo que o política de grupo Management ou o gpedit.
    - A configuração se aplica a usuários ou dispositivos.

### <a name="open-group-policy-management"></a>Abrir gerenciamento de Política de Grupo

Nesta seção, mostramos uma política no Intune e sua política de correspondência no Editor de Gerenciamento de Política de Grupo.

#### <a name="compare-a-device-policy"></a>Comparar uma política de dispositivo

1. No **computador do administrador**, abra o aplicativo de **Gerenciamento de política de grupo** .

    Este aplicativo é instalado com o **rsat: ferramentas de gerenciamento de política de grupo**, que é um recurso opcional que você instala no Windows. [Pré-requisitos](#prerequisites) (neste artigo) lista as etapas para instalá-lo.

2. Expanda **domínios** > selecione seu domínio. Por exemplo, selecione **contoso.net**.
3. Clique com o botão direito do mouse na política **OfficeandEdge** > **Editar**. Isso abre o aplicativo Editor de Gerenciamento de Política de Grupo.

    > [!div class="mx-imgBorder"]
    > ![clique com o botão direito do mouse na política de grupo ADMX do Office e do Edge e selecione Editar](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management.png)

    **OfficeandEdge** é uma política de grupo que inclui os modelos ADMX do Office e do Microsoft Edge. Essa política é descrita em [pré-requisitos](#prerequisites) (neste artigo).

4. Expanda **configuração do computador** > **políticas** > **Modelos Administrativos** > **painel de controle** > **personalização**. Observe as configurações disponíveis.

    > [!div class="mx-imgBorder"]
    > ![expanda Configuração do computador no Editor de Gerenciamento de Política de Grupo e vá para personalização](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management-editor-admx-policy.png)

    Clique duas vezes em **impedir habilitar a câmera da tela de bloqueio**e veja as opções disponíveis:

    > [!div class="mx-imgBorder"]
    > ![ver as opções de configuração do computador na diretiva de grupo](./media/tutorial-walkthrough-administrative-templates/prevent-enabling-lock-screen-camera-admx-policy.png)

5. No centro de administração do gerenciamento de dispositivos, vá para o modelo **de administrador-modelo de dispositivos dos alunos do Windows 10** .
6. Selecione **todos os produtos** na lista suspensa e procure por **personalização**:

    > [!div class="mx-imgBorder"]
    > ![Pesquisar a personalização no modelo administrativo no Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/search-personalization-administrative-template.png)

    Observe as configurações disponíveis.

    O tipo de configuração é **dispositivo**e o caminho é **\control Panel\Personalization**. Esse caminho é semelhante ao que você acabou de ver no Editor de Gerenciamento de Política de Grupo. Se você abrir a configuração, verá as mesmas opções **não configuradas**, **habilitadas**e **desabilitadas** que você vê no editor de gerenciamento de política de grupo.

#### <a name="compare-a-user-policy"></a>Comparar uma política de usuário

1. Em seu modelo de administrador, procure **navegação InPrivate**. Observe o caminho e se a configuração se aplica a usuários e dispositivos.

2. Em **Editor de gerenciamento de política de grupo**, localize as configurações de usuário e dispositivo correspondentes:

    - Dispositivo: expanda **configuração do computador** > **políticas** > **Modelos Administrativos** > **componentes do Windows** > o **Internet Explorer** > **privacidade** > **desative a navegação InPrivate**.
    - Usuário: expanda **configuração do usuário** > **políticas** > **Modelos Administrativos** > **componentes do Windows** > o **Internet Explorer** > **privacidade** > **desative a navegação InPrivate**.

    > [!div class="mx-imgBorder"]
    > ![desativar a navegação InPrivate no Internet Explorer usando o modelo ADMX](./media/tutorial-walkthrough-administrative-templates/group-policy-turn-off-inprivate-browsing.png)

> [!TIP]
> Para ver as políticas internas do Windows, você também pode usar o GPEdit (**Editar** aplicativo de política de grupo).

#### <a name="compare-an-edge-policy"></a>Comparar uma política de borda

1. No centro de administração do gerenciamento de dispositivos, vá para o modelo **de administrador-modelo de dispositivos dos alunos do Windows 10** .
2. Selecione **borda versão 77 e posterior** na lista suspensa.
3. Procure **inicialização**. Observe as configurações disponíveis.
4. Em Editor de Gerenciamento de Política de Grupo, encontre estas configurações:

    - Dispositivo: expanda **configuração do computador** > **políticas** > **modelos administrativos** > **Microsoft Edge** > **inicialização, Home Page e nova página da guia**.
    - Usuário: expanda **configuração do usuário** > **políticas** > **modelos administrativos** > **Microsoft Edge** > **inicialização, página inicial e nova guia**

### <a name="what-did-i-just-do"></a>O que eu acabei de fazer?

Você criou um modelo administrativo no Intune. Neste modelo, examinamos algumas configurações de ADMX e examinamos as mesmas configurações de ADMX no gerenciamento de Política de Grupo.

## <a name="add-settings-to-the-students-admin-template"></a>Adicionar configurações ao modelo de administrador de alunos

Neste modelo, configuramos algumas configurações do Internet Explorer para bloquear dispositivos compartilhados por vários alunos.

1. Em seu **modelo de administrador-dispositivos de aluno do Windows 10**, procure desativar a **navegação InPrivate**e selecione a política de dispositivo:

    > [!div class="mx-imgBorder"]
    > ![desativar a política de dispositivo de navegação InPrivate no modelo administrativo no Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/turn-off-inprivate-browsing-administrative-template.png)

2. Nesta janela, observe a descrição e os valores que você pode definir. Essas opções são semelhantes às que você vê na diretiva de grupo.
3. Selecione **habilitado** > **OK** para salvar as alterações.
4. Além disso, defina as seguintes configurações do Internet Explorer. Certifique-se de selecionar **OK** para salvar as alterações.

    - **Permitir arrastar e soltar ou copiar e colar arquivos**
      - **Tipo**: dispositivo
      - **Caminho**: \Windows Windows\Internet Explorer\painel de controle de \ Page\Internet Zone
      - **Valor**: desabilitado

    - **Evitar ignorar erros de certificado**
      - **Tipo**: dispositivo
      - **Caminho**: \Windows Windows\Internet Explorer\painel de controle
      - **Valor**: habilitado

    - **Desabilitar a alteração de home page configurações**
      - **Tipo**: usuário
      - **Caminho**: \Windows Windows\Internet Explorer
      - **Valor**: habilitado
      - **Home Page**: Insira uma URL, como `contoso.com`.

5. Limpe o filtro de pesquisa. Observe que as configurações que você configurou estão listadas na parte superior:

    > [!div class="mx-imgBorder"]
    > ![configurações definidas são listadas na parte superior em Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/configured-settings-administrative-template.png)

### <a name="assign-your-template"></a>Atribuir seu modelo

1. Em seu modelo, selecione **atribuições**. Talvez seja necessário fechar o modelo e, em seguida, selecioná-lo na lista **dispositivos – perfis de configuração** :

    > [!div class="mx-imgBorder"]
    > ![selecione o perfil de modelo administrativo na lista perfis de configuração de dispositivo no Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/filter-administrative-template-device-configuration-profiles-list.png)

2. Escolha **Selecionar grupos para incluir**. É mostrada uma lista de usuários e grupos existentes.
3. Selecione o grupo **todos os dispositivos dos alunos do Windows 10** que você criou anteriormente > **selecione**.

    Se você estiver usando este tutorial em um ambiente de produção, considere adicionar grupos que estão vazios. O objetivo é praticar a atribuição do modelo.

4. **Guarde** as suas alterações.

Assim que o perfil é salvo, ele se aplica aos dispositivos quando eles fazem check-in no Intune. Se os dispositivos estiverem conectados à Internet, isso poderá acontecer imediatamente. Para obter mais informações sobre tempos de atualização de política, consulte [quanto tempo leva para que os dispositivos obtenham uma política, um perfil ou um aplicativo depois que eles são atribuídos](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

Ao atribuir políticas e perfis estritos ou restritivos, não bloqueie-se. Considere criar um grupo que é excluído de suas políticas e perfis. A ideia é ter acesso para solucionar problemas. Monitore esse grupo para confirmar que ele está sendo usado como pretendido.

### <a name="what-did-i-just-do"></a>O que eu acabei de fazer?

No centro de administração do Endpoint Manager, você criou um perfil de configuração de dispositivo de modelo administrativo e atribuiu esse perfil a um grupo que você criou.

## <a name="create-a-onedrive-template"></a>Criar um modelo do OneDrive

Nesta seção, você cria um modelo de administrador do OneDrive no Intune para controlar algumas configurações. Essas configurações específicas são escolhidas porque são normalmente usadas pelas organizações.

1. Crie outro perfil (**dispositivos** > **perfis de configuração** > **Criar perfil**).

2. Introduza as seguintes propriedades:

    - **Nome**: Insira o **modelo de administrador – políticas do onedrive que se aplicam a todos os usuários do Windows 10**.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: selecione **Windows 10 e posterior**.
    - **Tipo de perfil**: selecione **modelos administrativos**.

3. Selecione **Criar**.
4. Selecione **Office** na lista suspensa.
5. **Habilite** as configurações a seguir. Certifique-se de selecionar **OK** para salvar as alterações.

    - **Conectar silenciosamente usuários ao cliente de sincronização do OneDrive com suas credenciais do Windows**
    - **Usar arquivos do OneDrive sob demanda**
    - **Impedir que os usuários sincronizem contas pessoais do OneDrive**

As configurações são semelhantes às seguintes configurações:

> [!div class="mx-imgBorder"]
> ![criar um modelo administrativo do OneDrive no Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/one-drive-administrative-template.png)

Para obter mais informações sobre as configurações do cliente do OneDrive, consulte [usar política de grupo para controlar as configurações do cliente de sincronização do onedrive](https://docs.microsoft.com/onedrive/use-group-policy).

### <a name="assign-your-template"></a>Atribuir seu modelo

1. Em seu modelo, selecione **atribuições**.
2. Escolha **Selecionar grupos para incluir**. É mostrada uma lista de usuários e grupos existentes.
3. Selecione o grupo **todos os dispositivos Windows** que você criou anteriormente > **selecione**.

    Se você estiver usando este tutorial em um ambiente de produção, considere adicionar grupos que estão vazios. O objetivo é praticar a atribuição do modelo.

4. **Guarde** as suas alterações.

Neste ponto, você criou alguns modelos administrativos e os atribuiu a grupos que você criou. A próxima etapa é criar um modelo administrativo usando o Windows PowerShell e a API de Microsoft Graph para o Intune.

## <a name="optional-create-a-policy-using-powershell-and-graph-api"></a>Opcional: criar uma política usando o PowerShell e API do Graph

Esta seção usa os recursos a seguir. Instalaremos esses recursos nesta seção.

- [SDK do Intune PowerShell](https://github.com/microsoft/Intune-PowerShell-SDK)
- [API de Microsoft Graph para o Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

1. No **computador do administrador**, abra o **Windows PowerShell** como administrador:

    1. Na barra de pesquisa, insira **PowerShell**.
    2. Clique com o botão direito do mouse em **Windows PowerShell** > **Executar como administrador**.

    > [!div class="mx-imgBorder"]
    > ![executar o Windows PowerShell como administrador](./media/tutorial-walkthrough-administrative-templates/run-windows-powershell-administrator.png)

2. Obter e definir a política de execução.

    1. Insira: `get-ExecutionPolicy`

        Anote em que ele está definido, o que pode ser **restringido**. Quando terminar com o tutorial, defina-o de volta para seu valor original.

    2. Insira: `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`

    3. Insira `Y` para alterá-lo.

    A política de execução do PowerShell ajuda a impedir a execução de scripts mal-intencionados. Para obter mais informações, consulte [sobre as políticas de execução](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies).

3. Insira: `Install-Module -Name Microsoft.Graph.Intune`

    Insira `Y` se:

    - Solicitado a instalar o provedor do NuGet
    - Solicitado a instalar os módulos de um repositório não confiável

    Pode levar vários minutos para ser concluído. Quando terminar, um prompt semelhante ao seguinte prompt será mostrado:

    > [!div class="mx-imgBorder"]
    > ![prompt do Windows PowerShell depois de instalar um módulo](./media/tutorial-walkthrough-administrative-templates/powershell-prompt.png)

4. No navegador da Web, vá para [https://github.com/Microsoft/Intune-PowerShell-SDK/releases](https://github.com/Microsoft/Intune-PowerShell-SDK/releases)e selecione o arquivo **Intune-PowerShell-SDK_v6.1907.00921.0001. zip** .

    1. Selecione **salvar como**e selecione uma pasta que você vai lembrar. `c:\psscripts` é uma boa opção.
    2. Abra a pasta, clique com o botão direito do mouse no arquivo. zip > **extraia todas as** > **extração**. Sua estrutura de pastas é semelhante à seguinte pasta:

        > [!div class="mx-imgBorder"]
        > ![estrutura de pastas do SDK do Intune PowerShell após ser extraída](./media/tutorial-walkthrough-administrative-templates/psscripts-directory.png)

5. Na guia **Exibir** , verifique **as extensões de nome de arquivo**:

    > [!div class="mx-imgBorder"]
    > ![selecionar extensões de nome de arquivo na guia Exibir no Explorer](./media/tutorial-walkthrough-administrative-templates/file-names-extension.png)

6. Em sua pasta e vá para `c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471`. Clique com o botão direito do mouse em cada. dll > **propriedades** > **desbloquear**.

    > [!div class="mx-imgBorder"]
    > ![desbloquear as DLLs](./media/tutorial-walkthrough-administrative-templates/unblock-dll.png)

7. Em seu aplicativo do **Windows PowerShell** , digite:

    ```powershell
    Import-Module c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471\Microsoft.Graph.Intune.psd1
    ```

    Insira `R` se for solicitado a executar a partir do Publicador não confiável.

8. Os modelos administrativos do Intune usam a versão beta do Graph:

    1. Insira: `Update-MSGraphEnvironment -SchemaVersion 'beta'`

    2. Insira: `Connect-MSGraph -AdminConsent`

    3. Quando solicitado, entre com a mesma conta de administrador do Microsoft 365. Esses cmdlets criam a política em sua organização de locatários.

        **Usuário**: Insira a conta de administrador de sua assinatura de locatário do Microsoft 365.  
        **Senha**: Insira sua senha.

    4. Selecione **Aceitar**.

9. Crie o perfil de configuração de **configuração de teste** . introduza:

    ```powershell
    $configuration = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations -Content '{"displayName":"Test Configuration","description":"A test configuration created through PS"}' -HttpMethod POST
    ```

    Quando esses cmdlets forem bem-sucedidos, o perfil será criado. Para confirmar, acesse o centro de administração do Endpoint Manager > **perfis de configuração**. Seu perfil de **configuração de teste** deve ser listado.

10. Obtenha todos os SettingDefinitions. introduza:

    ```powershell
    $settingDefinitions = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions -HttpMethod GET
    ```

11. Localize a ID de definição usando o nome de exibição da configuração. introduza:

    ```powershell
    $desiredSettingDefinition = $settingDefinitions.value | ? {$_.DisplayName -Match "Silently sign in users to the OneDrive sync client with their Windows credentials"}
    ```

12. Defina uma configuração. introduza:

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues" -Content ("{""enabled"":""true"",""configurationType"":""policy"",""definition@odata.bind"":""https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions('$($desiredSettingDefinition.id)')""}") -HttpMethod POST
    ```

    ```powershell
    Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -Content ("{""enabled"":""false""}") -HttpMethod PATCH
    ```

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -HttpMethod GET
    ```

### <a name="see-your-policy"></a>Veja sua política

1. No centro de administração do Endpoint Manager > **perfis de configuração** > **Atualizar**.
2. Selecione o perfil de **configuração de teste** > **configurações**.
3. Na lista suspensa, selecione **todos os produtos**.

Você verá a configuração **conectar silenciosamente usuários ao cliente de sincronização do onedrive com suas credenciais do Windows** .

## <a name="policy-best-practices"></a>Práticas recomendadas de política

Ao criar políticas e perfis no Intune, há algumas recomendações e práticas recomendadas a serem consideradas. Para obter mais informações, consulte [práticas recomendadas de política e perfil](device-profile-create.md#recommendations).

## <a name="clean-up-resources"></a>Limpar recursos

Quando não for mais necessário, você pode:

- Exclua os grupos que você criou:

  - **Todos os dispositivos dos alunos do Windows 10**
  - **Todos os dispositivos Windows**
  - **Todos os professores**

- Exclua os modelos de administração que você criou:

  - **Modelo de administração-dispositivos de aluno do Windows 10**
  - **Modelo de administrador – políticas do OneDrive que se aplicam a todos os usuários do Windows 10**
  - **Configuração de teste**

- Defina a política de execução do Windows PowerShell de volta para seu valor original. O exemplo a seguir define a política de execução como restrita:

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Restricted
  ```

## <a name="next-steps"></a>Próximos passos

Neste tutorial, você ficou mais familiarizado com o [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), usou o construtor de consultas para criar grupos dinâmicos e criou modelos administrativos no Intune para definir [as configurações do ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies). Você também comparado usando modelos ADMX locais e na nuvem com o Intune. Como um bônus, você usou cmdlets do PowerShell para criar um modelo administrativo.

Para obter mais informações sobre modelos administrativos no Intune, consulte:

> [!div class="nextstepaction"]
> [Usar modelos do Windows 10 para definir configurações de política de grupo no Intune](administrative-templates-windows.md)
