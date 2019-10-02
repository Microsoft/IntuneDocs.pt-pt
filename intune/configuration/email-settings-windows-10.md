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
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 22db8f4b531d65169d1a0f2289a3221d6760ba05
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730640"
---
# <a name="email-profile-settings-for-devices-running-windows-10---intune"></a>Definições do perfil de e-mail para dispositivos com o Windows 10 – Intune

Use as configurações de perfil de email para configurar o aplicativo de email em seus dispositivos que executam o Windows 10.

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

- **Atributo de endereço de email do AAD**: Escolha como o endereço de email do usuário é gerado. Selecione **Nome principal de utilizador** (`user1@contoso.com` ou `user1`) para utilizar o nome principal completo como o endereço de e-mail ou o **Endereço SMTP primário** (`user1@contoso.com`) para utilizar o endereço SMTP primário para iniciar sessão no Exchange.

## <a name="security-settings"></a>Definições de segurança

- **SSL**: Utilize comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange Server.

## <a name="synchronization-settings"></a>Definições de sincronização

- **Quantidade de email para sincronizar**: Escolha o número de dias de email que você deseja sincronizar. Em alternativa, selecione **Ilimitada** para sincronizar todos os e-mails disponíveis.
- **Agenda de sincronização**: Selecione a agenda de dispositivos para sincronizar os dados do Exchange Server você também pode selecionar **à medida que as mensagens chegam**, que sincroniza os dados assim que ele chega, ou **manual**, onde o usuário do dispositivo deve iniciar a sincronização.

## <a name="content-sync-settings"></a>Definições de sincronização de conteúdo

- **Tipo de conteúdo a ser sincronizado**: Selecione os tipos de conteúdo dos quais você deseja sincronizar os dispositivos:
  - **Contactos**
  - **Calendário**
  - **Tarefas**

## <a name="next-steps"></a>Passos Seguintes
[Configurar as definições de e-mail no Intune](../email-settings-configure.md)
