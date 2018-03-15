---
title: "Criar e implementar políticas de proteção de aplicações"
titleSuffix: Microsoft Intune
description: "Saiba como criar e atribuir políticas de proteção de aplicações do Microsoft Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c7ad60a27e32aaab49e77789364aecdc5ea7fc60
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Como criar e atribuir políticas de proteção de aplicações

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Saiba como criar e atribuir políticas de proteção de aplicações do Microsoft Intune aos seus utilizadores. Este tópico também descreve como fazer alterações a políticas existentes.

## <a name="before-you-begin"></a>Antes de começar

Se estiver a procurar instruções no portal clássico do Intune, veja [Como criar políticas de proteção de aplicações](https://docs.microsoft.com/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune).

As políticas de proteção de aplicações podem ser aplicadas às aplicações em execução nos dispositivos que podem ou não ser geridos pelo Intune. Para obter uma descrição mais detalhada acerca do funcionamento das políticas de proteção de aplicações e dos cenários suportados pelas políticas de proteção de aplicações do Intune, veja [O que são políticas de proteção de aplicações do Microsoft Intune](app-protection-policy.md).

Se estiver a procurar uma lista de MAM com aplicações suportadas, veja as [Listas de aplicações de MAM](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

##  <a name="create-an-app-protection-policy"></a>Criar uma política de proteção de aplicações
1.  Na carga de trabalho **Aplicações móveis**, selecione **Políticas de proteção de aplicações** na secção **Gerir**. Esta seleção abre o painel **Políticas de proteção de aplicações**, onde pode criar novas políticas e editar as já existentes.
2. Selecione **Adicionar uma política**.

  ![Captura de ecrã do painel "Adicionar uma política"](./media/app-protection-add-policy.png)

3.  Escreva um nome para a política, adicione uma pequena descrição e selecione o tipo de plataforma para a sua política. Se for necessário, pode criar mais de uma política para cada plataforma.

4.  Selecione **Aplicações** para abrir o painel **Aplicações**, onde é apresentada uma lista de aplicações disponíveis. Selecione uma ou mais aplicações na lista que pretende associar à política que está a criar.
5. Após escolher as aplicações, selecione a opção **Selecionar** para guardar a sua seleção.

    > [!IMPORTANT]
    > Tem de selecionar pelo menos uma aplicação para criar uma política.

6.  Selecione **Configurar definições obrigatórias** no painel **Adicionar uma política** para abrir as **Definições**.

    Existem duas categorias de definições de política: **Reposicionamento de Dados** e **Acesso**.  As políticas de reposicionamento de dados são aplicáveis à entrada e saída de dados das aplicações. As políticas de acesso determinam a forma como o utilizador final acede às aplicações num contexto de trabalho.
    Para começar, as definições de política têm valores predefinidos. Se os valores predefinidos cumprirem os seus requisitos, não precisa de fazer alterações.

    > [!TIP]
    > Estas definições de política apenas são impostas quando utilizar aplicações no contexto profissional. Quando os utilizadores finais utilizam a aplicação para realizar uma tarefa pessoal, estes não são afetados por estas políticas.

7.  Escolha **OK** para guardar esta configuração. Está agora novamente no painel **Adicionar uma política**. Escolha **Criar** para criar a política e guardar as suas definições.
8. Escolha **OK** para guardar esta configuração. Está agora novamente no painel **Adicionar uma política**.
9. Escolha **Criar** para criar a política e guardar as suas definições.

Quando acabar de criar uma política, conforme descrito no procedimento anterior, esta não é implementada para nenhum utilizador. Para implementar uma política, veja a secção [Implementar uma política para utilizadores](app-protection-policies.md#deploy-a-policy-to-users).

## <a name="deploy-a-policy-to-users"></a>Implementar uma política para utilizadores


1. No painel **Políticas de proteção de aplicações**, selecione uma política.

1. No painel **Política**, selecione a opção **Atribuições**, que irá abrir o painel **Proteção de Aplicações do Intune – Atribuições**. Selecione **Selecionar grupos para incluir** no painel **Atribuições** para abrir o painel **Selecionar grupos para incluir**.

   ![Captura de ecrã do painel Atribuições, com a opção do menu Selecionar grupos para incluir realçada](./media/app-protection-policy-add-users.png)

2.  É apresentada uma lista dos grupos de utilizadores no painel **Adicionar grupo de utilizadores**. Esta lista mostra todos os grupos de segurança no seu **Azure Active Directory**. Selecione os grupos de utilizadores aos quais pretende aplicar esta política e, em seguida, selecione **Selecionar**. Escolher **Selecionar** implementa a política para os utilizadores.

    ![Captura de ecrã do painel Adicionar um grupo de utilizadores a mostrar a lista de utilizadores do Azure Active Directory](./media/azure-ad-user-group-list.png)

Acabou de criar uma política e de a implementar para os utilizadores.

Apenas os utilizadores a que foram atribuídas licenças do Microsoft Intune são afetados pela política. Os utilizadores no grupo de segurança selecionado a quem não foi atribuída uma licença do Intune não são afetados.

>[!IMPORTANT]
> Se estiver a utilizar o Intune com o Configuration Manager para gerir os seus dispositivos, a política só é aplicada aos utilizadores diretamente no grupo que selecionou. Os membros dos grupos subordinados aninhados dentro do grupo que selecionou não são afetados.

Os utilizadores finais podem transferir as aplicações a partir da Apple Store ou do Google Play. Para obter mais informações, consulte:
* [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-android.md)
* [O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-ios.md)

##  <a name="change-existing-policies"></a>Alterar políticas existentes
Pode editar uma política existente e aplicá-la aos utilizadores visados. No entanto, quando altera as políticas existentes, os utilizadores que já têm sessão iniciada nas aplicações não verão as alterações durante um período de 8 horas.

Para ver o efeito das alterações imediatamente, o utilizador final tem de terminar sessão na aplicação e voltar a iniciar sessão.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Para alterar a lista de aplicações associadas à política

1.  No painel **Políticas de proteção de aplicações**, selecione a política que pretende alterar para abrir um painel específico à política que acabou de selecionar.

2.  No painel da política, selecione **Aplicações alvo** para abrir a lista de aplicações.

3.  Remova ou adicione aplicações a partir da lista e selecione o ícone **Guardar** para guardar as alterações.

### <a name="to-change-the-list-of-user-groups"></a>Para alterar a lista de grupos de utilizadores


1.  No painel **Políticas de proteção de aplicações**, selecione a política que pretende alterar para abrir o painel específico à política que selecionou.

2.  No painel de políticas, selecione **Atribuições** para abrir o painel **Proteção de Aplicações do Intune – Atribuições**, que mostra a lista dos grupos de utilizadores que atualmente têm esta política.

3.  Para adicionar um novo grupo de utilizadores à política, no separador **Incluir**, selecione **Selecionar grupos para incluir** e selecione o grupo de utilizadores. Escolha **Selecionar** para implementar a política no grupo que selecionou.

4.  Para eliminar um grupo de utilizadores, no separador **Excluir**, selecione **Selecionar grupos para excluir** e selecione o grupo de utilizadores. Selecione a opção **Selecionar** para remover o grupo de utilizadores.

### <a name="to-change-policy-settings"></a>Para alterar definições de política

1.  No painel **Políticas de proteção de aplicações**, selecione a política que pretende alterar para abrir um painel específico à política que acabou de selecionar.

2.  Selecione **Definições da política** para abrir o painel **Definições da política**.

3.  Altere as definições e selecione o ícone **Guardar** para guardar as alterações.

## <a name="policy-settings"></a>Definições de política
Para ver uma lista completa das definições de política para iOS e Android, selecione uma das seguintes ligações:

- [Políticas para iOS](app-protection-policy-settings-ios.md)
- [Políticas para Android](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Próximos passos
[Monitorizar o estado do utilizador e de conformidade](app-protection-policies-monitor.md)

### <a name="see-also"></a>Consulte também
* [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-android.md)
* [O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-ios.md)
