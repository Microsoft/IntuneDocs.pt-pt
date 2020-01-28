---
title: Adicionar aplicações Web ao Microsoft Intune
titleSuffix: ''
description: Saiba adicionar aplicações web (aplicações de servidor de clientes) ao Microsoft Intune.
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
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 90cdff66d32ac5edb3b1867a545f2c9627ccfe39
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754784"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Adicionar aplicações Web ao Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Intune suporta uma variedade de tipos de aplicações, incluindo aplicações Web. Uma aplicação Web é uma aplicação de servidor de cliente. O servidor proporciona a aplicação Web, que inclui a IU, conteúdos e funcionalidades. Além disso, normalmente as plataformas de alojamento na Web modernas oferecem segurança, balanceamento de carga e outras vantagens. A manutenção de uma aplicação Web é feita separadamente na Web. Tem de utilizar o Microsoft Intune para apontar para este tipo de aplicação. Também tem de designar os grupos de utilizadores que podem aceder a esta aplicação. 

Antes de poder gerir e atribuir uma aplicação aos utilizadores, adicione-a ao Intune. 

Intune cria um atalho para a aplicação web no dispositivo do utilizador. Para dispositivos iOS, um atalho para a aplicação web é adicionado ao ecrã principal. Para dispositivos Android Device Admin, um atalho para a aplicação web é adicionado ao widget portal da empresa Intune e o widget precisa de ser fixado manualmente pelo utilizador. Para dispositivos Windows, é colocado um atalho para a aplicação web no Menu Iniciar.

> [!Note]
> Um navegador deve ser instalado no dispositivo do utilizador para lançar aplicações web. 

> [!Note]
> Para dispositivos Android Enterprise, consulte [links web geridos do Google Play](apps-add-android-for-work.md#managed-google-play-web-links)

## <a name="add-a-web-app-to-intune"></a>Adicionar uma aplicação Web ao Intune
Para adicionar uma aplicação ao Intune como um atalho para uma aplicação na Web, faça o seguinte:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
3. No painel do **tipo select,** sob os **outros** tipos disponíveis, selecione o **link Web**.
4. Clique em **Selecionar**. Os passos da **aplicação Add** são apresentados.
5. Na página de informações da **App,** adicione as seguintes informações:
    - **Nome**: introduza o nome da aplicação tal como deve ser apresentado no portal da empresa. 

        > [!NOTE]
        > Se alterar o nome da aplicação através do portal do Azure no Intune após ter implementado e instalado a aplicação, a mesma deixará de poder ser visada através de comandos.

    - **Descrição**: introduza uma descrição para a aplicação. Esta descrição é apresentada aos utilizadores no portal da empresa.
    - **Publicador**: introduza o nome do publicador desta aplicação.
    - **URL da Aplicação**: introduza o URL do site que aloja a aplicação que pretende atribuir.
    - **Categoria**: opcionalmente, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Desta forma, permitirá que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Mostre-o como uma aplicação em destaque no Portal da Empresa**: Selecione esta opção para exibir a suite de aplicações em destaque na página principal do portal da empresa quando os utilizadores navegam para apps.
    - **Exigir um browser gerido para abrir esta ligação**: selecione esta opção para atribuir uma ligação a um site ou uma aplicação Web aos utilizadores para que possam abri-la no browser gerido do Intune. Este browser deve estar instalado nos respetivos dispositivos.
    - **Logótipo**: carregue um ícone que será associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
6. Clique em **Seguir** para exibir a página **de tags scope.**
7. Clique em **Selecionar etiquetas** de âmbito para adicionar opcionalmente etiquetas de âmbito para a aplicação. Para mais informações, consulte [Utilize o controlo de acesso baseado em funções (RBAC) e as etiquetas](~/fundamentals/scope-tags.md)de âmbito para TI distribuídos .
8. Clique em **Avançar** para exibir a página **atribuições** .
9. Selecione as atribuições de grupo para a aplicação. Para mais informações, consulte [Adicionar grupos para organizar utilizadores e dispositivos](~/fundamentals/groups-add.md). 
10. Clique em **Seguir** para exibir a página **Review + criar.** Reveja os valores e configurações que inseriu para a aplicação.
11. Quando terminar, clique em **Criar** para adicionar a app ao Intune.

    A lâmina **de visão geral** da aplicação que criou é exibida.

> [!Note]
> Atualmente, a implementação de aplicações Web do Intune em dispositivos iOS está associada ao perfil de gestão, pelo que não é possível removê-la manualmente. Pode alterar o tipo de implementação para **Desinstalar** no portal do Intune. Quando o fizer, poderá remover manualmente a implementação. No entanto, se remover a implementação antes de alterar a intenção de atribuição de aplicações para **Desinstalar**, a aplicação Web ficará permanentemente no dispositivo até que se proceda à anulação da inscrição do dispositivo no Intune.

Os utilizadores finais podem lançar aplicações web diretamente a partir da aplicação Portal da Empresa do Windows, selecionando a aplicação web e, em seguida, escolhendo a opção **Open no navegador.** O URL publicado na Web é aberto diretamente no navegador web. 

## <a name="next-steps"></a>Próximos passos

A aplicação que criou será apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. Para obter ajuda, veja [Atribuir aplicações a grupos](apps-deploy.md). 
