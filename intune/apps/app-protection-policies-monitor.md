---
title: Como monitorizar políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Este tópico descreve como monitorar as políticas de proteção de aplicativo no Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/13/2019
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
ms.openlocfilehash: 36a84296aabd2d78cbc3cdc14ffb8f696afa5c22
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75205263"
---
# <a name="how-to-monitor-app-protection-policies"></a>Como monitorizar políticas de proteção de aplicações
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Você pode monitorar o status das políticas de proteção de aplicativo que você aplicou aos usuários do painel proteção de aplicativo do Intune na [portal do Azure](https://portal.azure.com). Além disso, você pode encontrar informações sobre os usuários afetados pelas políticas de proteção de aplicativo, o status de conformidade da política e quaisquer problemas que seus usuários possam estar enfrentando.

Há três locais diferentes para monitorar as políticas de proteção de aplicativo:
- Vista de resumo
- Vista detalhada
- Vista de relatórios

O período de retenção dos dados de proteção do aplicativo é de 90 dias. Todas as instâncias de aplicativo que fizeram check-in no serviço do Intune nos últimos 90 dias estão incluídas no relatório de status de proteção do aplicativo. Uma *instância de aplicativo* é um usuário único + aplicativo + dispositivo. 

> [!NOTE]
> Para obter mais informações, veja [Como criar e atribuir políticas de proteção de aplicações](app-protection-policies.md).

## <a name="summary-view"></a>Vista de resumo

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **aplicativos** > **monitorar** > **status de proteção do aplicativo**.

   ![Captura de tela do bloco Resumo no painel de gerenciamento de aplicativos móveis do Intune](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Usuários atribuídos**: o número total de usuários atribuídos em sua empresa que estão usando um aplicativo associado a uma política em um contexto de trabalho e são protegidos e licenciados, bem como os usuários atribuídos que são desprotegidos e não licenciados.
- **Usuários sinalizados**: o número de usuários que estão tendo problemas com seus dispositivos. Dispositivos com jailbreak (iOS) e com raiz (Android) são relatados sob **usuários sinalizados**. Além disso, os usuários com dispositivos sinalizados pela verificação de atestado de dispositivo do Google SafetyNet (se ativado pelo administrador de ti) são relatados aqui. 
- **Usuários com aplicativos potencialmente prejudiciais**: o número de usuários que podem ter um aplicativo prejudicial em seu dispositivo Android detectado pelo Google Play proteger. 
- **Status do usuário para IOS** e **status do usuário para Android**: o número de usuários que usaram um aplicativo que tem uma política atribuída a ele em um contexto de trabalho para a plataforma relacionada. Essas informações mostram o número de usuários gerenciados pela política, bem como o número de usuários que estão usando um aplicativo que não é direcionado por nenhuma política em um contexto de trabalho. Poderá considerar adicionar estes utilizadores à sua política.
- **Aplicativos Ios protegidos** e **principais aplicativos Android**protegidos: com base nos aplicativos Ios e Android mais usados, essas informações mostram o número de aplicativos protegidos e desprotegidos por plataforma.
- **Principais aplicativos Ios configurados sem registro** e **aplicativos Android configurados principais sem registro**: com base nos aplicativos Ios e Android mais usados para dispositivos não registrados, essas informações mostram o número de aplicativos configurados por plataforma (como no, usando uma política de configuração de aplicativo).

    > [!NOTE]
    > Se tiver múltiplas políticas por plataforma, um utilizador só será considerado gerido por políticas quando lhe tiver sido atribuída pelo menos uma política.

## <a name="detailed-view"></a>Vista detalhada
Você pode acessar a exibição detalhada do resumo escolhendo o bloco **usuários sinalizados** e o bloco **usuários com aplicativos potencialmente prejudiciais** .

### <a name="flagged-users"></a>Utilizadores sinalizados
A vista detalhada mostra a mensagem de erro, a aplicação que foi acedida quando ocorreu o erro, a plataforma de SO do dispositivo afetado e um carimbo de data/hora. Normalmente, o erro é para dispositivos desbloqueados (iOS) ou com raiz (Android). Além disso, os usuários com dispositivos sinalizados pela verificação de inicialização condicional ' atestado de dispositivo SafetyNet ' são relatados aqui com o motivo conforme relatado pelo Google. Para que um usuário seja removido do relatório, o status do próprio dispositivo precisa ser alterado, o que ocorre após a próxima verificação de detecção de raiz (ou verificação de jailbreak/SafetyNet ocorre) que precisa relatar um resultado positivo. Se o dispositivo for realmente corrigido, a atualização no relatório de usuários sinalizados ocorrerá quando o painel for recarregado.

### <a name="users-with-potentially-harmful-apps"></a>Usuários com aplicativos potencialmente prejudiciais
Os usuários com dispositivos sinalizados pela verificação **exigir a verificação de ameaça na inicialização condicional de aplicativos** são relatados aqui, com a categoria ameaça, conforme relatado pelo Google. Se houver aplicativos listados neste relatório que estão sendo implantados por meio do Intune, contate o desenvolvedor do aplicativo para o aplicativo ou remova o aplicativo de ser atribuído aos seus usuários. A exibição detalhada mostra:

- **Usuário**: o nome do usuário.
- **ID do pacote do aplicativo**: essa é a maneira como o sistema operacional Android determina exclusivamente um aplicativo.
- **Se o aplicativo estiver habilitado para Mam**: se o aplicativo está sendo implantado por meio de Microsoft Intune. 
- A **categoria de ameaça**: a categoria de ameaças determinada pelo Google ao qual este aplicativo se enquadra. 
- **Email**: o email do usuário.
- **Nome do dispositivo**: nomes de qualquer dispositivo que esteja associado à conta do usuário.
- **Um carimbo de hora**: esta é a data da última sincronização que o Google fez com Microsoft Intune em relação a aplicativos potencialmente prejudiciais.

## <a name="reporting-view"></a>Vista de relatórios

Você pode encontrar os mesmos relatórios na parte superior do painel **status de proteção do aplicativo** . Para exibir esses relatórios, selecione **aplicativos** > **status de proteção de aplicativo** > **relatórios**. O painel **relatórios** fornece vários relatórios com base no usuário e no aplicativo, incluindo o seguinte:

### <a name="user-report"></a>Relatório do usuário
Pode procurar um único utilizador e ver o estado de conformidade do mesmo. O painel **Relatório da aplicação** mostra as seguintes informações para um utilizador selecionado:
- **Ícone**: exibe se o status do aplicativo está atualizado.
- **Nome do aplicativo**: o nome do aplicativo.
- **Nome do dispositivo**: dispositivos que estão associados à conta do usuário.
- **Tipo de dispositivo**: o tipo de dispositivo ou sistema operacional que o dispositivo está executando.
- **Políticas**: as políticas associadas ao aplicativo.
- **Estado**:
  - **Com entrada dada:** a política foi implementada no utilizador e a aplicação foi utilizada no contexto profissional pelo menos uma vez.
  - **Não verificado**: a política foi implantada para o usuário, mas o aplicativo não foi usado no contexto de trabalho desde então.
- **Última sincronização**: quando o aplicativo foi sincronizado pela última vez com o Intune. 

>[!NOTE]
> A **última** coluna de sincronização representa o mesmo valor no relatório de status do usuário no console e no relatório de política de proteção de aplicativo [exportável. csv](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities). A diferença é um pequeno atraso na sincronização entre o valor nos dois relatórios. 
>
> O tempo referenciado na última sincronização é quando o Intune viu a instância do aplicativo pela última vez. Quando um usuário inicia um aplicativo, ele pode notificar o serviço de Proteção de Aplicativo do Intune no tempo de inicialização, dependendo de quando ele fez o último check-in. Consulte [os tempos de intervalo de repetição para check-in de política de proteção de aplicativo](~/apps/app-protection-policy-delivery.md). Se um usuário não tiver usado esse aplicativo em particular no último intervalo de check-in (que geralmente é de 30 minutos para uso ativo) e iniciar o aplicativo, então:
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

### <a name="app-report"></a>Relatório do aplicativo
Você pode pesquisar por plataforma e aplicativo e, em seguida, esse relatório fornecerá dois status de proteção de aplicativo diferentes que você pode selecionar antes de gerar o relatório. Os status podem ser **protegidos** ou **desprotegidos**.

  - Status do usuário para a atividade de MAM gerenciada (**protegida**): este relatório descreve a atividade de cada aplicativo de Mam gerenciado, por usuário. Ele mostra todos os aplicativos direcionados pelas políticas de MAM para cada usuário e o status de cada aplicativo como check-in com políticas de MAM. O relatório também inclui o status de cada aplicativo que foi direcionado com uma política de MAM, mas nunca foi feito check-in.
  - Status do usuário para atividade de MAM não gerenciada (**desprotegido**): este relatório descreve a atividade de aplicativos habilitados para MAM que atualmente não são gerenciados por usuário. Isso pode acontecer porque:
    - Esses aplicativos estão sendo usados por um usuário ou um aplicativo que atualmente não é direcionado por uma política de MAM.
    - Todas as aplicações estão registadas, mas não estão a receber políticas de MAM.

    ![Captura de tela do painel relatórios do aplicativo de um usuário, com detalhes para três aplicativos](./media/app-protection-policies-monitor/MAM-reporting-4.png)

### <a name="user-configuration-report"></a>**Relatório de configuração do usuário**
Com base em um usuário selecionado, este relatório fornece detalhes sobre as configurações de aplicativo que o usuário recebeu.

### <a name="app-configuration-report"></a>**Relatório de configuração de aplicativo**
Com base na plataforma e no aplicativo selecionados, este relatório fornece detalhes sobre quais usuários receberam configurações para o aplicativo selecionado.

### <a name="app-learning-report-for-windows-information-protection"></a>Relatório de aprendizado de aplicativos para a proteção de informações do Windows
Este relatório mostra quais aplicativos estão tentando cruzar limites de política.

### <a name="website-learning-for-windows-information-protection"></a>Aprendizado de site da proteção de informações do Windows
Este relatório mostra quais sites estão tentando cruzar limites de política.

## <a name="export-app-protection-activities"></a>Exportar atividades de proteção do aplicativo
Pode exportar todas as atividades de políticas de proteção de aplicações para um ficheiro .csv único. Esta funcionalidade pode ser útil para analisar todos os estados de proteção de aplicações comunicados pelos utilizadores. O **arquivo. csv de proteção do aplicativo mostra**:
- **Usuário**: o nome do usuário.
- **Email**: o email do usuário.
- **Aplicativo**: o nome do aplicativo.
- **Versão do aplicativo**: a versão do aplicativo.
- **Nome do dispositivo**: nomes de qualquer dispositivo que esteja associado à conta do usuário.
- **Fabricante do dispositivo**: lista o fabricante do dispositivo (somente Android). 
- **Modelo de dispositivo**: lista o fabricante do dispositivo (somente Android). 
- **Versão do patch do Android**: a data do último patch de segurança do Android.
- **ID do dispositivo do AAD**: esta coluna será populada se o dispositivo for ingressado no AAD.
- **ID do dispositivo MDM**: esta coluna será preenchida se o dispositivo for registrado Microsoft Intune MDM.
- **Plataforma**: o sistema operacional.
- **Versão da plataforma**: a versão do sistema operacional.
- **Tipo de gerenciamento**: tipo de gerenciamento no dispositivo. Por exemplo, Android Enterprise, não gerenciado ou MDM.  
- **Status de proteção do aplicativo**: desprotegido ou protegido.
- **Política**: as políticas de proteção de aplicativo associadas ao aplicativo.
- **Última sincronização**: quando o aplicativo foi sincronizado pela última vez com Microsoft Intune. 
- **Estado de conformidade**: se o aplicativo no dispositivo do usuário está em conformidade com as políticas de acesso condicional com base no aplicativo.  

Siga estas etapas para gerar arquivo. csv de proteção do aplicativo ou arquivo. csv de configuração de aplicativo:

1. No painel de gestão de aplicações móveis do Intune, selecione **Relatório de proteção de aplicações**.

    ![Captura de tela do link de download da proteção de aplicativo](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Escolha **Sim** para salvar o relatório e, em seguida, escolha **salvar como**. Selecione a pasta na qual você deseja salvar o relatório.

    ![Captura de ecrã da caixa de confirmação Guardar relatório](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)
   
> [!NOTE]
> O Intune fornece campos de relatório de dispositivo adicionais, incluindo ID de registro do aplicativo, fabricante do Android, modelo e versão do patch de segurança, bem como o modelo do iOS. No Intune, você acessa esses campos selecionando **aplicativos** > **status de proteção do aplicativo** > **relatório de proteção do aplicativo: Ios, Android**. Além disso, esses parâmetros ajudam a configurar a lista de **permissões** para o fabricante do dispositivo (Android), a lista de **permissões** para o modelo de dispositivo (Android e Ios) e a configuração de **versão mínima do patch de segurança do Android** .   
 
## <a name="see-also"></a>Consulte também
- [Gerir a transferência de dados entre aplicações iOS](data-transfer-between-apps-manage-ios.md)
- [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-android.md)
- [O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-ios.md)
