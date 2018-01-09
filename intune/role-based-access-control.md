---
title: RBAC com o Intune
titleSuffix: Azure portal
description: "Pré-visualização do Azure no Intune: saiba como o RBAC lhe permite controlar quem pode realizar ações e fazer alterações."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e33ee50ea7973a2ea2cf71c06255d99e1bc48f45
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/30/2017
---
# <a name="role-based-administration-control-rbac-with-intune"></a>Controlo de administração baseada em funções (RBAC) com o Intune

O RBAC ajuda-o a controlar quem pode executar várias tarefas do Intune na sua organização e a quem se aplicam essas tarefas. Pode utilizar as funções incorporadas que abrangem alguns cenários comuns do Intune ou pode criar as suas próprias funções. Uma função é definida por:

- **Definição de função**: o nome de uma função, os recursos que gere e as permissões concedidas a cada recurso.
- **Membros**: os grupos de utilizadores aos quais são concedidas as permissões.
- **Âmbito**: os grupos de utilizadores ou dispositivos que os membros podem gerir.
- **Atribuição**: após a configuração da definição, dos membros e do âmbito, a função é atribuída.

![Exemplo de RBAC do Intune](./media/intune-rbac-1.PNG)

Com o novo portal do Azure, o **Azure Active Directory (Azure AD)** fornece duas Funções de Diretório que podem ser utilizadas com o Intune. A estas funções é concedida uma permissão total para realizar todas as atividades no Intune:

- **Administrador Global:** os utilizadores com esta função têm acesso a todas as funcionalidades administrativas no Azure AD, bem como a serviços que federam para o Azure AD como o Exchange Online, o SharePoint Online e o Skype para Empresas Online. A pessoa que se inscreve no inquilino do Azure AD torna-se um administrador global. Apenas os administradores globais podem atribuir outras funções de administradores do Azure AD. Pode existir mais de um administrador global na sua organização. Os administradores globais podem redefinir a palavra-passe para qualquer utilizador e todos os outros administradores.

- **Administrador de Serviço do Intune:** os utilizadores com esta função têm permissões globais no Intune quando o serviço está presente. Adicionalmente, além das restrições de substituição do Azure, esta função permite gerir utilizadores e dispositivos, assim como criar e gerir grupos do Intune.

- **Administrador de Acesso Condicional:** os utilizadores com esta função só têm permissões para ver, criar, modificar e eliminar políticas de acesso condicional.

    > [!IMPORTANT]
    > A função Administrador de Serviço do Intune não permite gerir configurações de acesso condicional do Azure AD.

    > [!TIP]
    > O Intune também mostra três extensões do Azure AD: **Utilizadores**, **Grupos** e **Acesso condicional** que são controladas através do RBAC do Azure AD. Além disso, o **Administrador da Conta de Utilizador** só executa as atividades do utilizador/grupo do AAD e não tem permissões completas para executar todas as atividades no Intune. Para obter mais detalhes, veja [RBAC com o Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles).

## <a name="roles-created-in-the-intune-classic-portal"></a>Funções criadas no portal clássico do Intune

Apenas os utilizadores **Administradores de Serviços** do Intune com permissões “Completas” são migrados do portal clássico do Intune para o Intune no portal do Azure. Precisa de reatribuir os utilizadores **Administradores de Serviço** com acesso “Só de leitura” ou “Suporte técnico” nas funções de Intune do portal do Azure e removê-los do portal clássico.

> [!IMPORTANT]
> Talvez seja necessário manter o acesso de Administrador de Serviços do Intune no portal clássico se os seus administradores ainda precisarem de acesso para gerir PCs com o Intune.

## <a name="built-in-roles"></a>Funções incorporadas

As seguintes funções estão incorporadas no Intune e pode atribuí-las a grupos sem qualquer configuração adicional:

- **Operador do Suporte Técnico**: executa tarefas remotas em utilizadores e dispositivos e pode atribuir políticas ou aplicações a utilizadores ou dispositivos.
- **Gestor de Políticas e Perfis**: gere a política de conformidade, perfis de configuração, inscrição da Apple e identificadores de dispositivos empresariais.
- **Operador Só de Leitura**: vê as informações do utilizador, do dispositivo, da inscrição, da configuração e da aplicação. Não pode fazer alterações ao Intune.
- **Gestor de Aplicações**: gere aplicações móveis e geridas e pode ler as informações do dispositivo.

### <a name="to-assign-a-built-in-role"></a>Para atribuir uma função incorporada

1. Nas **Funções do Intune**, escolha a função incorporada que quer atribuir.

2. No painel <*nome da função*> – **Propriedades**, escolha **Gerir** e, em seguida, **Atribuições**.

    > [!NOTE]
    > Não pode eliminar ou editar funções incorporadas

3. No painel de função personalizada, escolha **Atribuir**.

4. No painel **Atribuições de Função**, introduza um **Nome** e uma **Descrição** opcional para a atribuição e, em seguida, escolha o seguinte:
    - **Membros** – Selecione um grupo que inclua o utilizador ao qual pretende conceder as permissões.
    - **Âmbito** – Selecione um grupo que inclua os utilizadores que o membro acima terá permissão para gerir.
<br></br>
5. Quando tiver terminado, clique em **OK**. A nova atribuição é apresentada na lista de atribuições.

### <a name="intune-rbac-table"></a>Tabela de RBAC do Intune

- Transfira a [tabela de RBAC do Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) para ver mais detalhes sobre o que cada função pode fazer.

## <a name="custom-roles"></a>Funções personalizadas

Pode criar uma função personalizada que inclui todas as permissões necessárias para uma função de tarefa específica. Por exemplo, se um grupo do departamento de TI gerir aplicações, políticas e perfis de configuração, pode juntar todas essas permissões numa só função personalizada.

> [!IMPORTANT]
> Para criar, editar ou atribuir funções, a sua conta tem de ter uma das seguintes permissões no Azure AD:
> - **Administrador Global**
> - **Administrador de Serviços do Intune**

### <a name="to-create-a-custom-role"></a>Para criar uma função personalizada

1. Inicie sessão no [portal do Azure](https://portal.azure.com) com as suas credenciais do Intune.

2. Selecione **Mais serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3. Escolha **Intune** e, quando o Dashboard do Intune for apresentado, escolha **Funções do Intune**.

4. No painel **Funções do Intune**, escolha **Funções do Intune** e, em seguida, **Adicionar personalizada**.

5. No painel **Adicionar Função Personalizada**, introduza um nome e uma descrição para a nova função e, em seguida, clique em **Permissões**.

3. No painel **Permissões**, escolha as permissões que quer utilizar com esta função. Utilize a [Tabela de RBAC do Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) para ajudá-lo a decidir quais as permissões que quer aplicar.

4. Quando tiver terminado, escolha **OK**.

5. No painel **Adicionar Função Personalizada**, clique em **Criar**. A nova função é apresentada na lista no painel **Funções do Intune**.

### <a name="to-assign-a-custom-role"></a>Para atribuir uma função personalizada

1. Nas **Funções do Intune**, escolha a função personalizada que quer atribuir.

2. No painel <*nome da função*> – **Propriedades**, escolha **Gerir** e, em seguida, **Atribuições**. Neste painel, também pode editar ou eliminar funções existentes.

3. No painel de função personalizada, escolha **Atribuir**.

4. No painel **Atribuições de Função**, introduza um **Nome** e uma **Descrição** opcional para a atribuição e, em seguida, escolha o seguinte:
    - **Membros** – Selecione um grupo que inclua o utilizador ao qual pretende conceder as permissões.
    - **Âmbito** – Selecione um grupo que inclua os utilizadores que o membro acima terá permissão para gerir.
<br></br>
5. Quando tiver terminado, clique em **OK**. A nova atribuição é apresentada na lista de atribuições.

## <a name="next-steps"></a>Próximos passos

[Utilizar a função de operador do Suporte Técnico do Intune com o portal de resolução de problemas](help-desk-operators.md)

## <a name="see-also"></a>Consulte também

[Assign roles using Azure AD (Atribuir funções através do Azure AD)](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)
