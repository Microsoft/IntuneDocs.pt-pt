---
title: "Políticas de firewall para PCs Windows"
description: "O Intune pode ajudá-lo a proteger os PCs que gere com o cliente Intune de várias formas, incluindo ajudá-lo a configurar as definições da Firewall do Windows."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: dd90b483c7fab7b118a55e6e3d9709da52f12e43
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/15/2017
---
# <a name="help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune"></a>Ajudar a proteger PCs com o Windows a utilizarem políticas de Firewall do Windows no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Microsoft Intune pode ajudá-lo a proteger os PCs Windows que gere com o cliente Intune de várias formas. Uma forma como o faz é ao fornecer políticas que lhe permitem configurar as definições da Firewall do Windows nos PCs.

Se ainda não instalou o cliente de PC Windows Intune nos seus computadores, veja o artigo [Instalar o cliente de PC Windows com o Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Utilize as informações nas secções seguintes para o ajudar a configurar, implementar e monitorizar as políticas de Firewall do Windows em PCs Windows.

## <a name="use-intune-policies-to-manage-windows-firewall"></a>Utilizar políticas do Intune para gerir a Firewall do Windows
A política da Firewall do Windows permite-lhe criar e implementar definições que controlam a Firewall do Windows em PCs geridos. Não é possível gerir exceções personalizadas da Firewall do Windows. Estas definições não afetam firewalls de terceiros.

> [!NOTE]
> Se a política do Microsoft Intune e a Política de Grupo estiverem configuradas para gerir a mesma definição no PC, a definição da Política de Grupo sobrepõe-se à política do Microsoft Intune. Para obter informações sobre como evitar conflitos entre a política do Intune e a Política de Grupo, veja o artigo [Resolver conflitos de políticas de GPO e do Microsoft Intune](resolve-gpo-and-microsoft-intune-policy-conflicts.md).
>
> Se pretender implementar as definições da Firewall do Windows em computadores que executem o Windows Vista, primeiro tem de instalar a [Correção KB971800](http://support2.microsoft.com/kb/971800) nesses computadores.

> [!IMPORTANT]
> Para gerir a Firewall do Windows com o Intune, certifique-se de que os dois serviços seguintes estão ativados nos computadores que está a gerir:
>
> -   Firewall do Windows
> -   Agente de Política IPsec

## <a name="configure-a-windows-firewall-policy"></a>Configurar uma política da Firewall do Windows

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), selecione **Política** &gt; **Adicionar Política**.

2.  Configure e implemente uma política das **Definições da Firewall do Windows**. Pode utilizar as definições recomendadas ou personalizar as mesmas. Se precisar de mais informações sobre como criar e implementar políticas, veja o artigo [Tarefas de gestão comuns do PC Windows com o computador cliente do Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

    A secção seguinte apresenta uma lista dos valores que pode configurar na política, bem como dos valores predefinidos que serão utilizados se não personalizar a política.

Depois de implementar uma política da Firewall do Windows, pode ver o respetivo estado na página **Todas as Políticas** da área de trabalho **Política**.

## <a name="specify-policy-settings-for-windows-firewall"></a>Especifique as definições de política da Firewall do Windows

### <a name="turn-on-windows-firewall"></a>Ativar a Firewall do Windows

Estas definições de política ativam a Firewall do Windows em computadores geridos que estão:
- Ligado a um domínio (por exemplo, na área de trabalho)
- Ligado a uma rede privada (fidedigna) (como uma rede doméstica)
- Ligado a uma rede pública não fidedigna (como num café)

O valor predefinido para cada uma destas definições é **Sim**, que é o valor mais seguro.



### <a name="block-all-incoming-connections-including-those-in-the-list-of-allowed-programs"></a>Bloquear todas as ligações recebidas, incluindo as que se encontram na lista de programas permitidos

Estas definições de política configuram a Firewall do Windows para bloquear o tráfego de rede recebido em computadores geridos que são:
- Ligado a um domínio (por exemplo, na área de trabalho)
- Ligado a uma rede privada (fidedigna) (como uma rede doméstica)
- Ligado a uma rede pública não fidedigna (como num café)

O valor predefinido para cada uma destas definições é **Sim**, que é o valor mais seguro.

> [!IMPORTANT]
> Se o seu ambiente incluir computadores geridos a executar o Windows Vista sem service packs instalados, tem de instalar a atualização associada ao [artigo 971800](http://go.microsoft.com/fwlink/?LinkId=188405) na Base de Dados de Conhecimento Microsoft ou desativar as definições de política **Bloquear todas as ligações recebidas** nas políticas implementadas nesses computadores.

### <a name="notify-the-user-when-windows-firewall-blocks-a-new-program"></a>Notificar o utilizador quando a Firewall do Windows bloquear um programa novo

Estas definições de políticas determinam se uma Firewall do Windows notifica um utilizador de PC quando bloqueia tráfego de rede recebido quando o computador gerido está:
- Ligado a um domínio (por exemplo, na área de trabalho)
- Ligado a uma rede privada (fidedigna) (como uma rede doméstica)
- Ligado a uma rede pública não fidedigna (como num café)

O valor predefinido para cada uma destas definições é **Sim**.


### <a name="configure-predefined-exceptions"></a>Configurar exceções predefinidas

Pode configurar exceções que permitam tipos específicos de tráfego de rede através da firewall, independentemente dos valores configurados anteriormente. Nenhuma destas definições está configurada por predefinição.

|Nome da definição|Detalhes|
|------------------|--------------------|
|**BranchCache – Obtenção de Conteúdo**<br>(Windows 7 ou posterior)|Permite que os clientes do BranchCache utilizem HTTP para obter conteúdo de outros clientes do BranchCache no modo distribuído, e a partir da cache alojada enquanto no modo de cache alojada. Esta definição utiliza HTTP.|
|**BranchCache – Cliente de Cache Alojada**<br>(Windows 7 ou posterior)|Permite que os clientes do BranchCache utilizem uma cache alojada. Esta definição utiliza HTTPS.|
|**BranchCache – Servidor de Cache Alojada**|Permite que os clientes do BranchCache utilizem uma cache alojada para comunicar com outros clientes. Esta definição utiliza HTTPS.|
|**BranchCache – Deteção de Elementos da Rede**<br>(Windows 7 ou posterior)|Permite que os clientes do BranchCache utilizem o protocolo Web Services Dynamic Discovery (WS-Discovery) para procurar a disponibilidade de conteúdos na sub-rede local.|
|**Serviço de Colocação em Cache Ponto a Ponto BITS**|Permite que os clientes utilizem o Serviço de Transferência Inteligente em Segundo Plano (BITS) para localizar e partilhar ficheiros armazenados na cache BITS em clientes na mesma sub-rede. Esta definição utiliza os Serviços Web em Dispositivos (WSDAPI) e Chamada de Procedimento Remoto (RPC).|
|**Ligar a um Projetor de Rede**|Permite que os utilizadores se liguem a projetores em redes com ou sem fios para projetar apresentações. Esta definição utiliza WSDAPI.|
|**Componentes Essenciais de Rede**|Permite que os clientes utilizem o IPv4 e o IPv6 para ligar a recursos de rede.|
|**Coordenador de Transações Distribuídas**|Ativa que os computadores geridos coordenem transações que atualizam recursos protegidos por transações, como bases de dados, filas de mensagens e sistemas de ficheiros.|
|**Partilha de Ficheiros e Impressoras**|Ativa que os utilizadores partilhem ficheiros e impressoras locais com outros utilizadores na rede. Esta definição utiliza NetBIOS, Link Local Multicast Name Resolution (LLMNR), protocolo Server Message Block (SMB) e RPC.|
|**Grupo Doméstico**<br>(Windows 7 ou posterior)|Ativa que os computadores geridos participem numa rede de Grupo Doméstico.|
|**Serviço iSCSI**|Ativa que os computadores geridos liguem a dispositivos e servidores iSCSI.|
|**Serviço de Gestão de Chaves**|Permite a contabilização de computadores relativamente à verificação de licenças em ambientes empresariais.|
|**Media Center Extenders**|Ativa que os Media Center Extenders comuniquem com computadores com o Windows Media Center. Esta definição utiliza o Simple Service Discovery Protocol (SSDP) e qWave.|
|**Serviço Netlogon**|Configura um canal de segurança entre os clientes de domínio e um controlador de domínio para a autenticação de utilizadores e serviços. Esta definição utiliza RPC.|
|**Deteção de Redes**|Permite que os computadores detetem e sejam detetados por outros dispositivos na rede. Esta definição utiliza os Serviços de Publicação e Alojamento de Deteção de Funções e protocolos de rede SSDP, NetBIOS, LLMNR e UPnP.|
|**Alertas e Registos de Desempenho**|Ativa a gestão remota do serviço Alertas e Registos de Desempenho. Esta definição utiliza RPC.|
|**Administração Remota**|Ativa a administração remota do computador.|
|**Assistência Remota**|Permite que os utilizadores de computadores geridos peçam assistência remota a outros utilizadores na rede. Esta definição utiliza protocolos de rede SSDP, Peer Name Resolution Protocol (PNRP), Teredo e UPnP.|
|**Ambiente de Trabalho Remoto**|Permite que o computador utilize o Ambiente de Trabalho Remoto para aceder a outros computadores.|
|**Gestão do Registo de Eventos Remoto**|Permite a visualização e gestão remota dos registos de eventos de cliente. Esta definição utiliza Pipes Nomeados e RPC.|
|**Gestão de Tarefas Agendadas Remota**|Ativa a gestão remota do serviço de agendamento de tarefas. Esta definição utiliza RPC.|
|**Gestão do Serviço Remota**|Ativa a gestão remota de serviços locais em clientes. Esta definição utiliza Pipes Nomeados e RPC.|
|**Gestão de Volumes Remota**|Ativa a gestão remota de volumes de discos de software e hardware. Esta definição utiliza RPC.|
|**Encaminhamento e Acesso Remoto**|Ativa ligações VPN recebidas e ligações de acesso remoto a computadores.|
|**Secure Socket Tunneling Protocol (protocolo SSTP)**|Ativa ligações VPN recebidas a computadores geridos com o Secure Socket Tunneling Protocol (SSTP). Esta definição utiliza HTTPS.|
|**Trap SNMP**|Permite aos computadores geridos a receção de tráfego do serviço Trap Simple Network Management Protocol (SNMP).|
|**Estrutura UPnP**|Configura o serviço Estrutura UPnP em computadores para que os mesmos possam detetar e utilizar dispositivos certificados por UPnP.|
|**Serviço de Registo de Nomes de Computadores de Colaboração do Windows**|Permite que os computadores localizem e comuniquem com outros computadores através de SSDP e PNRP.|
|**Windows Media Player**|Permite que os utilizadores recebam transmissão de multimédia em sequência através de User Datagram Protocol (UDP).|
|**Serviço de Partilha de Rede do Windows Media Player**|Permite que os utilizadores partilhem multimédia através de uma rede. Esta definição utiliza os protocolos de rede SSDP, qWave e UPnP.|
|**Serviço de Partilha de Rede do Windows Media Player (Internet)**<br>(Windows 7 ou posterior)|Permite que os utilizadores partilhem multimédia doméstica através da Internet.|
|**Área de Reunião do Windows**|Permite que os utilizadores colaborem através de uma rede para partilhar documentos, programas e do respetivo ambiente de trabalho. Esta definição utiliza os protocolos Distributed File System Replication (DFSR) and P2P.|
|**Fundação de Colaboração Ponto a Ponto do Windows**|Configura vários programas e tecnologias ponto a ponto de modo a ativar que os mesmos se liguem. Esta definição utiliza SSDP e PNRP.|
|**Gestão Remota do Windows (Compatibilidade)**|Ativa a gestão remota de computadores geridos com o WS-Management, um protocolo baseado em serviços Web para a gestão remota de sistemas operativos e dispositivos.|
|**Gestão Remota do Windows**<br>(Windows 8 ou posterior)|Ativa a gestão remota de computadores geridos com o WS-Management, um protocolo baseado em serviços Web para a gestão remota de sistemas operativos e dispositivos.|
|**Windows Virtual PC**<br>(Windows 7 ou posterior)|Permite que as máquinas virtuais comuniquem com outros computadores.|
|**Dispositivos Portáteis Sem Fios**|Ativa a transferência de multimédia de câmaras ou dispositivos multimédia ligados à rede para computadores geridos com do Media Transfer Protocol (MTP). Esta definição utiliza protocolos de rede SSDP e UPnP.|

### <a name="see-also"></a>Consulte também
[Políticas para proteger PCs Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)
