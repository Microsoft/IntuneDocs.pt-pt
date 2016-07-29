---
title: "Utilização de largura de banda de rede do Intune | Microsoft Intune"
description: "utilização de largura de banda de rede do Intune"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2a192c71b1b82f59b34ea614d09d895174f8112b
ms.openlocfilehash: 2a600b7948c55a408314aedc3895c25fcc09251d


---

# Utilização de largura de banda de rede do Intune

Antes de configurar o [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)], reveja este tópico e outros requisitos indicados em [O que deve saber antes de iniciar o Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md).

Utilize as informações nas seguintes secções para planear o tráfego de rede dos clientes do [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)].

## Tráfego de rede médio
A seguinte tabela lista o tamanho e frequência aproximados dos conteúdos comuns que circulam na rede para cada cliente.

> [!NOTE]
> Para garantir que os computadores e dispositivos móveis recebem as atualizações e conteúdos necessários do serviço do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], estes têm de ser regularmente ligados à Internet. O tempo necessário para receber as atualizações ou conteúdos irá variar, mas por regra, deverão manter uma ligação ininterrupta à Internet durante, pelo menos, 1 hora por dia.

|Tipo de conteúdo|Tamanho aproximado|Frequência e detalhes|
|----------------|--------------------|-------------------------|
|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] instalação do cliente<br /><br />**São aplicáveis os seguintes requisitos, para além da instalação do cliente do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]**|125 MB|**Uma vez**<br /><br />O tamanho da transferência do cliente varia consoante o sistema operativo do computador cliente.|
|Pacote de inscrição de clientes|15 MB|**Uma vez**<br /><br />São possíveis transferências adicionais quando existirem atualizações para este tipo de conteúdo.|
|Agente do Endpoint Protection|65 MB|**Uma vez**<br /><br />São possíveis transferências adicionais quando existirem atualizações para este tipo de conteúdo.|
|Agente do Operations Manager|11 MB|**Uma vez**<br /><br />São possíveis transferências adicionais quando existirem atualizações para este tipo de conteúdo.|
|Agente de políticas|3 MB|**Uma vez**<br /><br />São possíveis transferências adicionais quando existirem atualizações para este tipo de conteúdo.|
|Assistência Remota através do agente Microsoft Easy Assist|6 MB|**Uma vez**<br /><br />São possíveis transferências adicionais quando existirem atualizações para este tipo de conteúdo.|
|Operações diárias de clientes|6 MB|**Diariamente**<br /><br />O cliente do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] comunica regularmente com o serviço do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para procurar atualizações e políticas e para comunicar o estado do cliente ao serviço.|
|Atualizações de definições de software maligno do Endpoint Protection|Varia<br /><br />Normalmente, entre 40 KB a 2 MB|**Diariamente**<br /><br />Até três vezes por dia.|
|Atualização do motor do Endpoint Protection|5 MB|**Mensalmente**|
|Atualizações de software|Varia<br /><br />O tamanho depende das atualizações que implementar.|**Mensalmente**<br /><br />Normalmente, as atualizações de software são lançadas na segunda terça-feira de cada mês.<br /><br />Um computador inscrito ou implementado recentemente pode utilizar mais largura de banda de rede ao transferir todas as atualizações lançadas anteriormente.|
|Service packs|Varia<br /><br />O tamanho varia consoante o service pack que implementar.|**Varia**<br /><br />Depende da altura em que implementar os service packs.|
|Distribuição de software|Varia<br /><br />O tamanho depende do software que implementar.|**Varia**<br /><br />Depende da altura em que implementar o software.|

## Formas de reduzir a utilização da largura de banda de rede
Pode utilizar um ou mais dos seguintes métodos para reduzir a utilização da largura de banda de rede dos clientes do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

### Utilizar um servidor proxy para colocar os pedidos de conteúdo em cache
Pode utilizar um servidor proxy que coloque conteúdos em cache para reduzir as transferências em duplicado e reduzir a utilização da largura de banda de rede por parte dos clientes que efetuam pedidos de conteúdo da Internet.

Um servidor proxy com colocação em cache recebe pedidos de conteúdo efetuados por computadores clientes na sua rede, obtém esses conteúdos da Internet e pode, em seguida, colocar as respostas de HTTP e as transferências de binários em cache. O servidor utiliza as informações colocadas em cache para responder a pedidos posteriores dos computadores clientes do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

Seguem-se as definições típicas para utilizar um servidor proxy que coloca conteúdos em cache para os clientes do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

|Definição|Valor recomendado|Detalhes|
|-----------|---------------------|-----------|
|Tamanho da cache|De 5 GB até 30 GB|O valor varia com base no número de computadores clientes na sua rede e nas configurações que utiliza. Para impedir que os ficheiros sejam eliminados demasiado cedo, ajuste o tamanho da cache do seu ambiente.|
|Tamanho do ficheiro de cache individual|950 MB|Esta definição pode não estar disponível em todos os servidores proxy com colocação em cache.|
|Tipos de objeto a colocar em cache|HTTP<br /><br />HTTPS<br /><br />BITS|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] são ficheiros CAB obtidos através de uma transferência do Serviço de Transferência Inteligente em Segundo Plano (BITS) através de HTTP.|
Para obter informações sobre como utilizar um servidor proxy para colocar conteúdos em cache, consulte a documentação da sua solução de servidor proxy.

### Utilizar o Serviço de Transferência Inteligente em Segundo Plano em computadores
[!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] suporta a utilização do Serviço de Transferência Inteligente em Segundo Plano (BITS) num computador Windows para reduzir a largura de banda de rede utilizada durante as horas que configurar. Pode configurar uma política para o BITS na página **Largura de banda de rede** da política do Agente do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

Para saber mais sobre o BITS e computadores Windows, veja [Background Intelligent Transfer Service (Serviço de Transferência Inteligente em Segundo Plano)](http://technet.microsoft.com/library/bb968799.aspx) na Biblioteca TechNet.

### Utilizar o BranchCache nos computadores
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] podem utilizar o BranchCache para reduzir o tráfego da rede alargada (WAN). Os seguintes sistemas operativos que são suportados como clientes também suportam o BranchCache:

-   [!INCLUDE[nextref_client_7](../includes/nextref_client_7_md.md)]

-   [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]

-   [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)]

Para utilizar o BranchCache, o computador cliente tem de ter o BranchCache ativado e, em seguida, ser configurado para o **modo de cache distribuída**.

Por predefinição, o BranchCache e o modo de cache distribuída são ativados no computador quando o cliente do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] é instalado. No entanto, se o cliente já tiver uma Política de Grupo que desativa o BranchCache, o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] não substitui essa política e o BranchCache permanecerá desativado nesse computador.

Se utiliza o BranchCache, deve comunicar com os outros administradores na sua organização responsáveis pela gestão da Política de Grupo e a política de Firewall do [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)], para garantir que não implementam políticas que desativem o BranchCache ou exceções da Firewall. Para obter mais informações sobre o BranchCache, consulte [Descrição Geral do BranchCache](http://technet.microsoft.com/library/hh831696.aspx).

### Consulte também
[What to know before you start Microsoft Intune (O que deve saber antes de iniciar o Microsoft Intune)](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


