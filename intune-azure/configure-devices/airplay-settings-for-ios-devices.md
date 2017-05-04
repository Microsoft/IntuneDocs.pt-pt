---
title: "Definições do AirPlay do Intune para dispositivos iOS"
titleSuffix: Intune Azure preview
description: "Saiba como pode utilizar o Intune para ajudar a ligar automaticamente os dispositivos iOS a dispositivos compatíveis com o AirPlay."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: f1f7aa6a0b441b51f20d104c4353a1542a9e01ad
ms.lasthandoff: 04/19/2017


---

# <a name="intune-airplay-settings-for-ios-devices"></a>Definições do AirPlay do Intune para dispositivos iOS

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Utilize estas definições para ajudar a ligar os dispositivos iOS que gere a dispositivos compatíveis com o AirPlay (tal como a Apple TV) na sua rede.
Com esta funcionalidade, pode:

- **Configurar uma lista de dispositivos e de palavras-passe** – aprovisione dispositivos com o nome e a palavra-passe de dispositivos AirPlay para permitir que estes se liguem automaticamente quando estiverem ao alcance. Se indicar uma palavra-passe, os utilizadores finais não precisam de a introduzir quando se ligam.
- **Configurar destinos permitidos** – configure uma lista de dispositivos AirPlay (por ID do dispositivo). Os utilizadores finais só poderão ver e estabelecer ligação aos dispositivos listados (apenas para dispositivos supervisionados).

## <a name="get-started"></a>Introdução

1. No painel **Funcionalidades do dispositivo**, escolha **AirPlay**.
2. No painel **AirPlay**, escolha uma ou ambas as ações seguintes:

## <a name="configure-a-device-and-password-list"></a>Configurar uma lista de dispositivos e a palavra-passe

1. No painel **Palavras-passe**, introduza o **Nome do Dispositivo** e a **Palavra-passe** de um dispositivo Airplay como, por exemplo, **Contoso Apple TV**.
2. Após introduzir os detalhes do dispositivo, clique em **Adicionar**. O dispositivo irá aparecer na lista **Nome do Dispositivo**.
3. Continue a adicionar dispositivos. Quando terminar, escolha **OK**.


## <a name="configure-allowed-destinations"></a>Configurar destinos permitidos

1. No painel **Destinos permitidos (apenas supervisionados)*, introduza o **ID do Dispositivo** de um dispositivo Airplay como, por exemplo, 52:46:CD:51:83:4C.
2. Depois de introduzir o ID do dispositivo, clique em **Adicionar**. O ID é apresentado na lista **ID do Dispositivo**.
3. Continue a adicionar dispositivos. Quando terminar, escolha **OK**.

Também pode importar o dispositivo, as palavras-passe e os destinos permitidos a partir de um ficheiro de valores separados por vírgulas (csv).



