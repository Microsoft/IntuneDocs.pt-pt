---
title: Adicionar aplicações de linha de negócio Windows ao Microsoft Intune
titleSuffix: ''
description: Saiba como adicionar aplicações de linha de negócio (LOB) Windows com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6f4c7b5e3cca06a3ec10ea1b3dfc5e45546c841f
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563910"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Adicionar aplicações de linha de negócio Windows ao Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Uma aplicação de linha de negócio (LOB) é uma aplicação que adiciona a partir de um ficheiro de instalação da aplicação. Normalmente, este tipo de aplicação é criado internamente. Os seguintes passos fornecem orientação para ajudá-lo a adicionar uma aplicação LOB Windows ao Microsoft Intune.

> [!IMPORTANT]
> Ao implantar aplicativos Win32 usando um arquivo de instalação com a extensão *. msi* , considere usar a [extensão de gerenciamento do Intune](../apps/intune-management-extension.md). Se você misturar a instalação de aplicativos Win32 e aplicativos de linha de negócios durante o registro do AutoPilot, a instalação do aplicativo poderá falhar.  

## <a name="step-1-specify-the-software-setup-file"></a>Passo 1: especificar o ficheiro de configuração do software

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
3. No painel **Adicionar aplicativo** , selecione **aplicativo de linha de negócios** como o tipo de **aplicativo**.

## <a name="step-2-configure-the-app-package-file"></a>Passo 2: configurar o ficheiro de pacote de aplicação

1. No painel **Adicionar aplicação**, selecione **Ficheiro de pacote de aplicação**.
2. No painel **Ficheiro de pacote de aplicação**, selecione o botão Procurar. Em seguida, selecione um ficheiro de instalação do Windows com a extensão **.msi**, **.appx** ou **.appxbundle**.

    > [!NOTE]
    > As extensões de ficheiros de aplicações do Windows incluem **.msi**, **.appx**, **.appxbundle**, **.msix** e **.msixbundle**.  

1. Quando tiver terminado, selecione **OK**.


## <a name="step-3-configure-app-information"></a>Passo 3: configurar as informações da aplicação

1. No painel **Adicionar aplicação**, selecione **Informações da aplicação**.
2. No painel **Informações da aplicação**, configure as informações seguintes. Alguns dos valores neste painel podem ser preenchidos automaticamente.
    - **Nome**: introduza o nome da aplicação tal como aparece no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só aparece uma das aplicações no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. A descrição aparece no portal da empresa.
    - **Publicador**: introduza o nome do publicador da aplicação.
    - **Ignorar versão da aplicação**: defina como **Sim** se a aplicação for atualizada automaticamente pelo programador da aplicação. Esta opção aplica-se apenas a aplicações .msi para dispositivos móveis.
    - **Categoria**: selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. As categorias permitem que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar esta aplicação em destaque no Portal da Empresa**: apresente a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações**: opcionalmente, pode introduzir o URL para um site que contenha informações sobre a aplicação. O URL aparece no portal da empresa.
    - **URL de Privacidade**: opcionalmente, pode introduzir o URL para um site que contenha informações sobre a privacidade da aplicação. O URL aparece no portal da empresa.
    - **Argumentos da linha de comandos**: opcionalmente, pode introduzir qualquer argumento da linha de comandos que pretenda aplicar ao ficheiro .msi quando este for executado.  Um exemplo é **/q**. Não inclua o comando msiexec ou argumentos, como **/i** ou **/x**, pois eles são usados automaticamente. Para obter mais informações, consulte [Opções de linha de comando](https://docs.microsoft.com/windows/desktop/Msi/command-line-options). Se o. O arquivo MSI precisa de opções de linha de comando adicionais considere o uso do [Gerenciamento de aplicativos Win32](app-management.md).
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação. Por exemplo, **Departamento de RH**.
    - **Notas**: introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: carregue um ícone associado à aplicação. O ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
3. Quando tiver terminado, selecione **OK**.

## <a name="step-4-finish-up"></a>Passo 4: concluir

1. No painel **Adicionar aplicação**, verifique se configurou as informações da aplicação corretamente.
2. Selecione **Adicionar** para carregar a aplicação para o Intune.

## <a name="step-5-update-a-line-of-business-app"></a>Passo 5: atualizar uma aplicação de linha de negócio

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

   > [!NOTE]
   > Para que o serviço do Intune implante com êxito um novo arquivo APPX no dispositivo, você deve incrementar a `Version` cadeia de caracteres no arquivo AppxManifest. xml em seu pacote APPX.

## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Configurar uma aplicação MSI móvel de atualização automática para ignorar o processo de verificação da versão

Pode configurar uma aplicação MSI móvel de atualização automática conhecida para ignorar o processo de verificação da versão.

Alguns aplicativos baseados no instalador MSI são atualizados automaticamente pelo desenvolvedor do aplicativo ou por outro método de atualização. Para estas aplicações MSI atualizadas automaticamente, pode configurar a definição **Ignorar versão da aplicação** no painel **Informações da aplicação**. Quando muda esta opção para **Sim**, o Microsoft Intune não irá impor a versão da aplicação instalada no cliente Windows.

Esta funcionalidade é útil para evitar que ocorra uma condição race. Por exemplo, pode ocorrer uma condição race quando a aplicação é atualizada automaticamente pelo programador e pelo Intune. Ambos podem tentar impor uma versão da aplicação num cliente Windows, o que cria um conflito.

## <a name="next-steps"></a>Próximos passos

- A aplicação criada aparece na lista de aplicações. Agora pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

- Saiba mais sobre as formas como pode monitorizar as propriedades e atribuições da sua aplicação. Veja [Como monitorizar informações e atribuições da aplicação](apps-monitor.md).

- Saiba mais sobre o contexto da sua aplicação no Intune. Veja [Descrição geral do ciclo de vida das aplicações no Microsoft Intune](app-lifecycle.md).
