---
title: Adicionar aplicações da loja Android ao Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre como adicionar aplicações da loja Android ao Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f62cb3a99a9cfd328cc041f095b0980eacc99852
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>Adicionar aplicações da loja Android ao Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Antes de atribuir uma aplicação a um dispositivo ou grupo de utilizadores, tem de primeiro adicionar a aplicação ao Microsoft Intune. Pode adicionar uma aplicação da loja Android ao Intune a partir do portal do Azure ao fazer o seguinte:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**.  
    O Intune encontra-se na secção **Monitorização + Gestão**.
1. No painel **Intune**, selecione **Aplicações móveis**.
2. No painel de carga de trabalho de **Aplicações móveis**, em **Gerir**, selecione **Aplicações**.
3. Selecione **Adicionar**.
4. No painel **Adicionar Aplicação**, nos tipos de **Aplicações da loja** disponíveis, selecione **Android**.
5. Para configurar as informações da aplicação, selecione **Configurar** e, em seguida, forneça as seguintes informações.  
    Consoante a aplicação que tenha selecionado, alguns dos valores podem ter sido preenchidos automaticamente.
    - **Nome**: introduza o nome da aplicação tal como deve ser apresentado no portal da empresa. Certifique-se de que utiliza nomes de aplicação que sejam exclusivos. Se um nome de aplicação for duplicado, apenas um deles será apresentado aos utilizadores no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. Esta descrição é apresentada aos utilizadores no portal da empresa.
    - **Publicador**: introduza o nome do publicador da aplicação.
    - **URL da loja de aplicações**: introduza o URL da loja de aplicações da aplicação que pretende criar.
    - **Sistema operativo mínimo**: na lista, selecione a versão mínima do sistema operativo em que a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Categoria**: opcionalmente, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Desta forma, permitirá que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da Empresa**: selecione esta opção para apresentar o conjunto de aplicações em destaque na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação (por exemplo, *Departamento de RH*).
    - **Notas**: opcionalmente, introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: opcionalmente, carregue um ícone que será associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
1. Selecione **OK**.
2. Selecione **Adicionar**.

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. 

## <a name="next-steps"></a>Próximos passos

- [Atribuir aplicações a grupos](apps-deploy.md)