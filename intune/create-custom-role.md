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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: d053b0b37931443a343c91b5122b7a097d248c51
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048695"
---
# <a name="create-a-custom-role-in-intune"></a>Criar uma função personalizada no Intune

Pode criar uma função personalizada do Intune que inclui todas as permissões necessárias para uma função de tarefa específica. Por exemplo, se um grupo do departamento de TI gerir aplicações, políticas e perfis de configuração, pode juntar todas essas permissões numa só função personalizada. Depois de criar uma função personalizada, pode [atribuir](assign-role.md) -lo a quaisquer utilizadores que têm essas permissões.

Para criar, editar ou atribuir funções, a sua conta tem de ter uma das seguintes permissões no Azure AD:
- **Administrador Global**
- **Administrador de Serviços do Intune**

## <a name="to-create-a-custom-role"></a>Para criar uma função personalizada

1. Inicie sessão no [portal do Azure](https://portal.azure.com) com as suas credenciais do Intune.

2. Selecione **Todos os serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3. Escolher **Intune** > **funções** > **todas as funções** > **adicionar**.

4. No painel **Adicionar Função Personalizada**, introduza um nome e uma descrição para a nova função e, em seguida, clique em **Permissões**.

5. No painel **Permissões**, escolha as permissões que quer utilizar com esta função. Utilize a [Tabela de RBAC do Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) para ajudá-lo a decidir quais as permissões que quer aplicar.

6. Sobre o **âmbito (etiquetas)** painel, selecione as etiquetas para esta função. Esta função pode aceder a recursos que também tenham essas marcas.

7. Quando tiver terminado, selecione **OK**.

8. No painel **Adicionar Função Personalizada**, clique em **Criar**. A nova função é apresentada na lista no **funções do Intune – todas as funções** painel.

## <a name="next-steps"></a>Passos Seguintes
- [Atribuir uma função a um utilizador](assign-role.md)
- [Saiba mais sobre o controlo de acesso baseado em funções no Intune](role-based-access-control.md)
