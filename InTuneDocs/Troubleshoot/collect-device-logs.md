---
title: Recolher registos de dispositivos | Microsoft Intune
description: Saiba como recolher registos dos seus dispositivos geridos.
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3a081109cd499d3bdda75cb6c8a4dab9d9d28fab
ms.openlocfilehash: ec7d522e8dcff66d1b84fed3c4c0cc708e555e67


---

# <a name="device-logs"></a>Registos de dispositivos

Como parte dos seus esforços de resolução de problemas, poderá pretender recolher registos de dispositivos de utilizador. As instruções para recolher esses registos são aqui descritas. Normalmente, poderá necessitar de aceder ao dispositivo ou pedir ao utilizador que recolha os registos e os envie para si.

### <a name="android-log-location"></a>Localização de registo Android
Os registos Android estão localizados em *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*. O utilizador pode também enviar ficheiros de registo por e-mail, conforme descrito em [Enviar registos de dados de diagnóstico de dispositivos Android ao administrador de TI por e-mail](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android).

### <a name="ios-logs"></a>Registos de iOS

O utilizador pode enviar-lhe os erros de inscrição, conforme descrito em [Enviar erros de inscrição de dispositivos iOS ao administrador de TI](/intune/enduser/send-errors-to-your-it-admin-ios)

### <a name="mac-os-x-devices"></a>Dispositivos Mac OS X

1. Abra a aplicação **Consola**.
2. Em **FICHEIROS**, escolha **system.log**.
3. Na barra de menus na parte superior, selecione **Ficheiro** > **Guardar uma Cópia Como...** e guarde o ficheiro.

### <a name="windows-phone"></a>Windows Phone

No **Portal da Empresa do Windows Phone**, o utilizador terá de escolher o **...** para aceder ao menu e, em seguida, escolher **Enviar Registos**. Esta opção está disponível antes e depois de iniciar sessão no portal.

### <a name="windows"></a>Windows

Para o Portal da Empresa do Windows, os registos estão localizados em *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.



<!--HONumber=Oct16_HO3-->


