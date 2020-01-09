---
title: Ponto final da API do Armazém de Dados do Intune
titleSuffix: Microsoft Intune
description: Este tópico de referência descreve o Microsoft Intune data warehouse estrutura de URL da API. São fornecidos exemplos de filtro.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e19cc606792c59d2f5676aeca41d862308f1ab32
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654146"
---
# <a name="intune-data-warehouse-api-endpoint"></a>Ponto final da API do Armazém de Dados do Intune

Pode utilizar a API do Armazém de Dados do Intune com uma conta com controlos de acesso baseados em funções específicos e credenciais do Azure AD. Em seguida, irá autorizar o seu cliente REST com o Azure AD ao utilizar o OAuth 2.0. Por fim, irá formar um URL significativo para chamar um recurso do armazém de dados.

[!INCLUDE [reports-credential-reqs](../includes/reports-credential-reqs.md)]

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

| Elemento | Exemplo | Description |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| location | msua06 | O URL base pode ser encontrado ao ver o painel API do Armazém de Dados no portal do Azure. |
| entity-collection | devicePropertyHistories | O nome da coleção da entidade do OData. Para obter mais informações sobre as coleções e entidades no modelo de dados, veja [Modelo de Dados](reports-ref-data-model.md). |
| api-version | beta | Versão da API a aceder. Para obter mais informações, veja [Versão](reports-api-url.md#api-version-information). |
| maxhistorydays | 7 | O número máximo de dias do histórico a obter (opcional). Este parâmetro pode ser fornecido a qualquer coleção, mas só entrará em vigor em coleções que incluam `dateKey` como parte da sua propriedade chave. Veja [Filtros de Intervalo DateKey](reports-api-url.md#datekey-range-filters) para obter mais informações. |

## <a name="api-version-information"></a>Informações sobre a versão da API

Agora, pode utilizar a versão v1.0 do Armazém de Dados do Intune, ao definir o parâmetro de consulta `api-version=v1.0`. As atualizações para coleções no Armazém de Dados são acumulativas por natureza e não interrompem cenários existentes.

Pode experimentar as nossas funcionalidades mais recentes do Armazém de Dados com a versão beta. Para utilizar a versão beta, o seu URL tem de conter o parâmetro de consulta `api-version=beta`. A versão beta oferece funcionalidades antes de estas estarem disponíveis globalmente como um serviço suportado. À medida que o Intune adiciona novas funcionalidades, a versão beta poderá alterar o contrato de dados e comportamento. Todos os códigos personalizados ou ferramentas de relatórios dependentes da versão beta poderão interromper as atualizações contínuas.

## <a name="odata-query-options"></a>Opções de consulta de OData

A versão atual dá suporte aos seguintes parâmetros de consulta OData: `$filter`, `$select`, `$skip,` e `$top`. Em `$filter`, somente `DateKey` ou `RowLastModifiedDateTimeUTC` podem ter suporte quando as colunas são aplicáveis e outras propriedades disparam uma solicitação inválida.

## <a name="datekey-range-filters"></a>Filtros de Intervalo DateKey

Os filtros de intervalo `DateKey` podem ser utilizados para limitar a quantidade de dados a transferir em algumas coleções com um filtro de intervalo `dateKey` como propriedade chave. O filtro `DateKey` pode ser utilizado para otimizar o desempenho do serviço ao proporcionar o seguinte parâmetro de consulta `$filter`:

1. O filtro `DateKey` sozinho no `$filter`, a apoiar os operadores `lt/le/eq/ge/gt` e a juntar-se ao operador lógico `and`, onde estes podem ser mapeados a uma data de início e/ou uma data de fim.
2. O filtro `maxhistorydays` é dado como uma opção de consulta personalizada.<br>

## <a name="filter-examples"></a>Exemplos de filtros

> [!NOTE]
> Os exemplos de filtro pressupõem que hoje é 2/21/2019.

|                             Filtro                             |           Otimização do Desempenho           |                                          Description                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    Completa                                      |    Devolver dados com um `DateKey` entre 20180214 e 20180221.                                     |
|    `$filter=DateKey eq 20180214`                                 |    Completa                                      |    Devolver dados com um `DateKey` igual a 20180214.                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    Completa                                      |    Devolver dados com um `DateKey` entre 20180214 e 20180220.                                     |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    Completa                                      |    Devolver dados com um `DateKey` igual a 20180214. `maxhistorydays` é ignorado.                            |
|    `$filter=RowLastModifiedDateTimeUTC ge 2018-02-21T23:18:51.3277273Z`                                |    Completa                                       |    Retornar dados com `RowLastModifiedDateTimeUTC` é maior ou igual a `2018-02-21T23:18:51.3277273Z`                             |
