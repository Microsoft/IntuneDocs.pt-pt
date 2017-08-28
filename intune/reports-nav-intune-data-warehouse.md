---
title: "API do Armazém de Dados do Intune | Documentos da Microsoft"
description: "Pode utilizar a API para criar relatórios que fornecem informações sobre o ambiente móvel da sua empresa."
keywords: "Armazém de Dados do Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 701D6CE9-43F6-4A29-8E84-E2B59931C635
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 52b498beb024b86282c93be7aa5a248800db6609
ms.sourcegitcommit: 294de4d4058de2c625abb8143e90880d27da9284
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/15/2017
---
#  <a name="intune-data-warehouse-api"></a>API do Armazém de Dados do Intune

A API do Armazém de Dados do Intune permite-lhe aceder aos seus dados do Intune num formato legível por máquina para utilizar na sua ferramenta de análise favorita. Pode utilizar a API para criar relatórios que fornecem informações sobre o ambiente móvel da sua empresa. A API utiliza o protocolo OData, que segue os padrões normais para:

  -   Cabeçalhos de pedidos e respostas
  -   Códigos de estado
  -   Métodos HTTP
  -   Convenções de URLs
  -   Tipos de suporte de dados
  -   Formatos de payload
  -   Opções de consulta

O OData (Protocolo Open Data) é um padrão de OASIS (Organização para o Avanço dos Padrões de Informação Estruturada) que define a melhor prática para criar e consumir APIs RESTful. O Armazém de Dados do Intune utiliza a versão 4.0 do OData.

Esta secção de referência fornece uma descrição geral dos pontos finais, métodos HTTP suportados, devolução de formatos de payload e documentação do modelo de dados do Armazém de Dados do Intune.

> [!Important]  
> Pode experimentar as nossas funcionalidades mais recentes do Armazém de Dados com a versão beta. Para utilizar a versão beta, o seu URL tem de conter o parâmetro de consulta `api-version=beta`. A versão beta oferece funcionalidades antes de estas estarem disponíveis globalmente como um serviço suportado. À medida que o Intune adiciona novas funcionalidades, a versão beta poderá alterar o contrato de dados e comportamento. Todos os códigos personalizados ou ferramentas de relatórios dependentes da versão beta poderão interromper as atualizações contínuas. <!--If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

## <a name="odata-custom-client"></a>Cliente personalizado OData

Pode aceder ao modelo de dados do Armazém de Dados do Intune através de ponto finais RESTful. Para obter acesso aos seus dados, o seu cliente tem de conceder autorização com o Microsoft Azure Active Directory (Azure AD) com OAuth 2.0. Primeiro configura uma aplicação Web e uma aplicação cliente no Azure, e concede permissões ao cliente. O seu cliente local receberá autorização e poderá, em seguida, comunicar com os pontos finais do Armazém de Dados.

Para obter mais informações, veja [Get data from the Data Warehouse API with a REST client (Obter dados a partir da API do Armazém de Dados com um cliente REST)](reports-proc-data-rest.md)

## <a name="interacting-with-the-api"></a>Interagir com a API

A API necessita de autorização com o Azure AD. O Azure AD utiliza o OAuth 2.0. Assim que for autorizado, poderá obter dados a partir da API com um verbo HTTP GET e ao contactar as coleções da entidade expostas. Para obter mais detalhes, veja:

 -  [Autorização](reports-api-url.md)
 -  [Estrutura do URL da API](reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Modelo de dados do Armazém de Dados do Intune

O OData define um modelo de dados abstrato e um protocolo que permite a qualquer cliente aceder às informações expostas por qualquer origem de dados. O tópico de documentação do modelo de dados contém uma explicação sobre os espaços de nomes, entidades e objetos devolvidos no modelo de dados do Armazém de Dados do Intune. Para obter mais informações, veja [Modelo de Dados do Armazém de Dados](reports-ref-data-model.md).

## <a name="next-steps"></a>Próximos passos

[Cenários de Autenticação do Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)  
[odata.org](http://www.odata.org)  
[Versão 4.0 do OData](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)  