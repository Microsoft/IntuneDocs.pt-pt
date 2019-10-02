---
title: Como monitorizar políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Este tópico descreve como monitorar o status de conformidade das políticas de gerenciamento de aplicativo móvel no Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fad554ace3b7c8c279161f149bc06854dfaca93d
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731368"
---
# <a name="how-to-monitor-app-protection-policies"></a>Como monitorizar políticas de proteção de aplicações
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Você pode monitorar o status de conformidade das políticas de MAM (gerenciamento de aplicativo móvel) que você aplicou aos usuários do painel de proteção de aplicativo do Intune na [portal do Azure](https://portal.azure.com). Além disso, você pode encontrar informações sobre os usuários afetados pelas políticas de MAM, o status de conformidade da política de MAM e quaisquer problemas que os usuários possam estar enfrentando.

Há três locais diferentes para monitorar o status de conformidade das políticas de MAM:
- Vista de resumo
- Vista detalhada
- Vista de relatórios

> [!NOTE]
> Para obter informações sobre como criar políticas de proteção de aplicações, veja [Como criar e atribuir políticas de proteção de aplicações](app-protection-policies.md).

O período de retenção dos dados de proteção do aplicativo é de 90 dias. Todas as instâncias de aplicativo que fizeram check-in no serviço de MAM nos últimos 90 dias serão incluídas no relatório de status de proteção do aplicativo. Uma instância de aplicativo é um usuário único + aplicativo + dispositivo. 

## <a name="summary-view"></a>Vista de resumo

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. Na carga de trabalho **aplicativos cliente** , escolha **status de proteção de aplicativo** na seção **Monitor** para ver a exibição de Resumo:

![Mosaico de resumo no painel de gestão de aplicações móveis do Intune](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Usuários atribuídos**: O número total de usuários atribuídos em sua empresa que estão usando um aplicativo associado a uma política em um contexto de trabalho e são protegidos e licenciados, bem como os usuários atribuídos que são desprotegidos e não licenciados.
- **Usuários sinalizados**: O número de usuários que estão enfrentando problemas. Dispositivos com jailbreak (iOS) e com raiz (Android) são relatados sob **usuários sinalizados**. Os usuários com dispositivos sinalizados pela verificação de atestado de dispositivo do Google SafetyNet (se ativado pelo administrador de ti) são relatados aqui. 
- **Usuários com aplicativos potencialmente prejudiciais**: O número de usuários que podem ter um aplicativo prejudicial em seu dispositivo Android detectado pelo Google Play proteger. 
- **Status do usuário para IOS** e **status do usuário para Android**: O número de usuários que usaram um aplicativo que tem uma política atribuída a ele em um contexto de trabalho para a plataforma relacionada. Essas informações mostram o número de usuários gerenciados pela política, bem como o número de usuários que estão usando um aplicativo que não é direcionado por nenhuma política em um contexto de trabalho. Poderá considerar adicionar estes utilizadores à sua política.
- **Principais aplicativos do IOS protegidos**: Com base nos aplicativos iOS mais usados, essas informações mostram o número de aplicativos iOS protegidos e desprotegidos.
- **Principais aplicativos Android protegidos**: Com base nos aplicativos Android mais usados, essas informações mostram o número de aplicativos Android protegidos e desprotegidos.
- **Principais aplicativos Ios configurados sem registro**: Com base nos aplicativos iOS mais usados para dispositivos não registrados, essas informações mostram o número de aplicativos iOS configurados.
- **Principais aplicativos Android configurados sem registro**: Com base nos aplicativos Android mais usados para dispositivos não registrados, essas informações mostram o número de aplicativos Android configurados.

    > [!NOTE]
    > Se você tiver várias políticas por plataforma, um usuário será considerado gerenciado pela política quando tiver pelo menos uma política atribuída a eles.

## <a name="detailed-view"></a>Vista detalhada
Você pode acessar a exibição detalhada do resumo escolhendo o bloco status do **usuário** (com base na plataforma do sistema operacional), os **usuários com aplicativos potencialmente prejudiciais** e o bloco **usuários sinalizados** .

### <a name="user-status"></a>Estado de utilizador
Pode procurar um único utilizador e ver o estado de conformidade do mesmo. O painel **Relatório da aplicação** mostra as seguintes informações para um utilizador selecionado:
- **Ícone**: Exibe se o status do aplicativo está atualizado.
- **Nome do aplicativo**: O nome do aplicativo.
- **Nome do dispositivo**: Dispositivos que estão associados à conta do usuário.
- **Tipo de dispositivo**: O tipo de dispositivo ou sistema operacional que o dispositivo está executando.
- **Políticas**: As políticas associadas ao aplicativo.
- **Status**:
  - **Check-in**: A política foi implantada para o usuário e o aplicativo foi usado no contexto de trabalho pelo menos uma vez.
  - **Não verificado**: A política foi implantada para o usuário, mas o aplicativo não foi usado no contexto de trabalho desde então.
- **Última sincronização**: Quando o dispositivo foi sincronizado pela última vez.

>[!NOTE]
> Se os utilizadores que procurou não tiverem a política de MAM implementada, verá uma mensagem a informar que não existem políticas de MAM que abranjam esses utilizadores.

Para ver o relatório para um utilizador, siga estes passos:

1. Para selecionar um usuário, escolha o bloco Resumo de **status do usuário** .

    ![Captura de tela do bloco Resumo do gerenciamento de aplicativos móveis do Intune](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. No painel **Relatório da aplicação** que abrir, selecione **Selecionar utilizador** para procurar um utilizador do Azure Active Directory.

    ![Captura de tela da opção Selecionar usuário no painel relatórios do aplicativo](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. Selecione o utilizador na lista. Pode ver os detalhes do estado de conformidade do utilizador.

### <a name="flagged-users"></a>Utilizadores sinalizados
A vista detalhada mostra a mensagem de erro, a aplicação que foi acedida quando ocorreu o erro, a plataforma de SO do dispositivo afetado e um carimbo de data/hora. Os usuários com dispositivos sinalizados pela verificação de inicialização condicional ' atestado de dispositivo SafetyNet ' são relatados aqui com o motivo conforme relatado pelo Google.

### <a name="users-with-potentially-harmful-apps"></a>Usuários com aplicativos potencialmente prejudiciais
A exibição detalhada mostra o usuário, a ID do pacote do aplicativo, se o aplicativo estiver habilitado para MAM, categoria de ameaça, email, nome do dispositivo e um carimbo de data/hora. Os usuários com dispositivos sinalizados por ' exigir verificação de ameaças na verificação de inicialização do Bloquear de aplicativos ' são relatados aqui com a categoria de ameaça conforme relatado pelo Google. Se houver aplicativos listados neste relatório que estão sendo implantados por meio do Intune, contate o desenvolvedor do aplicativo para o aplicativo e/ou remova o aplicativo de ser atribuído aos usuários finais. 

## <a name="reporting-view"></a>Vista de relatórios

Você pode encontrar os mesmos relatórios na parte superior da folha **status de proteção do aplicativo** .

> [!NOTE]
> O Intune fornece campos de relatório de dispositivo adicionais, incluindo ID de registro do aplicativo, fabricante do Android, modelo e versão do patch de segurança, bem como o modelo do iOS. No Intune, esses campos estão disponíveis selecionando **aplicativos** > cliente**status de proteção do aplicativo** e escolhendo **relatório de proteção do aplicativo: Ios, Android**. Além disso, esses parâmetros irão ajudá-lo a configurar o **permitir** lista para o fabricante do dispositivo (Android), o **permitir** lista para o modelo do dispositivo (Android e iOS) e o patch de segurança mínima para Android definição de versão. 

Relatórios adicionais estão disponíveis para ajudá-lo com o status de conformidade da política de MAM. Para exibir esses relatórios, selecione **aplicativos** > cliente**relatórios**de**status** > de proteção do aplicativo. 

A folha **relatórios** fornece vários relatórios com base no usuário e no aplicativo, incluindo o seguinte:


- **Relatório do usuário**: Este relatório descreve as mesmas informações que você pode encontrar no relatório de **status do usuário** , na seção [exibição detalhada](app-protection-policies-monitor.md#detailed-view) acima.

- **Relatório do aplicativo**: Além de selecionar a plataforma e o aplicativo, este relatório fornece dois status de proteção de aplicativo diferentes que você pode selecionar antes de gerar o relatório. Os status podem ser **protegidos** ou **desprotegidos**.

  - Status do usuário para a atividade de MAM gerenciada (**protegida**): Este relatório descreve a atividade de cada aplicativo de MAM gerenciado, por usuário. Mostra todas as aplicações visadas pelas políticas de MAM para cada utilizador e uma discriminação do estado de cada aplicação como registada com políticas de MAM ou como visada por uma política de MAM, mas nunca registada.
  - Status do usuário para atividade de MAM não gerenciada (**desprotegido**): Este relatório descreve a atividade de aplicativos habilitados para MAM que atualmente não são gerenciados, por usuário. Isto pode acontecer pelos seguintes motivos:
    - Estas aplicações estão a ser utilizadas por um utilizador ou por uma aplicação que não seja atualmente visada por uma política de MAM.
    - Todas as aplicações estão registadas, mas não estão a receber políticas de MAM.

    ![Captura de tela da folha de relatórios de aplicativo de um usuário com detalhes para três aplicativos](./media/app-protection-policies-monitor/MAM-reporting-4.png)

- **Relatório de configuração do usuário**: Com base em um usuário selecionado, este relatório fornece detalhes sobre as configurações de aplicativo que o usuário recebeu.
- **Relatório de configuração de aplicativo**: Base na plataforma e aplicativo selecionados, este relatório fornece detalhes sobre quais usuários receberam configurações para o aplicativo selecionado.
- **Relatório de aprendizado de aplicativos para a proteção de informações do Windows**: Este relatório mostra quais aplicativos estão tentando cruzar limites de política.
- **Aprendizado de site da proteção de informações do Windows**: Este relatório mostra quais sites estão tentando cruzar limites de política.

## <a name="table-grouping"></a>Agrupamento de tabelas

Depois que os dados de **relatório do usuário de proteção do aplicativo** são exibidos, você pode agregar dados pelo seguinte:

- **Resultado da validação:** Os dados são mostrados agrupados por status de proteção de aplicativo, que pode ser falha, aviso ou êxito.
- **Nome do aplicativo:** Os dados são mostrados agrupados por aplicativos (o nome real do aplicativo) com falha, aviso ou êxito.

## <a name="export-app-protection-activities-to-csv"></a>Exportar atividades de proteção de aplicações para CSV

Você pode exportar todas as suas atividades de política de proteção de aplicativo para um único arquivo *. csv* . Esta funcionalidade pode ser útil para analisar todos os estados de proteção de aplicações comunicados pelos utilizadores.

Siga estes passos para gerar o Relatório de proteção de aplicações:

1. No painel de gestão de aplicações móveis do Intune, selecione **Relatório de proteção de aplicações**.

    ![Captura de tela do link de download da proteção de aplicativo](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Escolha **Sim** para salvar o relatório, escolha **salvar como** e selecione a pasta na qual deseja salvar o relatório.

    ![Captura de ecrã da caixa de confirmação Guardar relatório](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)

## <a name="see-also"></a>Consulte também
- [Gerir a transferência de dados entre aplicações iOS](data-transfer-between-apps-manage-ios.md)
- [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-android.md)
- [O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-ios.md)
