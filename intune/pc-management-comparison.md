---
title: Comparar opções de gestão de PCs Windows
titleSuffix: Microsoft Intune
description: Inscrição de dispositivos iOS pertencentes à empresa através do Programa de Registo de Aparelho (DEP) da Apple ou do Apple Configurator.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 47c5892541359263383621307d269936f01fa2c6
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041534"
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>Comparar a gestão de PCs Windows como computadores ou dispositivos móveis

[!INCLUDE [classic-portal](includes/classic-portal.md)]

As organizações podem utilizar o Microsoft Intune para gerir PCs Windows como dispositivos móveis com a gestão de dispositivos móveis (MDM) ou como computadores com o cliente de software do Intune.  A Microsoft recomenda que os clientes utilizem a solução de gestão MDM sempre que possível. Para ajudá-lo a compreender melhor as diferenças entre estas opções, o gráfico a seguir compara as duas opções de gestão.

|**Capacidade/cenário** |**Windows como Computador**<br>Cliente de software do Intune | **Windows como Dispositivo Móvel**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**Sistemas operativos** |Windows 10, Windows 8 e posterior, Windows 7, Windows Vista | Windows 10 e posterior |
|**Suporte do Portal do Intune** |[Consola do Silverlight](https://manage.microsoft.com)|[Portal do Azure](https://portal.azure.com) |
|**Acesso condicional**|Não disponível|Disponível <br>[O que é o acesso condicional?](conditional-access.md)|
|**Inscrição em massa**|Não disponível|Disponível <br>[Inscrição em massa para dispositivos Windows](windows-bulk-enroll.md)|
|**Perfis de dispositivo**|Não disponível|Disponível <br>[O que são os perfis de dispositivos do Microsoft Intune?](device-profiles.md)|
|**Inscrição sem agente**|Não disponível |Disponível<br>[Inscrever dispositivos Windows](windows-enroll.md)|
|**Gestão de atualizações de software**| Atualizações do Windows e atualizações de aplicações da Microsoft<br>[Manter os PCs Windows atualizados com as atualizações de software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)|Loja Microsoft para Empresas para as atualizações de aplicações do Windows 10 e da Microsoft<br> [Configurar definições do Windows Update para Empresas](windows-update-for-business-configure.md) |
|**Gestão de licença de software**|Disponível <br>[Gerir contratos de licença para software para computadores com Windows](manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)|Loja Microsoft para Empresas (apenas para aplicações .appx)<br>[Gerir aplicações compradas na Loja Microsoft para Empresas](windows-store-for-business.md)|
|**Inventário**|Disponível <br>[Ver o inventário de hardware e software dos PCs Windows](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md)|Disponível <br>[Como monitorizar informações da aplicação](apps-monitor.md)<br>[O que é a gestão de dispositivos](device-management.md)|
|**Política de firewall do Windows**|Disponível <br>[Ajudar a proteger PCs com o Windows a utilizarem políticas de Firewall do Windows](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) |Disponível <br>[Firewall do Windows Defender](endpoint-protection-windows-10.md#windows-defender-firewall)|
|**Proteção contra software maligno**|Endpoint Protection<br>[Ajude a proteger os PCs Windows com o Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)|Windows Defender<br>[Ativar o Windows Defender](advanced-threat-protection.md)|
|**Assistência remota** |TeamViewer<br>[Pedir e fornecer assistência remota para PCs Windows](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md)|TeamViewer<br> [Utilizar o TeamViewer para administrar remotamente dispositivos do Intune](device-profile-android-teamviewer.md) |
|**Implementação de aplicações** | Não disponível para a Loja Microsoft para Empresas,<br>.exe, .appx e múltiplos ficheiros .msi apenas<br>[Adicionar aplicações para PCs Windows que executam o cliente de software do Intune](add-apps-for-windows-pcs-in-microsoft-intune.md)|Disponível para aplicações da Loja Microsoft e aplicações de linha de negócio<br>[Como adicionar aplicações da loja Windows](store-apps-windows.md)<br>[Como adicionar aplicações de linha de negócio (LOB) Windows](lob-apps-windows.md)|
|**Proteção de aplicações**|Não disponível|Disponível <br>[O que são as políticas de proteção de aplicações?](app-protection-policy.md)|
|**Atestado de estado de funcionamento**|Não disponível|Disponível|


### <a name="advantages-of-mdm-windows-pc-management"></a>Vantagens da gestão MDM de PCs Windows
A gestão de PCs Windows com a gestão de dispositivos móveis moderna tem as seguintes vantagens:
- **Escalabilidade** – Dimensionamento da gestão MDM com a gestão na cloud do Intune. O cliente de software do Intune está limitado a 7000 PCs.
- **Simplicidade** – Utiliza capacidades de gestão modernas incluídas no sistema operativo sem depender de um cliente de software transferido
- **Consistência** – Os PCs Windows geridos como todos os outros dispositivos móveis na sua organização
<!-- - **Cloud optimization** - -->
