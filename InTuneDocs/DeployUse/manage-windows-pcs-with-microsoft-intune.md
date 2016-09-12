---
title: Gerir PCs com software de cliente | Microsoft Intune
description: "Efetue a gestão de PCs Windows instalando o software de cliente do Intune."
keywords: 
author: nathbarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cf471320f122eea7804ff6cd6cad208f8cd5a692
ms.openlocfilehash: f264dc3740ce9b117fcc01c39792904a2dc6e7ab


---

# Gerir PCs Windows com o software de cliente de PC do Intune
Em vez de [inscrever PCs Windows como dispositivos móveis](set-up-windows-device-management-with-microsoft-intune.md), pode inscrever e gerir PCs Windows ao instalar o software de cliente do Intune.

O Intune gere os PCs Windows através de políticas semelhantes às utilizadas pelos Objetos de Política de Grupo (GPOs) dos Serviços de Domínio do Active Directory do Windows Server (AD DS). Se pretende gerir computadores associados a domínios do Active Directory com o Intune, deve [certificar-se de que as políticas do Intune não entram em conflito com quaisquer GPOs](resolve-gpo-and-microsoft-intune-policy-conflicts.md) que estejam implementadas na sua organização.

Embora o cliente de software do Intune suporte [funcionalidades de gestão que ajudam a proteger PCs](policies-to-protect-windows-pcs-in-microsoft-intune.md) ao gerir atualizações de software, a Firewall do Windows e o Endpoint Protection, os PCs geridos com o cliente do Intune não podem ser segmentados com outras políticas do Intune, incluindo essas definições da política do **Windows** específicas da gestão do dispositivo móvel.

> [!NOTE]
> Os dispositivos que estejam a executar o Windows 8.1 ou posterior podem ser geridos através de um cliente do Intune ou podem ser inscritos como dispositivos móveis. As informações abaixo aplicam-se a computadores que estejam a executar o cliente do Intune. A instalação do cliente de PC do Intune e a inscrição de dispositivos Windows para gestão de dispositivos móveis em simultâneo não é suportada.

## Requisitos para a gestão do cliente de PC do Intune

**Hardware**: seguem-se os requisitos mínimos de hardware para instalar o cliente do Intune:

|Requisito|Mais informações|
|---------------|--------------------|
|Rede|O cliente requer o computador para ter ligação à Internet.|
|Processador e Memória|Consulte os requisitos de processador e RAM do sistema operativo do computador.|
|Espaço em disco|200 MB de espaço disponível no disco antes da instalação do software do cliente.|

**Software**: seguem-se os requisitos de software para instalar o cliente:

|Requisito|Mais informações|
|---------------|--------------------|
|Sistema operativo | Dispositivo Windows com Windows 7 ou posterior |
|Permissões administrativas|A conta que instala o software de cliente tem de ter permissões de administrador local no dispositivo.|
|Windows Installer 3.1|O computador tem de ter instalado, no mínimo, o Windows Installer 3.1.<br /><br />Para ver a versão existente do Windows Installer num computador:<br /><br />-   No computador, clique com o botão direito do rato em **%windir%\System32\msiexec.exe** e, em seguida, clique em **Propriedades**.<br /><br />Pode transferir a versão mais recente do Windows Installer em [Redistribuíveis do Windows Installer](http://go.microsoft.com/fwlink/?LinkID=234258) no site da Microsoft Developer Network.|
|Remover software de cliente incompatível|Antes de instalar o software de cliente do Intune, tem de desinstalar qualquer software de cliente do Configuration Manager ou do System Management Server desse PC.|

## Instalar o cliente do computador Intune
O software de cliente do Intune pode ser instalado das seguintes formas:

-  [Implementar manualmente o software de cliente do Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md#to-manually-deploy-the-client-software). Neste tipo de implementação, um administrador transfere o software de cliente Intune e instala-o manualmente em cada computador.

  Para transferir o software de cliente do Intune, abra a [consola de administração do Intune](https://manage.microsoft.com), escolha **Administração** > **Transferência de Software de Cliente** e clique em **Transferir Software de Cliente**.

-  Utilize os mesmos ficheiros que transfere para instalar manualmente o software de cliente do Intune para [implementar o cliente em computadores associados a domínios através de GPOs do Active Directory](install-the-windows-pc-client-with-microsoft-intune.md#to-automatically-deploy-the-client-software-by-using-group-policy).

-  Implemente o software de cliente do Intune em computadores como parte de uma [implementação do sistema operativo](install-the-windows-pc-client-with-microsoft-intune.md#install-the-microsoft-intune-client-software-as-part-of-an-image).

-  Envie instruções de utilizadores com o URL do Portal da Empresa do Intune, [https://portal.manage.microsoft.com](http://go.microsoft.com/fwlink/?LinkId=825632). Quando abrem o Portal da Empresa, os utilizadores recebem um pedido para inscrever os respetivos PCs ao transferir e executar o software de cliente do Intune.

## Gestão de computadores com o cliente de computador do Intune
Após instalar o software de cliente do Intune, o software de cliente permite várias capacidades de gestão de computador, incluindo: [gestão de aplicações](deploy-apps-in-microsoft-intune.md), Endpoint Protection, inventário de hardware e software, controlo remoto (através de pedidos de assistência remota), atualizações de software e elaboração de relatórios sobre definições de compatibilidade.

Várias tarefas de gestão de computador ativadas pelo cliente do computador são geridas através de políticas do Intune, como:

-   Configurar as [definições da Firewall do Windows](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) nos computadores geridos.

-   Configurar as [definições de atualizações de software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) para computadores geridos para procurar e transferir atualizações de software necessárias.

-   Ajudar a proteger os computadores geridos de potenciais ameaças e software malicioso através da gestão de [monitorização em tempo real e do Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).

![Modelo de políticas para PCs Windows](../media/pc_policy_template.png)

Além das ações do agente de cliente do Intune executadas localmente nos computadores individuais, também pode utilizar a consola de administração do Intune para executar outras [tarefas de gestão de computador comuns](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) em PCs Windows com o cliente instalado para:

-   Ver informações de inventário de hardware e de software acerca dos computadores geridos.

-   Para reiniciar um computador remotamente

-   Extinguir um computador para desinstalar o software de cliente e removê-lo da gestão com o Intune

-   Ligar utilizadores a computadores geridos específicos

-   Responder a pedidos de assistência remota

Normalmente, o agente de cliente do Intune é executado silenciosamente, em segundo plano, sem que seja necessária uma grande interação por parte do utilizador ou a resolução de problemas. No entanto, se necessitar de ajuda para resolver problemas de gestão do computador, existem vários [recursos disponíveis para o ajudar a resolvê-los](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune).



<!--HONumber=Aug16_HO4-->


