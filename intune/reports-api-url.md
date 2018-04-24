---
title: Ponto final da API do Armazém de Dados do Intune
titlesuffix: Microsoft Intune
description: O tópico de referência descreve a estrutura do URL da API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2b25140cb5c3c8c70ff42186352362c57dcf6ee7
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="intune-data-warehouse-api-endpoint"></a>Ponto final da API do Armazém de Dados do Intune

Pode utilizar a API do Armazém de Dados do Intune com uma conta com controlos de acesso baseados em funções específicos e credenciais do Azure AD. Em seguida, irá autorizar o seu cliente REST com o Azure AD ao utilizar o OAuth 2.0. Por fim, irá formar um URL significativo para chamar um recurso do armazém de dados.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="authorization"></a>Autorização

O Azure Active Directory (Azure AD) utiliza o OAuth 2.0 para lhe permitir autorizar o acesso a aplicações Web e a APIs Web no seu inquilino do Azure AD. Este guia é independente do idioma e descreve como enviar e receber mensagens HTTP sem utilizar as suas bibliotecas open-source. O fluxo do código de autorização de OAuth 2.0 é descrito na [secção 4.1](https://tools.ietf.org/html/rfc6749#section-4.1) da especificação de OAuth 2.0.

Para obter mais informações, veja [Authorize access to web applications using OAuth 2.0 and Azure Active Directory (Autorizar o acesso a aplicações Web com o OAuth 2.0 e o Azure Active Directory)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).

## <a name="api-url-structure"></a>Estrutura do URL da API

Os pontos finais da API do Armazém de Dados leem as entidades para cada conjunto. A API suporta um verbo **GET** HTTP e um subconjunto de opções de consulta.

O URL do Intune utiliza o seguinte formato:  
https://fef.{<strong><em>location</em></strong>}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{<strong><em>entity-collection</em></strong>}?api-version={<strong><em>api-version</em></strong>}

O URL contém os seguintes elementos:

| Elemento | Exemplo | Descrição |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| location | msua06 | O URL base pode ser encontrado ao ver o painel API do Armazém de Dados no portal do Azure. |
| entity-collection | datas | O nome da coleção da entidade do OData. Para obter mais informações sobre as coleções e entidades no modelo de dados, veja [Modelo de Dados](reports-ref-data-model.md). |
| api-version | beta | Versão da API a aceder. Para obter mais informações, veja [Versão](#API-version-information). |


## <a name="api-version-information"></a>Informações sobre a versão da API

A versão atual da API é: `beta`. 

## <a name="odata-query-options"></a>Opções de consulta de OData

A versão atual suporta os seguintes parâmetros de consulta de OData: `$filter, $orderby, $select, $skip,` e `$top`.