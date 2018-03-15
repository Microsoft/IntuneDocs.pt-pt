---
title: "Configurar as políticas de atualização de iOS no Microsoft Intune"
titlesuffix: 
description: "Configure políticas de atualização para iOS para forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de software disponíveis mais recentes."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.openlocfilehash: 2062f9cd551ec6d7f42449041e6c8de837221631
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2018
---
# <a name="configure-ios-update-policies-in-microsoft-intune"></a>Configurar as políticas de atualização de iOS no Microsoft Intune
As políticas de atualização para iOS permitem-lhe forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de software disponíveis mais recentes. Pode configurar os dias e as horas em que não pretende que os dispositivos instalem a atualização.

## <a name="configure-the-ios-update-policy"></a>Configurar a política de atualização de iOS
1. Aceda à página Intune no portal do Azure.
2. Na página **Intune**, selecione **Atualizações de software** > **Políticas de Atualização de iOS**.
4. Na página Políticas, selecione **Criar** e, em seguida, introduza um nome e descrição para a política.
5. Selecione **Definições** > **Configurar** e introduza os detalhes para quando os dispositivos iOS não são forçados a instalar a atualização mais recente.
6. Escolha **OK** para guardar esta configuração. Está novamente na página **Criar política de atualização**. Escolha **Criar** para criar a política e guardar as suas definições.

O perfil é criado e apresentado na página da lista de políticas de atualização de iOS.

## <a name="assign-an-ios-update-policy-to-users"></a>Atribuir uma política de atualização de iOS a utilizadores
Para atribuir uma política de atualização de iOS a utilizadores, escolha uma política que tenha configurado. As políticas existentes encontram-se na página **Atualizações de software** > **Políticas de Atualização de iOS**.
1. Escolha a política que quer atribuir aos utilizadores e, em seguida, **Atribuições**. É aberta a página onde pode selecionar grupos de segurança do Azure Active Directory e atribuí-los à política.
2. Selecione **Selecionar grupos** para abrir a página que apresenta os grupos de segurança do Azure AD. Escolha **Selecionar** para implementar a política aos utilizadores.

Aplicou a política aos utilizadores. Os dispositivos utilizados pelos utilizadores visados pela política são avaliados quanto à conformidade das atualizações.

## <a name="change-the-restricted-days-for-the-policy"></a>Alterar os dias restritos da política
1. Na página **Atualizações de software**, selecione **Políticas de Atualização de iOS**.
2. Selecione a política de atualização de iOS que pretende atualizar.
3. Selecione **Propriedades** e atualize a informação de dias restritos.

## <a name="monitor-ios-devices-with-older-ios-versions"></a>Monitorizar dispositivos iOS com versões mais antigas do iOS 
<!-- 1352223 -->
O relatório **Dispositivos iOS Desatualizados** está disponível na página **Atualizações de software** > **Políticas de Atualização de iOS**. No relatório, poderá ver uma lista dos dispositivos iOS supervisionados que foram abrangidos por uma política de atualização de iOS e que não foi possível atualizar. Pode ver o estado com o motivo pelo qual cada um dos dispositivos não foi atualizado automaticamente.