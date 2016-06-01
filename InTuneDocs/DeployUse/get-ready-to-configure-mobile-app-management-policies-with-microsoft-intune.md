---
# required metadata

title: Configurar políticas de gestão de aplicações móveis | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configurar políticas de gestão de aplicações móveis com o Microsoft Intune
Este tópico descreve o que necessita antes de poder criar políticas de gestão de aplicações móveis (MAM) no portal do Azure.
Se estiver a utilizar atualmente a **consola de administração do Intune** para gerir os seus dispositivos, pode criar uma política de MAM que suporte aplicações para dispositivos inscritos no Intune, utilizando a [consola de administração do Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)
>[!IMPORTANT]
> Poderá não ver todas as definições de política de MAM na consola de administração do Intune. O portal do Azure é a nova consola de administração para a criação de políticas de MAM.

##  Plataformas suportadas
- iOS 8.1 ou posterior

- Android 4 ou posterior

##  Aplicações suportadas
Para ver a lista completa de aplicações suportadas, aceda à [Galeria de aplicações móveis do Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) na página de parceiros de aplicações do Microsoft Intune.
Clique na aplicação para ver os cenários suportados, as plataformas e se pretende ou não que a aplicação suporte várias identidades.

**Antes** de poder configurar políticas de MAM, precisará do seguinte:

-   **Uma subscrição do Microsoft Intune**.    Os utilizadores finais necessitam de licenças do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para obter aplicações com a política de MAM.

-   A **autoridade de gestão de dispositivos móveis** tem de ser definida para o **Intune** ou o **Configuration Manager**, dependendo se está a utilizar apenas o Intune ou o Configuration Manager integrado no Intune para gerir os seus dispositivos. Se estiver a utilizar a gestão de dispositivos móveis incorporada do O365, tem de comprar uma subscrição do Intune e [definir a autoridade de gestão de dispositivos móveis para o Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)
-   Uma subscrição do **Office 365 (O365)** necessária para o seguinte:
  - Aplicar políticas de MAM a aplicações com suporte de várias identidades.
  - Criar contas profissionais do SharePoint Online e do Exchange Online. O Exchange no local e o SharePoint no local não são suportados.


- **Azure Active Directory (Azure AD)** para criar utilizadores. O Azure AD autentica o utilizador quando o utilizador final inicia a aplicação e introduz as respetivas credenciais de trabalho.

    > Se estiver a configurar utilizadores com a consola do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] , tenha em atenção que a configuração da política de MAM passa a ser efetuada no portal do Azure e, para utilizar este portal, tem de configurar grupos de utilizadores do Azure AD através do portal do Office 365.


## Criar utilizadores e atribuir licenças do Microsoft Intune

1. Precisa de uma subscrição: já tem uma subscrição do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] se estiver a utilizar atualmente o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para gerir os dispositivos.  Tem também uma subscrição do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] se tiver adquirido uma licença do EMS. Se estiver a tentar que o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] consulte as capacidades do MAM, pode obter uma conta de avaliação [aqui](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/)

    Para verificar se tem uma subscrição do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] , no portal do Office, aceda à página de Faturação.  Deverá ver [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] como **Ativo** nas subscrições.

2.  Inicie sessão no   [portal do Office](http://portal.office.com) com as suas credenciais de administrador.

3.  Navegue para a página **Utilizadores Ativos** para adicionar utilizadores e atribuir licenças do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

    ![Página para adicionar utilizadores do Portal do Office](../media/AppManagement/OfficePortal_AddUsers.png)

4.  Para permitir a um utilizador aceder ao portal do Office, portal do Azure AD e portal do Azure, atribua a **função de administrador global** ao utilizador.

    ![Captura de ecrã do portal do Office que mostra a página Utilizadores Ativos ](../media/AppManagement/OfficePortal_AddRoletoUser.png)

5.  As políticas de MAM são implementadas em grupos de utilizadores no Azure Active Directory. Para criar grupos de utilizadores que pretende utilizar para as políticas de MAM, navegue para a página **Grupos** no **portal do Office** e clique no ícone **+** para criar um novo grupo de segurança.  Escreva um nome e uma descrição e clique em **Criar**. Quando o grupo for criado, pode adicionar utilizadores ao grupo clicando em **Editar membros** no grupo de segurança criado recentemente. O grupo de segurança é criado no Azure Active Directory.

    ![Captura de ecrã da página que mostra a seleção da função Administrador global na página Editar funções de utilizador](../media/AppManagement/OfficePortal_CreateGroups.png)

A tabela seguinte lista as funções e as permissões que pode atribuir aos utilizadores de administração.

|||
|--|----|
|**Função**|**Permissões**|
|Administrador global (portal do O365)|Acesso ao portal do O365 e portal do Azure AD<br /><br />Acesso ao portal do Azure (pode efetuar tarefas de gestão de funções e de aplicações móveis).|
|Função de proprietário (portal do Azure)|Acesso ao portal do Azure (pode efetuar tarefas de gestão de funções e de aplicações móveis).|
|Função de contribuidor (portal do Azure)|Acesso ao portal do Azure (apenas pode efetuar tarefas de gestão de aplicações móveis).|

## Atribuir a função de contribuinte a um utilizador

Os**administradores globais** têm acesso ao portal do Azure.  Se pretender que outros utilizadores de administração possam configurar políticas e efetuar outras tarefas de gestão de aplicações móveis, pode atribuir a **função de contribuinte** ao utilizador conforme descrito abaixo:


1.  No painel **Definições**, na secção **Gestão de recursos**, clique em **Utilizadores**

    ![Captura de ecrã do painel Utilizadores no portal do Azure](../media/AppManagement/AzurePortal_MAM_AddUsers.png)

2.  Clique em **Adicionar** para abrir o painel **Adicionar acesso** .

3.  Clique em **Selecionar uma função** e, em seguida, em **Função de contribuinte**

    ![Captura de ecrã do painel Selecionar no portal do Azure](../media/AppManagement/AzurePortal_MAM_AddRole.png)

4.  Assim que tiver selecionado a função, clique em **Adicionar utilizador**e procure o utilizador por nome de utilizador ou endereço de e-mail. Os utilizadores que vê nesta lista são os primeiros 1000 utilizadores que criou anteriormente no Azure AD através do portal do Office. Clique em **OK** no painel **Adicionar acesso** para guardar e atribuir a função ao utilizador.

    ![Captura de ecrã do painel Adicionar no portal do Azure](../media/AppManagement/AzurePortal_MAM_AddusertoRole.png)

    > Se selecionar um utilizador que não tenha uma licença do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] atribuída, este não poderá aceder ao portal.

## Passos seguintes
[Criar e implementar políticas de gestão de aplicações móveis com o Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


