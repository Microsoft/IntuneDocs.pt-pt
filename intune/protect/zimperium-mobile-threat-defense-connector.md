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
ms.openlocfilehash: b4ff350bd8c1c16eedd30a6b7af4f3927bce3c3e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72508764"
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Conector Zimperium Mobile Threat Defense com o Intune

Você pode controlar o acesso de dispositivos móveis a recursos corporativos usando o acesso condicional com base na avaliação de risco realizada pelo Zimperium, uma solução MTD (defesa contra ameaças móveis) que se integra ao Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos a executar a aplicação Zimperium.

Você pode configurar políticas de acesso condicional com base na avaliação de risco do Zimperium habilitada por meio das políticas de conformidade do dispositivo do Intune. A política de avaliação de risco pode permitir ou impedir que dispositivos não compatíveis acessem recursos corporativos com base em ameaças detectadas.

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>Como é que o Intune e o Zimperium ajudam a proteger os recursos da empresa?

A aplicação Zimperium para Android e iOS captura o sistema de ficheiros, pilha da rede, telemetria da aplicação e do dispositivo sempre que estiverem disponíveis e, em seguida, envia os dados telemétricos para o serviço cloud do Zimperium para avaliar o risco de ameaças contra dispositivos móveis do dispositivo.

A política de conformidade de dispositivos do Intune inclui uma regra para o Zimperium Mobile Threat Defense, que se baseia na avaliação de riscos do Zimperium. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou. Caso se verifique que o dispositivo não está em conformidade, será bloqueado o acesso dos utilizadores aos recursos empresariais como o Exchange Online e o SharePoint Online. Os utilizadores também recebem orientações da aplicação Zimperium instalada nos respetivos dispositivos para resolver o problema e recuperar o acesso a recursos empresariais.

## <a name="sample-scenarios"></a>Cenários de exemplo

Veja abaixo alguns cenários que ocorrem quando integra o Zimperium com o Intune:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas

Quando forem detetadas aplicações maliciosas, como software maligno, nos dispositivos, pode bloquear os dispositivos até a ameaça ser resolvida:

- Ligar ao e-mail empresarial

- Sincronizar ficheiros empresariais com a aplicação OneDrive for Work

- Aceder às aplicações da empresa

**Bloquear quando as aplicações maliciosas forem detetadas:**

![Imagem conceitual de aplicativos mal-intencionados detectados](./media/zimperium-mobile-threat-defense-connector/Maliciousapps_blocked_Zimperium.png)

**Acesso concedido na remediação:**

![Imagem conceitual de acesso concedido após a correção](./media/zimperium-mobile-threat-defense-connector/maliciousapps_unblocked_Zimperium.png)

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

  - Para obter mais informações, consulte o [site do Zimperium](https://www.zimperium.com/zips-mobile-ips).

## <a name="next-steps"></a>Próximos passos

- [Integrar o Zimperium com o Intune](zimperium-mtd-connector-integration.md)

- [Configurar aplicações do Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Criar a política de conformidade de dispositivos do Zimperium](mtd-device-compliance-policy-create.md)

- [Ativar o conector Zimperium MTD](mtd-connector-enable.md)
