---
title: Localizar dispositivos iOS perdidos com o Intune
titleSuffix: Intune on Azure
description: Saiba como localizar dispositivos iOS perdidos ou roubados com o Intune. "
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 80aa0e5afd1f8862b181d455ff6b545e462f90c9
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Localizar dispositivos iOS perdidos ou roubados com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A ação de dispositivos **Localizar Dispositivo** apresenta a localização de um dispositivo iOS perdido ou roubado num mapa. O dispositivo tem de ser um dispositivo iOS pertencente à empresa, inscrito através do DEP, que esteja no modo supervisionado. Para utilizar esta ação, o dispositivo tem de ter o [modo perdido](/intune-azure/manage-devices/lost-mode.md) ativado.

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo iOS e, em seguida, escolha a ação remota de dispositivos **Localizar Dispositivo**.
6. Depois de o dispositivo ser localizado, é apresentada a sua localização no painel **Localizar dispositivo**.
    ![Painel Localizar dispositivo](./media/locate-device.png)

>[!NOTE]
>Por motivos de privacidade, a ampliação do mapa é limitada.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Informações de segurança e de privacidade das ações localizar dispositivo e modo perdido
- Nenhuma informação de localização do dispositivo é enviada para o Intune até ativar esta ação.
- Quando utiliza a ação localizar dispositivo, as coordenadas de latitude e longitude do dispositivo são enviadas para o Intune e apresentadas no portal do Azure.
- Os dados são armazenados durante 24 horas e, em seguida, são removidos. Não pode remover manualmente os dados de localização.
- Os dados de localização são encriptados quando são armazenados e, igualmente, quando estão a ser transmitidos.
- Ao configurar o modo perdido, recomendamos que a mensagem que introduzir para ser apresentada no ecrã de bloqueio inclua informações que indiquem a quem encontrar o dispositivo para devolvê-lo.
