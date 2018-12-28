---
title: Bloquear aplicações sem autenticação moderna no Intune
titleSuffix: Microsoft Intune
description: Saiba como bloquear aplicações que não utilizam autenticação moderna (ADAL) com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: dc9318d46892eab21e81c7eb2992f3476720abd1
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642460"
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Bloquear aplicações que não utilizam autenticação moderna (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Acesso condicional com base na aplicação com políticas de proteção de aplicações dependem de aplicativos usando [autenticação moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), que é uma implementação de OAuth2. Aplicativos mais atuais de ambiente de trabalho e móveis de Office utilizam autenticação moderna. No entanto, existem aplicações de terceiros e aplicações do Office mais antigas que utilizam outros métodos de autenticação, como autenticação básica e a autenticação baseada em formulários.

## <a name="block-apps"></a>Bloquear aplicações

Para bloquear o acesso às aplicações que não utilizam autenticação moderna, recomendamos os seguintes métodos:

- Configure regras de afirmações do ADFS para bloquear protocolos de autenticação não moderna. São fornecidas instruções detalhadas no cenário 3 – [bloquear todo o acesso ao O365, exceto aplicações baseadas no browser](https://technet.microsoft.com/library/dn592182.aspx).
- Para o **Exchange e SharePoint Online**, utilize o Acesso Condicional do Azure Active Directory e o commandlet Set-SPOTenant do PowerShell para o SharePoint online. Para obter instruções detalhadas, veja [Configurar o SharePoint Online e Exchange Online para o acesso condicional do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication#legacy-authentication-protocols).


>[!IMPORTANT]
>O acesso condicional com base na aplicação não pode ser utilizado com a autenticação baseada no certificado do Azure Active Directory (Azure AD). Só pode ter um destes configurado de cada vez.

## <a name="next-steps"></a>Passos Seguintes

- [Acesso condicional com base na aplicação com o Intune](app-based-conditional-access-intune.md)
