---
title: Definições de e-mail para dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
description: Crie um perfil de e-mail de configuração de dispositivos que utiliza os servidores Exchange e obtém atributos do Azure Active Directory. Também pode ativar o SSL, autenticar utilizadores com certificados ou nome de utilizador/palavra-passe e sincronizar e-mails em dispositivos iOS com o Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2d27e90655e54051d73989202d2bc849a66208f5
ms.sourcegitcommit: 488be75cbee88455b33c68a3ec2acb864d461bf8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/22/2018
ms.locfileid: "41910807"
---
# <a name="email-profile-settings-for-ios-devices---intune"></a>Definições de perfil de e-mail para dispositivos iOS – Intune

Utilize as definições do perfil de e-mail para configurar os seus dispositivos iOS.

> [!IMPORTANT]
> Estamos a fazer algumas melhorias à funcionalidade S/MIME descrita neste artigo. Por esse motivo, a funcionalidade S/MIME será removida temporariamente do Intune. Quando esta funcionalidade for lançada, iremos remover esta nota.

## <a name="email-settings"></a>Definições de e-mail

- **Servidor de e-mail**: introduza o nome de anfitrião do seu servidor Exchange.
- **Nome da conta**: introduza o nome a apresentar da conta de e-mail. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de utilizador do AAD**: este nome é o atributo que o Intune obtém do Azure Active Directory (AAD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:
  - **Nome Principal de Utilizador**: obtém o nome, como `user1` ou `user1@contoso.com`
  - **Endereço SMTP primário**: obtém o nome no formato de endereço de e-mail, como `user1@contoso.com`
  - **Nome da Conta SAM**: precisa do domínio, como `domain\user1`.

    Introduza também:  
    - **Origem de nome de domínio do utilizador**: selecione **AAD** (Azure Active Directory) ou **Personalizado**.

      Ao optar por obter os atributos do **AAD**, introduza:
      - **Origem de nome de domínio do utilizador do AAD**: selecione esta opção para obter o atributo **Nome de domínio completo** ou **Nome NetBIOS** do utilizador

      Ao optar por utilizar atributos **Personalizados**, introduza:
      - **Nome de domínio personalizado para utilizar**: introduza um valor para o Intune utilizar como nome de domínio, como `contoso.com` ou `contoso`

- **Atributo de endereço de e-mail do AAD**: selecione como é gerado o endereço de e-mail do utilizador. Selecione **Nome principal de utilizador** (`user1@contoso.com` ou `user1`) para utilizar o nome principal completo como o endereço de e-mail ou o **Endereço SMTP primário** (`user1@contoso.com`) para utilizar o endereço SMTP primário para iniciar sessão no Exchange.
- **Método de autenticação**: selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como o método de autenticação utilizado pelo perfil de e-mail. A autenticação multifator do Azure não é suportada.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente que servirá para autenticar a ligação ao Exchange.
- **SSL**: **ative** para utilizar a comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o servidor Exchange.
- **S/MIME**: **Ative o S/MIME** para enviar e-mails com uma assinatura S/MIME. Quando estiver ativado, também pode encriptar e-mails para destinatários que podem receber e-mails encriptados e desencriptar e-mails recebidos de remetentes.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado PKCS criado anteriormente para autenticar a ligação ao Exchange e/ou encriptar trocas de e-mails.
- **Quantidade de e-mails a sincronizar**: selecione o número de dias de e-mails que pretende sincronizar. Em alternativa, selecione **Ilimitada** para sincronizar todos os e-mails disponíveis.
- **Permitir a movimentação de mensagens para outras contas de e-mail**: **Ativar** permite que os utilizadores movam mensagens de e-mail entre contas diferentes configuradas nos dispositivos.
- **Permitir o envio de e-mails a partir de aplicações de terceiros**: **Ativar** permite que o utilizador selecione este perfil como a conta predefinida para o envio de e-mails e permite que as aplicações de terceiros abram o e-mail na aplicação de e-mail nativa, por exemplo, para anexar ficheiros ao e-mail.
- **Sincronizar endereços de e-mail utilizados recentemente**: **Ativar** permite que os utilizadores sincronizem a lista de endereços de e-mail que foram recentemente utilizados no dispositivo com o servidor.

## <a name="next-steps"></a>Próximos passos
[Configurar as definições de e-mail no Intune](email-settings-configure.md)
