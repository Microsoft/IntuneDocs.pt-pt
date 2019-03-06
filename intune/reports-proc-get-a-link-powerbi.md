---
title: Estabelecer uma ligação ao Armazém de Dados com o Power BI
titlesuffix: Microsoft Intune
description: Pode transferir um ficheiro para utilizar com o Microsoft Power BI que lhe permite carregar relatórios interativos gerados automaticamente para o seu inquilino do Microsoft Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b911adab0357bea50e3e08821766d45e903e69b
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57394135"
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Estabelecer uma ligação ao Armazém de Dados com o Power BI

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>Instalar o Power BI

Instale a versão mais recente do Power BI Desktop. Pode transferir o Power BI Desktop em: [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="load-the-data-and-reports-using-the-power-bi-file-pbix"></a>Carregar os dados e relatórios com o ficheiro do Power BI (pbix)

O ficheiro do Power BI (pbix) contém informações de ligação para o seu inquilino e um conjunto de relatórios criados previamente com base no modelo de dados do Armazém de Dados. Abra o ficheiro no Power BI Desktop e inicie sessão no Azure AD. O relatório carrega os dados do seu inquilino do Intune.

> [!Important]  
> Cada ficheiro do Power BI (pbix) poderá ser diferente consoante a localização do inquilino. Se estiver a gerir múltiplos inquilinos do Intune, certifique-se de que utiliza o ficheiro transferido a partir do portal do Azure enquanto tem sessão iniciada nesse inquilino.  

1.  Inicie sessão no portal do Azure e selecione **Monitorização + Gestão** > **Intune**. Também pode procurar recursos para o **Intune**.  
2.  Abra o painel **API do Armazém de Dados do Microsoft Intune (Pré-visualização)**.
3.  Selecione **Transferir o ficheiro do Power BI**. O ficheiro com uma extensão (pbix) será transferido para a localização que especificar.
4.  Abra o ficheiro com o Power BI. Os *Relatórios do Armazém de Dados do Intune* são carregados, mas poderão demorar um momento a obter os dados do seu inquilino.
5.  Selecione **Atualizar** para carregar os seus dados de inquilino e rever os relatórios.
6.  Se o Power BI não tiver sido autenticado com as suas credenciais do Azure Active Directory, o Power BI irá pedir-lhe que forneça as suas credenciais. Ao selecionar as suas credenciais, escolha **Conta organizacional** como o seu método de autenticação.

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>Carregue os dados no Power BI com a ligação de OData

Com um cliente autenticado no Azure AD, o URL de OData liga-se ao ponto final RESTful na API do Armazém de Dados que expõe o modelo de dados ao seu cliente de relatórios. Siga estas instruções para utilizar o Power BI Desktop para ligar e criar os seus próprios relatórios. Não está limitado ao Power BI Desktop, mas pode utilizar a sua ferramenta de análise favorita com o URL de OData fornecido. O cliente suporta autenticações OAUTH2.0 e OData v4.0 Standard.

1.  Inicie sessão no portal do Azure e selecione **Monitorização + Gestão** > **Intune**. Também pode procurar recursos para o **Intune**.  
2.  Abra o painel **API do Armazém de Dados do Microsoft Intune (Pré-visualização)**.
3. Obtenha o URL de feed personalizado no painel de relatórios, por exemplo `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`
4. Abra o **Power BI Desktop**.
5. Selecione **Base** > **Obter Dados**. Selecione **Feed OData**.
6. Selecione **Básico**.
7. Escreva ou cole o **URL de OData** na caixa URL.
8. Selecione **OK**.
9. Se não tiver sido autenticado no Azure AD para o seu inquilino do cliente de ambiente de trabalho do Power BI, escreva as suas credenciais. Para obter acesso aos seus dados, tem de conceder autorização com o Azure Active Directory (Azure AD) com OAuth 2.0.  
    1.  Selecione **Conta organizacional**.  
    2.  Escreva o nome de utilizador e a palavra-passe.  
    3.  Selecione **Iniciar Sessão**.  
    4.  Selecione **Ligar**.  
10. Selecione **Carregar**.

## <a name="next-steps"></a>Passos Seguintes

Pode encontrar respostas a perguntas sobre o seu ambiente, como o número de dispositivos inscritos por dia durante a última semana. Pode obter informações sobre o seu inquilino do Intune e população de clientes através dos relatórios que utilizaram o ficheiro do Power BI (pbix) do Armazém de Dados do Intune obtido no painel no Azure. No entanto, o Intune proporciona muitas outras formas de expandir ou reutilizar os dados. Pode fazer muito mais com o Power BI e a API do Armazém de Dados do Intune, por exemplo:

<!-- -  You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
 -  Os dados do inquilino estão organizados para o ajudar a extrair informações dos seus dados. Para obter mais informações sobre a forma como os dados estão organizados, veja [Modelo de Dados do Armazém de Dados](reports-ref-data-model.md).
 -  Também pode aceder a dados de uma interface RESTful e incorporar os dados na sua própria aplicação. Para obter mais informações, veja [Get data from the Data Warehouse API with a REST client (Obter dados a partir da API do Armazém de Dados com um cliente REST)](reports-proc-data-rest.md).
