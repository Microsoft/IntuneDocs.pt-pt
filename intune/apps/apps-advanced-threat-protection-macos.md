---
title: Adicione o Microsoft Defender ATP aos dispositivos macOS utilizando o Microsoft Intune
titleSuffix: ''
description: Saiba adicionar o Microsoft Defender ATP aos dispositivos macOS utilizando o Microsoft Intune.
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
ms.openlocfilehash: 6ae6e8a621b10ec969fa3fcfb2dfeabb8d5a7bdd
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569905"
---
# <a name="add-microsoft-defender-atp-to-macos-devices-using-microsoft-intune"></a>Adicione o Microsoft Defender ATP aos dispositivos macOS utilizando o Microsoft Intune

Antes de poder implementar, configurar, monitorizar ou proteger aplicações, deve adicioná-las ao Intune. Um dos tipos de [aplicações](~/apps/apps-add.md#app-types-in-microsoft-intune) disponíveis é o Microsoft Defender Advanced Threat Protection (ATP). Ao selecionar este tipo de aplicação em Intune, pode atribuir e instalar o Microsoft Defender ATP em dispositivos que gere o macOS. Este tipo de aplicação facilita a atribuição do Microsoft Defender ATP aos dispositivos macOS sem que utilize a ferramenta de embrulho da aplicação macOS. Para ajudar a manter as aplicações mais seguras e atualizadas, a aplicação vem com o Microsoft AutoUpdate (MAU).

## <a name="prerequisites"></a>Pré-requisitos
- O dispositivo macOS deve estar a funcionar macOS 10.13 ou mais tarde.
- O dispositivo macOS deve ter pelo menos 650 MB de espaço em disco.
- Desloque a extensão do núcleo em Intune. Consulte mais informações, consulte [Adicionar extensões de kernel macOS em Intune](~/configuration/kernel-extensions-overview-macos.md).

> [!IMPORTANT]
> A extensão do kernel só pode ser aprovada automaticamente se estiver presente no dispositivo antes da instalação da aplicação ATP Microsoft Defender. Caso contrário, os utilizadores verão a mensagem "System blocked" nos Macs e devem aprovar a extensão indo para **preferências** de segurança ou **preferências** de sistema > **Segurança e Privacidade** e, em seguida, selecionando **Permitir**. Para mais informações, consulte problemas de extensão de [kernel de Resolução no Microsoft Defender ATP para Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-support-kext).

## <a name="add-microsoft-defender-atp-to-intune"></a>Adicione o Microsoft Defender ATP ao Intune
Pode adicionar o Microsoft Defender ATP ao Intune utilizando os seguintes passos:

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações** > **Adicionar**.
3. Na lista do **tipo App** no ATP do **Microsoft Defender,** selecione **macOS**.

## <a name="configure-app-information"></a>Configurar as informações da aplicação
Neste passo, fornece informações sobre esta implementação da aplicação. Esta informação ajuda-o a identificar a aplicação em Intune, e ajuda os utilizadores a encontrar a app no portal da empresa.

1. Clique em **informações da App** para exibir o painel de informações da **App.**
2. No painel de informações da **App,** fornece informações sobre a implementação desta aplicação. Esta informação ajuda-o a identificar a aplicação em Intune, e ajuda os utilizadores a encontrar a app no portal da empresa.
    - **Nome**: Introduza o nome da aplicação tal como será apresentado no portal da empresa. Certifique-se de que todos os nomes são únicos. Se existir o mesmo nome duas vezes, só é apresentada uma das aplicações aos utilizadores no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. Por exemplo, pode enumerar os utilizadores visados na descrição.
    - **Publicador**: a Microsoft aparece como o publicador.
    - **Categoria**: em alternativa, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Esta definição facilita aos utilizadores encontrar a app quando navegam no portal da empresa.
    - **Exiba-o como uma aplicação em destaque no Portal da Empresa**: Selecione esta opção para exibir a aplicação em destaque na página principal do portal da empresa quando os utilizadores navegam para apps.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: a Microsoft aparece como o programador.
    - **Proprietário**: a Microsoft aparece como o proprietário.
    - **Notas**: opcionalmente, introduza quaisquer notas que queira associar a esta aplicação.
3. Selecione **OK**.

## <a name="select-scope-tags-optional"></a>Selecione etiquetas de âmbito (opcional)
Pode utilizar etiquetas de âmbito para determinar quem pode ver informações sobre aplicações do cliente no Intune. Para mais detalhes sobre etiquetas de âmbito, consulte Use o controlo de acesso baseado em funções e etiquetas de âmbito para TI distribuídos.
1.  Selecione **Scope (Tags)** > **Adicionar**.
2.  Utilize a caixa **Select** para procurar etiquetas de mira.
3.  Selecione a caixa de verificação junto às etiquetas de âmbito que pretende atribuir a esta aplicação.
4.  Clique em **selecionar** > **OK**.

## <a name="add-the-app"></a>Adicionar a aplicação
Quando tiver concluído a configuração, selecione **Adicionar** a partir do painel de aplicações da **App.** 

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. 

> [!NOTE]
> Atualmente, a Apple não fornece uma forma de a Intune desinstalar o Microsoft Defender ATP em dispositivos macOS.

## <a name="next-steps"></a>Próximos passos
- Para saber configurar o Microsoft Defender ATP em dispositivos macOS, consulte [configure Microsoft Defender ATP em dispositivos macOS](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-preferences).
- Para saber mais sobre como incluir e excluir atribuições de aplicações a partir de grupos de utilizadores, veja [Incluir e excluir atribuições de aplicações](~/apps/apps-inc-exl-assignments.md).
- [Atribuir aplicações a grupos](~/apps/apps-deploy.md)

