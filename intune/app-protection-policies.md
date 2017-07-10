---
title: "Criar e implementar políticas de proteção de aplicações"
titleSuffix: Intune on Azure
description: "Saiba como as políticas de proteção de aplicações do Intune podem ajudar a proteger os dados da empresa utilizados por aplicações geridas.\""
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 56a19bc4d970f230f719af9369dada45ffb65e76
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Como criar e atribuir políticas de proteção de aplicações

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="before-you-begin"></a>Antes de começar

Se estiver a procurar instruções na consola clássica do Intune, veja [Como criar políticas de proteção de aplicações](https://docs.microsoft.com/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune).

As políticas de proteção de aplicações podem ser aplicadas às aplicações em execução nos dispositivos que podem ou não ser geridos pelo Intune. Para obter uma descrição mais detalhada acerca do funcionamento das políticas de proteção de aplicações e dos cenários suportados pelas políticas de proteção de aplicações do Intune, veja [O que são políticas de proteção de aplicações do Microsoft Intune](app-protection-policy.md).

Se estiver a procurar uma lista de MAM com aplicações suportadas, veja as [Listas de aplicações de MAM](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

##  <a name="create-an-app-protection-policy"></a>Criar uma política de proteção de aplicações
1.  Na carga de trabalho **Aplicações móveis**, escolha **Gerir** > **Políticas de proteção de aplicações**.

2.  É apresentado o painel **Políticas de proteção de aplicações**, onde pode criar novas políticas e editar as já existentes. Selecione **Adicionar uma política**.

  ![Captura de ecrã do painel Adicionar uma política](./media/app-protection-add-policy.png)

3.  Escreva um nome para a política, adicione uma breve descrição e selecione o tipo de plataforma para criar uma política para iOS ou Android. Pode criar mais de uma política para cada plataforma.

4.  Escolha **Aplicações** para abrir o painel **Aplicações** onde é apresentada uma lista de aplicações disponíveis. Selecione uma ou mais aplicações na lista que pretende associar à política que está a criar. Depois de selecionar as aplicações, selecione **Selecionar** na parte inferior do painel **Aplicações** para guardar a sua seleção.

    > [!IMPORTANT]
    > Tem de selecionar pelo menos uma aplicação para criar uma política.

5.  No painel **Adicionar uma política**, escolha **Configurar definições necessárias** para abrir o painel de definições de política.

    Existem duas categorias de definições de política: **Reposicionamento de Dados** e **Acesso**.  As políticas de reposicionamento de dados são aplicáveis ao movimento de dados de e para as aplicações, enquanto que as políticas de acesso determinam a forma como o utilizador final acede às aplicações num contexto profissional.
    Para começar, as definições de política têm valores predefinidos. Não é necessário efetuar quaisquer alterações se os valores predefinidos cumprirem os requisitos.

    > [!TIP]
    > Estas definições de política apenas são impostas quando utilizar aplicações no contexto profissional.  Quando o utilizador final utiliza a aplicação para realizar uma tarefa pessoal, este não será afetado por estas políticas.



6.  Escolha **OK** para guardar esta configuração. Está agora novamente no painel **Adicionar uma política** . Escolha **Criar** para criar a política e guardar as suas definições.


Quando acabar de criar uma política, conforme descrito no procedimento anterior, esta não é implementada para nenhum utilizador. Para implementar uma política, consulte a secção seguinte, "Implementar uma política para utilizadores".

## <a name="deploy-a-policy-to-users"></a>Implementar uma política para utilizadores

1.  No painel **Política**, escolha **Grupos de utilizadores**, que abre o painel **Grupos de utilizadores**. Escolha **Adicionar um grupo de utilizadores** no painel **Grupos de utilizadores** para abrir o painel **Adicionar um grupo de utilizadores**.

  ![Captura de ecrã do painel Grupos de utilizadores com a opção de menu Adicionar um grupo de utilizadores realçada](./media/app-protection-policy-add-users.png)

2.  É apresentada uma lista dos grupos de utilizadores no painel **Adicionar grupo de utilizadores** . Esta é uma lista de todos os grupos de segurança no seu **Azure Active Directory**. Selecione os grupos de utilizadores aos quais pretende aplicar esta política e, em seguida, selecione **Selecionar**. Escolher **Selecionar** implementa a política para os utilizadores.
  ![Captura de ecrã do painel Adicionar um grupo de utilizadores, que mostra a lista de utilizadores do Azure Active Directory](./media/azure-ad-user-group-list.png)

Criou agora uma política e implementou-a a utilizadores.

Apenas os utilizadores com licenças do Microsoft Intune atribuídas são afetados pela política. Os utilizadores que estão no grupo de segurança que selecionou que não têm uma licença do Microsoft Intune atribuída não são afetados.

>[!IMPORTANT]
> Se estiver a utilizar o Intune com o Configuration Manager para gerir os seus dispositivos iOS e Android, a política só é aplicada aos utilizadores diretamente no grupo que selecionou. Os membros dos grupos subordinados aninhados dentro do grupo que selecionou não são afetados.

Os utilizadores finais podem transferir as aplicações a partir da Apple Store ou do Google Play. Para obter mais informações, consulte:
* [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-android.md)
* [O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-ios.md)

##  <a name="change-existing-policies"></a>Alterar políticas existentes
Pode editar uma política existente e aplicá-la aos utilizadores visados. No entanto, quando altera as políticas existentes, os utilizadores que já têm sessão iniciada nas aplicações não verão as alterações durante um período de 8 horas.

Para ver o efeito das alterações imediatamente, o utilizador final terá de terminar sessão na aplicação e voltar a iniciar sessão.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Para alterar a lista de aplicações associadas à política

1.  No painel **Política de aplicação**, escolha a política que pretende alterar. Esta ação abre um painel  específico da política que acabou de selecionar.

2.  No painel da política, escolha **Aplicações alvo** para abrir a lista de aplicações.

3.  Remova ou adicione aplicações a partir da lista e selecione o ícone **Guardar** para guardar as alterações.

### <a name="to-change-the-list-of-user-groups"></a>Para alterar a lista de grupos de utilizadores

1.  No painel **Política de aplicação**, escolha a política que pretende alterar. Esta ação abre o painel específico da política que selecionou.

2.  No painel da política, escolha **Grupos de utilizadores** para abrir o painel **Grupo de utilizadores** que mostra a lista dos grupos de utilizadores atuais que têm esta política.

3.  Para adicionar um novo grupo de utilizadores à política, selecione **Adicionar grupo de utilizadores** e selecione o grupo de utilizadores. Escolha **Selecionar** para implementar a política no grupo que selecionou.

4.  Para eliminar um grupo de utilizadores, realce o grupo de utilizadores que pretende remover. Em seguida, selecione as reticências (…) e **Eliminar** para remover o grupo de utilizadores.
  ![Captura de ecrã que mostra a opção Eliminar ](./media/app-protection-policy-delete-user.png)

### <a name="to-change-policy-settings"></a>Para alterar definições de política

1.  No painel **Política de aplicação**, escolha a política que pretende alterar. Esta ação abre um painel  específico da política que acabou de selecionar.


2.  Escolha **Definições de política** para abrir o painel **Definições de política**.

3.  Altere as definições e selecione o ícone **Guardar** para guardar as alterações.

## <a name="policy-settings"></a>Definições de política
Para ver uma lista completa das definições de política para iOS e Android, selecione uma das seguintes opções:

- [Políticas para iOS](app-protection-policy-settings-ios.md)
- [Políticas para Android](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Passos seguintes
[Monitorizar o estado do utilizador e de conformidade](app-protection-policies-monitor.md)

### <a name="see-also"></a>Consulte também
* [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-android.md)
* [O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-ios.md)
