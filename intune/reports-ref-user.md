---
title: Utilizador – Armazém de Dados do Intune
titlesuffix: Microsoft Intune
description: Tópico de referência para a categoria User das coleções de entidades na API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b6161540b4b05ebab35942a1657adc30bce6afdb
ms.sourcegitcommit: 445a54dc6826a549d770a9953549ae2191d391c2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/17/2018
ms.locfileid: "45727480"
---
# <a name="reference-for-user-entity"></a>Referência para a entidade de utilizador

A categoria **Utilizador** contém a entidade **Utilizador** que define as propriedades do utilizador no modelo de dados.

## <a name="user"></a>Função do

A entidade **User** lista todos os utilizadores do Azure Active Directory (Azure AD) com licenças atribuídas na sua empresa.

A coleção de entidades **Utilizador** contém dados do utilizador. Estes registos incluem estados do utilizador durante o período de recolha dos dados, mesmo que o utilizador tenha sido removido. Por exemplo, um utilizador pode ser adicionado ao Intune e, em seguida, removido no decorrer do mês anterior. Apesar de este utilizador não estar presente no momento do relatório, o utilizador e o estado estão presentes nos dados do mês anterior. Pode criar um relatório que mostrará a duração da presença no histórico do utilizador nos seus dados.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| UserKey |Identificador exclusivo do utilizador no armazém de dados – chave de substituição. |123 |
| UserId |Identificador exclusivo do utilizador – semelhante a UserKey, mas é uma chave natural. |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Endereço de e-mail do utilizador. |John@constoso.com |
| UPN | O nome principal do utilizador. | John@constoso.com |
| DisplayName |Nome a apresentar do utilizador. |João |
| IntuneLicensed |Especifica se este utilizador tem ou não licença do Intune. |True/False |
| IsDeleted | Indica se todas as licenças do utilizador expiraram e se o utilizador foi, por conseguinte, removido do Intune. Para um único registo, este sinalizador não se altera. Em vez disso, é criado um novo registo para um novo estado do utilizador. |True/False |
| StartDateInclusiveUTC |Se IsDeleted = FALSE, DateTime em UTC quando foi atribuída uma licença ao utilizador e este começou a ter uma presença no Intune. Se IsDeleted = TRUE, DateTime em UTC quando as licenças do utilizador expiraram e quando este foi removido do Intune. |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |Se IsDeleted = FALSE, DateTime em UTC quando a licença do utilizador expirou e quando este foi removido do Intune. A licença expirou durante o dia anterior. Se IsDeleted = TRUE, DateTime em UTC quando o utilizador voltou a ter uma licença nova e quando foi recriado no Intune.  |11/23/2016 12:00:00 AM |
| IsCurrent |Indica se este registo representa o estado mais recente do utilizador. Podem existir vários registos para um único utilizador, mas apenas um deles representa o estado atual.  |True/False |
| RowLastModifiedDateTimeUTC |Data e hora em UTC quando o registo foi modificado pela última vez no armazém de dados  |11/23/2016 12:00:00 AM |

## <a name="next-steps"></a>Próximos passos
 - Pode utilizar a coleção de entidades **Utilizador Atual** para limitar os dados do utilizador aos utilizadores que estão atualmente ativos. Para obter mais informações, veja [Referência para a entidade do utilizador atual](reports-ref-current-user.md).
 - Para saber mais sobre como o armazém de dados controla a duração de um utilizador no Intune, veja [User lifetime representation in the Intune Data Warehouse (Representação da duração do utilizador no Armazém de Dados do Intune)](reports-ref-user-timeline.md).
