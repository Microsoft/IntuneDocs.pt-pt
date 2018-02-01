---
title: "Utilizar o Armazém de Dados do Intune | Documentos da Microsoft"
description: "Pode utilizar o Armazém de Dados do Intune para criar relatórios que fornecem informações sobre o ambiente móvel da sua empresa."
keywords: "Armazém de Dados do Intune"
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 37ad088d722cfa2c543f43e4aa579a879dd4a4dd
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
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

> [!Note]
> Se estiver a utilizar a gestão de dispositivos móveis (MDM) híbrida com o System Center Configuration Manager (SCCM) e o Microsoft Intune significa que pretende obter os seus dados do SCCM. O Armazém de Dados do Intune contém apenas dados do Intune. Pode utilizar um dashboard do Power BI do SCCM para os seus relatórios personalizados. Para obter mais informações, veja "[Announcing the Power BI solution template for System Center Configuration Manager"]( https://powerbi.microsoft.com/blog/sccm-solution-template) (Anunciar o modelo de solução do Power BI para o System Center Configuration Manager) e "[Create a Power BI report and dashboard"](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/create-powerbi-report-dashboard) (Criar um relatório e dashboard do Power BI).


> [!Important]  
> Pode experimentar as nossas funcionalidades mais recentes do Armazém de Dados com a versão beta. Para utilizar a versão beta, o seu URL tem de conter o parâmetro de consulta `api-version=beta`. A versão beta oferece funcionalidades antes de estas estarem disponíveis globalmente como um serviço suportado. À medida que o Intune adiciona novas funcionalidades, a versão beta poderá alterar o contrato de dados e comportamento. Todos os códigos personalizados ou ferramentas de relatórios dependentes da versão beta poderão interromper as atualizações contínuas.

**Próximos passos**

- Obtenha uma ligação e utilize o Power BI para obter informações. Para obter instruções, consulte [Connect to the Data Warehouse with Power BI (Ligar ao Armazém de Dados do Intune com o Power BI – em inglês)](reports-proc-get-a-link-powerbi.md).
- Com a sua ligação, crie um relatório personalizado com o Power BI. Para obter instruções, veja [Create a report from the OData feed with Power BI (Criar um relatório a partir do feed OData com o Power BI)](reports-proc-create-with-odata.md).
- Para saber mais sobre a API do Armazém de Dados do Intune, o modelo de dados e as relações entre entidades<!-- , and an example of creating a custom client to retrieve data,-->, consulte a [API do Armazém de Dados do Intune](reports-nav-intune-data-warehouse.md).