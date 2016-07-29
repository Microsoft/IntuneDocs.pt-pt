---
title: Recolher registos de dispositivos | Microsoft Intune
description: 
keywords: 
author: Nbigman
manager: angrobe
ms.date: 06/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9915b275101e287498217c4f35e1c0e56d2425c2
ms.openlocfilehash: 46579569c33b50f4b19a62d83c1db5e0e304621b


---

# Registos de dispositivos

Como parte dos seus esforços de resolução de problemas, poderá pretender recolher registos de dispositivos de utilizador. As instruções para recolher esses registos são aqui descritas. Normalmente, poderá necessitar de aceder ao dispositivo ou pedir ao utilizador que recolha os registos e os envie para si.

### Localização de registo Android
Os registos Android estão localizados em *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*. O utilizador pode também enviar ficheiros de registo por e-mail, conforme descrito em [Enviar registos de dados de diagnóstico de dispositivos Android ao administrador de TI por e-mail](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android).

### Registos de iOS

O utilizador pode enviar-lhe os erros de inscrição, conforme descrito em [Enviar erros de inscrição de dispositivos iOS ao administrador de TI](/intune/enduser/send-errors-to-your-it-admin-ios)

### Dispositivos Mac OS X

1. Abra a aplicação **Consola**.
2. Em **FICHEIROS**, escolha **system.log**.
3. Na barra de menus na parte superior, selecione **Ficheiro** > **Guardar uma Cópia Como...** e guarde o ficheiro.

### Windows Phone

No **Portal da Empresa do Windows Phone**, o utilizador terá de escolher o **...** para aceder ao menu e, em seguida, escolher **Enviar Registos**. Esta opção está disponível antes e depois de iniciar sessão no portal.

### Windows

Para o Portal da Empresa do Windows, os registos estão localizados em *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.



<!--HONumber=Jul16_HO4-->


