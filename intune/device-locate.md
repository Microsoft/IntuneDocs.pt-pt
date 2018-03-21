---
title: "Localizar dispositivos iOS perdidos com o Microsoft Intune – Azure | Microsoft Docs"
description: "Localize dispositivos iOS perdidos ou roubados com a funcionalidade Localizar Dispositivo no Microsoft Intune e utilize-a para obter detalhes de segurança e informações de privacidade."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4bc51ef7f9af9cc97fd4c11408a1857679aee665
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Localizar dispositivos iOS perdidos ou roubados com o Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Para localizar um dispositivo iOS perdido ou roubado num mapa, utilize a ação **Localizar Dispositivo**. O dispositivo iOS tem de ser propriedade de uma empresa, tem de estar inscrito no programa de registo de aparelho (DEP) e tem de estar no modo supervisionado. Antes de utilizar esta ação, certifique-se de que o dispositivo está no [modo perdido](device-lost-mode.md).

## <a name="supported-platforms"></a>Plataformas suportadas

- iOS 9.3 e posterior

Esta funcionalidade **não** é suportada para os seguintes sistemas: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>Localizar um dispositivo perdido ou roubado

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Dispositivos** e, em seguida, selecione **Todos os dispositivos**.
4. Na lista de dispositivos que gere, selecione um dispositivo iOS, selecione **...Mais** e, em seguida, selecione a ação remota **Localizar dispositivo**.
5. Após localizar o dispositivo, a localização dele é apresentada em **Localizar dispositivo**.
    ![Localizar um dispositivo com o Intune no Azure](./media/locate-device.png)

>[!NOTE]
>Por motivos de privacidade, a ampliação do mapa é limitada.

## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>Informações de segurança e privacidade para o modo perdido e ações de localização do dispositivo
- Nenhuma informação de localização do dispositivo é enviada para o Intune até ativar esta ação.
- Quando utiliza a ação localizar dispositivo, as coordenadas de latitude e longitude do dispositivo são enviadas para o Intune e apresentadas no portal do Azure.
- Os dados são armazenados durante 24 horas e, em seguida, são removidos. Não pode remover manualmente os dados de localização.
- Os dados de localização são encriptados quando são armazenados e, igualmente, quando estão a ser transmitidos.
- Ao configurar o modo perdido, pode personalizar uma mensagem que é apresentada no ecrã de bloqueio. Nesta mensagem, para ajudar a pessoa que encontrar o dispositivo, certifique-se de que inclui detalhes específicos sobre como devolver o dispositivo perdido.

## <a name="next-steps"></a>Próximos passos

Para ver o estado de ativação da definição Localizar Dispositivo, aceda a **Dispositivos** e selecione **Ações do dispositivo**.
