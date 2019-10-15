---
title: Armazenamento e processamento de dados no Intune
titleSuffix: Microsoft Intune
description: Saiba como os dados pessoais são armazenados e processados no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: edb07842-6a16-482e-8c1d-541a29e169a8
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c9a8bd5888ab0977d1ca553d059c1e96cccda75
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306895"
---
# <a name="data-storage-and-processing-in-intune"></a>Armazenamento e processamento de dados no Intune

Depois que [o Intune coleta os dados, o](privacy-data-collect.md)armazenamento e o processamento desses dados prosseguem conforme detalhado abaixo.

## <a name="storing-personal-data"></a>Armazenando dados pessoais

Todos os dados não telemétricos coletados são processados por meio do serviço do Intune e são armazenados em um ou mais dos seguintes locais de armazenamento: 

- SQLAzure 
- Coleções confiáveis (Service Fabric)  
- Storage do Azure 

A telemetria (logs de serviço, logs de desempenho, erros etc.) que são fundamentais para monitorar e fornecer um serviço estável são enviadas para armazenamentos de dados de telemetria da Microsoft.

### <a name="storage-locations"></a>Locais de armazenamento

A Microsoft oferece e opera serviços do Intune em muitas regiões em todo o mundo. O Intune respeita as eleições de local de armazenamento feitas pelo administrador para dados do cliente.

Para obter mais informações, consulte [onde os dados estão localizados?](https://www.microsoft.com/trust-center/privacy/data-location)

### <a name="personal-data-retention"></a>Retenção de dados pessoais

Em geral, os dados pessoais são retidos pelo Intune até 30 dias depois que o usuário é removido do gerenciamento do Intune.

Os dados de telemetria coletados como parte do uso do Intune são mantidos por um máximo de 30 dias.

Os logs de auditoria são mantidos por até um ano.

## <a name="processing-personal-data"></a>Processando dados pessoais

O Intune processa dados pessoais com sistemas de certificação ISO. Para obter mais informações, consulte o [portal de confiança do serviço](https://www.microsoft.com/en-us/TrustCenter/stp).

### <a name="profiling-and-marketing"></a>Criação de perfil e marketing

Microsoft Intune não usa nenhum dado pessoal coletado como parte do fornecimento do serviço para fins de criação de perfil ou marketing. 

### <a name="restrict-processing-of-personal-data"></a>Restringir o processamento de dados pessoais

Para restringir o processamento dos dados pessoais de um usuário, você pode excluir a conta de usuários:
1. Exportar uma cópia eletrônica dos dados pessoais do usuário, incluindo
    - accounts
    - dados de serviço
    - logs associados
2. Excluindo a conta do usuário e os dados associados do Intune.

## <a name="next-steps"></a>Passos seguintes

Saiba mais sobre como o Intune [protege e compartilha](privacy-data-secure-share.md) dados pessoais. 
