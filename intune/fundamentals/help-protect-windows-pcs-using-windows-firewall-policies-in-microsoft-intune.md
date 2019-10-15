---
title: Políticas de firewall para computadores Windows
titleSuffix: Microsoft Intune
description: O Intune pode ajudá-lo a proteger os PCs gerenciados com o cliente do Intune de várias maneiras, incluindo ajudá-lo a definir as configurações do firewall do Windows.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8e5a67ade5f1b3c9efc2674887a042bd828136fa
ms.sourcegitcommit: a2654f3642b43b29ab0e1cbb2dfa2b56aae18d0e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72310744"
---
# <a name="help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune"></a>Ajudar a proteger computadores Windows usando políticas de firewall do Windows no Microsoft Intune

[!INCLUDE [classic-portal](../../intune-classic/includes/classic-portal.md)]

> [!NOTE]
> As informações neste tópico aplicam-se somente a áreas de trabalho do Windows que você está gerenciando como PCs usando o cliente de software do Intune. Se você quiser gerenciar as configurações de firewall para computadores Windows registrados como dispositivos móveis, consulte [Adicionar configurações de proteção de ponto de extremidade no Intune](../protect/endpoint-protection-configure.md).

Microsoft Intune pode ajudá-lo a proteger computadores Windows gerenciados com o cliente do Intune de várias maneiras. Uma maneira na qual ele faz isso é fornecer políticas que permitem que você defina as configurações do firewall do Windows nos computadores.

Se você ainda não instalou o cliente do computador Windows do Intune em seus computadores, consulte [instalar o cliente do computador Windows com o Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Use as informações nas seções a seguir para ajudá-lo a configurar, implantar e monitorar as políticas de firewall do Windows em computadores Windows.

## <a name="use-intune-policies-to-manage-windows-firewall"></a>Usar políticas do Intune para gerenciar o Firewall do Windows
A política de firewall do Windows permite criar e implantar configurações que controlam o Firewall do Windows em PCs gerenciados. Você não pode gerenciar exceções personalizadas para o Firewall do Windows, e essas configurações não afetam os firewalls de terceiros.

> [!NOTE]
> Se Microsoft Intune política e Política de Grupo estiverem configurados para gerenciar a mesma configuração no PC, a configuração Política de Grupo substituirá a política de Microsoft Intune. Para obter informações sobre como evitar conflitos entre a política e Política de Grupo do Intune, consulte [resolver GPOs e conflitos de política de Microsoft Intune](resolve-gpo-and-microsoft-intune-policy-conflicts.md).
>
> Se você quiser implantar as configurações do firewall do Windows em computadores que executam o Windows Vista, primeiro instale o [hotfix KB971800](https://support2.microsoft.com/kb/971800) nesses computadores.

> [!IMPORTANT]
> Para gerenciar o Firewall do Windows usando o Intune, verifique se os dois serviços a seguir estão habilitados nos computadores que você gerencia:
>
> - Firewall do Windows
> - Agente de política IPsec

## <a name="configure-a-windows-firewall-policy"></a>Configurar uma política de firewall do Windows

1. No [console de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **política** &gt; **Adicionar política**.

2. Configurar e implantar uma política de **configurações do firewall do Windows** . Você pode usar as configurações recomendadas ou personalizar as configurações. Se você precisar de mais informações sobre como criar e implantar políticas, consulte [tarefas comuns de gerenciamento de computadores Windows com o cliente de computador Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

    A seção a seguir lista os valores que você pode configurar na política e também os valores padrão que serão usados se você não personalizar a política.

Depois de implantar uma política de firewall do Windows, você pode exibir seu status na página **todas as políticas** do espaço de trabalho **política** .

## <a name="specify-policy-settings-for-windows-firewall"></a>Especificar configurações de política para o Firewall do Windows

### <a name="turn-on-windows-firewall"></a>Ativar o Firewall do Windows

Essas configurações de política habilitam o Firewall do Windows em computadores gerenciados que são:
- Conectado a um domínio (por exemplo, no local de trabalho)
- Conectado a uma rede privada (confiável) (como uma rede doméstica)
- Conectado a uma rede pública não confiável (como uma lanchonete)

O valor padrão para cada uma dessas configurações é **Sim**, que é o valor mais seguro.



### <a name="block-all-incoming-connections-including-those-in-the-list-of-allowed-programs"></a>Bloquear todas as conexões de entrada, incluindo aquelas na lista de programas permitidos

Essas configurações de política configuram o Firewall do Windows para bloquear o tráfego de rede de entrada em computadores gerenciados que são:
- Conectado a um domínio (por exemplo, no local de trabalho)
- Conectado a uma rede privada (confiável) (como uma rede doméstica)
- Conectado a uma rede pública não confiável (como uma lanchonete)

O valor padrão para cada uma dessas configurações é **Sim**, que é o valor mais seguro.

> [!IMPORTANT]
> Se seu ambiente inclui computadores gerenciados que executam o Windows Vista sem Service Packs instalados, você deve instalar a atualização associada ao [artigo 971800](https://go.microsoft.com/fwlink/?LinkId=188405) na base de dados de conhecimento Microsoft ou desabilitar o **bloqueio de todas as entradas** configurações de política de conexões em políticas que são implantadas nesses computadores.

### <a name="notify-the-user-when-windows-firewall-blocks-a-new-program"></a>Notificar o usuário quando o Firewall do Windows bloquear um novo programa

Essas configurações de política determinam se o Firewall do Windows notifica um usuário de PC quando bloqueia o tráfego de rede de entrada quando o computador gerenciado é:
- Conectado a um domínio (por exemplo, no local de trabalho)
- Conectado a uma rede privada (confiável) (como uma rede doméstica)
- Conectado a uma rede pública não confiável (como uma lanchonete)

O valor padrão para cada uma dessas configurações é **Sim**.


### <a name="configure-predefined-exceptions"></a>Configurar exceções predefinidas

Você pode configurar exceções que permitem tipos específicos de tráfego de rede por meio do firewall, independentemente dos valores que você configurou anteriormente. Nenhuma dessas configurações é configurada por padrão.

|Nome da definição|Detalhes|
|------------------|--------------------|
|**BranchCache-Recuperação de conteúdo**<br>(Windows 7 ou posterior)|Permite que os clientes do BranchCache usem HTTP para recuperar conteúdo de outros clientes do BranchCache enquanto estiverem no modo distribuído e do cache hospedado enquanto estiverem no modo de cache hospedado. Essa configuração usa HTTP.|
|**BranchCache-cliente de cache hospedado**<br>(Windows 7 ou posterior)|Permite que os clientes BranchCache usem um cache hospedado. Essa configuração usa HTTPS.|
|**BranchCache-servidor de cache hospedado**|Permite que os clientes do BranchCache usem um cache hospedado para se comunicar com outros clientes. Essa configuração usa HTTPS.|
|**BranchCache-descoberta de mesmo nível**<br>(Windows 7 ou posterior)|Permite que os clientes do BranchCache usem o protocolo WS-Discovery (descoberta dinâmica de serviços Web) para pesquisar a disponibilidade do conteúdo na sub-rede local.|
|**Cache de BITS**|Permite que os clientes usem Serviço de Transferência Inteligente em Segundo Plano (BITS) para localizar e compartilhar arquivos armazenados no cache do BITS em clientes na mesma sub-rede. Essa configuração usa serviços da Web em dispositivos (WSDAPI) e RPC (chamada de procedimento remoto).|
|**Conectar-se a um projetor de rede**|Permite que os usuários se conectem a projetores em redes com ou sem fio para projetar apresentações. Essa configuração usa WSDAPI.|
|**Rede principal**|Permite que os clientes usem IPv4 e IPv6 para se conectarem aos recursos de rede.|
|**Coordenador de Transações Distribuídas**|Permite que computadores gerenciados coordenem transações que atualizam recursos protegidos por transações, como bancos de dados, filas de mensagens e sistemas de arquivos.|
|**Compartilhamento de arquivos e impressoras**|Permite que os usuários compartilhem arquivos e impressoras locais com outros usuários na rede. Essa configuração usa NetBIOS, resolução de nomes multicast de link local (LLMNR), protocolo SMB e RPC.|
|**Base**<br>(Windows 7 ou posterior)|Permite que computadores gerenciados participem de uma rede de grupo doméstico.|
|**Serviço iSCSI**|Permite que computadores gerenciados se conectem a dispositivos e servidores iSCSI.|
|**Serviço de gerenciamento de chaves**|Permite que os computadores sejam contados para conformidade de licenças em ambientes corporativos.|
|**Extensores do Media Center**|Permite que os extensores do Media Center se comuniquem com computadores que executam o Windows Media Center. Essa configuração usa o SSDP (protocolo de descoberta de serviço) e o qWave.|
|**Serviço Netlogon**|Configura um canal de segurança entre clientes de domínio e um controlador de domínio para autenticar usuários e serviços. Essa configuração usa RPC.|
|**Descoberta de rede**|Permite que os computadores descubram outros dispositivos e sejam descobertos por outros dispositivos na rede. Essa configuração usa serviços de host e publicação de descoberta de função e protocolos de rede SSDP, NetBIOS, LLMNR e UPnP.|
|**Logs e Alertas de Desempenho**|Permite que o serviço de Logs e Alertas de Desempenho seja gerenciado remotamente. Essa configuração usa RPC.|
|**Administração remota**|Habilita a administração remota do computador.|
|**Assistência remota**|Permite que os usuários de computadores gerenciados solicitem assistência remota de outros usuários na rede. Essa configuração usa SSDP, protocolo PNRP (Peer Name Resolution Protocol), Teredo e protocolos de rede UPnP.|
|**Ambiente de Trabalho Remoto**|Permite que o computador use Área de Trabalho Remota para acessar outros computadores.|
|**Gerenciamento remoto do log de eventos**|Permite que os logs de eventos do cliente sejam exibidos e gerenciados remotamente. Essa configuração usa pipes nomeados e RPC.|
|**Gerenciamento remoto de tarefas agendadas**|Habilita o gerenciamento remoto do serviço de agendamento de tarefas. Essa configuração usa RPC.|
|**Gerenciamento remoto de serviços**|Habilita o gerenciamento remoto de serviços locais em clientes. Essa configuração usa pipes nomeados e RPC.|
|**Gerenciamento de volume remoto**|Habilita o gerenciamento remoto de volume de disco de software e hardware. Essa configuração usa RPC.|
|**Roteamento e acesso remoto**|Permite conexões de entrada VPN e acesso remoto aos computadores.|
|**Protocolo de túnel de soquete seguro**|Permite conexões VPN de entrada para computadores gerenciados com SSTP (Secure Socket encapsulating Protocol). Essa configuração usa HTTPS.|
|**Interceptação SNMP**|Permite que os computadores gerenciados recebam o tráfego do serviço de interceptação SNMP (Simple Network Management Protocol).|
|**Estrutura UPnP**|Configura o serviço de estrutura UPnP em computadores para permitir que eles descubram e usem dispositivos UPnP certificados.|
|**Serviço de registro de nome do computador de colaboração do Windows**|Permite que os computadores localizem e se comuniquem com outros computadores usando o SSDP e o PNRP.|
|**Windows Media Player**|Permite que os usuários recebam mídia de streaming por UDP (User Datagram Protocol).|
|**Serviço de compartilhamento de rede do Windows Media Player**|Permite que os usuários compartilhem mídia em uma rede. Essa configuração usa os protocolos de rede SSDP, qWave e UPnP.|
|**Serviço de compartilhamento de rede do Windows Media Player (Internet)**<br>(Windows 7 ou posterior)|Permite que os usuários compartilhem mídias domésticas pela Internet.|
|**Espaço de reunião do Windows**|Permite que os usuários colaborem em uma rede para compartilhar documentos, programas e suas áreas de trabalho. Essa configuração usa o DFSR (replicação Sistema de Arquivos Distribuído) e o P2P.|
|**Base de colaboração ponto a ponto do Windows**|Configura vários programas e tecnologias ponto a ponto para permitir que eles se conectem. Essa configuração usa SSDP e PNRP.|
|**Gerenciamento Remoto do Windows (compatibilidade)**|Permite o gerenciamento remoto de computadores gerenciados com o WS-Management, um protocolo baseado em serviços Web para o gerenciamento remoto de dispositivos e sistemas operacionais.|
|**Gestão Remota do Windows**<br>(Windows 8 ou posterior)|Permite o gerenciamento remoto de computadores gerenciados com o WS-Management, um protocolo baseado em serviços Web para o gerenciamento remoto de dispositivos e sistemas operacionais.|
|**PC virtual do Windows**<br>(Windows 7 ou posterior)|Permite que as máquinas virtuais se comuniquem com outros computadores.|
|**Dispositivos portáteis sem fio**|Habilita a transferência de mídia de um dispositivo de mídia ou câmera habilitada para rede para computadores gerenciados com o MTP (protocolo de transferência de mídia). Essa configuração usa protocolos de rede SSDP e UPnP.|

## <a name="see-also"></a>Ver também
[Políticas para proteger computadores Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)
