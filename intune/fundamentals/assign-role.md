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
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 780a248f16a8a5028875c9c2401921ea23d0af24
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540933"
---
# <a name="assign-a-role-to-an-intune-user"></a>Atribuir uma função a um usuário do Intune

Você pode atribuir uma função interna ou [personalizada](create-custom-role.md) a um usuário [do](role-based-access-control.md#built-in-roles) Intune.

Para criar, editar ou atribuir funções, a sua conta tem de ter uma das seguintes permissões no Azure AD:
- **Administrador Global**
- **Administrador de Serviços do Intune**

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **administração de locatário** > **funções** > **todas as funções**.

2. Na folha **funções do Intune – todas as funções** , escolha a função interna que você deseja atribuir.

3. Na folha*nome da função*de < >- **visão geral** , escolha **gerenciar** **atribuições**de > .

4. No painel de função personalizada, escolha **Atribuir**.

5. Na folha **atribuições de função** , insira um **nome de atribuição** e uma descrição de **atribuição** opcional para a atribuição.

6. Para **Membros (grupos)** , escolha um grupo que contenha o usuário ao qual você deseja conceder as permissões.

7. Para **escopo (grupos)** , escolha um grupo que contenha os usuários/dispositivos que o membro acima terá permissão para gerenciar.

8. Para **escopo (marcas)** , escolha as marcas em que essa atribuição de função será aplicada.

9. Quando tiver terminado, selecione **OK**. A nova atribuição é apresentada na lista de atribuições.


## <a name="next-steps"></a>Próximos passos
- [Saiba mais sobre o controle de acesso baseado em função no Intune](role-based-access-control.md)
- [Criar uma função personalizada](create-custom-role.md)
