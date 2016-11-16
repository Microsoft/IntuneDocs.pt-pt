<<<<<<< HEAD
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

||||||| merged common ancestors
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

=======
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
ms.sourcegitcommit: 19b0b502d2c8c261947c461f27a0e8153df5b186
ms.openlocfilehash: 1e65c1fa25e273ba03218f79ebeff611138e8013

>>>>>>> 7353fd98b7133f29a0609623f98f8455486209c3

---

# <a name="device-logs"></a>Registos de dispositivos

Como parte dos seus esforços de resolução de problemas, poderá pretender recolher registos de dispositivos de utilizador. As instruções para recolher esses registos são aqui descritas. Normalmente, poderá necessitar de aceder ao dispositivo ou pedir ao utilizador que recolha os registos e os envie para si.

### <a name="android-logs"></a>Registos de Android
Os registos Android estão localizados em *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*. 

Por vezes os ficheiros não são apresentados, especialmente nos dispositivos Android mais recentes. Se tal acontecer, peça aos seus utilizadores finais para abrirem a aplicação do Portal da Empresa para Android, acederem às **Definições**, selecionarem **Copiar Registos** e, em seguida, reiniciarem os respetivos dispositivos. 

Para obter mais informações sobre como os seus utilizadores finais podem enviar registos de dados, consulte os seguintes artigos:

- [Utilizar o registo verboso para ajudar o administrador de TI a corrigir problemas de dispositivos](/intune/enduser/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) – descreve a forma como os utilizadores podem ativar o Registo Verboso, que lhe envia automaticamente todos os registos de dados dos seus utilizadores. O registo verboso está ativado por predefinição.

- [Enviar registos de dados de diagnóstico ao administrador de TI por e-mail](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android) 

- [Enviar registos de dados de diagnóstico ao administrador de TI por cabo USB](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>Registos de iOS

Os utilizadores podem enviar-lhe os erros de inscrição, conforme descrito em [Enviar erros de inscrição de dispositivos iOS ao administrador de TI](/intune/enduser/send-errors-to-your-it-admin-ios).

### <a name="mac-os-x-logs"></a>Registos de Mac OS X

1. Abra a aplicação **Consola**.
2. Em **FICHEIROS**, escolha **system.log**.
3. Na barra de menus na parte superior, selecione **Ficheiro** > **Guardar uma Cópia Como...** e guarde o ficheiro.

### <a name="windows-phone"></a>Windows Phone

Na aplicação do portal da empresa do Windows Phone os utilizadores selecionam **…** para aceder ao menu e, em seguida, escolher **Enviar Registos**. Esta opção está disponível antes e depois de iniciar sessão na aplicação do Portal da Empresa.

### <a name="windows"></a>Windows

<<<<<<< HEAD
Para o Portal da Empresa do Windows, os registos estão localizados em *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.

||||||| merged common ancestors
Para o Portal da Empresa do Windows, os registos estão localizados em *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.

=======
No Portal da Empresa do Windows, os registos estão localizados em *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.

>>>>>>> 7353fd98b7133f29a0609623f98f8455486209c3


<!--HONumber=Nov16_HO2-->


