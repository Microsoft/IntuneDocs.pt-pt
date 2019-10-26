---
title: Atribuir perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Utilize o portal do Azure para atribuir políticas e perfis de dispositivo a utilizadores e dispositivos. Saiba como excluir grupos de uma atribuição de perfis no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a19515e859f5e78f7611bbd10088aea5f7c44650
ms.sourcegitcommit: f12bd2ce10b6241715bae2d2857f33c474287166
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/24/2019
ms.locfileid: "72892621"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Atribuir perfis de utilizador e dispositivo no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Criou um perfil que inclui todas as definições que introduziu. O passo seguinte é implementar ou “atribuir” o perfil aos grupos de utilizadores ou dispositivos do Microsoft Azure Active Directory (Microsoft Azure AD). Quando for atribuído, os utilizadores e os dispositivos recebem o perfil e as definições que introduziu são aplicadas.

O artigo mostra como atribuir um perfil, inclui também alguma informação sobre a utilização de etiquetas de âmbito nos perfis.

> [!NOTE]  
> Quando uma política é removida ou não é mais atribuída a um dispositivo, a configuração pode manter o valor existente. A configuração não reverte para um valor padrão. Para alterar a configuração para um valor diferente, crie uma nova política e atribua-a.

## <a name="before-you-begin"></a>Antes de começar

Verifique se você tem a função apropriada para atribuir políticas. Para obter mais informações, consulte [RBAC (controle de acesso baseado em função) com Microsoft Intune](../fundamentals/role-based-access-control.md).

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

Os perfis de configuração de dispositivo do Intune permitem que você inclua e exclua grupos da atribuição de política.

Como prática recomendada, crie e atribua políticas especificamente para seus grupos de usuários. E criar e atribuir políticas diferentes especificamente para seus grupos de dispositivos. Para obter mais informações sobre grupos, consulte [Adicionar grupos para organizar usuários e dispositivos](../fundamentals/groups-add.md).

Ao atribuir suas políticas, use a tabela a seguir ao incluir e excluir grupos. Uma marca de seleção significa que há suporte para a atribuição:

![Opções com suporte incluem ou exclua grupos de uma atribuição de perfil](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>O que você deve saber

- A exclusão tem precedência sobre a inclusão nos seguintes cenários de tipo de Grupo:

  - Incluindo grupos de usuários e excluindo grupos de usuários
  - Incluindo grupos de dispositivos e excluindo o grupo de dispositivos

  Por exemplo, você atribui um perfil de dispositivo ao grupo de usuários **todos os usuários corporativos** , mas exclui membros do grupo de usuários da **equipe de gerenciamento sênior** . Como ambos os grupos são grupos de usuários, **todos os usuários corporativos** , exceto a **equipe de gerenciamento sênior** , obtêm a política.

- O Intune não avalia as relações de grupo de usuário para dispositivo. Se você atribuir políticas a grupos mistos, os resultados poderão não ser o que você deseja ou esperar.

  Por exemplo, você atribui um perfil de dispositivo ao grupo de usuários **todos os usuários** , mas exclui um grupo de dispositivos de **todos os dispositivos pessoais** . Nessa atribuição de política de grupo mista, **todos os usuários** obtêm a política. A exclusão não se aplica.

  Como resultado, não é recomendável atribuir políticas a grupos mistos.

## <a name="next-steps"></a>Próximos passos

Veja [monitorizar perfis de dispositivos](device-profile-monitor.md) para obter orientações sobre como monitorizar os perfis e os dispositivos que executam os seus perfis.
