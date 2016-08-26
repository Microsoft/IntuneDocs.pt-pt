---
title: "Capacidades de gestão de PCs Windows | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 665e4a1aa7ee22db91b47660a179384f7c3e4393
ms.openlocfilehash: 9e7a2f5cb2afdeca737c0c8b1b91418352ad5539


---

# Capacidades de gestão de PCs Windows (com o cliente de PC do Microsoft Intune)
Na maioria dos cenários, irá inscrever os dispositivos no Microsoft Intune, o que fornece um conjunto maior de capacidades do que o cliente de PC do Intune. No entanto, também pode gerir os PCs com o cliente de PC do Intune, que proporciona as seguintes funcionalidades:

-   **Gerir atualizações de software** - pode manter os PCs atualizados e gerir quando as atualizações são aplicadas.

-   **Política de Firewall do Windows** - ajuda a garantir que nenhum PC utilizado pela sua empresa tem uma Firewall do Windows configurada incorretamente ou inativa.

-   **Proteção antimalware** - o Intune inclui o Endpoint Protection, que ajuda a proteger os seus PCs de software maligno.

-   **Assistência remota** - o Intune permite que os utilizadores contactem os técnicos de suporte de TI, que podem fornecer assistência através de uma funcionalidade de ambiente de trabalho remoto incluída no Intune <!--- (requires TeamViewer software)--->.

-   **Gestão de licenças de software** - controle quantas licenças de software estão disponíveis e quantas licenças disponíveis estão a ser utilizadas.
-   **Implementação de aplicações** - implemente software em PCs geridos por si. Algumas funcionalidades de gestão de aplicações não estão disponíveis ao gerir computadores com o software cliente.


O Intune suporta a instalação do software de cliente de PC num máximo de 7 000 dispositivos Windows.

## Requisitos do sistema operativo
O Intune pode gerir computadores com as seguintes versões do Windows (x86 e x64):


-   **Windows Vista** - Versões Business, Enterprise e Ultimate.

-   **Windows 7** - versões Pro, Enterprise e Ultimate (sem service pack ou com SP1).

-   **Windows 8** - versões Pro e Enterprise.

-   **Windows 8.1** - versões Pro e Enterprise.

- **Windows 10** -versões Home, Pro, Education e Enterprise.


## Requisitos mínimos de hardware
Seguem-se os requisitos mínimos de hardware para instalar o computador cliente do Intune:

|Requisito|Detalhes|
|---------------|--------------------|
|Rede|O cliente requer o computador para ter ligação à Internet.|
|Processador e Memória|Consulte os requisitos de processador e RAM do sistema operativo do computador.|
|Espaço em disco|200 MB de espaço disponível no disco antes da instalação do software do cliente.|

## Mais requisitos
Seguem-se os requisitos de software para instalar o computador cliente do Intune:

|Requisito|Detalhes|
|---------------|--------------------|
|Permissões administrativas|A conta que instalar o software do cliente tem de ter permissões de administrador local nesse computador.|
|Windows Installer 3.1|O PC tem de ter instalado, no mínimo, o Windows Installer 3.1.|
|Remover software de cliente incompatível|Antes de instalar o cliente de PC do Intune, tem de desinstalar o software cliente seguinte nesse computador:<br /><br />- Qualquer versão do Configuration Manager<br />- Qualquer versão do Microsoft Systems Management Server (SMS)|

### Consulte também
[Funcionalidades de gestão de dispositivos móveis no Microsoft Intune](./mobile-device-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


