---
title: Bloquear aplicações sem autenticação moderna no Intune
titleSuffix: Microsoft Intune
description: Saiba mais sobre os aplicativos e a ADAL (autenticação moderna) usando o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81c7746985bd3449ce4e5f2d90780bcd117069eb
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509655"
---
# <a name="block-apps-that-dont-use-modern-authentication-adal"></a>Bloquear aplicações que não utilizam a autenticação moderna (ADAL)

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O acesso condicional baseado em aplicativo com políticas de proteção de aplicativo depende de aplicativos que usam [autenticação moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), que é uma implementação de OAuth2. A maioria das aplicações atuais do Office de ambiente de trabalho e móveis utiliza a autenticação moderna. No entanto, há aplicativos de terceiros e aplicativos mais antigos do Office que usam outros métodos de autenticação, como autenticação básica e autenticação baseada em formulários.

## <a name="block-access-to-apps"></a>Bloquear o acesso a aplicações

Para bloquear o acesso às aplicações que não utilizam a autenticação moderna, utilize as políticas de proteção de aplicações do Intune para implementar o acesso condicional. Para obter mais informações, consulte [acesso condicional baseado em aplicativo com o Intune](app-based-conditional-access-intune.md).

## <a name="additional-information"></a>Informações adicionais

Para obter mais informações sobre o acesso condicional do Microsoft Azure AD, veja os seguintes tópicos:
- [O que é o acesso condicional no Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Como funciona o acesso condicional baseado em aplicativo](app-based-conditional-access-intune.md#how-app-based-conditional-access-works)
- [Configurar o SharePoint Online e o Exchange Online para Azure Active Directory acesso condicional](https://docs.microsoft.com/azure/active-directory/conditional-access/conditional-access-for-exo-and-spo)

## <a name="next-steps"></a>Próximos passos

- [Acesso condicional baseado em aplicativo com o Intune](app-based-conditional-access-intune.md)
