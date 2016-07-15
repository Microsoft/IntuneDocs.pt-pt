---
title: Sincronizar o Active Directory e adicionar utilizadores ao Intune | Microsoft Intune
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed26d65b98a0ae1bbc4fbac682fb53fddd50b4e5
ms.openlocfilehash: 70a2d32de67f0a69bbc29ca68a1c831c9cf38796


---


# Sincronizar o Active Directory e adicionar utilizadores ao Intune
Pode configurar a sincronização de diretórios para importar contas de utilizador do Active Directory no local para o Microsoft Azure Active Directory (Azure AD). Ligar o serviço do Active Directory no local a todos os serviços baseados no Azure Active Directory simplifica bastante a gestão da identidade de utilizadores. Também pode configurar funcionalidades de início de sessão único para tornar a experiência de autenticação dos utilizadores familiar e fácil.

Para tornar as coisas ainda mais fáceis, se utilizar vários serviços com o mesmo [inquilino do Azure AD](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), as contas de utilizador que tiver sincronizado anteriormente estão disponíveis em todos os serviços baseados na nuvem que partilhem a mesma subscrição do inquilino do Azure AD.

## Sincronizar os utilizadores no local com o Azure AD
A única ferramenta de que precisa para sincronizar as contas de utilizador com o Azure AD é o [Assistente do Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). O Assistente do Azure AD Connect proporciona uma experiência orientada e simplificada para ligar a sua infraestrutura de identidade no local à nuvem.  Escolha a sua topologia e as suas necessidades (um ou vários diretórios, sincronização de palavras-passe ou federação) e o assistente implementará e configurará todos os componentes necessários para ter a sua ligação pronta, incluindo serviços de sincronização, Serviços de Federação do Active Directory (AD FS) e o módulo Azure AD PowerShell.

> [!TIP]
> O Azure AD Connect engloba capacidades que foram anteriormente lançadas como Dirsync e Azure AD Sync. Saiba mais sobre a [integração de diretórios](http://technet.microsoft.com/library/jj573653.aspx). Para saber quais são as vantagens de sincronizar as contas de utilizador do diretório no local com o Azure AD, veja [Semelhanças entre o Active Directory e o Azure AD](http://technet.microsoft.com/library/dn518177.aspx).

## Conceder permissões de administrador
Depois de acrescentar utilizadores à sua subscrição do Intune, recomendamos que conceda [credenciais administrativas](administrative-accounts-websites-perms.md) a algumas contas de utilizador. A consola utilizada para atribuir credenciais administrativas depende do tipo de administrador que pretende atribuir:

-   **Administrador inquilino**: utilize o **[!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)]** para atribuir este tipo de administrador para gerir a sua subscrição, incluindo faturação, armazenamento na nuvem e gestão dos utilizadores que podem utilizar o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

-   **Administrador do serviço**: utilize a **[!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]** para atribuir este tipo de administrador a tarefas quotidianas, incluindo gestão de dispositivos móveis ou de computadores, implementação de políticas ou de software e execução de relatórios.


### Passos seguintes
Parabéns! Acabou de concluir o passo 3 do *Guia de introdução do Intune*.

>[!div class="step-by-step"]

>[&larr; **Definições de domínio**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Gerir licenças do Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Jun16_HO4-->


