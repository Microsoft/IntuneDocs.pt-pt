---
title: "Compreender os seus dispositivos com o inventário | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 42e21b802fb605c98f688485c3b77703b3950e94
ms.openlocfilehash: 55b99e326e4f22aee62b207eb2e976a8d52e70c3


---

# Compreender os seus dispositivos com o inventário no Microsoft Intune
O Microsoft Intune permite ver o inventário de dispositivos inscritos e PCs Windows que executam o software de cliente do Intune.

## O que é recolhido dos dispositivos inscritos?
Para ver o inventário recolhido pelos dispositivos móveis, execute os [Relatórios de Inventário de Dispositivos Móveis](understand-microsoft-intune-operations-by-using-reports.md). O Intune recolhe o seguinte inventário dos dispositivos inscritos:

|Propriedade|Recolhido por|
|------------|-----------------------|
|**Nome**|Todos os dispositivos|
|**Sistema Operativo**|Todos os dispositivos|
|**Fabricante**|Todos os dispositivos|
|**Modelo**|Todos os dispositivos|
|**Canal de Gestão**|Todos os dispositivos|
|**Registado no AAD**|Todos os dispositivos, exceto Mac OS X|
|**Compatível**|Todos os dispositivos|
|**EAS Ativado**|Todos os dispositivos, exceto Mac OS X|
|**ID de Ativação do EAS**|Todos os dispositivos, exceto Mac OS X|
|**Hora de Ativação do EAS**|Todos os dispositivos, exceto Mac OS X|
|**Estado da Gestão**|Todos os dispositivos|
|**Endereço de E-mail**|Todos os dispositivos|
|**ID do Exchange ActiveSync**|Todos os dispositivos|
|**Com jailbreak ou root**|Apenas dispositivos iOS e Android|
|**ID de Dispositivo Exclusivo**|Todos os dispositivos, exceto Exchange ActiveSync|
|**Número de série**|Dispositivos iOS, Mac OS X, Android, Windows 8.1 e Windows 10|
|**Espaço de Armazenamento Total**|Dispositivos iOS, Mac OS X, Windows 8.1 e Windows 10|
|**Espaço de Armazenamento Livre**|Dispositivos iOS, Mac OS X, Windows 8.1 e Windows 10|
|**Número de Telefone**<br>Os telefones que são classificados como empresariais estão identificados com o respetivo número de telefone completo quando, por exemplo, executa um relatório de inventário de dispositivos móveis. Os números de telefone BYOD são mascarados com &#42;, com apenas os 4 últimos dígitos apresentados.|Dispositivos iOS, Android e Windows Phone|
|**IMEI**|Dispositivos Exchange ActiveSync, iOS, Android e Windows Phone|
|**MEID**<br>Identificador de Equipamento Móvel|Apenas dispositivos iOS|
|**MAC Wi-Fi**|Todos os dispositivos, exceto Exchange ActiveSync|
|**Operadora Subscritora**|Apenas dispositivos iOS e Android|
|**Tecnologia de Rede Móvel**|Apenas dispositivos iOS e Android|
|**Supervisionado**|Apenas dispositivos iOS|
|**Estado do Bloqueio de Ativação**|Apenas dispositivos iOS|
|**Data de Inscrição**|Todos os dispositivos|
|**Última Actualização**|Todos os dispositivos|
|**MAC Ethernet**|Apenas dispositivos Mac OS X|
|**Bloqueio de Ativação Ativado**|Apenas dispositivos iOS|
|**Encriptação Ativada**|Todos os dispositivos|

## O que é recolhido dos PCs Windows
> [!IMPORTANT]
> Esta secção aplica-se apenas aos PCs Windows que executam o software de cliente de PC Windows do Intune.

Para ver o inventário recolhido pelos PCs Windows, execute os [Relatórios de Inventário de Computadores](understand-microsoft-intune-operations-by-using-reports.md). O Intune recolhe o seguinte inventário dos PCs Windows:

-   **Nome**

-   **Tipo de Chassis**

-   **Fabricante**

-   **Modelo**

-   **Sistema Operativo**

-   **Versão do TPM**

-   **Espaço Total em Disco**

-   **Espaço em Disco Utilizado**

-   **Espaço Livre em Disco**

-   **Nome do Disco do SO**

-   **Espaço em Disco do SO**

-   **Espaço Livre em Disco do SO**

-   **Memória Física**

-   **Nome do Processador**

-   **Arquitetura do Processador**

-   **Velocidade da CPU**

-   **Endereço IP**

-   **Número de série**

-   **Último Utilizador a Iniciar Sessão**

-   **Utilizador Atribuído**

-   **Última Actualização**

<!-- this section below belongs in the planning journey
### See Also
[Monitoring and reports with Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
-->



<!--HONumber=Jun16_HO4-->


