---
title: "Definições personalizadas do Intune para dispositivos Windows Phone 8.1"
titleSuffix: Azure portal
description: "Saiba quais são as definições que pode utilizar num perfil personalizado do Windows Phone 8.1.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 21c55041-3821-4a62-9f85-855b97dba269
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 566037e507e6344187acb6528b2db86a82e28937
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="custom-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>Definições personalizadas para dispositivos Windows Phone 8.1 no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize o perfil **Personalizado** para Windows Phone 8.1 do Microsoft Intune para atribuir as definições OMA-URI que podem ser utilizadas para controlar as funcionalidades nos dispositivos Windows Phone 8.1. Tratam-se de definições padrão utilizadas por inúmeros fabricantes de dispositivos móveis para controlar as funcionalidades dos dispositivos.

Esta capacidade destina-se a permitir a atribuição de definições que não são configuráveis com outras políticas do Intune.

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Definições de políticas personalizadas para dispositivos Windows Phone 8.1

1. Utilize as instruções em [Como configurar definições personalizadas dos dispositivos no Microsoft Intune](custom-settings-configure.md) para começar.
2. No painel **Criar Perfil**, escolha **Definições** para adicionar uma ou mais definições OMA-URI.
3. No painel **Adicionar Linha**, configure os seguintes valores para cada definição:
    - **Nome** – Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.
    - **Descrição** – Introduza uma descrição geral da definição e outras informações relevantes para o ajudar a localizá-la.
    - **OMA-URI** – Especifique o OMA-URI para o qual pretende fornecer uma definição.
    - **Tipo de dados** – Selecione o tipo de dados em que especificará esta definição OMA-URI. Escolha entre **Cadeia**, **Data e hora**, **Número inteiro**, **Vírgula flutuante** ou **Booleano**.
    - **Valor** – Introduza o valor que quer associar ao OMA-URI que introduziu.

4. Clique em **OK** quando tiver terminado e, em seguida, continue a adicionar mais definições, conforme necessário.
