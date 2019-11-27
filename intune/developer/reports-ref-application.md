---
title: Referência para as entidades de aplicações
titleSuffix: Microsoft Intune
description: Tópico de referência para a categoria Application das coleções de entidades na API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4a8fa34673340e4adca7b64707d8c79d4808460
ms.sourcegitcommit: 1cf063c98e1caae00a6e6fab821cc3254562bca9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74290956"
---
# <a name="reference-for-application-entities"></a>Referência para as entidades de aplicações

A categoria de **aplicativo** contém entidades para dispositivos que rastreiam informações como:

- Versões de uma aplicação
- Origem da instalação de uma aplicação
- Tipo de programadores que criaram uma aplicação
- Tipos de software geridos para uma aplicação, por exemplo **sidecar** ou **ambiente de trabalho**
- Estado VPP (Volume Purchasing Program) de uma aplicação

## <a name="apprevisions"></a>appRevisions

A entidade **appRevision** apresenta uma lista de todas as versões das aplicações.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| appKey |Identificador exclusivo da Aplicação. |123 |
| applicationId |Identificador exclusivo da Aplicação – semelhante à AppKey, mas esta é uma chave natural. |b66bc706-ffff-7437-0340-032819502773 |
| revisão |A versão como mencionada pelo administrador durante o carregamento do binário. |2 |
| Título |Nome da aplicação. |Excel |
| publisher |Publicador da aplicação. |Microsoft |
| UploadState |Estado de carregamento da aplicação. |1 |
| appTypeKey |Referência ao AppType descrito na secção seguinte. | |
| vppProgramTypeKey |Referência ao VppProgramType descrito abaixo. | |
| creationTime |A hora em que esta revisão foi criada. |11/23/2016 12:00:00 AM |
| modificadotime |A última vez em que algo relacionado com esta revisão foi alterado. |11/23/2016 12:00:00 AM |
| size |Tamanho do binário. | |
| startDateInclusiveUTC |Data e hora em UTC em que a revisão da Aplicação foi criada no armazém de dados. |11/23/2016 12:00:00 AM |
| endDateExclusiveUTC |Data e hora em UTC em que a revisão desta aplicação se tornou obsoleta. |11/23/2016 12:00:00 AM |
| isCurrent |Indica se a versão desta Aplicação é atual ou não no armazém de dados. |True/False |
| rowLastModifiedDateTimeUTC |Data e hora em UTC em que esta versão da aplicação foi modificada pela última vez no armazém de dados. |11/23/2016 12:00:00 AM |

## <a name="apptypes"></a>appTypes

A entidade **appType** apresenta uma lista da origem da instalação de uma aplicação.

| Propriedade  | Descrição |
|---------|------------|
| appTypeID |ID do tipo |
| appTypeKey |Chave de substituição da chave |
| appTypeName |Tipo de aplicação |

### <a name="example"></a>Exemplo

| AppTypeID  | Nome | Descrição |
|---------|------------|--------|
| 0 |Aplicação da loja Android | Uma aplicação da loja Android. |
| 1 |Aplicação LOB Android | Uma aplicação de linha de negócios Android. |
| 2 |Aplicação gerida da loja Android (MAM) | Uma aplicação da loja Android com gestão ativada. |
| 3 |Aplicação da loja iOS | Uma aplicação da loja iOS. |
| 4 |Aplicação LOB iOS | Uma aplicação de linha de negócios iOS. |
| 5 |Aplicação da loja iOS gerida (MAM?) | Uma aplicação da loja iOS com gestão ativada. |
| 6 |O365 Pro Plus Suite | O Office 365 Pro Plus Suite para Windows 10. |
| 7 |Aplicação Web | Uma aplicação Web. |
| 8 |Aplicação da loja Windows Phone 8.1 | Uma aplicação da loja Windows Phone 8.1. |
| 9 |Aplicação da loja Windows | Uma aplicação da loja Windows. |
| 10 |Aplicação LOB do Windows | Uma aplicação de linha de negócio AppX do Windows. |
| 11 |Windows Mobile MSI | Uma aplicação de linha de negócios MSI. |
| 12 |Aplicação LOB para Windows Phone | Uma aplicação de linha de negócio do Windows Phone. |


## <a name="vppprogramtypes"></a>vppProgramTypes

A entidade **vppProgramType** apresenta uma lista de tipos de programas VPP possíveis para uma aplicação.

| Propriedade  | Descrição |
|---------|------------|
| vppProgramTypeID | ID do tipo. |
| vppProgramTypeKey | Chave de substituição da chave. |
| vppProgramTypeName | Tipo de Programa VPP. |

### <a name="example"></a>Exemplo

| VppProgramID  | Nome | Descrição |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Programa VPP da Microsoft. |
| 00000000-0000-0000-0000-000000000000 | Ainda não está disponível | Valor predefinido, Sem VPP. |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Programa VPP da Apple. |



## <a name="applicationinventories"></a>applicationInventories

A entidade **deinventário** lista os aplicativos encontrados no dispositivo no momento da coleta de inventário.

| Propriedade  | Descrição |
|---------|------------|
| deviceKey | Esta é uma referência à tabela de Dispositivos que contém o ID de dispositivo do Intune. |
| dateKey | Referência à tabela de data que indica o dia do inventário. |
| applicationName | O nome da aplicação. |
| applicationVersion | Versão da aplicação. |
| bundleSize | O tamanho da aplicação em bytes. |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates

A entidade **mobileAppInstallState** representa o estado de instalação de um aplicativo móvel depois que ele tiver sido atribuído a um grupo que contém dispositivos, usuários ou ambos.

| Propriedade | Descrição |
|---|---|
| appInstallStateKey | O ID exclusivo do estado de instalação da aplicação da sua conta. |
| appInstallState | Valor Enum do estado de instalação da aplicação. |
| appInstallStateName | Nome do estado de instalação da aplicação. |



