---
title: Ativar o modo perdido para iOS com o Intune
titleSuffix: Intune on Azure
description: Saiba como utilizar o Intune para ativar o modo perdido em dispositivos iOS perdidos ou roubados.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a34d008ae76355578c6f24a932c9e1e501d5b46b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="activate-lost-mode-on-ios-devices"></a>Ativar o modo perdido em dispositivos iOS


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A ação de dispositivos **Modo perdido** ajuda-o a ativar o modo perdido em dispositivos iOS perdidos ou roubados. Este modo permite-lhe especificar uma mensagem e um número de telefone que serão apresentados no ecrã de bloqueio do dispositivo

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo iOS e, em seguida, escolha a ação remota de dispositivos **Modo perdido**.
6. No painel **Modo perdido**, ative o modo perdido, introduza a mensagem que será apresentada e, opcionalmente, um número de telefone de contacto.
7. Clique em **OK**.

Quando ativar o modo perdido, bloqueia qualquer utilização do dispositivo. O utilizador final não pode aceder ao dispositivo até desativar o modo perdido. Quando o modo perdido está ativado, pode utilizar a ação **Localizar dispositivo** para saber onde este se encontra.
Para utilizar o modo perdido, o dispositivo tem de ser um dispositivo iOS pertencente à empresa, inscrito através do DEP, que esteja no modo supervisionado.

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Informações de segurança e de privacidade das ações localizar dispositivo e modo perdido
- Nenhuma informação de localização do dispositivo é enviada para o Intune até ativar esta ação.
- Quando utiliza a ação localizar dispositivo, as coordenadas de latitude e longitude do dispositivo são enviadas para o Intune e apresentadas no portal do Azure.
- Os dados são armazenados durante 24 horas e, em seguida, são removidos. Não pode remover manualmente os dados de localização.
- Os dados de localização são encriptados quando são armazenados e, igualmente, quando estão a ser transmitidos.
- Ao configurar o modo perdido, recomendamos que a mensagem que introduzir para ser apresentada no ecrã de bloqueio inclua informações que indiquem a quem encontrar o dispositivo para devolvê-lo.

