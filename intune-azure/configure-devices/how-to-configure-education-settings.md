---
title: "Configurar as definições de educação do Intune"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como utilizar o Intune para configurar as definições de educação nos dispositivos que gere."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: ca4f1adc5704ecd66d2af7823f95ca63ec20469e
ms.openlocfilehash: 5c73719c4fd2805f91c6af3ba48c39f5d798aaeb
ms.lasthandoff: 03/17/2017


---

# <a name="how-to-configure-education-settings-in-microsoft-intune"></a>Como configurar as definições de educação no Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Os perfis de educação permitem-lhe especificar os detalhes que configuram a aplicação Fazer um Teste do Windows, incluindo detalhes da conta e o URL de teste. Quando configurar esta opção, a aplicação Fazer um Teste abre-se com o teste que especificar e mais nenhuma aplicação pode ser executada no dispositivo até que o teste esteja concluído.

Utilize as informações deste tópico para conhecer as noções básicas sobre como configurar perfis de restrição de dispositivos e, em seguida, leia os tópicos de cada plataforma para saber mais sobre as especificações dos dispositivos.

## <a name="create-a-device-profile-containing-education-profile-settings"></a>Criar um perfil de dispositivo com as definições de perfil de educação

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de restrição de dispositivos.
5. Na lista pendente **Plataforma**, selecione **Windows 10 e posterior**.
6. Na lista pendente **Tipo de perfil**, escolha **Perfil de educação**. 
7. Escolha Definições > Configurar e, em seguida, no painel **Fazer um Teste**, configure o seguinte:
    - **Nome de utilizador da conta** –introduza o nome de utilizador da conta utilizada com Fazer um Teste. Pode ser uma conta de domínio, uma conta do Azure Active Directory (AAD) ou uma conta de computador local.
    - **URL de avaliação** – indique o URL do teste que quer que os utilizadores realizem. Para obter mais informações, veja a documentação de Fazer um Teste.
    - **Monitorização do ecrã** – especifique se quer monitorizar a atividade do ecrã enquanto os utilizadores estão a fazer um teste.
    - **Sugestão de texto** – permita ou bloqueie as sugestões de texto enquanto os utilizadores estão a fazer o teste.
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](how-to-assign-device-profiles.md).




