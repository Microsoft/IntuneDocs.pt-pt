---
title: Gerir PCs com software de cliente | Documentos da Microsoft
description: "Efetue a gestão de PCs Windows instalando o software de cliente do Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3d2f3a7233ea7a5127baf5a08be1ccb41f717244
ms.openlocfilehash: 4344251ede6d8cc338d84782d224d87fd78d5bd8


---

# <a name="manage-windows-pcs-with-intune-pc-client-software"></a>Gerir PCs Windows com o software de cliente de PC do Intune
Em vez de [inscrever PCs Windows como dispositivos móveis](set-up-windows-device-management-with-microsoft-intune.md), pode inscrever e gerir PCs Windows ao instalar o software de cliente do Intune.

O Intune gere os PCs Windows através de políticas semelhantes às utilizadas pelos Objetos de Política de Grupo (GPOs) dos Serviços de Domínio do Active Directory do Windows Server (AD DS). Se pretende gerir computadores associados a domínios do Active Directory com o Intune, [certifique-se de que as políticas do Intune não entram em conflito com quaisquer GPOs](resolve-gpo-and-microsoft-intune-policy-conflicts.md) que estejam implementadas na sua organização.

Embora o cliente de software do Intune suporte [capacidades de gestão que ajudam a proteger PCs](policies-to-protect-windows-pcs-in-microsoft-intune.md) ao gerir atualizações de software, a firewall do Windows e o Endpoint Protection, os PCs geridos com o cliente de software do Intune não podem ser segmentados com outras políticas do Intune, incluindo essas definições da política do **Windows** específicas da gestão do dispositivo móvel.

> [!NOTE]
> Pode gerir dispositivos Windows 8.1 ou posterior como PCs através do cliente do Intune ou como dispositivos móveis com a funcionalidade de gestão de dispositivos móveis (MDM). Não pode utilizar ambos os métodos em conjunto. Este tópico aplica-se apenas à gestão de dispositivos como PCs ao executar o cliente de software do Intune.

## <a name="requirements-for-intune-pc-client-management"></a>Requisitos para a gestão do cliente de PC do Intune

**Hardware**: seguem-se os requisitos mínimos de hardware para instalar o cliente do Intune:

|Requisito|Mais informações|
|---------------|--------------------|
|Rede|O cliente requer o computador para ter ligação à Internet.|
|Processador e Memória|Consulte os requisitos de processador e RAM do sistema operativo do computador.|
|Espaço em disco|200 MB de espaço disponível no disco antes da instalação do software do cliente.|

**Software**: seguem-se os requisitos de software para instalar o cliente:

|Requisito|Mais informações|
|---------------|--------------------|
|Sistema operativo | Dispositivo Windows a executar o Windows Vista ou posterior. As versões Home Edition não são suportadas.|
|Permissões administrativas|A conta que instala o software de cliente tem de ter permissões de administrador local no dispositivo.|
|Windows Installer 3.1|O computador tem de ter instalado, no mínimo, o Windows Installer 3.1.<br /><br />Para ver a versão existente do Windows Installer num computador:<br /><br />  No PC, clique com o botão direito do rato em **%windir%\System32\msiexec.exe** e, em seguida, clique em **Propriedades**.<br /><br />Pode transferir a versão mais recente do Windows Installer em [Redistribuíveis do Windows Installer](http://go.microsoft.com/fwlink/?LinkID=234258) no site da Microsoft Developer Network.|
|Remover software de cliente incompatível|Antes de instalar o software de cliente do Intune, desinstale qualquer software de cliente do Configuration Manager, Operations Manager, Operations Management Suite e Service Manager desse PC.|

## <a name="computer-management-with-the-intune-computer-client"></a>Gestão de computadores com o cliente de computador do Intune
Uma vez que o software de cliente do Intune esteja instalado, as capacidades de gestão incluem: 

- [Gestão de aplicações](deploy-apps-in-microsoft-intune.md)

- [Monitorização em tempo real e Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)

- [Gestão de definições da Firewall do Windows](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md), inventário de hardware e software, controlo remoto (através de pedidos de assistência remota)

- [Definições de atualização de software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)

- Relatórios de definições de compatibilidade

Determinadas opções de gestão disponíveis para PCs geridos como dispositivos móveis estão disponíveis para os PCs com software gerido pelo cliente, incluindo:

-   Eliminação completa (a eliminação seletiva está disponível)

-   Acesso condicional

-   Políticas de Windows, excetuando as políticas de **Gestão de computadores**

  ![Modelo de políticas para PCs Windows](../media/pc_policy_template.png)

Além das ações do agente de cliente do Intune executadas localmente nos computadores individuais, também pode utilizar a consola de administração do Intune para executar outras [tarefas de gestão de computador comuns](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) em PCs Windows com o cliente instalado para:

-   Ver informações de inventário de hardware e de software acerca dos computadores geridos.

-   Para reiniciar um computador remotamente

-   Extinguir um computador para desinstalar o software de cliente e removê-lo da gestão com o Intune

-   Ligar utilizadores a computadores geridos específicos

-   Responder a pedidos de assistência remota

Normalmente, o agente de cliente do Intune é executado silenciosamente, em segundo plano, sem que seja necessária uma grande interação por parte do utilizador ou a resolução de problemas. No entanto, se necessitar de ajuda para resolver problemas de gestão do computador, existem vários [recursos disponíveis para o ajudar a resolvê-los](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune).



<!--HONumber=Dec16_HO3-->


