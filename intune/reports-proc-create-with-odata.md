---
title: Criar um relatório do Intune no feed OData com Power BI
titleSuffix: Microsoft Intune
description: Crie uma visualização de treemap com o Power BI Desktop com um filtro interativo da API do Armazém de Dados do Microsoft Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4494d5f75336f7152668cfa1bb6fa1cd1a94305c
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167855"
---
# <a name="create-an-intune-report-from-the-odata-feed-with-power-bi"></a>Criar um relatório do Intune no feed OData com Power BI

Este artigo explica como criar uma visualização de mapa de arquivo de seus dados do Intune usando Power BI Desktop que os usuários têm um filtro interativo. Por exemplo, seu CFO pode gostar de saber como a distribuição geral de dispositivos é comparada entre dispositivos de propriedade da empresa e dispositivos pessoais. O treemap fornece informações sobre o número total de tipos de dispositivos. Pode analisar o número de dispositivos iOS, Android e Windows pessoais ou pertencentes à empresa.

## <a name="overview-of-creating-the-chart"></a>Descrição geral da criação do gráfico

Para criar este gráfico, irá:
1. Instalar o Power BI Desktop, caso ainda não o tenha feito.
2. Ligar-se ao modelo de dados do Armazém de Dados do Intune e obter dados atuais para o modelo.
3. Criar ou gerir as relações do modelo de dados.
4. Criar o gráfico com dados da tabela **Dispositivos**.
5. Criar um filtro interativo.
6. Ver o gráfico final.

### <a name="a-note-about-tables-and-entities"></a>Uma nota sobre tabelas e entidades

Trabalha com tabelas no Power BI. Uma tabela contém campos de dados. Cada campo de dados tem um tipo de dados. O campo só pode conter dados do tipo de dados. Os tipos de dados são números, texto, datas, entre outros. Quando carrega o modelo, as tabelas no Power BI são preenchidas com dados do histórico recentes do seu inquilino. Embora os dados específicos sejam alterados com o tempo, a estrutura da tabela não será alterada a menos que o modelo de dados subjacente seja atualizado.

A utilização do termo *entidade* e *tabela* poderá ser confusa. O modelo de dados pode ser acessado por meio de um feed OData (Protocolo Open Data). No universo do OData, os contentores denominados tabelas no Power BI são designados entidades. Estes termos referem-se ao mesmo elemento que contém os seus dados. Para obter mais informações sobre OData, consulte a [visão geral do OData](/odata/overview).

## <a name="install-power-bi-desktop"></a>Instalar o Power BI Desktop

Instale a versão mais recente do Power BI Desktop. Você pode baixar Power BI Desktop de: [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Ligar-se ao feed OData do Armazém de Dados do Intune do seu inquilino

> [!Note]  
> Precisa de permissão para aceder a **Relatórios** no Intune. Para obter mais informações, veja [Autorização](reports-api-url.md).

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Abra o painel **data warehouse do Intune** selecionando o link data warehouse em **outras tarefas** no lado direito da folha **Microsoft Intune-visão geral** .
3. Copie o URL do feed personalizado. Por exemplo: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
4. Abra o Power BI Desktop.
5. Na menu de menus, selecione **arquivo** > **obter Data** > **OData feed**.
6. Cole a URL de feed personalizada, que você copiou da etapa anterior, na caixa URL na janela **feed OData** .
7. Selecione **Básico**.

    ![Feed OData para o data warehouse do Intune para seu locatário](media/reports-create-01-odatafeed.png)

8. Selecione **OK**.
9. Selecione **Conta escolar ou profissional** e, em seguida, inicie sessão com as suas credenciais do Intune.

    ![Credenciais da conta escolar ou profissional](media/reports-create-02-org-account.png)

10. Selecione **Ligar**. O Navegador será aberto e irá mostrar-lhe a lista de tabelas no Armazém de Dados do Intune.

    ![Captura de tela do navegador – a lista de tabelas de data warehouse](media/reports-create-02-loadentities.png)

11. Selecione as tabelas **Dispositivos** e **TiposdeProprietário**.  Selecione **Carregar**. O Power BI carrega os dados para o modelo.

## <a name="create-a-relationship"></a>Criar uma relação

Pode importar múltiplas tabelas para analisar não só os dados numa única tabela, mas também os dados relacionados nas tabelas. Power BI tem um recurso chamado **AutoDetect** que tenta localizar e criar relações para você. As tabelas na data warehouse foram criadas para funcionar com o recurso de detecção automática no Power BI. No entanto, mesmo que Power BI não encontre automaticamente as relações, você ainda poderá gerenciar as relações.

![Gerenciar relações de dados relacionados entre tabelas](media/reports-create-03-managerelationships.png)

1. Selecione **Gerir Relações**.
2. Selecione **detecção automática...** se Power bi ainda não tiver detectado as relações.

A relação é apresentada numa coluna De para uma coluna Para. Neste exemplo, o campo de dados **ChavedoTipodeProprietário** na tabela **Dispositivos** liga-se ao campo de dados **ChavedoTipodeProprietário** na tabela **TiposdeProprietário**. Você usa a relação para pesquisar o nome sem formatação do código do tipo de dispositivo na tabela **dispositivos** .

## <a name="create-a-treemap-visualization"></a>Criar uma visualização de treemap

Um gráfico de mapa de plano mostra dados hierárquicos como caixas nas caixas. Cada ramo da hierarquia é uma caixa com caixas mais pequenas a mostrar sub-ramos. Você pode usar Power BI área de trabalho para criar um mapa de estrutura de dados de locatário do Intune que mostra quantidades relativas de tipos de fabricante de dispositivo.

![Power BIndo visualizações do mapa de mapas](media/reports-create-03-treemap.png)

1. No painel **visualizações** , localize e selecione **mapa**de página. O gráfico de **mapa** de plano será adicionado à tela de relatório.
2. No painel **campos** , localize a `devices` tabela.
3. Expanda `devices` a tabela e selecione `manufacturer` o campo de dados.
4. Arraste o `manufacturer` campo de dados para a tela relatório e solte-o no gráfico **mapa** de plano.
5. Arraste o `deviceKey` campo `devices` de dados da tabela para o painel **visualizações** e solte-o na seção **valores** na caixa rotulada **adicionar campos de dados aqui**.  

Agora, tem um elemento visual que mostra a distribuição dos fabricantes de dispositivos na sua organização.

![Mapa de mapas com dados-a distribuição de fabricantes de dispositivos](media/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Adicionar um filtro

Pode adicionar um filtro ao seu treemap para poder responder a perguntas adicionais com a sua aplicação.

1. Para adicionar um filtro, selecione a tela de relatório e, em seguida, selecione o **ícone** de segmentação (![mapa de janela](media/reports-create-slicer.png)com o modelo de dados e relações com suporte) em **visualizações**. A visualização de **segmentação** vazia será exibida na tela.
2. No painel **campos** , localize a `ownerTypes` tabela.
3. Expanda `ownerTypes` a tabela e selecione `ownerTypeName` o campo de dados.
4. Arraste o `onwerTypeName` campo `ownerTypes` de dados da tabela para o painel **filtros** e solte-o na seção **filtros nesta página** na caixa rotulada **adicionar campos de dados aqui**.  

   Na tabela, há um campo de dados chamado `OwnerTypeKey`que contém dados como se um dispositivo é de propriedade da empresa ou pessoal. `OwnerTypes` Como você gostaria de mostrar nomes amigáveis nesse filtro, procure a `ownerTypes` tabela e arraste o **ownerTypeName** para a segmentação. Este exemplo mostra de que forma o modelo de dados suporta relações entre tabelas.

![Mapa de mapas com filtro-dá suporte a relações entre tabelas](media/reports-create-08_ownertype.png)

Agora tem um filtro interativo que pode utilizar para alternar entre dispositivos pessoais e dispositivos pertencentes à empresa. Utilize este filtro para ver como a distribuição é alterada.

1. Selecione **empresa** dentro da segmentação para ver a distribuição de dispositivos de propriedade da empresa.
2. Selecione **pessoal** na segmentação para ver os dispositivos de propriedade pessoal.

## <a name="next-steps"></a>Passos seguintes

- Saiba mais sobre como [criar e gerir relações](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) no Power BI Desktop na documentação do Power BI.
- Consulte o [Modelo do Armazém de Dados do Intune](reports-ref-data-model.md).
