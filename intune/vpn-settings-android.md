---
title: Definições de VPN do Microsoft Intune para dispositivos Android
titlesuffix: ''
description: Saiba mais sobre as definições do Intune que pode utilizar para configurar ligações de VPN em dispositivos Android
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7f52c43f8918589c1b66034ad68908f4d5ddba6d
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905126"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-android"></a>Configurar definições de VPN no Microsoft Intune para dispositivos Android 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com Android.


Pode configurar as definições de VPN para as seguintes plataformas:

- [Android](#android-vpn-settings)
- [Dispositivos com perfil de trabalho do Android](#android-for-work-vpn-settings)

Consoante as definições que escolher, nem todos os seguintes valores serão configuráveis.

## <a name="android-vpn-settings"></a>Definições VPN do Android
**Nome da ligação** – Introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Endereço IP ou FQDN** – forneça o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos são ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
- **Método de autenticação** – escolha como os dispositivos serão autenticados no servidor VPN em:
    - **Certificados** – Selecione um perfil de certificado SCEP ou PKCS que criou anteriormente para autenticar a ligação. Para obter mais detalhes sobre os perfis de certificado, veja [Como configurar certificados](certificates-configure.md).
    - **Nome de utilizador e palavra-passe** – Os utilizadores finais têm de indicar um nome de utilizador e uma palavra-passe para iniciar sessão no servidor VPN.
- **Tipo de ligação** – selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Citrix**

- **Identificação Digital** (apenas no Check Point Capsule VPN) – especifique uma cadeia de carateres (por exemplo, "Código de Identificação Digital da Contoso") que servirá para verificar a fidedignidade do servidor VPN. A identificação digital pode ser enviada para o cliente para que confie em qualquer servidor que apresente essa mesma identificação digital ao ligar. Se o dispositivo ainda não incluir a identificação digital, pedirá ao utilizador para confiar no servidor VPN ao qual se está a ligar e mostra a identificação digital (o utilizador verifica-a manualmente e escolhe Confiar para ligar).
- **Introduzir pares de chave e valor para os atributos de VPN do Citrix** (apenas no Citrix) – Introduza pares de chave e valor, disponibilizados pelo Citrix, para configurar as propriedades da ligação VPN.

## <a name="android-work-profile-device-vpn-settings"></a>Definições de VPN dos dispositivos com perfil de trabalho do Android

**Nome da ligação** – Introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Endereço IP ou FQDN** – forneça o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos são ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
- **Método de autenticação** – escolha como os dispositivos serão autenticados no servidor VPN em:
    - **Certificados** – Selecione um perfil de certificado SCEP ou PKCS que criou anteriormente para autenticar a ligação. Para obter mais detalhes sobre os perfis de certificado, veja [Como configurar certificados](certificates-configure.md).
    - **Nome de utilizador e palavra-passe** – Os utilizadores finais têm de indicar um nome de utilizador e uma palavra-passe para iniciar sessão no servidor VPN.
- **Tipo de ligação** – selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

