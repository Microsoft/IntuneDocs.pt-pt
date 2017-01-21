---
title: "Autenticação multifator com o Azure AD | Documentos da Microsoft"
description: "Como solicitar a autenticação multifator no Azure AD para inscrição de dispositivos."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 12/12/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: 
translationtype: Human Translation
ms.sourcegitcommit: 85462d6cb5e3dc6ce8e94fe8fd1bc1c1c2b6e4f3
ms.openlocfilehash: 6e20eca60886781ae884107a224245639c5f107c


---

# <a name="multi-factor-authentication-for-microsoft-intune"></a>Autenticação multifator para Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Intune integra a autenticação multifator (MFA) do Azure AD para a inscrição de dispositivos para ajudá-lo a proteger os seus recursos empresariais. A MFA requer fatores de autenticação como a autenticação de texto, para além de nomes de utilizador e palavras-passe. A MFA é suportada para iOS, Android, Windows 8.1 ou posterior ou Windows Phone 8.1 ou dispositivos posteriores.

> [!NOTE]
>
> Esta é a nova experiência da MFA no Intune. A experiência anterior, a partir da qual os clientes estão a ser migrados, está descrita em [Proteger dispositivos Windows com a autenticação multifator](protect-windows-devices-with-multi-factor-authentication.md).
>
> Em versões mais antigas do Configuration Manager (anteriores à versão 1610), ainda verá a definição da MFA na consola de administração do Configuration Manager. Não tente configurar a MFA na consola de administração do Configuration Manager, pois não funcionará. Configure a MFA conforme descrito neste tópico.

### <a name="configuring-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Configurar o Intune para exigir a autenticação multifator na inscrição de dispositivos
Para exigir a MFA na inscrição do dispositivo, siga estes passos:

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



<!--HONumber=Dec16_HO3-->


