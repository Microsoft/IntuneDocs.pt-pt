---
title: Linha Cronológica da Entidade do Utilizador do Armazém de Dados
titlesuffix: Microsoft Intune
description: Saiba como o Armazém de Dados do Intune representa os Utilizadores numa linha cronológica.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 363D148E-688F-4830-B6DE-AB4FE3648817
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 4493ea8442642c09ee7a94b9b73fe0412c015649
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189916"
---
# <a name="user-lifetime-representation-in-the-microsoft-intune-data-warehouse"></a>Representação da duração do utilizador no Armazém de Dados do Microsoft Intune

Pode utilizar o mês dos instantâneos de dados armazenados no Armazém de Dados do Intune para responder a perguntas sobre tendências baseadas no tempo. Por exemplo, pode ver o número de utilizadores que são adicionados ao longo de um mês. Também poderá perguntar qual é o número de utilizadores que foram removidos do sistema.

Para obter este tipo de informações, o armazém de dados armazena informações históricas. O armazém de dados consegue registar a duração de uma entidade. O armazém regista quando uma entidade foi criada, quando o estado da entidade é alterado e quando uma entidade é eliminada. Com o histórico capturado com instantâneos de valores quantitativos diários, pode comparar um dia com o dia anterior e assim sucessivamente.

Trabalhar com durações de entidades pode ser confuso, uma vez que as entidades mudam de estado. Isto significa que se observar um instantâneo no dia 30, pode não existir qualquer registo de utilizador no estado ativo nos dados. No dia 29 e 28, o registo da entidade pode existir como ativo. Antes do dia 28, o utilizador não existia.

Este cenário poderá ser mais claro se percorrer a duração de uma entidade.

Vamos assumir que é atribuída uma licença a um utilizador chamado **João Silva** a 01/06/2017. Neste caso, a tabela **Utilizador** teria a entrada seguinte: 
 
| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| João Silva | FALSO | 01/06/2017 | 31/12/9999 | VERDADEIRO
 
João Silva desiste da licença a 25/07/2017. A tabela **Utilizador** tem as seguintes entradas. As alterações nos registos existentes estão `marked`. 

| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| João Silva | FALSO | 01/06/2017 | `07/26/2017` | `FALSE` 
| João Silva | VERDADEIRO | 26/07/2017 | 31/12/9999 | VERDADEIRO 

A primeira linha indica que João Silva existiu no Intune de 01/06/2017 a 25/07/2017. O segundo registo indica que o utilizador foi eliminado a 25/07/2017 e já não está presente no Intune.

Vamos assumir que é atribuída uma nova licença a João Silva a 31/08/2017. Neste caso, a tabela Utilizador teria as entradas seguintes:
 
| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| João Silva | FALSO | 01/06/2017 | 26/07/2017 | FALSO 
| João Silva | VERDADEIRO | 26/07/2017 | `08/31/2017` | `FALSE` 
| João Silva | FALSO | 31/08/2017 | 31/12/9999 | VERDADEIRO 
 
Uma pessoa que pretenda ver o estado atual de todos os utilizadores deve aplicar um filtro em que `IsCurrent = TRUE`. 
 
Uma pessoa que pretenda ver apenas os utilizadores existentes deve aplicar um filtro em que `IsCurrent = TRUE AND IsDeleted = FALSE`.

## <a name="dimension-tables-in-the-entity-lifetime"></a>Tabelas de dimensões da duração de entidade

Para armazenar o histórico das alterações de estados nas entidades, o Intune não elimina os registos. Em vez disso, marca o registo como eliminado. Esta ação chama-se eliminação de forma recuperável. As tabelas de dimensões utilizam várias colunas de metadados para controlar a duração dos registos. 

As colunas de metadados utilizadas com mais frequência são: 

| Nome da Propriedade de Metadados  | Interpretação dos Valores |
|--|--|
| IsDeleted | Indica se a entidade foi eliminada no Intune. |
| StartDateInclusiveUTC  | A data UTC em que a entidade foi carregada para o Armazém de Dados do Intune. A entidade pode ter sido criada antes de ser importada para o Armazém de Dados do Intune. |
| DeletedDateUTC  | A data UTC em que a entidade foi eliminada no Intune. |  

Qualquer coluna de metadados que comece com o prefixo **Linha**, como **RowLastModifiedDateTimeUTC**, indica quando um registo foi criado ou modificado no Armazém de Dados do Intune. O armazém fica a jusante dos dados do Intune. Este valor não tem qualquer relação com a duração da entidade no Intune.  
 
Qualquer pessoa que pretenda ver apenas as entidades dessa dimensão que atualmente existem deve aplicar um filtro em que **IsDeleted = FALSE**.

## <a name="next-steps"></a>Passos Seguintes

 - Para obter informações sobre a entidade **Utilizador Atual**, veja [Referência para a entidade Utilizador Atual](reports-ref-current-user.md).
 - Para obter informações sobre a entidade **Utilizador**, veja [Referência para a entidade Utilizador](reports-ref-user.md).