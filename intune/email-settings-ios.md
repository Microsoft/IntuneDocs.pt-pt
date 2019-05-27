---
title: Definições de e-mail para dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
description: Ver uma lista de todas as definições de e-mail que pode configurar e adicionar dispositivos iOS no Microsoft Intune, incluindo a utilização de servidores do Exchange e ao obter os atributos do Azure Active Directory. Também pode ativar o SSL, autenticar utilizadores com certificados ou o nome de utilizador/palavra-passe e sincronizar o e-mail em dispositivos iOS através de perfis de configuração de dispositivo no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/11/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0faf9220b4859c41ef8c4393fe15f385eaac8cc3
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66042108"
---
# <a name="email-profile-settings-for-ios-devices-in-intune"></a>Definições de perfil de e-mail para dispositivos iOS no Intune

No Microsoft Intune, pode criar e configurar o e-mail para ligar a um servidor de e-mail, escolha a forma como autenticar utilizadores, utilizar S/MIME para encriptação e muito mais.

Este artigo apresenta e descreve todas as definições de e-mail disponíveis para dispositivos iOS. Pode criar um perfil de configuração do dispositivo para enviar por push ou implementar estas definições de e-mail nos seus dispositivos iOS.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](email-settings-configure.md#create-a-device-profile).

## <a name="email-settings"></a>Definições de e-mail

- **Servidor de e-mail**: Introduza o nome de anfitrião do seu Exchange server.
- **Nome da conta**: Introduza o nome a apresentar para a conta de e-mail. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de utilizador do AAD**: Este nome é o atributo que Intune obtém do Azure Active Directory (AAD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:
  - **Nome Principal de utilizador**: Obtém o nome, tais como `user1` ou `user1@contoso.com`
  - **Endereço SMTP principal**: Obtém o nome no formato de endereço de e-mail, tal como `user1@contoso.com`
  - **sAM nome da conta**: Requer o domínio, tal como `domain\user1`.

    Introduza também:  
    - **Origem de nome de domínio do utilizador**: Escolher **AAD** (o Azure Active Directory) ou **personalizado**.

      Ao optar por obter os atributos do **AAD**, introduza:
      - **Atributo de nome de domínio de utilizador do AAD**: Optar por receber as **nome de domínio completo** ou o **nome NetBIOS** atributo do utilizador

      Ao optar por utilizar atributos **Personalizados**, introduza:
      - **Nome de domínio personalizado para utilizar**: Introduza um valor que o Intune utiliza para o nome de domínio, tal como `contoso.com` ou `contoso`

- **Atributo de endereço de e-mail do AAD**: Escolha como é gerado o endereço de e-mail do utilizador. Selecione o **Nome principal de utilizador** (`user1@contoso.com` ou `user1`) para utilizar o nome principal completo como endereço de e-mail. Selecione **Endereço SMTP Principal** (`user1@contoso.com`) para utilizar o endereço SMTP principal para iniciar sessão no Exchange.
- **Método de autenticação**: Selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como método de autenticação utilizado pelo perfil de e-mail. A autenticação multifator do Azure não é suportada.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente que servirá para autenticar a ligação ao Exchange.
- **SSL**: **Ativar** utiliza a comunicação de Secure Sockets Layer (SSL) ao enviar e receber e-mails e ao comunicar com o Exchange server.
- **OAuth**: **Ativar** utiliza a comunicação de Open Authorization (OAuth) ao enviar e receber e-mails e ao comunicar com o Exchange. Se o seu servidor OAuth utilizar a autenticação de certificados, selecione **Certificado** como **Método de autenticação** e inclua o certificado juntamente com o perfil. Caso contrário, selecione **Nome de utilizador e palavra-passe** como **Método de autenticação**. Quando utilizar o OAuth, certifique-se de que:

  - Confirma que sua solução de e-mail suporta OAuth antes de direcionar este perfil para os seus utilizadores. O Office 365 Exchange Online suporta OAuth. O Exchange no Local e outras soluções de parceiro ou de terceiros poderão não suportar OAuth. É possível configurar o Exchange no Local para Autenticação Moderna (veja a mensagem de blogue [Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/) [Apresentamos a Autenticação Moderna Híbrida para o Exchange no Local]).

    Se o perfil de e-mail utilizar o OAuth e o serviço de e-mail não o suportar, a opção **Reintroduzir a palavra-passe** parecerá não funcionar. Por exemplo, não acontece nada quando o utilizador seleciona **Reintroduzir a palavra-passe** nas definições de dispositivos da Apple.

  - Quando o OAuth está ativado, os utilizadores finais têm uma experiência diferente de início de sessão no e-mail através de "Autenticação moderna" que suporta autenticação multifator (MFA). 

  - Algumas organizações desativam a funcionalidade que permite que os utilizadores finais utilizem o [acesso de gestão personalizada à aplicação](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access). Neste cenário, o início de sessão através de Autenticação Moderna poderá falhar até que um Administrador crie a aplicação empresarial "Contas iOS" e conceda acesso à aplicação no Azure AD aos utilizadores.

    A ação predefinida é a adição de uma aplicação através da funcionalidade do [Painel de Acesso da Aplicação](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) **Adicionar Aplicação** **sem a aprovação empresarial**. Para obter mais informações, veja [Atribuir utilizadores a Aplicações](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > Quando ativar o OAuth, ocorrerá o seguinte:  
  > 1. Será emitido um novo perfil para os dispositivos já visados.
  > 2. Será novamente pedido aos utilizadores finais que introduzam as respetivas credenciais.

- **S/MIME**: **Ativar S/MIME** para permitir aos utilizadores iniciar sessão e/ou encriptar o e-mail na aplicação de e-mail nativa do iOS. 

  Quando utilizar S/MIME com uma mensagem de e-mail, está a confirmar a autenticidade do remetente e a integridade e confidencialidade da mensagem.

  - **Assinatura de S/MIME ativada**: Escolher **ativar** para permitir que os utilizadores assinar digitalmente o e-mail de envio para a conta que introduziu. Assinatura irão ajudar os utilizadores que recebem mensagens de ter a certeza de que a mensagem veio do remetente específico e não a partir de alguém fingindo ser o remetente. **Desativar** não permite que os utilizadores assinar digitalmente a mensagem.
    - **Permitir que o utilizador altere a definição**: Escolher **ativar** para permitir que os utilizadores alterar o comportamento de assinatura S/MIME. **Desativar** impede os utilizadores de alterar a assinatura S/MIME definição configurada. Disponível no iOS 12 e mais recentes.

  - **Certificado de assinatura S/MIME**: Selecione um perfil de certificado PKCS ou SCEP existente que é utilizado para assinar mensagens de e-mail.
    - **Permitir que o utilizador altere a definição**: Escolher **ativar** para permitir que os utilizadores alterar o certificado de assinatura. **Desativar** impede os utilizadores de alterar o certificado de assinatura e força os utilizadores para utilizar o certificado que configurou. Disponível no iOS 12 e mais recentes.

  - **Encriptar por predefinição**: **Ativar** encripta todas as mensagens como comportamento predefinido. **Desativar** não criptografar todas as mensagens, como o comportamento padrão.
    - **Permitir que o utilizador altere a definição**: Escolher **ativar** para permitir aos utilizadores alterar o comportamento de encriptação predefinido. **Desativar** impede os utilizadores de alterar o comportamento padrão de encriptação e força os utilizadores utilizem definições que configurou. Disponível no iOS 12 e mais recentes.

  - **Forçar a encriptação por mensagem**: Encriptação por mensagem permite aos utilizadores escolher os e-mails sejam encriptados antes de serem enviados. Escolher **ativar** para mostrar a opção de encriptação por mensagem ao criar um novo e-mail. Os utilizadores, em seguida, podem optar por participar no ou optar por criptografia por mensagem. **Desativar** impede que a opção de encriptação por mensagem de apresentação.

    Se o **Encrypt, por predefinição** está habilitada, ativar a encriptação por mensagem permite que os utilizadores a opção de desativar a encriptação por mensagem. Se o **Encrypt, por predefinição** definição estiver desativada, ativar a encriptação por mensagem permite aos utilizadores escolher encriptação por mensagem.

  - **Certificado de encriptação S/MIME**: Selecione um perfil de certificado PKCS ou SCEP existente que é utilizado para encriptar mensagens de e-mail.
    - **Permitir que o utilizador altere a definição**: Escolher **ativar** para permitir que os utilizadores alterar o certificado de encriptação. **Desativar** impede os utilizadores de alterar o certificado de encriptação e força os utilizadores para utilizar o certificado que configurou. Disponível no iOS 12 e mais recentes.
- **Quantidade de e-mails a sincronizar**: Escolha o número de dias de e-mail que pretende sincronizar. Em alternativa, selecione **Ilimitada** para sincronizar todos os e-mails disponíveis.
- **Permitir que as mensagens sejam movidas para outras contas de e-mail**: **Ativar** permite que os utilizadores movam mensagens de e-mail entre contas diferentes utilizadores configurados nos seus dispositivos.
- **Permitir que o e-mail seja enviado a partir de aplicações de terceiros**: **Ativar** permite aos utilizadores Selecione este perfil como conta predefinida para o envio de e-mail. que as aplicações de terceiros abram o e-mail na aplicação de e-mail nativa, por exemplo, para anexar ficheiros ao e-mail.
- **Sincronizar endereços de e-mail utilizados recentemente**: **Ativar** permite que os usuários sincronizar a lista de endereços de e-mail que foram recentemente utilizados no dispositivo com o servidor.

## <a name="next-steps"></a>Passos Seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).

Configurar as definições de e-mail num [Android](email-settings-android.md), [com o Windows 10](email-settings-windows-10.md), e [Windows Phone 8.1](email-settings-windows-phone-8-1.md) dispositivos.
