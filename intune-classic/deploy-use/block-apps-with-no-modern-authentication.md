---
title: "Bloquear aplicações sem autenticação moderna"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 098b652c-01e0-45d1-a731-620b0d3dc7c1
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0f192c0e41cf3b639cbfdac3f8c4fc3b8167266d
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Bloquear aplicações que não utilizam autenticação moderna (ADAL)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O acesso condicional com base na aplicação com políticas de proteção de aplicações depende de aplicações que utilizem o método de [autenticação moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), que se trata de uma implementação de OAuth2. A maioria das aplicações modernas do Office para ambiente de trabalho e para dispositivos móveis utilizam autenticação moderna, no entanto, existem aplicações de terceiros e aplicações do Office mais antigas que utilizam outros métodos de autenticação como a autenticação básica e a autenticação baseada em formulários.

Para bloquear o acesso a estas aplicações, recomendamos que efetue o seguinte:

* Configure regras de afirmações do ADFS para bloquear protocolos de autenticação não moderna. São fornecidas instruções detalhadas no cenário 3 – [bloquear todo o acesso ao O365, exceto aplicações baseadas no browser](https://technet.microsoft.com/library/dn592182.aspx).
* Para o **SharePoint Online**, desative a autenticação não moderna no serviço do SharePoint Online através do commandlet PowerShell [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx) para definir a propriedade de protocolos de autenticação legada como falsa:

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false

```


>[!IMPORTANT]
>O acesso condicional baseado na aplicação não pode ser utilizado com a autenticação baseada no certificado do Azure Active Directory (Azure AD). Só pode ter um destes configurado de cada vez.

### <a name="see-also"></a>Consulte também
[Permitir que apenas aplicações suportadas pelo Intune acedam aos serviços do O365](allow-policy-managed-apps-access-to-o365.md)
