---
title: Android & definições de e-mail do Android Enterprise no Microsoft Intune – Azure | Documentos da Microsoft
description: Criar um dispositivo de perfis de e-mail de configuração que utilizam servidores do Exchange e obter atributos do Azure Active Directory. Ativar SSL ou SMIME, autenticar utilizadores com certificados ou o nome de utilizador/palavra-passe e sincronizar o e-mail e agendas on Android e Android através do Microsoft Intune de dispositivos de perfil de trabalho.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/15/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: b96363d679a6f09327bf9a1b46421e786d1956a8
ms.sourcegitcommit: 912aee714432c4a1e8efeee253ca2be4f972adaa
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54316887"
---
# <a name="android-and-android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Android e definições de dispositivos Android Enterprise para configurar o e-mail, autenticação e a sincronização no Intune

Este artigo apresenta uma lista e descreve as definições de correio eletrónico diferente que pode controlar em dispositivos Android e Android Enterprise. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para configurar um servidor de e-mail, utilize o SSL para encriptar mensagens de correio eletrónico e muito mais.

Enquanto administrador do Intune, pode criar e atribuir definições de e-mail aos seguintes dispositivos Android:

- Android Samsung Knox Standard
- Android Enterprise

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](email-settings-configure.md).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Servidor de e-mail**: Introduza o nome de anfitrião do seu Exchange server.
- **Nome da conta**: Introduza o nome a apresentar para a conta de e-mail. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de utilizador do AAD**: Este nome é o atributo que Intune obtém do Azure Active Directory (AAD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:
  - **Nome Principal de utilizador**: Obtém o nome, tais como `user1` ou `user1@contoso.com`
  - **Nome de utilizador**: Obtém apenas o nome, tal como `user1`
  - **sAM nome da conta**: Requer o domínio, tal como `domain\user1`. O nome da conta SAM só pode ser utilizado em dispositivos Android. O Android Enterprise não é suportado.

    Introduza também:  
    - **Origem de nome de domínio do utilizador**: Escolher **AAD** (o Azure Active Directory) ou **personalizado**.

      Ao optar por obter os atributos do **AAD**, introduza:
      - **Atributo de nome de domínio de utilizador do AAD**: Optar por receber as **nome de domínio completo** ou o **nome NetBIOS** atributo do utilizador

      Ao optar por utilizar atributos **Personalizados**, introduza:
      - **Nome de domínio personalizado para utilizar**: Introduza um valor que o Intune utiliza para o nome de domínio, tal como `contoso.com` ou `contoso`

- **Atributo de endereço de e-mail do AAD**: Escolha como é gerado o endereço de e-mail do utilizador. Selecione **Nome principal de utilizador** (`user1@contoso.com` ou `user1`) para utilizar o nome principal completo como o endereço de e-mail ou o **Endereço SMTP primário** (`user1@contoso.com`) para utilizar o endereço SMTP primário para iniciar sessão no Exchange.

- **Método de autenticação**: Selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como método de autenticação utilizado pelo perfil de e-mail.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a ligação ao Exchange.

### <a name="security-settings"></a>Definições de segurança

- **SSL**: Utilize comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange Server.
- **S/MIME**: Envie e-mail através de encriptação S/MIME.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a ligação ao Exchange.

### <a name="synchronization-settings"></a>Definições de sincronização

- **Quantidade de e-mails a sincronizar**: Escolher o número de dias de e-mail que pretende sincronizar ou selecione **ilimitado** para sincronizar todos os e-mails disponíveis.
- **Agenda de sincronização**: Selecione o agendamento para dispositivos sincronizar dados do Exchange server. Também pode selecionar **Quando chegarem mensagens**, que sincroniza os dados quando chegam, ou **Manual**, em que o utilizador do dispositivo tem de iniciar a sincronização.

### <a name="content-sync-settings"></a>Definições de sincronização de conteúdo

- **Tipo de conteúdo a sincronizar**: Selecione os tipos de conteúdo que pretende sincronizar nos dispositivos. **Não configurado** desativa esta definição. Quando definido como **não configurado**, se a sincronização de permite que um utilizador final no dispositivo, a sincronização está desabilitada novamente quando o dispositivo for sincronizado com o Intune, conforme a política é reforçada. 

  Pode sincronizar o seguinte conteúdo: 
  - **Contactos**
  - **Calendário**
  - **Tarefas**

## <a name="android-enterprise"></a>Android Enterprise

- **Aplicação de e-mail**: Selecione **Gmail** ou **Nine Work**
- **Servidor de e-mail**: O nome de anfitrião do seu Exchange server.
- **Atributo de nome de utilizador do AAD**: Este nome é o atributo no Active Directory (AD) ou Azure AD, o que é utilizado para gerar o nome de utilizador para este perfil de e-mail. Selecione o **Endereço SMTP Principal**, como user1@contoso.com, ou o **Nome Principal de Utilizador**, como user1 ou user1@contoso.com.
- **Atributo de endereço de e-mail do AAD**: Como é gerado o endereço de e-mail para o utilizador em cada dispositivo. Selecione o **Nome Principal de Utilizador** para utilizar o nome principal completo como o endereço de e-mail ou o **Nome de utilizador**.
- **Método de autenticação**: Selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como método de autenticação utilizado pelo perfil de e-mail.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a ligação ao Exchange.
- **SSL**: Utilize comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange Server.
- **Quantidade de e-mails a sincronizar**: Escolher o número de dias de e-mail que pretende sincronizar ou selecione **ilimitado** para sincronizar todos os e-mails disponíveis.
- **Tipo de conteúdo a sincronizar** (Nine Work apenas): Selecione os tipos de conteúdo que pretende sincronizar nos dispositivos. **Não configurado** desativa esta definição. Quando definido como **não configurado**, se a sincronização de permite que um utilizador final no dispositivo, a sincronização está desabilitada novamente quando o dispositivo for sincronizado com o Intune, conforme a política é reforçada. 

  Pode sincronizar o seguinte conteúdo: 
  - **Contactos**
  - **Calendário**
  - **Tarefas**

## <a name="next-steps"></a>Passos Seguintes
[Configurar as definições de e-mail no Intune](email-settings-configure.md)
