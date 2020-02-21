---
title: Pontos finais de rede para implementações governamentais dos EUA - Microsoft Intune
titleSuffix: ''
description: Reveja os pontos finais do governo dos EUA para Intune.
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
ms.openlocfilehash: d7edf84ada3c84b7ad31748909ef81a877237fd5
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514477"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Pontos finais do governo dos EUA para a Microsoft Intune

Esta página lista os pontos finais do governo dos EUA necessários para configurações de procuração nas suas implementações intune.

Para gerir dispositivos protegidos por firewalls e servidores proxy, tem de ativar as comunicações para o Intune.

- O servidor proxy tem de suportar **HTTP (80)** e **HTTPS(443)** , porque os clientes do Intune utilizam ambos os protocolos
- Para certas tarefas (como transferir atualizações de software), o Intune necessita de acesso não autenticado do servidor proxy ao site manage.microsoft.com

Pode modificar as definições do servidor proxy em computadores cliente individuais. Também pode utilizar as definições da Política de Grupo para alterar as definições para todos os computadores cliente localizados atrás de um servidor proxy especificado.

Os dispositivos geridos requerem configurações que permitam a **Todos os Utilizadores** aceder a serviços através de firewalls.

Para obter mais informações sobre a inscrição automática do Windows 10 e o registo de dispositivos para clientes do governo dos EUA, consulte [a inscrição para dispositivos Windows](../enrollment/windows-enroll.md#windows-10-auto-enrollment-and-device-registration).

As tabelas que se seguem listam as portas e os serviços a que o cliente do Intune acede:

|**Ponto final**|**Endereço IP**|
|---------------------|-----------|
|*.manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>Cliente do Governo dos EUA designado pontos finais:
- Portal Azure: https:\//portal.azure.us/ 
- Escritório 365: https:\//portal.office365.us/ 
- Intune Company Portal: https:\//portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Pontos finais do serviço parceiro que Intune depende:
- Serviço AAD Sync: https:\//syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Evo STS: https:\//login.microsoftonline.us
- Procuração do diretório: https:\//directoryproxy.microsoftazure.us/DirectoryProxy.svc
- AAD Graph: https:\//directory.microsoftazure.us e https:\//graph.microsoftazure.us
- MS Graph: https:\//graph.microsoft.us
- ADRS: https:\//enterpriseregistration.microsoftonline.us

## <a name="windows-push-notification-services"></a>Serviços de Notificação push do Windows
Em dispositivos geridos pela Intune geridos através da utilização de Mobile Device Management (MDM), os Serviços de Notificação push do Windows (WNS) são necessários para ações do dispositivo e outras atividades imediatas. Para mais informações, consulte [Configurações de Firewall da Enterprise e Proxy para apoiar o tráfego wns](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)

## <a name="apple-device-network-information"></a>Informações da rede de dispositivos Apple

|**Usado para**|**Nome de anfitrião (endereço IP/sub-rede)**|**Protocolo**|**Porto**|
|------------|-----------|------------|-----------|
|Obter e apresentar o conteúdo de servidores da Apple|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br>\*.phobos.itunes-apple.com.akadns.net|HTTP|80|
|Comunicação com servidores APNS|#-courier.push.apple.com<br>'#' é um número aleatório de 0 a 50.|TCP|5223 e 443|
|Várias funções, incluindo aceder à internet, loja iTunes, loja de aplicações macOS, iCloud, mensagens, etc.|phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net|HTTP/HTTPS|80 ou 443|

Para obter mais informações, consulte:

- [Portas TCP e UDP utilizadas por produtos de software apple](https://support.apple.com/HT202944)
- [Sobre macOS, iOS/iPadOS e ligações de servidoriTunes e processos de fundo do iTunes](https://support.apple.com/HT201999)
- [Se os seus clientes macOS e iOS/iPadOS não estiverem a receber notificações push da Apple](https://support.apple.com/HT203609)

## <a name="next-steps"></a>Próximos passos
[Pontos finais da rede para Microsoft Intune](intune-endpoints.md)

