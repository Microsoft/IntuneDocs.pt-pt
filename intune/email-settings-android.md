---
title: Definições de e-mail Android no Microsoft Intune – Azure | Documentos da Microsoft
description: Criar um dispositivo de perfis de e-mail de configuração que utilizam servidores do Exchange e obter atributos do Azure Active Directory. Ativar SSL ou SMIME, autenticar utilizadores com certificados ou o nome de utilizador/palavra-passe e sincronizar o e-mail e agendas em dispositivos Android Samsung Knox com o Microsoft Intune.
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
ms.openlocfilehash: 4336be8d24ac4a81ec6fca09f22d594000bbd9a5
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831397"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Definições de dispositivo Android para configurar o e-mail, autenticação e a sincronização no Intune

Este artigo apresenta uma lista e descreve as definições de correio eletrónico diferente que pode controlar em dispositivos Android Samsung Knox no Intune. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para configurar um servidor de e-mail, utilize o SSL para encriptar mensagens de correio eletrónico e muito mais.

Enquanto administrador do Intune, pode criar e atribuir definições de e-mail para dispositivos Android Samsung Knox Standard.

Para obter mais informações sobre perfis de e-mail no Intune, consulte [configurar definições de e-mail](email-settings-configure.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](email-settings-configure.md#create-a-device-profile).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Servidor de e-mail**: Introduza o nome de anfitrião do seu Exchange server. Por exemplo, introduza `outlook.office365.com`.
- **Nome da conta**: Introduza o nome a apresentar para a conta de e-mail. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de utilizador do AAD**: Este nome é o atributo que Intune obtém do Azure Active Directory (Azure AD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:
  - **Nome Principal de utilizador**: Obtém o nome, tais como `user1` ou `user1@contoso.com`
  - **Nome de utilizador**: Obtém apenas o nome, tal como `user1`
  - **sAM nome da conta**: Requer o domínio, tal como `domain\user1`. nome da conta sAM só é utilizado com dispositivos Android.

    Introduza também:  
    - **Origem de nome de domínio do utilizador**: Escolher **AAD** (o Azure Active Directory) ou **personalizado**.

      Ao optar por obter os atributos do **AAD**, introduza:
      - **Atributo de nome de domínio de utilizador do AAD**: Optar por receber as **nome de domínio completo** ou o **nome NetBIOS** atributo do utilizador

      Ao optar por utilizar atributos **Personalizados**, introduza:
      - **Nome de domínio personalizado para utilizar**: Introduza um valor que o Intune utiliza para o nome de domínio, tal como `contoso.com` ou `contoso`

- **Atributo de endereço de e-mail do AAD**: Este nome é o atributo de correio eletrónico que Intune obtém do Azure AD. Intune gera dinamicamente o endereço de e-mail que é utilizado por este perfil. As opções são:
  - **Nome principal de utilizador**:  Utiliza o nome principal completo, como `user1@contoso.com` ou `user1`, como o endereço de e-mail.
  - **Endereço SMTP principal**: Utiliza o endereço SMTP principal, como `user1@contoso.com`, para iniciar sessão no Exchange.

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
  - **Contactos**: Escolher **ativar** para permitir que os utilizadores finais a sincronização de contactos para que os dispositivos deles.
  - **Calendário**: Escolher **ativar** para permitir que os utilizadores finais sincronizar o calendário para seus dispositivos.
  - **Tarefas**: Escolher **ativar** para permitir que os utilizadores finais sincronizar todas as tarefas nos seus dispositivos.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode criar perfis de e-mail para [Android Enterprise - perfil de trabalho](email-settings-android-enterprise.md), [iOS](email-settings-ios.md), [Windows 10 e posterior](email-settings-windows-10.md), e [Windows Phone 8.1](email-settings-windows-phone-8-1.md).
