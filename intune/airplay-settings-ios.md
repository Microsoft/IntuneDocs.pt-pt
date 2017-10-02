---
title: "Definições do AirPlay do Intune para dispositivos iOS"
titlesuffix: Azure portal
description: "Saiba como pode utilizar o Intune para ajudar a ligar automaticamente os dispositivos iOS a dispositivos compatíveis com o AirPlay."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ff64e8657d65ea8e233cde8d3e3219d2bdab6ce7
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/15/2017
---
# <a name="intune-airplay-settings-for-ios-devices"></a>Definições do AirPlay do Intune para dispositivos iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize estas definições para ajudar a ligar os dispositivos iOS que gere a dispositivos compatíveis com o AirPlay (tal como a Apple TV) na sua rede.
Com esta funcionalidade, pode:

- **Configurar uma lista de dispositivos e palavras-passe** – Permite que os utilizadores se liguem automaticamente aos dispositivos AirPlay que estão no intervalo. Forneça-lhes o nome e a palavra-passe dos dispositivos AirPlay para que não precisem de indicá-los quando se ligam.
- **Configurar destinos permitidos** – configure uma lista de dispositivos AirPlay (por ID do dispositivo). Os utilizadores finais só podem ver e ligar-se a dispositivos listados (apenas para dispositivos supervisionados).

## <a name="get-started"></a>Introdução

1. No painel **Funcionalidades do dispositivo**, escolha **AirPlay**.
2. No painel **AirPlay**, escolha uma ou ambas as ações seguintes:

## <a name="configure-a-device-and-password-list"></a>Configurar uma lista de dispositivos e a palavra-passe

1. No painel **Palavras-passe**, introduza o **Nome do Dispositivo** e a **Palavra-passe** de um dispositivo AirPlay como, por exemplo, **Contoso Apple TV**.
2. Após introduzir os detalhes do dispositivo, clique em **Adicionar**. O dispositivo aparece na lista **Nome do Dispositivo**.
3. Continue a adicionar dispositivos. Quando terminar, escolha **OK**.


## <a name="configure-allowed-destinations"></a>Configurar destinos permitidos

1. No painel **Destinos permitidos (apenas supervisionados)**, introduza o **ID do Dispositivo** de um dispositivo AirPlay como, por exemplo, 52:46:CD:51:83:4C.
2. Depois de introduzir o ID do dispositivo, clique em **Adicionar**. O ID é apresentado na lista **ID do Dispositivo**.
3. Continue a adicionar dispositivos. Quando terminar, escolha **OK**.

Também pode importar o dispositivo, as palavras-passe e os destinos permitidos a partir de um ficheiro de valores separados por vírgulas (csv).


## <a name="next-steps"></a>Próximos passos

Agora pode atribuir o perfil do dispositivo aos grupos que selecionar. Para obter detalhes, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).

