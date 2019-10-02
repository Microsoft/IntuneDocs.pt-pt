---
title: Configurações de Wi-Fi para dispositivos Android Enterprise e quiosque-Microsoft Intune | Microsoft Docs
description: Crie ou adicione um perfil de configuração de dispositivos Wi-Fi para o Quiosque do Android e o Android Enterprise. Veja as diferentes definições, incluindo a adição de certificados, a escolha de um tipo de EAP e a seleção de um método de autenticação no Microsoft Intune. Para dispositivos de quiosque, introduza também a Chave pré-partilhada da sua rede.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 51096b4ff42902b5feb8cecdebf9d839821e1bb2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730396"
---
# <a name="add-wi-fi-settings-for-devices-running-android-enterprise-and-android-kiosk-in-microsoft-intune"></a>Adicionar definições de Wi-Fi para dispositivos com o quiosque Android ou Android Enterprise no Microsoft Intune

Você pode criar um perfil com configurações de WiFi específicas e, em seguida, implantar esse perfil em seus dispositivos Android Enterprise e Android dedicado. O Microsoft Intune oferece muitas funcionalidades, incluindo a autenticação na rede, a utilização de uma chave pré-partilhada e mais.

Este artigo descreve estas definições. [Usar Wi-Fi em seus dispositivos](wi-fi-settings-configure.md) inclui mais informações sobre o recurso Wi-fi no Microsoft Intune.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](wi-fi-settings-configure.md#create-a-device-profile).

## <a name="device-owner-only"></a>Proprietário do dispositivo apenas

Selecione esta opção se estiver usando um dispositivo Android Enterprise dedicado como um quiosque.

### <a name="basic"></a>Básica

- **Tipo de Wi-Fi**: Selecione **Básico**.
- **Nome da rede**: Insira um nome para esta conexão Wi-Fi. Os usuários finais veem esse nome quando navegam em seu dispositivo para conexões Wi-FI disponíveis. Por exemplo, digite **contoso WiFi**.
- **SSID**: Insira o **identificador do conjunto de serviços**, que é o nome real da rede sem fio à qual os dispositivos se conectam. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Conectar automaticamente**: Escolha **habilitar** para se conectar automaticamente a esta rede quando o dispositivo estiver no intervalo. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: Escolha **habilitar** para ocultar essa rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de Wi-Fi**: Selecione o protocolo de segurança para autenticar na rede Wi-Fi. As opções são:

  - **Abrir (sem autenticação)** : Use esta opção somente se a rede não for segura.
  - **Chave pré-compartilhada WEP**: Insira a senha em **chave pré-compartilhada**. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK.
  - **Chave pré-compartilhada WPA**: Insira a senha em **chave pré-compartilhada**. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK.

### <a name="enterprise"></a>Empresarial

- **Tipo de Wi-Fi**: Escolha **Enterprise**.
- **SSID**: Insira o **identificador do conjunto de serviços**, que é o nome real da rede sem fio à qual os dispositivos se conectam. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Conectar automaticamente**: Escolha **habilitar** para se conectar automaticamente a esta rede quando o dispositivo estiver no intervalo. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: Escolha **habilitar** para ocultar essa rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de EAP**: Escolha o tipo de protocolo EAP (Extensible Authentication Protocol) usado para autenticar conexões sem fio seguras. As opções são:

  - **EAP-TLS**: Introduza também:

    - **Confiança do servidor** - **certificado raiz para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Quando o cliente se conecta à rede, esse certificado é apresentado ao servidor e autentica a conexão.

    -  - **Certificado de cliente de autenticação de cliente para autenticação de cliente (certificado de identidade)** : Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

    - **Privacidade de identidade (identidade externa)** : Insira o texto enviado na resposta a uma solicitação de identidade de EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **EAP-TTLS**: Introduza também:

    - **Confiança do servidor** - **certificado raiz para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Quando o cliente se conecta à rede, esse certificado é apresentado ao servidor e autentica a conexão.

    - **Autenticação de cliente**: Escolha um **método de autenticação**. As opções são:

      - **Nome de usuário e senha**: Solicite ao usuário um nome de usuário e uma senha para autenticar a conexão. Introduza também:
        - **Método não EAP (identidade interna)** : Escolha como você autentica a conexão. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Palavra-passe não encriptada (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : Insira o texto enviado na resposta a uma solicitação de identidade de EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **PEAP**: Introduza também:

    - **Confiança do servidor** - **certificado raiz para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Quando o cliente se conecta à rede, esse certificado é apresentado ao servidor e autentica a conexão.

    - **Autenticação de cliente**: Escolha um **método de autenticação**. As opções são:

      - **Nome de usuário e senha**: Solicite ao usuário um nome de usuário e uma senha para autenticar a conexão. Introduza também:
        - **Método não EAP para autenticação (identidade interna)** : Escolha como você autentica a conexão. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Nenhum**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : Insira o texto enviado na resposta a uma solicitação de identidade de EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

## <a name="work-profile-only"></a>Apenas perfil de trabalho

### <a name="basic"></a>Básica

- **Tipo de Wi-Fi**: Selecione **Básico**.
- **SSID**: Insira o **identificador do conjunto de serviços**, que é o nome real da rede sem fio à qual os dispositivos se conectam. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Conectar automaticamente**: Escolha **habilitar** para se conectar automaticamente a esta rede quando o dispositivo estiver no intervalo. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: Escolha **habilitar** para ocultar essa rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.

### <a name="enterprise"></a>Empresarial

- **Tipo de Wi-Fi**: Escolha **Enterprise**.
- **SSID**: Insira o **identificador do conjunto de serviços**, que é o nome real da rede sem fio à qual os dispositivos se conectam. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Conectar automaticamente**: Escolha **habilitar** para se conectar automaticamente a esta rede quando o dispositivo estiver no intervalo. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: Escolha **habilitar** para ocultar essa rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de EAP**: Escolha o tipo de protocolo EAP (Extensible Authentication Protocol) usado para autenticar conexões sem fio seguras. As opções são:

  - **EAP-TLS**: Introduza também:

    - **Confiança do servidor** - **certificado raiz para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Quando o cliente se conecta à rede, esse certificado é apresentado ao servidor e autentica a conexão.

    -  - **Certificado de cliente de autenticação de cliente para autenticação de cliente (certificado de identidade)** : Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

    - **Privacidade de identidade (identidade externa)** : Insira o texto enviado na resposta a uma solicitação de identidade de EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **EAP-TTLS**: Introduza também:

    - **Confiança do servidor** - **certificado raiz para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Quando o cliente se conecta à rede, esse certificado é apresentado ao servidor e autentica a conexão.

    - **Autenticação de cliente**: Escolha um **método de autenticação**. As opções são:

      - **Nome de usuário e senha**: Solicite ao usuário um nome de usuário e uma senha para autenticar a conexão. Introduza também:
        - **Método não EAP (identidade interna)** : Escolha como você autentica a conexão. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Palavra-passe não encriptada (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : Insira o texto enviado na resposta a uma solicitação de identidade de EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **PEAP**: Introduza também:

    - **Confiança do servidor** - **certificado raiz para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Quando o cliente se conecta à rede, esse certificado é apresentado ao servidor e autentica a conexão.

    - **Autenticação de cliente**: Escolha um **método de autenticação**. As opções são:

      - **Nome de usuário e senha**: Solicite ao usuário um nome de usuário e uma senha para autenticar a conexão. Introduza também:
        - **Método não EAP para autenticação (identidade interna)** : Escolha como você autentica a conexão. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Nenhum**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : Insira o texto enviado na resposta a uma solicitação de identidade de EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

## <a name="next-steps"></a>Passos seguintes

O perfil é criado, mas não faz nada. Em seguida, [atribua esse perfil](device-profile-assign.md) e [monitore seu status.](device-profile-monitor.md)..

Você também pode criar perfis de Wi-Fi para dispositivos [Android](wi-fi-settings-android.md), [Ios](wi-fi-settings-ios.md), [macOS](wi-fi-settings-macos.md), [Windows 10](wi-fi-settings-windows.md)e [Windows 8.1](wi-fi-settings-import-windows-8-1.md) .
