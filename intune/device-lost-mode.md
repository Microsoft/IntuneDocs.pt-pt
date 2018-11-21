---
title: Ativar o modo perdido do iOS com o Microsoft Intune – Azure | Microsoft Docs
description: Ative ou inicie o modo perdido para personalizar uma mensagem que será apresentada no ecrã de bloqueio de um dispositivo iOS perdido ou roubado com o Microsoft Intune. Além disso, obtenha detalhes sobre as informações de segurança e privacidade quando utilizar a ação Modo perdido.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b708ed69817ca85dc6648242ceafbdfa25b91fc9
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180702"
---
# <a name="enable-lost-mode-on-ios-devices-with-intune"></a>Ativar o Modo Perdido em dispositivos iOS com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A ação de dispositivos **Modo perdido** ajuda-o a ativar o modo perdido em dispositivos iOS perdidos ou roubados. Este modo permite-lhe introduzir uma mensagem e um número de telefone que serão apresentados no ecrã de bloqueio do dispositivo. Para utilizar o modo perdido, o dispositivo tem de ser um dispositivo iOS pertencente à empresa que esteja num modo supervisionado.

## <a name="supported-platforms"></a>Plataformas suportadas

- iOS 9.3 e posterior

Esta funcionalidade não é suportada para os seguintes sistemas: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>Ativar o modo perdido

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Dispositivos** e, em seguida, selecione **Todos os dispositivos**.
4. Na lista de dispositivos que gere, selecione um dispositivo iOS e selecione **…Mais**. Em seguida, selecione a ação remota **Modo perdido**.
5. No **Modo perdido**, ative esta funcionalidade. Em seguida, introduza a mensagem a apresentar e um número de telefone de contacto.
6. Selecione **OK** para guardar as alterações.

Ao ativar o modo perdido, bloqueia qualquer utilização do dispositivo. O utilizador final não pode aceder ao dispositivo até desativar o modo perdido. Quando o modo perdido estiver ativado, utilize a ação [Localizar dispositivo](device-locate.md) para localizá-lo.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Informações de segurança e de privacidade das ações localizar dispositivo e modo perdido
- Nenhuma informação de localização do dispositivo é enviada para o Intune até ativar esta ação.
- Quando utiliza a ação localizar dispositivo, as coordenadas de latitude e longitude do dispositivo são enviadas para o Intune e apresentadas no portal do Azure.
- Os dados são armazenados durante 24 horas e, em seguida, são removidos. Não pode remover manualmente os dados de localização.
- Os dados de localização são encriptados quando são armazenados e, igualmente, quando estão a ser transmitidos.
- Na mensagem que introduzir para apresentar no ecrã de bloqueio, não se esqueça de incluir detalhes específicos para devolver o dispositivo perdido.

## <a name="next-steps"></a>Passos Seguintes

Para ver o estado de ativação da funcionalidade Modo perdido, aceda a **Dispositivos** e selecione **Ações do dispositivo**.