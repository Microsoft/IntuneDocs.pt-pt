---
title: Controlo de acesso baseado em funções (RBAC) com o Microsoft Intune
description: Saiba como RBAC permite-lhe controlar quem pode realizar ações e fazer alterações no Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b711da0cb8bceb3273215a41e75a5180e957fb4
ms.sourcegitcommit: 0adb41c0640743d5cb726e66ad2427e3ad6faf20
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658561"
---
# <a name="role-based-access-control-rbac-with-microsoft-intune"></a>Controlo de acesso baseado em funções (RBAC) com o Microsoft Intune

Controlo de acesso baseado em funções (RBAC) ajuda-o a gerir quem tem acesso a recursos da sua organização e o que podem fazer com esses recursos.  Por [atribuir funções de](assign-role.md) aos seus utilizadores do Intune, pode limitar o que eles possam ver e alterar. Cada função tem um conjunto de permissões que determinam o que os utilizadores com essa função podem aceder e a alteração na sua organização.

Para criar, editar ou atribuir funções, a sua conta tem de ter uma das seguintes permissões no Azure AD:
- **Administrador Global**
- **Administrador de Serviços do Intune**

## <a name="roles"></a>Funções
Uma função define o conjunto de permissões concedido aos utilizadores atribuídos a essa função.
Pode utilizar ambas as funções incorporadas e personalizadas. Funções incorporadas abrangem alguns cenários comuns do Intune. Pode [criar suas próprias funções personalizadas](create-custom-role.md) com o conjunto exato de permissões de que precisa. Várias funções do Azure Active Directory tem permissões para o Intune.
Para ver uma função, escolha **Intune** > **funções** > **todas as funções** > Escolha uma função. Verá as seguintes páginas:

-   **Propriedades**: O nome, descrição, tipo, as atribuições e etiquetas de âmbito para a função. 
-   **Permissões**: Indica um conjunto muito de definir quais as permissões que a função tem de botões de alternar.
-   **Atribuições de**: Uma lista de [atribuições de funções]( assign-role.md) definir quais usuários têm acesso para que os utilizadores/dispositivos. Uma função pode ter várias atribuições e um utilizador pode ser em várias atribuições.

### <a name="built-in-roles"></a>Funções incorporadas
Pode atribuir funções incorporadas para grupos sem configuração adicional. Não é possível eliminar ou editar o nome, descrição, tipo ou permissões de uma função incorporada. Para obter uma lista completa das permissões para cada função incorporada, consulte a [tabela RBAC do Intune] ((https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a).

- **Operador do suporte técnico**: Executa tarefas remotas em utilizadores e dispositivos e pode atribuir políticas ou aplicações a utilizadores ou dispositivos.
- **Política e o Gerenciador de perfis**: Gere a política de conformidade, perfis de configuração, inscrição da Apple, identificadores de dispositivo da empresa e linhas de base de segurança.
- **Operador só de leitura**: Utilizador de vistas, dispositivo, inscrição, configuração e informações sobre a aplicação. Não é possível efetuar alterações ao Intune.
- **Gerenciador de aplicativos**: Gere aplicações móveis e geridas, pode ler as informações do dispositivo e pode ver os perfis de configuração do dispositivo.
- **Administrador de função do Intune**: Gere funções personalizadas do Intune e adiciona as atribuições de funções incorporadas do Intune. É a única função do Intune que pode atribuir permissões a administradores.
- **Administrador de escola**: Gere a dispositivos Windows 10 no [o Intune for Education](introduction-intune-education.md).

### <a name="custom-roles"></a>Funções personalizadas
Pode criar suas próprias funções com permissões personalizadas. Para obter mais informações sobre funções personalizadas, consulte [criar uma função personalizada](create-custom-role.md).

### <a name="azure-active-directory-roles-with-intune-access"></a>Funções do Active Directory do Azure com o acesso do Intune
| Função do Azure Active Directory | Todos os dados do Intune | Dados de auditoria do Intune |
| --- | :---: | :---: |
| Administrador Global | Leitura/escrita | Leitura/escrita |
| Administrador de Serviços do Intune | Leitura/escrita | Leitura/escrita |
| Administrador de Acesso Condicional | Nenhum | Nenhum |
| Administrador de Segurança | Só de leitura | Só de leitura |
| Operador de segurança | Só de leitura | Só de leitura |
| Leitor de segurança | Só de leitura | Só de leitura |
| Leitor global | Só de leitura | Só de leitura |
| Administrador de conformidade | Nenhum | Só de leitura |
| Administrador de dados de conformidade | Nenhum | Só de leitura |

> [!TIP]
> O Intune também mostra três extensões do Azure AD: **Os utilizadores**, **grupos**, e **acesso condicional**, que são controladas através do RBAC do Azure AD. Além disso, o **Administrador da Conta de Utilizador** só executa as atividades do utilizador/grupo do AAD e não tem permissões completas para executar todas as atividades no Intune. Para obter mais informações, consulte [RBAC com o Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles).
### <a name="roles-created-in-the-intune-classic-portal"></a>Funções criadas no portal clássico do Intune
Apenas os utilizadores **Administradores de Serviços** do Intune com permissões “Completas” são migrados do portal clássico do Intune para o Intune no portal do Azure. Tem a reatribuir o Intune **os administradores de serviços** os utilizadores com "Só de leitura" ou "Suporte técnico" acesso para as funções do Intune no portal do Azure e removê-los no portal clássico.
> [!IMPORTANT]
> Poderá ter de manter o acesso de administrador de serviço do Intune no portal clássico se os seus administradores ainda precisarem de acesso para gerir PCs com o Intune.

## <a name="role-assignments"></a>Atribuições de funções
Define uma atribuição de função:

- os utilizadores que estão atribuídos à função
- que recursos podem ver
- que recursos podem alterar.

Pode atribuir funções personalizadas e incorporadas aos seus utilizadores. A ser atribuída uma função do Intune, o utilizador tem de ter uma licença do Intune.
Para ver uma atribuição de função, escolha **Intune** > **funções** > **todas as funções** > Escolha uma função > Escolha uma atribuição. Verá as seguintes páginas:

-   **Propriedades**: O nome, descrição, função, membros, âmbitos e as etiquetas da atribuição.
-   **Membros**: Todos os utilizadores em grupos listados tem permissão para gerir os utilizadores/dispositivos que estão listados no âmbito (grupos).
-   **Âmbito (grupos)**: Todos os utilizadores/dispositivos nestes grupos podem ser geridos pelos utilizadores nos membros.
-   **[Âmbito (etiquetas)](scope-tags.md)**: Os utilizadores em membros podem ver os recursos que têm o mesmo âmbito.

### <a name="multiple-role-assignments"></a>Várias atribuições de funções
Se um utilizador tiver várias atribuições de funções, permissões nessas atribuições de funções de expandir a diferentes objetos da seguinte forma:

- Atribuir permissões só se aplicam aos objetos (como as políticas ou aplicações) na atribuição dessa função âmbito (grupos). Atribuir permissões não se aplicam a objetos em outras atribuições de funções, a menos que a atribuição de outra especificamente concede-los.
- São aplicáveis outras permissões (como criar e leitura), a todos os objetos do mesmo tipo (como todas as políticas ou todas as aplicações) em qualquer uma das atribuições do utilizador.
- Permissões para objetos de diferentes tipos (como as políticas ou aplicações), não se aplicam entre si. Por exemplo, uma permissão de leitura para uma política, não fornece uma permissão de leitura às aplicações em atribuições do utilizador.

## <a name="next-steps"></a>Passos Seguintes
- [Atribuir uma função a um utilizador](assign-role.md)
- [Criar uma função personalizada](create-custom-role.md)
