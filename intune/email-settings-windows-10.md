---
title: Definições de e-mail para dispositivos com o Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Crie um perfil de e-mail de configuração de dispositivos que utiliza os servidores Exchange e obtém atributos do Azure Active Directory. Também pode ativar o SSL e sincronizar e-mails e agendas em dispositivos com o Windows 10 através do Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 911d16cfd729af1c55e3c06b9b30d94f281ed18a
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57391354"
---
# <a name="email-profile-settings-for-devices-running-windows-10---intune"></a>Definições do perfil de e-mail para dispositivos com o Windows 10 – Intune

Utilize as definições de perfil de e-mail para configurar a aplicação de correio nos seus dispositivos com o Windows 10.

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

- **Atributo de endereço de e-mail do AAD**: Escolha como é gerado o endereço de e-mail do utilizador. Selecione **Nome principal de utilizador** (`user1@contoso.com` ou `user1`) para utilizar o nome principal completo como o endereço de e-mail ou o **Endereço SMTP primário** (`user1@contoso.com`) para utilizar o endereço SMTP primário para iniciar sessão no Exchange.

## <a name="security-settings"></a>Definições de segurança

- **SSL**: Utilize comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange Server.

## <a name="synchronization-settings"></a>Definições de sincronização

- **Quantidade de e-mails a sincronizar**: Escolha o número de dias de e-mail que pretende sincronizar. Em alternativa, selecione **Ilimitada** para sincronizar todos os e-mails disponíveis.
- **Agenda de sincronização**: Selecione o agendamento para sincronizar os dados do servidor do Exchange também pode selecionar os dispositivos **quando chegarem mensagens**, que sincroniza os dados assim que chegam, ou **Manual**, em que o utilizador do dispositivo tem de iniciar a sincronização.

## <a name="content-sync-settings"></a>Definições de sincronização de conteúdo

- **Tipo de conteúdo a sincronizar**: Selecione os tipos de conteúdo que pretende sincronizar nos dispositivos a partir de:
  - **Contactos**
  - **Calendário**
  - **Tarefas**

## <a name="next-steps"></a>Passos Seguintes
[Configurar as definições de e-mail no Intune](email-settings-configure.md)
