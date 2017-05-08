---
title: "Utilização de largura de banda de rede do Intune | Documentos da Microsoft"
description: "utilização de largura de banda de rede do Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: 5211d2222e5e8ef9328f60ed13f0146925194c5f
ms.lasthandoff: 04/26/2017


---

# <a name="intune-network-bandwidth-use"></a>Utilização de largura de banda de rede do Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Esta orientação ajuda os administradores do Intune a compreenderem os requisitos de rede do serviço Intune. Pode utilizar estas informações para compreender os requisitos de largura de banda e as definições de portas e endereços IP necessárias para as definições de proxy.

## <a name="average-network-traffic"></a>Tráfego de rede médio
A tabela lista o tamanho e frequência aproximados dos conteúdos comuns que circulam na rede para cada cliente.

> [!NOTE]
> Para garantir que os computadores e dispositivos móveis recebem as atualizações e conteúdos necessários do serviço do Intune, estes têm de ser regularmente ligados à Internet. O tempo necessário para receber as atualizações ou conteúdos irá variar, mas por regra, deverão manter uma ligação ininterrupta à Internet durante, pelo menos, 1 hora por dia.

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
Pode utilizar um servidor proxy que coloque conteúdos em cache para reduzir as transferências em duplicado e reduzir a utilização da largura de banda de rede por parte dos clientes que efetuam pedidos de conteúdo da Internet.

Um servidor proxy com colocação em cache recebe pedidos de conteúdo efetuados por computadores clientes na sua rede, obtém esses conteúdos da Internet e pode, em seguida, colocar as respostas de HTTP e as transferências de binários em cache. O servidor utiliza as informações colocadas em cache para responder a pedidos posteriores dos computadores clientes do Intune.

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
Os clientes Intune podem utilizar o BranchCache para reduzir o tráfego da rede alargada (WAN). Os seguintes sistemas operativos que são suportados como clientes também suportam o BranchCache:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Para utilizar o BranchCache, o computador cliente tem de ter o BranchCache ativado e, em seguida, ser configurado para o **modo de cache distribuída**.

Por predefinição, o BranchCache e o modo de cache distribuída são ativados no computador quando o cliente do Intune é instalado. No entanto, se o cliente já tiver uma Política de Grupo que desativa o BranchCache, o Intune não substitui essa política e o BranchCache permanecerá desativado nesse computador.

Se utiliza o BranchCache, deve comunicar com os outros administradores na sua organização responsáveis pela gestão da Política de Grupo e a política de Firewall do Intune, para garantir que não implementam políticas que desativem o BranchCache ou exceções da Firewall. Para obter mais informações sobre o BranchCache, consulte [Descrição Geral do BranchCache](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Requisitos da comunicação de rede

Tem de ativar as comunicações de rede entre os dispositivos que gere e utiliza para gerir a sua subscrição do Intune e os sites que são precisos para serviços baseados na cloud.

O Intune não utiliza uma infraestrutura no local, como servidores a executar software do Intune, mas existem opções para utilizar na infraestrutura no local, incluindo as ferramentas de sincronização do Active Directory e do Exchange.

Para gerir computadores atrás de firewalls e de servidores proxy, tem de configurar as firewalls e os servidores proxy para permitirem comunicações com o Intune.

### <a name="requirements-for-proxy-servers"></a>Requisitos para servidores proxy
Para gerir computadores atrás de um servidor proxy, tenha em conta o seguinte:

-   O servidor proxy tem de suportar **HTTP** e **HTTPS**, porque os clientes do Intune utilizam ambos os protocolos
-   O Intune suporta servidores proxy não autenticados

Pode modificar as definições de servidor proxy em computadores cliente individuais ou pode utilizar as definições de Política de Grupo para alterar as definições de todos os computadores cliente atrás de um servidor proxy específico.

### <a name="requirements-for-firewalls-ports-and-domains"></a>Requisitos para firewalls, portas e domínios
Os dispositivos geridos requerem configurações que permitam a **Todos os Utilizadores** aceder a serviços através de firewalls.

A tabela que se segue lista as portas e os serviços a que o cliente do Intune acede.

|**Domínio**|**Portas**|**Endereço IP**|
|------|----|---|
|manage.microsoft.com<br>a.manage.microsoft.com<br>admin.manage.microsoft.com<br>enterpriseenrollment.manage.microsoft.com<br>enterpriseenrollment-s.manage.microsoft.com<br>i.manage.microsoft.com<br>p.manage.microsoft.com<br>r.manage.microsoft.com|80 e 443|134.170.168.254<br>134.170.51.126
|m.manage.microsoft.com|80 e 443| 13.91.59.243<br>40.68.30.140
|portal.manage.microsoft.com|80 e 443|40.121.50.69<br>52.169.30.159
|account.manage.microsoft.com|80 e 443|157.56.13.59
|fef.msua01.manage.microsoft.com|80 e 443|138.91.243.97
|fef.msua02.manage.microsoft.com|80 e 443|23.96.112.46
|fef.msua04.manage.microsoft.com|80 e 443|23.96.112.28
|fef.msua05.manage.microsoft.com|80 e 443|138.91.244.151
|fef.msub01.manage.microsoft.com|80 e 443|137.135.128.214
|fef.msub02.manage.microsoft.com|80 e 443|137.135.130.29
|fef.msub03.manage.microsoft.com|80 e 443|23.97.165.17
|fef.msub05.manage.microsoft.com|80 e 443|23.97.166.52
|fef.msuc01.manage.microsoft.com|80 e 443|207.46.225.1
|fef.msuc02.manage.microsoft.com|80 e 443|23.98.66.118
|fef.msuc03.manage.microsoft.com|80 e 443|23.101.0.100
|fef.msuc05.manage.microsoft.com|80 e 443|207.46.154.33
|fef.msua06.manage.microsoft.com|80 e 443|104.42.188.1
|fei.msua01.manage.microsoft.com|80 e 443|138.91.240.131
|fei.msua02.manage.microsoft.com|80 e 443|23.96.112.143
|fei.msua04.manage.microsoft.com|80 e 443|23.96.112.147
|fei.msua05.manage.microsoft.com|80 e 443|138.91.240.163
|fei.msub01.manage.microsoft.com|80 e 443|137.135.130.85
|fei.msub02.manage.microsoft.com|80 e 443|137.135.132.149
|fei.msub03.manage.microsoft.com|80 e 443|23.97.160.232
|fei.msub05.manage.microsoft.com|80 e 443|23.97.162.250
|fei.msuc01.manage.microsoft.com|80 e 443|207.46.224.73
|fei.msuc02.manage.microsoft.com|80 e 443|23.98.66.194
|fei.msuc03.manage.microsoft.com|80 e 443|23.101.2.105
|fei.msuc05.manage.microsoft.com|80 e 443|207.46.147.126
|fei.msua06.manage.microsoft.com|80 e 443|138.91.149.190
|m.fei.msua01.manage.microsoft.com|80 e 443|138.91.240.131
|m.fei.msua02.manage.microsoft.com|80 e 443|23.96.112.143
|m.fei.msua04.manage.microsoft.com|80 e 443|23.96.112.147
|m.fei.msua05.manage.microsoft.com|80 e 443|138.91.240.163
|m.fei.msub01.manage.microsoft.com|80 e 443|137.135.130.85
|m.fei.msub02.manage.microsoft.com|80 e 443|137.135.132.149
|m.fei.msub03.manage.microsoft.com|80 e 443|23.97.160.232
|m.fei.msub05.manage.microsoft.com|80 e 443|23.97.162.250
|m.fei.msuc01.manage.microsoft.com|80 e 443|207.46.224.73
|m.fei.msuc02.manage.microsoft.com|80 e 443|23.98.66.194
|m.fei.msuc03.manage.microsoft.com|80 e 443|23.101.2.105
|m.fei.msuc05.manage.microsoft.com|80 e 443|207.46.147.126
|m.fei.msua06.manage.microsoft.com|80 e 443|138.91.149.190
|m.msua01.manage.microsoft.com|80 e 443|157.55.50.182
|m.msua02.manage.microsoft.com|80 e 443|134.170.49.121
|m.msua04.manage.microsoft.com|80 e 443|134.170.49.126
|m.msua05.manage.microsoft.com|80 e 443|157.55.240.190
|m.msua06.manage.microsoft.com|80 e 443|134.170.49.114
|m.msub01.manage.microsoft.com|80 e 443|94.245.121.50
|m.msub02.manage.microsoft.com|80 e 443|94.245.121.58
|m.msub03.manage.microsoft.com|80 e 443|94.245.121.56
|m.msub05.manage.microsoft.com|80 e 443|157.56.113.123
|m.msuc01.manage.microsoft.com|80 e 443|104.44.84.187
|m.msuc02.manage.microsoft.com|80 e 443|104.44.84.188
|m.msuc03.manage.microsoft.com|80 e 443|104.44.84.189
|m.msuc05.manage.microsoft.com|80 e 443|111.221.76.60
|msua01.manage.microsoft.com|80 e 443|157.55.50.182
|msua02.manage.microsoft.com|80 e 443|134.170.49.121
|msua04.manage.microsoft.com|80 e 443|134.170.49.126
|msua05.manage.microsoft.com|80 e 443|157.55.240.190
|msub01.manage.microsoft.com|80 e 443|94.245.121.50
|msub02.manage.microsoft.com|80 e 443|94.245.121.58
|msub03.manage.microsoft.com|80 e 443|94.245.121.56
|msub05.manage.microsoft.com|80 e 443|157.56.113.123
|msuc01.manage.microsoft.com|80 e 443|104.44.84.187
|msuc02.manage.microsoft.com|80 e 443|104.44.84.188
|msuc03.manage.microsoft.com|80 e 443|104.44.84.189
|msuc05.manage.microsoft.com|80 e 443|111.221.76.60
|msua06.manage.microsoft.com|80 e 443|134.170.49.114
|ncufun.account.manage.microsoft.com|80 e 443|157.55.252.224
|neufun.account.manage.microsoft.com|80 e 443|65.52.229.134
|portal.fei.msua01.manage.microsoft.com|80 e 443|138.91.240.131
|portal.fei.msua02.manage.microsoft.com|80 e 443|23.96.112.143
|portal.fei.msua04.manage.microsoft.com|80 e 443|23.96.112.147
|portal.fei.msua05.manage.microsoft.com|80 e 443|138.91.240.163
|portal.fei.msub01.manage.microsoft.com|80 e 443|137.135.130.85
|portal.fei.msub02.manage.microsoft.com|80 e 443|137.135.132.149
|portal.fei.msub03.manage.microsoft.com|80 e 443|23.97.160.232
|portal.fei.msub05.manage.microsoft.com|80 e 443|23.97.162.250
|portal.fei.msuc01.manage.microsoft.com|80 e 443|207.46.224.73
|portal.fei.msuc02.manage.microsoft.com|80 e 443|23.98.66.194
|portal.fei.msuc03.manage.microsoft.com|80 e 443|23.101.2.105
|portal.fei.msuc05.manage.microsoft.com|80 e 443|207.46.147.126
|portal.fei.msua06.manage.microsoft.com|80 e 443|138.91.149.190
|portal.msua01.manage.microsoft.com|80 e 443|157.55.50.182
|portal.msua02.manage.microsoft.com|80 e 443|134.170.49.121
|portal.msua04.manage.microsoft.com|80 e 443|134.170.49.126
|portal.msua05.manage.microsoft.com|80 e 443|157.55.240.190
|portal.msub01.manage.microsoft.com|80 e 443|94.245.121.50
|portal.msub02.manage.microsoft.com|80 e 443|94.245.121.58
|portal.msub03.manage.microsoft.com|80 e 443|94.245.121.56
|portal.msub05.manage.microsoft.com|80 e 443|157.56.113.123
|portal.msuc01.manage.microsoft.com|80 e 443|104.44.84.187
|portal.msuc02.manage.microsoft.com|80 e 443|104.44.84.188
|portal.msuc03.manage.microsoft.com|80 e 443|104.44.84.189
|portal.msuc05.manage.microsoft.com|80 e 443|111.221.76.60
|portal.msua06.manage.microsoft.com|80 e 443|134.170.49.114
|ssu2.manage.microsoft.com|80 e 443|157.55.99.181
|status.manage.microsoft.com|80 e 443|157.55.99.170
|swda01.manage.microsoft.com<br>swda02.manage.microsoft.com<br>swdb01.manage.microsoft.com<br>swdb02.manage.microsoft.com<br>swdc01.manage.microsoft.com<br>swdc02.manage.microsoft.com|80 e 443|93.184.215.200
|*.microsoftonline-p.com|80 e 443||
|has.spserv.microsoft.com<br>Necessário para o serviço de atestado de estado de funcionamento do dispositivo|443||
|*.microsoftonline-p.net|80 e 443||
|*.portal.office.com|80 e 443||
|*.spynet2.microsoft.com|443||
|c.microsoft.com|80 e 443||
|c1.microsoft.com|80 e 443||
|blob.core.windows.net|80 e 443||
|ajax.aspnetcdn.com|80 e 443||
|*.googleapis.com<br>Este domínio é necessário para o suporte do JQuery quando utiliza o site do portal da empresa.|80 e 443||
|wustat.microsoft.com|80 e 443||
|Serviços de Atualização da Microsoft|\*.update.microsoft.com<br>download.microsoft.com<br>update.microsoft.com<br>\*.download.windowsupdate.com<br>download.windowsupdate.com<br>\*.windowsupdate.com<br>windowsupdate.microsoft.com<br>ntservicepack.microsoft.com|80 e 443|
|Pedidos de pesquisa de DNS|manage.microsoft.com.nsatc.net|80|
|Comunicação de dispositivos Samsung KNOX Standard através da firewall|Para permitir que os dispositivos Samsung KNOX Standard contactem os servidores KNOX Standard através da firewall, siga as instruções nas FAQ do Samsung KNOX Standard.||
|Comunicação de acesso condicional|443|204.79.197.200|
|Documentação, Ajuda e suporte:</br></br>*.livemeeting.com<br>\*.microsoftonline.com<br>\*.social.technet.microsoft.com<br>blogs.technet.com<br>go.microsoft.com<br>onlinehelp.microsoft.com<br>www.microsoft.com|80|||


>[!div class="step-by-step"]

>[&larr; **Pré-requisitos**](what-to-know-before-you-start-microsoft-intune.md)     [**Subscrição** &rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)  

