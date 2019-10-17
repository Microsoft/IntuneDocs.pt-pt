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
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: edb07842-6a16-482e-8c1d-541a29e169a8
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 07a9232203c7d93eb1b9e81b962d2369e77b7421
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509041"
---
# <a name="data-storage-and-processing-in-intune"></a>Armazenamento e processamento de dados no Intune

Depois de o Intune [recolher os dados](privacy-data-collect.md), o armazenamento e processamento desses dados são feitos da forma descrita abaixo.

## <a name="storing-personal-data"></a>Armazenamento de dados pessoais

Todos os dados recolhidos que não sejam telemétricos são processados através do serviço do Intune e armazenados em uma ou mais das localizações de armazenamento seguintes: 

- SQLAzure 
- Coleções Fiáveis (Service Fabric)  
- Armazenamento do Azure 

A telemetria (registos de serviço, registos de desempenho, erros, etc.) que é essencial para a monitorização e o fornecimento de um serviço estável é enviada para os arquivos de dados telemétricos da Microsoft.

### <a name="storage-locations"></a>Localizações de armazenamento

A Microsoft disponibiliza e opera serviços do Intune em muitas regiões do mundo. O Intune respeita as escolhas do administrador quanto à localização de armazenamento dos Dados do Cliente.

Para obter mais informações, consulte [onde os dados estão localizados?](https://www.microsoft.com/trust-center/privacy/data-location)

### <a name="personal-data-retention"></a>Retenção de dados pessoais

Em geral, os dados pessoais são retidos pelo Intune até 30 dias depois que o usuário é removido do gerenciamento do Intune.

Os dados de telemetria coletados como parte do uso do Intune são mantidos por um máximo de 30 dias.

Os registos de auditoria são retidos por um período máximo de um ano.

## <a name="processing-personal-data"></a>Processamento de dados pessoais

O Intune processa os dados pessoais através de sistemas com certificação ISO. Para obter mais informações, veja o [Portal de Confiança do Serviço](https://www.microsoft.com/en-us/TrustCenter/stp).

### <a name="profiling-and-marketing"></a>Criação de perfis e marketing

O Microsoft Intune não utiliza os dados pessoais recolhidos como parte do fornecimento do serviço para efeitos de criação de perfis ou marketing. 

### <a name="restrict-processing-of-personal-data"></a>Restrição do processamento de dados pessoais

Para restringir o processamento de dados pessoais do utilizador, pode eliminar a conta do utilizador ao:
1. Exportar uma cópia eletrónica dos dados pessoais do utilizador, incluindo
    - contas
    - dados do serviço
    - registos associados
2. Eliminar a conta do utilizador e os dados associados do Intune.

## <a name="next-steps"></a>Próximos passos

Saiba mais sobre como o Intune [protege e partilha](privacy-data-secure-share.md) dados pessoais. 
