---
title: Utilize o controlo de acesso baseado em funções (RBAC) e as etiquetas de âmbito para TI distribuídos no Intune ; Microsoft Docs
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
ms.openlocfilehash: dfb9ec9d28b00e454884bbf0bf296cd72cba4b6f
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369799"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Utilizar o controlo de acesso baseado em funções (RBAC) e etiquetas de âmbito para TI distribuídos

Pode utilizar etiquetas de controlo de acesso e de alcance baseadas em papéis para se certificar de que os administradores certos têm o acesso e visibilidade certos aos objetos Intune certos. As funções determinam quais os administradores de acesso a que objetos. As etiquetas de âmbito determinam quais os objetos que os administradores podem ver.

Por exemplo, digamos que um administrador regional de Seattle tem o papel de Policy and Profile Manager. Quer que este administrador veja e gere apenas os perfis e políticas que se aplicam apenas aos dispositivos de Seattle. Para configurar este acesso, seria:

1. Crie uma etiqueta chamada Seattle.
2. Criar uma atribuição de funções para o papel de Gestor de Política e Perfil com: 
    - Membros (Grupos) = Um grupo de segurança chamado Seattle IT administradores. Todos os administradores deste grupo terão permissão para gerir políticas e perfis para utilizadores/dispositivos no Âmbito (Grupos).
    - Âmbito (Grupos) = Um grupo de segurança chamado utilizadores de Seattle. Todos os utilizadores/dispositivos deste grupo podem ter os seus perfis e políticas geridos pelos administradores dos Membros (Grupos). 
    - Âmbito (Tags) = Seattle. Os administradores dos membros (Grupos) podem ver objetos Intune que também têm a etiqueta de âmbito de Seattle.
3. Adicione a etiqueta de âmbito de Seattle às políticas e perfis a que pretende que os administradores dos Deputados (Grupos) tenham acesso.
4. Adicione a etiqueta de âmbito de Seattle aos dispositivos que pretende visíveis para administradores nos Membros (Grupos). 

## <a name="default-scope-tag"></a>Etiqueta de âmbito padrão
A etiqueta de âmbito predefinido é adicionada automaticamente a todos os objetos não marcados que suportam etiquetas de âmbito.

A função de etiqueta de âmbito padrão é semelhante à funcionalidade de âmbitos de segurança no Microsoft Endpoint Configuration Manager. 

## <a name="to-create-a-scope-tag"></a>Para criar uma etiqueta de âmbito

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha a **administração do Inquilino** > **Funções** > **Scope (Tags)**  > **Criar**.
2. Na página **Basics,** forneça um **Nome** e **uma Descrição**opcional. Selecione **Next**.
3. Na página **de Atribuição,** escolha os grupos que contêm os dispositivos que pretende atribuir esta etiqueta de âmbito. Selecione **Next**.
4. Na **página Review + criar,** escolha **Criar**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Para atribuir uma etiqueta de âmbito a uma função

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha a **administração do Inquilino** > **Papéis** > **Todas as funções** > escolha um papel > **Atribuições** > **Atribuição**.
2. Na página **Basics,** forneça um nome de **atribuição** e **descrição.** Selecione **Next**.
3. Na página dos **Grupos De Administração,** escolha **grupos Select para incluir**, e selecione os grupos que deseja como parte desta atribuição. Os utilizadores deste grupo terão permissões para gerir utilizadores/dispositivos no Âmbito (Grupos). Selecione **Next**.

    ![Screenshot de grupos membros selecionados.](./media/scope-tags/select-member-groups.png)

4. Na página dos **Grupos de Âmbito,** selecione uma das seguintes opções para **Atribuir**
    - **Grupos selecionados**: selecione os grupos que contêm os utilizadores/deivces que pretende gerir. Todos os utilizadores/dispositivos dos grupos selecionados serão geridos pelos utilizadores nos Grupos DeAdministração.
    - **Todos os utilizadores**: Todos os utilizadores podem ser geridos pelos utilizadores nos Grupos De Administração.
    - **Todos os dispositivos**: Todos os dispositivos podem ser geridos pelos utilizadores nos Grupos De Administração.
    - **Todos os utilizadores e todos os dispositivos**: Todos os utilizadores e dispositivos podem ser geridos pelos utilizadores nos Grupos Admin.

5. Escolha **Seguinte**
6. Na página **de tags Scope,** selecione as etiquetas que pretende adicionar a esta função. Os utilizadores dos Grupos Admin terão acesso a objetos Intune que também tenham a mesma etiqueta de âmbito.
7. Escolha **O Próximo** para ir à página Review + **criar** e, em seguida, escolher **Criar**.

## <a name="assign-scope-tags-to-other-objects"></a>Atribuir etiquetas de âmbito a outros objetos

Para objetos que suportam etiquetas de mira, as etiquetas de âmbito geralmente aparecem em **Propriedades**. Por exemplo, para atribuir uma etiqueta de âmbito a um perfil de configuração, siga estes passos:

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **Dispositivos** > Perfis de **Configuração** > escolha um perfil.

2. Escolha **Propriedades** > **Scope (Tags)**  > **Editar** > **Selecione etiquetas** de âmbito > escolha as etiquetas que pretende adicionar ao perfil.
4. Escolha **Selecione** > **Rever + guardar**.

## <a name="scope-tag-details"></a>Detalhes da etiqueta de âmbito
Ao trabalhar com etiquetas de âmbito, lembre-se destes detalhes: 

- Pode atribuir etiquetas de âmbito a um tipo de objeto Intune se o inquilino puder ter várias versões desse objeto (tais como atribuições de papéis ou apps).
  Os seguintes objetos Intune são exceções a esta regra e não suportam atualmente etiquetas de âmbito:
    - Perfis ESP do Windows
    - Categorias de Dispositivos
    - Restrições de Inscrição
    - Identificadores de dispositivos corp
    - Dispositivos de piloto automático
    - Localizações de conformidade do dispositivo
    - Dispositivos Jamf
- As aplicações vPP e os ebooks associados ao símbolo VPP herdam as etiquetas de âmbito atribuídas ao token VPP associado.
- Os dispositivos do Programa de Inscrição de Dispositivos (DEP) e os perfis DEP associados ao token DEP herdam as etiquetas de âmbito atribuídas ao símbolo de DEP associado.
- Quando um administrador criar um objeto em Intune, todas as etiquetas de âmbito atribuídas a esse administrador serão automaticamente atribuídas ao novo objeto.
- Intune RBAC não se aplica às funções de Diretório Ativo Azure. Assim, as funções intune Service Admins e Global Admins têm acesso total à Intune, independentemente do alcance que tenham.
- Se uma atribuição de funções não tiver etiqueta de âmbito, essa administração de TI pode ver todos os objetos com base nas permissões de administração de TI. Os administradores que não têm etiquetas de âmbito têm essencialmente todas as etiquetas de âmbito.
- Só pode atribuir uma etiqueta de âmbito que tem nas suas atribuições de funções.
- Só pode visar grupos listados no Scope (Grupos) da sua atribuição de funções.
- Se tiver uma etiqueta de âmbito atribuída ao seu papel, não pode eliminar todas as etiquetas de âmbito num objeto Intune. Pelo menos uma etiqueta de mira é necessária.

## <a name="next-steps"></a>Passos Seguintes

Saiba como as etiquetas de alcance se comportam quando existem [várias atribuições de papéis.](role-based-access-control.md#multiple-role-assignments)
Efetue a gestão das suas [funções](role-based-access-control.md) e [perfis](../configuration/device-profile-assign.md).


