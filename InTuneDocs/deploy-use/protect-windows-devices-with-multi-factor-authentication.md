---
title: "Autenticação multifator para Windows | Documentos da Microsoft"
description: "O Intune integra a autenticação multifator (MFA) para ajudar a proteger os seus recursos empresariais."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: cc60ffb2cd7a1d0cad141712ba7e2341954b1f02


---

# <a name="protect-windows-devices-with-multi-factor-authentication"></a>Proteger dispositivos Windows autenticação multifator

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Microsoft Intune integra a autenticação multifator (MFA) para ajudar a proteger os seus recursos empresariais. A MFA requer fatores de autenticação como a autenticação de texto, para além de nomes de utilizador e palavras-passe. O Intune suporta a utilização da MFA durante a inscrição de dispositivos com Windows 8.1 ou posterior, Windows Phone 8.1, Windows 10 ou Windows 10 Mobile.

>[!NOTE]
>
>A MFA pode ser necessária por utilizador ou por grupo no servidor do AD FS.  


## <a name="on-premises-infrastructure-requirements-for-adfs-mfa"></a>Requisitos de infraestrutura no local para a MFA no ADFS
Para configurar a autenticação multifator, precisa de:

-   Inscrição automática, conforme descrito em [Configurar a gestão de dispositivos Windows](set-up-windows-device-management-with-microsoft-intune.md).
-   **Um domínio do Active Directory ao qual é associado o servidor do ADFS.**

-   **O servidor dos Serviços de Federação do Active Directory (ADFS), configurado para a MFA.** Um servidor com o Windows Server 2012 R2 e configurado como um servidor do ADFS. Para mais informações, consulte: [Proteger recursos na cloud e no local com o Servidor Multi-Factor Authentication do Azure com o Windows Server 2012 R2 AD FS](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/)

Os servidores cumprem os requisitos de sistema em [Requisitos de Sistema e Informações de Instalação para o Windows Server 2012 R2](http://technet.microsoft.com/library/dn303418.aspx).

 


#### <a name="mfa-with-intune"></a>MFA com o Intune
Se a sua organização tiver uma infraestrutura de TI no local que inclua um domínio do Active Directory com os Serviços de Federação do Active Directory (ADFS), pode configurar a MFA no seu servidor de federação e, em seguida, ativar a MFA para inscrição no Intune. Ao configurar a MFA no Intune, os utilizadores podem autenticar-se uma vez durante a inscrição e, em seguida, utilizar os recursos da empresa sem repetir sempre o processo de MFA.

>[!NOTE]
>
>A MFA pode ser necessária por utilizador ou por grupo no servidor do AD FS.  

#### <a name="mfa-without-intune"></a>MFA sem o Intune
Se configurar a MFA no servidor de federação, mas não a ativar para inscrição no Intune, os utilizadores terão de utilizar a MFA sempre que acederem aos recursos da empresa (e não apenas na inscrição de dispositivos).

Também pode utilizar a MFA do Azure Active Directory (Azure AD) para exigir a MFA sempre que os utilizadores acederem aos recursos da empresa, por utilizador. A MFA do Azure AD é um serviço na cloud que não exige uma infraestrutura de TI no local. Para saber como configurar a MFA do Azure AD, veja [Introdução à Multi-Factor Authentication do Azure na cloud](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/).

## <a name="requiring-adfs-mfa-during-enrollment-of-windows-devices"></a>Exigir a MFA no ADFS durante a inscrição de dispositivos Windows
Para obter mais informações sobre como ativar a MFA no ADFS, consulte [Gerir Riscos com a Autenticação Multifator Adicional para Aplicações Confidenciais](http://technet.microsoft.com/library/dn280949.aspx).

## <a name="set-up-device-enrollment-mfa-in-intune"></a>Configurar a MFA na inscrição de dispositivos no Intune
>[!Important]  
>Ative a MFA no seu ambiente de inquilino ou no local do Azure AD antes de exigir a MFA para a inscrição de dispositivos Windows no Intune. Se não o fizer, os utilizadores que tentarem inscrever os respetivos dispositivos Windows ou efetuar a associação do Azure AD nos respetivos dispositivos irão receber uma mensagem de erro quando a inscrição automática durante a Associação do Azure AD estiver configurada.

1.  Na consola de administração do Intune, escolha **Admin** &gt; **Mobile Device Management** &gt; **Multi-factor authentication**.

2.  Escolha **Configurar a Multi-factor Authentication** e, em seguida, escolha **Ativar Multi-factor Authentication**.



<!--HONumber=Dec16_HO5-->


