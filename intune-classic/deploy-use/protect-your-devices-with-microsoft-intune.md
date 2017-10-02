---
title: Proteger dispositivos com o Microsoft Intune
description: "Saiba mais sobre algumas das formas como o Intune o pode ajudar a que proteger os dispositivos contra acesso não autorizado e outras ameaças."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5bc18913ef361ce23e4524a6b74a7ad0c6018c9d
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/15/2017
---
# <a name="protect-devices-with-microsoft-intune"></a>Proteger dispositivos com o Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Microsoft Intune oferece um conjunto completo de capacidades para o ajudar a proteger os dispositivos que gere e os dados armazenados nesses dispositivos. Leia este tópico para saber o básico sobre estas capacidades e descobrir como pode saber mais.

## <a name="general-ways-to-protect-all-devices"></a>Formas gerais para proteger todos os dispositivos

### <a name="device-configuration"></a>Configuração do dispositivo
As [políticas de configuração](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) do Intune ajudam a proteger e configurar dispositivos, através do controlo de inúmeras definições e funcionalidades. Por exemplo:
- Pode restringir a utilização das funcionalidades de hardware do dispositivo, como a câmara ou o Bluetooth.
- Pode configurar aplicações conformes e não conformes. O utilizador será alertado se estiver instalada uma aplicação não conforme (e algumas plataformas podem realmente bloquear a instalação).

### <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>Repor códigos de acesso quando o acesso dos utilizadores aos respetivos dispositivos é bloqueado
Uma vez que o primeiro passo para proteger os dados da empresa em dispositivos móveis consiste em exigir um código de acesso para utilizar o dispositivo, por vezes, precisa de [repor um código de acesso](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) ou ajudar um empregado a fazê-lo, seja através da remoção do código de acesso ou da definição de um código de acesso temporário em modo remoto. Também pode [bloquear um dispositivo remotamente](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) se este for perdido ou roubado.

### <a name="retire-devices-and-remove-data"></a>Extinguir dispositivos e remover dados
Quando um dispositivo tem de ser [removido da gestão do Intune](retire-devices-from-microsoft-intune-management.md) (por exemplo, um utilizador sai ou o dispositivo perde-se ou é roubado), é provável que queira remover os dados desse dispositivo. O Intune fornece uma variedade de métodos para garantir que os dados da empresa permanecem seguros.

### <a name="require-devices-to-be-compliant"></a>Exigir conformidade dos dispositivos
O Intune inclui [políticas de conformidade do dispositivo](introduction-to-device-compliance-policies-in-microsoft-intune.md) que permitem-lhe avaliar (e em alguns casos remediar) dispositivos que não estão em conformidade com as regras que especificar. Por exemplo, pode informar sobre os dispositivos iOS que estão desbloqueados por jailbreak, se os dispositivos estão encriptados ou se os dispositivos Windows 10 são reportados como estando em bom estado de funcionamento pelo Serviço de Atestado de Estado de Funcionamento.

### <a name="protect-apps-and-the-data-they-use"></a>Proteger aplicações e os dados que utilizam
O Intune oferece-lhe uma variedade de funcionalidades para o ajudar a proteger as aplicações e os respetivos dados. Por exemplo, as políticas de gestão de aplicações móveis (MAM) podem impedir que seja criada uma cópia de segurança de uma aplicação protegida, restringir copiar e colar para outras aplicações, exigir um PIN para aceder a uma aplicação e muito mais. Para obter mais detalhes sobre como proteger aplicações, veja [Proteger aplicações e dados com o Microsoft Intune](protect-apps-and-data-with-microsoft-intune.md)

### <a name="add-an-additional-layer-of-protection-to-devices"></a>Adicionar uma camada adicional de proteção aos dispositivos
A [autenticação multifator (MFA)](multi-factor-authentication-azure-active-directory.md) é uma forma mais segura de autenticar os utilizadores dos dispositivos na rede.  Com a MFA, os utilizadores necessitam de confirmar a identidade para além do nome de utilizador e da palavra-passe, através de uma chamada telefónica ou mensagem de texto.

## <a name="further-capabilities-for-windows-devices"></a>Capacidades adicionais para dispositivos Windows

### <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>Controlar as definições do Windows Hello para Empresas em dispositivos Windows
O Intune permite efetuar a integração com o [Windows Hello para Empresas](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) (anteriormente denominado Microsoft Passport), que é um método de início de sessão alternativo para Windows 10 e posterior que utiliza o Active Directory ou uma conta do Azure Active Directory para substituir uma palavra-passe, um smart card ou um smart card virtual.

## <a name="further-capabilities-for-ios-devices"></a>Capacidades adicionais para dispositivos iOS

### <a name="bypass-activation-lock-on-ios-devices"></a>Ignorar Bloqueio de Ativação em dispositivos iOS
O Bloqueio de Ativação é uma funcionalidade que o ajuda a proteger os dispositivos dos utilizadores ao exigir que o Apple ID e a palavra-passe deles sejam introduzidos antes que qualquer pessoa possa apagá-los ou reativá-los. No entanto, esta funcionalidade pode originar problemas, por exemplo, se os utilizadores saírem da empresa sem remover o bloqueio. [Ignorar Bloqueio de Ativação de iOS](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md) pode ajudar ao remover o bloqueio de dispositivos iOS supervisionados, o que lhe permite realocá-los ou apagá-los.



## <a name="protect-windows-pcs-managed-with-the-intune-client"></a>Proteger os PCs Windows geridos com o cliente do Intune
O Intune continua a suportar políticas de segurança para PCs Windows que não inscreve, mas que gere com o software cliente de computador do Intune. Para saber como estas políticas podem ajudar a proteger os seus PCs Windows, consulte [Utilizar políticas para ajudar a proteger PCs Windows que executem o software cliente do Intune](policies-to-protect-windows-pcs-in-microsoft-intune.md).
