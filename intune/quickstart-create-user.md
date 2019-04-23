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
ms.openlocfilehash: b49595493b5db3e5735e0a4717c27e91f058b8d8
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61511378"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-them-a-license"></a>Início rápido: Criar um utilizador no Intune e atribuir-lhes uma licença

Neste início rápido, irá criar um utilizador e, em seguida, atribuir-lhes do Intune. Quando utilizar o Intune, cada pessoa que pretende ter acesso aos dados da empresa tem de ter sua própria conta de utilizador. Os administradores do Intune podem configurar os utilizadores mais tarde para gerir o controlo de acesso.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://aka.ms/intuneportal) como um [Administrador Global ou um administrador de serviço do Intune](users-add.md#types-of-administrators). Se criou uma Subscrição de avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="create-a-user"></a>Criar um utilizador

Os utilizadores tem de ter uma conta de utilizador para se inscrever na gestão de dispositivos do Intune. Para criar um novo utilizador:

1. No Intune, selecione **Utilizadores** > **Todos os utilizadores** > **Novo utilizador**.
![Browser](media/quickstart-create-user/create-user.png)
2. Na caixa **Nome**, introduza um nome, como *Dewey Kellum*.
3. Na caixa **Nome de utilizador**, introduza um identificador de utilizador, como Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Se ainda não configurou o seu nome de domínio do cliente, utilize o nome de domínio verificado que utilizou para criar a subscrição do Intune (ou [avaliação gratuita](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Selecione **Mostrar palavra-passe** e tome nota da palavra-passe gerada automaticamente para poder iniciar sessão num dispositivo de teste.
5. Selecione **Criar**.

## <a name="assign-a-license-to-the-user"></a>Atribuir uma licença ao utilizador

Depois de criar um utilizador, tem de utilizar o [Centro de administração do Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) para atribuir-lhes uma licença do Intune. Se não atribuir ao utilizador uma licença, conseguirão inscrever o dispositivo no Intune. 

Para atribuir uma licença do Intune a um utilizador:

1. Inicie sessão para o [Centro de administração do Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) com as mesmas credenciais que utilizou para iniciar sessão no Intune.
2. Escolher **usuários** > **utilizadores ativos** > e selecione o utilizador que acabou de criar.
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

Neste início rápido, criou um utilizador e atribuída uma licença do Intune. Para obter mais informações sobre como adicionar utilizadores ao Intune, veja [Adicionar utilizadores e conceder permissões administrativas no Intune](users-add.md).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Início rápido: Criar um grupo para gerir utilizadores](quickstart-create-group.md)
