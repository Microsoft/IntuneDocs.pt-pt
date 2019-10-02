---
title: Configurar as definições de Wi-Fi para dispositivos macOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Crie ou adicione um perfil de configuração de dispositivos Wi-Fi para dispositivos macOS. Veja as diferentes definições, incluindo a adição de certificados, a escolha de um tipo de EAP e a seleção de um método de autenticação no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f81f4f04d1321697bce5de48eae50c2bdd8f15b7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730372"
---
# <a name="add-wi-fi-settings-for-macos-devices-in-microsoft-intune"></a>Adicionar definições de Wi-Fi para dispositivos macOS no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Pode criar um perfil com definições de Wi-Fi específicas e, em seguida, implementar este perfil nos seus dispositivos macOS. O Microsoft Intune oferece muitas funcionalidades, incluindo a autenticação na rede, a adição de um certificado PKS ou SCEP e mais.

Essas configurações de Wi-Fi são separadas em duas categorias: Configurações básicas e configurações de nível empresarial.

Este artigo descreve estas definições.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](device-profile-create.md).

> [!NOTE]
> Essas configurações estão disponíveis para todos os tipos de registro. Para obter mais informações sobre os tipos de registro, consulte [registro do MacOS](../enrollment/macos-enroll.md).

## <a name="basic-profiles"></a>Perfis básicos

- **Tipo de Wi-Fi**: Selecione **Básico**.
- **Nome da rede**: Insira um nome para esta conexão Wi-Fi. Este valor é o nome que os utilizadores veem quando navegam na lista de ligações disponíveis nos seus dispositivos.
- **SSID**: Abreviação do **identificador do conjunto de serviços**. Esta propriedade é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores apenas veem o nome da rede configurada por si quando selecionam a ligação.
- **Conectar automaticamente**: Escolha **habilitar** para se conectar automaticamente a esta rede quando o dispositivo estiver no intervalo. Escolha **Desativar** para impedir que os dispositivos se liguem automaticamente.
- **Rede oculta**: Escolha **habilitar** para ocultar essa rede da lista de redes disponíveis no dispositivo. O SSID não é difundido. Escolha **Desativar** para mostrar esta rede na lista de redes disponíveis no dispositivo.
- **Tipo de segurança**: Selecione o protocolo de segurança para autenticar na rede Wi-Fi. As opções são:

  - **Abrir (sem autenticação)** : Use esta opção somente se a rede não for segura.
  - **WPA/WPA2-Pessoal**: Insira a senha em **chave pré-compartilhada**. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK.
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

    -  - **Nomes do servidor do certificado**de confiança do servidor: **Adicione** um ou mais nomes comuns usados nos certificados emitidos pela autoridade de certificação (CA) confiável. Quando introduzir estas informações, pode ignorar a janela de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.
    - **Certificado raiz para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.

    -  - **Certificado de cliente de autenticação de cliente para autenticação de cliente (certificado de identidade)** : Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

  - **EAP-TTLS**: Introduza também:

    -  - **Nomes do servidor do certificado**de confiança do servidor: **Adicione** um ou mais nomes comuns usados nos certificados emitidos pela autoridade de certificação (CA) confiável. Quando introduzir estas informações, pode ignorar a janela de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.
    - **Certificado raiz para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.

    - **Autenticação de Cliente** – escolha um **Método de autenticação**. As opções são:

      - **Nome de usuário e senha**: Solicite ao usuário um nome de usuário e uma senha para autenticar a conexão. Introduza também:
        - **Método não EAP (identidade interna)** : Escolha como você autentica a conexão. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi.

          As opções são: **Senha não criptografada (PAP)** , **Challenge Handshake Authentication Protocol (CHAP)** , **Microsoft CHAP (ms-CHAP)** ou **Microsoft CHAP versão 2 (MS-CHAP v2)**

      - **Certificados**: Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : Insira o texto enviado na resposta a uma solicitação de identidade de EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

  - **LEAP**

  - **PEAP**: Introduza também:

    -  - **Nomes do servidor do certificado**de confiança do servidor: **Adicione** um ou mais nomes comuns usados nos certificados emitidos pela autoridade de certificação (CA) confiável. Quando introduzir estas informações, pode ignorar a janela de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.
    - **Certificado raiz para validação do servidor**: Escolha um perfil de certificado raiz confiável existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.

    - **Autenticação de Cliente** – escolha um **Método de autenticação**. As opções são:

      - **Nome de usuário e senha**: Solicite ao usuário um nome de usuário e uma senha para autenticar a conexão. 

      - **Certificados**: Escolha o perfil de certificado de cliente SCEP ou PKCS que também é implantado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.

      - **Privacidade de identidade (identidade externa)** : Insira o texto enviado na resposta a uma solicitação de identidade de EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

- **Configurações de proxy**: As opções são:
  - **Nenhum**: Nenhuma configuração de proxy está configurada.
  - **Manual**: Insira o **endereço do servidor proxy** como um endereço IP e o **número da porta**.
  - **Automático**: Use um arquivo para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, `http://proxy.contoso.com`) que contém o ficheiro de configuração.

## <a name="next-steps"></a>Passos seguintes

O perfil é criado, mas não faz nada. Em seguida, [atribua esse perfil](device-profile-assign.md) e [monitore seu status](device-profile-monitor.md).

Defina as configurações de Wi-Fi em dispositivos [Android](wi-fi-settings-android.md), [Android Enterprise](wi-fi-settings-android-enterprise.md), [Ios](wi-fi-settings-ios.md)e [Windows 10](wi-fi-settings-windows.md) .
