---
title: "Processo de integração no Intune | Documentos da Microsoft"
description: "Este artigo fornece todos os detalhes que precisa de ter em consideração quando integrar a solução do Intune apenas na cloud no seu ambiente."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 307a4aec1d9b86a92bde9114fdfd45846a82a2f3
ms.lasthandoff: 04/25/2017


---

# <a name="intune-implementation"></a>Implementação do Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Durante a fase de integração, implementará o Intune no seu ambiente de produção. O processo de implementação consistirá na configuração do Intune e das dependências externas (caso seja necessário) com base nos seus [requisitos de casos de utilização](section-3-determine-use-case-requirements.md) que foram revistos nas secções anteriores deste guia.

A secção seguinte fornece uma descrição geral do processo de implementação do Intune, que inclui requisitos e tarefas de alto nível.

>[!TIP]
> Para mais informações sobre o processo de implementação do Intune, consulte [Recursos adicionais](additional-resources.md).

## <a name="intune-requirements"></a>Requisitos do Intune

Os principais requisitos do Intune autónomo encontram-se indicados abaixo:

-   Subscrição do Intune/EMS

-   Subscrição do Office 365 (para aplicações do Office e aplicações geridas pela política de MAM)

-   Certificado do Apple APNs (para ativar a gestão da plataforma de dispositivos iOS)

-   Azure AD Connect (para a sincronização de diretórios)

-   Conector no Local do Intune para o Exchange (para a AC para o Exchange no Local caso seja necessário)

-   Intune Certificate Connector (para a implementação do certificado de SCEP, caso seja necessário)

>[!TIP]
> Encontrará mais informações sobre os requisitos da versão autónoma do Intune [aqui](https://docs.microsoft.com/intune/get-started/what-to-know-before-you-start-microsoft-intune).

## <a name="intune-implementation-process"></a>Processo de implementação do Intune

### <a name="overview-of-implementation-tasks"></a>Descrição geral das tarefas de implementação

Eis uma descrição geral de cada tarefa inerente ao processo de implementação do Intune.

#### <a name="task-1-add-intune-subscription"></a>Tarefa 1: adicionar uma subscrição do Intune

Conforme indicado na secção de requisitos acima, é necessária uma subscrição do Intune ou do EMS. Se a sua organização não tiver uma subscrição do Intune ou do EMS, contacte a Microsoft ou a sua equipa da conta Microsoft para a informar de que pretende comprar o Enterprise Mobility + Security (EMS) ou o Intune.

-   Saiba mais sobre [como pode comprar o Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing).

#### <a name="task-2-add-office-365-subscription"></a>Tarefa 2: adicionar a subscrição do Office 365

Este passo é opcional. Conforme indicado na secção de requisitos acima, se planeia utilizar o Exchange Online e gerir aplicações móveis do Office com a política de MAM, precisa de ter uma subscrição do Office 365. Se a sua organização não tiver uma subscrição do Office 365, contacte a Microsoft ou a sua equipa da conta Microsoft para a informar de que pretende comprar o Office 365.

-   Saiba mais sobre [como pode comprar o Office 365](https://products.office.com/business/compare-office-365-for-business-plans).

#### <a name="task-3-add-users-groups-in-azure-ad"></a>Tarefa 3: adicionar grupos de utilizadores no Azure AD

Poderá ter de adicionar grupos de segurança ou de utilizadores no AD ou no AAD com base nos seus cenários e requisitos de casos de utilização de implementação do Intune. Deve rever os seus grupos de segurança e de utilizadores atuais no Active Directory ou no Azure Active Directory e determinar se vão totalmente ao encontro das suas necessidades. Normalmente, os novos grupos de segurança e de utilizadores são adicionados no Active Directory e sincronizados para o Azure Active Directory através do Azure AD Directory Connect.

-   Saiba mais sobre [como pode adicionar utilizadores/grupos no Intune](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3).

#### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>Tarefa 4: atribuir licenças de utilizador do Intune e do Office 365

Todos os utilizadores que serão visados para a implementação do Office 365 e do EMS/Intune têm de ter uma licença que lhes foi atribuída. Pode realizar-se a atribuição de licenças do Office 365 e do EMS/Intune no portal do centro de administração do Office 365.

-   Saiba mais sobre [como atribuir licenças do Intune](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4).

#### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>Tarefa 5: definir o Intune como a Autoridade de Gestão de Dispositivos Móveis

Para poder configurar, gerir e inscrever dispositivos através do Intune, tem de definir o Intune como a Autoridade de Gestão de Dispositivos. A definição da Autoridade de Gestão de Dispositivos é concluída na área de trabalho Administração do Portal de Administração do Intune.

-   Saiba mais sobre [como definir a Autoridade de Gestão de Dispositivos](https://docs.microsoft.com/intune/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority).

#### <a name="task-6-enable-device-platforms"></a>Tarefa 6: ativar as plataformas de dispositivos

Por predefinição, na consola de administração do Intune, a maioria das plataformas de dispositivos está ativada, à exceção dos dispositivos da Apple (iOS e Mac). Antes de os dispositivos iOS poderem ser inscritos e geridos no Intune, a plataforma do dispositivo tem de ser ativada. A ativação das plataformas de dispositivos iOS é um processo constituído por três passos: criação e transferência do certificado do APNs e carregamento do certificado do APNs no Intune.

-   Saiba mais sobre [como funciona a configuração de gestão de dispositivos Mac e iOS.](https://docs.microsoft.com/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)

#### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>Tarefa 7: adicionar e implementar políticas de termos e condições

O Microsoft Intune suporta a adição e a implementação de políticas de termos e condições. A adição e implementação das políticas de termos e condições são concluídas na área de trabalho Política do Portal de Administração do Intune. Adicione políticas de termos e condições conforme adequado e implemente-as nos grupos visados com base nos seus requisitos e casos de utilização de implementação do Intune.

-   Saiba mais sobre [como adicionar e implementar políticas de termos e condições](https://docs.microsoft.com/intune/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune).

#### <a name="task-8-add-and-deploy-configuration-policies"></a>Tarefa 8: adicionar e implementar políticas de configuração

O Microsoft Intune suporta a adição e a implementação de dois tipos de políticas de Configuração: as políticas de configuração gerais e as personalizadas. A adição e implementação das políticas de Configuração são concluídas na área de trabalho Política do Portal de Administração do Intune. Adicione políticas de Configuração conforme adequado e implemente-as em grupos visados com base nos seus requisitos e casos de utilização de implementação do Intune.

-   Saiba mais sobre [como adicionar e implementar políticas de configuração](https://docs.microsoft.com/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies).

#### <a name="task-9-add-and-deploy-resource-profiles"></a>Tarefa 9: adicionar e implementar perfis de recursos

O Microsoft Intune suporta os perfis de E-mail, Wi-Fi e VPN. A adição e implementação de perfis são concluídas na área de trabalho Política do Portal de Administração do Intune. Adicione perfis de E-mail, Wi-Fi e VPN conforme adequado e implemente-os em grupos visados com base nos seus requisitos e casos de utilização de implementação do Intune.

-   Saiba mais sobre [a ativação de acesso aos recursos da empresa com o Intune](https://docs.microsoft.com/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune).

#### <a name="task-10-add-and-deploy-apps"></a>Tarefa 10: adicionar e implementar aplicações

O Microsoft Intune suporta a implementação de aplicações Web, LOB e de lojas de aplicações públicas. Também suporta a gestão de aplicações que integraram o SDK do Intune através da sua associação a políticas de MAM. A adição e implementação de aplicações são concluídas na área de trabalho Aplicações do Portal de Administração do Intune. A adição e implementação de políticas de MAM são concluídas na área de trabalho Política do Portal de Administração do Intune. Adicione aplicações conforme adequado e implemente-as em grupos visados com base nos seus requisitos e casos de utilização de implementação do Intune.

-   Saiba mais sobre [a adição e implementação de aplicações](https://docs.microsoft.com/intune/deploy-use/deploy-apps).

#### <a name="task-11-add-and-deploy-compliance-policies"></a>Tarefa 11: adicionar e implementar políticas de conformidade

O Microsoft Intune suporta políticas de Conformidade. A adição e implementação das políticas de Conformidade são concluídas na área de trabalho Política do Portal de Administração do Intune. Adicione políticas de Conformidade conforme adequado e implemente-as nos grupos visados com base nos seus requisitos e casos de utilização de implementação do Intune.

-   Saiba mais sobre [políticas de conformidade](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune).

#### <a name="task-12-enable-conditional-access-policies"></a>Tarefa 12: ativar políticas de Acesso Condicional

O Microsoft Intune suporta o Acesso Condicional para Exchange Online e Exchange no Local, SharePoint Online, Skype para Empresas Online e Dynamics CRM Online. A ativação de políticas de Acesso Condicional é efetuada na área de trabalho Política do Portal de Administração do Intune. Ative e configure o Acesso Condicional conforme adequado com base nos seus [requisitos e casos de utilização de implementação do Intune](section-3-determine-use-case-requirements.md).

-   Saiba mais sobre o [acesso condicional](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

#### <a name="task-13-enroll-devices"></a>Tarefa 13: inscrever dispositivos

O Intune suporta plataformas de dispositivos iOS, Mac OS, Android, Windows Desktop e Windows Mobile. Ative plataformas de dispositivos móveis conforme adequado com base nos seus requisitos e casos de utilização de implementação do Intune.

-   Saiba mais sobre [como inscrever dispositivos](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune).

>[!TIP]
> Consulte este [módulo de sessão do Microsoft Virtual Academy Intune](https://mva.microsoft.com/training-courses/deploying-microsoft-enterprise-mobility-suite-16408?l=PPWNoZxvD_1404778676) para obter mais informações sobre o processo de implementação do Intune.

## <a name="next-section"></a>Secção Seguinte

A secção seguinte fornece orientações para [testar e validar a sua implementação do Intune](section-9-test-and-validation.md).

