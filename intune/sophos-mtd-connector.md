---
title: Configurar a integração do Sophos Mobile com o Intune
titleSuffix: Intune on Azure
description: Como configurar a solução de Sophos Mobile com o Microsoft Intune para controlar o acesso de dispositivos móveis aos seus recursos empresariais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4363bb4feba52c15b8918a7c6ea02fa2917a00de
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66044948"
---
# <a name="sophos-mobile-threat-defense-connector-with-intune"></a>Conector de Sophos Mobile Threat Defense com o Intune
Pode controlar o acesso de dispositivos móveis a recursos da empresa através do acesso condicional com base na avaliação de riscos realizada pelo Sophos Mobile, uma solução de defesa contra ameaças móveis (MTD) que se integra com o Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos que executam a aplicação Sophos Mobile.
Pode configurar políticas de acesso condicional com base na avaliação de riscos de Sophos Mobile ativada através de políticas de conformidade do Intune dispositivos, que pode ser usado para permitir ou bloquear dispositivos não conformes acedam aos recursos empresariais com base em ameaças detetadas.

## <a name="how-do-intune-and-sophos-mobile-help-protect-your-company-resources"></a>Como é o Intune e Sophos Mobile ajudam a proteger os seus recursos da empresa?
Aplicação de Sophos Mobile para Android e iOS captura o sistema de ficheiros, pilha de rede, dispositivos e telemetria do application onde disponível e, em seguida, envia os dados de telemetria para o serviço de cloud de Sophos Mobile para avaliar o risco do dispositivo para ameaças contra dispositivos móveis.
A política de conformidade de dispositivo do Intune inclui uma regra para Sophos Mobile Threat Defense, que se baseia na avaliação de risco do Sophos Mobile. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou. Caso se verifique que o dispositivo não está em conformidade, será bloqueado o acesso dos utilizadores aos recursos empresariais como o Exchange Online e o SharePoint Online. Os utilizadores também recebem orientações da aplicação Sophos Mobile instalada nos respetivos dispositivos para resolver o problema e recuperar o acesso aos recursos empresariais.  

## <a name="sample-scenarios"></a>Cenários de exemplo
Seguem-se alguns cenários comuns.  
### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas
Quando forem detetadas aplicações maliciosas, como software maligno, nos dispositivos, pode impedir os dispositivos de fazer as seguintes ações até a ameaça ser resolvida:
- Ligar ao e-mail empresarial
- Sincronizar ficheiros empresariais com a aplicação OneDrive for Work
- Aceder às aplicações da empresa

**Bloquear quando forem detetadas aplicações maliciosas**:
 
![Imagem conceptual de aplicações maliciosas detetadas](./media/sophos-mtd-connector/sophos_malicious_apps_blocked.png)  

**Acesso concedido na remediação**:  
![Imagem conceptual de acesso concedido após a remediação](./media/sophos-mtd-connector/sophos_malicious_apps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede  
Detete ameaças à rede, como ataques Man-in-the-middle e Proteja o acesso a redes Wi-Fi com base no risco do dispositivo.  

**Bloquear o acesso de rede através de Wi-Fi**:  
![Bloquear o acesso de rede através de Wi-Fi](./media/sophos-mtd-connector/sophos_network_wifi_blocked.png)

**Acesso concedido na remediação**:   
![Acesso concedido na remediação](./media/sophos-mtd-connector/sophos_network_wifi_unblocked.png)  

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede  
Detete ameaças à sua rede, como ataques Man-in-the-middle e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.  

**Bloquear o SharePoint Online quando forem detetadas ameaças à rede**:   
![Bloquear o SharePoint Online quando forem detetadas ameaças de rede](./media/sophos-mtd-connector/sophos_network_spo_blocked.png)  

**Acesso concedido na remediação**:  
![Acesso concedido na remediação, por exemplo, Sharepoint](./media/sophos-mtd-connector/sophos_network_spo_unblocked.png)  

## <a name="supported-platforms"></a>Plataformas suportadas  
- Android 5.0 e posterior
- iOS 11.0 e posterior

## <a name="prerequisites"></a>Pré-requisitos  
- Azure Active Directory Premium
- Subscrição do Microsoft Intune 
- Subscrição Sophos Mobile Threat Defense

Para obter mais informações, consulte a [Web site da Sophos](https://www.sophos.com/products/mobile-control).  

## <a name="next-steps"></a>Passos Seguintes  
- [Integrar Sophos com o Intune](sophos-mtd-connector-integration.md)
- [Configurar as aplicações da Sophos](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Criar política de conformidade de dispositivos Sophos](mtd-device-compliance-policy-create.md)
- [Ativar o conector de MTD da Sophos](mtd-connector-enable.md)
