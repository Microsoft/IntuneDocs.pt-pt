---
title: Início Rápido – criar um utilizador no Intune
description: Início Rápido – criar um utilizador no Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/25/2019
ms.author: erikje
ms.manager: dougeby
ms.assetid: 820fcb18-0927-4ebd-be79-dce92b51c261
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 75a875fc3ff11eb1e3befad425c16a710544f781
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72509876"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-them-a-license"></a>Início rápido: criar um usuário no Intune e atribuir a eles uma licença

Neste guia de início rápido, você criará um usuário e atribuirá a eles uma licença do Intune. Ao usar o Intune, cada pessoa que você deseja ter acesso aos dados da empresa deve ter sua própria conta de usuário. Os administradores do Intune podem configurar os usuários posteriormente para gerenciar o controle de acesso.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Entre no [Intune](https://aka.ms/intuneportal) como um [administrador global ou um administrador de serviços do Intune](users-add.md#types-of-administrators). Se você tiver criado uma assinatura de avaliação do Intune, a conta com a qual você criou a assinatura será o administrador global.

## <a name="create-a-user"></a>Criar um utilizador

Os usuários devem ter uma conta de usuário para se registrarem no gerenciamento de dispositivos do Intune. Para criar um novo usuário:

1. No Intune, selecione **Utilizadores** > **Todos os utilizadores** > **Novo utilizador**.
![Browser](./media/quickstart-create-user/create-user.png)
2. Na caixa **Nome**, introduza um nome, como *Dewey Kellum*.
3. Na caixa **Nome de utilizador**, introduza um identificador de utilizador, como Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Se você não tiver configurado o nome de domínio do cliente, use o nome de domínio verificado usado para criar a assinatura do Intune (ou [avaliação gratuita](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Selecione **Mostrar palavra-passe** e tome nota da palavra-passe gerada automaticamente para poder iniciar sessão num dispositivo de teste.
5. Selecione **Criar**.

## <a name="assign-a-license-to-the-user"></a>Atribuir uma licença ao utilizador

Depois de criar um usuário, você deve usar o [centro de administração Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) para atribuir uma licença do Intune a eles. Se você não atribuir o usuário a uma licença, ele não poderá registrar seu dispositivo no Intune. 

Para atribuir uma licença do Intune a um usuário:

1. Entre no centro de [Administração do Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) com as mesmas credenciais que você usou para entrar no Intune.
2. Escolha **usuários** > **usuários ativos** > e escolha o usuário que você acabou de criar.
3. Junto a **Licenças de produtos**, selecione **Editar**.
4. Em **Localização**, selecione uma localização para o utilizador.
5. Clique **em** próximo à licença do Intune (ou outra licença que você tenha, que inclui o Intune). O [nome do produto](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)** apresentado é utilizado como o plano de serviço na gestão do Azure 

   > [!NOTE]
   > Esta definição utiliza uma das suas licenças para este utilizador. Se estiver a utilizar um ambiente de avaliação, terá de reatribuir posteriormente esta licença a um utilizador real num ambiente em direto.
6. Selecione **Guardar** > **Fechar**.

O novo usuário do Intune ativo agora mostrará que ele está usando uma licença do **Intune** .

## <a name="clean-up-resources"></a>Limpar recursos

Se você não precisar mais desse usuário, poderá excluir o usuário navegando até a [Microsoft 365 centro de administração](http://go.microsoft.com/fwlink/p/?LinkId=698854) e escolhendo **usuários** > **usuários ativos** > *escolher o usuário na lista* > **excluir usuário** > **excluir usuário** > **confirmar alterações** > **fechar**.

## <a name="next-steps"></a>Próximos passos

Neste guia de início rápido, você criou um usuário e atribuiu uma licença do Intune a ele. Para obter mais informações sobre como adicionar utilizadores ao Intune, veja [Adicionar utilizadores e conceder permissões administrativas no Intune](users-add.md).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Guia de Início Rápido: criar um grupo para gerir utilizadores](../quickstart-create-group.md)
