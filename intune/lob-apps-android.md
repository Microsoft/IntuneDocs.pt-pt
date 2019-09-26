---
title: Adicionar aplicações de linha de negócio Android ao Microsoft Intune
description: Saiba mais sobre como adicionar um aplicativo de LOB (linha de negócios) Android para Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5456fe2b8553c61a81a86aa72c0f34fff86fcd3c
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71303406"
---
# <a name="add-an-android-line-of-business-app-to-microsoft-intune"></a>Adicionar aplicações de linha de negócio Android ao Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Uma aplicação de linha de negócio (LOB) é uma aplicação que adiciona ao Intune a partir de um ficheiro de instalação da aplicação. Normalmente, este tipo de aplicação é criado internamente. O Intune instala a aplicação LOB no dispositivo do utilizador. 

> [!Note]
> Para obter mais informações sobre aplicativos LOB e o console do desenvolvedor Google Play, consulte [publicação de aplicativo de LOB (Managed Google Play Private) usando o console do desenvolvedor do Google](apps-add-android-for-work.md?#managed-google-play-private-lob-app-publishing-using-the-google-developer-console). 

> [!Note]
> Para dispositivos Android for Work, consulte [adicionar aplicativos gerenciados Google Play a dispositivos Android Enterprise com o Intune](apps-add-android-for-work.md). 

## <a name="step-1-specify-the-software-setup-file"></a>Passo 1: Especificar o ficheiro de configuração do software

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. No painel **Intune**, selecione **Aplicações do cliente**.
3. Na carga de trabalho **Aplicações do cliente**, selecione **Gerir** > **Aplicações**.
4. Acima da lista de aplicações, selecione **Adicionar**.
5. No painel **Adicionar aplicação**, selecione **Aplicação de linha de negócio**.

## <a name="step-2-configure-the-app-package-file"></a>Passo 2: Configurar o ficheiro do pacote de aplicação

1. No painel **Adicionar aplicação**, selecione **Ficheiro de pacote de aplicação**.
2. No painel **Ficheiro de pacote de aplicação**, selecione o botão Procurar. Em seguida, selecione um ficheiro de instalação do Android com a extensão **.apk**.
3. Quando tiver terminado, selecione **OK**.

## <a name="step-3-configure-app-information"></a>Passo 3: Configurar as informações da aplicação

1. No painel **Adicionar aplicação**, selecione **Informações da aplicação**.
2. No painel **Informações da aplicação**, adicione os detalhes da sua aplicação. Consoante a aplicação que tenha escolhido, alguns dos valores neste painel podem ser preenchidos automaticamente.
    - **Nome**: introduza o nome da aplicação tal como aparece no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só aparece uma das aplicações no portal da empresa.
    - **Descrição**: Insira a descrição do aplicativo. A descrição aparece no portal da empresa.
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

A aplicação criada agora aparece na lista de aplicações. Na lista, pode atribuir a aplicação aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

## <a name="step-5-update-a-line-of-business-app"></a>Passo 5: Atualizar uma aplicação de linha de negócio

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

Se a **seleção de aplicativos de fontes externas** estiver habilitada no dispositivo Android, o usuário será solicitado antes de instalar a atualização. Caso contrário, a atualização será instalada automaticamente.

> [!Note]
> Para o serviço do Intune implementar com êxito um novo ficheiro APK no dispositivo, tem de incrementar a cadeia `android:versionCode` no ficheiro AndroidManifest.xml do pacote APK.

## <a name="next-steps"></a>Passos seguintes

- A aplicação criada aparece na lista de aplicações. Agora pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

- Saiba mais sobre as formas como pode monitorizar as propriedades e atribuições da sua aplicação. Veja [Como monitorizar informações e atribuições da aplicação](apps-monitor.md).

- Saiba mais sobre o contexto da sua aplicação no Intune. Veja [Descrição geral dos ciclos de vida de dispositivos e aplicações](introduction-device-app-lifecycles.md).
