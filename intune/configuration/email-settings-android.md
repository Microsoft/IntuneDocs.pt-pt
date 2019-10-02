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
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 647e1cd6925df27d42186599ad6786e866742b44
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730676"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Configurações do dispositivo Android para configurar email, autenticação e sincronização no Intune

Este artigo lista e descreve as diferentes configurações de email que você pode controlar em dispositivos Android Samsung Knox no Intune. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para configurar um servidor de e-mail, utilize o SSL para encriptar mensagens de correio eletrónico e muito mais.

Como administrador do Intune, você pode criar e atribuir configurações de email a dispositivos Android Samsung Knox Standard.

Para saber mais sobre perfis de email no Intune, consulte [definir configurações de email](email-settings-configure.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](email-settings-configure.md#create-a-device-profile).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Servidor de email**: Insira o nome do host do seu servidor Exchange. Por exemplo, introduza `outlook.office365.com`.
- **Nome da conta**: Insira o nome de exibição para a conta de email. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de usuário do AAD**: Esse nome é o atributo que o Intune obtém de Azure Active Directory (Azure AD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:
  - **Nome principal do usuário**: Obtém o nome, `user1` como ou`user1@contoso.com`
  - **Nome de usuário**: Obtém somente o nome, como`user1`
  - **nome da conta sAM**: Requer o domínio, `domain\user1`como. o nome da conta sAM é usado somente com dispositivos Android.

    Introduza também:  
    - **Origem do nome de domínio do usuário**: Escolha **AAD** (Azure Active Directory) ou **personalizado**.

      Ao optar por obter os atributos do **AAD**, introduza:
      - **Atributo de nome de domínio do usuário do AAD**: Opte por obter o **nome de domínio completo** ou o atributo de **nome NetBIOS** do usuário

      Ao optar por utilizar atributos **Personalizados**, introduza:
      - **Nome de domínio personalizado a ser usado**: Insira um valor que o Intune usa para o nome de domínio, `contoso.com` como ou`contoso`

- **Atributo de endereço de email do AAD**: Esse nome é o atributo de email que o Intune obtém do Azure AD. O Intune gera dinamicamente o endereço de email usado por esse perfil. As opções são:
  - **Nome principal do usuário**:  Usa o nome de entidade de segurança completo `user1@contoso.com` , `user1`como ou, como o endereço de email.
  - **Endereço SMTP primário**: Usa o endereço SMTP primário, `user1@contoso.com`como, para entrar no Exchange.

- **Método de autenticação**: Selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como método de autenticação utilizado pelo perfil de e-mail.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a ligação ao Exchange.

### <a name="security-settings"></a>Definições de segurança

- **SSL**: Utilize comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange Server.
- **S/MIME**: Envie e-mail através de encriptação S/MIME.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a ligação ao Exchange.

### <a name="synchronization-settings"></a>Definições de sincronização

- **Quantidade de email para sincronizar**: Escolha o número de dias de email que você deseja sincronizar ou selecione **ilimitado** para sincronizar todos os emails disponíveis.
- **Agenda de sincronização**: Selecione a agenda de dispositivos para sincronizar os dados do Exchange Server. Também pode selecionar **Quando chegarem mensagens**, que sincroniza os dados quando chegam, ou **Manual**, em que o utilizador do dispositivo tem de iniciar a sincronização.

### <a name="content-sync-settings"></a>Definições de sincronização de conteúdo

- **Tipo de conteúdo a ser sincronizado**: Selecione os tipos de conteúdo que você deseja sincronizar nos dispositivos. **Não configurado** desabilita essa configuração. Quando definido como **não configurado**, se um usuário final habilitar a sincronização no dispositivo, a sincronização será desabilitada novamente quando o dispositivo for sincronizado com o Intune, pois a política é reforçada. 

  Você pode sincronizar o seguinte conteúdo:  
  - **Contatos**: Escolha **habilitar** para permitir que os usuários finais sincronizem contatos com seus dispositivos.
  - **Calendário**: Escolha **habilitar** para permitir que os usuários finais sincronizem o calendário com seus dispositivos.
  - **Tarefas**: Escolha **habilitar** para permitir que os usuários finais sincronizem tarefas para seus dispositivos.

## <a name="next-steps"></a>Passos seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Você também pode criar perfis de email para [Android Enterprise – perfil de trabalho](email-settings-android-enterprise.md), [Ios](email-settings-ios.md), [Windows 10 e posterior](email-settings-windows-10.md)e [Windows Phone 8,1](email-settings-windows-phone-8-1.md).
