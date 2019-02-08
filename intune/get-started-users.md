---
title: Introdução à gestão de utilizadores
titlesuffix: Microsoft Intune
description: Adicione um utilizador ao Intune e atribua-lhe uma licença para que possa aceder aos recursos da empresa em dispositivos móveis.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 646a72eaa3837b48b4af718904064fddaeb98955
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55840387"
---
# <a name="get-started-managing-users"></a>Introdução à gestão de utilizadores

Considere todas as pessoas diferentes na sua organização. Cada pessoa que utiliza dados da empresa precisará de um utilizador para gerir o acesso aos mesmos no Intune.

## <a name="how-do-i-create-a-user"></a>Como posso criar um utilizador?

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Após abrir o painel **Microsoft Intune**, selecione **Utilizadores**. Na página **Todos os utilizadores**, selecione **+ Novo utilizador**.
4. Introduza os detalhes do utilizador, como o **Nome** e o **Nome de utilizador**. A parte do nome de domínio do nome de utilizador tem de ser um dos seguintes domínios:
    - o nome de domínio predefinido inicial "contoso.onmicrosoft.com" ou
    - um nome de domínio verificado e não federado, como "contoso.com".
5. Em **Grupos**, selecione [um grupo](get-started-groups.md) ao qual pretende adicionar o utilizador.
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

## <a name="next-steps"></a>Passos Seguintes

[Introdução aos grupos](get-started-groups.md) – organize os utilizadores em grupos para ser mais fácil gerir as políticas e aplicações a que podem aceder.
