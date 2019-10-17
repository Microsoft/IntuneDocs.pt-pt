---
title: Conector da Defesa Contra Ameaças para Dispositivos Móveis do Pradeo com o Intune
titleSuffix: Intune on Azure
description: Saiba como integrar o Intune com o conector de defesa contra ameaças móveis do Pradeo para controlar o acesso de dispositivos móveis aos seus recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: cde4d389-1770-4226-85a3-a2f3b3fb92a3
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 563b117583f8b8c1f4da08d5d4e3399d5939bf97
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504366"
---
# <a name="pradeo-mobile-threat-defense-connector-with-intune"></a>Conector da Defesa Contra Ameaças para Dispositivos Móveis do Pradeo com o Intune

Você pode controlar o acesso de dispositivos móveis a recursos corporativos usando o acesso condicional com base na avaliação de risco realizada pelo Pradeo, uma solução MTD (defesa contra ameaças móveis) que se integra ao Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos a executar a aplicação Pradeo.

Você pode configurar políticas de acesso condicional com base na avaliação de risco do Pradeo habilitada por meio das políticas de conformidade do dispositivo do Intune, que você pode usar para permitir ou bloquear dispositivos não compatíveis para acessar recursos corporativos com base em ameaças detectadas.

## <a name="how-do-intune-and-pradeo-help-protect-your-company-resources"></a>Como é que o Intune e o Pradeo ajudam a proteger os recursos da empresa?

A aplicação Pradeo para Android e iOS captura o sistema de ficheiros, pilha da rede, telemetria da aplicação e do dispositivo sempre que estiverem disponíveis e, em seguida, envia os dados telemétricos para o serviço cloud do Pradeo para avaliar o risco de ameaças contra dispositivos móveis do dispositivo.

A política de conformidade de dispositivos do Intune inclui uma regra para a Defesa Contra Ameaças para Dispositivos Móveis do Pradeo, que se baseia na avaliação de riscos do Pradeo. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou. Caso se verifique que o dispositivo não está em conformidade, será bloqueado o acesso dos utilizadores aos recursos empresariais como o Exchange Online e o SharePoint Online. Os utilizadores também recebem orientações da aplicação Pradeo instalada nos respetivos dispositivos para resolver o problema e recuperar o acesso a recursos empresariais.

## <a name="sample-scenarios"></a>Cenários de exemplo

Seguem-se alguns cenários comuns.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas

Quando forem detetadas aplicações maliciosas, como software maligno, nos dispositivos, pode impedir os dispositivos de fazer as seguintes ações até a ameaça ser resolvida:

- Ligar ao e-mail empresarial

- Sincronizar ficheiros empresariais com a aplicação OneDrive for Work

- Aceder às aplicações da empresa

**Bloquear quando as aplicações maliciosas forem detetadas:**

![Imagem conceitual de aplicativos mal-intencionados detectados](./media/pradeo-mobile-threat-defense-connector/pradeo_maliciousapps_blocked.png)

**Acesso concedido na remediação:**

![Acesso concedido a aplicações maliciosas detetadas](./media/pradeo-mobile-threat-defense-connector/pradeo_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede

Detete ameaças à rede, tal como ataques **Man-in-the-middle**, e proteja o acesso a redes Wi-Fi com base no risco do dispositivo.

**Bloquear o acesso à rede através de Wi-Fi:**

![Bloquear o acesso à rede através de Wi-Fi](./media/pradeo-mobile-threat-defense-connector/pradeo_network_wifi_blocked.png)

**Acesso concedido na remediação:**

![Imagem conceitual do acesso concedido na correção](./media/pradeo-mobile-threat-defense-connector/pradeo_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças à sua rede, tal como ataques **Man-in-the-middle**, e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Bloquear o SharePoint Online quando forem detetadas ameaças à rede:**

![Bloquear o SharePoint Online quando forem detetadas ameaças à rede](./media/pradeo-mobile-threat-defense-connector/pradeo_network_spo_blocked.png)

**Acesso concedido na remediação:**

![Imagem conceitual do acesso concedido na correção para o exemplo do SharePoint](./media/pradeo-mobile-threat-defense-connector/pradeo_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Plataformas suportadas

- **Android 4.0.3 e posterior**

- **iOS 7 e posterior**

## <a name="prerequisites"></a>Pré-requisitos

- Azure Active Directory Premium

- Subscrição do Microsoft Intune

- Segurança do Pradeo para a subscrição da Defesa Contra Ameaças para Dispositivos Móveis

  - Para obter mais informações, consulte o [site do Pradeo](https://www.pradeo.com/en-US/mobile-threat-protection).

## <a name="next-steps"></a>Próximos passos

- [Integrar o Pradeo com o Intune](pradeo-mtd-connector-integration.md)

- [Configurar as aplicações do Pradeo](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Criar uma política de conformidade de dispositivo do Pradeo](mtd-device-compliance-policy-create.md)

- [Ativar o conector de MTD do Pradeo](mtd-connector-enable.md)