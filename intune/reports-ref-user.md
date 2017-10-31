---
title: Utilizador | Microsoft Docs
description: "Tópico de referência para a categoria User das coleções de entidades na API do Armazém de Dados do Intune."
keywords: "Armazém de Dados do Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: be8b7041882539c4e379074cffea385f582f686e
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/20/2017
---
# <a name="reference-for-user-entity"></a>Referência para a entidade de utilizador

A categoria **User** contém a entidade **User** que define as propriedades de utilizador e agente no modelo de dados.

**User**

A entidade **User** lista todos os utilizadores do Azure Active Directory (Azure AD) com licenças atribuídas na sua empresa.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| UserKey |Identificador exclusivo do utilizador no armazém de dados – chave de substituição. |123 |
| UserId |Identificador exclusivo do utilizador – semelhante a UserKey, mas é uma chave natural. |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Endereço de e-mail do utilizador. |John@constoso.com |
| Nome a Apresentar |Nome a apresentar do utilizador. |João |
| IntuneLicensed |Especifica se este utilizador tem ou não licença do Intune. |True/False |
| IsDeleted |Indica se este registo de utilizador foi atualizado.  True: este utilizador tem um novo registo com campos atualizados nesta tabela. False: o registo mais recente deste utilizador. |True/False |
| StartDateInclusiveUTC |Data e hora em UTC em que este utilizador foi criado no armazém de dados. |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |Data e hora em UTC em que a propriedade IsDeleted foi alterada para True. |11/23/2016 12:00:00 AM |
| IsCurrent |Indica se o registo deste utilizador é atual ou não no armazém de dados. |True/False |
| RowLastModifiedDateTimeUTC |Data e hora em UTC em que este utilizador foi modificado pela última vez no armazém de dados. |11/23/2016 12:00:00 AM |

