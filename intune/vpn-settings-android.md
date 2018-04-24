---
title: Definições de VPN do Microsoft Intune para dispositivos Android
titlesuffix: ''
description: Saiba mais sobre as definições do Intune que pode utilizar para configurar ligações de VPN em dispositivos Android
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7c3b4964baec0ae957cfb392843ce527bf13934e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-android"></a>Configurar definições de VPN no Microsoft Intune para dispositivos Android 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com Android.


Pode configurar as definições de VPN para as seguintes plataformas:

- [Android](#android-vpn-settings)
- [Android for Work](#android-for-work-vpn-settings)

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

## <a name="android-for-work-vpn-settings"></a>Definições VPN do Android for Work

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

