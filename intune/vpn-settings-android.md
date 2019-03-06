---
title: Configurar definições de VPN para dispositivos Android no Microsoft Intune – Azure | Microsoft Docs
description: Ao criar um perfil de configuração de VPN para dispositivos Android e Android for Work, introduza o nome da ligação, o endereço IP ou FQDN do servidor VPN, selecione a forma como os utilizadores autenticam no servidor VPN e, em seguida, selecione os tipos de ligação Citrix, SonicWall, Check Point Capsule, Pulse Secure e Microsoft Edge.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b90c9462ab41dcb03d131601e456c6c783aeb0ed
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57399168"
---
# <a name="configure-vpn-settings-for-devices-running-android-in-intune"></a>Configurar definições de VPN no Microsoft Intune para dispositivos Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com Android.

Pode configurar as definições de VPN para as seguintes plataformas:

- [Android](#android-vpn-settings)
- [Android Enterprise](#android-enterprise-vpn-settings)

Consoante as definições que escolher, nem todos os seguintes valores serão configuráveis.

## <a name="android-vpn-settings"></a>Definições VPN do Android

- **Nome da ligação**: Introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo as ligações VPN disponíveis.
- **IP ou FQDN do endereço**: Introduza o endereço IP ou nome de domínio completamente qualificado (FQDN) do servidor VPN ao qual os dispositivos ligados. Por exemplo, introduza **192.168.1.1** ou **vpn.contoso.com**.

  - **Método de autenticação**: Escolha como os dispositivos serão autenticados no servidor VPN. As opções são:

    - **Certificados**: Selecione um perfil de certificado SCEP ou PKCS existente para autenticar a ligação. [Configurar certificados](certificates-configure.md) lista os passos para criar um perfil de certificado.
    - **Nome de utilizador e palavra-passe**: Quando iniciar sessão no servidor VPN, os utilizadores finais são-lhe pedidos para introduzir um nome de utilizador e palavra-passe.

- **Tipo de ligação**: Selecione o tipo de ligação de VPN. As opções são:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Citrix**

- **Impressão digital** (verificar apenas ponto Capsule VPN): Introduza uma cadeia de caracteres, como **código de identificação digital da Contoso**para confirmar que o servidor VPN pode ser confiável. A impressão digital pode ser enviada para o cliente para que confie em qualquer servidor que tenha essa mesma impressão digital ao ligar. Se o dispositivo ainda não incluir a impressão digital, pedirá ao utilizador para confiar no servidor VPN ao mostrar a impressão digital. O utilizador verifica manualmente a mesma e opta por confiar para estabelecer a ligação.
- **Introduza pares de chave e valor para os atributos de VPN do Citrix** (apenas no Citrix): Introduza pares de chave e valor, disponibilizados pelo Citrix. Estes valores configuram as propriedades da ligação VPN.

## <a name="android-enterprise-vpn-settings"></a>Definições de VPN do Android enterprise

- **Nome da ligação**: Introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo as ligações VPN disponíveis.
- **IP ou FQDN do endereço**: Introduza o endereço IP ou nome de domínio completamente qualificado (FQDN) do servidor VPN ao qual os dispositivos ligados. Por exemplo, introduza **192.168.1.1** ou **vpn.contoso.com**.

  - **Método de autenticação**: Escolha como os dispositivos serão autenticados no servidor VPN. As opções são:
  
    - **Certificados**: Selecione um perfil de certificado SCEP ou PKCS existente para autenticar a ligação. [Configurar certificados](certificates-configure.md) lista os passos para criar um perfil de certificado.
    - **Nome de utilizador e palavra-passe**: Quando iniciar sessão no servidor VPN, os utilizadores finais são-lhe pedidos para introduzir um nome de utilizador e palavra-passe.

- **Tipo de ligação**: Selecione o tipo de ligação de VPN. As opções são:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="next-steps"></a>Passos Seguintes
[VPN profiles in Intune (Perfis VPN no Intune)](vpn-settings-configure.md)
