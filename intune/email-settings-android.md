---
title: "Definições de e-mail do Intune para dispositivos Android e Android for Work"
titleSuffix: Azure portal
description: "Saiba mais sobre as definições do Intune que pode utilizar para configurar ligações de e-mail em dispositivos Android.\""
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4d3458cc-fcaa-4648-b13f-bf1f0616c1c5
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 14f726d330e1cd8e4a0f7bfcfac8fe931c66d23b
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="email-profile-settings-for-android--devices-in-microsoft-intune"></a>Definições de perfis de e-mail para dispositivos Android no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Como um administrador do Intune, pode criar e atribuir definições de e-mail aos seguintes dispositivos Android:
- [Android Samsung Knox Standard](#android-samsung-knox-standard-email-settings)
- [Android for Work](#android-for-work-email-settings)

## <a name="android-samsung-knox-standard-email-settings"></a>Definições de e-mail para Android Samsung Knox Standard
- **Servidor de e-mail** – O nome de anfitrião do servidor Exchange.
- **Nome da conta** – O nome a apresentar para a conta de e-mail conforme aparece aos utilizadores nos dispositivos.
- **Atributo de nome de utilizador do AAD** – Este nome é o atributo no Active Directory (AD) ou Azure AD utilizado para gerar o nome de utilizador para este perfil de e-mail. Selecione o **Endereço SMTP Principal**, como user1@contoso.com, ou o **Nome Principal de Utilizador**, como user1 ou user1@contoso.com.
- **Atributo de endereço de e-mail do AAD** – Como é gerado o endereço de e-mail do utilizador em cada dispositivo. Selecione **Endereço SMTP Principal** para utilizar o endereço SMTP principal para iniciar sessão no Exchange ou selecione **Nome Principal de Utilizador** para utilizar o nome principal completo como o endereço de e-mail.
- **Método de autenticação** – Selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como método de autenticação utilizado pelo perfil de e-mail.
    - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a ligação ao Exchange.

### <a name="security-settings"></a>Definições de segurança

- **SSL** – Utilize a comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange Server.
- **S/MIME** – Envie e-mails com a encriptação S/MIME.
    - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a ligação ao Exchange.

### <a name="synchronization-settings"></a>Definições de sincronização

- **Quantidade de e-mails a sincronizar** – Selecione o número de dias de e-mail que pretende sincronizar ou selecione **Sem Limite** para sincronizar todos os e-mails disponíveis.
- **Agenda de sincronização** – Selecione o agendamento através do qual os dispositivos sincronizam os dados do servidor Exchange. Também pode selecionar **Quando chegarem mensagens**, que sincroniza os dados quando chegam, ou **Manual**, em que o utilizador do dispositivo tem de iniciar a sincronização.

### <a name="content-sync-settings"></a>Definições de sincronização de conteúdo

- **Tipo de conteúdo a sincronizar** – Selecione os tipos de conteúdo que pretende sincronizar nos dispositivos a partir de:
    - **Contactos**
    - **Calendário**
    - **Tarefas**

## <a name="android-for-work-email-settings"></a>Definições de e-mail do Android for Work

- **Aplicação de e-mail** – Selecione **Gmail** ou **Nine Work**
- **Servidor de e-mail** – O nome de anfitrião do servidor Exchange.
- **Atributo de nome de utilizador do AAD** – Este nome é o atributo no Active Directory (AD) ou Azure AD que servirá para gerar o nome de utilizador para este perfil de e-mail. Selecione o **Endereço SMTP Principal**, como user1@contoso.com, ou o **Nome Principal de Utilizador**, como user1 ou user1@contoso.com.
- **Atributo de endereço de e-mail do AAD** – Como é gerado o endereço de e-mail do utilizador em cada dispositivo. Selecione o **Nome Principal de Utilizador** para utilizar o nome principal completo como o endereço de e-mail ou o **Nome de utilizador**.
- **Método de autenticação** – Selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como método de autenticação utilizado pelo perfil de e-mail.
    - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente para autenticar a ligação ao Exchange.
- **SSL** – Utilize a comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange Server.
- **Quantidade de e-mails a sincronizar** – Selecione o número de dias de e-mail que pretende sincronizar ou selecione **Sem Limite** para sincronizar todos os e-mails disponíveis.
- **Tipo de conteúdo a sincronizar** (Nine Work apenas) – Selecione os tipos de conteúdo que pretende sincronizar nos dispositivos a partir de:
    - **Contactos**
    - **Calendário**
    - **Tarefas**
