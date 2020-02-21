---
title: Acesso Condicional baseado em aplicativos com Intune
titleSuffix: Microsoft Intune
description: Saiba como funciona o Acesso Condicional baseado em aplicativos com o Intune.
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
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9fe275be3f7eccee7f60dc27e5068e5b91ca93d
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514154"
---
# <a name="app-based-conditional-access-with-intune"></a>Acesso Condicional baseado em aplicativos com Intune

As [políticas de proteção de aplicações do Intune](../apps/app-protection-policy.md) ajudam-no a proteger os dados da sua empresa em dispositivos inscritos no Intune. Também pode utilizar políticas de proteção de aplicações em dispositivos de funcionários que não estejam inscritos para gestão no Intune. Neste caso, apesar de a sua empresa não gerir o dispositivo, ainda precisa de garantir que os recursos e os dados da empresa estão protegidos.

O Acesso Condicional baseado em aplicativos e a gestão de aplicações de clientes adicionam uma camada de segurança, certificando-se de que apenas aplicações de clientes que suportam políticas de proteção de aplicações Intune podem aceder ao Exchange online e a outros serviços do Office 365.

> [!NOTE]
> Uma aplicação gerida é uma aplicação que tem políticas de proteção de aplicações aplicadas à mesma e pode ser gerida pelo Intune.

Pode bloquear as aplicações de correio incorporados no iOS/iPadOS e Android quando permite apenas que a aplicação Microsoft Outlook aceda ao Exchange Online. Além disso, pode bloquear o acesso ao SharePoint Online para as aplicações que não têm políticas de proteção de aplicações do Intune aplicadas.

## <a name="prerequisites"></a>Pré-requisitos

Antes de criar uma política de acesso condicional baseada em aplicativos, deve ter:

- **Enterprise Mobility + Security (EMS)** ou uma **subscrição do Azure Active Directory (AD) Premium**
- Os utilizadores têm de ter uma licença do EMS ou do Azure AD

Para mais informações, consulte os preços da [Mobilidade Empresarial](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) ou [os preços do Diretório Ativo Azure.](https://azure.microsoft.com/pricing/details/active-directory/)

## <a name="supported-apps"></a>Aplicações suportadas

Uma lista de aplicações que suportam o Acesso Condicional baseado em aplicações pode ser encontrada na documentação técnica de referência técnica de acesso condicional do [Diretório Ativo Azure.](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)

O Acesso Condicional baseado em [aplicativos também suporta aplicações de linha de negócio (LOB),](app-modern-authentication-block.md)mas estas aplicações precisam de usar a [autenticação moderna do Office 365.](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) 

## <a name="how-app-based-conditional-access-works"></a>Como funciona o Acesso Condicional baseado em aplicativos

Neste exemplo, o administrador aplicou políticas de proteção de aplicações à aplicação Outlook seguida de uma regra de Acesso Condicional que adiciona a app Outlook a uma lista aprovada de aplicações que podem ser usadas no acesso a e-mails corporativos.

> [!NOTE]
> O fluxograma seguinte pode ser usado para outras aplicações geridas.

![Processo de acesso condicional baseado em aplicativos ilustrado num gráfico de fluxo](./media/app-based-conditional-access-intune/ca-intune-common-ways-3.png)

1. O utilizador tenta autenticar-se no Azure AD a partir da aplicação Outlook.

2. O utilizador é redirecionado para a loja de aplicações para instalar uma aplicação de mediador quando tenta autenticar-se pela primeira vez. A aplicação de mediador pode ser o Microsoft Authenticator para iOS ou o Portal da Empresa da Microsoft para dispositivos Android.

   Se os utilizadores tentarem utilizar uma aplicação de e-mail nativa, serão redirecionados para a App Store para instalarem a aplicação Outlook.

3. A aplicação de mediador é instalada no dispositivo.

4. A aplicação de mediador inicia o processo de registo do Microsoft Azure AD que cria um registo de dispositivo no Microsoft Azure AD. Este não é o mesmo que o processo de inscrição de dispositivos móveis (MDM), mas este registo é necessário para que as políticas de Acesso Condicional possam ser aplicadas no dispositivo.

5. A aplicação de mediador verifica a identidade da aplicação. Existe uma camada de segurança para que a aplicação de mediador possa validar se a aplicação está autorizada para ser utilizada pelo utilizador.

6. A aplicação de mediador envia o ID da Aplicação Cliente para o Azure AD como parte do processo de autenticação do utilizador para verificar se este consta na lista aprovada de políticas.

7. O Azure AD permite ao utilizador autenticar-se e utilizar a aplicação com base na lista aprovada de políticas. Se a aplicação não estiver na lista, o Microsoft Azure AD recusará o acesso à aplicação.

8. A aplicação Outlook comunica com o Serviço Cloud do Outlook para iniciar a comunicação com o Exchange Online.

9. O Serviço Cloud do Outlook comunica com o Azure AD para recuperar o token de acesso de serviço do Exchange Online para o utilizador.

10. A aplicação Outlook comunica com o Exchange Online para recuperar o e-mail empresarial do utilizador.

11. O e-mail empresarial é entregue na caixa de correio do utilizador.

## <a name="next-steps"></a>Próximos passos
[Criar uma política de acesso condicional baseada em aplicativos](app-based-conditional-access-intune-create.md)

[Bloquear aplicações que não tenham autenticação moderna](app-modern-authentication-block.md)
