---
title: Inscrever dispositivos Android no Intune
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como inscrever dispositivos Android na pré-visualização do Azure no Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: b2cbabea781840df0a2a283f803dc76520590aba
ms.lasthandoff: 04/19/2017


---

# <a name="enroll-android-devices"></a>Inscrever dispositivos Android

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

O Intune permite-lhe gerir dispositivos Android, incluindo dispositivos Samsung Knox Standard. Para ativar a gestão de dispositivos, os seus utilizadores têm de inscrever os dispositivos deles ao transferir a aplicação Portal da Empresa do Intune disponível no Google Play e, em seguida, ao abrir a aplicação e seguir as instruções de inscrição. Assim que os dispositivos Android estiverem a ser geridos, pode [criar políticas de conformidade](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android), [gerir aplicações](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-management) e muito mais.

Os dispositivos que executem o Samsung KNOX Standard agora suportam a gestão de vários utilizadores do Intune. Deste modo, os utilizadores finais podem iniciar e terminar sessão no dispositivo com as credenciais do Azure AD e o dispositivo será gerido centralmente quer esteja a ser utilizado ou não. Quando os utilizadores finais iniciam sessão, têm acesso às aplicações e obtêm as políticas aplicadas às mesmas. Quando os utilizadores terminam sessão, todos os dados das aplicações são limpos.

## <a name="prerequisite"></a>Pré-requisito

Tem de definir a autoridade de MDM **Microsoft Intune** para se preparar para gerir dispositivos móveis. Veja [Set the MDM authority (Definir a autoridade de MDM)](set-mdm-authority.md) para obter instruções. Este item só é definido uma vez, quando está a configurar pela primeira vez o Intune para gestão de dispositivos móveis, pelo que é provável que já o tenha feito.

## <a name="set-up-android-enrollment"></a>Configurar inscrição do Android

Por predefinição, o Intune permite a inscrição de dispositivos Android e Samsung Knox Standard.

Para impedir a inscrição de dispositivos Android ou apenas de dispositivos Android pessoais, veja [Set device type restrictions (Definir restrições de tipos de dispositivos)](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions).

Para definir o máximo de dispositivos que um utilizador pode inscrever, veja [Set device limit restrictions (Definir restrições de limite de dispositivos)](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-limit-restrictions).

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indicar aos utilizadores como devem inscrever os dispositivos para acederem aos recursos da empresa

Terá de indicar aos utilizadores finais para acederem ao Google Play para transferir a aplicação Portal da Empresa do Intune e, em seguida, para abrirem a aplicação e seguirem as instruções para inscrever os seus dispositivos. A aplicação guia os utilizadores ao longo do processo de inscrição ao explicar aquilo que os utilizadores podem esperar e que os administradores de TI poderão ver ou não nos seus dispositivos.

Também poderá enviar-lhes uma ligação para os passos de inscrição online: [Inscrever o seu dispositivo Android no Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android).

Para obter informações sobre outras tarefas do utilizador final, veja estes artigos:

- [Recursos sobre a experiência do utilizador final com o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)
- [Utilizar o dispositivo Android com o Intune](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)

