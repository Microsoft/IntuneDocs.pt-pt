---
title: Ativar o iOS/iPadOS perdeu o modo com o Microsoft Intune - Azure  Microsoft Docs
description: Ligue ou comece a perder o modo para personalizar uma mensagem que aparece no ecrã de bloqueio de um dispositivo iOS/iPadOS perdido ou roubado utilizando o Microsoft Intune. Além disso, obtenha detalhes sobre as informações de segurança e privacidade quando utilizar a ação Modo perdido.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96e037b3d4bcec09765a0228e4f35041fe316cf6
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782180"
---
# <a name="enable-lost-mode-on-iosipados-devices-with-intune"></a>Ativar o modo perdido nos dispositivos iOS/iPadOS com Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A ação do dispositivo **lost** ajuda-o a ativar o modo perdido em dispositivos iOS/iPadOS perdidos ou roubados. Este modo permite-lhe introduzir uma mensagem e um número de telefone que serão apresentados no ecrã de bloqueio do dispositivo. Para utilizar o modo perdido, o dispositivo deve ser um dispositivo iOS/iPadOS de propriedade corporativa que esteja em modo supervisionado.

## <a name="supported-platforms"></a>Plataformas suportadas

- iOS 9.3 e posterior
- iPadOS 13.0 ou mais tarde

Esta funcionalidade não é suportada para os seguintes sistemas: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>Ativar o modo perdido

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **Dispositivos** e, em seguida, selecione **Todos os dispositivos**.
4. A partir da lista de dispositivos que gere, escolha um dispositivo iOS/iPadOS e, em seguida, escolha o **modo Perdido (apenas supervisionado)** .
5. No **modo Perdido,** selecione **Ativar**.
6. Na **Mensagem para visualizar no ecrã de bloqueio,** escreva uma mensagem para visualizar no ecrã de bloqueio do dispositivo.
7. Opcionalmente, introduza um número de telefone no número de telefone para a caixa **de visualização.**
6. Selecione **OK** para guardar as alterações.

Ao ativar o modo perdido, bloqueia qualquer utilização do dispositivo. O utilizador final não pode aceder ao dispositivo até desativar o modo perdido. Quando o modo perdido estiver ativado, utilize a ação [Localizar dispositivo](device-locate.md) para localizá-lo.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Informações de segurança e de privacidade das ações localizar dispositivo e modo perdido
- Nenhuma informação de localização do dispositivo é enviada para o Intune até ativar esta ação.
- Quando utiliza a ação localizar dispositivo, as coordenadas de latitude e longitude do dispositivo são enviadas para o Intune e apresentadas no portal do Azure.
- Os dados são armazenados durante 24 horas e, em seguida, são removidos. Não pode remover manualmente os dados de localização.
- Os dados de localização são encriptados quando são armazenados e, igualmente, quando estão a ser transmitidos.
- Na mensagem que introduzir para apresentar no ecrã de bloqueio, não se esqueça de incluir detalhes específicos para devolver o dispositivo perdido.

## <a name="next-steps"></a>Próximos passos

Para ver o estado de ativação da funcionalidade Modo perdido, aceda a **Dispositivos** e selecione **Ações do dispositivo**.
