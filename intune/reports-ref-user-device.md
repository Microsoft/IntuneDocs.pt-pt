---
title: "Utilizar a Associação de Dispositivos do Utilizador – Armazém de Dados do Intune | Documentos da Microsoft"
description: "Uma lista de alterações na API do Armazém de Dados do Intune."
keywords: "Armazém de Dados do Intune"
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9032ffa547daeb19e694a0245dfec676d85a5793
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="user-device-association"></a>Associação de Dispositivos do Utilizador

A entidade **UserDeviceAssociation** contém associações de dispositivos do utilizador na sua organização.

| Nome               | Descrição                                                                                      | Exemplo                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | Identificador exclusivo do utilizador no armazém de dados. (Chave de substituição).                              | 123                    |
| DeviceKey          | Identificador exclusivo do dispositivo no armazém de dados.                                            | 123                    |
| CreatedDateTimeUTC | Data e hora em que a associação de dispositivos do utilizador foi criada. Utiliza o formato UTC.                                | 11/23/2016 12:00:00 AM |
| IsDeleted          | Indica que o utilizador anulou a inscrição desse dispositivo e essa associação já não está atualizada. | True/False             |
| EndedDateTimeUTC   | Data e hora em UTC em que a propriedade IsDeleted foi alterada para **True**.                                              | 23/06/2017 12:00:00 |
