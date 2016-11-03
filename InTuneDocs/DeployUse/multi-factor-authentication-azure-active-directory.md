---
title: "Autenticação multifator com o Azure AD | Microsoft Intune"
description: "Como solicitar a autenticação multifator no Azure AD para inscrição de dispositivos."
keywords: 
author: nbigman
ms.author: nbigman
manager: angerobe
ms.date: 09/22/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: NOINDEX,NOFOLLOW
translationtype: Human Translation
ms.sourcegitcommit: a7cced90c482498b5f5af424165f8dcf77b79b75
ms.openlocfilehash: ccd55cc8637ebccfdbddd05c4f6b182c7923a2ab


---

# Autenticação multifator para Microsoft Intune

O Intune integra a autenticação multifator (MFA) do Azure AD para a inscrição de dispositivos para ajudá-lo a proteger os seus recursos empresariais. A MFA requer fatores de autenticação como a autenticação de texto, para além de nomes de utilizador e palavras-passe. A MFA é suportada para iOS, Android, Windows 8.1 ou posterior ou Windows Phone 8.1 ou dispositivos posteriores.

> [!NOTE]
>
> Em versões mais antigas do Configuration Manager (anteriores à versão 1610), ainda verá a definição da MFA na consola de administração do Configuration Manager. Não tente configurar a MFA na consola de administração do Configuration Manager, pois não funcionará. Configure a MFA conforme descrito neste tópico.

### Configurar o Intune para exigir a autenticação multifator na inscrição de dispositivos
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



<!--HONumber=Sep16_HO4-->


