---
title: Como adicionar aplicações de linha de negócio macOS ao Microsoft Intune
titlesuffix: ''
description: Saiba como adicionar aplicações de linha de negócio (LOB) macOS ao Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d527b36876adf29c12d3577f7dcd09416b4d5a37
ms.sourcegitcommit: 40b1d82df99f09a75a17065cdd0e84d8038f460a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/22/2018
ms.locfileid: "40255474"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>Como adicionar aplicações de linha de negócio (LOB) macOS ao Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilize as informações neste artigo para adicionar aplicações de linha de negócio macOS ao Microsoft Intune. Tem de transferir uma ferramenta externa para pré-processar os ficheiros *.pkg* para poder carregar o ficheiro de linha de negócio para o Microsoft Intune. O pré-processamento dos ficheiros *.pkg* tem de ser realizado num dispositivo macOS.

> [!NOTE]
> Apesar de os utilizadores de dispositivos macOS poderem remover algumas das aplicações macOS incorporadas, tais como Bolsa e Mapas, não pode utilizar o Intune para implementar novamente essas aplicações. Se os utilizadores finais eliminarem essas aplicações, têm de aceder à App Store e reinstalar manualmente.

## <a name="before-your-start"></a>Antes de começar

Tem de transferir uma ferramenta externa para pré-processar os ficheiros *.pkg* para poder carregar o ficheiro de linha de negócio para o Microsoft Intune. O pré-processamento dos ficheiros *.pkg* tem de ser realizado num dispositivo macOS. Utilize a Ferramenta de Encapsulamento de Aplicações do Intune para Mac para permitir que as aplicações Mac sejam geridas pelo Microsoft Intune.

> [!IMPORTANT]
> Apenas os ficheiros *.pkg* podem servir para carregar aplicações LOB macOS para o Microsoft Intune. A conversão de outros formatos, como *.dmg* em *.pkg*, não é suportada.

1. Transfira e execute a [Ferramenta de Encapsulamento de Aplicações do Intune para Mac](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac).

    > [!NOTE]
    > A **Ferramenta de Encapsulamento de Aplicações do Intune para Mac** tem de ser executada numa máquina macOS.

2. Utilize o comando `IntuneAppUtil` na **Ferramenta de Encapsulamento de Aplicações do Intune para Mac** para encapsular o ficheiro da aplicação LOB *.pkg* num ficheiro *.intunemac*.<br>

    Comandos de exemplo a utilizar para a Ferramenta de Encapsulamento de Aplicações do Intune para Mac:
    
    - `IntuneAppUtil -h`<br>
    Este comando mostra informações de utilização da ferramenta.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    Este comando encapsula o ficheiro de aplicação LOB *.pkg* num ficheiro *.intunemac*.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    Este comando extrai os parâmetros detetados e a versão do ficheiro *.intunemac* criado.

## <a name="step-1---specify-the-software-setup-file"></a>Passo 1 – Especificar o ficheiro de configuração do software

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações móveis**.
4. Na carga de trabalho **Aplicações móveis**, escolha **Gerir** > **Aplicações**.
5. Acima da lista de aplicações, escolha **Adicionar**.
6. No painel **Adicionar aplicação**, selecione **Aplicação de linha de negócio**.

## <a name="step-2---configure-the-app-package-file"></a>Passo 2 – Configurar o ficheiro de pacote de aplicação

1. No painel **Adicionar aplicação**, selecione **Ficheiro de pacote de aplicação**.
2. No painel **Ficheiro de pacote de aplicação**, escolha o botão Procurar e selecione um ficheiro de instalação do macOS com a extensão *.intunemac*.
3. Quando terminar, escolha **OK**.


## <a name="step-3---configure-app-information"></a>Passo 3 – Configurar as informações da aplicação

1. No painel **Adicionar aplicação**, selecione **Informações da aplicação**.
2. No painel **Informações da aplicação**, adicione os detalhes da sua aplicação. Consoante a aplicação que tenha selecionado, alguns dos valores neste painel podem ter sido preenchidos automaticamente:
    - **Nome** – introduza o nome da aplicação a apresentar no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só é apresentada uma das aplicações aos utilizadores no portal da empresa.
    - **Descrição** – introduza uma descrição da aplicação a apresentar aos utilizadores no portal da empresa.
    - **Publicador** – Introduza o nome do publicador da aplicação.
    - **Sistema Operativo Mínimo** – Na lista, escolha a versão mínima do sistema operativo no qual a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Categoria** – selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. Isto irá permitir que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar esta aplicação em destaque no Portal da Empresa** – Apresente a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações** – Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade** – Opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador** – opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário** – Opcionalmente, introduza um nome para o proprietário desta aplicação, por exemplo, **Departamento de RH**.
    - **Notas** – Introduza quaisquer notas que pretenda associar esta aplicação.
    - **Logótipo** – carregue um ícone associado à aplicação. Este é o ícone que é apresentado com a aplicação quando os utilizadores procuram no portal da empresa.
3. Quando terminar, escolha **OK**.

## <a name="step-4---finish-up"></a>Passo 4 – Concluir

1. No painel **Adicionar aplicação**, verifique se os detalhes da sua aplicação estão corretos.
2. Escolha **Adicionar** para carregar a aplicação para o Intune.

A aplicação que criou é apresentada na lista de aplicações, onde pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

> [!NOTE]
> Se o ficheiro *.pkg* contiver várias aplicações ou instaladores de aplicações, o Microsoft Intune apenas comunicará que a *aplicação* foi instalada com êxito quando todas as aplicações instaladas no dispositivo forem detetadas.

## <a name="step-5---update-a-line-of-business-app"></a>Passo 5 – Atualizar uma aplicação de linha de negócio

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Para o serviço do Intune implementar com êxito um novo ficheiro *.pkg* no dispositivo, tem de incrementar o pacote `version` e a cadeia `CFBundleVersion` no ficheiro *packageinfo* do pacote *.pkg*.

## <a name="next-steps"></a>Próximos passos

- A aplicação que criou é apresentada na lista de aplicações. Agora pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

- Saiba mais sobre as formas como pode monitorizar as propriedades e atribuições da sua aplicação. Para obter mais informações, veja [Como monitorizar informações e atribuições da aplicação](apps-monitor.md).

- Saiba mais sobre o contexto da sua aplicação no Intune. Para obter mais informações, veja [Descrição geral dos ciclos de vida de dispositivos e aplicações](introduction-device-app-lifecycles.md)
