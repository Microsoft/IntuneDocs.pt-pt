---
title: Configurações de email do Android no Microsoft Intune – Azure | Microsoft Docs
description: Criar um dispositivo de perfis de e-mail de configuração que utilizam servidores do Exchange e obter atributos do Azure Active Directory. Habilitar SSL ou SMIME, autenticar usuários com certificados ou nome de usuário/senha e sincronizar email e agendas em dispositivos Android Samsung Knox usando o Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 43a2b00ae824656621c8a586e41ba6425c69ed40
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506761"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Configurações do dispositivo Android para configurar email, autenticação e sincronização no Intune

Este artigo lista e descreve as diferentes configurações de email que você pode controlar em dispositivos Android Samsung Knox no Intune. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para configurar um servidor de e-mail, utilize o SSL para encriptar mensagens de correio eletrónico e muito mais.

Como administrador do Intune, você pode criar e atribuir configurações de email a dispositivos Android Samsung Knox Standard.

Para saber mais sobre perfis de email no Intune, consulte [definir configurações de email](email-settings-configure.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](email-settings-configure.md#create-a-device-profile).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Servidor de e-mail**: introduza o nome de anfitrião do seu servidor Exchange. Por exemplo, introduza `outlook.office365.com`.
- **Nome da conta**: introduza o nome a apresentar da conta de e-mail. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de utilizador do AAD**: este nome é o atributo que o Intune obtém do Azure Active Directory (Azure AD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:
  - **Nome Principal de Utilizador**: obtém o nome, como `user1` ou `user1@contoso.com`.
  - **Nome de utilizador**: obtém apenas o nome como `user1`
  - **Nome da Conta SAM**: precisa do domínio, como `domain\user1`. o nome da conta sAM é usado somente com dispositivos Android.

    Introduza também:  
    - **Origem de nome de domínio do utilizador**: selecione **AAD** (Azure Active Directory) ou **Personalizado**.

      Ao optar por obter os atributos do **AAD**, introduza:
      - **Origem de nome de domínio do utilizador do AAD**: selecione esta opção para obter o atributo **Nome de domínio completo** ou **Nome NetBIOS** do utilizador

      Ao optar por utilizar atributos **Personalizados**, introduza:
      - **Nome de domínio personalizado para utilizar**: introduza um valor para o Intune utilizar como nome de domínio, como `contoso.com` ou `contoso`

- **Atributo de endereço de email do AAD**: esse nome é o atributo de email que o Intune obtém do Azure AD. O Intune gera dinamicamente o endereço de email usado por esse perfil. As opções são:
  - **Nome principal do usuário**: usa o nome da entidade de segurança completa, como `user1@contoso.com` ou `user1`, como o endereço de email.
  - **Endereço SMTP primário**: usa o endereço SMTP primário, como `user1@contoso.com`, para entrar no Exchange.

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

- **Tipo de conteúdo a ser sincronizado**: selecione os tipos de conteúdo que você deseja sincronizar nos dispositivos. **Não configurado** desabilita essa configuração. Quando definido como **não configurado**, se um usuário final habilitar a sincronização no dispositivo, a sincronização será desabilitada novamente quando o dispositivo for sincronizado com o Intune, pois a política é reforçada. 

  Você pode sincronizar o seguinte conteúdo:  
  - **Contatos**: escolha **habilitar** para permitir que os usuários finais sincronizem contatos com seus dispositivos.
  - **Calendário**: escolha **habilitar** para permitir que os usuários finais sincronizem o calendário com seus dispositivos.
  - **Tarefas**: escolha **habilitar** para permitir que os usuários finais sincronizem tarefas para seus dispositivos.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Você também pode criar perfis de email para [Android Enterprise – perfil de trabalho](email-settings-android-enterprise.md), [Ios](email-settings-ios.md), [Windows 10 e posterior](email-settings-windows-10.md)e [Windows Phone 8,1](email-settings-windows-phone-8-1.md).
