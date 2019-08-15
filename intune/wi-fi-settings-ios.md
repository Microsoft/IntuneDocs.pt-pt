---
title: Configurar as definições de Wi-Fi para dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Crie ou adicione um perfil de configuração de dispositivos Wi-Fi para dispositivos iOS. Veja as diferentes definições, incluindo a adição de certificados, a escolha de um tipo de EAP e a seleção de um método de autenticação no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04b864689bce1814eba78dc2435905d4df82e8c0
ms.sourcegitcommit: b30a2ba2b67aa2fc3421f0b2f6c5f361a0de612a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/14/2019
ms.locfileid: "69022687"
---
# <a name="add-wi-fi-settings-for-ios-devices-in-microsoft-intune"></a>Adicionar definições de Wi-Fi para dispositivos iOS no Microsoft Intune

Pode criar um perfil com definições de Wi-Fi específicas e, em seguida, implementar este perfil nos seus dispositivos iOS. O Microsoft Intune oferece muitas funcionalidades, incluindo a autenticação na rede, a adição de um certificado PKS ou SCEP e mais.

Essas configurações de Wi-Fi são separadas em duas categorias: Configurações básicas e configurações de nível empresarial.

Este artigo descreve estas definições.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](device-profile-create.md).

## <a name="basic-profiles"></a>Perfis básicos

- **Tipo de Wi-Fi**: Selecione **Básico**.
- **Nome da rede**: Insira um nome para esta conexão Wi-Fi. Este valor é o nome que os utilizadores veem quando navegam na lista de ligações disponíveis nos seus dispositivos.
- **SSID**: Abreviação do **identificador do conjunto de serviços**. Esta propriedade é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores apenas veem o nome da rede configurada por si quando selecionam a ligação.
- **Conectar automaticamente**: Escolha **habilitar** para se conectar automaticamente a esta rede quando o dispositivo estiver no intervalo. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: Escolha **habilitar** se o SSID da rede não for transmitido. Escolha **desabilitar** se o SSID da rede for transmitido e estiver visível.
- **Tipo de segurança**: Selecione o protocolo de segurança para autenticar na rede Wi-Fi. As opções são:

  - **Abrir (sem autenticação)** : Use esta opção somente se a rede não for segura.
  - **WPA/WPA2-Pessoal**: Insira a senha na **chave pré-compartilhada**. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK.
  - **WEP**

- **Configurações de proxy**: As opções são:
  - **Nenhum**: Nenhuma configuração de proxy está configurada.
  - **Manual**: Insira o **endereço do servidor proxy** como um endereço IP e o **número da porta**.
  - **Automático**: Use um arquivo para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, `http://proxy.contoso.com`) que contém o ficheiro de configuração.

## <a name="enterprise-profiles"></a>Perfis empresariais

- **Tipo de Wi-Fi**: Escolha **Enterprise**.
- **SSID**: Abreviação do **identificador do conjunto de serviços**. Esta propriedade é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores apenas veem o nome da rede configurada por si quando selecionam a ligação.
- **Conectar automaticamente**: Escolha **habilitar** para se conectar automaticamente a esta rede quando o dispositivo estiver no intervalo. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: Escolha **habilitar** para ocultar essa rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.

- **Tipo de EAP**: Escolha o tipo de protocolo EAP (Extensible Authentication Protocol) usado para autenticar conexões sem fio seguras. As opções são:

  - **EAP-FAST**: Insira as **configurações de Protected Access Credential (PAC)** . Esta opção utiliza credenciais de acesso protegido para criar um túnel autenticado entre o cliente e o servidor de autenticação. As opções são:
    - **Não utilizar (PAC)**
    - **Use (PAC)** : Se existir um arquivo PAC existente, use-o.
    - **Usar e provisionar PAC**: Crie e adicione o arquivo PAC aos seus dispositivos.
    - **Usar e provisionar PAC anonimamente**: Crie e adicione o arquivo PAC aos seus dispositivos sem autenticação no servidor.

  - **EAP-SIM**

  - **EAP-TLS**: Introduza também:

    -  - **Nomes do servidor do certificado**de confiança do servidor: **Adicione** um ou mais nomes comuns usados nos certificados emitidos por sua AC (autoridade de certificação) confiável para seus servidores de acesso à rede sem fio. Por exemplo, adicione `mywirelessserver.contoso.com` ou `mywirelessserver`. Quando introduzir estas informações, pode ignorar a janela de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.
    - **Certificado raiz para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Esse certificado permite que o cliente confie no certificado do servidor de acesso à rede sem fio.

      Selecione **OK** para guardar as alterações.

    -  - **Certificado de cliente de autenticação de cliente para autenticação de cliente (certificado de identidade)** : Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      Selecione **OK** para guardar as alterações.

  - **EAP-TTLS**: Introduza também:

    -  - **Nomes do servidor do certificado**de confiança do servidor: **Adicione** um ou mais nomes comuns usados nos certificados emitidos por sua AC (autoridade de certificação) confiável para seus servidores de acesso à rede sem fio. Por exemplo, adicione `mywirelessserver.contoso.com` ou `mywirelessserver`. Quando introduzir estas informações, pode ignorar a janela de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.
    - **Certificado raiz para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Esse certificado permite que o cliente confie no certificado do servidor de acesso à rede sem fio.

      Selecione **OK** para guardar as alterações.

    - **Autenticação de Cliente** – escolha um **Método de autenticação**. As opções são:

      - **Nome de usuário e senha**: Solicite ao usuário um nome de usuário e uma senha para autenticar a conexão. Introduza também:
        - **Método não EAP (identidade interna)** : Escolha como você autentica a conexão. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi.

          As opções são: **Senha não criptografada (PAP)** , **Challenge Handshake Authentication Protocol (CHAP)** , **Microsoft CHAP (ms-CHAP)** ou **Microsoft CHAP versão 2 (MS-CHAP v2)**

      - **Certificados**: Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

        Selecione **OK** para guardar as alterações.

      - **Privacidade de identidade (identidade externa)** : Insira o texto enviado na resposta a uma solicitação de identidade de EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **LEAP**

  - **PEAP**: Introduza também:

    -  - **Nomes do servidor do certificado**de confiança do servidor: **Adicione** um ou mais nomes comuns usados nos certificados emitidos por sua AC (autoridade de certificação) confiável para seus servidores de acesso à rede sem fio. Por exemplo, adicione `mywirelessserver.contoso.com` ou `mywirelessserver`. Quando introduzir estas informações, pode ignorar a janela de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.
    - **Certificado raiz para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Esse certificado permite que o cliente confie no certificado do servidor de acesso à rede sem fio.

      Selecione **OK** para guardar as alterações.

    - **Autenticação de Cliente** – escolha um **Método de autenticação**. As opções são:

      - **Nome de usuário e senha**: Solicite ao usuário um nome de usuário e uma senha para autenticar a conexão. 

      - **Certificados**: Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

        Selecione **OK** para guardar as alterações.

      - **Privacidade de identidade (identidade externa)** : Insira o texto enviado na resposta a uma solicitação de identidade de EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

- **Configurações de proxy**: As opções são:
  - **Nenhum**: Nenhuma configuração de proxy está configurada.
  - **Manual**: Insira o **endereço do servidor proxy** como um endereço IP e o **número da porta**.
  - **Automático**: Use um arquivo para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, `http://proxy.contoso.com`) que contém o ficheiro de configuração.

Selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e é apresentado na lista de perfis.

## <a name="next-steps"></a>Passos Seguintes

O perfil é criado, mas não faz nada. Em seguida, [atribua este perfil](device-profile-assign.md).

## <a name="more-resources"></a>Mais recursos

[Descrição geral das definições de Wi-Fi](wi-fi-settings-configure.md), incluindo outras plataformas disponíveis.
