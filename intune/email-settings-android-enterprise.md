---
title: As definições de e-mail do Android Enterprise no Microsoft Intune – Azure | Documentos da Microsoft
description: Criar perfis de e-mail de configuração que utilizam servidores do Exchange de dispositivos e obter atributos do Azure Active Directory. Ativar SSL ou SMIME, autenticar utilizadores com certificados ou o nome de utilizador/palavra-passe e sincronizar o e-mail e agendas em dispositivos de perfil de trabalho Android através do Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/10/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: ff2732bb68d7e3f2199f392275d476374ee0c10c
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831693"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Definições de dispositivos empresariais Android para configurar o e-mail, autenticação e a sincronização no Intune

Este artigo apresenta uma lista e descreve as definições de correio eletrónico diferente que pode controlar em dispositivos Android Enterprise. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para configurar um servidor de e-mail, utilize o SSL para encriptar mensagens de correio eletrónico e muito mais.

Enquanto administrador do Intune, pode criar e atribuir definições de e-mail para dispositivos Android Enterprise no perfil de trabalho.

Para obter mais informações sobre perfis de e-mail no Intune, consulte [configurar definições de e-mail](email-settings-configure.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](email-settings-configure.md#create-a-device-profile)e selecione o perfil de trabalho.

## <a name="android-enterprise"></a>Android Enterprise

- **Aplicação de e-mail**: Selecione **Gmail** ou **Nine Work**
- **Servidor de e-mail**: O nome de anfitrião do seu Exchange server. Por exemplo, introduza `outlook.office365.com`.
- **Atributo de nome de utilizador do AAD**: Este nome é o atributo que Intune obtém do Azure Active Directory (Azure AD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:

  - **Nome Principal de utilizador**: Obtém o nome, tais como `user1` ou `user1@contoso.com`
  - **Nome de utilizador**: Obtém apenas o nome, tal como `user1`

- **Atributo de endereço de e-mail do AAD**: Este nome é o atributo de correio eletrónico que Intune obtém do Azure AD. Intune gera dinamicamente o endereço de e-mail que é utilizado por este perfil. As opções são:
  - **Nome principal de utilizador**:  Utiliza o nome principal completo, como `user1@contoso.com` ou `user1`, como o endereço de e-mail.
  - **Endereço SMTP principal**: Utiliza o endereço SMTP principal, como `user1@contoso.com`, para iniciar sessão no Exchange.

- **Método de autenticação**: Selecione **nome de utilizador e palavra-passe** ou **certificados** como método de autenticação utilizado pelo perfil de e-mail.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a ligação ao Exchange.
- **SSL**: Escolher **ativar** para utilizar a comunicação de Secure Sockets Layer (SSL) ao enviar e receber e-mails e ao comunicar com o Exchange server.
- **Quantidade de e-mails a sincronizar**: Escolha o período de tempo de e-mail que pretende sincronizar. Em alternativa, selecione **ilimitado** para sincronizar todos os e-mails disponíveis.
- **Tipo de conteúdo a sincronizar** (Nine Work apenas): Escolha quais os dados que pretende sincronizar nos dispositivos. As opções são:
  - **Contactos**: Escolher **ativar** para permitir que os utilizadores finais a sincronização de contactos para que os dispositivos deles.
  - **Calendário**: Escolher **ativar** para permitir que os utilizadores finais sincronizar o calendário para seus dispositivos.
  - **Tarefas**: Escolher **ativar** para permitir que os utilizadores finais sincronizar todas as tarefas nos seus dispositivos.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode criar perfis de e-mail para [Android Samsung Knox](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 e posterior](email-settings-windows-10.md), e [Windows Phone 8.1](email-settings-windows-phone-8-1.md) dispositivos.