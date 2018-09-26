---
title: Criar um relatório a partir do feed OData com o Power BI
titlesuffix: Microsoft Intune
description: Crie uma visualização de treemap com o Power BI Desktop com um filtro interativo da API do Armazém de Dados do Microsoft Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f4425f508164332295899a6132782833889aa830
ms.sourcegitcommit: bea4a81d262607c6e9dd1e26f5cd1a2faf7d051b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/14/2018
ms.locfileid: "45602270"
---
# <a name="create-a-report-from-the-odata-feed-with-power-bi"></a>Criar um relatório a partir do feed OData com o Power BI

Este artigo explica como criar uma visualização de treemap com o Power BI Desktop com um filtro interativo. Por exemplo, o seu Diretor Financeiro poderá gostar da forma como a distribuição geral de dispositivos compara dispositivos pertencentes à empresa e dispositivos pessoais. O treemap fornece informações sobre o número total de tipos de dispositivos. Pode analisar o número de dispositivos iOS, Android e Windows pessoais ou pertencentes à empresa.

### <a name="overview-of-creating-the-chart"></a>Descrição geral da criação do gráfico

Para criar este gráfico, tem de:
1. Instalar o Power BI Desktop, caso ainda não o tenha feito.
2. Ligar-se ao modelo de dados do Armazém de Dados do Intune e obter dados atuais para o modelo.
3. Criar ou gerir as relações do modelo de dados.
4. Criar o gráfico com dados da tabela **Dispositivos**.
5. Criar um filtro interativo.
6. Ver o gráfico final.

### <a name="a-note-about-tables-and-entities"></a>Uma nota sobre tabelas e entidades

Trabalha com tabelas no Power BI. Uma tabela contém campos de dados. Cada campo de dados tem um tipo de dados. O campo só pode conter dados do tipo de dados. Os tipos de dados são números, texto, datas, entre outros. Quando carrega o modelo, as tabelas no Power BI são preenchidas com dados do histórico recentes do seu inquilino. Embora os dados específicos sejam alterados com o tempo, a estrutura da tabela não será alterada a menos que o modelo de dados subjacente seja atualizado.

A utilização do termo _entidade_ e _tabela_ poderá ser confusa. O modelo de dados está acessível através de um feed OData. No universo do OData, os contentores denominados tabelas no Power BI são designados entidades. Estes termos referem-se ao mesmo elemento que contém os seus dados.

## <a name="install-power-bi-desktop"></a>Instalar o Power BI Desktop

Instale a versão mais recente do Power BI Desktop. Pode transferir o Power BI Desktop em: [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Ligar-se ao feed OData do Armazém de Dados do Intune do seu inquilino

> [!Note]  
> Precisa de permissão para aceder a **Relatórios** no Intune. Para obter mais informações, veja [Autorização](reports-api-url.md).

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Abra o painel **Armazém de Dados do Intune**.
4. Copie o URL do feed personalizado. Por exemplo: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
5. Abra o Power BI Desktop.
6. Selecione **Obter Dados** > **Feed OData**.
7. Cole o URL do feed personalizado na caixa URL na janela **Feed OData**.
8. Selecione **Básico**.

    ![Feed OData](media/reports-create-01-odatafeed.png)

9. Selecione **OK**.
10. Selecione **Conta escolar ou profissional** e, em seguida, inicie sessão com as suas credenciais do Intune.

    ![Credenciais da conta escolar ou profissional](media/reports-create-02-org-account.png)

11. Selecione **Ligar**. O Navegador será aberto e irá mostrar-lhe a lista de tabelas no Armazém de Dados do Intune.

    ![O Navegador](media/reports-create-02-loadentities.png)

12. Selecione as tabelas **Dispositivos** e **TiposdeProprietário**.  Selecione **Carregar**. O Power BI carrega os dados para o modelo.

## <a name="create-a-relationship"></a>Criar uma relação

Pode importar múltiplas tabelas para analisar não só os dados numa única tabela, mas também os dados relacionados nas tabelas.  O Power BI tem uma funcionalidade denominada **Deteção automática** que tenta localizar e criar relações automaticamente. As tabelas no Armazém de Dados foram criadas para trabalharem com a funcionalidade Deteção automática do Power BI. No entanto, mesmo se o Power BI não localizar automaticamente as relações, ainda pode gerir as mesmas.

![Gerir relações](media/reports-create-03-managerelationships.png)

1. Selecione **Gerir Relações**.
2. Selecione **Deteção automática...** caso o Power BI não tenha ainda detetado as relações.

A relação é apresentada numa coluna De para uma coluna Para. Neste exemplo, o campo de dados **ChavedoTipodeProprietário** na tabela **Dispositivos** liga-se ao campo de dados **ChavedoTipodeProprietário** na tabela **TiposdeProprietário**. Utiliza as relações para procurar um nome simples do código do tipo de dispositivo na tabela **Dispositivos**.

## <a name="create-a-treemap-visualization"></a>Criar uma visualização de treemap

Um gráfico treemap mostra dados hierárquicos como caixas em caixas. Cada ramo da hierarquia é uma caixa com caixas mais pequenas a mostrar sub-ramos. Pode utilizar o Power BI Desktop para criar um treemap dos seus dados do Intune.

![Visualizações > treemap](media/reports-create-03-treemap.png)

1. Selecione um tipo de gráfico. Selecione **Treemap**.
2. No modelo de dados, localize a tabela **Dispositivos**.
3. Expanda a **tabela Dispositivos** e selecione o campo de dados **Fabricante** no painel **Campos**.
4. Arraste o campo de dados **Fabricante** para o gráfico Treemap na tela do relatório.
5. Arraste o campo de dados **ChavedeDispositivo** da tabela **Dispositivos** para a secção **Valores** no painel **Visualizações** e largue na caixa etiquetada **Arrastar o campo de dados para aqui**.  

Agora, tem um elemento visual que mostra a distribuição dos fabricantes de dispositivos na sua organização.

![Treemap com dados](media/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Adicionar um filtro

Pode adicionar um filtro ao seu treemap para poder responder a perguntas adicionais com a sua aplicação.


1. Para adicionar um filtro, selecione a tela do relatório e, em seguida, selecione o **Ícone de segmentação de dados** (![Treemap com dados](media/reports-create-slicer.png)) em **Visualizações**.
2. Localize a tabela **TiposdeProprietário** e arraste o campo de dados **NomedoTipodeProprietário** na secção **Filtros** no painel **Visualizações**.  

   Na tabela Dispositivos, existe um campo de dados denominado **ChavedoTipodeProprietário** que contém um código que identifica se um dispositivo é pessoal ou pertencente à empresa. Uma vez que pretende mostrar nomes amigáveis neste filtro, procure a tabela **TiposdeProprietário** e arraste o **NomedoTipodeProprietário**. Este exemplo mostra de que forma o modelo de dados suporta relações entre tabelas.

![Treemap com filtro](media/reports-create-08_ownertype.png)

Agora tem um filtro interativo que pode utilizar para alternar entre dispositivos pessoais e dispositivos pertencentes à empresa. Utilize este filtro para ver como a distribuição é alterada.

1. Selecione **Empresa** para ver a distribuição de dispositivos pertencentes à empresa.
2. Selecione **Pessoal** para ver os dispositivos pessoais.

## <a name="next-steps"></a>Próximos passos

 - Saiba mais sobre como [criar e gerir relações](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) no Power BI Desktop na documentação do Power BI.
 - Consulte o [Modelo do Armazém de Dados do Intune](https://docs.microsoft.com/intune/reports-ref-data-model).
