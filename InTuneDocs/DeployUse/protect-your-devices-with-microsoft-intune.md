---
title: Proteger dispositivos | Microsoft Intune
description: "Saiba mais sobre algumas das formas como o Intune o pode ajudar a que proteger os dispositivos contra acesso não autorizado e outras ameaças."
keywords: 
author: Robstackmsft
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c999a852b68762002ac94269e27ecbf46c8f9999
ms.openlocfilehash: 3318590eaedc6f0e96fb463dc016d5786eeb38fb


---

# Proteger dispositivos com o Microsoft Intune
Depois de ter os dispositivos geridos pelo Intune, deverá certificar-se de que estão protegidos contra o acesso não autorizado e outras ameaças. Seguem-se algumas das funcionalidades do Intune que o ajudam a realizar estes objetivos.

> [!TIP]
> Este tópico não contém todas as formas em que o Intune pode ajudar a proteger os seus dispositivos. Por exemplo, pode utilizar as políticas do Intune para configurar várias definições de segurança para os seus dispositivos, como configurar palavras-passe, definições de encriptação e funcionalidades de hardware, tais como Bluetooth e a câmara do dispositivo. Consulte [Gerir definições e funcionalidades nos seus dispositivos com o Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) para saber mais sobre estas definições.

## Repor códigos de acesso quando o acesso dos utilizadores aos respetivos dispositivos é bloqueado
O primeiro passo para proteger os dados da empresa em dispositivos móveis é exigir um código de acesso para utilizar o dispositivo. Por vezes é necessário [repor um código de acesso](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) ou ajudar um empregado a fazê-lo, ao remover o código de acesso ou ao definir remotamente um código de acesso temporário. Também pode [bloquear um dispositivo remotamente](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) se este for perdido ou roubado.

## Adicionar uma camada adicional de proteção aos dispositivos Windows
A [autenticação multifator (MFA)](protect-windows-devices-with-multi-factor-authentication.md) é uma forma mais segura de autenticar os utilizadores com dispositivos Windows e Windows Phone na rede. Com a MFA, os utilizadores necessitam de confirmar a identidade para além do nome de utilizador e da palavra-passe, através de uma chamada telefónica ou mensagem de texto.

## Controlar as definições do Microsoft Passport em dispositivos Windows
O Intune integra-se no [Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), que é um método de início de sessão alternativo para o Windows 10 e posterior. O Microsoft Passport for Work utiliza o Active Directory ou uma conta do Azure Active Directory para substituir uma palavra-passe, um smart card ou um smart card virtual.

## Ignorar Bloqueio de Ativação em dispositivos iOS
O Bloqueio de Ativação é uma funcionalidade que o ajuda a proteger os dispositivos dos utilizadores ao exigir que o Apple ID e a palavra-passe deles sejam introduzidos antes que qualquer pessoa possa apagá-los ou reativá-los. No entanto, esta funcionalidade pode originar problemas, por exemplo, se os utilizadores saírem da empresa sem remover o bloqueio. [Ignorar Bloqueio de Ativação de iOS](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md) pode ajudar ao remover o bloqueio de dispositivos iOS supervisionados, o que lhe permite realocá-los ou apagá-los.

## Proteger os PCs Windows geridos com o cliente do Intune
O Intune continua a suportar políticas de segurança para PCs Windows que não inscreve, mas que gere com o software cliente de computador do Intune. Para saber como estas políticas podem ajudar a proteger os seus PCs Windows, consulte [Utilizar políticas para ajudar a proteger PCs Windows que executem o software cliente do Intune](policies-to-protect-windows-pcs-in-microsoft-intune.md).



<!--HONumber=Aug16_HO2-->


