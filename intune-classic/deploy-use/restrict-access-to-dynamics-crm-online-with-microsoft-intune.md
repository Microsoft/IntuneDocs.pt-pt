---
title: Proteger o Dynamics CRM Online
description: Proteger e controlar o acesso ao Dynamics CRM online com acesso condicional.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f1c4522b-5a34-4f5a-89d2-7809c4352af7
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e2f720c8a6613884397111c2a421fa1cfdc0eb53
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="protect-access-to-dynamics-crm-online-with-intune"></a>Proteger o acesso ao Dynamics CRM Online com o Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Pode controlar o acesso ao Microsoft Dynamics CRM Online a partir de dispositivos iOS e Android com acesso condicional do Microsoft Intune.  O acesso condicional do Intune tem dois componentes:
* Uma [política de conformidade de dispositivos](introduction-to-device-compliance-policies-in-microsoft-intune.md) que o dispositivo tem de cumprir para ser considerado compatível.
* Uma [política de acesso condicional](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) onde especifica as condições que o dispositivo tem de cumprir para poder aceder ao serviço.

Para saber mais sobre como funciona o acesso condicional, leia o artigo [Proteger o acesso ao e-mail, O365 e a outros serviços](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

> [!IMPORTANT]
> Para implementar o acesso condicional, tem de ter subscrições do Intune e do Azure Active Directory Premium e os utilizadores têm de estar licenciados para ambos os produtos. A **subscrição do Enterprise Mobility + Security (EMS)** inclui as subscrições do Intune e do Azure Active Directory Premium. Para obter mais detalhes, consulte a [página de preços do Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing). Se não tiver uma subscrição do EMS, pode obter uma subscrição do Azure Active Directory Premium. Consulte a [página de preços do Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

Quando um utilizador visado tentar utilizar a aplicação Dynamics CRM no respetivo dispositivo, ocorre a seguinte avaliação:

![Diagrama que mostra os pontos de decisão que são utilizados para determinar se um dispositivo tem permissão de acesso a um serviço ou se está bloqueado](../media/mdm-ca-dynamics-crm-flow-diagram.png)

O dispositivo que necessita de acesso ao Dynamics CRM tem de:
* Ser um dispositivo **Android** ou **iOS**.
* Estar **inscrito** no Intune.
* Ser **compatível** com todas políticas de conformidade do Intune implementadas.

O estado do dispositivo é armazenado no Azure Active Directory, o qual concede ou bloqueia o acesso, com base nas condições que especificar.

Se não for cumprida uma condição, é apresentada ao utilizador uma das duas mensagens seguintes quando iniciar sessão:
* Se o dispositivo não estiver inscrito no Intune ou registado no Azure Active Directory, será apresentada uma mensagem com instruções sobre como instalar a aplicação Portal da Empresa e inscrevê-la.
* Se o dispositivo não for compatível, será apresentada uma mensagem que direciona o utilizador para o site do Portal da Empresa do Microsoft Intune ou para a aplicação Portal da Empresa, onde pode obter informações sobre o problema e como resolvê-lo.

## <a name="configure-conditional-access-for-dynamics-crm-online"></a>Configurar o acesso condicional para o Dynamics CRM Online  
### <a name="step-1-configure-active-directory-security-groups"></a>Passo 1: configurar grupos de segurança do Active Directory

Antes de começar, configure grupos de segurança do Azure Active Directory para a política de acesso condicional. Pode configurar estes grupos no **centro de administração do Office 365**. Pode utilizar estes grupos para adicionar ou excluir os utilizadores da política. Quando um utilizador é direcionado por uma política, cada dispositivo que utiliza tem de estar em conformidade para poder aceder aos recursos.

Pode especificar dois tipos de grupo a utilizar para a política do Dynamics CRM:
* **Grupos visados**. Contém os grupos de utilizadores aos quais se aplica a política.
* **Grupos excluídos**. Contém os grupos de utilizadores excluídos da política.

Se um utilizador estiver em ambos os grupos, significa que está excluído da política.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Passo 2: configurar e implementar uma política de conformidade
[Crie](create-a-device-compliance-policy-in-microsoft-intune.md) uma política de conformidade e [implemente](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) a mesma em todos os dispositivos que serão afetados pela política. Estes são todos os dispositivos utilizados pelos utilizadores nos Grupos visados.

> [!NOTE]
> Enquanto as políticas de conformidade são implementadas nos grupos do Intune, as políticas de acesso condicional são direcionadas para os grupos de segurança do Azure Active Directory.

> [!IMPORTANT]
> Se não tiver implementado uma política de conformidade, os dispositivos serão tratados como em conformidade.

Quando estiver pronto, avance para o Passo 3.
### <a name="step-3-configure-the-dynamics-crm-policy"></a>Passo 3: configurar a política de Dynamics CRM
Em seguida, configure a política para exigir que apenas os dispositivos geridos e compatíveis podem aceder ao Dynamics CRM. Esta política será armazenada no Azure Active Directory.

1. Na consola de administração do Intune, selecione **Política > Acesso Condicional > Política Dynamics CRM Online**.

   ![Captura de ecrã da página de política de acesso condicional do Dynamics CRM Online](../media/mdm-ca-dynamics-crm-policy-configuration.png)

2. Escolha a política **Ativar acesso condicional**.
3. Em **Acesso da aplicação**, pode optar por aplicar a política de acesso condicional a:
   * **iOS**
   * **Android**
4. Em **Grupos Visados**, escolha **Modificar** para selecionar os grupos de segurança do Azure Active Directory aos quais será aplicada a política. Pode optar por direcionar esta opção a todos os utilizadores ou apenas a um grupo de utilizadores específico.
5. Como opção, em **Grupos Excluídos**, selecione **Modificar** para selecionar os grupos de segurança do Azure Active Directory que estão excluídos desta política.
6. Quando tiver terminado, escolha **Guardar**.

Configurou o acesso condicional para o Dynamics CRM. Não tem de implementar a política de acesso condicional, pois esta entra em vigor imediatamente.
##  <a name="monitor-the-compliance-and-conditional-access-policies"></a>Monitorizar a conformidade e as políticas de acesso condicional

Na área de trabalho **Grupos**, pode ver o estado do acesso condicional dos seus dispositivos.

Escolha qualquer grupo de dispositivos móveis e, em seguida, no separador **Dispositivos**, escolha um dos seguintes **Filtros**:
* **Dispositivos não registados com o AAD**. Estes dispositivos são bloqueados no Dynamics CRM.
* **Dispositivos que não são compatíveis**. Estes dispositivos são bloqueados no Dynamics CRM.
* **Dispositivos registados com o AAD e que são compatíveis**. Estes dispositivos podem aceder ao Dynamics CRM.

##  <a name="next-steps"></a>Próximos passos
* [Proteger o acesso ao Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)

* [Proteger o acesso ao Exchange no local](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
* [Proteger o acesso ao SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

* [Proteger o acesso ao Skype para Empresas Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
