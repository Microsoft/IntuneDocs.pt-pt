---
title: O dispositivo tem um certificado em falta | Documentos da Microsoft
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 01/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: df973b18-9166-417d-8aa3-49edd2bda256
searchScope:
- User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: c42e2ee0e4ebf7e2b2bdf7ec5eba8a73b953e867
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="your-android-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone"></a>Está em falta um certificado no seu dispositivo Android que, geralmente, vem instalado no telemóvel

Se o dispositivo não estiver inscrito no Intune e não tiver um certificado que, geralmente, vem instalado no seu telemóvel, não poderá iniciar sessão na aplicação Portal da Empresa. Ao tentar iniciar sessão, verá a seguinte mensagem:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Pode corrigir este problema ao obter o certificado necessário a partir da [página de certificados da Digicert](https://www.digicert.com/digicert-root-certificates.htm).

1. Localize e transfira o certificado __Baltimore CyberTrust Root__. Também o pode transferir diretamente [aqui](https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt).

2. Arraste para baixo a partir da parte superior do ecrã para mostrar a lista das suas notificações recentes e toque em **BaltimoreCyberTrustRoot.crt**.

3. O seu dispositivo irá pedir-lhe para **Dar um Nome ao Certificado**. Não altere o nome predefinido do certificado que é apresentado.

4. Certifique-se de que a **Utilização da Credencial** está definida como **Utilizada para VPN e aplicações** e, em seguida, toque em **OK**.

    ![screenshot-certificate-name-dialog-showing-baltimore-certificate-name](./media/andr-cert_install-2-add_cert_name.png)

5. Feche o seu browser e a aplicação Portal da Empresa.

6. Reabra a aplicação Portal da Empresa. Agora deverá conseguir iniciar sessão na aplicação Portal da Empresa. Se ainda assim não conseguir utilizar a aplicação Portal da Empresa, contacte o suporte da empresa através das informações fornecidas no [site do Portal da Empresa](https://portal.manage.microsoft.com#HelpDeskDialog) para obter mais instruções.

>[!NOTE]
> Se instalar esse certificado não resolver o problema e vir uma mensagem a indicar que tem um "certificado em falta", precisará de executar passos adicionais para [instalar o certificado em falta](your-device-is-missing-an-IT-required-certificate-android.md).

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
