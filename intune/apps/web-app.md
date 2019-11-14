---
title: Adicionar aplicações Web ao Microsoft Intune
titleSuffix: ''
description: Saiba como adicionar aplicativos Web (aplicativos cliente-servidor) a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/13/2019
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
ms.openlocfilehash: 997cf043f8ea61133d6e61f4584ad9349aedbf73
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2019
ms.locfileid: "74060048"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Adicionar aplicações Web ao Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Intune suporta uma variedade de tipos de aplicações, incluindo aplicações Web. Uma aplicação Web é uma aplicação de servidor de cliente. O servidor proporciona a aplicação Web, que inclui a IU, conteúdos e funcionalidades. Além disso, normalmente as plataformas de alojamento na Web modernas oferecem segurança, balanceamento de carga e outras vantagens. A manutenção de uma aplicação Web é feita separadamente na Web. Tem de utilizar o Microsoft Intune para apontar para este tipo de aplicação. Também tem de designar os grupos de utilizadores que podem aceder a esta aplicação. 

Antes de poder gerir e atribuir uma aplicação aos utilizadores, adicione-a ao Intune. 

O Intune cria um atalho para o aplicativo Web no dispositivo do usuário. Para dispositivos iOS, um atalho para o aplicativo Web é adicionado à tela inicial. Para dispositivos Android, um atalho para o aplicativo Web é adicionado ao widget portal da empresa do Intune e o widget precisa ser fixado manualmente pelo usuário. Para dispositivos Windows, um atalho para o aplicativo Web é colocado no menu iniciar.

> [!Note]
> Um navegador deve ser instalado no dispositivo do usuário para iniciar aplicativos Web. 

## <a name="add-a-web-app-to-intune"></a>Adicionar uma aplicação Web ao Intune
Para adicionar uma aplicação ao Intune como um atalho para uma aplicação na Web, faça o seguinte:

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. No painel da carga de trabalho **Aplicações do cliente**, em **Gerir**, selecione **Aplicações**.
5. No painel **Aplicações**, selecione **Adicionar**.
6. No painel **Adicionar aplicação**, na lista pendente **Tipo de aplicação** selecione **Ligação Web**.
7. Selecione **Configurar**.
8. No painel **Informações da aplicação**, adicione as informações seguintes:
    - **Nome**: introduza o nome da aplicação tal como deve ser apresentado no portal da empresa. 

        > [!NOTE]
        > Se alterar o nome da aplicação através do portal do Azure no Intune após ter implementado e instalado a aplicação, a mesma deixará de poder ser visada através de comandos.

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
>
> Atualmente, a implementação de aplicações Web do Intune em dispositivos iOS está associada ao perfil de gestão, pelo que não é possível removê-la manualmente. Pode alterar o tipo de implementação para **Desinstalar** no portal do Intune. Quando o fizer, poderá remover manualmente a implementação. No entanto, se remover a implementação antes de alterar a intenção de atribuição de aplicações para **Desinstalar**, a aplicação Web ficará permanentemente no dispositivo até que se proceda à anulação da inscrição do dispositivo no Intune.

Os usuários finais podem iniciar aplicativos Web diretamente do aplicativo Windows Portal da Empresa selecionando o aplicativo Web e escolhendo a opção **abrir no navegador**. A URL da Web publicada é aberta diretamente no navegador da Web. 

## <a name="next-steps"></a>Próximos passos

A aplicação que criou será apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. Para obter ajuda, veja [Atribuir aplicações a grupos](apps-deploy.md). 
