---
title: Localizar dispositivos iOS perdidos com o Intune
titlesuffix: Azure portal
description: Saiba como localizar dispositivos iOS perdidos ou roubados com o Intune. "
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 864d528091de7a6113485347304b0dc254af2c7d
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/23/2018
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Localizar dispositivos iOS perdidos ou roubados com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A ação de dispositivos **Localizar Dispositivo** apresenta a localização de um dispositivo iOS perdido ou roubado num mapa. O dispositivo tem de ser um dispositivo iOS pertencente à empresa, inscrito através do DEP, que esteja no modo supervisionado. Para utilizar esta ação, o dispositivo tem de ter o [modo perdido](device-lost-mode.md) ativado.

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – não suportado
- Windows Phone – não suportado
- iOS – suportado no iOS 9.3 e posterior (no Modo perdido), supervisionado e pertencente à empresa
- macOS – não suportado
- Android – não suportado

## <a name="how-to-locate-a-lost-or-stolen-device"></a>Como localizar um dispositivo perdido ou roubado

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, selecione um dispositivo iOS, selecione **...Mais** e, em seguida, selecione a ação remota **Localizar dispositivo**.
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


## <a name="next-steps"></a>Passos seguintes

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos**, selecione **Ações do dispositivo**.