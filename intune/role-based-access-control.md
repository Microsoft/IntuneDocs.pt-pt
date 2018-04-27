---
title: RBAC com o Microsoft Intune
description: Saiba como o Controlo de Acesso Baseado em Funções (RBAC) lhe permite controlar quem efetua ações e alterações no Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 98355ec1cf54597f488bd2426ac77f35809070fd
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/26/2018
---
# <a name="role-based-administration-control-rbac-with-microsoft-intune"></a>Controlo de acesso baseado em funções (RBAC) com o Microsoft Intune

O RBAC ajuda-o a controlar quem pode executar várias tarefas do Intune na sua organização e a quem se aplicam essas tarefas. Pode utilizar as funções incorporadas que abrangem alguns cenários comuns do Intune ou pode criar as suas próprias funções. Uma função é definida por:

- **Definição de função**: o nome de uma função, os recursos que gere e as permissões concedidas a cada recurso.
- **Membros**: os grupos de utilizadores aos quais são concedidas as permissões.
- **Âmbito**: os grupos de utilizadores ou dispositivos que os membros podem direcionar para a implementação de políticas ou aplicações ou para efetuar tarefas remotas.
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
- **Administrador de Escola**: gere os dispositivos Windows 10 no [Intune for Education](introduction-intune-education.md) e pode efetuar as seguintes ações: 

|Permissão|Operação|
|---|---|
|Dados da Auditoria|Ler|
|Configurações dos Dispositivos|Atribuir, Criar, Eliminar, Ler, Atualizar|
|Gestores de Inscrição de Dispositivos|Ler, Atualizar|
|Dispositivos Geridos|Ler, Atualizar<!--, Delete [To be added in 1803]-->|
|Aplicações móveis|Atribuir, Criar, Eliminar, Ler, Atualizar|
|Relatórios|Ler|
|Ações Remotas|Limpar o PC, Reiniciar, Bloqueio Remoto, Extinguir, Sincronizar Dispositivos, Eliminação|
|Organização|Ler|

### <a name="to-assign-a-built-in-role"></a>Para atribuir uma função incorporada

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Funções do Intune** e, em seguida, **Todas as funções**.
1. No painel **Funções do Intune – Todas as funções**, selecione a função incorporada que pretende atribuir.

2. No painel <*nome da função*> – **Descrição Geral**, selecione **Gerir** e, em seguida, **Atribuições**.

    > [!NOTE]
    > Não pode eliminar ou editar funções incorporadas

3. No painel Função personalizada, selecione **Atribuir**.

4. No painel **Atribuições de Função**, introduza um **Nome** e uma **Descrição** opcional para a atribuição e, em seguida, selecione o seguinte:
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

2. Selecione **Todos os serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3. Escolha **Intune** e, quando o Dashboard do Intune for apresentado, escolha **Funções do Intune**.

4. No painel **Funções do Intune**, selecione **Todas as funções** e, em seguida, **Adicionar personalização**.

5. No painel **Adicionar Função Personalizada**, introduza um nome e uma descrição para a nova função e, em seguida, clique em **Permissões**.

3. No painel **Permissões**, selecione as permissões que quer utilizar com esta função. Utilize a [Tabela de RBAC do Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) para ajudá-lo a decidir quais as permissões que quer aplicar.

4. Quando tiver terminado, escolha **OK**.

5. No painel **Adicionar Função Personalizada**, clique em **Criar**. A nova função é apresentada na lista no painel **Funções do Intune – Todas as funções**.

### <a name="to-assign-a-custom-role"></a>Para atribuir uma função personalizada

1. No painel **Funções do Intune – Todas as funções**, selecione a função personalizada que pretende atribuir.

2. No painel <*nome da função*> – **Descrição Geral**, selecione **Gerir** e, em seguida, **Atribuições**. Neste painel, também pode editar ou eliminar funções existentes.

3. No painel Função personalizada, selecione **Atribuir**.

4. No painel **Atribuições de Função**, introduza um **Nome** e uma **Descrição** opcional para a atribuição e, em seguida, selecione o seguinte:
    - **Membros** – Selecione um grupo que inclua o utilizador ao qual pretende conceder as permissões.
    - **Âmbito** – Selecione um grupo que inclua os utilizadores que o membro acima terá permissão para gerir.
<br></br>
5. Quando tiver terminado, clique em **OK**. A nova atribuição é apresentada na lista de atribuições.

## <a name="next-steps"></a>Próximos passos

[Utilizar a função de operador do Suporte Técnico do Intune com o portal de resolução de problemas](help-desk-operators.md)

## <a name="see-also"></a>Consulte também

[Assign roles using Azure AD (Atribuir funções através do Azure AD)](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)
