---
title: Configurar definições de Wi-Fi para dispositivos Android no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Crie ou adicione um perfil de configuração de dispositivos Wi-Fi para Android. Veja as diferentes definições, incluindo a adição de certificados, a escolha de um tipo de EAP e a seleção de um método de autenticação no Microsoft Intune.
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
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a9bd1691b7943f02c9577e962fb1bcd5d9cf40a
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585339"
---
# <a name="add-wi-fi-settings-for-devices-running-android-in-microsoft-intune"></a>Adicionar definições de Wi-Fi para dispositivos Android no Microsoft Intune

Pode criar um perfil com definições de Wi-Fi específicas e, em seguida, implementar este perfil nos seus dispositivos Android. O Microsoft Intune oferece muitas funcionalidades, incluindo a autenticação na rede, a adição de um certificado PKS ou SCEP e mais.

Estas definições de Wi-Fi estão separadas em duas categorias: Definições básicas e Definições de nível empresarial.

Este artigo descreve estas definições.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](device-profile-create.md).

## <a name="basic"></a>Basic

- **Tipo de Wi-Fi**: escolha **Básico**.
- **SSID**: Insira o **identificador do conjunto de serviços**, que é o nome real da rede sem fio à qual os dispositivos se conectam. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Rede oculta**: escolha **Ativar** para ocultar esta rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.

## <a name="enterprise"></a>Porte

- **Tipo de Wi-Fi**: escolha **Empresarial**.
- **SSID**: Insira o **identificador do conjunto de serviços**, que é o nome real da rede sem fio à qual os dispositivos se conectam. No entanto, os utilizadores apenas veem o **nome da rede** que configurou quando selecionam a ligação.
- **Rede oculta**: escolha **Ativar** para ocultar esta rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de EAP**: escolha o tipo Protocolo EAP (Extensible Authentication Protocol) utilizado para autenticar as ligações sem fios protegidas. As opções são: 

  - **EAP-TLS**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Esse certificado é apresentado ao servidor quando o cliente se conecta à rede. Ele autentica a conexão.

    - **Autenticação de Cliente** - **Certificado de cliente para autenticação de cliente (Certificado de identidade)** : escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

    - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **EAP-TTLS**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Esse certificado é apresentado ao servidor quando o cliente se conecta à rede. Ele autentica a conexão.

    - **Autenticação de cliente**: escolha um **método de autenticação**. As opções são:

      - **Nome de utilizador e Palavra-passe**: pedir ao utilizador um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP (identidade interna)** : escolha a forma como autentica a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Palavra-passe não encriptada (PAP)**
          - **CHAP (Challenge Handshake Authentication Protocol)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **PEAP**: introduza também:

    - **Fidedignidade do Servidor** - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Esse certificado é apresentado ao servidor quando o cliente se conecta à rede. Ele autentica a conexão.

    - **Autenticação de cliente**: escolha um **método de autenticação**. As opções são:

      - **Nome de utilizador e Palavra-passe**: pedir ao utilizador um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP para autenticação (identidade interna)** : escolha a forma como autentica a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi. As opções são:

          - **Nenhum**
          - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

      - **Certificados**: escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

## <a name="next-steps"></a>Próximos passos

O perfil é criado, mas não faz nada. Em seguida, [atribua este perfil](device-profile-assign.md).

## <a name="more-resources"></a>Mais recursos

- [Descrição geral das definições de Wi-Fi](wi-fi-settings-configure.md), incluindo outras plataformas.

- Está a utilizar dispositivos de Quiosque Android ou Android Enterprise? Em caso afirmativo, examine [as configurações de Wi-Fi para dispositivos que executam dispositivos Android Enterprise e dedicados](wi-fi-settings-android-enterprise.md).
