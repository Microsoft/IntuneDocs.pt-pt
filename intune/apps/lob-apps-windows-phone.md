---
title: Adicionar aplicações de linha de negócio Windows Phone ao Microsoft Intune
titleSuffix: ''
description: Saiba como adicionar aplicações de linha de negócio (LOB) Windows Phone com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 31e7a1502f984218f92c6b41db4fb76b2d7f2d15
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731128"
---
# <a name="add-a-windows-phone-line-of-business-app-to-microsoft-intune"></a>Adicionar aplicações de linha de negócio Windows Phone ao Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Utilize as informações neste artigo para adicionar aplicações de linha de negócio (LOB) Windows Phone ao Microsoft Intune. Uma aplicação LOB é uma aplicação que adiciona ao Intune a partir de um ficheiro de instalação da aplicação. Normalmente, este tipo de aplicação é criado internamente. O Intune instala a aplicação LOB no dispositivo do utilizador. 

## <a name="step-1-specify-the-software-setup-file"></a>Passo 1: Especificar o ficheiro de configuração do software

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. Na carga de trabalho **Aplicações do cliente**, selecione **Gerir** > **Aplicações**.
5. Acima da lista de aplicações, selecione **Adicionar**.
6. No painel **Adicionar aplicação**, selecione **Aplicação de linha de negócio**.

## <a name="step-2-configure-the-app-package-file"></a>Passo 2: Configurar o ficheiro do pacote de aplicação

1. No painel **Adicionar aplicação**, selecione **Ficheiro de pacote de aplicação**.
2. No painel **Ficheiro de pacote de aplicação**, selecione o botão Procurar. Em seguida, selecione um ficheiro de instalação do Windows Phone com a extensão **.xap**.
3. Quando tiver terminado, selecione **OK**.


## <a name="step-3-configure-app-information"></a>Passo 3: Configurar as informações da aplicação

1. No painel **Adicionar aplicação**, selecione **Informações da aplicação**.
2. No painel **Informações da aplicação**, configure as informações da aplicação. Consoante a aplicação que tenha escolhido, alguns dos valores neste painel podem ser preenchidos automaticamente.
    - **Nome**: introduza o nome da aplicação tal como aparece no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só aparece uma das aplicações no portal da empresa.
    - **Descrição**: Introduza uma descrição para a aplicação. A descrição aparece no portal da empresa.
    - **Publicador**: Introduza o nome do publicador da aplicação.
    - **Categoria**: selecione uma ou mais das categorias de aplicações incorporadas ou selecione uma categoria que tenha criado. As categorias permitem que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da Empresa**: Apresente a aplicação de forma bem visível na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações**: Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL aparece no portal da empresa.
    - **URL de Privacidade**: Opcionalmente, introduza o URL de um site que contenha informações sobre a privacidade desta aplicação. O URL aparece no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação. Por exemplo, **Departamento de RH**.
    - **Notas**: introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: carregue um ícone associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
3. Quando tiver terminado, selecione **OK**.

## <a name="step-4-finish-up"></a>Passo 4: Concluir

1. No painel **Adicionar aplicação**, verifique se configurou as informações corretamente.
2. Selecione **Adicionar** para carregar a aplicação para o Intune.

## <a name="next-steps"></a>Passos seguintes

- A aplicação criada aparece na lista de aplicações. Agora pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

- Saiba mais sobre as formas como pode monitorizar as propriedades e atribuições da sua aplicação. Veja [Como monitorizar informações e atribuições da aplicação](apps-monitor.md).

- Saiba mais sobre o contexto da sua aplicação no Intune. Veja [Descrição geral dos ciclos de vida de dispositivos e aplicações](../fundamentals/device-lifecycle.md).
