---
title: Criar políticas de conformidade do dispositivo no Microsoft Intune-Azure | Microsoft Docs
description: Crie políticas de conformidade do dispositivo, visão geral dos níveis de status e gravidade, usando o status InGracePeriod, trabalhando com o acesso condicional, manipulando dispositivos sem uma política atribuída e as diferenças de conformidade no portal do Azure e no portal clássico no Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 76998c32f09b20e624359cc8a38231e14a70399b
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72786081"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Criar uma política de conformidade no Microsoft Intune

As políticas de conformidade de dispositivos são um elemento fundamental ao utilizar o Intune para proteger os recursos da sua organização. No Intune, pode criar regras e definições que os dispositivos têm de cumprir para serem considerados como estando em conformidade, como a versão mínima do SO. Se o dispositivo não estiver em conformidade, você poderá bloquear o acesso a dados e recursos usando o [acesso condicional](conditional-access.md).

Também pode tomar medidas quanto à não conformidade, tais como enviar um e-mail de notificação ao utilizador. Para obter uma descrição geral do que fazem e como são utilizadas as políticas de conformidade, veja [introdução à conformidade de dispositivos](device-compliance-get-started.md).

Este artigo:

- Apresenta os pré-requisitos e os passos para criar uma política de conformidade.
- Mostra como atribuir a política aos grupos de utilizadores e dispositivos.
- Descreve funcionalidades adicionais, incluindo etiquetas de âmbito para “filtrar” as políticas, e os passos que pode efetuar nos dispositivos que não estão em conformidade.
- Apresenta os tempos de ciclos de atualização de entrada quando os dispositivos recebem as atualizações de política.

## <a name="before-you-begin"></a>Antes de começar

Para utilizar as políticas de conformidade de dispositivos:

- Utilize as seguintes subscrições:

  - Intune
  - Se você usar o acesso condicional, precisará do Azure Active Directory (AD) Premium Edition. A página [Preços do Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/) descreve as funcionalidades das diferentes edições. A conformidade no Intune não exige o Microsoft Azure AD.

- Utilize uma plataforma suportada:

  - Administrador do dispositivo Android
  - Android Enterprise
  - iOS
  - macOS
  - Windows 10
  - Windows 8.1
  - Wnodows Phone 8.1

- Inscreva os dispositivos no Intune (necessário para ver o estado de conformidade).

- Inscreva os dispositivos para um utilizador ou inscreva sem um utilizador primário. Os dispositivos inscritos para vários utilizadores não são suportados.

## <a name="create-the-policy"></a>Criar a política

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Conformidade do dispositivo**. Você tem as seguintes opções:

    - **Visão geral**: mostra um resumo e um número de dispositivos que são compatíveis, não avaliados e assim por diante. Também apresenta as políticas e as definições individuais nas suas políticas. Para obter mais informações, veja [Monitorizar as políticas de conformidade dos dispositivos do Intune](compliance-policy-monitor.md).
    - **Gerenciar**: Crie políticas de dispositivo, envie [notificações](quickstart-send-notification.md) para dispositivos sem conformidade e habilite o [isolamento de rede](use-network-locations.md).
    - **Monitor**: Verifique o status de conformidade de seus dispositivos e na configuração e no nível de política. O artigo [Monitorizar as políticas de conformidade dos dispositivos do Intune](compliance-policy-monitor.md) pode ser útil. Além disso, veja os registos e verifique o estado do agente de ameaças dos dispositivos.
    - **Configuração**: Use as [políticas de conformidade internas](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies), habilite a [ATP (proteção avançada contra ameaças) do Microsoft defender](advanced-threat-protection.md), adicione um [conector de defesa contra ameaças móveis](mobile-threat-defense.md)e use o [JAMF](conditional-access-integrate-jamf.md).

3. Selecione **Políticas** > **Criar Política**. Introduza as seguintes propriedades:

   - **Nome**: Insira um nome descritivo para a política. Atribua nomes às políticas de forma que possa identificá-las facilmente mais tarde. Por exemplo, um bom nome de política é **Marcar os dispositivos iOS desbloqueados por jailbreak como não conformes**.  

   - **Descrição**: Insira uma descrição para a política. Esta definição é opcional, mas recomendada.  

   - **Plataforma**: escolha a plataforma dos seus dispositivos. As opções são:
     - **Administrador do dispositivo Android**
     - **Android Enterprise**
     - **iOS/iPadOS**
     - **macOS**
     - **Windows Phone 8.1**
     - **Windows 8.1 e posterior**
     - **Windows 10 e posterior**

     Para o *Android Enterprise*, você deve selecionar um **tipo de perfil**:
     - **Proprietário do dispositivo**
     - **Perfil de trabalho**

   - **Configurações**: os artigos a seguir listam e descrevem as configurações para cada plataforma:
     - [Administrador do dispositivo Android](compliance-policy-create-android.md)
     - [Android Enterprise](compliance-policy-create-android-for-work.md)
     - [iOS/iPadOS](compliance-policy-create-ios.md)
     - [macOS](compliance-policy-create-mac-os.md)
     - [Windows Phone 8.1, Windows 8.1 e posterior](compliance-policy-create-windows-8-1.md)
     - [Windows 10 e posterior](compliance-policy-create-windows.md)  

   - **Locais** *(administrador de dispositivo Android)* : em sua política, você pode forçar a conformidade pelo local do dispositivo. Escolha uma das localizações existentes. Ainda não tem uma localização? Veja [Utilizar Localizações (barreira de rede)](use-network-locations.md) no Intune para obter algumas orientações.  

   - **Ações de não conformidade**: para dispositivos que não atendem às suas políticas de conformidade, você pode adicionar uma sequência de ações para aplicar automaticamente. Pode alterar a agenda quando o dispositivo for marcado como não conforme, tal como após um dia. Também pode configurar uma segunda ação que envia um e-mail para o utilizador quando o dispositivo não estiver em conformidade.
    
     O artigo [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) fornece mais informações, incluindo como criar um e-mail de notificação para os seus utilizadores.

     Por exemplo, está a utilizar a funcionalidade Localizações e adiciona uma localização numa política de conformidade. A ação predefinida de não conformidade aplica-se quando selecionar pelo menos uma localização. Se o dispositivo não estiver ligado às localizações selecionadas, será imediatamente considerado não conforme. Pode dar aos seus utilizadores um período de tolerância, por exemplo um dia.

   - **Scope (Tags)** : as marcas de escopo são uma ótima maneira de atribuir e filtrar políticas a grupos específicos, como vendas, RH, todos os funcionários de US-NC e assim por diante. Depois de adicionar as definições, também pode adicionar uma etiqueta de âmbito às políticas de conformidade. O artigo [Utilizar etiquetas de âmbito para filtrar políticas](../fundamentals/scope-tags.md) pode ser útil.

4. Quando terminar, selecione **OK** > **Criar** para guardar as alterações. A política é criada e apresentada na lista. Em seguida, atribua a política aos grupos.

## <a name="assign-the-policy"></a>Atribuir a política

Depois de criar uma política, o passo seguinte é atribuir a política aos grupos:

1. Escolha uma política que tenha criado. As políticas existentes encontram-se em **Conformidade do dispositivo** > **Políticas**.
2. Selecione a política > **Atribuições**. Pode incluir ou excluir grupos de segurança do Azure Active Directory (AD).
3. Escolha **Grupos selecionados** para ver os grupos de segurança do Azure AD. Selecione os grupos que você deseja que essa política aplique > escolha **salvar** para implantar a política.

Os usuários ou dispositivos direcionados por sua política são avaliados quanto à conformidade quando fazem check-in com o Intune.

### <a name="evaluate-how-many-users-are-targeted"></a>Avaliar a quantidade de utilizadores visados

Quando atribui a política, também pode **Avaliar** quantos utilizadores são afetados. Esta funcionalidade calcula os utilizadores, mas não calcula os dispositivos.

1. No Intune, selecione **Conformidade do dispositivo** > **Políticas**.
2. Selecione uma política > **Atribuições** > **Avaliar**. É apresentada uma mensagem que mostra a quantidade de utilizadores visados por esta política.

Se o botão **Avaliar** ficar cinzento, verifique se a política foi atribuída a um ou mais grupos.

<!-- ## Actions for noncompliance

For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. You can change the schedule when the device is marked non-compliant, such as after one day. You can also configure a second action that sends an email to the user when the device isn't compliant.

[Add actions for noncompliant devices](actions-for-noncompliance.md) provides more information, including creating a notification email to your users.

For example, you're using the Locations feature, and add a location in a compliance policy. The default action for noncompliance applies when you select at least one location. If the device isn't connected to the selected locations, it's immediately considered not compliant. You can give your users a grace period, such as one day.

## Scope tags

Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. After you add the settings, you can also add a scope tag to your compliance policies. [Use scope tags to filter policies](../fundamentals/scope-tags.md) is a good resource.
-->

## <a name="refresh-cycle-times"></a>Tempos de ciclos de atualização

O Intune usa ciclos de atualização diferentes para verificar se há atualizações de políticas de conformidade. Se o dispositivo tiver sido registrado recentemente, o check-in será executado com mais frequência. [Ciclos de atualização de política e perfil](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) lista os tempos de atualização estimados.

A qualquer momento, os usuários podem abrir o aplicativo Portal da Empresa e sincronizar o dispositivo para verificar imediatamente se há atualizações de política.

### <a name="assign-an-ingraceperiod-status"></a>Atribuir um estado InGracePeriod

O estado InGracePeriod de uma política de conformidade é um valor. Este valor é determinado pela combinação do período de tolerância de um dispositivo e o estado real de um dispositivo para essa política de conformidade.

Mais concretamente, se um dispositivo tiver um estado NonCompliant para uma política de conformidade atribuída e:

- O dispositivo não tem nenhum período de carência atribuído a ele; em seguida, o valor atribuído para a política de conformidade é não compatível
- O dispositivo tem um período de carência que expirou e, em seguida, o valor atribuído para a política de conformidade é não compatível
- O dispositivo tem um período de carência no futuro e, em seguida, o valor atribuído para a política de conformidade é InGracePeriod

A tabela seguinte apresenta um resumo destas opções:

|Estado de conformidade real|Valor do período de tolerância atribuído|Estado de conformidade em vigor|
|---------|---------|---------|
|NonCompliant |Sem período de tolerância atribuído |NonCompliant |
|NonCompliant |Data de ontem|NonCompliant|
|NonCompliant |Data de amanhã|InGracePeriod|

Para obter mais informações sobre a monitorização de políticas de conformidade do dispositivo, veja [Monitorizar as Políticas de conformidade do dispositivo do Intune](compliance-policy-monitor.md).

### <a name="assign-a-resulting-compliance-policy-status"></a>Atribuir um resultado de estado das políticas de conformidade

Se um dispositivo tiver múltiplas políticas de conformidade e estados de conformidade diferentes para duas ou mais políticas de conformidade atribuídas, isso significa que está atribuído um único resultado de estado de conformidade. Esta atribuição baseia-se num nível de gravidade concetual atribuído a cada estado de conformidade. Cada estado de conformidade tem o seguinte nível de gravidade:

|Estado  |Gravidade  |
|---------|---------|
|Unknown     |1|
|NotApplicable     |2|
|Compatível|3|
|InGracePeriod|4|
|NonCompliant|5|
|Error|6|

Quando um dispositivo tem múltiplas políticas de conformidade, é atribuído o nível de gravidade mais elevado de todas as políticas a esse dispositivo.

Por exemplo, um dispositivo tem três políticas de conformidade atribuídas: uma com o estado Desconhecido (gravidade = 1), outra com o estado Conforme (gravidade = 3) e uma com o estado Em Período de Tolerância (gravidade = 4). O estado Em Período de Tolerância tem o nível de gravidade mais elevado. Por isso, todas as três políticas têm o estado de conformidade Em Período de Tolerância.

## <a name="next-steps"></a>Próximos passos

[Monitorizar as políticas](compliance-policy-monitor.md).
