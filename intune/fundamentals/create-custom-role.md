---
title: Criar uma função personalizada no Intune
description: Saiba como criar uma função personalizada no Microsoft Intune.
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
ms.openlocfilehash: 68c2dc7df123593513c14e16e2626c7426f50b01
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207422"
---
# <a name="create-a-custom-role-in-intune"></a>Criar uma função personalizada no Intune

Você pode criar uma função personalizada do Intune que inclua todas as permissões necessárias para uma função de trabalho específica. Por exemplo, se um grupo do departamento de TI gerir aplicações, políticas e perfis de configuração, pode juntar todas essas permissões numa só função personalizada. Depois de criar uma função personalizada, você pode [atribuí](assign-role.md) -la a qualquer usuário que precise dessas permissões.

Para criar, editar ou atribuir funções, a sua conta tem de ter uma das seguintes permissões no Azure AD:
- **Administrador Global**
- **Administrador de Serviços do Intune**

## <a name="to-create-a-custom-role"></a>Para criar uma função personalizada

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **funções** > **todas as funções** > **Adicionar**.

2. No painel **Adicionar Função Personalizada**, introduza um nome e uma descrição para a nova função e, em seguida, clique em **Permissões**.

3. No painel **Permissões**, escolha as permissões que quer utilizar com esta função.

4. Na folha **escopo (marcas)** , escolha as marcas para essa função. Essa função pode acessar recursos que também têm essas marcas.

5. Quando tiver terminado, selecione **OK**.

6. No painel **Adicionar Função Personalizada**, clique em **Criar**. A nova função é exibida na lista na folha **funções do Intune – todas as funções** .


## <a name="copy-a-role"></a>Copiar uma função

Você também pode copiar uma função existente.

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **funções** > **todas as funções** > Selecionar uma função na lista > **duplicar**.

2. Em **função duplicada**, insira um nome. Certifique-se de usar um nome exclusivo.

3. Todas as permissões e marcas de escopo da função original já serão selecionadas. Posteriormente, você pode alterar o **nome**, a **Descrição**, **as permissões**e o **escopo (marcas)** da função duplicada.

4. Selecione **Criar**. 

## <a name="next-steps"></a>Próximos passos
- [Atribuir uma função a um usuário](assign-role.md)
- [Saiba mais sobre o controle de acesso baseado em função no Intune](role-based-access-control.md)
