---
title: Definir configurações de rede com fio para dispositivos macOS no Microsoft Intune-Azure | Microsoft Docs
titleSuffix: ''
description: Criar ou adicionar um perfil de configuração de dispositivo de rede com fio para dispositivos macOS. Veja as diferentes definições, incluindo a adição de certificados, a escolha de um tipo de EAP e a seleção de um método de autenticação no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/4/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7dba36d03489bcdeee3c3c1f69a4995823dd21ee
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74994294"
---
# <a name="add-wired-network-settings-for-macos-devices-in-microsoft-intune"></a>Adicionar configurações de rede com fio para dispositivos macOS no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Você pode criar um perfil com configurações de rede com fio específicas e, em seguida, implantar esse perfil em seus dispositivos macOS. O Microsoft Intune oferece muitas funcionalidades, incluindo a autenticação na rede, a adição de um certificado PKS ou SCEP e mais. 

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](device-profile-create.md).

> [!NOTE]
> Essas configurações estão disponíveis para todos os tipos de registro. Para obter mais informações sobre os tipos de registro, consulte [registro do MacOS](../enrollment/macos-enroll.md).

## <a name="profiles"></a>Perfis

- **Tipo de perfil**: escolha **rede com fio**.
- **Interface de rede**: 
- **Tipo de EAP**: escolha o tipo Protocolo EAP (Extensible Authentication Protocol) utilizado para autenticar as ligações sem fios protegidas. As opções são:
  - **EAP-FAST**: introduza as **Definições de PAC (Protected Access Credential)** . Esta opção utiliza credenciais de acesso protegido para criar um túnel autenticado entre o cliente e o servidor de autenticação. As opções são:
    - **Não utilizar (PAC)**
    - **Utilizar (PAC)** : se existir um ficheiro PAC, utilize-o.
    - **Utilizar e Aprovisionar PAC**: crie e adicione o ficheiro PAC aos seus dispositivos.
    - **Utilizar e Aprovisionar PAC Anonimamente**: crie e adicione o ficheiro PAC aos seus dispositivos sem autenticar no servidor.
  - **EAP-TLS**: introduza também:
    - **Fidedignidade do Servidor** - **Nomes do servidor do certificado**: **adicione** um ou mais nomes comuns utilizados em certificados emitidos pela sua autoridade de certificação (AC) fidedigna. Quando introduzir estas informações, pode ignorar a janela de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.
    - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.
    - **Autenticação de Cliente** - **Certificado de cliente para autenticação de cliente (Certificado de identidade)** : escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.
  - **EAP-TTLS**: introduza também:
    - **Fidedignidade do Servidor** - **Nomes do servidor do certificado**: **adicione** um ou mais nomes comuns utilizados em certificados emitidos pela sua autoridade de certificação (AC) fidedigna. Quando introduzir estas informações, pode ignorar a janela de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.
    - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.
    - **Autenticação de Cliente** – escolha um **Método de autenticação**. As opções são:
      - **Nome de utilizador e Palavra-passe**: pedir ao utilizador um nome de utilizador e palavra-passe para autenticar a ligação. Introduza também:
        - **Método não EAP (identidade interna)** : escolha a forma como autentica a ligação. Garanta que escolhe o mesmo protocolo que está configurado na sua rede Wi-Fi.
          As suas opções: **Palavra-passe não encriptada (PAP)** , **Protocolo CHAP (Challenge Handshake Authentication Protocol)** , **Microsoft CHAP (MS-CHAP)** ou **Microsoft CHAP versão 2 (MS-CHAP v2)**
      - **Certificados**: escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.
      - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.
  - **LEAP**
  - **PEAP**: introduza também:
    - **Fidedignidade do Servidor** - **Nomes do servidor do certificado**: **adicione** um ou mais nomes comuns utilizados em certificados emitidos pela sua autoridade de certificação (AC) fidedigna. Quando introduzir estas informações, pode ignorar a janela de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.
    - **Certificado de raiz para a validação do servidor**: escolha um perfil de certificado de raiz fidedigna existente. Este certificado é apresentado ao servidor quando o cliente se liga à rede e serve para autenticar a ligação.
    - **Autenticação de Cliente** – escolha um **Método de autenticação**. As opções são:
      - **Nome de utilizador e Palavra-passe**: pedir ao utilizador um nome de utilizador e palavra-passe para autenticar a ligação. 
      - **Certificados**: escolha o perfil de certificado de cliente SCEP ou PKCS que também é implementado no dispositivo. Este certificado é a identidade apresentada pelo dispositivo ao servidor para autenticar a ligação.
      - **Privacidade de identidade (identidade externa)** : introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor, como `anonymous`. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

## <a name="next-steps"></a>Próximos passos

O perfil é criado, mas não faz nada. Em seguida, [atribua esse perfil](device-profile-assign.md) e [monitore seu status](device-profile-monitor.md).

Defina as configurações de Wi-Fi em dispositivos [Android](wi-fi-settings-android.md), [Android Enterprise](wi-fi-settings-android-enterprise.md), [Ios](wi-fi-settings-ios.md)e [Windows 10](wi-fi-settings-windows.md) .
