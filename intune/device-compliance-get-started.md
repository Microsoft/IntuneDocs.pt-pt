---
title: Políticas de conformidade de dispositivos do Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre a conformidade de dispositivos do Microsoft Intune
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fb3ec168844708d80c83909ab6c58a52ca62e53c
ms.sourcegitcommit: a22309174e617e59ab0cdd0a55abde38711a5f35
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/23/2018
---
# <a name="get-started-with-microsoft-intune-device-compliance-policies"></a>Começar a utilizar políticas de conformidade de dispositivos do Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

As políticas de conformidade de dispositivos do Intune definem as regras e as definições que um dispositivo tem de cumprir para ser considerado conforme pelo Intune.

Estas regras incluem o seguinte:

- Utilizar uma palavra-passe para aceder a dispositivos

- Encriptação

- Se o dispositivo está desbloqueado por jailbreak ou rooting

- Versão mínima do SO obrigatória

- Versão máxima de SO permitida

- Exigir que o dispositivo esteja ao nível ou abaixo do nível da Defesa Contra Ameaças para Dispositivos Móveis

Também pode utilizar as políticas de conformidade do dispositivo para monitorizar o estado de conformidade nos seus dispositivos.

## <a name="device-compliance-requirements"></a>Requisitos de conformidade do dispositivo

Os requisitos de conformidade são essencialmente regras, como exigir um PIN ou encriptação do dispositivo, que pode especificar como obrigatórias ou não obrigatórias numa política de conformidade.

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

##  <a name="pre-requisites"></a>Pré-requisitos

Tem de ter as seguintes subscrições para utilizar as políticas de conformidade do dispositivo com o Intune:

- Intune

- Azure AD Premium

###  <a name="supported-platforms"></a>Plataformas Suportadas:

-   Android

-   iOS

-   macOS (pré-visualização)

-   Windows 8.1

-   Windows Phone 8.1

-   Windows 10

> [!IMPORTANT]
> Os dispositivos têm de ser inscritos no Intune para comunicarem os respetivos estados de conformidade.

## <a name="how-intune-device-compliance-policies-work-with-azure-ad"></a>De que forma as políticas de conformidade de dispositivos do Intune funcionam com o Azure AD

Quando um dispositivo é inscrito no Intune, é efetuado o processo de registo do Azure AD, o que atualiza os atributos do dispositivo com informações adicionais no Azure AD. Uma das principais informações do dispositivo é o estado de conformidade do dispositivo, que é utilizado pelas políticas de acesso condicional para bloquear ou permitir o acesso a e-mails e outros recursos da empresa.

- Saiba mais sobre o [processo de registo do Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/device-management-introduction).

### <a name="assigning-a-resulting-device-configuration-profile-status"></a>Atribuir um resultado de estado dos perfis de configuração do dispositivo

Se um dispositivo tiver múltiplos perfis de configuração atribuídos e estados de conformidade diferentes para dois ou mais dos perfis de configuração atribuídos, então tem de ser atribuído um único resultado de estado de conformidade. Esta atribuição baseia-se num nível de gravidade concetual atribuído a cada estado de conformidade. Cada estado de conformidade tem o seguinte nível de gravidade:


|Estado  |Gravidade  |
|---------|---------|
|Pending     |1|
|Succeeded     |2|
|Failed     |3|
|Error     |4|

Um resultado de estado de dois ou mais perfis de configuração é então atribuído ao selecionar o nível de gravidade mais elevado de todos os perfis atribuídos a um dispositivo.

Por exemplo, imaginemos que um dispositivo tem três perfis atribuídos: um com o estado Pending (gravidade = 1), outro com o estado Succeeded (gravidade = 2) e um com o estado Error (gravidade = 4). O estado Error tem o nível de gravidade mais elevado, pelo que é atribuído como o resultado do estado de conformidade a todos os três perfis.

### <a name="assigning-an-ingraceperiod-status-for-an-assigned-compliance-policy"></a>Atribuir um estado InGracePeriod a uma política de conformidade atribuída

O estado InGracePeriod de uma política de conformidade é um valor determinado através da combinação do período de tolerância de um dispositivo e do estado real do mesmo em relação à política de conformidade atribuída. 

Mais concretamente, se um dispositivo tiver um estado NonCompliant para uma política de conformidade atribuída e:

- o dispositivo não tiver um período de tolerância atribuído, então o valor atribuído para a política de conformidade é NonCompliant.
- o dispositivo tiver um período de tolerância expirado, então o valor atribuído para a política de conformidade é NonCompliant.
- o dispositivo tiver um período de tolerância futuro, então o valor atribuído para a política de conformidade é InGracePeriod.

A seguinte tabela apresenta um resumo dos pontos anteriores:


|Estado de conformidade real|Valor do período de tolerância atribuído|Estado de conformidade em vigor|
|---------|---------|---------|
|NonCompliant |Sem período de tolerância atribuído |NonCompliant |
|NonCompliant |Data de ontem|NonCompliant|
|NonCompliant |Data de amanhã|InGracePeriod|

Para obter mais informações sobre a monitorização de políticas de conformidade do dispositivo, veja [Monitorizar as Políticas de conformidade do dispositivo do Intune](compliance-policy-monitor.md).

### <a name="assigning-a-resulting-compliance-policy-status"></a>Atribuir um resultado de estado das políticas de conformidade

Se um dispositivo tiver múltiplas políticas de conformidade atribuídas e estados de conformidade diferentes para duas ou mais políticas de conformidade atribuídas, então tem de ser atribuído um único resultado de estado de conformidade. Esta atribuição baseia-se num nível de gravidade concetual atribuído a cada estado de conformidade. Cada estado de conformidade tem o seguinte nível de gravidade: 

|Estado  |Gravidade  |
|---------|---------|
|Unknown     |1|
|NotApplicable     |2|
|Compatível|3|
|InGracePeriod|4|
|NonCompliant|5|
|Error|6|

Um resultado de estado de duas ou mais políticas de conformidade é então determinado ao selecionar o nível de gravidade mais elevado de todas as políticas atribuídas a um dispositivo.
 
Por exemplo, imaginemos que um dispositivo tem três políticas de conformidade atribuídas: uma com o estado Unknown (gravidade = 1), outra com o estado Compliant (gravidade = 3) e uma com o estado InGracePeriod (gravidade = 4). O estado InGracePeriod tem o nível de gravidade mais elevado, pelo que é atribuído como o resultado de estado de conformidade a todos os três perfis.  

##  <a name="ways-to-use-device-compliance-policies"></a>Formas de utilizar as políticas de conformidade de dispositivos

### <a name="with-conditional-access"></a>Com acesso condicional
Pode utilizar a política de conformidade com acesso condicional para permitir que apenas os dispositivos que estejam em conformidade com uma ou mais regras de política de conformidade do dispositivo acedam ao e-mail e a outros recursos empresariais.

### <a name="without-conditional-access"></a>Sem acesso condicional
Também pode utilizar as políticas de conformidade do dispositivo, independentemente do acesso condicional. Quando utilizar políticas de conformidade de forma independente, os dispositivos visados são avaliados e reportados com o respetivo estado de conformidade. Por exemplo, pode obter um relatório sobre o número de dispositivos que não estão encriptados ou quais os dispositivos que têm jailbreak ou root. No entanto, quando utilizar políticas de conformidade de forma independente, não existem restrições de acesso aos recursos da empresa.

Pode implementar a política de conformidade em utilizadores. Quando uma política de conformidade é implementada num utilizador, os dispositivos do utilizador são verificados relativamente à conformidade. Para saber quanto tempo é que os dispositivos móveis demoram a obter uma política após esta ser implementada, veja [Resolver problemas de perfis de dispositivos no Microsoft Intune](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

#### <a name="actions-for-non-compliance"></a>Ações de não conformidade

As ações de não conformidade permitem-lhe configurar uma sequência cronológica de ações que são aplicadas aos dispositivos que não cumprem os critérios da política de conformidade. Para obter mais informações, veja [Ações automáticas de não conformidade](actions-for-noncompliance.md).

##  <a name="using-device-compliance-policies-in-the-intune-classic-portal-vs-azure-portal"></a>Utilizar as políticas de conformidade de dispositivos no portal clássico do Intune em comparação com o portal do Azure

Conheça as principais diferenças para o ajudar na transição para o novo fluxo de trabalho das políticas de conformidade de dispositivos no portal do Azure.

- No portal do Azure, as políticas de conformidade são criadas em separado para cada plataforma suportada.
- No portal clássico do Intune, uma política de conformidade de dispositivos era comum a todas as plataformas suportadas.

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migrate-device-compliance-policies-from-the-intune-classic-portal-to-the-azure-portal"></a>Migrar políticas de conformidade de dispositivos do portal clássico do Intune para o portal do Azure

As políticas de conformidade de dispositivos criadas no [portal clássico do Intune](https://manage.microsoft.com) não aparecem na nova [página do Intune no portal do Azure](https://portal.azure.com). No entanto, continuam a ser direcionadas para os utilizadores e geríveis através do portal clássico do Intune.

Se quiser tirar partido das novas funcionalidades relacionadas com a conformidade de dispositivos no portal do Azure, terá de criar novas políticas de conformidade de dispositivos no próprio portal do Azure. Se atribuir uma nova política de conformidade de dispositivos no portal do Azure a um utilizador a quem também tenha sido atribuída uma política de conformidade de dispositivos do portal clássico do Intune, as políticas de conformidade de dispositivos do Intune no portal do Azure terão precedência sobre as criadas no portal clássico do Intune.

##  <a name="next-steps"></a>Próximos passos

- Crie uma política de conformidade de dispositivos para as seguintes plataformas:

   - [Android](compliance-policy-create-android.md)
   - [Android for Work](compliance-policy-create-android-for-work.md)
   - [iOS](compliance-policy-create-ios.md)
   - [macOS](compliance-policy-create-mac-os.md)
   - [Windows](compliance-policy-create-windows.md)

- Para obter informações sobre as entidades de políticas do Armazém de Dados do Intune, veja [Referência para as entidades de políticas](reports-ref-policy.md).
