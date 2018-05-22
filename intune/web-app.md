---
title: Adicionar aplicações Web ao Microsoft Intune
titleSuffix: ''
description: Saiba como adicionar aplicações Web ao Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0d62341e35bf851bb429b15a582183bec62a9d4a
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="add-web-apps-to-microsoft-intune"></a>Adicionar aplicações Web ao Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Intune suporta uma variedade de tipos de aplicações, incluindo aplicações Web. Uma aplicação Web é uma aplicação de servidor de cliente. O servidor proporciona a aplicação Web, que inclui a IU, conteúdos e funcionalidades. Além disso, normalmente as plataformas de alojamento na Web modernas oferecem segurança, balanceamento de carga e outras vantagens. A manutenção de uma aplicação Web é feita separadamente na Web. Tem de utilizar o Microsoft Intune para apontar para este tipo de aplicação. Também tem de designar os grupos de utilizadores que podem aceder a esta aplicação. 

Antes de poder gerir e atribuir uma aplicação aos utilizadores, adicione-a ao Intune. O Intune cria um atalho para a aplicação Web no ecrã principal do dispositivo do utilizador.

> [!Note]
> As aplicações Web não são suportadas nos dispositivos Android for Work e macOS.

## <a name="add-a-web-app-to-intune"></a>Adicionar uma aplicação Web ao Intune
Para adicionar uma aplicação ao Intune como um atalho para uma aplicação na Web, faça o seguinte:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**.  
    O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações móveis**.
4. No painel de carga de trabalho de **Aplicações móveis**, em **Gerir**, selecione **Aplicações**.
5. No painel **Aplicações**, selecione **Adicionar**.
6. No painel **Adicionar aplicação**, na lista pendente **Tipo de aplicação** selecione **Ligação Web**.
7. Selecione **Configurar**.
8. No painel **Informações da aplicação**, adicione as informações seguintes:
    - **Nome**: introduza o nome da aplicação tal como deve ser apresentado no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. Esta descrição é apresentada aos utilizadores no portal da empresa.
    - **Publicador**: introduza o nome do publicador desta aplicação.
    - **URL da Aplicação**: introduza o URL do site que aloja a aplicação que pretende atribuir.
    - **Categoria**: opcionalmente, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Desta forma, permitirá que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da Empresa**: selecione esta opção para apresentar o conjunto de aplicações em destaque na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **Exigir um browser gerido para abrir esta ligação**: selecione esta opção para atribuir uma ligação a um site ou uma aplicação Web aos utilizadores para que possam abri-la no browser gerido do Intune. Este browser deve estar instalado nos respetivos dispositivos.
    - **Logótipo**: carregue um ícone que será associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
9. Selecione **OK**.
10. No painel **Adicionar aplicação**, selecione **Adicionar**.

> [!Note]
> Os utilizadores têm de adicionar o widget do Intune ao ecrã principal para apresentar aplicações Web que tenham sido atribuídas a dispositivos Android.

## <a name="next-steps"></a>Próximos passos

A aplicação que criou será apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. Para obter ajuda, veja [Atribuir aplicações a grupos](apps-deploy.md). 
