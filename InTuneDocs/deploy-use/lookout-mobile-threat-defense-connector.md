---
title: "Conector de defesa contra ameaças para dispositivos móveis do Lookout | Documentos da Microsoft"
description: "Proteja o acesso a recursos da empresa com base em riscos de aplicações, redes e dispositivos com o conector de Defesa Contra Ameaças para Dispositivos Móveis do Lookout e o Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d42fa20a3bc6b6f4a74dd0872aae25cfb33067b9
ms.openlocfilehash: dfed1ece238210e8b98934d8add7dbb9b0f1c1fb
ms.lasthandoff: 03/21/2017


---

# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Conector de Defesa Contra Ameaças para Dispositivos Móveis do Lookout com o Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Pode controlar o acesso dos dispositivos móveis a recursos da empresa, com base na avaliação de riscos realizada pelo Lookout, uma solução de Defesa Contra Ameaças para Dispositivos Móveis integrada no Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos através do serviço Lookout, incluindo:
- Vulnerabilidades do sistema operativo
- Aplicações maliciosas instaladas
- Perfis de rede maliciosos

Pode configurar políticas de acesso condicional com base na avaliação de riscos do Lookout ativada através de políticas de conformidade do Intune. As definições permitem-lhe autorizar ou bloquear dispositivos não conformes com base nas ameaças detetadas.

## <a name="how-do-intune-and-lookout-mobile-threat-defense-help-protect-company-resources"></a>Como é que o Intune e o Conetor de Defesa Contra Ameaças para Dispositivos Móveis do Lookout ajudam a proteger os recursos da empresa?
A aplicação móvel da Lookout, o **Lookout for Work**, está instalada e em execução nos dispositivos móveis. Esta aplicação captura o sistema de ficheiros, a pilha de rede e a telemetria de dispositivos e aplicações sempre que estiverem disponíveis e, em seguida, envia-os para o serviço Lookout na cloud para avaliar o risco do dispositivo relativamente a ameaças móveis. Pode alterar as classificações dos níveis de risco das ameaças na consola do Lookout para atender às suas necessidades.  

A política de conformidade no Intune inclui uma regra para a Defesa Contra Ameaças para Dispositivos Móveis do Lookout baseada na avaliação de riscos do Lookout. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou.

Se o dispositivo for considerado não conforme, o acesso a recursos como o Exchange Online e o SharePoint Online poderá ser bloqueado. Os utilizadores com dispositivos bloqueados recebem os passos para resolver o problema e recuperar o acesso. As orientações são iniciadas a partir da aplicação Lookout for Work.

## <a name="supported-platforms"></a>Plataformas suportadas:
O Lookout suporta as seguintes plataformas, quando inscritas no Intune:
* **Android 4.1 e posterior**
* **iOS 8 e posterior** Para obter informações adicionais sobre o suporte de plataformas e idiomas, visite o [site da Lookout](https://personal.support.lookout.com/hc/en-us/articles/114094140253).

## <a name="prerequisites"></a>Pré-requisitos:
* Subscrição do Microsoft Intune
* Azure Active Directory
* Subscrição empresarial do Lookout Mobile Endpoint Security  

Para mais informações, consulte [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="sample-scenarios"></a>Cenários de exemplo
Seguem-se alguns cenários comuns:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas
Quando forem detetadas aplicações maliciosas, como software maligno, nos dispositivos, pode impedir os dispositivos de fazer o seguinte até a ameaça ser resolvida:
* Ligar ao e-mail empresarial
* Sincronizar ficheiros empresariais com a aplicação OneDrive for Work
* Aceder às aplicações da empresa

**Bloquear quando forem detetadas aplicações maliciosas:**
![diagrama a mostrar a política de acesso condicional a bloquear o acesso quando o dispositivo é identificado como não conforme devido a aplicações maliciosas no dispositivo](../media/mtp/malicious-apps-blocked.png)

**Acesso concedido na remediação:**

![Diagrama a mostrar a política de acesso condicional a conceder acesso quando o dispositivo é identificado como sendo compatível após a remediação](../media/mtp/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede
Detete ameaças à rede, tal como ataques Man-in-the-middle, e proteja o acesso a redes Wi-Fi com base no risco do dispositivo.

**Bloquear o acesso à rede através de Wi-Fi:**
![diagrama a mostrar o acesso condicional a bloquear o acesso Wi-Fi com base em ameaças à rede](../media/mtp/network-wifi-blocked.png)

**Acesso concedido na remediação:**

![Diagrama a mostrar o acesso condicional a permitir o acesso na remediação da ameaça](../media/mtp/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças à sua rede, tal como ataques Man-in-the-middle e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Bloquear o SharePoint Online quando forem detetadas ameaças à rede:**

![Diagrama a mostrar o acesso condicional a bloquear o acesso do dispositivo ao SharePoint Online com base na deteção da ameaça](../media/mtp/network-spo-blocked.png)


**Acesso concedido na remediação:**

![Diagrama a mostrar o acesso condicional a permitir o acesso após a ameaça da rede ser corrigida](../media/mtp/network-spo-unblocked.png)

## <a name="next-steps"></a>Passos seguintes
Seguem-se os principais passos que tem de efetuar para implementar esta solução:
1.    [Configurar a sua subscrição do Lookout](device-threat-protection-subscription-setup.md)
2.    [Ativar a Defesa Contra Ameaças para Dispositivos Móveis do Lookout no Intune](device-threat-protection-enable.md)
3.  [Configurar e implementar a aplicação Defesa Contra Ameaças para Dispositivos Móveis do Lookout](device-threat-protection-apps.md)
4.    [Configurar a política de conformidade do dispositivo do Lookout](device-threat-protection-policy.md)
5.    [Resolver problemas com a integração da Defesa Contra Ameaças para Dispositivos Móveis do Lookout](http://docs.microsoft.com/intune/troubleshoot/device-threat-protection-troubleshooting)

