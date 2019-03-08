---
title: Definições de Wi-Fi para dispositivos Android Enterprise e de local público – Microsoft Intune | Documentos da Microsoft
description: Crie ou adicione um perfil de configuração de dispositivos Wi-Fi para o Quiosque do Android e o Android Enterprise. Veja as diferentes definições, incluindo a adição de certificados, a escolha de um tipo de EAP e a seleção de um método de autenticação no Microsoft Intune. Para dispositivos de quiosque, introduza também a Chave pré-partilhada da sua rede.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d96bf5a4b0d9a8ce6aa7de0123a8bcc7e6db9692
ms.sourcegitcommit: 9a4c5b6c2ce511edaeace25426a23f180cb71e15
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/07/2019
ms.locfileid: "57566442"
---
# <a name="add-wi-fi-settings-for-devices-running-android-enterprise-and-android-kiosk-in-microsoft-intune"></a>Adicionar definições de Wi-Fi para dispositivos com o quiosque Android ou Android Enterprise no Microsoft Intune

Pode criar um perfil com definições de Wi-Fi específicas e, em seguida, implementar este perfil nos dispositivos de quiosque do Android e Android Enterprise. O Microsoft Intune oferece muitas funcionalidades, incluindo a autenticação na rede, a utilização de uma chave pré-partilhada e mais.

Este artigo descreve estas definições. [Utilizar o Wi-Fi nos seus dispositivos](wi-fi-settings-configure.md) inclui mais informações sobre a funcionalidade Wi-Fi no Microsoft Intune.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](wi-fi-settings-configure.md#create-a-device-profile).

## <a name="device-owner-only---kiosk"></a>Apenas proprietário do dispositivo – quiosque

Selecione esta opção se utilizar um dispositivo Android Enterprise como um quiosque.

- **Nome da rede**: Introduza um nome para esta ligação Wi-Fi. Este valor é o nome que os utilizadores veem quando navegam na lista de ligações disponíveis nos seus dispositivos.
- **SSID**: Abreviação de **identificador do conjunto de serviço**. Esta definição é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Ligar automaticamente**: Escolher **ativar** para ligar automaticamente a esta rede quando o dispositivo estiver no intervalo. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: Escolher **ativar** para ocultar esta rede na lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de Wi-Fi**: Selecione o protocolo de segurança para autenticar-se à rede Wi-Fi. As opções são:

  - **Abrir (sem autenticação)**: Utilize esta opção apenas se a rede não for protegida.
  - **Chave WEP pré-partilhada**: Introduza a palavra-passe na **chave pré-partilhada**. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK.
  - **Chave WPA pré-partilhada**: Introduza a palavra-passe na **chave pré-partilhada**. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK.

Selecione **OK** para guardar as alterações.

## <a name="work-profile-only"></a>Apenas perfil de trabalho

### <a name="basic-settings"></a>Definições básicas

- **Tipo de Wi-Fi**: Selecione **Básico**.
- **SSID**: Abreviação de **identificador do conjunto de serviço**. Esta definição é o nome real da rede sem fios à qual os dispositivos se ligam.
- **Ligar automaticamente**: Escolher **ativar** para ligar automaticamente a esta rede quando o dispositivo estiver no intervalo. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: Escolher **ativar** para ocultar esta rede na lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.

## <a name="enterprise-profile"></a>Perfil empresarial

- **Tipo de Wi-Fi**: Escolher **Enterprise**.
- **SSID**: Abreviação de **identificador do conjunto de serviço**. Esta definição é o nome real da rede sem fios à qual os dispositivos se ligam.
- **Ligar automaticamente**: Escolher **ativar** para ligar automaticamente a esta rede quando o dispositivo estiver no intervalo. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: Escolher **ativar** para ocultar esta rede na lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de EAP**: Escolha o tipo de protocolo de autenticação extensível (EAP) utilizado para autenticar as ligações sem fios protegidas. As opções são: 

  - **EAP-TLS**: Introduza também:

    - **Fidedignidade do servidor** - **certificado de raiz para validação do servidor**: Escolha um perfil de certificado de raiz fidedigna existente. Quando o cliente se conecta à rede, este certificado é apresentado para o servidor e irá autenticar a ligação.

      Selecione **OK** para guardar as alterações.

    - **Autenticação de cliente** - **certificado de cliente para autenticação de cliente (certificado de identidade)**: Escolha o SCEP ou PKCS de cliente de perfil de certificado que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      Selecione **OK** para guardar as alterações.

  - **EAP-TTLS**: Introduza também:

    - **Fidedignidade do servidor** - **certificado de raiz para validação do servidor**: Escolha um perfil de certificado de raiz fidedigna existente. Quando o cliente se conecta à rede, este certificado é apresentado para o servidor e irá autenticar a ligação.

      Selecione **OK** para guardar as alterações.

    - **Autenticação de Cliente** – escolha um **Método de autenticação**. As opções são:

      - **Nome de utilizador e palavra-passe**: Pedir ao utilizador para um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP (identidade interna)**: Escolha a forma como autenticar a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi.

          As opções são: **Palavra-passe de não encriptada (PAP)**, **protocolo de autenticação de Handshake de desafio (CHAP)**, **Microsoft CHAP (MS-CHAP)**, ou **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certificados**: Escolha o SCEP ou PKCS de cliente de perfil de certificado que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

        Selecione **OK** para guardar as alterações.

      - **Privacidade de identidade (identidade externa)**: Introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **PEAP**: Introduza também:

    - **Fidedignidade do servidor** - **certificado de raiz para validação do servidor**: Escolha um perfil de certificado de raiz fidedigna existente. Quando o cliente se conecta à rede, este certificado é apresentado para o servidor e irá autenticar a ligação.

      Selecione **OK** para guardar as alterações.

    - **Autenticação de Cliente** – escolha um **Método de autenticação**. As opções são:

      - **Nome de utilizador e palavra-passe**: Pedir ao utilizador para um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP para autenticação (identidade interna)**: Escolha a forma como autenticar a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi.

          As opções são: **NONE** ou **Microsoft CHAP versão 2 (MS-CHAP v2)**

      - **Certificados**: Escolha o SCEP ou PKCS de cliente de perfil de certificado que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

        Selecione **OK** para guardar as alterações.

      - **Privacidade de identidade (identidade externa)**: Introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

Selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e é apresentado na lista de perfis.

## <a name="next-steps"></a>Passos Seguintes

O perfil é criado, mas não faz nada. Em seguida, [atribuir este perfil](device-profile-assign.md) e [monitorizar o estado.](device-profile-monitor.md).

Também pode criar perfis de Wi-Fi para [Android](wi-fi-settings-android.md), [iOS](wi-fi-settings-ios.md), [macOS](wi-fi-settings-macos.md), [com o Windows 10](wi-fi-settings-windows.md), e [Windows 8.1](wi-fi-settings-import-windows-8-1.md)dispositivos.
