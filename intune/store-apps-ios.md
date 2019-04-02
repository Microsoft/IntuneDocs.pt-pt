---
title: Adicionar aplicações da loja iOS ao Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre como adicionar aplicações da loja iOS ao Microsoft Intune. Pode atribuir aplicações ao utilizar este método se as aplicações são gratuitas na App Store.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 454000ccc7ac2d6f531b5ab43bb7652541559992
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799542"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>Adicionar aplicações da loja iOS ao Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilize as informações neste artigo para ajudá-lo a adicionar aplicações da loja iOS ao Microsoft Intune. As aplicações da loja iOS são aplicações que o Intune instala nos dispositivos dos seus utilizadores. Os utilizadores fazem parte da força de trabalho da sua empresa. As aplicações da loja iOS são atualizadas automaticamente.

>[!NOTE]
>Embora os utilizadores de dispositivos iOS possam remover algumas aplicações iOS incorporadas, tais como Bolsa e Mapas, não pode utilizar o Intune para implementar novamente essas aplicações. Se os seus utilizadores eliminarem essas aplicações, terão de aceder à App Store e reinstalá-las manualmente.

## <a name="before-you-start"></a>Antes de começar

Só pode atribuir aplicações com este método se forem gratuitas na App Store. Se quiser atribuir aplicações pagas com o Intune, considere utilizar o [programa de compra em volume do iOS](vpp-apps-ios.md).

>[!NOTE]
>Ao trabalhar com o Microsoft Intune, recomendamos que utilize o browser Microsoft Edge ou Google Chrome.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**.  
    O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. No painel da carga de trabalho **Aplicações do cliente**, em **Gerir**, selecione **Aplicações**.
5. No painel **Aplicações**, selecione **Adicionar**.
6. Na lista **Tipo de aplicação**, nos tipos de **Aplicação da loja**, selecione **iOS**.
7. Selecione **Procurar na App Store**.
8. No painel **Procurar na App Store**, selecione a região da App Store.
9. Na caixa **Procurar**, escreva o nome (ou parte do mesmo) da aplicação.  
    O Intune procura na loja e apresenta uma lista de resultados relevantes.
10. Na lista de resultados, selecione a aplicação que pretende e, em seguida, selecione **Selecionar**.
11. No painel **Adicionar aplicação**, selecione **Informações da aplicação** para configurar a aplicação.
12. No painel **Informações da aplicação**, adicione as informações da aplicação. Consoante a aplicação que tenha selecionado, alguns dos valores neste painel podem ter sido preenchidos automaticamente:
    - **Nome**: Introduza o nome da aplicação porque está a ser apresentado no portal da empresa. Certifique-se de que utiliza nomes de aplicação que sejam exclusivos. Se um nome de aplicação for duplicado, apenas um deles será apresentado aos utilizadores no portal da empresa.
    - **Descrição**: Introduza uma descrição para a aplicação. Esta descrição é apresentada aos utilizadores no portal da empresa.
    - **Publisher**: Introduza o nome do publicador da aplicação.
    - **URL da Appstore**: Escreva o URL da aplicação Store da aplicação que pretende criar.
    - **Sistema operativo mínimo**: Na lista, selecione a versão mais antiga do sistema operativo no qual a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Tipo de dispositivo aplicável**: Na lista, selecione os dispositivos que são utilizados pela aplicação.
    - **Categoria**: Opcionalmente, selecione uma ou mais das categorias de aplicações incorporadas ou uma categoria que criou. Desta forma, permitirá que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da empresa**: Selecione esta opção para apresentar o conjunto de aplicações de forma destacada na página principal do portal da empresa, quando os utilizadores procurarem aplicações.
    - **URL de informações**: Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de privacidade**: Opcionalmente, introduza o URL de um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Desenvolvedor**: Opcionalmente, introduza o nome do programador da aplicação. Este campo só é visível para administradores e não para os utilizadores.
    - **Proprietário**: Opcionalmente, introduza um nome para o proprietário desta aplicação, por exemplo, *departamento de RH*. Este campo só é visível para administradores e não para os utilizadores.
    - **Notas de**: Opcionalmente, introduza quaisquer notas que pretende associar esta aplicação. Este campo só é visível para o administrador e não estará visível para os utilizadores finais.
    - **Logótipo**: Opcionalmente, carregue um ícone que será associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
13. Selecione **OK**.
14. Selecione **Adicionar**.

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar.

## <a name="next-steps"></a>Passos Seguintes

- [Atribuir aplicações a grupos](apps-deploy.md)
