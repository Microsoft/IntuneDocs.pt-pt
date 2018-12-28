---
title: Adicionar aplicações da Microsoft Store ao Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre como adicionar aplicações da Microsoft Store (Loja Windows) ao Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 36ddac5b9fc7d03e0ef3e719e7c1d46d7881d2ac
ms.sourcegitcommit: 279f923b1802445e501324a262d14e8bfdddabde
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/21/2018
ms.locfileid: "53737955"
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Adicionar aplicações da Microsoft Store ao Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Antes de poder atribuir, monitorizar, configurar ou proteger aplicações, tem de adicioná-las ao Intune. 

## <a name="add-an-app-to-intune"></a>Adicionar uma aplicação ao Intune
Pode adicionar uma aplicação da Microsoft Store ao Intune ao fazer o seguinte:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**.  
    O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. No painel da carga de trabalho **Aplicações do cliente**, em **Gerir**, selecione **Aplicações**.
5. No painel **Aplicações**, selecione **Adicionar**.
6. No painel **Adicionar aplicação**, selecione um **Tipo de aplicação** do **Windows** e, em seguida, selecione **Informações da aplicação**.
7. No painel **Informações da aplicação**, adicione as informações da aplicação. Consoante a aplicação que tenha selecionado, alguns dos valores neste painel podem ter sido preenchidos automaticamente:
    - **Nome**: Introduza o nome da aplicação porque está a ser apresentado no portal da empresa. Certifique-se de que utiliza nomes de aplicação que sejam exclusivos. Se um nome de aplicação for duplicado, apenas um deles será apresentado aos utilizadores no portal da empresa.
    - **Descrição**: Introduza uma descrição para a aplicação. Esta descrição é apresentada aos utilizadores no portal da empresa.
    - **Publicador**: Introduza o nome do publicador da aplicação.
    - **URL da Appstore**: Escreva o URL da aplicação Store da aplicação que pretende criar.
    - **Categoria**: Opcionalmente, selecione uma ou mais das categorias de aplicações incorporadas ou uma categoria que criou. Desta forma, permitirá que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da empresa**: Selecione esta opção para apresentar o conjunto de aplicações de forma destacada na página principal do portal da empresa, quando os utilizadores procurarem aplicações.
    - **URL de informações**: Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de privacidade**: Opcionalmente, introduza o URL de um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Desenvolvedor**: Opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: Opcionalmente, introduza um nome para o proprietário desta aplicação, por exemplo, *departamento de RH*.
    - **Notas de**: Opcionalmente, introduza quaisquer notas que pretende associar esta aplicação.
    - **Logótipo**: Opcionalmente, carregue um ícone que será associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
8. Selecione **OK**.
9. Selecione **Adicionar**.

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. As aplicações da Microsoft Store só podem ser atribuídas a grupos com o tipo de atribuição **Disponível para dispositivos inscritos** (os utilizadores instalam a aplicação a partir da aplicação ou site do Portal da Empresa).

## <a name="next-steps"></a>Passos Seguintes
- [Atribuir aplicações a grupos](apps-deploy.md)
