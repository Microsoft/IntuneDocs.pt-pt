---
title: Adicionar aplicações incorporadas a dispositivos móveis com o Microsoft Intune
titlesuffix: ''
description: Saiba como pode utilizar o Intune para facilitar a instalação de aplicações incorporadas em dispositivos móveis.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: e3bb60d3d6bd7321ea3e378c747e87481b659888
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181552"
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>Adicionar aplicações incorporadas ao Microsoft Intune

As aplicações *incorporadas* permitem-lhe atribuir facilmente aplicações geridas organizadas, como aplicações do Office 365, a dispositivos iOS e Android. Pode atribuir aplicações específicas a este tipo de aplicação, como o Excel, OneDrive, Outlook, Skype, entre outras. Depois de adicionar uma aplicação, verá o tipo da aplicação como *Aplicação iOS incorporada* ou *Aplicação Android incorporada*. Ao utilizar o tipo de aplicação incorporada, pode escolher quais destas aplicações irá publicar para os utilizadores dos dispositivos.

Nas versões anteriores da consola do Intune, o Intune disponibilizava várias aplicações geridas do Office 365 predefinidas, como o Outlook e o OneDrive. Os tipos destas aplicações geridas eram identificados como *Aplicação da Loja iOS Gerida* ou *Aplicação Android Gerida*. Em vez de utilizar estes tipos de aplicação, recomendamos que utilize o tipo de aplicação incorporada. O tipo de aplicação incorporada proporciona uma maior flexibilidade para editar e eliminar aplicações do Office 365.

>[!NOTE]
>As aplicações do Office 365 predefinidas que estejam identificadas como *Aplicação da Loja iOS Gerida* e *Aplicação Android Gerida* são removidas da lista de aplicações quando todas as tarefas forem eliminadas.

## <a name="add-a-built-in-app"></a>Adicionar uma aplicação incorporada

Para adicionar uma aplicação incorporada às suas aplicações disponíveis no Microsoft Intune, faça o seguinte:
1. Inicie sessão no portal do Azure.
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
1. Na **aplicações de cliente - aplicações** painel, selecione a aplicação incorporada que pretende modificar.  
    É apresentado um painel da aplicação incorporada.
2. Em **Gerir**, selecione a opção **Propriedades**.
3. Selecione a opção **Configurar** para modificar as informações da aplicação incorporada.
4. No painel **Informações da aplicação**, pode modificar as seguintes informações:
    - **Nome**: introduza o nome da aplicação incorporada tal como será apresentado no portal da empresa. Certifique-se de que todos os nomes que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só é apresentada uma das aplicações aos utilizadores no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. 
    - **Publicador**: introduza o nome do publicador da aplicação.
    - **Categoria**: opcionalmente, selecione uma ou mais das categorias de aplicações incorporadas. Esta opção permite que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar esta aplicação em destaque no portal da empresa**: apresente a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação (por exemplo, *Departamento de RH*).
    - **Notas**: introduza quaisquer notas que queira associar a esta aplicação.
    - **Carregar Ícone**: carregue um ícone que será apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
4. Selecione **OK**.
5. No painel **Propriedades**, selecione **Guardar**.

## <a name="next-steps"></a>Passos Seguintes

- Agora pode atribuir as aplicações aos grupos que escolher. Para obter mais informações, veja [Atribuir aplicações a grupos](apps-deploy.md).
