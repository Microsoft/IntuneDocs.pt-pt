---
title: Conector do Lookout MTD com o Microsoft Intune
titlesuffix: ''
description: Saiba mais sobre como integrar o Intune com o Lookout Mobile Threat Defense (Defesa Contra Ameaças para Dispositivos Móveis) para controlar o acesso de dispositivos móveis aos seus recursos empresariais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/09/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d7a545fe08acc9ab88086fa92be934c860ae4716
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179546"
---
# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Conector de Defesa Contra Ameaças para Dispositivos Móveis do Lookout com o Intune

Pode controlar o acesso dos dispositivos móveis a recursos da empresa, com base na avaliação de riscos realizada pelo Lookout, uma solução de Defesa Contra Ameaças para Dispositivos Móveis integrada no Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos através do serviço Lookout, incluindo:
- Vulnerabilidades do sistema operativo
- Aplicações maliciosas instaladas
- Perfis de rede maliciosos

Pode configurar políticas de acesso condicional com base na avaliação de riscos do Lookout ativada através de políticas de conformidade do Intune. As definições permitem-lhe autorizar ou bloquear dispositivos não conformes com base nas ameaças detetadas.

## <a name="how-do-intune-and-lookout-mobile-threat-defense-help-protect-company-resources"></a>Como é que o Intune e o Conetor de Defesa Contra Ameaças para Dispositivos Móveis do Lookout ajudam a proteger os recursos da empresa?
A aplicação móvel da Lookout, o **Lookout for Work**, está instalada e em execução nos dispositivos móveis. Esta aplicação captura o sistema de ficheiros, a pilha de rede e a telemetria de dispositivos e aplicações sempre que estiverem disponíveis e, em seguida, envia-os para o serviço Lookout na cloud para avaliar o risco do dispositivo relativamente a ameaças móveis. Pode alterar as classificações dos níveis de risco das ameaças na consola do Lookout para atender às suas necessidades.  

A política de conformidade no Intune inclui uma regra para a Defesa Contra Ameaças para Dispositivos Móveis do Lookout baseada na avaliação de riscos do Lookout. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou.

Se o dispositivo for considerado não conforme, o acesso a recursos como o Exchange Online e o SharePoint Online poderá ser bloqueado. Os utilizadores com dispositivos bloqueados recebem os passos para resolver o problema e recuperar o acesso. As orientações são iniciadas a partir da aplicação Lookout for Work.

## <a name="supported-platforms"></a>Plataformas suportadas
O Lookout suporta as seguintes plataformas, quando inscritas no Intune:
* **Android 4.1 e posterior**
* **iOS 8 e posterior** Para obter informações adicionais sobre o suporte de plataformas e idiomas, visite o [site da Lookout](https://personal.support.lookout.com/hc/articles/114094140253).

## <a name="prerequisites"></a>Pré-requisitos
* Subscrição do Microsoft Intune
* Azure Active Directory
* Subscrição empresarial do Lookout Mobile Endpoint Security  

Para mais informações, consulte [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="sample-scenarios"></a>Cenários de exemplo

Veja a seguir os cenários comuns ao utilizar a Defesa Contra Ameaças a Dispositivos Móveis com o Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas
Quando forem detetadas aplicações maliciosas, como software maligno, nos dispositivos, pode impedir os dispositivos de fazer o seguinte até a ameaça ser resolvida:
* Ligar ao e-mail empresarial
* Sincronizar ficheiros empresariais com a aplicação OneDrive for Work
* Aceder às aplicações da empresa

**Bloquear quando as aplicações maliciosas forem detetadas:**

![diagrama a mostrar a política de acesso condicional a bloquear o acesso quando o dispositivo é identificado como não conforme devido a aplicações maliciosas no mesmo](./media/malicious-apps-blocked.png)

**Acesso concedido na remediação:**

![Diagrama a mostrar a política de acesso condicional a conceder acesso quando o dispositivo é identificado como sendo compatível após a remediação](./media/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede
Detete ameaças à rede, tal como ataques man-in-the-middle, e proteja o acesso a redes Wi-Fi com base no risco do dispositivo.

**Bloquear o acesso à rede através de Wi-Fi:**

![diagrama a mostrar o acesso condicional a bloquear o acesso Wi-Fi com base em ameaças à rede](./media/network-wifi-blocked.png)

**Acesso concedido na remediação:**

![Diagrama a mostrar o acesso condicional a permitir o acesso na remediação da ameaça](./media/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças à sua rede, tal como ataques Man-in-the-middle e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Bloquear o SharePoint Online quando forem detetadas ameaças à rede:**

![Diagrama a mostrar o acesso condicional a bloquear o acesso do dispositivo ao SharePoint Online com base na deteção da ameaça](./media/network-spo-blocked.png)


**Acesso concedido na remediação:**

![Diagrama a mostrar o acesso condicional a permitir o acesso após a ameaça da rede ser corrigida](./media/network-spo-unblocked.png)

## <a name="next-steps"></a>Passos Seguintes
Seguem-se os principais passos que tem de efetuar para implementar esta solução:
1.  [Configurar a sua integração do Lookout](lookout-mtd-connector-integration.md)
2.  [Ativar a Defesa Contra Ameaças para Dispositivos Móveis do Lookout no Intune](mtd-connector-enable.md)
3.  [Adicionar e voltar a assinar aplicação Lookout for Work](mtd-apps-ios-app-configuration-policy-add-assign.md)
4.  [Configurar a política de conformidade do dispositivo do Lookout](mtd-device-compliance-policy-create.md)
