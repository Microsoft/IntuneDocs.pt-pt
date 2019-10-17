---
title: Conector da Symantec com o Microsoft Intune
titleSuffix: Microsoft Intune
description: Saiba mais sobre como integrar o Symantec Endpoint Protection Mobile para controlar o acesso de dispositivos móveis aos seus recursos empresariais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/09/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be8fbb0bd96891eb3af3157deddfc325ebc5f2b9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508923"
---
# <a name="symantec-endpoint-protection-mobile-connector"></a>Conector do Symantec Endpoint Protection Mobile

Você pode controlar o acesso de dispositivos móveis a recursos corporativos usando o acesso condicional com base na avaliação de risco realizada pelo Symantec Endpoint Protection Mobile (setembro de dispositivos móveis), uma solução de defesa contra ameaças móveis que se integra ao Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos com o SEP Mobile, incluindo:

- Defesa física

- Defesa da rede

- Defesa da aplicação

- Defesa contra vulnerabilidades

Você pode habilitar a avaliação de risco móvel de setembro por meio das políticas de conformidade do dispositivo do Intune e, em seguida, usar políticas de acesso condicional para permitir ou bloquear o acesso de dispositivo não compatível a recursos corporativos com base em ameaças detectadas

## <a name="how-do-intune-and-sep-mobile-help-protect-your-company-resources"></a>Como é que o Intune e o SEP Mobile ajudam a proteger os recursos da empresa?

A aplicação SEP Mobile para Android ou iOS captura o sistema de ficheiros, a pilha de rede e a telemetria dos dispositivos e das aplicações sempre que estiverem disponíveis e, em seguida, envia-os para o serviço cloud da Symantec para avaliar o risco do dispositivo relativamente a ameaças móveis.

A política de conformidade de dispositivos do Intune inclui uma regra para o SEP Mobile, que se baseia na avaliação de riscos do SEP Mobile. Quando esta regra está ativada, o Intune avalia a conformidade do dispositivo com a política que ativou.

Se o dispositivo for considerado não conforme, o acesso a recursos como o Exchange Online e o SharePoint Online será bloqueado. Os utilizadores com os dispositivos bloqueados recebem orientações da aplicação SEP Mobile para resolver o problema e recuperar o acesso aos recursos empresariais.

O Intune suporta dois modos de integração com o SEP Mobile:

- A **Configuração básica**, que é um modo só de leitura que permite a visibilidade do SEP Mobile para dispositivos no Intune.

- A **Integração total**, que permite ao SEP Mobile comunicar detalhes de incidentes de segurança e riscos do dispositivo ao Intune.

## <a name="sample-scenarios"></a>Cenários de exemplo

Seguem-se alguns cenários comuns:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controlar o acesso com base em ameaças de aplicações maliciosas

Quando forem detetadas aplicações maliciosas, como software maligno, nos dispositivos, pode bloquear os dispositivos até a ameaça ser resolvida:

- Ligar ao e-mail empresarial

- Sincronizar ficheiros empresariais com a aplicação OneDrive for Work

- Aceder às aplicações da empresa

**Bloquear quando as aplicações maliciosas forem detetadas:**

![Imagem conceitual de aplicativos mal-intencionados detectados](./media/skycure-mobile-threat-defense-connector/symantec-arch-1.png)

**Acesso concedido na remediação:**

![Imagem de acesso concedida na correção após a detecção de aplicativos mal-intencionados](./media/skycure-mobile-threat-defense-connector/symantec-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Controlar o acesso com base em ameaças à rede

Detete ameaças como **Man-in-the-middle** na rede e proteja o acesso às redes Wi-Fi com base no risco do dispositivo.

**Bloquear o acesso à rede através de Wi-Fi:**

![Bloquear o acesso à rede através de Wi-Fi](./media/skycure-mobile-threat-defense-connector/symantec-arch-3.png)

**Acesso concedido na remediação:**

![Acesso concedido na remediação](./media/skycure-mobile-threat-defense-connector/symantec-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar o acesso ao SharePoint Online com base em ameaças à rede

Detete ameaças na rede, tais como ataques **Man-in-the-middle**, e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Bloquear o SharePoint Online quando forem detetadas ameaças à rede:**

![Bloquear o SharePoint Online quando forem detetadas ameaças à rede](./media/skycure-mobile-threat-defense-connector/symantec-arch-5.png)

**Acesso concedido na remediação:**

![Exemplo de acesso concedido na remediação para o SharePoint](./media/skycure-mobile-threat-defense-connector/symantec-arch-6.png)

## <a name="supported-platforms"></a>Plataformas suportadas

- **Android 4.1 e posterior**

- **iOS 8 e posterior**

## <a name="pre-requisites"></a>Pré-requisitos

- Azure Active Directory Premium

- Subscrição do Microsoft Intune

- Subscrição do Symantec Endpoint Protection Mobile

Para obter mais informações, veja o [site da Symantec](https://www.skycure.com/skycure-microsoft-integration/).

## <a name="next-steps"></a>Próximos passos

Veja a seguir os passos necessários para integrar o Intune com o SEP Mobile:

- [Configurar a integração do SEP Mobile com o Intune](skycure-mtd-connector-integration.md)

- [Adicionar e atribuir aplicações do SEP Mobile, o Microsoft Authenticator e a política de configuração de aplicações iOS](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Criar a política de conformidade de dispositivos do SEP Mobile com o Intune](mtd-device-compliance-policy-create.md)

- [Ativar o conector do SEP Mobile MTD no Intune](mtd-connector-enable.md)