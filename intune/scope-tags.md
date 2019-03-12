---
title: Filtrar políticas com etiquetas de âmbito no Microsoft Intune – Azure | Microsoft Docs
description: Utilize etiquetas de âmbito para filtrar perfis de configuração para funções específicas.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bca2d52bb47a149c6a36bc1b8cbc4d65e50c0f4c
ms.sourcegitcommit: 3abc3bb93a95a81154146325c26c119a784e7487
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/11/2019
ms.locfileid: "57756807"
---
# <a name="use-rbac-and-scope-tags-for-distributed-it"></a>Utilizar etiquetas de âmbito e o RBAC para distribuído IT

Pode utilizar o controlo de acesso baseado em funções (RBAC) e etiquetas de âmbito para se certificar de que os administradores da direita tem o acesso correto e a visibilidade dos objetos certo do Intune. Funções de determinam que acesso os administradores têm a quais objetos. Etiquetas de âmbito determinam quais os administradores podem ver os objetos.

Por exemplo, digamos que um administrador de escritório regional de Seattle é atribuído a função de política e o Gerenciador de perfis. Pretende que este administrador para ver e gerir apenas as políticas e perfis que só se aplicam a dispositivos de Seattle. Para fazer isso, seria:

1. Crie uma etiqueta de âmbito chamada Seattle.
2. Crie uma atribuição de função para a função de política e o Gerenciador de perfis com: 
    - Membros (grupos) = um grupo de segurança chamado administradores de TI de Seattle. Todos os administradores deste grupo terão permissão para gerir as políticas e perfis de utilizadores/dispositivos no âmbito (grupos).
    - Âmbito (grupos) = uma segurança grupo chamado Seattle utilizadores. Todos os utilizadores/dispositivos neste grupo pode ter seus perfis e políticas geridas pelos administradores em membros (grupos). 
    - Âmbito (etiquetas) = Seattle. Os administradores no membro (grupos) podem ver os dispositivos que também têm a etiqueta de âmbito de Seattle.
3. Adicione a etiqueta de âmbito de Seattle para políticas e perfis que pretende que os administradores de membros (grupos) para conseguir aceder.
4. Adicione a etiqueta de âmbito de Seattle para dispositivos que pretende que sejam visíveis para os administradores em membros (grupos). 


## <a name="to-create-a-scope-tag"></a>Para criar uma etiqueta de âmbito

1. No Intune, escolha **funções** > **âmbito (etiquetas)** > **criar**.

    ![Captura de ecrã de criar uma etiqueta de âmbito.](./media/scope-tags/create-scope-tag.png)

2. Forneça um **Nome** e uma **Descrição**.
3. Selecione **Criar**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Para atribuir uma etiqueta de âmbito a uma função

1. No Intune, escolha **funções** > **todas as funções** > Escolha uma função > **atribuições** > **atribuir**.

    ![Captura de ecrã de atribuir o âmbito a uma função.](./media/scope-tags/assign-scope-to-role.png)

2. Fornecer uma **nome da atribuição** e **Descrição**.
3. Escolher **membros (grupos)** > **Add** > Escolha os grupos que pretende como parte desta atribuição > **selecionar**  >   **OK**. mUsers deste grupo terão permissão para gerir as políticas e perfis de utilizadores/dispositivos no âmbito (grupos).

    ![Captura de ecrã dos grupos de seleção de membro.](./media/scope-tags/select-member-groups.png)

4. Se pretender gerir os utilizadores/dispositivos de um conjunto específico de grupos, escolha **âmbito (grupos)** > **grupos selecionados** > **selecionar grupos para incluir**> Escolha os grupos de > **selecionar** > **OK**. Todos os utilizadores/dispositivos neste grupo pode ter seus perfis e políticas geridas pelos administradores em membros (grupo).

    ![Captura de ecrã dos grupos de âmbito selecione.](./media/scope-tags/select-scope-groups.png)

    Em alternativa, pode escolher **todos os dispositivos**, **todos os utilizadores**, ou **todos os utilizadores e todos os dispositivos**.

    ![Captura de ecrã de outras opções para grupos de âmbito selecione.](./media/scope-tags/scope-group-other-options.png)
    
5. Escolher **âmbito (etiquetas)** > **Add** > Escolha as etiquetas que pretende adicionar a esta função > **selecionar** > **OK**. Utilizadores membros (grupos) têm acesso às políticas e perfis que também têm a mesma etiqueta de âmbito.

    ![Captura de ecrã de etiquetas de âmbito selecione.](./media/scope-tags/select-scope-tags.png)

6. Escolha **OK**. 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Para adicionar uma etiqueta de âmbito a um perfil de configuração
1. No Intune, escolha **configuração do dispositivo** > **perfis** > Escolha um perfil.

    ![Captura de ecrã do perfil de select.](./media/scope-tags/choose-profile.png)

2. Escolher **propriedades** > **âmbito (etiquetas)** > **adicionar**.

    ![Captura de ecrã de adicionar etiquetas de âmbito.](./media/scope-tags/add-scope-tags.png)

3. Sob **selecionar etiquetas**, escolha as etiquetas que pretende adicionar ao perfil.
4. Escolher **selecionar** > **OK** > **guardar**.

## <a name="scope-tag-details"></a>Detalhes da etiqueta de âmbito
Ao trabalhar com etiquetas de âmbito, lembre-se estes detalhes:

- Atualmente, é possível atribuir etiquetas de âmbito para:
    - Atribuições de funções
    - Políticas de conformidade de dispositivo
    - Perfis de configuração de dispositivos
    - Cadências de atualizações do Windows 10
    - Dispositivos geridos
    - Aplicações
    - Políticas de configuração de aplicações – os dispositivos geridos
    - Scripts do PowerShell
    - Tokens DEP
- Quando um administrador cria um objeto no Intune, todas as etiquetas de âmbito atribuídas para cada administrador serão automaticamente atribuídas para o novo objeto.
- RBAC do Intune não se aplica a funções do Azure Active Directory. Por isso, as funções de administradores de serviço do Intune e os administradores globais têm acesso de administrador completo para o Intune, não importa o que eles têm de etiquetas de âmbito.
- Os administradores numa atribuição de função com etiquetas de âmbito também podem ver o Intune objetos com sem etiquetas de âmbito.
- Só pode atribuir uma etiqueta de âmbito que tiver no seu atribuições de funções.
- Pode apenas os grupos de destino que estão listados no âmbito (grupos) da sua atribuição de função.
- Se tiver uma etiqueta de âmbito atribuída à sua função, não é possível eliminar todas as etiquetas de âmbito de um objeto do Intune. Etiqueta de pelo menos um âmbito é necessária.
- Se um utilizador tiver várias atribuições de funções, permissões nessas atribuições de funções de expandir a diferentes objetos da seguinte forma:
    - Atribuir permissões só se aplicam aos objetos (como as políticas ou aplicações) na atribuição dessa função âmbito (grupos). Atribuir permissões não se aplicam a objetos em outras atribuições de funções, a menos que a atribuição de outra especificamente concede-los.
    - São aplicáveis outras permissões (como criar e leitura), a todos os objetos do mesmo tipo (como todas as políticas ou todas as aplicações) em qualquer uma das atribuições do utilizador.
    - Permissões para objetos de diferentes tipos (como as políticas ou aplicações), não se aplicam entre si. Por exemplo, uma permissão de leitura para uma política, não fornece uma permissão de leitura às aplicações em atribuições do utilizador.





## <a name="next-steps"></a>Passos Seguintes

Efetue a gestão das suas [funções](role-based-access-control.md) e [perfis](device-profile-assign.md).
