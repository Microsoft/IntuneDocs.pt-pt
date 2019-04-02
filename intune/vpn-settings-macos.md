---
title: Definições de VPN para dispositivos macOS no Microsoft Intune
titleSuffix: ''
description: Saiba mais sobre as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f752ec33ca7a69d698ffe2c06c726f3881cc35ce
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798449"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-macos"></a>Configurar definições de VPN no Microsoft Intune para dispositivos com macOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com macOS.

Consoante as definições que escolher, nem todos os valores na lista seguinte serão configuráveis.

## <a name="base-vpn-settings"></a>Definições de VPN Base

**Nome da ligação** – Introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Endereço IP ou FQDN** – forneça o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos são ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
- **Método de autenticação** – escolha como os dispositivos serão autenticados no servidor VPN em:
    - **Certificados** – Em **Certificado de autenticação**, escolha um perfil de certificado SCEP ou PKCS que criou anteriormente para autenticar a ligação. Para obter mais detalhes sobre os perfis de certificado, veja [Como configurar certificados](certificates-configure.md).
    - **Nome de utilizador e palavra-passe** – Os utilizadores finais têm de indicar um nome de utilizador e uma palavra-passe para iniciar sessão no servidor VPN.
- **Tipo de ligação** – selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **VPN Personalizada**
- **Dividir túnel** - **Ative** ou **Desative** esta opção para permitir que os dispositivos decidam qual a ligação a utilizar consoante o tráfego. Por exemplo, um utilizador num hotel utiliza a ligação VPN para aceder aos ficheiros de trabalho, mas utiliza a rede padrão do hotel para a navegação normal na Internet.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>Definições de VPN Personalizada

Se tiver selecionado **VPN Personalizada**, configure estas definições adicionais:

- **Identificador VPN** – É o identificador da aplicação VPN que está a utilizar e é disponibilizado pelo seu fornecedor de VPN.
- **Introduzir pares de chave e valor para os atributos de VPN personalizados** – Adicione ou importe **Chaves** e **Valores** para personalizar a ligação VPN. Mais uma vez, estes valores são habitualmente disponibilizados pelo seu fornecedor de VPN.


## <a name="proxy-settings"></a>Definições de proxy

- **Script de configuração automática** – Utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor Proxy** que contém o ficheiro de configuração. Por exemplo, introduza `http://proxy.contoso.com`.
- **Endereço** – Introduza o endereço do servidor proxy (como um endereço IP).
- **Número de porta** – Introduza o número de porta associado ao servidor proxy.
