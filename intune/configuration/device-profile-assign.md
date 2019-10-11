---
title: Atribuir perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Use o portal do Azure para atribuir perfis de dispositivo e políticas a usuários e dispositivos. Saiba como excluir grupos de uma atribuição de perfil no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db1f0944a6725d1f361ea20c972d8ffa8f5d9035
ms.sourcegitcommit: a50a1ca123ecc2c5ac129f112f73838748f56476
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2019
ms.locfileid: "72237214"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Atribuir perfis de usuário e de dispositivo no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Você cria um perfil e inclui todas as configurações inseridas. A próxima etapa é implantar ou "atribuir" o perfil ao usuário do Azure Active Directory (Azure AD) ou aos grupos de dispositivos. Quando atribuído, os usuários e dispositivos recebem seu perfil e as configurações que você inseriu são aplicadas.

Este artigo mostra como atribuir um perfil e inclui algumas informações sobre como usar marcas de escopo em seus perfis.

> [!NOTE]  
> Quando uma política é removida ou não é mais atribuída a um dispositivo, a configuração pode manter o valor existente. A configuração não reverte para um valor padrão. Para alterar a configuração para um valor diferente, crie uma nova política e atribua-a.

## <a name="assign-a-device-profile"></a>Atribuir um perfil de dispositivo

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **configuração do dispositivo** > **perfis**. Todos os perfis são listados.
3. Selecione o perfil ao qual você deseja atribuir > **atribuições**.
4. Escolha **incluir** grupos ou **excluir** grupos e, em seguida, selecione seus grupos. Ao selecionar seus grupos, você está escolhendo um grupo do Azure AD. Para selecionar vários grupos, mantenha pressionada a tecla **Ctrl** e selecione seus grupos.

    ![Captura de tela de opções para incluir ou excluir grupos de uma atribuição de perfil](./media/device-profile-assign/group-include-exclude.png)

5. **Salve** suas alterações.

### <a name="evaluate-how-many-users-are-targeted"></a>Avaliar quantos usuários são direcionados

Ao atribuir o perfil, você também pode **avaliar** quantos usuários são afetados. Este recurso calcula os usuários; Ele não calcula os dispositivos.

1. No Intune, selecione **configuração do dispositivo** > **perfis**.
2. Selecione um perfil > **atribuições** > **avaliar**. Uma mensagem mostra quantos usuários são direcionados por esse perfil.

Se o botão **avaliar** estiver esmaecido, verifique se o perfil está atribuído a um ou mais grupos.

## <a name="use-scope-tags-or-applicability-rules"></a>Usar marcas de escopo ou regras de aplicabilidade

Ao criar ou atualizar um perfil, você também pode adicionar marcas de escopo e regras de aplicabilidade ao perfil.

As **marcas de escopo** são uma ótima maneira de atribuir e filtrar políticas a grupos específicos, como recursos humanos ou todos os funcionários de US-NC. [Use as marcas de escopo e RBAC para distribuídas](../fundamentals/scope-tags.md) com mais informações.

Em dispositivos Windows 10, você pode adicionar **regras de aplicabilidade** para que o perfil se aplique somente a uma versão específica do sistema operacional ou a uma edição específica do Windows. [As regras de aplicabilidade](device-profile-create.md#applicability-rules) têm mais informações.

## <a name="exclude-groups-from-a-profile-assignment"></a>Excluir grupos de uma atribuição de perfil

Os perfis de configuração de dispositivo do Intune permitem que você exclua grupos da atribuição de política.

O Intune não analisa as relações de grupo de usuário para dispositivo. A inclusão de grupos de usuários, ao excluir grupos de dispositivos, pode não obter os resultados esperados. Em cenários de grupo de usuários para grupo de usuários e grupos de dispositivos para dispositivos, a exclusão tem precedência sobre a inclusão.

Por exemplo, você atribui um perfil de dispositivo ao grupo de usuários **todos os usuários corporativos** , mas exclui membros do grupo de usuários da **equipe de gerenciamento sênior** . Como ambos os grupos são grupos de usuários, todos os membros da **equipe de gerenciamento sênior** são excluídos da política, mesmo que eles sejam membros do grupo **todos os usuários corporativos** .

A inclusão tem precedência sobre a exclusão ao usar grupos mistos, como grupo de usuários a dispositivo, ou grupo de grupos de dispositivos para usuários.

Por exemplo, você deseja atribuir um perfil de dispositivo a todos os usuários em sua organização, exceto dispositivos de quiosque. Você inclui o grupo **todos os usuários** , mas exclui o grupo **todos os dispositivos** . Nesse caso, todos os usuários e seus dispositivos obtêm a política, mesmo que o dispositivo do usuário esteja no grupo **todos os dispositivos** .

A exclusão só examina os membros diretos do grupo. Ele não inclui dispositivos associados a um usuário. No entanto, os dispositivos que não têm um usuário não obtêm a política. Esse comportamento ocorre porque os dispositivos sem usuários não têm nenhuma relação com o grupo **todos os usuários** .

Se você incluir **todos os dispositivos**e excluir **todos os usuários**, todos os dispositivos receberão a política. Nesse cenário, a intenção é excluir os dispositivos que têm um usuário associado dessa política. No entanto, ele não exclui os dispositivos porque a exclusão só compara Membros diretos do grupo.

## <a name="next-steps"></a>Passos seguintes

Consulte [monitorar perfis de dispositivo](device-profile-monitor.md) para obter orientação sobre como monitorar seus perfis e os dispositivos que executam seus perfis.
