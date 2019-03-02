---
title: Adicionar aplicações de linha de negócio iOS ao Microsoft Intune
titlesuffix: ''
description: Saiba mais sobre como adicionar uma aplicação de linha de negócio (LOB) iOS ao Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7206a29bea5a53bf13b43a9881c629f27e949dbb
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230011"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>Adicionar aplicações de linha de negócio iOS ao Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilize as informações neste artigo para o ajudar a adicionar aplicações de linha de negócio (LOB) iOS ao Microsoft Intune.

>[!NOTE]
>Os utilizadores de dispositivos iOS podem remover algumas aplicações iOS incorporadas, tal como Bolsa e Mapas. Não pode utilizar o Intune para implementar novamente essas aplicações. Se os utilizadores eliminarem essas aplicações, terão de aceder à loja de aplicações e reinstalá-las manualmente.

## <a name="step-1-specify-the-software-setup-file"></a>Passo 1: Especifique o ficheiro de configuração de software

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. Na carga de trabalho **Aplicações do cliente**, selecione **Gerir** > **Aplicações**.
5. Acima da lista de aplicações, selecione **Adicionar**.
6. No painel **Adicionar Aplicação**, selecione **Aplicação de linha de negócio**.

## <a name="step-2-configure-the-app-package-file"></a>Passo 2: Configurar o ficheiro de pacote de aplicação

1. No painel **Adicionar aplicação**, selecione **Ficheiro de pacote de aplicação**.
2. No painel **Ficheiro de pacote de aplicação**, selecione o botão Procurar. Em seguida, selecione um ficheiro de instalação do iOS com a extensão **.ipa**.
3. Quando tiver terminado, selecione **OK**.


## <a name="step-3-configure-app-information"></a>Passo 3: Configurar as informações da aplicação

1. No painel **Adicionar aplicação**, selecione **Informações da aplicação**.
2. No painel **Informações da aplicação**, adicione os detalhes da sua aplicação. Consoante a aplicação que tenha escolhido, alguns dos valores neste painel podem ser preenchidos automaticamente.
    - **Nome**: Introduza o nome da aplicação tal como aparece no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só aparece uma das aplicações no portal da empresa.
    - **Descrição**: Introduza uma descrição para a aplicação. A descrição aparece no portal da empresa.
    - **Publisher**: Introduza o nome do publicador da aplicação.
    - **Sistema operativo mínimo**: Na lista, escolha a versão mínima do sistema operativo no qual a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Categoria**: Selecione uma ou mais das categorias de aplicações incorporadas ou selecione uma categoria que criou. As categorias permitem que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da empresa**: Apresente a aplicação de forma bem visível na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de informações**: Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL aparece no portal da empresa.
    - **URL de privacidade**: Opcionalmente, introduza o URL de um site que contenha informações sobre a privacidade desta aplicação. O URL aparece no portal da empresa.
    - **Desenvolvedor**: Opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: Opcionalmente, introduza um nome para o proprietário desta aplicação. Por exemplo, **Departamento de RH**.
    - **Notas de**: Introduza quaisquer notas que pretende associar esta aplicação.
    - **Logótipo**: Carregue um ícone que está associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
3. Quando tiver terminado, selecione **OK**.

## <a name="step-4-finish-up"></a>Passo 4: Concluir

1. No painel **Adicionar aplicação**, verifique se os detalhes da sua aplicação estão corretos.
2. Selecione **Adicionar** para carregar a aplicação para o Intune.

A aplicação criada agora aparece na lista de aplicações. Na lista, pode atribuir as aplicações aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

> [!NOTE]
> Os perfis de aprovisionamento de aplicações LOB para iOS apresentam um aviso com 30 dias de antecedência antes de expirarem.

## <a name="step-5-update-a-line-of-business-app"></a>Passo 5: Atualizar uma aplicação de linha de negócio

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Para o serviço do Intune implementar com êxito um novo ficheiro IPA no dispositivo, tem de incrementar a cadeia `CFBundleVersion` no ficheiro Info.plist do pacote IPA.

## <a name="next-steps"></a>Passos Seguintes

- A aplicação criada aparece na lista de aplicações. Agora pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

- Saiba mais sobre as formas como pode monitorizar as propriedades e atribuições da sua aplicação. Veja [Como monitorizar informações e atribuições da aplicação](apps-monitor.md).

- Saiba mais sobre o contexto da sua aplicação no Intune. Veja [Descrição geral dos ciclos de vida de dispositivos e aplicações](introduction-device-app-lifecycles.md).
