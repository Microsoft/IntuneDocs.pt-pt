---
title: "Como adicionar aplicações de linha de negócios Windows ao Microsoft Intune"
titlesuffix: 
description: "Saiba como adicionar aplicações de linha de negócio (LOB) Windows ao Microsoft Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/16/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b687b71f9d264364ff758fdd46b0739465c16865
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-add-windows-line-of-business-lob-apps-to-microsoft-intune"></a>Como adicionar aplicações de linha de negócio (LOB) Windows ao Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Uma aplicação de linha de negócio (LOB) é uma aplicação que adiciona a partir de um ficheiro de instalação da aplicação. Normalmente, estes tipos de aplicações são escritos internamente. Os seguintes passos fornecem orientação para ajudá-lo a adicionar uma aplicação LOB Windows ao Microsoft Intune.

## <a name="step-1---specify-the-software-setup-file"></a>Passo 1 – Especificar o ficheiro de configuração do software

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** + **Intune**.
3. No painel **Intune**, escolha **Gerir aplicações**.
4. Na carga de trabalho **Aplicações móveis**, escolha **Gerir** > **Aplicações**.
5. Acima da lista de aplicações, escolha **Adicionar**.
6. No painel **Adicionar Aplicação**, escolha **Aplicação de linha de negócio**.

## <a name="step-2---configure-the-app-package-file"></a>Passo 2 – Configurar o ficheiro de pacote de aplicação

1. No painel **Adicionar aplicação**, escolha o ficheiro **Pacote de aplicação**.
2. No painel de ficheiros **Pacote de aplicação**, selecione o botão Procurar e selecione um ficheiro de instalação do Windows com a extensão **.msi**, **.appx** ou **.appxbundle**.
3. Quando terminar, escolha **OK**.


## <a name="step-3---configure-app-information"></a>Passo 3 – Configurar as informações da aplicação

1. No painel **Adicionar aplicação**, escolha o ficheiro **Pacote de aplicação**.
2. No painel **Informações da aplicação**, configure as seguintes informações (alguns dos valores neste painel poderão ser preenchidos automaticamente):
    - **Nome** – Introduza o nome da aplicação tal como será apresentado no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só é apresentada uma das aplicações aos utilizadores no portal da empresa.
    - **Descrição** - Introduza uma descrição para a aplicação. A descrição é apresentada aos utilizadores no portal da empresa.
    - **Publicador** – Introduza o nome do publicador da aplicação.
    - **Categoria** – selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. Categorizar aplicações facilita a localização da aplicação por parte dos utilizadores, à medida que procuram no portal da empresa.
    - **Apresentar esta aplicação em destaque no Portal da Empresa** – apresente a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações** – opcionalmente, pode introduzir o URL para um site que contenha informações sobre a aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade** – opcionalmente, pode introduzir o URL para um site que contenha informações sobre a privacidade da aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Argumentos da linha de comandos** – opcionalmente, pode introduzir qualquer argumento da linha de comandos que pretenda aplicar ao ficheiro .msi quando este for executado, como **/q**.
    - **Programador** – opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário** – Opcionalmente, introduza um nome para o proprietário desta aplicação, por exemplo, **Departamento de RH**.
    - **Notas** – Introduza quaisquer notas que pretenda associar esta aplicação.
    - **Logótipo** – carregue um ícone associado à aplicação. O ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
3. Quando terminar, escolha **OK**.

## <a name="step-4---finish-up"></a>Passo 4 – Concluir

1. No painel **Adicionar aplicação**, verifique se configurou as informações da aplicação corretamente.
2. Escolha **Adicionar** para carregar a aplicação para o Intune.

## <a name="step-5---update-a-line-of-business-app"></a>Passo 5 – Atualizar uma aplicação de linha de negócio

[!INCLUDE[shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

## <a name="configuring-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Configurar uma aplicação MSI móvel de atualização automática para ignorar o processo de verificação da versão

Pode configurar uma aplicação MSI móvel de atualização automática conhecida para ignorar o processo de verificação da versão. Algumas aplicações baseadas em instalação MSI são automaticamente atualizadas pelo programador da aplicação. Para estas aplicações MSI atualizadas automaticamente, pode configurar a definição **Ignorar versão da aplicação** no painel **Informações da aplicação**. Quando esta opção está definida para **Sim**, o Microsoft Intune não irá impor a versão da aplicação instalada no cliente Windows. Esta funcionalidade é útil para evitar que ocorra uma condição race. Por exemplo, este tipo de condição race poderia ocorrer quando a aplicação de atualização automática por parte do programador também é atualizada pelo Intune. Ambos podem tentar impor uma versão da aplicação no cliente Windows, o que pode criar um conflito.

## <a name="next-steps"></a>Passos seguintes

A aplicação que criou é apresentada na lista de aplicações. Agora pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

Saiba mais sobre as formas como pode monitorizar as propriedades e atribuições da sua aplicação. Para obter mais informações, consulte [Como monitorizar informações e atribuições da aplicação](apps-monitor.md).

Saiba mais sobre o contexto da sua aplicação no Intune. Para obter mais informações, consulte [Descrição geral dos ciclos de vida de dispositivos e aplicações](introduction-device-app-lifecycles.md)