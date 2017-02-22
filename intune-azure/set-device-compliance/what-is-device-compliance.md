---
title: "Conformidade de dispositivos | Pré-visualização do Azure no Intune | Documentos da Microsoft"
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
translationtype: Human Translation
ms.sourcegitcommit: 7693d49e2f0fa6e4aa40b6bb71433a7eaab8dd15
ms.openlocfilehash: a4254503e4e6b86079f862966dee2727934f1ee6


---

# <a name="what-is-device-compliance-in-intune-azure-preview"></a>O que é a conformidade de dispositivos na pré-visualização do Azure no Intune?


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Para ajudar a proteger dados da empresa, tem de garantir que os dispositivos utilizados para aceder às aplicações e aos dados da empresa cumprem determinadas regras. As regras incluem a utilização de um PIN para aceder a dispositivos e encriptar dados armazenados em dispositivos. Um conjunto dessas regras denomina-se **política de conformidade**.

##  <a name="how-should-i-use-a-device-compliance-policy"></a>Como devo utilizar uma política de conformidade de dispositivos?
Pode utilizar a política de conformidade com acesso condicional para permitir que apenas os dispositivos que estejam em conformidade com as regras de política de conformidade acedam a e-mail e outros serviços.

Também pode utilizar a política de conformidade independentemente do acesso condicional.
Quando utilizar políticas de conformidade de forma independente, os dispositivos visados são avaliados e reportados com o respetivo estado de conformidade. Por exemplo, pode obter um relatório sobre o número de dispositivos que não estão encriptados ou quais os dispositivos que têm jailbreak ou root. No entanto, quando utilizar políticas de conformidade de forma independente, não existem restrições de acesso aos recursos da empresa.

Pode implementar a política de conformidade em utilizadores. Quando uma política de conformidade é implementada num utilizador, os dispositivos do utilizador são verificados relativamente à conformidade. Para saber quanto tempo os dispositivos móveis demoram a obter uma política após a mesma ser implementada, veja Gerir definições e funcionalidades nos seus dispositivos.

##  <a name="concepts"></a>Conceitos
Seguem-se alguns termos e conceitos que são úteis para compreender a utilização de políticas de conformidade.

### <a name="compliance-requirements"></a>Requisitos de conformidade
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

##  <a name="differences-between-the-classic-intune-admin-console-and-intune-in-the-azure-portal"></a>Diferenças entre a consola de administração clássica do Intune e o Intune no portal do Azure


Se tem utilizado a consola de administração clássica do Intune, tenha em atenção as seguintes diferenças para ajudar na transição para o novo fluxo de trabalho de conformidade de dispositivos no portal do Azure:


-   No portal do Azure, as políticas de conformidade são criadas em separado para cada plataforma suportada. Na consola de administração do Intune, uma política de conformidade era comum a todas as plataformas suportadas.


<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="next-steps"></a>Próximos passos

[Introdução às políticas de conformidade](get-started-with-device-compliance.md)


<!---### See also

Conditional access--->



<!--HONumber=Feb17_HO1-->


