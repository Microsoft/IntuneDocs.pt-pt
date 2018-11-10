---
title: Instalar aplicações do Office 365 em dispositivos com o Microsoft Intune
titlesuffix: ''
description: Saiba como pode utilizar o Microsoft Intune para facilitar a instalação das aplicações do Office 365 em dispositivos Windows 10.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 740eee3324a9dc2266b987e119694e2ff70fe2e9
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236378"
---
# <a name="assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Atribuir aplicações do Office 365 a dispositivos Windows 10 com o Microsoft Intune

Este tipo de aplicação faz com que seja mais fácil atribuir aplicações do Office 365 aos dispositivos que gere que executem o Windows 10. Também poderá instalar as aplicações do cliente de ambiente de trabalho do Microsoft Project Online e do Microsoft Visio Pro para Office 365 se tiver as devidas licenças. As aplicações que quer são mostradas como uma entrada única na lista de aplicações na consola do Intune.

> [!NOTE]
> Tem de utilizar licenças do Office 365 ProPlus para ativar as aplicações do Office 365 ProPlus implementadas através do Microsoft Intune. De momento, o Intune não suporta o Office 365 Empresas.

## <a name="before-you-start"></a>Antes de começar

> [!IMPORTANT]
> Se existirem aplicações do Office .msi no dispositivo do utilizador final, tem de utilizar a funcionalidade **Remover MSI** para desinstalar estas aplicações em segurança. Caso contrário, as aplicações do Office 365 fornecidas pelo Intune não serão instaladas com êxito.

- Os dispositivos em que pretende implementar estas aplicações têm de ter a Atualização para Criativos do Windows 10 ou posterior.
- O Intune só suporta a adição de aplicações do Office que pertençam ao conjunto de aplicações Office 365.
- Se estiverem abertas aplicações do Office quando o Intune instalar o conjunto de aplicações, a instalação poderá falhar e os utilizadores poderão perder os dados dos ficheiros não guardados.
- Este método de instalação não é suportado em dispositivos com o Windows 10 S, Windows Home, Windows Team, Windows Holographic ou Windows Holographic for Business.
- O Intune não suporta a instalação de aplicações de ambiente de trabalho do Office 365 da Microsoft Store (denominadas aplicações Office Centennial) num dispositivo em que já implementou aplicações do Office 365 com o Intune. Se instalar esta configuração, poderá causar perda ou danos em dados.
- As múltiplas atribuições de aplicações necessárias ou disponíveis não são acumulativas. Uma atribuição de aplicação posterior irá substituir as atribuições de aplicações instaladas pré-existentes. Por exemplo, se o primeiro conjunto de aplicações do Office incluir o Word, mas o conjunto posterior não o incluir, o Word será desinstalado. Esta condição não se aplica às aplicações Visio ou Project.
- **Versão do Office**: selecione se pretende atribuir a versão de 32 bits ou de 64 bits do Office. Pode instalar a versão de 32 bits em dispositivos de 32 e de 64 bits, mas só pode instalar a versão de 64 bits em dispositivos de 64 bits.
- **Remover MSI dos dispositivos de utilizador final**: escolha se pretende remover as aplicações .MSI do Office já existentes dos dispositivos de utilizador final. A instalação não será concluída com êxito se existirem aplicações MSI já existentes em dispositivos de utilizador final. As aplicações a desinstalar não se limitam às selecionadas para instalação em **Configurar o Conjunto de Aplicações**, na medida em que irá remover todas as aplicações do Office (MSI) do dispositivo de utilizador final. Para obter mais informações, veja [Remover versões MSI do Office existentes ao atualizar para o Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Quando o Intune reinstalar o Office nos computadores dos seus utilizadores finais, estes terão automaticamente os mesmos pacotes de idiomas de que dispunham com instalações anteriores do Office .MSI.

## <a name="get-started"></a>Introdução

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os Serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. No painel da carga de trabalho **Aplicações do cliente**, em **Gerir**, selecione **Aplicações**.
5. Selecione **Adicionar**.
6. No painel **Adicionar aplicações**, na lista **Tipo de aplicação**, em **Conjunto de Aplicações do Office 365**, selecione **Windows 10**.

Agora pode configurar o conjunto de aplicações.

## <a name="configure-the-app-suite"></a>Configurar o conjunto de aplicações

Selecione as aplicações do Office que quer atribuir aos dispositivos.

1. No painel **Adicionar Aplicação**, selecione **Configurar Conjunto de Aplicações**.
2. No painel **Configurar Conjunto de Aplicações**, selecione as aplicações padrão do Office que quer atribuir aos dispositivos.  
    Além disso, poderá instalar aplicações do cliente de ambiente de trabalho do Microsoft Project Online e do Microsoft Visio Pro para Office 365 se tiver as devidas licenças.
3. Selecione **OK**.

## <a name="configure-app-information"></a>Configurar as informações da aplicação

Neste passo, vai fornecer as informações acerca do conjunto de aplicações. Estas informações ajudam-no a identificar o conjunto de aplicações no Intune e também ajudam os utilizadores a encontrá-lo no portal da empresa.

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

## <a name="configure-app-settings"></a>Configurar as definições da aplicação

Neste passo, configure as opções de instalação do conjunto de aplicações. As definições aplicam-se a todas as aplicações que adicionou ao conjunto.

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

## <a name="finish-up"></a>Concluir

Quando tiver concluído, no painel **Adicionar Aplicação**, selecione **Adicionar**. A aplicação que criou é apresentada na lista de aplicações.

## <a name="errors-during-installation-of-the-app-suite"></a>Erros durante a instalação do conjunto de aplicações

A seguinte tabela lista códigos de erro comuns que poderá encontrar e o seu significado.

### <a name="status-for-office-csp"></a>Estado do CSP do Office

||||
|-|-|-|
|Estado|Fase|Descrição|
|1460 (ERROR_TIMEOUT)|Transferência|Falha ao transferir a Ferramenta de Implementação do Office|    
|13 (ERROR_INVALID_DATA)|-|Não foi possível verificar a assinatura da Ferramenta de Implementação do Office transferida|
|Código de erro de CertVerifyCertificateChainPolicy|-|Falha na verificação de certificação da Ferramenta de Implementação do Office transferida|    
|997|WIP|A instalar|
|0|Após a instalação|Instalação concluída com êxito|    
|1603 (ERROR_INSTALL_FAILURE)|-|Falha numa verificação de pré-requisitos, como:<ul><li>SxS (tentativa de instalação quando o MSI do Office 2016 se encontra instalado)</li><li>Erro de correspondência de versão</li><li>Outros</li></ul>|  
|0x8000ffff (E_UNEXPECTED)|-|Tentativa de desinstalação quando a tecnologia Clique-e-Use do Office não existe no computador|     
|17002|-|Falha ao concluir o cenário (instalação). Motivos possíveis:<ul><li>Instalação cancelada pelo utilizador</li><li>Instalação cancelada por outra instalação</li><li>Falta de espaço em disco durante a instalação</li><li>ID de idioma desconhecido</li></ul>|
|17004|-|SKUs desconhecidos|   


### <a name="office-deployment-tool-error-codes"></a>Códigos de erro da Ferramenta de Implementação do Office

|||||
|-|-|-|-|
|Cenário|Código de retorno|IU|Nota|
|Tentativa de desinstalação quando não existe nenhuma instalação Clique-e-Use ativa|-2147418113, 0x8000ffff ou 2147549183|Código de Erro: 30088-1008<br>Código de Erro: 30125-1011 (404)|Ferramenta de Implementação do Office|
|Instalação quando já existe uma versão MSI instalada|1603|-|Ferramenta de Implementação do Office|
|Instalação cancelada pelo utilizador ou por outra instalação|17002|-|Clique-e-Use|
|Tentativa de instalação da versão de 64 bits num dispositivo com a versão de 32 bits instalada.|1603|-|Código de retorno da Ferramenta de Implementação do Office|
|Tentativa de instalação de um SKU desconhecido (trata-se de um caso de utilização ilegítima do CSP do Office, visto que devemos passar apenas SKUs válidos)|17004|-|Clique-e-Use|
|Falta de espaço|17002|-|Clique-e-Use|
|O cliente da versão Clique-e-Use falhou ao iniciar (inesperado)|17000|-|Clique-e-Use|
|O cliente da versão Clique-e-Use falhou ao colocar o cenário em fila (inesperado)|17001|-|Clique-e-Use|

## <a name="next-steps"></a>Próximos passos

- Para atribuir as aplicações aos grupos que escolher, veja [Atribuir aplicações a grupos](/intune-azure/manage-apps/deploy-apps).
