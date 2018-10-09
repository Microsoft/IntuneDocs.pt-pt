---
title: MTD do Check Point SandBlast com o Microsoft Intune
titlesuffix: ''
description: Saiba como integrar o Intune com a solução de Defesa Contra Ameaças Check Point SandBlast Mobile para controlar o acesso aos seus recursos empresariais a partir de dispositivos móveis.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 706a4228-9bdf-41e0-b8d1-64c923dd2d2b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5766c4ebe7b261356248b00d0ca2d8937d3db79a
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231532"
---
# <a name="check-point-sandblast-mobile-threat-defense-connector-with-intune"></a>Conector de Defesa Contra Ameaças do Check Point SandBlast Mobile no Intune

Pode controlar o acesso a recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Check Point SandBlast Mobile, uma solução de defesa contra ameaças para dispositivos móveis que está integrada com o Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos que executam a aplicação Check Point SandBlast Mobile.

Pode configurar políticas de acesso condicional baseadas na avaliação de riscos do Check Point SandBlast Mobile, que é ativada através de políticas de conformidade de dispositivos do Intune, as quais pode utilizar para permitir ou impedir que os dispositivos não conformes acedam aos recursos da empresa com base em ameaças detetadas.

## <a name="how-do-intune-and-check-point-sandblast-mobile-help-protect-your-company-resources"></a>De que forma o Intune e o Check Point SandBlast Mobile ajudam a proteger os recursos da sua empresa?

A aplicação Check Point Sandblast Mobile para Android e iOS captura o sistema de ficheiros, pilha da rede, telemetria aplicacional e do dispositivo sempre que estiverem disponíveis e, em seguida, envia os dados telemétricos para o serviço cloud do Check Point SandBlast para avaliar o risco de ameaças contra dispositivos móveis do dispositivo.

A política de conformidade do dispositivo do Intune inclui uma regra para a Defesa Contra Ameaças do Check Point SandBlast Mobile, que é baseada na avaliação de riscos do Check Point SandBlast. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou. Caso se verifique que o dispositivo não está em conformidade, será bloqueado o acesso dos utilizadores aos recursos empresariais como o Exchange Online e o SharePoint Online. Os utilizadores também recebem orientações da aplicação Check Point SandBlast Mobile instalada nos respetivos dispositivos para resolver o problema e recuperar o acesso a recursos empresariais.

<!-- ## Sample scenarios 
closing syntax for comment above is missing. Please insert closing syntax at intended location. -->

Seguem-se alguns cenários comuns:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas

Quando forem detetadas aplicações maliciosas, como software maligno, nos dispositivos, pode bloquear os dispositivos até a ameaça ser resolvida:

-   Ligar ao e-mail empresarial

-   Sincronizar ficheiros empresariais com a aplicação OneDrive for Work

-   Aceder às aplicações da empresa

**Bloquear quando as aplicações maliciosas forem detetadas:**

![MTD do Check Point – bloqueio quando as aplicações maliciosas são detetadas](./media/checkpoint-MTD-2.PNG)

**Acesso concedido na remediação:**

![MTD do Check Point – acesso concedido](./media/checkpoint-MTD-3.PNG)

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede

Detete ameaças como **Man-in-the-middle** na rede e proteja o acesso às redes Wi-Fi com base no risco do dispositivo.

**Bloquear o acesso à rede através de Wi-Fi:**

![MTD do Check Point – bloqueio do acesso à rede através de Wi-Fi](./media/checkpoint-MTD-4.PNG)

**Acesso concedido na remediação:**

![MTD do Check Point – acesso Wi-Fi concedido](./media/checkpoint-MTD-5.PNG)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças na rede, tais como ataques **Man-in-the-middle**, e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Bloquear o SharePoint Online quando forem detetadas ameaças à rede:**

![MTD do Check Point – bloqueio do acesso ao SharePoint Online](./media/checkpoint-MTD-6.PNG)

**Acesso concedido na remediação:**

![MTD do Check Point – acesso ao SharePoint Online concedido](./media/checkpoint-MTD-7.PNG)

## <a name="supported-platforms"></a>Plataformas suportadas

-   **Android 4.1 e posterior**

-   **iOS 8 e posterior**

## <a name="pre-requisites"></a>Pré-requisitos

-   Azure Active Directory Premium

-   Subscrição do Microsoft Intune

-   Subscrição do Check Point SandBlast Mobile – Defesa Contra Ameaças
    -   Veja o [site do Check Point SandBlast](https://www.checkpoint.com/) para obter mais informações.

## <a name="next-steps"></a>Próximos passos

- [Integrar o Check Point SandBlast com o Intune](checkpoint-sandblast-mobile-mtd-connector-integration.md)

- [Configurar a aplicação Check Point SandBlast Mobile](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Criar a política de conformidade de dispositivos do CheckPoint SandBlast Mobile](mtd-device-compliance-policy-create.md)

- [Ativar o conector da MTD do CheckPoint SandBlast Mobile](mtd-connector-enable.md)
