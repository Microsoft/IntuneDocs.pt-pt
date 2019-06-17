---
title: Promover a adoção com acesso condicional
titleSuffix: Microsoft Intune
description: Saiba como utilizar o acesso condicional para promover a inscrição no Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2bedaf279d65ee1ed7f8dda4e8d866fb848bade7
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044582"
---
# <a name="drive-end-user-adoption-with-conditional-access-in-microsoft-intune"></a>Promover a adoção com acesso condicional no Microsoft Intune

A ativação de funcionalidades de acesso condicional com o Intune, tais como bloquear o e-mail para dispositivos não inscritos, pode ajudar a promover a inscrição e conformidade, mas não são necessários para a migração seja concluída com êxito. Os requisitos de segurança e os objetivos de adoção da migração devem determinar a taxa de êxito.

## <a name="migration-campaign-with-conditional-access"></a>Campanha de migração com acesso condicional

Esta é uma abordagem típica para melhorar uma campanha de migração com acesso condicional:

1.  Configure regras de acesso condicional para ser impostas para todos os utilizadores, mas exclua especificamente os utilizadores que precisam de migrar do fornecedor de MDM antigo. Pode criar um grupo de utilizadores do Azure AD com todos os utilizadores de acesso condicional excluídos.

2.  Como migrar os utilizadores, removê-los a partir do grupo de exclusão de acesso condicional.

3.  Após a conclusão da migração, configure todas as políticas de acesso condicional para bloquearem por predefinição, a menos que o Intune permite o acesso.

### <a name="advantages"></a>Vantagens

-   Concede o controlo de acesso a novas contas de utilizador que não foram geridas pela solução anterior.

-   Concede um período de tolerância para os utilizadores da solução anterior migrarem.

-   Minimiza a perda de produtividade.

### <a name="disadvantages"></a>Desvantagens

-   Os utilizadores da solução anterior podem potencialmente aceder aos recursos através de dispositivos não geridos até que o acesso condicional estiver ativado para esses utilizadores.


Esta é uma abordagem entre muitas. Pode escolher um processo mais simples que difere todo o acesso condicional até depois de todas as fases terem tido instrução para inscrever ou um processo mais rigoroso que impõe o acesso condicional desde o início e exige a conformidade total para todos os acessos.

-   Saiba mais sobre o [Acesso Condicional](conditional-access.md).

## <a name="task-list-for-conditional-access"></a>Lista de tarefas para o acesso condicional

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>Tarefa 1: Decidir como irá implementar o acesso condicional

[Formas comuns de utilizar o acesso condicional](conditional-access-intune-common-ways-use.md).

### <a name="task-2-set-up-intune-conditional-access"></a>Tarefa 2: Configurar o acesso condicional do Intune

Escolha uma das seguintes opções:

-   [Configurar o acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

-   [Instalar o conector do Exchange no local com o Intune](exchange-connector-install.md)

-   [Definir políticas de acesso condicional com base na aplicação para o Exchange Online](app-based-conditional-access-intune-create.md)

-   [Definir políticas de acesso condicional com base na aplicação para o SharePoint Online](app-based-conditional-access-intune-create.md)

-   [Bloquear aplicações que não utilizam autenticação moderna (ADAL)](app-modern-authentication-block.md)

## <a name="next-steps"></a>Passos Seguintes

Saiba mais sobre o [ciclo de migração típico](migration-guide-cycle.md).
