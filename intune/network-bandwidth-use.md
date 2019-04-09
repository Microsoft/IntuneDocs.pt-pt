---
title: Detalhes de largura de banda e requisitos de rede do Microsoft Intune
titleSuffix: ''
description: Reveja os detalhes de largura de banda e requisitos de configuração de rede do Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9dca4dc0b0b93d8466835ce0518268a548f3174a
ms.sourcegitcommit: 9daaeba9a960c50efcc951856234fbfec3635737
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231759"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Largura de banda e requisitos de configuração de rede do Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Esta orientação ajuda os administradores do Intune a compreenderem os requisitos de rede do serviço Intune. Pode utilizar estas informações para compreender os requisitos de largura de banda e as definições de portas e endereços IP necessárias para as definições de proxy.

## <a name="average-network-traffic"></a>Tráfego de rede médio
A tabela lista o tamanho e frequência aproximados dos conteúdos comuns que circulam na rede para cada cliente.

> [!NOTE]
> Para garantir que os dispositivos recebem as atualizações e conteúdos do Intune, estes têm de ser regularmente ligados à Internet. O tempo necessário para receber as atualizações ou conteúdos pode variar, mas deverão manter uma ligação ininterrupta à Internet durante, pelo menos, uma hora por dia.

|Tipo de conteúdo|Tamanho aproximado|Frequência e detalhes|
|----------------|--------------------|-------------------------|
|Instalação do cliente Intune<br /><br />**São aplicáveis os seguintes requisitos, para além da instalação do cliente do Intune**|125 MB|**Uma vez**<br /><br />O tamanho da transferência do cliente varia consoante o sistema operativo do computador cliente.|
|Pacote de inscrição de clientes|15 MB|**Uma vez**<br /><br />São possíveis transferências adicionais quando existirem atualizações para este tipo de conteúdo.|
|Agente do Endpoint Protection|65 MB|**Uma vez**<br /><br />São possíveis transferências adicionais quando existirem atualizações para este tipo de conteúdo.|
|Agente do Operations Manager|11 MB|**Uma vez**<br /><br />São possíveis transferências adicionais quando existirem atualizações para este tipo de conteúdo.|
|Agente de políticas|3 MB|**Uma vez**<br /><br />São possíveis transferências adicionais quando existirem atualizações para este tipo de conteúdo.|
|Assistência Remota através do agente Microsoft Easy Assist|6 MB|**Uma vez**<br /><br />São possíveis transferências adicionais quando existirem atualizações para este tipo de conteúdo.|
|Operações diárias de clientes|6 MB|**Diariamente**<br /><br />O cliente do Intune comunica regularmente com o serviço do Intune para procurar atualizações e políticas e para comunicar o estado do cliente ao serviço.|
|Atualizações de definições de software maligno do Endpoint Protection|Varia<br /><br />Normalmente, entre 40 KB a 2 MB|**Diariamente**<br /><br />Até três vezes por dia.|
|Atualização do motor do Endpoint Protection|5 MB|**Mensalmente**|
|Atualizações de software|Varia<br /><br />O tamanho depende das atualizações que implementar.|**Mensalmente**<br /><br />Normalmente, as atualizações de software são lançadas na segunda terça-feira de cada mês.<br /><br />Um computador inscrito ou implementado recentemente pode utilizar mais largura de banda de rede ao transferir todas as atualizações lançadas anteriormente.|
|Service packs|Varia<br /><br />O tamanho varia consoante o service pack que implementar.|**Varia**<br /><br />Depende da altura em que implementar os service packs.|
|Distribuição de software|Varia<br /><br />O tamanho depende do software que implementar.|**Varia**<br /><br />Depende da altura em que implementar o software.|

## <a name="ways-to-reduce-network-bandwidth-use"></a>Formas de reduzir a utilização da largura de banda de rede
Pode utilizar um ou mais dos seguintes métodos para reduzir a utilização da largura de banda de rede dos clientes do Intune.

### <a name="use-a-proxy-server-to-cache-content-requests"></a>Utilizar um servidor proxy para colocar os pedidos de conteúdo em cache
Um servidor proxy pode colocar conteúdos em cache para reduzir as transferências em duplicado e reduzir a largura de banda de rede dos conteúdos da Internet.

Um servidor proxy de colocação em cache que recebe pedidos de conteúdo de clientes pode obter esses conteúdos e colocar em cache tanto as respostas Web como as transferências. O servidor utiliza os dados colocados em cache para responder a pedidos posteriores dos clientes.

Seguem-se as definições típicas para utilizar um servidor proxy que coloca conteúdos em cache para os clientes do Intune.


|          Definição           |           Valor recomendado           |                                                                                                  Detalhes                                                                                                  |
|----------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Tamanho da cache         |             De 5 GB até 30 GB             | O valor varia com base no número de computadores clientes na sua rede e nas configurações que utiliza. Para impedir que os ficheiros sejam eliminados demasiado cedo, ajuste o tamanho da cache do seu ambiente. |
| Tamanho do ficheiro de cache individual |                950 MB                 |                                                                     Esta definição pode não estar disponível em todos os servidores proxy com colocação em cache.                                                                     |
|   Tipos de objeto a colocar em cache    | HTTP<br /><br />HTTPS<br /><br />BITS |                                               Os pacotes Intune são ficheiros CAB obtidos através de uma transferência do Serviço de Transferência Inteligente em Segundo Plano (BITS) através de HTTP.                                               |

Para obter informações sobre como utilizar um servidor proxy para colocar conteúdos em cache, consulte a documentação da sua solução de servidor proxy.

### <a name="use-background-intelligent-transfer-service-bits-on-computers"></a>Utilizar o serviço de transferência inteligente em segundo plano (BITS) em computadores
Durante as horas que configurar, pode utilizar o BITS num computador Windows para reduzir a largura de banda de rede. Pode configurar uma política de BITS na **largura de banda de rede** página da política de agente do Intune.

Para saber mais sobre o BITS e computadores Windows, veja [Background Intelligent Transfer Service (Serviço de Transferência Inteligente em Segundo Plano)](http://technet.microsoft.com/library/bb968799.aspx) na Biblioteca TechNet.

### <a name="use-branchcache-on-computers"></a>Utilizar o BranchCache nos computadores
Os clientes Intune podem utilizar o BranchCache para reduzir o tráfego da rede alargada (WAN). O BranchCache é suportado pelos seguintes sistemas operativos:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Para utilizar o BranchCache, o computador cliente tem de ter o BranchCache ativado e, em seguida, ser configurado para o **modo de cache distribuída**.

Quando o cliente do Intune é instalado em computadores, BranchCache e o modo de cache distribuída são ativados por predefinição. No entanto, se a política de grupo tiver desativado o BranchCache, o Intune não substitui essa política e BranchCache permanece desativado.

Se utiliza o BranchCache, trabalhe em conjunto com outros administradores na sua organização para gerir a Política de Grupo e a política de Firewall do Intune. Certifique-se de que não implementam políticas que desativem o BranchCache ou exceções da Firewall. Para obter mais informações sobre o BranchCache, consulte [Descrição Geral do BranchCache](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Requisitos da comunicação de rede

Ative as comunicações de rede entre os dispositivos que gere e os pontos finais necessários para serviços baseados na nuvem.

Como um serviço apenas na cloud, o Intune não exige infraestrutura no local, como servidores ou gateways.

Para gerir dispositivos por trás de firewalls e servidores proxy, tem de ativar a comunicação do Intune.

- O servidor proxy tem de suportar **HTTP (80)** e **HTTPS(443)**, porque os clientes do Intune utilizam ambos os protocolos
- Para algumas tarefas (como transferir as atualizações de software), o Intune necessita de acesso ao servidor de proxy não autenticados para manage.microsoft.com

Pode modificar as definições do servidor proxy em computadores cliente individuais. Também pode utilizar as definições de política de grupo para alterar as definições para todos os computadores de cliente localizados atrás de um servidor de proxy especificado.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

Os dispositivos geridos requerem configurações que permitam a **Todos os Utilizadores** aceder a serviços através de firewalls.

As tabelas que se seguem listam as portas e os serviços a que o cliente do Intune acede:

|**Domínios**|**Endereço IP**|
|---------------------|-----------|
|login.microsoftonline.com | Mais informações em [Intervalos de endereços IP e URLs do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |52.175.12.209<br>20.188.107.228<br>52.138.193.149<br>51.144.161.187<br>52.160.70.20<br>52.168.54.64 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 40.83.123.72<br>13.76.177.110<br>52.169.9.87<br>52.174.26.23<br>104.40.82.191<br>13.82.96.212|
|fei.msua01.manage.microsoft.com<br>portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com<br>fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>fei.msua04.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.amsua0202.manage.microsoft.com <br>portal.fei.amsua0202.manage.microsoft.com <br>m.fei.amsua0202.manage.microsoft.com<br>fei.amsua0402.manage.microsoft.com <br>portal.fei.amsua0402.manage.microsoft.com <br>m.fei.amsua0402.manage.microsoft.com|52.160.70.20<br>52.168.54.64 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>fei.amsub0202.manage.microsoft.com <br>portal.fei.amsub0202.manage.microsoft.com <br>m.fei.amsub0202.manage.microsoft.com<br>fei.amsub0302.manage.microsoft.com <br>portal.fei.amsub0302.manage.microsoft.com <br>m.fei.amsub0302.manage.microsoft.com|52.138.193.149<br>51.144.161.187|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com|52.175.12.209<br>20.188.107.228|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|52.169.82.238|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
|fef.amsua0202.manage.microsoft.com|52.165.165.17|
|fef.amsua0402.manage.microsoft.com|40.69.157.122|
|fef.amsua0502.manage.microsoft.com|13.85.68.142|
|fef.amsua0602.manage.microsoft.com|52.161.28.64|
|fef.amsub0102.manage.microsoft.com|40.118.98.207|
|fef.amsub0202.manage.microsoft.com|40.69.208.122|
|fef.amsub0302.manage.microsoft.com|13.74.145.65|
|enterpriseregistration.windows.net|52.175.211.189|
|Admin.manage.microsoft.com|52.224.221.227<br>52.161.162.117<br>52.178.44.195<br>52.138.206.56<br>52.230.21.208<br>13.75.125.10|
|wip.mam.manage.microsoft.com|52.187.76.84<br>13.76.5.121<br>52.165.160.237<br>40.86.82.163<br>52.233.168.142<br>168.63.101.57|
|mam.manage.microsoft.com|104.40.69.125<br>13.90.192.78<br>40.85.174.177<br>40.85.77.31<br>137.116.229.43<br>52.163.215.232<br>52.174.102.180|






### <a name="apple-device-network-information"></a>Informações da rede de dispositivos Apple


|Utilizado para|Nome de anfitrião (endereço IP/sub-rede)|Protocolo|Porta|
|-----|--------|------|-------|
|Receber notificações Push do serviço do Intune através do Apple Push Notification Service (APNS). Consulte a documentação da Apple [aqui](https://support.apple.com/en-us/HT203609)|                                    gateway.push.apple.com (17.0.0.0/8)                                  |    TCP     |     2195     |
|Enviar comentários para o serviço do Intune através do Apple Push Notification Service (APNS)|                                  feedback.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2196     |
|Recuperar e exibir o conteúdo a partir de servidores da Apple|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br> \*.phobos.itunes-apple.com.akadns.net |    HTTP    |      80      |
|Comunicações com os servidores do APNS|#-courier.push.apple.com (17.0.0.0/8)<br>'#' é um número aleatório entre 0 e 50.|    TCP     |  5223 e 443  |
|Várias funcionalidades, inclusive, acesso a World Wide Web, loja do iTunes, loja de aplicações de macOS, iCloud, mensagens, etc. |phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net| HTTP/HTTPS |  80 ou 443   |

Para obter mais informações, consulte da Apple [portas TCP e UDP, usadas por produtos de software da Apple](https://support.apple.com/en-us/HT202944), [sobre o macOS, iOS e o iTunes de ligações de anfitrião do servidor e o iTunes fundo processos](https://support.apple.com/en-us/HT201999), e [se sua os clientes macOS e iOS não estão a receber notificações push da Apple](https://support.apple.com/en-us/HT203609).