---
title: "O dispositivo tem um certificado necessário em falta | Documentos da Microsoft"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope:
- User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 7c454584df4f0eb6b3a9dfe10ee7b887bcdee2ca
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="your-device-is-missing-a-required-certificate"></a>O dispositivo tem um certificado necessário em falta

## <a name="whats-a-certificate"></a>O que é um certificado?

A [criptografia](https://technet.microsoft.com/library/cc962030.aspx) é a ciência de proteger as informações. A criptografia foi utilizada, tradicionalmente, para enviar mensagens em código para [assegurar que a comunicação é secreta](https://technet.microsoft.com/library/cc962019.aspx). Na sua forma mais simples, a criptografia substitui ou transpõe as letras para criar uma mensagem em código numa mensagem oculta, ilegível ou codificada. Só alguém com uma chave de descodificação ou um _certificado_ pode converter a mensagem novamente para a sua forma original e legível. Os seus dispositivos Android utilizam certificados no Intune para assegurar que as comunicações entre o seu dispositivo e os recursos da sua organização, como e-mails e documentos, são sempre mantidos em segurança desde o envio até à receção.

## <a name="fixing-certificate-issues"></a>Corrigir problemas de certificados

Se o seu dispositivo Android não estiver inscrito no Intune e não tiver um determinado certificado de que o suporte da empresa necessita, não poderá iniciar sessão na aplicação Portal da Empresa. Ao tentar iniciar sessão, verá a seguinte mensagem:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

O primeiro passo que deve experimentar consiste em verificar se o seu dispositivo tem um [certificado em falta que geralmente vem pré-instalado](your-device-is-missing-a-preinstalled-certificate-android.md).

Se esta opção não funcionar, o suporte da empresa poderá [pedir-lhe para instalar um segundo certificado para uma segurança adicional](your-device-is-missing-an-IT-required-certificate-android.md).

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
