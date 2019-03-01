---
title: Adicionar aplicações de linha de negócio Windows ao Microsoft Intune
titlesuffix: ''
description: Saiba como adicionar uma aplicação de linha de negócio (LOB) Windows através do Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9002397e4cdaabd2d05482e7e1dcdaa1558273e
ms.sourcegitcommit: c89e41e7bd546e4feceae26d82326230a16a713c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017086"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Adicionar aplicações de linha de negócio Windows ao Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Uma aplicação de linha de negócio (LOB) é uma aplicação que adiciona a partir de um ficheiro de instalação da aplicação. Normalmente, este tipo de aplicação é criado internamente. Os seguintes passos fornecem orientação para ajudá-lo a adicionar uma aplicação LOB Windows ao Microsoft Intune.

## <a name="step-1-specify-the-software-setup-file"></a>Passo 1: Especifique o ficheiro de configuração de software

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. Na carga de trabalho **Aplicações do cliente**, selecione **Gerir** > **Aplicações**.
5. Acima da lista de aplicações, selecione **Adicionar**.
6. No painel **Adicionar aplicação**, selecione **Aplicação de linha de negócio**.

## <a name="step-2-configure-the-app-package-file"></a>Passo 2: Configurar o ficheiro de pacote de aplicação

1. No painel **Adicionar aplicação**, selecione **Ficheiro de pacote de aplicação**.
2. No painel **Ficheiro de pacote de aplicação**, selecione o botão Procurar. Em seguida, selecione um ficheiro de instalação do Windows com a extensão **.msi**, **.appx** ou **.appxbundle**.

    > [!NOTE]
    > As extensões de ficheiros de aplicações do Windows incluem **.msi**, **.appx**, **.appxbundle**, **.msix** e **.msixbundle**.  

1. Quando tiver terminado, selecione **OK**.


## <a name="step-3-configure-app-information"></a>Passo 3: Configurar as informações da aplicação

1. No painel **Adicionar aplicação**, selecione **Informações da aplicação**.
2. No painel **Informações da aplicação**, configure as seguintes informações. Alguns dos valores neste painel podem ser preenchidos automaticamente.
    - **Nome**: Introduza o nome da aplicação tal como aparece no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só aparece uma das aplicações no portal da empresa.
    - **Descrição**: Introduza uma descrição para a aplicação. A descrição aparece no portal da empresa.
    - **Publisher**: Introduza o nome do publicador da aplicação.
    - **Ignorar versão da aplicação**: Defina como **Sim** se o programador da aplicação atualiza automaticamente a aplicação. Esta opção aplica-se apenas a aplicações .msi para dispositivos móveis.
    - **Categoria**: Selecione uma ou mais das categorias de aplicações incorporadas ou selecione uma categoria que criou. As categorias permitem que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da empresa**: Apresente a aplicação de forma bem visível na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de informações**: Opcionalmente, introduza o URL de um site que contenha informações sobre a aplicação. O URL aparece no portal da empresa.
    - **URL de privacidade**: Opcionalmente, introduza o URL de um site que contém informações de privacidade para a aplicação. O URL aparece no portal da empresa.
    - **Argumentos da linha de comandos**: Opcionalmente, introduza qualquer argumento da linha de comandos que pretende aplicar ao ficheiro. msi quando este for executado. Um exemplo é **/q**.
    - **Desenvolvedor**: Opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: Opcionalmente, introduza um nome para o proprietário desta aplicação. Por exemplo, **Departamento de RH**.
    - **Notas de**: Introduza quaisquer notas que pretende associar esta aplicação.
    - **Logótipo**: Carregue um ícone que está associado à aplicação. O ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
3. Quando tiver terminado, selecione **OK**.

## <a name="step-4-finish-up"></a>Passo 4: Concluir

1. No painel **Adicionar aplicação**, verifique se configurou as informações da aplicação corretamente.
2. Selecione **Adicionar** para carregar a aplicação para o Intune.

## <a name="step-5-update-a-line-of-business-app"></a>Passo 5: Atualizar uma aplicação de linha de negócio

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Configurar uma aplicação MSI móvel de atualização automática para ignorar o processo de verificação da versão

Pode configurar uma aplicação MSI móvel de atualização automática conhecida para ignorar o processo de verificação da versão. 

Algumas aplicações baseadas no programa de instalação MSI são automaticamente atualizadas pelo programador da aplicação. Para estas aplicações MSI atualizadas automaticamente, pode configurar a definição **Ignorar versão da aplicação** no painel **Informações da aplicação**. Quando muda esta opção para **Sim**, o Microsoft Intune não irá impor a versão da aplicação instalada no cliente Windows. 

Esta funcionalidade é útil para evitar que ocorra uma condição race. Por exemplo, pode ocorrer uma condição race quando a aplicação é atualizada automaticamente pelo programador e pelo Intune. Ambos podem tentar impor uma versão da aplicação num cliente Windows, o que cria um conflito.

## <a name="next-steps"></a>Passos Seguintes

- A aplicação criada aparece na lista de aplicações. Agora pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

- Saiba mais sobre as formas como pode monitorizar as propriedades e atribuições da sua aplicação. Veja [Como monitorizar informações e atribuições da aplicação](apps-monitor.md).

- Saiba mais sobre o contexto da sua aplicação no Intune. Veja [Descrição geral dos ciclos de vida de dispositivos e aplicações](introduction-device-app-lifecycles.md).
