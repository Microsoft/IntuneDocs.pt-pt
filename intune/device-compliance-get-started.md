---
title: "Políticas de conformidade de dispositivos do Intune"
titleSuffix: Azure portal
description: "Utilize este tópico para saber mais sobre a conformidade de dispositivos no Microsoft Intune\""
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a916fa0d-890d-4efb-941c-7c3c05f8fe7c
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1e6d758d10a3527e0dc350115f2f8f10e2c62322
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="get-started-with-intune-device-compliance-policies"></a>Introdução às políticas de conformidade de dispositivos do Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="what-is-device-compliance-in-intune"></a>O que é a conformidade de dispositivos no Intune?

As políticas de conformidade de dispositivos do Intune definem as regras e as definições que um dispositivo tem de cumprir para ser considerado conforme pelo Intune.

Estas regras incluem o seguinte:

- Utilizar uma palavra-passe para aceder a dispositivos

- Encriptação

- Se o dispositivo está desbloqueado por jailbreak ou rooting

- Versão mínima do SO obrigatória

- Versão máxima de SO permitida

- Exigir que o dispositivo esteja ao nível ou abaixo do nível da Defesa Contra Ameaças para Dispositivos Móveis

Também pode utilizar as políticas de conformidade do dispositivo para monitorizar o estado de conformidade nos seus dispositivos.

### <a name="device-compliance-requirements"></a>Requisitos de conformidade do dispositivo

Os requisitos de conformidade são essencialmente regras, como exigir um PIN ou encriptação do dispositivo, que pode especificar como obrigatórias ou não obrigatórias numa política de conformidade.

<!---### Actions for noncompliance

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

##  <a name="pre-requisites"></a>Pré-requisitos

Tem de ter as seguintes subscrições para utilizar as políticas de conformidade do dispositivo com o Intune:

- EMS do Intune

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

- Saiba mais sobre o [processo de registo do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-overview).

##  <a name="ways-to-use-device-compliance-policies"></a>Formas de utilizar as políticas de conformidade de dispositivos

### <a name="with-conditional-access"></a>Com acesso condicional
Pode utilizar a política de conformidade com acesso condicional para permitir que apenas os dispositivos que estejam em conformidade com uma ou mais regras de política de conformidade do dispositivo acedam ao e-mail e a outros recursos empresariais.

### <a name="without-conditional-access"></a>Sem acesso condicional
Também pode utilizar as políticas de conformidade do dispositivo, independentemente do acesso condicional. Quando utilizar políticas de conformidade de forma independente, os dispositivos visados são avaliados e reportados com o respetivo estado de conformidade. Por exemplo, pode obter um relatório sobre o número de dispositivos que não estão encriptados ou quais os dispositivos que têm jailbreak ou root. No entanto, quando utilizar políticas de conformidade de forma independente, não existem restrições de acesso aos recursos da empresa.

Pode implementar a política de conformidade em utilizadores. Quando uma política de conformidade é implementada num utilizador, os dispositivos do utilizador são verificados relativamente à conformidade. Para saber quanto tempo os dispositivos móveis demoram a obter uma política após a mesma ser implementada, veja Gerir definições e funcionalidades nos seus dispositivos.

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

Crie uma política de conformidade de dispositivos para as seguintes plataformas:

- [Android](compliance-policy-create-android.md)
- [Android for Work](compliance-policy-create-android-for-work.md)
- [iOS](compliance-policy-create-ios.md)
- [macOS](compliance-policy-create-mac-os.md)
- [Windows](compliance-policy-create-windows.md)
