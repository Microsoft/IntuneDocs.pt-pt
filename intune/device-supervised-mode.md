---
title: Ativar o modo supervisionado do iOS com o Intune
titlesuffix: Azure portal
description: Saiba como ativar o modo supervisionado do iOS com o Intune.
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/15/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8190814-07f0-42d8-9b3a-87c67dd2b7ed
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ea93e7d3f2f55b002037fdcabf21fa0ed2cfc7c3
ms.sourcegitcommit: 6d69403266dbcb31c879432719798935c94917fa
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/19/2018
---
# <a name="turn-on-ios-supervised-mode"></a>Ativar o modo supervisionado do iOS


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O modo supervisionado do iOS da Apple dá mais opções aos administradores para gerirem dispositivos da Apple. É útil para dispositivos pertencentes à empresa e implementados em escala. Por exemplo, pode restringir o AirDrop ou impedir que os utilizadores alterem o nome do dispositivo. Para obter uma lista das definições que exigem o modo supervisionado, veja [Definições de restrição de dispositivos iOS no Microsoft Intune](device-restrictions-ios.md).

O Intune suporta o modo supervisionado como parte do [Programa de Registo de Aparelho (DEP)](device-enrollment-program-enroll-ios.md) da Apple.

Para obter uma lista dos controlos da Apple que exigem o modo supervisionado, veja [Payload settings reference (Referência de definições de payload)](http://help.apple.com/configurator/mac/2.4/#/cad5370d089) da Apple.

## <a name="turn-on-supervised-mode-during-enrollment"></a>Ativar o modo supervisionado durante a inscrição

No Intune, pode ativar o modo supervisionado para dispositivos ao [criar um perfil de inscrição da Apple no DEP](https://docs.microsoft.com/en-us/intune/device-enrollment-program-enroll-ios#create-an-apple-enrollment-profile). Em **Definições da Gestão de Dispositivos**, selecione a caixa de verificação **Supervisionado**.

## <a name="turn-on-supervised-mode-after-enrollment"></a>Ativar o modo supervisionado após a inscrição

Após a inscrição, a única forma de ativar o modo supervisionado é ao ligar um dispositivo iOS a um Mac e [utilizar o Apple Configurator](apple-configurator-enroll-ios.md) (que irá repor o dispositivo). Não pode configurar um dispositivo com o modo Supervisionado no Intune após a inscrição.

## <a name="identify-a-supervised-device"></a>Identificar um dispositivo supervisionado

Para determinar se um dispositivo é supervisionado, consulte o ecrã de bloqueio ou a página **Acerca de**:
- No ecrã de bloqueio do dispositivo, estará escrito **Este iPhone é gerido pela "Nome da Empresa".**
- Na página **Acerca de**, estará escrito **Este iPhone é supervisionado. A empresa consegue monitorizar o seu tráfego de Internet e localizar este dispositivo.**

## <a name="next-steps"></a>Próximos passos

Para saber mais sobre outras opções de gestão de dispositivos, veja [O que é a gestão de dispositivos do Microsoft Intune?](device-management.md)
