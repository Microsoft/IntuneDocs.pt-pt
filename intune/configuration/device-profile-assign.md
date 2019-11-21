---
title: Atribuir perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Utilize o portal do Azure para atribuir políticas e perfis de dispositivo a utilizadores e dispositivos. Saiba como excluir grupos de uma atribuição de perfis no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/20/2019
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
ms.openlocfilehash: 275b3961e87f0d0eda8299337fe3fb7ac89ef03b
ms.sourcegitcommit: 1a22b8b31424847d3c86590f00f56c5bc3de2eb5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74261697"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Atribuir perfis de utilizador e dispositivo no Microsoft Intune

Criou um perfil que inclui todas as definições que introduziu. O passo seguinte é implementar ou “atribuir” o perfil aos grupos de utilizadores ou dispositivos do Microsoft Azure Active Directory (Microsoft Azure AD). Quando for atribuído, os utilizadores e os dispositivos recebem o perfil e as definições que introduziu são aplicadas.

O artigo mostra como atribuir um perfil, inclui também alguma informação sobre a utilização de etiquetas de âmbito nos perfis.

> [!NOTE]  
> Quando um perfil é removido ou não é mais atribuído a um dispositivo, a configuração pode manter o valor existente. A configuração não reverte para um valor padrão. Para alterar a configuração para um valor diferente, crie um novo perfil e atribua-o.

## <a name="before-you-begin"></a>Antes de começar

Verifique se você tem a função apropriada para atribuir perfis. Para obter mais informações, consulte [RBAC (controle de acesso baseado em função) com Microsoft Intune](../fundamentals/role-based-access-control.md).

## <a name="assign-a-device-profile"></a>Atribuir um perfil do dispositivo

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração**. Todos os perfis são apresentados.
3. Selecione o perfil que quer atribuir > **Atribuições**.
4. Escolha **Incluir** ou **Excluir** grupos e, em seguida, selecione os grupos. Ao selecionar os seus grupos, estará a escolher um grupo do Azure AD. Para selecionar vários grupos, mantenha premida a tecla **Ctrl** e selecione os grupos.

    ![Captura de ecrã das opções para incluir ou excluir grupos de uma atribuição de perfis](./media/device-profile-assign/group-include-exclude.png)

5. **Guarde** as suas alterações.

### <a name="evaluate-how-many-users-are-targeted"></a>Avaliar a quantidade de utilizadores visados

Quando atribui o perfil, também pode **Avaliar** quantos utilizadores são afetados. Esta funcionalidade calcula os utilizadores, mas não calcula os dispositivos.

1. No centro de administração, selecione **dispositivos** > **perfis de configuração**.
2. Selecione um perfil > **Atribuições** > **Avaliar**. É apresentada uma mensagem que mostra a quantidade de utilizadores visados por este perfil.

Se o botão **Avaliar** ficar cinzento, verifique se o perfil foi atribuído a um ou mais grupos.

## <a name="use-scope-tags-or-applicability-rules"></a>Usar marcas de escopo ou regras de aplicabilidade

Ao criar ou atualizar um perfil, você também pode adicionar marcas de escopo e regras de aplicabilidade ao perfil.

As **marcas de escopo** são uma ótima maneira de atribuir e filtrar perfis a grupos específicos, como recursos humanos ou todos os funcionários de US-NC. Para obter mais informações, veja [Utilizar o RBAC e etiquetas de âmbito para TI distribuídas](../fundamentals/scope-tags.md).

Em dispositivos Windows 10, você pode adicionar **regras de aplicabilidade** para que o perfil se aplique somente a uma versão específica do sistema operacional ou a uma edição específica do Windows. [As regras de aplicabilidade](device-profile-create.md#applicability-rules) têm mais informações.

## <a name="user-groups-vs-device-groups"></a>Grupos de usuários versus grupos de dispositivos

Muitos usuários perguntam quando usar grupos de usuários e quando usar grupos de dispositivos. A resposta depende de sua meta. Aqui estão algumas diretrizes para você começar.

### <a name="device-groups"></a>Device groups

Se você quiser aplicar as configurações em um dispositivo, independentemente de quem está conectado, atribua seus perfis a um grupo de dispositivos. As configurações aplicadas aos grupos de dispositivos sempre vão com o dispositivo, e não para o usuário.

Por exemplo:

- Os grupos de dispositivos são úteis para gerenciar dispositivos que não têm um usuário dedicado. Por exemplo, você tem dispositivos que imprimem tíquetes, inventário de verificação, são compartilhados por operadores de turno, são atribuídos a um depósito específico e assim por diante. Coloque esses dispositivos em um grupo de dispositivos e atribua seus perfis a esse grupo de dispositivos.

- Você cria um [perfil do DFCI (interface de configuração de firmware do dispositivo) do Intune](device-firmware-configuration-interface-windows.md) que atualiza as configurações no BIOS. Por exemplo, você configura esse perfil para desabilitar a câmera do dispositivo ou bloquear as opções de inicialização para impedir que os usuários inicializem outro sistema operacional. Esse perfil é um bom cenário para atribuir a um grupo de dispositivos.

- Em alguns dispositivos Windows específicos, você sempre deseja controlar algumas configurações do Microsoft Edge, independentemente de quem estiver usando o dispositivo. Por exemplo, você deseja bloquear todos os downloads, limitar todos os cookies para a sessão de navegação atual e excluir o histórico de navegação. Para esse cenário, coloque esses dispositivos Windows específicos em um grupo de dispositivos. Em seguida, crie um [modelo administrativo no Intune](administrative-templates-windows.md), adicione essas configurações de dispositivo e, em seguida, atribua esse perfil ao grupo de dispositivos.

Para resumir, use grupos de dispositivos quando você não se importa com quem está conectado no dispositivo ou se alguém está conectado. Você deseja que suas configurações estejam sempre no dispositivo.

### <a name="user-groups"></a>Grupos de utilizadores

As configurações de perfil aplicadas a grupos de usuários sempre vão com o usuário e vão para o usuário quando entrar em seus vários dispositivos. É normal que os usuários tenham muitos dispositivos, como uma superfície Pro for Work e um dispositivo iOS pessoal. E é normal que uma pessoa acesse email e outros recursos da organização desses dispositivos.

Por exemplo:

- Você deseja colocar um ícone de suporte técnico para todos os usuários em todos os seus dispositivos. Nesse cenário, coloque esses usuários em um grupo de usuários e atribua o perfil de ícone de suporte técnico a esse grupo de usuários.
- Um usuário recebe um novo dispositivo de propriedade da organização. O usuário entra no dispositivo com sua conta de domínio. O dispositivo é registrado automaticamente no Azure AD e é gerenciado automaticamente pelo Intune. Esse perfil é um bom cenário para atribuir a um grupo de usuários.
- Sempre que um usuário entra em um dispositivo, você deseja controlar recursos em aplicativos, como OneDrive ou Office. Nesse cenário, atribua as configurações de perfil do OneDrive ou do Office a um grupo de usuários.

  Por exemplo, você deseja bloquear controles ActiveX não confiáveis em seus aplicativos do Office. Você pode criar um [modelo administrativo no Intune](administrative-templates-windows.md), definir essa configuração e atribuir esse perfil a um grupo de usuários.

Para resumir, use grupos de usuários quando desejar que suas configurações e regras sempre passem com o usuário, qualquer dispositivo que eles usam.

## <a name="exclude-groups-from-a-profile-assignment"></a>Excluir grupos de uma atribuição de perfis

Os perfis de configuração de dispositivo do Intune permitem incluir e excluir grupos da atribuição de perfil.

Como prática recomendada, crie e atribua perfis especificamente para seus grupos de usuários. E criar e atribuir perfis diferentes especificamente para seus grupos de dispositivos. Para obter mais informações sobre grupos, consulte [Adicionar grupos para organizar usuários e dispositivos](../fundamentals/groups-add.md).

Ao atribuir seus perfis, use a tabela a seguir ao incluir e excluir grupos. Uma marca de seleção significa que há suporte para a atribuição:

![Opções com suporte incluem ou exclua grupos de uma atribuição de perfil](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>O que deve saber

- A exclusão tem precedência sobre a inclusão nos seguintes cenários de tipo de Grupo:

  - Incluindo grupos de usuários e excluindo grupos de usuários
  - Incluindo grupos de dispositivos e excluindo o grupo de dispositivos

  Por exemplo, você atribui um perfil de dispositivo ao grupo de usuários **todos os usuários corporativos** , mas exclui membros do grupo de usuários da **equipe de gerenciamento sênior** . Como ambos os grupos são grupos de usuários, **todos os usuários corporativos** , exceto a **equipe de gerenciamento sênior** , obtêm o perfil.

- O Intune não avalia as relações de grupo de usuário para dispositivo. Se você atribuir perfis a grupos mistos, os resultados poderão não ser o que você deseja ou esperar.

  Por exemplo, você atribui um perfil de dispositivo ao grupo de usuários **todos os usuários** , mas exclui um grupo de dispositivos de **todos os dispositivos pessoais** . Nesta atribuição de perfil de grupo misto, **todos os usuários** obtêm o perfil. A exclusão não se aplica.

  Como resultado, não é recomendável atribuir perfis a grupos mistos.

## <a name="next-steps"></a>Próximos passos

Veja [monitorizar perfis de dispositivos](device-profile-monitor.md) para obter orientações sobre como monitorizar os perfis e os dispositivos que executam os seus perfis.
