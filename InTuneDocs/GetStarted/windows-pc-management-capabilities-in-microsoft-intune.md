---
title: Funcionalidades de cliente de software de PCs do Intune | Microsoft Intune
description: Saiba mais acerca das funcionalidades do Intune quando gere PCs Windows com o cliente de software do Intune.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 453323aa38eed0a01aa8d583376162734439a69c
ms.openlocfilehash: 0d4ec8077e2521b23808fcb537c4b2389fee714a


---

# Funcionalidades de gestão de PCs Windows ao utilizar o cliente de software do Intune
Na maioria dos cenários, irá inscrever os dispositivos no Microsoft Intune, o que fornece um conjunto maior de capacidades. No entanto, também pode gerir os PCs com o cliente de software do Intune, que proporciona as seguintes funcionalidades:

-   **[Gestão de atualizações de software](/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)** pode manter os PCs atualizados e decidir quando as atualizações são aplicadas.

-   **[Política de Firewall do Windows](/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)** ajuda a garantir que nenhum PC utilizado na sua empresa tem uma Firewall do Windows configurada incorretamente ou inativa.

-   **[Proteção antimalware](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)**o Intune inclui o Endpoint Protection, que ajuda a proteger os seus PCs de software malicioso.

-   **[Assistência remota](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#request-and-provide-remote-assistance-to-windows-pcs-that-use-the-intune-client-software )** o Intune permite que os utilizadores contactem os técnicos de suporte de TI, que podem fornecer assistência através de uma funcionalidade de ambiente de trabalho remoto incluída no Intune (requer o software TeamViewer).

-   **[Gestão de licenças de software](/intune/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)** controle quantas licenças de software estão disponíveis e quantas licenças disponíveis estão a ser utilizadas.
-   **[Implementação de aplicações](/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)** implemente software em PCs geridos por si. Algumas funcionalidades de gestão de aplicações não estão disponíveis ao gerir PCs com o cliente de software.


O Intune suporta a instalação do cliente de software num máximo de 7000 dispositivos Windows.

## Requisitos do sistema operativo
O Intune pode gerir PCs com as seguintes versões do Windows (32 e 64 bits):


-   **Windows Vista** – Versões Business, Enterprise e Ultimate

-   **Windows 7** – Versões Pro, Enterprise e Ultimate (sem service pack ou com SP1)

-   **Windows 8** – Versões Pro e Enterprise

-   **Windows 8.1** – Versões Pro e Enterprise

- **Windows 10** – Versões Pro, Education e Enterprise


## Requisitos mínimos de hardware
Seguem-se os requisitos mínimos de hardware para instalar o cliente de software do Intune:

|Requisito|Detalhes|
|---------------|--------------------|
|Rede|O cliente requer o computador para ter ligação à Internet.|
|Processador e memória|Consulte os requisitos de processador e RAM do sistema operativo do computador.|
|Espaço em disco|200 MB de espaço disponível no disco antes da instalação do software do cliente.|

## Mais requisitos
Seguem-se os requisitos de software para instalar o cliente de software do Intune:

|Requisito|Detalhes|
|---------------|--------------------|
|Permissões administrativas|A conta que instalar o software do cliente tem de ter permissões de administrador local nesse computador.|
|Windows Installer 3.1|O computador tem de ter instalado, no mínimo, o Windows Installer 3.1.|
|Remover software de cliente incompatível|Antes de instalar o cliente de PC do Intune, tem de desinstalar o software cliente seguinte nesse computador:<br /><br />– Qualquer versão do Configuration Manager<br />– Qualquer versão do Microsoft Systems Management Server (SMS)|

### Consulte também
[Funcionalidades de gestão de dispositivos inscritos do Microsoft Intune](./mobile-device-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Sep16_HO2-->


