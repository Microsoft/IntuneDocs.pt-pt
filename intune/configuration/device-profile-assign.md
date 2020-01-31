---
title: Atribuir perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Utilize o centro de administração do Microsoft Endpoint Manager para atribuir perfis e políticas de dispositivos a utilizadores e dispositivos. Saiba como excluir grupos de uma atribuição de perfis no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2020
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
ms.openlocfilehash: 5b61c333f41054194b44c7517e508fe1ef6d28d4
ms.sourcegitcommit: b0d683917af83170f85022b270270d8ced8e301c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76812375"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Atribuir perfis de utilizador e dispositivo no Microsoft Intune

Criou um perfil que inclui todas as definições que introduziu. O passo seguinte é implementar ou “atribuir” o perfil aos grupos de utilizadores ou dispositivos do Microsoft Azure Active Directory (Microsoft Azure AD). Quando for atribuído, os utilizadores e os dispositivos recebem o perfil e as definições que introduziu são aplicadas.

O artigo mostra como atribuir um perfil, inclui também alguma informação sobre a utilização de etiquetas de âmbito nos perfis.

> [!NOTE]  
> Quando um perfil é removido ou já não é atribuído a um dispositivo, coisas diferentes podem acontecer, dependendo das definições do perfil. As definições baseiam-se em CSPs, e cada CSP pode lidar com a remoção do perfil de forma diferente. Por exemplo, uma definição pode manter o valor existente, e não voltar a um valor predefinido. O comportamento é controlado por cada CSP no sistema operativo. Para obter uma lista de CSPs do Windows, consulte a referência do fornecedor de serviços de [configuração (CSP).](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)
>
> Para alterar uma definição para um valor diferente, crie um novo perfil, configure a definição para **Não configurado,** e atribua o perfil. Uma vez aplicado ao dispositivo, os utilizadores devem ter controlo para alterar a definição para o seu valor preferido.
>
> Ao configurar estas definições, sugerimos a implantação para um grupo piloto. Para obter mais conselhos de lançamento intune, consulte [criar um plano](../fundamentals/planning-guide-rollout-plan.md)de lançamento .

## <a name="before-you-begin"></a>Antes de começar

Certifique-se de que tem o papel adequado para atribuir perfis. Para mais informações, consulte o [controlo de acesso baseado em Role (RBAC) com](../fundamentals/role-based-access-control.md)o Microsoft Intune .

## <a name="assign-a-device-profile"></a>Atribuir um perfil do dispositivo

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > perfis de **configuração**. Todos os perfis são apresentados.
3. Selecione o perfil que quer atribuir > **Atribuições**.
4. Escolha **Incluir** ou **Excluir** grupos e, em seguida, selecione os grupos. Ao selecionar os seus grupos, estará a escolher um grupo do Azure AD. Para selecionar vários grupos, mantenha premida a tecla **Ctrl** e selecione os grupos.

    ![Captura de ecrã das opções para incluir ou excluir grupos de uma atribuição de perfis](./media/device-profile-assign/group-include-exclude.png)

5. **Guarde** as suas alterações.

### <a name="evaluate-how-many-users-are-targeted"></a>Avaliar a quantidade de utilizadores visados

Quando atribui o perfil, também pode **Avaliar** quantos utilizadores são afetados. Esta funcionalidade calcula os utilizadores, mas não calcula os dispositivos.

1. No centro de administração, selecione **Dispositivos** > Perfis de **Configuração**.
2. Selecione um perfil > **Atribuições** > **Avaliar**. É apresentada uma mensagem que mostra a quantidade de utilizadores visados por este perfil.

Se o botão **Avaliar** ficar cinzento, verifique se o perfil foi atribuído a um ou mais grupos.

## <a name="use-scope-tags-or-applicability-rules"></a>Utilize etiquetas de âmbito ou regras de aplicabilidade

Quando cria ou atualiza um perfil, também pode adicionar etiquetas de âmbito e regras de aplicabilidade ao perfil.

**As etiquetas** de âmbito são uma ótima maneira de filtrar perfis para grupos específicos, como `US-NC IT Team` ou `JohnGlenn_ITDepartment`. Para obter mais informações, veja [Utilizar o RBAC e etiquetas de âmbito para TI distribuídas](../fundamentals/scope-tags.md).

Nos dispositivos Windows 10, pode adicionar regras de **aplicabilidade** para que o perfil se aplique apenas a uma versão oS específica ou a uma edição específica do Windows. As regras de [aplicabilidade](device-profile-create.md#applicability-rules) têm mais informações.

## <a name="user-groups-vs-device-groups"></a>Grupos de utilizadores vs. grupos de dispositivos

Muitos utilizadores perguntam quando usar grupos de utilizadores e quando usar grupos de dispositivos. A resposta depende do seu objetivo. Aqui está uma orientação para começar.

### <a name="device-groups"></a>Device groups

Se pretender aplicar as definições num dispositivo, independentemente de quem tenha assinado, atribua os seus perfis a um grupo de dispositivos. As definições aplicadas aos grupos de dispositivos vão sempre com o dispositivo, não com o utilizador.

Por exemplo:

- Os grupos de dispositivos são úteis para a gestão de dispositivos que não têm um utilizador dedicado. Por exemplo, você tem dispositivos que imprimem bilhetes, inventário de digitalização, são partilhados por trabalhadores por turnos, são atribuídos a um armazém específico, e assim por diante. Coloque estes dispositivos num grupo de dispositivos e atribua os seus perfis ao grupo de dispositivos.

- Cria um [perfil insintonizado do Dispositivo Firmware (DFCI)](device-firmware-configuration-interface-windows.md) que atualiza as definições no BIOS. Por exemplo, configura este perfil para desativar a câmara do dispositivo ou bloquear as opções de arranque para evitar que os utilizadores arranquem outro SISTEMA. Este perfil é um bom cenário para atribuir a um grupo de dispositivos.

- Em alguns dispositivos Windows específicos, pretende sempre controlar algumas definições do Microsoft Edge, independentemente de quem estiver a utilizar o dispositivo. Por exemplo, você deseja bloquear todos os downloads, limitar todos os cookies à sessão de navegação atual, e eliminar o histórico de navegação. Para este cenário, coloque estes dispositivos Windows específicos num grupo de dispositivos. Em seguida, crie um [Modelo Administrativo no Intune,](administrative-templates-windows.md)adicione estas definições do dispositivo e, em seguida, atribua este perfil ao grupo de dispositivos.

Para resumir, utilize grupos de dispositivos quando não se importa quem assinou o dispositivo, ou se alguém está inscrito. Quer que as suas definições estejam sempre no dispositivo.

### <a name="user-groups"></a>Grupos de utilizadores

As definições de perfil aplicadas aos grupos de utilizadores vão sempre com o utilizador e vão com o utilizador quando estão inscritos nos seus muitos dispositivos. É normal que os utilizadores tenham muitos dispositivos, como um Surface Pro para trabalho, e um dispositivo iOS pessoal. E é normal que uma pessoa aceda a emails e outros recursos da organização a partir destes dispositivos.

Por exemplo:

- Você deseja colocar um ícone de Help Desk para todos os utilizadores em todos os seus dispositivos. Neste cenário, coloque estes utilizadores num grupo de utilizadores e atribua o seu perfil de ícone do Help Desk a este grupo de utilizadores.
- Um utilizador recebe um novo dispositivo de propriedade organizacional. O utilizador insere-se no dispositivo com a sua conta de domínio. O dispositivo é automaticamente registado em Azure AD, e gerido automaticamente pela Intune. Este perfil é um bom cenário para atribuir a um grupo de utilizadores.
- Sempre que um utilizador faz o instituto num dispositivo, pretende controlar funcionalidades em aplicações, como o OneDrive ou o Office. Neste cenário, atribua as definições de perfil do OneDrive ou do Office a um grupo de utilizadores.

  Por exemplo, pretende bloquear controlos ActiveX não confiáveis nas suas aplicações do Office. Pode criar um [Modelo Administrativo em Intune,](administrative-templates-windows.md)configurar esta definição e, em seguida, atribuir este perfil a um grupo de utilizadores.

Para resumir, utilize os grupos de utilizadores quando quiser que as suas definições e regras acompanhem sempre o utilizador, qualquer que seja o dispositivo que utilizem.

## <a name="exclude-groups-from-a-profile-assignment"></a>Excluir grupos de uma atribuição de perfis

Os perfis de configuração do dispositivo intonantes permitem-lhe incluir e excluir grupos da atribuição de perfis.

Como uma boa prática, crie e atribua perfis especificamente para os seus grupos de utilizadores. E criar e atribuir perfis diferentes especificamente para os grupos de dispositivos. Para obter mais informações sobre grupos, consulte [Adicionar grupos para organizar utilizadores e dispositivos](../fundamentals/groups-add.md).

Ao atribuir os seus perfis, utilize a tabela seguinte ao incluir e excluir grupos. Uma marca de verificação significa que a atribuição é suportada:

![Opções suportadas incluem ou excluem grupos de uma atribuição de perfil](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>O que deve saber

- A exclusão prevalece sobre a inclusão nos seguintes cenários de grupo:

  - Incluindo grupos de utilizadores e excluindo grupos de utilizadores
  - Incluindo grupos de dispositivos e excluindo o grupo de dispositivos

  Por exemplo, atribui um perfil de dispositivo ao grupo de utilizadores de **todos os utilizadores corporativos,** mas exclui membros do grupo de utilizadores do Staff de **Gestão Sénior.** Uma vez que ambos os grupos são grupos de utilizadores, **todos os utilizadores corporativos,** exceto o pessoal **de Gestão Sénior** obtêm o perfil.

- Intune não avalia as relações de grupo de utilizador para dispositivo. Se atribuir perfis a grupos mistos, os resultados podem não ser o que pretende ou espera.

  Por exemplo, atribui um perfil de dispositivo ao grupo de utilizadores **de Todos os Utilizadores,** mas exclui um grupo de **dispositivos pessoais.** Nesta atribuição de perfil de grupo misto, **todos os utilizadores** obtêm o perfil. A exclusão não se aplica.

  Como resultado, não é recomendado atribuir perfis a grupos mistos.

## <a name="next-steps"></a>Próximos passos

Veja [monitorizar perfis de dispositivos](device-profile-monitor.md) para obter orientações sobre como monitorizar os perfis e os dispositivos que executam os seus perfis.
