---
title: Conformidade do dispositivo
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: utilize este tópico para saber mais sobre a conformidade de dispositivos no Microsoft Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a916fa0d-890d-4efb-941c-7c3c05f8fe7c
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: f316b332c3f1b80b9d6af488943298fcfea13741
ms.openlocfilehash: 8cc5e12308871a3b023bed49e9647b888971f849
ms.lasthandoff: 03/30/2017


---

# <a name="what-is-device-compliance-in-intune-azure-preview"></a>O que é a conformidade de dispositivos na pré-visualização do Azure no Intune?

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

As políticas de conformidade do dispositivo no Intune definem as regras e as definições que um dispositivo tem de cumprir para ser considerado conforme pelas políticas de acesso condicional do Intune e de EMS. Também pode utilizar as políticas de conformidade do dispositivo para monitorizar e resolver problemas de conformidade com dispositivos. 

Estas regras incluem o seguinte:

- Utilizar uma palavra-passe para aceder a dispositivos
- Encriptação
- Se o dispositivo está desbloqueado por jailbreak ou rooting
- Versão mínima do SO obrigatória
- Versão máxima de SO permitida
- Exigir que o dispositivo esteja ao nível ou abaixo do nível da Defesa Contra Ameaças para Dispositivos Móveis

<!---##  Concepts
Following are some terms and concepts that are useful to understanding how to use compliance policies.

### Device compliance requirements
Compliance requirements are essentially rules like requiring a device PIN or encryption that you can specify as required or not required for a compliance policy.

### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be non-compliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

##  <a name="how-should-i-use-a-device-compliance-policy"></a>Como devo utilizar uma política de conformidade de dispositivos?

### <a name="using-ems-conditional-access"></a>Utilizar o acesso condicional de EMS
Pode utilizar a política de conformidade com acesso condicional de EMS para permitir que apenas os dispositivos que estejam em conformidade com uma ou mais regras de política de conformidade do dispositivo acedam ao e-mail e a outros recursos empresariais.

### <a name="not-using-ems-conditional-access"></a>Não utilizar o acesso condicional de EMS
Também pode utilizar as políticas de conformidade do dispositivo, independentemente do acesso condicional de EMS.
Quando utilizar políticas de conformidade de forma independente, os dispositivos visados são avaliados e reportados com o respetivo estado de conformidade. Por exemplo, pode obter um relatório sobre o número de dispositivos que não estão encriptados ou quais os dispositivos que têm jailbreak ou root. No entanto, quando utilizar políticas de conformidade de forma independente, não existem restrições de acesso aos recursos da empresa.

Pode implementar a política de conformidade em utilizadores. Quando uma política de conformidade é implementada num utilizador, os dispositivos do utilizador são verificados relativamente à conformidade. Para saber quanto tempo os dispositivos móveis demoram a obter uma política após a mesma ser implementada, veja Gerir definições e funcionalidades nos seus dispositivos.

##  <a name="intune-classic-admin-console-vs-intune-azure-preview-portal"></a>Consola de administração clássica do Intune vs. Portal de pré-visualização do Azure no Intune

Se tem utilizado a consola de administração clássica do Intune, tenha em consideração as seguintes diferenças para ajudar na transição para o novo fluxo de trabalho da política de conformidade do dispositivo no portal do Azure:

-   No portal do Azure, as políticas de conformidade são criadas em separado para cada plataforma suportada. Na consola de administração do Intune, uma política de conformidade era comum a todas as plataformas suportadas.

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migration-from-intune-classic-console-to-intune-azure-preview-portal"></a>Migração da consola clássica do Intune para o portal de pré-visualização do Azure no Intune

As políticas de conformidade de dispositivos criadas na [consola clássica do Intune](https://manage.microsoft.com) não aparecem no novo [portal do Azure do Intune](https://portal.azure.com). No entanto, continuarão a ser visadas para os utilizadores e geríveis através da consola clássica do Intune.

Se pretender tirar partido das novas funcionalidades relacionadas com a conformidade de dispositivos no portal do Azure no Intune, terá de criar novas políticas de conformidade de dispositivos no próprio portal do Azure do Intune. Se atribuir uma nova política de conformidade de dispositivos no portal do Azure do Intune a um utilizador a quem também tenha sido atribuída uma política de conformidade de dispositivos do portal clássico do Intune, as políticas de conformidade de dispositivos do portal do Azure do Intune terão precedência sobre as criadas na consola clássica do Intune.

##  <a name="next-steps"></a>Próximos passos

[Introdução às políticas de conformidade do dispositivo](get-started-with-device-compliance.md)


<!---### See also

Conditional access--->

