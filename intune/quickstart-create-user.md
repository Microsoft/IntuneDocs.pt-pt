---
title: Início Rápido – criar um utilizador no Intune
description: Início Rápido – criar um utilizador no Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/25/2019
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: ed34b8bdd91057e64f72c68166c15b89fa80c187
ms.sourcegitcommit: 9af102e1232d9a568a7901783c30ba9905e64d99
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/26/2019
ms.locfileid: "58477099"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>Início rápido: Criar um utilizador e atribuir uma licença ao mesmo

Neste guia de início rápido, irá criar um utilizador e, em seguida, atribuir uma licença ao mesmo. Ao utilizar o Intune, é necessário que todas as pessoas que pretende que tenham acesso aos dados da empresa tenham uma conta de utilizador. Os administradores do Intune podem configurar posteriormente esses utilizadores para gerirem o controlo de acesso.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto [Administrador global ou um Administrador de Serviços do Intune](users-add.md#types-of-administrators). Se criou uma Subscrição de avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="create-a-user"></a>Criar um utilizador

As pessoas necessitam de ter uma conta de utilizador para se inscreverem na gestão de dispositivos do Intune.

1. No Intune, selecione **Utilizadores** > **Todos os utilizadores** > **Novo utilizador**.
![Browser](media/quickstart-create-user/create-user.png)
2. Na caixa **Nome**, introduza um nome, como *Dewey Kellum*.
3. Na caixa **Nome de utilizador**, introduza um identificador de utilizador, como Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Se ainda não configurou o seu nome de domínio de cliente, utilize o nome de domínio verificado que utilizou para criar a subscrição do Intune (ou a [versão de avaliação gratuita](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Selecione **Mostrar palavra-passe** e tome nota da palavra-passe gerada automaticamente para poder iniciar sessão num dispositivo de teste.
5. Selecione **Criar**.

## <a name="assign-a-license-to-the-user"></a>Atribuir uma licença ao utilizador

Depois de criar um utilizador, tem de utilizar o [Centro de administração do Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) para atribuir uma licença do Intune a esse utilizador. Se não lhe atribuir uma licença, o utilizador não conseguirá inscrever o dispositivo no Intune. 

1. Inicie sessão para o [Centro de administração do Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) com as mesmas credenciais que utilizou para iniciar sessão no Intune.
2. Selecione **Utilizadores** > **Utilizadores Ativos** > selecione o utilizador que acabou de criar.
3. Junto a **Licenças de produtos**, selecione **Editar**.
4. Em **Localização**, selecione uma localização para o utilizador.
5. Clique em **Ativado** junto à licença do Intune (ou a outra licença que inclua o Intune). O [nome do produto](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)** apresentado é utilizado como o plano de serviço na gestão do Azure 

   > [!NOTE]
   > Esta definição utiliza uma das suas licenças para este utilizador. Se estiver a utilizar um ambiente de avaliação, terá de reatribuir posteriormente esta licença a um utilizador real num ambiente em direto.
6. Selecione **Guardar** > **Fechar**.

O novo utilizador ativo do Intune mostrará que está a utilizar uma licença do **Intune**.

## <a name="clean-up-resources"></a>Limpar recursos

Se não precisa mais este utilizador, pode eliminar o utilizador ao navegar para o [Centro de administração do Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) e escolha **utilizadores** > **utilizadores ativos**  >  *escolha o utilizador na lista* > **eliminação do utilizador** > **eliminação do utilizador** > **confirmar as alterações** > **fechar**.

## <a name="next-steps"></a>Passos Seguintes

Neste guia de início rápido, criou um utilizador e atribuiu uma licença ao mesmo. Para obter mais informações sobre como adicionar utilizadores ao Intune, veja [Adicionar utilizadores e conceder permissões administrativas no Intune](users-add.md).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Início rápido: Criar um grupo para gerir utilizadores](quickstart-create-group.md)
