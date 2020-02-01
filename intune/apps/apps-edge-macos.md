---
title: Adicione o Microsoft Edge aos dispositivos macOS utilizando o Microsoft Intune
titleSuffix: ''
description: Saiba adicionar o Microsoft Edge aos dispositivos macOS utilizando o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
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
ms.openlocfilehash: 6ebcb81cd0f186a3fd23e0701d12ea871eab129a
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912578"
---
# <a name="add-microsoft-edge-to-macos-devices-using-microsoft-intune"></a>Adicione o Microsoft Edge aos dispositivos macOS utilizando o Microsoft Intune

Para poder implantar, configurar, monitorar ou proteger aplicativos, você deve adicioná-los ao Intune. Um dos tipos de [aplicativo](~/apps/apps-add.md#app-types-in-microsoft-intune) disponíveis é o Microsoft Edge *versão 77 e posterior*. Ao selecionar este tipo de aplicação em Intune, pode atribuir e instalar a versão 77 do Microsoft Edge *e, mais tarde,* aos dispositivos que gere o macOS. Este tipo de aplicação facilita a atribuição do Microsoft Edge aos dispositivos macOS sem que utilize a ferramenta de embrulho da aplicação macOS. Para ajudar a manter as aplicações mais seguras e atualizadas, a aplicação vem com o Microsoft AutoUpdate (MAU).

> [!IMPORTANT]
> Este tipo de aplicação está em **pré-visualização pública** e oferece canais de programador e beta para macOS. A implantação está em inglês (apenas EN), mas os usuários finais podem alterar o idioma de exibição no navegador em **configurações** > **idiomas**. 

> [!NOTE]
> O Microsoft Edge *versão 77 e mais tarde* está disponível para o Windows 10 também.

## <a name="prerequisites"></a>Pré-requisitos
- O dispositivo macOS deve estar a funcionar com o macOS 10.12 ou mais tarde antes de instalar o Microsoft Edge.

## <a name="add-microsoft-edge-to-intune"></a>Adicione microsoft edge ao Intune
Pode adicionar a versão 77 do Microsoft Edge e, mais tarde, a Intune utilizando os seguintes passos:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
3. Na lista do **tipo App** no **Microsoft Edge, versão 77 e posterior**, selecione **macOS**.

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
2. No painel **configurações do aplicativo** , selecione **estável**, **beta** ou **dev** na lista **canal** para determinar em qual canal de borda você implantará o aplicativo.

    - O canal **estável** é o canal recomendado para implantação ampla em ambientes corporativos. Ele é atualizado a cada seis semanas, cada versão incorporando melhorias do canal beta.
    - O canal **beta** é a experiência de visualização mais estável do Microsoft Edge e a melhor opção para um piloto completo em sua organização. Com as principais atualizações a cada seis semanas, cada versão incorpora os aprendizados e melhorias do canal de desenvolvimento.
    - O canal de **desenvolvimento** está pronto para os comentários empresariais no Windows, no Windows Server e no MacOS. Ele é atualizado toda semana e contém as melhorias e correções mais recentes.

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
Quando tiver concluído a configuração, selecione **Adicionar** a partir do painel de aplicações da **App.** 

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. 

> [!NOTE]
> Atualmente, a Apple não fornece uma forma de a Intune desinstalar o Microsoft Edge em dispositivos macOS.

## <a name="next-steps"></a>Próximos passos
- Para saber configurar o Microsoft Edge em dispositivos macOS, consulte [configure Microsoft Edge em dispositivos macOS](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac).
- Para saber mais sobre como incluir e excluir atribuições de aplicações a partir de grupos de utilizadores, veja [Incluir e excluir atribuições de aplicações](~/apps/apps-inc-exl-assignments.md).
- [Atribuir aplicações a grupos](~/apps/apps-deploy.md)

