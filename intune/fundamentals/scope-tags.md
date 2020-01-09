---
title: Usar o RBAC (controle de acesso baseado em função) e marcas de escopo para distribuí-lo no Intune | Microsoft Docs
description: Utilize etiquetas de âmbito para filtrar perfis de configuração para funções específicas.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.assetid: a21d3039-f2ed-4f43-b6fa-d00c071edbc4
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e1f81d26227bb206aa55ca495f4a4ee5e8ae9907
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548117"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Usar o controle de acesso baseado em função (RBAC) e marcas de escopo para distribuição de ti

Você pode usar o controle de acesso baseado em função e as marcas de escopo para garantir que os administradores corretos tenham o acesso e a visibilidade certos para os objetos do Intune corretos. As funções determinam quais administradores de acesso têm para quais objetos. As marcas de escopo determinam quais objetos os administradores podem ver.

Por exemplo, digamos que um administrador regional do Office de Seattle tenha a função gerente de política e perfil. Você deseja que esse administrador Veja e gerencie apenas os perfis e as políticas que se aplicam somente a dispositivos de Seattle. Para configurar esse acesso, você deve:

1. Crie uma marca de escopo chamada Seattle.
2. Crie uma atribuição de função para a função de Gerenciador de políticas e perfis com: 
    - Membros (grupos) = um grupo de segurança chamado Seattle IT admins. Todos os administradores deste grupo terão permissão para gerenciar políticas e perfis para usuários/dispositivos no escopo (grupos).
    - Escopo (grupos) = um grupo de segurança chamado usuários de Seattle. Todos os usuários/dispositivos nesse grupo podem ter seus perfis e políticas gerenciados pelos administradores nos Membros (grupos). 
    - Scope (Tags) = Seattle. Os administradores no membro (grupos) podem ver objetos do Intune que também têm a marca de escopo Seattle.
3. Adicione a marca de escopo Seattle a políticas e perfis aos quais você deseja que os administradores em Membros (grupos) tenham acesso.
4. Adicione a marca de escopo Seattle aos dispositivos que você deseja que fiquem visíveis para os administradores nos Membros (grupos). 

## <a name="default-scope-tag"></a>Marca de escopo padrão
A marca de escopo padrão é automaticamente adicionada a todos os objetos não marcados que dão suporte a marcas de escopo.

O recurso de marca de escopo padrão é semelhante ao recurso de escopos de segurança no Microsoft Endpoint Configuration Manager. 

## <a name="to-create-a-scope-tag"></a>Para criar uma etiqueta de âmbito

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **administração de locatário** > **funções** > **escopo (marcas)**  > **criar**.

    ![Captura de tela da criação de uma marca de escopo.](./media/scope-tags/create-scope-tag.png)

2. Forneça um **nome** e uma **Descrição**opcional.
3. Se você quiser todos os dispositivos em grupos específicos, escolha **atribuir marca de escopo a todos os dispositivos nos grupos selecionados**.
    1. Na página **Selecionar grupos a serem incluídos** , escolha os grupos que contêm os dispositivos aos quais você deseja atribuir essa marca de escopo.
    2. Clique em **Selecionar**.
4. Selecione **Criar**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Para atribuir uma etiqueta de âmbito a uma função

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **administração de locatário** > **funções** > **todas as funções** > escolha uma função > **atribuições** > **atribuir**.
2. Forneça um **nome de atribuição** e uma **Descrição**.
3. Escolha **Membros (grupos)**  > **Adicionar** > escolha os grupos que você deseja como parte dessa atribuição > **selecione** > **OK**. Os usuários nesse grupo terão permissões para gerenciar usuários/dispositivos no escopo (grupos).

    ![Captura de tela de selecionar grupos de membros.](./media/scope-tags/select-member-groups.png)

4. Se você quiser gerenciar usuários/dispositivos em um conjunto específico de grupos, escolha **escopo (grupos)**  > **grupos selecionados** > **selecione grupos para incluir** > escolha os grupos > **selecione** > **OK**. Todos os usuários/dispositivos nesse grupo serão gerenciados pelos administradores nos Membros (grupo).

    ![Captura de tela de selecionar grupos de escopo.](./media/scope-tags/select-scope-groups.png)

    Como alternativa, você pode escolher **todos os dispositivos**, **todos os usuários**ou todos os **usuários & todos os dispositivos**.

    ![Captura de tela de outras opções para selecionar grupos de escopo.](./media/scope-tags/scope-group-other-options.png)
    
5. Escolha **escopo (marcas)**  > **Adicionar** > escolha as marcas que você deseja adicionar a essa função > **selecione** > **OK**. Os usuários em Membros (grupos) terão acesso aos objetos do Intune que também têm a mesma marca de escopo.

    ![Captura de tela de selecionar marcas de escopo.](./media/scope-tags/select-scope-tags.png)

6. Escolha **OK**. 

## <a name="assign-scope-tags-to-other-objects"></a>Atribuir marcas de escopo a outros objetos

Para objetos que dão suporte a marcas de escopo, marcas de escopo geralmente aparecem em **Propriedades**. Por exemplo, para atribuir uma marca de escopo a um perfil de configuração, siga estas etapas:

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **perfis de configuração** > escolha um perfil.

2. Escolha **propriedades** > **escopo (marcas)**  > **Adicionar**.

    ![Captura de tela de adicionar marcas de escopo.](./media/scope-tags/add-scope-tags.png)

3. Em **selecionar marcas**, escolha as marcas que você deseja adicionar ao perfil.
4. Escolha **selecionar** > **OK** > **salvar**.


## <a name="scope-tag-details"></a>Detalhes da marca de escopo
Ao trabalhar com marcas de escopo, lembre-se destes detalhes: 

- Você pode atribuir marcas de escopo a um tipo de objeto do Intune se o locatário puder ter várias versões desse objeto (como atribuições de função ou aplicativos).
  Os seguintes objetos do Intune são exceções a essa regra e atualmente não dão suporte a marcas de escopo:
    - Perfis do Windows ESP
    - Categorias de dispositivo
    - Restrições de registro
    - Identificadores de dispositivo Corp
    - Dispositivos de piloto automático
    - Locais de conformidade do dispositivo
    - Dispositivos JAMF
- Os aplicativos VPP e os livros eletrônicos associados ao token VPP herdam as marcas de escopo atribuídas ao token VPP associado.
- Os dispositivos de Programa de registro de dispositivos (DEP) e os perfis de DEP associados ao token DEP herdam as marcas de escopo atribuídas ao token DEP associado.
- Quando um administrador cria um objeto no Intune, todas as marcas de escopo atribuídas a esse administrador serão automaticamente atribuídas ao novo objeto.
- O RBAC do Intune não se aplica a Azure Active Directory funções. Portanto, as funções Administradores de serviço do Intune e administradores globais têm acesso de administrador completo ao Intune, independentemente das marcas de escopo que têm.
- Se uma atribuição de função não tiver nenhuma marca de escopo, o administrador de ti poderá ver todos os objetos com base nas permissões de administradores de ti. Os administradores que não têm marcas de escopo essencialmente têm todas as marcas de escopo.
- Você só pode atribuir uma marca de escopo que você tem em suas atribuições de função.
- Você só pode direcionar grupos listados no escopo (grupos) de sua atribuição de função.
- Se você tiver uma marca de escopo atribuída à sua função, não poderá excluir todas as marcas de escopo em um objeto do Intune. Pelo menos uma marca de escopo é necessária.

## <a name="next-steps"></a>Próximos passos

Saiba como as marcas de escopo se comportam quando há [várias atribuições de função](role-based-access-control.md#multiple-role-assignments).
Efetue a gestão das suas [funções](role-based-access-control.md) e [perfis](../configuration/device-profile-assign.md).
