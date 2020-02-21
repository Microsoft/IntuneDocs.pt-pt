---
title: Adicionar aplicações da loja iOS ao Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre como adicionar aplicações da loja iOS ao Microsoft Intune. Poderá atribuir aplicações com este método se forem gratuitas na App Store.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f2baf60fed2c6010e5ae0784cda166ac4fabfd57
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511740"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>Adicionar aplicações da loja iOS ao Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Utilize as informações neste artigo para ajudá-lo a adicionar aplicações da loja iOS ao Microsoft Intune. As aplicações da loja iOS são aplicações que o Intune instala nos dispositivos dos seus utilizadores. Os utilizadores fazem parte da força de trabalho da sua empresa. As aplicações da loja iOS são atualizadas automaticamente.

>[!NOTE]
>Embora os utilizadores de dispositivos iOS/iPadOS possam remover algumas aplicações incorporadas para iOS/iPadOS, como Stocks e Maps, não é possível utilizar o Intune para reimplementar essas aplicações. Se os seus utilizadores eliminarem essas aplicações, terão de aceder à App Store e reinstalá-las manualmente.

## <a name="before-you-start"></a>Antes de começar

Só pode atribuir aplicações com este método se forem gratuitas na App Store. Se pretender atribuir aplicações pagas utilizando o Intune, considere utilizar o [programa de compra de volume iOS/iPadOS](vpp-apps-ios.md).

>[!NOTE]
>Ao trabalhar com o Microsoft Intune, recomendamos que utilize o browser Microsoft Edge ou Google Chrome.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações** > **Adicionar**.
3. No painel do **tipo select,** nos tipos de **aplicativos da Loja** disponíveis, selecione a **aplicação de loja iOS**.
4. Clique em **Selecionar**.<br>
   Os passos da **aplicação Add** são apresentados.
5. Selecione **Procurar na App Store**.
6. No painel **Search the App Store,** selecione o país/região da App Store.
7. Na caixa **Procurar**, escreva o nome (ou parte do mesmo) da aplicação.  
    O Intune procura na loja e apresenta uma lista de resultados relevantes.
8. Na lista de resultados, selecione a aplicação que pretende e, em seguida, selecione **Selecionar**.<br>

   A página de **informações** da App será exibida no painel de **aplicações Add.** Quando possível, as informações da aplicação serão adicionadas com base na aplicação selecionada a partir da loja.

9. Na página de informações da **App,** adicione os detalhes da aplicação. Consoante a aplicação que tenha selecionado, alguns dos valores neste painel podem ter sido preenchidos automaticamente:
    - **Nome**: introduza o nome da aplicação tal como deve ser apresentado no portal da empresa. Certifique-se de que utiliza nomes de aplicação que sejam exclusivos. Se um nome de aplicação for duplicado, apenas um deles será apresentado aos utilizadores no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. Esta descrição é apresentada aos utilizadores no portal da empresa.
    - **Publicador**: introduza o nome do publicador da aplicação.
    - **URL da Loja de Aplicações**: escreva o URL da Loja de Aplicações da aplicação que pretende criar.
    - **Sistema operativo mínimo**: na lista, selecione a versão mínima do sistema operativo em que a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Tipo de dispositivo aplicável**: na lista, selecione os dispositivos utilizados pela aplicação.
    - **Categoria**: opcionalmente, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Desta forma, permitirá que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Mostre-o como uma aplicação em destaque no Portal da Empresa**: Selecione esta opção para exibir a suite de aplicações em destaque na página principal do portal da empresa quando os utilizadores navegam para apps.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação. Este campo só é visível para administradores e não para os utilizadores.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação (por exemplo, *Departamento de RH*). Este campo só é visível para administradores e não para os utilizadores.
    - **Notas**: opcionalmente, introduza quaisquer notas que queira associar a esta aplicação. Este campo só é visível para o administrador e não estará visível para os utilizadores finais.
    - **Logótipo**: opcionalmente, carregue um ícone que será associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
10. Clique em **Seguir** para exibir a página **de tags scope.**
11. Clique em **Selecionar etiquetas** de âmbito para adicionar opcionalmente etiquetas de âmbito para a aplicação. Para mais informações, consulte [Utilize o controlo de acesso baseado em funções (RBAC) e as etiquetas](~/fundamentals/scope-tags.md)de âmbito para TI distribuídos .
12. Clique em **Seguir** para exibir a página **de Tarefas.**
13. Selecione as atribuições de grupo para a aplicação. Para mais informações, consulte [Adicionar grupos para organizar utilizadores e dispositivos](~/fundamentals/groups-add.md). 
14. Clique em **Seguir** para exibir a página **Review + criar.** Reveja os valores e configurações que inseriu para a aplicação.
15. Quando terminar, clique em **Criar** para adicionar a app ao Intune.

A lâmina **de visão geral** da aplicação que criou é exibida.

## <a name="next-steps"></a>Próximos passos

- [Atribuir aplicações a grupos](apps-deploy.md)
