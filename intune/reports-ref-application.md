---
title: "Aplicação | Documentos da Microsoft"
description: "Tópico de referência para a categoria Application das coleções de entidades na API do Armazém de Dados do Intune."
keywords: "Armazém de Dados do Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: cd684feec1df6b20f9349052496a21895527710b
ms.sourcegitcommit: 0d9bfd92bf5958261ed83b1f150bf207b7ba7e56
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/21/2017
---
# <a name="reference-for-application-entities"></a>Referência para as entidades de aplicações

A categoria **Application** contém entidades para dispositivos móveis que registam informações como:

  -  Versões de uma aplicação
  -  Origem da instalação de uma aplicação
  -  Tipo de programadores que criaram uma aplicação
  -  Tipos de software geridos para uma aplicação, por exemplo **sidecar** ou **ambiente de trabalho**
  -  Estado VPP (Volume Purchasing Program) de uma aplicação

## <a name="apprevision"></a>AppRevision

A entidade **AppRevision** apresenta uma lista de todas as versões das aplicações.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| AppKey |Identificador exclusivo da Aplicação |123 |
| ApplicationID |Identificador exclusivo da Aplicação – semelhante à AppKey, mas esta é uma chave natural. |b66bc706-ffff-7437-0340-032819502773 |
| Revision |A versão como mencionada pelo administrador durante o carregamento do binário |2 |
| Title |Nome da aplicação |Excel |
| Publisher |Publicador da aplicação |Microsoft |
| UploadState |Estado de carregamento da aplicação |1 |
| AppTypeKey |Referência ao AppType descrito na secção seguinte. | |
| VppProgramTypeKey |Referência ao VppProgramType descrito abaixo | |
| CreationTime |A hora em que esta revisão foi criada |11/23/2016 12:00:00 AM |
| ModifiedTime |A última vez em que algo relacionado com esta revisão foi alterado |11/23/2016 12:00:00 AM |
| Size |Tamanho do binário | |
| StartDateInclusiveUTC |Data e hora em UTC em que a revisão da Aplicação foi criada no armazém de dados |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |Data e hora em UTC em que a revisão desta aplicação se tornou obsoleta |11/23/2016 12:00:00 AM |
| IsCurrent |Indica se a versão desta Aplicação é atual ou não no armazém de dados |True/False |
| RowLastModifiedDateTimeUTC |Data e hora em UTC em que esta versão da aplicação foi modificada pela última vez no armazém de dados |11/23/2016 12:00:00 AM |

## <a name="apptypes"></a>AppTypes

A entidade **AppTypes** apresenta uma lista da origem da instalação de uma aplicação.

| Propriedade  | Descrição |
|---------|------------|
| AppTypeID |ID do tipo |
| AppTypeKey |Chave de substituição da chave |
| AppTypeName |Tipo de aplicação |

## <a name="example"></a>Exemplo

| AppTypeID  | Nome | Descrição |
|---------|------------|--------|
| 0 |Aplicação da loja Android |Uma aplicação da loja Android |
| 1 |Aplicação LOB Android |Uma aplicação de linha de negócios Android |
| 2 |Aplicação gerida da loja Android (MAM) |Uma aplicação da loja Android com gestão ativada |
| 3 |Aplicação da loja iOS |Uma aplicação da loja iOS |
| 4 |Aplicação LOB iOS |Uma aplicação de linha de negócios iOS |
| 5 |Aplicação da loja iOS gerida (MAM?) |Uma aplicação da loja iOS com gestão ativada |
| 6 |O365 Pro Plus Suite |O Office 365 Pro Plus Suite para Windows 10 |
| 7 |Aplicação Web |Uma aplicação Web |
| 8 |Aplicação da loja Windows Phone 8.1 |Uma aplicação da loja Windows Phone 8.1 |
| 9 |Aplicação da loja Windows |Uma aplicação da loja Windows |
| 10 |Aplicação LOB do Windows |Uma aplicação de linha de negócio AppX do Windows |
| 11 |Windows Mobile MSI |Uma aplicação de linha de negócios MSI |
| 12 |Aplicação LOB para Windows Phone |Uma aplicação de linha de negócio do Windows Phone |


## <a name="vppprogramtypes"></a>VppProgramTypes

A entidade **VppProgramTypes** apresenta uma lista de programas VPP possíveis para uma aplicação.

| Propriedade  | Descrição |
|---------|------------|
| VppProgramTypeID |ID do tipo |
| VppProgramTypeKey |Chave de substituição da chave |
| VppProgramTypeName |Tipo de Programa de VPP |

## <a name="example"></a>Exemplo

| VppProgramID  | Nome | Descrição |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 |Microsoft |Programa VPP da Microsoft |
| 00000000-0000-0000-0000-000000000000 |Ainda não está disponível |Valor predefinido, Sem VPP |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B |Apple |Programa VPP da Apple |



## <a name="applicationinventory"></a>ApplicationInventory

A entidade **ApplicationInventory** lista as aplicações encontradas no dispositivo aquando da recolha do inventário.

| Propriedade  | Descrição |
|---------|------------|
| DeviceKey |Esta é uma referência à tabela de Dispositivos que contém o ID de dispositivo do Intune |
| DateKey |Referência à tabela de data que indica o dia do inventário |
| ApplicationName |O Nome da aplicação |
| ApplicationVersion |Versão da aplicação |
| BundleSize |O tamanho da aplicação em bytes |
