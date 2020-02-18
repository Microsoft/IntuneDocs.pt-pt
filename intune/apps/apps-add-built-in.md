---
title: Adicionar aplicações incorporadas a dispositivos móveis com o Microsoft Intune
titleSuffix: ''
description: Saiba como pode utilizar o Intune para facilitar a instalação de aplicações incorporadas em dispositivos móveis.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96cd4997029c15396db91e9866bbb387c20f1044
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414436"
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>Adicionar aplicações incorporadas ao Microsoft Intune

O tipo de aplicações *incorporadas* facilita a atribuição de aplicações geridas com curadoria, como aplicações do Office 365, para dispositivos iOS/iPadOS e Android. Pode atribuir aplicações específicas a este tipo de aplicação, como o Excel, OneDrive, Outlook, Skype, entre outras. Depois de adicionar uma aplicação, verá o tipo da aplicação como *Aplicação iOS incorporada* ou *Aplicação Android incorporada*. Ao utilizar o tipo de aplicação incorporada, pode escolher quais destas aplicações irá publicar para os utilizadores dos dispositivos.

Nas versões anteriores da consola do Intune, o Intune disponibilizava várias aplicações geridas do Office 365 predefinidas, como o Outlook e o OneDrive. Os tipos destas aplicações geridas eram identificados como *Aplicação da Loja iOS Gerida* ou *Aplicação Android Gerida*. Em vez de utilizar estes tipos de aplicação, recomendamos que utilize o tipo de aplicação incorporada. O tipo de aplicação incorporada proporciona uma maior flexibilidade para editar e eliminar aplicações do Office 365.

>[!NOTE]
>As aplicações do Office 365 predefinidas que estejam identificadas como *Aplicação da Loja iOS Gerida* e *Aplicação Android Gerida* são removidas da lista de aplicações quando todas as tarefas forem eliminadas.

## <a name="add-a-built-in-app"></a>Adicionar uma aplicação incorporada

Para adicionar uma aplicação incorporada às suas aplicações disponíveis no Microsoft Intune, faça o seguinte:
1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações** > **Adicionar**.
3. No painel do **tipo select,** sob os tipos de **aplicativos da Loja** disponíveis, selecione app **Built-In**.
4. Clique em **Selecionar**. Os passos da **aplicação Add** são apresentados.
5. Na página **de aplicações Select Built-in,** clique em Selecionar a **aplicação** Para selecionar as aplicações que pretende incluir.
6. Selecione as aplicações incorporadas que pretende incluir. 
7. Depois de ter selecionado as aplicações, clique em **Select** no painel de **aplicações Select Built-in.**
8. Clique em **Seguir** para exibir a página **de tags scope.**
9. Clique em **Selecionar etiquetas** de âmbito para adicionar opcionalmente etiquetas de âmbito para a aplicação. Para mais informações, consulte [Utilize o controlo de acesso baseado em funções (RBAC) e as etiquetas](~/fundamentals/scope-tags.md)de âmbito para TI distribuídos .
10. Clique em **Seguir** para exibir a página **de Tarefas.**
11. Selecione as atribuições de grupo para a aplicação. Para mais informações, consulte [Adicionar grupos para organizar utilizadores e dispositivos](~/fundamentals/groups-add.md). 
12. Clique em **Seguir** para exibir a página **Review + criar.** Reveja os valores e configurações que inseriu para a aplicação.
13. Quando terminar, clique em **Criar** para adicionar a app ao Intune.

    A lâmina **de visão geral** da aplicação que criou é exibida.

## <a name="configure-app-information"></a>Configurar as informações da aplicação

Pode modificar as informações da aplicação incorporada. Estas informações ajudam-no a identificar a aplicação no Intune e também ajudam os utilizadores a encontrá-la no portal da empresa.
1. Selecione **Apps** > **Todas as aplicações** e selecione a aplicação incorporada que pretende modificar.  
   É apresentado um painel da aplicação incorporada.
2. Selecione **Propriedades**.
3. **Selecione Editar** ao lado de **informações**da App .
4. No painel **Informações da aplicação**, pode modificar as seguintes informações:
    - **Nome**: introduza o nome da aplicação incorporada tal como será apresentado no portal da empresa. Certifique-se de que todos os nomes que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só é apresentada uma das aplicações aos utilizadores no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. 
    - **Publicador**: introduza o nome do publicador da aplicação.
    - **Categoria**: opcionalmente, selecione uma ou mais das categorias de aplicações incorporadas. Esta opção permite que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Mostre isto como uma aplicação em destaque no portal da empresa**: Mostrar a app em destaque na página principal do portal da empresa quando os utilizadores navegam para apps.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação (por exemplo, *Departamento de RH*).
    - **Notas**: introduza quaisquer notas que queira associar a esta aplicação.
    - **Carregar Ícone**: carregue um ícone que será apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
5. Clique em **Rever + guarde** para exibir a página **Review + criar.** Reveja os valores e configurações que inseriu para a aplicação.
13. Quando terminar, clique em **Guardar** para atualizar a aplicação em Intune.

    A lâmina **de visão geral** da aplicação que criou é exibida.

## <a name="next-steps"></a>Próximos passos

- Agora pode atribuir as aplicações aos grupos que escolher. Para obter mais informações, veja [Atribuir aplicações a grupos](apps-deploy.md).
