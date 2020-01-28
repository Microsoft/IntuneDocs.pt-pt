---
title: Adicionar e atribuir aplicativos Win32 ao Microsoft Intune
titleSuffix: ''
description: Saiba como adicionar, atribuir e gerenciar aplicativos Win32 com o Microsoft Intune. Este tópico inclui uma descrição geral das funcionalidades de gestão e da entrega de aplicações Win32 do Intune, bem como informações de resolução de problemas com aplicações Win32.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
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
ms.openlocfilehash: c120fab1da43230888866cba9d818d7b433b711e
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755294"
---
# <a name="intune-standalone---win32-app-management"></a>Intune autônomo-gerenciamento de aplicativos do Win32

O [Intune autônomo](../fundamentals/mdm-authority-set.md) agora permite um maior recurso de gerenciamento de aplicativos do Win32. Embora seja possível para clientes ligados à cloud utilizarem o Configuration Manager para a gestão de aplicações Win32, os clientes exclusivos do Intune terão melhores funcionalidades de gestão para as suas aplicações Win32 de linha de negócio (LOB). Este tópico fornece uma descrição geral da funcionalidade de gestão de aplicações Win32 do Intune e informações de resolução de problemas.

> [!NOTE]
> Essa funcionalidade de gerenciamento de aplicativo dá suporte à arquitetura do sistema operacional de 32 bits e 64 bits para aplicativos do Windows.

> [!IMPORTANT]
> Ao implantar aplicativos Win32, considere usar a [extensão de gerenciamento do Intune](../apps/intune-management-extension.md) exclusivamente, especialmente quando você tiver um instalador de aplicativo do Win32 com vários arquivos. Se você misturar a instalação de aplicativos Win32 e aplicativos de linha de negócios durante o registro do AutoPilot, a instalação do aplicativo poderá falhar.  

## <a name="prerequisites"></a>Pré-requisitos

Para usar o gerenciamento de aplicativos Win32, certifique-se de atender aos seguintes critérios:

- Windows 10 versão 1607 ou posterior (versões Enterprise, pro e Education)
- O cliente do Windows 10 tem de estar: 
  - Os dispositivos devem ser ingressados no Azure AD e registrados automaticamente. A extensão de gerenciamento do Intune dá suporte ao ingresso no Azure AD, dispositivos de diretiva de grupo ingressados no domínio híbrido. 
  > [!NOTE]
  > Para o cenário de política de grupo registrado-o usuário final usa a conta de usuário local para ingressar no AAD de seu dispositivo Windows 10. O usuário deve fazer logon no dispositivo usando sua conta de usuário do AAD e inscrever-se no Intune. O Intune instalará a extensão de gerenciamento do Intune no dispositivo se um script do PowerShell ou um aplicativo Win32 for direcionado para o usuário ou dispositivo.
- O tamanho do aplicativo do Windows é limitado a 8 GB por aplicativo.

## <a name="prepare-the-win32-app-content-for-upload"></a>Preparar o conteúdo da aplicação Win32 para carregamento

Use a [ferramenta de preparação de conteúdo do Microsoft Win32](https://go.microsoft.com/fwlink/?linkid=2065730) para pré-processar aplicativos clássicos (Win32) do Windows. A ferramenta converte os arquivos de instalação do aplicativo no formato *. intunewin* . A ferramenta também detecta alguns dos atributos exigidos pelo Intune para determinar o estado de instalação do aplicativo. Depois de usar essa ferramenta na pasta do instalador de aplicativos, você poderá criar um aplicativo Win32 no console do Intune.

> [!IMPORTANT]
> A [ferramenta de preparação de conteúdo do Microsoft Win32](https://go.microsoft.com/fwlink/?linkid=2065730) zips todos os arquivos e subpastas ao criar o arquivo *. intunewin* . Lembre-se de manter a ferramenta de preparação de conteúdo do Microsoft Win32 separada dos arquivos e pastas do instalador, para que você não inclua a ferramenta ou outros arquivos e pastas desnecessários no arquivo *. intunewin* .

Você pode baixar a [ferramenta de preparação de conteúdo do Microsoft Win32](https://go.microsoft.com/fwlink/?linkid=2065730) do GitHub como um arquivo zip. O arquivo compactado contém uma pasta chamada **Microsoft-Win32-Content-Prep-Tool-Master**. A pasta contém a ferramenta Prep, a licença, um Leiame e as notas de versão. 

### <a name="process-flow-to-create-intunewin-file"></a>Fluxo de processo para criar arquivo. intunewin

   <img alt="Process flow to create a .intunewin file" src="./media/apps-win32-app-management/prepare-win32-app.svg" width="700">

### <a name="run-the-microsoft-win32-content-prep-tool"></a>Executar a ferramenta de preparação de conteúdo do Microsoft Win32

Se você executar `IntuneWinAppUtil.exe` na janela de comando sem parâmetros, a ferramenta irá orientá-lo a inserir os parâmetros necessários passo a passo. Ou, você pode adicionar os parâmetros ao comando com base nos seguintes parâmetros de linha de comando disponíveis.

### <a name="available-command-line-parameters"></a>Parâmetros da linha de comandos disponíveis 

|    **Parâmetro da linha de comandos**    |    **Descrição**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    Ajuda    |
|    `-c <setup_folder>`     |    Pasta para todos os arquivos de instalação. Todos os arquivos nesta pasta serão compactados no arquivo *. intunewin* .    |
|    `-s <setup_file>`     |    Ficheiro de configuração (como *setup.exe* ou *setup.msi*).    |
|    `-o <output_folder>`     |    Pasta de saída para o ficheiro *.intunewin* gerado.    |
|    `-q`       |    Modo silencioso    |

### <a name="example-commands"></a>Comandos de exemplo

|    **Comando de exemplo**    |    **Descrição**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    Este comando mostra informações de utilização da ferramenta.    |
|    `IntuneWinAppUtil -c c:\testapp\v1.0 -s c:\testapp\v1.0\setup.exe -o c:\testappoutput\v1.0 -q`    |    Este comando irá gerar o ficheiro `.intunewin` a partir da pasta de origem especificada e do ficheiro de configuração. Para o ficheiro de configuração MSI, esta ferramenta irá obter as informações necessárias para o Intune. Se `-q` for especificado, o comando será executado no modo silencioso e, se o ficheiro de saída já existir, será substituído. Além disso, se a pasta de saída não existir, será criada automaticamente.    |

Ao gerar um arquivo *. intunewin* , coloque todos os arquivos necessários para fazer referência a uma subpasta da pasta de instalação do. Em seguida, use um caminho relativo para fazer referência ao arquivo específico que você precisa. Por exemplo:

**Pasta de origem da instalação:** *c:\testapp\v1.0*<br>
**Arquivo de licença:** *c:\testapp\v1.0\licenses\license.txt*

Consulte o arquivo *License. txt* usando o caminho relativo *licenses\license.txt*.

## <a name="create-assign-and-monitor-a-win32-app"></a>Criar, atribuir e monitorizar uma aplicação Win32

Tal como uma aplicação de linha de negócio (LOB), pode adicionar uma aplicação Win32 ao Microsoft Intune. Este tipo de aplicação é, normalmente, escrita internamente ou por terceiros. 

### <a name="process-flow-to-add-a-win32-app-to-intune"></a>Fluxo do processo para adicionar um aplicativo Win32 ao Intune

<img alt="Process flow to add a Win32 app to Intune" src="./media/apps-win32-app-management/add-win32-app.svg" width="500">

### <a name="add-a-win32-app-to-intune"></a>Adicionar um aplicativo Win32 ao Intune

Os seguintes passos fornecem orientação para ajudá-lo a adicionar uma aplicação Windows ao Intune.

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
3. No painel do **tipo select,** sob os **outros** tipos de aplicações, selecione **a aplicação Windows (Win32)** .

    > [!IMPORTANT]
    > Certifique-se de usar a versão mais recente da ferramenta de preparação de conteúdo do Microsoft Win32. Se você não usar a versão mais recente, verá um aviso indicando que o aplicativo foi empacotado usando uma versão mais antiga da ferramenta de preparação de conteúdo do Microsoft Win32. 

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

        Por exemplo, se o nome de arquivo do aplicativo for **MyApp123**, adicione o seguinte:<br>
        `msiexec /p “MyApp123.msp”`<p>
        E, se o aplicativo for `ApplicationName.exe`, o comando será o nome do aplicativo seguido pelos argumentos do comando (switches) com suporte no pacote. <br>Por exemplo:<br>
        `ApplicationName.exe /quiet`<br>
        No comando acima, o pacote de `ApplicationName.exe` dá suporte ao argumento de comando `/quiet`.<p> 
        Para os argumentos específicos com suporte no pacote de aplicativos, contate o fornecedor do aplicativo.

    - **Desinstalar**o comando : Adicione a linha de comando desinstalação completa para desinstalar a aplicação com base no GUID da aplicação. 

        Por exemplo: `msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    - **Instalar o comportamento**: Desloque o comportamento de instalação para qualquer **sistema** ou **utilizador**.

        > [!NOTE]
        > Pode configurar uma aplicação Win32 para que esta seja instalada no contexto de **Utilizador** ou **Sistema**. O contexto de **Utilizador** refere-se apenas a um determinado utilizador. O contexto de **Sistema** refere-se a todos os utilizadores de um dispositivo com o Windows 10.
        >
        > Os utilizadores finais não necessitam de ter sessão iniciada no dispositivo para instalarem aplicações Win32.
        > 
        > A instalação e desinstalação do aplicativo Win32 será executada sob o privilégio de administrador (por padrão) quando o aplicativo for definido como instalar no contexto do usuário e o usuário final no dispositivo tiver privilégios de administrador.
    
    - **Comportamento de reinício**do dispositivo : Selecione uma das seguintes opções:
        - **Determine o comportamento com base nos códigos**de devolução : Escolha esta opção para reiniciar o dispositivo com base nos códigos de devolução.
        - **Nenhuma ação específica**: Escolha esta opção para suprimir o reinício do dispositivo durante a instalação de aplicações baseadas em MSI.
        - **A instalação da aplicação pode forçar o reinício**do dispositivo : Escolha esta opção para permitir que a instalação da aplicação esteja concluída sem suprimir o reinício.
        - O **Intune forçará uma reinicialização obrigatória do dispositivo**: escolha esta opção para sempre reiniciar o dispositivo após uma instalação de aplicativo bem-sucedida.

    - **Especifique códigos de devolução para indicar o comportamento pós-instalação**: Adicione os códigos de devolução utilizados para especificar o comportamento de retry da instalação da aplicação ou o comportamento pós-instalação. As entradas de código de retorno são adicionadas por predefinição durante a criação de aplicações. No entanto, pode adicionar códigos de retorno adicionais ou alterar os códigos de retorno existentes.
        1. Na coluna **tipo Código,** desloque o **tipo código** para um dos seguintes:
            - **Falha** – o valor de retorno que indica uma falha na instalação do aplicativo.
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
        1. Clique em **Adicionar** para exibir o painel **Adicionar uma regra de requisito** e configurar regras de requisito adicionais. Selecione o **tipo de requisito** para escolher o tipo de regra que será usado para determinar como um requisito é validado. As regras de requisito podem ser baseadas em informações do sistema de arquivos, valores de registro ou scripts do PowerShell. 
            - **Arquivo**: quando você escolhe **arquivo** como o **tipo de requisito**, a regra de requisito deve detectar um arquivo ou pasta, data, versão ou tamanho. 
                - **Caminho** – o caminho completo da pasta que contém o ficheiro ou pasta a detetar.
                - **Ficheiro ou pasta** – o ficheiro ou pasta a detetar.
                - **Propriedade** – selecione o tipo de regra usado para validar a presença do aplicativo.
                - **Associado a uma aplicação de 32 bits em clientes de 64 bits** – selecione **Sim** para expandir as variáveis de ambiente de caminho no contexto de 32 bits em clientes de 64 bits. Selecione **Não** (predefinição) para expandir as variáveis de caminho no contexto de 64 bits em clientes de 64 bits. Os clientes de 32 bits utilizarão sempre o contexto de 32 bits.
            - **Registro**: quando você escolhe o **registro** como o **tipo de requisito**, a regra de requisito deve detectar uma configuração de registro com base no valor, na cadeia de caracteres, no número inteiro ou na versão.
                - **Caminho da chave** – o caminho completo da entrada de registo que contém o valor a detetar.
                - **Nome do valor** – o nome do valor do registo a detetar. Se este valor estiver vazio, a deteção irá ocorrer na chave. O valor (predefinido) de uma chave será utilizado como valor de deteção, se o método de deteção for diferente da existência de ficheiro ou pasta.
                - **Requisito de chave do registro** – selecione o tipo de comparação de chave do registro usado para determinar como a regra de requisito é validada.
                - **Associado a uma aplicação de 32 bits em clientes de 64 bits** – selecione **Sim** para procurar o registo de 32 bits em clientes de 64 bits. Selecione **Não** (predefinição) para procurar o registo de 64 bits em clientes de 64 bits. Os clientes de 32 bits irão sempre procurar o registo de 32 bits.
            - **Script**: escolha o **script** como o **tipo de requisito**, quando não for possível criar uma regra de requisito com base no arquivo, no registro ou em qualquer outro método disponível no console do Intune.
                - **Arquivo de script** – para regra de requisito baseada em script do PowerShell, se o código existir for 0, detectaremos o stdout mais detalhadamente. Por exemplo, podemos detectar STDOUT como um inteiro que tem um valor de 1.
                - **Executar script como processo de 32 bits em clientes de 64 bits** -selecione **Sim** para executar o script em um processo de 32 bits em clientes de 64 bits. Selecione **não** (padrão) para executar o script em um processo de 64 bits em clientes de 64 bits. Os clientes de 32 bits executam o script em um processo de 32 bits.
                - **Executar este script usando as credenciais conectadas**: selecione **Sim** para executar o script usando as credenciais de dispositivo conectado * *.
                - **Impor a verificação de assinatura do script** – selecione **Sim** para verificar se o script está assinado por um editor fidedigno, o que permitirá que o script seja executado sem avisos ou instruções apresentados. O script será executado desbloqueado. Selecione **Não** (predefinição) para executar o script com a confirmação do utilizador final sem verificação da assinatura.
                - **Selecionar tipo de dados de saída**: selecione o tipo de dados usado ao determinar uma correspondência de regra de requisito.
        2. Quando terminar de definir as regras de exigência, selecione **OK**.
2. Clique em **Seguir** para visualizar a página de regras de **Deteção.**   

### <a name="step-4-detection-rules"></a>Passo 4: Regras de deteção

1. Na página regras de **Deteção,** configure as regras para detetar a presença da aplicação:
    
    **Formato de regras**: Selecione como será detetada a presença da aplicação. Pode optar por configurar manualmente as regras de deteção ou utilizar um script personalizado para detetar a presença da aplicação. Tem de escolher, pelo menos, uma regra de deteção. 

    > [!NOTE]
    > No painel **Regras de deteção**, pode optar por adicionar múltiplas regras. As condições para **todas** as regras têm de ser cumpridas para detetar a aplicação.
    >
    > Se o Intune detectar que o aplicativo não está presente no dispositivo, o Intune oferecerá o aplicativo novamente após 24 horas. Isso só ocorrerá para aplicativos direcionados com a intenção necessária.

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
            
            2. Verifique se o valor do registro existe.
        
                ![Captura de ecrã do painel de regras de deteção – o valor de registo existe](./media/apps-win32-app-management/apps-win32-app-06.png)    
        
            3. Verifique a existência de uma cadeia de valor de registo idêntica.
        
                ![Captura de ecrã do painel de regras de deteção – cadeia de valor de registo idêntica](./media/apps-win32-app-management/apps-win32-app-07.png)    
     
    - **Utilizar um script de deteção personalizado** – especifique o script do PowerShell que será utilizado para detetar esta aplicação. 
    
       1. **Ficheiro de script** – selecione um script do PowerShell que irá detetar a presença da aplicação no cliente. A aplicação será detetada quando o script devolver um código de saída de valor 0 e escrever um valor de cadeia de carateres em STDOUT.

       2. **Executar script como processo de 32 bits em clientes de 64 bits** -selecione **Sim** para executar o script em um processo de 32 bits em clientes de 64 bits. Selecione **não** (padrão) para executar o script em um processo de 64 bits em clientes de 64 bits. Os clientes de 32 bits executam o script em um processo de 32 bits.

       3. **Impor a verificação de assinatura do script** – selecione **Sim** para verificar se o script está assinado por um editor fidedigno, o que permitirá que o script seja executado sem avisos ou instruções apresentados. O script será executado desbloqueado. Selecione **Não** (predefinição) para executar o script com a confirmação do utilizador final sem verificação da assinatura.
    
            O agente do Intune verifica os resultados do script. Lê os valores escritos pelo script no fluxo de saída padrão (STDOUT), no fluxo de erro padrão (STDERR) e no código de saída. Se a saída do script tiver um valor diferente de zero, o script falha e o estado de deteção de aplicação é Não instalada. Se o código de saída for zero e STDOUT tiver dados, o estado de deteção de aplicação é Instalada. 

            > [!NOTE]
            > A Microsoft recomenda codificar seu script como UTF-8. Quando a saída do script tiver o valor de 0, a execução do script foi efetuada com êxito. O segundo canal de saída indica que foi detetada uma aplicação – os dados do STDOUT indicam que a aplicação foi encontrada no cliente. Não procuramos uma cadeia de carateres específica no STDOUT.

2. Depois de adicionar a sua regra(s), selecione **Next** para exibir a página **Dependencies.**

### <a name="step-5-dependencies"></a>Passo 5: Dependências

As dependências de aplicativo são aplicativos que devem ser instalados antes que seu aplicativo Win32 possa ser instalado. Você pode exigir que outros aplicativos sejam instalados como dependências. Especificamente, o dispositivo deve instalar os aplicativos dependentes antes de instalar o aplicativo Win32. Há um máximo de 100 dependências, que inclui as dependências de quaisquer dependências incluídas, bem como o próprio aplicativo. Você pode adicionar dependências do aplicativo Win32 somente depois que seu aplicativo Win32 tiver sido adicionado e carregado no Intune. Depois que seu aplicativo Win32 tiver sido adicionado, você verá a opção **Dependencies** no painel do seu aplicativo Win32. 

Qualquer dependência de aplicativo Win32 precisa ser também um aplicativo Win32. Ele não oferece suporte dependendo de outros tipos de aplicativo, como aplicativos de LOB ou aplicativos da loja de um único MSI.

Ao adicionar uma dependência de aplicativo, você pode pesquisar com base no nome do aplicativo e no Publicador. Além disso, você pode classificar suas dependências adicionadas com base no nome do aplicativo e no Publicador. Dependências de aplicativo adicionadas anteriormente não podem ser selecionadas na lista de dependências de aplicativo adicionadas. 

Você pode escolher se deseja ou não instalar cada aplicativo dependente automaticamente. Por padrão, a opção de **instalação automática** é definida como **Sim** para cada dependência. Ao instalar automaticamente um aplicativo dependente, mesmo que o aplicativo dependente não seja direcionado para o usuário ou dispositivo, o Intune instalará o aplicativo no dispositivo para atender à dependência antes de instalar seu aplicativo Win32. É importante observar que uma dependência pode ter subdependências recursivas e cada subdependência será instalada antes da instalação da dependência principal. Além disso, a instalação de dependências não segue uma ordem de instalação em um determinado nível de dependência.

### <a name="select-the-dependencies"></a>Selecione as dependências

Na página **Dependencies,** selecione aplicações que devem ser instaladas antes da aplicação Win32 poder ser instalada:
1. Clique em **Adicionar** para exibir o painel de **dependência adicionar.**
3. Depois de adicionar os aplicativos dependentes, clique em **selecionar**.
4. Escolha se instala automaticamente a aplicação dependente selecionando **Sim** ou **Não** sob a coluna **Instalar automaticamente.**
5. Clique em **Seguir** para exibir a página **de tags scope.**

### <a name="understand-additional-dependency-details"></a>Compreender detalhes adicionais de dependência

O usuário final verá as notificações do sistema do Windows indicando que os aplicativos dependentes estão sendo baixados e instalados como parte do processo de instalação do aplicativo Win32. Além disso, quando um aplicativo dependente não está instalado, o usuário final normalmente verá uma das seguintes notificações:
- 1 ou mais aplicativos dependentes não puderam ser instalados
- 1 ou mais requisitos de aplicativo dependente não atendidos
- 1 ou mais aplicativos dependentes estão aguardando a reinicialização do dispositivo

Se você optar por não **instalar automaticamente** uma dependência, a instalação do aplicativo Win32 não será tentada. Além disso, o relatório de aplicativo mostrará que a dependência foi sinalizada como `failed` e também fornecerá um motivo de falha. Você pode exibir a falha na instalação da dependência clicando em uma falha (ou aviso) fornecida nos [detalhes da instalação](troubleshoot-app-install.md#win32-app-installation-troubleshooting)do aplicativo Win 32. 

Cada dependência aderirá à lógica de repetição do aplicativo Win32 do Intune (tente instalar três vezes após aguardar 5 minutos) e o agendamento de reavaliação global. Além disso, as dependências só são aplicáveis no momento da instalação do aplicativo Win32 no dispositivo. As dependências não são aplicáveis para desinstalar um aplicativo Win32. Para excluir uma dependência, você deve clicar nas reticências (três pontos) à esquerda do aplicativo dependente localizado no final da linha da lista de dependências. 

## <a name="step-6---select-scope-tags-optional"></a>Passo 6 - Selecione etiquetas de âmbito (opcional)
Você pode usar marcas de escopo para determinar quem pode ver as informações do aplicativo cliente no Intune. Para mais detalhes sobre etiquetas de âmbito, consulte [Use o controlo de acesso baseado em funções e as etiquetas](../fundamentals/scope-tags.md)de âmbito para TI distribuídos .

1. Clique em **Selecionar etiquetas** de âmbito para adicionar opcionalmente etiquetas de âmbito para a aplicação. 
2. Clique em **Avançar** para exibir a página **atribuições** .

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

Neste ponto, você concluiu as etapas para adicionar um aplicativo Win32 ao Intune. Para obter informações sobre a atribuição e monitorização de aplicações, veja [Atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md) e [Monitorizar informações e atribuições da aplicação com o Microsoft Intune](apps-monitor.md).

## <a name="delivery-optimization"></a>Otimização de Entrega

Os clientes do Windows 10 1709 e posteriores baixarão o conteúdo do aplicativo Win32 do Intune usando um componente de otimização de entrega no cliente do Windows 10. A otimização de entrega fornece a funcionalidade ponto a ponto que está ativada por padrão. A otimização de entrega pode ser configurada pela diretiva de grupo e por meio da configuração do dispositivo do Intune. Para obter mais informações, consulte [otimização de entrega para Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

> [!NOTE]
> Você também pode instalar um servidor de cache conectado da Microsoft em seus pontos de distribuição Configuration Manager para armazenar em cache o conteúdo do aplicativo Win32 do Intune. Para obter mais informações, consulte [cache conectado da Microsoft em Configuration Manager-suporte para aplicativos Win32 do Intune](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune).

## <a name="install-required-and-available-apps-on-devices"></a>Instalar aplicações necessárias e disponíveis em dispositivos

O usuário final verá as notificações do sistema do Windows para as instalações de aplicativo necessárias e disponíveis. A imagem seguinte mostra uma notificação de alerta de exemplo na qual a instalação da aplicação não é concluída até que o dispositivo seja reiniciado. 

![Captura de tela de notificações do sistema do Windows para uma instalação de aplicativo](./media/apps-win32-app-management/apps-win32-app-08.png)    

A imagem a seguir notifica o usuário final que as alterações de aplicativo estão sendo feitas no dispositivo.

![Captura de tela notificando o usuário de que as alterações do aplicativo estão sendo feitas](./media/apps-win32-app-management/apps-win32-app-09.png)    

## <a name="set-win32-app-availability-and-notifications"></a>Definir disponibilidade e notificações de aplicações Win32
Pode configurar o tempo de início e prazo para uma aplicação Win32. Na hora de início, a extensão de gestão Intune iniciará o download e cache de conteúdo da aplicação para a intenção necessária. O aplicativo será instalado na hora do prazo. Para aplicações disponíveis, a hora de início ditará quando a aplicação for visível no Portal da Empresa e os conteúdos serão descarregados quando o utilizador final solicitar a aplicação do Portal da Empresa. Além disso, pode permitir um período de reinício da graça. 

Detete a disponibilidade da aplicação com base numa data e hora para uma aplicação necessária utilizando os seguintes passos:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos**.
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
7. No painel **Editar atribuição** , defina as **notificações de usuário finalizador** para **Mostrar todas as notificações do sistema**. Note que pode definir **notificações finais** do utilizador para mostrar todas as notificações de **torradas,** mostrar notificações de **torradas para reiniciar o computador**ou ocultar todas as notificações de **torradas**.
8. Detete a disponibilidade da **App** para **Uma data e hora específicas** e selecione a sua data e hora. Esta data e hora especifica quando a aplicação é descarregada para o dispositivo de utilizadores finais. 
9. Detete o prazo de **instalação** da App para **Uma data e hora específicas** e selecione a sua data e hora. Esta data e hora especifica quando a aplicação é instalada no dispositivo de utilizadores finais. Quando for feita mais de uma atribuição para o mesmo utilizador ou dispositivo, o prazo de instalação da aplicação é escolhido com base no mais cedo possível.

10. Clique **ativado** ao lado do período de **graça restart**. O período de graça de reinício começa assim que a instalação da aplicação estiver concluída no dispositivo. Quando desativado, o aparelho pode reiniciar sem aviso prévio. <br>Pode personalizar as seguintes opções:
    - **Período de carência da reinicialização do dispositivo (minutos)** : o valor padrão é 1440 minutos (24 horas). Este valor pode ser no máximo 2 semanas.
    - **Selecione quando deve visualizar a caixa de diálogo de contagem regressiva antes de o reinício ocorrer (minutos)** : O valor predefinido é de 15 minutos.
    - **Permitir que o utilizador ressone a notificação de reinício:** Pode escolher **Sim** ou **Não**.
        - **Selecione a duração do soneto (minutos)** : O valor predefinido é de 240 minutos (4 horas). O valor do soneca não pode ser mais do que reiniciar o período de graça.

11. Clique em **Rever + salvar**.

## <a name="toast-notifications-for-win32-apps"></a>Notificações do sistema para aplicativos Win32 
Se necessário, você pode suprimir a exibição de notificações do sistema de usuário final por atribuição de aplicativo. No Intune, selecione **aplicativos** > **todos os aplicativos** > selecione o aplicativo > **atribuições** > **incluir grupos**. 

> [!NOTE]
> As aplicações Win32 instaladas da extensão de gestão do Intune não serão desinstaladas em dispositivos não inscritos. Os administradores podem tirar partido da exclusão de atribuição para não oferecer aplicações Win32 em dispositivos BYOD.

## <a name="troubleshoot-win32-app-issues"></a>Resolver problemas relacionados com aplicações Win32
Os registos de agente no computador cliente encontram-se normalmente em `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Pode tirar partido de `CMTrace.exe` para ver estes ficheiros de registo. Para obter mais informações, consulte [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace).

![Captura de tela dos logs de agente no computador cliente](./media/apps-win32-app-management/apps-win32-app-10.png)    

> [!IMPORTANT]
> Para permitir a instalação e execução correta de aplicativos LOB Win32, as configurações de anti-malware devem excluir os seguintes diretórios de serem verificados:<p>
> **Em computadores cliente x64**:<br>
> *C:\Arquivos de programas (x86) \Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*
>  
> **Em computadores cliente x86**:<br>
> *C:\Arquivos de Programas\microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*

### <a name="detecting-the-win32-app-file-version-using-powershell"></a>Detectando a versão do arquivo do aplicativo Win32 usando o PowerShell

Se você tiver dificuldade para detectar a versão do arquivo do aplicativo Win32, considere usar ou modificar o seguinte comando do PowerShell:

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

No comando do PowerShell acima, substitua a cadeia de caracteres `<path to binary file>` pelo caminho para o arquivo do aplicativo Win32. Um caminho de exemplo seria semelhante ao seguinte:<br>
`C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe`

Além disso, substitua a cadeia de caracteres `<file version of successfully detected file>` pela versão do arquivo que você precisa detectar. Uma cadeia de caracteres de versão de arquivo de exemplo seria semelhante ao seguinte:<br>
`2019.0150.18118.00 ((SSMS_Rel).190420-0019)`

Se você precisar obter as informações de versão do seu aplicativo Win32, poderá usar o seguinte comando do PowerShell:

``` PowerShell

[System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion

```

No comando do PowerShell acima, substitua `<path to binary file>` pelo caminho do arquivo.

### <a name="additional-troubleshooting-areas-to-consider"></a>Áreas de solução de problemas adicionais a serem consideradas
- Verificar o direcionamento para garantir que o agente está instalado no dispositivo – uma aplicação Win32 direcionada para um grupo ou um Script do PowerShell direcionado para um grupo irá criar a política de instalação de agente para o grupo de segurança.
- Verificar a versão do SO – Windows 10 1607 e posterior.  
- Verificar a SKU do Windows 10 – o Windows 10 S ou versões do Windows em execução com o modo S ativado não suportam a instalação da MSI.

Para obter mais informações sobre como solucionar problemas de aplicativos Win32, consulte [solução de problemas de instalação do aplicativo Win32](troubleshoot-app-install.md#win32-app-installation-troubleshooting).

## <a name="next-steps"></a>Próximos passos

- Para obter mais informações sobre como adicionar aplicações ao Intune, veja [Adicionar aplicações ao Microsoft Intune](apps-add.md).
