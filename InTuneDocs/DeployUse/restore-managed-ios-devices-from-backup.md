---
title: "Restaurar dispositivos iOS geridos pelo Intune a partir da cópia de segurança| Microsoft Intune"
description: "Forneça orientações aos utilizadores finais acerca de como voltarem a inscrever os respetivos dispositivos depois de os restaurarem a partir da cópia de segurança."
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 612b0954a81de1ee8d4a1e96c7440239437dec14
ms.openlocfilehash: 5fc4423f8fd0c5829be5fe6c96949e126991e430


---

# Restaurar dispositivos iOS geridos pelo Intune a partir da cópia de segurança

Existirão casos em que você ou os seus utilizadores irão precisar de restaurar um dispositivo iOS a partir de uma cópia de segurança, como quando um utilizador tem um dispositivo novo. Este tópico explica-lhe os passos adicionais que pode ter de efetuar para configurar a gestão do Intune após restaurar o dispositivo.

## Restaurar cópias de segurança no mesmo dispositivo

Caso a cópia de segurança esteja a ser restaurada para o mesmo dispositivo, o estado de inscrição desse dispositivo também será restaurado. Não é necessária qualquer ação adicional.

## Restaurar cópias de segurança em dispositivos diferentes

Caso a cópia de segurança esteja a ser restaurada num dispositivo diferente, o estado da inscrição não é automaticamente restaurado no novo dispositivo. Os utilizadores têm de seguir os passos de inscrição padrão na versão 2.1.22 ou posterior da aplicação Portal da Empresa para [inscreverem o respetivo dispositivo iOS no Intune](/Intune/EndUser/enroll-your-device-in-intune-ios).

> [!NOTE]
> Caso esteja a aplicar políticas de acesso condicional aos seus utilizadores finais, estes não conseguirão aceder ao e-mail empresarial até se voltarem a inscrever.

> [!TIP]
> Um exemplo de comunicação dos seus utilizadores pode ser o seguinte: para inscrever o seu novo dispositivo, certifique-se de que a versão da aplicação Portal da Empresa é a 2.1.22 ou posterior. Para verificar a versão, abra a aplicação Portal da Empresa, toque no botão Menu no canto superior direito e, em seguida, toque em Sobre. Se estiver a utilizar uma versão anterior, saia da aplicação Portal da Empresa e abra a App Store. Toque no botão Atualizações no canto inferior direito e, em seguida, toque no botão Atualizar junto ao item Portal da Empresa na lista. Quando a atualização for concluída, inicie a aplicação Portal da Empresa e [inscreva o seu dispositivo iOS no Intune](/Intune/EndUser/enroll-your-device-in-intune-ios).



<!--HONumber=Oct16_HO2-->


