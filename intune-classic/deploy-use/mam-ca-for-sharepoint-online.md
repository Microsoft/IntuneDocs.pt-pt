---
title: "Criar uma política de acesso condicional com base na aplicação para o SharePoint Online"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ms.reviewer: chrisgre
ms.suite: ems
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2d9065281436d4c44e6af7d7a4401786a2a01965
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="set-up-app-based-conditional-access-ca-policies-for-sharepoint-online"></a>Configurar políticas de acesso condicional (AC) com base na aplicação para o SharePoint Online

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Este tópico fornece orientações sobre como configurar a política de acesso condicional com base na aplicação para o SharePoint Online. O AC com base na aplicação ajuda os administradores a permitir apenas as aplicações móveis com políticas de proteção do Intune aplicadas.

## <a name="to-create-the-app-based-ca-policy-for-sharepoint-online"></a>Para criar a política de AC com base na aplicação para o SharePoint Online

1. Aceda ao [portal do Azure](https://portal.azure.com) e inicie sessão com as suas credenciais.

    > [!NOTE]
    > Se não estiver familiarizado com a experiência do Portal do Azure, leia o tópico [Portal do Azure para políticas de proteção de aplicações](azure-portal-for-microsoft-intune-mam-policies.md).

2. Selecione **Mais serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3. Selecione **Intune App Protection** > **Gestão de aplicações móveis do Intune** > **Todas as Definições**.

4. No painel Gestão de aplicações móveis do Intune, selecione o mosaico SharePoint Online.

5. No painel **Aplicações permitidas**, escolha a opção **Permitir aplicações que suportem políticas de aplicação do Intune** para permitir apenas as aplicações que são suportadas pelas políticas de proteção de aplicações do Intune.

    > [!NOTE] 
    > Quando seleciona a opção para permitir apenas as aplicações que são suportadas pelas políticas de proteção da aplicação do Intune, é apresentada **apenas** uma lista de aplicações suportadas.

    ![Captura de ecrã do painel de aplicações permitidas que mostra a lista de aplicações](../media/mam-ca-spo-allowed-apps.png)

## <a name="to-assign-app-based-ca-policies-to-your-users"></a>Para atribuir políticas de AC com base na aplicação aos seus utilizadores

1. Abra o painel **Grupos de utilizadores restritos** e, em seguida, escolha **Adicionar grupo de utilizadores**.

2. Selecione um ou mais grupos de utilizadores que devem receber esta política.

    ![Captura de ecrã do painel de grupos de utilizadores restritos com a opção adicionar grupo de utilizadores realçada](../media/mam-ca-spo-restricted-groups.png)

    > [!IMPORTANT] 
    > Poderá querer que alguns utilizadores do grupo que selecionou no passo anterior não sejam afetados por esta política. Nesses casos, adicione o grupo de utilizadores à lista de grupos de utilizadores excluídos. 

3. No painel **SharePoint Online**, escolha **Grupos de utilizador excluídos** e, em seguida, escolha **Adicionar grupo de utilizadores** para abrir a lista de grupos de utilizadores.

4. Selecione os grupos que pretende excluir desta política.  

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>Para modificar ou eliminar grupos de utilizadores a partir de uma política de AC com base na aplicação existente

1. Abra o painel **Grupos de utilizadores restritos** e, em seguida, realce o grupo de utilizadores que pretende eliminar.
2. Clique na elipse para ver as opções de eliminação.
3. Selecione **Eliminar** para remover o grupo de utilizadores da lista.

> [!NOTE] 
> Pode seguir o procedimento dos passos para remover um grupo de utilizadores da lista de **Grupo de utilizadores excluídos**.

## <a name="next-steps"></a>Próximos passos

[Bloquear aplicações que não utilizam autenticação moderna](block-apps-with-no-modern-authentication.md)

## <a name="see-also"></a>Consulte também

[Proteger os dados da aplicação com políticas de proteção de aplicações](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Configurar o AC com base na aplicação para o Exchange Online](mam-ca-for-exchange-online.md)

