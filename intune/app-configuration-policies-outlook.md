---
title: Definições do Outlook para dispositivos iOS e Android no Microsoft Intune
description: Crie uma política de configuração para configurar as definições do Microsoft Outlook em execução em dispositivos iOS e Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7fc9f34bbd3d14ac4291582247b1e45169c2cccc
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828936"
---
# <a name="microsoft-outlook-configuration-settings"></a>Definições de configuração do Microsoft Outlook 

Utilize uma política de configuração para configurar as definições do Microsoft Outlook em execução em dispositivos iOS e Android. 

Para criar uma política de configuração de aplicações para dispositivos iOS geridos, veja [Adicionar políticas de configuração de aplicações para dispositivos iOS geridos](app-configuration-policies-use-ios.md). Para criar uma política de configuração de aplicações para dispositivos Android geridos, veja [Adicionar políticas de configuração de aplicações para dispositivos Android geridos](app-configuration-policies-use-android.md). 

## <a name="configuration-settings"></a>Definições de configuração

Ao adicionar uma política de configuração no Intune, pode definir configurações específicas para configurar o Microsoft Outlook. No painel **Definições de configuração** pode definir a configuração da conta de e-mail.

### <a name="email-account-settings"></a>Definições da conta de e-mail

As seguintes definições de configuração são específicas para o Microsoft Outlook.

- **Servidor de e-mail**: introduza o nome de anfitrião do seu servidor Exchange.
- **Nome da conta de e-mail**: introduza o nome a apresentar da conta de e-mail. Este nome será apresentado nos dispositivos dos utilizadores.
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
- **Domínio da conta**: (opcional) o domínio da conta.

## <a name="next-steps"></a>Próximos passos
[Configurar as definições de e-mail no Intune](email-settings-configure.md)

