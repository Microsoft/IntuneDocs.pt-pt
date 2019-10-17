---
title: Conduzir a adoção do usuário final com acesso condicional
titleSuffix: Microsoft Intune
description: Saiba como usar o acesso condicional para direcionar o registro no Microsoft Intune.
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
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 115313816542fd642e6a0c67900abd48b7146e42
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72510075"
---
# <a name="drive-end-user-adoption-with-conditional-access-in-microsoft-intune"></a>Conduzir a adoção do usuário final com acesso condicional no Microsoft Intune

A habilitação de recursos de acesso condicional com o Intune, como o bloqueio de email para dispositivos não registrados, pode ajudar a orientar o registro e a conformidade, mas eles não são necessários para que uma migração seja bem-sucedida. Os requisitos de segurança e os objetivos de adoção da migração devem determinar a taxa de êxito.

## <a name="migration-campaign-with-conditional-access"></a>Campanha de migração com acesso condicional

Aqui está uma abordagem típica para aprimorar uma campanha de migração com acesso condicional:

1. Defina as regras de acesso condicional a serem impostas para todos os usuários, mas exclua especificamente os usuários que precisam migrar do provedor de MDM antigo. Você pode criar um grupo de usuários do Azure AD com todos os usuários excluídos de acesso condicional.

2. À medida que os usuários migram, remova-os do grupo de exclusão de acesso condicional.

3. Após a conclusão da migração, configure todas as políticas de acesso condicional para bloquear por padrão, a menos que o Intune permita o acesso.

### <a name="advantages"></a>Vantagens

- Concede o controlo de acesso a novas contas de utilizador que não foram geridas pela solução anterior.

- Concede um período de tolerância para os utilizadores da solução anterior migrarem.

- Minimiza a perda de produtividade.

### <a name="disadvantages"></a>Desvantagens

- Os usuários da solução anterior poderiam potencialmente acessar recursos usando dispositivos não gerenciados até que o acesso condicional seja habilitado para esses usuários.


Esta é uma abordagem entre muitas. Você pode escolher um processo mais simples que adie todo o acesso condicional até que todas as fases tenham sido instruídas a se registrar ou um processo mais estrito que impõe o acesso condicional do início e exija total conformidade para todo o acesso.

- Saiba mais sobre o [Acesso Condicional](../protect/conditional-access.md).

## <a name="task-list-for-conditional-access"></a>Lista de tarefas para acesso condicional

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>Tarefa 1: decidir como você vai implementar o acesso condicional

[Maneiras comuns de usar o acesso condicional](../protect/conditional-access-intune-common-ways-use.md).

### <a name="task-2-set-up-intune-conditional-access"></a>Tarefa 2: configurar o acesso condicional do Intune

Escolha uma das seguintes opções:

- [Configurar o acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

- [Instalar o conector do Exchange no local com o Intune](../protect/exchange-connector-install.md)

- [Configurar políticas de acesso condicional com base no aplicativo para o Exchange Online](../protect/app-based-conditional-access-intune-create.md)

- [Configurar políticas de acesso condicional com base no aplicativo para o SharePoint Online](../protect/app-based-conditional-access-intune-create.md)

- [Bloquear aplicações que não utilizam autenticação moderna (ADAL)](../protect/app-modern-authentication-block.md)

## <a name="next-steps"></a>Próximos passos

Saiba mais sobre o [ciclo de migração típico](../migration-guide-cycle.md).
