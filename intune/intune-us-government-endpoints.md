---
title: Pontos finais de rede para implementações de administração pública dos EUA - Microsoft Intune
titleSuffix: ''
description: Reveja os pontos finais de administração pública dos EUA para o Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7a86069b7f4093fb437171d5699df2302fc6fd2a
ms.sourcegitcommit: df413d1786c9aa0f409424c1e9e102bf230bbe39
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66721697"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Pontos finais de administração pública dos EUA para o Microsoft Intune

Esta página apresenta uma lista de pontos de extremidade de Governo dos EUA, necessários para as definições de proxy das implementações do Intune.

Para gerir dispositivos protegidos por firewalls e servidores proxy, tem de ativar as comunicações para o Intune.

- O servidor proxy tem de suportar **HTTP (80)** e **HTTPS(443)** , porque os clientes do Intune utilizam ambos os protocolos
- Para certas tarefas (como transferir atualizações de software), o Intune necessita de acesso não autenticado do servidor proxy ao site manage.microsoft.com

Pode modificar as definições do servidor proxy em computadores cliente individuais. Também pode utilizar as definições da Política de Grupo para alterar as definições para todos os computadores cliente localizados atrás de um servidor proxy especificado.

Os dispositivos geridos requerem configurações que permitam a **Todos os Utilizadores** aceder a serviços através de firewalls.

As tabelas que se seguem listam as portas e os serviços a que o cliente do Intune acede:

|**Endpoint**|**Endereço IP**|
|---------------------|-----------|
|*.manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>Cliente do US Government designado pontos finais:
- Portal do Azure: https://portal.azure.us/ 
- Office 365: https://portal.office365.us/ 
- Portal da empresa do Intune: https://portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Parceiro pontos finais de serviço que depende do Intune:
- Serviço do AAD Sync: https://syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Evo STS: https://login.microsoftonline.us
- Proxy de diretório: https://directoryproxy.microsoftazure.us/DirectoryProxy.svc
- Graph do AAD: https://directory.microsoftazure.us e https://graph.microsoftazure.us
- Gráfico de MS: https://graph.microsoft.us
- ADRS: https://enterpriseregistration.microsoftonline.us
