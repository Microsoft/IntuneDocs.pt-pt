---
# required metadata

title: Proteger dispositivos com o Microsoft Intune | Microsoft Intune
description:
keywords:
author: Robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Proteger dispositivos com o Microsoft Intune
Depois de ter os dispositivos geridos pelo Intune, deverá certificar-se de que estão protegidos contra o acesso não autorizado e outras ameaças. Seguem-se algumas das funcionalidades do Intune que o ajudam a realizar estes objetivos.

> [!TIP]
> Este tópico não contém todas as formas em que o Intune pode ajudar a proteger os seus dispositivos. Por exemplo, pode utilizar as políticas do Intune para configurar várias definições de segurança para os seus dispositivos, como configurar palavras-passe, definições de encriptação e funcionalidades de hardware, tais como Bluetooth e a câmara do dispositivo. Consulte [Gerir definições e funcionalidades nos seus dispositivos com o Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) para saber mais sobre estas definições.

## Repor códigos de acesso quando o acesso dos utilizadores aos respetivos dispositivos é bloqueado
Uma vez que o primeiro passo para proteger os dados da empresa em dispositivos móveis consiste em exigir um código de acesso para utilizar o dispositivo, por vezes, precisa de [repor um código de acesso](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) ou ajudar um empregado a fazê-lo, seja através da remoção do código de acesso ou da definição de um código de acesso temporário em modo remoto. Também pode [bloquear um dispositivo remotamente](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) se este for perdido ou roubado.

## Adicionar uma camada adicional de proteção aos dispositivos Windows
A [autenticação multifator (MFA)](protect-windows-devices-with-multi-factor-authentication.md) é uma forma mais segura de autenticar os utilizadores com dispositivos Windows e Windows Phone na rede.  Com a MFA, os utilizadores necessitam de confirmar a identidade para além do nome de utilizador e da palavra-passe, através de uma chamada telefónica ou mensagem de texto.

## Controlar as definições do Microsoft Passport em dispositivos Windows
O Intune permite efetuar a integração com o [Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), que é um método de início de sessão alternativo para Windows 10 e posterior que utiliza o Active Directory ou uma conta do Azure Active Directory para substituir uma palavra-passe, um smart card ou um smart card virtual.

## Proteger os PCs Windows geridos com o cliente do Intune
O Intune continua a suportar políticas de segurança para PCs Windows que não inscreve, mas que gere com o software cliente de computador do Intune. Para saber como estas políticas podem ajudar a proteger os seus PCs Windows, consulte [Utilizar políticas para ajudar a proteger PCs Windows que executem o software cliente do Intune](policies-to-protect-windows-pcs-in-microsoft-intune.md).


<!--HONumber=May16_HO1-->


