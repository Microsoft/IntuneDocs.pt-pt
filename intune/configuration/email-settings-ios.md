---
title: Configure as definições de email para dispositivos iOS/iPadOS no Microsoft Intune - Azure Microsoft Docs
description: Consulte uma lista de todas as definições de e-mail que pode configurar e adicionar aos dispositivos iOS e iPadOS no Microsoft Intune, incluindo a utilização de servidores Exchange e obter atributos do Diretório Ativo do Azure. Também pode ativar o SSL, autenticar utilizadores com certificados ou username/password, e sincronizar o e-mail em dispositivos iOS/iPadOS utilizando perfis de configuração do dispositivo no Microsoft Intune.
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
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ea06c50b1da237d4a822e80a8085b3b51913cec
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512811"
---
# <a name="add-e-mail-settings-for-ios-and-ipados-devices-in-microsoft-intune"></a>Adicione as definições de e-mail para dispositivos iOS e iPadOS no Microsoft Intune

No Microsoft Intune, pode criar e configurar e-mails para se conectar a um servidor de e-mail, escolher como os utilizadores autenticam, usam S/MIME para encriptação, e muito mais.

Este artigo lista e descreve todas as definições de e-mail disponíveis para dispositivos que executam iOS/iPadOS. Pode criar um perfil de configuração do dispositivo para empurrar ou implementar estas definições de e-mail para os seus dispositivos iOS/iPadOS.

## <a name="before-you-begin"></a>Antes de começar

Criar um perfil de [configuração do dispositivo](../email-settings-configure.md).

> [!NOTE]
> Estas configurações estão disponíveis para todos os tipos de inscrição. Para obter mais informações sobre os tipos de matrículas, consulte a [inscrição do iOS/iPadOS.](../ios-enroll.md)

## <a name="exchange-activesync-account-settings"></a>Trocar as definições de conta ActiveSync

- **Servidor de e-mail**: introduza o nome de anfitrião do seu servidor Exchange.
- **Nome da conta**: introduza o nome a apresentar da conta de e-mail. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de utilizador do AAD**: este nome é o atributo que o Intune obtém do Azure Active Directory (AAD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:
  - **Nome Principal de Utilizador**: obtém o nome, como `user1` ou `user1@contoso.com`
  - **Endereço SMTP primário**: obtém o nome no formato de endereço de e-mail, como `user1@contoso.com`
  - **Nome da Conta SAM**: precisa do domínio, como `domain\user1`. Introduza também:  
    - **Origem de nome de domínio do utilizador**: selecione **AAD** (Azure Active Directory) ou **Personalizado**.
      - **AAD:** Obtenha os atributos da Azure AD. Introduza também:
        - **Atributo de nome de domínio do utilizador a partir de AAD**: Escolha obter o nome de **domínio completo** (`contoso.com`) ou o **nome NetBIOS** (`contoso`) do utilizador.

      - **Personalizado**: Obtenha os atributos a partir de um nome de domínio personalizado. Introduza também:
        - **Nome de domínio personalizado a utilizar**: Introduza um valor que Intune utiliza para o nome de domínio, como `contoso.com` ou `contoso`.

- **Atributo de endereço de e-mail do AAD**: selecione como é gerado o endereço de e-mail do utilizador. As opções são:
  - **Nome principal**do utilizador : Utilize o nome principal completo como endereço de e-mail, como `user1@contoso.com` ou `user1`.
  - **Endereço Principal SMTP**: Utilize o endereço SMTP primário para iniciar sessão no Exchange, como `user1@contoso.com`.
- Método de **autenticação**: Escolha como os utilizadores autenticam o servidor de e-mail. As opções são:
  - **Certificado**: Selecione um perfil de certificado SCEP ou PKCS do cliente que criou anteriormente para autenticar a ligação De troca. Esta opção proporciona a experiência mais segura e perfeita para os seus utilizadores.
  - **Nome de utilizador e palavra-passe**: Os utilizadores são solicitados a introduzir o seu nome de utilizador e palavra-passe.
  - **Credencial derivada:** Utilize um certificado derivado do cartão inteligente de um utilizador. Para mais informações, consulte [Use credenciais derivadas no Microsoft Intune](../protect/derived-credentials.md).

  >[!NOTE]
  > A autenticação multifator do Azure não é suportada.
  
- **SSL**: **Ativar** resulta na utilização da comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o servidor Exchange.
- **OAuth**: **Ativar** resulta na utilização da comunicação Open Authorization (OAuth) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange. Se o seu servidor OAuth utilizar a autenticação de certificados, selecione **Certificado** como **Método de autenticação** e inclua o certificado juntamente com o perfil. Caso contrário, selecione **Nome de utilizador e palavra-passe** como **Método de autenticação**. Quando utilizar o OAuth, certifique-se de que:

  - Confirma que sua solução de e-mail suporta OAuth antes de direcionar este perfil para os seus utilizadores. O Office 365 Exchange Online suporta OAuth. O Exchange no Local e outras soluções de parceiro ou de terceiros poderão não suportar OAuth. É possível configurar o Exchange no Local para Autenticação Moderna (veja a mensagem de blogue [Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/) [Apresentamos a Autenticação Moderna Híbrida para o Exchange no Local]).

    Se o perfil de e-mail utilizar o OAuth e o serviço de e-mail não o suportar, a opção **Reintroduzir a palavra-passe** parecerá não funcionar. Por exemplo, não acontece nada quando o utilizador seleciona **Reintroduzir a palavra-passe** nas definições de dispositivos da Apple.

  - Quando o OAuth está ativado, os utilizadores finais têm uma experiência diferente de início de sessão no e-mail através de "Autenticação moderna" que suporta autenticação multifator (MFA). 

  - Algumas organizações desativam a funcionalidade que permite que os utilizadores finais utilizem o [acesso de gestão personalizada à aplicação](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access). Neste cenário, o início de sessão através de Autenticação Moderna poderá falhar até que um Administrador crie a aplicação empresarial "Contas iOS" e conceda acesso à aplicação no Azure AD aos utilizadores.

    A ação padrão é adicionar uma aplicação utilizando a funcionalidade de adição de **app** do Painel de Acesso à [Aplicação](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) **sem aprovação de negócios.** Para obter mais informações, veja [Atribuir utilizadores a Aplicações](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > Quando ativar o OAuth, ocorrerá o seguinte:  
  > 1. Será emitido um novo perfil para os dispositivos já visados.
  > 2. Será novamente pedido aos utilizadores finais que introduzam as respetivas credenciais.

## <a name="exchange-activesync-profile-configuration"></a>Configuração de perfil ActiveSync de troca

> [!IMPORTANT]
> Configurar estas definições implementa um novo perfil para o dispositivo, mesmo quando um perfil de e-mail existente é atualizado para incluir estas definições. Os utilizadores são solicitados a introduzir a sua palavra-passe da conta Exchange ActiveSync. Estas definições afetam quando a palavra-passe é introduzida.

- **Troque dados para sincronizar**: Ao utilizar o Exchange ActiveSync, escolha os serviços de Troca sincronizados no dispositivo: Calendário, Contactos, Lembretes, Notas e E-mail. As opções são:
  - **Todos os dados** (predefinido): O Sync está ativado para todos os serviços.
  - **Só para emails:** O Sync está ativado apenas para e-mail. O Sync está desativado para os outros serviços.
  - **Apenas para o calendário:** O sincronizado está ativado apenas para o Calendário. O Sync está desativado para os outros serviços.
  - **Calendário e Contactos: O**Sincronizado está ativado apenas para calendários e contactos. O Sync está desativado para os outros serviços.
  - **Apenas contactos:** O Sync está ativado apenas para contactos. O Sync está desativado para os outros serviços.

  Esta funcionalidade aplica-se a:  
  - iOS 13.0 e mais recente
  - iPadOS 13.0 e mais recente

- **Permitir que os utilizadores alterem as definições**de sincronização : Escolha se os utilizadores podem alterar as definições de Exchange ActiveSync para os serviços de Troca no dispositivo: Calendário, Contactos, Lembretes, Notas e E-mail. As opções são:

  - **Sim** (padrão): Os utilizadores podem alterar o comportamento sincronizado de todos os serviços. Escolher **Sim** permite alterações a *todos os* serviços.
  - **Não**: Os utilizadores não podem alterar as definições de sincronização de todos os serviços. Escolha **Não há** alterações de blocos em *todos os* serviços.

  > [!TIP]
  > Se configurar os **dados de Troca para sincronizar** a definição para sincronizar apenas alguns serviços, recomendamos selecionar **Não** para esta definição. Escolher **Não** impede os utilizadores de alterar o serviço De troca sincronizado.

  Esta funcionalidade aplica-se a:  
  - iOS 13.0 e mais recente
  - iPadOS 13.0 e mais recente

## <a name="exchange-activesync-email-settings"></a>Trocar definições de e-mail ActiveSync

- **S/MIME**: S/MIME utiliza certificados de e-mail que fornecem segurança extra às suas comunicações de e-mail, assinando, encriptando e desencriptando. Quando utiliza S/MIME com uma mensagem de correio eletrónico, confirma a autenticidade do remetente e a integridade e confidencialidade da mensagem.

  As opções são:

  - **Desative S/MIME** (predefinição): Não utiliza um certificado de e-mail S/MIME para assinar, encriptar ou desencriptar e-mails.
  - **Ativar S/MIME**: Permite que os utilizadores assinem e/ou criptografem e-mails na aplicação de correio nativo iOS/iPadOS. Introduza também:

    - **S/MIME ativada**por assinatura : **Desativar** (predefinido) não permite que os utilizadores assinem digitalmente a mensagem. **O Enable** permite que os utilizadores assinem digitalmente o e-mail de saída para a conta que inseriu. A assinatura ajuda os utilizadores que recebem mensagens a terem a certeza de que a mensagem veio do remetente específico, e não de alguém que finge ser o remetente.
      - **Permitir que o utilizador altere a definição**: **Ativar** permite que os utilizadores alterem as opções de assinatura. **Desativar** (predefinido) impede os utilizadores de alterar a assinatura e obriga os utilizadores a utilizarem a assinatura configurada.
      - **Tipo de certificado de assinatura**: As suas opções:
        - **Não configurado**: Intune não atualiza nem altera esta definição.
        - **Nenhum:** Como administrador, não se força um certificado específico. Selecione esta opção para que os utilizadores possam escolher o seu próprio certificado.
        - **Credencial derivada:** Utilize um certificado derivado do cartão inteligente de um utilizador. Para mais informações, consulte [Use credenciais derivadas no Microsoft Intune](../protect/derived-credentials.md).
        - **Certificados**: Selecione um perfil de certificado PKCS ou SCEP existente que seja utilizado para a assinatura de mensagens de correio eletrónico.
      - **Permitir que o utilizador altere a definição**: **Ativar** permite que os utilizadores alterem o certificado de assinatura. **Desativar** (predefinido) impede os utilizadores de alterar o certificado de assinatura e obriga os utilizadores a utilizarem o certificado configurado.

        Esta funcionalidade aplica-se a:  
        - iOS 12 e mais recente
        - iPadOS 12 e mais recente

    - **Criptografe por defeito**: **Ative** encriptar todas as mensagens como o comportamento predefinido. **Desativar** (padrão) não encripta todas as mensagens como o comportamento predefinido.
      - **Permitir que o utilizador altere a definição**: **Ativar** permite que os utilizadores alterem o comportamento de encriptação predefinido. **O desativação** impede que os utilizadores mudem o comportamento predefinido da encriptação e força os utilizadores a utilizarem a encriptação configurada.

        Esta funcionalidade aplica-se a:  
        - iOS 12 e mais recente
        - iPadOS 12 e mais recente

    - **Encriptação**de força por mensagem : A encriptação por mensagem permite que os utilizadores escolham quais os e-mails encriptados antes de serem enviados.

      **O Enable** mostra a opção de encriptação por mensagem ao criar um novo e-mail. Os utilizadores podem então optar por optar por optar por encriptação por mensagem. Se a definição **de encriptação por padrão** também estiver ativada, permitir a encriptação por mensagem permite que os utilizadores optem por não encriptar por mensagem.

      **Desativar** (predefinido) impede que a opção de encriptação por mensagem se mostre. Se a definição **de encriptação por padrão** também for desativada, permitir a encriptação por mensagem permite que os utilizadores optem pela encriptação por mensagem.

      - **Tipo de certificado de encriptação**: As suas opções:
        - **Não configurado**: Intune não atualiza nem altera esta definição.
        - **Nenhum:** Como administrador, não se força um certificado específico. Selecione esta opção para que os utilizadores possam escolher o seu próprio certificado.
        - **Credencial derivada:** Utilize um certificado derivado do cartão inteligente de um utilizador. Para mais informações, consulte [Use credenciais derivadas no Microsoft Intune](../protect/derived-credentials.md).
        - **Certificados**: Selecione um perfil de certificado PKCS ou SCEP existente que seja utilizado para a assinatura de mensagens de correio eletrónico.
      - **Permitir que o utilizador altere a definição**: **Permitir** que os utilizadores alterem o certificado de encriptação. **Desativar** (predefinido) impede os utilizadores de alterar o certificado de encriptação e obriga os utilizadores a utilizar em conjunto o certificado configurado.

        Esta funcionalidade aplica-se a:  
        - iOS 12 e mais recente
        - iPadOS 12 e mais recente

- **Quantidade de e-mails a sincronizar**: selecione o número de dias de e-mails que pretende sincronizar. Em alternativa, selecione **Ilimitada** para sincronizar todos os e-mails disponíveis.
- **Permitir que as mensagens sejam transferidas para outras contas de e-mail**: **Ativar** (predefinido) permite que os utilizadores movam mensagens de correio eletrónico entre diferentes contas que os utilizadores configuram nos seus dispositivos.
- **Permitir que o e-mail seja enviado a partir de aplicações de terceiros**: **Ativar** (predefinido) permite que os utilizadores selecionem este perfil como a conta predefinida para envio de e-mail. que as aplicações de terceiros abram o e-mail na aplicação de e-mail nativa, por exemplo, para anexar ficheiros ao e-mail.
- **Sincronizar endereços de e-mail recentemente utilizados**: **Ativar** (predefinido) permite que os utilizadores sincronizem a lista de endereços de e-mail que foram recentemente utilizados no dispositivo com o servidor.

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](../device-profile-assign.md) e [monitorize o estado](../device-profile-monitor.md).

Configure as definições de e-mail nos dispositivos [Android](../email-settings-android.md), [Android Enterprise,](../email-settings-android-enterprise.md) [Windows 10](email-settings-windows-10.md)e [Windows Phone 8.1.](email-settings-windows-phone-8-1.md)
