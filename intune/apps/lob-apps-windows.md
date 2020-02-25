---
title: Adicionar aplicações de linha de negócio Windows ao Microsoft Intune
titleSuffix: ''
description: Saiba como adicionar aplicações de linha de negócio (LOB) Windows com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2020
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
ms.openlocfilehash: ceb4d2354ca073cf05f526df7638aebf8f16d5b7
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569494"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Adicionar aplicações de linha de negócio Windows ao Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Uma aplicação de linha de negócio (LOB) é uma aplicação que adiciona a partir de um ficheiro de instalação da aplicação. Normalmente, este tipo de aplicação é criado internamente. Os seguintes passos fornecem orientação para ajudá-lo a adicionar uma aplicação LOB Windows ao Microsoft Intune.

> [!IMPORTANT]
> Ao implementar aplicações Win32 utilizando um ficheiro de instalação com a extensão .msi (embalada num ficheiro .intunewin utilizando a Ferramenta de Preparação de Conteúdo), considere utilizar a extensão de [gestão Intune](../apps/intune-management-extension.md). Se misturar a instalação de aplicações Win32 e aplicações de linha de negócio durante a inscrição no AutoPilot, a instalação da aplicação poderá falhar.  

## <a name="select-the-app-type"></a>Selecione o tipo de aplicativo

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações** > **Adicionar**.
3. No painel do **tipo de aplicação Select,** sob os **outros** tipos de aplicações, selecione **app Line-of-business**.
4. Clique em **Selecionar**. Os passos da **aplicação Add** são apresentados.

## <a name="step-1---app-information"></a>Passo 1 - Informações sobre aplicativos

### <a name="select-the-app-package-file"></a>Selecione o ficheiro de pacote de aplicativos

1. No painel de **aplicações Adicionar,** clique em Selecionar o ficheiro de pacote de **aplicativos**. 
2. No painel **Ficheiro de pacote de aplicação**, selecione o botão Procurar. Em seguida, selecione um ficheiro de instalação do Windows com a extensão **.msi**, **.appx**, ou **.appxbundle**.
   Os detalhes da aplicação serão apresentados.

    > [!NOTE]
    > As extensões de ficheiros de aplicações do Windows incluem **.msi**, **.appx**, **.appxbundle**, **.msix** e **.msixbundle**.  

3. Quando terminar, selecione **OK** no painel de **ficheiros** do pacote app para adicionar a aplicação.

### <a name="set-app-information"></a>Definir informações de aplicativos

1. Na página de informações da **App,** adicione os detalhes para a sua aplicação. Consoante a aplicação que tenha escolhido, alguns dos valores neste painel podem ser preenchidos automaticamente.
    - **Nome**: introduza o nome da aplicação tal como aparece no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só aparece uma das aplicações no portal da empresa.
    - **Descrição**: introduza a descrição da aplicação. A descrição aparece no portal da empresa.
    - **Publicador**: introduza o nome do publicador da aplicação.
    - **Sistema Operativo Mínimo**: na lista, escolha a versão mínima do sistema operativo no qual a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Categoria**: selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. As categorias permitem que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Mostre isto como uma aplicação em destaque no Portal da Empresa**: Mostrar a aplicação em destaque na página principal do portal da empresa quando os utilizadores navegam para apps.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL aparece no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL aparece no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação. Por exemplo, **Departamento de RH**.
    - **Notas**: introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: carregue um ícone associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
2. Clique em **Seguir** para exibir a página **de tags scope.**

## <a name="step-2---select-scope-tags-optional"></a>Passo 2 - Selecione etiquetas de âmbito (opcional)
Pode utilizar etiquetas de âmbito para determinar quem pode ver informações sobre aplicações do cliente no Intune. Para mais detalhes sobre etiquetas de âmbito, consulte [Use o controlo de acesso baseado em funções e as etiquetas](../fundamentals/scope-tags.md)de âmbito para TI distribuídos .

1. Clique em **Selecionar etiquetas** de âmbito para adicionar opcionalmente etiquetas de âmbito para a aplicação. 
2. Clique em **Seguir** para exibir a página **de Tarefas.**

## <a name="step-3---assignments"></a>Passo 3 - Atribuições

1. Selecione o **Necessário**, **Disponível para dispositivos matriculados,** ou **desinstale** as atribuições do grupo para a aplicação. Para mais informações, consulte [grupos Add para organizar utilizadores e dispositivos](~/fundamentals/groups-add.md) e [atribuir aplicações a grupos com](apps-deploy.md)o Microsoft Intune .
2. Clique em **Seguir** para exibir a página **Review + criar.** 

## <a name="step-4---review--create"></a>Passo 4 - Rever + criar

1. Reveja os valores e configurações que inseriu para a aplicação.
2. Quando terminar, clique em **Criar** para adicionar a app ao Intune.

    A lâmina **de visão geral** para a aplicação de linha de negócio seleção é apresentada.

A aplicação criada agora aparece na lista de aplicações. Na lista, pode atribuir as aplicações aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

## <a name="update-a-line-of-business-app"></a>Atualizar uma aplicação de linha de negócio

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

   > [!NOTE]
   > Para que o serviço Intune implemente com sucesso um novo ficheiro APPX para o dispositivo, tem de incrementar a cadeia `Version` no ficheiro AppxManifest.xml no seu pacote APPX.

## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Configurar uma aplicação MSI móvel de atualização automática para ignorar o processo de verificação da versão

Pode configurar uma aplicação MSI móvel de atualização automática conhecida para ignorar o processo de verificação da versão.

Algumas aplicações baseadas em instaladores MSI são automaticamente atualizadas pelo programador de aplicações ou por outro método de atualização. Para estas aplicações MSI atualizadas automaticamente, pode configurar a definição **Ignorar versão da aplicação** no painel **Informações da aplicação**. Quando muda esta opção para **Sim**, o Microsoft Intune não irá impor a versão da aplicação instalada no cliente Windows.

Esta funcionalidade é útil para evitar que ocorra uma condição race. Por exemplo, pode ocorrer uma condição race quando a aplicação é atualizada automaticamente pelo programador e pelo Intune. Ambos podem tentar impor uma versão da aplicação num cliente Windows, o que cria um conflito.

## <a name="next-steps"></a>Próximos passos

- A aplicação criada aparece na lista de aplicações. Agora pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

- Saiba mais sobre as formas como pode monitorizar as propriedades e atribuições da sua aplicação. Veja [Como monitorizar informações e atribuições da aplicação](apps-monitor.md).

- Saiba mais sobre o contexto da sua aplicação no Intune. Veja [Descrição geral do ciclo de vida das aplicações no Microsoft Intune](app-lifecycle.md).

- Saiba mais sobre aplicações Win32. Ver [Gestão de aplicações Win32](~/apps/apps-win32-app-management.md).
