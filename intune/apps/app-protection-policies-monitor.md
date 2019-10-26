---
title: Como monitorizar políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Este tópico descreve como monitorar as políticas de proteção de aplicativo no Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 000b1d04dd3f520b55b1d33545a8803e23bf8965
ms.sourcegitcommit: 0d6f323152ec62f7d383891cce12ea0a4289cd8f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/24/2019
ms.locfileid: "72889582"
---
# <a name="how-to-monitor-app-protection-policies"></a>Como monitorizar políticas de proteção de aplicações
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Você pode monitorar o status de conformidade das políticas de MAM (gerenciamento de aplicativo móvel) que você aplicou aos usuários do painel de proteção de aplicativo do Intune na [portal do Azure](https://portal.azure.com). Além disso, você pode encontrar informações sobre os usuários afetados pelas políticas de MAM, o status de conformidade da política de MAM e quaisquer problemas que os usuários possam estar enfrentando.

Há três locais diferentes para monitorar as políticas de proteção de aplicativo:
- Vista de resumo
- Vista detalhada
- Vista de relatórios

> [!NOTE]
> Para obter mais informações, veja [Como criar e atribuir políticas de proteção de aplicações](app-protection-policies.md).

O período de retenção dos dados de proteção do aplicativo é de 90 dias. Todas as instâncias de aplicativo que fizeram check-in no serviço de MAM nos últimos 90 dias estão incluídas no relatório de status de proteção do aplicativo. Uma *instância de aplicativo* é um usuário único + aplicativo + dispositivo. 

## <a name="summary-view"></a>Vista de resumo

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. Para ver a exibição de resumo, na carga de trabalho **aplicativos cliente** , em **Monitor**, escolha **status de proteção do aplicativo**.

   ![Captura de tela do bloco Resumo no painel de gerenciamento de aplicativos móveis do Intune](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Usuários atribuídos**: o número total de usuários atribuídos em sua empresa que estão usando um aplicativo associado a uma política em um contexto de trabalho e são protegidos e licenciados, bem como os usuários atribuídos que são desprotegidos e não licenciados.
- **Usuários sinalizados**: o número de usuários que estão tendo problemas com seus dispositivos. Dispositivos com jailbreak (iOS) e com raiz (Android) são relatados sob **usuários sinalizados**. Além disso, os usuários com dispositivos sinalizados pela verificação de atestado de dispositivo do Google SafetyNet (se ativado pelo administrador de ti) são relatados aqui. 
- **Usuários com aplicativos potencialmente prejudiciais**: o número de usuários que podem ter um aplicativo prejudicial em seu dispositivo Android detectado pelo Google Play proteger. 
- **Status do usuário para IOS** e **status do usuário para Android**: o número de usuários que usaram um aplicativo que tem uma política atribuída a ele em um contexto de trabalho para a plataforma relacionada. Essas informações mostram o número de usuários gerenciados pela política, bem como o número de usuários que estão usando um aplicativo que não é direcionado por nenhuma política em um contexto de trabalho. Poderá considerar adicionar estes utilizadores à sua política.
- **Principais aplicativos Ios protegidos**: com base nos aplicativos Ios mais usados, essas informações mostram o número de aplicativos Ios protegidos e desprotegidos.
- **Principais aplicativos Android protegidos**: com base nos aplicativos Android mais usados, essas informações mostram o número de aplicativos Android protegidos e desprotegidos.
- **Principais aplicativos Ios configurados sem registro**: com base nos aplicativos Ios mais usados para dispositivos não registrados, essas informações mostram o número de aplicativos Ios configurados.
- **Principais aplicativos Android configurados sem registro**: com base nos aplicativos Android mais usados para dispositivos não registrados, essas informações mostram o número de aplicativos Android configurados.

    > [!NOTE]
    > Se tiver múltiplas políticas por plataforma, um utilizador só será considerado gerido por políticas quando lhe tiver sido atribuída pelo menos uma política.

## <a name="detailed-view"></a>Vista detalhada
Você pode acessar a exibição detalhada do resumo escolhendo o bloco status do **usuário** (baseado na plataforma do so do dispositivo), o bloco **usuários com aplicativos potencialmente prejudiciais** e os **usuários sinalizados** .

### <a name="user-status"></a>Estado de utilizador
Pode procurar um único utilizador e ver o estado de conformidade do mesmo. O painel **Relatório da aplicação** mostra as seguintes informações para um utilizador selecionado:
- **Ícone**: exibe se o status do aplicativo está atualizado.
- **Nome do aplicativo**: o nome do aplicativo.
- **Nome do dispositivo**: dispositivos que estão associados à conta do usuário.
- **Tipo de dispositivo**: o tipo de dispositivo ou sistema operacional que o dispositivo está executando.
- **Políticas**: as políticas associadas ao aplicativo.
- **Status**:
  - **Com entrada dada:** a política foi implementada no utilizador e a aplicação foi utilizada no contexto profissional pelo menos uma vez.
  - **Não verificado**: a política foi implantada para o usuário, mas o aplicativo não foi usado no contexto de trabalho desde então.
- **Última sincronização**: quando o aplicativo foi sincronizado pela última vez com o Intune. 

>[!NOTE]
> A **última** coluna de sincronização representa o mesmo valor no relatório de status do usuário no console e no relatório de política de proteção de aplicativo [exportável. csv](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities). A diferença é um pequeno atraso na sincronização entre o valor nos dois relatórios. 
>
> O tempo referenciado na última sincronização é quando o Intune viu a instância do aplicativo pela última vez. Quando um usuário inicia um aplicativo, ele pode notificar o serviço de Proteção de Aplicativo do Intune no tempo de inicialização, dependendo de quando ele fez o último check-in. Consulte [os tempos de intervalo de repetição para check-in de política de proteção de aplicativo](https://docs.microsoft.com/en-us/intune/app-protection-policy-delivery). Se um usuário não tiver usado esse aplicativo em particular no último intervalo de check-in (que geralmente é de 30 minutos para uso ativo) e iniciar o aplicativo, então:
>
> - O relatório da política de proteção de aplicativo exportável. csv tem a hora mais recente, dentro de 1 minuto (mínimo) a 30 minutos (máximo).
> - O relatório de status do usuário tem a hora mais recente instantaneamente.
>
> Por exemplo, considere um usuário de destino e licenciado que inicia um aplicativo protegido às 12:00 PM:
> - Se esta for uma entrada pela primeira vez, isso significa que o usuário foi desconectado antes e não tem um registro de instância de aplicativo com o Intune. Depois que o usuário entra, o usuário Obtém um novo registro de instância de aplicativo e pode ser verificado imediatamente (com os mesmos atrasos de tempo listados anteriormente para check-ins futuros). Assim, a hora da última sincronização é 12:00 PM no relatório de status do usuário e 12:01 PM (ou 12:30 PM no mais recente) no relatório de política de proteção de aplicativo. 
> - Se o usuário estiver apenas iniciando o aplicativo, a hora da última sincronização relatada dependerá da última vez em que o usuário fez o check-in.


Para ver o relatório para um utilizador, siga estes passos:

1. Para selecionar um usuário, escolha o bloco Resumo de **status do usuário** .

    ![Captura de tela do bloco Resumo do gerenciamento de aplicativos móveis do Intune](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. No painel **relatório do aplicativo** , escolha **Selecionar usuário** para procurar um usuário Azure Active Directory.

    ![Captura de tela da opção Selecionar usuário no painel relatórios do aplicativo](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. Selecione o utilizador na lista. Pode ver os detalhes do estado de conformidade do utilizador.

>[!NOTE]
> Se os utilizadores que procurou não tiverem a política de MAM implementada, verá uma mensagem a informar que não existem políticas de MAM que abranjam esses utilizadores.

### <a name="flagged-users"></a>Utilizadores sinalizados
A vista detalhada mostra a mensagem de erro, a aplicação que foi acedida quando ocorreu o erro, a plataforma de SO do dispositivo afetado e um carimbo de data/hora. Normalmente, o erro é para dispositivos desbloqueados (iOS) ou com raiz (Android). Além disso, os usuários com dispositivos sinalizados pela verificação de inicialização condicional ' atestado de dispositivo SafetyNet ' são relatados aqui com o motivo conforme relatado pelo Google. Para que um usuário seja removido do relatório, o status do próprio dispositivo precisa ser alterado, o que ocorre após a próxima verificação de detecção de raiz (ou verificação de jailbreak/SafetyNet ocorre) que precisa relatar um resultado positivo. Se o dispositivo for realmente corrigido, a atualização do relatório de usuários sinalizados ocorrerá quando a lâmina for recarregada.

### <a name="users-with-potentially-harmful-apps"></a>Usuários com aplicativos potencialmente prejudiciais
A exibição detalhada mostra:

- O usuário.
- A ID do pacote do aplicativo.
- Se o aplicativo estiver habilitado para MAM.
- A categoria de ameaça.
- O email.
- O nome do dispositivo.
- Um carimbo de data/hora.

Os usuários com dispositivos sinalizados pela verificação **exigir a verificação de ameaça na inicialização condicional de aplicativos** são relatados aqui, com a categoria ameaça, conforme relatado pelo Google. Se houver aplicativos listados neste relatório que estão sendo implantados por meio do Intune, contate o desenvolvedor do aplicativo para o aplicativo ou remova o aplicativo de ser atribuído aos seus usuários. 

## <a name="reporting-view"></a>Vista de relatórios

Você pode encontrar os mesmos relatórios na parte superior da folha **status de proteção do aplicativo** .

> [!NOTE]
> O Intune fornece campos de relatório de dispositivo adicionais, incluindo ID de registro do aplicativo, fabricante do Android, modelo e versão do patch de segurança, bem como o modelo do iOS. No Intune, você acessa esses campos selecionando **aplicativos cliente** > **status de proteção de aplicativo** > **relatório de proteção de aplicativo: Ios, Android**. Além disso, esses parâmetros ajudam a configurar a lista de **permissões** para o fabricante do dispositivo (Android), a lista de **permissões** para o modelo de dispositivo (Android e Ios) e a configuração de versão mínima do patch de segurança do Android. 

Relatórios adicionais estão disponíveis para ajudá-lo com o status de conformidade da política de MAM. Para exibir esses relatórios, selecione **aplicativos cliente** > **relatórios** **status de proteção de aplicativo** > . 

A folha **relatórios** fornece vários relatórios com base no usuário e no aplicativo, incluindo o seguinte:

- **Relatório do usuário**: este relatório descreve as mesmas informações que podem ser encontradas no relatório de **status do usuário** , na seção [exibição detalhada](app-protection-policies-monitor.md#detailed-view) acima.

- **Relatório do aplicativo**: além de selecionar a plataforma e o aplicativo, este relatório fornece dois status de proteção de aplicativo diferentes que você pode selecionar antes de gerar o relatório. Os status podem ser **protegidos** ou **desprotegidos**.

  - Status do usuário para a atividade de MAM gerenciada (**protegida**): este relatório descreve a atividade de cada aplicativo de Mam gerenciado, por usuário. Ele mostra todos os aplicativos direcionados pelas políticas de MAM para cada usuário e o status de cada aplicativo como check-in com políticas de MAM. O relatório também inclui o status de cada aplicativo que foi direcionado com uma política de MAM, mas nunca foi feito check-in.
  - Status do usuário para atividade de MAM não gerenciada (**desprotegido**): este relatório descreve a atividade de aplicativos habilitados para MAM que atualmente não são gerenciados por usuário. Isso pode acontecer porque:
    - Esses aplicativos estão sendo usados por um usuário ou um aplicativo que atualmente não é direcionado por uma política de MAM.
    - Todas as aplicações estão registadas, mas não estão a receber políticas de MAM.

    ![Captura de tela da folha de relatórios de aplicativo de um usuário, com detalhes para três aplicativos](./media/app-protection-policies-monitor/MAM-reporting-4.png)

- **Relatório de configuração do usuário**: com base em um usuário selecionado, este relatório fornece detalhes sobre as configurações de aplicativo que o usuário recebeu.
- **Relatório de configuração de aplicativo**: base na plataforma e aplicativo selecionados, este relatório fornece detalhes sobre quais usuários receberam configurações para o aplicativo selecionado.
- **Relatório de aprendizado de aplicativos para proteção de informações do Windows**: este relatório mostra quais aplicativos estão tentando cruzar limites de política.
- **Aprendizado de site da proteção de informações do Windows**: este relatório mostra quais sites estão tentando cruzar limites de política.

## <a name="table-grouping"></a>Agrupamento de tabelas

Depois que os dados do **relatório do usuário de proteção do aplicativo** são mostrados, você pode agregar dados pelo seguinte:

- **Resultado da validação**: os dados são agrupados pelo status de proteção do aplicativo, que pode ser "falha", "aviso" ou "êxito".
- **Nome do aplicativo**: os dados são agrupados pelo nome real do aplicativo. Novamente, o status pode ser "falha", "aviso" ou "êxito".

## <a name="export-app-protection-activities"></a>Exportar atividades de proteção do aplicativo

Pode exportar todas as atividades de políticas de proteção de aplicações para um ficheiro .csv único. Esta funcionalidade pode ser útil para analisar todos os estados de proteção de aplicações comunicados pelos utilizadores.

Siga estas etapas para gerar o relatório de proteção do aplicativo:

1. No painel de gestão de aplicações móveis do Intune, selecione **Relatório de proteção de aplicações**.

    ![Captura de tela do link de download da proteção de aplicativo](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Escolha **Sim** para salvar o relatório e, em seguida, escolha **salvar como**. Selecione a pasta na qual você deseja salvar o relatório.

    ![Captura de ecrã da caixa de confirmação Guardar relatório](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)

## <a name="see-also"></a>Consulte também
- [Gerir a transferência de dados entre aplicações iOS](data-transfer-between-apps-manage-ios.md)
- [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-android.md)
- [O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-ios.md)
