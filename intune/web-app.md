---
title: "Como adicionar aplicações Web ao Intune"
titleSuffix: Azure portal
description: "Saiba mais sobre adicionar aplicações Web ao Intune.\""
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cfa70879a460826d22eb6fab2e0d08603e567d6e
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>Como adicionar aplicações Web ao Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Antes de poder gerir e atribuir uma aplicação aos utilizadores, adicione-a ao Intune. O Intune suporta uma variedade de tipos de aplicações, incluindo aplicações Web.

> [!Note]
> As aplicações Web não são suportadas nos dispositivos Android for Work.

Conclua os seguintes passos para adicionar uma aplicação ao Intune como um atalho para uma aplicação na Web:

1. Inicie sessão no portal do Azure.
2. Através de **Mais recursos**, procure e selecione **Intune**.
3. No painel **Microsoft Intune**, selecione **Aplicações móveis**.
4. No painel **Aplicações móveis**, selecione **Aplicações**.
5. Acima da lista de aplicações, selecione **Adicionar**. O painel **Adicionar aplicação** é apresentado.
6. No painel **Adicionar aplicação**, selecione **Aplicação Web** na lista pendente **Tipo de aplicação**.
7. Selecione a opção **Configurar** para apresentar o painel **Informações da aplicação**.
8. No painel **Informações da aplicação**, adicione as informações seguintes:
    - **Nome** – introduza o nome da aplicação tal como deve ser apresentado no portal da empresa.
    - **Descrição** - Introduza uma descrição para a aplicação. A descrição é apresentada aos utilizadores finais no portal da empresa.
    - **Publicador** – Introduza o nome do publicador desta aplicação.
    - **URL da Aplicação** - introduza o URL do site que aloja a aplicação que quer atribuir.
    - **Categoria (opcional)** – Selecione uma ou mais categorias das aplicações incorporadas, ou uma categoria criada por si. Esta seleção permitirá que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar esta aplicação em destaque no Portal da Empresa** – Apresente a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **Exigir um browser gerido para abrir esta ligação** – quando atribui uma ligação a um site ou uma aplicação Web aos utilizadores, estes poderão abri-la no browser gerido do Intune. Este browser deve estar instalado nos respetivos dispositivos.
    - **Logótipo** – carregue um logótipo associado à aplicação. Este é o logótipo que é apresentado com a aplicação quando os utilizadores procuram no portal da empresa.
9. Quando tiver terminado, no painel **Adicionar informações**, selecione **OK**.
10. Em seguida, no painel **Adicionar aplicação**, selecione **Adicionar**.

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).