---
title: RBAC com o Microsoft Intune
description: Saiba como o Controlo de Acesso Baseado em Funções (RBAC) lhe permite controlar quem efetua ações e alterações no Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a57dca7f6b817177cbd131e969c1b5aa52a248a8
ms.sourcegitcommit: e0374b3ced83c8876a4f78b326869c10588a55e5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56307775"
---
# <a name="role-based-administration-control-rbac-with-microsoft-intune"></a>Controlo de acesso baseado em funções (RBAC) com o Microsoft Intune

O RBAC ajuda-o a controlar quem pode executar várias tarefas do Intune na sua organização e a quem se aplicam essas tarefas. Pode utilizar as funções incorporadas que abrangem alguns cenários comuns do Intune ou pode criar as suas próprias funções. Uma função é definida por:

- **Definição de função**: O nome de uma função, os recursos que gere e as permissões concedidas a cada recurso.
- **Membros**: Os grupos de utilizadores que são concedidos as permissões.
- **Âmbito (grupos)**: Os grupos de utilizadores ou dispositivos que os membros podem gerir.
- **[Âmbito (etiquetas)](https://docs.microsoft.com/intune/scope-tags)**: As etiquetas em que se aplique a atribuição de função.
- **Atribuição**: Quando a definição, os membros e âmbito tenham sido configurados, a função é atribuída.

![Exemplo de RBAC do Intune](./media/intune-rbac-1.PNG)

Com o novo portal do Azure, o **Azure Active Directory (Azure AD)** fornece duas Funções de Diretório que podem ser utilizadas com o Intune. A estas funções é concedida uma permissão total para realizar todas as atividades no Intune:

- **Administrador global:** Os utilizadores com esta função têm acesso a todas as funcionalidades administrativas no Azure AD, bem como serviços que federam para o Azure AD como o Exchange Online, SharePoint Online e Skype para empresas Online. A pessoa que se inscreve no inquilino do Azure AD torna-se um administrador global. Apenas os administradores globais podem atribuir outras funções de administradores do Azure AD. Pode existir mais de um administrador global na sua organização. Os administradores globais podem redefinir a palavra-passe para qualquer utilizador e todos os outros administradores.

- **Administrador de serviço do Intune:** Os utilizadores com esta função possuem permissões globais no Intune quando o serviço está presente. Adicionalmente, além das restrições de substituição do Azure, esta função permite gerir utilizadores e dispositivos, assim como criar e gerir grupos do Intune.

- **Administrador de acesso condicional:** Os utilizadores com esta função só têm permissões para ver, criar, modificar e eliminar políticas de acesso condicional.

    > [!IMPORTANT]
    > A função Administrador de Serviço do Intune não permite gerir configurações de acesso condicional do Azure AD.
    > A ser atribuída uma função do Intune, o utilizador tem de ter uma licença do Intune.

    > [!TIP]
    > O Intune também mostra três extensões do Azure AD: **Os utilizadores**, **grupos**, e **acesso condicional**, que são controladas através do RBAC do Azure AD. Além disso, o **Administrador da Conta de Utilizador** só executa as atividades do utilizador/grupo do AAD e não tem permissões completas para executar todas as atividades no Intune. Para obter mais informações, consulte [RBAC com o Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles).

## <a name="roles-created-in-the-intune-classic-portal"></a>Funções criadas no portal clássico do Intune

Apenas os utilizadores **Administradores de Serviços** do Intune com permissões “Completas” são migrados do portal clássico do Intune para o Intune no portal do Azure. Tem a reatribuir o Intune **os administradores de serviços** os utilizadores com "Só de leitura" ou "Suporte técnico" acesso para as funções do Intune no portal do Azure e removê-los no portal clássico.

> [!IMPORTANT]
> Poderá ter de manter o acesso de administrador de serviço do Intune no portal clássico se os seus administradores ainda precisarem de acesso para gerir PCs com o Intune.

## <a name="built-in-roles"></a>Funções incorporadas

Pode atribuir funções incorporadas para grupos sem configuração adicional. Não é possível eliminar ou editar uma função incorporada.

- **Operador do suporte técnico**: Executa tarefas remotas em utilizadores e dispositivos e pode atribuir políticas ou aplicações a utilizadores ou dispositivos.
- **Política e o Gerenciador de perfis**: Gere a política de conformidade, perfis de configuração, inscrição da Apple e identificadores de dispositivo da empresa.
- **Operador só de leitura**: Utilizador de vistas, dispositivo, inscrição, configuração e informações sobre a aplicação. Não é possível efetuar alterações ao Intune.
- **Gerenciador de aplicativos**: Gere aplicações móveis e geridas, pode ler as informações do dispositivo e pode ver os perfis de configuração do dispositivo.
- **Administrador de função do Intune**: Gere funções personalizadas do Intune e adiciona as atribuições de funções incorporadas do Intune. É a única função do Intune que pode atribuir permissões a administradores.
- **Administrador de escola**: Gere a dispositivos Windows 10 no [o Intune for Education](introduction-intune-education.md)e pode efetuar as seguintes ações: 

    |Permissão|Operação|
    |---|---|
    |Dados da Auditoria|Leitura|
    |Configurações dos Dispositivos|Atribuir, Criar, Eliminar, Ler, Atualizar|
    |Gestores de Inscrição de Dispositivos|Ler, Atualizar|
    |Dispositivos Geridos|Ler, Atualizar<!--, Delete [To be added in 1803]-->|
    |Aplicações móveis|Atribuir, Criar, Eliminar, Ler, Atualizar|
    |Relatórios|Leitura|
    |Ações Remotas|Limpar o PC, Reiniciar, Bloqueio Remoto, Extinguir, Sincronizar Dispositivos, Eliminação|
    |Organização|Leitura|

### <a name="to-assign-a-built-in-role"></a>Para atribuir uma função incorporada

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Sobre o **Intune** painel, escolha **funções** > **todas as funções**.
4. Sobre o **funções do Intune – todas as funções** painel, selecione a função incorporada que pretende atribuir.

5. Na <*nome da função*>- **descrição geral** painel, escolha **gerir** > **atribuições**.

6. No painel de função personalizada, escolha **Atribuir**.

7. Na **atribuições de funções** painel, introduza um **nome da atribuição** e opcionais **descrição da atribuição** para a atribuição.

8. Para **membros (grupos)**, escolha um grupo que contém o usuário quer conceder as permissões.

9. Para **âmbito (grupos)**, escolha um grupo que contém os utilizadores que o membro acima terá permissão para gerir.

10. Para **âmbito (etiquetas)**, escolha as etiquetas em que esta atribuição de função será aplicada.

11. Quando tiver terminado, selecione **OK**. A nova atribuição é apresentada na lista de atribuições.

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

3. Escolher **Intune** > **funções** > **todas as funções** > **adicionar**.

4. No painel **Adicionar Função Personalizada**, introduza um nome e uma descrição para a nova função e, em seguida, clique em **Permissões**.

5. No painel **Permissões**, escolha as permissões que quer utilizar com esta função. Utilize a [Tabela de RBAC do Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) para ajudá-lo a decidir quais as permissões que quer aplicar.

6. Sobre o **âmbito (etiquetas)** painel, escolha as etiquetas em que será aplicada esta função personalizada.

7. Quando tiver terminado, selecione **OK**.

7. No painel **Adicionar Função Personalizada**, clique em **Criar**. A nova função é apresentada na lista no **funções do Intune – todas as funções** painel.

### <a name="to-assign-a-custom-role"></a>Para atribuir uma função personalizada

Siga os mesmos passos [para atribuir uma função incorporada](https://docs.microsoft.com/intune/role-based-access-control#to-assign-a-built-in-role) e selecione a função personalizada.

## <a name="next-steps"></a>Passos Seguintes

[Utilizar a função de operador do Suporte Técnico do Intune com o portal de resolução de problemas](help-desk-operators.md)

## <a name="see-also"></a>Consulte também

[Assign roles using Azure AD (Atribuir funções através do Azure AD)](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)
