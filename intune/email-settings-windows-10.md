---
title: Definições de e-mail para dispositivos com o Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Crie um perfil de e-mail de configuração de dispositivos que utiliza os servidores Exchange e obtém atributos do Azure Active Directory. Também pode ativar o SSL e sincronizar e-mails e agendas em dispositivos com o Windows 10 através do Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 04834f21e5fd2f6ed0f7454988936397d3249987
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37904973"
---
# <a name="email-profile-settings-for-devices-running-windows-10---intune"></a>Definições do perfil de e-mail para dispositivos com o Windows 10 – Intune

Utilize as definições do perfil de e-mail para configurar os seus dispositivos com o Windows 10.

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
[Configurar as definições de e-mail no Intune](email-settings-configure.md)