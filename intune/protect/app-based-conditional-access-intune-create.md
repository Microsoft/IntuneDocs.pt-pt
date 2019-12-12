---
title: Configurar a política de acesso condicional com base no aplicativo com o Intune
titleSuffix: Microsoft Intune
description: Saiba como criar uma política de acesso condicional com base no aplicativo com o Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 465f8b0001e5e2a049a3ffe12469bdb5057854ec
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712840"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configurar políticas de acesso condicional com base no aplicativo com o Intune

Configure políticas de acesso condicional com base no aplicativo para aplicativos que fazem parte da lista de aplicativos aprovados. A lista de aplicações aprovadas consiste em aplicações que foram testadas pela Microsoft.

Antes de poder usar políticas de acesso condicional com base no aplicativo, você precisa ter [políticas de proteção de aplicativo do Intune](../apps/app-protection-policies.md) aplicadas aos seus aplicativos.

> [!IMPORTANT]
> Este artigo percorre as etapas para adicionar uma política de acesso condicional com base no aplicativo. Pode utilizar os mesmos passos quando adicionar aplicações, como o SharePoint Online, Microsoft Teams e Microsoft Exchange Online a partir da lista de aplicações aprovadas.

## <a name="create-app-based-conditional-access-policies"></a>Criar políticas de acesso condicional com base no aplicativo

O Acesso Condicional é uma tecnologia do Azure Active Directory (Azure AD). O nó de acesso condicional que você acessa do *Intune* é o mesmo nó que você acessa do *Azure ad*. Como é o mesmo nó, você não precisa alternar entre o Intune e o Azure AD para configurar políticas.

Antes de poder criar políticas de acesso condicional do centro de administração do Microsoft Endpoint Manager, você deve ter uma licença Azure AD Premium.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Para criar uma política de acesso condicional com base no aplicativo

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)

2. Selecione **Endpoint security** > **acesso condicional** > **nova política**.

3. Insira um **nome**de política e, em *atribuições*, selecione **usuários e grupos**. Utilize as opções Incluir ou Excluir para adicionar os grupos à política e selecione **Concluído**.

4. Selecione **aplicativos de nuvem ou ações**e escolha quais aplicativos proteger. Por exemplo, escolha **Selecionar aplicações** e selecione **Office 365 SharePoint Online** e **Office 365 Exchange Online**.

   Selecione **Concluído** para guardar as alterações.

5. Selecione **Condições** > **Aplicações do cliente** para aplicar a política a aplicações e browsers. Por exemplo, selecione **Sim** e, em seguida, ative **Browser** e **Aplicações móveis e clientes de ambiente de trabalho**.

   Selecione **Concluído** para guardar as alterações.

6. Em *controles de acesso*, selecione **conceder** para aplicar o acesso condicional com base na conformidade do dispositivo. Por exemplo, selecione **Conceder acesso** > **Pedir que o dispositivo seja marcado como conforme**.

   Escolha **Selecionar** para guardar as alterações.

7. Para **habilitar política**, selecione **ativado**e, em seguida, selecione **criar** para salvar suas alterações.





## <a name="next-steps"></a>Próximos passos
[Bloquear aplicações que não tenham autenticação moderna](app-modern-authentication-block.md)

## <a name="see-also"></a>Consulte também

[Proteger os dados da aplicação com políticas de proteção de aplicações](../apps/app-protection-policies.md)
[Acesso Condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
