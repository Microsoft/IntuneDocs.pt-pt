---
title: Configuração básica do Microsoft Intune
description: Este artigo fornece os passos necessários para configurar o Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: b5e075bdf834f70cf0c138942338963886662ae3
ms.sourcegitcommit: c0b954c82cd732b5328f92b618947bf425bf0a91
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/12/2019
ms.locfileid: "56086017"
---
# <a name="basic-setup"></a>Configuração básica

Depois de avaliar o seu ambiente, está na altura de configurar o Microsoft Intune.

## <a name="external-dependencies-for-an-intune-deployment"></a>Dependências externas para uma implementação do Intune

### <a name="identity"></a>identidade

O Intune precisa do Azure Active Directory (AAD) como o fornecedor de identidades e de agrupamentos de utilizadores. Saiba mais sobre:

-  [Requisitos de identidade](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)

-   [Requisitos da sincronização de diretórios](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)

-   [Autenticação multifator (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)

-   [Planear os grupos de utilizadores e de dispositivos](users-add.md)

-   [Como criar grupos de utilizadores e dispositivos](groups-get-started.md)

Se a sua organização já estiver a utilizar o Office 365, o Intune terá de utilizar o mesmo ambiente do Azure Active Directory.

### <a name="pki-optional"></a>PKI (opcional)

Se estiver a planear utilizar a autenticação baseada em certificados para perfis de e-mail, VPN ou Wi-Fi com o Intune, terá de confirmar se tem uma [infraestrutura PKI suportada](certificates-configure.md), pronta para criar e implementar perfis de certificados. Saiba mais sobre a configuração de certificados no Intune:

-   [Como configurar a infraestrutura de certificados para o SCEP](/intune/certificates-scep-configure)

-   [Como configurar a infraestrutura de certificados para o PFX](/intune/certficates-pfx-configure).


## <a name="task-list-for-an-intune-setup"></a>Lista de tarefas para uma configuração do Intune

### <a name="task-1-intune-subscription"></a>Tarefa 1: Subscrição do Intune

Para poder migrar para o Intune, precisa primeiro de uma subscrição do Intune.

-   Pode visitar [esta página](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0), que lhe dá instruções sobre como:

    -   Criar uma nova subscrição do Intune ligada a um novo inquilino do AAD.

    -   Ligar a subscrição do Intune ao iniciar sessão num inquilino do AAD existente.

### <a name="task-2-assign-intune-user-licenses"></a>Tarefa 2: Atribuir licenças de utilizador do Intune

-   Saiba [como atribuir licenças de utilizador do Intune](licenses-assign.md).

-   Se tiver criado um novo inquilino do Azure Active Directory, saiba [como criar novos utilizadores ou sincronizar o utilizador a partir do seu Active Directory (AD) no local.](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="task-3-set-your-mdm-authority-to-intune"></a>Tarefa 3: Defina a autoridade MDM para Intune

O Intune pode ser gerido através do portal do Azure ou da consola do Configuration Manager Current Branch. A menos que precise de integrar o Intune com uma implementação do Configuration Manager Current Branch, recomendamos que faça a gestão do Intune a partir do [Portal do Azure](https://portal.azure.com).

Defina a autoridade MDM para o **Intune**, de modo a ativar o portal do Azure no Intune. A utilização de uma autoridade MDM diferente permite ao Intune transferir a gestão de MDM para consolas de gestão da Microsoft alternativas. Estes casos são pouco comuns.

> [!IMPORTANT]
> Se estiver a transferir a gestão de dispositivos móveis para o Intune pela primeira vez, deverá definir a autoridade MDM para o Intune.

Saiba [como definir a autoridade de gestão móvel](mdm-authority-set.md).

## <a name="next-step"></a>Passo seguinte

Configurar [políticas de gestão de aplicações e dispositivos](migration-guide-configure-policies.md).
