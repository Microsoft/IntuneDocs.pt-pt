---
title: Configurar definições de Wi-Fi para dispositivos Android no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Crie ou adicione um perfil de configuração de dispositivos Wi-Fi para Android. Veja as diferentes definições, incluindo a adição de certificados, a escolha de um tipo de EAP e a seleção de um método de autenticação no Microsoft Intune.
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
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d341aeace950f62ae699aa7760a65c0fd2f74fa
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550060"
---
# <a name="add-wi-fi-settings-for-devices-running-android-in-microsoft-intune"></a>Adicionar definições de Wi-Fi para dispositivos Android no Microsoft Intune

Pode criar um perfil com definições de Wi-Fi específicas e, em seguida, implementar este perfil nos seus dispositivos Android. O Microsoft Intune oferece muitas funcionalidades, incluindo a autenticação na rede, a adição de um certificado PKS ou SCEP e mais.

Essas configurações de Wi-Fi são separadas em duas categorias: Configurações básicas e configurações de nível empresarial.

Este artigo descreve estas definições.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](device-profile-create.md).

## <a name="basic"></a>Básica

- **Tipo de Wi-Fi**: Selecione **Básico**.
- **SSID**: Insira o **identificador do conjunto de serviços**, que é o nome real da rede sem fio à qual os dispositivos se conectam. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Conectar automaticamente**: Escolha **habilitar** para se conectar automaticamente a esta rede quando o dispositivo estiver no intervalo. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: Escolha **habilitar** para ocultar essa rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.

## <a name="enterprise"></a>Empresarial

- **Tipo de Wi-Fi**: Escolha **Enterprise**.
- **SSID**: Insira o **identificador do conjunto de serviços**, que é o nome real da rede sem fio à qual os dispositivos se conectam. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Conectar automaticamente**: Escolha **habilitar** para se conectar automaticamente a esta rede quando o dispositivo estiver no intervalo. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: Escolha **habilitar** para ocultar essa rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de EAP**: Escolha o tipo de protocolo EAP (Extensible Authentication Protocol) usado para autenticar conexões sem fio seguras. As opções são: 

  - **EAP-TLS**: Introduza também:

    -  - **Certificado raiz de confiança do servidor para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Esse certificado é apresentado ao servidor quando o cliente se conecta à rede. Ele autentica a conexão.

    -  - **Certificado de cliente de autenticação de cliente para autenticação de cliente (certificado de identidade)** : Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

    - **Privacidade de identidade (identidade externa)** : Insira o texto enviado na resposta a uma solicitação de identidade de EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **EAP-TTLS**: Introduza também:

    -  - **Certificado raiz de confiança do servidor para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Esse certificado é apresentado ao servidor quando o cliente se conecta à rede. Ele autentica a conexão.

    - **Autenticação de cliente**: Escolha um **método de autenticação**. As opções são:

      - **Nome de usuário e senha**: Solicite ao usuário um nome de usuário e uma senha para autenticar a conexão. Introduza também:
        - **Método não EAP (identidade interna)** : Escolha como você autentica a conexão. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Palavra-passe não encriptada (PAP)**
          - **CHAP (Challenge Handshake Authentication Protocol)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : Insira o texto enviado na resposta a uma solicitação de identidade de EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **PEAP**: Introduza também:

    -  - **Certificado raiz de confiança do servidor para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Esse certificado é apresentado ao servidor quando o cliente se conecta à rede. Ele autentica a conexão.

    - **Autenticação de cliente**: Escolha um **método de autenticação**. As opções são:

      - **Nome de usuário e senha**: Solicite ao usuário um nome de usuário e uma senha para autenticar a conexão. Introduza também:
        - **Método não EAP para autenticação (identidade interna)** : Escolha como você autentica a conexão. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Nenhum**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : Insira o texto enviado na resposta a uma solicitação de identidade de EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

## <a name="next-steps"></a>Passos seguintes

O perfil é criado, mas não faz nada. Em seguida, [atribua este perfil](device-profile-assign.md).

## <a name="more-resources"></a>Mais recursos

- [Descrição geral das definições de Wi-Fi](wi-fi-settings-configure.md), incluindo outras plataformas.

- Está a utilizar dispositivos de Quiosque Android ou Android Enterprise? Em caso afirmativo, examine [as configurações de Wi-Fi para dispositivos que executam dispositivos Android Enterprise e dedicados](wi-fi-settings-android-enterprise.md).
