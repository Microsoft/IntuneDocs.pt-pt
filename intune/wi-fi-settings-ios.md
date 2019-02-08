---
title: Configurar as definições de Wi-Fi para dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Crie ou adicione um perfil de configuração de dispositivos Wi-Fi para dispositivos iOS. Veja as diferentes definições, incluindo a adição de certificados, a escolha de um tipo de EAP e a seleção de um método de autenticação no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0a17be2e6cb30612fbf8a91f63d3b99ed6c7e19b
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55837445"
---
# <a name="add-wi-fi-settings-for-ios-devices-in-microsoft-intune"></a>Adicionar definições de Wi-Fi para dispositivos iOS no Microsoft Intune

Pode criar um perfil com definições de Wi-Fi específicas e, em seguida, implementar este perfil nos seus dispositivos iOS. O Microsoft Intune oferece muitas funcionalidades, incluindo a autenticação na rede, a adição de um certificado PKS ou SCEP e mais.

Estas definições de Wi-Fi estão separadas para duas categorias: As definições de nível empresarial e as definições básicas.

Este artigo descreve estas definições.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](device-profile-create.md).

## <a name="basic-profiles"></a>Perfis básicos

- **Tipo de Wi-Fi**: Selecione **Básico**.
- **Nome da rede**: Introduza um nome para esta ligação Wi-Fi. Este valor é o nome que os utilizadores veem quando navegam na lista de ligações disponíveis nos seus dispositivos.
- **SSID**: Abreviação de **identificador do conjunto de serviço**. Esta propriedade é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores apenas veem o nome da rede configurada por si quando selecionam a ligação.
- **Ligar automaticamente**: Escolher **ativar** para ligar automaticamente a esta rede quando o dispositivo estiver no intervalo. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: Escolher **ativar** se não estiver difundiu o SSID da rede. Escolher **desativar** se o SSID da rede é difundiu e visíveis.
- **Tipo de segurança**: Selecione o protocolo de segurança para autenticar-se à rede Wi-Fi. As opções são:

  - **Abrir (sem autenticação)**: Utilize esta opção apenas se a rede não for protegida.
  - **WPA/WPA2 – pessoal**: Introduza a palavra-passe na **chave pré-partilhada**. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK.
  - **WEP**

- **Definições de proxy**: As opções são:
  - **Nenhum**: Não existem definições de proxy estão configuradas.
  - **Manual**: Introduza o **endereço do servidor Proxy** como um endereço IP e a respetiva **número de porta**.
  - **Automática**: Utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, `http://proxy.contoso.com`) que contém o ficheiro de configuração.

## <a name="enterprise-profiles"></a>Perfis empresariais

- **Tipo de Wi-Fi**: Escolher **Enterprise**.
- **SSID**: Abreviação de **identificador do conjunto de serviço**. Esta propriedade é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores apenas veem o nome da rede configurada por si quando selecionam a ligação.
- **Ligar automaticamente**: Escolher **ativar** para ligar automaticamente a esta rede quando o dispositivo estiver no intervalo. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: Escolher **ativar** para ocultar esta rede na lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.

- **Tipo de EAP**: Escolha o tipo de protocolo de autenticação extensível (EAP) utilizado para autenticar as ligações sem fios protegidas. As opções são:

  - **EAP-FAST**: Introduza o **definições de credencial (PAC) de acesso protegido**. Esta opção utiliza credenciais de acesso protegido para criar um túnel autenticado entre o cliente e o servidor de autenticação. As opções são:
    - **Não utilizar (PAC)**
    - **Utilizar (PAC)**: Se existir um ficheiro PAC existente, utilizá-lo.
    - **Utilizar e aprovisionar PAC**: Criar e adicionar o ficheiro PAC para os seus dispositivos.
    - **Utilizar e aprovisionar PAC anonimamente**: Criar e adicionar o ficheiro PAC para os seus dispositivos sem autenticar para o servidor.

  - **EAP-SIM**

  - **EAP-TLS**: Introduza também:

    - **Fidedignidade do servidor** - **nomes de servidor de certificado**: **Adicionar** um ou mais nomes comuns utilizados em certificados emitidos pela sua autoridade de certificação fidedigna (AC). Quando introduzir estas informações, pode ignorar a janela de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.
    - **Certificado de raiz para validação do servidor**: Escolha um perfil de certificado de raiz fidedigna existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.

      Selecione **OK** para guardar as alterações.

    - **Autenticação de cliente** - **certificado de cliente para autenticação de cliente (certificado de identidade)**: Escolha o SCEP ou PKCS de cliente de perfil de certificado que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      Selecione **OK** para guardar as alterações.

  - **EAP-TTLS**: Introduza também:

    - **Fidedignidade do servidor** - **nomes de servidor de certificado**: **Adicionar** um ou mais nomes comuns utilizados em certificados emitidos pela sua autoridade de certificação fidedigna (AC). Quando introduzir estas informações, pode ignorar a janela de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.
    - **Certificado de raiz para validação do servidor**: Escolha um perfil de certificado de raiz fidedigna existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.

      Selecione **OK** para guardar as alterações.

    - **Autenticação de Cliente** – escolha um **Método de autenticação**. As opções são:

      - **Nome de utilizador e palavra-passe**: Pedir ao utilizador para um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP (identidade interna)**: Escolha a forma como autenticar a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi.

          As opções são: **Palavra-passe de não encriptada (PAP)**, **protocolo de autenticação de Handshake de desafio (CHAP)**, **Microsoft CHAP (MS-CHAP)**, ou **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certificados**: Escolha o SCEP ou PKCS de cliente de perfil de certificado que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

        Selecione **OK** para guardar as alterações.

      - **Privacidade de identidade (identidade externa)**: Introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **LEAP**

  - **PEAP**: Introduza também:

    - **Fidedignidade do servidor** - **nomes de servidor de certificado**: **Adicionar** um ou mais nomes comuns utilizados em certificados emitidos pela sua autoridade de certificação fidedigna (AC). Quando introduzir estas informações, pode ignorar a janela de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.
    - **Certificado de raiz para validação do servidor**: Escolha um perfil de certificado de raiz fidedigna existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.

      Selecione **OK** para guardar as alterações.

    - **Autenticação de Cliente** – escolha um **Método de autenticação**. As opções são:

      - **Nome de utilizador e palavra-passe**: Pedir ao utilizador para um nome de utilizador e palavra-passe para autenticar a ligação. 

      - **Certificados**: Escolha o SCEP ou PKCS de cliente de perfil de certificado que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

        Selecione **OK** para guardar as alterações.

      - **Privacidade de identidade (identidade externa)**: Introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

- **Definições de proxy**: As opções são:
  - **Nenhum**: Não existem definições de proxy estão configuradas.
  - **Manual**: Introduza o **endereço do servidor Proxy** como um endereço IP e a respetiva **número de porta**.
  - **Automática**: Utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, `http://proxy.contoso.com`) que contém o ficheiro de configuração.

Selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e é apresentado na lista de perfis.

## <a name="next-steps"></a>Passos Seguintes

O perfil é criado, mas não faz nada. Em seguida, [atribua este perfil](device-profile-assign.md).

## <a name="more-resources"></a>Mais recursos

[Descrição geral das definições de Wi-Fi](wi-fi-settings-configure.md), incluindo outras plataformas disponíveis.
