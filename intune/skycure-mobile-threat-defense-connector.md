---
title: Conector Skycure com o Intune
titleSuffix: Intune on Azure
description: "Integração do conector Skycure com o Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c55fa5b3ea86127648850ae7374107ca65db9764
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="skycure-mobile-threat-defense-connector"></a>Conector Skycure Mobile Threat Defense

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

![Aplicações maliciosas detetadas](./media/skycure-arch-1.png)

**Acesso concedido na remediação:**

![Acesso concedido a aplicações maliciosas detetadas](./media/skycure-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede

Detete ameaças como **Man-in-the-middle** na rede e proteja o acesso às redes Wi-Fi com base no risco do dispositivo.

**Bloquear o acesso à rede através de Wi-Fi:**

![Bloquear o acesso à rede através de Wi-Fi](./media/skycure-arch-3.png)

**Acesso concedido na remediação:**

![Acesso concedido na remediação](./media/skycure-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças na rede, tais como ataques **Man-in-the-middle**, e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Bloquear o SharePoint Online quando forem detetadas ameaças à rede:**

![Bloquear o SharePoint Online quando forem detetadas ameaças à rede](./media/skycure-arch-5.png)

**Acesso concedido na remediação:**

![Exemplo de acesso concedido na remediação para o SharePoint](./media/skycure-arch-6.png)

## <a name="supported-platforms"></a>Plataformas suportadas

-   **Android 4.1 e posterior**

-   **iOS 8 e posterior**

## <a name="pre-requisites"></a>Pré-requisitos

-   Azure Active Directory Premium

-   Subscrição do Microsoft Intune

-   Subscrição do Skycure Mobile Threat Defense

Para obter mais informações, veja o [site do Skycure](https://www.skycure.com/skycure-microsoft-integration/).

## <a name="next-steps"></a>Passos seguintes

Veja a seguir os passos necessários para integrar o Intune com o Skycure:

1.  [Configurar o Skycure para utilizar o Início de Sessão Único (SSO) do Azure Active Directory](skycure-azure-sso-configure.md)

2.  [Transferir a política de configuração de aplicações iOS do Skycure](skycure-ios-app-configuration-policy-download.md)

3.  [Adicionar e atribuir aplicações do Skycure, o Microsoft Authenticator e a política de configuração de aplicações iOS](mtd-apps-ios-app-configuration-policy-add-assign.md)

4.  [Configurar a integração do Skycure com o Intune](skycure-mtd-connector-integration.md)

5.  [Ativar o Skycure Mobile Threat Defense no Intune](mtd-connector-enable.md)

6.  [Criar a política de conformidade de dispositivos do Skycure Mobile Threat Defense no Intune](mtd-device-compliance-policy-create.md)
