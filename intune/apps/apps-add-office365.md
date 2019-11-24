---
title: Adicionar aplicativos do Office 365 a dispositivos Windows 10 usando o Microsoft Intune
titleSuffix: ''
description: Saiba como você pode usar Microsoft Intune para instalar aplicativos do Office 365 em dispositivos Windows 10.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2cb247ec25b134fa9810a426be88b7fc90999394
ms.sourcegitcommit: 2c8a41ee95a3fde150667a377770e51b621ead65
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73635413"
---
# <a name="add-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Adicionar aplicativos do Office 365 a dispositivos Windows 10 com Microsoft Intune

Antes de poder atribuir, monitorizar, configurar ou proteger aplicações, tem de adicioná-las ao Intune. Um dos tipos de [aplicativo](apps-add.md#app-types-in-microsoft-intune) disponíveis são os aplicativos do Office 365 para dispositivos Windows 10. Ao selecionar esse tipo de aplicativo no Intune, você pode atribuir e instalar aplicativos do Office 365 em dispositivos gerenciados que executam o Windows 10. Você também pode atribuir e instalar aplicativos para o cliente de área de trabalho do Microsoft Project online e o Microsoft Visio online plano 2, se você tiver licenças para eles. Os aplicativos do Office 365 disponíveis são exibidos como uma única entrada na lista de aplicativos no console do Intune no Azure.

> [!NOTE]
> Tem de utilizar licenças do Office 365 ProPlus para ativar as aplicações do Office 365 ProPlus implementadas através do Microsoft Intune. De momento, o Intune não suporta o Office 365 Empresas.

## <a name="before-you-start"></a>Antes de começar

> [!IMPORTANT]
> Se existirem aplicações do Office .msi no dispositivo do utilizador final, tem de utilizar a funcionalidade **Remover MSI** para desinstalar estas aplicações em segurança. Caso contrário, as aplicações do Office 365 fornecidas pelo Intune não serão instaladas com êxito.

- Os dispositivos em que pretende implementar estas aplicações têm de ter a Atualização para Criativos do Windows 10 ou posterior.
- O Intune só suporta a adição de aplicações do Office que pertençam ao conjunto de aplicações Office 365.
- Se estiverem abertas aplicações do Office quando o Intune instalar o conjunto de aplicações, a instalação poderá falhar e os utilizadores poderão perder os dados dos ficheiros não guardados.
- Não há suporte para esse método de instalação nos dispositivos Windows Home, Windows Team, Windows Holographic ou Windows Holographic for Business.
- O Intune não suporta a instalação de aplicações de ambiente de trabalho do Office 365 da Microsoft Store (denominadas aplicações Office Centennial) num dispositivo em que já implementou aplicações do Office 365 com o Intune. Se instalar esta configuração, poderá causar perda ou danos em dados.
- As múltiplas atribuições de aplicações necessárias ou disponíveis não são acumulativas. Uma atribuição de aplicação posterior irá substituir as atribuições de aplicações instaladas pré-existentes. Por exemplo, se o primeiro conjunto de aplicações do Office incluir o Word, mas o conjunto posterior não o incluir, o Word será desinstalado. Esta condição não se aplica às aplicações Visio ou Project.
- No momento, não há suporte para várias implantações do Office 365. Somente uma implantação será entregue ao dispositivo
- **Versão do Office**: selecione se pretende atribuir a versão de 32 bits ou de 64 bits do Office. Pode instalar a versão de 32 bits em dispositivos de 32 e de 64 bits, mas só pode instalar a versão de 64 bits em dispositivos de 64 bits.
- **Remover MSI dos dispositivos de utilizador final**: escolha se pretende remover as aplicações .MSI do Office já existentes dos dispositivos de utilizador final. A instalação não será concluída com êxito se existirem aplicações MSI já existentes em dispositivos de utilizador final. As aplicações a desinstalar não se limitam às selecionadas para instalação em **Configurar o Conjunto de Aplicações**, na medida em que irá remover todas as aplicações do Office (MSI) do dispositivo de utilizador final. Para obter mais informações, veja [Remover versões MSI do Office existentes ao atualizar para o Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Quando o Intune reinstalar o Office nos computadores dos seus utilizadores finais, estes terão automaticamente os mesmos pacotes de idiomas de que dispunham com instalações anteriores do Office .MSI.

## <a name="get-started"></a>Introdução

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. No painel da carga de trabalho **Aplicações do cliente**, em **Gerir**, selecione **Aplicações**.
5. Selecione **Adicionar**.
6. No painel **Adicionar aplicações**, na lista **Tipo de aplicação**, em **Conjunto de Aplicações do Office 365**, selecione **Windows 10**.

## <a name="select-settings-format"></a>Selecionar formato de configurações

Você pode escolher um método para definir a configuração do aplicativo selecionando um **formato de configurações**. A configuração das opções de formato inclui:
- Designer de configuração
- Introduzir dados XML

Quando você escolher o **Designer de configuração** , a folha **Adicionar aplicativo** será alterada para oferecer duas opções de configurações adicionais:
- Configurar pacote de aplicativos
- Configurações do pacote de aplicativos

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

Ao escolher **inserir dados XML** , adicione a folha **Adicionar aplicativo** com exibir a opção **inserir dados XML** . Selecione para exibir a folha do **arquivo de configuração** . 

![Adicionar o designer de configuração do Office 365](./media/apps-add-office365/apps-add-office365-01.png)
    
Para obter mais informações sobre a opção **inserir dados XML** , consulte [inserir dados XML](apps-add-office365.md#enter-xml-format) abaixo.

## <a name="configure-app-suite-information"></a>Configurar informações do pacote de aplicativos

Neste passo, vai fornecer as informações acerca do conjunto de aplicações. Estas informações ajudam-no a identificar o conjunto de aplicações no Intune e também ajuda os utilizadores a encontrá-la no portal da empresa.

1. No painel **Adicionar Aplicação**, selecione **Informações do Conjunto de Aplicações**.
2. No painel **Informações do Conjunto de Aplicações**, faça o seguinte:
    - **Nome do Conjunto**: introduza o nome do conjunto de aplicações tal como será apresentado no portal da empresa. Confirme que todos os nomes de conjuntos de aplicações que utiliza são exclusivos. Se o nome de um conjunto de aplicações existir em duplicado, apenas uma das aplicações será apresentada aos utilizadores no portal da empresa.
    - **Descrição do Conjunto**: introduza uma descrição para o conjunto de aplicações. Por exemplo, pode listar as aplicações que selecionou para inclusão.
    - **Publicador**: a Microsoft aparece como o publicador.
    - **Categoria**: em alternativa, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Esta definição irá permitir que os utilizadores encontrem o conjunto de aplicações mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da Empresa**: selecione esta opção para apresentar o conjunto de aplicações em destaque na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: a Microsoft aparece como o programador.
    - **Proprietário**: a Microsoft aparece como o proprietário.
    - **Notas**: introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: o logótipo do Office 365 é apresentado com a aplicação quando os utilizadores procuram no portal da empresa.
3. Selecione **OK**.

## <a name="configure-app-suite"></a>Configurar pacote de aplicativos

Se você tiver selecionado a opção **Designer de configuração** na caixa suspensa **formato de configuração** , verá a opção **Configurar pacote de aplicativos** na folha **Adicionar aplicativo** . Selecione as aplicações do Office que quer atribuir aos dispositivos.

1. No painel **Adicionar Aplicação**, selecione **Configurar Conjunto de Aplicações**.
2. No painel **Configurar Conjunto de Aplicações**, selecione as aplicações padrão do Office que quer atribuir aos dispositivos.  
    Além disso, você pode instalar aplicativos para o cliente de área de trabalho do Microsoft Project online e o Microsoft Visio online plano 2, se você tiver licenças para eles.
3. Selecione **OK**.

## <a name="configure-app-suite-settings"></a>Definir configurações do pacote de aplicativos

Se você tiver selecionado a opção **Designer de configuração** na caixa suspensa **formato de configuração** , verá a opção configurações do pacote de **aplicativos** na folha **Adicionar aplicativo** . Neste passo, configure as opções de instalação do conjunto de aplicações. As definições aplicam-se a todas as aplicações que adicionou ao conjunto.

1. No painel **Adicionar Aplicação**, selecione **Definições do Conjunto de Aplicações**.
2. No painel **Definições do Conjunto de Aplicações**, faça o seguinte:
    - **Versão do Office**: selecione se quer atribuir a versão de 32 bits ou de 64 bits do Office. Pode instalar a versão de 32 bits em dispositivos de 32 e de 64 bits, mas só pode instalar a versão de 64 bits em dispositivos de 64 bits.
    - **Atualizar Canal**: selecione a forma como o Office é atualizado nos dispositivos. Para obter mais informações sobre os vários canais de atualização, veja a [Descrição geral dos canais de atualização do Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus). Escolha entre:
        - **Mensalmente**
        - **Via de Atualizações Mensais (Direcionada)**
        - **Via de Atualizações Mensais Semianuais**
        - **Via de Atualizações Mensais Semianuais (Direcionada)**

        Depois de selecionar um canal, pode selecionar opcionalmente **Específico** para instalar uma versão específica do Office no canal selecionado em dispositivos de utilizador final. Em seguida, selecione a **Versão específica** do Office a utilizar.
        
        As versões disponíveis serão alteradas ao longo do tempo. Por conseguinte, ao criar uma nova implementação, as versões disponíveis podem ser mais recentes e não ter determinadas versões mais antigas disponíveis. As implementações atuais continuarão a implementar a versão mais antiga, mas a lista de versões será constantemente atualizada por canal.
        
        Para dispositivos que atualizam a respetiva versão fixa (ou quaisquer outras propriedades) e são implementados como disponíveis, o estado de comunicação será apresentado como Instalado se a versão anterior tiver sido instalada até ocorrer a entrada do dispositivo. Quando a entrada do dispositivo ocorrer, o estado será alterado temporariamente para Desconhecido, embora não seja apresentado ao utilizador. Quando o utilizador iniciar a instalação da versão mais recente disponível, o estado será alterado para Instalado.
        
        Para obter mais informações, veja [Overview of update channels for Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus) (Descrição geral dos canais de atualização do Office 365 ProPlus).

    - **Remover MSI dos dispositivos de utilizador final**: escolha se pretende remover as aplicações .MSI do Office já existentes dos dispositivos de utilizador final. A instalação não será concluída com êxito se existirem aplicações MSI já existentes em dispositivos de utilizador final. As aplicações a desinstalar não se limitam às selecionadas para instalação em **Configurar o Conjunto de Aplicações**, na medida em que irá remover todas as aplicações do Office (MSI) do dispositivo de utilizador final. Para obter mais informações, veja [Remover versões MSI do Office existentes ao atualizar para o Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Quando o Intune reinstalar o Office nos computadores dos seus utilizadores finais, estes terão automaticamente os mesmos pacotes de idiomas de que dispunham com instalações anteriores do Office .MSI. 
    - **Aceitar automaticamente o contrato de licença do utilizador final**: selecione esta opção se não precisar que os utilizadores finais aceitem o contrato de licença. O Intune irá aceitar automaticamente o contrato.
    - **Utilizar a ativação de computadores partilhados**:selecione esta opção quando existirem múltiplos utilizadores a partilhar um computador. Para obter mais informações, veja [Overview of shared computer activation for Office 365](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus)(Descrição geral da ativação de computadores partilhados para o Office 365).
    - **Idiomas**: o Office é instalado automaticamente em qualquer dos idiomas suportados que vierem instalados com o Windows no dispositivo dos utilizadores finais. Selecione esta opção se quiser instalar idiomas adicionais no conjunto de aplicações. <p></p>
    Pode implementar idiomas adicionais para aplicações do Office 365 Pro Plus geridas através do Intune. A lista de idiomas disponíveis inclui o **Tipo** do pacote de idiomas (núcleo, parcial e verificação). No portal do Azure, selecione **Microsoft Intune** > **Aplicações do cliente** > **Aplicações** > **Adicionar**. Na lista **Tipo de aplicação**, no painel **Adicionar aplicação**, selecione **Windows 10** em **Office 365 Suite**. Selecione **Idiomas** no painel **Definições do Conjunto de Aplicações**. Para obter informações adicionais, veja [Descrição geral da implementação de idiomas no Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).

## <a name="select-scope-tags-optional"></a>Selecionar marcas de escopo (opcional)
Você pode usar marcas de escopo para determinar quem pode ver as informações do aplicativo cliente no Intune. Para obter detalhes completos sobre marcas de escopo, consulte [usar o controle de acesso baseado em função e marcas de escopo para distribuí-lo](../fundamentals/scope-tags.md).

1. Selecione **escopo (marcas)**  > **Adicionar**.
2. Use a caixa **selecionar** para procurar marcas de escopo.
3. Marque a caixa de seleção ao lado das marcas de escopo que você deseja atribuir a este aplicativo.
4. Selecione **Selecionar** > **OK**.

## <a name="enter-xml-format"></a>Inserir formato XML

Se você tiver selecionado a opção **inserir dados XML** na caixa suspensa **formato de configuração** , verá a opção **Inserir formato XML** na folha **Adicionar aplicativo** . Para obter mais informações, consulte [Opções de configuração para a ferramenta de implantação do Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

## <a name="finish-up"></a>Concluir

Quando tiver concluído, no painel **Adicionar Aplicação**, selecione **Adicionar**. A aplicação que criou é apresentada na lista de aplicações. A próxima etapa é atribuir os aplicativos aos grupos que você escolher. Para obter mais informações, veja [Atribuir aplicações a grupos](~/apps/apps-deploy.md).

## <a name="deployment-details"></a>Detalhes da implantação

Depois que a política de implantação do Intune for atribuída aos computadores de destino por meio do [provedor de serviços de configuração do Office (CSP)](https://docs.microsoft.com/windows/client-management/mdm/office-csp), o dispositivo final baixará automaticamente o pacote de instalação do local *officecdn.Microsoft.com* . Você verá dois diretórios aparecendo no diretório *arquivos de programas* :

![Pacotes de instalação do Office no diretório de arquivos de programas](./media/apps-add-office365/office-folder.png)

No diretório *Microsoft Office* , uma nova pasta é criada onde os arquivos de instalação são armazenados:

![Nova pasta criada em Microsoft Office Directory](./media/apps-add-office365/created-folder.png)

No diretório *Microsoft Office 15* , os arquivos do inicializador de instalação do clique para executar do Office são armazenados. A instalação será iniciada automaticamente se o tipo de atribuição for necessário:

![Clique para executar os arquivos do inicializador de instalação](./media/apps-add-office365/clicktorun-files.png)

A instalação estará no modo silencioso se a atribuição do O365 Suite estiver configurada conforme necessário. Os arquivos de instalação baixados serão excluídos assim que a instalação for bem-sucedida. Se a atribuição estiver configurada como **disponível**, os aplicativos do Office aparecerão no aplicativo portal da empresa para que os usuários finais possam disparar a instalação manualmente.

## <a name="troubleshooting"></a>Resolução de Problemas
O Intune usa a [ferramenta de implantação do Office](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool) para baixar e implantar o Office 365 ProPlus em seus computadores cliente usando a CDN do [Office 365](https://docs.microsoft.com/office365/enterprise/content-delivery-networks). Referencie as práticas recomendadas descritas em [Gerenciando pontos de extremidade do Office 365](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints) para garantir que sua configuração de rede permita que os clientes acessem a CDN diretamente, em vez de rotear o tráfego da CDN por meio de proxies centrais para evitar introduzir latência desnecessária.

Execute o [suporte da Microsoft e o assistente de recuperação para o Office 365](https://diagnostics.office.com) em um dispositivo de destino se você encontrar problemas de instalação ou tempo de execução.

### <a name="additional-troubleshooting-details"></a>Detalhes adicionais de solução de problemas

Quando não for possível instalar os aplicativos do O365 em um dispositivo, você deverá identificar se o problema é relacionado ao Intune ou ao sistema operacional/do Office. Se você puder ver as duas pastas *Microsoft Office* e *Microsoft Office 15* aparecendo no diretório *arquivos de programas* do dispositivo, você pode confirmar que o Intune iniciou a implantação com êxito. Se não for possível ver as duas pastas aparecendo em *arquivos de programas*, você deverá confirmar os casos a seguir:

- O dispositivo está registrado corretamente no Microsoft Intune. 
- Há uma conexão de rede ativa no dispositivo. Se o dispositivo estiver no modo avião, estiver desativado ou em um local sem serviço, a política não será aplicada até que a conectividade de rede seja estabelecida.
- Os requisitos de rede do Intune e do Office 365 são atendidos e os intervalos de IP relacionados são acessíveis com base nos seguintes artigos:

  - [Largura de banda e requisitos de configuração de rede do Intune](https://docs.microsoft.com/intune/network-bandwidth-use)
  - [Intervalos de endereços IP e URLs do Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

- Os grupos corretos foram atribuídos ao pacote de aplicativos do O365. 

Além disso, monitore o tamanho do diretório *c:\Arquivos de Programas\microsoft Office\Updates\Download*. O pacote de instalação baixado da nuvem do Intune será armazenado nesse local. Se o tamanho não aumentar ou apenas aumentar muito lentamente, é recomendável verificar novamente a conectividade e a largura de banda da rede.

Depois de concluir que a infraestrutura de rede e o Intune funcionam conforme o esperado, você deve analisar o problema de uma perspectiva de sistema operacional. Considere as seguintes condições:

- O dispositivo de destino deve ser executado na atualização do Windows 10 para criadores ou posterior.
- Nenhum aplicativo existente do Office é aberto enquanto o Intune implanta os aplicativos.
- As versões de MSI existentes do Office foram removidas corretamente do dispositivo. O Intune utiliza o clique para executar o Office, o que não é compatível com o Office MSI. Esse comportamento é mencionado ainda mais neste documento:<br>
  [O Office instalado com Clique para executar e Windows Installer no mesmo computador não é suportado](https://support.office.com/article/office-installed-with-click-to-run-and-windows-installer-on-same-computer-isn-t-supported-30775ef4-fa77-4f47-98fb-c5826a6926cd)
- O usuário de conexão deve ter permissão para instalar aplicativos no dispositivo.
- Confirme se não há nenhum problema com base no log do Windows Visualizador de Eventos **logs do windows** -> **aplicativos**.
- Capture logs detalhados de instalação do Office durante a instalação. Para tal, siga estes passos:<br>
    1. Ative o log detalhado para a instalação do Office nos computadores de destino. Para fazer isso, execute o seguinte comando para modificar o registro:<br>
        `reg add HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /t REG_DWORD /d 3`<br>
    2. Implante o pacote do Office 365 nos dispositivos de destino novamente.<br>
    3. Aguarde aproximadamente 15 a 20 minutos e vá para a pasta **% Temp%** e a pasta **%WINDIR%\temp** , classificar por **data de modificação**, selecione os arquivos *{nome da máquina}-{timestamp}. log* que são modificados de acordo com o tempo de reprodução.<br>
    4. Execute o seguinte comando para desabilitar o log detalhado:<br>
        `reg delete HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /f`<br>
        Os logs detalhados podem fornecer mais informações detalhadas sobre o processo de instalação.

## <a name="errors-during-installation-of-the-app-suite"></a>Erros durante a instalação do conjunto de aplicações

Consulte [como habilitar o log ULS do Office 365 ProPlus](https://blogs.technet.microsoft.com/odsupport/2018/06/18/how-to-enable-office-365-proplus-uls-logging) para obter informações sobre como exibir logs de instalação detalhados.

A seguinte tabela lista códigos de erro comuns que poderá encontrar e o seu significado.

### <a name="status-for-office-csp"></a>Estado do CSP do Office

| Estado | Fase | Descrição |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460 (ERROR_TIMEOUT) | Transferência | Falha ao transferir a Ferramenta de Implementação do Office |
| 13 (ERROR_INVALID_DATA) | - | Não foi possível verificar a assinatura da Ferramenta de Implementação do Office transferida |
| Código de erro de CertVerifyCertificateChainPolicy | - | Falha na verificação de certificação da Ferramenta de Implementação do Office transferida |
| 997 | WIP | A instalar |
| 0 | Após a instalação | Instalação concluída com êxito |
| 1603 (ERROR_INSTALL_FAILURE) | - | Falha em qualquer verificação de pré-requisito, como: SxS (tentativa de instalar quando 2016 MSI está instalado) versão mismatchOthers |
| 0x8000ffff (E_UNEXPECTED) | - | Tentativa de desinstalação quando a tecnologia Clique-e-Use do Office não existe no computador |
| 17002 | - | Falha ao concluir o cenário (instalação). Motivos possíveis: instalação cancelada pelo userinstallion cancelada por outra instalação do espaço em disco durante a ID do idioma installationUnknown |
| 17004 | - | SKUs desconhecidos |


### <a name="office-deployment-tool-error-codes"></a>Códigos de erro da Ferramenta de Implementação do Office

| Cenário | Código de retorno | IU | Nota |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------|
| Tentativa de desinstalação quando não existe nenhuma instalação Clique-e-Use ativa | -2147418113, 0x8000ffff ou 2147549183 | Código de erro: código de 30088-1008Error: 30125-1011 (404) | Ferramenta de Implementação do Office |
| Instalação quando já existe uma versão MSI instalada | 1603 | - | Ferramenta de Implementação do Office |
| Instalação cancelada pelo utilizador ou por outra instalação | 17002 | - | Clique-e-Use |
| Tentativa de instalação da versão de 64 bits num dispositivo com a versão de 32 bits instalada. | 1603 | - | Código de retorno da Ferramenta de Implementação do Office |
| Tentativa de instalação de um SKU desconhecido (trata-se de um caso de utilização ilegítima do CSP do Office, visto que devemos passar apenas SKUs válidos) | 17004 | - | Clique-e-Use |
| Falta de espaço | 17002 | - | Clique-e-Use |
| O cliente da versão Clique-e-Use falhou ao iniciar (inesperado) | 17000 | - | Clique-e-Use |
| O cliente da versão Clique-e-Use falhou ao colocar o cenário em fila (inesperado) | 17001 | - | Clique-e-Use |

## <a name="next-steps"></a>Próximos passos

- Para atribuir as aplicações aos grupos que escolher, veja [Atribuir aplicações a grupos](/intune-azure/manage-apps/deploy-apps).
