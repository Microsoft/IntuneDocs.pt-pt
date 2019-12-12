---
title: Adicionar aplicações da loja iOS ao Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre como adicionar aplicações da loja iOS ao Microsoft Intune. Poderá atribuir aplicações com este método se forem gratuitas na App Store.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: c5616b27b97d5623958ec872390e2a6de79db3c5
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74563456"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>Adicionar aplicações da loja iOS ao Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Utilize as informações neste artigo para ajudá-lo a adicionar aplicações da loja iOS ao Microsoft Intune. As aplicações da loja iOS são aplicações que o Intune instala nos dispositivos dos seus utilizadores. Os utilizadores fazem parte da força de trabalho da sua empresa. As aplicações da loja iOS são atualizadas automaticamente.

>[!NOTE]
>Embora os utilizadores de dispositivos iOS possam remover algumas aplicações iOS incorporadas, tais como Bolsa e Mapas, não pode utilizar o Intune para implementar novamente essas aplicações. Se os seus utilizadores eliminarem essas aplicações, terão de aceder à App Store e reinstalá-las manualmente.

## <a name="before-you-start"></a>Antes de começar

Só pode atribuir aplicações com este método se forem gratuitas na App Store. Se quiser atribuir aplicações pagas com o Intune, considere utilizar o [programa de compra em volume do iOS](vpp-apps-ios.md).

>[!NOTE]
>Ao trabalhar com o Microsoft Intune, recomendamos que utilize o browser Microsoft Edge ou Google Chrome.

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
3. Na lista **Tipo de aplicação**, nos tipos de **Aplicação da loja**, selecione **iOS**.
4. Selecione **Procurar na App Store**.
5. No painel **Pesquisar na loja de aplicativos** , selecione a localidade país/região da loja de aplicativos.
6. Na caixa **Procurar**, escreva o nome (ou parte do mesmo) da aplicação.  
    O Intune procura na loja e apresenta uma lista de resultados relevantes.
7. Na lista de resultados, selecione a aplicação que pretende e, em seguida, selecione **Selecionar**.
8. No painel **Adicionar aplicação**, selecione **Informações da aplicação** para configurar a aplicação.
9. No painel **Informações da aplicação**, adicione as informações da aplicação. Consoante a aplicação que tenha selecionado, alguns dos valores neste painel podem ter sido preenchidos automaticamente:
    - **Nome**: introduza o nome da aplicação tal como deve ser apresentado no portal da empresa. Certifique-se de que utiliza nomes de aplicação que sejam exclusivos. Se um nome de aplicação for duplicado, apenas um deles será apresentado aos utilizadores no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. Esta descrição é apresentada aos utilizadores no portal da empresa.
    - **Publicador**: introduza o nome do publicador da aplicação.
    - **URL da Loja de Aplicações**: escreva o URL da Loja de Aplicações da aplicação que pretende criar.
    - **Sistema operativo mínimo**: na lista, selecione a versão mínima do sistema operativo em que a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Tipo de dispositivo aplicável**: na lista, selecione os dispositivos utilizados pela aplicação.
    - **Categoria**: opcionalmente, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Desta forma, permitirá que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da Empresa**: selecione esta opção para apresentar o conjunto de aplicações em destaque na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação. Este campo só é visível para administradores e não para os utilizadores.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação (por exemplo, *Departamento de RH*). Este campo só é visível para administradores e não para os utilizadores.
    - **Notas**: opcionalmente, introduza quaisquer notas que queira associar a esta aplicação. Este campo só é visível para o administrador e não estará visível para os utilizadores finais.
    - **Logótipo**: opcionalmente, carregue um ícone que será associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
10. Selecione **OK**.
11. Selecione **Adicionar**.

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar.

## <a name="next-steps"></a>Próximos passos

- [Atribuir aplicações a grupos](apps-deploy.md)
