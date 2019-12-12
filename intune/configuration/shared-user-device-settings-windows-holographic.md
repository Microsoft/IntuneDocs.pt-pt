---
title: Configurações do dispositivo compartilhado comercial do Windows Holographic-Microsoft Intune-Azure | Microsoft Docs
description: Adicione e use o Windows Holographic for Business para configurar dispositivos que são compartilhados ou usados por vários usuários no Microsoft Intune. Consulte uma lista das configurações de gerenciamento de conta e o que elas fazem nos dispositivos, incluindo o Microsoft HoloLens.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9c89712539d4e5bd78cc317af2af396f8ca7006
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72492216"
---
# <a name="windows-holographic-for-business-settings-to-manage-shared-devices-using-intune"></a>Configurações do Windows Holographic para empresas para gerenciar dispositivos compartilhados usando o Intune

Os dispositivos Windows Holographic for Business, como o Microsoft HoloLens, podem ser usados por vários usuários. Os dispositivos que têm vários usuários são chamados de dispositivos compartilhados e fazem parte das soluções de MDM (gerenciamento de dispositivo móvel).

Usando Microsoft Intune, os usuários podem entrar nesses dispositivos compartilhados com uma conta de convidado. À medida que usam o dispositivo, eles só obtêm acesso aos recursos permitidos.

Este artigo lista e descreve as configurações usadas em um perfil de configuração de dispositivo do Windows Holographic for Business. Quando o perfil é criado no Intune, você implanta ou atribui o perfil aos grupos de dispositivos em sua organização. Você também pode atribuir esse perfil a um grupo de dispositivos com tipos de dispositivos mistos e versões de sistema operacional.

Para obter mais informações sobre esse recurso no Intune, consulte [controlar o acesso, contas e recursos de energia no PC compartilhado ou em dispositivos de vários usuários](shared-user-device-settings.md). Para obter mais informações sobre o CSP do Windows, consulte [ACCOUNTMANAGEMENT CSP](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp).

## <a name="before-your-begin"></a>Antes de começar

[Crie o perfil](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>Configurações de dispositivo de vários usuários compartilhado

> [!NOTE]
> Dispositivos que executam o Windows Holographic for Business, incluindo o Microsoft HoloLens, dão suporte apenas às configurações de **Gerenciamento de conta** . Se você definir qualquer uma das outras configurações mostradas no Intune, incluindo o **modo de computador compartilhado**, ela não afetará esses dispositivos.

- **Gerenciamento de conta**: Defina como **habilitar** para excluir automaticamente as contas locais criadas por convidados e contas no AD e no Azure AD. Quando um usuário desconecta o dispositivo ou quando a manutenção do sistema é executada, essas contas são excluídas. Quando habilitado, também defina:
  - **Exclusão de conta**: escolha quando as contas são excluídas: **no limite de espaço de armazenamento**, no limite de espaço de **armazenamento e no limite inativo**, ou **imediatamente após**o logout. Insira também:
    - **Iniciar exclusão limite (%)** : Insira um percentual (0-100) de espaço em disco. Quando o espaço total de disco/armazenamento cai abaixo do valor inserido, as contas armazenadas em cache são excluídas. Ele exclui continuamente as contas para recuperar o espaço em disco. As contas que estão inativas mais longas são excluídas primeiro.
    - **Parar exclusão limite (%)** : Insira um percentual (0-100) de espaço em disco. Quando o espaço total de disco/armazenamento atende ao valor inserido, a exclusão é interrompida.

  Defina como **desabilitar** para manter as contas local, AD e Azure ad criadas por convidados.

  > [!NOTE]
  > Os dispositivos Microsoft HoloLens só dão suporte às configurações de **Gerenciamento de conta** .

## <a name="next-steps"></a>Próximos passos

- [Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
- Consulte as configurações para [Windows 10 e mais recente](shared-user-device-settings-windows.md).
