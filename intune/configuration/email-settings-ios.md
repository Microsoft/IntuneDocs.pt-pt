---
title: Definir configurações de email para dispositivos iOS no Microsoft Intune-Azure | Microsoft Docs
description: Veja uma lista de todas as configurações de email que você pode configurar e adicionar aos dispositivos iOS no Microsoft Intune, incluindo o uso de servidores Exchange e a obtenção de atributos de Azure Active Directory. Você também pode habilitar o SSL, autenticar usuários com certificados ou nome de usuário/senha e sincronizar emails em dispositivos iOS usando perfis de configuração de dispositivo no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4cbf9c29a1e694726b1b42f7072eea859f812751
ms.sourcegitcommit: 8c25aeefb7cbc6444a8596af22fccd1c5426877a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72593802"
---
# <a name="add-e-mail-settings-for-ios-devices-in-microsoft-intune"></a>Adicionar configurações de email para dispositivos iOS no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

No Microsoft Intune, você pode criar e configurar o email para se conectar a um servidor de email, escolher como os usuários se autenticam, usar S/MIME para criptografia e muito mais.

Este artigo lista e descreve todas as configurações de email disponíveis para dispositivos que executam o iOS. Você pode criar um perfil de configuração de dispositivo para enviar por Push ou implantar essas configurações de email em seus dispositivos iOS.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração de dispositivo](../email-settings-configure.md).

> [!NOTE]
> Essas configurações estão disponíveis para todos os tipos de registro. Para obter mais informações sobre os tipos de registro, consulte [registro do IOS](../ios-enroll.md).

## <a name="email-settings"></a>Definições de e-mail

- **Servidor de e-mail**: introduza o nome de anfitrião do seu servidor Exchange.
- **Nome da conta**: introduza o nome a apresentar da conta de e-mail. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de utilizador do AAD**: este nome é o atributo que o Intune obtém do Azure Active Directory (AAD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:
  - **Nome Principal de Utilizador**: obtém o nome, como `user1` ou `user1@contoso.com`.
  - **Endereço SMTP primário**: obtém o nome no formato de endereço de e-mail, como `user1@contoso.com`
  - **Nome da Conta SAM**: precisa do domínio, como `domain\user1`.

    Introduza também:  
    - **Origem de nome de domínio do utilizador**: selecione **AAD** (Azure Active Directory) ou **Personalizado**.

      Ao optar por obter os atributos do **AAD**, introduza:
      - **Origem de nome de domínio do utilizador do AAD**: selecione esta opção para obter o atributo **Nome de domínio completo** ou **Nome NetBIOS** do utilizador

      Ao optar por utilizar atributos **Personalizados**, introduza:
      - **Nome de domínio personalizado para utilizar**: introduza um valor para o Intune utilizar como nome de domínio, como `contoso.com` ou `contoso`

- **Atributo de endereço de e-mail do AAD**: selecione como é gerado o endereço de e-mail do utilizador. Selecione o **Nome principal de utilizador** (`user1@contoso.com` ou `user1`) para utilizar o nome principal completo como endereço de e-mail. Selecione **Endereço SMTP Principal** (`user1@contoso.com`) para utilizar o endereço SMTP principal para iniciar sessão no Exchange.
- **Método de autenticação**: selecione **nome de usuário e senha**, **certificados**ou **credencial derivada** como o método de autenticação usado pelo perfil de email. A autenticação multifator do Azure não é suportada.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente que servirá para autenticar a ligação ao Exchange.
- **SSL**: **Ativar** resulta na utilização da comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o servidor Exchange.
- **OAuth**: **Ativar** resulta na utilização da comunicação Open Authorization (OAuth) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange. Se o seu servidor OAuth utilizar a autenticação de certificados, selecione **Certificado** como **Método de autenticação** e inclua o certificado juntamente com o perfil. Caso contrário, selecione **Nome de utilizador e palavra-passe** como **Método de autenticação**. Quando utilizar o OAuth, certifique-se de que:

  - Confirma que sua solução de e-mail suporta OAuth antes de direcionar este perfil para os seus utilizadores. O Office 365 Exchange Online suporta OAuth. O Exchange no Local e outras soluções de parceiro ou de terceiros poderão não suportar OAuth. É possível configurar o Exchange no Local para Autenticação Moderna (veja a mensagem de blogue [Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/) [Apresentamos a Autenticação Moderna Híbrida para o Exchange no Local]).

    Se o perfil de e-mail utilizar o OAuth e o serviço de e-mail não o suportar, a opção **Reintroduzir a palavra-passe** parecerá não funcionar. Por exemplo, não acontece nada quando o utilizador seleciona **Reintroduzir a palavra-passe** nas definições de dispositivos da Apple.

  - Quando o OAuth está ativado, os utilizadores finais têm uma experiência diferente de início de sessão no e-mail através de "Autenticação moderna" que suporta autenticação multifator (MFA). 

  - Algumas organizações desativam a funcionalidade que permite que os utilizadores finais utilizem o [acesso de gestão personalizada à aplicação](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access). Neste cenário, o início de sessão através de Autenticação Moderna poderá falhar até que um Administrador crie a aplicação empresarial "Contas iOS" e conceda acesso à aplicação no Azure AD aos utilizadores.

    A ação predefinida é a adição de uma aplicação através da funcionalidade do [Painel de Acesso da Aplicação](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) **Adicionar Aplicação** **sem a aprovação empresarial**. Para obter mais informações, veja [Atribuir utilizadores a Aplicações](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > Quando ativar o OAuth, ocorrerá o seguinte:  
  > 1. Será emitido um novo perfil para os dispositivos já visados.
  > 2. Será novamente pedido aos utilizadores finais que introduzam as respetivas credenciais.

- **S/MIME**: **habilite s/MIME** para permitir que os usuários assinem e/ou criptografem emails no aplicativo de email nativo do Ios. 

  Ao usar S/MIME com uma mensagem de email, você confirma a autenticidade do remetente e a integridade e a confidencialidade da mensagem.

  - **Assinatura S/MIME habilitada**: escolha **habilitar** para permitir que os usuários assinem digitalmente o email de saída para a conta que você inseriu. A assinatura ajuda os usuários que recebem mensagens a ter certeza de que a mensagem provém do remetente específico, e não de alguém fingindo ser o remetente. **Desabilitar** não permite que os usuários assinem a mensagem digitalmente.
    - **Permitir que o usuário altere a configuração**: escolha **habilitar** para permitir que os usuários alterem o comportamento de assinatura S/MIME. **Desabilitar** impede que os usuários alterem a configuração de assinatura S/MIME que você configurou. Disponível no iOS 12 e mais recente.

  - **Certificado de assinatura S/MIME**: selecione um perfil de certificado PKCS ou SCEP existente que é usado para assinar mensagens de email.
    - **Permitir que o usuário altere a configuração**: escolha **habilitar** para permitir que os usuários alterem o certificado de autenticação. **Desabilitar** impede que os usuários alterem o certificado de autenticação e força os usuários a usar o certificado configurado. Disponível no iOS 12 e mais recente.

  - **Criptografar por padrão**: **habilitar** criptografa todas as mensagens como o comportamento padrão. **Desabilitar** não criptografa todas as mensagens como o comportamento padrão.
    - **Permitir que o usuário altere a configuração**: escolha **habilitar** para permitir que os usuários alterem o comportamento de criptografia padrão. **Desabilitar** impede que os usuários alterem o comportamento padrão de criptografia e obriga os usuários a usar a configuração que você configurou. Disponível no iOS 12 e mais recente.

  - **Forçar a criptografia por mensagem**: a criptografia por mensagem permite que os usuários escolham quais emails são criptografados antes de serem enviados. Escolha **habilitar** para mostrar a opção de criptografia por mensagem ao criar um novo email. Os usuários podem optar por aceitar ou recusar a criptografia por mensagem. **Desabilitar** impede que a opção de criptografia por mensagem seja exibida.

    Se a configuração **criptografar por padrão** estiver habilitada, habilitar a criptografia por mensagem permitirá que os usuários recusem a criptografia por mensagem. Se a configuração **criptografar por padrão** estiver desabilitada, habilitar a criptografia por mensagem permitirá que os usuários aceitem a criptografia por mensagem.

  - **Certificado de criptografia S/MIME**: selecione um perfil de certificado PKCS ou SCEP existente que é usado para criptografar mensagens de email.
    - **Permitir que o usuário altere a configuração**: escolha **habilitar** para permitir que os usuários alterem o certificado de criptografia. **Desabilitar** impede que os usuários alterem o certificado de criptografia e força os usuários a usar o certificado configurado. Disponível no iOS 12 e mais recente.
- **Quantidade de e-mails a sincronizar**: selecione o número de dias de e-mails que pretende sincronizar. Em alternativa, selecione **Ilimitada** para sincronizar todos os e-mails disponíveis.
- **Permitir a movimentação de mensagens para outras contas de e-mail**: **Ativar** permite que os utilizadores movam mensagens de e-mail entre contas diferentes que os utilizadores configuraram nos respetivos dispositivos.
- **Permitir o envio de e-mails a partir de aplicações de terceiros**: **Ativar** permite que os utilizadores selecionem este perfil como a conta predefinida para o envio de e-mails e que as aplicações de terceiros abram o e-mail na aplicação de e-mail nativa, por exemplo, para anexar ficheiros ao e-mail.
- **Sincronizar endereços de e-mail utilizados recentemente**: **Ativar** permite que os utilizadores sincronizem a lista de endereços de e-mail que foram recentemente utilizados no dispositivo com o servidor.

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](../device-profile-assign.md) e [monitorize o estado](../device-profile-monitor.md).

Defina configurações de email em dispositivos [Android](../email-settings-android.md), [Android Enterprise](../email-settings-android-enterprise.md), [Windows 10](email-settings-windows-10.md)e [Windows Phone 8,1](email-settings-windows-phone-8-1.md) .
