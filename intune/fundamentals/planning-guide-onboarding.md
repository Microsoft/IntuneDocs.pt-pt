---
title: Processo de integração do Intune
titleSuffix: Microsoft Intune
description: Este artigo fornece todos os detalhes que precisa de ter em consideração quando integrar a solução do Microsoft Intune apenas na cloud no seu ambiente.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1cdfc7d42d3bffe1abe21deddfe146af953b150a
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514953"
---
# <a name="implement-your-microsoft-intune-plan"></a>Implementar o plano do Microsoft Intune

Durante a fase de integração, implementará o Intune no seu ambiente de produção. O processo de implementação consiste na configuração do Intune e das dependências externas (se for necessário) com base nos seus [requisitos de casos de utilização](planning-guide-requirements.md).

A secção seguinte fornece uma descrição geral do processo de implementação do Intune, que inclui requisitos e tarefas de alto nível.

## <a name="intune-requirements"></a>Requisitos do Intune

Os principais requisitos do Intune autónomo são:

- Subscrição do Intune/Enterprise Mobility + Security (EMS)

- Subscrição do Office 365 (para aplicações do Office e aplicações geridas por políticas de proteção de aplicações)

- Apple APNs Certificate (para permitir a gestão da plataforma do dispositivo iOS/iPadOS)

- Azure AD Connect (para a sincronização de diretórios)

- Conector intune on-premises para troca (para acesso condicional para troca no local, se necessário)

- Intune Certificate Connector (para a implementação do certificado de SCEP, caso seja necessário)

>[!TIP]
> Veja a lista de [dispositivos suportados](supported-devices-browsers.md) para obter uma lista completa de dispositivos que pode gerir com o Intune.

## <a name="intune-implementation-process"></a>Processo de implementação do Intune

Identificámos 13 tarefas distintas para o processo de implementação do Intune. Consoante os seus requisitos empresariais, infraestruturas existentes e estratégia de gestão de dispositivos, algumas destas tarefas já poderão estar concluídas. Outras tarefas podem não se aplicar ao seu plano.

### <a name="task-1-get-an-intune-subscription"></a>Tarefa 1: obter uma subscrição do Intune

Conforme indicado na secção de requisitos do Intune acima, precisa de uma subscrição do Intune ou do EMS. Se a sua organização não tiver uma, contacte a Microsoft ou a sua equipa da conta Microsoft para a informar de que pretende comprar o Enterprise Mobility + Security (EMS) ou o Intune.

- Saiba mais sobre [como pode comprar o Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing).

### <a name="task-2-add-office-365-subscription"></a>Tarefa 2: adicionar a subscrição do Office 365

Este passo é opcional. Precisa de uma subscrição do Office 365 se planear utilizar o Exchange Online e gerir as aplicações do Office para dispositivos móveis com as políticas de proteção de aplicações. Se a sua organização não tiver uma subscrição do Office 365, contacte a Microsoft ou a sua equipa da conta Microsoft para a informar de que pretende comprar o Office 365.

- Saiba mais sobre [como pode comprar o Office 365](https://products.office.com/business/compare-office-365-for-business-plans).

### <a name="task-3-add-users-groups-in-azure-ad"></a>Tarefa 3: adicionar grupos de utilizadores no Azure AD

Poderá ser necessário adicionar utilizadores ou grupos de segurança no Active Directory ou no Azure Active Directory com base nos seus cenários de casos de utilização e requisitos da implementação do Intune. Reveja os seus grupos de segurança e de utilizadores atuais no Active Directory ou no Azure Active Directory e determine se correspondem totalmente às suas necessidades. Quando adiciona novos grupos de segurança e de utilizadores, recomendamos que os adicione no Active Directory e sincronize com o Azure Active Directory através do Azure AD Connect.

- Saiba mais sobre [como pode adicionar utilizadores/grupos no Intune](users-add.md).
<!---why not send them to the AAD connect topic? Question out to Andre: https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect--->


### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>Tarefa 4: atribuir licenças de utilizador do Intune e do Office 365

Todos os utilizadores que visar para a implementação do Office 365 e do EMS/Intune têm de ter uma licença atribuída. Pode atribuir licenças EMS/Intune e Office 365 no centro de administração da Microsoft 365.

- Saiba mais sobre [como atribuir licenças do Intune](licenses-assign.md).

### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>Tarefa 5: definir o Intune como a autoridade de gestão de dispositivos móveis

Para poder configurar, gerir e inscrever dispositivos através do Intune, tem de definir o Intune como a autoridade de gestão de dispositivos.

- Saiba mais sobre [como definir a autoridade de gestão de dispositivos](mdm-authority-set.md).

### <a name="task-6-enable-device-platforms"></a>Tarefa 6: ativar as plataformas de dispositivos

Por padrão, a maioria das plataformas de dispositivos estão ativadas, exceto para dispositivos Apple (iOS/iPadOS e Mac). Antes de os dispositivos iOS/iPadOS poderem ser matriculados e geridos em Intune, a plataforma do dispositivo deve ser ativada. Para tal, tem de criar um certificado Push de MDM e de o adicionar ao Intune.

- Saiba mais sobre [como ativar dispositivos Apple para inscrição](../enrollment/apple-mdm-push-certificate-get.md).

### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>Tarefa 7: adicionar e implementar políticas de termos e condições

O Intune suporta políticas de termos e condições. Adicione políticas de termos e condições conforme adequado e implemente-as nos grupos visados com base nos seus requisitos e casos de utilização de implementação do Intune.

- Saiba mais sobre [como adicionar e implementar políticas de termos e condições](../enrollment/terms-and-conditions-create.md).

### <a name="task-8-add-and-deploy-configuration-policies"></a>Tarefa 8: adicionar e implementar políticas de configuração

O Intune suporta dois tipos de políticas de configuração: gerais e personalizadas. Adicione políticas de configuração conforme adequado e implemente-as nos grupos visados com base nos seus requisitos e casos de utilização de implementação do Intune.

- Saiba mais sobre [como adicionar e implementar políticas de configuração](../configuration/device-profiles.md).

### <a name="task-9-add-and-deploy-resource-profiles"></a>Tarefa 9: adicionar e implementar perfis de recursos

O Intune suporta os perfis de e-mail, Wi-Fi e VPN. Adicione estes perfis conforme adequado e implemente-os nos grupos visados com base nos seus requisitos e casos de utilização de implementação do Intune.

- Saiba mais sobre [como ativar o acesso aos recursos da empresa com o Intune](../configuration/device-profiles.md).

### <a name="task-10-add-and-deploy-apps"></a>Tarefa 10: adicionar e implementar aplicações

O Intune suporta a implementação de aplicações Web, aplicações de linha de negócio e aplicações públicas da Loja. Também pode gerir aplicações que integraram o SDK do Intune ao associá-las a políticas de proteção de aplicações. Adicione aplicações conforme adequado e implemente-as nos grupos visados com base nos seus requisitos e casos de utilização de implementação do Intune.

- Saiba mais sobre como [adicionar e implementar](../apps/app-management.md) aplicações.

### <a name="task-11-add-and-deploy-compliance-policies"></a>Tarefa 11: adicionar e implementar políticas de conformidade

O Intune suporta políticas de conformidade. Adicione políticas de conformidade conforme adequado e implemente-as nos grupos visados com base nos seus requisitos e casos de utilização de implementação do Intune.

- Saiba mais sobre [políticas de conformidade](../protect/device-compliance-get-started.md).

### <a name="task-12-enable-conditional-access-policies"></a>Tarefa 12: Ativar políticas de acesso condicional

Intune suporta acesso condicional para troca online, troca no local, SharePoint Online, Skype para Negócios Online e Dynamics CRM Online. Ative e configure o Acesso Condicional conforme apropriado com base nos casos e requisitos de utilização da sua intune.

- Saiba mais sobre o [Acesso Condicional](../protect/conditional-access.md).

### <a name="task-13-enroll-devices"></a>Tarefa 13: inscrever dispositivos

O Intune suporta as plataformas de dispositivos móveis iOS/iPadOS, Mac OS, Android, Windows e Windows. Inscreva plataformas de dispositivos móveis conforme adequado com base nos seus requisitos e casos de utilização de implementação do Intune.

- Saiba mais sobre [como inscrever dispositivos](../enrollment/device-enrollment.md).


## <a name="next-steps"></a>Próximos passos
Veja as orientações para [testar e validar a sua implementação do Intune](planning-guide-test-validation.md).
