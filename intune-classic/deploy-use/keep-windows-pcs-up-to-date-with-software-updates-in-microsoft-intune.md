---
title: Atualizações de software para PCs Windows
description: O Intune ajuda-o a manter os seus computadores atualizados ao garantir que as correções de erros e atualizações de software mais recentes são rapidamente instaladas.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 48e9c41a-d2de-424e-9610-cfd1ad514210
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 391c6788d8503ee52bbe15a112cf897e11caf2e5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune"></a>Manter os PCs Windows atualizados com atualizações de software no Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

O Microsoft Intune pode ajudar a proteger os seus computadores geridos de várias formas, incluindo a gestão de atualizações de software que mantêm os seus computadores atualizados, assegurando que os patches e as atualizações de software mais recentes são rapidamente instaladas.

Se ainda não instalou o cliente Intune nos seus computadores, consulte [Instalar o cliente do PC Windows com o Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Quando estiverem disponíveis novas atualizações do Microsoft Update ou tiver criado uma atualização de terceiros e estas forem aplicáveis aos seus computadores geridos, é apresentada uma notificação na página **Descrição geral** da área de trabalho **Atualizações**. Após escolher esta ligação de notificação, pode realizar várias operações como ver mais informações sobre a atualização, aprovar ou recusar a atualização e ver os computadores que instalarão a atualização, se for aprovada.

> [!IMPORTANT]
> A área de trabalho **Atualizações** não é apresentada na consola do administrador até instalar o cliente e gerir com êxito, pelo menos, um computador cliente.

À medida que as atualizações são aprovadas e instaladas, pode examinar o êxito ou falha da instalação na área de trabalho **Atualizações** da consola do Intune.

As seguintes secções ajudam-no a manter o software dos seus computadores geridos atualizado.

## <a name="before-you-start"></a>Antes de começar
Antes de começar a criar e aprovar atualizações de software, configure e implemente políticas para os seus computadores que controlam quando e como as atualizações são instaladas.

### <a name="to-configure-update-policy-settings"></a>Para configurar definições de política de atualização

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), selecione **Política** &gt; **Descrição Geral** &gt; **Adicionar Política**.

2.  Configure e implemente uma política de **Definições do Agente do Microsoft Intune** para as definições da atualização. Pode utilizar definições recomendadas ou personalizar as mesmas. Se precisar de mais informações sobre como criar e implementar políticas, veja o artigo [Tarefas de gestão comuns do PC Windows com o computador cliente do Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

A tabela seguinte mostra os valores que pode configurar na política e os valores recomendados que serão utilizados se não personalizar a política. Pode encontrar estas definições na secção **Atualizações**.

  |Definição de política|Detalhes|
    |------------------|--------------------|
    |**Frequência de deteção de atualizações e aplicações (horas)** |Especifica a frequência (de 8 a 22 horas) com que o Intune procura novas atualizações e aplicações.<br /><br />Valor recomendado: **8** horas.|
    |**Instalação automatizada ou a pedido de atualizações e aplicações** |Especifica se as atualizações são instaladas automaticamente ou se é pedido ao utilizador antes de instalar. Esta definição permite-lhe também agendar a instalação das atualizações e aplicações.<br /><br />**Instalar atualizações e aplicações automaticamente conforme agendado** instala atualizações e aplicações através da agenda especificada.<br /><br />Enquanto definição dependente de uma política, **Utilizar Manutenção Automática para computadores com Windows**  especifica que as atualizações e as aplicações são instaladas durante a janela de manutenção automática do Windows.<br /><br />**Pedir ao utilizador para instalar** pede ao utilizador para instalar atualizações quando estas estão prontas.<br /><br />Valores recomendados:<br /><br />Definição **Instalar atualizações e aplicações automaticamente conforme agendado** selecionada<br /><br />**Dia agendado: todos os dias**<br /><br />**Hora agendada: 3:00**<br /><br />Definição **Utilizar Manutenção Automática para computadores Windows** selecionada|
    |**Permitir a instalação imediata de atualizações que não interrompem o Windows** |**Permitir** instala atualizações imediatamente após serem transferidas, exceto as atualizações que iriam interromper ou reiniciar o Windows. Estas atualizações são instaladas de acordo com a configuração da definição **Instalação automatizada ou a pedido de atualizações**.<br /><br />**Não permitir** instala atualizações de acordo com a configuração da definição **Instalação automatizada ou a pedido de atualizações**.<br /><br />Valor recomendado: **Permitir** |
    |**Atrasar o reinício do Windows após a instalação das atualizações e aplicações agendadas (minutos)** |Especifica (de 1-30 minutos) o tempo de espera para reiniciar o Windows após instalar as atualizações e aplicações agendadas.<br /><br />Valor recomendado: **15 minutos** |
    |**Atrasar após reiniciar o Windows para começar a instalar as atualizações e aplicações agendadas perdidas (minutos)** |Especifica (de 1-60 minutos) quanto tempo aguardar para começar a instalação de atualizações e aplicações após o Windows ser reiniciado quando uma atualização agendada foi perdida.<br /><br />Valor recomendado: **5 minutos**|
    |**Permitir que utilizadores com sessão iniciada controlem o reinício do Windows após instalar as atualizações e aplicações agendadas** |Especifica se o utilizador com sessão iniciada pode atrasar o reinício do Windows (se estiver definido para **Sim**) ou ser notificado relativamente ao reinício automático do Windows (se estiver definido para **Não**). Se nenhum utilizador tiver sessão iniciada quando a instalação agendada de atualizações e aplicações for concluída, o Windows é reiniciado automaticamente conforme necessário. Quando estiver predefinido para **Não**, o tempo antes de o Windows reiniciar está definido para 5 minutos.<br /><br />Valor recomendado: **Sim**|
    |**Pedir ao utilizador para reiniciar o Windows durante as atualizações obrigatórias do agente do cliente do Intune** |Especifica se é pedido aos utilizadores com sessão iniciada que reiniciem o Windows quando uma atualização obrigatória do cliente do Intune exige que o Windows reinicie.<br /><br />Valor recomendado: **Sim**|
    |**Agenda de instalação de atualizações obrigatórias do agente do cliente do Microsoft Intune** |Agenda quando ocorre a instalação de atualizações de cliente.<br /><br />Valor recomendado: não configurado|
    |**Atrasar entre pedidos para reiniciar o Windows após a instalação das atualizações e aplicações agendadas (minutos)** |Especifica com que frequência (de 1-1440 minutos) é pedido ao utilizador para reiniciar o Windows quando é instalada uma atualização ou aplicação agendada que exige o reinício do Windows e o utilizador atrasa o mesmo.<br /><br />Valor recomendado: **30 minutos** |

## <a name="update-software-made-by-microsoft"></a>Atualizar software criado pela Microsoft
Atualizar software Microsoft exige pouco trabalho da sua parte. No entanto, antes de começar, deve configurar duas coisas:

-   **Categorias dos produtos e classificações de atualizações** - define as categorias e classificações de atualizações que pretende disponibilizar a computadores. Por exemplo, poderá decidir que apenas pretende instalar atualizações críticas para o Microsoft Office.

-   **Regras de aprovação automática** - estas regras aprovam automaticamente tipos de atualizações específicos e reduzem o overhead administrativo. Por exemplo, é recomendável aprovar automaticamente todas as atualizações de software críticas.

Utilize os dois métodos seguintes para ajudá-lo a preparar-se para utilizar as atualizações de software:

### <a name="configure-the-product-categories-and-update-classifications-you-want-to-make-available-to-managed-computers"></a>Configurar as categorias dos produtos e classificações de atualizações que pretende disponibilizar a computadores geridos

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Admin**&gt;**Atualizações**.

2.  Na página **Definições de Serviço: Atualizações**, na lista **Categorias de Produtos**, selecione as categorias de atualizações que pretende disponibilizar aos computadores. Tenha em atenção que as atualizações mais comuns estão selecionadas por predefinição.

    > [!IMPORTANT]
    > Para garantir que os computadores recebem as atualizações que foram aprovadas pelo administrador, a definição da Política de Grupo do Windows Server Update Services (WSUS), **Especificar localização do serviço de atualizações da Microsoft na intranet** não pode estar aplicada a computadores inscritos com o Intune.

3.  Na lista **Classificações de Atualizações**, selecione as classes de atualização que pretende disponibilizar a computadores geridos. Novamente, as opções mais comuns estão selecionadas por predefinição.

4.  Escolha **Guardar** para armazenar as suas seleções.

### <a name="to-configure-automatic-approval-rules-for-software-updates"></a>Para configurar regras de aprovação automática para atualizações de software

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Admin**&gt;**Atualizações**.

2.  Na secção **Regras de Aprovação Automática** da página **Definições do Servidor: Atualizações**, escolha **Novo**.

3.  Na página **Geral** do Assistente de Criação de Regra de Aprovação Automática, especifique o nome e descrição opcional da regra.

4.  Na página **Categorias dos Produtos**, selecione os produtos para os quais pretende que as atualizações sejam aprovadas automaticamente.

5.  Na página **Classificações de Atualizações**, especifique as classificações de atualizações que pretende aprovar automaticamente.

6.  Na página **Implementação**, efetue o seguinte:

    -   Selecione os grupos de computadores nos quais pretende implementar a nova regra e, em seguida, escolha **Adicionar**.

    -   Para especificar um prazo de instalação para as atualizações, selecione a caixa de verificação **Impor um prazo de instalação para estas atualizações** e, em seguida, na lista **Prazo de instalação**, selecione o prazo de instalação.

        > [!NOTE]
        > Se especificar um prazo de instalação, o computador gerido pode exigir que reinicie uma ou mais vezes após ter passado o intervalo do prazo.

    -   Quando terminar, escolha **Seguinte**.

7.  Na página **Resumo**, reveja as definições da nova regra e, em seguida, escolha **Concluir**.

A nova regra é apresentada na secção **Regras de Aprovação Automática** da página **Definições de Serviço: Atualizações**.

> [!NOTE]
> Quando cria uma regra de aprovação automática, esta só aprova atualizações futuras e não aprova automaticamente atualizações já existentes no Intune. Para aprovar estas atualizações tem de executar a regra de aprovação automática.


### <a name="to-edit-run-or-delete-an-automatically-approved-update-rule"></a>Para editar, executar ou eliminar uma regra de atualização aprovada automaticamente

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Admin**&gt;**Atualizações**.

2.  Na secção **Regras de Aprovação Automática**, selecione uma regra e, em seguida, efetue um dos seguintes:

    -   Para editar a regra, escolha **Editar** e, em seguida, altere os parâmetros da regra no **Assistente de Atualização da Regra de Aprovação Automática**.

    -   Para executar a regra, escolha **Executar Seleção**.

    -   Para eliminar a regra, escolha **Eliminar**.

        > [!NOTE]
        > Eliminar uma regra não afeta atualizações anteriores que foram aprovadas pela regra eliminada.

## <a name="update-software-not-made-by-microsoft"></a>Atualizar software que não foi criado pela Microsoft
Pode implementar atualizações para software que não foi criado pela Microsoft. Pode fazê-lo ao utilizar o assistente **Carregar Atualização** para colocar a atualização no espaço de Armazenamento na Cloud; após isso pode aprovar ou recusar a atualização tal como com software Microsoft.

### <a name="to-upload-and-configure-a-third-party-update"></a>Para carregar e configurar uma atualização de outros fornecedores que não a Microsoft

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Atualizações** &gt; **Descrição Geral** &gt; **Carregar**.

2.  Na página **Ficheiros de atualização**, escolha **Procurar** para selecionar os ficheiros de configuração necessários para instalar o pacote de atualizações. O ficheiro pode ser um ficheiro do Windows Installer (.msi), um ficheiro do Windows Installer Patch (.msp) ou um ficheiro de programa .exe. Também pode incluir ficheiros ou pastas adicionais que estejam na mesma pasta que o ficheiro de configuração.

    É apresentado o tamanho total dos ficheiros selecionados para carregar. Tenha em atenção que este tamanho não inclui os tamanhos expandidos ou descomprimidos de ficheiros de instalação.

3.  Após especificar os ficheiros de configuração, a página **Descrição da atualização** apresenta o nome, a descrição e a classificação das informações do software que o Intune extraiu dos ficheiros de configuração do software. Pode selecionar uma classificação para identificar o tipo de atualização que está a implementar (Atualizações, Atualizações Críticas, Atualizações de Segurança, Coletânea de Atualizações ou Service Packs). Escolha **Seguinte** quando terminar.

4.  Na página **Requisitos** do assistente, selecione a arquitetura (32 bits, 64 bits ou ambos) e os sistemas operativos dos computadores geridos para os quais esta aplicação será aplicável.

5.  Na página **Regras de deteção**, especifique como o Intune determina se a atualização já existe em computadores geridos. Se utilizar a opção predefinida, **Utilizar as regras de deteção predefinidas**, o Intune instala sempre o pacote de atualizações uma vez em cada computador visado.

    > [!NOTE]
    > Se o ficheiro de configuração da atualização que especificou for um ficheiro do Windows Installer ou .msp, a página **Regras de deteção** do assistente não é apresentada. Isto deve-se ao facto de os ficheiros do Windows Installer e .msp incluírem as suas próprias instruções para detetar instalações de atualizações anteriores.

    Selecione uma ou mais das seguintes regras para determinar se a atualização já está instalada nos computadores geridos:

    -   **O ficheiro existe**

    -   **O código de produto MSI existe**

    -   **A chave do registo existe**

6.  Forneça as informações adicionais necessárias para configurar a regra de deteção, como o caminho e nome do ficheiro, o código de produto do Windows Installer ou uma chave do registo e, em seguida, escolha **Seguinte**.

7.  Na página **Pré-requisitos** do assistente, especifique o software que já tem de estar instalado antes de esta atualização poder ser instalada. Pode especificar **Nenhum**, selecionar um pacote de software que já tenha sido adicionado e seja gerido pelo Intune ou pode especificar as seguintes regras para descrever o software:

    -   **O ficheiro existe**

    -   **O código de produto MSI existe**

    -   **A chave do registo existe**

8.  Forneça as informações adicionais necessárias para configurar a regra de deteção, como o caminho e o nome do ficheiro, o código de produto do Windows Installer ou uma chave do registo e, em seguida, escolha **Seguinte**.

9. Na página **Argumentos da linha de comandos** do assistente, pode adicionar as propriedades da instalação necessárias à linha de comandos de instalação para modificar o comportamento do ficheiro de configuração. Por exemplo, algum software suporta a propriedade **/q** para ativar a instalação automática. Consulte a documentação do seu pacote de software para saber mais sobre argumentos da linha de comandos suportados. Especifique os argumentos da linha de comandos de que precisa e, em seguida, escolha **Seguinte**.

    > [!NOTE]
    > Se a atualização não suportar a instalação automática, não pode instalar a atualização através do Intune

10. Na página **Códigos de retorno** do assistente, pode especificar como os códigos de retorno da instalação da atualização são interpretados. Por predefinição, o Intune utiliza códigos de retorno de norma da indústria para comunicar uma instalação falhada ou com êxito de um pacote de atualizações. Os códigos de retorno fornecidos são:

|Código de retorno|Detalhes|
|---------------|------------------|
|**0**|Êxito|
|**3010**|Êxito ao reiniciar|

11. Qualquer código de retorno não indicado é considerado uma falha.
Algumas atualizações utilizam interpretações não padrão de códigos de retorno. Neste caso, pode especificar as suas próprias interpretações do código de retorno.

12. Especifique ou edite os códigos de retorno necessários e, em seguida, escolha **Seguinte**.

13. Na página **Resumo** do assistente, reveja as medidas que serão tomadas e, em seguida, escolha **Carregar** para concluir o assistente.

A atualização carregada é armazenada no armazenamento na cloud do Intune. Se não tiver espaço livre suficiente para carregar o pacote de atualizações, será notificado do facto durante o processo de carregamento. O Intune não consegue determinar se existe espaço livre suficiente até o carregamento das atualizações ser iniciado, porque os ficheiros de configuração e de instalação comprimidos necessitam de mais espaço quando são descomprimidos.

Após ser carregada para Intune, é apresentada uma atualização de software de terceiros na área de trabalho **Atualizações** no painel **Todas as Atualizações**. Em seguida, pode aprovar e implementar a atualização. Para obter mais informações, consulte a secção seguinte "Aprovar e recusar atualizações".

## <a name="approve-and-decline-updates"></a>Aprovar e recusar atualizações
Quando as instalações estão prontas para serem instaladas, é apresentada uma mensagem na página **Descrição Geral das Atualizações** da área de trabalho **Atualizações**, em **Estado da Atualização**. Escolha esta mensagem para abrir a página **Todas as Atualizações**, para ver que atualizações estão prontas para aprovação.

Pode utilizar a lista **Filtros** para encontrar atualizações mais facilmente. Por exemplo, pode apresentar apenas atualizações que falharam ou atualizações ultrapassadas.

Quando seleciona uma atualização da lista, são disponibilizados mais comandos que permitem gerir atualizações conforme apresentado na seguinte tabela:

|Tarefa|Detalhes|
|--------|--------------------|
|**Ver Propriedades**|Apresenta informações detalhadas sobre a atualização, incluindo o número de computadores para os quais é aplicável.|
|**Editar**|Apenas para atualizações de outros fornecedores que não a Microsoft. Permite-lhe editar as propriedades da atualização.|
|**Aprovar**|Aprova a atualização selecionada e permite-lhe configurar em que grupos será implementada. Para obter mais informações, consulte o procedimento **Aprovar atualizações** neste tópico.|
|**Recusar**|Remove aprovações anteriores da atualização e oculta a atualização das vistas predefinidas. Além disso, os dados do relatório da atualização serão removidos.<br /><br />Se, posteriormente, pretender localizar uma atualização recusada, defina o filtro na página **Todas as Atualizações** para **Recusada**. Em seguida, pode aprovar esta atualização conforme necessário.<br /><br />Se uma atualização foi recusada porque a atualização expirou no Microsoft Update, essa atualização não pode ser aprovada na consola de administração do Intune.<br /><br />Se eliminar uma política de atualizações implementada em computadores, os valores dessas definições de política de atualizações são repostos para o estado predefinido no sistema operativo instalado nos computadores.|
|**Eliminar**|Apenas para atualizações de outros fornecedores que não a Microsoft. Elimina a atualização selecionada.|
|**Carregar**|Inicia o assistente **Carregar Atualização** que permite carregar atualizações de outros fornecedores que não a Microsoft que pretende implementar.|

### <a name="to-approve-updates"></a>Para aprovar atualizações

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Atualizações** &gt; **Descrição Geral** &gt; **Novas atualizações a aprovar**.

    Na área de trabalho **Atualizações**, escolha **Descrição Geral** &gt; **Novas atualizações a aprovar**.

    > [!NOTE]
    > A ligação **Novas atualizações a aprovar** é apresentada na área **Estado das Atualizações** apenas quando existe, pelo menos, um computador gerido que precisa que uma atualização seja aprovada.

2.  Selecione uma atualização, reveja as propriedades da atualização na parte inferior da página para garantir que pretende aprovar a atualização e, em seguida, escolha **Aprovar**. Pode selecionar múltiplas atualizações ao premir a tecla **CTRL** à medida que seleciona cada item.

3.  Na página **Selecionar Grupos**, selecione um grupo no qual pretenda implementar as atualizações e, em seguida, escolha **Adicionar**. Quando terminar de especificar os grupos, escolha **Seguinte**.

4.  Na página **Ação de Implementação**, efetue o seguinte para cada grupo na lista:

    -   Na lista **Aprovação**, selecione um dos seguintes:

        -   **Instalação Necessária** - Instala a atualização em computadores no grupo especificado.

        -   **Não Instalar** - Comunica apenas a aplicabilidade e não instala a atualização.

        -   **Instalação Disponível** - o utilizador pode instalar a aplicação a pedido a partir do Portal da Empresa.

        -   **Desinstalar** - Remove as atualizações de computadores no grupo visado.

            > [!IMPORTANT]
            > A atualização é removida mesmo que não tenha sido instalada pelo Intune.

    -   Na lista **Prazo**, selecione um dos seguintes:

        -   **Nenhum** - Indica que não é imposto um prazo para a instalação da atualização e os utilizadores podem recusar a atualização continuamente.

        -   **Logo que possível** - Instala a atualização na próxima oportunidade em computadores visados.

        -   **Personalizado** - Especifica a data e a hora em que são instaladas atualizações aprovadas.

        -   **Uma semana**, **Duas semanas**, **Um mês** - instala a atualização num período de tempo específico.

5.  Escolha **Concluir** para guardar as definições ou **Cancelar** para eliminar as definições e voltar para a lista de atualizações.

    > [!IMPORTANT]
    > A menos que a ação **Não Instalar**, **Instalação Necessária**ou **Desinstalar** tenha sido configurada explicitamente para um grupo subordinado, uma ação configurada para um grupo principal é herdada pelos respetivos grupos subordinados.

6.  Pode verificar o painel de detalhes na parte inferior da página **Todas as Atualizações** para mensagens de lembrete sobre a atualização.


### <a name="see-also"></a>Consulte também
[Políticas para proteger PCs Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)
