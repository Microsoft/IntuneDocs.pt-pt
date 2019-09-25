---
title: Detalhes de largura de banda e requisitos de rede do Microsoft Intune
titleSuffix: ''
description: Reveja os detalhes de largura de banda e requisitos de configuração de rede do Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6d5e8d76a06ac45fed2b9759e519ffc7fabf7ec
ms.sourcegitcommit: d2989b9992d10d133573d9bc31479659fb7e242c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/18/2019
ms.locfileid: "71238315"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Largura de banda e requisitos de configuração de rede do Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Você pode usar essas informações para entender os requisitos de largura de banda para suas implantações do Intune.

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
> [!NOTE]
> Se utilizar um servidor proxy para colocar em cache pedidos de conteúdo, a comunicação só será encriptada entre o cliente e o proxy e do proxy para o Intune. A ligação do cliente para o Intune não será encriptada ponto a ponto.

Para obter informações sobre como utilizar um servidor proxy para colocar conteúdos em cache, consulte a documentação da sua solução de servidor proxy.

### <a name="use-background-intelligent-transfer-service-bits-on-computers"></a>Utilizar o Serviço de Transferência Inteligente em Segundo Plano (BITS) nos computadores
Durante as horas que configurar, pode utilizar o BITS num computador Windows para reduzir a largura de banda da rede. Pode configurar uma política do BITS na página **Largura de banda de rede** da política do Agente do Intune.

> [!NOTE]
> Na gestão MDM no Windows, apenas a interface de gestão do SO para o tipo de aplicação MobileMSI utiliza o BITS para a transferência. O AppX/MsiX utiliza a sua própria pilha de transferência não BITS e as aplicações Win32 através do agente do Intune utilizam a Otimização de Entrega em vez do BITS.

Para saber mais sobre o BITS e computadores Windows, veja [Background Intelligent Transfer Service (Serviço de Transferência Inteligente em Segundo Plano)](https://technet.microsoft.com/library/bb968799.aspx) na Biblioteca TechNet.

### <a name="delivery-optimization"></a>Otimização de entrega
A otimização de entrega permite usar o Intune para reduzir o consumo de largura de banda quando seus dispositivos Windows 10 baixam aplicativos e atualizações. Usando um cache distribuído de organização própria, os downloads podem ser extraídos de servidores tradicionais e fontes alternativas (como pares de rede).

Para ver a lista completa de versões e tipos de conteúdo do Windows 10 com suporte pela otimização de entrega, consulte o [artigo otimização de entrega para atualizações do Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#requirements).

Você pode [Configurar a otimização de entrega](delivery-optimization-settings.md) como parte dos perfis de configuração do dispositivo.


### <a name="use-branchcache-on-computers"></a>Utilizar o BranchCache nos computadores
Os clientes Intune podem utilizar o BranchCache para reduzir o tráfego da rede alargada (WAN). O BranchCache é suportado pelos seguintes sistemas operativos:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Para utilizar o BranchCache, o computador cliente tem de ter o BranchCache ativado e, em seguida, ser configurado para o **modo de cache distribuída**.

Quando o cliente do Intune é instalado nos computadores, o BranchCache e o modo de cache distribuída são ativados, por predefinição. No entanto, se a Política de Grupo tiver desativado o BranchCache, o Intune não substituirá essa política e o BranchCache permanecerá desativado.

Se utiliza o BranchCache, trabalhe em conjunto com outros administradores na sua organização para gerir a Política de Grupo e a política de Firewall do Intune. Confirme que não implementam políticas que desativem o BranchCache ou exceções da Firewall. Para obter mais informações sobre o BranchCache, consulte [Descrição Geral do BranchCache](https://technet.microsoft.com/library/hh831696.aspx).

> [!NOTE]
> Você pode usar Microsoft Intune para gerenciar computadores Windows [como dispositivos móveis com o MDM (gerenciamento de dispositivo móvel)](windows-enroll.md) ou como computadores com o cliente de software do Intune. A Microsoft recomenda que os clientes [usem a solução de gerenciamento de MDM](windows-enroll.md) sempre que possível. Quando gerenciada dessa forma, o BranchCache não tem suporte. Para obter mais informações, consulte [comparar o gerenciamento de computadores Windows como computadores ou dispositivos móveis](pc-management-comparison.md).


## <a name="next-steps"></a>Passos seguintes

[Examinar pontos de extremidade do Intune](intune-endpoints.md)

