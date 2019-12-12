---
title: Usar o Sophos Mobile com o Intune
titleSuffix: Intune on Azure
description: Como usar a solução do Sophos Mobile com o Microsoft Intune para controlar o acesso de dispositivos móveis aos seus recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e8823aa8467ef380223a486874c68d52926db733
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503737"
---
# <a name="sophos-mobile-threat-defense-connector-with-intune"></a>Conector de defesa contra ameaças móveis do Sophos com o Intune
Você pode controlar o acesso de dispositivos móveis a recursos corporativos usando o acesso condicional com base na avaliação de risco realizada pelo Sophos Mobile, uma solução de MTD (defesa contra ameaças móveis) que se integra ao Microsoft Intune. O risco é avaliado com base na telemetria coletada de dispositivos que executam o aplicativo do Sophos Mobile.
Você pode configurar políticas de acesso condicional com base na análise de risco móvel do Sophos habilitada por meio de políticas de conformidade do dispositivo do Intune, que você pode usar para permitir ou bloquear dispositivos não compatíveis para acessar recursos corporativos com base em ameaças detectadas.

## <a name="how-do-intune-and-sophos-mobile-help-protect-your-company-resources"></a>Como o Intune e o Sophos Mobile ajudam a proteger os recursos da empresa?
O aplicativo móvel do Sophos para Android e iOS captura o sistema de arquivos, a pilha de rede, o dispositivo e a telemetria do aplicativo, quando disponível, e envia os dados de telemetria para o serviço de nuvem do Sophos Mobile para avaliar o risco do dispositivo para ameaças móveis.
A política de conformidade do dispositivo do Intune inclui uma regra para a defesa contra ameaças móveis do Sophos, que se baseia na avaliação de riscos móveis do Sophos. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou. Caso se verifique que o dispositivo não está em conformidade, será bloqueado o acesso dos utilizadores aos recursos empresariais como o Exchange Online e o SharePoint Online. Os usuários também recebem orientação do aplicativo móvel do Sophos instalado em seus dispositivos para resolver o problema e obter novamente o acesso aos recursos corporativos.  

## <a name="sample-scenarios"></a>Cenários de exemplo
Seguem-se alguns cenários comuns.  
### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas
Quando forem detetadas aplicações maliciosas, como software maligno, nos dispositivos, pode impedir os dispositivos de fazer as seguintes ações até a ameaça ser resolvida:
- Ligar ao e-mail empresarial
- Sincronizar ficheiros empresariais com a aplicação OneDrive for Work
- Aceder às aplicações da empresa

**Bloquear quando aplicativos mal-intencionados forem detectados**:
 
![Imagem conceitual de aplicativos mal-intencionados detectados](./media/sophos-mtd-connector/sophos_malicious_apps_blocked.png)  

**Acesso concedido na correção**:  
![imagem conceitual de acesso concedido após a correção](./media/sophos-mtd-connector/sophos_malicious_apps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede  
Detecte ameaças à sua rede, como ataques man-in-the-Middle, e proteja o acesso a redes Wi-Fi com base no risco do dispositivo.  

**Bloquear o acesso à rede por meio de Wi-Fi**:  
![bloquear o acesso à rede por meio de Wi-Fi](./media/sophos-mtd-connector/sophos_network_wifi_blocked.png)

**Acesso concedido na correção**:   
Acesso ![concedido na correção](./media/sophos-mtd-connector/sophos_network_wifi_unblocked.png)  

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede  
Detecte ameaças à sua rede, como ataques man-in-the-Middle, e impeça a sincronização de arquivos corporativos com base no risco do dispositivo.  

**Bloquear o SharePoint Online quando ameaças à rede forem detectadas**:   
![bloquear o SharePoint Online quando ameaças de rede forem detectadas](./media/sophos-mtd-connector/sophos_network_spo_blocked.png)  

**Acesso concedido na correção**:  
Acesso ![concedido na correção do](./media/sophos-mtd-connector/sophos_network_spo_unblocked.png) de exemplo do SharePoint  

## <a name="supported-platforms"></a>Plataformas suportadas  
- Android 5,0 e posterior
- iOS 11.0 e posterior

## <a name="prerequisites"></a>Pré-requisitos  
- Azure Active Directory Premium
- Subscrição do Microsoft Intune 
- Assinatura da defesa contra ameaças móveis do Sophos

Para obter mais informações, consulte o [site do Sophos](https://www.sophos.com/products/mobile-control).  

## <a name="next-steps"></a>Próximos passos  
- [Integrar o Sophos ao Intune](sophos-mtd-connector-integration.md)
- [Configurar aplicativos do Sophos](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Criar política de conformidade do dispositivo Sophos](mtd-device-compliance-policy-create.md)
- [Habilitar o conector do Sophos MTD](mtd-connector-enable.md)
