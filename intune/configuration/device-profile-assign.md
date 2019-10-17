---
title: Atribuir perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Utilize o portal do Azure para atribuir políticas e perfis de dispositivo a utilizadores e dispositivos. Saiba como excluir grupos de uma atribuição de perfis no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6579ad9eb902bcd5ad43662115f56a10681c32ba
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506870"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Atribuir perfis de utilizador e dispositivo no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Criou um perfil que inclui todas as definições que introduziu. O passo seguinte é implementar ou “atribuir” o perfil aos grupos de utilizadores ou dispositivos do Microsoft Azure Active Directory (Microsoft Azure AD). Quando for atribuído, os utilizadores e os dispositivos recebem o perfil e as definições que introduziu são aplicadas.

O artigo mostra como atribuir um perfil, inclui também alguma informação sobre a utilização de etiquetas de âmbito nos perfis.

> [!NOTE]  
> Quando uma política é removida ou não é mais atribuída a um dispositivo, a configuração pode manter o valor existente. A configuração não reverte para um valor padrão. Para alterar a configuração para um valor diferente, crie uma nova política e atribua-a.

## <a name="assign-a-device-profile"></a>Atribuir um perfil do dispositivo

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis**. Todos os perfis são apresentados.
3. Selecione o perfil que quer atribuir > **Atribuições**.
4. Escolha **Incluir** ou **Excluir** grupos e, em seguida, selecione os grupos. Ao selecionar os seus grupos, estará a escolher um grupo do Azure AD. Para selecionar vários grupos, mantenha premida a tecla **Ctrl** e selecione os grupos.

    ![Captura de ecrã das opções para incluir ou excluir grupos de uma atribuição de perfis](./media/device-profile-assign/group-include-exclude.png)

5. **Guarde** as suas alterações.

### <a name="evaluate-how-many-users-are-targeted"></a>Avaliar a quantidade de utilizadores visados

Quando atribui o perfil, também pode **Avaliar** quantos utilizadores são afetados. Esta funcionalidade calcula os utilizadores, mas não calcula os dispositivos.

1. No Intune, selecione **Configuração do dispositivo** > **Perfis**.
2. Selecione um perfil > **Atribuições** > **Avaliar**. É apresentada uma mensagem que mostra a quantidade de utilizadores visados por este perfil.

Se o botão **Avaliar** ficar cinzento, verifique se o perfil foi atribuído a um ou mais grupos.

## <a name="use-scope-tags-or-applicability-rules"></a>Usar marcas de escopo ou regras de aplicabilidade

Ao criar ou atualizar um perfil, você também pode adicionar marcas de escopo e regras de aplicabilidade ao perfil.

As **etiquetas de âmbito** são uma ótima forma de atribuir e filtrar políticas para grupos específicos, tais como Recursos Humanos ou Todos os funcionários dos EUA. Para obter mais informações, veja [Utilizar o RBAC e etiquetas de âmbito para TI distribuídas](../fundamentals/scope-tags.md).

Em dispositivos Windows 10, você pode adicionar **regras de aplicabilidade** para que o perfil se aplique somente a uma versão específica do sistema operacional ou a uma edição específica do Windows. [As regras de aplicabilidade](device-profile-create.md#applicability-rules) têm mais informações.

## <a name="exclude-groups-from-a-profile-assignment"></a>Excluir grupos de uma atribuição de perfis

Os perfis de configuração de dispositivos do Intune permitem-lhe excluir grupos da atribuição de políticas.

O Intune não analisa as relações de grupo de usuário para dispositivo. Incluir grupos de utilizadores e excluir grupos de dispositivos poderá não gerar os resultados esperados. Em cenários de grupo de usuários para grupo de usuários e grupos de dispositivos para dispositivos, a exclusão tem precedência sobre a inclusão.

Por exemplo, você atribui um perfil de dispositivo ao grupo de usuários **todos os usuários corporativos** , mas exclui membros do grupo de usuários da **equipe de gerenciamento sênior** . Como ambos os grupos são grupos de usuários, todos os membros da **equipe de gerenciamento sênior** são excluídos da política, mesmo que eles sejam membros do grupo **todos os usuários corporativos** .

A inclusão tem precedência sobre a exclusão ao usar grupos mistos, como grupo de usuários a dispositivo, ou grupo de grupos de dispositivos para usuários.

Por exemplo, você deseja atribuir um perfil de dispositivo a todos os usuários em sua organização, exceto dispositivos de quiosque. Deve incluir o grupo **Todos os Utilizadores** e excluir o grupo **Todos os Dispositivos**. Neste caso, a política será aplicada a todos os utilizadores e aos dispositivos deles, mesmo que esses dispositivos façam parte do grupo **Todos os Dispositivos**.

A exclusão contempla apenas os membros diretos do grupo. Não inclui dispositivos associados a um utilizador. No entanto, os dispositivos que não têm um usuário não obtêm a política. Esse comportamento ocorre porque os dispositivos sem usuários não têm nenhuma relação com o grupo **todos os usuários** .

Se incluir o grupo **Todos os Dispositivos** e excluir **Todos os Utilizadores**, todos os dispositivos irão receber a política. Neste cenário, o objetivo é excluir desta política os dispositivos que tiverem um utilizador associado. No entanto, isto não exclui os dispositivos porque a exclusão só compara membros diretos do grupo.

## <a name="next-steps"></a>Próximos passos

Veja [monitorizar perfis de dispositivos](device-profile-monitor.md) para obter orientações sobre como monitorizar os perfis e os dispositivos que executam os seus perfis.
