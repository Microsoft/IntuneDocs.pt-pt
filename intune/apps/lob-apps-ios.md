---
title: Adicionar aplicações de linha de negócio iOS ao Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre como adicionar um aplicativo de LOB (linha de negócios) do iOS a Microsoft Intune.
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
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7e1d3c6a427dcbd4a7946c5f3e180de56e8cb955
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74563511"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>Adicionar aplicações de linha de negócio iOS ao Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Utilize as informações neste artigo para o ajudar a adicionar aplicações de linha de negócio (LOB) iOS ao Microsoft Intune. Um aplicativo LOB (linha de negócios) é um aplicativo que você adiciona ao Intune de um arquivo de instalação do aplicativo IPA. Normalmente, este tipo de aplicação é criado internamente. Primeiro, você precisará ingressar no programa corporativo do desenvolvedor do iOS. Para obter mais informações sobre como fazer isso, consulte o [site da Apple](https://developer.apple.com/programs/ios/enterprise/).

>[!NOTE]
>Os utilizadores de dispositivos iOS podem remover algumas aplicações iOS incorporadas, tal como Bolsa e Mapas. Não pode utilizar o Intune para implementar novamente essas aplicações. Se os utilizadores eliminarem essas aplicações, terão de aceder à loja de aplicações e reinstalá-las manualmente.
>
>As aplicações LOB iOS têm um limite de tamanho máximo de 4 GB por aplicação.

## <a name="step-1-specify-the-software-setup-file"></a>Passo 1: especificar o ficheiro de configuração do software

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
3. No painel **Adicionar aplicativo** , selecione **aplicativo de linha de negócios** como o tipo de **aplicativo**.

## <a name="step-2-configure-the-app-package-file"></a>Passo 2: configurar o ficheiro de pacote de aplicação

1. No painel **Adicionar aplicação**, selecione **Ficheiro de pacote de aplicação**.
2. No painel **Ficheiro de pacote de aplicação**, selecione o botão Procurar. Em seguida, selecione um ficheiro de instalação do iOS com a extensão **.ipa**.
3. Quando tiver terminado, selecione **OK**.


## <a name="step-3-configure-app-information"></a>Passo 3: configurar as informações da aplicação

1. No painel **Adicionar aplicação**, selecione **Informações da aplicação**.
2. No painel **Informações da aplicação**, adicione os detalhes da sua aplicação. Consoante a aplicação que tenha escolhido, alguns dos valores neste painel podem ser preenchidos automaticamente.
    - **Nome**: introduza o nome da aplicação tal como aparece no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só aparece uma das aplicações no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. A descrição aparece no portal da empresa.
    - **Publicador**: introduza o nome do publicador da aplicação.
    - **Sistema Operativo Mínimo**: na lista, escolha a versão mínima do sistema operativo no qual a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Categoria**: selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. As categorias permitem que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar esta aplicação em destaque no Portal da Empresa**: apresente a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL aparece no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL aparece no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação. Por exemplo, **Departamento de RH**.
    - **Notas**: introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: carregue um ícone associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
3. Quando tiver terminado, selecione **OK**.

## <a name="step-4-finish-up"></a>Passo 4: concluir

1. No painel **Adicionar aplicação**, verifique se os detalhes da sua aplicação estão corretos.
2. Selecione **Adicionar** para carregar a aplicação para o Intune.

A aplicação criada agora aparece na lista de aplicações. Na lista, pode atribuir as aplicações aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

> [!NOTE]
> Os perfis de aprovisionamento de aplicações LOB para iOS apresentam um aviso com 30 dias de antecedência antes de expirarem.

## <a name="step-5-update-a-line-of-business-app"></a>Passo 5: atualizar uma aplicação de linha de negócio

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

A atualização para o aplicativo de linha de negócios será instalada automaticamente.

> [!NOTE]
> Para o serviço do Intune implementar com êxito um novo ficheiro IPA no dispositivo, tem de incrementar a cadeia `CFBundleVersion` no ficheiro Info.plist do pacote IPA.

## <a name="next-steps"></a>Próximos passos

- A aplicação criada aparece na lista de aplicações. Agora pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

- Saiba mais sobre as formas como pode monitorizar as propriedades e atribuições da sua aplicação. Veja [Como monitorizar informações e atribuições da aplicação](apps-monitor.md).

- Saiba mais sobre o contexto da sua aplicação no Intune. Veja [Descrição geral dos ciclos de vida de dispositivos e aplicações](../fundamentals/device-lifecycle.md).
