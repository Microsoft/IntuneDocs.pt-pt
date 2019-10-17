---
title: Configurar o Mobile Security com o Intune
titleSuffix: Intune on Azure
description: Como configurar a segurança móvel do inativo com Microsoft Intune para controlar o acesso de dispositivos móveis aos seus recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7cc63be3c7c536cba67ef92288c12cc4032ae200
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508817"
---
# <a name="wandera-mobile-threat-defense-connector-with-intune"></a>Conector de defesa contra ameaças móveis do com o Intune  

Controle o acesso de dispositivos móveis a recursos corporativos usando o acesso condicional com base na avaliação de risco realizada pelo. O backr é uma solução de MTD (defesa contra ameaças móveis) que se integra ao Microsoft Intune.  O risco é avaliado com base na telemetria coletada de dispositivos pelo serviço de inatividade, incluindo:
- Vulnerabilidades do sistema operativo
- Aplicações maliciosas instaladas
- Perfis de rede maliciosos
- Cryptojacking

Você pode configurar políticas de *acesso condicional* que se baseiam na avaliação de risco da, habilitadas por meio de políticas de conformidade do dispositivo do Intune. A política de avaliação de risco pode permitir ou impedir que dispositivos não compatíveis acessem recursos corporativos com base em ameaças detectadas.  


## <a name="how-do-intune-and-wandera-mobile-threat-defense-help-protect-your-company-resources"></a>Como o Intune e a defesa contra ameaças móveis ajudam a proteger os recursos da empresa?  

O aplicativo móvel do backit é instalado diretamente usando Microsoft Intune. Este aplicativo captura a telemetria do sistema de arquivos, da pilha de rede e do dispositivo e do aplicativo (quando disponível). Essas informações são sincronizadas com o serviço de nuvem da inatividade para avaliar o risco do dispositivo para ameaças móveis. Essas classificações de nível de risco são configuráveis para atender às suas necessidades no console do inentrar, RADAR.

A política de conformidade no Intune inclui uma regra para MTD com base na avaliação de risco do onit. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou.

Para dispositivos que não estão em conformidade, o acesso a recursos como o Office 365 pode ser bloqueado. Os usuários em dispositivos bloqueados recebem orientação do aplicativo de inativação para resolver o problema e restabelecer o acesso.

## <a name="supported-platforms"></a>Plataformas suportadas  

As seguintes plataformas têm suporte para o inverter quando registrados no Intune:

- Android 5,0 e posterior  
- iOS 10,2 e posterior  

Para obter mais informações sobre a plataforma e o dispositivo, consulte o [site da Web](https://www.wandera.com/why-wandera/features/device-support/)de busca.

## <a name="prerequisites"></a>Pré-requisitos  

- Subscrição do Microsoft Intune  
- Azure Active Directory  
- Defesa contra ameaças móveis do (anteriormente chamado de chamada de segurança)  

Para obter mais informações, consulte [Mobile Security](https://www.wandera.com/mobile-security/).
 
## <a name="sample-scenarios"></a>Cenários de exemplo

Aqui estão os cenários comuns ao usar o MTD de página de inpágina com o Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas  

Quando aplicativos mal-intencionados, como malwares, são detectados nos dispositivos, você pode bloquear dispositivos de ferramentas comuns até que possa resolver a ameaça. Os blocos comuns incluem:  
- Ligar ao e-mail empresarial  
- Sincronizar ficheiros empresariais com a aplicação OneDrive for Work  
- Aceder às aplicações da empresa  

**Bloquear quando aplicativos mal-intencionados forem detectados**:

![Imagem conceitual de aplicativos mal-intencionados detectados](./media/wandera-mtd-connector/wandera-malicious-apps-blocked.png)  

**Acesso concedido na correção**: 

![Imagem conceitual de acesso concedido após a correção](./media/wandera-mtd-connector/wandera-malicious-apps-unblocked.png)


### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede  

Detecte ameaças à sua rede, como ataques man-in-the-middle e proteja o acesso a redes Wi-Fi com base no risco do dispositivo.  

**Bloquear o acesso à rede por meio de Wi-Fi**:  

![Bloquear o acesso à rede através de Wi-Fi](./media/wandera-mtd-connector/wandera-network-wifi-blocked.png)

**Acesso concedido na correção**:  

![Acesso concedido na remediação](./media/wandera-mtd-connector/wandera-network-wifi-unblocked.png)  

## <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças à sua rede, tal como ataques Man-in-the-middle e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Bloquear o SharePoint Online quando ameaças à rede forem detectadas**:  

![Bloquear o SharePoint Online quando forem detetadas ameaças à rede](./media/wandera-mtd-connector/wandera-network-spo-blocked.png)  


**Acesso concedido na correção**:  

![Acesso concedido na correção para o exemplo do SharePoint](./media/wandera-mtd-connector/wandera-network-spo-unblocked.png)  

## <a name="next-steps"></a>Próximos passos

- [Integrar o ao Intune](wandera-mtd-connector-integration.md)
- [Configurar aplicativos de inativação](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Criar política de conformidade do dispositivo da vagaa](mtd-device-compliance-policy-create.md)
- [Habilitar conector do MTD](mtd-connector-enable.md)