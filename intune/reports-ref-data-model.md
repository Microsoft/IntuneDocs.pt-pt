---
title: "Modelo de dados do Armazém de Dados | Documentos da Microsoft"
description: "O Armazém de Dados do Intune copia dados diariamente para fornecer uma apresentação do histórico do seu ambiente móvel em contínua mudança."
keywords: "Armazém de Dados do Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d56935bc2828273af28323e40d9f3b4e2bd84025
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/04/2017
---
# <a name="data-warehouse-data-model"></a>Modelo de dados do Armazém de Dados

O Armazém de Dados do Intune copia dados diariamente para fornecer uma apresentação do histórico do seu ambiente móvel em contínua mudança.

Os dados extraídos do seu inquilino são adicionados a um armazém de dados. O armazém é um conjunto de entidades e relações com significado para o tipo de questões que pretende perguntar. Por exemplo, pode rever o número de instalações por dia de uma aplicação Android desenvolvida internamente durante a última semana para saber se existe uma tendência crescente de instalações. A estrutura do armazém de dados permite-lhe obter informações sobre o seu ambiente móvel. Por sua vez, as ferramentas de análise, como o Microsoft Power BI, podem utilizar o modelo de dados do Armazém de Dados para criar visualizações e dashboards dinâmicos.

A estrutura do Armazém de Dados do Intune utiliza um modelo de esquema de estrela. Um esquema de estrela organiza os factos ao longo da dimensão de tempo. Um *facto* no contexto do modelo é uma medida quantitativa, como o número de dispositivos, número de aplicações ou momento de inscrição. Uma *dimensão* no contexto do modelo é um conjunto de categorias e das respetivas relações hierárquicas. Por exemplo, os dias são agrupados em meses e os meses são agrupados em anos. Um modelo de esquema de estrela é otimizado para flexibilidade e análise de dados para que possa criar os relatórios necessários para compreender o seu ambiente móvel em evolução.

O armazém expõe os dados nas seguintes categorias de nível superior:
  -  Utilização e aplicações com proteção de aplicações ativada
  -  Dispositivos inscritos, propriedades e inventário
  -  Inventário de aplicações e software
  -  Políticas de conformidade e de configuração de dispositivos

**Conjuntos de entidades de modelo de dados**

Os conjuntos de entidades chamam-se coleções de entidades no modelo de dados. Estes conjuntos contêm entidades que definem os dados colecionados no modelo. Cada conjunto de entidades fornece um ponto de acesso no modelo de dados do Armazém de Dados. Encontrará detalhes sobre as seguintes categorias de entidades:

  -  [Date](reports-ref-date.md)
  -  [User](reports-ref-user.md)
  -  [Mobile App Management (MAM)](reports-ref-mobile-app-management.md)
  -  [Devices](reports-ref-devices.md)
  -  [Application](reports-ref-application.md)
  -  [Policy](reports-ref-policy.md)

<!-- ## Data Model relationships

For more information on the relationships in the data model, see [Relationships of Entities](). -->