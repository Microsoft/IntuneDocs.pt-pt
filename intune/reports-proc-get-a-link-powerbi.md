---
title: "Estabelecer uma ligação ao Armazém de Dados com o Power BI | Documentos da Microsoft"
description: "Pode transferir um ficheiro para utilizar com o Microsoft Power BI que lhe permite carregar relatórios interativos gerados automaticamente para o seu inquilino do Intune."
keywords: "Armazém de Dados do Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a9d99b71b9f84eea45ae597ed0f69010f6e95805
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/04/2017
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Estabelecer uma ligação ao Armazém de Dados com o Power BI

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Pode transferir um ficheiro para utilizar com o Microsoft Power BI que lhe permite carregar relatórios interativos gerados automaticamente para o seu inquilino do Intune. O ficheiro do Power BI (pbix) do Armazém de Dados contém definições de ligação ao seu inquilino e os seguintes gráficos e relatórios de exemplo: 

  -  Dispositivos
  -  Inscrição
  -  Política de proteção de aplicações
  -  Política de conformidade
  -  Perfis de configuração de dispositivos
  -  Atualizações de software
  -  Relatórios do inventário de dispositivos

Também existem tendências destacadas para a inscrição, conformidade, perfil de configuração do dispositivo e atualizações de software. Os relatórios e gráficos de exemplo aplicam filtros fáceis de utilizar à tela. Para utilizar filtros avançados, consulte o painel **Filtros** no Power BI Desktop. 

Os seguintes passos mostram como transferir o ficheiro do Power BI e como utilizar a ligação de OData com o Power BI.

## <a name="install-power-bi"></a>Instalar o Power BI

Instale a versão mais recente do Power BI Desktop. Pode transferir o Power BI Desktop em: [PowerBI.microsoft.com](https://powerbi.microsoft.com/en-us/desktop) 

## <a name="load-the-data-and-reports-using-the-power-bi-file-pbix"></a>Carregar os dados e relatórios com o ficheiro do Power BI (pbix)

O ficheiro do Power BI (pbix) contém informações de ligação para o seu inquilino e um conjunto de relatórios criados previamente com base no modelo de dados do Armazém de Dados. Abra o ficheiro no Power BI Desktop e inicie sessão no Azure AD. O relatório carrega os dados do seu inquilino do Intune.

1.  Inicie sessão no portal do Azure e selecione **Monitorização + Gestão** > **Intune**. Também pode procurar recursos para o **Intune**.  
2.  Abra o painel **API do Armazém de Dados do Microsoft Intune (Pré-visualização)**.
3.  Clique em **Transferir o ficheiro do Power BI**. O ficheiro com uma extensão (pbix) será transferido para a localização que especificar.
4.  Abra o ficheiro com o Power BI. Os *Relatórios do Armazém de Dados do Intune* são carregados, mas poderão demorar um momento a obter os dados do seu inquilino.
5.  Clique em **Atualizar** para carregar os dados do inquilino e rever os relatórios.
6.  Se o Power BI não tiver sido autenticado com as suas credenciais do Azure Active Directory, o Power BI irá pedir-lhe que forneça as suas credenciais. Ao selecionar as suas credenciais, escolha **Conta organizacional** como o seu método de autenticação.

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>Carregue os dados no Power BI com a ligação de OData

Com um cliente autenticado no Azure AD, o URL de OData liga-se ao ponto final RESTful na API do Armazém de Dados que expõe o modelo de dados ao seu cliente de relatórios. Siga estas instruções para utilizar o Power BI Desktop para ligar e criar os seus próprios relatórios. Não está limitado ao Power BI Desktop, mas pode utilizar a sua ferramenta de análise favorita com o URL de OData fornecido. O cliente suporta autenticações OAUTH2.0 e OData v4.0 Standard.

1.  Obtenha o **URL de OData** no painel de relatórios, por exemplo `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`.
2.  Abra o **Power BI Desktop**.
3.  Selecione **Base** > **Obter Dados**. Selecione **Feed OData**.
4.  Selecione **Básico**.
5.  Escreva ou cole o **URL de OData** na caixa URL.
6.  Clique em **OK**.
7.  Se não tiver sido autenticado no Azure AD para o seu inquilino do cliente de ambiente de trabalho do Power BI, escreva as suas credenciais.  
    a.  Selecione **Conta organizacional**.  
    b.  Escreva o nome de utilizador e a palavra-passe.  
    c.  Clique em **Iniciar Sessão.**  
    d.  Clique em **Ligar**.  
8.  Clique em **Carregar**.

## <a name="next-steps"></a>Próximos passos

Pode encontrar respostas a perguntas sobre o seu ambiente, como o número de dispositivos inscritos por dia durante a última semana. Pode obter informações sobre o seu inquilino do Intune e população de clientes através dos relatórios que utilizaram o ficheiro do Power BI (pbix) do Armazém de Dados do Intune obtido no painel no Azure. No entanto, o Intune proporciona muitas outras formas de expandir ou reutilizar os dados. Pode fazer muito mais com o Power BI e a API do Armazém de Dados do Intune, por exemplo:

<!-- -  You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
 -  Os dados do inquilino estão organizados para o ajudar a extrair informações dos seus dados. Para obter mais informações sobre a forma como os dados estão organizados, veja [Modelo de Dados do Armazém de Dados](reports-ref-data-model.md). 
<!-- -  You can also access the data from a RESTful interface and incorporate the data into your own app. For more information, see [Get data from the Data Warehouse API with a REST client](reports-proc-data-rest.md). -->