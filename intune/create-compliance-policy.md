---
title: Políticas de conformidade de dispositivos no Microsoft Intune – Azure | Microsoft Docs
description: Começar a utilizar com políticas de conformidade de dispositivo de utilização, visão geral do Estado e níveis de gravidade, utilizar o estado InGracePeriod, trabalhar com acesso condicional, processamento de dispositivos sem uma política atribuída e as diferenças de conformidade no portal do Azure e portal clássico no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: da0aa98774f25bf290391225c6ccae56a3859c22
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59425332"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Criar uma política de conformidade no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

As políticas de conformidade de dispositivos são um elemento fundamental ao utilizar o Intune para proteger os recursos da sua organização. No Intune, pode criar regras e definições que os dispositivos têm de cumprir para ser considerado conforme, tais como uma versão mínima do SO. Se o dispositivo não estiver em conformidade, pode bloquear o acesso aos dados e recursos através do [acesso condicional](conditional-access.md).

Também pode efetuar ações de não conformidade, tal como enviar uma notificação por e-mail ao utilizador. Para uma descrição geral do que as políticas de conformidade fazem e como são utilizadas, consulte [introdução à conformidade de dispositivo](device-compliance-get-started.md).

Este artigo:

- Lista os pré-requisitos e os passos para criar uma política de conformidade.
- Mostra como atribuir a política aos grupos de utilizadores e dispositivos.
- Descreve as funcionalidades adicionais, incluindo etiquetas de âmbito para "Filtrar" suas políticas e os passos que pode efetuar em dispositivos que não estão em conformidade.
- Lista a atualização de entrada quando os dispositivos recebem as atualizações de política de tempos de ciclos.

## <a name="before-you-begin"></a>Antes de começar

Para utilizar as políticas de conformidade do dispositivo, não se esqueça de:

- Utilize as seguintes subscrições:

  - Intune
  - Se utilizar o acesso condicional, em seguida, terá a edição Premium do Azure Active Directory (AD). [Os preços do Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/) lista o que fazer com as edições diferentes. Conformidade do Intune, não precisa do Azure AD.

- Utilize uma plataforma suportada:

  - Android
  - Android Enterprise
  - iOS
  - macOS (pré-visualização)
  - Windows 10
  - Windows 8.1
  - Windows Phone 8.1

- Inscrever dispositivos no Intune (necessário para ver o estado de conformidade)

- Inscrever dispositivos a um utilizador ou inscrever-se sem um utilizador primário. Dispositivos inscritos para vários utilizadores não são suportados.

## <a name="create-the-policy"></a>Criar a política

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Selecione **Conformidade do dispositivo**. Tem as seguintes opções:

    - **Descrição geral**: Mostra um resumo e número de dispositivos que estão em conformidade, não avaliadas, e assim por diante. Ele também lista as políticas e definições individuais em suas diretivas. [Monitorizar políticas de conformidade de dispositivos do Intune](compliance-policy-monitor.md) fornece algumas boas informações.
    - **Gerir**: Criar políticas de dispositivo, envie [notificações](quickstart-send-notification.md) para dispositivos não conformes e habilite [delimitação por barreiras de rede](use-network-locations.md).
    - **Monitor**: Verificar o estado de conformidade dos seus dispositivos e ao nível da definição e a política. [Monitorizar políticas de conformidade de dispositivos do Intune](compliance-policy-monitor.md) é um bom recurso. Além disso, ver registos e verificar o estado do agente de ameaças dos seus dispositivos.
    - **Configuração**: Utilizar o [políticas de conformidade internos](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies), ativar [proteção avançada contra ameaças (ATP) do Windows Defender](advanced-threat-protection.md), adicionar um [conector de defesa contra ameaças móveis](mobile-threat-defense.md)e utilizar [Jamf](conditional-access-integrate-jamf.md).

3. Selecione **Políticas** > **Criar Política**. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome descritivo para a política. Atribuir nomes às políticas, para que possa identificar facilmente mais tarde. Por exemplo, é um nome de política boa **marcar como não conforme os dispositivos com jailbreak iOS**.
    - **Descrição**: Introduza uma descrição para a política. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Escolha a plataforma dos seus dispositivos. As opções são:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 e posterior**
       - **Windows 10 e posterior**

    - **Definições**: Os artigos seguintes listam e descrevem as definições para cada plataforma:

        - [Android](compliance-policy-create-android.md)
        - [Android Enterprise](compliance-policy-create-android-for-work.md)
        - [iOS](compliance-policy-create-ios.md)
        - [macOS](compliance-policy-create-mac-os.md)
        - [Windows Phone 8.1, Windows 8.1 e posterior](compliance-policy-create-windows-8-1.md)
        - [Windows 10 e posterior](compliance-policy-create-windows.md)

4. Quando terminar, selecione **OK** > **criar** para guardar as alterações. A política é criada e apresentada na lista. Em seguida, atribua a política aos seus grupos.

## <a name="assign-user-groups"></a>Atribuir grupos de utilizadores

Depois de criar uma política, a próxima etapa é atribuir a política aos seus grupos:

1. Escolha uma política que criou. As políticas existentes encontram-se em **Conformidade do dispositivo** > **Políticas**.
2. Selecione a política > **atribuições**. Pode incluir ou excluir grupos de segurança do Azure Active Directory (AD).
3. Escolha **Grupos selecionados** para ver os grupos de segurança do Azure AD. Selecione os grupos de utilizador que pretende aplicar esta política > Escolha **guardar** para implementar a política aos utilizadores.

Aplicou a política aos utilizadores. Os dispositivos utilizados pelos utilizadores abrangidos pela política são avaliados quanto à conformidade.

### <a name="evaluate-how-many-users-are-targeted"></a>Avaliar o número de utilizadores é visado

Quando atribui a política, também pode **Evaluate** quantos utilizadores são afetados. Esta funcionalidade calcula os utilizadores. ele não calcula a dispositivos.

1. No Intune, selecione **conformidade do dispositivo** > **políticas**.
2. Selecione uma política > **atribuições** > **Evaluate**. Uma mensagem mostra quantos utilizadores são visados por esta política.

Se o **Evaluate** botão está a cinzento, certifique-se de que a política é atribuída a um ou mais grupos.

## <a name="actions-for-noncompliance"></a>Ações de não conformidade

Para dispositivos que não cumprem as políticas de conformidade, é possível adicionar uma sequência de ações para aplicar automaticamente. Pode alterar a agenda quando o dispositivo for marcado como não conforme, tal como após um dia. Também pode configurar uma segunda ação que envia um e-mail para o utilizador quando o dispositivo não estiver em conformidade.

O artigo [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) fornece mais informações, incluindo como criar um e-mail de notificação para os seus utilizadores.

Por exemplo, está a utilizar a funcionalidade Localizações e adiciona uma localização numa política de conformidade. A ação predefinida de não conformidade aplica-se quando selecionar pelo menos uma localização. Se o dispositivo não estiver ligado às localizações selecionadas, será imediatamente considerado não conforme. Pode dar aos seus utilizadores um período de tolerância, por exemplo um dia.

## <a name="scope-tags"></a>Scope tags (Etiquetas de âmbito)

Etiquetas de âmbito são uma excelente forma de atribuir e filtrar políticas a grupos específicos, como vendas, RH, funcionários de todos os E.U.A. por NC e assim por diante. Depois de adicionar as definições, também pode adicionar uma etiqueta de âmbito para as políticas de conformidade. [Utilizar etiquetas de âmbito para políticas de filtro](scope-tags.md) é um bom recurso.

## <a name="refresh-cycle-times"></a>Tempos de ciclos de atualização

Quando a verificação de compatibilidade, o Intune utiliza o mesmo ciclo de atualização como perfis de configuração. Em geral, os tempos são:

| Plataforma | Ciclo de atualização|
| --- | --- |
| iOS | A cada 6 horas |
| macOS | A cada 6 horas |
| Android | A cada 8 horas |
| PCs com o Windows 10 inscritos como dispositivos | A cada 8 horas |
| Windows Phone | A cada 8 horas |
| Windows 8.1 | A cada 8 horas |

Se o dispositivo inscrito recentemente, o check-in de conformidade é executado com mais frequência:

| Plataforma | Frequência |
| --- | --- |
| iOS | A cada 15 minutos durante 6 horas e, em seguida, a cada 6 horas |  
| macOS | A cada 15 minutos durante 6 horas e, em seguida, a cada 6 horas | 
| Android | A cada 3 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas | 
| PCs com o Windows 10 inscritos como dispositivos | A cada 3 minutos durante 30 minutos e, em seguida, a cada 8 horas | 
| Windows Phone | A cada 5 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas | 
| Windows 8.1 | A cada 5 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas | 

Em qualquer altura, os utilizadores podem abrir a aplicação Portal da empresa e sincronizar o dispositivo para verificar imediatamente uma política.

### <a name="assign-an-ingraceperiod-status"></a>Atribuir um estado InGracePeriod

O estado InGracePeriod de uma política de conformidade é um valor. Este valor é determinado pela combinação do período de tolerância de um dispositivo e o estado real de um dispositivo para essa política de conformidade.

Mais concretamente, se um dispositivo tiver um estado NonCompliant para uma política de conformidade atribuída e:

- o dispositivo não tiver um período de tolerância atribuído, então o valor atribuído para a política de conformidade é NonCompliant
- o dispositivo tiver um período de tolerância expirado, então o valor atribuído para a política de conformidade é NonCompliant
- o dispositivo tiver um período de tolerância futuro, então o valor atribuído para a política de conformidade é InGracePeriod

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
|Desconhecido     |1|
|NotApplicable     |2|
|Compatível|3|
|InGracePeriod|4|
|NonCompliant|5|
|Erro|6|

Quando um dispositivo tem múltiplas políticas de conformidade, é atribuído o nível de gravidade mais elevado de todas as políticas a esse dispositivo.

Por exemplo, um dispositivo tem três políticas de conformidade atribuídas ao mesmo: um Estado desconhecido (gravidade = 1), outra com o estado (gravidade = 3) e um Estado InGracePeriod (gravidade = 4). O estado InGracePeriod tem o nível de gravidade mais elevado. Por isso, todas as três políticas tem o estado de conformidade InGracePeriod.

## <a name="next-steps"></a>Passos Seguintes

[Monitorizar as suas políticas](compliance-policy-monitor.md).