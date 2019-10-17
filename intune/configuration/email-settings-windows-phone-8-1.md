---
title: Definições de e-mail do Microsoft Intune para o Windows Phone 8.1
titleSuffix: ''
description: Saiba mais sobre as definições do Intune que pode utilizar para configurar ligações de e-mail em dispositivos com o Windows Phone 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 455d69328f8b70b1de73067c6290b6955df1e710
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506759"
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Definições de perfis de e-mail no Microsoft Intune para dispositivos com o Windows Phone 8.1

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este artigo mostra-lhe as definições de perfis de e-mail que pode configurar para os seus dispositivos com Windows Phone 8.1.


- **Aplicar todas as definições apenas ao Windows Phone 8.1** – Esta é uma definição que pode configurar no portal clássico do Intune. No portal do Azure, esta definição não pode ser alterada. Se esta definição estiver definida como **Configurada**, as definições só são aplicadas a dispositivos com o Windows Phone 8.1. Se estiver definida como **Não configurada**, estas definições também são aplicadas a dispositivos com o Windows 10 Mobile.
- **Servidor de e-mail** – O nome de anfitrião do servidor Exchange.
- **Nome da conta** – O nome a apresentar para a conta de e-mail conforme aparece aos utilizadores nos dispositivos.
- **Atributo de nome de utilizador do AAD** – este é o atributo no Active Directory (AD) ou Azure AD que servirá para gerar o nome de utilizador para este perfil de e-mail. Selecione o **Endereço SMTP Principal**, como **user1@contoso.com** , ou o **Nome Principal de Utilizador**, como **user1** ou **user1@contoso.com** .
- **Atributo de endereço de e-mail do AAD** – Como é gerado o endereço de e-mail do utilizador em cada dispositivo. Selecione **Endereço SMTP Principal** para utilizar o endereço SMTP principal para iniciar sessão no Exchange ou selecione **Nome Principal de Utilizador** para utilizar o nome principal completo como o endereço de e-mail.


## <a name="security-settings"></a>Definições de segurança

- **SSL** – Utilize a comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange Server.



## <a name="synchronization-settings"></a>Definições de sincronização

- **Quantidade de e-mails a sincronizar** – Selecione o número de dias de e-mail que pretende sincronizar ou selecione **Sem limite** para sincronizar todos os e-mails disponíveis.
- **Agenda de sincronização** – Selecione o agendamento através do qual os dispositivos sincronizam os dados do servidor Exchange. Também pode selecionar **Quando chegarem mensagens**, que sincroniza os dados assim que chegam, ou **Manual**, em que o utilizador do dispositivo tem de iniciar a sincronização.

## <a name="content-sync-settings"></a>Definições de sincronização de conteúdo

- **Tipo de conteúdo a sincronizar** – Selecione os tipos de conteúdo que pretende sincronizar nos dispositivos a partir de:
  - **Contactos**
  - **Calendário**
  - **Tarefas**
