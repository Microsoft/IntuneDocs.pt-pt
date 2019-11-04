---
title: Gerir PCs com software de cliente no Microsoft Intune - Azure | Microsoft Docs
description: Efetue a gestão de PCs Windows instalando o software de cliente do Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/15/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb67cf2cb17b78c4034c3b73e229e160723d975e
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414396"
---
# <a name="manage-windows-pcs-as-computers-via-intune-software-client"></a>Gerir PCs Windows como computadores através do cliente de software do Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

> [!WARNING]
> A Microsoft anunciou que [o suporte do Windows 7 termina a 14 de Janeiro de 2020](https://support.microsoft.com/help/4057281/windows-7-support-will-end-on-january-14-2020). Nesta data, o Intune também retira o suporte para dispositivos com o Windows 7. A Microsoft recomenda vivamente que passe para o Windows 10 para evitar interrupções de serviço ou suporte.
> 
> Para obter mais informações, consulte [planejamento para alteração do Intune: perto do fim do suporte para o Windows 7](../fundamentals/whats-new.md#intune-plan-for-change-nearing-end-of-support-for-windows-7).

> [!NOTE]
> Pode utilizar o Microsoft Intune para gerir PCs com Windows [como dispositivos móveis com a gestão de dispositivos móveis (MDM)](../enrollment/windows-enroll.md) ou como computadores com o cliente de software do Intune, conforme descrito abaixo. No entanto, a Microsoft recomenda que os clientes [utilizem a solução de gestão MDM](../enrollment/windows-enroll.md) sempre que possível. Para obter mais informações, consulte [comparar o gerenciamento de computadores Windows como computadores ou dispositivos móveis](pc-management-comparison.md) 

O Intune oferece uma solução abrangente de gestão de dispositivos móveis para organizações. O Intune pode gerir PCs Windows como dispositivos móveis através das capacidades de gestão de dispositivos modernas incorporadas no sistema operativo do Windows 10. Para satisfazer as necessidades de gestão da sua organização, o Intune também pode gerir PCs Windows como computadores com o software de cliente do Intune. Este método de gestão utiliza capacidades de gestão de computadores tradicionais no sistema operativo Windows legado.

O cliente de software do Intune é mais adequado para PCs Windows que executem sistemas operativos legados, tais como o Windows 7, que não podem ser geridos como dispositivos móveis. O cliente de software do Intune utiliza as capacidades de gestão, como a Política de Grupo, para gerir os PCs a partir da cloud.

O Intune suporta a gestão de PCs Windows como computadores através do cliente de software para um máximo de 7000 PCs. Para implementações maiores, faça a gestão dos PCs Windows 10 como dispositivos móveis. Cada versão do Intune e atualização do Windows 10 inclui funcionalidades de gestão com base na arquitetura de gestão de dispositivos móveis. Recomendamos que mova a sua organização para o Windows 10 gerido como dispositivos móveis.

> [!NOTE]
> Pode gerir dispositivos com o Windows 8.1 e posterior, como PCs através do software de cliente do Intune ou como dispositivos móveis. Não pode utilizar ambos os métodos no mesmo dispositivo. Pondere com atenção antes de decidir gerir os PCs com software de cliente do Intune. Este tópico aplica-se apenas à gestão de dispositivos como PCs ao executar o software de cliente do Intune.

## <a name="requirements-for-intune-pc-client-management"></a>Requisitos para a gestão do cliente de PC do Intune

**Hardware**:  
Veja a seguir os requisitos mínimos de hardware para instalar o software cliente do Intune:

|Requisito|Mais informações|
|---------------|--------------------|
|Rede|O cliente requer o computador para ter ligação à Internet.|
|Processador e Memória|Consulte os requisitos de processador e RAM do sistema operativo do computador.|
|Espaço em disco|200 MB de espaço disponível no disco antes da instalação do software do cliente.|

**Software**:  
Veja a seguir os requisitos de software para a instalação do software cliente do:

|Requisito|Mais informações|
|---------------|--------------------|
|Sistema operativo | Dispositivo Windows com Windows 7 SP1 e Windows 8.1 ou posterior. </br></br>**As versões Home Edition não são suportadas.**|
|Permissões administrativas|A conta que instala o software de cliente tem de ter permissões de administrador local no dispositivo.|
|Windows Installer 3.1|O computador tem de ter instalado, no mínimo, o Windows Installer 3.1.<br /><br />Para ver a versão existente do Windows Installer num computador:<br /><br />  No PC, clique com o botão direito do rato em **%windir%\System32\msiexec.exe** e, em seguida, clique em **Propriedades**.<br /><br />Pode transferir a versão mais recente do Windows Installer em [Redistribuíveis do Windows Installer](https://go.microsoft.com/fwlink/?LinkID=234258) no site da Microsoft Developer Network.|
|Remover software de cliente incompatível|Antes de instalar o software de cliente do Intune, desinstale todo o software de cliente do Configuration Manager, Operations Manager e Service Manager desse PC.|

## <a name="deploying-the-intune-software-client"></a>Implementar o cliente de software do Intune
Como administrador do Intune, pode disponibilizar o cliente de software do Intune aos utilizadores de várias formas. Para obter orientações, veja [Instalar o cliente de software do Intune em PCs Windows](../install-the-windows-pc-client-with-microsoft-intune.md).

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>Capacidades de gestão de computadores do software de cliente do Intune
Na maioria dos cenários, irá inscrever os dispositivos no Microsoft Intune, o que fornece um conjunto maior de capacidades. No entanto, também pode gerir os PCs com o cliente de software do Intune, que proporciona as seguintes funcionalidades:

- **[Gestão de atualizações de software](../keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)** pode manter os PCs atualizados e decidir quando as atualizações são aplicadas.

- **[Política de Firewall do Windows](../help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)** ajuda a garantir que nenhum PC utilizado na sua empresa tem uma Firewall do Windows configurada incorretamente ou inativa.

- **[Proteção antimalware](../help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)** o Intune inclui o Endpoint Protection, que ajuda a proteger os seus PCs de software malicioso.

- **[Assistência remota](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)** o Intune permite que os utilizadores contactem os técnicos de suporte de TI, que podem fornecer assistência através de uma funcionalidade de ambiente de trabalho remoto incluída no Intune (requer o software TeamViewer).

- **[Gestão de licenças de software](../manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)** controle quantas licenças de software estão disponíveis e quantas licenças disponíveis estão a ser utilizadas.
- **[Implementação de aplicações](add-apps-for-windows-pcs-in-microsoft-intune.md)** implemente software em PCs geridos por si. Algumas funcionalidades de gestão de aplicações não estão disponíveis ao gerir PCs com o cliente de software.

<!-- - **Compliance settings reporting** -->

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>Políticas e implementações de aplicações do software de cliente do Intune

Embora o software de cliente do Intune suporte [capacidades de gestão que ajudam a proteger PCs](policies-to-protect-windows-pcs-in-microsoft-intune.md) ao gerir atualizações de software, a firewall do Windows e o Endpoint Protection, os PCs geridos com o software de cliente do Intune não podem ser segmentados com outras políticas do Intune, incluindo essas definições da política do **Windows** específicas da gestão do dispositivo móvel.

Quando utiliza o software de cliente do Intune para gerir PCs Windows, pode utilizar apenas as políticas apresentadas na secção **Gestão de Computadores**.

O Intune faz a gestão dos PCs Windows através de políticas semelhantes às utilizadas pelos Objetos de Política de Grupo (GPOs) dos Serviços de Domínio do Active Directory (AD DS) do Windows Server. Se gerir computadores associados a domínios do Active Directory com o Intune, [confirme que as políticas do Intune não entram em conflito com outros GPOs](resolve-gpo-and-microsoft-intune-policy-conflicts.md) utilizados na sua organização. Para obter mais informações, veja [Group Policy for beginners (Política de Grupo para principiantes)](https://technet.microsoft.com/library/hh147307.aspx).

  ![Selecionar modelo para a nova política do PC Windows](./media/manage-windows-pcs-with-microsoft-intune/select-template-for-pc-policy.png)

Quando estiver a implementar aplicações, pode utilizar apenas o Windows Installer (.exe, .msi).

  ![Selecionar a plataforma e a localização para os ficheiros de software de cliente de PC](./media/manage-windows-pcs-with-microsoft-intune/select-platform-of-software-files-for-pc-agent.png)

## <a name="common-tasks-for-windows-pcs"></a>Tarefas comuns dos PCs Windows

Pode utilizar a consola de administração do Intune para realizar outras tarefas comuns de gestão de computadores nos PCs Windows que tenham o cliente instalado:
- [Utilizar políticas para simplificar a gestão de PCs](use-policies-to-simplify-windows-pc-management.md) – Descreve as políticas de **Gestão de Computadores** do Intune e lista as definições do Microsoft Intune Center.

- [Ver o inventário de hardware e software dos PCs Windows](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md) – Explica como criar um relatório que lista as informações sobre as capacidades do hardware dos PCs e o software instalado nos mesmos. Também explica como atualizar o inventário dos PCs para garantir que está atualizado.
- [Extinguir um PC Windows](retire-a-windows-pc-with-microsoft-intune.md) – Lista os passos para extinguir um PC Windows e descreve o que acontece quando extingue um PC.
- [Gerir a associação utilizador-dispositivo dos PCs Windows](../manage-user-device-linking-for-windows-pcs-with-microsoft-intune.md) – Explica quando e como precisa de associar um utilizador a um PC antes de implementar software para o utilizador.
- [Pedir e fornecer assistência remota para PCs Windows](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md) – Explica como os utilizadores de PCs do Intune obtêm a ajuda de assistência remota do utilizador e descreve os pré-requisitos e a configuração do TeamViewer.

Para obter mais informações sobre as tarefas mencionadas acima, veja [Tarefas comuns de gestão de computadores](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

## <a name="management-limitations-of-the-intune-client-software"></a>Limitações de gestão do software de cliente do Intune

Algumas opções de gestão, que podem ser utilizadas para gerir os PCs como dispositivos móveis, não podem ser utilizadas para PCs que sejam geridos com o software de cliente do Intune:

- Eliminação completa (a eliminação seletiva está disponível)
- Conditional Access

Tenha também em atenção que na consola de administração do Intune, certas secções como **Atualizações**, **Proteção** e **Licenças** só serão apresentadas se tiver inscrito os dispositivos com o software de cliente do Intune.

  ![Itens da consola de administrador que são apresentados apenas para clientes de PC](./media/manage-windows-pcs-with-microsoft-intune/admin-console-settings-only-for-pc-agent.png)

## <a name="help-with-troubleshooting"></a>Ajuda na resolução de problemas

Normalmente, o software de cliente do Intune é executado de forma discreta em segundo plano sem exigir demasiada interação ou resolução de problemas por parte do utilizador. Se tiver de resolver problemas de gestão do PC, pode verificar os registos. O software de cliente do Intune e os registos correspondentes são instalados no diretório %Program Files%\Microsoft\OnlineManagement.

Também pode ver a [inscrição de dispositivos](../enrollment/device-enrollment.md) para obter mais informações sobre inscrever dispositivos com o Microsoft Intune.
