---
title: Instalar o software de cliente de PCs
description: Utilize este guia para ajudá-lo a gerir os PCs Windows através do software de cliente do Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
ms.date: 07/13/2017
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4dd9fc00475c8a8eea28bef2150f25639ac38e15
ms.sourcegitcommit: ede86a3cb094c12e3e218b956abb9935bec76902
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/05/2019
ms.locfileid: "67572604"
---
# <a name="install-the-intune-software-client-on-windows-pcs"></a>Instalar o software de cliente do Intune em PCs Windows

[!INCLUDE [classic-portal](includes/classic-portal.md)]

> [!NOTE]
> Pode utilizar o Microsoft Intune para gerir PCs com Windows [como dispositivos móveis com a gestão de dispositivos móveis (MDM)](windows-enroll.md) ou como computadores com o cliente de software do Intune, conforme descrito abaixo. No entanto, a Microsoft recomenda que os clientes [utilizem a solução de gestão MDM](windows-enroll.md) sempre que possível. Para obter mais informações consulte [comparar a gestão de Windows PCs como computadores ou dispositivos móveis](pc-management-comparison.md) 


Os PCs Windows podem ser inscritos instalando o software de cliente do Intune. O software de cliente do Intune pode ser instalado através dos seguintes métodos:

- Pelo administrador de TI, com recurso a um dos seguintes métodos: instalação manual, Política de Grupo ou da instalação incluída numa imagem de disco

- Pelos utilizadores finais, que instalam manualmente o software de cliente

O software de cliente do Intune contém o software mínimo necessário para inscrever o PC na gestão do Intune. Após um PC ter sido inscrito, o software de cliente do Intune transfere todo o software de cliente necessário para efetuar a gestão de PCs.

Esta série de transferências reduz o impacto sobre a largura de banda da rede e minimiza o tempo necessário para efetuar a inscrição inicial do PC no Intune. Também garante que, após a conclusão da segunda transferência, o cliente tem o software mais recente disponível.

Uma licença do Intune permite a instalação do software de cliente do Intune em até cinco PCs.

## <a name="download-the-intune-client-software"></a>Transferir o software de cliente do Intune

Todos os métodos mencionados, com exceção daqueles em que os utilizadores instalam o software de cliente do Intune manualmente, exigem que os administradores de TI transfiram primeiro o software, de modo a que este possa ser implementado posteriormente para os utilizadores finais.

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), clique em **Admin (Administrador)** &gt; **Client Software Download (Transferir Software de Cliente)** .

   ![Transferir o cliente de PC do Intune](./media/https://docs.microsoft.com/intune/media/install-the-windows-pc-client/pc-sa-client-download.png)

2. Na página **Client Software Download (Transferência de Software de Cliente)** , clique em **Client Software Download (Transferir Software de Cliente)** . Em seguida, guarde o pacote **Microsoft_Intune_Setup.zip** que contém o software numa localização segura na sua rede.

   O pacote de instalação do software de cliente do Intune contém informações exclusivas e específicas sobre a sua conta, disponíveis num certificado incorporado. Se existirem utilizadores não autorizados que consigam obter acesso ao pacote de instalação, estes poderão inscrever PCs na conta representada pelo certificado incorporado e poderão obter acesso a recursos da empresa.

3. Extraia os conteúdos do pacote de instalação para uma localização segura na sua rede.

    > [!IMPORTANT]
    > Não mude o nome ou remova o ficheiro **ACCOUNTCERT** que é extraído ou a instalação de software de cliente falhará.

## <a name="deploy-the-client-software-manually"></a>Implementar o software de cliente manualmente

Nos computadores onde pretende instalar o software de cliente, aceda à pasta onde se encontram os ficheiros de instalação do software de cliente. Em seguida, execute **Microsoft_Intune_Setup.exe** para instalar o software de cliente.

> [!NOTE]
> O estado da instalação é apresentado quando paira o rato sobre o ícone na barra de tarefas no PC cliente.

## <a name="deploy-the-client-software-by-using-group-policy"></a>Implementar o software de cliente com uma Política de Grupo

1. Na pasta que contém os ficheiros**Microsoft_Intune_Setup.exe** e **MicrosoftIntune.accountcert**, execute o seguinte comando para extrair os programas de instalação baseados no Windows Installer para computadores de 32 bits e 64 bits:

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2. Copie os ficheiros **Microsoft_Intune_x86.msi**, **Microsoft_Intune_x64.msi** e **MicrosoftIntune.accountcert** para uma localização de rede que possa ser acedida por todos os computadores nos quais irá instalar o software de cliente.

    > [!IMPORTANT]
    > Não separe ou mude o nome dos ficheiros ou a instalação do software de cliente falhará.

3. Utilize a Política de Grupo para implementar software nos computadores na sua rede.

    Para obter mais informações sobre como utilizar a Política de Grupo para implementar software automaticamente, veja [Group Policy for Beginners (Política de Grupos para Principiantes)](https://technet.microsoft.com/library/hh147307.aspx).

## <a name="deploy-the-client-software-as-part-of-an-image"></a>Implementar o software de cliente como parte de uma imagem
Pode implementar o software de cliente do Intune em computadores como parte de uma imagem de sistema operativo, ao utilizar o seguinte procedimento como guia:

1. Copie os ficheiros de instalação do cliente, **Microsoft_Intune_Setup.exe** e **MicrosoftIntune.accountcert**, para a pasta **%Systemdrive%\Temp\Microsoft_Intune_Setup** no computador de referência.

2. Crie a entrada de registo **WindowsIntuneEnrollPending** ao adicionar o seguinte comando ao script **SetupComplete.cmd** :

    ```
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3. Adicione o seguinte comando ao **setupcomplete.cmd** para executar o pacote de inscrição com o argumento da linha de comandos /PrepareEnroll:

    ```
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```
    > [!TIP]
    > O script **SetupComplete.cmd** permite à Configuração do Windows efetuar modificações ao sistema antes de o utilizador iniciar sessão. O argumento da linha de comandos **/PrepareEnroll** prepara um computador de destino para ser inscrito automaticamente no Intune após a Configuração do Windows ser concluída.

4. Coloque o**SetupComplete.cmd** na pasta **%Windir%\Setup\Scripts** no computador de referência.

5. Capture uma imagem do computador de referência e, em seguida, efetue a implementação nos computadores visados.

    Quando o computador de destino reiniciar no final da Configuração do Windows, é criada a chave de registo **WindowsIntuneEnrollPending**. O pacote de inscrição verifica se o computador está inscrito. Se o computador estiver inscrito, não é necessária mais nenhuma ação. Se o computador não estiver inscrito, o pacote de inscrição cria uma Tarefa de Inscrição Automática do Microsoft Intune.

    Quando a tarefa de inscrição automática for executada na próxima hora agendada, verifica a existência do valor de registo **WindowsIntuneEnrollPending** e tenta inscrever o PC de destino no Intune. Se a inscrição falhar por alguma razão, é repetida da próxima vez que a tarefa for executada. As repetições serão efetuadas durante um mês.

    A Tarefa de Inscrição Automática do Intune, o valor de registo **WindowsIntuneEnrollPending** e o certificado de conta serão eliminados do computador de destino quando a inscrição for bem-sucedida ou após um mês (o que ocorrer primeiro).

## <a name="instruct-users-to-self-enroll"></a>Dar instruções aos utilizadores para se inscreverem

Os utilizadores devem instalar o software de cliente do Intune ao aceder ao [site do Portal da Empresa](https://portal.manage.microsoft.com). As informações exatas que os utilizadores veem no portal Web variam consoante a Autoridade MDM e a plataforma/versão do SO do PC do utilizador.

Se não tiver sido atribuída uma licença do Intune aos utilizadores ou se a Autoridade MDM da organização não tiver sido definida como o Intune, não serão apresentadas quaisquer opções de inscrição aos utilizadores.

Se tiver sido atribuída uma licença do Intune aos utilizadores e a Autoridade MDM da organização tiver sido definida como o Intune:

- Os utilizadores que tiverem PCs com o Windows 7 ou o Windows 8 verão APENAS a opção para se inscreverem no Intune ao transferir e instalar o software de cliente do PC que é exclusivo da sua organização.

- Os utilizadores que tiverem PCs com o Windows 10 ou o Windows 8.1 verão duas opções de inscrição:

  - **Inscrever o PC como um dispositivo móvel**: Os usuários escolhem a **encontrar horizontalmente o método de inscrição** botão e será direcionado para obter instruções sobre como inscrever o PC como um dispositivo móvel. Este botão é apresentado em destaque, dado que a inscrição MDM é considerada a opção de inscrição predefinida e preferida. No entanto, a opção de inscrição MDM não se aplica a este tópico, que abrange apenas a instalação de software de cliente.
  - **Inscrever o PC com o software de cliente do Intune**: Terá de dizer aos utilizadores para selecionar o **clique aqui para transferi-la** link, que direcionará a instalação de software de cliente.

A seguinte tabela apresenta um resumo das opções.

  ![Opções de inscrição predefinidas por plataforma](./media/install-the-windows-pc-client/default-enrollment-options-table.png)

As seguintes capturas de ecrã mostram aquilo que os utilizadores veem ao inscrever os seus dispositivos com o software de cliente.

Inicialmente, será pedido aos utilizadores para identificarem ou inscreverem o seu dispositivo.

  ![identificar ou inscrever o dispositivo](./media/install-the-windows-pc-client/identify-device-or-enroll.png)

Para que os seus utilizadores possam instalar o software de cliente do PC, terá de indicar-lhes que selecionem a ligação **Clique aqui para transferir**, que permite aos utilizadores que transfiram o software de cliente do PC e guia os mesmos ao longo do processo de instalação. O botão **Find out how to enroll (Saiba como inscrever-se)** direciona os utilizadores a um conjunto de documentação sobre como inscrever dispositivos através da inscrição MDM, a qual não é relevante para as instruções deste software de cliente.

  ![selecione a ligação Clique aqui para transferir](./media/install-the-windows-pc-client/enroll-your-windows-device.png)

Quando os utilizadores clicam na ligação é-lhes apresentado o botão **Download Software (Transferir Software)** , o qual devem selecionar para iniciar a instalação do software de cliente do PC.

  ![selecione o botão Download Software (Transferir Software)](./media/install-the-windows-pc-client/download-pc-client-software.png)

Em seguida, é pedido aos utilizadores que iniciem sessão com as credenciais da sua empresa.

  ![Inicie sessão com as suas credenciais](./media/install-the-windows-pc-client/sign-in-to-intune.png)

Os utilizadores serão direcionados para a página de Boas-vindas para proceder à instalação.

  ![Página de boas-vindas da instalação do cliente do PC](./media/install-the-windows-pc-client/welcome-to-pc-agent-install-wizard.png)

Os utilizadores devem selecionar **Seguinte** para iniciar a instalação.

  ![Página de boas-vindas da instalação do cliente do PC](./media/install-the-windows-pc-client/welcome-to-pc-agent-install-wizard.png)

Quando a instalação estiver concluída, os utilizadores devem selecionar **Concluir**.

  ![Conclua a instalação do cliente do PC](./media/install-the-windows-pc-client/completed-the-setup-wizard.png)

Se os utilizadores tentarem inscrever o PC como um dispositivo móvel após o terem inscrito através do cliente de software de PC do Intune, verão o seguinte ecrã de erro.

  ![Ecrã que é apresentado se o PC já estiver inscrito](./media/install-the-windows-pc-client/page-shown-if-pc-already-enrolled.png)

## <a name="monitor-and-validate-successful-client-deployment"></a>Monitorizar e validar implementações de cliente com êxito
Utilize um dos seguintes procedimentos para ajudá-lo a monitorizar e a validar implementações de cliente com êxito.

### <a name="to-verify-the-installation-of-the-client-software-from-the-microsoft-intune-administrator-console"></a>Para verificar a instalação do software de cliente a partir da consola do administrador do Microsoft Intune

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), clique em **Groups (Grupos)** &gt; **All Devices (Todos os Dispositivos)** &gt; **All Computers (Todos os Computadores)** .

2. Na lista, localize os computadores que estão a comunicar com o Intune ou procure um computador gerido específico ao escrever o nome do computador (ou qualquer parte do nome) na caixa **Search devices (Procurar dispositivos)** .

3. Analise o estado do computador no painel inferior da consola. Resolva os erros existentes.

### <a name="to-create-a-computer-inventory-report-to-display-all-enrolled-computers"></a>Para criar um relatório de inventário de computadores para apresentar todos os computadores inscritos

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), clique em **Reports (Relatórios)** &gt; **Computer Inventory Reports (Relatórios de Inventário de Computadores)** .

2. Na página **Create New Report (Criar Novo Relatório)** , deixe os valores predefinidos em todos os campos (exceto se quiser aplicar filtros) e, em seguida, clique em **View Report (Ver Relatório)** .

3. A página **Relatório de Inventário de Computadores** é aberta numa nova janela que apresenta todos os computadores inscritos com êxito no Intune.

    > [!TIP]
    > Clique em qualquer cabeçalho de coluna no relatório para ordenar a lista pelos conteúdos dessa coluna.

## <a name="uninstall-the-windows-client-software"></a>Desinstalar o cliente de software do Windows

Existem duas formas de anular a inscrição do software de cliente do Windows:

- A partir da consola de administração do Intune (método recomendado)
- A partir de uma linha de comandos no cliente

### <a name="unenroll-by-using-the-intune-admin-console"></a>Anular a inscrição através da consola de administração do Intune

Para anular a inscrição do software de cliente através da consola de administração do Intune, aceda a **Grupos** > **Todos os Computadores** > **Dispositivos**. Clique com o botão direito do rato no cliente e selecione **Extinguir/Limpar**.

### <a name="unenroll-by-using-a-command-prompt-on-the-client"></a>Anular a inscrição através de uma linha de comandos no cliente

Numa linha de comandos elevada, execute um dos seguintes comandos.

**Método 1**:

    "C:\Program Files\Microsoft\OnlineManagement\Common\ProvisioningUtil.exe" /UninstallAgents /MicrosoftIntune

**Método 2**: tenha em atenção que todos estes agentes se encontram instalados em todos os SKUs do Windows:

    wmic product where name="Microsoft Endpoint Protection Management Components" call uninstall
    wmic product where name="Microsoft Intune Notification Service" call uninstall
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall
    wmic product where name="Microsoft Online Management Policy Agent" call uninstall
    wmic product where name="Microsoft Policy Platform" call uninstall
    wmic product where name="Microsoft Security Client" call uninstall
    wmic product where name="Microsoft Online Management Client" call uninstall
    wmic product where name="Microsoft Online Management Client Service" call uninstall
    wmic product where name="Microsoft Easy Assist v2" call uninstall
    wmic product where name="Microsoft Intune Monitoring Agent" call uninstall
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall
    wmic product where name="Windows Firewall Configuration Provider" call uninstall
    wmic product where name="Microsoft Intune Center" call uninstall
    wmic product where name="Microsoft Online Management Update Manager" call uninstall
    wmic product where name="Microsoft Online Management Agent Installer" call uninstall
    wmic product where name="Microsoft Intune" call uninstall
    wmic product where name="Windows Endpoint Protection Management Components" call uninstall
    wmic product where name="Windows Intune Notification Service" call uninstall
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall
    wmic product where name="Windows Online Management Policy Agent" call uninstall
    wmic product where name="Windows Policy Platform" call uninstall
    wmic product where name="Windows Security Client" call uninstall
    wmic product where name="Windows Online Management Client" call uninstall
    wmic product where name="Windows Online Management Client Service" call uninstall
    wmic product where name="Windows Easy Assist v2" call uninstall
    wmic product where name="Windows Intune Monitoring Agent" call uninstall
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall
    wmic product where name="Windows Firewall Configuration Provider" call uninstall
    wmic product where name="Windows Intune Center" call uninstall
    wmic product where name="Windows Online Management Update Manager" call uninstall
    wmic product where name="Windows Online Management Agent Installer" call uninstall
    wmic product where name="Windows Intune" call uninstall

> [!TIP]
> A anulação da inscrição do cliente irá gerar um registo obsoleto no lado do servidor relativamente ao cliente afetado. A anulação da inscrição é um processo assíncrono e existem nove agentes a desinstalar, pelo que poderá demorar até 30 minutos a ser concluída.

### <a name="check-the-unenrollment-status"></a>Verificar o estado da anulação da inscrição

Verifique o caminho "%ProgramFiles%\Microsoft\OnlineManagement" e certifique-se de que são apresentados apenas os seguintes diretórios à esquerda:

- AgentInstaller
- Logs
- Updates
- Common

### <a name="remove-the-onlinemanagement-folder"></a>Remover a pasta OnlineManagement

O processo de anulação da inscrição não remove a pasta OnlineManagement. Aguarde 30 minutos após a desinstalação e, em seguida, execute este comando. Se o executar demasiado cedo, a desinstalação poderá apresentar um estado desconhecido. Para remover a pasta, inicie uma linha de comandos elevada e execute:

    "rd /s /q %ProgramFiles%\Microsoft\OnlineManagement".

### <a name="next-steps"></a>Passos Seguintes
[Tarefas de gestão comuns de PCs Windows com o cliente de software do Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
