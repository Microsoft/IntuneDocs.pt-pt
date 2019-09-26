---
title: Políticas de conformidade de dispositivos no Microsoft Intune – Azure | Microsoft Docs
description: Comece a usar as políticas de conformidade do dispositivo, visão geral dos níveis de status e gravidade, usando o status do InGracePeriod, trabalhando com o acesso condicional, manipulando dispositivos sem uma política atribuída e as diferenças de conformidade no portal do Azure e Portal clássico no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b7519b07b3ac2d40734c32b79466c6d7f4f5d4e8
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/24/2019
ms.locfileid: "71303963"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Criar uma política de conformidade no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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

  - Android
  - Android Enterprise
  - iOS
  - macOS (pré-visualização)
  - Windows 10
  - Windows 8.1
  - Windows Phone 8.1

- Inscreva os dispositivos no Intune (necessário para ver o estado de conformidade).

- Inscreva os dispositivos para um utilizador ou inscreva sem um utilizador primário. Os dispositivos inscritos para vários utilizadores não são suportados.

## <a name="create-the-policy"></a>Criar a política

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Conformidade do dispositivo**. Você tem as seguintes opções:

    - **Descrição geral**: mostra um resumo e o número de dispositivos conformes, não avaliados e assim por diante. Também apresenta as políticas e as definições individuais nas suas políticas. Para obter mais informações, veja [Monitorizar as políticas de conformidade dos dispositivos do Intune](compliance-policy-monitor.md).
    - **Gerir**: crie políticas de dispositivos, envie [notificações](quickstart-send-notification.md) para dispositivos não conformes e ative a [barreira de rede](use-network-locations.md).
    - **Monitorizar**: verifique o estado de conformidade dos dispositivos ao nível das definições e das políticas. O artigo [Monitorizar as políticas de conformidade dos dispositivos do Intune](compliance-policy-monitor.md) pode ser útil. Além disso, veja os registos e verifique o estado do agente de ameaças dos dispositivos.
    - **Configurar**: Use as [políticas de conformidade internas](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies), habilite a [ATP (proteção avançada contra ameaças) do Microsoft defender](advanced-threat-protection.md), adicione um [conector de defesa contra ameaças móveis](mobile-threat-defense.md)e use o [JAMF](conditional-access-integrate-jamf.md).

3. Selecione **Políticas** > **Criar Política**. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para a política. Atribua nomes às políticas de forma que possa identificá-las facilmente mais tarde. Por exemplo, um bom nome de política é **Marcar os dispositivos iOS desbloqueados por jailbreak como não conformes**.
    - **Descrição**: introduza uma descrição para a política. Esta definição é opcional, mas recomendada.
    - **Plataforma**: escolha a plataforma dos dispositivos. As opções são:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 e posterior**
       - **Windows 10 e posterior**

    - **Definições**: Os seguintes artigos apresentam e descrevem as definições de cada plataforma:

        - [Android](compliance-policy-create-android.md)
        - [Android Enterprise](compliance-policy-create-android-for-work.md)
        - [iOS](compliance-policy-create-ios.md)
        - [macOS](compliance-policy-create-mac-os.md)
        - [Windows Phone 8.1, Windows 8.1 e posterior](compliance-policy-create-windows-8-1.md)
        - [Windows 10 e posterior](compliance-policy-create-windows.md)

4. Quando terminar, selecione **OK** > **Criar** para guardar as alterações. A política é criada e apresentada na lista. Em seguida, atribua a política aos grupos.

## <a name="assign-user-groups"></a>Atribuir grupos de utilizadores

Depois de criar uma política, o passo seguinte é atribuir a política aos grupos:

1. Escolha uma política que tenha criado. As políticas existentes encontram-se em **Conformidade do dispositivo** > **Políticas**.
2. Selecione a política > **Atribuições**. Pode incluir ou excluir grupos de segurança do Azure Active Directory (AD).
3. Escolha **Grupos selecionados** para ver os grupos de segurança do Azure AD. Selecione os grupos de utilizadores aos quais pretende aplicar esta política > escolha **Guardar** para implementar a política para os utilizadores.

Aplicou a política aos utilizadores. Os dispositivos utilizados pelos utilizadores abrangidos pela política são avaliados quanto à conformidade.

### <a name="evaluate-how-many-users-are-targeted"></a>Avaliar a quantidade de utilizadores visados

Quando atribui a política, também pode **Avaliar** quantos utilizadores são afetados. Esta funcionalidade calcula os utilizadores, mas não calcula os dispositivos.

1. No Intune, selecione **Conformidade do dispositivo** > **Políticas**.
2. Selecione uma política > **Atribuições** > **Avaliar**. É apresentada uma mensagem que mostra a quantidade de utilizadores visados por esta política.

Se o botão **Avaliar** ficar cinzento, verifique se a política foi atribuída a um ou mais grupos.

## <a name="actions-for-noncompliance"></a>Ações de não conformidade

Para dispositivos que não cumprem as políticas de conformidade, é possível adicionar uma sequência de ações a aplicar automaticamente. Pode alterar a agenda quando o dispositivo for marcado como não conforme, tal como após um dia. Também pode configurar uma segunda ação que envia um e-mail para o utilizador quando o dispositivo não estiver em conformidade.

O artigo [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) fornece mais informações, incluindo como criar um e-mail de notificação para os seus utilizadores.

Por exemplo, está a utilizar a funcionalidade Localizações e adiciona uma localização numa política de conformidade. A ação predefinida de não conformidade aplica-se quando selecionar pelo menos uma localização. Se o dispositivo não estiver ligado às localizações selecionadas, será imediatamente considerado não conforme. Pode dar aos seus utilizadores um período de tolerância, por exemplo um dia.

## <a name="scope-tags"></a>Scope tags (Etiquetas de âmbito)

As etiquetas de âmbito são uma ótima forma de atribuir e filtrar políticas para grupos específicos, tal como Vendas, RH, Todos os funcionários dos EUA e assim sucessivamente. Depois de adicionar as definições, também pode adicionar uma etiqueta de âmbito às políticas de conformidade. O artigo [Utilizar etiquetas de âmbito para filtrar políticas](scope-tags.md) pode ser útil.

## <a name="refresh-cycle-times"></a>Tempos de ciclos de atualização

O Intune usa ciclos de atualização diferentes para verificar se há atualizações de políticas de conformidade. Se o dispositivo tiver sido registrado recentemente, o check-in será executado com mais frequência. [Ciclos de atualização de política e perfil](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) lista os tempos de atualização estimados.

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

|State  |Severity  |
|---------|---------|
|Desconhecido     |1|
|NotApplicable     |2|
|Compatível|3|
|InGracePeriod|4|
|NonCompliant|5|
|Erro|6|

Quando um dispositivo tem múltiplas políticas de conformidade, é atribuído o nível de gravidade mais elevado de todas as políticas a esse dispositivo.

Por exemplo, um dispositivo tem três políticas de conformidade atribuídas: uma com o estado Desconhecido (gravidade = 1), outra com o estado Conforme (gravidade = 3) e uma com o estado Em Período de Tolerância (gravidade = 4). O estado Em Período de Tolerância tem o nível de gravidade mais elevado. Por isso, todas as três políticas têm o estado de conformidade Em Período de Tolerância.

## <a name="next-steps"></a>Passos seguintes

[Monitorizar as políticas](compliance-policy-monitor.md).