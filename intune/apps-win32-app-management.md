---
title: Adicionar aplicações Win32 ao Microsoft Intune
titlesuffix: ''
description: Saiba como adicionar, fornecer e gerir aplicações de Win32 com o Microsoft Intune. Este tópico inclui uma descrição geral das funcionalidades de gestão e da entrega de aplicações Win32 do Intune, bem como informações de resolução de problemas com aplicações Win32.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 6e8a74763f29707aa3e774be52f7b383b040ec1e
ms.sourcegitcommit: b93db06ba435555f5b126f97890931484372fcfb
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/04/2018
ms.locfileid: "52829152"
---
# <a name="intune-standalone---win32-app-management-public-preview"></a>Intune Autónomo – gestão de aplicações Win32 (Pré-visualização Pública)

O Intune autónomo permitirá aceder a melhores funcionalidades de gestão de aplicações Win32. Embora seja possível para clientes ligados à cloud utilizarem o Configuration Manager para a gestão de aplicações Win32, os clientes exclusivos do Intune terão melhores funcionalidades de gestão para as suas aplicações Win32 de linha de negócio (LOB). Este tópico fornece uma descrição geral da funcionalidade de gestão de aplicações Win32 do Intune e informações de resolução de problemas.

## <a name="prerequisites-for-public-preview"></a>Pré-requisitos para a pré-visualização pública

- Windows 10 versão 1607 ou posteriores (versões Enterprise, Pro e Education)
- O cliente do Windows 10 tem de estar: 
    - associado ao Azure Active Directory (AAD) ou Azure Active Directory Híbrido e
    - inscrito no Intune (gerido pela MDM)
- O tamanho da aplicação Windows está limitado a 8 GB por aplicação na pré-visualização pública 

## <a name="prepare-the-win32-app-content-for-upload"></a>Preparar o conteúdo da aplicação Win32 para carregamento

Utilize a [Microsoft Intune Win32 App Upload Prep Tool](https://github.com/Microsoft/Intune-Win32-App-Packaging-Tool) (Ferramenta de Preparação para Carregamento de Aplicações Win32 no Microsoft Intune) para processar previamente as aplicações Win32. A ferramenta de empacotamento converte os ficheiros de instalação da aplicação no formato *.intunewin*. A ferramenta de empacotamento também deteta alguns dos atributos exigidos pelo Intune para determinar o estado de instalação da aplicação. Depois de utilizar esta ferramenta na pasta do instalador da aplicação, poderá criar uma aplicação Win32 na consola do Intune.

Pode transferir a [Microsoft Intune Win32 App Upload Prep Tool](https://github.com/Microsoft/Intune-Win32-App-Packaging-Tool) (Ferramenta de Preparação para Carregamento da Aplicação Win32 no Microsoft Intune) do GitHub.

### <a name="available-command-line-parameters"></a>Parâmetros da linha de comandos disponíveis 

|    **Parâmetro da linha de comandos**    |    **Descrição**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    Ajuda    |
|    `-c <setup_folder>`     |    A pasta de configuração para todos os ficheiros de configuração.    |
|   ` -s <setup_file>`     |    Ficheiro de configuração (como *setup.exe* ou *setup.msi*).    |
|    `-o <output_folder>`     |    Pasta de saída para o ficheiro *.intunewin* gerado.    |
|    `-q`       |    Modo silencioso    |

### <a name="example-commands"></a>Comandos de exemplo

|    **Comando de exemplo**    |    **Descrição**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    Este comando mostra informações de utilização da ferramenta.    |
|    `IntuneWinAppUtil -c <setup_folder> -s <source_setup_file> -o <output_folder> <-q>`    |    Este comando irá gerar o ficheiro `.intunewin` a partir da pasta de origem especificada e do ficheiro de configuração. Para o ficheiro de configuração MSI, esta ferramenta irá obter as informações necessárias para o Intune. Se `-q` for especificado, o comando será executado no modo silencioso e, se o ficheiro de saída já existir, será substituído. Além disso, se a pasta de saída não existir, será criada automaticamente.    |

Ao gerar uma *.intunewin* arquivo, colocar todos os ficheiros tem de referenciar numa subpasta da pasta de configuração. Em seguida, utilize um caminho relativo para referenciar o ficheiro específico, que precisa. Por exemplo:

**Pasta de origem de configuração:** *c:\testapp\v1.0*<br>
**Ficheiro de licença:** *c:\testapp\v1.0\licenses\license.txt*

Consulte a *license.txt* ficheiro ao utilizar o caminho relativo *licenses\license.txt*.

## <a name="create-assign-and-monitor-a-win32-app"></a>Criar, atribuir e monitorizar uma aplicação Win32

Tal como uma aplicação de linha de negócio (LOB), pode adicionar uma aplicação Win32 ao Microsoft Intune. Este tipo de aplicação é, normalmente, escrita internamente ou por terceiros. Os seguintes passos fornecem orientação para ajudá-lo a adicionar uma aplicação Windows ao Intune.

### <a name="step-1-specify-the-software-setup-file"></a>Passo 1: especificar o ficheiro de configuração do software

1.  Inicie sessão no [portal do Azure](https://portal.azure.com/).
2.  Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3.  No painel **Intune**, selecione **Aplicações do cliente** > **Aplicações** > **Adicionar**.
4.  No painel **Adicionar aplicação**, selecione **Aplicação do Windows (Win32) - pré-visualização** na lista pendente fornecida.

    ![Captura de ecrã Adicionar aplicação – caixa de lista pendente Adicionar tipo](./media/apps-win32-app-01.png)

### <a name="step-2-upload-the-app-package-file"></a>Passo 2: carregar o ficheiro de pacote de aplicação

1.  No painel **Adicionar aplicação**, selecione **Ficheiro de pacote de aplicação** para selecionar um ficheiro. O painel Ficheiro de pacote de aplicação será apresentado.

    ![Captura de ecrã do ficheiro de pacote de aplicação](./media/apps-win32-app-02.png)

2.  No painel **Ficheiro de pacote de aplicação**, selecione o botão Procurar. Em seguida, selecione um ficheiro de instalação do Windows com a extensão *.intunewin*.
3.  Quando tiver terminado, selecione **OK**.

### <a name="step-3-configure-app-information"></a>Passo 3: configurar as informações da aplicação

1.  No painel **Adicionar aplicação**, selecione **Informações da aplicação** para configurar a aplicação.
2.  No painel **Informações da aplicação**, configure as seguintes informações. Alguns dos valores neste painel podem ser preenchidos automaticamente.
    - **Nome**: introduza o nome da aplicação tal como aparece no portal da empresa. Se existir o mesmo nome de aplicação duas vezes, cada aplicação irá aparecer no portal da empresa.
    - **Descrição**: introduza uma descrição para a aplicação. A descrição aparece no portal da empresa.
    - **Publicador**: introduza o nome do fabricante da aplicação.
    - **Categoria**: selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. As categorias permitem que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar esta aplicação em destaque no Portal da Empresa**: apresente a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações**: opcionalmente, pode introduzir o URL para um site que contenha informações sobre a aplicação. O URL aparece no portal da empresa.
    - **URL de Privacidade**: opcionalmente, pode introduzir o URL para um site que contenha informações sobre a privacidade da aplicação. O URL aparece no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação. Por exemplo, **Departamento de RH**.
    - **Notas**: introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: carregue um ícone associado à aplicação. O ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
3.  Quando tiver terminado, selecione **OK**.

### <a name="step-4-configure-app-installation-details"></a>Passo 4: configurar os detalhes de instalação da aplicação
1.  No painel **Adicionar aplicação**, selecione **Programa** para configurar a instalação da aplicação e os comandos de remoção da aplicação.
2.  Adicione a linha de comandos de instalação completa para instalar a aplicação. 

    Por exemplo, se o nome de ficheiro da aplicação for **MyApp123**, adicione o seguinte: `msiexec /i “MyApp123.msi”`

3.  Adicione a linha de comandos de desinstalação completa para desinstalar a aplicação com base no GUID da aplicação. 

    Por exemplo: `msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    > [!NOTE]
    > Pode configurar uma aplicação Win32 para que esta seja instalada no contexto de **Utilizador** ou **Sistema**. O contexto de **Utilizador** refere-se apenas a um determinado utilizador. O contexto de **Sistema** refere-se a todos os utilizadores de um dispositivo com o Windows 10.
    >
    > Os utilizadores finais não necessitam de ter sessão iniciada no dispositivo para instalarem aplicações Win32.

4.  Quando tiver terminado, selecione **OK**.

### <a name="step-5-configure-app-requirements"></a>Passo 5: configurar os requisitos da aplicação

1.  No painel **Adicionar aplicação**, selecione **Requisitos** para configurar os requisitos que os dispositivos têm de cumprir antes de a aplicação ser instalada.
2.  No painel **Requisitos**, configure as seguintes informações. Alguns dos valores neste painel podem ser preenchidos automaticamente.
    - **Arquitetura de sistema operativo**: selecione as arquiteturas necessárias para instalar a aplicação.
    - **Sistema operativo mínimo**: selecione o sistema operativo mínimo necessário para instalar a aplicação.
    - **Espaço em disco necessário (MB)**: opcionalmente, adicione o espaço livre em disco necessário na unidade do sistema para instalar a aplicação.
    - **Memória física necessária (MB)**: opcionalmente, adicione a memória física (RAM) necessária para instalar a aplicação.
    - **Número mínimo de processadores lógicos necessários**: opcionalmente, adicione o número mínimo de processadores lógicos necessários para instalar a aplicação.
    - **Velocidade de CPU mínima necessária (MHz)**: opcionalmente, adicione a velocidade mínima de CPU necessária para instalar a aplicação.
3.  Quando tiver terminado, selecione **OK**.

### <a name="step-6-configure-app-detection-rules"></a>Passo 6: configurar as regras de deteção da aplicação

1.  No painel **Adicionar aplicação**, selecione **Regras de deteção** para configurar as regras para detetar a presença da aplicação.
2.  No campo **Formato de regras**, selecione a forma como a presença da aplicação será detetada. Pode optar por configurar manualmente as regras de deteção ou utilizar um script personalizado para detetar a presença da aplicação. Tem de escolher, pelo menos, uma regra de deteção. 

    > [!NOTE]
    > No painel **Regras de deteção**, pode optar por adicionar múltiplas regras. As condições para **todas** as regras têm de ser cumpridas para detetar a aplicação.

    - **Configurar regras de deteção manualmente** – pode selecionar um dos seguintes tipos de regra:
        1.  **MSI** – verificar com base na verificação da versão MSI. Esta opção só pode ser adicionada uma vez. Ao escolher este tipo de regra, tem duas definições:
            - **Código de produto MSI** – adicione um código de produto MSI válido para a aplicação.
            - **Verificação de versão de produto MSI** – selecione **Sim** para verificar a versão de produto MSI além do código de produto MSI.
        2.  **Ficheiro** – verifique com base na deteção do ficheiro ou pasta, data, versão ou tamanho.
            - **Caminho** – o caminho completo da pasta que contém o ficheiro ou pasta a detetar.
            - **Ficheiro ou pasta** – o ficheiro ou pasta a detetar.
            - **Método de deteção** – selecione o tipo de método de deteção utilizado para validar a presença da aplicação.
            - **Associado a uma aplicação de 32 bits em clientes de 64 bits** – selecione **Sim** para expandir as variáveis de ambiente de caminho no contexto de 32 bits em clientes de 64 bits. Selecione **Não** (predefinição) para expandir as variáveis de caminho no contexto de 64 bits em clientes de 64 bits. Os clientes de 32 bits utilizarão sempre o contexto de 32 bits.
            
            **Exemplos de deteção baseada em ficheiros**
            1.  Verifique a existência do ficheiro.
         
                ![Captura de ecrã do painel de regras de deteção – existência do ficheiro](./media/apps-win32-app-03.png)
        
            2.  Verifique a existência da pasta.
         
                ![Captura de ecrã do painel de regras de deteção – existência da pasta](./media/apps-win32-app-04.png)
        
        3. **Registo** – verifique com base no valor, cadeia de carateres, número inteiro ou versão.
            - **Caminho da chave** – o caminho completo da entrada de registo que contém o valor a detetar.
            - **Nome do valor** – o nome do valor do registo a detetar. Se este valor estiver vazio, a deteção irá ocorrer na chave. O valor (predefinido) de uma chave será utilizado como valor de deteção, se o método de deteção for diferente da existência de ficheiro ou pasta.
            - **Método de deteção** – selecione o tipo de método de deteção utilizado para validar a presença da aplicação.
            - **Associado a uma aplicação de 32 bits em clientes de 64 bits** – selecione **Sim** para procurar o registo de 32 bits em clientes de 64 bits. Selecione **Não** (predefinição) para procurar o registo de 64 bits em clientes de 64 bits. Os clientes de 32 bits irão sempre procurar o registo de 32 bits.
            
            **Exemplos de deteção baseada em registos**
            1.  Verifique se existe uma chave de registo.
            
                ![Captura de ecrã do painel de regras de deteção – a chave de registo existe](./media/apps-win32-app-05.png)    
            
            2.  Verifique a existência do valor de registo (**não está disponível em pré-visualização**).
        
                ![Captura de ecrã do painel de regras de deteção – o valor de registo existe](./media/apps-win32-app-06.png)    
        
            3.  Verifique a existência de uma cadeia de valor de registo idêntica.
        
                ![Captura de ecrã do painel de regras de deteção – cadeia de valor de registo idêntica](./media/apps-win32-app-07.png)    
     
    - **Utilizar um script de deteção personalizado** – especifique o script do PowerShell que será utilizado para detetar esta aplicação. 
    
        1.  **Ficheiro de script** – selecione um script do PowerShell que irá detetar a presença da aplicação no cliente. A aplicação será detetada quando o script devolver um código de saída de valor 0 e escrever um valor de cadeia de carateres em STDOUT.
        2.  **Execute o script como um processo de 32 bits em clientes de 64 bits** - selecione **Sim** para executar o script com as credenciais de logon do usuário final. Selecione **Não** (predefinição) para executar o script no contexto do sistema.
        3.  **Impor a verificação de assinatura do script** – selecione **Sim** para verificar se o script está assinado por um editor fidedigno, o que permitirá que o script seja executado sem avisos ou instruções apresentados. O script será executado desbloqueado. Selecione **Não** (predefinição) para executar o script com a confirmação do utilizador final sem verificação da assinatura.
    
        O sidecar do Intune verifica os resultados do script. Lê os valores escritos pelo script no fluxo de saída padrão (STDOUT), no fluxo de erro padrão (STDERR) e no código de saída. Se a saída do script tiver um valor diferente de zero, o script falha e o estado de deteção de aplicação é Não instalada. Se o código de saída for zero e STDOUT tiver dados, o estado de deteção de aplicação é Instalada. 
    
        > [!NOTE]
        > Quando a saída do script tiver o valor de 0, a execução do script foi efetuada com êxito. O segundo canal de saída indica que foi detetada uma aplicação – os dados do STDOUT indicam que a aplicação foi encontrada no cliente. Não procuramos uma cadeia de carateres específica no STDOUT.
    
3.  Depois de adicionar a(s) regra(s), selecione **Adicionar** > **OK**.

### <a name="step-7-configure-app-return-codes"></a>Passo 7: configurar os códigos de retorno da aplicação

1.  No painel **Adicionar aplicação**, selecione **Códigos de retorno** para adicionar os códigos de retorno utilizados para especificar o comportamento de tentativa de instalação da aplicação ou o comportamento após a instalação. As entradas de código de retorno são adicionadas por predefinição durante a criação de aplicações. No entanto, pode adicionar códigos de retorno adicionais ou alterar os códigos de retorno existentes. 
2.  No painel **Códigos de retorno**, adicione códigos de retorno adicionais ou altere os códigos de retorno existentes.
    - **Falha ao** – o valor de retorno que indica uma falha de instalação da aplicação.
    - **Reinício total** – o código de retorno de reinício total não permite que as aplicações Win32 seguintes sejam instaladas no cliente sem reinício. 
    - **Reinício parcial** – o código de retorno de reinício parcial permite que a aplicação Win32 seguinte seja instalada sem a necessidade de um reinício de cliente. O reinício é necessário para concluir a instalação da aplicação atual.
    - **Tentar Novamente** – o agente de código de retorno de repetição irá tentar instalar a aplicação três vezes. Aguardará durante 5 minutos entre cada tentativa. 
    - **Bem Sucedido** – o valor de retorno que indica que a aplicação foi instalada com êxito.
3.  Selecione **OK** depois de adicionar ou alterar a lista de códigos de retorno.

### <a name="step-8-add-the-app"></a>Passo 8: adicionar a aplicação

1.  No painel **Adicionar aplicação**, verifique se configurou as informações da aplicação corretamente.
2.  Selecione **Adicionar** para carregar a aplicação para o Intune.

### <a name="step-9-assign-the-app"></a>Passo 9: atribuir a aplicação

1.  No painel da aplicação, selecione **Atribuições**.
2.  Selecione **Adicionar Grupo** para abrir o painel **Adicionar grupo** que está relacionado com a aplicação.
3.  Para a aplicação específica, selecione um **tipo de atribuição**:
    - **Disponível para dispositivos inscritos**: os utilizadores instalam a aplicação a partir da aplicação ou site Portal da Empresa.
    - **Obrigatório**: a aplicação é instalada em dispositivos nos grupos selecionados.
    - **Desinstalar**: a aplicação é desinstalada dos dispositivos nos grupos selecionados.
4.  Selecione **Grupos Incluídos** e atribua os grupos que irão utilizar esta aplicação.
5.  No painel **Atribuir**, selecione **OK** para concluir a seleção de grupos incluídos.
6.  Selecione **Excluir Grupos** se quiser excluir grupos de utilizadores de serem afetados por esta atribuição de aplicações.
7.  No painel **Adicionar grupo**, selecione **OK**.
8.  No painel **Atribuições** de aplicações, selecione **Guardar**.

Neste ponto, concluiu os passos para adicionar uma aplicação Win32 ao Intune. Para obter informações sobre a atribuição e monitorização de aplicações, veja [Atribuir aplicações a grupos com o Microsoft Intune](https://docs.microsoft.com/intune/apps-deploy) e [Monitorizar informações e atribuições da aplicação com o Microsoft Intune](https://docs.microsoft.com/intune/apps-monitor).

## <a name="delivery-optimization"></a>Otimização da entrega

Windows 10 RS3 e aos clientes acima irá transferir o conteúdo da aplicação Intune Win32 usando um componente de otimização de entrega no cliente Windows 10. Otimização da entrega fornece uma funcionalidade de ponto-a-ponto que ele está ativado por predefinição. Otimização da entrega pode ser configurada pela política de grupo e no futuro através de MDM do Intune. Para obter mais informações, consulte [otimização de entrega para o Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

## <a name="install-required-and-available-apps-on-devices"></a>Instalar aplicações necessárias e disponíveis em dispositivos

O utilizador final verá notificações de alerta do Windows para as instalações de aplicações necessário e disponível. A imagem seguinte mostra uma notificação de alerta de exemplo na qual a instalação da aplicação não é concluída até que o dispositivo seja reiniciado. 

![Exemplo de captura de ecrã das notificações de alerta do Windows para a instalação de uma aplicação](./media/apps-win32-app-08.png)    

A imagem seguinte notifica o utilizador final que as alterações da aplicação estão a ser efetuadas no dispositivo.

![Exemplo de captura de ecrã de notificar o utilizador final que estão a ser efetuadas alterações de aplicação no dispositivo](./media/apps-win32-app-09.png)    

## <a name="troubleshoot-win32-app-issues"></a>Resolver problemas relacionados com aplicações Win32
Os registos de agente no computador cliente encontram-se normalmente em `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Pode tirar partido de `CMTrace.exe` para ver estes ficheiros de registo. O *CMTrace.exe* pode ser transferido a partir das [Ferramentas de Cliente SCCM](https://docs.microsoft.com/sccm/core/support/tools). 

![Captura de ecrã dos registos de agente](./media/apps-win32-app-10.png)    

### <a name="troubleshooting-areas-to-consider"></a>Áreas de resolução de problemas a considerar
- Verificar o direcionamento para garantir que o agente está instalado no dispositivo – uma aplicação Win32 direcionada para um grupo ou um Script do PowerShell direcionado para um grupo irá criar a política de instalação de agente para o grupo de segurança.
- Verificar a versão do SO – Windows 10 1607 e posterior.  
- Verificar a SKU do Windows 10 – o Windows 10 S ou versões do Windows em execução com o modo S ativado não suportam a instalação da MSI.

## <a name="next-steps"></a>Passos Seguintes

- Para obter mais informações sobre como adicionar aplicações ao Intune, veja [Adicionar aplicações ao Microsoft Intune](apps-add.md).
