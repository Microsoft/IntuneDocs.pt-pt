---
title: Atribuir uma função a um usuário do Intune
description: Saiba como atribuir uma função interna ou personalizada a um usuário no Microsoft Intune.
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
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0539e4d12173ba2c7ba8d3af3364daf69ddbbf34
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071540"
---
# <a name="assign-a-role-to-an-intune-user"></a>Atribuir uma função a um usuário do Intune

Você pode atribuir uma função interna ou [personalizada](create-custom-role.md) a um usuário [do](role-based-access-control.md#built-in-roles) Intune.

Para criar, editar ou atribuir funções, a sua conta tem de ter uma das seguintes permissões no Azure AD:
- **Administrador Global**
- **Administrador de Serviços do Intune**

Para obter uma lista completa das permissões para cada função interna, consulte a [tabela RBAC do Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a).

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).

2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.

3. Na folha **Intune** , escolha **funções** > **todas as funções**.

4. Na folha **funções do Intune – todas as funções** , escolha a função interna que você deseja atribuir.

5. Na folha*nome da função*de < >- **visão geral** , escolha **gerenciar** > **atribuições**.

6. No painel de função personalizada, escolha **Atribuir**.

7. Na folha **atribuições de função** , insira um **nome de atribuição** e uma descrição de **atribuição** opcional para a atribuição.

8. Para **Membros (grupos)** , escolha um grupo que contenha o usuário ao qual você deseja conceder as permissões.

9. Para **escopo (grupos)** , escolha um grupo que contenha os usuários/dispositivos que o membro acima terá permissão para gerenciar.

10. Para **escopo (marcas)** , escolha as marcas em que essa atribuição de função será aplicada.

11. Quando tiver terminado, selecione **OK**. A nova atribuição é apresentada na lista de atribuições.


## <a name="next-steps"></a>Passos seguintes
- [Saiba mais sobre o controle de acesso baseado em função no Intune](role-based-access-control.md)
- [Criar uma função personalizada](create-custom-role.md)
