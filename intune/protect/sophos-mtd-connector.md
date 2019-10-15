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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9bacc784b9d9498196186b1fac0ef948789832b5
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306832"
---
# <a name="sophos-mobile-threat-defense-connector-with-intune"></a>Conector de defesa contra ameaças móveis do Sophos com o Intune
Você pode controlar o acesso de dispositivos móveis a recursos corporativos usando o acesso condicional com base na avaliação de risco realizada pelo Sophos Mobile, uma solução de MTD (defesa contra ameaças móveis) que se integra ao Microsoft Intune. O risco é avaliado com base na telemetria coletada de dispositivos que executam o aplicativo do Sophos Mobile.
Você pode configurar políticas de acesso condicional com base na análise de risco móvel do Sophos habilitada por meio de políticas de conformidade do dispositivo do Intune, que você pode usar para permitir ou bloquear dispositivos não compatíveis para acessar recursos corporativos com base em ameaças detectadas.

## <a name="how-do-intune-and-sophos-mobile-help-protect-your-company-resources"></a>Como o Intune e o Sophos Mobile ajudam a proteger os recursos da empresa?
O aplicativo móvel do Sophos para Android e iOS captura o sistema de arquivos, a pilha de rede, o dispositivo e a telemetria do aplicativo, quando disponível, e envia os dados de telemetria para o serviço de nuvem do Sophos Mobile para avaliar o risco do dispositivo para ameaças móveis.
A política de conformidade do dispositivo do Intune inclui uma regra para a defesa contra ameaças móveis do Sophos, que se baseia na avaliação de riscos móveis do Sophos. Quando essa regra é habilitada, o Intune avalia a conformidade do dispositivo com a política que você habilitou. Se o dispositivo for considerado incompatível, os usuários serão bloqueados no acesso a recursos corporativos como o Exchange Online e o SharePoint Online. Os usuários também recebem orientação do aplicativo móvel do Sophos instalado em seus dispositivos para resolver o problema e obter novamente o acesso aos recursos corporativos.  

## <a name="sample-scenarios"></a>Cenários de exemplo
Aqui estão alguns cenários comuns.  
### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicativos mal-intencionados
Quando aplicativos mal-intencionados, como malwares, são detectados nos dispositivos, você pode bloquear dispositivos das seguintes ações até que a ameaça seja resolvida:
- Conectando-se ao email corporativo
- Sincronizando arquivos corporativos com o aplicativo OneDrive for Work
- Acessando aplicativos da empresa

**Bloquear quando aplicativos mal-intencionados forem detectados**:
 
![Imagem conceitual de aplicativos mal-intencionados detectados](./media/sophos-mtd-connector/sophos_malicious_apps_blocked.png)  

**Acesso concedido na correção**:  
imagem ![Conceptual de acesso concedido após a correção @ no__t-1

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede  
Detecte ameaças à sua rede, como ataques man-in-the-Middle, e proteja o acesso a redes Wi-Fi com base no risco do dispositivo.  

**Bloquear o acesso à rede por meio de Wi-Fi**:  
acesso à rede ![Block por meio de Wi-Fi @ no__t-1

**Acesso concedido na correção**:   
![Access concedido na correção @ no__t-1  

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede  
Detecte ameaças à sua rede, como ataques man-in-the-Middle, e impeça a sincronização de arquivos corporativos com base no risco do dispositivo.  

**Bloquear o SharePoint Online quando ameaças à rede forem detectadas**:   
![Block o SharePoint Online quando ameaças de rede são detectadas @ no__t-1  

**Acesso concedido na correção**:  
![Access concedidos na correção para o SharePoint example @ no__t-1  

## <a name="supported-platforms"></a>Plataformas suportadas  
- Android 5,0 e posterior
- iOS 11,0 e posterior

## <a name="prerequisites"></a>Pré-requisitos  
- Azure Active Directory Premium
- Assinatura Microsoft Intune 
- Assinatura da defesa contra ameaças móveis do Sophos

Para obter mais informações, consulte o [site do Sophos](https://www.sophos.com/products/mobile-control).  

## <a name="next-steps"></a>Passos seguintes  
- [Integrar o Sophos ao Intune](sophos-mtd-connector-integration.md)
- [Configurar aplicativos do Sophos](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Criar política de conformidade do dispositivo Sophos](mtd-device-compliance-policy-create.md)
- [Habilitar o conector do Sophos MTD](mtd-connector-enable.md)
