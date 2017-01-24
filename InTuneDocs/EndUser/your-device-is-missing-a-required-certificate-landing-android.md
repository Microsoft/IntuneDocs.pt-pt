---
title: "O dispositivo tem um certificado necessário em falta | Documentos da Microsoft"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 207297601634f390051a6345b96bf09e1d031747
ms.openlocfilehash: 6b37cede797f965b82c067b274517277d8597939

---


# <a name="your-device-is-missing-a-required-certificate"></a>O dispositivo tem um certificado necessário em falta

## <a name="whats-a-certificate"></a>O que é um certificado?

A [criptografia](https://technet.microsoft.com/en-us/library/cc962030.aspx) é a ciência de proteger as informações. A criptografia foi utilizada, tradicionalmente, para enviar mensagens em código para [assegurar que a comunicação é secreta](https://technet.microsoft.com/en-us/library/cc962019.aspx). Na sua forma mais simples, a criptografia substitui ou transpõe as letras para criar uma mensagem em código numa mensagem oculta, ilegível ou codificada. Só alguém com uma chave de descodificação ou um _certificado_ pode converter a mensagem novamente para a sua forma original e legível. Os seus dispositivos Android utilizam certificados no Intune para assegurar que as comunicações entre o seu dispositivo e os recursos da sua organização, como e-mails e documentos, são sempre mantidos em segurança desde o envio até à receção.

## <a name="fixing-certificate-issues"></a>Corrigir problemas de certificados

Se o seu dispositivo Android não estiver inscrito no Intune e não tiver um determinado certificado de que o administrador de TI necessita, não poderá iniciar sessão na aplicação Portal da Empresa. Ao tentar iniciar sessão, verá a seguinte mensagem:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

O primeiro passo que deve experimentar consiste em verificar se o seu dispositivo tem um [certificado em falta que geralmente vem pré-instalado](your-device-is-missing-a-preinstalled-certificate-android.md).

Se esta opção não funcionar, o seu administrador de TI pode [pedir-lhe para instalar um segundo certificado para uma segurança adicional](your-device-is-missing-an-IT-required-certificate-android.md).

Ainda precisa de ajuda? Contacte o administrador de TI. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](http://portal.manage.microsoft.com).



<!--HONumber=Jan17_HO2-->


