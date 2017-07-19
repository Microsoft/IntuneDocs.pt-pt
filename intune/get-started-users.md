---
title: "Introdução aos utilizadores"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fc1c4f6d18fd78f455be8e333bb765080184c908
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/03/2017
---
# <a name="get-started-with-users"></a>Introdução aos utilizadores

![Um utilizador genérico no Azure](/intune/media/generic-intune-user.png)

O Azure AD faz a gestão de grupos de objetos da sua organização, tais como dispositivos e aplicações, mas também de grupos de utilizadores. Pode agrupar utilizadores ou dispositivos em vez de gerir cada dispositivo individualmente. Isto permite-lhe atribuir facilmente aplicações e definições a grandes números de utilizadores e dispositivos.

## <a name="how-do-i-create-a-user"></a>Como posso criar um utilizador?

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Através da opção **Procurar recursos**, procure **Utilizadores e grupos**.
3. Assim que tiver aberto o painel **Utilizadores e grupos**, selecione **Todos os utilizadores** e, em seguida, selecione **+ Novo utilizador**.
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
