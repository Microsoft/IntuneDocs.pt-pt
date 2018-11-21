---
title: Definições do Outlook para dispositivos iOS e Android no Microsoft Intune
description: Crie uma política de configuração para configurar as definições do Microsoft Outlook em execução em dispositivos iOS e Android.
keywords: ''
author: Erikre
ms.author: erikre
ms.reviewer: smithre4
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 691029cc7b9fd8880c5440a84b95bbf2462920d6
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180328"
---
# <a name="microsoft-outlook-configuration-settings"></a>Definições de configuração do Microsoft Outlook 

Utilize uma política de configuração para configurar as definições do Microsoft Outlook em execução em dispositivos iOS e Android. 

Para criar uma política de configuração de aplicações para dispositivos iOS geridos, veja [Adicionar políticas de configuração de aplicações para dispositivos iOS geridos](app-configuration-policies-use-ios.md). Para criar uma política de configuração de aplicações para dispositivos Android geridos, veja [Adicionar políticas de configuração de aplicações para dispositivos Android geridos](app-configuration-policies-use-android.md). 

## <a name="configuration-settings"></a>Definições de configuração

Ao adicionar uma política de configuração no Intune, pode definir configurações específicas para configurar o Microsoft Outlook. No painel **Definições de configuração** pode definir a configuração da conta de e-mail.

### <a name="basic-authentication-email-account-settings"></a>Definições de contas de e-mail com a Autenticação básica
O Outlook para iOS e Android proporciona aos administradores do Exchange a capacidade de enviar configurações de conta aos seus utilizadores no local que utilizam a Autenticação básica com o protocolo ActiveSync. Para obter mais informações, veja [Account setup in Outlook for iOS and Android using Basic authentication](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/account-setup) (Configuração de contas no Outlook para iOS e Android com a Autenticação básica). Para ativar a configuração de contas, pode configurar as seguintes definições:

- **Servidor de e-mail**: introduza o nome de anfitrião do seu servidor Exchange no local (por exemplo, mail.contoso.com).
- **Nome da conta de e-mail**: introduza o nome a apresentar da conta de e-mail. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de utilizador do AAD**: este nome é o atributo que o Intune obtém do Azure Active Directory (Azure AD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções incluem:
  - **Nome Principal de Utilizador**: obtém o nome, como `user1` ou `user1@contoso.com`
  - **Endereço SMTP primário**: obtém o nome no formato de endereço de e-mail, como `user1@contoso.com`
- **Atributo de endereço de e-mail do AAD**: selecione como é gerado o endereço de e-mail do utilizador. Selecione **Nome principal de utilizador** (`user1@contoso.com` ou `user1`) para utilizar o nome principal completo como o endereço de e-mail ou o **Endereço SMTP primário** (`user1@contoso.com`) para utilizar o endereço SMTP primário para iniciar sessão no Exchange. A recomendação é selecionar **Endereço SMTP primário**.
- **Domínio da conta**: (opcional) o domínio da conta.

## <a name="next-steps"></a>Passos Seguintes
[Configurar as definições de e-mail no Intune](email-settings-configure.md)

