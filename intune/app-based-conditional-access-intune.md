---
title: "Acesso condicional com base na aplicação com o Intune"
description: "Compreenda os conceitos de como o acesso condicional baseado em aplicações funciona com o Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9899f08cac650b1fea05370eb52327bc3c204a48
ms.sourcegitcommit: 3bafbec5822bb5baa2d313f2bd19f35a67438beb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2017
---
# <a name="app-based-conditional-access-with-intune"></a>Acesso condicional com base na aplicação com o Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

As [políticas de proteção de aplicações do Intune](app-protection-policy.md) ajudam-no a proteger os dados da sua empresa em dispositivos inscritos no Intune. Também pode utilizar políticas de proteção de aplicações em dispositivos de funcionários que não estejam inscritos para gestão no Intune. Neste caso, apesar de a sua empresa não gerir o dispositivo, ainda precisa de garantir que os recursos e os dados da empresa estão protegidos.

O acesso condicional com base em aplicações e a gestão de aplicações móveis adicionam uma camada de segurança ao garantir que apenas as aplicações móveis que suportam políticas de proteção de aplicações do Intune podem aceder ao Exchange Online e a outros serviços do Office 365.

> [!NOTE]
> Uma aplicação gerida é uma aplicação que tem políticas de proteção de aplicações aplicadas à mesma e pode ser gerida pelo Intune.

Pode bloquear as aplicações de e-mail incorporadas no iOS e Android quando permite apenas à aplicação Microsoft Outlook o acesso ao Exchange Online. Além disso, pode bloquear o acesso ao SharePoint Online para as aplicações que não têm políticas de proteção de aplicações do Intune aplicadas.

## <a name="prerequisites"></a>Pré-requisitos
Antes de criar uma política de acesso condicional com base em aplicações, tem de ter:

- **Enterprise Mobility + Security (EMS)** ou uma **subscrição do Azure Active Directory (AD) Premium**
- Os utilizadores têm de ter uma licença do EMS ou do Azure AD

Para obter mais informações, veja [Preços do Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) ou [Preços do Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

## <a name="supported-apps"></a>Aplicações suportadas

- **Exchange Online**:
    - Microsoft Outlook para Android e iOS.
<br></br>
- **SharePoint Online**
    - Microsoft Word para iOS e Android
    - Microsoft Excel para iOS e Android
    - Microsoft PowerPoint para iOS e Android
    - Microsoft OneDrive para Empresas para iOS e Android
    - Microsoft OneNote para iOS
<br></br>
- **Microsoft Teams**

O acesso condicional com base em aplicações [também suporta aplicações de linha de negócio (LOB)](https://docs.microsoft.com/intune-classic/deploy-use/block-apps-with-no-modern-authentication), mas estas aplicações precisam de utilizar a [autenticação moderna do Office 365](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a).

## <a name="how-app-based-conditional-access-works"></a>Como funciona o acesso condicional com base nas aplicações

Neste exemplo, o administrador tem políticas de proteção de aplicações aplicadas à aplicação Outlook seguidas de uma regra de acesso condicional que adiciona a aplicação Outlook a uma lista aprovada de aplicações que podem ser utilizadas ao aceder ao e-mail empresarial.

> [!NOTE]
> A estrutura de fluxograma a seguir pode ser utilizada para outras aplicações geridas.

![Fluxograma do acesso condicional com base em aplicações com o Intune](./media/ca-intune-common-ways-3.png)

1.  O utilizador tenta autenticar-se no Azure AD a partir da aplicação Outlook.

2.  O utilizador é redirecionado para a loja de aplicações para instalar uma aplicação de mediador quando tenta autenticar-se pela primeira vez. A aplicação de mediador pode ser o Microsoft Authenticator para iOS ou o Portal da Empresa da Microsoft para dispositivos Android.

 Se os utilizadores tentarem utilizar uma aplicação de e-mail nativa, serão redirecionados para a App Store para instalarem a aplicação Outlook.

3.  A aplicação de mediador é instalada no dispositivo.

4.  A aplicação de mediador inicia o processo de registo do Azure AD que cria um registo de dispositivo no Azure AD. Este processo não é igual ao processo de inscrição de gestão de dispositivos móveis (MDM). Contudo, este registo é necessário para que as políticas de acesso condicional possam ser aplicadas no dispositivo.

5.  A aplicação de mediador verifica a identidade da aplicação. Existe uma camada de segurança para que a aplicação de mediador possa validar se aplicação está autorizada a ser utilizado pelo utilizador.

6.  A aplicação de mediador envia o ID da Aplicação Cliente para o Azure AD como parte do processo de autenticação do utilizador para verificar se este consta na lista aprovada de políticas.

7.  O Azure AD permite ao utilizador autenticar-se e utilizar a aplicação com base na lista aprovada de políticas. Se a aplicação não constar na lista, o Azure AD recusa o acesso à aplicação.

8.  A aplicação Outlook comunica com o Serviço Cloud do Outlook para iniciar a comunicação com o Exchange Online.

9.  O Serviço Cloud do Outlook comunica com o Azure AD para recuperar o token de acesso de serviço do Exchange Online para o utilizador.

10.  A aplicação Outlook comunica com o Exchange Online para recuperar o e-mail empresarial do utilizador.

11.  O e-mail empresarial é entregue na caixa de correio do utilizador.

## <a name="next-steps"></a>Próximos passos
[Criar uma política de acesso condicional com base na aplicação](app-based-conditional-access-intune-create.md)

[Bloquear aplicações que não tenham autenticação moderna](app-modern-authentication-block.md)
