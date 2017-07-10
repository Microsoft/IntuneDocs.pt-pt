---
title: "Acesso da aplicação para o Exchange Online"
description: "Este tópico descreve como pode configurar uma política de acesso condicional para aplicações MAM."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f2cd1a1f-fd29-4081-8dfa-c40993a107d5
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2ef4a0c0e642026d625d7139b2ea2629cdd96930
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="create-an-exchange-online-conditional-access-to-only-allow-apps-supported-by-mam"></a>Criar um acesso condicional do Exchange Online para permitir apenas aplicações suportadas por MAM

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este tópico fornece-lhe instruções passo a passo sobre como configurar o acesso condicional para que o Exchange Online permita apenas aplicações móveis que suportem políticas de proteção da aplicações do Intune.


## <a name="create-an-exchange-online-policy"></a>Criar uma política do Exchange Online
1.  Inicie sessão no [portal do Azure](https://portal.azure.com) que inclui a funcionalidade de acesso da aplicação. Se não estiver familiarizado com a experiência do portal do Azure, leia o tópico [Portal do Azure para políticas de proteção de aplicações](azure-portal-for-microsoft-intune-mam-policies.md).

2.  Selecione **Mais Serviços** e escreva "Intune".

3.  Selecione **Intune App Protection**.

4.  No painel **Gestão de aplicações móveis do Intune**, selecione **Todas as Definições**.

5.  Na secção **Acesso condicional**, selecione **Exchange Online**.

    ![Captura de ecrã do painel de definições a mostrar a secção de acesso condicional com a opção Exchange Online realçada](../media/MAM-conditional-access-1.png)

6. No painel **Aplicações permitidas**, selecione a opção **Permitir aplicações que suportem políticas de aplicação do Intune** para permitir que apenas as aplicações que são suportadas pelas políticas de proteção de aplicações do Intune consigam aceder ao Exchange Online. Quando selecionar esta opção, é apresentada a lista de aplicações suportadas.

    >[!NOTE]
    >Todos os clientes de correio do Exchange Active Sync, incluindo os clientes de correio incorporado em iOS e >Android que se ligam ao Exchange Online ficarão impedidos de enviar ou receber >e-mail. Em alternativa, os utilizadores irão receber um único e-mail a informar que têm de utilizar a aplicação de correio do >Outlook.

7. Para aplicar esta política aos utilizadores, abra o painel **Grupos de utilizadores restritos** e selecione **Adicionar grupo de utilizadores**. Selecione um ou mais grupos de utilizadores que devem receber esta política.

    ![Captura de ecrã do painel de grupos de utilizadores restritos com a opção adicionar grupo de utilizadores realçada](../media/mam-ca-add-user-group.png)

8. Poderá querer que alguns utilizadores do grupo que selecionou no passo anterior não sejam afetados por esta política. Nesses casos, adicione o grupo de utilizadores à lista de grupos de utilizadores excluídos. No painel **Exchange Online**, selecione **Grupos de utilizadores excluídos**. Selecione **Adicionar grupo de utilizadores** para abrir a lista de grupos de utilizadores. Selecione os grupos que pretende excluir desta política.  

## <a name="modify-an-existing-policy"></a>Modificar uma política existente
### <a name="add-or-delete-user-groups"></a>Adicionar ou eliminar grupos de utilizadores

Para **eliminar um grupo de utilizadores**, na lista de **grupos de utilizadores restritos**, abra o painel **Grupos de utilizadores restritos**, selecione o grupo que quer eliminar e clique nas **reticências (...)** para ver a opção **Eliminar**. Selecione **Eliminar** para remover o grupo de utilizadores da lista. Pode seguir o mesmo procedimento para remover um grupo de utilizadores da lista de **grupos de utilizadores excluídos**.


## <a name="next-steps"></a>Passos seguintes
[Bloquear aplicações que não tenham autenticação moderna](block-apps-with-no-modern-authentication.md)
### <a name="see-also"></a>Consulte também
[Proteger os dados da aplicação com políticas de proteção de aplicações](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
