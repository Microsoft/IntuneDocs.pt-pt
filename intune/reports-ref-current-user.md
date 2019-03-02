---
title: Utilizador Atual – Armazém de Dados do Intune
titlesuffix: Microsoft Intune
description: Tópico de referência para a categoria de utilizador atual das coleções de entidades na API do armazém de dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: C10E6752-E925-40AD-ABBF-6B621FB7AFC4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08c837ea56276083851977fb4f1972961132296b
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233054"
---
# <a name="reference-for-current-user-entity"></a>Referência para a entidade Utilizador Atual

A categoria **Utilizador Atual** contém as propriedades do utilizador no modelo de dados. A coleção de entidades **Utilizador Atual** está limitada apenas aos utilizadores atualmente ativos. A entidade contém todos os utilizadores do Azure Active Directory aos quais está atualmente atribuída uma licença. A licença pode ser uma licença do Intune, uma licença Híbrida ou uma licença do Microsoft Office 365. Se um utilizador tiver sido removido, não será representado na coleção Utilizador Atual. Para ver uma coleção com o histórico de alterações do estado do utilizador, veja[Referência para a entidade de utilizador](reports-ref-user.md).


## <a name="current-user"></a>Utilizador Atual

A entidade **Utilizador Atual** enumera todos os utilizadores do Azure Active Directory (Azure AD) com licenças atribuídas na empresa.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| UserKey |Identificador exclusivo do utilizador no armazém de dados – chave de substituição. |123 |
| UserId |Identificador exclusivo do utilizador – semelhante a UserKey, mas é uma chave natural. |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Endereço de e-mail do utilizador. |John@constoso.com |
| UPN | O nome principal do utilizador. | John@constoso.com |
| displayName |Nome a apresentar do utilizador. |João |
| IntuneLicensed |Especifica se este utilizador tem ou não licença do Intune. |Verdadeiro/Falso |
| StartDateInclusiveUTC |Data e hora em UTC em que este utilizador foi criado no armazém de dados. |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Data e hora em UTC em que este utilizador foi modificado pela última vez no armazém de dados. |11/23/2016 12:00:00 AM |

## <a name="next-steps"></a>Passos Seguintes
 - Pode utilizar a coleção de entidades **Utilizadores** para expandir os dados do utilizador para os utilizadores que não estão atualmente ativos. Para obter mais informações, veja [Referência para a entidade de utilizador](reports-ref-user.md).
 - Para saber mais sobre como o armazém de dados controla a duração de um utilizador no Intune, veja [Representação da duração do utilizador no Armazém de Dados do Intune](reports-ref-user-timeline.md).
