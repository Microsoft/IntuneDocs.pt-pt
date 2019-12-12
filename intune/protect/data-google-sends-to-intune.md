---
title: Dados que a Google envia para o Intune
titleSuffix: Microsoft Intune
description: Lista de dados que a Google envia para o Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c379c8db-788a-454e-9098-665ea3bc7b56
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 914ce3aa15099b7692d524dbfa368f99f0d092e8
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504487"
---
# <a name="data-google-sends-to-intune"></a>Dados que a Google envia para o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Quando a gestão de dispositivos empresariais Android está ativada num dispositivo, o Microsoft Intune estabelece uma ligação com a Google e as informações do utilizador e do dispositivo são partilhadas entre o Intune e a Google. Antes de o Microsoft Intune poder estabelecer uma ligação, tem de criar uma conta Google.

A seguinte tabela lista os dados que a Google envia para o Intune quando a gestão de dispositivos está ativada num dispositivo:


| Dados que a Google envia para o Intune | Details | Utilizado para | Exemplo |
|:---:|:---:|:---:|:---:|
| Dados empresariais | Identificadores empresariais do cliente na Google. | Associa as informações do cliente entre o Intune e a Google. | Exemplo de **enterpriseId**: LC04eik8a6.<br>**Name (Nome)** . O nome do Administrador tal como foi introduzido na configuração do Android Enterprise. Exemplo: João Silva.<br>**E-mail do administrador**. YourAdmin@gmail.com que foi utilizado durante a configuração do Android Enterprise. |
| Dados de aplicação | Dados para aplicações geridas da Play Store. | Direcionar a aplicação para utilizadores ou dispositivos como disponível ou obrigatória. | Exemplo do **Nome da Aplicação**: Aplicação do Inventário do Armazém da Contoso.<br>Exemplo do **Identificador Exclusivo para representar a aplicação**: app:com.Contoso.Warehouse.InventoryTracking |
| Conta de serviço | Conta de serviço interna exclusiva da Google para utilização com as chamadas de um cliente específico. | Utilizada para fazer chamadas para a Google em nome do cliente (para ver as aplicações, os dispositivos e mais) | Exemplo de **Nome**: InternalAccount@InternalService.com.<br>Exemplo de **Chaves**: ServiceAccountPassword |


Para deixar de utilizar a gestão de dispositivos Android Enterprise com o Microsoft Intune e eliminar os dados, tem de desativar a gestão de dispositivos Android Enterprise do Microsoft Intune e eliminar a sua conta Google. Consulte a conta Google para saber como desempenhar a gestão da conta.


