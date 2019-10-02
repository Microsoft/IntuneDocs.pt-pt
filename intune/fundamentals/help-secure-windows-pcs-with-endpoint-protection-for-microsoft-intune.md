---
title: Endpoint Protection para PCs Windows
titleSuffix: Microsoft Intune
description: Proteja os seus computadores geridos com o Endpoint Protection, que proporciona proteção em tempo real contra ameaças de software maligno.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 002241bf-6cd0-4c75-a4f0-891ac7e6721a
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8de39d0265b6ef4ce7e78f9bbe512928d2e098de
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731792"
---
# <a name="help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune"></a>Ajude a proteger os PCs Windows com o Endpoint Protection para o Microsoft Intune

[!INCLUDE [classic-portal](../../intune-classic/includes/classic-portal.md)]

O Microsoft Intune pode ajudá-lo a proteger os seus computadores geridos com o Endpoint Protection, que proporciona proteção em tempo real contra ameaças de software maligno, mantém as definições de software maligno atualizadas e analisa automaticamente os computadores. O Endpoint Protection também proporciona ferramentas que o ajudam a gerir e monitorizar ataques de software maligno.

Se ainda não instalou o cliente Intune nos seus computadores, consulte [Instalar o cliente do PC Windows com o Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Utilize as informações das secções seguintes para o ajudar a configurar, implementar e monitorizar o Endpoint Protection.

## <a name="choose-when-to-use-endpoint-protection"></a>Escolher quando utilizar o Endpoint Protection
Enquanto administrador de TI, uma das suas principais prioridades é manter os computadores que gere protegidos de software maligno e vírus. Antes de implementar o Intune em PCs Windows na sua organização, deve decidir como pretende proteger os seus computadores ao selecionar uma das seguintes opções e configurar as definições de política associadas:


|                                                                                                                                                                       Pretende:                                                                                                                                                                        |                                                                                                       Definições de política do Endpoint Protection                                                                                                        |                                                                                                                                                  Mais informações                                                                                                                                                  |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                             Utilizar o Endpoint Protection do Microsoft Intune apenas se não existir uma aplicação de proteção de pontos finais de terceiros instalada.<br /><br />Pode utilizar o Endpoint Protection do Microsoft Intune em todos os computadores nos quais não se encontre instalada nenhuma aplicação de proteção de pontos finais de terceiros instalada.                                              | Instalar o Endpoint Protection = <strong>Sim</strong><br /><br />Ativar o Endpoint Protection = <strong>Sim</strong><br /><br />Instalar o Endpoint Protection mesmo que se encontre instalada uma aplicação de proteção de pontos finais de terceiros = <strong>Não</strong>  |                                                                      Se for detetada uma aplicação de proteção de pontos finais de terceiros, o Endpoint Protection do Microsoft Intune não é instalado e, se estava instalado anteriormente, é desinstalado.                                                                       |
| Utilizar o Endpoint Protection do Microsoft Intune, mesmo que exista uma aplicação de proteção de pontos finais de terceiros instalada.<br /><br />Com esta abordagem, executará o Endpoint Protection do Microsoft Intune e a aplicação de proteção de pontos finais de terceiros em simultâneo. Devido a potenciais problemas de desempenho, não recomendamos esta configuração. | Instalar o Endpoint Protection = <strong>Sim</strong><br /><br />Ativar o Endpoint Protection = <strong>Sim</strong><br /><br />Instalar o Endpoint Protection mesmo que se encontre instalada uma aplicação de proteção de pontos finais de terceiros = <strong>Sim</strong> |                        Utilize se:<br /><br />– Quiser passar a utilizar o Endpoint Protection do Microsoft Intune.<br />– Implementar um novo cliente que irá utilizar o Endpoint Protection do Microsoft Intune.<br />– Atualizar qualquer cliente que irá utilizar o Endpoint Protection do Microsoft Intune.                         |
|                                                                                                             Utilizar o Intune sem o Endpoint Protection do Microsoft Intune. Em alternativa, utilizará uma aplicação de proteção de pontos finais de terceiros.                                                                                                             |                                                                                                Instalar o Endpoint Protection = <strong>Não</strong>                                                                                                 | Esta configuração não é recomendada se não estiver a utilizar uma aplicação de proteção de pontos finais de terceiros, porque esta pode expor os computadores da sua organização a software maligno ou a outros ataques.<br /><br />O Endpoint Protection do Microsoft Intune não é instalado e, se estava instalado anteriormente, é desinstalado. |

Para mudar da sua aplicação de proteção de pontos finais atual para o Endpoint Protection do Microsoft Intune, faça o seguinte:

1. Deixe a sua aplicação de proteção de pontos finais atual em execução enquanto implementa o software de cliente Intune nesses computadores.

2. Confirme que o Endpoint Protection do Microsoft Intune está instalado e que está a ajudar a proteger os computadores cliente.

3. Remova o software de proteção de pontos finais de terceiros ao:

    - Utilizar a distribuição de software Intune para implementar uma ferramenta de remoção de software fornecida pelo fabricante da aplicação de proteção de pontos finais de terceiros. Para mais informações, consulte [Implementar aplicações com o Microsoft Intune](../apps/apps-deploy.md).

    - Remover a aplicação de proteção de pontos finais de terceiros manualmente.

> [!NOTE]
> O Intune não desinstalará automaticamente aplicações de proteção de pontos finais de terceiros.

## <a name="configure-microsoft-intune-endpoint-protection"></a>Configurar o Endpoint Protection do Microsoft Intune
Utilize os seguintes passos para o ajudar a configurar o Endpoint Protection do Microsoft Intune.

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Política** > **Adicionar Política**.

2. Expanda a opção **Gestão de Computadores** e, em seguida, selecione **Definições do Agente do Microsoft Intune**. Selecione **Criar e Implementar uma Política Personalizada** para especificar uma política para as definições do Endpoint Protection. Em seguida, selecione o botão **Criar Política**.

Pode utilizar as definições recomendadas ou personalizar as mesmas. Se precisar de mais informações sobre como criar e implementar políticas, consulte o tópico [Tarefas de gestão comuns do PC Windows com o cliente do computador do Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

  ![Definições do Endpoint Protection](./media/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune/pol-sa-pc-endpoint-policy.png)

Pode ver a política implementada do Endpoint Protection na página **Todas as Políticas** da área de trabalho **Política**.

## <a name="specify-endpoint-protection-service-settings"></a>Especificar as definições de serviço do Endpoint Protection

|                                                 Definição de política                                                  |                                                                                                                                                                                                                                                                                                                                                                                                             Detalhes                                                                                                                                                                                                                                                                                                                                                                                                             |
|-----------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                  <strong>Instalar o Endpoint Protection</strong>                                   | Defina como <strong>Sim</strong> para instalar o Endpoint Protection em computadores geridos. Se uma aplicação de proteção de pontos finais de terceiros for detetada durante a instalação, o Endpoint Protection só será instalado se a definição <strong>Instalar o Endpoint Protection mesmo que se encontre instalada uma aplicação de proteção de pontos finais de terceiros</strong> estiver definida como <strong>Sim</strong>. <strong>Nota:</strong> Por padrão, o Intune Endpoint Protection é instalado em computadores gerenciados. Se não quiser instalar o Endpoint Protection nos seus computadores geridos, tem de definir explicitamente esta política para <strong>Não</strong>. Se o Endpoint Protection tiver sido anteriormente instalado e a política for atualizada para <strong>Não</strong>, o cliente do Endpoint Protection será desinstalado.<br />Valor recomendado: <strong>Sim</strong> |
| <strong>Instalar o Endpoint Protection mesmo que se encontre instalada uma aplicação de proteção de pontos finais de terceiros</strong> |                                                                                                                                                                                                                                                                                                                Defina como <strong>Sim</strong> para instalar o Endpoint Protection do Microsoft Intune mesmo que seja detetada uma aplicação de proteção de pontos finais de terceiros.<br /><br />Valor recomendado: <strong>Sim</strong>                                                                                                                                                                                                                                                                                                                |
|                                   <strong>Ativar o Endpoint Protection</strong>                                   |                                                                                                                                                                                                            Defina como <strong>Sim</strong> para ativar o Endpoint Protection do Microsoft Intune nos computadores que têm o cliente do Endpoint Protection.<br /><br />Se definir como <strong>Não</strong> e o Endpoint Protection do Microsoft Intune estiver instalado, a interface de utilizador do cliente do Endpoint Protection não será apresentada aos utilizadores e todas as funcionalidades de proteção estarão inativas.<br /><br />Valor recomendado: <strong>Sim</strong>                                                                                                                                                                                                             |
|                                       <strong>Desativar IU de Cliente</strong>                                        |                                                                                                                                                                                                                                                                                                      Defina como <strong>Sim</strong> para ocultar a interface de utilizador do cliente Endpoint Protection do Microsoft Intune dos utilizadores (é necessário reiniciar o computador cliente para que as alterações sejam aplicadas).<br /><br />Valor recomendado: <strong>Não</strong>                                                                                                                                                                                                                                                                                                       |
| <strong>Instalar o Endpoint Protection mesmo que se encontre instalada uma aplicação de proteção de pontos finais de terceiros</strong> |                                                                                                                                                                                                                                                                                                       Defina como <strong>Sim</strong> para forçar a instalação do Endpoint Protection do Microsoft Intune, mesmo que seja detetada uma aplicação de proteção de pontos finais de terceiros.<br /><br />Valor recomendado: <strong>Não</strong>                                                                                                                                                                                                                                                                                                       |
|                    <strong>Criar um ponto de restauro do sistema antes de remediação de software maligno</strong>                    |                                                                                                                                                                                                                                                                                                                                 Defina como <strong>Sim</strong> para criar um Ponto de Restauro do Sistema do Windows antes do início de remediações de software maligno.<br /><br />Valor recomendado: <strong>Sim</strong>                                                                                                                                                                                                                                                                                                                                  |
|                                 <strong>Controlar software maligno resolvido (dias)</strong>                                  |                                                                                                                                                                                                                                                                                      Permite ao Endpoint Protection controlar software maligno resolvido durante um período de tempo específico, para que possa verificar manualmente computadores anteriormente infetados.<br /><br />Pode especificar um valor de 0 a 30 dias.<br /><br />Valor recomendado: <strong>7 dias</strong>                                                                                                                                                                                                                                                                                       |

Se tiver definido os valores da política das definições **Instalar o Endpoint Protection** e **Ativar o Endpoint Protection** para **Sim** e o valor da política de **Instalar o Endpoint Protection mesmo que se encontre instalada uma aplicação de proteção de pontos finais de terceiros** para **Não**, o Endpoint Protection do Microsoft Intune deteta que está instalada outra aplicação de proteção de pontos finais. Isto significa que o Endpoint Protection não será instalado ou será desinstalado se já se encontrar presente. No entanto, o Endpoint Protection do Microsoft Intune informa acerca do estado de funcionamento da outra aplicação de proteção de pontos finais no Intune.

  O Microsoft Security Essentials alerta o utilizador com proteção em tempo real quando potenciais ameaças, tais como vírus e spyware, estão a tentar instalar-se ou a executar no seu PC. No momento em que isto acontecer, verá uma mensagem na área de notificação no lado direito da barra de tarefas.

### <a name="specify-real-time-protection-settings"></a>Especificar definições de proteção em tempo real

|Definição de política|Detalhes|
|------------------|--------------------|
|**Ativar proteção em tempo real**|Ativa a monitorização e análise de todos os ficheiros e aplicações acedidos. Também bloqueia aplicações e ficheiros maliciosos antes de estes serem executados em computadores.<br /><br />Valor recomendado: **Sim**|
|**Analisar todas as transferências**|Permite a análise de todos os ficheiros e anexos transferidos da Internet para computadores.<br /><br />Valor recomendado: **Sim**|
|**Monitorizar a atividade de programas e ficheiros em computadores**|Ativa a monitorização de ficheiros recebidos e ficheiros enviados e a atividade de programas em computadores. Com esta definição, o Endpoint Protection pode monitorizar a altura em que os ficheiros e programas começam a ser executados e alertá-lo relativamente a ações realizadas pelos mesmos ou ações efetuadas nos mesmos.<br /><br />Valor recomendado: **Sim**|
|**Ficheiros monitorizados**|Permite-lhe escolher se apenas os ficheiros recebidos, os ficheiros enviados ou se todos os ficheiros são monitorizados.<br /><br />Valor recomendado: **Monitorar todos os arquivos**|
|**Ativar a monitorização de comportamento**|Permite ao Endpoint Protection do Microsoft Intune verificar a existência de padrões específicos de atividades suspeitas em computadores cliente.<br /><br />Valor recomendado: **Sim**|
|**Ativar o Sistema de Inspeção de Rede**|Ativa o Sistema de Inspeção de Rede (NIS) em computadores cliente. O NIS utiliza assinaturas de vulnerabilidades conhecidas do [Centro Microsoft de Proteção Contra Software Maligno](https://go.microsoft.com/fwlink/?LinkId=234249) para ajudar a detetar e a bloquear tráfego de rede malicioso.<br /><br />Valor recomendado: **Sim**|

  ![Definições em tempo real do Endpoint Protection](./media/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune/pol-sa-pc-policy-realtime.png)

### <a name="specify-scan-schedule-settings"></a>Especificar definições de agendamento de análise

|Definição de política|Mais informações|
|------------------|--------------------|
|**Agendar uma análise rápida diária**|Agenda uma análise rápida diária de ficheiros utilizados frequentemente e de ficheiros de sistema importantes em computadores. Esta análise rápida afeta pouco o desempenho.<br /><br />Valor recomendado: **Sim**|
|**Executar uma análise rápida caso não tenham ocorrido duas análises consecutivas**|Configura o Endpoint Protection para executar automaticamente uma análise rápida em computadores caso não tenham sido efetuadas duas análises rápidas consecutivas.<br /><br />Valor recomendado: **Sim**|
|**Agendar uma análise completa**|Configura uma análise completa de todos os ficheiros e recursos nos discos rígidos dos computadores locais. Esta análise pode demorar algum tempo e pode afetar o desempenho do computador (o tempo que demora depende do número de ficheiros e recursos que são analisados).<br /><br />Valor recomendado: **Não**|
|**Executar uma análise completa caso não tenham ocorrido duas análises completas consecutivas**|Configura o Endpoint Protection para executar automaticamente uma análise completa em computadores caso não tenham sido efetuadas duas análises consecutivas.<br /><br />Valor recomendado: Não configurado|

### <a name="specify-scan-options-settings"></a>Especificar definições de opções de análise

|Definição de política|Detalhes|
|------------------|--------------------|
|**Executar uma análise completa após a instalação do Endpoint Protection**|Defina como **Sim** para permitir que o Endpoint Protection execute automaticamente uma análise completa do sistema após a instalação em computadores. Esta análise apenas é executada quando os computadores estão inativos, de forma a minimizar as consequências na produtividade do utilizador.<br /><br />Valor recomendado: **Sim**|
|**Executar automaticamente uma análise completa, quando necessário, após remoção de software maligno**|Defina como **Sim** para permitir que o Endpoint Protection execute automaticamente uma análise completa do sistema em computadores após a remoção de software maligno, para ajudar a confirmar que não foram afetados outros ficheiros.<br /><br />Valor recomendado: **Sim**|
|**Iniciar uma análise agendada apenas quando o computador estiver inativo**|Defina como **Sim** para impedir o início de análises agendadas quando os computadores estiverem a ser utilizados, de modo a evitar perda de produtividade por parte dos utilizadores.<br /><br />Valor recomendado: **Sim**|
|**Verificar as definições de software maligno mais recentes antes de iniciar uma análise**|Defina como **Sim** para permitir que o Endpoint Protection verifique automaticamente as definições de software maligno mais recentes antes de iniciar uma análise em computadores.<br /><br />Valor recomendado: **Sim**|
|**Analisar ficheiros de arquivo**|Defina como **Sim** para configurar o Endpoint Protection para procurar software maligno em ficheiros de arquivo (como ficheiros .zip ou .cab) em computadores.<br /><br />Valor recomendado: **Não**|
|**Analisar mensagens de e-mail**|Defina como **Sim** para configurar o Endpoint Protection para analisar mensagens de e-mail recebidas quando estas chegam aos computadores.<br /><br />Valor recomendado: **Sim**|
|**Analisar ficheiros abertos a partir de pastas partilhadas na rede**|Defina como **Sim** para configurar o Endpoint Protection para analisar ficheiros abertos a partir de pastas partilhadas na rede. Normalmente, são ficheiros acedidos através de um caminho UNC (Universal Naming Convention). A ativação desta funcionalidade pode causar problemas a utilizadores com acesso só de leitura, uma vez que não podem remover software maligno.<br /><br />Valor recomendado: **Não**|
|**Analisar unidades de rede mapeadas**|Defina como **Sim** para configurar o Endpoint Protection para analisar ficheiros em unidades de rede mapeadas. A ativação desta funcionalidade pode causar problemas a utilizadores com acesso só de leitura, uma vez que não podem remover software maligno.<br /><br />Valor recomendado: **Não**|
|**Analisar unidades amovíveis**|Defina como **Sim** para configurar o Endpoint Protection para procurar software maligno e software indesejado em unidades amovíveis, como pens USB, quando executa uma análise completa em computadores.<br /><br />Valor recomendado: **Sim**|
|**Limitar a utilização da CPU durante a análise**|Defina a percentagem máxima da utilização do CPU que pode ser utilizada durante as análises agendadas em computadores. Pode definir este valor de 1 a 100 %.<br /><br />Valor recomendado: **50%**|

### <a name="choose-default-actions-settings"></a>Selecionar as predefinições de ações

A definição **Escolher como o Endpoint Protection age em software maligno dos seguintes níveis de alerta** especifica a ação predefinida que o Endpoint Protection executa quando é detetado software maligno de vários níveis de alerta. Para cada nível de alerta, pode remover o software maligno, colocá-lo em quarentena ou efetuar a ação recomendada da Microsoft.

Valor recomendado: **Ação recomendada**, que permite Endpoint Protection para a ação de recomendar.   

### <a name="decide-whether-to-choose-the-excluded-files-and-folders-settings"></a>Decidir se deve selecionar as definições de pastas e ficheiros excluídos

A definição **Ficheiros e pastas a serem excluídos ao executar uma análise ou utilizar a proteção em tempo real** exclui ficheiros ou pastas específicos quando uma análise é executada ou quando a proteção em tempo real é utilizada em computadores.

### <a name="decide-whether-to-choose-the-excluded-processes-settings"></a>Decidir se deve selecionar as definições de processos excluídos

A definição **Processos a serem excluídos ao executar uma análise ou ao utilizar a proteção em tempo real** permite-lhe excluir processos específicos quando uma análise está em execução ou quando a proteção em tempo real é utilizada em computadores. Só pode excluir ficheiros com as seguintes extensões: **.exe**, **.com** ou **.scr**.

### <a name="decide-whether-to-choose-the-excluded-file-types-settings"></a>Decidir se pretende escolher as definições de tipos de ficheiro excluídos

A definição **Extensões de ficheiros a serem excluídas ao executar uma análise ou ao utilizar a proteção em tempo real** permite excluir extensões de nome de ficheiro específicas quando uma análise é executada ou quando a proteção em tempo real é utilizada em computadores.

### <a name="specify-microsoft-active-protection-service-settings"></a>Especificar definições do Serviço de Proteção Ativa Microsoft
O Serviço de Proteção Ativa Microsoft é uma comunidade online que o ajuda a decidir como reagir a potenciais ameaças. A comunidade também ajuda a parar a propagação de novas infeções de software maligno. Pode **Aderir ao Serviço de Proteção Ativa Microsoft** ao selecionar **Sim** e, em seguida, especificar o **Nível de Associação**:
- **Básico** – envia informações básicas sobre software maligno detetado à Microsoft. Estas informações incluem a origem do software, as ações aplicadas por si ou que o Endpoint Protection aplica automaticamente e se as mesmas tiveram êxito.
- **Avançado** – envia mais informações sobre software maligno, spyware e software potencialmente indesejado à Microsoft. Isto inclui informações sobre a localização do software, nomes dos ficheiros, como o software funciona e como afetou o seu computador.

Também pode **Receber definições dinâmicas baseadas em relatórios do Serviço de Proteção Ativa Microsoft**.

## <a name="choose-management-tasks-for-endpoint-protection"></a>Selecionar tarefas de gestão do Endpoint Protection
As tarefas seguintes ajudam-no a realizar várias tarefas de gestão em computadores geridos que executam o Endpoint Protection.
- Atualizar definições de software maligno
  - Consola do Intune – a partir da área de trabalho **Grupos**, selecione os computadores que pretende atualizar. Selecione **Tarefas Remotas** &gt; **Atualizar Definições de Software Maligno**.
  - Computador gerido – Inicie o software do cliente Endpoint Protection a partir da área de notificação do Windows. Selecione o separador **Atualizar** e, em seguida, selecione **Atualizar**.
- Executar uma análise de software maligno:
  - Consola do Intune – a partir da área de trabalho **Grupos**, selecione os computadores que pretende analisar. Selecione **Executar uma Análise Completa de Software Maligno** ou **Executar uma Análise Rápida de Software Maligno**.
  - Computador gerido – inicie o software do cliente Endpoint Protection a partir da área de notificação do Windows. Selecione **Rápida**, **Completa** ou **Personalizada** e, em seguida, selecione **Analisar agora**.

Pode ver o estado de uma tarefa remota ao selecionar a ligação **Tarefas Remotas** no canto inferior direito da consola do Intune. A caixa de diálogo **Estado da Tarefa Remota** indica as tarefas remotas atuais, o estado da tarefa, o nome do dispositivo e quaisquer erros comunicados. Também fornece uma ligação para informações de resolução de problemas, se adequado.

## <a name="monitor-endpoint-protection"></a>Monitorizar o Endpoint Protection
Pode monitorizar o estado de software maligno nos seus computadores ao utilizar a área de trabalho **Proteção** da [consola de administração do Microsoft Intune](https://manage.microsoft.com/). Esta área de trabalho contém duas páginas:
- **Descrição Geral da Proteção** – apresenta problemas importantes como ligações que pode escolher para obter mais informações. Os problemas que podem ser apresentados incluem:
  - **Instâncias de software maligno que necessitam de seguimento** – clique na ligação para ver uma lista de problemas de software maligno, incluindo a ação de seguimento necessária para resolver o problema. Pode explorar esta lista para ver que computadores são afetados.
  - **Computadores com software maligno que necessitam de seguimento** – clique na ligação para ver todos os computadores com problemas de software maligno não resolvidos, incluindo a ação de seguimento necessária para resolver o problema.
  - **Dispositivos não protegidos** – Clique na ligação para ver computadores não protegidos por software do proteção de pontos finais, devido à não instalação do software ou a um erro. Selecione um computador para ver mais detalhes.
  - **Dispositivos com outra aplicação de proteção de pontos finais em execução** – Clique na ligação para ver computadores com uma aplicação de proteção de pontos finais de terceiros em execução.
- **Todos os malwares** – exibe uma lista de todos os malwares ativos encontrados em seus computadores. Pode explorar esta lista para ver todos os computadores que são afetados por um software maligno específico ou pode selecionar uma das seguintes tarefas:
  - **Ver Propriedades** – abre uma página com mais informações sobre o software maligno selecionado.
  - **Saber Mais Sobre Este Software Maligno** – Abre um tópico do Centro Microsoft de Proteção Contra Software Maligno com mais informações sobre o software maligno.

> [!IMPORTANT]
> A área de trabalho **Proteção** só é apresentada na consola de administração quando tiver instalado o cliente e estiver a gerir, no mínimo, um cliente do computador.

  ![Monitorizar o Endpoint Protection](./media/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune/pol-sa-ep-monitor.png)

### <a name="how-to-view-recent-detection-paths-for-malware-on-computers"></a>Como ver Caminhos de Deteção Recentes para software maligno em computadores
O Intune pode apresentar os caminhos de até 10 das instâncias de software maligno detetadas mais recentemente num dispositivo. O **Caminho de Deteção Recente** está desativado por predefinição. Para ativar esta vista:

1. Na [Consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Grupos** > **Todos os Dispositivos** > **Todos os Computadores**.
2. Clique com o botão direito do rato no computador cujos caminhos de deteção recentes pretende ver e selecione **Propriedades**.
3. Selecione **Software Maligno** nos separadores na parte superior.

   ![Selecionar o separador Software Maligno e clicar na caixa de verificação Caminhos de Deteção Recentes](./media/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune/malware-path-column.png)
4. Clique com o botão direito do rato no cabeçalho da coluna. É apresentada uma lista das colunas disponíveis. Selecione a caixa de verificação **Caminhos de Deteção Recentes** na lista. A coluna **Caminhos de Deteção Recentes** aparece e apresenta até 10 das instâncias de software maligno monitorizadas mais recentemente no dispositivo.

## <a name="run-a-malware-scan-or-update-malware-definitions-on-a-computer"></a>Executar uma análise de software maligno ou atualizar as definições de software maligno num computador
O Intune pode executar uma análise de software maligno completa ou rápida ao utilizar o Endpoint Protection ou o Windows Defender num PC gerido remotamente que tenha o cliente do Intune instalado.

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), aceda a **Grupos** > **Descrição Geral** > **Todos os Dispositivos** > **Todos os Computadores** e, em seguida, selecione o computador que pretende direcionar.

2. Selecione a lista pendente **Tarefas Remotas** e, em seguida, selecione a tarefa para executar no computador remoto.

## <a name="need-more-help"></a>Precisa de mais ajuda?
Para mais ajuda e suporte, consulte [Resolução de Problemas do Endpoint Protection no Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md).

## <a name="see-also"></a>Consulte também
[Políticas para proteger PCs Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)
