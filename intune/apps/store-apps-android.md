---
title: Adicionar aplicações da loja Android ao Microsoft Intune
titleSuffix: ''
description: Saiba como adicionar aplicações de loja Android da loja Google Play ao Microsoft Intune.
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
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6b9f6a9303e53652959639193633cdcc00dfb99
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755090"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>Adicionar aplicações da loja Android ao Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Antes de atribuir uma aplicação a um dispositivo ou grupo de utilizadores, tem de primeiro adicionar a aplicação ao Microsoft Intune. 

## <a name="add-an-app"></a>Adicione uma aplicação

Pode adicionar uma aplicação da loja Android ao Intune a partir do portal do Azure ao fazer o seguinte:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
3. No painel de **aplicativos Select,** sob os tipos de **aplicativos da Loja** disponíveis, selecione **aplicativo de loja Android**.
4. Clique em **Selecionar**.<br>
   Os passos da **aplicação Add** são apresentados.
5. Para configurar as **informações** da App para a aplicação Android, navegue para a [loja Google Play](https://play.google.com/store) e procure a aplicação que pretende implementar. Exiba a página da aplicação e tome nota dos detalhes da aplicação. 
6. Na página de informações da **App,** adicione os detalhes da aplicação:
    - **Nome**: introduza o nome da aplicação tal como deve ser apresentado no portal da empresa. Certifique-se de que utiliza nomes de aplicação que sejam exclusivos. Se um nome de aplicação for duplicado, apenas um deles será apresentado aos utilizadores no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. Esta descrição é apresentada aos utilizadores no portal da empresa.
    - **Publicador**: introduza o nome do publicador da aplicação.
    - **URL da loja de aplicações**: introduza o URL da loja de aplicações da aplicação que pretende criar. Utilize o URL da página da aplicação quando os detalhes da aplicação forem apresentados na loja. 
    - **Sistema operativo mínimo**: na lista, selecione a versão mínima do sistema operativo em que a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Categoria**: opcionalmente, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Desta forma, permitirá que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Mostre-o como uma aplicação em destaque no Portal da Empresa**: Selecione esta opção para exibir a suite de aplicações em destaque na página principal do portal da empresa quando os utilizadores navegam para apps. Aplica-se a aplicações implementadas com intenção disponível.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação, por exemplo, *Departamento de RH*.
    - **Notas**: opcionalmente, introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: opcionalmente, carregue um ícone que será associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
7. Clique em **Seguir** para exibir a página **de tags scope.**
8. Clique em **Selecionar etiquetas** de âmbito para adicionar opcionalmente etiquetas de âmbito para a aplicação. Para mais informações, consulte [Utilize o controlo de acesso baseado em funções (RBAC) e as etiquetas](~/fundamentals/scope-tags.md)de âmbito para TI distribuídos .
9. Clique em **Avançar** para exibir a página **atribuições** .
10. Selecione as atribuições de grupo para a aplicação. Para mais informações, consulte [Adicionar grupos para organizar utilizadores e dispositivos](~/fundamentals/groups-add.md). 
11. Clique em **Seguir** para exibir a página **Review + criar.** Reveja os valores e configurações que inseriu para a aplicação.
12. Quando terminar, clique em **Criar** para adicionar a app ao Intune.

A lâmina **de visão geral** da aplicação que criou é exibida.

## <a name="next-steps"></a>Próximos passos

- [Atribuir aplicações a grupos](apps-deploy.md)
