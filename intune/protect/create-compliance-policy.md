---
title: Criar políticas de conformidade do dispositivo no Microsoft Intune-Azure | Microsoft Docs
description: Crie políticas de conformidade do dispositivo, visão geral dos níveis de status e gravidade, usando o status InGracePeriod, trabalhando com o acesso condicional, manipulando dispositivos sem uma política atribuída e as diferenças de conformidade no portal do Azure e no portal clássico no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ec8003264c28ea40d53731c8fb8c3eddef7fded
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306574"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Criar uma política de conformidade no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

As políticas de conformidade do dispositivo são um recurso importante ao usar o Intune para proteger os recursos da sua organização. No Intune, você pode criar regras e configurações que os dispositivos devem atender para serem considerados em conformidade, como uma versão mínima do so. Se o dispositivo não estiver em conformidade, você poderá bloquear o acesso a dados e recursos usando o [acesso condicional](conditional-access.md).

Você também pode executar ações de não conformidade, como enviar um email de notificação para o usuário. Para obter uma visão geral do que as políticas de conformidade fazem e como elas são usadas, consulte Introdução [à conformidade do dispositivo](device-compliance-get-started.md).

Este artigo:

- Lista os pré-requisitos e as etapas para criar uma política de conformidade.
- Mostra como atribuir a política a seus grupos de usuários e dispositivos.
- Descreve recursos adicionais, incluindo marcas de escopo para "filtrar" suas políticas e etapas que você pode executar em dispositivos que não são compatíveis.
- Lista os tempos de ciclo de atualização de check-in quando os dispositivos recebem atualizações de política.

## <a name="before-you-begin"></a>Antes de começar

Para usar as políticas de conformidade do dispositivo, verifique se você:

- Use as seguintes assinaturas:

  - Intune
  - Se você usar o acesso condicional, precisará do Azure Active Directory (AD) Premium Edition. [Azure Active Directory preços](https://azure.microsoft.com/pricing/details/active-directory/) lista o que você obtém com as diferentes edições. A conformidade do Intune não requer o Azure AD.

- Use uma plataforma com suporte:

  - Android
  - Android Enterprise
  - iOS
  - macOS (versão prévia)
  - Windows 10
  - Windows 8.1
  - Windows Phone 8,1

- Registrar dispositivos no Intune (necessário para ver o status de conformidade)

- Registrar dispositivos em um usuário ou registrar sem um usuário primário. Não há suporte para dispositivos registrados em vários usuários.

## <a name="create-the-policy"></a>Criar a política

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **conformidade do dispositivo**. Existem as seguintes opções:

    - **Visão geral**: mostra um resumo e um número de dispositivos que são compatíveis, não avaliados e assim por diante. Ele também lista as políticas e configurações individuais em suas políticas. [Monitorar as políticas de conformidade do dispositivo do Intune](compliance-policy-monitor.md) fornece algumas boas informações.
    - **Gerenciar**: Crie políticas de dispositivo, envie [notificações](quickstart-send-notification.md) para dispositivos sem conformidade e habilite o [isolamento de rede](use-network-locations.md).
    - **Monitor**: Verifique o status de conformidade de seus dispositivos e na configuração e no nível de política. [Monitorar as políticas de conformidade do dispositivo do Intune](compliance-policy-monitor.md) é um bom recurso. Exiba também os logs e verifique o status do agente de ameaça de seus dispositivos.
    - **Configuração**: Use as [políticas de conformidade internas](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies), habilite a [ATP (proteção avançada contra ameaças) do Microsoft defender](advanced-threat-protection.md), adicione um [conector de defesa contra ameaças móveis](mobile-threat-defense.md)e use o [JAMF](conditional-access-integrate-jamf.md).

3. Selecione **políticas** > **criar política**. Insira as seguintes propriedades:

    - **Nome**: Insira um nome descritivo para a política. Nomeie suas políticas para que você possa identificá-las facilmente mais tarde. Por exemplo, um bom nome de política é **Marcar dispositivos com jailbreak IOS como não compatível**.
    - **Descrição**: Insira uma descrição para a política. Essa configuração é opcional, mas recomendada.
    - **Plataforma**: escolha a plataforma dos seus dispositivos. Suas opções:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8,1**
       - **Windows 8.1 e posterior**
       - **Windows 10 e posterior**

    - **Configurações**: os artigos a seguir listam e descrevem as configurações para cada plataforma:

        - [Android](compliance-policy-create-android.md)
        - [Android Enterprise](compliance-policy-create-android-for-work.md)
        - [iOS](compliance-policy-create-ios.md)
        - [macOS](compliance-policy-create-mac-os.md)
        - [Windows Phone 8,1, Windows 8.1 e posterior](compliance-policy-create-windows-8-1.md)
        - [Windows 10 e posterior](compliance-policy-create-windows.md)

4. Quando terminar, selecione **OK** > **criar** para salvar suas alterações. A política é criada e mostrada na lista. Em seguida, atribua a política aos seus grupos.

## <a name="assign-the-policy"></a>Atribuir a política

Depois que uma política é criada, a próxima etapa é atribuir a política aos seus grupos:

1. Escolha uma política que você criou. As políticas existentes estão nas**políticas**de **conformidade do dispositivo** > .
2. Selecione a política > **atribuições**. Você pode incluir ou excluir grupos de segurança Azure Active Directory (AD).
3. Escolha **grupos selecionados** para ver os grupos de segurança do Azure AD. Selecione os grupos que você deseja que essa política aplique > escolha **salvar** para implantar a política.

Os usuários ou dispositivos direcionados por sua política são avaliados quanto à conformidade quando fazem check-in com o Intune.

### <a name="evaluate-how-many-users-are-targeted"></a>Avaliar quantos usuários são direcionados

Ao atribuir a política, você também pode **avaliar** quantos usuários são afetados. Este recurso calcula os usuários; Ele não calcula os dispositivos.

1. No Intune, selecione **conformidade do dispositivo** > **políticas**.
2. Selecione uma política > **atribuições** > **avaliar**. Uma mensagem mostra quantos usuários são direcionados por essa política.

Se o botão **avaliar** estiver esmaecido, verifique se a política está atribuída a um ou mais grupos.

## <a name="actions-for-noncompliance"></a>Ações de não conformidade

Para dispositivos que não atendem às suas políticas de conformidade, você pode adicionar uma sequência de ações a serem aplicadas automaticamente. Você pode alterar o agendamento quando o dispositivo é marcado como não compatível, como depois de um dia. Você também pode configurar uma segunda ação que envia um email para o usuário quando o dispositivo não está em conformidade.

[Adicionar ações para dispositivos não compatíveis](actions-for-noncompliance.md) fornece mais informações, incluindo a criação de um email de notificação para seus usuários.

Por exemplo, você está usando o recurso de locais e adiciona um local em uma política de conformidade. A ação padrão para não conformidade se aplica quando você seleciona pelo menos um local. Se o dispositivo não estiver conectado aos locais selecionados, ele será imediatamente considerado como não em conformidade. Você pode dar a seus usuários um período de carência, como um dia.

## <a name="scope-tags"></a>Marcas de escopo

As marcas de escopo são uma ótima maneira de atribuir e filtrar políticas a grupos específicos, como vendas, RH, todos os funcionários de US-NC e assim por diante. Depois de adicionar as configurações, você também pode adicionar uma marca de escopo às suas políticas de conformidade. [Use marcas de escopo para filtrar políticas](../fundamentals/scope-tags.md) é um bom recurso.

## <a name="refresh-cycle-times"></a>Tempos de ciclo de atualização

O Intune usa ciclos de atualização diferentes para verificar se há atualizações de políticas de conformidade. Se o dispositivo tiver sido registrado recentemente, o check-in será executado com mais frequência. [Ciclos de atualização de política e perfil](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) lista os tempos de atualização estimados.

A qualquer momento, os usuários podem abrir o aplicativo Portal da Empresa e sincronizar o dispositivo para verificar imediatamente se há atualizações de política.

### <a name="assign-an-ingraceperiod-status"></a>Atribuir um status de InGracePeriod

O status de InGracePeriod para uma política de conformidade é um valor. Esse valor é determinado pela combinação do período de carência de um dispositivo e o status real de um dispositivo para essa política de conformidade.

Especificamente, se um dispositivo tiver um status não compatível para uma política de conformidade atribuída e:

- O dispositivo não tem nenhum período de carência atribuído a ele; em seguida, o valor atribuído para a política de conformidade é não compatível
- O dispositivo tem um período de carência que expirou e, em seguida, o valor atribuído para a política de conformidade é não compatível
- O dispositivo tem um período de carência no futuro e, em seguida, o valor atribuído para a política de conformidade é InGracePeriod

A tabela a seguir resume estes pontos:

|Status de conformidade real|Valor do período de carência atribuído|Status de conformidade efetivo|
|---------|---------|---------|
|Não compatíveis |Nenhum período de carência atribuído |Não compatíveis |
|Não compatíveis |Data de ontem|Não compatíveis|
|Não compatíveis |Data do amanhã|InGracePeriod|

Para obter mais informações sobre como monitorar políticas de conformidade do dispositivo, consulte [monitorar políticas de conformidade do dispositivo do Intune](compliance-policy-monitor.md).

### <a name="assign-a-resulting-compliance-policy-status"></a>Atribuir um status de política de conformidade resultante

Se um dispositivo tiver várias políticas de conformidade e o dispositivo tiver status de conformidade diferentes para duas ou mais das políticas de conformidade atribuídas, um único status de conformidade resultante será atribuído. Essa atribuição se baseia em um nível de severidade conceitual atribuído a cada status de conformidade. Cada status de conformidade tem o seguinte nível de gravidade:

|Estado  |Gravidade  |
|---------|---------|
|Desconhecido     |1|
|NotApplicable     |2|
|Em conformidade|3|
|InGracePeriod|4|
|Não compatíveis|5|
|Erro|6|

Quando um dispositivo tem várias políticas de conformidade, o nível de severidade mais alto de todas as políticas é atribuído a esse dispositivo.

Por exemplo, um dispositivo tem três políticas de conformidade atribuídas a ele: um status desconhecido (severidade = 1), um status em conformidade (severidade = 3) e um status de InGracePeriod (gravidade = 4). O status de InGracePeriod tem o nível de severidade mais alto. Portanto, todas as três políticas têm o status de conformidade do InGracePeriod.

## <a name="next-steps"></a>Passos seguintes

[Monitore suas políticas](compliance-policy-monitor.md).
