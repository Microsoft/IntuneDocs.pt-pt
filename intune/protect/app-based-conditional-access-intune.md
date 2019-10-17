---
title: Acesso condicional baseado em aplicativo com o Intune
titleSuffix: Microsoft Intune
description: Saiba como o acesso condicional baseado em aplicativo funciona com o Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d3cae06c3ce763fe8ca94bbed9bf35e8abef52c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502611"
---
# <a name="app-based-conditional-access-with-intune"></a>Acesso condicional baseado em aplicativo com o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

As [políticas de proteção de aplicações do Intune](../apps/app-protection-policy.md) ajudam-no a proteger os dados da sua empresa em dispositivos inscritos no Intune. Também pode utilizar políticas de proteção de aplicações em dispositivos de funcionários que não estejam inscritos para gestão no Intune. Neste caso, apesar de a sua empresa não gerir o dispositivo, ainda precisa de garantir que os recursos e os dados da empresa estão protegidos.

O acesso condicional baseado em aplicativo e o gerenciamento de aplicativo cliente adicionam uma camada de segurança, garantindo que somente os aplicativos cliente que dão suporte às políticas de proteção de aplicativo do Intune possam acessar o Exchange Online e outros serviços do Office 365.

> [!NOTE]
> Uma aplicação gerida é uma aplicação que tem políticas de proteção de aplicações aplicadas à mesma e pode ser gerida pelo Intune.

Pode bloquear as aplicações de e-mail incorporadas no iOS e Android quando permite apenas à aplicação Microsoft Outlook o acesso ao Exchange Online. Além disso, pode bloquear o acesso ao SharePoint Online para as aplicações que não têm políticas de proteção de aplicações do Intune aplicadas.

## <a name="prerequisites"></a>Pré-requisitos
Antes de criar uma política de acesso condicional com base no aplicativo, você deve ter:

- **Enterprise Mobility + Security (EMS)** ou uma **subscrição do Azure Active Directory (AD) Premium**
- Os utilizadores têm de ter uma licença do EMS ou do Azure AD

Para obter mais informações, consulte [preços do Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) ou [preços de Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

## <a name="supported-apps"></a>Aplicações suportadas

Uma lista de aplicativos que dão suporte ao acesso condicional baseado em aplicativo pode ser encontrada na [documentação de referência técnica do acesso condicional do Azure Active Directory.](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)

O acesso condicional baseado em aplicativo [também oferece suporte a aplicativos de linha de negócios (LOB)](app-modern-authentication-block.md), mas esses aplicativos precisam usar a [autenticação moderna do Office 365](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a). 

## <a name="how-app-based-conditional-access-works"></a>Como funciona o acesso condicional baseado em aplicativo

Neste exemplo, o administrador aplicou políticas de proteção de aplicativo ao aplicativo Outlook seguido por uma regra de acesso condicional que adiciona o aplicativo Outlook a uma lista aprovada de aplicativos que podem ser usados ao acessar o email corporativo.

> [!NOTE]
> A estrutura de fluxograma a seguir pode ser utilizada para outras aplicações geridas.

![Processo de acesso condicional baseado em aplicativo ilustrado em um gráfico de fluxo](./media/app-based-conditional-access-intune/ca-intune-common-ways-3.png)

1. O utilizador tenta autenticar-se no Azure AD a partir da aplicação Outlook.

2. O utilizador é redirecionado para a loja de aplicações para instalar uma aplicação de mediador quando tenta autenticar-se pela primeira vez. A aplicação de mediador pode ser o Microsoft Authenticator para iOS ou o Portal da Empresa da Microsoft para dispositivos Android.

   Se os utilizadores tentarem utilizar uma aplicação de e-mail nativa, serão redirecionados para a App Store para instalarem a aplicação Outlook.

3. A aplicação de mediador é instalada no dispositivo.

4. A aplicação de mediador inicia o processo de registo do Microsoft Azure AD que cria um registo de dispositivo no Microsoft Azure AD. Isso não é o mesmo que o processo de registro do MDM (gerenciamento de dispositivo móvel), mas esse registro é necessário para que as políticas de acesso condicional possam ser impostas no dispositivo.

5. A aplicação de mediador verifica a identidade da aplicação. Existe uma camada de segurança para que a aplicação de mediador possa validar se a aplicação está autorizada para ser utilizada pelo utilizador.

6. A aplicação de mediador envia o ID da Aplicação Cliente para o Azure AD como parte do processo de autenticação do utilizador para verificar se este consta na lista aprovada de políticas.

7. O Azure AD permite ao utilizador autenticar-se e utilizar a aplicação com base na lista aprovada de políticas. Se a aplicação não estiver na lista, o Microsoft Azure AD recusará o acesso à aplicação.

8. A aplicação Outlook comunica com o Serviço Cloud do Outlook para iniciar a comunicação com o Exchange Online.

9. O Serviço Cloud do Outlook comunica com o Azure AD para recuperar o token de acesso de serviço do Exchange Online para o utilizador.

10. A aplicação Outlook comunica com o Exchange Online para recuperar o e-mail empresarial do utilizador.

11. O e-mail empresarial é entregue na caixa de correio do utilizador.

## <a name="next-steps"></a>Próximos passos
[Criar uma política de acesso condicional com base no aplicativo](app-based-conditional-access-intune-create.md)

[Bloquear aplicações que não tenham autenticação moderna](app-modern-authentication-block.md)