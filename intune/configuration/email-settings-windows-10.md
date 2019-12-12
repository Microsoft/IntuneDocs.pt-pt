---
title: Definições de e-mail para dispositivos com o Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Crie um perfil de e-mail de configuração de dispositivos que utiliza os servidores Exchange e obtém atributos do Azure Active Directory. Também pode ativar o SSL e sincronizar e-mails e agendas em dispositivos com o Windows 10 através do Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9882749ec90f2a1de4edf53535a79d893ca60e63
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72492805"
---
# <a name="email-profile-settings-for-devices-running-windows-10---intune"></a>Definições do perfil de e-mail para dispositivos com o Windows 10 – Intune

Use as configurações de perfil de email para configurar o aplicativo de email em seus dispositivos que executam o Windows 10.

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

- **Atributo de endereço de e-mail do AAD**: selecione como é gerado o endereço de e-mail do utilizador. Selecione **Nome principal de utilizador** (`user1@contoso.com` ou `user1`) para utilizar o nome principal completo como o endereço de e-mail ou o **Endereço SMTP primário** (`user1@contoso.com`) para utilizar o endereço SMTP primário para iniciar sessão no Exchange.

## <a name="security-settings"></a>Definições de segurança

- **SSL**: utilize a comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o servidor Exchange.

## <a name="synchronization-settings"></a>Definições de sincronização

- **Quantidade de e-mails a sincronizar**: selecione o número de dias de e-mails que pretende sincronizar. Em alternativa, selecione **Ilimitada** para sincronizar todos os e-mails disponíveis.
- **Agenda de sincronização**: selecione a agenda dos dispositivos para sincronizar dados a partir do servidor Exchange. Também pode selecionar **À medida que as mensagens são recebidas**, para sincronizar os dados assim que forem recebidos, ou **Manual**, em que o utilizador do dispositivo tem de iniciar a sincronização.

## <a name="content-sync-settings"></a>Definições de sincronização de conteúdo

- **Tipo de conteúdo a sincronizar** – selecione os tipos de conteúdos que pretende sincronizar nos dispositivos a partir de:
  - **Contactos**
  - **Calendário**
  - **Tarefas**

## <a name="next-steps"></a>Próximos passos
[Configurar as definições de e-mail no Intune](../email-settings-configure.md)
