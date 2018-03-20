---
title: "Definições de e-mail do Microsoft Intune para dispositivos com o Windows 10"
titleSuffix: 
description: "Saiba mais sobre as definições do Microsoft Intune que pode utilizar para configurar as definições de e-mail em dispositivos com o Windows 10."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b02579895123995f9b4205d64e9bf67ce04de746
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-windows-10"></a>Definições de perfis de e-mail no Microsoft Intune para dispositivos com o Windows 10

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este artigo mostra-lhe as definições de perfis de e-mail que pode configurar para os seus dispositivos com o Windows 10.


- **Servidor de e-mail** – O nome de anfitrião do servidor Exchange.
- **Nome da conta** – O nome a apresentar para a conta de e-mail conforme aparece aos utilizadores nos dispositivos.
- **Atributo de nome de utilizador do AAD** – este é o atributo no Active Directory (AD) ou Azure AD que servirá para gerar o nome de utilizador para este perfil de e-mail. Selecione o **Endereço SMTP Principal**, como **user1@contoso.com**, ou o **Nome Principal de Utilizador**, como **user1** ou **user1@contoso.com**.
- **Atributo de endereço de e-mail do AAD** – Como é gerado o endereço de e-mail do utilizador em cada dispositivo. Selecione **Endereço SMTP Principal** para utilizar o endereço SMTP principal para iniciar sessão no Exchange ou selecione **Nome Principal de Utilizador** para utilizar o nome principal completo como o endereço de e-mail.


## <a name="security-settings"></a>Definições de segurança

- **SSL** – Utilize a comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange Server.



## <a name="synchronization-settings"></a>Definições de sincronização

- **Quantidade de e-mails a sincronizar** – Selecione o número de dias de e-mail que pretende sincronizar ou selecione **Sem Limite** para sincronizar todos os e-mails disponíveis.
- **Agenda de sincronização** – Selecione o agendamento através do qual os dispositivos sincronizam os dados do servidor Exchange. Também pode selecionar **Quando chegarem mensagens**, que sincroniza os dados assim que chegam, ou **Manual**, em que o utilizador do dispositivo tem de iniciar a sincronização.

## <a name="content-sync-settings"></a>Definições de sincronização de conteúdo

- **Tipo de conteúdo a sincronizar** – Selecione os tipos de conteúdo que pretende sincronizar nos dispositivos a partir de:
    - **Contactos**
    - **Calendário**
    - **Tarefas**
