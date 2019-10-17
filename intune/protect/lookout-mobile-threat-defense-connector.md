---
title: Conector do Lookout MTD com o Microsoft Intune
titleSuffix: Microsoft Intune
description: Saiba mais sobre como integrar o Intune com o Lookout Mobile Threat Defense (Defesa Contra Ameaças para Dispositivos Móveis) para controlar o acesso de dispositivos móveis aos seus recursos empresariais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f0123647fb1e8a1d52506ad0753906f974103aad
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502219"
---
# <a name="lookout-mobile-endpoint-security-connector-with-intune"></a>Conector do Mobile Endpoint Security com o Intune

Pode controlar o acesso dos dispositivos móveis a recursos da empresa, com base na avaliação de riscos realizada pelo Lookout, uma solução de Defesa Contra Ameaças para Dispositivos Móveis integrada no Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos através do serviço Lookout, incluindo:
- Vulnerabilidades do sistema operativo
- Aplicações maliciosas instaladas
- Perfis de rede maliciosos

Você pode configurar políticas de acesso condicional com base na avaliação de risco da consulta habilitada por meio das políticas de conformidade do Intune. As definições permitem-lhe autorizar ou bloquear dispositivos não conformes com base nas ameaças detetadas.

## <a name="how-do-intune-and-lookout-mobile-endpoint-security-help-protect-company-resources"></a>Como o Intune e a consulta ao Mobile Endpoint Security ajudam a proteger os recursos da empresa?
A aplicação móvel da Lookout, o **Lookout for Work**, está instalada e em execução nos dispositivos móveis. Esta aplicação captura o sistema de ficheiros, a pilha de rede e a telemetria de dispositivos e aplicações sempre que estiverem disponíveis e, em seguida, envia-os para o serviço Lookout na cloud para avaliar o risco do dispositivo relativamente a ameaças móveis. Pode alterar as classificações dos níveis de risco das ameaças na consola do Lookout para atender às suas necessidades.  

A política de conformidade no Intune inclui uma regra para a Defesa Contra Ameaças para Dispositivos Móveis do Lookout baseada na avaliação de riscos do Lookout. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou.

Se o dispositivo for considerado incompatível, o acesso a recursos como o Exchange Online e o SharePoint Online poderá ser bloqueado. Os usuários em dispositivos bloqueados recebem etapas para resolver o problema e restabelecer o acesso. As orientações são iniciadas a partir da aplicação Lookout for Work.

## <a name="supported-platforms"></a>Plataformas suportadas  
O Lookout suporta as seguintes plataformas, quando inscritas no Intune:
* **Android 4.1 e posterior**  
* **iOS 8 e posterior**  

Para obter informações adicionais sobre o suporte a plataformas e idiomas, visite o [site da Web](https://personal.support.lookout.com/hc/articles/114094140253)de consulta.  

## <a name="prerequisites"></a>Pré-requisitos
* Subscrição empresarial do Lookout Mobile Endpoint Security  
* Subscrição do Microsoft Intune
* Azure Active Directory Premium
* EMS (Enterprise Mobility and Security) E3 ou e5, com licenças atribuídas a usuários.  

Para mais informações, consulte [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="sample-scenarios"></a>Cenários de exemplo

Aqui estão os cenários comuns ao usar o Mobile Endpoint Security com o Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas
Quando forem detetadas aplicações maliciosas, como software maligno, nos dispositivos, pode impedir os dispositivos de fazer o seguinte até a ameaça ser resolvida:
* Ligar ao e-mail empresarial
* Sincronizar ficheiros empresariais com a aplicação OneDrive for Work
* Aceder às aplicações da empresa

**Bloquear quando as aplicações maliciosas forem detetadas:**

![Imagem conceitual de bloqueio de acesso de política devido a aplicativos mal-intencionados](./media/lookout-mobile-threat-defense-connector/malicious-apps-blocked.png)

**Acesso concedido na remediação:**

![Imagem conceitual mostrando o acesso concedido aos dispositivos após a correção](./media/lookout-mobile-threat-defense-connector/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede
Detete ameaças à rede, tal como ataques man-in-the-middle, e proteja o acesso a redes Wi-Fi com base no risco do dispositivo.

**Bloquear o acesso à rede através de Wi-Fi:**

![Imagem mostrando o bloqueio do acesso WiFi com base em ameaças de rede](./media/lookout-mobile-threat-defense-connector/network-wifi-blocked.png)

**Acesso concedido na remediação:**

![Imagem conceitual do acesso condicional que permite o acesso após a correção](./media/lookout-mobile-threat-defense-connector/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças à sua rede, tal como ataques Man-in-the-middle e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Bloquear o SharePoint Online quando forem detetadas ameaças à rede:**

![Imagem conceitual de bloqueio de acesso ao SharePoint Online](./media/lookout-mobile-threat-defense-connector/network-spo-blocked.png)


**Acesso concedido na remediação:**

![Imagem conceitual de permitir o acesso após a correção da ameaça de rede](./media/lookout-mobile-threat-defense-connector/network-spo-unblocked.png)

## <a name="next-steps"></a>Próximos passos
Seguem-se os principais passos que tem de efetuar para implementar esta solução:
1. [Configurar a sua integração do Lookout](lookout-mtd-connector-integration.md)
2. [Habilitar a segurança de ponto de extremidade móvel no Intune](mtd-connector-enable.md)
3. [Adicionar e voltar a assinar aplicação Lookout for Work](mtd-apps-ios-app-configuration-policy-add-assign.md)
4. [Configurar a política de conformidade do dispositivo do Lookout](mtd-device-compliance-policy-create.md)
