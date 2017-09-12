---
title: "Introdução aos utilizadores"
titlesuffix: Azure portal
description: "Adicione um utilizador ao Intune para lhe permitir aceder a recursos da empresa em dispositivos móveis."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a33eb2d5dc96a2647cf2582bbc6cd4ba2d9c0961
ms.sourcegitcommit: fa6aaf12611c3e03e38e467806fc30b1d0255e88
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/12/2017
---
# <a name="get-started-with-managing-users"></a>Introdução à gestão de utilizadores

Considere todas as pessoas diferentes na sua organização. Cada pessoa que utiliza dados da empresa precisará de um utilizador para gerir o acesso aos mesmos no Intune.

## <a name="how-do-i-create-a-user"></a>Como posso criar um utilizador?

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Utilize a opção **Procurar recursos**, procure o **Intune**.
3. Após abrir o painel **Microsoft Intune**, selecione **Utilizadores**. Na página **Todos os utilizadores**, selecione **+ Novo utilizador**.
4. Introduza os detalhes do utilizador, como o **Nome** e o **Nome de utilizador**. A parte do nome de domínio do nome de utilizador tem de ser o nome de domínio inicial predefinido "contoso.onmicrosoft.com" ou um nome de domínio não federado verificado, tal como "contoso.com".
5. Em **Grupos**, selecione o grupo de teste ao qual pretende adicionar o utilizador.
6. Guarde a palavra-passe de utilizador gerada automaticamente para que a possa utilizar para iniciar sessão no dispositivo de teste. Tem de dar esta palavra-passe aos utilizadores para que a possam alterar para uma palavra-passe normal que consigam memorizar.
7. No painel **Utilizador**, selecione **Criar**.

## <a name="assigning-licenses-to-users"></a>Atribuir licenças aos utilizadores

Depois de criar um utilizador, tem de utilizar o [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) para atribuir uma licença do Intune a esse utilizador. Se não lhes atribuir uma licença, os utilizadores não conseguirão inscrever o dispositivo para gestão.

1. Inicie sessão no [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) com as mesmas credenciais que utilizou para iniciar sessão no Intune.
2. Selecione **Utilizadores** > **Utilizadores Ativos** e, em seguida, selecione o utilizador que criou anteriormente.
3. Poderá ter de aguardar alguns momentos para que todas as informações do utilizador carreguem. Depois de carregarem, selecione **Editar** em **Licenças de produtos** do utilizador.
4. Atribua uma **Localização** ao utilizador e, em seguida, **ative** o Intune.

 > [!NOTE]
 > Esta ação utiliza uma das suas licenças para este utilizador. Se estiver a utilizar o seu ambiente em direto, pode desativar esta licença mais tarde para reatribuí-la a um utilizador real.

5. Selecione **Guardar**.

## <a name="next-steps"></a>Próximos passos

[Introdução aos grupos](get-started-groups.md) – organize os utilizadores em grupos para ser mais fácil gerir as políticas e aplicações a que podem aceder.
