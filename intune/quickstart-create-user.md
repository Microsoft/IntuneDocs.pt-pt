---
title: Início Rápido – criar um utilizador no Intune
description: Início Rápido – criar um utilizador no Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 6a1d591e635dccd99551d9b8d40e099724a85d77
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581807"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>Início Rápido: criar um utilizador e atribuir uma licença ao mesmo

Neste início rápido, vai criar um utilizador e, em seguida, atribuir uma licença ao mesmo. Ao utilizar o Intune, é necessário que todas as pessoas que pretende que tenham acesso aos dados da empresa tenham uma conta de utilizador. Os administradores do Intune podem, em seguida, configurar esses utilizadores para gerirem o controlo de acesso.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto Administrador Global ou Administrador de Serviços do Intune.

## <a name="create-a-user"></a>Criar um utilizador

As pessoas necessitam de ter uma conta de utilizador para se inscreverem na gestão de dispositivos do Intune.

1. No Intune, selecione **Utilizadores** > **Todos os utilizadores** > **Novo utilizador**.
![Browser](media/quickstart-create-user/create-user.png)
2. Na caixa **Nome**, introduza *Dewey Kellum*.
3. Na caixa **Nome de utilizador**, introduza *Dewey@contoso.onmicrosoft.com*.
4. Selecione **Grupos** > **Todos** > **Selecionar**.
5. Selecione **Mostrar palavra-passe** e tome nota da palavra-passe gerada automaticamente para poder iniciar sessão num dispositivo de teste.
6. Selecione **Criar**.

## <a name="assign-a-license-to-the-user"></a>Atribuir uma licença ao utilizador

Depois de criar um utilizador, tem de utilizar o [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) para atribuir uma licença do Intune a esse utilizador. Se não lhe atribuir uma licença, o utilizador não conseguirá inscrever o dispositivo no Intune. 

1. Inicie sessão no [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) com as mesmas credenciais que utilizou para iniciar sessão no Intune.
2. Selecione **Utilizadores** > **Utilizadores Ativos** > selecione o utilizador que acabou de criar.
3. Em **Localização**, selecione uma localização para o utilizador.
3. Selecione **Licenças de produtos** e defina **Enterprise Mobility + Security E3** (ou outra licença que tiver que contenha o Intune) para **Ativado**.
   > [!NOTE]
   > Esta ação utiliza uma das suas licenças para este utilizador. Se estiver a utilizar o seu ambiente em direto, pode desativar esta licença mais tarde para reatribuí-la a um utilizador real.
5. Escolha **Guardar**.

## <a name="clean-up-resources"></a>Limpar recursos

Se não precisar mais este utilizador, pode eliminá-lo ao selecionar **Utilizadores** > **Todos os utilizadores** > selecione o utilizador na lista > **Eliminar utilizador** > **Sim**.

## <a name="next-steps"></a>Próximos passos

Neste início rápido, criou um utilizador e atribuiu uma licença ao mesmo. Agora pode atribuir esse utilizador a um grupo.

> [!div class="nextstepaction"]
> [Criar um grupo](quickstart-create-group.md)
