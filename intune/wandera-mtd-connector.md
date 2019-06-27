---
title: Configurar a segurança do Mobile Wandera com o Intune
titleSuffix: Intune on Azure
description: Como configurar a segurança do Mobile Wandera com o Microsoft Intune para controlar o acesso de dispositivos móveis aos seus recursos empresariais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6219d4a176eebf81747461b3cc8b478e46e86898
ms.sourcegitcommit: 6bba9f2ef4d1ec699f5713a4da4f960e7317f1cd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2019
ms.locfileid: "67407693"
---
# <a name="wandera-mobile-threat-defense-connector-with-intune"></a>Conector de Wandera Mobile Threat Defense com o Intune  

Controlar o acesso aos recursos da empresa através do acesso condicional com base na avaliação de riscos realizada pelo Wandera dispositivos móveis. Wandera é uma solução de defesa contra ameaças móveis (MTD) que se integra com o Microsoft Intune.  O risco é avaliado com base na telemetria recolhida dos dispositivos através do serviço de Wandera, incluindo:
- Vulnerabilidades do sistema operativo
- Aplicações maliciosas instaladas
- Perfis de rede maliciosos
- Cryptojacking

Pode configurar *acesso condicional* corre o risco de políticas que se baseiam em Wandera avaliação, ativada através de políticas de conformidade de dispositivos do Intune. Política de avaliação de risco pode permitir ou bloquear dispositivos não conformes acedam a recursos empresariais com base em ameaças detetadas.  


## <a name="how-do-intune-and-wandera-mobile-threat-defense-help-protect-your-company-resources"></a>Como é o Intune e Wandera Mobile Threat Defense ajudam a proteger os seus recursos da empresa?  

Aplicação móvel do Wandera instala forma totalmente integrada com o Microsoft Intune. Esta aplicação captura o sistema de ficheiros, a pilha de rede e a telemetria de aplicações e dispositivos (onde disponível). Estas informações são sincronizadas para o serviço de nuvem de Wandera para avaliar o risco do dispositivo para ameaças contra dispositivos móveis. Estas classificações de nível de risco são configuráveis para se adequar às suas necessidades na consola do Wandera, RADAR.

A política de conformidade no Intune inclui uma regra para MTD com base na avaliação de riscos do Wandera. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou.

Para dispositivos que não estão em conformidades, acesso a recursos como o Office 365 pode ser bloqueado. Os utilizadores com dispositivos bloqueados recebem orientações da aplicação Wandera para resolver o problema e recuperar o acesso.

## <a name="supported-platforms"></a>Plataformas suportadas  

As seguintes plataformas são suportadas para Wandera quando inscritos no Intune:

- Android 5.0 e posterior  
- iOS 10.2 e posterior  

Para obter mais informações sobre a plataforma e dispositivo, consulte a [Wandera site](https://www.wandera.com/why-wandera/features/device-support/).

## <a name="prerequisites"></a>Pré-requisitos  

- Subscrição do Microsoft Intune  
- Azure Active Directory  
- Wandera Mobile Threat Defense (anteriormente conhecido como Wandera Secure)  

Para obter mais informações, consulte [Wandera Mobile Security](https://www.wandera.com/mobile-security/).
 
## <a name="sample-scenarios"></a>Cenários de exemplo

Aqui estão os cenários comuns ao utilizar Wandera MTD com o Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas  

Quando são detetadas aplicações maliciosas como software maligno nos dispositivos, pode bloquear a ferramentas comuns de dispositivos até que pode resolver a ameaça. Blocos comuns incluem:  
- Ligar ao e-mail empresarial  
- Sincronizar ficheiros empresariais com a aplicação OneDrive for Work  
- Aceder às aplicações da empresa  

**Bloquear quando forem detetadas aplicações maliciosas**:

![Imagem conceptual de aplicações maliciosas detetadas](./media/wandera-mtd-connector/wandera-malicious-apps-blocked.png)  

**Acesso concedido na remediação**: 

![Imagem conceptual de acesso concedido após a remediação](./media/wandera-mtd-connector/wandera-malicious-apps-unblocked.png)


### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede  

Detete ameaças à rede, tal como ataques man-in-the-middle e Proteja o acesso a redes Wi-Fi com base no risco do dispositivo.  

**Bloquear o acesso de rede através de Wi-Fi**:  

![Bloquear o acesso à rede através de Wi-Fi](./media/wandera-mtd-connector/wandera-network-wifi-blocked.png)

**Acesso concedido na remediação**:  

![Acesso concedido na remediação](./media/wandera-mtd-connector/wandera-network-wifi-unblocked.png)  

## <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças à sua rede, tal como ataques Man-in-the-middle e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Bloquear o SharePoint Online quando forem detetadas ameaças à rede**:  

![Bloquear o SharePoint Online quando forem detetadas ameaças à rede](./media/wandera-mtd-connector/wandera-network-spo-blocked.png)  


**Acesso concedido na remediação**:  

![Acesso concedido na remediação, por exemplo, SharePoint](./media/wandera-mtd-connector/wandera-network-spo-unblocked.png)  

## <a name="next-steps"></a>Passos Seguintes

- [Integrar Wandera com o Intune](Wandera-mtd-connector-integration.md)
- [Configurar as aplicações de Wandera](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Criar política de conformidade do dispositivo Wandera](mtd-device-compliance-policy-create.md)
- [Ativar o conector de Wandera MTD](mtd-connector-enable.md)