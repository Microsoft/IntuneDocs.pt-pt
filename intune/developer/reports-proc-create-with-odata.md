---
title: Criar um relatório do Intune a partir do feed OData com o Power BI
titleSuffix: Microsoft Intune
description: Crie uma visualização de treemap com o Power BI Desktop com um filtro interativo da API do Armazém de Dados do Microsoft Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7fbbffb187fc9e9537bf647bc33e3d98879369c3
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576060"
---
# <a name="create-an-intune-report-from-the-odata-feed-with-power-bi"></a>Criar um relatório do Intune a partir do feed OData com o Power BI

Este artigo explica como criar uma visualização do mapa de árvores dos seus dados Intune usando o Power BI Desktop que os utilizadores usam um filtro interativo. Por exemplo, o seu CFO pode gostar de saber como a distribuição global de dispositivos se compara entre dispositivos da empresa e dispositivos pessoais. O treemap fornece informações sobre o número total de tipos de dispositivos. Pode rever o número de dispositivos iOS/iPadOS, Android e Windows que sejam propriedade da empresa ou propriedade pessoal.

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

A utilização do termo *entidade* e *tabela* poderá ser confusa. O modelo de dados é acessível através de um feed OData (Open Data Protocol). No universo do OData, os contentores denominados tabelas no Power BI são designados entidades. Estes termos referem-se ao mesmo elemento que contém os seus dados. Para mais informações sobre o OData, consulte a visão geral do [OData](/odata/overview).

## <a name="install-power-bi-desktop"></a>Instalar o Power BI Desktop

Instale a versão mais recente do Power BI Desktop. Pode transferir o Power BI Desktop em: [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Ligar-se ao feed OData do Armazém de Dados do Intune do seu inquilino

> [!Note]  
> Precisa de permissão para aceder a **Relatórios** no Intune. Para obter mais informações, veja [Autorização](../reports-api-url.md).

1. Inscreva-se em [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Abra o painel **Intune Data Warehouse** selecionando o link Data Warehouse em **outras tarefas** no lado direito da **microsoft Intune - lâmina de visão geral.**
3. Copie o URL do feed personalizado. Por exemplo: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
4. Abra o Power BI Desktop.
5. A partir da barra de menus, selecione **File** > **Obter Dados** > **feed Odata**.
6. Colhe o URL de alimentação personalizado, que copiou do passo anterior, para a caixa DEL Na janela de **alimentação OData.**
7. Selecione **Básico**.

    ![Feed OData para o Intune Data Warehouse para o seu inquilino](./media/reports-proc-create-with-odata/reports-create-01-odatafeed.png)

8. Selecione **OK**.
9. Selecione **Conta escolar ou profissional** e, em seguida, inicie sessão com as suas credenciais do Intune.

    ![Credenciais da conta escolar ou profissional](./media/reports-proc-create-with-odata/reports-create-02-org-account.png)

10. Selecione **Ligar**. O Navegador será aberto e irá mostrar-lhe a lista de tabelas no Armazém de Dados do Intune.

    ![Screenshot do Navegador - A lista de tabelas data Warehouse](./media/reports-proc-create-with-odata/reports-create-02-loadentities.png)

11. Selecione as tabelas **Dispositivos** e **TiposdeProprietário**.  Selecione **Carregar**. O Power BI carrega os dados para o modelo.

## <a name="create-a-relationship"></a>Criar uma relação

Pode importar múltiplas tabelas para analisar não só os dados numa única tabela, mas também os dados relacionados nas tabelas. O Power BI tem uma funcionalidade chamada **auto-detecte** que tenta encontrar e criar relações para si. As tabelas do Data Warehouse foram construídas para trabalhar com a funcionalidade de deteção automática no Power BI. No entanto, mesmo que o Power BI não encontre automaticamente as relações, ainda pode gerir as relações.

![Gerir relações de dados relacionados entre tabelas](./media/reports-proc-create-with-odata/reports-create-03-managerelationships.png)

1. Selecione **Gerir Relações**.
2. Selecione **Autodetect...** se o Power BI ainda não detetou as relações.

A relação é apresentada numa coluna De para uma coluna Para. Neste exemplo, o campo de dados **ChavedoTipodeProprietário** na tabela **Dispositivos** liga-se ao campo de dados **ChavedoTipodeProprietário** na tabela **TiposdeProprietário**. Usa a relação para procurar o nome simples do código do tipo dispositivo na tabela de **dispositivos.**

## <a name="create-a-treemap-visualization"></a>Criar uma visualização de treemap

Um gráfico de mapa de árvores mostra dados hierárquicos como caixas dentro de caixas. Cada ramo da hierarquia é uma caixa com caixas mais pequenas a mostrar sub-ramos. Pode utilizar o ambiente de trabalho Power BI para criar um mapa de árvores dos dados do seu inquilino Intune que mostre quantidades relativas de tipos de fabricantes de dispositivos.

![Visualizações de mapa de árvores Power BI](./media/reports-proc-create-with-odata/reports-create-03-treemap.png)

1. No painel **de Visualizações,** encontre e selecione **Treemap**. O gráfico **do Treemap** será adicionado à tela do relatório.
2. No painel **Fields,** encontre a mesa `devices`.
3. Expanda a tabela `devices` e selecione o campo de dados `manufacturer`.
4. Arraste o campo de dados `manufacturer` para a tela do relatório e deixe-o cair no gráfico do **Treemap.**
5. Arraste o campo de dados `deviceKey` da tabela `devices` para o painel **de Visualizações** e deixe-o cair sob a secção **Valores** na caixa rotulada Adicionar campos de **dados aqui**.  

Agora, tem um elemento visual que mostra a distribuição dos fabricantes de dispositivos na sua organização.

![Treemap com dados - A distribuição de fabricantes de dispositivos](./media/reports-proc-create-with-odata/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Adicionar um filtro

Pode adicionar um filtro ao seu treemap para poder responder a perguntas adicionais com a sua aplicação.

1. Para adicionar um filtro, selecione a tela do relatório e, em seguida, selecione o **ícone Slicer** (![Treemap com modelo de dados e relações apoiadas](./media/reports-proc-create-with-odata/reports-create-slicer.png)) no âmbito de **Visualizações**. A visualização vazia do **Slicer** aparecerá na tela.
2. No painel **Fields,** encontre a mesa `ownerTypes`.
3. Expanda a tabela `ownerTypes` e selecione o campo de dados `ownerTypeName`.
4. Arraste o campo de dados `onwerTypeName` da tabela `ownerTypes` para o painel dos **Filtros** e deixe-o cair sob os **Filtros nesta** secção de página na caixa rotulada Adicionar campos de **dados aqui**.  

   Sob a tabela `OwnerTypes`, há um campo de dados chamado `OwnerTypeKey`que contém dados sobre se um dispositivo é propriedade da empresa ou pessoal. Uma vez que gostaria de mostrar nomes amigáveis neste filtro, procure a tabela `ownerTypes` e arraste o **proprietárioTypeName** para o Slicer. Este exemplo mostra de que forma o modelo de dados suporta relações entre tabelas.

![Treemap com filtro - Suporta relações entre mesas](./media/reports-proc-create-with-odata/reports-create-08_ownertype.png)

Agora tem um filtro interativo que pode utilizar para alternar entre dispositivos pessoais e dispositivos pertencentes à empresa. Utilize este filtro para ver como a distribuição é alterada.

1. Selecione **Empresa** dentro do Slicer para ver se a empresa possui a distribuição de dispositivos.
2. Selecione **Personal** dentro do Slicer para ver os dispositivos pessoais.

## <a name="next-steps"></a>Próximos passos

- Saiba mais sobre como [criar e gerir relações](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) no Power BI Desktop na documentação do Power BI.
- Consulte o [Modelo do Armazém de Dados do Intune](reports-ref-data-model.md).
