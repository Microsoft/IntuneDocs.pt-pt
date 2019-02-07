---
title: Proteger dispositivos com o Microsoft Intune
titleSuffix: Microsoft Intune
description: Saiba mais sobre algumas das formas como o Intune o pode ajudar a que proteger os dispositivos contra acesso não autorizado e outras ameaças.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 1b751a1637023db138539415a6c52e12d53f1101
ms.sourcegitcommit: 5b4a6c17bdba2f87e6ae81a3ac0cb88438a0fa27
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55807771"
---
# <a name="protect-devices-with-microsoft-intune"></a>Proteger dispositivos com o Microsoft Intune

O Microsoft Intune ajuda-o a proteger os dispositivos que gere e os dados armazenados nesses dispositivos.

## <a name="device-configuration"></a>Configuração do dispositivo
As [políticas de configuração](device-profiles.md) do Intune ajudam a proteger e configurar dispositivos através do controlo de inúmeras definições e funcionalidades. Por exemplo:
- Pode restringir a utilização das funcionalidades de hardware do dispositivo, como a câmara ou o Bluetooth.
- Pode configurar aplicações conformes e não conformes. O utilizador recebe um alerta se estiver instalada uma aplicação não conforme (e algumas plataformas podem realmente bloquear a instalação).

## <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>Repor códigos de acesso quando o acesso dos utilizadores aos respetivos dispositivos é bloqueado
Uma vez que o primeiro passo para proteger os dados da empresa em dispositivos móveis consiste em exigir um código de acesso para utilizar o dispositivo, por vezes, precisa de [repor um código de acesso](device-passcode-reset.md) ou ajudar um empregado a fazê-lo, seja através da remoção do código de acesso ou da definição de um código de acesso temporário em modo remoto. Também pode [bloquear um dispositivo remotamente](device-remote-lock.md) se este for perdido ou roubado.

## <a name="retire-devices-and-remove-data"></a>Extinguir dispositivos e remover dados
Quando um dispositivo tem de ser [removido da gestão do Intune](devices-wipe.md) (por exemplo, um utilizador sai ou o dispositivo perde-se ou é roubado), é provável que queira remover os dados desse dispositivo. O Intune proporciona uma variedade de métodos para confirmar que os dados da empresa se mantêm seguros.

## <a name="require-devices-to-be-compliant"></a>Exigir conformidade dos dispositivos
O Intune inclui [políticas de conformidade do dispositivo](device-compliance-get-started.md) que lhe permitem avaliar (e em certos casos remediar) dispositivos que não estão em conformidade com as regras que especificar. Por exemplo, pode obter relatórios sobre:
- dispositivos iOS desbloqueados por jailbreak
- dispositivos encriptados ou não encriptados
- o estado de funcionamento de dispositivos Windows 10 (conforme determinado pelo Serviço de Atestado de Estado de Funcionamento).

## <a name="protect-apps-and-the-data-they-use"></a>Proteger aplicações e os dados que utilizam
O Intune oferece-lhe uma variedade de funcionalidades para o ajudar a proteger as aplicações e os respetivos dados. Por exemplo, as políticas de gestão de aplicações móveis (MAM) podem:
- impedir a cópia de segurança de dados a partir de uma aplicação protegida
- restringir as operações de cópia e colagem para outras aplicações
- exigir um PIN para aceder a uma aplicação. Para obter mais informações, veja [Protect apps and data with Microsoft Intune (Proteger aplicações e dados com o Microsoft Intune)](app-protection-policy.md)

## <a name="add-an-additional-layer-of-protection-to-devices"></a>Adicionar uma camada adicional de proteção aos dispositivos
A [autenticação multifator (MFA)](multi-factor-authentication.md) é uma forma mais segura de autenticar os utilizadores dos dispositivos na rede.  Com a MFA, os utilizadores necessitam de confirmar a identidade para além do nome de utilizador e da palavra-passe, através de uma chamada telefónica ou mensagem de texto.

## <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>Controlar as definições do Windows Hello para Empresas em dispositivos Windows
O Intune permite realizar a integração com o [Windows Hello para Empresas](windows-hello.md), que é um método de início de sessão alternativo para Windows 10 e posterior que utiliza o Active Directory ou uma conta do Azure Active Directory para substituir uma palavra-passe, um smart card ou um smart card virtual.

## <a name="bypass-activation-lock-on-ios-devices"></a>Ignorar Bloqueio de Ativação em dispositivos iOS
O Bloqueio de ativação é uma funcionalidade que ajuda a proteger os dispositivos dos utilizadores. A funcionalidade exige que os utilizadores introduzam o Apple ID e a palavra-passe antes de qualquer pessoa poder eliminar ou reativar o dispositivo. No entanto, esta funcionalidade pode originar problemas, por exemplo, se os utilizadores saírem da empresa sem remover o bloqueio. [Ignorar Bloqueio de Ativação de iOS]( device-activation-lock-bypass.md) pode ajudar ao remover o bloqueio de dispositivos iOS supervisionados, o que lhe permite realocá-los ou apagá-los.

## <a name="next-steps"></a>Passos Seguintes

Saiba mais sobre a [defesa contra ameaças para dispositivos móveis](mobile-threat-defense.md)


