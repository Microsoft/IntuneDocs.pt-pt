---
title: "Promover a adoção por parte de utilizadores finais de unidades com acesso condicional"
description: "O objetivo deste artigo é proporcionar informações sobre como tirar partido do acesso condicional para promover a inscrição no Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0b2fbcc1d63f229e1b63873841bc300bdde92fa3
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/03/2017
---
# <a name="drive-end-user-adoption-with-conditional-access"></a>Promover a adoção por parte de utilizadores finais de unidades com acesso condicional

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

A ativação de funcionalidades de acesso condicional com o Intune, tais como bloquear o e-mail para dispositivos cuja inscrição foi anulada, pode ajudar a promover a inscrição e a conformidade, mas não é obrigatória para que a migração seja concluída com êxito. Os requisitos de segurança e os objetivos de adoção da migração devem determinar a taxa de êxito.

## <a name="migration-campaign-with-conditional-access"></a>Campanha de migração com acesso condicional

Apresentamos a seguir uma abordagem típica para melhorar uma campanha de migração com acesso condicional:

1.  Configure regras de acesso condicional para serem impostas a todos os utilizadores, mas exclua especificamente os utilizadores que precisam de migrar do fornecedor de MDM antigo. Pode criar um grupo de utilizadores do Azure AD com todos os utilizadores de acesso condicional excluídos.

2.  À medida que os utilizadores migram, remova-os do grupo de exclusão de acesso condicional.

3.  Concluída a migração, configure todas as políticas de acesso condicional para bloquearem por predefinição, a menos que o Intune permita o acesso.

### <a name="advantages"></a>Vantagens

-   Concede o controlo de acesso a novas contas de utilizador que não foram geridas pela solução anterior.

-   Concede um período de tolerância para os utilizadores da solução anterior migrarem.

-   Minimiza a perda de produtividade.

### <a name="disadvantages"></a>Desvantagens

-   Os utilizadores da solução anterior podem potencialmente aceder aos recursos através de dispositivos não geridos até que o acesso condicional seja ativado para esses utilizadores.

> [!TIP]
> Esta é uma abordagem entre muitas. Pode escolher um processo mais simples que difere todo o acesso condicional até todas as fases terem tido instrução para se inscreverem ou um processo mais rigoroso que impõe o acesso condicional desde o início e exige a conformidade total para todo o acesso.

-   Saiba mais sobre o [acesso condicional](/intune/conditional-access).

## <a name="task-list-for-conditional-access"></a>Lista de tarefas do acesso condicional

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>Tarefa 1: Decidir como irá implementar o acesso condicional

[Formas comuns de utilizar o acesso condicional](/intune/conditional-access-intune-common-ways-use).

### <a name="task-2-set-up-intune-conditional-access"></a>Tarefa 2: Configurar o acesso condicional do Intune

Escolha uma das seguintes opções:

-   [Configurar o acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

-   [Instalar o conector do Exchange no local com o Intune](/intune/exchange-connector-install)

-   [Definir políticas de acesso condicional com base nas aplicações para Exchange Online](/intune/app-based-conditional-access-intune-exchange-online-create)

-   [Definir políticas de acesso condicional com base nas aplicações para o SharePoint Online](/intune/app-based-conditional-access-intune-sharepoint-online-create)

-   [Bloquear aplicações que não utilizam autenticação moderna (ADAL)](/intune/app-modern-authentication-block)

## <a name="next-steps"></a>Próximos passos

[Ciclo de migração típico](migration-guide-cycle.md)
