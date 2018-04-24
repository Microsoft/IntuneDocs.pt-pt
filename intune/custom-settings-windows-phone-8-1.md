---
title: Definições personalizadas do Microsoft Intune para dispositivos com o Windows Phone 8.1
titleSuffix: ''
description: Saiba quais são as definições que pode utilizar num perfil personalizado do Windows Phone 8.1.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 83c123f3752680dbc7faca76aa525a0f035831d7
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-phone-81"></a>Definições do dispositivo personalizadas do Microsoft Intune para dispositivos com o Windows Phone 8.1

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilize o perfil **Personalizado** para Windows Phone 8.1 do Microsoft Intune para atribuir as definições OMA-URI que podem ser utilizadas para controlar as funcionalidades nos dispositivos Windows Phone 8.1. Tratam-se de definições padrão utilizadas por inúmeros fabricantes de dispositivos móveis para controlar as funcionalidades dos dispositivos.

Esta capacidade destina-se a permitir a atribuição de definições que não são configuráveis com outras políticas do Intune.

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Definições de políticas personalizadas para dispositivos Windows Phone 8.1

1. Utilize as instruções em [Como configurar definições personalizadas dos dispositivos no Microsoft Intune](custom-settings-configure.md) para começar.
2. No painel **Definições OMA-URI Personalizadas**, selecione **Adicionar** para adicionar uma ou mais definições OMA-URI.
3. No painel **Adicionar Linha**, configure os seguintes valores para cada definição:
    - **Nome** – Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.
    - **Descrição** – Introduza uma descrição geral da definição e outras informações relevantes para o ajudar a localizá-la.
    - **OMA-URI** – Especifique o OMA-URI para o qual pretende fornecer uma definição.
    - **Tipo de dados** – selecione o tipo de dados nos quais especificar esta definição OMA-URI. Selecione entre **Cadeia**, **Cadeia (XML)**, **Data e hora**, **Número inteiro**, **Vírgula flutuante**, **Booleano** ou **Base64**.
    - **Valor** – introduza o valor ou ficheiro que pretende associar ao OMA-URI que introduziu.

4. Clique em **OK** quando tiver terminado e, em seguida, continue a adicionar mais definições, conforme necessário.
