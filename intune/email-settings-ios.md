---
title: Definições de e-mail para dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
description: Crie um perfil de e-mail de configuração de dispositivos que utiliza os servidores Exchange e obtém atributos do Azure Active Directory. Também pode ativar o SSL, autenticar utilizadores com certificados ou nome de utilizador/palavra-passe e sincronizar e-mails em dispositivos iOS com o Microsoft Intune.
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
ms.openlocfilehash: 3a231adf4e1f5687bc88c8c9b15241d3f89e711d
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905344"
---
# <a name="email-profile-settings-for-ios-devices---intune"></a>Definições de perfil de e-mail para dispositivos iOS – Intune

Utilize as definições do perfil de e-mail para configurar os seus dispositivos iOS.

## <a name="email-settings"></a>Definições de e-mail

- **Servidor de e-mail**: introduza o nome de anfitrião do seu servidor Exchange.
- **Nome da conta**: introduza o nome a apresentar da conta de e-mail. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de utilizador do AAD**: este nome é o atributo que o Intune obtém do Azure Active Directory (AAD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:
  - **Nome Principal de Utilizador**: obtém o nome, como `user1` ou `user1@contoso.com`.
  - **Endereço SMTP primário**: obtém o nome no formato de endereço de e-mail, como `user1@contoso.com`.
  - **Nome da Conta SAM**: precisa do domínio, como `domain\user1`.

    Introduza também:  
    - **Origem de nome de domínio do utilizador**: selecione **AAD** (Azure Active Directory) ou **Personalizado**.

      Ao optar por obter os atributos do **AAD**, introduza:
      - **Origem de nome de domínio do utilizador do AAD**: selecione esta opção para obter o atributo **Nome de domínio completo** ou **Nome NetBIOS** do utilizador.

      Ao optar por utilizar atributos **Personalizados**, introduza:
      - **Nome de domínio personalizado para utilizar**: introduza um valor para o Intune utilizar como nome de domínio, como `contoso.com` ou `contoso`.

- **Atributo de endereço de e-mail do AAD**: selecione como é gerado o endereço de e-mail do utilizador. Selecione **Nome principal de utilizador** (`user1@contoso.com` ou `user1`) para utilizar o nome principal completo como o endereço de e-mail ou o **Endereço SMTP primário** (`user1@contoso.com`) para utilizar o endereço SMTP primário para iniciar sessão no Exchange.
- **Método de autenticação**: selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como o método de autenticação utilizado pelo perfil de e-mail. A autenticação multifator do Azure não é suportada.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente que servirá para autenticar a ligação ao Exchange.
- **SSL**: utilize a comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o servidor Exchange.
- **S/MIME**: envie e-mails com uma assinatura S/MIME.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado PKCS criado anteriormente para autenticar a ligação ao Exchange.
- **Quantidade de e-mails a sincronizar**: selecione o número de dias de e-mails que pretende sincronizar. Em alternativa, selecione **Ilimitada** para sincronizar todos os e-mails disponíveis.
- **Permitir que as mensagens sejam movidas para outras contas de e-mail**: permite que os utilizadores movam mensagens de e-mail entre contas diferentes configuradas nos dispositivos.
- **Permitir o envio de e-mail a partir de aplicações de terceiros**: permita que o utilizador selecione este perfil como a conta predefinida para o envio de e-mails e permita que as aplicações de terceiros abram o e-mail na aplicação de e-mail nativa, por exemplo, para anexar ficheiros ao e-mail.
- **Sincronizar endereços de e-mail recentemente utilizados**: permite que os utilizadores sincronizem a lista de endereços de e-mail que foram recentemente utilizados no dispositivo com o servidor.

## <a name="next-steps"></a>Próximos passos
[Configurar as definições de e-mail no Intune](email-settings-configure.md)
