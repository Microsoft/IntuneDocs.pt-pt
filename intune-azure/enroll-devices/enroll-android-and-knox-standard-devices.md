---
title: "Inscrever dispositivos Android no Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como inscrever dispositivos Android na pré-visualização do Azure no Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: edd6303f3bb05dfff758cbb7d4bd08e21f083998


---

# <a name="enroll-android-devices"></a>Inscrever dispositivos Android

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Como administrador do Intune, pode ativar a gestão de dispositivos Android, incluindo dispositivos Samsung Knox Standard a partir do Portal da Empresa. Os utilizadores podem então inscrever os respetivos dispositivos com a aplicação Portal da Empresa disponível no Google Play.

## <a name="prerequisite"></a>Pré-requisito

Tem de definir a autoridade de MDM **Microsoft Intune** para se preparar para gerir dispositivos móveis. Veja [Set the MDM authority (Definir a autoridade de MDM)](set-mdm-authority.md) para obter instruções. Este item só é definido uma vez, quando está a configurar pela primeira vez o Intune para gestão de dispositivos móveis, pelo que é provável que já o tenha feito. 

## <a name="set-up-android-enrollment"></a>Configurar inscrição do Android

Por predefinição, o Intune é configurado para permitir a inscrição de dispositivos Android e Samsung Knox Standard. 

Para ver a definição para permitir ou bloquear a inscrição de dispositivos Android, aceda ao painel do Intune no portal do Azure e escolha **Inscrição** > **Restrições de Inscrição**. 

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indique aos utilizadores como devem inscrever os dispositivos para acederem aos recursos da empresa

Para obter instruções de inscrição do utilizador final, veja [Inscrever o dispositivo Android no Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android). O processo de inscrição informa os utilizadores sobre o que podem esperar e o que os administradores de TI podem e não podem ver nos respetivos dispositivos.

Para obter informações sobre outras tarefas do utilizador final, veja estes artigos:

- [Recursos sobre a experiência do utilizador final com o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [Utilizar o dispositivo Android com o Intune](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)


<!--HONumber=Feb17_HO1-->


