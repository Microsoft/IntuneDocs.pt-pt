---
title: Definições de Wi-Fi para dispositivos Android Enterprise e de local público
titleSuffix: Microsoft Intune
description: Crie ou adicione um perfil de configuração de dispositivos Wi-Fi para o Quiosque do Android e o Android Enterprise. Veja as diferentes definições, incluindo a adição de certificados, a escolha de um tipo de EAP e a seleção de um método de autenticação no Microsoft Intune. Para dispositivos de quiosque, introduza também a Chave pré-partilhada da sua rede.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 1424cd43c6ccde17724a4165fe74def4da291e29
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112362"
---
# <a name="add-wi-fi-settings-for-devices-running-android-enterprise-and-android-kiosk-in-microsoft-intune"></a>Adicionar definições de Wi-Fi para dispositivos com o quiosque Android ou Android Enterprise no Microsoft Intune

Pode criar um perfil com definições de Wi-Fi específicas e, em seguida, implementar este perfil nos dispositivos de quiosque do Android e Android Enterprise. O Microsoft Intune oferece muitas funcionalidades, incluindo a autenticação na rede, a utilização de uma chave pré-partilhada e mais.

Este artigo descreve estas definições.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](device-profile-create.md).

## <a name="device-owner-only---kiosk"></a>Apenas proprietário do dispositivo – quiosque

Selecione esta opção se utilizar um dispositivo Android Enterprise como um quiosque.

- **Nome da rede**: introduza um nome para esta ligação Wi-Fi. Este valor é o nome que os utilizadores veem quando navegam na lista de ligações disponíveis nos seus dispositivos.
- **SSID**: sigla de **service set identifier** (identificador do conjunto de serviço). Esta definição é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Ligar automaticamente**: escolha **Ativar** para ligar automaticamente a esta rede quando o dispositivo estiver dentro do alcance. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: escolha **Ativar** para ocultar esta rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de Wi-Fi**: selecione o protocolo de segurança para autenticar a rede Wi-Fi. As opções são:

  - **Abrir (sem autenticação)**: utilize esta opção apenas se a rede não estiver protegida.
  - **Chave WEP pré-partilhada**: introduza a palavra-passe na **Chave pré-partilhada**. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK.
  - **Chave WPA pré-partilhada**: introduza a palavra-passe na **Chave pré-partilhada**. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK.

Selecione **OK** para guardar as alterações.

## <a name="work-profile-only"></a>Apenas perfil de trabalho

### <a name="basic-settings"></a>Definições básicas

- **Tipo de Wi-Fi**: escolha **Básico**.
- **SSID**: sigla de **service set identifier** (identificador do conjunto de serviço). Esta definição é o nome real da rede sem fios à qual os dispositivos se ligam.
- **Ligar automaticamente**: escolha **Ativar** para ligar automaticamente a esta rede quando o dispositivo estiver dentro do alcance. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: escolha **Ativar** para ocultar esta rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.

## <a name="enterprise-profile"></a>Perfil empresarial

- **Tipo de Wi-Fi**: escolha **Empresarial**.
- **SSID**: sigla de **service set identifier** (identificador do conjunto de serviço). Esta definição é o nome real da rede sem fios à qual os dispositivos se ligam.
- **Ligar automaticamente**: escolha **Ativar** para ligar automaticamente a esta rede quando o dispositivo estiver dentro do alcance. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: escolha **Ativar** para ocultar esta rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de EAP**: escolha o tipo Protocolo EAP (Extensible Authentication Protocol) utilizado para autenticar as ligações sem fios protegidas. As opções são: 

  - **EAP-TLS**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.

      Selecione **OK** para guardar as alterações.

    - **Autenticação de Cliente** - **Certificado de cliente para autenticação de cliente (Certificado de identidade)**: escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      Selecione **OK** para guardar as alterações.

  - **EAP-TTLS**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.

      Selecione **OK** para guardar as alterações.

    - **Autenticação de Cliente** – escolha um **Método de autenticação**. As opções são:

      - **Nome de utilizador e Palavra-passe**: pedir ao utilizador um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP (identidade interna)**: escolha a forma como autentica a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi.

          As suas opções: **Palavra-passe não encriptada (PAP)**, **Protocolo CHAP (Challenge Handshake Authentication Protocol)**, **Microsoft CHAP (MS-CHAP)** ou **Microsoft CHAP versão 2 (MS-CHAP v2)**

      - **Certificados**: escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

        Selecione **OK** para guardar as alterações.

      - **Privacidade de identidade (identidade externa)**: introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **PEAP**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.

      Selecione **OK** para guardar as alterações.

    - **Autenticação de Cliente** – escolha um **Método de autenticação**. As opções são:

      - **Nome de utilizador e Palavra-passe**: pedir ao utilizador um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP para autenticação (identidade interna)**: escolha a forma como autentica a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi.

          As suas opções: **Nenhum** ou **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

        Selecione **OK** para guardar as alterações.

      - **Privacidade de identidade (identidade externa)**: introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

Selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e é apresentado na lista de perfis.

## <a name="next-steps"></a>Passos Seguintes

O perfil é criado, mas não faz nada. Em seguida, [atribua este perfil](device-profile-assign.md).

## <a name="more-resources"></a>Mais recursos

- Veja as definições disponíveis para dispositivos Android em [Definições de Wi-Fi para dispositivos Android](wi-fi-settings-android.md).
- [Descrição geral das definições de Wi-Fi](wi-fi-settings-configure.md), incluindo outras plataformas.