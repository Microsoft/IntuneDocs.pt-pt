---
title: RBAC (controle de acesso baseado em função) com Microsoft Intune
description: Saiba como o RBAC permite controlar quem pode executar ações e fazer alterações em Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a5372d079b08a3a324d8ef1d98d26c07073ccd45
ms.sourcegitcommit: 49f25efb9bc0f16f587f27878cf45de5e4e6a27f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/18/2019
ms.locfileid: "71094669"
---
# <a name="role-based-access-control-rbac-with-microsoft-intune"></a>RBAC (controle de acesso baseado em função) com Microsoft Intune

O RBAC (controle de acesso baseado em função) ajuda você a gerenciar quem tem acesso aos recursos da sua organização e o que eles podem fazer com esses recursos.  Ao [atribuir funções](assign-role.md) aos usuários do Intune, você pode limitar o que eles podem ver e alterar. Cada função tem um conjunto de permissões que determinam o que os usuários com essa função podem acessar e alterar dentro de sua organização.

Para criar, editar ou atribuir funções, a sua conta tem de ter uma das seguintes permissões no Azure AD:
- **Administrador Global**
- **Administrador de serviços do Intune** (também conhecido como **administrador do Intune**)

Para obter conselhos e sugestões sobre o Intune RBAC, você pode conferir esta série de cinco vídeos que demonstram exemplos e orientações passo a passos: [1](https://www.youtube.com/watch?v=5deXLMLcnKY), [2](https://www.youtube.com/watch?v=38dnMBLuxbQ), [3](https://www.youtube.com/watch?v=6vqg9cAkMbY), [4](https://www.youtube.com/watch?v=5yOLajFFMHE), [5](https://www.youtube.com/watch?v=P5DDvsSF4Wk).

## <a name="roles"></a>Funções
Uma função define o conjunto de permissões concedidos aos usuários atribuídos a essa função.
Você pode usar as funções internas e personalizadas. As funções internas abrangem alguns cenários comuns do Intune. Você pode [criar suas próprias funções personalizadas](create-custom-role.md) com o conjunto exato de permissões necessárias. Várias funções Azure Active Directory têm permissões para o Intune.
Para ver uma função, escolha**funções** > do **Intune** > **todas as funções** > escolha uma função. Você verá as seguintes páginas:

- **Propriedades**: O nome, a descrição, o tipo, as atribuições e as marcas de escopo da função. 
- **Permissões**: Lista um longo conjunto de alternâncias que definem quais permissões a função tem.
- **Atribuições**: Uma lista de [atribuições de função]( assign-role.md) que definem quais usuários têm acesso a quais usuários/dispositivos. Uma função pode ter várias atribuições e um usuário pode estar em várias atribuições.

### <a name="built-in-roles"></a>Funções incorporadas
Você pode atribuir funções internas a grupos sem configuração adicional. Você não pode excluir ou editar o nome, a descrição, o tipo ou as permissões de uma função interna.

- **Operador de suporte técnico**: Executa tarefas remotas em usuários e dispositivos e pode atribuir aplicativos ou políticas a usuários ou dispositivos.
- **Gerenciador de políticas e perfis**: Gerencia política de conformidade, perfis de configuração, registro da Apple, identificadores de dispositivos corporativos e linhas de base de segurança.
- **Operador somente leitura**: Exibe informações de usuário, dispositivo, registro, configuração e aplicativo. Não é possível fazer alterações no Intune.
- **Gerenciador de aplicativos**: Gerencia aplicativos móveis e gerenciados, pode ler informações do dispositivo e exibir perfis de configuração do dispositivo.
- **Administrador de função do Intune**: Gerencia funções personalizadas do Intune e adiciona atribuições para funções internas do Intune. É a única função do Intune que pode atribuir permissões aos administradores.
- **Administrador escolar**: Gerencia dispositivos Windows 10 no [Intune para educação](introduction-intune-education.md).

### <a name="custom-roles"></a>Funções personalizadas
Você pode criar suas próprias funções com permissões personalizadas. Para obter mais informações sobre funções personalizadas, consulte [criar uma função personalizada](create-custom-role.md).

### <a name="azure-active-directory-roles-with-intune-access"></a>Azure Active Directory funções com acesso ao Intune
| Azure Active Directory função | Todos os dados do Intune | Dados de auditoria do Intune |
| --- | :---: | :---: |
| Administrador Global | Leitura/gravação | Leitura/gravação |
| Administrador de Serviços do Intune | Leitura/gravação | Leitura/gravação |
| Administrador de Acesso Condicional | Nenhum | Nenhum |
| Administrador de Segurança | Só de leitura | Só de leitura |
| Operador de segurança | Só de leitura | Só de leitura |
| Leitor de segurança | Só de leitura | Só de leitura |
| Administrador de conformidade | Nenhum | Só de leitura |
| Administrador de dados de conformidade | Nenhum | Só de leitura |

> [!TIP]
> O Intune também mostra três extensões do Azure AD: **Usuários**, **grupos**e **acesso condicional**, que são controlados usando o RBAC do Azure AD. Além disso, o **Administrador da Conta de Utilizador** só executa as atividades do utilizador/grupo do AAD e não tem permissões completas para executar todas as atividades no Intune. Para obter mais informações, consulte [RBAC com o Azure ad](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles).
### <a name="roles-created-in-the-intune-classic-portal"></a>Funções criadas no portal clássico do Intune
Apenas os utilizadores **Administradores de Serviços** do Intune com permissões “Completas” são migrados do portal clássico do Intune para o Intune no portal do Azure. Você deve reatribuir os usuários dos **Administradores de serviço** do Intune com acesso "somente leitura" ou "assistência técnica" às funções do Intune no portal do Azure e removê-los do portal clássico.
> [!IMPORTANT]
> Talvez seja necessário manter o acesso de administrador de serviços do Intune no portal clássico se os administradores ainda precisarem de acesso para gerenciar computadores usando o Intune.

## <a name="role-assignments"></a>Atribuições de função
Uma atribuição de função define:

- quais usuários são atribuídos à função
- quais recursos eles podem ver
- quais recursos eles podem alterar.

Você pode atribuir funções personalizadas e internas a seus usuários. Para receber uma função do Intune, o usuário deve ter uma licença do Intune.
Para ver uma atribuição de função, escolha**funções** > do **Intune** > **todas as funções** > escolha uma função > escolha uma atribuição. Você verá as seguintes páginas:

- **Propriedades**: O nome, a descrição, a função, os membros, os escopos e as marcas da atribuição.
- **Membros**: Todos os usuários nos grupos de segurança do Azure listados têm permissão para gerenciar os usuários/dispositivos listados em escopo (grupos).
- **Escopo (grupos)** : Todos os usuários/dispositivos nesses grupos de segurança do Azure podem ser gerenciados pelos usuários em membros.
- **[Escopo (marcas)](scope-tags.md)** : Os usuários em membros podem ver os recursos que têm as mesmas marcas de escopo.

### <a name="multiple-role-assignments"></a>Atribuições de função múltipla
Se um usuário tiver várias atribuições de função, permissões e marcas de escopo, essas atribuições de função se estenderão a objetos diferentes da seguinte maneira:

- Atribuir permissões e marcas de escopo somente se aplicam aos objetos (como políticas ou aplicativos) no escopo de atribuição dessa função (grupos). Atribuir permissões e marcas de escopo não se aplicam a objetos em outras atribuições de função, a menos que a outra atribuição os conceda especificamente.
- Outras permissões (como criar, ler, atualizar, excluir) e marcas de escopo se aplicam a todos os objetos do mesmo tipo (como todas as políticas ou todos os aplicativos) em qualquer uma das atribuições do usuário.
- Permissões e marcas de escopo para objetos de diferentes tipos (como políticas ou aplicativos), não se aplicam entre si. Uma permissão de leitura para uma política, por exemplo, não fornece uma permissão de leitura para aplicativos nas atribuições do usuário.

## <a name="next-steps"></a>Passos Seguintes
- [Atribuir uma função a um usuário](assign-role.md)
- [Criar uma função personalizada](create-custom-role.md)
