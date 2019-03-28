---
title: Mover os dados da conta do Armazém de Dados do Intune
titlesuffix: Microsoft Intune
description: Compreenda como fazer cópias de segurança dos dados do Armazém de Dados do Intune ao mover a sua conta.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ee3ccbf9-82fc-4fbf-9d3d-8f05e431d090
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: c83ed35ab9c9c607f6283f2d5b18cf129f53cfab
ms.sourcegitcommit: d38ca1bf44e17211097aea481e00b6c1e87effae
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/27/2019
ms.locfileid: "58514369"
---
# <a name="move-your-intune-data-warehouse-account-data"></a>Mover os dados da conta do Armazém de Dados do Intune 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ao pedir para mover uma conta, está a pedir que o seu datacenter seja alterado para outra localização. Após a mudança, o Armazém de Dados irá repor e começar a gravar dados na nova localização com base no especificado no dia que começar a mudança. Para fazer uma cópia dos seus dados do Armazém de Dados anterior, conclua os seguintes passos **antes** de mover a conta. A maioria das tabelas do Armazém de Dados mantém os dados durante 30 dias, pelo que qualquer intervalo nos dados nestas tabelas deixará de estar disponível 30 dias depois de mover a conta. Para saber mais sobre os períodos de retenção de tabelas específicas, veja o [Modelo de dados do Armazém de Dados](reports-ref-data-model.md). 

## <a name="back-up-your-data-warehouse-data"></a>Criar uma cópia de segurança dos dados do Armazém de Dados 

Para fazer uma cópia de segurança dos seus dados do Armazém de Dados, tem de guardar os dados do Armazém de Dados num ficheiro *.csv* com a API do Armazém de Dados:  

1. Se estiver a utilizar a API do Armazém de Dados do Intune pela primeira vez, siga o processo único indicado no artigo [Obter dados a partir da API do Armazém de Dados do Intune com um cliente REST](reports-proc-data-rest.md).
2. Utilize o exemplo do PowerShell intitulado [Access the Intune Data Warehouse with PowerShell](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/PowerShell) (Aceder ao Armazém de Dados do Intune com o PowerShell) para transferir todos os seus dados para ficheiros CSV. 

## <a name="back-up-your-trend-charts-from-the-azure-portal"></a>Fazer uma cópia de segurança dos gráficos de tendências do portal do Azure

Alguns gráficos de tendências na vista do portal do Azure vão ser repostos. Pode fazer cópias de segurança destes gráficos ao executar o seguinte script no **Gráfico**:   

### <a name="terms--conditions-acceptance-reports"></a>Relatórios de Aceitação dos Termos e Condições
1. No portal do Azure, navegue para **Microsoft Intune** -> **Inscrição de Dispositivos** -> **Termos e Condições**.
2. Para cada item dos **Termos e Condições**, selecione **Relatório de Aceitação**, seguido de **Exportar**.
3. Guarde o relatório localmente.
 
### <a name="app-protection-reports"></a>Relatórios de Proteção de Aplicações  
1. No portal do Azure, navegue para **Microsoft Intune** -> **Aplicações do Cliente** -> **Estado da proteção de aplicações**.
2. Clique no ícone de transferência (⤓) para guardar cada relatório.

### <a name="device-configuration-charts"></a>Gráficos da Configuração do Dispositivo 
1. No portal do Azure, navegue para **Microsoft Intune** -> **DeviceConfiguration**.
2. Com a ferramenta [Testes de API do Graph ](https://developer.microsoft.com/graph/graph-explorer) da Microsoft, transfira os dados por trás dos gráficos. 
    - Para obter o estado de implementação de todos os perfis de configuração de todos os dispositivos, veja [Estado de implementação do dispositivo](https://graph.microsoft.com/beta/reports/deviceConfigurationDeviceActivity/content).

    - Para obter o estado de implementação de todos os perfis de configuração de dispositivos de todos os utilizadores, veja [Estado de implementação do utilizador](https://graph.microsoft.com/beta/reports/deviceConfigurationUserActivity/content).

    - Para obter o estado de implementação do perfil, veja [Disponibilizar o estado da implementação](https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations?$select=id,displayName,lastModifiedDateTime,deviceStatusOverview&$expand=deviceStatusOverview).
  
    > [!NOTE]
    > Tem de ter um token de autenticação válido para aceder às informações do estado de implementação e de configuração do dispositivo.

## <a name="device-enrollment-charts"></a>Gráficos de Inscrição de Dispositivos
1. No portal do Azure, navegue para **Microsoft Intune** -> **DeviceEnrollment**.
2. Com a ferramenta [Testes de API do Graph ](https://developer.microsoft.com/graph/graph-explorer) da Microsoft, transfira os dados por trás dos gráficos.
    - Para obter o estado de inscrição, copie esta [consulta do estado de inscrição](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentFailureTrends()/content) e cole-a na ferramenta [Testes de API do Graph](https://developer.microsoft.com/graph/graph-explorer).
    - Para obter as principais falhas de inscrição desta semana, copie esta [consulta do estado de inscrição](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentTopFailures(period=null)/content) e cole-a na ferramenta [Testes de API do Graph](https://developer.microsoft.com/graph/graph-explorer).

    > [!NOTE]
    > Tem de ter um token de autenticação válido para aceder aos dados de inscrição de dispositivos. 

## <a name="after-a-data-warehouse-account-move"></a>Após mover a conta do Armazém de Dados

Após mover a conta do Armazém de Dados, verá no Intune que o Armazém de Dados foi reposto e os dados estão agora armazenados na nova localização. Os gráficos e as opções de exportação serão repostos e verá uma notificação que, após clicar nela, o redirecionará para um artigo a explicar por que razão os gráficos foram repostos.  

## <a name="data-warehouse-move-example"></a>Exemplo de mudança do Armazém de Dados 

O cliente X pede que uma conta seja movida a 01/06/2018. Em resposta ao pedido, o cliente receberá uma ligação para ver documentação com detalhes sobre os passos a realizar se quiser fazer uma cópia de segurança do Armazém de Dados anterior. A 01/06/2018, o Armazém de Dados e os gráficos que suporta serão repostos e começarão a armazenar dados no novo datacenter. 

## <a name="next-steps"></a>Passos Seguintes

 - Saiba mais sobre [as novidades todas as semanas no Intune](whats-new.md). Também pode descobrir quais são as alterações futuras, os avisos importantes sobre o serviço e as informações sobre versões anteriores.
 - Leia o [Blogue do Microsoft Intune](https://go.microsoft.com/fwlink/?LinkID=273882).
