---
title: Conector do Check Point SandBlast Mobile no Intune
titlesuffix: Azure portal
description: "Integração do Check Point SandBlast com o Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 706a4228-9bdf-41e0-b8d1-64c923dd2d2b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d528ee9b72b5b7476845c0051f67f8a6ed887d1c
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="check-point-sandblast-mobile-threat-defense-connector-with-intune"></a>Conector de Defesa Contra Ameaças do Check Point SandBlast Mobile no Intune

Pode controlar o acesso a recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Check Point SandBlast Mobile, uma solução de defesa contra ameaças para dispositivos móveis que está integrada com o Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos que executam a aplicação Check Point SandBlast Mobile.

Pode configurar políticas de acesso condicional baseadas na avaliação de riscos do Check Point SandBlast Mobile, que é ativada através de políticas de conformidade de dispositivos do Intune, as quais pode utilizar para permitir ou impedir que os dispositivos não conformes acedam aos recursos da empresa com base em ameaças detetadas.

## <a name="how-do-intune-and-check-point-sandblast-mobile-help-protect-your-company-resources"></a>De que forma o Intune e o Check Point SandBlast Mobile ajudam a proteger os recursos da sua empresa?

A aplicação Check Point Sandblast Mobile para Android e iOS captura o sistema de ficheiros, pilha da rede, telemetria aplicacional e do dispositivo sempre que estiverem disponíveis e, em seguida, envia os dados telemétricos para o serviço cloud do Check Point SandBlast para avaliar o risco de ameaças contra dispositivos móveis do dispositivo.

A política de conformidade do dispositivo do Intune inclui uma regra para a Defesa Contra Ameaças do Check Point SandBlast Mobile, que é baseada na avaliação de riscos do Check Point SandBlast. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou. Caso se verifique que o dispositivo não está em conformidade, será bloqueado o acesso dos utilizadores aos recursos empresariais como o Exchange Online e o SharePoint Online. Os utilizadores também recebem orientações da aplicação Check Point SandBlast Mobile instalada nos respetivos dispositivos para resolver o problema e recuperar o acesso a recursos empresariais.

<!-- ## Sample scenarios

Here are some common scenarios:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

-   Connecting to corporate e-mail

-   Syncing corporate files with the OneDrive for Work app

-   Accessing company apps

**Block when malicious apps are detected:**

![Check Point MTD block when malicious apps are detected](./media/checkpoint-MTD-2.PNG)

**Access granted on remediation:**

![Check Point MTD access granted](./media/checkpoint-MTD-3.PNG)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

**Block network access through Wi-Fi:**

![Check Point MTD block network access through Wi-Fi](./media/checkpoint-MTD-4.PNG)

**Access granted on remediation:**

![Check Point MTD Wi-Fi access granted](./media/checkpoint-MTD-5.PNG)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network, and prevent synchronization of corporate files based on the device risk.

**Block SharePoint Online when network threats are detected:**

![Check Point MTD block SharePoint Online access](./media/checkpoint-MTD-6.PNG)

**Access granted on remediation:**

![Check Point MTD SharePoint Online access granted](./media/checkpoint-MTD-7.PNG)

## Supported platforms

-   **Android 4.1 and later**

-   **iOS 8 and later**

## Pre-requisites

-   Azure Active Directory Premium

-   Microsoft Intune subscription

-   Check Point SandBlast Mobile Threat Defense subscription
    -   See [CheckPoint SandBlast website](https://www.checkpoint.com/) for more information.

## Next steps

- [Integrate CheckPoint SandBlast with Intune](checkpoint-sandblast-mobile-mtd-connector-integration.md)

- [Set up CheckPoint SandBlast Mobile app](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Create CheckPoint SandBlast Mobile device compliance policy](mtd-device-compliance-policy-create.md)

- [Enable CheckPoint SandBlast Mobile MTD connector](mtd-connector-enable.md)
