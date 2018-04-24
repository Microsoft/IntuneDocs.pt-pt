---
title: Acesso condicional ao 0365 com base na aplicação
description: Compreenda os conceitos de como o acesso condicional para MAM pode ajudar a controlar as aplicações que têm acesso aos serviços do O365.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/05/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1f9446da0f553dca29bbfd96b99711c895cd8533
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="allow-only-mobile-apps-that-support-intune-app-protection-policies-to-access-office-365-services"></a>Permitir que apenas as aplicações móveis que suportam políticas de proteção de aplicações do Intune acedam aos serviços do Office 365

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

As [políticas de proteção de aplicações do Intune](protect-apps-and-data-with-microsoft-intune.md) ajudam-no a proteger os dados da sua empresa em dispositivos inscritos para gestão no Intune. Também pode utilizar políticas de proteção de aplicações em **dispositivos de funcionários que não estejam inscritos para gestão no Intune**.  Neste caso, apesar de não gerir o dispositivo, ainda precisa de garantir que os recursos e os dados da sua empresa estão protegidos. Através do acesso condicional com base na aplicação com MAM, pode criar uma política que permita que apenas as aplicações móveis que suportam políticas de proteção de aplicações do Intune possam aceder a serviços do Office 365, como o Exchange Online.

Por exemplo, ao permitir que apenas a **aplicação Microsoft Outlook** aceda ao Exchange Online, pode **bloquear as aplicações de correio incorporadas no iOS e Android**, que não têm a proteção de dados das políticas de MAM do Intune para obter e-mails do **Exchange Online**. Em alternativa, pode bloquear as aplicações móveis que não têm o suporte de MAM do Intune para aceder ao **SharePoint Online**.

O diagrama abaixo ilustra o fluxo utilizado pelas políticas de acesso condicional com base na aplicação para determinar quando deve permitir ou bloquear o acesso: ![Diagrama que mostra os vários critérios incluídos para determinar se deve permitir ou bloquear o acesso ](../media/mam-ca-decision-flow_simple.png).

Descrição das abreviações utilizadas nos diagramas:
* **CP**: aplicação Portal da Empresa
* **AA**: aplicação Azure Authenticator
* **AAD**: Azure Active Directory
* **EAS**: Exchange Active Sync

## <a name="prerequisites"></a>Pré-requisitos
**Antes** de criar uma política de acesso condicional com base na aplicação, tem de ter uma **subscrição premium do Enterprise Mobility + Security ou do Azure Active Directory** e os utilizadores têm de ter licença para o EMS ou para o Azure AD. Para saber mais detalhes, consulte a [página de preços do Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) ou a [página de preços do Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).


## <a name="supported-apps"></a>Aplicações suportadas
**Exchange Online**:
* **Microsoft Outlook** para Android e iOS.

**SharePoint Online**
* Microsoft Word para iOS e Android
* Microsoft Excel para iOS e Android
* Microsoft PowerPoint para iOS e Android
* Microsoft OneDrive para Empresas para iOS e Android
* Microsoft OneNote para iOS

>[!IMPORTANT]
>Para dispositivos Android, o registo do dispositivo inicial tem de ser feito ao iniciar sessão na aplicação OneDrive ou na aplicação Outlook. A aplicação OneNote para Android ainda não suporta MAM sem inscrição.

Para saber mais sobre a experiência de utilizador com uma aplicação com políticas de acesso condicional com base na aplicação, veja [O que esperar ao utilizar uma aplicação com acesso condicional para MAM](use-apps-with-mam-ca.md).


## <a name="next-steps"></a>Próximos passos
[Criar uma Política do Exchange Online para aplicações de MAM](mam-ca-for-exchange-online.md)

[Criar uma Política do SharePoint Online para aplicações MAM](mam-ca-for-sharepoint-online.md)

[Bloquear aplicações que não tenham autenticação moderna](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Consulte também

[Proteger os dados da aplicação com políticas de proteção de aplicações](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
