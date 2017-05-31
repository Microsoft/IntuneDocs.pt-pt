---
title: "Como adicionar aplicações da loja Windows Phone 8.1 ao Intune"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como adicionar aplicações da loja Windows Phone 8.1 ao Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 72a883b77a4f74abd312f68f276f6250d89b5dd7
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-add-windows-phone-81-store-apps-to-microsoft-intune"></a>Como adicionar aplicações da loja Windows Phone 8.1 ao Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]


1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Gerir aplicações**.
4. Na carga de trabalho **Aplicações móveis**, escolha **Gerir** > **Aplicações**.
5. Acima da lista de aplicações, escolha **Adicionar**.
6. No painel **Adicionar Aplicação**, escolha **Informações da Aplicação**.
7. No painel **Editar Aplicação**, configure as informações seguintes. Quando tiver terminado, clique em **Adicionar**. Consoante a aplicação que tenha escolhido, alguns dos valores neste painel podem ter sido preenchidos automaticamente:
    - **Nome da Aplicação** – Introduza o nome da aplicação tal como será apresentado no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se o mesmo nome de aplicação existir duas vezes, apenas uma das aplicações será apresentada aos utilizadores no portal da empresa.
    - **Descrição da Aplicação** – Introduza uma descrição para a aplicação. A descrição será apresentada aos utilizadores no portal da empresa.
    - **Publicador** - Introduza o nome do publicador da aplicação.
    - **URL da loja de aplicações** – Introduza o URL da loja de aplicações da aplicação que pretende criar.
    - **Sistema Operativo Mínimo** – Na lista, escolha a versão mínima do sistema operativo no qual a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Categoria (opcional)** – Selecione uma ou mais categorias das aplicações incorporadas, ou uma categoria criada por si. Isto irá permitir que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar esta aplicação em destaque no Portal da Empresa** – Apresente a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações** – Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL será apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade** – Opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL será apresentado aos utilizadores no portal da empresa.
    - **Programador** – Opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário** – Opcionalmente, introduza um nome para o proprietário desta aplicação, por exemplo, **Departamento de RH**.
    - **Notas** – Introduza quaisquer notas que pretenda associar esta aplicação.
    - **Carregar Ícone** – Carregue um ícone que será associado à aplicação. Este é o ícone que será apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
8. Quando terminar, no painel **Adicionar Aplicação**, escolha **Guardar**.

A aplicação que criou será apresentada na lista de aplicações onde a pode atribuir aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).
