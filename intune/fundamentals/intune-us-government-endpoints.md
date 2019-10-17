---
title: Pontos de extremidade de rede para implantações do governo dos EUA-Microsoft Intune
titleSuffix: ''
description: Examine os pontos de extremidade do governo dos EUA para o Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f6682cb-5fcd-4018-b7f7-71768ad3152e
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a5e52d1967ff6f5cf97334c099bc2b5b854ae87c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502695"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Pontos de extremidade do governo dos EUA para Microsoft Intune

Esta página lista os pontos de extremidade do governo dos EUA necessários para as configurações de proxy em suas implantações do Intune.

Para gerir dispositivos protegidos por firewalls e servidores proxy, tem de ativar as comunicações para o Intune.

- O servidor proxy tem de suportar **HTTP (80)** e **HTTPS(443)** , porque os clientes do Intune utilizam ambos os protocolos
- Para certas tarefas (como transferir atualizações de software), o Intune necessita de acesso não autenticado do servidor proxy ao site manage.microsoft.com

Pode modificar as definições do servidor proxy em computadores cliente individuais. Também pode utilizar as definições da Política de Grupo para alterar as definições para todos os computadores cliente localizados atrás de um servidor proxy especificado.

Os dispositivos geridos requerem configurações que permitam a **Todos os Utilizadores** aceder a serviços através de firewalls.

As tabelas que se seguem listam as portas e os serviços a que o cliente do Intune acede:

|**Extremidade**|**Endereço IP**|
|---------------------|-----------|
|*. manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>Pontos de extremidade designados pelo cliente do governo dos EUA:
- Portal do Azure: https: \//Portal. Azure. us/ 
- Office 365: https: \//Portal. office365. us/ 
- Portal da Empresa do Intune: https: \//Portal. Manage. Microsoft. us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Pontos de extremidade de serviço do parceiro dos quais o Intune depende:
- Serviço de AAD Sync: https: \//SyncService. gov. us. microsoftonline. com/DirectoryService. svc
- STS Evo: https: \//login. microsoftonline. us
- Proxy de diretório: https: \//directoryproxy. microsoftazure. us/DirectoryProxy. svc
- Grafo do AAD: https: \//Directory. microsoftazure. us e https: \//Graph. microsoftazure. us
- MS Graph: https: \//Graph. Microsoft. us
- ADRS: https: \//enterpriseregistration. microsoftonline. us
