---
title: Conector Skycure Mobile Threat Defense
description: "Proteja o acesso a recursos da empresa com base em riscos de aplicações, redes e dispositivos com o conector Skycure Mobile Threat Defense e o Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7a004e6c-604a-448c-bfb8-cfda63749f5b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 51f26d630537901ad39a215062f820a2c243e077
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2017
---
# <a name="skycure-mobile-threat-defense-connector"></a>Conector Skycure Mobile Threat Defense

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Pode controlar o acesso a recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Skycure, uma solução de defesa contra ameaças para dispositivos móveis que está integrada com o Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos através do Skycure, incluindo:

-   Defesa física

-   Defesa da rede

-   Defesa da aplicação

-   Defesa contra vulnerabilidades

Pode configurar políticas de acesso condicional baseadas na avaliação de riscos do Skycure, que é ativada através de políticas de conformidade de dispositivos do Intune, as quais pode utilizar para permitir ou impedir que os dispositivos não conformes acedam aos recursos da empresa com base em ameaças detetadas.

## <a name="how-do-intune-and-skycure-help-protect-your-company-resources"></a>Como é que o Intune e o Skycure ajudam a proteger os recursos da empresa?

A aplicação Skycure para dispositivos móveis Android ou iOS captura o sistema de ficheiros, a pilha de rede e a telemetria dos dispositivos e das aplicações sempre que estiverem disponíveis e, em seguida, envia-os para o serviço cloud do Skycure para avaliar o risco do dispositivo relativamente a ameaças móveis.

A política de conformidade de dispositivos do Intune inclui uma regra para o Skycure Mobile Threat Defense, que se baseia na avaliação de riscos do Skycure. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou.

Se o dispositivo for considerado não conforme, o acesso a recursos como o Exchange Online e o SharePoint Online poderá ser bloqueado. Os utilizadores com os dispositivos bloqueados recebem orientações da aplicação móvel Skycure para resolver o problema e recuperar o acesso aos recursos empresariais.

O Intune suporta dois modos de integração com o Skycure:

-   A **Configuração básica**, que é um modo só de leitura que permite a visibilidade do Skycure para dispositivos no Intune.

-   A **Integração total**, que permite ao Skycure reportar detalhes de incidentes de segurança e riscos do dispositivo do Skycure para o Intune.

## <a name="sample-scenarios"></a>Cenários de exemplo

Seguem-se alguns cenários comuns:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas

Quando forem detetadas aplicações maliciosas, como software maligno, nos dispositivos, pode bloquear os dispositivos até a ameaça ser resolvida:

-   Ligar ao e-mail empresarial

-   Sincronizar ficheiros empresariais com a aplicação OneDrive for Work

-   Aceder às aplicações da empresa

**Bloquear quando as aplicações maliciosas forem detetadas:**

![Aplicações maliciosas detetadas](../media/mtp/skycure-arch-1.png)

**Acesso concedido na remediação:**

![Acesso concedido a aplicações maliciosas detetadas](../media/mtp/skycure-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede

Detete ameaças como **Man-in-the-middle** na rede e proteja o acesso às redes Wi-Fi com base no risco do dispositivo.

**Bloquear o acesso à rede através de Wi-Fi:**

![Bloquear o acesso à rede através de Wi-Fi](../media/mtp/skycure-arch-3.png)

**Acesso concedido na remediação:**

![Acesso concedido na remediação](../media/mtp/skycure-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças na rede, tais como ataques **Man-in-the-middle**, e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Bloquear o SharePoint Online quando forem detetadas ameaças à rede:**

![Bloquear o SharePoint Online quando forem detetadas ameaças à rede](../media/mtp/skycure-arch-5.png)

**Acesso concedido na remediação:**

![Exemplo de acesso concedido na remediação para o SharePoint](../media/mtp/skycure-arch-6.png)

## <a name="supported-platforms"></a>Plataformas suportadas

-   **Android 4.1 e posterior**

-   **iOS 8 e posterior**

## <a name="pre-requisites"></a>Pré-requisitos

-   Azure Active Directory Premium

-   Subscrição do Microsoft Intune

-   Subscrição do Skycure Mobile Threat Defense

Para obter mais informações, veja o [site do Skycure](https://www.skycure.com/skycure-microsoft-integration/).

## <a name="next-steps"></a>Próximos passos

Veja a seguir os passos necessários para integrar o Intune com o Skycure:

1.  [Configurar o Skycure para utilizar o Início de Sessão Único (SS) do Azure Active Directory](/intune-classic/deploy-use/configure-skycure-to-use-azure-active-directory-single-sign-on)

2.  [Transferir a política de configuração de aplicações iOS do Skycure](/intune-classic/deploy-use/download-skycure-ios-app-configuration-policy)

3.  [Adicionar aplicações do Skycure, o Microsoft Authenticator e a política de configuração de aplicações móveis iOS](/intune-classic/deploy-use/add-skycure-apps-microsoft-authenticator-and-ios-app-configuration-policy)

4.  [Implementar aplicações do Skycure, o Microsoft Authenticator e a política de configuração de aplicações móveis iOS](/intune-classic/deploy-use/deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy)

5.  [Configurar a integração do Skycure com o Intune](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)

6.  [Ativar o Skycure Mobile Threat Defense no Intune](/intune-classic/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

7.  [Criar a política de conformidade do Skycure Mobile Threat Defense no Intune](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
