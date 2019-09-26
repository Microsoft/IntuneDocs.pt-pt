---
title: Adicionar aplicações de linha de negócio Windows ao Microsoft Intune
titleSuffix: ''
description: Saiba como adicionar aplicações de linha de negócio (LOB) Windows com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: eae10cc2a7e1965d83d2c0c59d138b44eafcddf0
ms.sourcegitcommit: 3baa9965095bb874d9b8c7a3cbb4aa925ed52cae
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/30/2019
ms.locfileid: "71303388"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Adicionar aplicações de linha de negócio Windows ao Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Uma aplicação de linha de negócio (LOB) é uma aplicação que adiciona a partir de um ficheiro de instalação da aplicação. Normalmente, este tipo de aplicação é criado internamente. Os seguintes passos fornecem orientação para ajudá-lo a adicionar uma aplicação LOB Windows ao Microsoft Intune.

## <a name="step-1-specify-the-software-setup-file"></a>Passo 1: Especificar o ficheiro de configuração do software

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. Na carga de trabalho **Aplicações do cliente**, selecione **Gerir** > **Aplicações**.
5. Acima da lista de aplicações, selecione **Adicionar**.
6. No painel **Adicionar aplicação**, selecione **Aplicação de linha de negócio**.

## <a name="step-2-configure-the-app-package-file"></a>Passo 2: Configurar o ficheiro do pacote de aplicação

1. No painel **Adicionar aplicação**, selecione **Ficheiro de pacote de aplicação**.
2. No painel **Ficheiro de pacote de aplicação**, selecione o botão Procurar. Em seguida, selecione um ficheiro de instalação do Windows com a extensão **.msi**, **.appx** ou **.appxbundle**.

    > [!NOTE]
    > As extensões de ficheiros de aplicações do Windows incluem **.msi**, **.appx**, **.appxbundle**, **.msix** e **.msixbundle**.  

1. Quando tiver terminado, selecione **OK**.


## <a name="step-3-configure-app-information"></a>Passo 3: Configurar as informações da aplicação

1. No painel **Adicionar aplicação**, selecione **Informações da aplicação**.
2. No painel **Informações da aplicação**, configure as seguintes informações. Alguns dos valores neste painel podem ser preenchidos automaticamente.
    - **Nome**: introduza o nome da aplicação tal como aparece no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só aparece uma das aplicações no portal da empresa.
    - **Descrição**: Introduza uma descrição para a aplicação. A descrição aparece no portal da empresa.
    - **Publicador**: Introduza o nome do publicador da aplicação.
    - **Ignorar versão da aplicação**: defina como **Sim** se a aplicação for atualizada automaticamente pelo programador da aplicação. Esta opção aplica-se apenas a aplicações .msi para dispositivos móveis.
    - **Categoria**: selecione uma ou mais das categorias de aplicações incorporadas ou selecione uma categoria que tenha criado. As categorias permitem que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da Empresa**: Apresente a aplicação de forma bem visível na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de informações**: opcionalmente, introduza o URL de um site que contenha informações sobre a aplicação. O URL aparece no portal da empresa.
    - **URL de privacidade**: opcionalmente, introduza o URL de um site que contenha informações sobre a privacidade da aplicação. O URL aparece no portal da empresa.
    - **Argumentos da linha de comandos**: opcionalmente, pode introduzir qualquer argumento da linha de comandos que pretenda aplicar ao ficheiro .msi quando este for executado.  Um exemplo é **/q**. Não inclua o comando msiexec ou argumentos, como **/i** ou **/x**, pois eles são usados automaticamente. Para obter mais informações, consulte [Opções de linha de comando](https://docs.microsoft.com/windows/desktop/Msi/command-line-options). Se o. O arquivo MSI precisa de opções de linha de comando adicionais considere o uso do [Gerenciamento de aplicativos Win32](apps-win32-app-management.md).
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação. Por exemplo, **Departamento de RH**.
    - **Notas**: introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: carregue um ícone associado à aplicação. O ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
3. Quando tiver terminado, selecione **OK**.

## <a name="step-4-finish-up"></a>Passo 4: Concluir

1. No painel **Adicionar aplicação**, verifique se configurou as informações da aplicação corretamente.
2. Selecione **Adicionar** para carregar a aplicação para o Intune.

## <a name="step-5-update-a-line-of-business-app"></a>Passo 5: Atualizar uma aplicação de linha de negócio

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

   > [!NOTE]
   > Para que o serviço do Intune implante com êxito um novo arquivo Appx no dispositivo, você deve incrementar `Version` a cadeia de caracteres no arquivo AppxManifest. xml em seu pacote Appx.
    
## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Configurar uma aplicação MSI móvel de atualização automática para ignorar o processo de verificação da versão

Pode configurar uma aplicação MSI móvel de atualização automática conhecida para ignorar o processo de verificação da versão. 

Algumas aplicações baseadas no programa de instalação MSI são automaticamente atualizadas pelo programador da aplicação. Para estas aplicações MSI atualizadas automaticamente, pode configurar a definição **Ignorar versão da aplicação** no painel **Informações da aplicação**. Quando muda esta opção para **Sim**, o Microsoft Intune não irá impor a versão da aplicação instalada no cliente Windows. 

Esta funcionalidade é útil para evitar que ocorra uma condição race. Por exemplo, pode ocorrer uma condição race quando a aplicação é atualizada automaticamente pelo programador e pelo Intune. Ambos podem tentar impor uma versão da aplicação num cliente Windows, o que cria um conflito.

## <a name="next-steps"></a>Passos seguintes

- A aplicação criada aparece na lista de aplicações. Agora pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

- Saiba mais sobre as formas como pode monitorizar as propriedades e atribuições da sua aplicação. Veja [Como monitorizar informações e atribuições da aplicação](apps-monitor.md).

- Saiba mais sobre o contexto da sua aplicação no Intune. Veja [Descrição geral do ciclo de vida das aplicações no Microsoft Intune](app-lifecycle.md).
