---
title: "Definições de VPN do Intune para dispositivos Android | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba mais sobre as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos Android."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 16c056ca-320e-4107-ad03-a0cf96c28885
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6cd3069a63bd657d1c9f5e33b96db39a3b3f98d2
ms.openlocfilehash: f93ab44889837fe8acc5dd5287b63f3b30678159


---

# <a name="vpn-settings-for-android-devices-in-intune-azure-preview"></a>Definições de VPN para dispositivos Android na pré-visualização do Azure no Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Consoante as definições que escolher, nem todos os valores na lista abaixo serão configuráveis.

**Nome da ligação** – Introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Endereço IP ou FQDN** – Forneça o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos serão ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
- **Método de autenticação** – Escolha como os dispositivos serão autenticados no servidor VPN em:
    - **Certificados** – Selecione um perfil de certificado SCEP ou PKCS que criou anteriormente para autenticar a ligação. Para obter mais detalhes sobre os perfis de certificado, veja [Como configurar certificados](how-to-configure-certificates.md).
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



<!--HONumber=Feb17_HO2-->

