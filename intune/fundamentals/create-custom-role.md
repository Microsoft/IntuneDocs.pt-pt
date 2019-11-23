---
title: Create a custom role in Intune
description: Learn how to create a custom role in Microsoft Intune.
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
ms.openlocfilehash: 3ca83287c58f8d2fb7c8eec5f8cc793e2c67b77a
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390709"
---
# <a name="create-a-custom-role-in-intune"></a>Create a custom role in Intune

You can create a custom Intune role that includes any permissions required for a specific job function. Por exemplo, se um grupo do departamento de TI gerir aplicações, políticas e perfis de configuração, pode juntar todas essas permissões numa só função personalizada. After creating a custom role, you can [assign](assign-role.md) it to any users that need those permissions.

Para criar, editar ou atribuir funções, a sua conta tem de ter uma das seguintes permissões no Azure AD:
- **Administrador Global**
- **Administrador de Serviços do Intune**

## <a name="to-create-a-custom-role"></a>Para criar uma função personalizada

1. Inicie sessão no [portal do Azure](https://portal.azure.com) com as suas credenciais do Intune.

2. Selecione **Todos os serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3. Choose **Intune** > **Roles** > **All roles** > **Add**.

4. No painel **Adicionar Função Personalizada**, introduza um nome e uma descrição para a nova função e, em seguida, clique em **Permissões**.

5. No painel **Permissões**, escolha as permissões que quer utilizar com esta função.

6. On the **Scope (Tags)** blade, choose the tags for this role. This role can access resources that also have these tags.

7. Quando tiver terminado, selecione **OK**.

8. No painel **Adicionar Função Personalizada**, clique em **Criar**. The new role is displayed in the list on the **Intune roles - All roles** blade.


## <a name="copy-a-role"></a>Copy a role

You can also copy an existing role.

1. Sign into the [Azure portal](https://portal.azure.com) with your Intune credentials and select **Intune**.

2. Select **Roles** > **All roles** > select a role in the list > **Duplicate**.

3. Under **Duplicate role**, enter a name. Make sure to use a unique name.

4. All the permissions and scope tags from the original role will already be selected. You can subsequently change the duplicate role's **Name**, **Description**, **Permissions**, and **Scope (Tags)** .

5. Selecione **Criar**. 

## <a name="next-steps"></a>Próximos passos
- [Assign a role to a user](assign-role.md)
- [Learn more about role-based access control in Intune](role-based-access-control.md)
