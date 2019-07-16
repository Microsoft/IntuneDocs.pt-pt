---
title: Utilizador – Armazém de Dados do Intune
titleSuffix: Microsoft Intune
description: Tópico de referência para a categoria User das coleções de entidades na API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 70a7b3f9f01bb401d56874b3f1fc55533c930e6b
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882403"
---
# <a name="reference-for-user-entity"></a>Referência da entidade do usuário

A categoria **Utilizador** contém a entidade **Utilizador** que define as propriedades do utilizador no modelo de dados.

## <a name="user"></a>Utilizador

A entidade **User** lista todos os utilizadores do Azure Active Directory (Azure AD) com licenças atribuídas na sua empresa.

A coleção de entidades **Utilizador** contém dados do utilizador. Estes registos incluem estados do utilizador durante o período de recolha dos dados, mesmo que o utilizador tenha sido removido. Por exemplo, um utilizador pode ser adicionado ao Intune e, em seguida, removido no decorrer do mês anterior. Apesar de este utilizador não estar presente no momento do relatório, o utilizador e o estado estão presentes nos dados do mês anterior. Pode criar um relatório que mostrará a duração da presença no histórico do utilizador nos seus dados.

|          Propriedade          |                                                                                                           Descrição                                                                                                          |                Exemplo               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| UserKey                    | Identificador exclusivo do utilizador no armazém de dados – chave de substituição.                                                                                                                                                         | 123                                  |
| UserId                     | Identificador exclusivo do utilizador – semelhante a UserKey, mas é uma chave natural.                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| UserEmail                  | Endereço de e-mail do utilizador.                                                                                                                                                                                                     | John@constoso.com                    |
| userPrincipalName                        | O nome principal do utilizador.                                                                                                                                                                                               | John@constoso.com                    |
| DisplayName                | Nome a apresentar do utilizador.                                                                                                                                                                                                      | João                                 |
| IntuneLicensed             | Especifica se este utilizador tem ou não licença do Intune.                                                                                                                                                                              | True/False                           |
| IsDeleted                  | Indica se todas as licenças do utilizador expiraram e se o utilizador foi, por conseguinte, removido do Intune. Para um único registo, este sinalizador não se altera. Em vez disso, é criado um novo registo para um novo estado do utilizador. | Verdadeiro/Falso                           |
| RowLastModifiedDateTimeUTC | Data e hora em UTC quando o registo foi modificado pela última vez no armazém de dados                                                                                                                                                 | 11/23/2016 0:00                      |


## <a name="next-steps"></a>Passos Seguintes
- Pode utilizar a coleção de entidades **Utilizador Atual** para limitar os dados do utilizador aos utilizadores que estão atualmente ativos. Para obter mais informações, veja [Referência para a entidade do utilizador atual](reports-ref-current-user.md).
- Para saber mais sobre como o armazém de dados controla a duração de um utilizador no Intune, veja [Representação da duração do utilizador no Armazém de Dados do Intune](reports-ref-user-timeline.md).
