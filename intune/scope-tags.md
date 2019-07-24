---
title: Filtrar políticas com etiquetas de âmbito no Microsoft Intune – Azure | Microsoft Docs
description: Utilize etiquetas de âmbito para filtrar perfis de configuração para funções específicas.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 627899eafb2175b2d3034045bd765a10f4a203d6
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882493"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Usar o controle de acesso baseado em função (RBAC) e marcas de escopo para distribuição de ti

Você pode usar o controle de acesso baseado em função e as marcas de escopo para garantir que os administradores corretos tenham o acesso e a visibilidade certos para os objetos do Intune corretos. As funções determinam quais administradores de acesso têm para quais objetos. As marcas de escopo determinam quais objetos os administradores podem ver.

Por exemplo, digamos que um administrador regional do escritório de Seattle receba a função de gerente de política e perfil. Você deseja que esse administrador Veja e gerencie apenas os perfis e as políticas que se aplicam somente a dispositivos de Seattle. Para fazer isso, você deve:

1. Crie uma marca de escopo chamada Seattle.
2. Crie uma atribuição de função para a função de Gerenciador de políticas e perfis com: 
    - Membros (grupos) = um grupo de segurança chamado Seattle IT admins. Todos os administradores deste grupo terão permissão para gerenciar políticas e perfis para usuários/dispositivos no escopo (grupos).
    - Escopo (grupos) = um grupo de segurança chamado usuários de Seattle. Todos os usuários/dispositivos nesse grupo podem ter seus perfis e políticas gerenciados pelos administradores nos Membros (grupos). 
    - Scope (Tags) = Seattle. Os administradores no membro (grupos) podem ver os dispositivos que também têm a marca de escopo Seattle.
3. Adicione a marca de escopo Seattle a políticas e perfis que você deseja que os administradores em Membros (grupos) possam acessar.
4. Adicione a marca de escopo Seattle aos dispositivos que você deseja que fiquem visíveis para os administradores nos Membros (grupos). 


## <a name="to-create-a-scope-tag"></a>Para criar uma etiqueta de âmbito

1. No Intune, escolha  > **escopo de funções (marcas)**  > **criar**.

    ![Captura de tela da criação de uma marca de escopo.](./media/scope-tags/create-scope-tag.png)

3. Se você quiser todos os dispositivos em grupos específicos, escolha **atribuir marca de escopo a todos os dispositivos nos grupos selecionados**.
    1. Na página **Selecionar grupos a serem incluídos** , escolha os grupos que contêm os dispositivos aos quais você deseja atribuir essa marca de escopo.
    2. Escolha **Selecionar**.
4. Selecione **Criar**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Para atribuir uma etiqueta de âmbito a uma função

1. No Intune, escolha **funções** > **todas as funções** > escolha uma função  > > atribuições**atribuir**.

    ![Captura de tela de atribuir escopo a uma função.](./media/scope-tags/assign-scope-to-role.png)

2. Forneça um **nome de atribuição** e uma **Descrição**.
3. Escolha **Membros (grupos)**  > **Adicionar** > escolha os grupos que você deseja como parte dessa atribuição > **selecione** > **OK**. os direitos de usuário neste grupo terão permissões para gerenciar políticas e perfis para usuários/dispositivos no escopo (grupos).

    ![Captura de tela de selecionar grupos de membros.](./media/scope-tags/select-member-groups.png)

4. Se você quiser gerenciar usuários/dispositivos em um conjunto específico de grupos, escolha **escopo (grupos)**  > **grupos** > selecionados**Selecione os grupos a serem incluídos** > escolha os grupos > **selecione** > **OK** . Todos os usuários/dispositivos nesse grupo podem ter seus perfis e políticas gerenciados pelos administradores nos Membros (grupo).

    ![Captura de tela de selecionar grupos de escopo.](./media/scope-tags/select-scope-groups.png)

    Como alternativa, você pode escolher **todos os dispositivos**, **todos os usuários**ou todos os **usuários & todos os dispositivos**.

    ![Captura de tela de outras opções para selecionar grupos de escopo.](./media/scope-tags/scope-group-other-options.png)
    
5. Escolha **escopo (marcas)**  > **Adicionar** > escolha as marcas que você deseja adicionar a essa função > **selecione** > **OK**. Os usuários em Membros (grupos) terão acesso às políticas e aos perfis que também têm a mesma marca de escopo.

    ![Captura de tela de selecionar marcas de escopo.](./media/scope-tags/select-scope-tags.png)

6. Escolha **OK**. 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Para adicionar uma etiqueta de âmbito a um perfil de configuração
1. No Intune, escolha**perfis** de **configuração** > de dispositivo > escolha um perfil.

    ![Captura de tela de selecionar perfil.](./media/scope-tags/choose-profile.png)

2. Escolha  > **escopo de Propriedades (marcas)**  > **Adicionar**.

    ![Captura de tela de adicionar marcas de escopo.](./media/scope-tags/add-scope-tags.png)

3. Em **selecionar marcas**, escolha as marcas que você deseja adicionar ao perfil.
4. Escolha **selecionar** > OkSalvar > .

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>Para atribuir uma marca de escopo a uma política de configuração de aplicativo
Para dispositivos com o **tipo de registro de dispositivo** definido como **dispositivos gerenciados**:
1. Escolha **aplicativos** > cliente**políticas de configuração de aplicativo** > escolha uma política de configuração de aplicativo.
2. Escolha escopo de **Propriedades** >  **(marcas)** > escolha as marcas que você deseja atribuir à política.

Para dispositivos com o **tipo de registro de dispositivo** definido como **aplicativos gerenciados**:
1. Escolha **aplicativos** > cliente**políticas de configuração de aplicativo** > escolha uma política de configuração de aplicativo.
2. Escolha **escopo (marcas)** > escolha as marcas que você deseja atribuir à política.


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>Para atribuir uma marca de escopo a um perfil de provisionamento de aplicativo iOS
1. No Intune, escolha **aplicativos** > cliente**perfis de provisionamento de aplicativo do IOS** > escolha um perfil.
2. Escolha escopo de **Propriedades** >  **(marcas)** > escolha as marcas que você deseja atribuir ao perfil.
3. Escolha **selecionar** > OkSalvar > .

## <a name="to-assign-a-scope-tag-to-an-apple-volume-purchase-program-vpp-token"></a>Para atribuir uma marca de escopo a um token Apple Volume Purchase Program (VPP)
1. No Intune, escolha **aplicativos** > cliente tokens de**VPP da Apple** > escolha um token VPP.
2. Selecione **escopo (marcas)** > escolha as marcas que você deseja atribuir ao perfil. Os aplicativos VPP e os livros eletrônicos associados ao token VPP herdam as marcas atribuídas.
3. Escolha **selecionar** > OkSalvar > .

## <a name="scope-tag-details"></a>Detalhes da marca de escopo
Ao trabalhar com marcas de escopo, lembre-se destes detalhes:

- Atualmente, você pode atribuir marcas de escopo a:
  - Atribuições de função
  - Políticas de conformidade de dispositivo
  - Perfis de configuração de dispositivos
  - Anéis de atualizações do Windows 10
  - Dispositivos geridos
  - Aplicações
  - Políticas de configuração de aplicativo – dispositivos gerenciados
  - Scripts do PowerShell
  - Tokens DEP
  - Perfil de provisionamento de aplicativo iOS
  - Tokens do VPP (Volume Purchase Program)
- Quando um administrador cria um objeto no Intune, todas as marcas de escopo atribuídas a esse administrador serão automaticamente atribuídas ao novo objeto.
- O RBAC do Intune não se aplica a Azure Active Directory funções. Portanto, as funções Administradores de serviço do Intune e administradores globais têm acesso de administrador completo ao Intune, independentemente das marcas de escopo que têm.
- Os administradores em uma atribuição de função com marcas de escopo também podem ver objetos do Intune sem marcas de escopo.
- Você só pode atribuir uma marca de escopo que você tem em suas atribuições de função.
- Você só pode direcionar grupos listados no escopo (grupos) de sua atribuição de função.
- Se você tiver uma marca de escopo atribuída à sua função, não poderá excluir todas as marcas de escopo em um objeto do Intune. Pelo menos uma marca de escopo é necessária.

## <a name="next-steps"></a>Passos Seguintes

Efetue a gestão das suas [funções](role-based-access-control.md) e [perfis](device-profile-assign.md).
