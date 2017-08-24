---
title: "Utilizar o Armazém de Dados do Intune | Documentos da Microsoft"
description: "Pode utilizar o Armazém de Dados do Intune para criar relatórios que fornecem informações sobre o ambiente móvel da sua empresa."
keywords: "Armazém de Dados do Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: cb311429e0537709b3476154bdef24347cb99026
ms.sourcegitcommit: 294de4d4058de2c625abb8143e90880d27da9284
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/15/2017
---
# <a name="use-the-intune-data-warehouse"></a>Utilizar o Armazém de Dados do Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize o Armazém de Dados do Intune para criar relatórios que forneçam informações sobre o ambiente móvel da sua empresa. Por exemplo, alguns dos relatórios incluem:
-   Tendência de utilizadores a inscrever-se no Intune para poder otimizar as suas aquisições de licenças
-   Discriminação de versões de SO e aplicações para poder rever o estado dos dispositivos móveis
-   Tendências de conformidade de dispositivos e inscrições para poder implementar atualizações à política de forma simples

O Armazém de Dados dá-lhe acesso a mais informações sobre o seu ambiente móvel do que o portal do Azure. Com o Armazém de Dados do Intune, pode aceder a:

  -  Dados históricos do Intune
  -  Dados atualizados diariamente
  -  Um modelo de dados com utilização do padrão OData

> [!Important]  
> Pode experimentar as nossas funcionalidades mais recentes do Armazém de Dados com a versão beta. Para utilizar a versão beta, o seu URL tem de conter o parâmetro de consulta `api-version=beta`. A versão beta oferece funcionalidades antes de estas estarem disponíveis globalmente como um serviço suportado. À medida que o Intune adiciona novas funcionalidades, a versão beta poderá alterar o contrato de dados e comportamento. Todos os códigos personalizados ou ferramentas de relatórios dependentes da versão beta poderão interromper as atualizações contínuas. <!-- If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

**Próximos passos**

- Obtenha uma ligação e utilize o Power BI para obter informações. Para obter instruções, consulte [Connect to the Data Warehouse with Power BI (Ligar ao Armazém de Dados do Intune com o Power BI – em inglês)](reports-proc-get-a-link-powerbi.md).
- Para saber mais sobre a API do Armazém de Dados do Intune, o modelo de dados e as relações entre entidades<!-- , and an example of creating a custom client to retrieve data,-->, consulte a [API do Armazém de Dados do Intune](reports-nav-intune-data-warehouse.md).