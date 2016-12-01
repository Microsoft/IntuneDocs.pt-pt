<<<<<<< HEAD
---
title: "Criar e implementar políticas de MAM | Microsoft Intune"
description: "Utilize as instruções passo a passo neste tópico para criar e implementar políticas de gestão de aplicações móveis."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1b9a343-1737-4a65-a9c6-aca48acad11c
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: e5befdd4925f88d41c454d9c1c36eaf02fdb598d

||||||| merged common ancestors
---
title: "Criar e implementar políticas de MAM | Microsoft Intune"
description: "Utilize as instruções passo a passo neste tópico para criar e implementar políticas de gestão de aplicações móveis."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1b9a343-1737-4a65-a9c6-aca48acad11c
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: e5befdd4925f88d41c454d9c1c36eaf02fdb598d

=======
---
title: "Criar e implementar políticas de MAM | Microsoft Intune"
description: "Utilize as instruções passo a passo neste tópico para criar e implementar políticas de gestão de aplicações móveis."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1b9a343-1737-4a65-a9c6-aca48acad11c
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 93960044c4fa322cf20677b612ce732b8a30f84b
ms.openlocfilehash: b5901c56384b7f5c80be4f849906e8bba4737ff0

>>>>>>> 6851ab9d7bde3f80f14f27ebf43e5f2b265939e2

---
<<<<<<< HEAD

# Criar e implementar políticas de gestão de aplicações móveis com o Microsoft Intune
As políticas de gestão de aplicações móveis (MAM) podem ser aplicadas a aplicações em execução em dispositivos que podem ou não ser geridos pelo Intune. Para obter uma descrição mais detalhada do funcionamento das políticas de MAM e dos cenários que as políticas de MAM do Intune suportam, leia o tópico [Proteger dados de aplicações com políticas de gestão de aplicações móveis](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).
||||||| merged common ancestors

# Criar e implementar políticas de gestão de aplicações móveis com o Microsoft Intune
As políticas de gestão de aplicações móveis (MAM) podem ser aplicadas a aplicações em execução em dispositivos que podem ou não ser geridos pelo Intune. Para obter uma descrição mais detalhada do funcionamento das políticas de MAM e dos cenários que as políticas de MAM do Intune suportam, leia o tópico [Proteger dados de aplicações com políticas de gestão de aplicações móveis](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).
=======

# <a name="create-and-deploy-mobile-app-management-policies-with-microsoft-intune"></a>Criar e implementar políticas de gestão de aplicações móveis com o Microsoft Intune
As políticas de gestão de aplicações móveis (MAM) podem ser aplicadas a aplicações em execução em dispositivos que podem ou não ser geridos pelo Intune. Para obter uma descrição mais detalhada do funcionamento das políticas de MAM e dos cenários que as políticas de MAM do Intune suportam, consulte [Proteger dados de aplicações com políticas de gestão de aplicações móveis](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).
>>>>>>> 6851ab9d7bde3f80f14f27ebf43e5f2b265939e2

Este tópico descreve o processo de criação de uma política de MAM no **portal do Azure**. O portal do Azure é a nova consola de administração para a criação de políticas de MAM e recomendamos que utilize este portal para criar políticas de MAM. O portal do Azure suporta os seguintes cenários MAM:
- Dispositivos inscritos no Intune.
- Dispositivos geridos por uma solução de MDM de terceiros.
- Dispositivos que não são geridos por qualquer solução MDM (BYOD).

>[!IMPORTANT]
Considere o seguinte se estiver atualmente a utilizar a **consola de administração do Intune** para gerir os seus dispositivos:

> * Pode criar uma política de MAM que suporta as aplicações para os dispositivos inscritos no Intune utilizando a [consola de administração do Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).
> * As políticas MAM criadas na consola de administração do Intune não podem ser importadas para o portal do Azure.  Têm de ser recriadas no portal do Azure.

> * Poderá não ver todas as definições de política de MAM na consola de administração do Intune. O portal do Azure é a nova consola de administração para a criação de políticas de MAM.

> * Para implementar aplicações geridas, tem de criar uma política de MAM na consola de administração do Intune. Neste caso, pode querer criar políticas de MAM na consola de administração do Intune e no portal do Azure: na consola de administração do Intune para se certificar de que tem a capacidade de implementar aplicações geridas e no portal do Azure porque é a nova consola de administração que tem todas as definições de política de MAM.

> * Se criar políticas de MAM na consola de administração do Intune e no portal do Azure, a política criada no portal do Azure é aplicada às aplicações.

Para ver uma lista de definições de política suportadas para plataformas Android e iOS, selecione uma das seguintes opções:

> [!div class="op_single_selector"]
- [Políticas para iOS](ios-mam-policy-settings.md)
- [Políticas para Android](android-mam-policy-settings.md)

##  <a name="create-a-mam-policy"></a>Criar uma política de MAM
Antes de criar uma política de MAM, reveja as informações de [pré-requisitos e suporte](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md).
1.  Escolha **Gestão de aplicações móveis do Intune &gt; Definições** para abrir o painel **Definições**.

    ![Captura de ecrã do painel de gestão de aplicações móveis do Intune](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > Se for a primeira vez que está a utilizar o portal do Azure, leia primeiro o artigo [Portal do Azure para políticas de MAM do Microsoft Intune](azure-portal-for-microsoft-intune-mam-policies.md) para se familiarizar com o portal.

2.  No painel **Definições**, escolha **Política de aplicação**. É aberto o painel **Política da aplicação**, onde irá criar novas políticas e editar as já existentes. Selecione **Adicionar uma política**.

    ![Captura de ecrã do painel Política de aplicação com a opção de menu Adicionar uma política realçada ](../media/AppManagement/AzurePortal_MAM_AddPolicy.png)

3.  Escreva um nome para a política, adicione uma breve descrição e selecione o tipo de plataforma para criar uma política para iOS ou Android. Pode criar mais de uma política para cada plataforma.

    ![Captura de ecrã do painel Adicionar uma política](../media/AppManagement/AzurePortal_MAM_AddPolicy_only.png)

4.  Escolha **Aplicações** para abrir o painel **Aplicações** onde é apresentada uma lista de aplicações disponíveis. Selecione uma ou mais aplicações na lista que pretende associar à política que está a criar. Depois de selecionar as aplicações, selecione **Selecionar** na parte inferior do painel **Aplicações** para guardar a sua seleção.

    > [!IMPORTANT]
    > Tem de selecionar pelo menos uma aplicação para criar uma política.

5.  No painel **Adicionar uma política**, escolha **Configurar definições necessárias** para abrir o painel de definições de política.

    Existem duas categorias de definições de política: **Reposicionamento de Dados** e **Acesso**.  As políticas de reposicionamento de dados são aplicáveis ao movimento de dados de e para as aplicações, enquanto que as políticas de acesso determinam a forma como o utilizador final acede às aplicações num contexto profissional.
    Para começar, as definições de política têm valores predefinidos. Não é necessário efetuar quaisquer alterações se os valores predefinidos cumprirem os requisitos.

    > [!TIP]
    > Estas definições de política apenas são impostas quando utilizar aplicações no contexto profissional.  Quando o utilizador final utiliza a aplicação para realizar uma tarefa pessoal, este não será afetado por estas políticas.

    ![Captura de ecrã do painel Definições, juntamente com o painel Adicionar uma política](../media/AppManagement/AzurePortal_MAM_PolicySettings.png)

6.  Escolha **OK** para guardar esta configuração. Está agora novamente no painel **Adicionar uma política** . Escolha **Criar** para criar a política e guardar as suas definições.

    ![Captura de ecrã do painel Adicionar uma política a mostrar que as Aplicações e Definições foram configuradas](../media/AppManagement/AzurePortal_MAM_CreatePolicy.png)



Quando acabar de criar uma política, conforme descrito no procedimento anterior, esta não é implementada para nenhum utilizador. Para implementar uma política, consulte a secção seguinte, "Implementar uma política para utilizadores".

> [!IMPORTANT]
> Se criar uma política de MAM para uma aplicação com a consola de administração do Intune e uma política de MAM através do portal do Azure, a política que criou com o portal do Azure tem precedência. No entanto, os relatórios na consola do Intune ou do Configuration Manager irão comunicar as definições de política criadas na consola de administração do Intune. Por exemplo:
>
> -   Criou uma política de MAM na consola de administração do Intune que bloqueia a cópia a partir de uma aplicação.
> -   Criou uma política de MAM na consola do Azure que permite a cópia a partir de uma aplicação.
> -   Associa ambas estas políticas à mesma aplicação.
> -   A política que criou a partir da consola do Azure tem precedência e a cópia é permitida.
> -   No entanto, o estado e os relatórios na consola do Intune indicarão incorretamente que a cópia está bloqueada.

## <a name="deploy-a-policy-to-users"></a>Implementar uma política para utilizadores

1.  No painel **Política**, escolha **Grupos de utilizadores**, que abre o painel **Grupos de utilizadores**. Escolha **Adicionar um grupo de utilizadores** no painel **Grupos de utilizadores** para abrir o painel **Adicionar um grupo de utilizadores**.

    ![Captura de ecrã do painel Grupos de utilizadores com a opção de menu Adicionar um grupo de utilizadores realçada](../media/AppManagement/AzurePortal_MAM_AddUserstoPolicy.png)

2.  É apresentada uma lista dos grupos de utilizadores no painel **Adicionar grupo de utilizadores** . Esta é uma lista de todos os grupos de segurança no seu **Azure Active Directory**. Selecione os grupos de utilizadores aos quais pretende aplicar esta política e, em seguida, selecione **Selecionar**. Escolher **Selecionar** implementa a política para os utilizadores.

    ![Captura de ecrã do painel Adicionar um grupo de utilizadores, que mostra a lista de utilizadores do Azure Active Directory](../media/AppManagement/AzurePortal_MAM_SelectUserstoDeploy.png)

    Criou agora uma política e implementou-a a utilizadores.

Apenas os utilizadores com licenças do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] atribuídas são afetados pela política. Os utilizadores que estão no grupo de segurança que selecionou que não têm uma licença do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] atribuída não são afetados.

>[!IMPORTANT]
> Se estiver a utilizar o Intune com o Configuration Manager para gerir os seus dispositivos iOS e Android, a política só é aplicada aos utilizadores diretamente no grupo que selecionou. Os membros dos grupos subordinados aninhados dentro do grupo que selecionou não são afetados.

Os utilizadores finais podem transferir as aplicações a partir da Apple Store ou do Google Play. Para obter mais informações, consulte:
* [O que esperar quando a sua aplicação Android é gerida por políticas de MAM](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [O que esperar quando a sua aplicação iOS é gerida por políticas de MAM](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

##  <a name="change-existing-policies"></a>Alterar políticas existentes
Pode editar uma política existente e aplicá-la aos utilizadores visados. No entanto, quando altera as políticas existentes, os utilizadores que já têm sessão iniciada nas aplicações não verão as alterações durante um período de 8 horas.

Para ver o efeito das alterações imediatamente, o utilizador final terá de terminar sessão na aplicação e voltar a iniciar sessão.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Para alterar a lista de aplicações associadas à política

1.  No painel **Política de aplicação**, escolha a política que pretende alterar. Esta ação abre um painel  específico da política que acabou de selecionar.

    ![Captura de ecrã de uma política existente aberta num painel separado](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  No painel da política, escolha **Aplicações alvo** para abrir a lista de aplicações.

3.  Remova ou adicione aplicações a partir da lista e selecione o ícone **Guardar** para guardar as alterações.

### <a name="to-change-the-list-of-user-groups"></a>Para alterar a lista de grupos de utilizadores

1.  No painel **Política de aplicação**, escolha a política que pretende alterar. Esta ação abre o painel específico da política que selecionou.

2.  No painel da política, escolha **Grupos de utilizadores** para abrir o painel **Grupo de utilizadores** que mostra a lista dos grupos de utilizadores atuais que têm esta política.

3.  Para adicionar um novo grupo de utilizadores à política, selecione **Adicionar grupo de utilizadores** e selecione o grupo de utilizadores. Escolha **Selecionar** para implementar a política no grupo que selecionou.

    ![Captura de ecrã do painel Adicionar um grupo de utilizadores com dois grupos de utilizadores selecionados](../media/AppManagement/AzurePortal_MAM_ChangePolicy_SelectUser.png)

4.  Para eliminar um grupo de utilizadores, realce o grupo de utilizadores que pretende remover. Em seguida, selecione as reticências (…) e **Eliminar** para remover o grupo de utilizadores.

    ![Captura de ecrã que mostra a opção Eliminar ](../media/AppManagement/AzurePortal_MAM_ChangePolicy_DeleteUser.png)

### <a name="to-change-policy-settings"></a>Para alterar definições de política

1.  No painel **Política de aplicação**, escolha a política que pretende alterar. Esta ação abre um painel  específico da política que acabou de selecionar.

    ![Captura de ecrã de uma política existente aberta num painel separado ](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  Escolha **Definições de política** para abrir o painel **Definições de política**.

3.  Altere as definições e selecione o ícone **Guardar** para guardar as alterações.

    ![Captura de ecrã do painel Definições de política que mostra a opção de menu Guardar na parte superior](../media/AppManagement/AzurePortal_MAM_ChangePolicy_ChangeSettings.png)

## <a name="policy-settings"></a>Definições de política
Para ver uma lista completa das definições de política para iOS e Android, selecione uma das seguintes opções:

> [!div class="op_single_selector"]
- [Políticas para iOS](ios-mam-policy-settings.md)
- [Políticas para Android](android-mam-policy-settings.md)

## <a name="next-steps"></a>Passos seguintes
[Monitorizar o estado do utilizador e de conformidade](monitor-mobile-app-management-policies-with-microsoft-intune.md)

### <a name="see-also"></a>Consulte também
* [O que esperar quando a sua aplicação Android é gerida por políticas de MAM](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [O que esperar quando a sua aplicação iOS é gerida por políticas de MAM](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)



<!--HONumber=Nov16_HO3-->


