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
ms.openlocfilehash: c83b47e70a6ef7f5eedb032846398dd669379c5c
ms.sourcegitcommit: d8bcf1a427035138f7dfe1e4f8b3c971c773dcd8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/04/2019
ms.locfileid: "74819725"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Pontos de extremidade do governo dos EUA para Microsoft Intune

Esta página lista os pontos de extremidade do governo dos EUA necessários para as configurações de proxy em suas implantações do Intune.

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

## <a name="us-government-customer-designated-endpoints"></a>Pontos de extremidade designados pelo cliente do governo dos EUA:
- Portal do Azure: https:\//portal.azure.us/ 
- Office 365: https:\//portal.office365.us/ 
- Portal da Empresa do Intune: https:\//portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Pontos de extremidade de serviço do parceiro dos quais o Intune depende:
- Serviço de AAD Sync: https:\//syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- STS Evo: https:\//login.microsoftonline.us
- Proxy de diretório: https:\//directoryproxy.microsoftazure.us/DirectoryProxy.svc
- Grafo do AAD: https:\//directory.microsoftazure.us e https:\//graph.microsoftazure.us
- MS Graph: https:\//graph.microsoft.us
- ADRS: https:\//enterpriseregistration.microsoftonline.us

## <a name="windows-push-notification-services"></a>Serviços de Notificação por Push do Windows (WNS)
Em dispositivos gerenciados pelo Intune gerenciados usando o MDM (gerenciamento de dispositivo móvel), o WNS (Windows PUsh Notification Services) é necessário para ações de dispositivo e outras atividades imediatas. Para obter mais informações, consulte [configurações de proxy e firewall corporativo para dar suporte ao tráfego WNS](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)

## <a name="apple-device-network-information"></a>Informações da rede de dispositivos Apple

|**Utilizado para**|**Nome do host (endereço IP/sub-rede)**|**Protocolo**|**Porta**|
|------------|-----------|------------|-----------|
|Obter e apresentar o conteúdo de servidores da Apple|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br>\*.phobos.itunes-apple.com.akadns.net|HTTP|80|
|Comunicação com servidores APNS|#-courier.push.apple.com<br>'#' é um número aleatório de 0 a 50.|TCP|5223 e 443|
|Várias funções, incluindo o acesso à Internet, à iTunes Store, ao macOS App Store, iCloud, sistema de mensagens etc.|phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net|HTTP/HTTPS|80 ou 443|

Para obter mais informações, consulte:

- [Portas TCP e UDP usadas por produtos de software da Apple](https://support.apple.com/HT202944)
- [Sobre conexões de host do macOS, iOS e iTunes Server e processos em segundo plano do iTunes](https://support.apple.com/HT201999)
- [Se seus clientes macOS e iOS não estiverem obtendo notificações por push da Apple](https://support.apple.com/HT203609)

## <a name="next-steps"></a>Próximos passos
[Pontos de extremidade de rede para Microsoft Intune](intune-endpoints.md)