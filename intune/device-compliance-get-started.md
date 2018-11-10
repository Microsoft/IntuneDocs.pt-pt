---
title: Políticas de conformidade de dispositivos no Microsoft Intune – Azure | Microsoft Docs
description: Requisitos para utilizar políticas de conformidade de dispositivos, descrição geral de estados e níveis de gravidade, utilização do estado InGracePeriod, trabalhar com acesso condicional, processamento de dispositivos sem uma política atribuída e as diferenças de conformidade no portal do Azure e no portal clássico no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 226713d893e05c2c2aeea49cde2ce92591d06391
ms.sourcegitcommit: 1134ecd733356277b40eb1c7f2b318b36d387e00
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/02/2018
ms.locfileid: "50915704"
---
# <a name="get-started-with-device-compliance-policies-in-intune"></a>Introdução às políticas de conformidade de dispositivos no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Os requisitos de conformidade são essencialmente regras, como exigir um PIN do dispositivo ou a encriptação. As políticas de conformidade de dispositivos definem as regras e definições que um dispositivo tem de seguir para ser considerado conforme. Estas regras incluem:

- Utilizar uma palavra-passe para aceder a dispositivos

- Encriptação

- Se o dispositivo está desbloqueado por jailbreak ou rooting

- Versão mínima do SO obrigatória

- Versão máxima de SO permitida

- Exigir que o dispositivo esteja ao nível ou abaixo do nível da Defesa Contra Ameaças para Dispositivos Móveis

Também pode utilizar as políticas de conformidade do dispositivo para monitorizar o estado de conformidade nos seus dispositivos.

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="prerequisites"></a>Pré-requisitos
Para utilizar políticas de conformidade de dispositivos, é necessário que:

- Utilize as seguintes subscrições:

  - Intune
  - Azure Active Directory (AAD) Premium

- Utilize uma plataforma suportada:

  - Android
  - iOS
  - macOS (pré-visualização)
  - Windows 8.1
  - Windows Phone 8.1
  - Windows 10

- Os dispositivos tenham de estar inscritos no Intune para comunicarem os respetivos estados de conformidade

- Os dispositivos inscritos a um utilizador ou com nenhum utilizador primário são suportados. Não são suportados vários contextos de utilizador.

## <a name="how-intune-device-compliance-policies-work-with-azure-ad"></a>De que forma as políticas de conformidade de dispositivos do Intune funcionam com o Azure AD

Quando um dispositivo é inscrito no Intune, é iniciado o processo de registo do Azure AD, o que atualiza os atributos do dispositivo no Azure AD. Uma das principais informações do dispositivo é o estado de conformidade do dispositivo. Este estado de conformidade do dispositivo é utilizado pelas políticas de acesso condicional para bloquear ou permitir o acesso a e-mails e outros recursos da empresa.

O [processo de registo do Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction) fornece mais informações.

### <a name="assign-a-resulting-device-configuration-profile-status"></a>Atribuir um resultado de estado dos perfis de configuração do dispositivo

Se um dispositivo tiver múltiplos perfis de configuração e estados de conformidade diferentes para dois ou mais dos perfis de configuração atribuídos, isso significa que está atribuído um único resultado de estado de conformidade. Esta atribuição baseia-se num nível de gravidade concetual atribuído a cada estado de conformidade. Cada estado de conformidade tem o seguinte nível de gravidade:

|Estado  |Gravidade  |
|---------|---------|
|Pending     |1|
|Succeeded     |2|
|Failed     |3|
|Error     |4|

Quando um dispositivo tem múltiplos perfis de configuração, é atribuído o nível de gravidade mais elevado de todos os perfis a esse dispositivo.

Por exemplo, imaginemos que um dispositivo tem três perfis atribuídos: um com o estado Pending (gravidade = 1), outro com o estado Succeeded (gravidade = 2) e um com o estado Error (gravidade = 4). O estado Error tem o nível de gravidade mais elevado, pelo que é atribuído como o resultado do estado de conformidade aos três perfis.

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
|Unknown     |1|
|NotApplicable     |2|
|Compatível|3|
|InGracePeriod|4|
|NonCompliant|5|
|Error|6|

Quando um dispositivo tem múltiplas políticas de conformidade, é atribuído o nível de gravidade mais elevado de todas as políticas a esse dispositivo.

Por exemplo, imaginemos que um dispositivo tem três políticas de conformidade atribuídas: uma com o estado Unknown (gravidade = 1), outra com o estado Compliant (gravidade = 3) e uma com o estado InGracePeriod (gravidade = 4). O estado InGracePeriod tem o nível de gravidade mais elevado, pelo que é atribuído o estado de conformidade InGracePeriod às três políticas.

## <a name="ways-to-use-device-compliance-policies"></a>Formas de utilizar as políticas de conformidade de dispositivos

#### <a name="with-conditional-access"></a>Com acesso condicional
Para dispositivos que estejam em conformidade com as regras da política, poderá conceder a esses dispositivos o acesso ao e-mail e a outros recursos da empresa. Se os dispositivos não estiverem em conformidade com as regras da política, não obtêm acesso aos recursos da empresa. Isto é o acesso condicional.

#### <a name="without-conditional-access"></a>Sem acesso condicional
Também pode utilizar as políticas de conformidade de dispositivos sem acesso condicional. Quando utilizar políticas de conformidade de forma independente, os dispositivos visados são avaliados e reportados com o respetivo estado de conformidade. Por exemplo, pode obter um relatório sobre o número de dispositivos que não estão encriptados ou quais os dispositivos que têm jailbreak ou root. Quando utilizar políticas de conformidade sem acesso condicional, não existem restrições de acesso aos recursos da empresa.

## <a name="ways-to-deploy-device-compliance-policies"></a>Formas de implementar as políticas de conformidade de dispositivos
Pode implementar a política de conformidade a utilizadores em grupos de utilizadores ou dispositivos em grupos de dispositivos. Quando uma política de conformidade é implementada num utilizador, todos os dispositivos do utilizador são verificados relativamente à conformidade. No Windows 10 versão 1803 e dispositivos mais recentes, é recomendado implementar para grupos de dispositivos *se* o utilizador primário não tiver inscrito o dispositivo. Utilizar grupos de dispositivos neste cenário ajuda com os relatórios de conformidade.

Um conjunto de **Definições de política de conformidade** (Portal do Azure > Conformidade do dispositivo) incorporadas é avaliado em todos os dispositivos inscritos no Intune. Estes incluem:

- **Marcar os dispositivos sem política de conformidade atribuída como**: esta propriedade tem dois valores:

  - **Compatível**: a funcionalidade de segurança está desativada
  - **Não compatível** (predefinição): a funcionalidade de segurança está ativada

  Se um dispositivo não tiver uma política de conformidade atribuída, este dispositivo é considerado não conforme. Por predefinição, os dispositivos são marcados como **Compatíveis**. Se utilizar o acesso condicional, recomendamos que altere a definição para **Não compatível**. Se um utilizador final não estiver em conformidade porque não foi atribuída uma política, então o Portal da Empresa indica `No compliance policies have been assigned`.

- **Deteção avançada de jailbreak**: quando ativada, esta definição faz com que os dispositivos iOS se registem no Intune com mais frequência. A ativação desta propriedade utiliza os serviços de localização do dispositivo e afeta a utilização da bateria. Os dados de localização do utilizador não são armazenados pelo Intune.

  Ativar esta definição exige que os dispositivos:
  - Ativem os serviços de localização ao nível do SO
  - Permitam que o Portal da Empresa utilize os serviços de localização
  - Avaliem e comuniquem o estado de jailbreak do mesmo no Intune, pelo menos, uma vez a cada 72 horas. Caso contrário, o dispositivo será marcado como não conforme. A avaliação é acionada ao abrir a aplicação do Portal da Empresa ou ao mover fisicamente o dispositivo para uma distância de 500 metros ou mais.

- **Período de validade do estado de conformidade (dias)**: introduza o período de tempo durante o qual os dispositivos devem comunicar o estado para todas as políticas de conformidade recebidas. Os dispositivos que não devolvam o estado dentro deste período de tempo são tratados como não conformes. O valor predefinido é 30 dias.

Todos os dispositivos têm uma **Política de Conformidade de Dispositivos Incorporada** (Portal do Azure > Conformidade do dispositivo > Conformidade com a política). Utilize esta política incorporada para monitorizar estas definições.

Para saber quanto tempo é que os dispositivos móveis demoram a obter uma política após esta ser implementada, veja [Resolver problemas de perfis de dispositivos](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

Os relatórios de conformidade são uma excelente forma de verificar o estado dos dispositivos. Veja [Monitor compliance policies](compliance-policy-monitor.md) (Monitorizar políticas de conformidade) para obter orientações.

### <a name="actions-for-noncompliance"></a>Ações de não conformidade
Pode configurar uma sequência cronológica de ações que são aplicadas aos dispositivos que não cumprem os critérios da política de conformidade. Estas ações de não conformidade podem ser automatizadas, conforme descrito em [Automatizar as ações de não conformidade](actions-for-noncompliance.md).

## <a name="azure-classic-portal-vs-azure-portal"></a>Portal clássico do Azure vs.  Portal do Azure

A principal diferença ao utilizar políticas de conformidade de dispositivos no portal do Azure:

- No portal do Azure, as políticas de conformidade são criadas em separado para cada plataforma suportada
- No portal clássico do Azure, uma política de conformidade de dispositivos é comum a todas as plataformas suportadas

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

## <a name="device-compliance-policies-in-the-classic-portal-and-azure-portal"></a>Políticas de conformidade de dispositivos no portal clássico do Azure e no portal do Azure

As políticas de conformidade de dispositivos criadas no [portal clássico do Azure](https://manage.microsoft.com) não aparecem no [portal do Azure](https://portal.azure.com). No entanto, continuam a ser direcionadas para os utilizadores e geríveis através do portal clássico.

Para utilizar as funcionalidades relacionadas com a conformidade de dispositivos no portal do Azure, terá de criar novas políticas de conformidade de dispositivos no portal do Azure. Se atribuir uma política de conformidade de dispositivos no portal do Azure a um utilizador a quem também tenha sido atribuída uma política de conformidade de dispositivos do portal clássico, as políticas de conformidade de dispositivos do portal do Azure terão precedência sobre as políticas criadas no portal clássico.

## <a name="next-steps"></a>Próximos passos

- Crie uma política de conformidade de dispositivos para as seguintes plataformas:

  - [Android](compliance-policy-create-android.md)
  - [Perfil de trabalho do Android](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Para obter informações sobre as entidades de políticas do Armazém de Dados do Intune, veja [Referência para as entidades de políticas](reports-ref-policy.md).
