---
title: "Configurar o acesso da aplicação para o SharePoint Online"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 992273f88e4bbe234f11f936d6416dbaf0d394e9
ms.lasthandoff: 04/19/2017


---

# <a name="create-a-sharepoint-online-conditional-access-policy-to-only-allow-apps-supported-by-mam"></a>Criar uma política de acesso condicional do SharePoint Online para permitir apenas aplicações suportadas pela MAM
Este tópico fornece-lhe as instruções passo a passo sobre como configurar o acesso condicional para que o Exchange Online permita apenas aplicações móveis que suportem políticas de gestão de aplicações móveis (MAM) do Intune.

## <a name="configure-a-sharepoint-online-policy"></a>Configurar uma política do SharePoint Online
**Passo 1:** inicie sessão no [portal do Azure](https://portal.azure.com) que inclui a funcionalidade de acesso da aplicação. Caso não esteja familiarizado com a experiência do portal do Azure, leia o tópico [Portal do Azure para políticas de MAM](azure-portal-for-microsoft-intune-mam-policies.md).

**Passo 2:** aceda a **Procurar > Intune > Painel de gestão de aplicações móveis do Intune > Definições** e, na secção **acesso condicional**, escolha **SharePoint Online**.

![Captura de ecrã do painel de definições que mostra a secção de acesso condicional e o painel do SharePoint Online aberto](../media/mam-ca-settings-spo.png)

**Passo 3:** no painel **Aplicações permitidas**, escolha **Permitir aplicações que suportam políticas de aplicação do Intune** para permitir que apenas as aplicações que são suportadas pelas políticas da MAM do Intune consigam aceder ao SharePoint Online. Quando seleciona a opção para permitir apenas as aplicações que são suportadas pelas políticas da MAM do Intune, é apresentada a lista de aplicações suportadas.

![Captura de ecrã do painel de aplicações permitidas que mostra a lista de aplicações](../media/mam-ca-spo-allowed-apps.png)

**Passo 4:** para aplicar esta política aos utilizadores, abra o painel **Grupos de utilizadores restritos** e escolha **Adicionar grupo de utilizadores**. Selecione um ou mais grupos de utilizadores que devem receber esta política.

![Captura de ecrã do painel de grupos de utilizadores restritos com a opção adicionar grupo de utilizadores realçada](../media/mam-ca-spo-restricted-groups.png)


**Passo 5:** poderá querer que alguns utilizadores no grupo de utilizadores que selecionou no passo anterior não sejam afetados por esta política. Nesses casos, adicione o grupo de utilizadores à lista de grupos de utilizadores excluídos. No painel **SharePoint Online**, selecione **Grupos de utilizadores excluídos**. Selecione **Adicionar grupo de utilizadores** para abrir a lista de grupos de utilizadores. Selecione os grupos que pretende excluir desta política.  

## <a name="modifying-an-existing-policy"></a>Modificar uma política existente
### <a name="adding-or-deleting-user-groups"></a>Adicionar ou eliminar grupos de utilizadores
Para **eliminar um grupo de utilizadores** da lista de **grupos de utilizadores restritos**, abra o painel Grupos de utilizadores restritos, selecione o grupo de utilizadores que quer eliminar e clique em … para ver a opção de eliminação. Selecione **Eliminar** para remover o grupo de utilizadores da lista. Pode seguir o mesmo procedimento para remover um grupo de utilizadores da lista de **grupos de utilizadores excluídos**.


## <a name="next-steps"></a>Próximos passos
[Configurar o acesso da aplicação para o Exchange Online](mam-ca-for-exchange-online.md)

[Bloquear aplicações que não tenham autenticação moderna](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Consulte também

[Proteger dados de aplicações com políticas de MAM](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

