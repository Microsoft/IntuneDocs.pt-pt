---
title: Adicionar o Microsoft Edge a dispositivos macOS usando o Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre como adicionar o Microsoft Edge a dispositivos macOS usando o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: c31dd652022ae0d394ab2229a0c25b362ad8574d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74563593"
---
# <a name="add-microsoft-edge-to-macos-devices-using-microsoft-intune"></a>Adicionar o Microsoft Edge a dispositivos macOS usando o Microsoft Intune

Para poder implantar, configurar, monitorar ou proteger aplicativos, você deve adicioná-los ao Intune. Um dos tipos de [aplicativo](~/apps/apps-add.md#app-types-in-microsoft-intune) disponíveis é o Microsoft Edge *versão 77 e posterior*. Ao selecionar esse tipo de aplicativo no Intune, você pode atribuir e instalar o Microsoft Edge *versão 77 e posterior* para os dispositivos gerenciados que executam o MacOS. Esse tipo de aplicativo facilita a atribuição do Microsoft Edge a dispositivos macOS sem a necessidade de usar a ferramenta de encapsulamento de aplicativos macOS. Para ajudar a manter os aplicativos mais seguros e atualizados, o aplicativo é fornecido com o Microsoft AutoUpdate (MAU).

> [!IMPORTANT]
> Este tipo de aplicativo está em **Visualização pública** e oferece canais de desenvolvedor e beta para MacOS. A implantação está em inglês (apenas EN), mas os usuários finais podem alterar o idioma de exibição no navegador em **configurações** > **idiomas**. 

> [!NOTE]
> O Microsoft Edge *versão 77 e posterior* está disponível para o Windows 10 também.

## <a name="prerequisites"></a>Pré-requisitos
- O dispositivo macOS deve estar executando o macOS 10,12 ou posterior antes de instalar o Microsoft Edge.

## <a name="add-microsoft-edge-to-intune"></a>Adicionar o Microsoft Edge ao Intune
Você pode adicionar o Microsoft Edge versão 77 e posterior ao Intune usando as seguintes etapas:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
3. Na lista **tipo de aplicativo** no **Microsoft Edge, versão 77 e posterior**, selecione **MacOS**.

## <a name="configure-app-information"></a>Configurar as informações da aplicação
Nesta etapa, você fornece informações sobre essa implantação de aplicativo. Essas informações ajudam a identificar o aplicativo no Intune e ajudam os usuários a localizar o aplicativo no portal da empresa.

1. Clique em **informações do aplicativo** para exibir o painel de informações do **aplicativo** .
2. No painel de **informações do aplicativo** , você fornece informações sobre essa implantação de aplicativo. Essas informações ajudam a identificar o aplicativo no Intune e ajudam os usuários a localizar o aplicativo no portal da empresa.
    - **Nome**: Insira o nome do aplicativo como ele será exibido no portal da empresa. Verifique se todos os nomes são exclusivos. Se existir o mesmo nome duas vezes, só é apresentada uma das aplicações aos utilizadores no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. Por exemplo, você pode listar os usuários de destino na descrição.
    - **Publicador**: a Microsoft aparece como o publicador.
    - **Categoria**: em alternativa, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Essa configuração torna mais fácil para os usuários localizar o aplicativo quando navegam pelo portal da empresa.
    - **Exibir como um aplicativo em destaque no portal da empresa**: Selecione esta opção para exibir o aplicativo de forma proeminente na página principal do portal da empresa quando os usuários procurarem aplicativos.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: a Microsoft aparece como o programador.
    - **Proprietário**: a Microsoft aparece como o proprietário.
    - **Notas**: opcionalmente, introduza quaisquer notas que queira associar a esta aplicação.
3. Selecione **OK**.

## <a name="configure-microsoft-edge-settings"></a>Configurar definições do Microsoft Edge
Nesta etapa, configure as opções de instalação para o aplicativo.

1. No painel **Adicionar aplicativo** , selecione **configurações do aplicativo**.
2. No painel **configurações do aplicativo** , o canal **beta** é selecionado automaticamente e não pode ser alterado.
    - O canal **beta** é a experiência de visualização mais estável do Microsoft Edge e a melhor opção para um piloto completo em sua organização. Com atualizações principais a cada seis semanas.

    > [!NOTE]
    > O logotipo do navegador Microsoft Edge é exibido com o aplicativo quando os usuários navegam pelo portal da empresa.
3.  Selecione **OK**.

## <a name="select-scope-tags-optional"></a>Selecionar marcas de escopo (opcional)
Você pode usar marcas de escopo para determinar quem pode ver as informações do aplicativo cliente no Intune. Para obter detalhes completos sobre marcas de escopo, consulte usar o controle de acesso baseado em função e marcas de escopo para distribuí-lo.
1.  Selecione **escopo (marcas)**  > **Adicionar**.
2.  Use a caixa **selecionar** para procurar marcas de escopo.
3.  Marque a caixa de seleção ao lado das marcas de escopo que você deseja atribuir a este aplicativo.
4.  Clique em **selecionar** > **OK**.

## <a name="add-the-app"></a>Adicionar a aplicação
Quando você tiver concluído a configuração, selecione **Adicionar** no painel **aplicativo de aplicativo** . 

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. 

> [!NOTE]
> Atualmente, a Apple não fornece uma maneira para o Intune desinstalar o Microsoft Edge em dispositivos macOS.

## <a name="next-steps"></a>Próximos passos
- Para saber como configurar o Microsoft Edge em dispositivos macOS, consulte [Configurar o Microsoft Edge em dispositivos MacOS](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac).
- Para saber mais sobre como incluir e excluir atribuições de aplicações a partir de grupos de utilizadores, veja [Incluir e excluir atribuições de aplicações](~/apps/apps-inc-exl-assignments.md).
- [Atribuir aplicações a grupos](~/apps/apps-deploy.md)

