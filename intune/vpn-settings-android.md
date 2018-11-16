---
title: Configurar definições de VPN para dispositivos Android no Microsoft Intune – Azure | Microsoft Docs
description: Ao criar um perfil de configuração de VPN para dispositivos Android e Android for Work, introduza o nome da ligação, o endereço IP ou FQDN do servidor VPN, selecione a forma como os utilizadores autenticam no servidor VPN e, em seguida, selecione os tipos de ligação Citrix, SonicWall, Check Point Capsule, Pulse Secure e Microsoft Edge.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 113d2e52783f3c7e9f013d2cc239efad45408c87
ms.sourcegitcommit: d8edd1c3d24123762dd6d14776836df4ff2a31dd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2018
ms.locfileid: "51576822"
---
# <a name="configure-vpn-settings-for-devices-running-android-in-intune"></a>Configurar definições de VPN no Microsoft Intune para dispositivos Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com Android.

Pode configurar as definições de VPN para as seguintes plataformas:

- [Android](#android-vpn-settings)
- [Android for Work](#android-for-work-vpn-settings)

Consoante as definições que escolher, nem todos os seguintes valores serão configuráveis.

## <a name="android-vpn-settings"></a>Definições VPN do Android

- **Nome da ligação**: introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo as ligações VPN disponíveis.
- **Endereço IP ou FQDN**: introduza o endereço IP ou nome de domínio completamente qualificado (FQDN) do servidor VPN ao qual os dispositivos são ligados. Por exemplo, introduza **192.168.1.1** ou **vpn.contoso.com**.

  - **Método de autenticação**: selecione como os dispositivos serão autenticados no servidor VPN. As opções são:

    - **Certificados**: selecione um perfil de certificado SCEP ou PKCS existente para autenticar a ligação. [Configurar certificados](certificates-configure.md) lista os passos para criar um perfil de certificado.
    - **Nome de utilizador e palavra-passe**: ao iniciar sessão no servidor VPN, é pedido aos utilizadores finais que introduzam um nome de utilizador e uma palavra-passe.

- **Tipo de ligação**: selecione o tipo de ligação VPN. As opções são:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Citrix**

- **Impressão digital** (apenas na VPN Check Point Capsule): introduza uma cadeia (por exemplo, **Código de Impressão Digital da Contoso**) para verificar a fidedignidade do servidor VPN. A impressão digital pode ser enviada para o cliente para que confie em qualquer servidor que tenha essa mesma impressão digital ao ligar. Se o dispositivo ainda não incluir a impressão digital, pedirá ao utilizador para confiar no servidor VPN ao mostrar a impressão digital. O utilizador verifica manualmente a mesma e opta por confiar para estabelecer a ligação.
- **Introduzir pares de chave e valor para os atributos de VPN do Citrix** (apenas no Citrix): introduza pares de chave e valor disponibilizados pelo Citrix. Estes valores configuram as propriedades da ligação VPN.

## <a name="android-for-work-vpn-settings"></a>Definições VPN dos dispositivos Android for Work

- **Nome da ligação**: introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo as ligações VPN disponíveis.
- **Endereço IP ou FQDN**: introduza o endereço IP ou nome de domínio completamente qualificado (FQDN) do servidor VPN ao qual os dispositivos são ligados. Por exemplo, introduza **192.168.1.1** ou **vpn.contoso.com**.

  - **Método de autenticação**: selecione como os dispositivos serão autenticados no servidor VPN. As opções são:
  
    - **Certificados**: selecione um perfil de certificado SCEP ou PKCS existente para autenticar a ligação. [Configurar certificados](certificates-configure.md) lista os passos para criar um perfil de certificado.
    - **Nome de utilizador e palavra-passe**: ao iniciar sessão no servidor VPN, é pedido aos utilizadores finais que introduzam um nome de utilizador e uma palavra-passe.

- **Tipo de ligação**: selecione o tipo de ligação VPN. As opções são:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

## <a name="next-steps"></a>Próximos passos
[VPN profiles in Intune (Perfis VPN no Intune)](vpn-settings-configure.md)
