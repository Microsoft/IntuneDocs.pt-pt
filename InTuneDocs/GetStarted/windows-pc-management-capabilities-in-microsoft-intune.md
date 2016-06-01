---
# required metadata

title: Funcionalidades de gestão de computadores com Windows no Microsoft Intune | Microsoft Intune
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

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Funções de gestão de computadores com Windows (com o computador cliente do Microsoft Intune)
Na maioria dos cenários, irá inscrever os dispositivos com o Microsoft Intune, o que fornece um conjunto maior de capacidades que o computador cliente do Intune. No entanto, também pode gerir PCs, utilizando o computador cliente do Intune que fornece as seguintes funcionalidades:

-   **Gerir atualizações de software** - Pode manter os computadores atualizados e gerir quando as atualizações são aplicadas.

-   **Política de Firewall do Windows** - Isto ajuda a garantir que nenhum computador utilizado pela sua empresa tem uma Firewall do Windows incorretamente configurada ou inativa.

-   **Proteção antimalware** - o Intune inclui o Endpoint Protection, que ajuda a proteger os seus PCs de software maligno.

-   **Assistência remota** - O Intune permite que os utilizadores contactem os técnicos de suporte de TI, que podem fornecer assistência através de uma funcionalidade de ambiente de trabalho remoto incluída no Intune.

-   **Gestão de licenças de software** - Controle quantas licenças de software estão disponíveis e quantas licenças disponíveis estão a ser utilizadas.
-   **Implementação de aplicações** - implemente software em PCs geridos por si. Algumas funcionalidades de gestão de aplicações não estão disponíveis ao gerir computadores com o software cliente.


## Requisitos do sistema operativo
O Intune pode gerir computadores com as seguintes versões do Windows (x86 e x64):


-   **Windows Vista** - Versões Business, Enterprise e Ultimate.

-   **Windows 7** - Versões Professional, Enterprise e Ultimate (sem service pack ou com SP1).

-   **Windows 8** - Versões Professional e Enterprise.

-   **Windows 8.1** - Versões Professional e Enterprise.


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
|Windows Installer 3.1|O computador tem de ter instalado, no mínimo, o Windows Installer 3.1.|
|Remover software de cliente incompatível|Antes de instalar o software de cliente de computador com Intune, tem de desinstalar o software de cliente seguinte desse computador:<br /><br />- Qualquer versão do Configuration Manager<br />- Qualquer versão do Microsoft Systems Management Server (SMS)|

### Consulte também
[Funcionalidades de gestão de dispositivos móveis no Microsoft Intune](/intune/understand/mobile-device-management-capabilties-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


