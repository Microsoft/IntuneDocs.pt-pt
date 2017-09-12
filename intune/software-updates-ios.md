---
title: "Configurar as políticas de atualização de iOS"
titlesuffix: Azure portal
description: "Configure políticas de atualização para iOS para forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de software disponíveis mais recentes."
keywords: 
author: dougeby
manager: dougeby
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6334421-85e1-4457-9c44-e5db8d4ee00e
ms.openlocfilehash: a119f00cc8a92aa6cf7a1009f910df817593e0e8
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="configure-ios-update-policies"></a>Configurar as políticas de atualização de iOS
As políticas de atualização para iOS permitem-lhe forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de software disponíveis mais recentes. Pode configurar os dias e as horas em que não pretende que os dispositivos instalem a atualização.

## <a name="configure-the-ios-update-policy"></a>Configurar a política de atualização de iOS
1. Aceda ao painel Intune no portal do Azure.
2. No painel **Intune**, selecione **Atualizações de software** > **Políticas de Atualização de iOS**.
4. No painel Políticas, selecione **Criar** e, em seguida, introduza um nome e descrição para a política.
5. Selecione **Definições** > **Configurar** e introduza os detalhes para quando os dispositivos iOS não serão forçados a instalar a atualização mais recente.
6. Escolha **OK** para guardar esta configuração. Está novamente no painel **Criar política de atualização**. Escolha **Criar** para criar a política e guardar as suas definições.

O perfil é criado e apresentado no painel da lista de políticas de atualização de iOS.

## <a name="assign-an-ios-update-policy-to-users"></a>Atribuir uma política de atualização de iOS a utilizadores
Para atribuir uma política de atualização de iOS a utilizadores, escolha uma política que tenha configurado. As políticas existentes encontram-se no painel **Atualizações de software** > **Políticas de Atualização de iOS**.
1. Escolha a política que quer atribuir aos utilizadores e, em seguida, **Atribuições**. Esta ação abre o painel onde pode selecionar grupos de segurança do Azure Active Directory e atribuí-los à política.
2. Escolha **Selecionar grupos** para abrir o painel que apresenta os grupos de segurança do Azure AD. Escolha **Selecionar** para implementar a política aos utilizadores.

Aplicou a política aos utilizadores. Os dispositivos utilizados pelos utilizadores visados pela política serão avaliados quanto à conformidade das atualizações.

## <a name="change-the-restricted-days-for-the-policy"></a>Alterar os dias restritos da política
1. No painel **Atualizações de software**, selecione **Políticas de Atualização de iOS**.
2. Selecione a política de atualização de iOS que pretende atualizar.
3. Selecione **Propriedades** e atualize a informação de dias restritos.
