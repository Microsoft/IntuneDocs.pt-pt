---
title: "Pré-requisitos para políticas de MAM | Microsoft Intune"
description: "Este tópico descreve os pré-requisitos para a configuração de utilizadores antes de criar políticas de gestão de aplicações móveis."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: ac820146d81fb121a60f7029f6a52a0056d6ab0a


---

# <a name="get-ready-to-configure-mobile-app-management-policies-on-the-azure-portal"></a>Prepare-se para configurar políticas de gestão de aplicações móveis no portal do Azure
Este tópico descreve os pré-requisitos e os passos que tem de concluir **antes** de poder criar políticas de gestão de aplicações móveis (MAM) no portal do Azure.

Para compreender como as políticas de MAM do Intune podem proteger os dados da sua empresa, consulte [Proteger aplicações e dados através de políticas de gestão de aplicações móveis](protect-apps-and-data-with-microsoft-intune.md).

## <a name="what-is-the-azure-portal"></a>O que é o portal do Azure?

O portal do Azure é a nova consola de administração para a criação de políticas de MAM. Este suporta os seguintes cenários MAM:
- Dispositivos que estão inscritos no Intune
- Dispositivos que são geridos por outra solução de MDM (Gestão de Dispositivos Móveis)
- Dispositivos que não são geridos por nenhuma solução de MDM (BYOD).

Atualmente, a **consola do administrador do Intune** e o **portal do Azure** permitem configurar políticas de MAM.  Tenha em consideração o seguinte:

* As políticas que criar no **portal do Azure** são suportadas por **todos os cenários de MAM** que foram listados anteriormente. A **consola do administrador do Intune** só suporta a criação de políticas para **dispositivos inscritos e geridos pelo Intune**.

* Poderá não ver todas as definições de políticas de MAM na consola do administrador do Intune porque as **novas definições** só podem ser adicionadas ao **portal do Azure**.

* Se criar políticas de MAM, **quer** na consola de administração do Intune como no portal do Azure, a política no **portal do Azure será aplicada às aplicações e implementada para os utilizadores**.
    * As políticas de MAM criadas na consola de administração do Intune não podem ser importadas para o portal do Azure.  Têm de ser recriadas no portal do Azure.


* Outras **funcionalidades de gestão de aplicações**, como implementar aplicações e políticas de configuração de aplicações, só estão atualmente disponíveis na **consola do administrador do Intune**.


Se for a primeira vez que utiliza o portal do Azure, leia [Portal do Azure para políticas de MAM do Microsoft Intune](azure-portal-for-microsoft-intune-mam-policies.md) para ter as noções básicas sobre como utilizar o portal do Azure.

Para obter instruções sobre como criar uma política de MAM na consola de administração do Intune, veja [Configurar e implementar as políticas de gestão de aplicações móveis na consola do Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).


##  <a name="supported-platforms"></a>Plataformas suportadas
- iOS 8.1 ou posterior
- Android 4 ou posterior

>[!NOTE]
>Os dispositivos Windows não suportam estas políticas de gestão de aplicações móveis. No entanto, quando inscrever dispositivos Windows 10 com o Intune, pode utilizar o Windows Information Protection, que oferece uma funcionalidade semelhante. Para mais detalhes, consulte [Protect your enterprise data using Windows Information Protection (WIP) (Proteger os seus dados empresariais com o Windows Information Protection [WIP] – em inglês)](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/protect-enterprise-data-using-wip).

##  <a name="supported-apps"></a>Aplicações suportadas
* **Aplicações da Microsoft:** estas aplicações têm o SDK da Aplicação do Intune incorporado e não requerem processamento adicional antes de aplicar as políticas de MAM.
Para ver a lista completa de aplicações da Microsoft suportadas, aceda à [galeria de aplicações móveis do Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps), na página de parceiros de aplicações do Microsoft Intune. Clique numa aplicação para ver os cenários e as plataformas suportados e se suporta várias identidades.

* **As aplicações de linha de negócio da sua organização:** tem de preparar estas aplicações para incluir o SDK da Aplicação do Intune antes de poder aplicar políticas de MAM.

  * Para saber que dispositivos são geridos pelo Intune, consulte [Decidir como preparar as aplicações para MAM](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).

  * Para dispositivos que não são geridos (por exemplo, dispositivos pertencentes aos funcionários) ou que são geridos por outra solução de gestão de dispositivos móveis, veja [Proteger aplicações e dados de linha de negócio em dispositivos não inscritos no Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).

## <a name="prerequisites"></a>Pré-requisitos

-   **Uma subscrição do Microsoft Intune**. Os utilizadores precisam de licenças do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para obter aplicações com a política de MAM.
Já tem uma subscrição do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] se estiver a utilizar atualmente o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para gerir os dispositivos. Também tem uma subscrição do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] se tiver comprado uma licença do Enterprise Mobility Suite (EMS). Se estiver a tentar [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] verificar as capacidades do MAM, pode obter uma conta de avaliação na [página do Microsoft Intune](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/).

    Para verificar se tem uma subscrição do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], no portal do Office, aceda à página de **Faturação**.  Se tiver uma subscrição, deverá ver [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] como **Ativo** nas subscrições.

-   **Uma subscrição do Office 365**, que é precisa para o seguinte:

  - Para aplicar políticas de MAM a aplicações com suporte de várias identidades.

  - Criar contas profissionais do SharePoint Online e do Exchange Online. O Exchange no local e o SharePoint no local não são suportados.

-   **Configuração do Skype para Empresas Online para autenticação moderna**. Para mais informações, consulte [Enable modern authentication (Ativar autenticação moderna)](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).


- Azure Active Directory (Azure AD) para criar utilizadores. O Azure AD autentica os utilizadores quando abrem a aplicação e introduzem as respetivas credenciais de trabalho.

    > [!NOTE]
    > Os grupos de utilizadores têm de ser configurados no Azure AD. Os grupos de utilizadores do Intune não podem ser utilizados para implementar políticas de MAM no portal do Azure.

### <a name="create-users-and-assign-microsoft-intune-licenses"></a>Criar utilizadores e atribuir licenças do Microsoft Intune

1.  Inicie sessão no [portal do Office](http://portal.office.com) com as suas credenciais de administrador.

2.  Adicione utilizadores, tal como descrito na secção **Passos para concluir uma avaliação de 30 dias do Intune** do [guia de avaliação do Intune](https://docs.microsoft.com/en-us/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune) e, em seguida, atribua licenças do Intune. Para permitir a um utilizador aceder ao portal do Office, ao portal do Azure AD e ao portal do Azure, atribua-lhe a função **Administrador global**.

5.  As políticas de MAM são implementadas em grupos de utilizadores no Azure Active Directory. Para criar grupos de utilizadores para as suas políticas de MAM, crie um grupo de utilizadores conforme descrito na secção **Criar um grupo de utilizadores** de [Criar grupos para organizar utilizadores e dispositivos de subscrições de avaliação](https://docs.microsoft.com/en-us/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-3).

### <a name="assign-roles-to-non-global-admin-users"></a>Atribuir funções para os utilizadores administradores não globais

Os Administradores globais têm acesso ao [portal do Azure](https://portal.azure.com).  Se quiser que os utilizadores que não são administradores globais possam configurar políticas e realizar outras tarefas de gestão de aplicações móveis, pode atribuir-lhes a função de contribuidor. Para obter instruções detalhadas, consulte [Utilizar atribuições de funções para gerir o acesso aos recursos de subscrição do Azure](https://azure.microsoft.com/en-us/documentation/articles/role-based-access-control-configure/).



A tabela seguinte lista as funções e as permissões que pode atribuir aos utilizadores administradores.



|||
|--|----|
|**Função**|**Permissões**|
|Administrador global (portal do Office 365)|Acesso ao portal do Office 365 e ao portal do Azure AD.<br /><br />Acesso ao portal do Azure (pode fazer tarefas de gestão de funções e de aplicações móveis).|
|Proprietário (portal do Azure)|Acesso ao portal do Azure (pode fazer tarefas de gestão de funções e de aplicações móveis).|
|Contribuidor (portal do Azure)|Acesso ao portal do Azure (só pode fazer tarefas de gestão de aplicações móveis).|




## <a name="next-steps"></a>Próximos passos
[Criar e implementar políticas de gestão de aplicações móveis com o Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


