---
# required metadata

title: Tarefas de gestão comuns do PC Windows | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: eb912c73-54d2-4d78-ac34-3cbe825804c7

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Tarefas de gestão comuns do PC Windows com o computador cliente do Microsoft Intune
Reveja as tarefas neste tópico para saber como gerir os computadores que executam o cliente do Intune. Se ainda não instalou o cliente nos seus computadores, consulte [Instalar o cliente do PC Windows com o Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md)


## Utilizar políticas para simplificar a gestão do PC
### Gerir a Firewall do Windows
As políticas simplificam a administração das definições da Firewall do Windows nos computadores geridos. Para obter mais informações, consulte [Ajudar a proteger PCs com o Windows a utilizarem políticas de Firewall do Windows no Microsoft Intune](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)

### Gerir o Centro do Microsoft Intune
O Centro do Microsoft Intune permite aos utilizadores:

-   Obter aplicações a partir do portal da empresa.

-   Procurar atualizações.

-   Gerir o Endpoint Protection do Microsoft Intune.

-   Pedir assistência remota.

O Centro do Microsoft Intune é instalado em todos os computadores geridos. Pode configurar as seguintes definições numa política do Intune e estas serão apresentadas aos utilizadores no Centro do Microsoft Intune:

|Definição de política|Detalhes|
|------------------|--------------------|
|**Nome**|O nome do administrador que gere o computador.<br /><br />Comprimento máximo: 40 carateres|
|**Número de telefone**|O número de telefone do administrador que gere o computador.<br /><br />Comprimento máximo: 20 carateres|
|**Endereço de e-mail**|O endereço de e-mail do administrador que gere o computador.<br /><br />Comprimento máximo: 40 carateres|
|**Nome do site**|O nome do seu site de suporte para utilizadores.<br /><br />Comprimento máximo: 40 carateres|
|**URL do site**|O URL do seu site de suporte.<br /><br />Comprimento máximo: 150 carateres|
|**Notas**|Uma nota que é apresentada aos utilizadores.<br /><br />Comprimento máximo: 120 carateres|

### Gerir definições de atualizações de software
Utilize as políticas para configurar as definições que os computadores geridos utilizam para procurar e transferir atualizações de software da Microsoft e de terceiros. Para mais informações, consulte [Manter os computadores com Windows atualizados com atualizações de software no Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)

### Gerir definições do Endpoint Protection
Utilize políticas para configurar definições do Endpoint Protection que irá depois implementar nos computadores geridos. Isto inclui o agendamento de análises, ações a efetuar quando é detetado software maligno, entre outros. Para mais informações, consulte [Ajude a proteger os PCs Windows com o Endpoint Protection para o Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)

## Ver o inventário de hardware e software
O Intune recolhe informações detalhadas sobre o hardware e o software de computadores geridos. Utilize as informações nos seguintes procedimentos para saber como criar:

-   Um relatório que lista as informações sobre as capacidades de hardware dos seus computadores.

-   Um relatório que lista o software instalado em cada computador.

-   Como atualizar o inventário de um computador para se certificar de que os dados do relatório estão atualizados.

### Para apresentar informações sobre os seus computadores

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Relatórios** &gt; **Relatórios de Inventário de Computadores**

2.  Na página **Criar Novo Relatório** , aceite os valores predefinidos ou personalize-os para filtrar os resultados que serão devolvidos pelo relatório. Por exemplo, pode selecionar apenas os computadores que executam o Windows 8.1 para serem apresentados no relatório.

3.  Escolha **Ver Relatório** para abrir o **Relatório de Inventários de Computadores** numa nova janela.

    Pode ordenar o relatório por qualquer uma das colunas, como **Nome**, **Tipo de Chassis** ou **Fabricante**, selecionando o cabeçalho de cada coluna.

### Para apresentar o software instalado nos seus computadores

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Relatórios** &gt; **Relatórios de Software Detetado**

2.  Na página **Criar Novo Relatório** , aceite os valores predefinidos ou personalize-os para filtrar os resultados que serão devolvidos pelo relatório. Por exemplo, pode selecionar para que apenas o software publicado pela Microsoft seja apresentado no relatório.

3.  Escolha **Ver Relatório** para abrir o **Relatório de Software Detetado** numa nova janela.

    Pode ordenar o relatório por qualquer uma das colunas, como **Nome**, **Publicador** ou **Categoria**, selecionando o cabeçalho de cada coluna. Pode expandir as atualizações na lista para mostrar mais detalhes (como os computadores em que estão instaladas) ao clicar na seta direcional junto ao item da lista.

### Para atualizar o inventário dos computadores e certificar-se de que está atualizado

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Grupos** &gt; **Todos os Dispositivos** (ou outro grupo que contenha o computador cujo inventário pretende atualizar).

2.  Selecione um computador ou prima se soltar a tecla **CTRL** para selecionar múltiplos computadores.

3.  Na barra de tarefas, escolha **Tarefas Remotas** &gt; **Atualizar Inventário**

4.  Para ver o estado da tarefa, escolha **Tarefas Remotas** no canto inferior direito da página.

    É apresentada a caixa de diálogo **Estado da Tarefa** , que mostra as tarefas remotas atuais, o estado das tarefas, o nome do dispositivo e todos os erros comunicados e fornece uma ligação para informações de resolução de problemas.


## Reiniciar um PC Windows remotamente

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Grupos** &gt; **Todos os Dispositivos** (ou outro grupo que contenha o computador que pretende reiniciar).

2.  Selecione um ou mais computadores e, em seguida, escolha **Tarefas Remotas** &gt; **Reiniciar o Computador**

3.  Para ver o estado da tarefa, escolha **Tarefas Remotas** no canto inferior direito da página.

4.  Na caixa de diálogo **Estado da Tarefa** , reveja as tarefas remotas atuais, os estados de tarefas, o nome do dispositivo e todos os erros comunicados.

## Extinguir um computador

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Grupos** &gt; **Todos os Dispositivos** (ou outro grupo que contenha o computador que pretende extinguir).

2.  Selecione os dispositivos que pretende extinguir e, em seguida, escolha **Extinguir/Limpar**

Para inscrever novamente um computador no Intune, reinstale o software de cliente no computador utilizando as informações do tópico [Instalar o cliente do PC Windows com o Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Se um computador não conseguir ligar ao Intune, é apresentada uma mensagem na área de trabalho **Dashboard**.

Quando extingue um computador:

-   Este é removido do inventário do Intune e a licença associada ao computador é disponibilizada para reutilização.

-   O estado do mesmo já não é apresentado na consola do Intune.

-   O Intune remove o software de cliente do computador. Se o computador não estiver ligado ao serviço Intune, o software de cliente será removido na próxima vez que for ligado.

-   O Endpoint Protection do Microsoft Intune é removido do computador. Se o computador tiver outra aplicação de ponto final instalada e esta estiver desativada, essa aplicação pode ser ativada novamente quando o Endpoint Protection do Microsoft Intune for removido, para garantir a proteção dos seus computadores.

-   Todas as políticas serão removidas do computador e os valores que estavam definidos pela política serão alterados.

-   O computador deixará de receber atualizações de software e atualizações de definições de software maligno do serviço Intune.

-   Dependendo de como estiverem configurados, os computadores extintos poderão continuar a receber atualizações ao utilizar os Windows Server Update Services, o Windows Update ou o Microsoft Update.

    > Se o software de cliente tiver sido instalado com um Objeto de Política de Grupo (GPO), tem de remover o Objeto de Política de Grupo (GPO) antes de poder remover o software de cliente, para impedir que o software seja reinstalado.

    Se o cliente não for desinstalado, leia [Resolução de problemas do Endpoint Protection](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune) para obter mais ajuda.

## Gerir a associação utilizador-dispositivo
Antes de poder implementar software para um utilizador, tem de associar o utilizador a um computador. Pode associar um utilizador a múltiplos computadores, mas cada computador só pode ser associado a um utilizador. Os utilizadores são automaticamente associados a qualquer computador que inscrevam no Intune através do portal da empresa.

### Para associar um utilizador a um computador

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Grupos** &gt; **Todos os Dispositivos** (ou outro grupo que contenha o computador que pretende associar a um utilizador).

2.  Selecione o computador que pretende associar a um utilizador e, em seguida, escolha **Associar Utilizador**

    A caixa de diálogo **Associar Utilizador** apresenta uma lista de utilizadores disponíveis com os respetivos nomes a apresentar, IDs de utilizador e o número de computadores a que cada utilizador está atualmente associado. Se um utilizador já estiver associado ao computador selecionado, o ID de utilizador e o nome desse utilizador serão apresentados em **Utilizador atual**. Se o computador não estiver associado a nenhum utilizador, o texto **Nenhum utilizador** aparecerá em **Utilizador Atual**

3.  Efetue uma das seguintes ações:

    -   Para deixar o computador associado ao utilizador atual, se existir um, escolha **Cancelar**

    -   Para remover a associação ao utilizador atual, se existir um, escolha **Remover ligação**&gt;**OK**

    -   Para associar o computador a um novo utilizador, selecione um utilizador na lista **Todos os utilizadores** . Confirme que os dados do utilizador estão corretos e, em seguida, escolha **OK**

> Se pretender restringir a capacidade dos próprios utilizadores finais se ligarem a computadores, ative a opção **Restringir a capacidade dos próprios utilizadores se ligarem a computadores** na política **Definições de Agente do Microsoft Intune**.

## Responder a um pedido de Assistência Remota
Os utilizadores podem pedir assistência com a Assistência Remota através do Microsoft Easy Assist, que é instalado automaticamente nos computadores geridos. Quando é feito um pedido, um alerta é apresentado na consola do Intune.

> A Assistência Remota não é suportada em computadores que executam o Windows 8 ou posterior.
>
> Se aceitar um pedido de Assistência Remota de um computador que não tem o Microsoft Easy Assist instalado, será pedido ao utilizador que o instale. O computador tem de ser reiniciado após a instalação. Pense em pré-carregar o Microsoft Easy Assist nos computadores dos seus utilizadores para evitar este reinício.

### Para gerir um pedido de Assistência Remota

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Alertas** &gt; **Assistência Remota**

2.  Selecione um pedido de Assistência Remota na lista **Alertas** para abrir a página de propriedades do pedido.

3.  Escolha **Aprovar o pedido e iniciar a Assistência Remota** para abrir uma caixa de diálogo que fornece opções para resolver o alerta.

4.  Efetue uma das seguintes ações:

    -   **Aceitar o pedido** - Para participar na sessão remota, escolha **Aceitar o pedido de Assistência Remota**

        O utilizador vê a mensagem: **O seu pedido foi aceite. Siga as instruções do Easy Assist para partilhar um programa ou o ambiente de trabalho com o seu administrador de sistema**

        > Não pode aceitar um pedido de assistência remota num computador Mac que esteja a executar a consola do administrador do Intune.

    -   **Recusar o pedido** - Feche a janela **Ver Informações de Resolução de Problemas** e, em seguida, escolha **Fechar Este Alerta** na janela de propriedades do alerta.

        O pedido será fechado e o utilizador verá uma mensagem a afirmar que o pedido foi recusado. Para pedir novamente Assistência Remota, o utilizador terá de enviar um novo pedido de Assistência Remota. Se fechar acidentalmente um alerta de Assistência Remota, contacte o utilizador que enviou o pedido de Assistência Remota e peça-lhe para enviar um novo pedido.


<!--HONumber=May16_HO2-->


