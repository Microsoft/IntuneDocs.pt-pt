---
title: Adicionar aplicações de linha de negócio iOS ao Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre como adicionar um aplicativo de LOB (linha de negócios) do iOS a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b25c664023cde25fd3ce1fdb59f03c9969a6efb0
ms.sourcegitcommit: cd03ea890f563b48339a8c8bb50386b8852ba894
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/19/2019
ms.locfileid: "71301829"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>Adicionar aplicações de linha de negócio iOS ao Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilize as informações neste artigo para o ajudar a adicionar aplicações de linha de negócio (LOB) iOS ao Microsoft Intune. Um aplicativo LOB (linha de negócios) é um aplicativo que você adiciona ao Intune de um arquivo de instalação do aplicativo IPA. Normalmente, este tipo de aplicação é criado internamente. Primeiro, você precisará ingressar no programa corporativo do desenvolvedor do iOS. Para obter mais informações sobre como fazer isso, consulte o [site da Apple](https://developer.apple.com/programs/ios/enterprise/).

>[!NOTE]
>Os utilizadores de dispositivos iOS podem remover algumas aplicações iOS incorporadas, tal como Bolsa e Mapas. Não pode utilizar o Intune para implementar novamente essas aplicações. Se os utilizadores eliminarem essas aplicações, terão de aceder à loja de aplicações e reinstalá-las manualmente.
>
>As aplicações LOB iOS têm um limite de tamanho máximo de 4 GB por aplicação.

## <a name="step-1-specify-the-software-setup-file"></a>Passo 1: Especificar o ficheiro de configuração do software

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. Na carga de trabalho **Aplicações do cliente**, selecione **Gerir** > **Aplicações**.
5. Acima da lista de aplicações, selecione **Adicionar**.
6. No painel **Adicionar Aplicação**, selecione **Aplicação de linha de negócio**.

## <a name="step-2-configure-the-app-package-file"></a>Passo 2: Configurar o ficheiro do pacote de aplicação

1. No painel **Adicionar aplicação**, selecione **Ficheiro de pacote de aplicação**.
2. No painel **Ficheiro de pacote de aplicação**, selecione o botão Procurar. Em seguida, selecione um ficheiro de instalação do iOS com a extensão **.ipa**.
3. Quando tiver terminado, selecione **OK**.


## <a name="step-3-configure-app-information"></a>Passo 3: Configurar as informações da aplicação

1. No painel **Adicionar aplicação**, selecione **Informações da aplicação**.
2. No painel **Informações da aplicação**, adicione os detalhes da sua aplicação. Consoante a aplicação que tenha escolhido, alguns dos valores neste painel podem ser preenchidos automaticamente.
    - **Nome**: introduza o nome da aplicação tal como aparece no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só aparece uma das aplicações no portal da empresa.
    - **Descrição**: Introduza uma descrição para a aplicação. A descrição aparece no portal da empresa.
    - **Publicador**: Introduza o nome do publicador da aplicação.
    - **Sistema operacional mínimo**: Na lista, escolha a versão mínima do sistema operacional na qual o aplicativo pode ser instalado. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Categoria**: selecione uma ou mais das categorias de aplicações incorporadas ou selecione uma categoria que tenha criado. As categorias permitem que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da Empresa**: Apresente a aplicação de forma bem visível na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações**: Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL aparece no portal da empresa.
    - **URL de Privacidade**: Opcionalmente, introduza o URL de um site que contenha informações sobre a privacidade desta aplicação. O URL aparece no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação. Por exemplo, **Departamento de RH**.
    - **Notas**: introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: carregue um ícone associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
3. Quando tiver terminado, selecione **OK**.

## <a name="step-4-finish-up"></a>Passo 4: Concluir

1. No painel **Adicionar aplicação**, verifique se os detalhes da sua aplicação estão corretos.
2. Selecione **Adicionar** para carregar a aplicação para o Intune.

A aplicação criada agora aparece na lista de aplicações. Na lista, pode atribuir as aplicações aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

> [!NOTE]
> Os perfis de aprovisionamento de aplicações LOB para iOS apresentam um aviso com 30 dias de antecedência antes de expirarem.

## <a name="step-5-update-a-line-of-business-app"></a>Passo 5: Atualizar uma aplicação de linha de negócio

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

A atualização para o aplicativo de linha de negócios será instalada automaticamente.

> [!NOTE]
> Para o serviço do Intune implementar com êxito um novo ficheiro IPA no dispositivo, tem de incrementar a cadeia `CFBundleVersion` no ficheiro Info.plist do pacote IPA.

## <a name="next-steps"></a>Passos seguintes

- A aplicação criada aparece na lista de aplicações. Agora pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

- Saiba mais sobre as formas como pode monitorizar as propriedades e atribuições da sua aplicação. Veja [Como monitorizar informações e atribuições da aplicação](apps-monitor.md).

- Saiba mais sobre o contexto da sua aplicação no Intune. Veja [Descrição geral dos ciclos de vida de dispositivos e aplicações](introduction-device-app-lifecycles.md).
