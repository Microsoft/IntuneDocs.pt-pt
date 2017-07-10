---
title: "Configuração básica do Intune"
description: "O objetivo deste artigo é apresentar os passos necessários para configurar o Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c3129b2a8d93e91493455da5f3e5fd1a59dd77bb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="basic-setup"></a>Configuração básica

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

Depois de avaliar o seu ambiente, está na altura de configurar o Intune.

## <a name="external-dependencies-for-an-intune-deployment"></a>Dependências externas para uma implementação do Intune

### <a name="identity"></a>Identidade

O Intune precisa do Azure Active Directory (AAD) como o fornecedor de identidades e de agrupamentos de utilizadores.

-   Saiba mais sobre os [requisitos de identidade](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview).

-   Saiba mais sobre os [requisitos da sincronização de diretórios](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements).

-   Saiba mais sobre os [requisitos de autenticação multifator](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements).

-   Saiba mais sobre como [planear os seus grupos de utilizadores e de dispositivos](/intune/users-permissions-add).

-   Saiba [como criar grupos de utilizadores e dispositivos](/intune/groups-get-started).

Se a sua organização já utiliza o Office 365, é importante que o Intune utilize o mesmo ambiente do Azure Active Directory.

### <a name="pki-optional"></a>PKI (opcional)

Se estiver a planear utilizar a autenticação baseada em certificados para perfis de e-mail, VPN ou Wi-Fi com o Intune, terá de confirmar se tem uma [infraestrutura PKI suportada](/intune/certificates-configure), pronta para criar e implementar perfis de certificados.

Seguem-se mais informações sobre a configuração de certificados no Intune.

-   [Como configurar a infraestrutura de certificados para o SCEP](/intune/certificates-scep-configure).

-   [Como configurar a infraestrutura de certificados para o PFX](/intune/certficates-pfx-configure).


## <a name="task-list-for-an-intune-setup"></a>Lista de tarefas para uma Configuração do Intune

### <a name="task-1-intune-subscription"></a>Tarefa 1: Subscrição do Intune

Para poder migrar para o Intune, precisa primeiro de uma subscrição do Intune.

-   Pode visitar [esta página](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0), que lhe dá instruções sobre como:

    -   Criar uma nova subscrição do Intune ligada a um novo inquilino do AAD.

    -   Ligar a subscrição do Intune ao iniciar sessão num inquilino do AAD existente.

### <a name="task-2-assign-intune-user-licenses"></a>Tarefa 2: Atribuir licenças de utilizador do Intune

-   Saiba [como atribuir licenças de utilizador do Intune](licenses-assign.md).

-   Se tiver criado um novo inquilino do Azure Active Directory, saiba [como criar novos utilizadores ou sincronizar o utilizador a partir do seu Active Directory (AD) no local.](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="task-3-set-your-mdm-authority-to-intune"></a>Tarefa 3: Definir a autoridade MDM para o Intune

O Intune pode ser gerido através do portal do Azure ou da consola do Configuration Manager Current Branch. A menos que precise de integrar o Intune com uma implementação do Configuration Manager Current Branch, recomenda-se a gestão do Intune a partir de [Portal do Azure](https://portal.azure.com).

Defina a autoridade MDM para o **Intune** para ativar o Portal do Azure no Intune. A utilização de uma autoridade MDM diferente permite ao Intune transferir a gestão de MDM para consolas de gestão da Microsoft alternativas. Estes casos são pouco comuns.

> [!IMPORTANT]
> Se estiver a transferir a gestão de dispositivos móveis para o Intune pela primeira vez, deverá definir a autoridade MDM para o Intune.

-   Saiba [como definir a autoridade de gestão móvel](/intune/mdm-authority-set).

## <a name="next-step"></a>Passo seguinte

[Configurar políticas de gestão de aplicações e dispositivos](migration-guide-configure-policies.md)
