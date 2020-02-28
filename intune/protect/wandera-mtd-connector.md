---
title: Configurar a Wandera Mobile Security com Intune
titleSuffix: Intune on Azure
description: Como configurar o Wandera Mobile Security com a Microsoft Intune para controlar o acesso de dispositivos móveis aos seus recursos corporativos.
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
ms.openlocfilehash: f82a64cdb66528e3e1d3a81fd6119c4a99dff504
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782266"
---
# <a name="wandera-mobile-threat-defense-connector-with-intune"></a>Conector de Defesa de Ameaças Móveis Wandera com Intune  

Controlar o acesso de dispositivos móveis aos recursos corporativos utilizando acesso condicional com base na avaliação de risco realizada pela Wandera. Wandera é uma solução de Defesa de Ameaças Móveis (MTD) que se integra com a Microsoft Intune.  O risco é avaliado com base na telemetria recolhida a partir de dispositivos pelo serviço Wandera, incluindo:
- Vulnerabilidades do sistema operativo
- Aplicações maliciosas instaladas
- Perfis de rede maliciosos
- Criptojacking

Pode configurar políticas de *acesso condicional* baseadas na avaliação de risco da Wandera, ativadas através de políticas de conformidade do dispositivo Intune. A política de avaliação de riscos pode permitir ou bloquear dispositivos não conformes de aceder a recursos corporativos com base em ameaças detetadas.  

> [!NOTE]
> Este fornecedor de Defesa de Ameaças Móveis não é suportado para dispositivos não matriculados.

## <a name="how-do-intune-and-wandera-mobile-threat-defense-help-protect-your-company-resources"></a>Como é que a Intune e a Wandera Mobile Threat Defense ajudam a proteger os recursos da sua empresa?  

A aplicação móvel da Wandera instala-se sem problemas usando o Microsoft Intune. Esta aplicação captura sistema de ficheiros, pilha de rede e telemetria de dispositivos e aplicações (sempre que disponível). Esta informação sincroniza-se com o serviço de nuvem Wandera para avaliar o risco do dispositivo para ameaças móveis. Estas classificações de nível de risco são configuráveis para atender às suas necessidades na consola Wandera, RADAR.

A política de conformidade em Intune inclui uma regra para mTD baseada na avaliação de risco da Wandera. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou.

Para dispositivos que não sejam conformes, o acesso a recursos como o Office 365 pode ser bloqueado. Os utilizadores de dispositivos bloqueados recebem orientação da app Wandera para resolver o problema e recuperar o acesso.

## <a name="supported-platforms"></a>Plataformas suportadas  

As seguintes plataformas são suportadas para Wandera quando matriculadas em Intune:

- Android 5.0 e mais tarde  
- iOS 10.2 e mais tarde  

Para mais informações sobre plataforma e dispositivo, consulte o [site wandera.](https://www.wandera.com/mobile-threat-defense/)

## <a name="prerequisites"></a>Pré-requisitos  

- Subscrição do Microsoft Intune  
- Azure Active Directory  
- Wandera Mobile Threat Defense (anteriormente Wandera Secure)  

Para mais informações, consulte [Wandera Mobile Security](https://www.wandera.com/mobile-security/).
 
## <a name="sample-scenarios"></a>Cenários de exemplo

Aqui estão os cenários comuns ao usar Wandera MTD com Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas  

Quando aplicações maliciosas como malware são detetadas em dispositivos, pode bloquear dispositivos a partir de ferramentas comuns até que possa resolver a ameaça. Os blocos comuns incluem:  
- Ligar ao e-mail empresarial  
- Sincronizar ficheiros empresariais com a aplicação OneDrive for Work  
- Aceder às aplicações da empresa  

**Bloqueie quando forem detetadas aplicações maliciosas:**

![Imagem conceptual de aplicações maliciosas detetada](./media/wandera-mtd-connector/wandera-malicious-apps-blocked.png)  

**Acesso concedido à reparação:** 

![Imagem conceptual de acesso concedida após remediação](./media/wandera-mtd-connector/wandera-malicious-apps-unblocked.png)


### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede  

Detete ameaças à sua rede, tais como ataques man-in-the-middle e proteja o acesso a redes Wi-Fi com base no risco do dispositivo.  

**Bloquear o acesso à rede através do Wi-Fi:**  

![Bloquear o acesso à rede através de Wi-Fi](./media/wandera-mtd-connector/wandera-network-wifi-blocked.png)

**Acesso concedido à reparação:**  

![Acesso concedido na remediação](./media/wandera-mtd-connector/wandera-network-wifi-unblocked.png)  

## <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças à sua rede, tal como ataques Man-in-the-middle e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Block SharePoint Online quando as ameaças de rede são detetadas:**  

![Bloquear o SharePoint Online quando forem detetadas ameaças à rede](./media/wandera-mtd-connector/wandera-network-spo-blocked.png)  


**Acesso concedido à reparação:**  

![Acesso concedido na reparação por exemplo do SharePoint](./media/wandera-mtd-connector/wandera-network-spo-unblocked.png)  

## <a name="next-steps"></a>Próximos passos

- [Integrar Wandera com Intune](wandera-mtd-connector-integration.md)
- [Configurar aplicativos Wandera](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Criar a política de conformidade do dispositivo Wandera](mtd-device-compliance-policy-create.md)
- [Ativar o conector Wandera MTD](mtd-connector-enable.md)
