---
title: "Definições de e-mail no Intune para dispositivos iOS"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba mais sobre as definições do Intune que pode utilizar para configurar ligações de e-mail em dispositivos iOS."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9f0fa6af-3669-439a-bd0d-75d8b1a0b135
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 6f941247295761815804b2e91234ce664c90e06f
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="email-profile-settings-for-ios-devices-in-microsoft-intune"></a>Definições de perfis de e-mail para dispositivos iOS no Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]



- **Servidor de e-mail** – O nome de anfitrião do servidor Exchange.
- **Nome da conta** – O nome a apresentar para a conta de e-mail conforme irá aparecer aos utilizadores nos dispositivos.
- **Atributo de nome de utilizador do AAD** – Este é o atributo no Active Directory (AD) ou Azure AD que servirá para gerar o nome de utilizador para este perfil de e-mail. Selecione o **Endereço SMTP Principal**, como **user1@contoso.com**, ou o **Nome Principal de Utilizador**, como **user1** ou **user1@contoso.com**.
- **Atributo de endereço de e-mail do AAD** – Como é gerado o endereço de e-mail do utilizador em cada dispositivo. Selecione **Endereço SMTP Principal** para utilizar o endereço SMTP principal para iniciar sessão no Exchange ou selecione **Nome Principal de Utilizador** para utilizar o nome principal completo como o endereço de e-mail.
- **Método de autenticação** – Selecione **Nome de Utilizador e Palavra-passe** ou **Certificados** como método de autenticação utilizado pelo perfil de e-mail.
    - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente que servirá para autenticar a ligação ao Exchange.
- **SSL** – Utilize a comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange Server.
- **S/MIME** – Envie e-mails com uma assinatura S/MIME.
    - Se tiver selecionado **Certificado**, selecione um perfil de certificado SCEP ou PKCS de cliente criado anteriormente que servirá para autenticar a ligação ao Exchange.
- **Quantidade de e-mails a sincronizar** – Selecione o número de dias de e-mail que pretende sincronizar ou selecione **Sem Limite** para sincronizar todos os e-mails disponíveis.
- **Permitir que as mensagens sejam movidas para outras contas de e-mail** – Esta opção permite que os utilizadores movam mensagens de e-mail entre contas diferentes configuradas nos dispositivos.
- **Permitir o envio de e-mail a partir de aplicações de terceiros** – Permita que o utilizador selecione este perfil como conta predefinida para o envio de e-mail e permita que as aplicações de terceiros abram o e-mail na aplicação de e-mail nativo, por exemplo, para anexar ficheiros ao e-mail.
- **Sincronizar endereços de e-mail recentemente utilizados** – Esta funcionalidade permite que os utilizadores sincronizem a lista de endereços de e-mail que foram recentemente utilizados no dispositivo com o servidor.

