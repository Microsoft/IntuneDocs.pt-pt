---
title: "Compreender os seus dispositivos com o inventário | Microsoft Intune"
description: "Utilize o Intune para ver informações sobre o hardware dos dispositivos que gere."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: dbf3ac5c7ab326fd82acb979ea7a4933ac68ff1c
ms.openlocfilehash: 1bfb47cccc6438bae54a57271e585bdc9f9f6611


---

# <a name="understand-your-devices-with-inventory-in-microsoft-intune"></a>Compreender os seus dispositivos com o inventário no Microsoft Intune
O Microsoft Intune permite ver o inventário de dispositivos inscritos e PCs Windows que executam o software de cliente do Intune.
Normalmente, o Intune recolhe o inventário de dispositivos geridos a cada 7 dias. Por este motivo, poderá haver um atraso antes de os relatórios mostrarem os resultados de alterações recentes nos dispositivos, por exemplo, uma alteração no nome do dispositivo ou no espaço de armazenamento livre.

## <a name="whats-collected-from-enrolled-devices"></a>O que é recolhido dos dispositivos inscritos?
Para ver o inventário recolhido pelos dispositivos móveis, execute os [Relatórios de Inventário de Dispositivos Móveis](understand-microsoft-intune-operations-by-using-reports.md). O Intune recolhe o seguinte inventário dos dispositivos inscritos:

|Propriedade|Recolhido por|
|------------|-----------------------|
|**Nome**|Todos os dispositivos|
|**Sistema Operativo**|Todos os dispositivos|
|**Fabricante**|Todos os dispositivos|
|**Modelo**|Todos os dispositivos|
|**Canal de Gestão**|Todos os dispositivos|
|**Registado no AAD**|Todos os dispositivos, exceto Mac OS X|
|**Compatibilidade:**|Todos os dispositivos|
|**EAS Ativado**|Todos os dispositivos, exceto Mac OS X|
|**ID de Ativação do EAS**|Todos os dispositivos, exceto Mac OS X|
|**Hora de Ativação do EAS**|Todos os dispositivos, exceto Mac OS X|
|**Estado da Gestão**|Todos os dispositivos|
|**Endereço de E-mail**|Todos os dispositivos|
|**ID do Exchange ActiveSync**|Todos os dispositivos|
|**Com Jailbreak ou Root**|Apenas dispositivos iOS e Android|
|**ID Exclusivo de Dispositivo**|Todos os dispositivos, exceto Exchange ActiveSync|
|**Número de série**|Dispositivos com iOS, Mac OS X, Android, Windows 8.1 e computadores com o Windows 10|
|**Espaço de Armazenamento Total**|Dispositivos com iOS, Mac OS X, Windows 8.1, Windows 10 Mobile e computadores com o Windows 10|
|**Espaço de Armazenamento Livre**|Dispositivos com iOS, Mac OS X, Windows 8.1 e computadores com o Windows 10|
|**Número de Telefone**<br>Os telefones que são classificados como empresariais estão identificados com o respetivo número de telefone completo (por exemplo, quando executa um relatório de inventário de dispositivos móveis). Os números de telefone BYOD são mascarados com &#42;, e apenas são apresentados os quatro últimos dígitos.|Dispositivos iOS, Android e Windows Phone|
|**IMEI**|Dispositivos Exchange ActiveSync, iOS, Android e Windows Phone|
|**MEID**<br>Identificador de Equipamento Móvel|Apenas dispositivos iOS|
|**MAC Wi-Fi**|Todos os dispositivos, exceto Exchange ActiveSync|
|**Operadora Subscritora**|Apenas dispositivos iOS e Android|
|**Tecnologia de Rede Móvel**|Apenas dispositivos iOS e Android|
|**Supervisionado**|Apenas dispositivos iOS|
|**Estado do Bloqueio de Ativação**|Apenas dispositivos iOS|
|**Data de Inscrição**|Todos os dispositivos|
|**Última Atualização**|Todos os dispositivos|
|**MAC Ethernet**|Apenas dispositivos Mac OS X|
|**Bloqueio de Ativação Ativado**|Apenas dispositivos iOS|
|**Encriptação Ativada**|Todos os dispositivos|

## <a name="whats-collected-from-windows-pcs"></a>O que é recolhido dos PCs Windows?
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

-   **Última Atualização**

<!-- this section below belongs in the planning journey
### See Also
[Monitoring and reports with Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
-->



<!--HONumber=Nov16_HO2-->

