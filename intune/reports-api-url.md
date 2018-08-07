---
title: Ponto final da API do Armazém de Dados do Intune
titlesuffix: Microsoft Intune
description: O tópico de referência descreve a estrutura do URL da API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/25/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 05251e3aeb0c290a51c378f8c67f3d55149b63dc
ms.sourcegitcommit: e6013abd9669ddd0d6449f5c129d5b8850ea88f3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/25/2018
ms.locfileid: "39254506"
---
# <a name="intune-data-warehouse-api-endpoint"></a>Ponto final da API do Armazém de Dados do Intune

Pode utilizar a API do Armazém de Dados do Intune com uma conta com controlos de acesso baseados em funções específicos e credenciais do Azure AD. Em seguida, irá autorizar o seu cliente REST com o Azure AD ao utilizar o OAuth 2.0. Por fim, irá formar um URL significativo para chamar um recurso do armazém de dados.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="authorization"></a>Autorização

O Azure Active Directory (Azure AD) utiliza o OAuth 2.0 para lhe permitir autorizar o acesso a aplicações Web e a APIs Web no seu inquilino do Azure AD. Este guia é independente do idioma e descreve como enviar e receber mensagens HTTP sem utilizar bibliotecas de código de fonte aberto. O fluxo do código de autorização de OAuth 2.0 é descrito na [secção 4.1](https://tools.ietf.org/html/rfc6749#section-4.1) da especificação de OAuth 2.0.

Para obter mais informações, veja [Authorize access to web applications using OAuth 2.0 and Azure Active Directory (Autorizar o acesso a aplicações Web com o OAuth 2.0 e o Azure Active Directory)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).

## <a name="api-url-structure"></a>Estrutura do URL da API

Os pontos finais da API do Armazém de Dados leem as entidades para cada conjunto. A API suporta um verbo **GET** HTTP e um subconjunto de opções de consulta.

O URL do Intune utiliza o seguinte formato:  
`https://fef.{location}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity-collection}?api-version={api-version}`

> [!NOTE]
> No URL apresentado acima, substitua `{location}`, `{entity-collection}` e `{api-version}` com base nos detalhes fornecidos na tabela abaixo.

O URL contém os seguintes elementos:

| Elemento | Exemplo | Descrição |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| location | msua06 | O URL base pode ser encontrado ao ver o painel API do Armazém de Dados no portal do Azure. |
| entity-collection | datas | O nome da coleção da entidade do OData. Para obter mais informações sobre as coleções e entidades no modelo de dados, veja [Modelo de Dados](reports-ref-data-model.md). |
| api-version | beta | Versão da API a aceder. Para obter mais informações, veja [Versão](#API-version-information). |
| maxhistorydays | 7 | O número máximo de dias do histórico a obter (opcional). Este parâmetro pode ser fornecido a qualquer coleção, mas só entrará em vigor em coleções que incluam `dateKey` como parte da sua propriedade chave. Veja [Filtros de Intervalo DateKey](reports-api-url.md#datekey-range-filters) para obter mais informações. |

## <a name="api-version-information"></a>Informações sobre a versão da API

A versão atual da API é: `beta`. 

## <a name="odata-query-options"></a>Opções de consulta de OData

A versão atual suporta os seguintes parâmetros de consulta de OData: `$filter, $orderby, $select, $skip,` e `$top`.

## <a name="datekey-range-filters"></a>Filtros de Intervalo DateKey

Os filtros de intervalo `DateKey` podem ser utilizados para limitar a quantidade de dados a transferir em algumas coleções com um filtro de intervalo `dateKey` como propriedade chave. O filtro `DateKey` pode ser utilizado para otimizar o desempenho do serviço ao proporcionar o seguinte parâmetro de consulta `$filter`:

1.  O filtro `DateKey` sozinho no `$filter`, a apoiar os operadores `lt/le/eq/ge/gt` e a juntar-se ao operador lógico `and`, onde estes podem ser mapeados a uma data de início e/ou uma data de fim.
2.  O filtro `maxhistorydays` é dado como uma opção de consulta personalizada.<br>

## <a name="filter-examples"></a>Exemplos de filtros

> [!NOTE]
> Os exemplos de filtros presumem que hoje é dia 21 de fevereiro de 2018.

|                             Filtro                             |           Otimização do Desempenho           |                                          Descrição                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    Completo                                      |    Devolver dados com um `DateKey` entre 20180214 e 20180221.                                     |
|    `$filter=DateKey eq 20180214`                                 |    Completo                                      |    Devolver dados com um `DateKey` igual a 20180214.                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    Completo                                      |    Devolver dados com um `DateKey` entre 20180214 e 20180220.                                     |
|    `maxhistorydays=7&$filter=Id gt 1`                            |    O Id gt 1 parcial não será otimizado    |    Devolver dados com um `DateKey` entre 20180214 e 20180221 e um Id superior a 1.             |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    Completo                                      |    Devolver dados com um `DateKey` igual a 20180214. `maxhistorydays` é ignorado.                            |
|    `$filter=DateKey eq 20180214 and Id gt 1`                     |    Nenhum                                      |    Não é tratado como um filtro de intervalo `DateKey`, logo não há melhoria de desempenho.                              |
|    `$filter=DateKey ne 20180214`                                 |    Nenhum                                      |    Não é tratado como um filtro de intervalo `DateKey`, logo não há melhoria de desempenho.                              |
|    `maxhistorydays=7&$filter=DateKey eq 20180214 and Id gt 1`    |    Nenhum                                      |    Não é tratado como um filtro de intervalo `DateKey`, logo não há melhoria de desempenho. `maxhistorydays` é ignorado.    |
