---
title: Conector da Defesa Contra Ameaças para Dispositivos Móveis do Pradeo com o Intune
titleSuffix: Intune on Azure
description: Configure o conector da Defesa Contra Ameaças para Dispositivos Móveis do Pradeo com o Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: cde4d389-1770-4226-85a3-a2f3b3fb92a3
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 129e9df21a922fccfe380babe7034ec475c4fc70
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61512161"
---
# <a name="pradeo-mobile-threat-defense-connector-with-intune"></a>Conector da Defesa Contra Ameaças para Dispositivos Móveis do Pradeo com o Intune

Pode controlar o acesso a recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Pradeo, uma solução de Defesa Contra Ameaças para Dispositivos Móveis (MTD) que está integrada com o Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos a executar a aplicação Pradeo.

Pode configurar políticas de acesso condicional baseadas na avaliação de riscos do Pradeo, que é ativada através das políticas de conformidade de dispositivos do Intune, as quais pode utilizar para permitir ou impedir que os dispositivos não conformes acedam aos recursos da empresa com base nas ameaças detetadas.

## <a name="how-do-intune-and-pradeo-help-protect-your-company-resources"></a>Como é que o Intune e o Pradeo ajudam a proteger os recursos da empresa?

A aplicação Pradeo para Android e iOS captura o sistema de ficheiros, pilha da rede, telemetria da aplicação e do dispositivo sempre que estiverem disponíveis e, em seguida, envia os dados telemétricos para o serviço cloud do Pradeo para avaliar o risco de ameaças contra dispositivos móveis do dispositivo.

A política de conformidade de dispositivos do Intune inclui uma regra para a Defesa Contra Ameaças para Dispositivos Móveis do Pradeo, que se baseia na avaliação de riscos do Pradeo. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou. Caso se verifique que o dispositivo não está em conformidade, será bloqueado o acesso dos utilizadores aos recursos empresariais como o Exchange Online e o SharePoint Online. Os utilizadores também recebem orientações da aplicação Pradeo instalada nos respetivos dispositivos para resolver o problema e recuperar o acesso a recursos empresariais.

## <a name="sample-scenarios"></a>Cenários de exemplo

Seguem-se alguns cenários comuns.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas

Quando forem detetadas aplicações maliciosas, como software maligno, nos dispositivos, pode impedir os dispositivos de fazer as seguintes ações até a ameaça ser resolvida:

-   Ligar ao e-mail empresarial

-   Sincronizar ficheiros empresariais com a aplicação OneDrive for Work

-   Aceder às aplicações da empresa

**Bloquear quando as aplicações maliciosas forem detetadas:**

![Imagem conceptual de aplicações maliciosas detetadas](./media/pradeo_maliciousapps_blocked.png)

**Acesso concedido na remediação:**

![Acesso concedido a aplicações maliciosas detetadas](./media/pradeo_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede

Detete ameaças à rede, tal como ataques **Man-in-the-middle**, e proteja o acesso a redes Wi-Fi com base no risco do dispositivo.

**Bloquear o acesso à rede através de Wi-Fi:**

![Bloquear o acesso à rede através de Wi-Fi](./media/pradeo_network_wifi_blocked.png)

**Acesso concedido na remediação:**

![Imagem conceptual de acesso concedido na remediação](./media/pradeo_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças à sua rede, tal como ataques **Man-in-the-middle**, e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Bloquear o SharePoint Online quando forem detetadas ameaças à rede:**

![Bloquear o SharePoint Online quando forem detetadas ameaças à rede](./media/pradeo_network_spo_blocked.png)

**Acesso concedido na remediação:**

![Imagem conceptual de acesso concedido na remediação, por exemplo, Sharepoint](./media/pradeo_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Plataformas suportadas

-   **Android 4.0.3 e posterior**

-   **iOS 7 e posterior**

## <a name="prerequisites"></a>Pré-requisitos

-   Azure Active Directory Premium

-   Subscrição do Microsoft Intune

-   Segurança do Pradeo para a subscrição da Defesa Contra Ameaças para Dispositivos Móveis

    -   Para obter mais informações, consulte o [site do Pradeo](https://www.pradeo.com/en-US/mobile-threat-protection).

## <a name="next-steps"></a>Passos Seguintes

- [Integrar o Pradeo com o Intune](pradeo-mtd-connector-integration.md)

- [Configurar as aplicações do Pradeo](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Criar uma política de conformidade de dispositivo do Pradeo](mtd-device-compliance-policy-create.md)

- [Ativar o conector de MTD do Pradeo](mtd-connector-enable.md)
