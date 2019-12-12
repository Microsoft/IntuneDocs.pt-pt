---
title: Configurações de email do Android Enterprise no Microsoft Intune-Azure | Microsoft Docs
description: Crie perfis de email de configuração de dispositivo que usam servidores Exchange e recupere atributos de Azure Active Directory. Habilite SSL ou SMIME, autentique usuários com certificados ou nome de usuário/senha e sincronize emails e agendas em dispositivos de perfil de trabalho do Android usando Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/07/2019
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
ms.openlocfilehash: 92d81e383a9964aaecbdd151397879236ffcb726
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72493554"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Configurações de dispositivo do Android Enterprise para configurar email, autenticação e sincronização no Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este artigo lista e descreve as diferentes configurações de email que você pode controlar em dispositivos Android Enterprise. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para configurar um servidor de e-mail, utilize o SSL para encriptar mensagens de correio eletrónico e muito mais.

Como administrador do Intune, você pode criar e atribuir configurações de email a dispositivos Android Enterprise no perfil de trabalho.

Para saber mais sobre perfis de email no Intune, consulte [definir configurações de email](email-settings-configure.md).

## <a name="before-you-begin"></a>Antes de começar

Crie um [perfil de configuração de dispositivo](email-settings-configure.md#create-a-device-profile) (escolha o perfil de trabalho) ou crie uma [política de configuração de aplicativo](../apps/app-configuration-policies-use-android.md).

## <a name="android-enterprise"></a>Android Enterprise

- **Aplicação de e-mail**: selecione **Gmail** ou **Nine Work**
- **Servidor de e-mail**: o nome de anfitrião do seu servidor Exchange. Por exemplo, introduza `outlook.office365.com`.
- **Atributo de nome de utilizador do AAD**: este nome é o atributo que o Intune obtém do Azure Active Directory (Azure AD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:

  - **Nome Principal de Utilizador**: obtém o nome, como `user1` ou `user1@contoso.com`.
  - **Nome de utilizador**: obtém apenas o nome como `user1`

- **Atributo de endereço de email do AAD**: esse nome é o atributo de email que o Intune obtém do Azure AD. O Intune gera dinamicamente o endereço de email usado por esse perfil. As opções são:
  - **Nome principal do usuário**: usa o nome da entidade de segurança completa, como `user1@contoso.com` ou `user1`, como o endereço de email.
  - **Endereço SMTP primário**: usa o endereço SMTP primário, como `user1@contoso.com`, para entrar no Exchange.

- **Método de autenticação**: selecione **nome de usuário e senha** ou **certificados** como o método de autenticação usado pelo perfil de email.
  - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a ligação ao Exchange.
- **SSL**: escolha **habilitar** para usar a comunicação de protocolo SSL (SSL) ao enviar emails, receber emails e comunicar-se com o Exchange Server.
- **Quantidade de email para sincronizar**: escolha a quantidade de tempo de email que você deseja sincronizar. Ou selecione **ilimitado** para sincronizar todos os emails disponíveis.
- **Tipo de conteúdo a ser sincronizado** (apenas nove trabalho): escolha quais dados você deseja sincronizar nos dispositivos. As opções são:
  - **Contatos**: escolha **habilitar** para permitir que os usuários finais sincronizem contatos com seus dispositivos.
  - **Calendário**: escolha **habilitar** para permitir que os usuários finais sincronizem o calendário com seus dispositivos.
  - **Tarefas**: escolha **habilitar** para permitir que os usuários finais sincronizem tarefas para seus dispositivos.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Você também pode criar perfis de email para [Android Samsung Knox](email-settings-android.md), [Ios](email-settings-ios.md), [Windows 10 e posterior](email-settings-windows-10.md)e [Windows Phone dispositivos 8,1](email-settings-windows-phone-8-1.md) .
