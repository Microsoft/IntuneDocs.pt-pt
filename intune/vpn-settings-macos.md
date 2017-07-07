---
title: "Definições de VPN para dispositivos macOS | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba mais sobre as definições do Intune que pode utilizar para configurar ligações de VPN em dispositivos macOS."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d203a70d-37df-4195-85f7-ad5ef14ac2a1
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 4737fc863e3eda92eafd0536a07abf4100ebe9cc
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="vpn-settings-for-macos-devices-in-microsoft-intune"></a>Definições de VPN para dispositivos macOS no Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Consoante as definições que escolher, nem todos os valores na lista abaixo serão configuráveis.

## <a name="base-vpn-settings"></a>**Definições de VPN Base**

**Nome da ligação** – Introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Endereço IP ou FQDN** – Forneça o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos serão ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
- **Método de autenticação** – Escolha como os dispositivos serão autenticados no servidor VPN em:
    - **Certificados** – Em **Certificado de autenticação**, escolha um perfil de certificado SCEP ou PKCS que criou anteriormente para autenticar a ligação. Para obter mais detalhes sobre os perfis de certificado, veja [Como configurar certificados](certificates-configure.md).
    - **Nome de utilizador e palavra-passe** – Os utilizadores finais têm de indicar um nome de utilizador e uma palavra-passe para iniciar sessão no servidor VPN.
- **Tipo de ligação** – Selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **VPN Personalizada**
- **Divisão de túnel** - **Ative** ou **Desative** esta opção para permitir que os dispositivos decidam qual a ligação a utilizar consoante o tráfego. Por exemplo, um utilizador num hotel utilizará a ligação VPN para aceder aos ficheiros de trabalho, mas utilizará a rede padrão do hotel para a navegação normal na Internet.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>Definições de VPN Personalizada

Se tiver selecionado **VPN Personalizada**, configure estas definições adicionais:

- **Identificador VPN** – É o identificador da aplicação VPN que está a utilizar e é disponibilizado pelo seu fornecedor de VPN.
- **Introduzir pares de chave e valor para os atributos de VPN personalizados** – Adicione ou importe **Chaves** e **Valores** para personalizar a ligação VPN. Mais uma vez, estes valores são habitualmente disponibilizados pelo seu fornecedor de VPN.


## <a name="proxy-settings"></a>Definições de proxy

- **Script de configuração automática** – Utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, **http://proxy.contoso.com**) que contém o ficheiro de configuração.
- **Endereço** – Introduza o endereço do servidor proxy (como um endereço IP).
- **Número de porta** – Introduza o número de porta associado ao servidor proxy.
