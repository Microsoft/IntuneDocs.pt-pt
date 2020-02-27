---
title: Configurações wi-fi para dispositivos Android Enterprise e quiosque - Microsoft Intune / Microsoft Docs
description: Crie ou adicione um perfil de configuração de dispositivos Wi-Fi para o Quiosque do Android e o Android Enterprise. Veja as diferentes definições, incluindo a adição de certificados, a escolha de um tipo de EAP e a seleção de um método de autenticação no Microsoft Intune. Para dispositivos de quiosque, introduza também a Chave pré-partilhada da sua rede.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/26/2020
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
ms.openlocfilehash: 6b6d5d51bedcd3f8251dd4ac307b58a08ba7cdc6
ms.sourcegitcommit: 8b716db3c0fdbb7dff62497ec283902a5069a343
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652441"
---
# <a name="add-wi-fi-settings-for-android-enterprise-dedicated-and-fully-managed-devices-in-microsoft-intune"></a>Adicione as definições de Wi-Fi para dispositivos Android Enterprise dedicados e totalmente geridos no Microsoft Intune

Pode criar um perfil com configurações wi-fi específicas e, em seguida, implementar este perfil para o seu Android Enterprise totalmente gerido e dedicado dispositivos. O Microsoft Intune oferece muitas funcionalidades, incluindo a autenticação na rede, a utilização de uma chave pré-partilhada e mais.

Este artigo descreve estas definições. [Utilize Wi-Fi nos seus dispositivos,](wi-fi-settings-configure.md) incluindo mais informações sobre a funcionalidade Wi-Fi no Microsoft Intune.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](wi-fi-settings-configure.md#create-a-device-profile).

## <a name="device-owner-only"></a>Proprietário do dispositivo apenas

Selecione esta opção se estiver a implementar para um dispositivo Android Enterprise dedicado ou totalmente gerido.  Os dispositivos android Enterprise dedicados e totalmente geridos suportam atualmente a implementação de certificados SCEP, mas não o PKCS.

### <a name="basic"></a>Básica

- **Tipo de Wi-Fi**: escolha **Básico**.
- **Nome da rede**: introduza um nome para esta ligação Wi-Fi. Os utilizadores finais vêem este nome quando navegam no seu dispositivo para ligações Wi-FI disponíveis. Por exemplo, introduza **Contoso WiFi**.
- **SSID**: Introduza o **identificador**de conjunto de serviços, que é o nome real da rede sem fios a que os dispositivos se ligam. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Rede oculta**: escolha **Ativar** para ocultar esta rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de Wi-Fi**: selecione o protocolo de segurança para autenticar a rede Wi-Fi. As opções são:

  - **Abrir (sem autenticação)** : utilize esta opção apenas se a rede não estiver protegida.
  - **Chave WEP pré-partilhada**: introduza a palavra-passe na **Chave pré-partilhada**. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK.
  - **Chave WPA pré-partilhada**: introduza a palavra-passe na **Chave pré-partilhada**. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK.

### <a name="enterprise"></a>Enterprise

- **Tipo de Wi-Fi**: escolha **Empresarial**.
- **SSID**: Introduza o **identificador**de conjunto de serviços, que é o nome real da rede sem fios a que os dispositivos se ligam. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Rede oculta**: escolha **Ativar** para ocultar esta rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de EAP**: escolha o tipo Protocolo EAP (Extensible Authentication Protocol) utilizado para autenticar as ligações sem fios protegidas. As opções são:

  - **EAP-TLS**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Quando o cliente se conecta à rede, este certificado é apresentado ao servidor e autentica a ligação.

    - **Autenticação do cliente** - **Certificado cliente para autenticação do cliente (Certificado de identidade)** : Escolha o perfil de certificado de cliente SCEP que também está implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

    - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **EAP-TTLS**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Quando o cliente se conecta à rede, este certificado é apresentado ao servidor e autentica a ligação.

    - **Autenticação do Cliente**: Escolha um método de **autenticação**. As opções são:

      - **Nome de utilizador e Palavra-passe**: pedir ao utilizador um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP (identidade interna)** : escolha a forma como autentica a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Palavra-passe não encriptada (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: Escolha o perfil de certificado de cliente SCEP que também está implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **PEAP**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Quando o cliente se conecta à rede, este certificado é apresentado ao servidor e autentica a ligação.

    - **Autenticação do Cliente**: Escolha um método de **autenticação**. As opções são:

      - **Nome de utilizador e Palavra-passe**: pedir ao utilizador um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP para autenticação (identidade interna)** : escolha a forma como autentica a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Nenhum**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: Escolha o perfil de certificado de cliente SCEP que também está implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

## <a name="work-profile-only"></a>Apenas perfil de trabalho

### <a name="basic"></a>Básica

- **Tipo de Wi-Fi**: escolha **Básico**.
- **SSID**: Introduza o **identificador**de conjunto de serviços, que é o nome real da rede sem fios a que os dispositivos se ligam. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Rede oculta**: escolha **Ativar** para ocultar esta rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.

### <a name="enterprise"></a>Enterprise

- **Tipo de Wi-Fi**: escolha **Empresarial**.
- **SSID**: Introduza o **identificador**de conjunto de serviços, que é o nome real da rede sem fios a que os dispositivos se ligam. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Rede oculta**: escolha **Ativar** para ocultar esta rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de EAP**: escolha o tipo Protocolo EAP (Extensible Authentication Protocol) utilizado para autenticar as ligações sem fios protegidas. As opções são:

  - **EAP-TLS**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Quando o cliente se conecta à rede, este certificado é apresentado ao servidor e autentica a ligação.

    - **Autenticação de Cliente** - **Certificado de cliente para autenticação de cliente (Certificado de identidade)** : escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

    - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **EAP-TTLS**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Quando o cliente se conecta à rede, este certificado é apresentado ao servidor e autentica a ligação.

    - **Autenticação do Cliente**: Escolha um método de **autenticação**. As opções são:

      - **Nome de utilizador e Palavra-passe**: pedir ao utilizador um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP (identidade interna)** : escolha a forma como autentica a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Palavra-passe não encriptada (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **PEAP**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Quando o cliente se conecta à rede, este certificado é apresentado ao servidor e autentica a ligação.

    - **Autenticação do Cliente**: Escolha um método de **autenticação**. As opções são:

      - **Nome de utilizador e Palavra-passe**: pedir ao utilizador um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP para autenticação (identidade interna)** : escolha a forma como autentica a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Nenhum**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

- **Definições de procuração**: Especifique a configuração de procuração utilizada pela sua organização. As opções são:

  - **Não** se usa um servidor de procuração.
  - **Automático** – Selecione esta opção para disponibilizar a definição de URL do *servidor proxy,* que utiliza para especificar o seu servidor proxy ou um ficheiro proxy Auto-Configuração (PAC) que contém uma lista dos seus servidores proxy.

- **URL do servidor proxy**: Esta definição está disponível quando define *as definições de Proxy* para *Automática*. Especifique uma das seguintes opções para direcionar os dispositivos para o seu servidor proxy:

  - Endereço IP. Por exemplo, `10.0.0.11`
  - Uma URL. Por exemplo, `http://proxyserver.contoso.com`.
  - O URL de um ficheiro proxy Auto-Configuração (PAC). Por exemplo: `http://proxy.contoso.com/proxy.pac`.

  Para obter mais informações sobre ficheiros PAC, consulte o [ficheiro Proxy Auto-Configuration (PAC)](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) (abre um site não Microsoft).

## <a name="next-steps"></a>Próximos passos

O perfil é criado, mas não faz nada. Em seguida, [atribua este perfil](device-profile-assign.md) e [monitorize o seu estado.](device-profile-monitor.md). .

Também pode criar perfis Wi-Fi para dispositivos [Android](wi-fi-settings-android.md), [iOS/iPadOS,](wi-fi-settings-ios.md) [macOS,](wi-fi-settings-macos.md) [Windows 10](wi-fi-settings-windows.md)e [Windows 8.1.](wi-fi-settings-import-windows-8-1.md)
