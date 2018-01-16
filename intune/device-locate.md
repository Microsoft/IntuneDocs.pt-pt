---
title: Localizar dispositivos iOS perdidos com o Intune
titlesuffix: Azure portal
description: Saiba como localizar dispositivos iOS perdidos ou roubados com o Intune. "
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 036ef508467e811b689393a157ada541fea70bcc
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/12/2018
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Localizar dispositivos iOS perdidos ou roubados com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A ação de dispositivos **Localizar Dispositivo** apresenta a localização de um dispositivo iOS perdido ou roubado num mapa. O dispositivo tem de ser um dispositivo iOS pertencente à empresa, inscrito através do DEP, que esteja no modo supervisionado. Para utilizar esta ação, o dispositivo tem de ter o [modo perdido](/intune-azure/manage-devices/lost-mode.md) ativado.

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – não suportado
- Windows Phone – não suportado
- iOS – suportado no iOS 9.3 e posterior (no Modo perdido), supervisionado e pertencente à empresa
- macOS – não suportado
- Android – não suportado

## <a name="how-to-locate-a-lost-or-stolen-device"></a>Como localizar um dispositivo perdido ou roubado

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


## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.