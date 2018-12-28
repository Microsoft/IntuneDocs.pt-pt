---
title: Adicionar aplicações da loja do Windows Phone 8.1 ao Microsoft Intune
titleSuffix: ''
description: Este tópico descreve como adicionar aplicações da loja Windows Phone 8.1 ao Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5892ffe0369ae7b43489c1ce5c327f88c0d857f3
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642528"
---
# <a name="add-windows-phone-81-store-apps-to-microsoft-intune"></a>Adicionar aplicações da loja do Windows Phone 8.1 ao Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Antes de atribuir uma aplicação a um dispositivo ou grupo de utilizadores, tem de primeiro adicionar a aplicação ao Microsoft Intune. 

## <a name="add-an-app-to-intune"></a>Adicionar uma aplicação ao Intune
Pode adicionar uma aplicação da loja do Windows Phone 8.1 ao Intune a partir do portal do Azure ao fazer o seguinte:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**.  
    O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. No painel da carga de trabalho **Aplicações do cliente**, em **Gerir**, selecione **Aplicações**.
5. No painel **Aplicações**, selecione **Adicionar**.
6. No painel **Adicionar aplicação**, selecione um **Tipo de aplicação** do **Windows Phone 8.1** e, em seguida, selecione **Informações da aplicação**.
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

A aplicação que criou será apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar.

## <a name="next-steps"></a>Passos Seguintes

- [Atribuir aplicações a grupos](apps-deploy.md)
