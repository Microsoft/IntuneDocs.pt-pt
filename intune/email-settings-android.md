---
title: Definições de e-mail para dispositivos Android e com perfil de trabalho do Android no Microsoft Intune – Azure | Microsoft Docs
description: Crie um perfil de e-mail de configuração de dispositivos que utilize os servidores Exchange e obtenha atributos do Azure Active Directory. Também pode ativar o SSL ou S/MIME, autenticar utilizadores com certificados ou nome de utilizador/palavra-passe e sincronizar e-mails e agendas em dispositivos Android e dispositivos com perfil de trabalho do Android com o Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 136ccb6079b16c13098c1dbd6ca49e8254c14f89
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905772"
---
# <a name="email-profile-settings-for-devices-running-android-and-android-enterprise---intune"></a>Definições de perfis de e-mail para dispositivos Android e Android Enterprise – Intune

Utilize as definições do perfil de e-mail para configurar os seus dispositivos Android.

Enquanto administrador do Intune, pode criar e atribuir definições de e-mail aos seguintes dispositivos Android:

- Android Samsung Knox Standard
- Android Enterprise

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Servidor de e-mail**: introduza o nome de anfitrião do seu servidor Exchange.
- **Nome da conta**: introduza o nome a apresentar da conta de e-mail. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de utilizador do AAD**: este nome é o atributo que o Intune obtém do Azure Active Directory (AAD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:
  - **Nome Principal de Utilizador**: obtém o nome, como `user1` ou `user1@contoso.com`.
  - **Nome de utilizador**: obtém apenas o nome como `user1`
  - **Nome da Conta SAM**: precisa do domínio, como `domain\user1`. O nome da conta SAM só pode ser utilizado em dispositivos Android. O Android Enterprise não é suportado.

    Introduza também:  
    - **Origem de nome de domínio do utilizador**: selecione **AAD** (Azure Active Directory) ou **Personalizado**.

      Ao optar por obter os atributos do **AAD**, introduza:
      - **Origem de nome de domínio do utilizador do AAD**: selecione esta opção para obter o atributo **Nome de domínio completo** ou **Nome NetBIOS** do utilizador.

      Ao optar por utilizar atributos **Personalizados**, introduza:
      - **Nome de domínio personalizado para utilizar**: introduza um valor para o Intune utilizar como nome de domínio, como `contoso.com` ou `contoso`.

- **Atributo de endereço de e-mail do AAD**: selecione como é gerado o endereço de e-mail do utilizador. Selecione **Nome principal de utilizador** (`user1@contoso.com` ou `user1`) para utilizar o nome principal completo como o endereço de e-mail ou o **Endereço SMTP primário** (`user1@contoso.com`) para utilizar o endereço SMTP primário para iniciar sessão no Exchange.

- **Método de autenticação**: selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como o método de autenticação utilizado pelo perfil de e-mail.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a ligação ao Exchange.

### <a name="security-settings"></a>Definições de segurança

- **SSL**: utilize a comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o servidor Exchange.
- **S/MIME**: envie e-mails com a encriptação S/MIME.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a ligação ao Exchange.

### <a name="synchronization-settings"></a>Definições de sincronização

- **Quantidade de e-mails a sincronizar** : selecione o número de dias de e-mail que pretende sincronizar ou selecione **Sem Limite** para sincronizar todos os e-mails disponíveis.
- **Agenda de sincronização**: selecione o agendamento através do qual os dispositivos sincronizam os dados do servidor Exchange. Também pode selecionar **Quando chegarem mensagens**, que sincroniza os dados quando chegam, ou **Manual**, em que o utilizador do dispositivo tem de iniciar a sincronização.

### <a name="content-sync-settings"></a>Definições de sincronização de conteúdo

- **Tipo de conteúdo a sincronizar** – selecione os tipos de conteúdos que pretende sincronizar nos dispositivos a partir de:
  - **Contactos**
  - **Calendário**
  - **Tarefas**

## <a name="android-enterprise"></a>Android Enterprise

- **Aplicação de e-mail**: selecione **Gmail** ou **Nine Work**
- **Servidor de e-mail**: o nome de anfitrião do seu servidor Exchange.
- **Atributo de nome de utilizador do AAD**: este nome é o atributo no Active Directory (AD) ou Azure AD que serve para gerar o nome de utilizador para este perfil de e-mail. Selecione o **Endereço SMTP Principal**, como user1@contoso.com, ou o **Nome Principal de Utilizador**, como user1 ou user1@contoso.com.
- **Atributo de endereço de e-mail do AAD**: como é gerado o endereço de e-mail do utilizador em cada dispositivo. Selecione o **Nome Principal de Utilizador** para utilizar o nome principal completo como o endereço de e-mail ou o **Nome de utilizador**.
- **Método de autenticação**: selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como o método de autenticação utilizado pelo perfil de e-mail.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a ligação ao Exchange.
- **SSL**: utilize a comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o servidor Exchange.
- **Quantidade de e-mails a sincronizar** : selecione o número de dias de e-mail que pretende sincronizar ou selecione **Sem Limite** para sincronizar todos os e-mails disponíveis.
- **Tipo de conteúdo a sincronizar** (Nine Work apenas) – selecione os tipos de conteúdo que pretende sincronizar nos dispositivos a partir de:
  - **Contactos**
  - **Calendário**
  - **Tarefas**

## <a name="next-steps"></a>Próximos passos
[Configurar as definições de e-mail no Intune](email-settings-configure.md)
