---
title: "Política de acesso condicional com base na aplicação com o Intune"
description: "Este tópico descreve como pode configurar uma política de acesso condicional com base na aplicação com o Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 88db3730be62a9b481d924b4f09b70be775cb067
ms.sourcegitcommit: 4dc5bed94cc965a54eacac2d87fb2d49c9300c3a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2017
---
# <a name="set-up-app-based-conditional-access-policies"></a>Configurar políticas de acesso condicional com base nas aplicações

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este tópico fornece instruções sobre como configurar políticas de acesso condicional baseado na aplicação, para aplicações que fazem parte da lista de aplicações aprovadas. A lista de aplicações aprovadas consiste em aplicações que foram testadas pela Microsoft.

> [!IMPORTANT]
> Este tópico explica os passos para adicionar uma política de acesso condicional baseado na aplicação com o Exchange Online, mas pode utilizar os mesmos passos ao adicionar outras aplicações, como o SharePoint Online, Microsoft Teams, entre outras da lista de aplicações aprovadas.

## <a name="to-create-an-app-based-conditional-access-policy"></a>Para criar uma política de acesso condicional com base na aplicação
1.  Aceda ao [portal do Azure](https://portal.azure.com) e inicie sessão com as suas credenciais.

2.  Selecione **Mais Serviços** e escreva "Intune".

3.  Selecione **Intune App Protection**.

4.  No painel **Gestão de aplicações móveis do Intune**, selecione **Todas as Definições**.

5.  Na secção **Acesso condicional**, selecione **Exchange Online**.

    ![Captura de ecrã do painel de definições a mostrar a secção de acesso condicional com a opção Exchange Online realçada](./media/MAM-conditional-access-1.png)

6. No painel **Aplicações permitidas**, selecione a opção **Permitir aplicações que suportem políticas de aplicação do Intune** para permitir que apenas as aplicações que são suportadas pelas políticas de proteção de aplicações do Intune consigam aceder ao Exchange Online. Quando selecionar esta opção, é apresentada a lista de aplicações suportadas.

    > [!NOTE]
    > Todos os clientes de correio do Exchange Active Sync, incluindo os clientes de correio incorporado em iOS e Android que se ligam ao Exchange Online ficarão impedidos de enviar ou receber e-mail. Em alternativa, os utilizadores irão receber um único e-mail a informar que têm de utilizar a aplicação de correio do Outlook.

7. Para aplicar esta política aos utilizadores, abra o painel **Grupos de utilizadores restritos** e selecione **Adicionar grupo de utilizadores**. Selecione um ou mais grupos de utilizadores que devem receber esta política.

    ![Captura de ecrã do painel de grupos de utilizadores restritos com a opção adicionar grupo de utilizadores realçada](./media/mam-ca-add-user-group.png)

8. Poderá querer que alguns utilizadores do grupo que selecionou no passo anterior não sejam afetados por esta política. Nesses casos, adicione o grupo de utilizadores à lista de grupos de utilizadores excluídos. No painel **Exchange Online**, selecione **Grupos de utilizadores excluídos**. Selecione **Adicionar grupo de utilizadores** para abrir a lista de grupos de utilizadores. Selecione os grupos que pretende excluir desta política.

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>Para modificar ou eliminar grupos de utilizadores a partir de uma política de AC com base na aplicação existente

1. Abra o painel **Grupos de utilizadores restritos** e, em seguida, realce o grupo de utilizadores que pretende eliminar.
2. Clique na elipse para ver as opções de eliminação.
3. Selecione **Eliminar** para remover o grupo de utilizadores da lista.

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>Criar políticas de acesso condicional com base nas aplicações na carga de trabalho do Azure AD

A partir da versão 1708 do Intune, os administradores de TI podem criar políticas de acesso condicional com base nas aplicações a partir da carga de trabalho do Azure AD. Isto é útil, uma vez que assim não precisa de alternar entre as cargas de trabalho do Azure e o Intune.

> [!IMPORTANT]
> Tem de ter uma licença do Azure AD Premium para criar políticas de acesso condicional do Azure AD a partir do Intune no portal do Azure.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Para criar uma política de acesso condicional com base na aplicação

> [!IMPORTANT]
> Tem de aplicar [políticas de proteção de aplicações do Intune](app-protection-policies.md) às suas aplicações antes de utilizar as políticas de acesso condicional com base nas aplicações.

1. No **Dashboard do Intune**, escolha **Acesso condicional**.

2. No painel **Políticas**, selecione **Nova política** para criar a sua nova política de acesso condicional com base na aplicação.

4. Após introduzir um nome da política e configurar as definições disponíveis na secção **Atribuições**, selecione **Conceder** na secção **Controlos de acesso**.

5. Selecione **Pedir aplicação aprovada do cliente** , selecione **Selecionar** e, em seguida, selecione **OK** para guardar a nova política.

## <a name="next-steps"></a>Próximos passos
[Bloquear aplicações que não tenham autenticação moderna](app-modern-authentication-block.md)

### <a name="see-also"></a>Consulte também

[Proteger os dados da aplicação com políticas de proteção de aplicações](app-protection-policies.md)
[Acesso Condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
