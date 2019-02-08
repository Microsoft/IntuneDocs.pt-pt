---
title: Adicionar aplicações da loja Android ao Microsoft Intune
titleSuffix: ''
description: Saiba como adicionar aplicações da loja Android a partir da Google Play store ao Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 27818b0078336c2cb12eba81483274a787373aec
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841390"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>Adicionar aplicações da loja Android ao Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Antes de atribuir uma aplicação a um dispositivo ou grupo de utilizadores, tem de primeiro adicionar a aplicação ao Microsoft Intune. 

## <a name="add-an-app"></a>Adicionar uma aplicação

Pode adicionar uma aplicação da loja Android ao Intune a partir do portal do Azure ao fazer o seguinte:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**.  
    O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. No painel da carga de trabalho **Aplicações do cliente**, em **Gerir**, selecione **Aplicações**.
5. Selecione **Adicionar**.
6. No painel **Adicionar Aplicação**, nos tipos de **Aplicações da loja** disponíveis, selecione **Android**.
7. Para configurar as informações da aplicação, selecione **Configurar** e, em seguida, forneça as seguintes informações. Para aplicações Android, aceda à [Google Play Store](https://play.google.com/store) e procure a aplicação que pretende implementar. Selecione a aplicação e anote os detalhes da aplicação. Consoante a aplicação que tenha selecionado, alguns dos valores podem ter sido preenchidos automaticamente.
    - **Nome**: Introduza o nome da aplicação porque está a ser apresentado no portal da empresa. Certifique-se de que utiliza nomes de aplicação que sejam exclusivos. Se um nome de aplicação for duplicado, apenas um deles será apresentado aos utilizadores no portal da empresa.
    - **Descrição**: Introduza uma descrição para a aplicação. Esta descrição é apresentada aos utilizadores no portal da empresa.
    - **Publisher**: Introduza o nome do publicador da aplicação.
    - **URL da Appstore**: Introduza o URL da loja de aplicações da aplicação que pretende criar.
    - **Sistema operativo mínimo**: Na lista, selecione a versão mais antiga do sistema operativo no qual a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Categoria**: Opcionalmente, selecione uma ou mais das categorias de aplicações incorporadas ou uma categoria que criou. Desta forma, permitirá que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da empresa**: Selecione esta opção para apresentar o conjunto de aplicações de forma destacada na página principal do portal da empresa, quando os utilizadores procurarem aplicações.
    - **URL de informações**: Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de privacidade**: Opcionalmente, introduza o URL de um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Desenvolvedor**: Opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: Opcionalmente, introduza um nome para o proprietário desta aplicação, por exemplo, *departamento de RH*.
    - **Notas de**: Opcionalmente, introduza quaisquer notas que pretende associar esta aplicação.
    - **Logótipo**: Opcionalmente, carregue um ícone que será associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
1. Selecione **OK**.
2. Selecione **Adicionar**.

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. 

## <a name="next-steps"></a>Passos Seguintes

- [Atribuir aplicações a grupos](apps-deploy.md)
