---
title: Configurar a política de acesso condicional com base no aplicativo com o Intune
titleSuffix: Microsoft Intune
description: Saiba como criar uma política de acesso condicional com base no aplicativo com o Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94e9fcc77f8260c4a63150b5d0aef033677c524a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509668"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configurar políticas de acesso condicional com base no aplicativo com o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Configure políticas de acesso condicional com base no aplicativo para aplicativos que fazem parte da lista de aplicativos aprovados. A lista de aplicações aprovadas consiste em aplicações que foram testadas pela Microsoft.

> [!IMPORTANT]
> Este artigo percorre as etapas para adicionar uma política de acesso condicional com base no aplicativo. Pode utilizar os mesmos passos quando adicionar aplicações, como o SharePoint Online, Microsoft Teams e Microsoft Exchange Online a partir da lista de aplicações aprovadas.

## <a name="create-app-based-conditional-access-policies"></a>Criar políticas de acesso condicional com base no aplicativo
O Acesso Condicional é uma tecnologia do Azure Active Directory (Azure AD). O nó de Acesso Condicional acedido a partir do *Intune* é o mesmo nó acedido a partir do *Azure AD*. Tal significa que não precisa de alternar entre o Intune e o Microsoft Azure AD para configurar políticas.

> [!IMPORTANT]
> Você precisa ter uma licença Azure AD Premium para criar políticas de acesso condicional no portal do Intune.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Para criar uma política de acesso condicional com base no aplicativo

> [!IMPORTANT]
> Você precisa ter [políticas de proteção de aplicativo do Intune](../apps/app-protection-policies.md) aplicadas aos seus aplicativos antes de usar políticas de acesso condicional com base no aplicativo.

1. No **painel do Intune**, selecione **acesso condicional**.

2. No painel **políticas** , escolha **nova política** para criar sua nova política de acesso condicional com base no aplicativo.

4. Após introduzir um nome da política e configurar as definições disponíveis na secção **Atribuições**, selecione **Conceder** na secção **Controlos de acesso**.

5. Selecione **Pedir aplicação aprovada do cliente** , **Selecionar** e, em seguida, **Guardar** para guardar a nova política.

## <a name="next-steps"></a>Próximos passos
[Bloquear aplicações que não tenham autenticação moderna](app-modern-authentication-block.md)

## <a name="see-also"></a>Consulte também

[Proteger os dados da aplicação com políticas de proteção de aplicações](../apps/app-protection-policies.md)
[Acesso Condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)