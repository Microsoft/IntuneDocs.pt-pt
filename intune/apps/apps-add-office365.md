---
title: Adicione aplicações do Office 365 aos dispositivos Windows 10 usando o Microsoft Intune
titleSuffix: ''
description: Saiba como pode utilizar o Microsoft Intune para instalar aplicações do Office 365 em dispositivos Windows 10.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
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
ms.openlocfilehash: 86d02ae1277ff2fd6dfce9bf206628f5dc1c2a84
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755337"
---
# <a name="add-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Adicione 365 aplicações do Office aos dispositivos windows 10 com microsoft Intune

Antes de poder atribuir, monitorizar, configurar ou proteger aplicações, tem de adicioná-las ao Intune. Um dos tipos de [aplicações](apps-add.md#app-types-in-microsoft-intune) disponíveis são as aplicações do Office 365 para dispositivos Windows 10. Ao selecionar este tipo de aplicação em Intune, pode atribuir e instalar aplicações do Office 365 para dispositivos que gere que executam o Windows 10. Também pode atribuir e instalar aplicações para o cliente de desktop do Microsoft Project Online e para o Microsoft Visio Online Plan 2, caso possua licenças para eles. As aplicações disponíveis do Office 365 são apresentadas como uma única entrada na lista de aplicações na consola Intune dentro do Azure.

> [!NOTE]
> Tem de utilizar licenças do Office 365 ProPlus para ativar as aplicações do Office 365 ProPlus implementadas através do Microsoft Intune. De momento, o Intune não suporta o Office 365 Empresas.

## <a name="before-you-start"></a>Antes de começar

> [!IMPORTANT]
> Se existirem aplicações do Office .msi no dispositivo do utilizador final, tem de utilizar a funcionalidade **Remover MSI** para desinstalar estas aplicações em segurança. Caso contrário, as aplicações do Office 365 fornecidas pelo Intune não serão instaladas com êxito.

- Os dispositivos em que pretende implementar estas aplicações têm de ter a Atualização para Criativos do Windows 10 ou posterior.
- O Intune só suporta a adição de aplicações do Office que pertençam ao conjunto de aplicações Office 365.
- Se estiverem abertas aplicações do Office quando o Intune instalar o conjunto de aplicações, a instalação poderá falhar e os utilizadores poderão perder os dados dos ficheiros não guardados.
- Este método de instalação não é suportado no Windows Home, Windows Team, Windows Holographic ou Windows Holographic para dispositivos Business.
- O Intune não suporta a instalação de aplicações de ambiente de trabalho do Office 365 da Microsoft Store (denominadas aplicações Office Centennial) num dispositivo em que já implementou aplicações do Office 365 com o Intune. Se instalar esta configuração, poderá causar perda ou danos em dados.
- As múltiplas atribuições de aplicações necessárias ou disponíveis não são acumulativas. Uma atribuição de aplicação posterior irá substituir as atribuições de aplicações instaladas pré-existentes. Por exemplo, se o primeiro conjunto de aplicações do Office incluir o Word, mas o conjunto posterior não o incluir, o Word será desinstalado. Esta condição não se aplica às aplicações Visio ou Project.
- Não são atualmente suportados múltiplos destacamentos do Office 365. Apenas uma implementação será entregue no dispositivo
- **Versão do Office**: selecione se pretende atribuir a versão de 32 bits ou de 64 bits do Office. Pode instalar a versão de 32 bits em dispositivos de 32 e de 64 bits, mas só pode instalar a versão de 64 bits em dispositivos de 64 bits.
- **Remover MSI dos dispositivos de utilizador final**: escolha se pretende remover as aplicações .MSI do Office já existentes dos dispositivos de utilizador final. A instalação não será concluída com êxito se existirem aplicações MSI já existentes em dispositivos de utilizador final. As aplicações a desinstalar não se limitam às selecionadas para instalação em **Configurar o Conjunto de Aplicações**, na medida em que irá remover todas as aplicações do Office (MSI) do dispositivo de utilizador final. Para obter mais informações, veja [Remover versões MSI do Office existentes ao atualizar para o Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Quando o Intune reinstalar o Office nos computadores dos seus utilizadores finais, estes terão automaticamente os mesmos pacotes de idiomas de que dispunham com instalações anteriores do Office .MSI.

## <a name="select-the-office-365-suite-app-type"></a>Selecione o tipo de aplicativo Office 365 Suite

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
3. Selecione o **Windows 10** na secção **Suite Office 365** do painel do **tipo Select.**
4. Clique em **Selecionar**. Os **passos da Suíte Add Office 365** são apresentados.


## <a name="step-1---app-suite-information"></a>Passo 1 - Informação da suite da aplicação

Neste passo, vai fornecer as informações acerca do conjunto de aplicações. Estas informações ajudam-no a identificar o conjunto de aplicações no Intune e também ajudam os utilizadores a encontrá-lo no portal da empresa.

1. Na página de informações do **suite app,** pode confirmar ou modificar os valores predefinidos:
    - **Nome do Conjunto**: introduza o nome do conjunto de aplicações tal como será apresentado no portal da empresa. Confirme que todos os nomes de conjuntos de aplicações que utiliza são exclusivos. Se o nome de um conjunto de aplicações existir em duplicado, apenas uma das aplicações será apresentada aos utilizadores no portal da empresa.
    - **Descrição do Conjunto**: introduza uma descrição para o conjunto de aplicações. Por exemplo, pode listar as aplicações que selecionou para inclusão.
    - **Publicador**: a Microsoft aparece como o publicador.
    - **Categoria**: em alternativa, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Esta definição irá permitir que os utilizadores encontrem o conjunto de aplicações mais facilmente quando procurarem no portal da empresa.
    - **Mostre-o como uma aplicação em destaque no Portal da Empresa**: Selecione esta opção para exibir a suite de aplicações em destaque na página principal do portal da empresa quando os utilizadores navegam para apps.
    - **URL de Informações**: opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade**: opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: a Microsoft aparece como o programador.
    - **Proprietário**: a Microsoft aparece como o proprietário.
    - **Notas**: introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: o logótipo do Office 365 é apresentado com a aplicação quando os utilizadores procuram no portal da empresa.
2. Clique em **Seguir** para exibir a página de suíte de **aplicação Configure.**

## <a name="step-2---option-1-configure-app-suite-using-the-configuration-designer"></a>Passo 2 - **(Opção 1**) Configure app suite usando o designer de configuração 

Pode escolher um método para configurar a definição de aplicações selecionando um formato de configuração de **configuração**. As opções de formato de definição incluem:
- Designer de configuração
- Introduzir dados XML

Quando escolher o designer de **configuração,** o painel de **aplicações Adicionar** mudará para oferecer três áreas adicionais:
- Configure app suite
- Informações de suíte de aplicativo
- Propriedades

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

1. Na página suite da **configuração** escolha **designer de configuração**.
   - **Selecione aplicações do Office**: Selecione as aplicações padrão do Office que pretende atribuir aos dispositivos, escolhendo as aplicações na lista de dropdown.
   - **Selecione outras aplicações do Office (licença necessária)** : Selecione aplicações adicionais do Office que pretende atribuir aos dispositivos e que tem licenças para escolher as aplicações na lista de dropdown. Estas aplicações incluem aplicações licenciadas, como o cliente do ambiente de trabalho Microsoft Project Online e o Microsoft Visio Online Plan 2.
   - **Arquitetura**: Escolha se pretende atribuir a versão de **32 bits** ou **64 bits** do Office ProPlus. Pode instalar a versão de 32 bits em dispositivos de 32 e de 64 bits, mas só pode instalar a versão de 64 bits em dispositivos de 64 bits.
    - **Atualizar Canal**: selecione a forma como o Office é atualizado nos dispositivos. Para obter mais informações sobre os vários canais de atualização, veja a [Descrição geral dos canais de atualização do Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus). Escolha entre:
        - **Mensalmente**
        - **Via de Atualizações Mensais (Direcionada)**
        - **Via de Atualizações Mensais Semianuais**
        - **Via de Atualizações Mensais Semianuais (Direcionada)**

        Depois de escolher um canal, pode escolher o seguinte:
        - **Remova outras versões**: Escolha **Sim** para remover outras versões do Office (MSI) dos dispositivos do utilizador. Escolha esta opção quando pretender remover o Office pré-existente . Aplicativos MSI de dispositivos de utilizador final. A instalação não será concluída com êxito se existirem aplicações MSI já existentes em dispositivos de utilizador final. As aplicações a desinstalar não se limitam às selecionadas para instalação em **Configurar o Conjunto de Aplicações**, na medida em que irá remover todas as aplicações do Office (MSI) do dispositivo de utilizador final. Para obter mais informações, veja [Remover versões MSI do Office existentes ao atualizar para o Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Quando o Intune reinstalar o Office nos computadores dos seus utilizadores finais, estes terão automaticamente os mesmos pacotes de idiomas de que dispunham com instalações anteriores do Office .MSI. 
        - **Versão a instalar**: Escolha a versão do Office que deve ser instalada.
        - **Versão específica**: Se tiver escolhido **o Specific** como versão **para instalar** na definição acima, pode selecionar para instalar uma versão específica do Office para o canal selecionado nos dispositivos de utilizador final. 
            
            As versões disponíveis serão alteradas ao longo do tempo. Por conseguinte, ao criar uma nova implementação, as versões disponíveis podem ser mais recentes e não ter determinadas versões mais antigas disponíveis. As implementações atuais continuarão a implementar a versão mais antiga, mas a lista de versões será constantemente atualizada por canal.
            
            Para dispositivos que atualizam a respetiva versão fixa (ou quaisquer outras propriedades) e são implementados como disponíveis, o estado de comunicação será apresentado como Instalado se a versão anterior tiver sido instalada até ocorrer a entrada do dispositivo. Quando a entrada do dispositivo ocorrer, o estado será alterado temporariamente para Desconhecido, embora não seja apresentado ao utilizador. Quando o utilizador iniciar a instalação da versão mais recente disponível, o estado será alterado para Instalado.
            
            Para obter mais informações, veja [Overview of update channels for Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus) (Descrição geral dos canais de atualização do Office 365 ProPlus).
    - **Utilizar a ativação de computadores partilhados**:selecione esta opção quando existirem múltiplos utilizadores a partilhar um computador. Para obter mais informações, veja [Overview of shared computer activation for Office 365](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus)(Descrição geral da ativação de computadores partilhados para o Office 365).
    - **Aceitar automaticamente o contrato de licença do utilizador final**: selecione esta opção se não precisar que os utilizadores finais aceitem o contrato de licença. O Intune irá aceitar automaticamente o contrato.
    - **Idiomas**: o Office é instalado automaticamente em qualquer dos idiomas suportados que vierem instalados com o Windows no dispositivo dos utilizadores finais. Selecione esta opção se quiser instalar idiomas adicionais no conjunto de aplicações. <p></p>
        Pode implementar idiomas adicionais para aplicações do Office 365 Pro Plus geridas através do Intune. A lista de idiomas disponíveis inclui o **Tipo** do pacote de idiomas (núcleo, parcial e verificação). No portal Azure, selecione **Microsoft Intune** > **Apps** > **Todas as aplicações** > **Add**. Na lista do **tipo app** do painel de **aplicações Add,** selecione **o Windows 10** no âmbito da **Suite Office 365**. Selecione **Idiomas** no painel de definições da **Suite app.** Para obter informações adicionais, veja [Descrição geral da implementação de idiomas no Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).
2. Clique em **Seguir** para exibir a página **de tags scope.**

## <a name="step-2---option-2-configure-app-suite-using-xml-data"></a>Passo 2 - **(Opção 2**) Configure app suite usando dados XML 

Se tiver selecionado a opção **de dados Enter XML** sob a caixa de dropdown do **formato Definição** na página suite da **app Configure,** pode configurar o suite de aplicações do Office utilizando um ficheiro de configuração personalizado.

![Adicionar designer de configuração do Office 365](./media/apps-add-office365/apps-add-office365-01.png)

1. Adicionei a sua configuração XML.
2. Clique em **Seguir** para exibir a página **de tags scope.**

Para obter mais informações sobre a introdução de dados XML, consulte as opções de [Configuração para a Ferramenta](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)de Implementação do Office .

## <a name="step-3---select-scope-tags-optional"></a>Passo 3 - Selecione etiquetas de âmbito (opcional)
Você pode usar marcas de escopo para determinar quem pode ver as informações do aplicativo cliente no Intune. Para mais detalhes sobre etiquetas de âmbito, consulte [Use o controlo de acesso baseado em funções e as etiquetas](../fundamentals/scope-tags.md)de âmbito para TI distribuídos .

1. Clique em **Selecionar etiquetas** de âmbito para adicionar opcionalmente etiquetas de âmbito para o suite da aplicação. 
2. Clique em **Avançar** para exibir a página **atribuições** .

## <a name="step-4---assignments"></a>Passo 4 - Atribuições

1. Selecione o **Necessário**, **Disponível para dispositivos matriculados,** ou **desinstale** as atribuições do grupo para o suite da aplicação. Para mais informações, consulte [grupos Add para organizar utilizadores e dispositivos](~/fundamentals/groups-add.md) e [atribuir aplicações a grupos com](apps-deploy.md)o Microsoft Intune .
2. Clique em **Seguir** para exibir a página **Review + criar.** 

## <a name="step-5---review--create"></a>Passo 5 - Rever + criar

1. Reveja os valores e configurações que inseriu para a suite da aplicação.
2. Quando terminar, clique em **Criar** para adicionar a app ao Intune.

    A lâmina **de visão geral** da suíte de aplicação Office 365 Window 10 que criou é exibida.

## <a name="deployment-details"></a>Detalhes de implantação

Assim que a política de implementação da Intune for atribuída às máquinas-alvo através do fornecedor de serviços de [configuração do Office (CSP),](https://docs.microsoft.com/windows/client-management/mdm/office-csp)o dispositivo final descarregará automaticamente o pacote de instalação a partir da *localização officecdn.microsoft.com.* Verá dois diretórios a aparecer no diretório de Ficheiros de *Programas:*

![Pacotes de instalação de escritórios no diretório de Ficheiros de Programa](./media/apps-add-office365/office-folder.png)

Sob o diretório do *Microsoft Office,* é criada uma nova pasta onde os ficheiros de instalação são armazenados:

![Nova pasta criada no diretório do Microsoft Office](./media/apps-add-office365/created-folder.png)

Sob o diretório do *Microsoft Office 15,* os ficheiros de instalação Click-to-Run do Office estão armazenados. A instalação iniciar-se-á automaticamente se for necessário o tipo de atribuição:

![Clique para executar ficheiros de lançador de instalação](./media/apps-add-office365/clicktorun-files.png)

A instalação estará em modo silencioso se a atribuição da Suite O365 estiver configurada conforme necessário. Os ficheiros de instalação descarregados serão eliminados assim que a instalação for bem sucedida. Se a atribuição estiver configurada como **disponível,** as aplicações do Office aparecerão na aplicação do Portal da Empresa para que os utilizadores finais possam ativar a instalação manualmente.

## <a name="troubleshooting"></a>Resolução de Problemas
Intune usa a Ferramenta de [Implementação](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool) do Office para descarregar e implementar o Office 365 ProPlus para os seus computadores clientes utilizando o [Office 365 CDN](https://docs.microsoft.com/office365/enterprise/content-delivery-networks). Consulte as melhores práticas descritas no [Managing Office 365 pontos finais](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints) para garantir que a configuração da sua rede permite que os clientes acedam diretamente ao CDN em vez de encaminhar o tráfego de CDN através de proxies centrais para evitar a introdução de latência sussóis.

Execute o Microsoft Support and Recovery Assistant para o [Office 365](https://diagnostics.office.com) num dispositivo direcionado se encontrar problemas de instalação ou tempo de execução.

### <a name="additional-troubleshooting-details"></a>Detalhes adicionais de resolução de problemas

Quando não conseguir instalar as aplicações O365 num dispositivo, deve identificar se o problema está relacionado com Intune ou relacionado com O/Office. Se conseguir ver as duas pastas que o *Microsoft Office* e o Microsoft *Office 15* aparecem no diretório de *Ficheiros* de Programas do dispositivo, pode confirmar que o Intune iniciou a implementação com sucesso. Se não conseguir ver as duas pastas que aparecem nos Ficheiros do *Programa,* deve confirmar os casos abaixo:

- O dispositivo está devidamente matriculado no Microsoft Intune. 
- Existe uma ligação de rede ativa no dispositivo. Se o dispositivo estiver em modo avião, estiver desligado ou estiver num local sem serviço, a política não se aplicará até que a conectividade da rede seja estabelecida.
- Os requisitos de rede intune e office 365 são cumpridos e as gamas IP relacionadas são acessíveis com base nos seguintes artigos:

  - [Requisitos de configuração de rede intune e largura de banda](https://docs.microsoft.com/intune/network-bandwidth-use)
  - [Intervalos de endereços IP e URLs do Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

- Os grupos corretos foram designados para a suíte de aplicação O365. 

Além disso, monitorize o tamanho do diretório *C:\Program Files\Microsoft Office\Updates\Download*. O pacote de instalação descarregado da nuvem Intune será armazenado neste local. Se o tamanho não aumentar ou apenas aumentar muito lentamente, é aconselhável verificar duas vezes a conectividade da rede e a largura de banda.

Uma vez que você pode concluir que tanto intune como a infraestrutura de rede funcionam como esperado, você deve analisar ainda mais a questão do ponto de vista do SISTEMA. Considere as seguintes condições:

- O dispositivo-alvo deve ser executado na Atualização de Criadores do Windows 10 ou posteriormente.
- Não são abertas aplicações existentes do Office enquanto a Intune implementa as aplicações.
- As versões MSI existentes do Office foram corretamente removidas do dispositivo. Intune utiliza o Office Click-to-Run que não é compatível com o Office MSI. Este comportamento é ainda mencionado neste documento:<br>
  [O escritório instalado com click-to-run e o instalador do Windows no mesmo computador não é suportado](https://support.office.com/article/office-installed-with-click-to-run-and-windows-installer-on-same-computer-isn-t-supported-30775ef4-fa77-4f47-98fb-c5826a6926cd)
- O utilizador de sessão deve ter permissão para instalar aplicações no dispositivo.
- Confirme que não existem problemas baseados no registo do Windows Event Viewer **Windows -> ** **Aplicações**.
- Capturar registos verbosos de instalação do Office durante a instalação. Para tal, siga estes passos:<br>
    1. Ative a exploração verbosa para a instalação do Office nas máquinas-alvo. Para tal, execute o seguinte comando para modificar o registo:<br>
        `reg add HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /t REG_DWORD /d 3`<br>
    2. Desloque novamente a Suite Office 365 para os dispositivos-alvo.<br>
    3. Aguarde aproximadamente 15 a 20 minutos e vá para a pasta **%temporária%** e a pasta **%windir%\temp,** classificar por **Data Modificada,** escolha os *ficheiros {Machine Name}-{TimeStamp}.log* que são modificados de acordo com o seu tempo de repro.<br>
    4. Executar o seguinte comando para desativar o registo verboso:<br>
        `reg delete HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /f`<br>
        Os registos verbosos podem fornecer informações mais detalhadas sobre o processo de instalação.

## <a name="errors-during-installation-of-the-app-suite"></a>Erros durante a instalação do conjunto de aplicações

Consulte [como ativar o Registo 365 ProPlus ULS](/office/troubleshoot/diagnostic-logs/how-to-enable-office-365-proplus-uls-logging) para obter informações sobre como visualizar registos de instalação verbosos.

A seguinte tabela lista códigos de erro comuns que poderá encontrar e o seu significado.

### <a name="status-for-office-csp"></a>Estado do CSP do Office

| Estado | Fase | Description |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460 (ERROR_TIMEOUT) | Transferência | Falha ao transferir a Ferramenta de Implementação do Office |
| 13 (ERROR_INVALID_DATA) | - | Não foi possível verificar a assinatura da Ferramenta de Implementação do Office transferida |
| Código de erro de CertVerifyCertificateChainPolicy | - | Falha na verificação de certificação da Ferramenta de Implementação do Office transferida |
| 997 | WIP | A instalar |
| 0 | Após a instalação | Instalação concluída com êxito |
| 1603 (ERROR_INSTALL_FAILURE) | - | Falhou qualquer verificação pré-requisito, como: SxS (Tentei instalar quando 2016 MSI é instalado)Desencontro de versãoOutros |
| 0x8000ffff (E_UNEXPECTED) | - | Tentativa de desinstalação quando a tecnologia Clique-e-Use do Office não existe no computador |
| 17002 | - | Falha ao concluir o cenário (instalação). Possíveis razões:Instalação cancelada pelo utilizadorInstalação cancelada por outra instalaçãoOut do espaço do disco durante a instalaçãoId de idioma desconhecido |
| 17004 | - | SKUs desconhecidos |


### <a name="office-deployment-tool-error-codes"></a>Códigos de erro da Ferramenta de Implementação do Office

| Cenário | Código de retorno | IU | Nota |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------|
| Tentativa de desinstalação quando não existe nenhuma instalação Clique-e-Use ativa | -2147418113, 0x8000ffff ou 2147549183 | Código de Erro: 30088-1008Código de Erro: 30125-1011 (404) | Ferramenta de Implementação do Office |
| Instalação quando já existe uma versão MSI instalada | 1603 | - | Ferramenta de Implementação do Office |
| Instalação cancelada pelo utilizador ou por outra instalação | 17002 | - | Clique-e-Use |
| Tentativa de instalação da versão de 64 bits num dispositivo com a versão de 32 bits instalada. | 1603 | - | Código de retorno da Ferramenta de Implementação do Office |
| Tentativa de instalação de um SKU desconhecido (trata-se de um caso de utilização ilegítima do CSP do Office, visto que devemos passar apenas SKUs válidos) | 17004 | - | Clique-e-Use |
| Falta de espaço | 17002 | - | Clique-e-Use |
| O cliente da versão Clique-e-Use falhou ao iniciar (inesperado) | 17000 | - | Clique-e-Use |
| O cliente da versão Clique-e-Use falhou ao colocar o cenário em fila (inesperado) | 17001 | - | Clique-e-Use |

## <a name="next-steps"></a>Próximos passos

- Para atribuir o suite de aplicações a grupos adicionais, consulte [as aplicações de atribuição a grupos](/intune-azure/manage-apps/deploy-apps).
