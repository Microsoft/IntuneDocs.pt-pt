---
title: Configurações de e-mail Android Enterprise no Microsoft Intune - Azure Microsoft Docs
description: Crie perfis de e-mail de configuração do dispositivo que utilizem servidores de Intercâmbio e recuperem atributos do Diretório Ativo do Azure. Ative o SSL ou o SMIME, autentica os utilizadores com certificados ou nome de utilizador/palavra-passe, e sincroniza o e-mail e os horários dos dispositivos de perfil de trabalho android utilizando o Microsoft Intune.
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
ms.reviewer: maholdaa
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 978ddf279dc221a56fddaf99da4dbb2377a93c24
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511158"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Configurações do dispositivo Android Enterprise para configurar e-mail, autenticação e sincronização em Intune



Este artigo lista e descreve as diferentes definições de e-mail que pode controlar em dispositivos Android Enterprise. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para configurar um servidor de e-mail, utilize o SSL para encriptar mensagens de correio eletrónico e muito mais.

Como administrador intune, pode criar e atribuir definições de e-mail aos dispositivos Android Enterprise no perfil de trabalho.

Para saber mais sobre perfis de e-mail em Intune, consulte [configurar as definições de e-mail](email-settings-configure.md).

## <a name="before-you-begin"></a>Antes de começar

Crie um perfil de [configuração](email-settings-configure.md#create-a-device-profile) do dispositivo (escolha o perfil de trabalho) ou crie uma política de configuração de [aplicações](../apps/app-configuration-policies-use-android.md).

## <a name="android-enterprise"></a>Android Enterprise

- **Aplicação de e-mail**: selecione **Gmail** ou **Nine Work**
- **Servidor de e-mail**: o nome de anfitrião do seu servidor Exchange. Por exemplo, introduza `outlook.office365.com`.
- **Atributo de nome de utilizador do AAD**: este nome é o atributo que o Intune obtém do Azure Active Directory (Azure AD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:

  - **Nome Principal de Utilizador**: obtém o nome, como `user1` ou `user1@contoso.com`
  - **Nome de utilizador**: obtém apenas o nome como `user1`

- **Atributo de endereço de e-mail da AAD**: Este nome é o atributo de e-mail que Intune recebe da AD Azure. Intune gera dinamicamente o endereço de e-mail que é usado por este perfil. As opções são:
  - **Nome principal**do utilizador : Utiliza o nome principal completo, como `user1@contoso.com` ou `user1`, como o endereço de e-mail.
  - **Endereço Principal SMTP**: Utiliza o endereço SMTP primário, como `user1@contoso.com`, para iniciar sessão no Exchange.

- **Método de autenticação**: Selecione **o nome de utilizador e a palavra-passe** ou **certificados** como método de autenticação utilizado pelo perfil de e-mail.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a ligação ao Exchange.
- **SSL:** Escolha **ativar** a utilização da comunicação Secure Sockets Layer (SSL) ao enviar e-mails, receber e-mails e comunicar com o servidor De Troca.
- **Quantidade de e-mail para sincronizar**: Escolha a quantidade de tempo de e-mail que pretende sincronizar. Ou, selecione **Ilimitado** para sincronizar todos os e-mails disponíveis.
- Tipo de **conteúdo a sincronizar** (Apenas Nove Trabalhos): Escolha quais os dados que pretende sincronizar nos dispositivos. As opções são:
  - **Contactos**: Escolha **o Enable** para permitir que os utilizadores finais sincronizem os contactos com os seus dispositivos.
  - **Calendário**: Escolha **o Habilitar** para permitir que os utilizadores finais sincroniem o calendário dos seus dispositivos.
  - **Tarefas**: Escolha **o Enable** para permitir que os utilizadores finais sincronem quaisquer tarefas nos seus dispositivos.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode criar perfis de email para [android Samsung Knox](email-settings-android.md), [iOS/iPadOS,](email-settings-ios.md) [Windows 10 e posteriormente](email-settings-windows-10.md), e [dispositivos Windows Phone 8.1.](email-settings-windows-phone-8-1.md)
