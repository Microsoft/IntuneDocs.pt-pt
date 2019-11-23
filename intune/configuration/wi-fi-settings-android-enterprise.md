---
title: Wi-Fi settings for Android Enterprise and kiosk devices - Microsoft Intune | Microsoft Docs
description: Crie ou adicione um perfil de configuração de dispositivos Wi-Fi para o Quiosque do Android e o Android Enterprise. Veja as diferentes definições, incluindo a adição de certificados, a escolha de um tipo de EAP e a seleção de um método de autenticação no Microsoft Intune. Para dispositivos de quiosque, introduza também a Chave pré-partilhada da sua rede.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: maholdaa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04d35f49f9e07cb72a1fea92210b05e0a95ec256
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390799"
---
# <a name="add-wi-fi-settings-for-android-enterprise-dedicated-and-fully-managed-devices-in-microsoft-intune"></a>Add Wi-Fi settings for Android Enterprise dedicated and fully managed devices in Microsoft Intune

You can create a profile with specific Wi-Fi settings, and then deploy this profile to your Android Enterprise fully managed and dedicated devices. O Microsoft Intune oferece muitas funcionalidades, incluindo a autenticação na rede, a utilização de uma chave pré-partilhada e mais.

Este artigo descreve estas definições. [Use Wi-Fi on your devices](wi-fi-settings-configure.md) includes more information about the Wi-Fi feature in Microsoft Intune.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](wi-fi-settings-configure.md#create-a-device-profile).

## <a name="device-owner-only"></a>Device owner only

Select this option if you are deploying to an Android Enterprise dedicated or fully managed device.  Android Enterprise dedicated and fully managed devices currently support SCEP certificate deployment, but not PKCS.

### <a name="basic"></a>Basic

- **Tipo de Wi-Fi**: escolha **Básico**.
- **Nome da rede**: introduza um nome para esta ligação Wi-Fi. End users see this name when they browse their device for available Wi-FI connections. For example, enter **Contoso WiFi**.
- **SSID**: Enter the **service set identifier**, which is the real name of the wireless network that devices connect to. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Rede oculta**: escolha **Ativar** para ocultar esta rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de Wi-Fi**: selecione o protocolo de segurança para autenticar a rede Wi-Fi. As opções são:

  - **Abrir (sem autenticação)** : utilize esta opção apenas se a rede não estiver protegida.
  - **Chave WEP pré-partilhada**: introduza a palavra-passe na **Chave pré-partilhada**. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK.
  - **Chave WPA pré-partilhada**: introduza a palavra-passe na **Chave pré-partilhada**. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK.

### <a name="enterprise"></a>Enterprise

- **Tipo de Wi-Fi**: escolha **Empresarial**.
- **SSID**: Enter the **service set identifier**, which is the real name of the wireless network that devices connect to. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Rede oculta**: escolha **Ativar** para ocultar esta rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de EAP**: escolha o tipo Protocolo EAP (Extensible Authentication Protocol) utilizado para autenticar as ligações sem fios protegidas. As opções são:

  - **EAP-TLS**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. When the client connects to the network, this certificate is presented to the server, and authenticates the connection.

    - **Client Authentication** - **Client certificate for client authentication (Identity certificate)** : Choose the SCEP client certificate profile that is also deployed to the device. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

    - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **EAP-TTLS**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. When the client connects to the network, this certificate is presented to the server, and authenticates the connection.

    - **Client Authentication**: Choose an **Authentication method**. As opções são:

      - **Nome de utilizador e Palavra-passe**: pedir ao utilizador um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP (identidade interna)** : escolha a forma como autentica a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Palavra-passe não encriptada (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificates**: Choose the SCEP client certificate profile that is also deployed to the device. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **PEAP**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. When the client connects to the network, this certificate is presented to the server, and authenticates the connection.

    - **Client Authentication**: Choose an **Authentication method**. As opções são:

      - **Nome de utilizador e Palavra-passe**: pedir ao utilizador um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP para autenticação (identidade interna)** : escolha a forma como autentica a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Nenhum**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificates**: Choose the SCEP client certificate profile that is also deployed to the device. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

## <a name="work-profile-only"></a>Apenas perfil de trabalho

### <a name="basic"></a>Basic

- **Tipo de Wi-Fi**: escolha **Básico**.
- **SSID**: Enter the **service set identifier**, which is the real name of the wireless network that devices connect to. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Rede oculta**: escolha **Ativar** para ocultar esta rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.

### <a name="enterprise"></a>Enterprise

- **Tipo de Wi-Fi**: escolha **Empresarial**.
- **SSID**: Enter the **service set identifier**, which is the real name of the wireless network that devices connect to. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Rede oculta**: escolha **Ativar** para ocultar esta rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de EAP**: escolha o tipo Protocolo EAP (Extensible Authentication Protocol) utilizado para autenticar as ligações sem fios protegidas. As opções são:

  - **EAP-TLS**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. When the client connects to the network, this certificate is presented to the server, and authenticates the connection.

    - **Autenticação de Cliente** - **Certificado de cliente para autenticação de cliente (Certificado de identidade)** : escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

    - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **EAP-TTLS**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. When the client connects to the network, this certificate is presented to the server, and authenticates the connection.

    - **Client Authentication**: Choose an **Authentication method**. As opções são:

      - **Nome de utilizador e Palavra-passe**: pedir ao utilizador um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP (identidade interna)** : escolha a forma como autentica a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Palavra-passe não encriptada (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **PEAP**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. When the client connects to the network, this certificate is presented to the server, and authenticates the connection.

    - **Client Authentication**: Choose an **Authentication method**. As opções são:

      - **Nome de utilizador e Palavra-passe**: pedir ao utilizador um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP para autenticação (identidade interna)** : escolha a forma como autentica a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Nenhum**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

## <a name="next-steps"></a>Próximos passos

O perfil é criado, mas não faz nada. Next, [assign this profile](device-profile-assign.md) and [monitor its status.](device-profile-monitor.md).

You can also create Wi-Fi profiles for [Android](wi-fi-settings-android.md), [iOS](wi-fi-settings-ios.md), [macOS](wi-fi-settings-macos.md), [Windows 10](wi-fi-settings-windows.md), and [Windows 8.1](wi-fi-settings-import-windows-8-1.md) devices.
