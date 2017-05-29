---
title: "Pré-requisitos para políticas de MAM | Documentos da Microsoft"
description: "Este tópico descreve os pré-requisitos para a configuração de utilizadores antes de criar políticas de gestão de aplicações móveis."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3c209a350a7de7ba7ddb71468c5cd4230dcf5423
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="get-ready-to-configure-app-protection-policies-in-the-azure-portal"></a>Preparar-se para configurar políticas de proteção de aplicações no portal do Azure

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este tópico descreve os pré-requisitos e os passos que tem de concluir **antes** de poder criar políticas de proteção de aplicações no portal do Azure.

Para compreender como as políticas de proteção de aplicações do Intune podem proteger os dados da sua empresa, veja [Proteger aplicações e dados com políticas de proteção de aplicações](protect-apps-and-data-with-microsoft-intune.md).

## <a name="what-is-the-azure-portal"></a>O que é o portal do Azure?

O portal do Azure é a nova consola de administração para criar políticas de proteção de aplicações. Este suporta os seguintes cenários MAM:
- Dispositivos que estão inscritos no Intune
- Dispositivos que são geridos por outra solução de MDM (Gestão de Dispositivos Móveis)
- Dispositivos que não são geridos por nenhuma solução de MDM (BYOD).

Atualmente, a **consola de administração do Intune** e o **portal do Azure** permitem-lhe configurar políticas de proteção de aplicações.  Tenha em consideração o seguinte:

* As políticas que criar no **portal do Azure** são suportadas por **todos os cenários de MAM** que foram listados anteriormente. A **consola de administração do Intune** só suporta a criação de políticas para **dispositivos inscritos e geridos pelo Intune**.

* Poderá não ver todas as definições da política de aplicações na consola de administração do Intune porque as **novas definições** só podem ser adicionadas ao **portal do Azure**.

* Se criar políticas de proteção de aplicações em **ambos**, na consola de administração do Intune e no portal do Azure, a política no **portal do Azure é aplicada às aplicações e é implementada para os utilizadores**.
    * As políticas de proteção de aplicações que são criadas na consola de administração do Intune não podem ser importadas para o portal do Azure.  Têm de ser recriadas no portal do Azure.


* Outras **funcionalidades de gestão de aplicações**, como implementar aplicações e políticas de configuração de aplicações, só estão atualmente disponíveis na **consola de administração do Intune**.


Se não estiver familiarizado com o portal do Azure, leia [Portal do Azure para políticas de proteção de aplicações do Microsoft Intune](azure-portal-for-microsoft-intune-mam-policies.md) para obter noções básicas sobre como utilizar o portal do Azure.

Para obter instruções sobre como criar uma política de aplicações na consola de administração do Intune, veja [Configurar e implementar políticas de proteção de aplicações na consola do Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).


##  <a name="supported-platforms"></a>Plataformas suportadas
- iOS 8.1 ou posterior
- Android 4 ou posterior
- Windows 10

>[!NOTE]
>A partir da versão 1703, as políticas de proteção de aplicações podem ser definidas para dispositivos Windows 10 no MAM sem o cenário de inscrição. Para mais detalhes, consulte [Protect your enterprise data using Windows Information Protection (WIP) (Proteger os seus dados empresariais com o Windows Information Protection [WIP] – em inglês)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).

##  <a name="supported-apps"></a>Aplicações suportadas
* **Aplicações da Microsoft:** estas aplicações têm o SDK da Aplicação Intune incorporado e não requerem processamentos adicionais antes de aplicar as políticas de proteção de aplicações.
Para ver a lista completa de aplicações da Microsoft suportadas, aceda à [galeria de aplicações móveis do Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps), na página de parceiros de aplicações do Microsoft Intune. Clique numa aplicação para ver os cenários e as plataformas suportados e se suporta várias identidades.

* **Aplicações de linha de negócio da sua organização:** tem de preparar estas aplicações para incluir o SDK da Aplicação Intune para poder aplicar políticas de proteção de aplicações.

  * Para saber que dispositivos são geridos pelo Intune, consulte [Decidir como preparar as aplicações para MAM](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).

  * Para dispositivos que não são geridos (por exemplo, dispositivos pertencentes aos funcionários) ou que são geridos por outra solução de gestão de dispositivos móveis, veja [Proteger aplicações e dados de linha de negócio em dispositivos não inscritos no Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).

## <a name="prerequisites"></a>Pré-requisitos

-   **Uma subscrição do Microsoft Intune**. Os utilizadores precisam de licenças do Intune para obter aplicações com as políticas de proteção de aplicações.
Já terá uma subscrição do Intune se estiver a utilizar atualmente o Intune para gerir os dispositivos. Também terá uma subscrição do Intune se tiver comprado uma licença do Enterprise Mobility Suite (EMS). Se estiver a experimentar o Intune para verificar as capacidades do MAM, pode obter uma conta de avaliação na [página do Microsoft Intune](https://www.microsoft.com/server-cloud/products/microsoft-intune/).

    Para verificar se tem uma subscrição do Intune, no portal do Office, aceda à página de **Faturação**.  Se tiver uma subscrição, deverá ver o Intune como **Ativo** nas subscrições.

-   **Uma subscrição do Office 365**, que é precisa para o seguinte:

  - Para aplicar políticas de proteção de aplicações a aplicações com suporte de várias identidades.

  - Criar contas profissionais do SharePoint Online e do Exchange Online. O Exchange no local e o SharePoint no local não são suportados.

-   **Configuração do Skype para Empresas Online para autenticação moderna**. Para mais informações, veja [Enable modern authentication (Ativar autenticação moderna)](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).


- Azure Active Directory (Azure AD) para criar utilizadores. O Azure AD autentica os utilizadores quando abrem a aplicação e introduzem as respetivas credenciais de trabalho.

    > [!NOTE]
    > Os grupos de utilizadores têm de ser configurados no Azure AD. Os grupos de utilizadores do Intune não podem ser utilizados para implementar políticas de proteção de aplicações no portal do Azure.

### <a name="create-users-and-assign-microsoft-intune-licenses"></a>Criar utilizadores e atribuir licenças do Microsoft Intune

1.  Inicie sessão no [portal do Office](https://portal.office.com) com as suas credenciais de administrador.

2.  Adicione utilizadores, tal como descrito na secção **Passos para concluir uma avaliação de 30 dias do Intune** do [guia de avaliação do Intune](/intune-classic/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune) e, em seguida, atribua licenças do Intune. Para permitir a um utilizador aceder ao portal do Office, ao portal do Azure AD e ao portal do Azure, atribua-lhe a função **Administrador global**.

5.  As políticas de proteção de aplicações são implementadas em grupos de utilizadores no Azure Active Directory. Para criar grupos de utilizadores para as suas políticas de proteção de aplicações, crie um grupo de utilizadores conforme descrito na secção **Criar um grupo de utilizadores** de [Criar grupos para organizar utilizadores e dispositivos de subscrições de avaliação](/intune-classic/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-3).

### <a name="assign-roles-to-non-global-admin-users"></a>Atribuir funções para os utilizadores administradores não globais

Os Administradores globais têm acesso ao [portal do Azure](https://portal.azure.com).  Se quiser que os utilizadores que não são administradores globais possam configurar políticas e realizar outras tarefas de gestão de aplicações móveis, veja o artigo [Utilizar atribuições de funções para gerir o acesso aos recursos de subscrição do Azure](https://azure.microsoft.com/documentation/articles/role-based-access-control-configure/).

## <a name="next-steps"></a>Passos seguintes
[Criar e implementar políticas de proteção de aplicações com o Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)

