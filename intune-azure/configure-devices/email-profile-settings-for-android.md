---
title: "Definições de e-mail do Intune para dispositivos Android | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba mais sobre as definições do Intune que pode utilizar para configurar ligações de e-mail em dispositivos Android."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4d3458cc-fcaa-4648-b13f-bf1f0616c1c5
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f16c9dfb41cb2cfe07ce473a131dac767dee9c74
ms.openlocfilehash: 38858170e50add07f41138848e49e97bde8ac1b2


---

# <a name="email-profile-settings-for-android-devices-in-intune-azure-preview"></a>Definições de perfil de e-mail para dispositivos Android na pré-visualização do Azure no Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]



- **Servidor de e-mail** – O nome de anfitrião do servidor Exchange.
- **Nome da conta** – O nome a apresentar para a conta de e-mail conforme irá aparecer aos utilizadores nos dispositivos.
- **Atributo de nome de utilizador do AAD** – Este é o atributo no Active Directory (AD) ou Azure AD que servirá para gerar o nome de utilizador para este perfil de e-mail. Selecione o **Endereço SMTP Principal**, como user1@contoso.com, ou o **Nome Principal de Utilizador**, como user1 ou user1@contoso.com.
- **Atributo de endereço de e-mail do AAD** – Como é gerado o endereço de e-mail do utilizador em cada dispositivo. Selecione **Endereço SMTP Principal** para utilizar o endereço SMTP principal para iniciar sessão no Exchange ou selecione **Nome Principal de Utilizador** para utilizar o nome principal completo como o endereço de e-mail.
- **Método de autenticação** – Selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como método de autenticação utilizado pelo perfil de e-mail.
    - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente que servirá para autenticar a ligação ao Exchange.

## <a name="security-settings"></a>Definições de segurança

- **SSL** – Utilize a comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange Server.
- **S/MIME** – Envie e-mails com a encriptação S/MIME.
    - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente que servirá para autenticar a ligação ao Exchange.

## <a name="synchronization-settings"></a>Definições de sincronização

- **Quantidade de e-mails a sincronizar** – Selecione o número de dias de e-mail que pretende sincronizar ou selecione **Sem limite** para sincronizar todos os e-mails disponíveis.
- **Agenda de sincronização** – Selecione o agendamento através do qual os dispositivos irão sincronizar os dados do servidor Exchange. Também pode selecionar **Quando chegarem mensagens**, que sincroniza os dados assim que chegam, ou **Manual**, em que o utilizador do dispositivo tem de iniciar a sincronização.

## <a name="content-sync-settings"></a>Definições de sincronização de conteúdo

- **Tipo de conteúdo a sincronizar** – Selecione os tipos de conteúdo que pretende sincronizar nos dispositivos a partir de:
    - **Contactos**
    - **Calendário**
    - **Tarefas**



<!--HONumber=Feb17_HO1-->


