---
title: Localizar dispositivos iOS perdidos com o Microsoft Intune – Azure | Microsoft Docs
description: Localize dispositivos iOS que foram perdidos ou roubados com a funcionalidade de localização de dispositivos no Microsoft Intune. Obtenha detalhes sobre as informações de segurança e privacidade ao utilizar a ação Localizar dispositivo.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/24/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c438ebeaae8a7259efb74089f51a6ca92003cfea
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509472"
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Localizar dispositivos iOS perdidos ou roubados com o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Para localizar um dispositivo iOS perdido ou roubado num mapa, utilize a ação **Localizar dispositivo**. O dispositivo tem de estar no modo supervisionado. Antes de utilizar esta ação, certifique-se de que o dispositivo está no [modo perdido](device-lost-mode.md).

## <a name="supported-platforms"></a>Plataformas suportadas

- iOS 9.3 e posterior

Esta funcionalidade não é suportada para os seguintes sistemas: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>Localizar um dispositivo perdido ou roubado

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Selecione **Dispositivos** e, em seguida, selecione **Todos os dispositivos**.
4. Na lista de dispositivos que gere, selecione um dispositivo iOS e selecione **…Mais**. Em seguida, selecione a ação remota **Localizar dispositivo**.
5. Após localizar o dispositivo, a localização dele é apresentada em **Localizar dispositivo**.
    ![Captura de ecrã da localização de um dispositivo com o Intune no Azure](./media/device-locate/locate-device.png)


## <a name="activate-lost-mode-sound-alert-on-an-ios-device"></a>Ativar o alerta de som do modo perdido num dispositivo iOS

Se um utilizar perder um dispositivo iOS 9.3 ou posterior, poderá acionar remotamente o dispositivo para reproduzir um som de alerta para que o utilizador o possa encontrar. O dispositivo tem de estar no [modo perdido](device-lost-mode.md).

No [Intune no portal do Azure](https://aka.ms/intuneportal), escolha **Dispositivos** > **Todos os dispositivos** > selecione um dispositivo iOS > **Descrição geral** > **Mais** > **Reproduzir som do Modo perdido (apenas supervisionar)** .

O som continuará a reproduzir até que o utilizador desative o som no dispositivo ou o dispositivo seja removido do modo perdido.


## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>Informações de segurança e privacidade para o modo perdido e ações de localização do dispositivo
- Nenhuma informação de localização do dispositivo é enviada para o Intune até ativar esta ação.
- Ao utilizar a ação Localizar dispositivo, as coordenadas de latitude e longitude do dispositivo podem ser obtidas através da Graph API.
- Os dados são armazenados durante 24 horas e, em seguida, são removidos. Não pode remover manualmente os dados de localização.
- Os dados de localização são encriptados quando são armazenados e, igualmente, quando estão a ser transmitidos.
- Ao configurar o modo perdido, pode personalizar uma mensagem que é apresentada no ecrã de bloqueio. Nesta mensagem, para ajudar a pessoa que encontrar o dispositivo, certifique-se de que inclui detalhes específicos sobre como devolver o dispositivo perdido.

## <a name="next-steps"></a>Próximos passos

Para ver o estado de ativação da ação Localizar Dispositivo, aceda a **Dispositivos** e selecione **Ações do dispositivo**.