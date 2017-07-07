---
title: "Definições personalizadas do Intune para dispositivos Android"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba quais são as definições que pode utilizar num perfil personalizado do Android."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: ff3d3b1596f58213bed2509b1bfd5ae81c63f440
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="custom-settings-for-android-devices-in-microsoft-intune"></a>Definições personalizadas para dispositivos Android no Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Utilize o perfil **Personalizado** para Android do Microsoft Intune para atribuir as definições OMA-URI que podem servir para controlar as funcionalidades nos dispositivos Android. Tratam-se de definições padrão utilizadas por inúmeros fabricantes de dispositivos móveis para controlar as funcionalidades dos dispositivos.

Esta capacidade destina-se a permitir a atribuição de definições do Android que não são configuráveis com as políticas do Intune.

## <a name="custom-profile-settings-for-android-devices"></a>Definições de perfil personalizado para dispositivos Android

1. Utilize as instruções em [Como configurar definições personalizadas dos dispositivos no Microsoft Intune](custom-settings-configure.md) para começar.
2. No painel **Criar Perfil**, escolha **Definições** para adicionar uma ou mais definições OMA-URI.
3. No painel **Editar Linha**, configure os seguintes valores para cada definição:
    - **Nome** – Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.
    - **Descrição** – Introduza uma descrição geral da definição e outras informações relevantes para o ajudar a localizá-la.
    - **Tipo de dados** – Selecione o tipo de dados em que especificará esta definição OMA-URI. Escolha entre **Cadeia**, **Cadeia (XML)**, **Data e hora**, **Número inteiro**, **Vírgula flutuante** ou **Booleano**.
    - **OMA-URI** – Especifique o OMA-URI para o qual pretende fornecer uma definição.
    - **Valor** – Introduza o valor que quer associar ao OMA-URI que introduziu.
4. Clique em **OK** quando tiver terminado e, em seguida, continue a adicionar mais definições, conforme necessário.
