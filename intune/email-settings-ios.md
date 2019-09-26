---
title: Definir configurações de email para dispositivos iOS no Microsoft Intune-Azure | Microsoft Docs
description: Veja uma lista de todas as configurações de email que você pode configurar e adicionar aos dispositivos iOS no Microsoft Intune, incluindo o uso de servidores Exchange e a obtenção de atributos de Azure Active Directory. Você também pode habilitar o SSL, autenticar usuários com certificados ou nome de usuário/senha e sincronizar emails em dispositivos iOS usando perfis de configuração de dispositivo no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8fa0a7edd1782cd3eae725e6adf0af867e0f3727
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71301928"
---
# <a name="add-e-mail-settings-for-ios-devices-in-microsoft-intune"></a>Adicionar configurações de email para dispositivos iOS no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

No Microsoft Intune, você pode criar e configurar o email para se conectar a um servidor de email, escolher como os usuários se autenticam, usar S/MIME para criptografia e muito mais.

Este artigo lista e descreve todas as configurações de email disponíveis para dispositivos que executam o iOS. Você pode criar um perfil de configuração de dispositivo para enviar por Push ou implantar essas configurações de email em seus dispositivos iOS.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](email-settings-configure.md).

> [!NOTE]
> Essas configurações estão disponíveis para todos os tipos de registro. Para obter mais informações sobre os tipos de registro, consulte [registro do IOS](ios-enroll.md).

## <a name="email-settings"></a>Definições de e-mail

- **Servidor de email**: Insira o nome do host do seu servidor Exchange.
- **Nome da conta**: Insira o nome de exibição para a conta de email. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de usuário do AAD**: Esse nome é o atributo que o Intune obtém de Azure Active Directory (AAD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:
  - **Nome principal do usuário**: Obtém o nome, `user1` como ou`user1@contoso.com`
  - **Endereço SMTP primário**: Obtém o nome no formato de endereço de email, como`user1@contoso.com`
  - **nome da conta sAM**: Requer o domínio, `domain\user1`como.

    Introduza também:  
    - **Origem do nome de domínio do usuário**: Escolha **AAD** (Azure Active Directory) ou **personalizado**.

      Ao optar por obter os atributos do **AAD**, introduza:
      - **Atributo de nome de domínio do usuário do AAD**: Opte por obter o **nome de domínio completo** ou o atributo de **nome NetBIOS** do usuário

      Ao optar por utilizar atributos **Personalizados**, introduza:
      - **Nome de domínio personalizado a ser usado**: Insira um valor que o Intune usa para o nome de domínio, `contoso.com` como ou`contoso`

- **Atributo de endereço de email do AAD**: Escolha como o endereço de email do usuário é gerado. Selecione o **Nome principal de utilizador** (`user1@contoso.com` ou `user1`) para utilizar o nome principal completo como endereço de e-mail. Selecione **Endereço SMTP Principal** (`user1@contoso.com`) para utilizar o endereço SMTP principal para iniciar sessão no Exchange.
- **Método de autenticação**: Selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como método de autenticação utilizado pelo perfil de e-mail. A autenticação multifator do Azure não é suportada.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente que servirá para autenticar a ligação ao Exchange.
- **SSL**: **Habilitar** usa comunicação de protocolo SSL (SSL) ao enviar emails, receber emails e comunicar-se com o Exchange Server.
- **OAuth**: **Habilitar** usa a comunicação do Open Authorization (OAuth) ao enviar emails, receber emails e comunicar-se com o Exchange. Se o seu servidor OAuth utilizar a autenticação de certificados, selecione **Certificado** como **Método de autenticação** e inclua o certificado juntamente com o perfil. Caso contrário, selecione **Nome de utilizador e palavra-passe** como **Método de autenticação**. Quando utilizar o OAuth, certifique-se de que:

  - Confirma que sua solução de e-mail suporta OAuth antes de direcionar este perfil para os seus utilizadores. O Office 365 Exchange Online suporta OAuth. O Exchange no Local e outras soluções de parceiro ou de terceiros poderão não suportar OAuth. É possível configurar o Exchange no Local para Autenticação Moderna (veja a mensagem de blogue [Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/) [Apresentamos a Autenticação Moderna Híbrida para o Exchange no Local]).

    Se o perfil de e-mail utilizar o OAuth e o serviço de e-mail não o suportar, a opção **Reintroduzir a palavra-passe** parecerá não funcionar. Por exemplo, não acontece nada quando o utilizador seleciona **Reintroduzir a palavra-passe** nas definições de dispositivos da Apple.

  - Quando o OAuth está ativado, os utilizadores finais têm uma experiência diferente de início de sessão no e-mail através de "Autenticação moderna" que suporta autenticação multifator (MFA). 

  - Algumas organizações desativam a funcionalidade que permite que os utilizadores finais utilizem o [acesso de gestão personalizada à aplicação](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access). Neste cenário, o início de sessão através de Autenticação Moderna poderá falhar até que um Administrador crie a aplicação empresarial "Contas iOS" e conceda acesso à aplicação no Azure AD aos utilizadores.

    A ação predefinida é a adição de uma aplicação através da funcionalidade do [Painel de Acesso da Aplicação](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) **Adicionar Aplicação** **sem a aprovação empresarial**. Para obter mais informações, veja [Atribuir utilizadores a Aplicações](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > Quando ativar o OAuth, ocorrerá o seguinte:  
  > 1. Será emitido um novo perfil para os dispositivos já visados.
  > 2. Será novamente pedido aos utilizadores finais que introduzam as respetivas credenciais.

- **S/MIME**: **Habilite o S/MIME** para permitir que os usuários assinem e/ou criptografem emails no aplicativo IOS Native mail. 

  Ao usar S/MIME com uma mensagem de email, você confirma a autenticidade do remetente e a integridade e a confidencialidade da mensagem.

  - **Assinatura S/MIME habilitada**: Escolha **habilitar** para permitir que os usuários assinem digitalmente o email de saída para a conta que você inseriu. A assinatura ajuda os usuários que recebem mensagens a ter certeza de que a mensagem provém do remetente específico, e não de alguém fingindo ser o remetente. **Desabilitar** não permite que os usuários assinem a mensagem digitalmente.
    - **Permitir que o usuário altere a configuração**: Escolha **habilitar** para permitir que os usuários alterem o comportamento de assinatura S/MIME. **Desabilitar** impede que os usuários alterem a configuração de assinatura S/MIME que você configurou. Disponível no iOS 12 e mais recente.

  - **Certificado de assinatura S/MIME**: Selecione um perfil de certificado PKCS ou SCEP existente que é usado para assinar mensagens de email.
    - **Permitir que o usuário altere a configuração**: Escolha **habilitar** para permitir que os usuários alterem o certificado de autenticação. **Desabilitar** impede que os usuários alterem o certificado de autenticação e força os usuários a usar o certificado configurado. Disponível no iOS 12 e mais recente.

  - **Criptografar por padrão**: **Habilitar** criptografa todas as mensagens como o comportamento padrão. **Desabilitar** não criptografa todas as mensagens como o comportamento padrão.
    - **Permitir que o usuário altere a configuração**: Escolha **habilitar** para permitir que os usuários alterem o comportamento de criptografia padrão. **Desabilitar** impede que os usuários alterem o comportamento padrão de criptografia e obriga os usuários a usar a configuração que você configurou. Disponível no iOS 12 e mais recente.

  - **Forçar criptografia por mensagem**: A criptografia por mensagem permite que os usuários escolham quais emails são criptografados antes de serem enviados. Escolha **habilitar** para mostrar a opção de criptografia por mensagem ao criar um novo email. Os usuários podem optar por aceitar ou recusar a criptografia por mensagem. **Desabilitar** impede que a opção de criptografia por mensagem seja exibida.

    Se a configuração **criptografar por padrão** estiver habilitada, habilitar a criptografia por mensagem permitirá que os usuários recusem a criptografia por mensagem. Se a configuração **criptografar por padrão** estiver desabilitada, habilitar a criptografia por mensagem permitirá que os usuários aceitem a criptografia por mensagem.

  - **Certificado de criptografia S/MIME**: Selecione um perfil de certificado PKCS ou SCEP existente que é usado para criptografar mensagens de email.
    - **Permitir que o usuário altere a configuração**: Escolha **habilitar** para permitir que os usuários alterem o certificado de criptografia. **Desabilitar** impede que os usuários alterem o certificado de criptografia e força os usuários a usar o certificado configurado. Disponível no iOS 12 e mais recente.
- **Quantidade de email para sincronizar**: Escolha o número de dias de email que você deseja sincronizar. Em alternativa, selecione **Ilimitada** para sincronizar todos os e-mails disponíveis.
- **Permitir que as mensagens sejam movidas para outras contas de email**: **Habilitar** permite que os usuários movam mensagens de email entre contas diferentes dos usuários configurados em seus dispositivos.
- **Permitir que o email seja enviado de aplicativos de**terceiros: **Habilitar** permite que os usuários selecionem esse perfil como a conta padrão para enviar email. que as aplicações de terceiros abram o e-mail na aplicação de e-mail nativa, por exemplo, para anexar ficheiros ao e-mail.
- **Sincronizar endereços de email usados recentemente**: **Habilitar** permite que os usuários sincronizem a lista de endereços de email que foram usados recentemente no dispositivo com o servidor.

## <a name="next-steps"></a>Passos seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).

Defina configurações de email em dispositivos [Android](email-settings-android.md), [Android Enterprise](email-settings-android-enterprise.md), [Windows 10](email-settings-windows-10.md)e [Windows Phone 8,1](email-settings-windows-phone-8-1.md) .
