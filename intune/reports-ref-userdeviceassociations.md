---
title: "Associação de Dispositivo do Utilizador | Microsoft Docs"
description: "Tópico de referência para a categoria Associação de Dispositivo do Utilizador das coleções de entidades na API do Armazém de Dados do Intune."
keywords: "Armazém de Dados do Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 09/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: BCDBABCB-A7B1-42F2-BDD1-D055E33F2239
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 490e29f87c65875a385472e6abe9400363383f9b
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/20/2017
---
# <a name="reference-for-user-device-association-entity"></a>Referência para a entidade Associação de Dispositivo do Utilizador

A categoria **Associação de Dispositivo do Utilizador** contém a entidade **Associação de Dispositivo do Utilizador** utilizada para definir associações de dispositivo na organização.

**Associação de Dispositivo do Utilizador**

A entidade **Associação de Dispositivo do Utilizador** representa as associações de dispositivo na organização.

| Nome               | Descrição                                                                                      | Exemplo                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | Identificador exclusivo do utilizador no armazém de dados – chave de substituição.                             | 123                    |
| DeviceKey          | Identificador exclusivo do dispositivo no armazém de dados.                                           | 123                    |
| CreatedDateTimeUTC | Data e hora em UTC em que a associação de dispositivo do utilizador foi criada.                               | 11/23/2016 12:00:00 AM |
| IsDeleted          | Indica que o utilizador anulou a inscrição desse dispositivo e essa associação já não está atualizada. | Verdadeiro                   |
| EndedDateTimeUTC   | Data e hora em UTC em que a propriedade IsDeleted foi alterada para **True**.                                         | 23/06/2017 12:00:00 |