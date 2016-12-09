---
title: Recolher registos de dispositivos | Microsoft Intune
description: Saiba como recolher registos dos seus dispositivos geridos.
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 11/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0c05b4e16f7b0a87215a0cd20f7d559cd8497296
ms.openlocfilehash: 0f175b1eb2d80a68c8b7864d21f5a9e585de458b


---

# <a name="device-logs"></a>Registos de dispositivos

Como parte dos seus esforços de resolução de problemas, pode pretender recolher registos de dispositivos de utilizador. As instruções para recolher esses registos são aqui descritas. Normalmente, precisa de aceder ao dispositivo para obter esses registos ou pedir ao utilizador que recolha os registos e os envie para si.

### <a name="android-logs"></a>Registos de Android
Os registos Android estão localizados em *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*.

Por vezes os ficheiros não são apresentados, especialmente nos dispositivos Android mais recentes. Se isso acontecer, solicite aos seus utilizadores para abrirem a aplicação do Portal da Empresa para Android. Em seguida, devem escolher **Definições**>**Copiar Registos** e reiniciar o respetivo dispositivo.

Para obter mais informações sobre como os seus utilizadores finais podem enviar registos de dados, consulte os seguintes artigos:

- [Utilizar o Registo Verboso para ajudar o administrador de TI a corrigir problemas de dispositivos](/intune/enduser/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android): descreve a forma como os utilizadores podem ativar o Registo Verboso, que lhe envia automaticamente todos os registos de dados dos seus utilizadores. O registo verboso está ativado por predefinição.

- [Enviar registos de dados de diagnóstico ao administrador de TI por e-mail](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)

- [Enviar registos de dados de diagnóstico ao administrador de TI por cabo USB](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>Registos de iOS

Os utilizadores podem enviar-lhe os erros de inscrição, conforme descrito em [Enviar erros de inscrição de dispositivos iOS ao administrador de TI](/intune/enduser/send-errors-to-your-it-admin-ios).

### <a name="mac-os-x-logs"></a>Registos de Mac OS X

1. Abra a aplicação **Consola**.
2. Em **FICHEIROS**, escolha **system.log**.
3. Na barra de menus na parte superior, escolha **Ficheiro** > **Guardar uma Cópia Como...**. Em seguida, guarde o ficheiro.

### <a name="windows-phone"></a>Windows Phone

Na aplicação do Portal da Empresa do Windows Phone, os utilizadores escolhem as reticências (**…**) para aceder ao menu e, em seguida, escolhem **Enviar Registos**. Esta opção está disponível antes e depois de iniciar sessão na aplicação do Portal da Empresa.

### <a name="windows"></a>Windows

No Portal da Empresa do Windows, os registos estão localizados em *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.



<!--HONumber=Nov16_HO5-->


