---
title: Bloquear aplicações sem autenticação moderna no Intune
titleSuffix: Microsoft Intune
description: Saiba como bloquear aplicações que não utilizam autenticação moderna (ADAL).
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 354109cc4d84e34eebd5df6df86919f386e143f6
ms.sourcegitcommit: 9f99b4a7f20ab4175d6fa5735d9f4fd6a03e0d3a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/14/2018
ms.locfileid: "40251650"
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Bloquear aplicações que não utilizam autenticação moderna (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O acesso condicional com base na aplicação com políticas de proteção de aplicações depende de aplicações que utilizem o método de [autenticação moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), que se trata de uma implementação de OAuth2. A maioria das aplicações atuais do Office de ambiente de trabalho e móveis utiliza autenticação moderna. No entanto, existem aplicações de terceiros e aplicações do Office mais antigas que utilizam outros métodos de autenticação como a autenticação básica e a autenticação baseada em formulários.

Para bloquear o acesso a estas aplicações, recomendamos que faça o seguinte:

* Configure regras de afirmações do ADFS para bloquear protocolos de autenticação não moderna. São fornecidas instruções detalhadas no cenário 3 – [bloquear todo o acesso ao O365, exceto aplicações baseadas no browser](https://technet.microsoft.com/library/dn592182.aspx).
* Para o **Exchange e SharePoint Online**, utilize o Acesso Condicional do Azure Active Directory e o commandlet Set-SPOTenant do PowerShell para o SharePoint online. Para obter instruções detalhadas, veja [Configurar o SharePoint Online e Exchange Online para o acesso condicional do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication#legacy-authentication-protocols).


>[!IMPORTANT]
>O acesso condicional com base na aplicação não pode ser utilizado com a autenticação baseada no certificado do Azure Active Directory (Azure AD). Só pode ter um destes configurado de cada vez.

### <a name="see-also"></a>Veja também
[Acesso condicional com base na aplicação com o Intune](app-based-conditional-access-intune.md)
