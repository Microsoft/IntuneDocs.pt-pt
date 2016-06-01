---
# required metadata

title: Proteger os dispositivos Windows com a autenticação multifator | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Protect Windows devices with multi-factor authentication
O Microsoft Intune integra a autenticação multifator (MFA) para ajudar a proteger os seus recursos empresariais. A MFA requer fatores de autenticação como a autenticação de texto, para além de nomes de utilizador e palavras-passe. O Intune suporta a utilização da MFA durante a inscrição de dispositivos Windows 8.1 ou posterior, Windows Phone 8.1 ou Windows 10 Desktop e Mobile. 

## Requisitos de infraestrutura no local para a MFA no ADFS
Para configurar a autenticação multifator, precisa de:

-   **Um domínio do Active Directory ao qual é associado o servidor do ADFS.**

-   **O servidor dos Serviços de Federação do Active Directory (ADFS), configurado para a MFA.** Um servidor com Windows Server 2012 R2, configurado como um servidor do ADFS. Para mais informações, consulte: [Proteger recursos na nuvem e no local com o Servidor Multi-Factor Authentication do Azure com o Windows Server 2012 R2 AD FS](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/)

Todos os servidores indicados acima têm de cumprir os requisitos de sistema fornecidos em [Requisitos de Sistema e Informações de Instalação para o Windows Server 2012 R2](http://technet.microsoft.com/library/dn303418.aspx)

#### MFA com o Intune
Se a sua organização tiver uma infraestrutura de TI no local que inclua um domínio do Active Directory com os Serviços de Federação do Active Directory (ADFS), pode configurar a MFA no seu servidor de federação e, em seguida, ativar a MFA para inscrição no Intune. Ao configurar a MFA no Intune, permite que os utilizadores se autentiquem uma vez durante a inscrição e, em seguida, acedam aos recursos da empresa sem repetir sempre o processo de MFA.

>A MFA pode ser necessária por utilizador ou por grupo no servidor do AD FS.  

#### MFA sem o Intune
Se configurar a MFA no servidor de federação, mas não a ativar para inscrição no Intune, os utilizadores terão de utilizar a MFA sempre que acederem aos recursos da empresa (e não apenas na inscrição de dispositivos).

Também pode utilizar a MFA do Azure Active Directory (AAD) para exigir a MFA sempre que os utilizadores acederem aos recursos da empresa, por utilizador. A MFA no AAD é um serviço em nuvem que não exige uma infraestrutura de TI no local. Para saber como configurar a MFA no AAD, consulte [Introdução à Multi-Factor Authentication do Azure na nuvem.](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/)

## Exigir a MFA no ADFS durante a inscrição de dispositivos Windows
Para obter informações sobre como ativar a MFA no ADFS, consulte [Gerir o Risco com a Multi-Factor Authentication Adicional para Aplicações Confidenciais](http://technet.microsoft.com/library/dn280949.aspx)

## Configurar a MFA na inscrição de dispositivos no Intune
>[!Important]  
>Ative a MFA no seu ambiente de inquilino ou no local do Azure AD antes de exigir a MFA para a inscrição de dispositivos Windows no Intune. Se não o fizer, os utilizadores irão receber uma mensagem de erro quando tentarem inscrever os respetivos dispositivos Windows ou quando tentarem efetuar a associação do Azure AD nos respetivos dispositivos, se estiver configurada a inscrição automática durante a Associação do Azure AD.

1.  Na consola de administração do Intune, clique em **Admin** &gt; **Gestão de Dispositivos Móveis** &gt; **Multi-factor authentication**

2.  Clique em **Configurar a Multi-factor Authentication** e,em seguida, clique em **Ativar Multi-factor Authentication**.



<!--HONumber=May16_HO2-->


