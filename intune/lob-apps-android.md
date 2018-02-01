---
title: "Como adicionar aplicações Android de linha de negócio ao Intune"
titlesuffix: Azure portal
description: "Saiba como adicionar aplicações de linha de negócio Android ao Intune.\""
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7b2aa6893e1d01fe83e92c711c7a487f49b92706
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-add-android-line-of-business-lob-apps-to-microsoft-intune"></a>Como adicionar aplicações de linha de negócio (LOB) Android ao Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="step-1---specify-the-software-setup-file"></a>Passo 1 – Especificar o ficheiro de configuração do software

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** + **Intune**.
3. No painel **Intune**, escolha **Gerir aplicações**.
4. Na carga de trabalho **Aplicações móveis**, escolha **Gerir** > **Aplicações**.
5. Acima da lista de aplicações, escolha **Adicionar**.
6. No painel **Adicionar Aplicação**, escolha **Aplicação de linha de negócio**.

## <a name="step-2---configure-the-app-package-file"></a>Passo 2 – Configurar o ficheiro de pacote de aplicação

1. No painel **Adicionar aplicação**, escolha o ficheiro **Pacote de aplicação**.
2. No painel **Ficheiro do pacote de aplicação**, escolha o botão procurar e selecione um ficheiro de instalação do Android com a extensão **.apk**.
3. Quando terminar, escolha **OK**.


## <a name="step-3---configure-app-information"></a>Passo 3 – Configurar as informações da aplicação

1. No painel **Adicionar aplicação**, escolha o ficheiro **Pacote de aplicação**.
2. No painel **Informações da aplicação**, adicione os detalhes da sua aplicação. Consoante a aplicação que tenha escolhido, alguns dos valores neste painel podem ter sido preenchidos automaticamente:
    - **Nome** – introduza o nome da aplicação a apresentar no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só é apresentada uma das aplicações aos utilizadores no portal da empresa.
    - **Descrição** – introduza a descrição da aplicação a apresentar aos utilizadores no portal da empresa.
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

1. No painel **Adicionar aplicação**, verifique os detalhes da sua aplicação.
2. Escolha **Adicionar** para carregar a aplicação para o Intune.

A aplicação que criou será apresentada na lista de aplicações onde a pode atribuir aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

## <a name="step-5---update-a-line-of-business-app"></a>Passo 5 – Atualizar uma aplicação de linha de negócio

[!INCLUDE[shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]Nota: para o serviço do Intune implementar com êxito um novo ficheiro APK no dispositivo, tem de incrementar a cadeia android:versionCode no ficheiro AndroidManifest.xml no pacote APK

## <a name="next-steps"></a>Próximos passos

A aplicação que criou é apresentada na lista de aplicações. Agora pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).

Saiba mais sobre as formas como pode monitorizar as propriedades e atribuições da sua aplicação. Para obter mais informações, consulte [Como monitorizar informações e atribuições da aplicação](apps-monitor.md).

Saiba mais sobre o contexto da sua aplicação no Intune. Para obter mais informações, consulte [Descrição geral dos ciclos de vida de dispositivos e aplicações](introduction-device-app-lifecycles.md)
