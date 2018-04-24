---
title: Dados que o Intune envia para a Google
titleSuffix: Microsoft Intune
description: Lista de dados que o Intune envia para a Google.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 78fef57849b8742bb10ece1717234af5cce3f4ba
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="data-intune-sends-to-google"></a>Dados que o Intune envia para a Google

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quando a gestão de dispositivos Android está ativada num dispositivo, o Microsoft Intune estabelece uma ligação com a Google e partilha informações do utilizador e do dispositivo com a mesma. Antes de o Microsoft Intune poder estabelecer uma ligação, tem de criar uma conta Google.

A seguinte tabela lista os dados que o Microsoft Intune envia para a Google quando a gestão de dispositivos está ativada num dispositivo:


| Dados enviados para a Google | Detalhes | Utilizado para | Exemplo |
|:---:|:---:|:---:|:---:|
| ID Empresarial | Tem origem na Google ao vincular a sua conta do Gmail ao Intune. | Identificador principal utilizado para comunicar entre o Intune e a Google.  Esta comunicação inclui a definição de políticas, a gestão de dispositivos e o vínculo/supressão do vínculo do Android Enterprise com o Intune. | Identificador exclusivo, Formato de exemplo: LC04eik8a6 |
| Corpo de Política | Tem origem no Intune ao guardar uma nova política de configuração ou aplicação. | Aplicar políticas a dispositivos. | Isto é uma coleção de todas as definições configuradas para uma política de configuração ou aplicação. Isto pode conter informações de clientes, se estas forem fornecidas como parte de uma política. Por exemplo, nomes de redes, nomes de aplicações e definições específicas da aplicação. |
| Dados do Dispositivo | Os dispositivos para cenários de Perfil Profissional começam com a inscrição no Intune. Os dispositivos para cenários de Dispositivo gerido começam com a inscrição na Google. | As informações de dados do dispositivo são enviadas entre o Intune e a Google para a realização de várias ações, como a aplicação de políticas, a gestão do dispositivo e a criação geral de relatórios. | **Identificador exclusivo para representar o Nome do Dispositivo.** Exemplo: enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**Identificador exclusivo para representar o Nome do Utilizador.** Exemplo: Enterprises/LC04ebru7b/users/116838519924207449711<br>**Estado do dispositivo.** Exemplos: Ativo, Desativado, Aprovisionamento.<br>**Estados de conformidade.** Exemplos: definição não suportada, aplicações obrigatórias em falta.<br>**Informações de Software.** Exemplos: versões de software e nível de patch.<br>**Informações de Rede.** Exemplos: IMEI, MEID, WifiMacAddress<br>**Definições do Dispositivo.** Exemplos: informações sobre os níveis de encriptação e sobre a permissão de aplicações desconhecidas no dispositivo.<br> Veja abaixo um exemplo de uma mensagem JSON. |
| Nova palavra-passe | Tem origem no Intune. | Repor o código de acesso do dispositivo. | Cadeia a representar uma nova palavra-passe. |
| Utilizador da Google | Google | Gerir o perfil profissional em cenários de Perfil Profissional (BYOD). | Identificador exclusivo para representar a conta do Gmail ligada. Exemplo: 114223373813435875042 |
| Dados da Aplicação | Tem origem no Intune ao guardar a política da aplicação. |  | Cadeia do Nome da Aplicação. Exemplo: app:com.microsoft.windowsintune.companyportal |
| Conta de Serviço Empresarial | Tem origem na Google a pedido do Intune. | Utilizado para a autenticação entre o Intune e a Google para transações que envolvem o cliente. | Existem várias partes:<br> **ID Empresarial**: documentada anteriormente.<br>**UPN**: UPN gerado utilizado na autenticação em nome de um cliente.<br>Exemplo: w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**Chave**: blob codificado Base64 utilizado em pedidos de autor, armazenados e encriptados no serviço, mas este é o aspeto do blob:<br> Identificador exclusivo para representar a chave do cliente<br>Exemplo: a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |

**Exemplo de Dados do Dispositivo**

Eis um exemplo de uma mensagem de dispositivo JSON da Google:



```
'{
  "name": "enterprises/LC02dhxx1r/devices/3195483be017acdc",
  "userId": "114223373813435875042",
  "adminType": "DEVICE_OWNER",
  "state": "ACTIVE",
  "appliedState": "ACTIVE",
  "policyCompliant": true,
  "enrollmentTime": "2017-10-06T15:17:41.702Z",
  "lastStatusReportTime": "2017-10-06T15:18:10.325Z",
  "lastPolicyComplianceReportTime": "2017-10-06T15:18:11.665Z",
  "lastPolicySyncTime": "2017-10-06T15:18:07.852Z",
  "appliedPolicyVersion": "2",
  "apiLevel": 26,
  "enrollmentTokenData": "brew 30 day token",
  "enrollmentTokenId": "yXdtW0_0L7c7Yo9DtRhEfPi3PcMqTorF3V1bTAw_eRs",
  "softwareInfo": {
    "androidVersion": "8.0.0",
    "cloudDpcVersionCode": 55314,
    "cloudDpcVersionName": "bv00553-rc14",
    "androidBuildNumber": "OPR4.170623.009",
    "deviceKernelVersion": "3.10.73-ga51b1600b7f8",
    "bootloaderVersion": "BHZ21c",
    "androidBuildTime": "2017-08-28T18:57:48Z",
    "securityPatchLevel": "2017-10-05",
    "androidBuildType": "user",
    "buildUser": "android-build"
  },
  "hardwareInfo": {
    "brand": "google",
    "hardware": "bullhead",
    "deviceBasebandVersion": "M8994F-2.6.39.3.03",
    "manufacturer": "LGE",
    "serialNumber": "01ed07873b3c20cd",
    "model": "Nexus 5X",
    "batteryShutdownTemperatures": [60.0],
    "batteryThrottlingTemperatures": [-3.4028235E38],
    "cpuShutdownTemperatures": [115.0, 115.0, 115.0, 115.0, 115.0, 115.0],
    "cpuThrottlingTemperatures": [60.0, 60.0, 60.0, 60.0, 60.0, 60.0],
    "gpuShutdownTemperatures": [-3.4028235E38],
    "gpuThrottlingTemperatures": [-3.4028235E38],
    "skinShutdownTemperatures": [-3.4028235E38],
    "skinThrottlingTemperatures": [37.0]
  },
  "displays": [{
    "name": "Built-in Screen",
    "refreshRate": 60,
    "state": "ON",
    "width": 1080,
    "height": 1920,
    "density": 420
  }],
  "appliedPolicyName": "enterprises/LC02dhxx1r/policies/default",
  "networkInfo": {
    "imei": "353626070676775",
    "wifiMacAddress": "02:00:00:00:00:00"
  },
  "memoryInfo": {
    "totalRam": "1902936064",
    "totalInternalStorage": "3169611776"
  },
  "memoryEvents": [{
    "eventType": "EXTERNAL_STORAGE_DETECTED",
    "createTime": "2017-10-06T15:18:09.959Z",
    "byteCount": "26720919552"
  }],
  "powerManagementEvents": [{
    "eventType": "BATTERY_LEVEL_COLLECTED",
    "createTime": "2017-10-06T15:18:09.939Z",
    "batteryLevel": 95.0
  }],
  "userName": "enterprises/LC02dhxx1r/users/114223373813435875042",
  "enrollmentTokenName": "enterprises/LC02dhxx1r/enrollmentTokens/yXdtW0_0L7c7Yo9DtRhEfPi3PcMqTorF3V1bTAw_eRs"
}'
```

Para parar de utilizar a gestão de dispositivos Android com o Microsoft Intune e eliminar os dados, tem de desativar a gestão de dispositivos Android do Microsoft Intune e eliminar a sua conta Google. Consulte a conta Google para saber como desempenhar a gestão da conta.


