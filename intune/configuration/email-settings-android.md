---
title: Definições de e-mail Android no Microsoft Intune - Azure Microsoft Docs
description: Criar um dispositivo de perfis de e-mail de configuração que utilizam servidores do Exchange e obter atributos do Azure Active Directory. Ative o SSL ou o SMIME, autentica os utilizadores com certificados ou nome de utilizador/palavra-passe, e sincroniza o e-mail e os horários dos dispositivos Android Samsung Knox utilizando o Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0a1bc53e0f05818b28bbd975e0de5cf5c9368afb
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512862"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Configurações do dispositivo Android para configurar e-mail, autenticação e sincronização em Intune

Este artigo lista e descreve as diferentes definições de e-mail que pode controlar nos dispositivos Android Samsung Knox em Intune. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para configurar um servidor de e-mail, utilize o SSL para encriptar mensagens de correio eletrónico e muito mais.

Como administrador intune, pode criar e atribuir definições de e-mail aos dispositivos Android Samsung Knox Standard.

Para saber mais sobre perfis de e-mail em Intune, consulte [configurar as definições de e-mail](email-settings-configure.md).

## <a name="before-you-begin"></a>Antes de começar

Criar um perfil de [configuração do dispositivo](email-settings-configure.md#create-a-device-profile).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Servidor de e-mail**: introduza o nome de anfitrião do seu servidor Exchange. Por exemplo, introduza `outlook.office365.com`.
- **Nome da conta**: introduza o nome a apresentar da conta de e-mail. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de utilizador do AAD**: este nome é o atributo que o Intune obtém do Azure Active Directory (Azure AD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:
  - **Nome Principal de Utilizador**: obtém o nome, como `user1` ou `user1@contoso.com`
  - **Nome de utilizador**: obtém apenas o nome como `user1`
  - **Nome da Conta SAM**: precisa do domínio, como `domain\user1`. O nome da conta sAM é usado apenas com dispositivos Android.

    Introduza também:  
    - **Origem de nome de domínio do utilizador**: selecione **AAD** (Azure Active Directory) ou **Personalizado**.

      Ao optar por obter os atributos do **AAD**, introduza:
      - **Origem de nome de domínio do utilizador do AAD**: selecione esta opção para obter o atributo **Nome de domínio completo** ou **Nome NetBIOS** do utilizador

      Ao optar por utilizar atributos **Personalizados**, introduza:
      - **Nome de domínio personalizado para utilizar**: introduza um valor para o Intune utilizar como nome de domínio, como `contoso.com` ou `contoso`

- **Atributo de endereço de e-mail da AAD**: Este nome é o atributo de e-mail que Intune recebe da AD Azure. Intune gera dinamicamente o endereço de e-mail que é usado por este perfil. As opções são:
  - **Nome principal**do utilizador : Utiliza o nome principal completo, como `user1@contoso.com` ou `user1`, como o endereço de e-mail.
  - **Endereço Principal SMTP**: Utiliza o endereço SMTP primário, como `user1@contoso.com`, para iniciar sessão no Exchange.

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

- Tipo de **conteúdo a sincronizar:** Selecione os tipos de conteúdo que pretende sincronizar nos dispositivos. **Não configurado desativa** esta definição. Quando definido para **Não configurado**, se um utilizador final permitir a sincronização no dispositivo, a sincronização é desativada novamente quando o dispositivo sincroniza com Intune, uma vez que a política é reforçada. 

  Pode sincronizar o seguinte conteúdo:  
  - **Contactos**: Escolha **o Enable** para permitir que os utilizadores finais sincronizem os contactos com os seus dispositivos.
  - **Calendário**: Escolha **o Habilitar** para permitir que os utilizadores finais sincroniem o calendário dos seus dispositivos.
  - **Tarefas**: Escolha **o Enable** para permitir que os utilizadores finais sincronem quaisquer tarefas nos seus dispositivos.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode criar perfis de email para Android Enterprise - perfil de [trabalho,](email-settings-android-enterprise.md) [iOS/iPadOS,](email-settings-ios.md) [Windows 10 e mais tarde](email-settings-windows-10.md)- e Windows Phone [8.1](email-settings-windows-phone-8-1.md).
