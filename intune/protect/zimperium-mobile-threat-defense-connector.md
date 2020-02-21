---
title: Conector de MTD Zimperium com o Intune
titleSuffix: Intune on Azure
description: Saiba como integrar o Intune com a solução de Defesa Contra Ameaças do Zimperium para controlar o acesso aos recursos empresariais a partir de dispositivos móveis.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/29/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d0fe5634e5af6ef4c6f19e067131f151733c0b5
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515242"
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Conector Zimperium Mobile Threat Defense com o Intune

Pode controlar o acesso de dispositivos móveis a recursos corporativos utilizando o Acesso Condicional com base na avaliação de risco realizada pela Zimperium, uma solução de Defesa de Ameaças Móveis (MTD) que se integra com a Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos a executar a aplicação Zimperium.

Pode configurar políticas de Acesso Condicional com base na avaliação de risco zimperium ativada através de políticas de conformidade do dispositivo Intune. A política de avaliação de riscos pode permitir ou bloquear dispositivos não conformes de aceder a recursos corporativos com base em ameaças detetadas.

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>Como é que o Intune e o Zimperium ajudam a proteger os recursos da empresa?

A aplicação zimperium para Android e iOS/iPadOS captura sistema de ficheiros, stack de rede, dispositivo e telemetria de aplicações sempre que disponível, envia depois os dados de telemetria para o serviço de nuvem Zimperium para avaliar o risco do dispositivo para ameaças móveis.

A política de conformidade de dispositivos do Intune inclui uma regra para o Zimperium Mobile Threat Defense, que se baseia na avaliação de riscos do Zimperium. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou. Caso se verifique que o dispositivo não está em conformidade, será bloqueado o acesso dos utilizadores aos recursos empresariais como o Exchange Online e o SharePoint Online. Os utilizadores também recebem orientações da aplicação Zimperium instalada nos respetivos dispositivos para resolver o problema e recuperar o acesso a recursos empresariais.

## <a name="sample-scenarios"></a>Cenários de exemplo

Veja abaixo alguns cenários que ocorrem quando integra o Zimperium com o Intune:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas

Quando forem detetadas aplicações maliciosas, como software maligno, nos dispositivos, pode bloquear os dispositivos até a ameaça ser resolvida:

- Ligar ao e-mail empresarial

- Sincronizar ficheiros empresariais com a aplicação OneDrive for Work

- Aceder às aplicações da empresa

**Bloquear quando as aplicações maliciosas forem detetadas:**

![Imagem conceptual de aplicações maliciosas detetada](./media/zimperium-mobile-threat-defense-connector/Maliciousapps_blocked_Zimperium.png)

**Acesso concedido na remediação:**

![Imagem conceptual de acesso concedida após remediação](./media/zimperium-mobile-threat-defense-connector/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede

Detete ameaças como **Man-in-the-middle** na rede e proteja o acesso às redes Wi-Fi com base no risco do dispositivo.

**Bloquear o acesso à rede através de Wi-Fi:**

![Bloquear o acesso à rede através de Wi-Fi](./media/zimperium-mobile-threat-defense-connector/network_wifi_blocked_Zimperium.png)

**Acesso concedido na remediação:**

![Acesso concedido na remediação](./media/zimperium-mobile-threat-defense-connector/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças na rede, tais como ataques **Man-in-the-middle**, e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Bloquear o SharePoint Online quando forem detetadas ameaças à rede:**

![Bloquear o SharePoint Online quando forem detetadas ameaças à rede](./media/zimperium-mobile-threat-defense-connector/network_spo_blocked_Zimperium.png)

**Acesso concedido na remediação:**

![Exemplo de acesso concedido na remediação para o SharePoint](./media/zimperium-mobile-threat-defense-connector/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>Plataformas suportadas

- **Android 4.1 e posterior**

- **iOS 8 e posterior**

## <a name="prerequisites"></a>Pré-requisitos

- Azure Active Directory Premium

- Subscrição do Microsoft Intune

- Subscrição do Zimperium Mobile Threat Defense

  - Para mais informações, consulte [o site da Zimperium.](https://www.zimperium.com/zips-mobile-ips)

## <a name="next-steps"></a>Próximos passos

- [Integrar o Zimperium com o Intune](zimperium-mtd-connector-integration.md)

- [Configurar aplicações do Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Criar a política de conformidade de dispositivos do Zimperium](mtd-device-compliance-policy-create.md)

- [Ativar o conector Zimperium MTD](mtd-connector-enable.md)
