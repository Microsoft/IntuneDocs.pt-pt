---
title: "Configurar as definições de educação do Intune para Windows 10"
titleSuffix: Azure portal
description: "Saiba como utilizar o Intune para configurar as definições de educação do Windows 10 nos dispositivos que gere.\""
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 18987c65c7ad0443c8bf3dc268284306cf64080d
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-configure-windows-10-education-settings-in-microsoft-intune"></a>Como configurar as definições de educação do Windows 10 no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Os perfis de educação permitem-lhe especificar os detalhes que configuram a aplicação Fazer um Teste do Windows, incluindo detalhes da conta e o URL de teste. Quando configurar esta opção, a aplicação Fazer um Teste abre-se com o teste que especificar e mais nenhuma aplicação pode ser executada no dispositivo até que o teste esteja concluído.

Para obter detalhes sobre a aplicação Fazer um Teste, veja [Take tests in Windows 10 (Fazer testes no Windows 10](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).

## <a name="create-a-device-profile-containing-education-profile-settings"></a>Criar um perfil de dispositivo com as definições de perfil de educação

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Configuração do dispositivo**.
2. No painel **Configuração do dispositivo**, na secção **Gerir**, selecione **Perfis**.
3. No painel Perfis, selecione **Criar perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de restrição de dispositivos.
5. Na lista pendente **Plataforma**, selecione **Windows 10 e posterior**.
6. Na lista pendente **Tipo de perfil**, escolha **Perfil de educação**. 
7. Selecione **Definições > Configurar** e, em seguida, no painel **Realize um Teste**, configure o seguinte:
    - **Tipo de conta** – selecione um tipo de conta no campo pendente.
    - **Nome de utilizador da conta** –introduza o nome de utilizador da conta utilizada com Fazer um Teste. Pode ser uma conta de domínio, uma conta do Azure Active Directory (AAD) ou uma conta de computador local.
    - **URL de avaliação** – indique o URL do teste que quer que os utilizadores realizem. Para obter mais informações, veja a documentação de Fazer um Teste.
    - **Monitorização do ecrã** – especifique se quer monitorizar a atividade do ecrã enquanto os utilizadores estão a fazer um teste.
    - **Sugestão de texto** – permita ou bloqueie as sugestões de texto enquanto os utilizadores estão a fazer o teste.
8. Quando tiver terminado, regresse ao painel **Criar perfil** e clique em **Criar**.

O perfil será criado e apresentado no painel Lista de perfis.

## <a name="next-steps"></a>Próximos passos

Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).



