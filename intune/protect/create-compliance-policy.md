---
title: Create device compliance policies in Microsoft Intune - Azure | Microsoft Docs
description: Create device compliance policies, overview of status and severity levels, using the InGracePeriod status, working with Conditional Access, handling devices without an assigned policy, and the differences in compliance in the Azure portal and classic portal in Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
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
ms.openlocfilehash: c8452f9b56032864380ec703bfd444dc85ef129b
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188268"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Criar uma política de conformidade no Microsoft Intune

As políticas de conformidade de dispositivos são um elemento fundamental ao utilizar o Intune para proteger os recursos da sua organização. No Intune, pode criar regras e definições que os dispositivos têm de cumprir para serem considerados como estando em conformidade, como a versão mínima do SO. If the device isn't compliant, you can then block access to data and resources using [Conditional Access](conditional-access.md).

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
  - If you use Conditional Access, then you need Azure Active Directory (AD) Premium edition. A página [Preços do Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/) descreve as funcionalidades das diferentes edições. A conformidade no Intune não exige o Microsoft Azure AD.

- Utilize uma plataforma suportada:

  - Android device administrator
  - Android Enterprise
  - iOS
  - macOS
  - Windows 10
  - Windows 8.1
  - Wnodows Phone 8.1

- Inscreva os dispositivos no Intune (necessário para ver o estado de conformidade).

- Inscreva os dispositivos para um utilizador ou inscreva sem um utilizador primário. Os dispositivos inscritos para vários utilizadores não são suportados.

## <a name="create-the-policy"></a>Criar a política

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Devices** > **Compliance policies** > **Create Policy**.

3. Specify the following properties:

   - **Name**: Enter a descriptive name for the policy. Atribua nomes às políticas de forma que possa identificá-las facilmente mais tarde. Por exemplo, um bom nome de política é **Marcar os dispositivos iOS desbloqueados por jailbreak como não conformes**.

   - **Description**: Enter a description for the policy. Esta definição é opcional, mas recomendada.

   - **Platform**: Choose the platform of your devices. As opções são:
     - **Android device administrator**
     - **Android Enterprise**
     - **iOS/iPadOS**
     - **macOS**
     - **Windows Phone 8.1**
     - **Windows 8.1 e posterior**
     - **Windows 10 e posterior**

     For *Android Enterprise*, you must then select a **Profile type**:
     - **Device owner**
     - **Work Profile**

   - **Settings**: The following articles list and describe the settings for each platform:
     - [Android device administrator](compliance-policy-create-android.md)
     - [Android Enterprise](compliance-policy-create-android-for-work.md)
     - [iOS/iPadOS](compliance-policy-create-ios.md)
     - [macOS](compliance-policy-create-mac-os.md)
     - [Windows Phone 8.1, Windows 8.1 e posterior](compliance-policy-create-windows-8-1.md)
     - [Windows 10 e posterior](compliance-policy-create-windows.md)  

   - **Locations** *(Android device administrator)* : In your policy, you can force compliance by the location of the device. Escolha uma das localizações existentes. Ainda não tem uma localização? Veja [Utilizar Localizações (barreira de rede)](use-network-locations.md) no Intune para obter algumas orientações.  

   - **Actions for noncompliance**: For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. Pode alterar a agenda quando o dispositivo for marcado como não conforme, tal como após um dia. Também pode configurar uma segunda ação que envia um e-mail para o utilizador quando o dispositivo não estiver em conformidade.

     O artigo [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) fornece mais informações, incluindo como criar um e-mail de notificação para os seus utilizadores.

     Por exemplo, está a utilizar a funcionalidade Localizações e adiciona uma localização numa política de conformidade. A ação predefinida de não conformidade aplica-se quando selecionar pelo menos uma localização. Se o dispositivo não estiver ligado às localizações selecionadas, será imediatamente considerado não conforme. Pode dar aos seus utilizadores um período de tolerância, por exemplo um dia.

   - **Scope (Tags)** : Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. Depois de adicionar as definições, também pode adicionar uma etiqueta de âmbito às políticas de conformidade. O artigo [Utilizar etiquetas de âmbito para filtrar políticas](../fundamentals/scope-tags.md) pode ser útil.

4. Quando terminar, selecione **OK** > **Criar** para guardar as alterações. A política é criada e apresentada na lista. Em seguida, atribua a política aos grupos.

## <a name="assign-the-policy"></a>Atribuir a política

Depois de criar uma política, o passo seguinte é atribuir a política aos grupos:

1. Escolha uma política que tenha criado. Existing policies are in **Devices** > **Compliance policies** > **Policies**.

2. Select the *policy* > **Assignments**. Pode incluir ou excluir grupos de segurança do Azure Active Directory (AD).

3. Escolha **Grupos selecionados** para ver os grupos de segurança do Azure AD. Select the groups you want this policy to apply > Choose **Save** to deploy the policy.

The users or devices targeted by your policy are evaluated for compliance when they check-in with Intune.

### <a name="evaluate-how-many-users-are-targeted"></a>Avaliar a quantidade de utilizadores visados

Quando atribui a política, também pode **Avaliar** quantos utilizadores são afetados. Esta funcionalidade calcula os utilizadores, mas não calcula os dispositivos.

1. In Intune, select **Devices** > **Compliance policies** > **Policies**.

2. Select a *policy* > **Assignments** > **Evaluate**. É apresentada uma mensagem que mostra a quantidade de utilizadores visados por esta política.

Se o botão **Avaliar** ficar cinzento, verifique se a política foi atribuída a um ou mais grupos.

<!-- ## Actions for noncompliance

For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. You can change the schedule when the device is marked non-compliant, such as after one day. You can also configure a second action that sends an email to the user when the device isn't compliant.

[Add actions for noncompliant devices](actions-for-noncompliance.md) provides more information, including creating a notification email to your users.

For example, you're using the Locations feature, and add a location in a compliance policy. The default action for noncompliance applies when you select at least one location. If the device isn't connected to the selected locations, it's immediately considered not compliant. You can give your users a grace period, such as one day.

## Scope tags

Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. After you add the settings, you can also add a scope tag to your compliance policies. [Use scope tags to filter policies](../fundamentals/scope-tags.md) is a good resource.
-->

## <a name="refresh-cycle-times"></a>Tempos de ciclos de atualização

Intune uses different refresh cycles to check for updates to compliance policies. If the device recently enrolled, the check-in runs more frequently. [Policy and profile refresh cycles](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) lists the estimated refresh times.

At any time, users can open the Company Portal app, and sync the device to immediately check for policy updates.

### <a name="assign-an-ingraceperiod-status"></a>Atribuir um estado InGracePeriod

O estado InGracePeriod de uma política de conformidade é um valor. Este valor é determinado pela combinação do período de tolerância de um dispositivo e o estado real de um dispositivo para essa política de conformidade.

Mais concretamente, se um dispositivo tiver um estado NonCompliant para uma política de conformidade atribuída e:

- The device has no grace period assigned to it, then the assigned value for the compliance policy is NonCompliant
- The device has a grace period that's expired, then the assigned value for the compliance policy is NonCompliant
- The device has a grace period that's in the future, then the assigned value for the compliance policy is InGracePeriod

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
