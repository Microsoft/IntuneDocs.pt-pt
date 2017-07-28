---
title: "Utilização de largura de banda de rede do Intune"
description: "utilização de largura de banda de rede do Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 531112301d0c3827ec7eb3ab4087218caa331b90
ms.sourcegitcommit: 2b7d644c7a4f85315e11a7d0c5885cc66975c2ad
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/14/2017
---
# <a name="intune-network-bandwidth-use"></a>Utilização de largura de banda de rede do Intune

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

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

|Definição|Valor recomendado|Detalhes|
|-----------|---------------------|-----------|
|Tamanho da cache|De 5 GB até 30 GB|O valor varia com base no número de computadores clientes na sua rede e nas configurações que utiliza. Para impedir que os ficheiros sejam eliminados demasiado cedo, ajuste o tamanho da cache do seu ambiente.|
|Tamanho do ficheiro de cache individual|950 MB|Esta definição pode não estar disponível em todos os servidores proxy com colocação em cache.|
|Tipos de objeto a colocar em cache|HTTP<br /><br />HTTPS<br /><br />BITS|Os pacotes Intune são ficheiros CAB obtidos através de uma transferência do Serviço de Transferência Inteligente em Segundo Plano (BITS) através de HTTP.|
Para obter informações sobre como utilizar um servidor proxy para colocar conteúdos em cache, consulte a documentação da sua solução de servidor proxy.

### <a name="use-background-intelligent-transfer-service-on-computers"></a>Utilizar o Serviço de Transferência Inteligente em Segundo Plano em computadores
O Intune suporta a utilização do Serviço de Transferência Inteligente em Segundo Plano (BITS) num computador Windows para reduzir a largura de banda de rede utilizada durante as horas que configurar. Pode configurar uma política para o BITS na página **Largura de banda de rede** da política do Agente do Intune.

Para saber mais sobre o BITS e computadores Windows, veja [Background Intelligent Transfer Service (Serviço de Transferência Inteligente em Segundo Plano)](http://technet.microsoft.com/library/bb968799.aspx) na Biblioteca TechNet.

### <a name="use-branchcache-on-computers"></a>Utilizar o BranchCache nos computadores
Os clientes Intune podem utilizar o BranchCache para reduzir o tráfego da rede alargada (WAN). O BranchCache é suportado pelos seguintes sistemas operativos:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Para utilizar o BranchCache, o computador cliente tem de ter o BranchCache ativado e, em seguida, ser configurado para o **modo de cache distribuída**.

Por predefinição, o BranchCache e o modo de cache distribuída são ativados nos computadores quando o cliente do Intune é instalado. No entanto, se a Política de Grupo tiver desativado o BranchCache, o Intune não substitui essa política e o BranchCache permanece desativado.

Se utiliza o BranchCache, trabalhe em conjunto com outros administradores na sua organização para gerir a Política de Grupo e a política de Firewall do Intune. Certifique-se de que não implementam políticas que desativem o BranchCache ou exceções da Firewall. Para obter mais informações sobre o BranchCache, consulte [Descrição Geral do BranchCache](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Requisitos da comunicação de rede

Ative as comunicações de rede entre os dispositivos que gere e os sites que são precisos para serviços baseados na cloud.

O Intune não utiliza uma infraestrutura no local, como servidores a executar software do Intune, mas existem opções para utilizar na infraestrutura no local, incluindo as ferramentas de sincronização do Active Directory e do Exchange.

Para gerir computadores protegidos por firewalls e servidores proxy, tem de ativar as comunicações para o Intune.

-   O servidor proxy tem de suportar **HTTP (80)** e **HTTPS(443)**, porque os clientes do Intune utilizam ambos os protocolos
-   O Intune necessita de acesso não autenticado ao servidor proxy do site manage.microsoft.com para efetuar certas tarefas, tais como transferir software e atualizações

Pode modificar as definições de servidor proxy em computadores cliente individuais ou pode utilizar as definições de Política de Grupo para alterar as definições de todos os computadores cliente atrás de um servidor proxy específico.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

Os dispositivos geridos requerem configurações que permitam a **Todos os Utilizadores** aceder a serviços através de firewalls.

As tabelas que se seguem listam as portas e os serviços a que o cliente do Intune acede:

|**Domínios**|**Endereço IP**|
|---------------------|-----------|
|portal.manage.microsoft.com<br> m.manage.microsoft.com |40.86.181.86<br>13.82.59.78<br>13.74.184.100<br>40.68.188.2<br>13.75.42.6<br>52.230.25.184 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 104.40.82.191 <br>13.82.96.212 <br>52.169.9.87 <br>52.174.26.23 <br>40.83.123.72 <br>13.76.177.110 |
|portal.fei.msua01.manage.microsoft.com<br>m.fei.msua01.manage.microsoft.com |13.64.196.170|
|fei.msua01.manage.microsoft.com<br> portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com |40.71.34.120 |
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com |13.64.198.190|
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br> m.fei.msua02.manage.microsoft.com |  13.64.198.190|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |13.64.188.173|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |40.71.32.174|
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |13.64.197.181 |
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |40.71.38.205|
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |13.64.191.182 |
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |40.71.37.51 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |40.118.250.246 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |13.90.142.194 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.64.250.226 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.90.151.142 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.169.155.165 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.174.188.97 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.178.190.24 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.174.16.215 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |40.69.69.27 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |52.166.196.199 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |40.69.71.164 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |52.174.182.102 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |40.69.78.145 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |52.174.192.105 |
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |13.94.46.250|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |52.163.119.15 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |13.75.124.145 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |52.163.119.5|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.175.35.226|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.163.119.6|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.175.38.24|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.163.119.3|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|23.97.165.17|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
