---
# required metadata

title: Gerir PCs Windows com o Intune | Microsoft Intune
description:
keywords:
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Gerir Computadores com Windows com o Microsoft Intune
Além da gestão de dispositivos móveis, também pode utilizar o Intune para gerir PCs Windows que estejam a executar sistemas operativos suportados através do software de cliente de PC Windows do Intune. Os requisitos de hardware e software para executar o cliente de computador são mínimos – basicamente qualquer sistema com capacidade para executar o Windows 7 ou posterior é suportado.  O software de cliente também pode ser facilmente instalado em computadores associados a domínios (em qualquer domínio) ou computadores não associados a domínios.

O Intune gere os PCs Windows através de políticas semelhantes às utilizadas pelos Objetos de Política de Grupo (GPOs) dos Serviços de Domínio do Active Directory do Windows Server (AD DS). Se pretende gerir computadores associados a domínios do Active Directory com o Intune, deve [certificar-se de que as políticas do Intune não entram em conflito com quaisquer GPOs](resolve-gpo-and-microsoft-intune-policy-conflicts.md) que estejam implementadas na sua organização.

> [!NOTE]
> O Microsoft Intune como serviço autónomo disponibiliza estas funcionalidades para a gestão de computadores. Os dispositivos que estejam a executar o Windows 8.1 podem ser geridos através de um cliente do Intune ou podem ser inscritos como dispositivos móveis. As informações abaixo aplicam-se a computadores que estejam a executar o cliente do Intune.

## Requisitos para a gestão de PCs do Intune

**Hardware**:

|Seguem-se os requisitos mínimos de hardware para instalar o cliente do Intune:|Requisito|
|---------------|--------------------|
|Mais informações|Rede|
|O cliente requer o computador para ter ligação à Internet.|Processador e Memória|
|Consulte os requisitos de processador e RAM do sistema operativo do computador.|Espaço em disco|

200 MB de espaço disponível no disco antes da instalação do software do cliente.

|**Software**:|Seguem-se os requisitos de software para instalar o cliente:|
|---------------|--------------------|
|Requisito|Mais informações|
|Permissões administrativas|A conta que instalar o software do cliente tem de ter permissões de administrador local nesse computador.<br /><br />Windows Installer 3.1<br /><br />O computador tem de ter instalado, no mínimo, o Windows Installer 3.1.<br /><br />Para ver a versão existente do Windows Installer num computador:|
|-   No PC, clique com o botão direito do rato em **%windir%\System32\msiexec.exe** e, em seguida, clique em **Propriedades**|Pode transferir a versão mais recente do Windows Installer em [Redistribuíveis do Windows Installer](http://go.microsoft.com/fwlink/?LinkID=234258) no site da Microsoft Developer Network.|

## Remover software de cliente incompatível
Antes de instalar o software de cliente do Intune, tem de desinstalar qualquer software de cliente do Configuration Manager ou do System Management Server desse PC. Instalar o cliente do computador Intune

-   O primeiro passo na gestão de PCs Windows com o Intune é instalar o cliente. O software de cliente pode ser instalado quando um PC for inscrito na gestão pelo serviço do Intune de uma das seguintes formas:

    Pode [implementar manualmente o software de cliente do Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md#to-manually-deploy-the-client-software). Neste tipo de implementação, um administrador transfere o software de cliente Intune e instala-o manualmente em cada computador.

-   Para transferir o software de cliente Intune, abra a consola de administração do Intune e, na área de Transferência de Software de cliente, transfira o pacote de software de cliente.

-   Depois de o software de cliente estar instalado, o Intune instala automaticamente o software adicional, conforme necessário, para gerir o computador. Pode utilizar os mesmos ficheiros que transfere para instalar manualmente o cliente do Intune para [implementar o cliente em computadores associados a domínios através de GPOs do Active Directory](install-the-windows-pc-client-with-microsoft-intune.md#to-automatically-deploy-the-client-software-by-using-group-policy)

-   [Os utilizadores finais podem inscrever cada um dos respetivos computadores](install-the-windows-pc-client-with-microsoft-intune.md#how-users-can-self-enroll-their-computers) através do Portal da Empresa do Intune.

## Cada computador inscrito é então ligado automaticamente à conta de utilizador utilizada para instalar o software de cliente do Intune.
Por fim, também pode implementar o software de cliente do Intune em computadores como parte de uma [implementação do sistema operativo](install-the-windows-pc-client-with-microsoft-intune.md#install-the-microsoft-intune-client-software-as-part-of-an-image)

Gestão de computadores com o cliente de computador do Intune

-   Depois de o cliente do Intune estar instalado, o software de cliente permite várias capacidades de gestão de computador, incluindo: [gestão de aplicações](deploy-apps-in-microsoft-intune.md), Endpoint Protection, inventário de hardware e software, controlo remoto (através de pedidos de assistência remota), atualizações de software e elaboração de relatórios sobre definições de compatibilidade.

-   Várias tarefas de gestão de computador ativadas pelo cliente do computador são geridas através de políticas do Intune, como:

-   Configurar as [definições da Firewall do Windows](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) nos computadores geridos.

Configurar as [definições de atualizações de software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) para computadores geridos para procurar e transferir atualizações de software necessárias.

-   Ajudar a proteger os computadores geridos de potenciais ameaças e software malicioso através da gestão de [monitorização em tempo real e do Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).

-   Além das ações do agente de cliente do Intune executadas localmente nos computadores individuais, também pode utilizar a consola de administração do Intune para executar outras [tarefas de gestão de computador comuns](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) em PCs Windows com o cliente instalado para:

-   Ver informações de inventário de hardware e de software acerca dos computadores geridos.

-   Para reiniciar um computador remotamente

-   Extinguir um computador para desinstalar o software de cliente e removê-lo da gestão com o Intune

Ligar utilizadores a computadores geridos específicos Responder a pedidos de assistência remota


<!--HONumber=May16_HO2-->


