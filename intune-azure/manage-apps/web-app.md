---
title: "Como adicionar aplicações Web ao Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como adicionar aplicações Web ao Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 8b14b9dfef7100a86c338c362ba56be329a8639c

---

# <a name="how-to-add-web-apps-to-microsoft-intune"></a>Como adicionar aplicações Web ao Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

1. Inicie sessão no portal do Azure.
2. Selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Gerir aplicações**.
4. Na carga de trabalho **Aplicações móveis**, selecione **Gerir** > **Aplicações**.
5. Acima da lista de aplicações, selecione **Adicionar**.
6. No painel **Adicionar Aplicação**, selecione **Informações da Aplicação**.
7. No painel **Editar Aplicação**, configure as informações seguintes. Quando tiver terminado, clique em **Adicionar**:
    - **URL da Aplicação** – Introduza o URL do site que aloja a aplicação que quer implementar.
    - **Nome da Aplicação** – Introduza o nome da aplicação tal como será apresentado no portal da empresa.
    - **Descrição da Aplicação** – Introduza uma descrição para a aplicação. A descrição será apresentada aos utilizadores finais no portal da empresa.
    - **Publicador** – Introduza o nome do publicador desta aplicação.
    - **Categoria (opcional)** – Selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. Isto irá permitir que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar esta aplicação em destaque no Portal da Empresa** – Apresente a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **Exigir um browser gerido para abrir esta ligação** – Quando implementa uma ligação para um site ou uma aplicação Web nos utilizadores, estes só poderão abri-la no browser gerido do Intune. Este browser deve estar instalado nos respetivos dispositivos.
    - **Carregar Ícone** – Carregue um ícone que será associado à aplicação. Este é o ícone que será apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
8. Quando terminar, no painel **Adicionar Aplicação**, selecione **Guardar**.

A aplicação que criou será apresentada na lista de aplicações onde a pode atribuir aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](/intune-azure/manage-apps/deploy-apps).


<!--HONumber=Feb17_HO3-->


