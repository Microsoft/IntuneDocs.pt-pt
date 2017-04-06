---
title: "Promover a adoção por parte de utilizadores finais de unidades com acesso condicional | Documentos da Microsoft"
description: "O objetivo deste artigo é proporcionar informações sobre como tirar partido do acesso condicional para promover a inscrição no Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: 26d11bc64802005bcce8cc1962d531af6ffe5cd5
ms.lasthandoff: 03/27/2017


---

# <a name="phase-2-drive-end-user-adoption-with-conditional-access"></a>Fase 2: Promover a adoção por parte de utilizadores finais de unidades com acesso condicional

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

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

-   Saiba mais sobre o [acesso condicional](https://docs.microsoft.com/intune-azure/conditional-access/what-is-conditional-access).

## <a name="task-list-for-conditional-access"></a>Lista de tarefas do acesso condicional

### <a name="task-1-get-ready-for-intune-conditional-access"></a>Tarefa 1: Preparar-se para o acesso condicional do Intune

-   Saiba [como configurar o acesso condicional](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

### <a name="task-2-setup-intune-conditional-access"></a>Tarefa 2: Configurar o acesso condicional do Intune

Escolha um dos seguintes tipos de políticas de acesso condicional para saber mais:

-   [Exchange Online e o novo Exchange Online Dedicado](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)

-   [Exchange no local e o Exchange Online dedicado legado](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)

-   [SharePoint Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)

-   [Skype para Empresas Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)

-   [Dynamics CRM Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)

-   [Cenários de exemplo de acesso ao e-mail](https://docs.microsoft.com/intune/deploy-use/restrict-email-access-example-scenarios)

## <a name="next-steps"></a>Próximos passos

[Fase 2: Ciclo de Migração Típico](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle)

