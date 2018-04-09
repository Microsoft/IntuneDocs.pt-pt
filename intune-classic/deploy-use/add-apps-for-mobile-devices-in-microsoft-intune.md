---
title: Adicionar aplicações a dispositivos inscritos
description: Antes de poder implementar uma aplicação, tem de adicioná-la ao Intune. Em seguida, fica disponível na consola do Intune, onde pode implementar e geri-la.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 01/11/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5b1f1ae-f177-450a-9af9-936a02d052e3
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9f5fec22a17eef39819b38567793a2f579815e59
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2018
---
# <a name="add-apps-for-enrolled-devices-to-intune"></a>Adicionar aplicações a dispositivos inscritos ao Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Antes de poder implementar ou gerir uma aplicação, tem de adicioná-la ao Microsoft Intune. Este tópico mostra-lhe como adicionar aplicações a dispositivos inscritos.


> [!IMPORTANT]
> As informações contidas neste tópico ajudam-no a adicionar as aplicações que pretende implementar em dispositivos inscritos e em PCs Windows inscritos. Se quiser adicionar aplicações a PCs Windows que gere com o software de cliente do Intune, consulte [Adicionar aplicações para PCs Windows no Microsoft Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).

## <a name="add-the-app"></a>Adicionar a aplicação
O Intune Software Publisher é utilizado para configurar as propriedades da aplicação e, quando aplicável, carregá-la para o seu espaço de armazenamento na cloud. Utilize o seguinte procedimento:

1.  Na [consola do administrador do Microsoft Intune](https://manage.microsoft.com), selecione **Aplicações** &gt; **Adicionar Aplicações** para iniciar o Publicador de Software do Intune.

    > [!TIP]
    > Poderá ter de introduzir o seu nome de utilizador e palavra-passe do Intune para que o publicador seja iniciado.

2.  Na página **Configuração de software** do publicador, selecione uma das seguintes opções para **Selecionar como este software é disponibilizado nos dispositivos**:
    - **Instalador de software**, para aplicações com a extensão **.msi**:
        - **Selecionar o tipo de ficheiro de instalador de software**. Esta definição indica o tipo de software que pretende implementar. Por exemplo, se pretender instalar uma aplicação iOS, escolha **Pacote de Aplicação para iOS (ficheiro &#42;.ipa)**.
        - **Especificar a localização dos ficheiros de configuração do software**. Introduza a localização dos ficheiros de instalação ou escolha **Procurar** para selecionar a localização numa lista.
        - **Incluir ficheiros e subpastas adicionais da mesma pasta**. Esta opção é apenas para o tipo de ficheiro do **Windows Installer**.<br>Alguns softwares que utilizam o Windows Installer necessitam de ficheiros de suporte que, normalmente, se encontram na mesma pasta que os ficheiros de instalação. Selecione esta opção se pretender também implementar estes ficheiros.<br>Este tipo de instalação utiliza algum do seu espaço de armazenamento na cloud.

  -   **Ligação externa**, para as aplicações que pretende criar, especificando uma ligação para uma loja de aplicações:

        - **Especifique o URL**. Especifique o URL de um dos seguintes:
            - O URL da loja de aplicações da aplicação que pretende implementar. Por exemplo, se pretender implementar a aplicação Ambiente de Trabalho Remoto para Android da Microsoft, especifique **https://play.google.com/store/apps/details?id=com.microsoft.rdc.android**.<br>Para localizar o URL da aplicação, utilize um motor de busca para procurar a página da loja que contém a aplicação. Por exemplo, para localizar a aplicação Ambiente de Trabalho Remoto, pode pesquisar por **Ambiente de Trabalho Remoto da Microsoft para Android**.
            - Um site. O Intune irá implementar um ícone de atalho para o site no dispositivo (conhecido como clip da Web).
            - Uma aplicação na Web. O Intune irá implementar um ícone de atalho para a aplicação no dispositivo.
        - **Solicitar um browser gerido para abrir esta ligação (apenas no Android e no iOS)**. Quando implementa uma ligação para um site ou uma aplicação Web nos utilizadores, estes só poderão abri-la no browser gerido do Intune. Este browser deve estar instalado nos respetivos dispositivos.<br>Para mais detalhes sobre o Managed Browser, consulte [Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).<br>Este tipo de instalação não utiliza o seu espaço de armazenamento na cloud.

  -   **Aplicação iOS gerida da loja de aplicações**, para aplicações gratuitas da iTunes Store que pretende gerir com políticas de gestão de aplicações móveis (MAM):

        - **Especifique o URL**. Introduza o URL da loja de aplicações da aplicação que pretende implementar. Por exemplo, se pretender implementar a aplicação Work Folders da Microsoft para iOS, especifique **https://itunes.apple.com/us/app/work-folders/id950878067?mt=8**.<br>Este tipo de instalação não utiliza o seu espaço de armazenamento na cloud.

        Por exemplo, se pretender implementar a aplicação Microsoft Word a partir da iTunes Store em dispositivos, a página teria o seguinte aspeto:

        ![Intune Software Publisher](./media/publisher-for-mobile.png)

> [!NOTE]
> Quando adicionar e implementar uma aplicação a partir de uma loja, os utilizadores finais têm de ter uma conta nessa loja para conseguir instalar a aplicação.

3.  Na página **Descrição do software**, configure o seguinte:

    > [!TIP]
    > Dependendo do tipo de instalador que está a utilizar, alguns destes valores podem ter sido introduzidos automaticamente.

    - **Publicador**. Introduza o nome do publicador da aplicação.
    - **Nome**. Introduza o nome da aplicação tal como será apresentado no portal da empresa.<br>Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só é apresentada uma das aplicações aos utilizadores no portal da empresa.
    - **Descrição**. Introduza uma descrição para a aplicação. A descrição será apresentada aos utilizadores no portal da empresa.
    - **URL para informações de software**. Isto apenas se encontra disponível apenas se tiver selecionado **Instalador de software**. Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL será apresentado aos utilizadores no portal da empresa.
    - **URL de privacidade**. Isto apenas se encontra disponível apenas se tiver selecionado **Instalador de software**. Opcionalmente, introduza o URL de um site que contenha informações sobre a privacidade desta aplicação. O URL será apresentado aos utilizadores no portal da empresa.
    - **Categoria** (opcional). Selecione uma das categorias de aplicações incorporadas. Isto irá permitir que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como uma aplicação em destaque e realçá-la no portal da empresa**. Apresente a aplicação de forma bem visível na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **Ícone** (opcional). Carregue um ícone que será associado à aplicação. Este é o ícone que será apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.

        Neste exemplo, configurou uma descrição para a aplicação Microsoft Word para iOS:

        ![Exemplo de descrição do software](./media/ios-software-description.png)

4.  Na página **Requisitos**, selecione os requisitos que têm de ser cumpridos antes de ser possível instalar a aplicação num dispositivo. Por exemplo, para um pacote de aplicações para iOS, pode selecionar a versão mínima do iOS necessária. Além disso, pode selecionar o tipo de dispositivo que deve ser, como um iPhone ou iPad.

    > [!TIP]
    > A página **Requisitos** não é apresentada para todos os tipos de aplicações.

5.  Se escolher o tipo de ficheiro **Windows Installer**, são apresentadas mais páginas do assistente. Este tipo de ficheiro é utilizado quando implementa software em PCs com o Windows 10 ou posterior que estão inscritos no Intune.

6.  Na página **Resumo**, reveja as informações que especificou. Quando estiver pronto, selecione **Carregar**.

7.  Selecione **Fechar** para concluir.

A aplicação é apresentada no nó **Aplicações** da área de trabalho **Aplicações**.

## <a name="example---deploying-msi-applications-to-windows-10-devices"></a>Exemplo - Implementar aplicações .msi em dispositivos Windows 10
Neste vídeo de quatro minutos, irá saber mais sobre como implementar aplicações do Windows Installer (msi) em dispositivos inscritos que executam o Windows 10.<br><br>

<iframe src="https://channel9.msdn.com/Series/How-to-Control-the-Uncontrolled/6--How-to-Deploy-MSI-Applications-to-Windows-10-Using-Intune-and-Mobile-Device-Management-MDM/player" width="640" height="360" allowFullScreen frameBorder="0"></iframe>

## <a name="next-steps"></a>Próximos passos

Depois de criar uma aplicação, o passo seguinte é implementá-la. Para obter mais informações, veja [Implementar aplicações no Microsoft Intune](deploy-apps.md).
