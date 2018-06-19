---
title: Comparar opções de gestão de PCs Windows
description: Inscrição de dispositivos iOS pertencentes à empresa através do Programa de Inscrição de Dispositivos (DEP) da Apple ou do Apple Configurator
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/27/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e2e341e8b8befa43106673607bd5c5264dd18db0
ms.sourcegitcommit: 2162ed46d939b4a9b85fa4e7e9943f2fb5948f1e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/20/2018
ms.locfileid: "31617277"
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>Comparar a gestão de PCs Windows como computadores ou dispositivos móveis

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

As organizações podem utilizar o Microsoft Intune para gerir PCs Windows como dispositivos móveis com a gestão de dispositivos móveis (MDM) ou como computadores com o cliente de software do Intune.  A Microsoft recomenda que os clientes utilizem a solução de gestão MDM sempre que possível. Para ajudá-lo a compreender melhor as diferenças entre estas opções, o gráfico a seguir compara as duas opções de gestão.

|**Capacidade/cenário** |**Windows como Computador**<br>Cliente de software do Intune | **Windows como Dispositivo Móvel**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**Sistemas operativos** |Windows 10, Windows 8 e posterior, Windows 7, Windows Vista | Windows 10 e posterior |
|**Suporte do Portal do Intune** |[Consola do Silverlight](https://manage.microsoft.com)|[Portal do Azure](https://portal.azure.com) |
|**Acesso condicional**|Não disponível|Disponível <br>[O que é o acesso condicional?](https://docs.microsoft.com/intune-azure/conditional-access/what-is-conditional-access)|
|**Inscrição em massa**|Não disponível|Disponível <br>[Inscrição em massa para dispositivos Windows](https://docs.microsoft.com/intune-azure/enroll-devices/bulk-enroll-windows)|
|**Perfis de dispositivo**|Não disponível|Disponível <br>[O que são os perfis de dispositivos do Microsoft Intune?](https://docs.microsoft.com/intune-azure/configure-devices/what-are-device-profiles)|
|**Inscrição sem agente**|Não disponível |Disponível<br>[Inscrever dispositivos Windows](https://docs.microsoft.com/intune-azure/enroll-devices/enroll-windows-devices)|
|**Gestão de atualizações de software**| Atualizações do Windows e atualizações de aplicações da Microsoft<br>[Manter os PCs Windows atualizados com as atualizações de software](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)|Loja Microsoft para Empresas para as atualizações de aplicações do Windows 10 e da Microsoft<br> [Configurar definições do Windows Update para Empresas](https://docs.microsoft.com/intune-azure/configure-devices/how-to-configure-windows-update-for-business) |
|**Gestão de licença de software**|Disponível <br>[Gerir contratos de licença para software para computadores com Windows](https://docs.microsoft.com/intune/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)|Loja Microsoft para Empresas (apenas para aplicações .appx)<br>[Gerir aplicações compradas na Loja Microsoft para Empresas](https://docs.microsoft.com/intune-azure/manage-apps/wsfb-apps)|
|**Inventário**|Disponível <br>[Ver o inventário de hardware e software dos PCs Windows](https://docs.microsoft.com/intune/deploy-use/view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune)|Disponível <br>[Como monitorizar informações da aplicação](https://docs.microsoft.com/intune/apps-monitor)<br>[O que é a gestão de dispositivos](https://docs.microsoft.com/intune/device-management)|
|**Política de firewall do Windows**|Disponível <br>[Ajudar a proteger PCs com o Windows a utilizarem políticas de Firewall do Windows](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune) |Disponível <br>[Firewall do Windows Defender](https://docs.microsoft.com/en-us/intune/endpoint-protection-windows-10#windows-defender-firewall)|
|**Proteção contra software maligno**|Endpoint Protection<br>[Ajude a proteger os PCs Windows com o Endpoint Protection](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)|Windows Defender<br>[Definições do Windows Defender](https://docs.microsoft.com/intune-azure/configure-devices/custom-for-windows-10#windows-defender-settings)|
|**Assistência remota** |TeamViewer<br>[Pedir e fornecer assistência remota para PCs Windows](https://docs.microsoft.com/intune/deploy-use/request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune)|TeamViewer<br> [Utilizar o TeamViewer para administrar remotamente dispositivos do Intune](https://docs.microsoft.com/en-us/intune/device-profile-android-teamviewer) |
|**Implementação de aplicações** | Não disponível para a Loja Microsoft para Empresas,<br>.exe, .appx e múltiplos ficheiros .msi apenas<br>[Adicionar aplicações para PCs Windows que executam o cliente de software do Intune](https://docs.microsoft.com/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)|Disponível para aplicações da Loja Microsoft e aplicações de linha de negócio<br>[Como adicionar aplicações da loja Windows](https://docs.microsoft.com/intune/store-apps-windows)<br>[Como adicionar aplicações de linha de negócio (LOB) Windows](https://docs.microsoft.com/intune/lob-apps-windows)|
|**Proteção de aplicações**|Não disponível|Disponível <br>[O que são as políticas de proteção de aplicações?](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-protection-policy)|
|**Atestado de estado de funcionamento**|Não disponível|Disponível|


### <a name="advantages-of-mdm-windows-pc-management"></a>Vantagens da gestão MDM de PCs Windows
A gestão de PCs Windows com a gestão de dispositivos móveis moderna tem as seguintes vantagens:
- **Escalabilidade** – Dimensionamento da gestão MDM com a gestão na cloud do Intune. O cliente de software do Intune está limitado a 7000 PCs.
- **Simplicidade** – Utiliza capacidades de gestão modernas incluídas no sistema operativo sem depender de um cliente de software transferido
- **Consistência** – Os PCs Windows geridos como todos os outros dispositivos móveis na sua organização
<!-- - **Cloud optimization** - -->
