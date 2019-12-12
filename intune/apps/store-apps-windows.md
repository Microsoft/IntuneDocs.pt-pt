---
title: Adicionar aplicações da Microsoft Store ao Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre como adicionar aplicações da Microsoft Store (Loja Windows) ao Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: 3c13d7960c0bb5c73908a0a574ab7d6c169d6460
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74563426"
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Adicionar aplicações da Microsoft Store ao Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Antes de poder atribuir, monitorizar, configurar ou proteger aplicações, tem de adicioná-las ao Intune. 

## <a name="add-an-app-to-intune"></a>Adicionar uma aplicação ao Intune
Pode adicionar uma aplicação da Microsoft Store ao Intune ao fazer o seguinte:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
3. No painel **Adicionar aplicação**, selecione um **Tipo de aplicação** do **Windows** e, em seguida, selecione **Informações da aplicação**.
4. No painel **Informações da aplicação**, adicione as informações da aplicação. Consoante a aplicação que tenha selecionado, alguns dos valores neste painel podem ter sido preenchidos automaticamente:
    - **Nome**: introduza o nome da aplicação tal como deve ser apresentado no portal da empresa. Certifique-se de que utiliza nomes de aplicação que sejam exclusivos. Se um nome de aplicação for duplicado, apenas um deles será apresentado aos utilizadores no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. Esta descrição é apresentada aos utilizadores no portal da empresa.
    - **Publicador**: introduza o nome do publicador da aplicação.
    - **URL da Loja de Aplicações**: escreva o URL da Loja de Aplicações da aplicação que pretende criar. A URL pode ser encontrada pesquisando o [Microsoft Store](https://store.microsoft.com) para o aplicativo desejado. Use a URL da barra de endereços do navegador.
    - **Categoria**: opcionalmente, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Desta forma, permitirá que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da Empresa**: selecione esta opção para apresentar o conjunto de aplicações em destaque na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação (por exemplo, *Departamento de RH*).
    - **Notas**: opcionalmente, introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: opcionalmente, carregue um ícone que será associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
5. Selecione **OK**.
6. Selecione **Adicionar**.

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. As aplicações da Microsoft Store só podem ser atribuídas a grupos com o tipo de atribuição **Disponível para dispositivos inscritos** (os utilizadores instalam a aplicação a partir da aplicação ou site do Portal da Empresa).

## <a name="next-steps"></a>Próximos passos
- [Atribuir aplicações a grupos](apps-deploy.md)
