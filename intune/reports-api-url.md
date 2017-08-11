---
title: "Ponto final da API do Armazém de Dados do Intune | Documentos da Microsoft"
description: "O tópico de referência descreve a estrutura do URL da API."
keywords: "Armazém de Dados do Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7723bb42eedcd97142f039ca52b60911fa91838b
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/04/2017
---
# <a name="intune-data-warehouse-api-endpoint"></a>Ponto final da API do Armazém de Dados do Intune

Pode utilizar a API do Armazém de Dados do Intune com uma conta com controlos de acesso baseados em funções específicos e credenciais do Azure AD. Em seguida, irá autorizar o seu cliente REST com o Azure AD ao utilizar o OAuth 2.0. Por fim, irá formar um URL significativo para chamar um recurso do armazém de dados.

## <a name="azure-ad-and-intune-credential-requirements"></a>Requisitos de credenciais do Azure AD e do Intune

A autenticação e a autorização são baseadas nas credenciais do Azure AD e no controlo de acesso baseado em funções (RBAC) do Intune. Todos os administradores globais e administradores de serviço do Intune do seu inquilino têm acesso à API por predefinição. Utilize as funções do Intune para fornecer acesso a mais utilizadores ao oferecer-lhes acesso ao **Recurso de relatórios**.

Os requisitos para aceder à API são:

  -  A licença do Intune tem de estar atribuída ao utilizador
  -  O utilizador tem de ser um dos seguintes:
      -  Administrador global do Azure AD
      -  Um administrador de serviços do Intune
      -  Utilizador com acesso baseado em funções ao recurso de **Relatórios**

## <a name="authorization"></a>Autorização

O Azure Active Directory (Azure AD) utiliza o OAuth 2.0 para lhe permitir autorizar o acesso a aplicações Web e a APIs Web no seu inquilino do Azure AD. Este guia é independente do idioma e descreve como enviar e receber mensagens HTTP sem utilizar as suas bibliotecas open-source. O fluxo do código de autorização de OAuth 2.0 é descrito na [secção 4.1](https://tools.ietf.org/html/rfc6749#section-4.1) da especificação de OAuth 2.0.

Para obter mais informações, veja [Authorize access to web applications using OAuth 2.0 and Azure Active Directory (Autorizar o acesso a aplicações Web com o OAuth 2.0 e o Azure Active Directory)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).

## <a name="api-url-structure"></a>Estrutura do URL da API

Os pontos finais da API do Armazém de Dados leem as entidades para cada conjunto. A API suporta um verbo **GET** HTTP e um subconjunto de opções de consulta.

O URL do Intune utiliza o seguinte formato:  
https://fef.{***localização***}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{***coleção da entidade***}?api-version={***versão da api***}

O URL contém os seguintes elementos:

| Elemento | Exemplo | Descrição |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| location | msua06 | O URL base pode ser encontrado ao ver o painel API do Armazém de Dados no portal do Azure. |
| entity-collection | datas | O nome da coleção da entidade do OData. Para obter mais informações sobre as coleções e entidades no modelo de dados, veja [Modelo de Dados](reports-ref-data-model.md). |
| api-version | beta | Versão da API a aceder. Para obter mais informações, veja [Versão](#API-version-information). |


## <a name="api-version-information"></a>Informações sobre a versão da API

A versão atual da API é: `beta`. 

## <a name="odata-query-options"></a>Opções de consulta de OData

A versão atual suporta os seguintes parâmetros de consulta de OData: `$skip, $top, $filter, $orderby`.