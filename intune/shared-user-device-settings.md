---
title: Definições de dispositivos partilhados ou de vários utilizadores no Microsoft Intune – Azure | Documentos da Microsoft
description: Adicionar e utilizar o Windows 10 e Windows Holographic for Business dispositivos que são partilhados ou utilizados por vários utilizadores no Microsoft Intune. Ver uma lista de todas as definições e o que fazer em dispositivos, incluindo o Microsoft HoloLens. Controlar as contas de convidado, gerir contas e eliminar contas inativas, permitir ou impedir guardar para o armazenamento local, definir power e opções de estado de suspensão, escolher quando as atualizações são instaladas e utilizam dispositivos em ambientes de educação num perfil de configuração do dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c2cf06508cc21682a580c09e8207343b09e39eb
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61506683"
---
# <a name="control-access-accounts-and-power-features-on-shared-pc-or-multi-user-devices-using-intune"></a>Controlar o acesso, contas e recursos de energia no PC partilhado ou dispositivos de vários utilizadores através do Intune

Dispositivos que têm vários utilizadores são chamados dispositivos partilhados e são uma parte comuns de dispositivos móveis (MDM) de soluções de gestão. Utilizar o Microsoft Intune, pode personalizar dispositivos partilhados com as seguintes plataformas:

- Windows 10 Professional e versões mais recentes
- Windows 10 Enterprise e versões mais recentes
- Windows Holographic for Business, como o HoloLens

Por exemplo, instituições de ensino tem dispositivos que são normalmente utilizados por vários estudantes. Com esta definição, o administrador do Intune escola pode ativar a funcionalidade de PC partilhados para permitir que um usuário cada vez. Os estudantes não é possível alternar entre contas diferentes com sessão iniciada no dispositivo. Quando o aluno termina sessão, também optar por remover todas as definições específicas do usuário.

Os utilizadores finais podem iniciar sessão para esses dispositivos partilhados com uma conta de convidado. Depois dos utilizadores iniciam sessão, as credenciais são colocadas em cache. Que usam o dispositivo, os utilizadores finais apenas obtém o acesso às funcionalidades que permite. Por exemplo, escolha quando o dispositivo está presente em suspensão modo, se os utilizadores podem ver e guardar ficheiros localmente, ativar ou desativar as definições de gestão de energia e muito mais. Também controlar se a conta de convidado elimina quando o utilizador inicia sessão-off, ou eliminar as contas inativas quando for atingido um limiar.

Este artigo mostra-lhe como criar um perfil de configuração e inclui ligações para as definições disponíveis e suas descrições.

Quando o perfil é criado no Intune, implementar ou atribuir o perfil a grupos de dispositivos na sua organização. Também pode atribuir este perfil a grupos de dispositivos com tipos de dispositivo misto e versões do sistema operativo (SO).

## <a name="create-the-profile"></a>Criar o perfil

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar Perfil**.
3. Introduza as seguintes propriedades:

   - **Nome**: Introduza um nome descritivo para o novo perfil.
   - **Descrição**: Introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
   - **Plataforma**: Selecione **Windows 10 e posterior**.
   - **Tipo de perfil**: Selecione **dispositivos de vários utilizadores partilhado**.

4. Configurar as definições para [Windows 10 e posterior](shared-user-device-settings-windows.md) ou [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md).

5. Selecione **OK** > **Criar** para guardar as alterações.

Seu perfil é criado e apresentado na lista, mas ele não faz nada ainda. Não se esqueça [atribuir o perfil](device-profile-assign.md) a grupos de dispositivos na sua organização.

## <a name="next-steps"></a>Passos Seguintes

- Ver todas as definições de [Windows 10 e versões mais recentes](shared-user-device-settings-windows.md) e [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md).
- [Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
