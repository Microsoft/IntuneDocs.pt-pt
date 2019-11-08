---
title: Configurações de dispositivo compartilhado ou de vários usuários no Microsoft Intune-Azure | Microsoft Docs
description: Adicione e use o Windows 10 e o Windows Holographic para dispositivos de negócios que são compartilhados ou usados por vários usuários no Microsoft Intune. Veja uma lista de todas as configurações e o que elas fazem nos dispositivos, incluindo o Microsoft HoloLens. Controle contas de convidado, gerencie contas e exclua contas inativas, permita ou Evite salvar no armazenamento local, defina opções de energia e suspensão, escolha quando as atualizações são instaladas e use dispositivos em ambientes de educação em um perfil de configuração de dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7fa8fb95579d887228dc6ec8f241d157169450b7
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755077"
---
# <a name="control-access-accounts-and-power-features-on-shared-pc-or-multi-user-devices-using-intune"></a>Controlar o acesso, contas e recursos de energia no computador compartilhado ou dispositivos de vários usuários usando o Intune

Os dispositivos que têm vários usuários são chamados de dispositivos compartilhados e são uma parte comum das soluções de MDM (gerenciamento de dispositivo móvel). Usando Microsoft Intune, você pode personalizar dispositivos compartilhados executando as seguintes plataformas:

- Windows 10 Professional e mais recente
- Windows 10 Enterprise e mais recente
- Windows Holographic para empresas, como o HoloLens

Por exemplo, escolas têm dispositivos que normalmente são usados por muitos alunos. Com essa configuração, o administrador da escola do Intune pode ativar o recurso de computador compartilhado para permitir um usuário de cada vez. Os alunos não podem alternar entre diferentes contas conectadas no dispositivo. Quando o aluno se desconecta, você também opta por remover todas as configurações específicas do usuário.

Os usuários finais podem entrar nesses dispositivos compartilhados com uma conta de convidado. Depois que os usuários entram, as credenciais são armazenadas em cache. Como eles usam o dispositivo, os usuários finais só têm acesso aos recursos que você permitir. Por exemplo, você escolhe quando o dispositivo entra no modo de suspensão, se os usuários podem ver e salvar arquivos localmente, habilitar ou desabilitar as configurações de gerenciamento de energia e muito mais. Você também controla se a conta de convidado exclui quando o usuário se desconecta ou exclui contas inativas quando um limite é atingido.

Este artigo mostra como criar um perfil de configuração e inclui links para as configurações disponíveis com suas descrições.

Quando o perfil é criado no Intune, você implanta ou atribui o perfil aos grupos de dispositivos em sua organização. Você também pode atribuir esse perfil a grupos de dispositivos com tipos de dispositivos mistos e versões de sistema operacional (SO).

## <a name="create-the-profile"></a>Criar o perfil

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

   - **Nome**: introduza um nome descritivo para o novo perfil.
   - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
   - **Plataforma**: selecione **Windows 10 e posterior**.
   - **Tipo de perfil**: selecione **dispositivo compartilhado de vários usuários**.

4. Defina as configurações para [Windows 10 e posterior](shared-user-device-settings-windows.md) ou [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md).

5. Selecione **OK** > **Criar** para guardar as alterações.

Seu perfil é criado e mostrado na lista, mas não está fazendo nada ainda. Certifique-se de [atribuir o perfil](device-profile-assign.md) aos grupos de dispositivos em sua organização.

## <a name="next-steps"></a>Próximos passos

- Veja todas as configurações para [Windows 10 e mais recente](shared-user-device-settings-windows.md) e [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md).
- [Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
