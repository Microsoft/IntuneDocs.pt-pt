---
title: Como monitorizar políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Este tópico descreve como monitorizar as políticas de proteção de aplicações em Intune.
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
ms.openlocfilehash: 5d2902c876fab12c1ba1e45783327f1ea08ab4d8
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414666"
---
# <a name="how-to-monitor-app-protection-policies"></a>Como monitorizar políticas de proteção de aplicações
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Pode monitorizar o estado das políticas de proteção de aplicações que aplicou aos utilizadores a partir do painel de proteção de aplicações Intune no [portal Azure](https://portal.azure.com). Além disso, pode encontrar informações sobre os utilizadores afetados pelas políticas de proteção de aplicações, estado de conformidade com a política e quaisquer problemas que os seus utilizadores possam estar a ter.

Existem três locais diferentes para monitorizar as políticas de proteção de aplicações:
- Vista de resumo
- Vista detalhada
- Vista de relatórios

O período de retenção para dados de proteção de aplicações é de 90 dias. Quaisquer casos de aplicações que tenham feito o check-in no serviço Intune nos últimos 90 dias estão incluídos no relatório de estado de proteção de aplicações. Uma *instância de aplicação* é um dispositivo único para utilizadores + app +. 

> [!NOTE]
> Para obter mais informações, veja [Como criar e atribuir políticas de proteção de aplicações](app-protection-policies.md).

## <a name="summary-view"></a>Vista de resumo

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **Apps** > **monitor** > estado de proteção da **aplicação**.

   ![Screenshot do azulejo resumo no painel de gestão de aplicações móveis Intune](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Utilizadores atribuídos**: O número total de utilizadores atribuídos na sua empresa que estão a usar uma app que está associada a uma política num contexto de trabalho e que estão protegidos e licenciados, bem como os utilizadores designados que estão desprotegidos e não licenciados.
- **Utilizadores sinalizados**: O número de utilizadores que estão a ter problemas com os seus dispositivos. Os dispositivos Jailbroken (iOS) e enraizados (Android) são reportados sob **utilizadores sinalizados.** Além disso, os utilizadores com dispositivos sinalizados pela verificação de atestado do dispositivo Google SafetyNet (se ligados pelo administrador de TI) são reportados aqui. 
- **Utilizadores com aplicações potencialmente nocivas**: O número de utilizadores que podem ter uma aplicação prejudicial no seu dispositivo Android detetada pelo Google Play Protect. 
- **Estado do utilizador para o iOS** e estatuto de **utilizador para Android**: O número de utilizadores que utilizaram uma aplicação que tenha uma política que lhes foi atribuída num contexto de trabalho para a plataforma relacionada. Estas informações mostram o número de utilizadores geridos pela apólice, bem como o número de utilizadores que estão a utilizar uma app que não é alvo de qualquer política num contexto de trabalho. Poderá considerar adicionar estes utilizadores à sua política.
- **Aplicações top protected iOS/iPadOS** e **aplicações para Android protegidas :** Com base nas aplicações iOS/iPadOS e Android mais utilizadas, esta informação mostra o número de aplicações protegidas e desprotegidas por plataforma.
- **As principais aplicações configuradas para iOS/iPadOS sem matrícula** e **as principais aplicações para Android Configuradas sem matrícula**: Com base nas aplicações iOS/iPadOS e Android mais utilizadas para dispositivos não matriculados, esta informação mostra o número de aplicações configuradas por plataforma (como em, utilizando uma política de configuração de apps).

    > [!NOTE]
    > Se tiver múltiplas políticas por plataforma, um utilizador só será considerado gerido por políticas quando lhe tiver sido atribuída pelo menos uma política.

## <a name="detailed-view"></a>Vista detalhada
Pode obter a visão detalhada do resumo, escolhendo o azulejo dos **utilizadores sinalizados,** e os **Utilizadores com azulejos de aplicações potencialmente prejudiciais.**

### <a name="flagged-users"></a>Utilizadores sinalizados
A vista detalhada mostra a mensagem de erro, a aplicação que foi acedida quando ocorreu o erro, a plataforma de SO do dispositivo afetado e um carimbo de data/hora. O erro é tipicamente para dispositivos de jailbroken (iOS) ou enraizados (Android). Além disso, os utilizadores com dispositivos sinalizados pela verificação de lançamento condicional do dispositivo 'SafetyNet' são reportados aqui com a razão, conforme relatado pela Google. Para que um utilizador seja removido do relatório, o estado do próprio dispositivo tem de ter mudado, o que acontece após a próxima verificação de deteção de raízes (ou verificação de jailbreak/verificação safetyNet) que precisa de reportar um resultado positivo. Se o dispositivo for verdadeiramente remediado, a atualização do relatório Utilizadores Sinalizados acontecerá quando o painel for recarregado.

### <a name="users-with-potentially-harmful-apps"></a>Utilizadores com aplicações potencialmente nocivas
Os utilizadores com dispositivos sinalizados pela verificação de **ameaças Desmedida em aplicações** de verificação de lançamento condicional são reportados aqui, com a categoria de ameaça como relatado pela Google. Se houver aplicações listadas neste relatório que estão a ser implementadas através do Intune, contacte o desenvolvedor da aplicação para a aplicação ou remova a aplicação de ser atribuída aos seus utilizadores. A opinião detalhada mostra:

- **Utilizador**: O nome do utilizador.
- Id do pacote de **aplicativos**: É assim que o Sistema Operativo Android determina de forma única uma aplicação.
- **Se a aplicação estiver ativada por MAM**: Se a aplicação está ou não a ser implementada através do Microsoft Intune. 
- A **categoria de ameaça**: Em que categoria de ameaça determinada pelo Google esta aplicação se insere. 
- **E-mail**: O e-mail do utilizador.
- **Nome**do dispositivo : Nomes de quaisquer dispositivos associados à conta do utilizador.
- **Um carimbo**de tempo : Esta é a data da última sincronização que a Google fez com a Microsoft Intune em relação a aplicações potencialmente nocivas.

## <a name="reporting-view"></a>Vista de relatórios

Pode encontrar os mesmos relatórios no topo do painel de proteção da **App.** Para visualizar estes relatórios, selecione **Apps** > estado de proteção de **aplicações** > **Relatórios**. O painel **de relatórios** fornece vários relatórios baseados no utilizador e na app, incluindo o seguinte:

### <a name="user-report"></a>Relatório do utilizador
Pode procurar um único utilizador e ver o estado de conformidade do mesmo. O painel **Relatório da aplicação** mostra as seguintes informações para um utilizador selecionado:
- **Ícone**: Mostra se o estado da aplicação está atualizado.
- Nome da **aplicação**: O nome da aplicação.
- **Nome**do dispositivo : Dispositivos associados à conta do utilizador.
- **Tipo de dispositivo**: O tipo de dispositivo ou sistema operativo que o dispositivo está a funcionar.
- **Políticas**: As políticas associadas à app.
- **Estado**:
  - **Com entrada dada:** a política foi implementada no utilizador e a aplicação foi utilizada no contexto profissional pelo menos uma vez.
  - **Não foi verificado**: A apólice foi implementada para o utilizador, mas a aplicação não foi utilizada no contexto de trabalho desde então.
- **Last Sync**: Quando a aplicação foi sincronizada pela última vez com Intune. 

>[!NOTE]
> A coluna **Last Sync** representa o mesmo valor tanto no relatório de estado do utilizador na consola como no relatório da Política de Proteção de Aplicações [exportável .csv](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities). A diferença é um pequeno atraso na sincronização entre o valor dos dois relatórios. 
>
> O tempo referenciado em Last Sync é quando Intune viu pela última vez a instância da aplicação. Quando um utilizador lança uma aplicação, pode notificar o serviço de Proteção de Aplicações Intune nessa altura de lançamento, dependendo da última vez que foi verificado. Consulte os intervalos de [repetição para o check-in da Política de Proteção](~/apps/app-protection-policy-delivery.md)de Aplicações . Se um utilizador não tiver usado essa aplicação em particular no último intervalo de check-in (que normalmente é de 30 minutos para uso ativo), e lançar a aplicação, então:
>
> - O relatório da Política de Proteção de Aplicações exportável .csv tem o mais recente tempo, dentro de 1 minuto (mínimo) a 30 minutos (máximo).
> - O relatório de estado do Utilizador tem o mais recente tempo instantaneamente.
>
> Por exemplo, considere um utilizador direcionado e licenciado que lança uma aplicação protegida às 12:00:
> - Se este é um sinal de inscrição pela primeira vez, isso significa que o utilizador foi assinado antes, e não tem um registo de instância de aplicação com Intune. Após o check-in do utilizador, o utilizador obtém um novo registo de instância de aplicação e pode ser imediatamente verificado (com os mesmos atrasos de tempo listados anteriormente para futuros check-ins). Assim, o tempo de Última Sincronização é às 12:00 no relatório do estado do utilizador e às 12:01 (ou 12:30 horas, o mais tardar) no relatório da Política de Proteção de Aplicações. 
> - Se o utilizador estiver apenas a lançar a aplicação, o tempo de Última Sincronização reportado depende da última vez que o utilizador registou o check-in.

Para ver o relatório para um utilizador, siga estes passos:

1. Para selecionar um utilizador, escolha o azulejo resumo do **estado do Utilizador.**

    ![Screenshot do azulejo resumo da gestão de aplicações móveis Intune](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. No painel de relatórios da **App,** escolha **o utilizador Select** para procurar um utilizador do Diretório Ativo Azure.

    ![Screenshot da opção select user no painel de relatórios da App](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. Selecione o utilizador na lista. Pode ver os detalhes do estado de conformidade do utilizador.

>[!NOTE]
> Se os utilizadores que procurou não tiverem a política de MAM implementada, verá uma mensagem a informar que não existem políticas de MAM que abranjam esses utilizadores.

### <a name="app-report"></a>Relatório de aplicativos
Pode pesquisar por plataforma e app, e então este relatório fornecerá dois diferentes status de proteção de aplicações que pode selecionar antes de gerar o relatório. Os estados podem ser **protegidos** ou **desprotegidos**.

  - Estado do utilizador para a atividade gerida do MAM **(Protegido**): Este relatório descreve a atividade de cada aplicação MAM gerida, por utilizador. Mostra todas as aplicações direcionadas pelas políticas de MAM para cada utilizador, e o estado de cada aplicação como verificado com as políticas do MAM. O relatório inclui também o estado de cada aplicação que foi direcionada com uma política de MAM, mas nunca foi verificada.
  - Estado do utilizador para atividade sem gestão de MAM **(Desprotegida**): Este relatório descreve a atividade de aplicações ativadas por MAM que não são atualmente geridas, por utilizador. Isto pode acontecer porque:
    - Estas aplicações estão a ser utilizadas por um utilizador ou por uma aplicação que não é atualmente alvo de uma política de MAM.
    - Todas as aplicações estão registadas, mas não estão a receber políticas de MAM.

    ![Screenshot do painel de relatórios da App de um utilizador, com detalhes para três apps](./media/app-protection-policies-monitor/MAM-reporting-4.png)

### <a name="user-configuration-report"></a>**Relatório de configuração do utilizador**
Com base num utilizador selecionado, este relatório fornece detalhes sobre quaisquer configurações de aplicações que o utilizador tenha recebido.

### <a name="app-configuration-report"></a>**Relatório de configuração de aplicativos**
Com base na plataforma e aplicação selecionadas, este relatório fornece detalhes sobre quais os utilizadores que receberam configurações para a aplicação selecionada.

### <a name="app-learning-report-for-windows-information-protection"></a>Relatório de aprendizagem de aplicativos para proteção de informações do Windows
Este relatório mostra quais as aplicações que estão a tentar ultrapassar os limites das políticas.

### <a name="website-learning-for-windows-information-protection"></a>Aprendizagem de websites para proteção de informação do Windows
Este relatório mostra quais os sítios web que estão a tentar ultrapassar os limites das políticas.

## <a name="export-app-protection-activities"></a>Atividades de proteção de aplicativos de exportação
Pode exportar todas as atividades de políticas de proteção de aplicações para um ficheiro .csv único. Esta funcionalidade pode ser útil para analisar todos os estados de proteção de aplicações comunicados pelos utilizadores. O **ficheiro App Protection .csv mostra:**
- **Utilizador**: O nome do utilizador.
- **E-mail**: O e-mail do utilizador.
- **App**: O nome da aplicação.
- Versão da **aplicação**: A versão da aplicação.
- **Nome**do dispositivo : Nomes de quaisquer dispositivos associados à conta do utilizador.
- **Fabricante do dispositivo**: Isto lista o fabricante do dispositivo (apenas Android). 
- **Modelo do dispositivo**: Isto lista o fabricante do dispositivo (apenas Android). 
- **Android Patch Versão**: A data do último Patch de Segurança Android.
- Id do **dispositivo AAD:** Esta coluna fica povoada se o dispositivo for aderido a AAD.
- **ID DO Dispositivo MDM**: Esta coluna fica povoada se o dispositivo estiver matriculado Microsoft Intune MDM.
- **Plataforma**: O sistema operativo.
- **Versão da plataforma**: A versão do sistema operativo.
- Tipo de **gestão**: Tipo de gestão no dispositivo. Por exemplo, Android Enterprise, sem gestão, ou MDM.  
- **Estado de Proteção de Aplicações**: Desprotegido ou protegido.
- **Política**: As políticas de proteção de aplicações associadas à aplicação.
- **Last Sync**: Quando a aplicação foi sincronizada pela última vez com o Microsoft Intune. 
- **Compliance State**: Se a aplicação no dispositivo do utilizador está em conformidade com quaisquer políticas de acesso condicional baseadas em aplicações.  

Siga estes passos para gerar ficheiro App Protection .csv ou ficheiro App Configuration .csv:

1. No painel de gestão de aplicações móveis do Intune, selecione **Relatório de proteção de aplicações**.

    ![Screenshot do link de descarregamento de proteção de aplicativos](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Escolha **Sim** para salvar o seu relatório e, em seguida, escolha **Save As**. Selecione a pasta em que pretende guardar o relatório.

    ![Captura de ecrã da caixa de confirmação Guardar relatório](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)
   
> [!NOTE]
> A Intune fornece campos adicionais de reporte de dispositivos, incluindo id de registo de aplicações, fabricante android, modelo e versão de patch de segurança, bem como modelo iOS. Intune, você acede a estes campos selecionando **Apps** > **estado de proteção** de aplicações > Relatório de Proteção de **Aplicações: iOS/iPadOS, Android**. Além disso, estes parâmetros ajudam a configurar a lista **de permitir** para o fabricante do dispositivo (Android), a lista **de permitir** para o modelo de dispositivo (Android e iOS) e a definição mínima de patch de **segurança Android.**   
 
## <a name="see-also"></a>Veja também
- [Gerir a transferência de dados entre aplicações iOS/iPadOS](data-transfer-between-apps-manage-ios.md)
- [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-android.md)
- [O que esperar quando a sua aplicação iOS/iPadOS for gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-ios.md)
