---
title: Atribuir uma função de utilizador do Intune
description: Saiba como atribuir uma função incorporada ou personalizada a um utilizador no Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a22fef1c04ae52a8a4cc65eaadc1ef6fcd524c19
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66043599"
---
# <a name="assign-a-role-to-an-intune-user"></a>Atribuir uma função de utilizador do Intune

Pode atribuir um [incorporadas](role-based-access-control.md#built-in-roles) ou [personalizado](create-custom-role.md) função de utilizador do Intune.

Para criar, editar ou atribuir funções, a sua conta tem de ter uma das seguintes permissões no Azure AD:
- **Administrador Global**
- **Administrador de Serviços do Intune**

Para obter uma lista completa das permissões para cada função incorporada, consulte a [tabela de RBAC do Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a).

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).

2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.

3. Sobre o **Intune** painel, escolha **funções** > **todas as funções**.

4. Sobre o **funções do Intune – todas as funções** painel, selecione a função incorporada que pretende atribuir.

5. Na <*nome da função*>- **descrição geral** painel, escolha **gerir** > **atribuições**.

6. No painel de função personalizada, escolha **Atribuir**.

7. Na **atribuições de funções** painel, introduza um **nome da atribuição** e opcionais **descrição da atribuição** para a atribuição.

8. Para **membros (grupos)**, escolha um grupo que contém o usuário quer conceder as permissões.

9. Para **âmbito (grupos)**, escolha um grupo que contém os utilizadores/dispositivos em que o membro acima terá permissão para gerir.

10. Para **âmbito (etiquetas)**, escolha as etiquetas em que esta atribuição de função será aplicada.

11. Quando tiver terminado, selecione **OK**. A nova atribuição é apresentada na lista de atribuições.


## <a name="next-steps"></a>Passos Seguintes
- [Saiba mais sobre o controlo de acesso baseado em funções no Intune](role-based-access-control.md)
- [Criar uma função personalizada](create-custom-role.md)
