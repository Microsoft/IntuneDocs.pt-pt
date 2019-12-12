---
title: Definir configurações de email para dispositivos iOS no Microsoft Intune-Azure | Microsoft Docs
description: Veja uma lista de todas as configurações de email que você pode configurar e adicionar aos dispositivos iOS no Microsoft Intune, incluindo o uso de servidores Exchange e a obtenção de atributos de Azure Active Directory. Você também pode habilitar o SSL, autenticar usuários com certificados ou nome de usuário/senha e sincronizar emails em dispositivos iOS usando perfis de configuração de dispositivo no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 73de0ac94ff02e43fe73ca6357f6008ba71e3b93
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74390825"
---
# <a name="add-e-mail-settings-for-ios-devices-in-microsoft-intune"></a>Adicionar configurações de email para dispositivos iOS no Microsoft Intune

No Microsoft Intune, você pode criar e configurar o email para se conectar a um servidor de email, escolher como os usuários se autenticam, usar S/MIME para criptografia e muito mais.

Este artigo lista e descreve todas as configurações de email disponíveis para dispositivos que executam o iOS. Você pode criar um perfil de configuração de dispositivo para enviar por Push ou implantar essas configurações de email em seus dispositivos iOS.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](../email-settings-configure.md).

> [!NOTE]
> Essas configurações estão disponíveis para todos os tipos de registro. Para obter mais informações sobre os tipos de registro, consulte [registro do IOS](../ios-enroll.md).

## <a name="exchange-activesync-account-settings"></a>Configurações de conta do Exchange ActiveSync

- **Servidor de e-mail**: introduza o nome de anfitrião do seu servidor Exchange.
- **Nome da conta**: introduza o nome a apresentar da conta de e-mail. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de utilizador do AAD**: este nome é o atributo que o Intune obtém do Azure Active Directory (AAD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:
  - **Nome Principal de Utilizador**: obtém o nome, como `user1` ou `user1@contoso.com`.
  - **Endereço SMTP primário**: obtém o nome no formato de endereço de e-mail, como `user1@contoso.com`
  - **Nome da Conta SAM**: precisa do domínio, como `domain\user1`. Introduza também:  
    - **Origem de nome de domínio do utilizador**: selecione **AAD** (Azure Active Directory) ou **Personalizado**.
      - **AAD**: obter os atributos do Azure AD. Introduza também:
        - **Atributo de nome de domínio de usuário do AAD**: escolha para obter o **nome de domínio completo** (`contoso.com`) ou o atributo de **nome NetBIOS** (`contoso`) do usuário.

      - **Personalizado**: Obtenha os atributos de um nome de domínio personalizado. Introduza também:
        - **Nome de domínio personalizado a ser usado**: Insira um valor que o Intune usa para o nome de domínio, como `contoso.com` ou `contoso`.

- **Atributo de endereço de e-mail do AAD**: selecione como é gerado o endereço de e-mail do utilizador. As opções são:
  - **Nome principal do usuário**: Use o nome da entidade de segurança completa como o endereço de email, como `user1@contoso.com` ou `user1`.
  - **Endereço SMTP primário**: Use o endereço SMTP primário para entrar no Exchange, como `user1@contoso.com`.
- **Método de autenticação**: escolha como os usuários são autenticados no servidor de email. As opções são:
  - **Certificado**: selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a conexão do Exchange. Essa opção fornece a experiência mais segura e direta para seus usuários.
  - **Nome de usuário e senha**: os usuários são solicitados a inserir seu nome de usuários e senha.
  - **Credencial derivada**: Use um certificado derivado do cartão inteligente de um usuário. Para obter mais informações, consulte [usar credenciais derivadas no Microsoft Intune](../protect/derived-credentials.md).

  >[!NOTE]
  > A autenticação multifator do Azure não é suportada.
  
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

## <a name="exchange-activesync-profile-configuration"></a>Configuração de perfil do Exchange ActiveSync

> [!IMPORTANT]
> A definição dessas configurações implanta um novo perfil no dispositivo, mesmo quando um perfil de email existente é atualizado para incluir essas configurações. Os usuários são solicitados a inserir sua senha de conta do Exchange ActiveSync. Essas configurações são afetadas quando a senha é inserida.

- **Trocar dados a serem sincronizados**: ao usar o Exchange ActiveSync, escolha os serviços do Exchange que são sincronizados no dispositivo: calendário, contatos, lembretes, anotações e email. As opções são:
  - **Todos os dados** (padrão): a sincronização está habilitada para todos os serviços.
  - **Somente email**: a sincronização está habilitada somente para email. A sincronização está desabilitada para os outros serviços.
  - **Somente calendário**: a sincronização está habilitada somente para calendário. A sincronização está desabilitada para os outros serviços.
  - **Somente calendário e contatos**: a sincronização está habilitada somente para calendário e contatos. A sincronização está desabilitada para os outros serviços.
  - **Somente contatos**: a sincronização está habilitada somente para contatos. A sincronização está desabilitada para os outros serviços.

  Esta funcionalidade aplica-se a:  
  - iOS 13,0 e mais recente
  - iPadOS 13,0 e mais recente

- **Permitir que os usuários alterem as configurações de sincronização**: escolha se os usuários podem alterar as configurações do Exchange ActiveSync para os serviços do Exchange no dispositivo: calendário, contatos, lembretes, anotações e email. As opções são:

  - **Sim** (padrão): os usuários podem alterar o comportamento de sincronização de todos os serviços. Escolher **Sim** permite alterações em *todos os* serviços.
  - **Não**: os usuários não podem alterar as configurações de sincronização de todos os serviços. Escolher **nenhum** bloco muda para *todos os* serviços.

  > [!TIP]
  > Se você tiver configurado a configuração **dados do Exchange para sincronização** para sincronizar apenas alguns serviços, recomendamos selecionar **não** para essa configuração. Escolher **não** impede que os usuários alterem o serviço do Exchange sincronizado.

  Esta funcionalidade aplica-se a:  
  - iOS 13,0 e mais recente
  - iPadOS 13,0 e mais recente

## <a name="exchange-activesync-email-settings"></a>Configurações de email do Exchange ActiveSync

- **S/MIME**: s/MIME usa certificados de email que fornecem segurança extra para suas comunicações de email assinando, criptografando e descriptografando. Ao usar S/MIME com uma mensagem de email, você confirma a autenticidade do remetente e a integridade e a confidencialidade da mensagem.

  As opções são:

  - **Desabilitar S/MIME** (padrão): não usa um certificado de email S/MIME para assinar, criptografar ou descriptografar emails.
  - **Habilitar S/MIME**: permite que os usuários assinem e/ou criptografem emails no aplicativo de email nativo do Ios. Introduza também:

    - **Assinatura S/MIME habilitada**: **desabilitar** (padrão) não permite que os usuários assinem a mensagem digitalmente. **Habilitar** permite que os usuários assinem digitalmente o email de saída para a conta que você inseriu. A assinatura ajuda os usuários que recebem mensagens a ter certeza de que a mensagem provém do remetente específico, e não de alguém fingindo ser o remetente.
      - **Permitir que o usuário altere a configuração**: **habilitar** permite que os usuários alterem as opções de assinatura. **Desabilitar** (padrão) impede que os usuários alterem a assinatura e obriga os usuários a usar a assinatura configurada.
      - **Tipo de certificado de autenticação**: suas opções:
        - **Não configurado**: o Intune não atualiza ou altera essa configuração.
        - **Nenhum**: como administrador, você não força um certificado específico. Selecione essa opção para que os usuários possam escolher seu próprio certificado.
        - **Credencial derivada**: Use um certificado derivado do cartão inteligente de um usuário. Para obter mais informações, consulte [usar credenciais derivadas no Microsoft Intune](../protect/derived-credentials.md).
        - **Certificados**: selecione um perfil de certificado PKCS ou SCEP existente que é usado para assinar mensagens de email.
      - **Permitir que o usuário altere a configuração**: **habilitar** permite que os usuários alterem o certificado de autenticação. **Desabilitar** (padrão) impede que os usuários alterem o certificado de autenticação e obriga os usuários a usar o certificado configurado.

        Esta funcionalidade aplica-se a:  
        - iOS 12 e mais recente
        - iPadOS 12 e mais recente

    - **Criptografar por padrão**: **habilitar** criptografa todas as mensagens como o comportamento padrão. **Desabilitar** (padrão) não criptografa todas as mensagens como o comportamento padrão.
      - **Permitir que o usuário altere a configuração**: **habilitar** permite que os usuários alterem o comportamento de criptografia padrão. **Desabilitar** impede que os usuários alterem o comportamento padrão de criptografia e obriga os usuários a usar a criptografia configurada.

        Esta funcionalidade aplica-se a:  
        - iOS 12 e mais recente
        - iPadOS 12 e mais recente

    - **Forçar a criptografia por mensagem**: a criptografia por mensagem permite que os usuários escolham quais emails são criptografados antes de serem enviados.

      **Habilitar** mostra a opção de criptografia por mensagem ao criar um novo email. Os usuários podem optar por aceitar ou recusar a criptografia por mensagem. Se a configuração **criptografar por padrão** também estiver habilitada, habilitar a criptografia por mensagem permitirá que os usuários recusem a criptografia por mensagem.

      **Desabilitar** (padrão) impede que a opção de criptografia por mensagem seja exibida. Se a configuração **criptografar por padrão** também estiver desabilitada, habilitar a criptografia por mensagem permitirá que os usuários aceitem a criptografia por mensagem.

      - **Tipo de certificado de criptografia**: suas opções:
        - **Não configurado**: o Intune não atualiza ou altera essa configuração.
        - **Nenhum**: como administrador, você não força um certificado específico. Selecione essa opção para que os usuários possam escolher seu próprio certificado.
        - **Credencial derivada**: Use um certificado derivado do cartão inteligente de um usuário. Para obter mais informações, consulte [usar credenciais derivadas no Microsoft Intune](../protect/derived-credentials.md).
        - **Certificados**: selecione um perfil de certificado PKCS ou SCEP existente que é usado para assinar mensagens de email.
      - **Permitir que o usuário altere a configuração**: **habilitar** permitir que os usuários alterem o certificado de criptografia. **Desabilitar** (padrão) impede que os usuários alterem o certificado de criptografia e obriga os usuários a usar o certificado configurado.

        Esta funcionalidade aplica-se a:  
        - iOS 12 e mais recente
        - iPadOS 12 e mais recente

- **Quantidade de e-mails a sincronizar**: selecione o número de dias de e-mails que pretende sincronizar. Em alternativa, selecione **Ilimitada** para sincronizar todos os e-mails disponíveis.
- **Permitir que as mensagens sejam movidas para outras contas de email**: **habilitar** (padrão) permite que os usuários movam mensagens de email entre contas diferentes dos usuários configurados em seus dispositivos.
- **Permitir que o email seja enviado de aplicativos de**terceiros: **habilitar** (padrão) permite que os usuários selecionem esse perfil como a conta padrão para enviar email. que as aplicações de terceiros abram o e-mail na aplicação de e-mail nativa, por exemplo, para anexar ficheiros ao e-mail.
- **Sincronizar endereços de email usados recentemente**: **habilitar** (padrão) permite que os usuários sincronizem a lista de endereços de email que foram usados recentemente no dispositivo com o servidor.

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](../device-profile-assign.md) e [monitorize o estado](../device-profile-monitor.md).

Defina configurações de email em dispositivos [Android](../email-settings-android.md), [Android Enterprise](../email-settings-android-enterprise.md), [Windows 10](email-settings-windows-10.md)e [Windows Phone 8,1](email-settings-windows-phone-8-1.md) .
