---
title: Atribuir uma função a um utilizador intonizado
description: Aprenda a atribuir uma função incorporada ou personalizada a um utilizador no Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19fff092f7eccfc6de2a027c7834c52698176cbf
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569171"
---
# <a name="assign-a-role-to-an-intune-user"></a>Atribuir uma função a um utilizador intonizado

Pode atribuir uma função [incorporada](role-based-access-control.md#built-in-roles) ou [personalizada](create-custom-role.md) a um utilizador Intune.

Para criar, editar ou atribuir funções, a sua conta tem de ter uma das seguintes permissões no Azure AD:
- **Administrador Global**
- **Administrador de Serviços do Intune**

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha a **administração do Inquilino** > **Papéis** > **todas as funções**.

2. Nas **funções Intune - Todas as funções,** escolha o papel incorporado que pretende atribuir > **Atribuições** > **Atribuir**.

5. Na página **Basics,** introduza um **nome de Atribuição** e descrição opcional de **Atribuição,** e depois escolha **A Seguinte**.

6. Na página **dos Grupos De Administração,** selecione o grupo que contém o utilizador a que pretende dar as permissões. Escolha **Seguinte**

7. Na página **Scope (Grupos),** escolha um grupo que contenha os utilizadores/dispositivos que o membro acima será autorizado a gerir. Escolha **Seguinte**.

8. Na página **Scope (Tags),** escolha etiquetas onde esta atribuição de funções será aplicada. Escolha **Seguinte**.

9. Na página **Review + Criar,** quando terminar, escolha **Criar**. A nova atribuição é apresentada na lista de atribuições.

## <a name="next-steps"></a>Próximos passos
- [Saiba mais sobre o controlo de acesso baseado em papéis em Intune](role-based-access-control.md)
- [Criar um papel personalizado](create-custom-role.md)


