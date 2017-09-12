---
title: "Definições de VPN no Intune VPN para dispositivos Android"
titlesuffix: Azure portal
description: "Saiba mais sobre as definições do Intune que pode utilizar para configurar ligações de VPN em dispositivos Android"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 16c056ca-320e-4107-ad03-a0cf96c28885
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 626db819f8dc9e68e38abe6de800fdf68cb5afe7
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="vpn-settings-for-android-devices-in-microsoft-intune"></a>Definições de VPN para dispositivos Android no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Como um administrador do Intune, pode configurar as definições de VPN para as seguintes plataformas:

- [Android](#android-vpn-settings)
- [Android for Work](#android-for-work-vpn-settings)

Consoante as definições que escolher, nem todos os valores indicados abaixo são configuráveis.

## <a name="android-vpn-settings"></a>Definições VPN do Android
**Nome da ligação** – Introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Endereço IP ou FQDN** – Forneça o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos serão ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
- **Método de autenticação** – Escolha como os dispositivos serão autenticados no servidor VPN em:
    - **Certificados** – Selecione um perfil de certificado SCEP ou PKCS que criou anteriormente para autenticar a ligação. Para obter mais detalhes sobre os perfis de certificado, veja [Como configurar certificados](certificates-configure.md).
    - **Nome de utilizador e palavra-passe** – Os utilizadores finais têm de indicar um nome de utilizador e uma palavra-passe para iniciar sessão no servidor VPN.
- **Tipo de ligação** – Selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Citrix**

- **Identificação Digital** (apenas no Check Point Capsule VPN) – Especifique uma cadeia de carateres (por exemplo, “Código de Identificação Digital da Contoso”) que servirá para verificar a fidedignidade do servidor VPN. A identificação digital pode ser enviada para o cliente para que confie em qualquer servidor que apresente essa mesma identificação digital ao ligar. Se o dispositivo ainda não incluir a identificação digital, pedirá ao utilizador para confiar no servidor VPN ao qual se está a ligar e mostra a identificação digital (o utilizador verifica-a manualmente e escolhe Confiar para ligar).
- **Introduzir pares de chave e valor para os atributos de VPN do Citrix** (apenas no Citrix) – Introduza pares de chave e valor, disponibilizados pelo Citrix, para configurar as propriedades da ligação VPN.

## <a name="android-for-work-vpn-settings"></a>Definições VPN do Android for Work

**Nome da ligação** – Introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Endereço IP ou FQDN** – Forneça o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos serão ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
- **Método de autenticação** – Escolha como os dispositivos serão autenticados no servidor VPN em:
    - **Certificados** – Selecione um perfil de certificado SCEP ou PKCS que criou anteriormente para autenticar a ligação. Para obter mais detalhes sobre os perfis de certificado, veja [Como configurar certificados](certificates-configure.md).
    - **Nome de utilizador e palavra-passe** – Os utilizadores finais têm de indicar um nome de utilizador e uma palavra-passe para iniciar sessão no servidor VPN.
- **Tipo de ligação** – Selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

- **Divisão do túnel** – Ative para permitir que um determinado tráfego da Web utilize a ligação VPN enquanto outro tráfego utiliza a Internet. Desative esta definição caso pretenda que todo o tráfego utilize a VPN quando estiver ativa.
