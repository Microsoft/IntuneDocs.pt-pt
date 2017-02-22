---
title: "Definições personalizadas do Intune para dispositivos Windows Phone 8.1 | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba quais são as definições que pode utilizar num perfil personalizado do Windows Phone 8.1."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 21c55041-3821-4a62-9f85-855b97dba269
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5ab494a3dd1e1bdea9703ab314574b192c5208ee
ms.openlocfilehash: 3656db2d9828dcc16c479ba072de691848fdd23b


---

# <a name="custom-settings-for-windows-phone-81-devices-in-intune-azure-preview"></a>Definições personalizadas para dispositivos Windows Phone 8.1 na pré-visualização do Azure no Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Utilize o perfil **Personalizado** para Windows Phone 8.1 do Microsoft Intune para implementar as definições OMA-URI que podem ser utilizadas para controlar funcionalidades nos dispositivos Windows Phone 8.1. Tratam-se de definições padrão utilizadas por inúmeros fabricantes de dispositivos móveis para controlar as funcionalidades dos dispositivos.

Esta capacidade destina-se a permitir a implementação de definições que não são configuráveis com outras políticas do Intune.

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Definições de políticas personalizadas para dispositivos Windows Phone 8.1

1. Utilize as instruções em [Como configurar definições personalizadas dos dispositivos no Microsoft Intune](how-to-configure-custom-settings.md) para começar.
2. No painel **Criar Perfil**, escolha **Definições** para adicionar uma ou mais definições OMA-URI.
3. No painel **Adicionar Linha**, configure os seguintes valores para cada definição:
    - **Nome** – Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.
    - **Descrição** – Introduza uma descrição geral da definição e outras informações relevantes para o ajudar a localizá-la.
    - **OMA-URI** – Especifique o OMA-URI para o qual pretende fornecer uma definição.
    - **Tipo de dados** – Selecione o tipo de dados em que especificará esta definição OMA-URI. Escolha entre **Cadeia**, **Data e hora**, **Número inteiro**, **Vírgula flutuante** ou **Booleano**.
    - **Valor** – Introduza o valor que quer associar ao OMA-URI que introduziu.

4. Clique em **OK** quando tiver terminado e, em seguida, continue a adicionar mais definições, conforme necessário.



<!--HONumber=Feb17_HO1-->


