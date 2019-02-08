---
title: Dados que a Google envia para o Intune
titleSuffix: Microsoft Intune
description: Lista de dados que a Google envia para o Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c379c8db-788a-454e-9098-665ea3bc7b56
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 51c2d77fc4f25307b1817fe4c98db2a7f8f66901
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848428"
---
# <a name="data-google-sends-to-intune"></a>Dados que a Google envia para o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quando a gestão de dispositivos empresariais Android está ativada num dispositivo, o Microsoft Intune estabelece uma ligação com a Google e as informações do utilizador e do dispositivo são partilhadas entre o Intune e a Google. Antes de o Microsoft Intune poder estabelecer uma ligação, tem de criar uma conta Google.

A seguinte tabela lista os dados que a Google envia para o Intune quando a gestão de dispositivos está ativada num dispositivo:


| Dados que a Google envia para o Intune | Detalhes | Utilizado para | Exemplo |
|:---:|:---:|:---:|:---:|
| Dados empresariais | Identificadores empresariais do cliente na Google. | Associa as informações do cliente entre o Intune e a Google. | **enterpriseId** exemplo: LC04eik8a6.<br>**Nome**. O nome do Administrador tal como foi introduzido na configuração do Android Enterprise. Exemplo: João Silva.<br>**E-mail do administrador**. YourAdmin@gmail.com que foi utilizado durante a configuração do Android Enterprise. |
| Dados da aplicação | Dados para aplicações geridas da Play Store. | Direcionar a aplicação para utilizadores ou dispositivos como disponível ou obrigatória. | **Nome da aplicação** exemplo: Aplicação do inventário do armazém da Contoso.<br>Exemplo do **Identificador Exclusivo para representar a aplicação**: app:com.Contoso.Warehouse.InventoryTracking |
| Conta de serviço | Conta de serviço interna exclusiva da Google para utilização com as chamadas de um cliente específico. | Utilizada para fazer chamadas para a Google em nome do cliente (para ver as aplicações, os dispositivos e mais) | Exemplo de **Nome**: InternalAccount@InternalService.com.<br>**Chaves** exemplo: ServiceAccountPassword |


Para deixar de utilizar a gestão de dispositivos Android Enterprise com o Microsoft Intune e eliminar os dados, tem de desativar a gestão de dispositivos Android Enterprise do Microsoft Intune e eliminar a sua conta Google. Consulte a conta Google para saber como desempenhar a gestão da conta.


