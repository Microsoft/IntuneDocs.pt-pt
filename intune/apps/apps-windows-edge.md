---
title: Adicionar o Microsoft Edge para Windows 10 ao Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre como adicionar o Microsoft Edge para Windows ao Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/03/2020
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
ms.openlocfilehash: 8d5082376c42ff3b92e3979a53b6deac3e59c88e
ms.sourcegitcommit: 32391f74241ee3289a76ccd5319fe700b800d427
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2020
ms.locfileid: "77075812"
---
# <a name="add-microsoft-edge-for-windows-10-to-microsoft-intune"></a>Adicionar o Microsoft Edge para Windows 10 ao Microsoft Intune

Para poder implantar, configurar, monitorar ou proteger aplicativos, você deve adicioná-los ao Intune. Um dos tipos de [aplicações](~/apps/apps-add.md#app-types-in-microsoft-intune) disponíveis é o Microsoft Edge *versão 77 e mais tarde.* Ao selecionar este tipo de aplicação em Intune, pode atribuir e instalar a versão 77 do Microsoft Edge *e, mais tarde,* aos dispositivos que gere que executam o Windows 10.

> [!IMPORTANT]
> Este tipo de aplicação está em **pré-visualização pública** e oferece canais estáveis, beta e dev para windows 10. A implementação é apenas em inglês (EN), no entanto os utilizadores finais podem alterar o idioma de exibição no navegador em **Definições** > **Idiomas**. O Microsoft Edge é um aplicativo Win32 instalado no contexto do sistema e em arquiteturas semelhantes (aplicativo x86 no sistema operacional x86 e aplicativo x64 no sistema operacional x64). O Intune detectará quaisquer instalações preexistentes do Microsoft Edge. Se estiver instalado no contexto do usuário, uma instalação do sistema irá substituí-lo. Se ele estiver instalado no contexto do sistema, o sucesso da instalação será relatado. Além disso, as atualizações automáticas do Microsoft Edge estão **on** por padrão.

> [!NOTE]
> A *versão 77 do* Microsoft Edge está disponível para o macOS também.
> 
> Você não pode usar a implantação de aplicativo interna do Microsoft Edge para computadores de ingresso no local de trabalho. A implantação de aplicativo interno requer a extensão de gerenciamento do Intune, que existe somente para dispositivos ingressados no AAD. Ainda pode implementar a versão 77 do Microsoft Edge *e, mais tarde,* utilizar uma *.msi* enviada para **apps**, consulte [adicionar uma aplicação de linha de negócio do Windows ao Microsoft Intune](~/apps/lob-apps-windows.md).

## <a name="prerequisites"></a>Pré-requisitos
- O Windows 10 RS2 e superior é necessário.
- Quaisquer versões pré-instaladas da versão 77 do Microsoft Edge *e posteriormente* para todos os canais no contexto do utilizador serão substituídas com o Edge instalado no contexto do sistema.

## <a name="configure-the-app-in-intune"></a>Configurar o aplicativo no Intune
Você pode adicionar um Microsoft Edge versão 77 e posterior ao Intune usando as seguintes etapas:

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações** > **Adicionar**.
3. Na lista do **tipo App** no **Microsoft Edge, versão 77 e posterior**, selecione O Windows **10**.

## <a name="configure-app-information"></a>Configurar as informações da aplicação
Nesta etapa, você fornece informações sobre essa implantação de aplicativo. Essas informações ajudam a identificar o aplicativo no Intune e ajudam os usuários a localizar o aplicativo no portal da empresa.

1. Clique em **informações da App** para exibir o painel de informações da **App.**
2. No painel de informações da **App,** fornece informações sobre a implementação desta aplicação. Essas informações ajudam a identificar o aplicativo no Intune e ajudam os usuários a localizar o aplicativo no portal da empresa.
    - **Nome**: Introduza o nome da aplicação tal como será apresentado no portal da empresa. Verifique se todos os nomes são exclusivos. Se existir o mesmo nome duas vezes, só é apresentada uma das aplicações aos utilizadores no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. Por exemplo, você pode listar os usuários de destino na descrição.
    - **Publicador**: a Microsoft aparece como o publicador.
    - **Categoria**: em alternativa, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Essa configuração torna mais fácil para os usuários localizar o aplicativo quando navegam pelo portal da empresa.
    - **Exiba-o como uma aplicação em destaque no Portal da Empresa**: Selecione esta opção para exibir a aplicação em destaque na página principal do portal da empresa quando os utilizadores navegam para apps.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: a Microsoft aparece como o programador.
    - **Proprietário**: a Microsoft aparece como o proprietário.
    - **Notas**: opcionalmente, introduza quaisquer notas que queira associar a esta aplicação.
3. Selecione **OK**.

## <a name="configure-app-settings"></a>Configurar as definições da aplicação
Nesta etapa, configure as opções de instalação para o aplicativo.

1. No painel **adicionar app,** selecione **as definições da App**.
2. No painel de definições da **App,** selecione **estável,** **Beta** ou **Dev** da lista **do Canal** para determinar de que Canal de Borda irá implementar a aplicação.
    - **O** canal estável é o canal recomendado para a implantação em ambientes empresariais. Ele é atualizado a cada seis semanas, cada versão incorporando melhorias do canal beta.
    - **O** canal Beta é a experiência de pré-visualização mais estável do Microsoft Edge e a melhor escolha para um piloto completo dentro da sua organização. Com as principais atualizações a cada seis semanas, cada versão incorpora os aprendizados e melhorias do canal de desenvolvimento.
    - O canal **Dev** está pronto para feedback da empresa no Windows, Windows Server e macOS. Ele é atualizado toda semana e contém as melhorias e correções mais recentes.

    > [!NOTE]
    > O logotipo do navegador Microsoft Edge é exibido com o aplicativo quando os usuários navegam pelo portal da empresa.

3.  Selecione **OK**.

## <a name="select-scope-tags-optional"></a>Selecionar marcas de escopo (opcional)
Você pode usar marcas de escopo para determinar quem pode ver as informações do aplicativo cliente no Intune. Para obter detalhes completos sobre marcas de escopo, consulte usar o controle de acesso baseado em função e marcas de escopo para distribuí-lo.
1.  Selecione **Scope (Tags)**  > **Adicionar**.
2.  Utilize a caixa **Select** para procurar etiquetas de mira.
3.  Marque a caixa de seleção ao lado das marcas de escopo que você deseja atribuir a este aplicativo.
4.  Clique em **selecionar** > **OK**.

## <a name="add-the-app"></a>Adicionar a aplicação
Quando tiver concluído a configuração da aplicação, selecione **Adicionar** a partir do painel de aplicações da **App.** 

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. 

> [!NOTE]
> No momento, se você cancelar a atribuição da implantação do Microsoft Edge, ela permanecerá no dispositivo.

## <a name="uninstall-the-app"></a>Desinstalar a aplicação

Quando necessitar de desinstalar o Microsoft Edge a partir dos dispositivos do utilizador, utilize os seguintes passos.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações** > app *Microsoft Edge* > **Atribuições** > **Adicionar grupo**.
3. No painel do **grupo Adicionar,** selecione **Desinstalar**.

    > [!NOTE]
    > A aplicação é desinstalada a partir de dispositivos nos grupos selecionados se intune já tiver instalado a aplicação no dispositivo através de uma **disposição disponível para dispositivos matriculados** ou atribuição **obrigatória** utilizando a mesma implementação.
4. Selecione **Grupos Incluídos** para selecionar os grupos de utilizadores que são afetados pela atribuição desta aplicação.
5. Selecione os grupos que pretende aplicar a atribuição de desinstalação.
6. Clique em **Selecionar** no painel de **grupos Select.**
7. Clique **ok** no painel **de atribuir** para definir a atribuição.
8. Selecione **Excluir Grupos** se quiser excluir grupos de utilizadores de serem afetados por esta atribuição de aplicações.
9. Se tiver optado por excluir grupos, em **Selecionar grupos**, selecione **Selecionar**.
10. Selecione **OK** no painel do **grupo Adicionar.**
11. Selecione **Guardar** no painel de atribuição de **aplicações.**

> [!IMPORTANT]
> Para desinstalar a aplicação com sucesso, certifique-se de remover os membros ou atribuição de grupo para instalação antes de atribuir a sua desinstalação. Se um grupo for designado para instalar uma aplicação e desinstalar uma aplicação, a aplicação permanecerá e não será removida.

## <a name="troubleshooting"></a>Resolução de problemas
**Microsoft Edge versão 77 e mais tarde para windows 10:**<br>
O Intune usa a extensão de gerenciamento do Intune para baixar e implantar o instalador do Microsoft Edge em dispositivos Windows 10 atribuídos e, em seguida, comunica as configurações de implantação ao instalador do Microsoft Edge, que baixa e instala o navegador Microsoft Edge diretamente da CDN. Consulte os [pré-requisitos para a extensão de gestão Intune](~/apps/intune-management-extension.md#prerequisites), e as melhores práticas descritas no acesso ao Azure Update Service e ao CDN para garantir que a configuração da sua rede permite que os dispositivos Windows 10 acedam a estes locais. Além disso, para permitir o acesso a arquivos de instalação de uma CDN para instalar o navegador, você precisa permitir o acesso a Windows Update pontos de extremidade. Para mais informações, consulte [Gerir pontos finais de ligação para windows 10, versão 1809 – Windows Update](https://docs.microsoft.com/windows/privacy/manage-windows-1809-endpoints#windows-update) e [pontos finais da Rede para o Microsoft Intune](~/fundamentals/intune-endpoints.md).

## <a name="next-steps"></a>Passos Seguintes
- [Atribuir aplicações a grupos](~/apps/apps-deploy.md)
