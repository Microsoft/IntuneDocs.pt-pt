---
title: Configurar a política de acesso condicional com base na aplicação com o Intune
titlesuffix: Microsoft Intune
description: Saiba como criar uma política de acesso condicional com base na aplicação com o Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 079671064c09c22d151ea71f8b3fb385652aef0f
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816927"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configurar políticas de acesso condicional com base na aplicação com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Configure políticas de acesso condicional com base na aplicação para aplicações que fazem parte da lista de aplicações aprovadas. A lista de aplicações aprovadas consiste em aplicações que foram testadas pela Microsoft.

> [!IMPORTANT]
> Este artigo explica os passos para adicionar uma política de acesso condicional com base nas aplicações. Pode utilizar os mesmos passos quando adicionar aplicações, como o SharePoint Online, Microsoft Teams e Microsoft Exchange Online a partir da lista de aplicações aprovadas.

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>Criar políticas de acesso condicional com base nas aplicações na carga de trabalho do Azure AD

Os administradores de TI podem criar políticas de acesso condicional com base nas aplicações a partir da carga de trabalho do Azure AD. Este acesso significa que não precisa de alternar entre as cargas de trabalho do Azure e do Intune.

> [!IMPORTANT]
> Tem de ter uma licença do Azure AD Premium para criar políticas de acesso condicional do Azure AD a partir do Intune no portal do Azure.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Para criar uma política de acesso condicional com base na aplicação

> [!IMPORTANT]
> Tem de aplicar [políticas de proteção de aplicações do Intune](app-protection-policies.md) às suas aplicações antes de utilizar as políticas de acesso condicional com base nas aplicações.

1. No **Dashboard do Intune**, escolha **Acesso condicional**.

2. No painel **Políticas**, selecione **Nova política** para criar a sua nova política de acesso condicional com base na aplicação.

4. Após introduzir um nome da política e configurar as definições disponíveis na secção **Atribuições**, selecione **Conceder** na secção **Controlos de acesso**.

5. Selecione **Pedir aplicação aprovada do cliente** , **Selecionar** e, em seguida, **Guardar** para guardar a nova política.

## <a name="next-steps"></a>Passos Seguintes
[Bloquear aplicações que não tenham autenticação moderna](app-modern-authentication-block.md)

### <a name="see-also"></a>Consulte também

[Proteger os dados da aplicação com políticas de proteção de aplicações](app-protection-policies.md)
[Acesso Condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
