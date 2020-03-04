---
title: Adicione e atribua aplicações Win32 ao Microsoft Intune
titleSuffix: ''
description: Saiba como adicionar, atribuir e gerir aplicações Win32 com o Microsoft Intune. Este tópico inclui uma descrição geral das funcionalidades de gestão e da entrega de aplicações Win32 do Intune, bem como informações de resolução de problemas com aplicações Win32.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 516d5148ac44d72aaacf1d670d2d4f0345823d49
ms.sourcegitcommit: 6608dc70d01376e0cd90aa620a2fe01337f6a2f1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260287"
---
# <a name="intune-standalone---win32-app-management"></a>Intune Autónomo - Gestão de aplicações Win32

[Intune autónoma](../fundamentals/mdm-authority-set.md) agora permite maiores capacidades de gestão de aplicações Win32. Embora seja possível para clientes ligados à cloud utilizarem o Configuration Manager para a gestão de aplicações Win32, os clientes exclusivos do Intune terão melhores funcionalidades de gestão para as suas aplicações Win32 de linha de negócio (LOB). Este tópico fornece uma descrição geral da funcionalidade de gestão de aplicações Win32 do Intune e informações de resolução de problemas.

> [!NOTE]
> Esta capacidade de gestão de aplicações suporta a arquitetura do sistema operativo de 32 bits e 64 bits para aplicações Windows.

> [!IMPORTANT]
> Ao implementar aplicações Win32, considere utilizar a [Intune Management Extension](../apps/intune-management-extension.md) exclusivamente, especialmente quando tiver um instalador de aplicações Win32 multi-ficheiros. Se misturar a instalação de aplicações Win32 e aplicações de linha de negócio durante a inscrição no AutoPilot, a instalação da aplicação poderá falhar.  

## <a name="prerequisites"></a>Pré-requisitos

Para utilizar a gestão de aplicações Win32, certifique-se de que cumpre os seguintes critérios:

- Windows 10 versão 1607 ou posterior (versões Enterprise, Pro e Education)
- O cliente do Windows 10 tem de estar: 
  - Os dispositivos devem ser unidos à Azure AD e inscritos automaticamente. A extensão de gestão Intune suporta a AD Azure, domínio híbrido aderido, dispositivos matriculados na política do grupo são suportados. 
  > [!NOTE]
  > Para o cenário de inscrição na política do grupo - O utilizador final utiliza a conta de utilizador local para a AAD juntar-se ao seu dispositivo Windows 10. O utilizador deve iniciar sessão no dispositivo utilizando a sua conta de utilizador AAD e inscrever-se no Intune. A Intune instalará a extensão Intune Management no dispositivo se um script PowerShell ou uma aplicação Win32 fordirecionado para o utilizador ou dispositivo.
- O tamanho da aplicação do Windows está limitado a 8 GB por aplicação.

## <a name="prepare-the-win32-app-content-for-upload"></a>Preparar o conteúdo da aplicação Win32 para carregamento

Utilize a Ferramenta de Preparação de [Conteúdo microsoft Win32](https://go.microsoft.com/fwlink/?linkid=2065730) para pré-processar as aplicações do Windows Classic (Win32). A ferramenta converte ficheiros de instalação de aplicação no formato *.intunewin.* A ferramenta também deteta alguns dos atributos exigidos por Intune para determinar o estado de instalação da aplicação. Depois de utilizar esta ferramenta na pasta do instalador de aplicações, poderá criar uma aplicação Win32 na consola Intune.

> [!IMPORTANT]
> A Ferramenta de Preparação de [Conteúdo microsoft Win32](https://go.microsoft.com/fwlink/?linkid=2065730) fecha todos os ficheiros e subpastas quando cria o ficheiro *.intunewin.* Certifique-se de manter a Ferramenta de Preparação de Conteúdo microsoft Win32 separada dos ficheiros e pastas do instalador, para que não inclua a ferramenta ou outros ficheiros e pastas desnecessários no ficheiro *.intunewin.*

Pode descarregar a Ferramenta de Preparação de [Conteúdo microsoft Win32](https://go.microsoft.com/fwlink/?linkid=2065730) do GitHub como ficheiro zip. O ficheiro zipped contém uma pasta chamada **Microsoft-Win32-Content-Prep-Tool-master**. A pasta contém a ferramenta de preparação, a licença, um readme e as notas de lançamento. 

### <a name="process-flow-to-create-intunewin-file"></a>Fluxo de processo para criar ficheiro .intunewin

   <img alt="Process flow to create a .intunewin file" src="./media/apps-win32-app-management/prepare-win32-app.svg" width="700">

### <a name="run-the-microsoft-win32-content-prep-tool"></a>Executar a ferramenta de preparação de conteúdo microsoft Win32

Se executar `IntuneWinAppUtil.exe` da janela de comando sem parâmetros, a ferramenta irá guiá-lo para inserir os parâmetros necessários passo a passo. Ou, pode adicionar os parâmetros ao comando com base nos seguintes parâmetros disponíveis da linha de comando.

### <a name="available-command-line-parameters"></a>Parâmetros da linha de comandos disponíveis 

|    **Parâmetro da linha de comandos**    |    **Descrição**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    Ajuda    |
|    `-c <setup_folder>`     |    Pasta para todos os ficheiros de configuração. Todos os ficheiros desta pasta serão comprimidos para o ficheiro *.intunewin.*    |
|    `-s <setup_file>`     |    Ficheiro de configuração (como *setup.exe* ou *setup.msi*).    |
|    `-o <output_folder>`     |    Pasta de saída para o ficheiro *.intunewin* gerado.    |
|    `-q`       |    Modo silencioso    |

### <a name="example-commands"></a>Comandos de exemplo

|    **Comando de exemplo**    |    **Descrição**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    Este comando mostra informações de utilização da ferramenta.    |
|    `IntuneWinAppUtil -c c:\testapp\v1.0 -s c:\testapp\v1.0\setup.exe -o c:\testappoutput\v1.0 -q`    |    Este comando irá gerar o ficheiro `.intunewin` a partir da pasta de origem especificada e do ficheiro de configuração. Para o ficheiro de configuração MSI, esta ferramenta irá obter as informações necessárias para o Intune. Se `-q` for especificado, o comando será executado no modo silencioso e, se o ficheiro de saída já existir, será substituído. Além disso, se a pasta de saída não existir, será criada automaticamente.    |

Ao gerar um ficheiro *.intunewin,* coloque quaisquer ficheiros necessários para se referir numa subpasta da pasta de configuração. Em seguida, use um caminho relativo para fazer referência ao ficheiro específico de que necessita. Por exemplo:

**Configurar pasta de origem:** *c:\testapp\v1.0*<br>
**Ficheiro de licença:** *c:\testapp\v1.0\licenses\license.txt*

Consulte o ficheiro *license.txt* utilizando as *licenças relativas de caminho\license.txt*.

## <a name="create-assign-and-monitor-a-win32-app"></a>Criar, atribuir e monitorizar uma aplicação Win32

Tal como uma aplicação de linha de negócio (LOB), pode adicionar uma aplicação Win32 ao Microsoft Intune. Este tipo de aplicação é, normalmente, escrita internamente ou por terceiros. 

### <a name="process-flow-to-add-a-win32-app-to-intune"></a>Fluxo de processo para adicionar uma app Win32 ao Intune

<img alt="Process flow to add a Win32 app to Intune" src="./media/apps-win32-app-management/add-win32-app.svg" width="500">

### <a name="add-a-win32-app-to-intune"></a>Adicione uma aplicação Win32 ao Intune

Os seguintes passos fornecem orientação para ajudá-lo a adicionar uma aplicação Windows ao Intune.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações** > **Adicionar**.
3. No painel do **tipo select,** sob os **outros** tipos de aplicações, selecione **a aplicação Windows (Win32)** .

    > [!IMPORTANT]
    > Certifique-se de que utiliza a versão mais recente da Ferramenta de Preparação de Conteúdo do Microsoft Win32. Se não utilizar a versão mais recente, verá um aviso indicando que a aplicação foi embalada utilizando uma versão mais antiga da Ferramenta de Preparação de Conteúdo do Microsoft Win32. 

4. Clique em **Selecionar**. Os passos da **aplicação Add** são apresentados.

## <a name="step-1---app-information"></a>Passo 1 - Informações sobre aplicativos

### <a name="select-the-app-package-file"></a>Selecione o ficheiro de pacote de aplicativos

1. No painel de **aplicações Adicionar,** clique em Selecionar o ficheiro de pacote de **aplicativos**. 
2. No painel **Ficheiro de pacote de aplicação**, selecione o botão Procurar. Em seguida, selecione um ficheiro de instalação do Windows com a extensão *.intunewin*.
   Os detalhes da aplicação serão apresentados.
3. Quando terminar, selecione **OK** no painel de ficheiros do **pacote app.**

### <a name="set-app-information"></a>Definir informações de aplicativos

1. Na página de informações da **App,** adicione os detalhes para a sua aplicação. Consoante a aplicação que tenha escolhido, alguns dos valores neste painel podem ser preenchidos automaticamente.
    - **Nome**: introduza o nome da aplicação tal como aparece no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só aparece uma das aplicações no portal da empresa.
    - **Descrição**: introduza a descrição da aplicação. A descrição aparece no portal da empresa.
    - **Publicador**: introduza o nome do publicador da aplicação.
    - **Categoria**: selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. As categorias permitem que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Mostre isto como uma aplicação em destaque no Portal da Empresa**: Mostrar a aplicação em destaque na página principal do portal da empresa quando os utilizadores navegam para apps.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL aparece no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL aparece no portal da empresa.
    - **Programador**: opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário**: opcionalmente, introduza o nome do proprietário desta aplicação. Por exemplo, **Departamento de RH**.
    - **Notas**: introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: carregue um ícone associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
2. Clique em **Seguir** para exibir a página **do Programa.**

## <a name="step-2-program"></a>Passo 2: Programa

1. Na página **programa,** configure os comandos de instalação e remoção da aplicação para a aplicação:
    - **Instale o comando**: Adicione a linha de comando de instalação completa para instalar a aplicação. 

        Por exemplo, se o nome do ficheiro da sua aplicação for **MyApp123,** adicione o seguinte:<br>
        `msiexec /p “MyApp123.msp”`<p>
        E, se a aplicação for `ApplicationName.exe`, o comando seria o nome da aplicação seguido pelos argumentos de comando (switches) suportados pelo pacote. <br>Por exemplo:<br>
        `ApplicationName.exe /quiet`<br>
        No comando acima, o pacote de `ApplicationName.exe` suporta o argumento de comando `/quiet`.<p> 
        Para obter os argumentos específicos suportados pelo pacote de aplicações, contacte o seu fornecedor de aplicações.

    - **Desinstalar**o comando : Adicione a linha de comando desinstalação completa para desinstalar a aplicação com base no GUID da aplicação. 

        Por exemplo: `msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    - **Instalar o comportamento**: Desloque o comportamento de instalação para qualquer **sistema** ou **utilizador**.

        > [!NOTE]
        > Pode configurar uma aplicação Win32 para que esta seja instalada no contexto de **Utilizador** ou **Sistema**. O contexto de **Utilizador** refere-se apenas a um determinado utilizador. O contexto de **Sistema** refere-se a todos os utilizadores de um dispositivo com o Windows 10.
        >
        > Os utilizadores finais não necessitam de ter sessão iniciada no dispositivo para instalarem aplicações Win32.
        > 
        > A instalação e desinstalação da aplicação Win32 será executada sob privilégio administrativo (por padrão) quando a aplicação estiver definida para ser instalada no contexto do utilizador e o utilizador final do dispositivo tiver privilégios de administração.
    
    - **Comportamento de reinício**do dispositivo : Selecione uma das seguintes opções:
        - **Determine o comportamento com base nos códigos**de devolução : Escolha esta opção para reiniciar o dispositivo com base nos códigos de devolução.
        - **Nenhuma ação específica**: Escolha esta opção para suprimir o reinício do dispositivo durante a instalação de aplicações baseadas em MSI.
        - **A instalação da aplicação pode forçar o reinício**do dispositivo : Escolha esta opção para permitir que a instalação da aplicação esteja concluída sem suprimir o reinício.
        - **Intune forçará um reinício obrigatório**do dispositivo : Escolha esta opção para reiniciar sempre o dispositivo após uma instalação bem sucedida da aplicação.

    - **Especifique códigos de devolução para indicar o comportamento pós-instalação**: Adicione os códigos de devolução utilizados para especificar o comportamento de retry da instalação da aplicação ou o comportamento pós-instalação. As entradas de código de retorno são adicionadas por predefinição durante a criação de aplicações. No entanto, pode adicionar códigos de retorno adicionais ou alterar os códigos de retorno existentes.
        1. Na coluna **tipo Código,** desloque o **tipo código** para um dos seguintes:
            - **Falha –** O valor de devolução que indica uma falha na instalação da aplicação.
            - **Reinício total** – o código de retorno de reinício total não permite que as aplicações Win32 seguintes sejam instaladas no cliente sem reinício. 
            - **Reinício parcial** – o código de retorno de reinício parcial permite que a aplicação Win32 seguinte seja instalada sem a necessidade de um reinício de cliente. O reinício é necessário para concluir a instalação da aplicação atual.
            - **Tentar Novamente** – o agente de código de retorno de repetição irá tentar instalar a aplicação três vezes. Aguardará durante 5 minutos entre cada tentativa. 
            - **Bem Sucedido** – o valor de retorno que indica que a aplicação foi instalada com êxito.
        2. Se necessário, clique em **Adicionar** códigos de devolução adicionais ou modificar os códigos de devolução existentes.
2. Clique em **Seguir** para visualizar a página **Requisitos.**        

## <a name="step-3-requirements"></a>Passo 3: Requisitos

1. Na página **Requisitos,** especifique os requisitos que os dispositivos devem cumprir antes da instalação da aplicação:
    - **Arquitetura de sistema operativo**: selecione as arquiteturas necessárias para instalar a aplicação.
    - **Sistema operativo mínimo**: selecione o sistema operativo mínimo necessário para instalar a aplicação.
    - **Espaço em disco necessário (MB)** : opcionalmente, adicione o espaço livre em disco necessário na unidade do sistema para instalar a aplicação.
    - **Memória física necessária (MB)** : opcionalmente, adicione a memória física (RAM) necessária para instalar a aplicação.
    - **Número mínimo de processadores lógicos necessários**: opcionalmente, adicione o número mínimo de processadores lógicos necessários para instalar a aplicação.
    - **Velocidade de CPU mínima necessária (MHz)** : opcionalmente, adicione a velocidade mínima de CPU necessária para instalar a aplicação.
    - **Configure regras de requisitos adicionais:** 
        1. Clique em **Adicionar** para mostrar o painel de **regra Adicionar um Requisito** e configurar regras de requisitos adicionais. Selecione o **tipo Requisito** para escolher o tipo de regra que utilizará para determinar como um requisito é validado. As regras de requisitos podem basear-se em informações do sistema de ficheiros, valores de registo ou scripts PowerShell. 
            - **Ficheiro**: Quando escolher o **Ficheiro** como **o tipo Requisito,** a regra do requisito deve detetar um ficheiro ou pasta, data, versão ou tamanho. 
                - **Caminho** – o caminho completo da pasta que contém o ficheiro ou pasta a detetar.
                - **Ficheiro ou pasta** – o ficheiro ou pasta a detetar.
                - **Propriedade** – Selecione o tipo de regra utilizada para validar a presença da app.
                - **Associado a uma aplicação de 32 bits em clientes de 64 bits** – selecione **Sim** para expandir as variáveis de ambiente de caminho no contexto de 32 bits em clientes de 64 bits. Selecione **Não** (predefinição) para expandir as variáveis de caminho no contexto de 64 bits em clientes de 64 bits. Os clientes de 32 bits utilizarão sempre o contexto de 32 bits.
            - **Registo**: Quando escolher o **Registo** como **o tipo requisito,** a regra da exigência deve detetar uma definição de registo baseada no valor, cadeia, inteiro ou versão.
                - **Caminho da chave** – o caminho completo da entrada de registo que contém o valor a detetar.
                - **Nome do valor** – o nome do valor do registo a detetar. Se este valor estiver vazio, a deteção irá ocorrer na chave. O valor (predefinido) de uma chave será utilizado como valor de deteção, se o método de deteção for diferente da existência de ficheiro ou pasta.
                - **Requisito da chave** do registo – Selecione o tipo de comparação da chave de registo utilizada para determinar como a regra de requisito é validada.
                - **Associado a uma aplicação de 32 bits em clientes de 64 bits** – selecione **Sim** para procurar o registo de 32 bits em clientes de 64 bits. Selecione **Não** (predefinição) para procurar o registo de 64 bits em clientes de 64 bits. Os clientes de 32 bits irão sempre procurar o registo de 32 bits.
            - **Script**: Escolha o **Script** como **o tipo Requisito,** quando não conseguir criar uma regra de exigência baseada no ficheiro, no registo ou em qualquer outro método disponível na consola Intune.
                - **Script file** – Para a regra de requisito baseado no script PowerShell, se o código existente for 0, detetaremos o STDOUT com mais detalhes. Por exemplo, podemos detetar O DSTOUT como um inteiro que tem um valor de 1.
                - **Executar o script como processo de 32 bits em clientes de 64 bits** - Selecione **Sim** para executar o script num processo de 32 bits em clientes de 64 bits. Selecione **No** (padrão) para executar o script num processo de 64 bits em clientes de 64 bits. Clientes de 32 bits executam o guião num processo de 32 bits.
                - **Executar este script utilizando as credenciais registadas**: Selecione **Sim** para executar o script utilizando as credenciais do dispositivo**.
                - **Impor a verificação de assinatura do script** – selecione **Sim** para verificar se o script está assinado por um editor fidedigno, o que permitirá que o script seja executado sem avisos ou instruções apresentados. O script será executado desbloqueado. Selecione **Não** (predefinição) para executar o script com a confirmação do utilizador final sem verificação da assinatura.
                - **Selecione o tipo**de dados de saída : Selecione o tipo de dados utilizado ao determinar uma regra de requisito.
        2. Quando terminar de definir as regras de exigência, selecione **OK**.
2. Clique em **Seguir** para visualizar a página de regras de **Deteção.**   

## <a name="step-4-detection-rules"></a>Passo 4: Regras de deteção

1. Na página regras de **Deteção,** configure as regras para detetar a presença da aplicação:
    
    **Formato de regras**: Selecione como será detetada a presença da aplicação. Pode optar por configurar manualmente as regras de deteção ou utilizar um script personalizado para detetar a presença da aplicação. Tem de escolher, pelo menos, uma regra de deteção. 

    > [!NOTE]
    > No painel **Regras de deteção**, pode optar por adicionar múltiplas regras. As condições para **todas** as regras têm de ser cumpridas para detetar a aplicação.
    >
    > Se intune detetar que a aplicação não está presente no dispositivo, intune irá oferecer novamente a aplicação após 24 horas. Isto só ocorrerá para aplicações direcionadas com intenção necessária.

    - **Configurar regras de deteção manualmente** – pode selecionar um dos seguintes tipos de regra:
        1. **MSI** – verificar com base na verificação da versão MSI. Esta opção só pode ser adicionada uma vez. Ao escolher este tipo de regra, tem duas definições:
            - **Código de produto MSI** – adicione um código de produto MSI válido para a aplicação.
            - **Verificação de versão de produto MSI** – selecione **Sim** para verificar a versão de produto MSI além do código de produto MSI.
        2. **Ficheiro** – verifique com base na deteção do ficheiro ou pasta, data, versão ou tamanho.
            - **Caminho** – o caminho completo da pasta que contém o ficheiro ou pasta a detetar.
            - **Ficheiro ou pasta** – o ficheiro ou pasta a detetar.
            - **Método de deteção** – selecione o tipo de método de deteção utilizado para validar a presença da aplicação.
            - **Associado a uma aplicação de 32 bits em clientes de 64 bits** – selecione **Sim** para expandir as variáveis de ambiente de caminho no contexto de 32 bits em clientes de 64 bits. Selecione **Não** (predefinição) para expandir as variáveis de caminho no contexto de 64 bits em clientes de 64 bits. Os clientes de 32 bits utilizarão sempre o contexto de 32 bits.
            
            **Exemplos de deteção baseada em ficheiros**
            1. Verifique a existência do ficheiro.
         
                ![Captura de ecrã do painel de regras de deteção – existência do ficheiro](./media/apps-win32-app-management/apps-win32-app-03.png)
        
            2. Verifique a existência da pasta.
         
                ![Captura de ecrã do painel de regras de deteção – existência da pasta](./media/apps-win32-app-management/apps-win32-app-04.png)
        
        3. **Registo** – verifique com base no valor, cadeia de carateres, número inteiro ou versão.
            - **Caminho da chave** – o caminho completo da entrada de registo que contém o valor a detetar.
            - **Nome do valor** – o nome do valor do registo a detetar. Se este valor estiver vazio, a deteção irá ocorrer na chave. O valor (predefinido) de uma chave será utilizado como valor de deteção, se o método de deteção for diferente da existência de ficheiro ou pasta.
            - **Método de deteção** – selecione o tipo de método de deteção utilizado para validar a presença da aplicação.
            - **Associado a uma aplicação de 32 bits em clientes de 64 bits** – selecione **Sim** para procurar o registo de 32 bits em clientes de 64 bits. Selecione **Não** (predefinição) para procurar o registo de 64 bits em clientes de 64 bits. Os clientes de 32 bits irão sempre procurar o registo de 32 bits.
            
            **Exemplos de deteção baseada em registos**
            1. Verifique se existe uma chave de registo.
            
                ![Captura de ecrã do painel de regras de deteção – a chave de registo existe](./media/apps-win32-app-management/apps-win32-app-05.png)    
            
            2. Verifique se o valor do registo existe.
        
                ![Captura de ecrã do painel de regras de deteção – o valor de registo existe](./media/apps-win32-app-management/apps-win32-app-06.png)    
        
            3. Verifique a existência de uma cadeia de valor de registo idêntica.
        
                ![Captura de ecrã do painel de regras de deteção – cadeia de valor de registo idêntica](./media/apps-win32-app-management/apps-win32-app-07.png)    
     
    - **Utilizar um script de deteção personalizado** – especifique o script do PowerShell que será utilizado para detetar esta aplicação. 
    
       1. **Ficheiro de script** – selecione um script do PowerShell que irá detetar a presença da aplicação no cliente. A aplicação será detetada quando o script devolver um código de saída de valor 0 e escrever um valor de cadeia de carateres em STDOUT.

       2. **Executar o script como processo de 32 bits em clientes de 64 bits** - Selecione **Sim** para executar o script num processo de 32 bits em clientes de 64 bits. Selecione **No** (padrão) para executar o script num processo de 64 bits em clientes de 64 bits. Clientes de 32 bits executam o guião num processo de 32 bits.

       3. **Impor a verificação de assinatura do script** – selecione **Sim** para verificar se o script está assinado por um editor fidedigno, o que permitirá que o script seja executado sem avisos ou instruções apresentados. O script será executado desbloqueado. Selecione **Não** (predefinição) para executar o script com a confirmação do utilizador final sem verificação da assinatura.
    
            Agente intonizado verifica os resultados do guião. Lê os valores escritos pelo script no fluxo de saída padrão (STDOUT), no fluxo de erro padrão (STDERR) e no código de saída. Se a saída do script tiver um valor diferente de zero, o script falha e o estado de deteção de aplicação é Não instalada. Se o código de saída for zero e STDOUT tiver dados, o estado de deteção de aplicação é Instalada. 

            > [!NOTE]
            > A Microsoft recomenda codificar o seu script como UTF-8. Quando a saída do script tiver o valor de 0, a execução do script foi efetuada com êxito. O segundo canal de saída indica que foi detetada uma aplicação – os dados do STDOUT indicam que a aplicação foi encontrada no cliente. Não procuramos uma cadeia de carateres específica no STDOUT.

2. Depois de adicionar a sua regra(s), selecione **Next** para exibir a página **Dependencies.**

## <a name="step-5-dependencies"></a>Passo 5: Dependências

As dependências das aplicações são aplicações que devem ser instaladas antes da sua aplicação Win32 poder ser instalada. Pode exigir que outras aplicações sejam instaladas como dependências. Especificamente, o dispositivo deve instalar as aplicações dependentes antes de instalar a aplicação Win32. Há um máximo de 100 dependências, que inclui as dependências de quaisquer dependências incluídas, bem como a própria app. Só pode adicionar dependências de aplicações Win32 depois da sua aplicação Win32 ter sido adicionada e enviada para Intune. Uma vez adicionada a sua aplicação Win32, verá a opção **Dependencies** no painel para a sua aplicação Win32. 

Qualquer dependência de aplicações Win32 também precisa ser uma aplicação Win32. Não suporta dependendo de outros tipos de aplicações, tais como aplicações mSI LOB individuais ou aplicações de loja.

Ao adicionar uma dependência de aplicações, pode pesquisar com base no nome da aplicação e na editora. Além disso, pode classificar as suas dependências adicionais com base no nome da aplicação e no editor. As dependências de aplicações adicionadas anteriormente não podem ser selecionadas na lista de dependência de aplicações adicionadas. 

Pode escolher se instala ou não cada aplicação dependente automaticamente. Por predefinição, a opção de **instalação automática** está definida para **Sim** para cada dependência. Ao instalar automaticamente uma aplicação dependente, mesmo que a aplicação dependente não seja direcionada para o utilizador ou dispositivo, a Intune instalará a aplicação no dispositivo para satisfazer a dependência antes de instalar a sua aplicação Win32. É importante notar que uma dependência pode ter subdependências recursivas, e cada subdependência será instalada antes de instalar a dependência principal. Além disso, a instalação de dependências não segue uma ordem de instalação a um determinado nível de dependência.

### <a name="select-the-dependencies"></a>Selecione as dependências

Na página **Dependencies,** selecione aplicações que devem ser instaladas antes da aplicação Win32 poder ser instalada:
1. Clique em **Adicionar** para exibir o painel de **dependência adicionar.**
3. Depois de ter adicionado as aplicações dependentes, clique em **Selecionar**.
4. Escolha se instala automaticamente a aplicação dependente selecionando **Sim** ou **Não** sob a coluna **Instalar automaticamente.**
5. Clique em **Seguir** para exibir a página **de tags scope.**

### <a name="understand-additional-dependency-details"></a>Compreender detalhes adicionais de dependência

O utilizador final verá notificações do Windows Toast indicando que as aplicações dependentes estão a ser descarregadas e instaladas como parte do processo de instalação da aplicação Win32. Além disso, quando uma aplicação dependente não é instalada, o utilizador final verá geralmente uma das seguintes notificações:
- 1 ou mais aplicações dependentes não foram instaladas
- 1 ou mais requisitos de aplicação dependentes não cumpridos
- 1 ou mais aplicações dependentes estão pendentes de um reboot do dispositivo

Se optar por não **instalar automaticamente** uma dependência, a instalação da aplicação Win32 não será tentada. Além disso, o relatório de aplicações mostrará que a dependência foi sinalizada como `failed` e também fornecer uma razão de falha. Pode ver a falha de instalação da dependência clicando numa falha (ou aviso) fornecida nos detalhes de [instalação](troubleshoot-app-install.md#win32-app-installation-troubleshooting)da aplicação Win 32 . 

Cada dependência irá aderir à lógica de retry da aplicação Intune Win32 (tente instalar 3 vezes depois de esperar 5 minutos) e ao calendário global de reavaliação. Além disso, as dependências só são aplicáveis no momento da instalação da aplicação Win32 no dispositivo. As dependências não são aplicáveis para desinstalar uma aplicação Win32. Para eliminar uma dependência, deve clicar nas elipses (três pontos) à esquerda da app dependente localizada no final da linha da lista de dependência. 

## <a name="step-6---select-scope-tags-optional"></a>Passo 6 - Selecione etiquetas de âmbito (opcional)
Pode utilizar etiquetas de âmbito para determinar quem pode ver informações sobre aplicações do cliente no Intune. Para mais detalhes sobre etiquetas de âmbito, consulte [Use o controlo de acesso baseado em funções e as etiquetas](../fundamentals/scope-tags.md)de âmbito para TI distribuídos .

1. Clique em **Selecionar etiquetas** de âmbito para adicionar opcionalmente etiquetas de âmbito para a aplicação. 
2. Clique em **Seguir** para exibir a página **de Tarefas.**

## <a name="step-7---assignments"></a>Passo 7 - Atribuições

Pode selecionar as atribuições de grupo **necessárias**, **disponíveis para dispositivos matriculados**ou **desinstalar** as atribuições do grupo para a aplicação. Para mais informações, consulte [grupos Add para organizar utilizadores e dispositivos](~/fundamentals/groups-add.md) e [atribuir aplicações a grupos com](apps-deploy.md)o Microsoft Intune .

1. Para a aplicação específica, selecione um tipo de atribuição:
    - **Obrigatório**: a aplicação é instalada em dispositivos nos grupos selecionados.
    - **Disponível para dispositivos inscritos**: os utilizadores instalam a aplicação a partir da aplicação ou site Portal da Empresa.
    - **Desinstalar**: a aplicação é desinstalada dos dispositivos nos grupos selecionados.
2. Clique em **Adicionar grupo** e atribua os grupos que irão utilizar esta aplicação.
3. No painel select **grupos,** selecione para atribuir com base em utilizadores ou dispositivos. 
4. Depois de ter selecionado os seus grupos, também pode definir **as notificações finais do utilizador,** **disponibilidade**e prazo de **instalação.** Para mais informações, consulte a disponibilidade e notificações da [aplicação set Win32.](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications)
5. Se pretender excluir quaisquer grupos de utilizadores de serem afetados por esta atribuição de aplicações, selecione **Incluído** na coluna **MODE.** O painel de **atribuição editar** será exibido. Pode definir o **modo** de ser **incluído** para ser **excluído**. Clique **em OK** para fechar o painel de atribuição **editar.**
6. Depois de ter concluído a definição das atribuições para as aplicações, clique em **Next** para exibir a página **Review + criar.**

## <a name="step-8---review--create"></a>Passo 8 - Rever + criar

1. Reveja os valores e configurações que inseriu para a aplicação. Verifique se configura corretamente as informações da aplicação.
2. Quando terminar, clique em **Criar** para adicionar a app ao Intune.

    A lâmina **de visão geral** para a aplicação de linha de negócio seleção é apresentada.

Neste ponto, completou etapas para adicionar uma aplicação Win32 ao Intune. Para obter informações sobre a atribuição e monitorização de aplicações, veja [Atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md) e [Monitorizar informações e atribuições da aplicação com o Microsoft Intune](apps-monitor.md).

## <a name="delivery-optimization"></a>Otimização de Entrega

O Windows 10 1709 e os clientes acima vão descarregar o conteúdo da aplicação Intune Win32 utilizando um componente de otimização de entregas no cliente do Windows 10. A otimização da entrega fornece uma funcionalidade peer-to-peer que é ligada por padrão. A otimização da entrega pode ser configurada pela política do grupo e através da configuração do Dispositivo Intune. Para mais informações, consulte [otimização de entrega para o Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

> [!NOTE]
> Também pode instalar um servidor De Cache ligado ao Microsoft no seu Gestor de Configuração para cache O conteúdo da aplicação Intune Win32. Para mais informações, consulte o Microsoft Connected Cache no Gestor de [Configuração - Suporte para aplicações Intune Win32](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune).

## <a name="install-required-and-available-apps-on-devices"></a>Instalar aplicações necessárias e disponíveis em dispositivos

O utilizador final verá notificações do Windows Toast para as instalações de aplicações necessárias e disponíveis. A imagem seguinte mostra uma notificação de alerta de exemplo na qual a instalação da aplicação não é concluída até que o dispositivo seja reiniciado. 

![Screenshot de notificações de torradas do Windows para uma instalação de aplicação](./media/apps-win32-app-management/apps-win32-app-08.png)    

A imagem que se segue notifica o utilizador final de que estão a ser feitas alterações na aplicação no dispositivo.

![Screenshot notificando o utilizador de que estão a ser feitas alterações na aplicação](./media/apps-win32-app-management/apps-win32-app-09.png)    

Além disso, a aplicação Portal da Empresa mostra mensagens adicionais de estado de instalação de aplicações para utilizadores finais. As seguintes condições aplicam-se às características de dependência win32:
- A aplicação falhou na instalação. As dependências definidas pelo administrador não foram satisfeitas.
- A aplicação instalada com sucesso, mas requer um recomeço.
- A aplicação está em processo de instalação, mas requer um recomeço para continuar.

## <a name="set-win32-app-availability-and-notifications"></a>Definir disponibilidade e notificações de aplicações Win32
Pode configurar o tempo de início e prazo para uma aplicação Win32. Na hora de início, a extensão de gestão Intune iniciará o download e cache de conteúdo da aplicação para a intenção necessária. A aplicação será instalada no prazo limite. Para aplicações disponíveis, a hora de início ditará quando a aplicação for visível no Portal da Empresa e os conteúdos serão descarregados quando o utilizador final solicitar a aplicação do Portal da Empresa. Além disso, pode permitir um período de reinício da graça. 

Detete a disponibilidade da aplicação com base numa data e hora para uma aplicação necessária utilizando os seguintes passos:

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações.**
3. Selecione uma aplicação Windows existente **(Win32)** da lista. 
4. A partir do painel de aplicações, selecione **Propriedades** > **Editar** ao lado da secção **de Atribuição >** Adicionar **grupo** abaixo do tipo de atribuição **exigido.** 
   Note que a disponibilidade da aplicação pode ser definida com base no tipo de atribuição. O **tipo de Atribuição** pode ser **exigido,** **disponível para dispositivos matriculados,** ou **desinstalar**.
5. Selecione um grupo no painel do **grupo Select** para especificar qual o grupo de utilizadores que será atribuído à aplicação. 

    > [!NOTE]
    > **As** opções do tipo de atribuição incluíam as seguintes:<br>
    > - **Necessário**: Pode optar por **tornar esta aplicação necessária para todos os utilizadores** e/ou fazer com que esta **aplicação seja necessária em todos os dispositivos**.<br>
    > - **Disponível para dispositivos matriculados**: Pode optar por **disponibilizar esta aplicação a todos os utilizadores com dispositivos matriculados**.<br>
    > - **Desinstalar**: Pode optar por**desinstalar esta aplicação para todos os utilizadores** e/ou **desinstalar esta aplicação para todos os dispositivos**.

6. Para modificar as opções de notificação do **utilizador Final,** selecione **Mostrar todas as notificações**de torradas .
7. No painel de **atribuição editar,** detete as **notificações** do utilizador Ender para **mostrar todas as notificações**de torradas . Note que pode definir **notificações finais** do utilizador para mostrar todas as notificações de **torradas,** mostrar notificações de **torradas para reiniciar o computador**ou ocultar todas as notificações de **torradas**.
8. Detete a disponibilidade da **App** para **Uma data e hora específicas** e selecione a sua data e hora. Esta data e hora especifica quando a aplicação é descarregada para o dispositivo de utilizadores finais. 
9. Detete o prazo de **instalação** da App para **Uma data e hora específicas** e selecione a sua data e hora. Esta data e hora especifica quando a aplicação é instalada no dispositivo de utilizadores finais. Quando for feita mais de uma atribuição para o mesmo utilizador ou dispositivo, o prazo de instalação da aplicação é escolhido com base no mais cedo possível.

10. Clique **ativado** ao lado do período de **graça restart**. O período de graça de reinício começa assim que a instalação da aplicação estiver concluída no dispositivo. Quando desativado, o aparelho pode reiniciar sem aviso prévio. <br>Pode personalizar as seguintes opções:
    - Período de graça de reinício do **dispositivo (minutos)** : O valor predefinido é de 1440 minutos (24 horas). Este valor pode ser no máximo 2 semanas.
    - **Selecione quando deve visualizar a caixa de diálogo de contagem regressiva antes de o reinício ocorrer (minutos)** : O valor predefinido é de 15 minutos.
    - **Permitir que o utilizador ressone a notificação de reinício:** Pode escolher **Sim** ou **Não**.
        - **Selecione a duração do soneto (minutos)** : O valor predefinido é de 240 minutos (4 horas). O valor do soneca não pode ser mais do que reiniciar o período de graça.

11. Clique em **Rever + salvar**.

## <a name="toast-notifications-for-win32-apps"></a>Notificações de brindes para aplicações Win32 
Se necessário, pode suprimir a apresentação de notificações de torradas finais por aplicação. A partir de Intune, selecione **Apps** > **Todas as aplicações** > selecione a app > **Atribuições** > **Incluir Grupos.** 

> [!NOTE]
> As aplicações Win32 instaladas da extensão de gestão do Intune não serão desinstaladas em dispositivos não inscritos. Os administradores podem tirar partido da exclusão de atribuição para não oferecer aplicações Win32 em dispositivos BYOD.

## <a name="troubleshoot-win32-app-issues"></a>Resolver problemas relacionados com aplicações Win32
Os registos de agente no computador cliente encontram-se normalmente em `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Pode tirar partido de `CMTrace.exe` para ver estes ficheiros de registo. Para mais informações, consulte [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace).

![Screenshot dos registos do Agente na máquina cliente](./media/apps-win32-app-management/apps-win32-app-10.png)    

> [!IMPORTANT]
> Para permitir a instalação e execução adequadas das aplicações LOB Win32, as definições anti-malware devem excluir a digitalização dos seguintes diretórios:<p>
> **Nas máquinas de clientes X64:**<br>
> *C:\Ficheiros do programa (x86)\Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*
>  
> **Nas máquinas de clientes X86:**<br>
> *C:\Program Files\Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*

### <a name="detecting-the-win32-app-file-version-using-powershell"></a>Deteção da versão de ficheiro de aplicação Win32 usando powerShell

Se tiver dificuldade em detetar a versão de ficheiro sinuoso win32, considere utilizar ou modificar o seguinte comando PowerShell:

``` PowerShell

$FileVersion = [System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion
#The below line trims the spaces before and after the version name
$FileVersion = $FileVersion.Trim();
if ("<file version of successfully detected file>" -eq $FileVersion)
{
#Write the version to STDOUT by default
$FileVersion
exit 0
}
else
{
#Exit with non-zero failure code
exit 1
}
```

No comando PowerShell acima, substitua a cadeia `<path to binary file>` pelo caminho para o ficheiro da aplicação Win32. Um caminho de exemplo seria semelhante ao seguinte:<br>
`C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe`

Além disso, substitua a cadeia `<file version of successfully detected file>` pela versão do ficheiro que precisa de detetar. Uma cadeia de versão de ficheiro de exemplo seria semelhante à seguinte:<br>
`2019.0150.18118.00 ((SSMS_Rel).190420-0019)`

Se precisar de obter as informações da versão da sua aplicação Win32, pode utilizar o seguinte comando PowerShell:

``` PowerShell

[System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion

```

No comando powerShell acima, substitua `<path to binary file>` pelo seu caminho de ficheiro.

### <a name="additional-troubleshooting-areas-to-consider"></a>Áreas adicionais de resolução de problemas a considerar
- Verificar o direcionamento para garantir que o agente está instalado no dispositivo – uma aplicação Win32 direcionada para um grupo ou um Script do PowerShell direcionado para um grupo irá criar a política de instalação de agente para o grupo de segurança.
- Verificar a versão do SO – Windows 10 1607 e posterior.  
- Verificar a SKU do Windows 10 – o Windows 10 S ou versões do Windows em execução com o modo S ativado não suportam a instalação da MSI.

Para mais informações sobre a resolução de problemas das aplicações Win32, consulte a instalação de problemas de instalação da [aplicação Win32](troubleshoot-app-install.md#win32-app-installation-troubleshooting).

## <a name="next-steps"></a>Próximos passos

- Para obter mais informações sobre como adicionar aplicações ao Intune, veja [Adicionar aplicações ao Microsoft Intune](apps-add.md).
