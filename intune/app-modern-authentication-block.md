---
title: Bloquear aplicações sem autenticação moderna no Intune
titleSuffix: Microsoft Intune
description: Saiba como bloquear aplicações que não utilizam autenticação moderna (ADAL) com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/22/2019
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4af330f14b8622dd0ee977b2fa81a726845f4da
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57400165"
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Bloquear aplicações que não utilizam autenticação moderna (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Acesso condicional com base na aplicação com políticas de proteção de aplicações dependem de aplicativos usando [autenticação moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), que é uma implementação de OAuth2. Aplicativos mais atuais de ambiente de trabalho e móveis de Office utilizam autenticação moderna. No entanto, existem aplicações de terceiros e aplicações do Office mais antigas que utilizam outros métodos de autenticação, como autenticação básica e a autenticação baseada em formulários.

## <a name="block-apps"></a>Bloquear aplicações

Para bloquear o acesso às aplicações que não utilizam autenticação moderna, recomendamos os seguintes métodos:

- Configure regras de afirmações do ADFS para bloquear protocolos de autenticação não moderna. São fornecidas instruções detalhadas no cenário 3 – [bloquear todo o acesso ao O365, exceto aplicações baseadas no browser](https://technet.microsoft.com/library/dn592182.aspx).
- Para **Exchange e SharePoint Online**, utilizar o acesso condicional e utilize o commandlet do PowerShell Set-SPOTenant para o SharePoint online. Para obter instruções detalhadas, veja [Configurar o SharePoint Online e Exchange Online para o acesso condicional do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication#legacy-authentication-protocols).


>[!IMPORTANT]
>Acesso condicional com base na aplicação não pode ser utilizado com a autenticação baseada em certificado do Azure Active Directory (Azure AD). Só pode ter um destes configurado de cada vez.

## <a name="next-steps"></a>Passos Seguintes

- [Acesso condicional com base na aplicação com o Intune](app-based-conditional-access-intune.md)
