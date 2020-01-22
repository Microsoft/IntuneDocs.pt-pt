---
title: Adicionar o Microsoft Edge para Windows 10 ao Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre como adicionar o Microsoft Edge para Windows ao Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/17/2020
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
ms.openlocfilehash: 42f1c8fae156eaf08203f4a88cad8433749940ac
ms.sourcegitcommit: b6fe084b0419b3c9d456a8b0439b00f8c784db23
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/21/2020
ms.locfileid: "76294800"
---
# <a name="add-microsoft-edge-for-windows-10-to-microsoft-intune"></a>Adicionar o Microsoft Edge para Windows 10 ao Microsoft Intune

Para poder implantar, configurar, monitorar ou proteger aplicativos, você deve adicioná-los ao Intune. Um dos tipos de [aplicativo](~/apps/apps-add.md#app-types-in-microsoft-intune) disponíveis é o Microsoft Edge *versão 77 e posterior*. Ao selecionar esse tipo de aplicativo no Intune, você pode atribuir e instalar o Microsoft Edge *versão 77 e posterior* para os dispositivos gerenciados que executam o Windows 10.

> [!IMPORTANT]
> Esse tipo de aplicativo está em **Visualização pública** e oferece canais estáveis, beta e de desenvolvimento para o Windows 10. A implantação está em inglês (apenas EN), mas os usuários finais podem alterar o idioma de exibição no navegador em **configurações** > **idiomas**. O Microsoft Edge é um aplicativo Win32 instalado no contexto do sistema e em arquiteturas semelhantes (aplicativo x86 no sistema operacional x86 e aplicativo x64 no sistema operacional x64). O Intune detectará quaisquer instalações preexistentes do Microsoft Edge. Se estiver instalado no contexto do usuário, uma instalação do sistema irá substituí-lo. Se ele estiver instalado no contexto do sistema, o sucesso da instalação será relatado. Além disso, as atualizações automáticas do Microsoft Edge são **ativadas** por padrão e o Microsoft Edge não pode ser desinstalado.

> [!NOTE]
> O Microsoft Edge *versão 77 e posterior* também está disponível para MacOS.
> 
> Você não pode usar a implantação de aplicativo interna do Microsoft Edge para computadores de ingresso no local de trabalho. A implantação de aplicativo interno requer a extensão de gerenciamento do Intune, que existe somente para dispositivos ingressados no AAD. Você ainda pode implantar o Microsoft Edge *versão 77 e posterior* usando um *. msi* carregado em **aplicativos**, consulte [Adicionar um aplicativo de linha de negócios do Windows para Microsoft Intune](~/apps/lob-apps-windows.md).

## <a name="prerequisites"></a>Pré-requisitos
- O Windows 10 RS2 e superior é necessário.
- Todas as versões pré-instaladas do Microsoft Edge *versão 77 e posterior* para todos os canais no contexto do usuário serão substituídas pelo Edge instalado no contexto do sistema.

## <a name="configure-the-app-in-intune"></a>Configurar o aplicativo no Intune
Você pode adicionar um Microsoft Edge versão 77 e posterior ao Intune usando as seguintes etapas:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
3. Na lista **tipo de aplicativo** no **Microsoft Edge, versão 77 e posterior**, selecione **Windows 10**.

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

## <a name="configure-app-settings"></a>Configurar as definições da aplicação
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
Quando você concluir a configuração do aplicativo, selecione **Adicionar** no painel **aplicativo de aplicativo** . 

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. 

> [!NOTE]
> No momento, se você cancelar a atribuição da implantação do Microsoft Edge, ela permanecerá no dispositivo.

## <a name="troubleshooting"></a>Resolução de Problemas
**Microsoft Edge versão 77 e posterior para Windows 10:**<br>
O Intune usa a extensão de gerenciamento do Intune para baixar e implantar o instalador do Microsoft Edge em dispositivos Windows 10 atribuídos e, em seguida, comunica as configurações de implantação ao instalador do Microsoft Edge, que baixa e instala o navegador Microsoft Edge diretamente da CDN. Referencie os [pré-requisitos para a extensão de gerenciamento do Intune](~/apps/intune-management-extension.md#prerequisites)e as práticas recomendadas descritas em acessando o serviço de atualização do Azure e a CDN para garantir que sua configuração de rede permita que os dispositivos Windows 10 acessem esses locais. Além disso, para permitir o acesso a arquivos de instalação de uma CDN para instalar o navegador, você precisa permitir o acesso a Windows Update pontos de extremidade. Para obter mais informações, consulte [gerenciar pontos de extremidade de conexão para o Windows 10, versão 1809 – Windows Update](https://docs.microsoft.com/windows/privacy/manage-windows-1809-endpoints#windows-update) e [pontos de extremidade de rede para Microsoft Intune](~/fundamentals/intune-endpoints.md).

## <a name="next-steps"></a>Próximos passos
- [Atribuir aplicações a grupos](~/apps/apps-deploy.md)
