---
title: Adicionar aplicações da loja Android ao Microsoft Intune
titleSuffix: ''
description: Saiba como adicionar aplicativos da Android Store da Google Play Store ao Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea7db3cb6839a466044f83b1849a7f91f7de1822
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731080"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>Adicionar aplicações da loja Android ao Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Antes de atribuir uma aplicação a um dispositivo ou grupo de utilizadores, tem de primeiro adicionar a aplicação ao Microsoft Intune. 

## <a name="add-an-app"></a>Adicionar um aplicativo

Pode adicionar uma aplicação da loja Android ao Intune a partir do portal do Azure ao fazer o seguinte:

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. No painel da carga de trabalho **Aplicações do cliente**, em **Gerir**, selecione **Aplicações**.
5. Selecione **Adicionar**.
6. No painel **Adicionar Aplicação**, nos tipos de **Aplicações da loja** disponíveis, selecione **Android**.
7. Para configurar as informações da aplicação, selecione **Configurar** e, em seguida, forneça as seguintes informações. Para aplicações Android, aceda à [Google Play Store](https://play.google.com/store) e procure a aplicação que pretende implementar. Selecione a aplicação e anote os detalhes da aplicação. Consoante a aplicação que tenha selecionado, alguns dos valores podem ter sido preenchidos automaticamente.
    - **Nome**: Introduza o nome da aplicação tal como deve ser apresentado no portal da empresa. Certifique-se de que utiliza nomes de aplicação que sejam exclusivos. Se um nome de aplicação for duplicado, apenas um deles será apresentado aos utilizadores no portal da empresa.
    - **Descrição**: Introduza uma descrição para a aplicação. Esta descrição é apresentada aos utilizadores no portal da empresa.
    - **Publicador**: Introduza o nome do publicador da aplicação.
    - **URL da App Store**: Insira a URL da loja de aplicativos do aplicativo que você deseja criar.
    - **Sistema operativo mínimo**: selecione na lista a versão mínima do sistema operativo em que a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Categoria**: opcionalmente, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Desta forma, permitirá que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da Empresa**: selecione esta opção para apresentar a aplicação de forma bem visível na página principal do portal da empresa quando os utilizadores procurarem aplicações. Aplica-se a aplicativos implantados com a intenção disponível.
    - **URL de informações**: Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de privacidade**: Opcionalmente, introduza o URL de um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação (por exemplo, *Departamento de RH*).
    - **Notas**: opcionalmente, introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: opcionalmente, carregue um ícone que será associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
8. Selecione **OK**.
9. Selecione **Adicionar**.

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. 

## <a name="next-steps"></a>Passos seguintes

- [Atribuir aplicações a grupos](apps-deploy.md)
