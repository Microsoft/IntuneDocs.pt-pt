---
title: Conector Better Mobile Threat Defense com o Intune
titleSuffix: Intune on Azure
description: Configure o conector Better Mobile Threat Defense com o Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: cbab3aae2e38e1ce7d3c8c526b706d70e0cf2b2a
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781211"
---
# <a name="better-mobile-threat-defense-connector-with-intune"></a>Conector Better Mobile Threat Defense com o Intune

Pode controlar o acesso de dispositivos móveis a recursos corporativos utilizando o Acesso Condicional com base na avaliação de risco realizada pela Better Mobile, uma solução de Defesa de Ameaças Móveis (MTD) que se integra com a Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos a executar a aplicação Better Mobile.

Pode configurar políticas de acesso condicional com base na avaliação de risco melhor móvel ativada através de políticas de conformidade de dispositivos intune para dispositivos matriculados, que pode utilizar para permitir ou bloquear dispositivos não conformes para aceder a recursos corporativos com base em detetados ameaças. Para dispositivos não matriculados, pode utilizar políticas de proteção de aplicações para impor um bloco ou limpeza seletiva com base em ameaças detetadas.

## <a name="how-do-intune-and-better-mobile-help-protect-your-company-resources"></a>Como é que o Intune e o Better Mobile ajudam a proteger os recursos da empresa?

A aplicação Better Mobile está instalada e em execução nos dispositivos móveis. Esta aplicação captura o sistema de ficheiros, a pilha de rede e a telemetria de dispositivos e aplicações sempre que estiverem disponíveis e, em seguida, envia os dados para o serviço Better Mobile na cloud para avaliar o risco do dispositivo relativamente a ameaças móveis.

A política de conformidade de dispositivos do Intune inclui uma regra para a Defesa Contra Ameaças para Dispositivos Móveis baseada na avaliação de riscos do Better Mobile. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou. Caso se verifique que o dispositivo não está em conformidade, será bloqueado o acesso dos utilizadores aos recursos empresariais como o Exchange Online e o SharePoint Online. Os utilizadores também recebem orientações da aplicação Better Mobile instalada nos respetivos dispositivos para resolver o problema e recuperar o acesso a recursos empresariais.

## <a name="sample-scenarios"></a>Cenários de exemplo

Seguem-se alguns cenários comuns.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas

Quando forem detetadas aplicações maliciosas, como software maligno, nos dispositivos, pode impedir os dispositivos de fazer as seguintes ações até a ameaça ser resolvida:

- Ligar ao e-mail empresarial

- Sincronizar ficheiros empresariais com a aplicação OneDrive for Work

- Aceder às aplicações da empresa

**Bloquear quando as aplicações maliciosas forem detetadas:**

![Imagem que mostra aplicações maliciosas detetadas](./media/better-mobile-threat-defense-connector/better_mobile_maliciousapps_blocked.png)

**Acesso concedido na remediação:**

![Acesso concedido a aplicações maliciosas detetadas](./media/better-mobile-threat-defense-connector/better_mobile_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede

Detete ameaças à rede, tal como ataques **Man-in-the-middle**, e proteja o acesso a redes Wi-Fi com base no risco do dispositivo.

**Bloquear o acesso à rede através de Wi-Fi:**

![Bloquear o acesso à rede através de Wi-Fi](./media/better-mobile-threat-defense-connector/better_mobile_network_wifi_blocked.png)

**Acesso concedido na remediação:**

![Imagem que mostra acesso concedido na reparação](./media/better-mobile-threat-defense-connector/better_mobile_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças à sua rede, tal como ataques **Man-in-the-middle**, e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Bloquear o SharePoint Online quando forem detetadas ameaças à rede:**

![Bloquear o SharePoint Online quando forem detetadas ameaças à rede](./media/better-mobile-threat-defense-connector/better_mobile_network_spo_blocked.png)

**Acesso concedido na remediação:**

![Exemplo de acesso concedido na remediação para o SharePoint](./media/better-mobile-threat-defense-connector/better_mobile_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Plataformas suportadas

- **Android 4.1 e posterior**

- **iOS 8.0 e posterior**

## <a name="prerequisites"></a>Pré-requisitos

- Azure Active Directory Premium

- Subscrição do Microsoft Intune

- Subscrição do Better Mobile Threat Defense

  - Para obter mais informações, veja o [site do Better Mobile](https://www.better.mobi/).

## <a name="next-steps"></a>Próximos passos

- [Integrar o Better Mobile com o Intune](better-mobile-mtd-connector-integration.md)

- [Configurar aplicações do Better Mobile](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Criar a política de conformidade de dispositivos do Better Mobile](mtd-device-compliance-policy-create.md)

- [Ativar o conector Better Mobile MTD](mtd-connector-enable.md)

- [Criar uma política de proteção de aplicações MTD](mtd-app-protection-policy.md) 
