---
title: Utilize as definições VPN para dispositivos Android no Microsoft Intune - Azure Microsoft Docs
description: Consulte todas as definições para criar ligações VPN em dispositivos Android no Microsoft Intune. Introduza o nome de ligação, endereço IP ou FQDN do servidor VPN, escolha como os utilizadores autenticam e escolha os tipos de ligação Citrix, SonicWall, Check Point Capsule e Pulse Secure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3f82cc74aa2e351ee63ffba2629e9ddddb57fc76
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512522"
---
# <a name="android-device-settings-to-configure-vpn-in-intune"></a>Configurações do dispositivo Android para configurar VPN em Intune

Este artigo lista e descreve as diferentes definições de ligação VPN que pode controlar em dispositivos Android. Como parte da sua solução de gestão de dispositivos móveis (MDM), utilize estas definições para criar uma ligação VPN, escolha como a VPN autentica, selecione um tipo de servidor VPN e muito mais.

Como administrador intune, pode criar e atribuir definições de VPN a dispositivos Android. 

Para saber mais sobre perfis VPN em Intune, consulte [perfis VPN](vpn-settings-configure.md).

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil](vpn-settings-configure.md#create-a-device-profile)de configuração do dispositivo , e escolha **o Android.**

## <a name="base-vpn"></a>Base VPN

- **Nome da ligação**: introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo as ligações VPN disponíveis. Por exemplo, introduza `Contoso VPN`.
- **Endereço IP ou FQDN**: introduza o endereço IP ou nome de domínio completamente qualificado (FQDN) do servidor VPN ao qual os dispositivos são ligados. Por exemplo, introduza **192.168.1.1** ou **vpn.contoso.com**.

  - **Método de autenticação**: selecione como os dispositivos serão autenticados no servidor VPN. As opções são:

    - **Certificados**: selecione um perfil de certificado SCEP ou PKCS existente para autenticar a ligação. [Configurar certificados](../protect/certificates-configure.md) lista os passos para criar um perfil de certificado.
    - **Nome de utilizador e palavra-passe**: Ao iniciar sessão no servidor VPN, os utilizadores finais são solicitados a introduzir o seu nome de utilizador e palavra-passe.

- **Tipo de ligação**: selecione o tipo de ligação VPN. As opções são:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **Acesso F5**
  - **Pulse Secure**
  - **Citrix SSO**

- **Impressão digital** (apenas na VPN Check Point Capsule): introduza uma cadeia (por exemplo, **Código de Impressão Digital da Contoso**) para verificar a fidedignidade do servidor VPN. Uma impressão digital é enviada para o cliente para que o cliente saiba confiar em qualquer servidor que tenha a mesma impressão digital. Se o dispositivo ainda não incluir a impressão digital, pedirá ao utilizador para confiar no servidor VPN ao mostrar a impressão digital. O utilizador verifica manualmente a impressão digital e opta por confiar para se conectar.
- **Introduzir pares de chave e valor para os atributos de VPN do Citrix** (apenas no Citrix): introduza pares de chave e valor disponibilizados pelo Citrix. Estes valores configuram as propriedades da ligação VPN. 

  Também pode **importar** um ficheiro de valores separados de vírem (.csv) com chaves e pares de valor. Certifique-se de rever os **meus dados tem cabeçalhos** e propriedades **chave.**

  Depois de adicionar os seus pares de chaves e valores, use **a Export** para fazer o back-up dos seus dados num ficheiro .csv.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode criar perfis VPN para [Android Enterprise](vpn-settings-android-enterprise.md), [iOS/iPadOS,](vpn-settings-ios.md) [macOS,](vpn-settings-macos.md) [Windows 10 e posteriormente](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md)e [Windows Phone 8.1.](vpn-settings-windows-phone-8-1.md)
