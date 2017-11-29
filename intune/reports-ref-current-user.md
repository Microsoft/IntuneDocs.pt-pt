---
title: "Utilizador – Armazém de Dados do Intune | Documentos da Microsoft"
description: "Tópico de referência para a categoria User das coleções de entidades na API do Armazém de Dados do Intune."
keywords: "Armazém de Dados do Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C10E6752-E925-40AD-ABBF-6B621FB7AFC4
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6f321a3a9ac09c004639a3db15df280fbdb5be3c
ms.sourcegitcommit: d26930f45ba9e6292a49bcb08defb5b3f14b704b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="reference-for-current-user-entity"></a>Referência para a entidade do utilizador atual

A categoria **Utilizador Atual** contém as propriedades de utilizador e de agente no modelo de dados. A coleção de entidades **Utilizador Atual** está limitada apenas aos utilizadores atualmente ativos. A entidade contém todos os utilizadores do Azure Active Directory aos quais está atualmente atribuída uma licença. A licença pode ser uma licença do Intune, uma licença Híbrida ou uma licença do Microsoft Office 365. Se um utilizador tiver sido removido, não será representado durante o período de recolha de dados. Para ver uma coleção com o histórico de alterações do estado do utilizador, veja[Referência para a entidade de utilizador](reports-ref-user.md).


## <a name="user"></a>Função do

A entidade **User** lista todos os utilizadores do Azure Active Directory (Azure AD) com licenças atribuídas na sua empresa.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| UserKey |Identificador exclusivo do utilizador no armazém de dados – chave de substituição. |123 |
| UserId |Identificador exclusivo do utilizador – semelhante a UserKey, mas é uma chave natural. |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Endereço de e-mail do utilizador. |John@constoso.com |
| UPN | O nome principal do utilizador. | John@constoso.com |
| Nome a Apresentar |Nome a apresentar do utilizador. |João |
| IntuneLicensed |Especifica se este utilizador tem ou não licença do Intune. |True/False |
| StartDateInclusiveUTC |Data e hora em UTC em que este utilizador foi criado no armazém de dados. |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Data e hora em UTC em que este utilizador foi modificado pela última vez no armazém de dados. |11/23/2016 12:00:00 AM |

## <a name="next-steps"></a>Próximos passos
 - Pode utilizar a coleção de entidades **Utilizadores** para expandir os dados do utilizador para os utilizadores que não estão atualmente ativos. Para obter mais informações, veja [Referência para a entidade de utilizador](reports-ref-user.md). 
 - Para saber mais sobre como o armazém de dados controla a duração de um utilizador no Intune, veja [Representação da duração do utilizador no Armazém de Dados do Intune](reports-ref-user-timeline.md).