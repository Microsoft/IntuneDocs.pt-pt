---
title: Adicionar aplicações incorporadas a dispositivos móveis com o Microsoft Intune
titleSuffix: ''
description: Saiba como pode utilizar o Intune para facilitar a instalação de aplicações incorporadas em dispositivos móveis.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2a94542311bc5ff4a25b2f9c6229898b1d891c6c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731296"
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>Adicionar aplicações incorporadas ao Microsoft Intune

As aplicações *incorporadas* permitem-lhe atribuir facilmente aplicações geridas organizadas, como aplicações do Office 365, a dispositivos iOS e Android. Pode atribuir aplicações específicas a este tipo de aplicação, como o Excel, OneDrive, Outlook, Skype, entre outras. Depois de adicionar uma aplicação, verá o tipo da aplicação como *Aplicação iOS incorporada* ou *Aplicação Android incorporada*. Ao utilizar o tipo de aplicação incorporada, pode escolher quais destas aplicações irá publicar para os utilizadores dos dispositivos.

Nas versões anteriores da consola do Intune, o Intune disponibilizava várias aplicações geridas do Office 365 predefinidas, como o Outlook e o OneDrive. Os tipos destas aplicações geridas eram identificados como *Aplicação da Loja iOS Gerida* ou *Aplicação Android Gerida*. Em vez de utilizar estes tipos de aplicação, recomendamos que utilize o tipo de aplicação incorporada. O tipo de aplicação incorporada proporciona uma maior flexibilidade para editar e eliminar aplicações do Office 365.

>[!NOTE]
>As aplicações do Office 365 predefinidas que estejam identificadas como *Aplicação da Loja iOS Gerida* e *Aplicação Android Gerida* são removidas da lista de aplicações quando todas as tarefas forem eliminadas.

## <a name="add-a-built-in-app"></a>Adicionar uma aplicação incorporada

Para adicionar uma aplicação incorporada às suas aplicações disponíveis no Microsoft Intune, faça o seguinte:
1. Inicie sessão no Portal do Azure.
2. Para apresentar o painel do Microsoft Intune, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. No painel **Aplicações do cliente**, em **Gerir**, selecione **Aplicações**.
5. Selecione **Adicionar**.
6. No painel **Adicionar aplicação**, na lista **Tipo de aplicação**, selecione **Aplicação incorporada**.
7. Selecione **Selecionar aplicação**.
8. No painel **Aplicação incorporada**, selecione as aplicações que quer incluir.
9. No painel **Adicionar aplicação**, selecione **Adicionar**.


## <a name="configure-app-information"></a>Configurar as informações da aplicação

Pode modificar as informações da aplicação incorporada. Estas informações ajudam-no a identificar a aplicação no Intune e também ajudam os utilizadores a encontrá-la no portal da empresa.
1. No painel **aplicativos cliente – aplicativos** , selecione o aplicativo interno que você deseja modificar.  
    É apresentado um painel da aplicação incorporada.
2. Em **Gerir**, selecione a opção **Propriedades**.
3. Selecione a opção **Configurar** para modificar as informações da aplicação incorporada.
4. No painel **Informações da aplicação**, pode modificar as seguintes informações:
    - **Nome**: Insira o nome do aplicativo interno como ele é exibido no portal da empresa. Certifique-se de que todos os nomes que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só é apresentada uma das aplicações aos utilizadores no portal da empresa.
    - **Descrição**: Introduza uma descrição para a aplicação. 
    - **Publicador**: Introduza o nome do publicador da aplicação.
    - **Categoria**: Opcionalmente, selecione uma ou mais das categorias de aplicativo internas. Esta opção permite que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Exibir como um aplicativo em destaque no portal da empresa**: Apresente a aplicação de forma bem visível na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações**: Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de privacidade**: Opcionalmente, introduza o URL de um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: Opcionalmente, insira um nome para o proprietário deste aplicativo (por exemplo, *departamento de RH*).
    - **Notas**: introduza quaisquer notas que queira associar a esta aplicação.
    - **Ícone de carregamento**: Carregue um ícone que é exibido com o aplicativo quando os usuários navegam pelo portal da empresa.
4. Selecione **OK**.
5. No painel **Propriedades**, selecione **Guardar**.

## <a name="next-steps"></a>Passos seguintes

- Agora pode atribuir as aplicações aos grupos que escolher. Para obter mais informações, veja [Atribuir aplicações a grupos](apps-deploy.md).
