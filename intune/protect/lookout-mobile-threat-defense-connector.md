---
title: Conector do Lookout MTD com o Microsoft Intune
titleSuffix: Microsoft Intune
description: Saiba mais sobre como integrar o Intune com o Lookout Mobile Threat Defense (Defesa Contra Ameaças para Dispositivos Móveis) para controlar o acesso de dispositivos móveis aos seus recursos empresariais.
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
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 628aa93af912d6c50a6897dbf871702e46b4893e
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782148"
---
# <a name="lookout-mobile-endpoint-security-connector-with-intune"></a>Conector de segurança de ponto de ponta móvel lookout com Intune

Pode controlar o acesso dos dispositivos móveis a recursos da empresa, com base na avaliação de riscos realizada pelo Lookout, uma solução de Defesa Contra Ameaças para Dispositivos Móveis integrada no Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos através do serviço Lookout, incluindo:
- Vulnerabilidades do sistema operativo
- Aplicações maliciosas instaladas
- Perfis de rede maliciosos

Pode configurar políticas de Acesso Condicional com base na avaliação de risco da Lookout, ativada através de políticas de conformidade intune para dispositivos matriculados, que pode utilizar para permitir ou bloquear dispositivos não conformes para aceder a recursos corporativos com base em ameaças detetadas. Para dispositivos não matriculados, pode utilizar políticas de proteção de aplicações para impor um bloco ou limpeza seletiva com base em ameaças detetadas.

## <a name="how-do-intune-and-lookout-mobile-endpoint-security-help-protect-company-resources"></a>Como é que a Intune e a Lookout Mobile Endpoint Security ajudam a proteger os recursos da empresa?
A aplicação móvel da Lookout, o **Lookout for Work**, está instalada e em execução nos dispositivos móveis. Esta aplicação captura o sistema de ficheiros, a pilha de rede e a telemetria de dispositivos e aplicações sempre que estiverem disponíveis e, em seguida, envia-os para o serviço Lookout na cloud para avaliar o risco do dispositivo relativamente a ameaças móveis. Pode alterar as classificações dos níveis de risco das ameaças na consola do Lookout para atender às suas necessidades.  

A política de conformidade no Intune inclui uma regra para a Defesa Contra Ameaças para Dispositivos Móveis do Lookout baseada na avaliação de riscos do Lookout. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou.

Se o dispositivo for considerado incompatível, o acesso a recursos como o Exchange Online e o SharePoint Online pode ser bloqueado. Os utilizadores de dispositivos bloqueados recebem medidas para resolver o problema e recuperar o acesso. As orientações são iniciadas a partir da aplicação Lookout for Work.

## <a name="supported-platforms"></a>Plataformas suportadas  
O Lookout suporta as seguintes plataformas, quando inscritas no Intune:
* **Android 4.1 e posterior**  
* **iOS 8 e posterior**  

Para obter informações adicionais sobre plataforma e suporte linguístico, visite o [site do Lookout.](https://personal.support.lookout.com/hc/articles/114094140253)  

## <a name="prerequisites"></a>Pré-requisitos
* Subscrição empresarial do Lookout Mobile Endpoint Security  
* Subscrição do Microsoft Intune
* Azure Active Directory Premium
* Mobilidade e Segurança Empresarial (EMS) E3 ou E5, com licenças atribuídas aos utilizadores.  

Para mais informações, consulte [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="sample-scenarios"></a>Cenários de exemplo

Aqui estão os cenários comuns ao usar mobile endpoint security com Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas
Quando forem detetadas aplicações maliciosas, como software maligno, nos dispositivos, pode impedir os dispositivos de fazer o seguinte até a ameaça ser resolvida:
* Ligar ao e-mail empresarial
* Sincronizar ficheiros empresariais com a aplicação OneDrive for Work
* Aceder às aplicações da empresa

**Bloquear quando as aplicações maliciosas forem detetadas:**

![Imagem conceptual da política que bloqueia o acesso devido a aplicações maliciosas](./media/lookout-mobile-threat-defense-connector/malicious-apps-blocked.png)

**Acesso concedido na remediação:**

![Imagem conceptual mostrando acesso a dispositivos após reparação](./media/lookout-mobile-threat-defense-connector/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede
Detete ameaças à rede, tal como ataques man-in-the-middle, e proteja o acesso a redes Wi-Fi com base no risco do dispositivo.

**Bloquear o acesso à rede através de Wi-Fi:**

![Imagem mostrando o bloqueio do acesso Wi-Fi com base em ameaças de rede](./media/lookout-mobile-threat-defense-connector/network-wifi-blocked.png)

**Acesso concedido na remediação:**

![Imagem conceptual do Acesso Condicional que permite o acesso após remediação](./media/lookout-mobile-threat-defense-connector/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças à sua rede, tal como ataques Man-in-the-middle e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Bloquear o SharePoint Online quando forem detetadas ameaças à rede:**

![Imagem conceptual de bloquear o acesso ao SharePoint Online](./media/lookout-mobile-threat-defense-connector/network-spo-blocked.png)


**Acesso concedido na remediação:**

![Imagem conceptual de permitir o acesso após a ameaça da rede é remediada](./media/lookout-mobile-threat-defense-connector/network-spo-unblocked.png)

## <a name="next-steps"></a>Próximos passos
Seguem-se os principais passos que tem de efetuar para implementar esta solução:
- [Configurar a sua integração do Lookout](lookout-mtd-connector-integration.md)
- [Ativar a segurança do ponto final móvel em Intune](mtd-connector-enable.md)
- [Adicionar e voltar a assinar aplicação Lookout for Work](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Configurar a política de conformidade do dispositivo do Lookout](mtd-device-compliance-policy-create.md)
- [Criar uma política de proteção de aplicações MTD](mtd-app-protection-policy.md)

