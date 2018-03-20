---
title: "Como adicionar aplicações de linha de negócio Windows Phone ao Microsoft Intune"
titlesuffix: 
description: "Saiba como adicionar aplicações de linha de negócio (LOB) Windows Phone ao Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8466a77929620ef9ef7c1559dae62990730d0acd
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-windows-phone-line-of-business-lob-apps-to-microsoft-intune"></a>Como adicionar aplicações de linha de negócio (LOB) Windows Phone ao Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize as informações neste artigo para ajudá-lo a adicionar aplicações de linha de negócio Windows Phone ao Intune. Uma aplicação de linha de negócio (LOB) é uma aplicação que adiciona ao Intune a partir de um ficheiro de instalação da aplicação. Normalmente, estes tipos de aplicações são escritos internamente. O Intune instala a aplicação LOB no dispositivo do utilizador. 

## <a name="step-1---specify-the-software-setup-file"></a>Passo 1 – Especificar o ficheiro de configuração do software

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações móveis**.
4. Na carga de trabalho **Aplicações móveis**, escolha **Gerir** > **Aplicações**.
5. Acima da lista de aplicações, escolha **Adicionar**.
6. No painel **Adicionar aplicação**, selecione **Aplicação de linha de negócio**.

## <a name="step-2---configure-the-app-package-file"></a>Passo 2 – Configurar o ficheiro de pacote de aplicação

1. No painel **Adicionar aplicação**, selecione **Ficheiro de pacote de aplicação**.
2. No painel do **Ficheiro de pacote de aplicação**, selecione o botão Procurar e selecione um ficheiro de instalação do Windows Phone com a extensão **.xap**.
3. Quando terminar, escolha **OK**.


## <a name="step-3---configure-app-information"></a>Passo 3 – Configurar as informações da aplicação

1. No painel **Adicionar aplicação**, selecione **Ficheiro de pacote de aplicação**.
2. No painel **Informações da aplicação**, configure as informações da aplicação. Consoante a aplicação que tenha escolhido, alguns dos valores neste painel podem ter sido preenchidos automaticamente:
    - **Nome** – Introduza o nome da aplicação tal como será apresentado no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só é apresentada uma das aplicações aos utilizadores no portal da empresa.
    - **Descrição** - Introduza uma descrição para a aplicação. A descrição é apresentada aos utilizadores no portal da empresa.
    - **Publicador** – Introduza o nome do publicador da aplicação.
    - **Ignorar versão da aplicação** – defina como **Sim** se a aplicação for atualizada automaticamente pelo programador da aplicação.
    - **Categoria** – selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. Utilizar categorias irá permitir que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar esta aplicação em destaque no Portal da Empresa** – Apresente a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações** – Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade** – Opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador** – opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário** – Opcionalmente, introduza um nome para o proprietário desta aplicação, por exemplo, **Departamento de RH**.
    - **Notas** – Introduza quaisquer notas que pretenda associar esta aplicação.
    - **Logótipo** – carregue um ícone associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
3. Quando terminar, escolha **OK**.

## <a name="step-4---finish-up"></a>Passo 4 – Concluir

1. No painel **Adicionar aplicação**, verifique se configurou as informações corretamente.
2. Escolha **Adicionar** para carregar a aplicação para o Intune.

## <a name="next-steps"></a>Próximos passos

- A aplicação que criou é apresentada na lista de aplicações. Agora pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

- Saiba mais sobre as formas como pode monitorizar as propriedades e atribuições da sua aplicação. Para obter mais informações, consulte [Como monitorizar informações e atribuições da aplicação](apps-monitor.md).

- Saiba mais sobre o contexto da sua aplicação no Intune. Para obter mais informações, consulte [Descrição geral dos ciclos de vida de dispositivos e aplicações](introduction-device-app-lifecycles.md)
