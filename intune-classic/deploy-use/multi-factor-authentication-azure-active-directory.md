---
title: "Autenticação multifator para inscrição de dispositivos no Intune"
description: "Como solicitar a autenticação multifator no Azure AD para inscrição de dispositivos."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 02/17/2017
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: 
ms.custom: intune-classic
ms.openlocfilehash: 805ca79932788786636d365109e06aee836d8a0e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="multi-factor-authentication-for-intune-device-enrollments"></a>Autenticação multifator para inscrições de dispositivos no Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Intune integra a autenticação multifator (MFA) do Azure AD para a inscrição de dispositivos para ajudá-lo a proteger os seus recursos empresariais.

A MFA exige dois ou mais dos seguintes métodos de verificação: 

- Algo que saiba (normalmente uma palavra-passe ou PIN).
- Algo que tenha (um dispositivo fidedigno que não seja duplicado facilmente, como um telemóvel).
- Algo que seja (biometria).

A MFA é suportada para iOS, Android, Windows 8.1 ou posterior ou Windows Phone 8.1 ou dispositivos posteriores.

> [!NOTE]
> Em versões mais antigas do Configuration Manager (anteriores à versão 1610), ainda verá a definição da MFA na consola de administração do Configuration Manager. Não tente configurar a MFA na consola de administração do Configuration Manager, pois não funcionará. Configure a MFA conforme descrito neste tópico.

### <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Configurar o Intune para exigir a autenticação multifator na inscrição de dispositivos
Para exigir MFA na inscrição de um dispositivo, siga estes passos:

1. Inicie sessão no [Portal do Microsoft Azure](https://manage.windowsazure.com) com as suas credenciais de administrador.
2. Escolha o seu inquilino.
2. Escolha o separador **aplicações**. Verá uma lista de serviços para os quais pode configurar funcionalidades de segurança do Azure AD.
3. Escolha **Inscrição do Microsoft Intune**.
4. Escolha **Configurar**. 
5. Em **autenticação multifator e regras de acesso com base na localização** pode:
    
    -  Ativar as regras de acesso
    -  Escolha se pretende aplicar as regras a todos os utilizadores ou a grupos de segurança específicos do Azure AD.
    -  Exija a autenticação multifator para a inscrição de todos os dispositivos.
    -  Exija a autenticação multifator para a inscrição quando o dispositivo não estiver em funcionamento.
    -  Escolha **Bloquear o acesso aos recursos empresariais** para impedir a inscrição de um dispositivo quando estiver ligado à rede empresarial. 
4. Também pode clicar na ligação para **definir/editar o local da rede profissional** para configurar os requisitos de conetividade de rede para a inscrição de dispositivos.

> [!IMPORTANT]
> 
> Não configure **Regras de acesso com base no dispositivo** para a Inscrição no Microsoft Intune.
