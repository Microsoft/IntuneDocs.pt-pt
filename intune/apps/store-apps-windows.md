---
title: Adicionar aplicações da Microsoft Store ao Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre como adicionar aplicações da Microsoft Store (Loja Windows) ao Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8743af2a05f6daebca5e1394ba5b7b8f13fcf7e3
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754920"
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Adicionar aplicações da Microsoft Store ao Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Antes de poder atribuir, monitorizar, configurar ou proteger aplicações, tem de adicioná-las ao Intune. 

## <a name="add-an-app-to-intune"></a>Adicionar uma aplicação ao Intune
Pode adicionar uma aplicação da Microsoft Store ao Intune ao fazer o seguinte:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
3. No painel do **tipo select,** nos tipos de **aplicativos da Loja** disponível, selecione a **aplicação de loja do Windows**.
4. Clique em **Selecionar**. Os passos da **aplicação Add** são apresentados.
5. Para configurar as **informações** da App para aplicações de loja Windows, navegue para a [loja da Microsoft](https://www.microsoft.com/store/apps) e procure a aplicação que pretende implementar. Exiba a página da aplicação e tome nota dos detalhes da aplicação. 
6. Na página de informações da **App,** adicione os detalhes da aplicação:
    - **Nome**: introduza o nome da aplicação tal como deve ser apresentado no portal da empresa. Certifique-se de que utiliza nomes de aplicação que sejam exclusivos. Se um nome de aplicação for duplicado, apenas um deles será apresentado aos utilizadores no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. Esta descrição é apresentada aos utilizadores no portal da empresa.
    - **Publicador**: introduza o nome do publicador da aplicação.
    - **URL da Loja de Aplicações**: escreva o URL da Loja de Aplicações da aplicação que pretende criar. O URL pode ser encontrado pesquisando na [Microsoft Store](https://www.microsoft.com/store/apps) para a aplicação desejada. Utilize o URL da barra de endereços do navegador.
    - **Categoria**: opcionalmente, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Desta forma, permitirá que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Mostre-o como uma aplicação em destaque no Portal da Empresa**: Selecione esta opção para exibir a suite de aplicações em destaque na página principal do portal da empresa quando os utilizadores navegam para apps.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação, por exemplo, *Departamento de RH*.
    - **Notas**: opcionalmente, introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: opcionalmente, carregue um ícone que será associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
7. Clique em **Seguir** para exibir a página **de tags scope.**
8. Clique em **Selecionar etiquetas** de âmbito para adicionar opcionalmente etiquetas de âmbito para a aplicação. Para mais informações, consulte [Utilize o controlo de acesso baseado em funções (RBAC) e as etiquetas](~/fundamentals/scope-tags.md)de âmbito para TI distribuídos .
9. Clique em **Avançar** para exibir a página **atribuições** .
10. Selecione as atribuições de grupo para a aplicação. Para mais informações, consulte [Adicionar grupos para organizar utilizadores e dispositivos](~/fundamentals/groups-add.md). 
11. Clique em **Seguir** para exibir a página **Review + criar.** Reveja os valores e configurações que inseriu para a aplicação.
12. Quando terminar, clique em **Criar** para adicionar a app ao Intune.

A lâmina **de visão geral** da aplicação que criou é exibida.

A aplicação que criou será apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar.

> [!IMPORTANT]
> As aplicações da Microsoft Store só podem ser atribuídas a grupos com o tipo de atribuição **Disponível para dispositivos inscritos** (os utilizadores instalam a aplicação a partir da aplicação ou site do Portal da Empresa).

## <a name="next-steps"></a>Próximos passos
- [Atribuir aplicações a grupos](apps-deploy.md)
