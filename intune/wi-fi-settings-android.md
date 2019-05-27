---
title: Configurar definições de Wi-Fi para dispositivos Android no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Crie ou adicione um perfil de configuração de dispositivos Wi-Fi para Android. Veja as diferentes definições, incluindo a adição de certificados, a escolha de um tipo de EAP e a seleção de um método de autenticação no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 745bd930e43c9d034f66f6d529b489308a1bfe23
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66050288"
---
# <a name="add-wi-fi-settings-for-devices-running-android-in-microsoft-intune"></a>Adicionar definições de Wi-Fi para dispositivos Android no Microsoft Intune

Pode criar um perfil com definições de Wi-Fi específicas e, em seguida, implementar este perfil nos seus dispositivos Android. O Microsoft Intune oferece muitas funcionalidades, incluindo a autenticação na rede, a adição de um certificado PKS ou SCEP e mais.

Estas definições de Wi-Fi estão separadas para duas categorias: As definições de nível empresarial e as definições básicas.

Este artigo descreve estas definições.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](device-profile-create.md).

## <a name="basic-profile"></a>Perfil básico

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

    - **Fidedignidade do servidor** - **certificado de raiz para validação do servidor**: Escolha um perfil de certificado de raiz fidedigna existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.

      Selecione **OK** para guardar as alterações.

    - **Autenticação de cliente** - **certificado de cliente para autenticação de cliente (certificado de identidade)**: Escolha o SCEP ou PKCS de cliente de perfil de certificado que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      Selecione **OK** para guardar as alterações.

  - **EAP-TTLS**: Introduza também:

    - **Fidedignidade do servidor** - **certificado de raiz para validação do servidor**: Escolha um perfil de certificado de raiz fidedigna existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.

      Selecione **OK** para guardar as alterações.

    - **Autenticação de Cliente** – escolha um **Método de autenticação**. As opções são:

      - **Nome de utilizador e palavra-passe**: Pedir ao utilizador para um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP (identidade interna)**: Escolha a forma como autenticar a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi.

          As opções são: **Palavra-passe de não encriptada (PAP)**, **protocolo de autenticação de Handshake de desafio (CHAP)**, **Microsoft CHAP (MS-CHAP)**, ou **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certificados**: Escolha o SCEP ou PKCS de cliente de perfil de certificado que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

        Selecione **OK** para guardar as alterações.

      - **Privacidade de identidade (identidade externa)**: Introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **PEAP**: Introduza também:

    - **Fidedignidade do servidor** - **certificado de raiz para validação do servidor**: Escolha um perfil de certificado de raiz fidedigna existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.

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

O perfil é criado, mas não faz nada. Em seguida, [atribua este perfil](device-profile-assign.md).

## <a name="more-resources"></a>Mais recursos

- [Descrição geral das definições de Wi-Fi](wi-fi-settings-configure.md), incluindo outras plataformas.

- Está a utilizar dispositivos de Quiosque Android ou Android Enterprise? Se sim, veja as [Definições de Wi-Fi para dispositivos de quiosque Android ou Android Enterprise](wi-fi-settings-android-enterprise.md).
