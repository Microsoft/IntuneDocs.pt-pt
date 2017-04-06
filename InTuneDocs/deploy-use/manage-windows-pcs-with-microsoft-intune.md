---
title: Gerir PCs com software de cliente | Documentos da Microsoft
description: "Efetue a gestão de PCs Windows instalando o software de cliente do Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: c66226b7fc31f91669c4f4f0693ccbd7c679189f
ms.openlocfilehash: 74f2848dcd2863022dac44cf302b330a99cf1a55
ms.lasthandoff: 03/29/2017


---

# <a name="manage-windows-pcs-with-intune-pc-client-software"></a>Gerir PCs Windows com o software de cliente de PC do Intune
A [inscrição de PCs Windows como dispositivos móveis](set-up-windows-device-management-with-microsoft-intune.md) é o método preferencial de inscrição de PCs Windows no Intune. No entanto, como administrador de TI, pode optar por inscrever e gerir PCs Windows ao instalar o software de cliente do Intune, conforme descrito neste tópico. O cliente de software do Intune não é suportado com a inscrição como um dispositivo móvel.

O Intune gere os PCs Windows através de políticas semelhantes às utilizadas pelos Objetos de Política de Grupo (GPOs) dos Serviços de Domínio do Active Directory do Windows Server (AD DS). Se pretende gerir computadores associados a domínios do Active Directory com o Intune, [certifique-se de que as políticas do Intune não entram em conflito com quaisquer GPOs](resolve-gpo-and-microsoft-intune-policy-conflicts.md) que estejam implementadas na sua organização. Pode ler mais sobre [GPOs](https://technet.microsoft.com/library/hh147307.aspx).

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>Políticas e implementações de aplicações do software de cliente do Intune

Embora o software de cliente do Intune suporte [capacidades de gestão que ajudam a proteger PCs](policies-to-protect-windows-pcs-in-microsoft-intune.md) ao gerir atualizações de software, a firewall do Windows e o Endpoint Protection, os PCs geridos com o software de cliente do Intune não podem ser segmentados com outras políticas do Intune, incluindo essas definições da política do **Windows** específicas da gestão do dispositivo móvel.

Quando utiliza o software de cliente do Intune para gerir PCs Windows, pode utilizar apenas as políticas apresentadas na secção **Gestão de Computadores**.

  ![Selecionar modelo para a nova política do PC Windows](../media/select-template-for-pc-policy.png)

Para obter as descrições detalhadas das políticas que pode definir, veja:

- [Utilizar políticas para ajudar a proteger PCs Windows que executem o software de cliente do Intune](https://docs.microsoft.com/intune/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)
- [Manter os PCs Windows atualizados com atualizações de software no Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)
- [Ajudar a proteger os PCs Windows através de políticas de Firewall do Windows no Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)
- [Ajudar a proteger os PCs Windows com o Endpoint Protection para o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

Além disso, quando implementar aplicações, pode utilizar apenas o Windows Installer (.exe, .msi).

  ![Selecionar a plataforma e a localização para os ficheiros de software de cliente de PC](../media/select-platform-of-software-files-for-pc-agent.png)

> [!NOTE]
> Pode gerir dispositivos com o Windows 8.1 ou posterior como PCs através do software de cliente do Intune ou como dispositivos móveis com a funcionalidade de gestão de dispositivos móveis (MDM). Não pode utilizar ambos os métodos em conjunto, por isso pondere cuidadosamente a sua decisão antes de decidir gerir PCs com o software de cliente do Intune. Este tópico aplica-se apenas à gestão de dispositivos como PCs ao executar o software de cliente do Intune.

## <a name="requirements-for-intune-pc-client-management"></a>Requisitos para a gestão do cliente de PC do Intune

**Hardware**: seguem-se os requisitos mínimos de hardware para instalar o software de cliente do Intune:

|Requisito|Mais informações|
|---------------|--------------------|
|Rede|O cliente requer o computador para ter ligação à Internet.|
|Processador e Memória|Consulte os requisitos de processador e RAM do sistema operativo do computador.|
|Espaço em disco|200 MB de espaço disponível no disco antes da instalação do software do cliente.|

**Software**: seguem-se os requisitos de software para instalar o software de cliente:

|Requisito|Mais informações|
|---------------|--------------------|
|Sistema operativo | Dispositivo Windows a executar o Windows Vista ou posterior. </br></br>**As versões Home Edition não são suportadas.**|
|Permissões administrativas|A conta que instala o software de cliente tem de ter permissões de administrador local no dispositivo.|
|Windows Installer 3.1|O computador tem de ter instalado, no mínimo, o Windows Installer 3.1.<br /><br />Para ver a versão existente do Windows Installer num computador:<br /><br />  No PC, clique com o botão direito do rato em **%windir%\System32\msiexec.exe** e, em seguida, clique em **Propriedades**.<br /><br />Pode transferir a versão mais recente do Windows Installer em [Redistribuíveis do Windows Installer](http://go.microsoft.com/fwlink/?LinkID=234258) no site da Microsoft Developer Network.|
|Remover software de cliente incompatível|Antes de instalar o software de cliente do Intune, desinstale qualquer software de cliente do Configuration Manager, Operations Manager, Operations Management Suite e Service Manager desse PC.|

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>Capacidades de gestão de computadores do software de cliente do Intune

Uma vez que o software de cliente do Intune esteja instalado, as capacidades de gestão incluem:

- [Gestão de aplicações](deploy-apps-in-microsoft-intune.md)

- [Monitorização em tempo real e Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) – o Endpoint Protection é o mesmo que o Windows Defender. O Endpoint Protection aplica-se ao Windows 7 e Windows 8. Para o Windows 10 e versões posteriores, o nome de produto foi alterado para Windows Defender.

- [Gestão de definições da Firewall do Windows](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md), inventário de hardware e software, controlo remoto (através de pedidos de assistência remota)

- [Definições de atualização de software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)

- Relatórios de definições de compatibilidade

Na consola de administração do Intune, certas secções como "Atualizações", "Proteção" e "Licenças" só aparecem se tiver inscrito dispositivos com o cliente de software do Intune.

  ![Itens da consola de administrador que são apresentados apenas para clientes de PC](../media/admin-console-settings-only-for-pc-agent.png)

Também pode utilizar a consola de administração do Intune para realizar outras tarefas comuns de gestão de computadores nos PCs Windows que tenham o cliente instalado:

-   Ver informações de inventário de hardware e de software acerca dos computadores geridos.
-   Para reiniciar um computador remotamente
-   Extinguir um computador para desinstalar o software de cliente e removê-lo da gestão com o Intune
-   Ligar utilizadores a computadores geridos específicos
-   Responder a pedidos de assistência remota

Para obter mais informações sobre as tarefas mencionadas acima, veja [Tarefas comuns de gestão de computadores](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

## <a name="management-limitations-of-the-intune-client-software"></a>Limitações de gestão do software de cliente do Intune

Algumas opções de gestão, que podem ser utilizadas para gerir os PCs como dispositivos móveis, não podem ser utilizadas para PCs que sejam geridos com o software de cliente do Intune:

-   Eliminação completa (a eliminação seletiva está disponível)

-   Acesso condicional

## <a name="help-with-troubleshooting"></a>Ajuda na resolução de problemas

Normalmente, o software de cliente do Intune é executado de forma discreta em segundo plano sem exigir demasiada interação ou resolução de problemas por parte do utilizador. Se tiver de resolver problemas de gestão do PC, pode verificar os registos. O software de cliente do Intune e os registos correspondentes são instalados no diretório %Program Files%\Microsoft\OnlineManagement.

Também pode rever [Resolver problemas de configuração do cliente no Microsoft Intune](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune) para verificar a existência de problemas que possam ocorrer, bem como quaisquer resoluções ou soluções.

