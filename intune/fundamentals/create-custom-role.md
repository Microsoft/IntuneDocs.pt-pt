---
title: Criar um papel personalizado em Intune
description: Aprenda a criar um papel personalizado no Microsoft Intune.
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
ms.openlocfilehash: bfa2758546595d1e6237d88e128958c50759eb04
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369810"
---
# <a name="create-a-custom-role-in-intune"></a>Criar um papel personalizado em Intune

Pode criar uma função intune personalizada que inclua quaisquer permissões necessárias para uma função de trabalho específica. Por exemplo, se um grupo do departamento de TI gerir aplicações, políticas e perfis de configuração, pode juntar todas essas permissões numa só função personalizada. Depois de criar uma função personalizada, pode [atribuí-la](assign-role.md) a todos os utilizadores que necessitem dessas permissões.

Para criar, editar ou atribuir funções, a sua conta tem de ter uma das seguintes permissões no Azure AD:
- **Administrador Global**
- **Administrador de Serviços do Intune**

## <a name="to-create-a-custom-role"></a>Para criar uma função personalizada

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha a **administração do Inquilino** > **Papéis** > **Todas as funções** > **Criar**.

2. Na página **Basics,** introduza um nome e descrição para o novo papel e, em seguida, escolha **Next**.

3. Na página **Permissões,** escolha as permissões que pretende utilizar com esta função.

4. Na página **Scope (Tags),** escolha as etiquetas para este papel. Este papel pode aceder a recursos que também têm estas tags. Selecione **Next**.

5. Na página **Review + criar** página, quando terminar, escolha **Criar**. O novo papel é apresentado na lista nas **funções Intune - Todas as funções.**

## <a name="copy-a-role"></a>Copiar um papel

Também pode copiar um papel existente.

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha a **administração do Inquilino** > **Papéis** > **Todas as funções** > selecione a caixa de verificação para um papel na lista > **Duplicate**.

2. Na página **Basics,** insira um nome. Certifique-se de usar um nome único.

3. Todas as permissões e etiquetas de âmbito do papel original já serão selecionadas. Posteriormente, pode alterar o **nome**, **descrição,** **permissões**e **âmbito**da função duplicada .

4. Depois de ter feito todas as alterações que deseja, escolha **Next** para chegar à página **Review + criar.** Selecione **Criar**. 

## <a name="next-steps"></a>Próximos passos
- [Atribuir uma função a um utilizador](assign-role.md)
- [Saiba mais sobre o controlo de acesso baseado em papéis em Intune](role-based-access-control.md)


