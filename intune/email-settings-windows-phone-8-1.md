---
title: "Definições de e-mail do Intune para o Windows Phone 8.1"
titleSuffix: Azure portal
description: "Saiba mais sobre as definições do Intune que pode utilizar para configurar ligações de e-mail em dispositivos Windows Phone 8.1.\""
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 352d6bd9-ec8c-439e-be3a-ad3daf307df2
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: beebbc49d076ac9d3d65ff7650e4cea3fb8925f6
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/12/2017
---
# <a name="email-profile-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>Definições de perfis de e-mail para dispositivos Windows Phone 8.1 no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


- **Aplicar todas as definições apenas ao Windows Phone 8.1** – Esta é uma definição que pode configurar no portal clássico do Intune. No portal do Azure, esta definição não pode ser alterada. Se esta definição estiver definida como **Configurada**, as definições só serão aplicadas a dispositivos com o Windows Phone 8.1. Se estiver definida como **Não configurada**, estas definições também serão aplicadas a dispositivos com o Windows 10 Mobile.
- **Servidor de e-mail** – O nome de anfitrião do servidor Exchange.
- **Nome da conta** – O nome a apresentar para a conta de e-mail conforme irá aparecer aos utilizadores nos dispositivos.
- **Atributo de nome de utilizador do AAD** – Este é o atributo no Active Directory (AD) ou Azure AD que servirá para gerar o nome de utilizador para este perfil de e-mail. Selecione o **Endereço SMTP Principal**, como **user1@contoso.com**, ou o **Nome Principal de Utilizador**, como **user1** ou **user1@contoso.com**.
- **Atributo de endereço de e-mail do AAD** – Como é gerado o endereço de e-mail do utilizador em cada dispositivo. Selecione **Endereço SMTP Principal** para utilizar o endereço SMTP principal para iniciar sessão no Exchange ou selecione **Nome Principal de Utilizador** para utilizar o nome principal completo como o endereço de e-mail.


## <a name="security-settings"></a>Definições de segurança

- **SSL** – Utilize a comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange Server.



## <a name="synchronization-settings"></a>Definições de sincronização

- **Quantidade de e-mails a sincronizar** – Selecione o número de dias de e-mail que pretende sincronizar ou selecione **Sem limite** para sincronizar todos os e-mails disponíveis.
- **Agenda de sincronização** – Selecione o agendamento através do qual os dispositivos irão sincronizar os dados do servidor Exchange. Também pode selecionar **Quando chegarem mensagens**, que sincroniza os dados assim que chegam, ou **Manual**, em que o utilizador do dispositivo tem de iniciar a sincronização.

## <a name="content-sync-settings"></a>Definições de sincronização de conteúdo

- **Tipo de conteúdo a sincronizar** – Selecione os tipos de conteúdo que pretende sincronizar nos dispositivos a partir de:
    - **Contactos**
    - **Calendário**
    - **Tarefas**
