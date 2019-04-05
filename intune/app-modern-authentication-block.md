---
title: Bloquear aplicações sem autenticação moderna no Intune
titleSuffix: Microsoft Intune
description: Saiba mais sobre a aplicação e a autenticação moderna (ADAL) com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/03/2019
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ca96f36f8813d80c7ebb07bfb3bd65f8aa0b392
ms.sourcegitcommit: 71314481e644025c005019b478b4cbeaf2390ea9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041679"
---
# <a name="block-apps-that-dont-use-modern-authentication-adal"></a>Impedir que as aplicações que não utilizam autenticação moderna (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Acesso condicional com base na aplicação com políticas de proteção de aplicações dependem de aplicativos usando [autenticação moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), que é uma implementação de OAuth2. Aplicativos mais atuais de ambiente de trabalho e móveis de Office utilizam autenticação moderna. No entanto, existem aplicações de terceiros e aplicações do Office mais antigas que utilizam outros métodos de autenticação, como autenticação básica e a autenticação baseada em formulários.

## <a name="block-access-to-apps"></a>Bloquear o acesso a aplicações

Para bloquear o acesso às aplicações que não utilizam autenticação moderna, utilize políticas de proteção de aplicações do Intune para implementar o acesso de condição. Para obter mais informações, consulte [acesso condicional com base na aplicação com o Intune](app-based-conditional-access-intune.md).

## <a name="additional-information"></a>Informações adicionais

Para obter mais informações sobre o acesso condicional do Azure AD, consulte os seguintes tópicos:
- [O que é o acesso condicional no Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Como funciona o acesso condicional com base na aplicação](app-based-conditional-access-intune.md#how-app-based-conditional-access-works)
- [Configurar o SharePoint Online e Exchange Online para o acesso condicional do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/conditional-access-for-exo-and-spo)

## <a name="next-steps"></a>Passos Seguintes

- [Acesso condicional com base na aplicação com o Intune](app-based-conditional-access-intune.md)
