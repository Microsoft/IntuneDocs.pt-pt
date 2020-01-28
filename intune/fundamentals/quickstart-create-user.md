---
title: Início Rápido – criar um utilizador no Intune
description: Início Rápido – criar um utilizador no Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.manager: dougeby
ms.assetid: 820fcb18-0927-4ebd-be79-dce92b51c261
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6aa57b71e052e3fc8566fcdff8bdd9ef5d1c39e
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754495"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-the-user-a-license"></a>Quickstart: Criar um utilizador em Intune e atribuir uma licença ao utilizador

Neste arranque rápido, irá criar um utilizador e, em seguida, atribuir ao utilizador uma licença Intune. Quando utiliza o Intune, cada pessoa que deseja ter acesso aos dados da empresa deve ter a sua própria conta de utilizador. Os administradores do Intune podem configurar os usuários posteriormente para gerenciar o controle de acesso.

## <a name="prerequisites"></a>Pré-requisitos

- Uma subscrição do Microsoft Intune. [Inscreva-se para uma conta de teste gratuita.](../fundamentals/free-trial-sign-up.md)

## <a name="sign-in-to-intune-in-microsoft-endpoint-manager"></a>Inscreva-se no Intune no Microsoft Endpoint Manager

Entre no [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) como um [administrador global ou um administrador de serviços do Intune](users-add.md#types-of-administrators). Se criou uma subscrição de teste Intune, a conta com a qual criou a subscrição é o administrador global.

## <a name="create-a-user"></a>Criar um utilizador

Um utilizador deve ter uma conta de utilizador para se inscrever na gestão do dispositivo Intune. Para criar um novo usuário:

1. No Microsoft Endpoint Manager, selecione **Utilizadores** > **Todos os utilizadores** > Novo **utilizador**: ![No Microsoft Endpoint Manager, selecione New user](./media/quickstart-create-user/create-user.png)
2. Na caixa **Nome,** introduza um nome, como *Dewey Kellum*: ![Adicione detalhes do utilizador](./media/quickstart-create-user/create-user-02.png)
3. Na caixa de **nomes do Utilizador,** introduza um identificador de utilizador, como Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Se você não tiver configurado o nome de domínio do cliente, use o nome de domínio verificado usado para criar a assinatura do Intune (ou [avaliação gratuita](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Selecione **Mostrar palavra-passe** e lembre-se da senha gerada automaticamente para que possa iniciar sessão num dispositivo de teste.
5. Selecione **Criar**.

## <a name="assign-a-license-to-the-user"></a>Atribuir uma licença ao utilizador

Depois de ter criado um utilizador, deve utilizar o centro de administração microsoft [365](https://go.microsoft.com/fwlink/p/?LinkId=698854) para atribuir uma licença Intune ao utilizador. Se você não atribuir o usuário a uma licença, ele não poderá registrar seu dispositivo no Intune.

Para atribuir uma licença do Intune a um usuário:

1. Entre no centro de [Administração do Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) com as mesmas credenciais que você usou para entrar no Intune.
2. Selecione **Utilizadores** > **Utilizadores Ativos**e, em seguida, selecione o utilizador que acabou de criar.
3. Selecione o separador **Licenças e Aplicações.**
4. Em **caso de Select localização**, selecione uma localização para o utilizador, se ainda não estiver definida.
2. Selecione a caixa de verificação **Intune** na secção **Licenças.** Se outra licença incluir o Intune, você poderá selecionar essa licença. O nome do [produto](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference) apresentado é usado como plano de serviço na gestão azure.

    ![Selecione o local e a licença do Intune](./media/quickstart-create-user/create-user-03.png)

   > [!NOTE]
   > Esta definição utiliza uma das suas licenças para o utilizador. Se estiver a usar um ambiente experimental, irá posteriormente reatribuir esta licença a um verdadeiro utilizador num ambiente ao vivo.

6. Selecione **guardar alterações**.

O novo usuário do Intune ativo agora mostrará que ele está usando uma licença do **Intune** .

## <a name="clean-up-resources"></a>Limpar recursos

Se já não necessitar deste utilizador, pode eliminar o utilizador indo ao centro de administração da [Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) e selecionando **utilizadores** > *utilizador* > o ícone de *utilizador eliminar* > apagar o **utilizador** > **Fechar**.

   ![Selecione o ícone excluir](./media/quickstart-create-user/create-user-04.png)

## <a name="next-steps"></a>Próximos passos

Neste arranque rápido, criou um utilizador e atribuiu uma licença Intune a esse utilizador. Para obter mais informações sobre como adicionar utilizadores ao Intune, veja [Adicionar utilizadores e conceder permissões administrativas no Intune](users-add.md).

Para continuar esta série de quickstarts Intune, vá para o próximo quickstart:

> [!div class="nextstepaction"]
> [Guia de Início Rápido: criar um grupo para gerir utilizadores](../quickstart-create-group.md)
