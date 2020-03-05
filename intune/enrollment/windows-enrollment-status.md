---
title: Configurar uma página de estado de inscrição
titleSuffix: Microsoft Intune
description: Configure uma página de saudação para os utilizadores que inscrevem dispositivos Windows 10.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: ericor
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 232d4841d71d738b4f099437fb4845928d887dd5
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78290315"
---
# <a name="set-up-an-enrollment-status-page"></a>Configurar uma página de estado de inscrição
 
[!INCLUDE [azure_portal](../includes/azure_portal.md)]
 
A Página de Estado de Inscrição (ESP) exibe informações de instalação sobre dispositivos Windows 10 (versão 1803 e posterior) durante a inscrição inicial do dispositivo. Por exemplo:
- ao utilizar [o Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/) 
- ou sempre que um dispositivo gerido é iniciado pela primeira vez após a aplicação de uma política da Página de Estado de Inscrição. 

A Página de Estado de Inscrição ajuda os utilizadores a compreender o estado do seu dispositivo durante a configuração do dispositivo. Pode criar vários perfis da Página de Estado de Inscrição e aplicá-los a diferentes grupos que contenham utilizadores. Os perfis podem ser definidos para:
- Ver o progresso da instalação.
- Bloquear a utilização até à conclusão da instalação.
- Especificar o que um utilizador pode fazer se a configuração do dispositivo falhar.

Também pode definir a ordem prioritária para que cada perfil tenha a responsabilidade de atribuições de perfil conflituosas ao mesmo utilizador.

> [!NOTE]
> A Página de Estado de Inscrição só pode ser direcionada a um utilizador que pertença a um grupo designado e a política é definida no dispositivo no momento da inscrição para todos os utilizadores que utilizem o dispositivo.  

## <a name="available-settings"></a>Definições disponíveis

 As seguintes definições podem ser configuradas para personalizar o comportamento da Página de Estado de Inscrição:

<table>
<th align="left">Definição<th align="left">Sim<th align="left">Não
<tr><td>Mostrar o progresso da instalação de aplicativos e perfis<td>A página de estado da inscrição é apresentada.<td>A página do estado da inscrição não está apresentada.
<tr><td>Bloqueie a utilização do dispositivo até que todas as aplicações e perfis estejam instalados<td>As definições nesta tabela são disponibilizadas para personalizar o comportamento da página de estado de inscrição, para que o utilizador possa resolver potenciais problemas de instalação.
<td>A página de estado de inscrição é apresentada sem opções adicionais para resolver falhas de instalação.
<tr><td>Permitir que os utilizadores reporem o dispositivo se ocorrer erro de instalação<td>É apresentado um botão de <b>reset</b> do dispositivo se houver uma falha de instalação.<td>O botão do <b>dispositivo Reset</b> não é apresentado se houver uma falha de instalação.
<tr><td>Permitir que os utilizadores utilizem o dispositivo se ocorrer erro de instalação<td>Um botão <b>Continue de qualquer forma</b> é exibido se houver uma falha de instalação.<td>O botão Continue de <b>qualquer forma</b> não é exibido se houver uma falha de instalação.
<tr><td>Mostre o erro de tempo quando a instalação demorar mais tempo do que o número especificado de minutos<td colspan="2">Especifique o número de minutos para esperar que a instalação esteja concluída. Um valor padrão de 60 minutos é introduzido.
<tr><td>Mostre mensagem personalizada quando ocorrer um erro<td>É fornecida uma caixa de texto onde pode especificar uma mensagem personalizada para visualizar se ocorrer um erro de instalação.<td>A mensagem predefinida é apresentada: <br><b>A Instalação excedeu o prazo fixado pela sua organização. Tente novamente ou contacte a pessoa de suporte de TI para obter ajuda.<b>
<tr><td>Permitir que os utilizadores recolham registos sobre erros de instalação<td>Se houver um erro de instalação, é apresentado um botão <b>de registos Collect.</b> <br>Se o utilizador clicar neste botão, é-lhes pedido que escolham um local para guardar o ficheiro de registo <b>MDMDiagReport.cab</b><td>O botão <b>de registos Collect</b> não é apresentado se houver um erro de instalação.
<tr><td>Bloqueie a utilização do dispositivo até que estas aplicações necessárias sejam instaladas se forem atribuídas ao utilizador/dispositivo<td colspan="2">Escolha <b>Todos</b> ou <b>Selecionados.</b> <br><br>Se <b>o Selected</b> for escolhido, aparece um botão de <b>aplicações Select</b> que lhe permite escolher quais as aplicações que devem ser instaladas antes de ativar o dispositivo.
</table>

## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Ativar página de estado de inscrição padrão para todos os utilizadores

Para ligar a Página de Estado de Inscrição, siga os passos abaixo.
 
1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **dispositivos** > **Windows** > Windows > Página de Estado de **Inscrição** .
2. No painel **Página de Estado de Inscrição**, selecione **Predefinição** > **Definições**.
3. Para **Mostrar progresso de instalação de aplicações e perfis**, selecione **Sim**.
4. Selecione as outras definições que pretende ativar e, em seguida, selecione **Guardar**.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>Criar perfil de página de estado de inscrição e atribuir a um grupo

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **dispositivos** > **Windows** > Windows página de estado de **inscriç > ão** > Criar o **perfil**.
2. Forneça um **Nome** e uma **Descrição**.
3. Selecione **Criar**.
4. Selecione o novo perfil na lista **Página de Estado de Inscrição**.
5. Selecione **Atribuições** > **Selecionar grupos** > selecione os grupos que pretende que adotem este perfil > **Selecionar** > **Guardar**.
6. Selecione **Definições** > selecione as definições que pretende aplicar a este perfil > **Guardar**.

## <a name="set-the-enrollment-status-page-priority"></a>Definir a prioridade de página de estado de inscrição

Um utilizador pode estar em muitos grupos e ter muitos perfis de Página de Estado de Inscrição. Para lidar com tais conflitos, pode definir as prioridades para cada perfil. Durante a inscrição, se alguém tiver mais do que um perfil de Página de Estado de Inscrição, apenas o perfil de prioridade mais elevado é aplicado ao dispositivo de inscrição.

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **dispositivos** > **Windows** > Windows > Página de Estado de **Inscrição** .
2. Paire o cursor sobre o perfil na lista.
3. Utilize os três pontos verticais para arrastar o perfil para a posição pretendida na lista.

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>Bloquear o acesso a um dispositivo até que uma aplicação específica esteja instalada

Pode especificar que aplicações têm de ser instaladas para o utilizador poder aceder à área de trabalho.

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **dispositivos** > **Windows** > Windows > Página de Estado de **Inscrição** .
2. Escolha um perfil > **Definições**.
3. Escolha **Sim** para **Mostrar progresso de instalação de aplicações e perfis**.
4. Escolha **Sim** para **Bloquear a utilização de dispositivos até que todas as aplicações e perfis sejam instalados**.
5. Escolha **selecionado** para utilização do dispositivo Block até que **estas aplicações necessárias sejam instaladas se forem atribuídas ao utilizador/dispositivo**.
6. Escolha **Selecionar aplicações** > escolha as aplicações > **Selecionar** > **Guardar**.

## <a name="enrollment-status-page-tracking-information"></a>Informação de rastreio da página de estado de inscrição

Existem três fases em que a Página de Estado de Inscrição rastreia informações; preparação do dispositivo, configuração do dispositivo e configuração da conta.

### <a name="device-preparation"></a>Preparação do dispositivo

Para a preparação do dispositivo, a página do estado de inscrição rastreia:
- Atestados de chave de módulo de plataforma fidedigno (TPM) (quando aplicável)
- progressos na adesão ao Azure Ative Directory
- matriculando-se em Intune
- instalação de extensões de gestão Intune

### <a name="device-setup"></a>Configuração do dispositivo

A Página de Estado de Inscrição rastreia os seguintes itens de configuração do dispositivo (se forem atribuídos a Todos os Dispositivos ou a um grupo de dispositivos em que o dispositivo de inscrição é membro):
- Políticas de segurança
  - Um fornecedor de serviços de configuração (CSO) para todas as inscrições.
  - Os CSPs configurados pelo Intune não são controlados aqui.
- Aplicações
  - Aplicações de linha de negócio (LoB) por computador.
  - As aplicações da loja de linha de negócio com contexto de instalação = Dispositivo.
  - As aplicações da loja e aplicações offline de linha de negócio com contexto de instalação = Dispositivo.
  - Aplicações Win32 (versão 10 do Windows 10 e apenas mais recentes) 
- Perfis de conectividade
  - Perfis de VPN ou de Wi-Fi atribuídos a **Todos os Dispositivos** ou a um grupo de dispositivos em que o dispositivo que está a ser inscrito é membro, mas apenas para dispositivos do Autopilot
- Perfis de certificado Wi-Fi atribuídos a **Todos os Dispositivos** ou a um grupo de dispositivos em que o dispositivo que está a ser inscrito é membro, mas apenas para dispositivos do Autopilot

### <a name="account-setup"></a>Configuração da conta
Para a configuração da conta, a Página de Estado de Inscrição rastreia os seguintes itens se forem atribuídos à corrente registada no utilizador:
- Políticas de segurança
  - Um CSP para todas as inscrições.
  - Os CSPs configurados pelo Intune não são controlados aqui.
- Aplicações
  - Aplicações MSI de linha de negócio por utilizador atribuídas a Todos os Dispositivos, Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.
  - Aplicações MSI de linha de negócio por computador atribuídas a Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.
  - Aplicações de loja LoB, aplicativos de loja online e aplicações de loja offline que são atribuídas a qualquer um dos seguintes objetos:
    - Todos os Dispositivos
    - Todos os Utilizadores
    - Um grupo de utilizadores em que o utilizador que está a inscrever o dispositivo é um membro com o contexto de instalação definido para o Utilizador.
  - Aplicações Win32 (versão 10 do Windows 10 e apenas mais recentes) 
- Perfis de conectividade
  - Perfis de VPN e de Wi-Fi atribuídos a Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.
- Certificados
  - Perfis de certificados atribuídos a Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.

### <a name="troubleshooting"></a>Resolução de Problemas
Perguntas de topo para resolução de problemas.

- Porque é que as minhas aplicações não foram instaladas durante a fase de configuração do Dispositivo durante a implementação do Autopilot que está a utilizar a Página de Estado de Inscrição?
  - Para garantir que as aplicações são instaladas durante uma fase de configuração do Dispositivo Autopilot, certifique-se de que 
        1. A aplicação é selecionada para bloquear o acesso na lista de aplicações selecionadas
        2. Está a direcionar as aplicações para o mesmo grupo de dispositivos Azure AD a que o seu perfil autopiloto está atribuído. 

- Porque é que a Página de Estado de Inscrição está a mostrar para implementações não autopilotos, por exemplo quando um utilizador faz login pela primeira vez num dispositivo matriculado de cogestão do Gestor de Configuração?  
  - A Página de Estado de Inscrição lista o estado de instalação de todos os métodos de inscrição, incluindo
      - Piloto automático
      - Cogestão do Gestor de Configuração
      - quando qualquer novo utilizador entrar no dispositivo que tenha a política da Página de Estado de Inscrição aplicada pela primeira vez
      - quando a página única **para dispositivos aprovisionados por uma definição de experiência fora da caixa (OOBE)** estiver em vigor e a política for definida, apenas o primeiro utilizador que assina no dispositivo obtém a Página de Estado de Inscrição

- Como posso desativar a Página de Estado de Inscrição se foi configurada no dispositivo?
  - A política da página de estado de inscrição é definida num dispositivo no momento da inscrição. Para desativar a Página do Estado de Inscrição, deve desativar as secções da página de estado de inscrição do utilizador e do dispositivo. Desativa as secções criando configurações oMA-URI personalizadas com as seguintes configurações.

      Desativar a página de estado de inscrição do utilizador:

      ```
      Name:  Disable User ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipUserStatusPage
      Data type:  Boolean
      Value:  True 
      ```
      Desativar a página de estado de inscrição do dispositivo:

      ```
      Name:  Disable Device ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipDeviceStatusPage
      Data type:  Boolean
      Value:  True 
      ```
- Como posso recolher ficheiros de registo?
  - Existem duas formas de recolher ficheiros de registo da Página de Inscrição:
      - Ativar a capacidade de os utilizadores recolherem registos na política de ESP. Quando ocorre um intervalo na Página de Estado de Inscrição, o utilizador final pode escolher a opção de **recolher registos**. Ao inserir uma unidade USB, os ficheiros de registo podem ser copiados para a unidade
      - Abra um pedido de comando inserindo a sequência de teclas Shift-F10 e, em seguida, introduza a seguinte linha de comando para gerar os ficheiros de registo: 

      ```
      mdmdiagnosticstool.exe -area Autopilot -cab <pathToOutputCabFile>.cab 
      ```

### <a name="known-issues"></a>Problemas conhecidos
Abaixo estão as questões conhecidas. 
- Desativar o perfil esp não remove a política de ESP dos dispositivos e os utilizadores ainda recebem ESP quando iniciam sessão no dispositivo pela primeira vez. A política não é removida quando o perfil da ESP é desativado. Tem de implantar o OMA-URI para desativar o ESP. Consulte acima as instruções sobre como desativar a ESP utilizando o OMA-URI. 
- Um reboot pendente irá sempre causar um intervalo. O tempo de tempo ocorre porque o dispositivo precisa de ser reiniciado. O reboot é necessário para permitir que o item rastreado na Página de Estado de Inscrição seja concluído. Um reboot fará com que a Página de Estado de Inscrição saia e depois de reiniciar o dispositivo não entrará durante a configuração da Conta após o reboot.  Considere não necessitar de um reboot com instalação de aplicação. 
- Um reboot durante a configuração do Dispositivo obrigará o utilizador a introduzir as suas credenciais antes da transição para a fase de configuração da Conta. As credenciais do utilizador não são preservadas durante o reboot. Para que o utilizador introduza as suas credenciais e a Página de Estado de Inscrição pode continuar. 
- A Página de Estado de Inscrição irá sempre descontar durante uma inscrição de conta de adicionar e conta escolar nas versões do Windows 10 menos de 1903. A Página de Estado de Inscrição aguarda que o registo da AD Azure esteja concluído. O problema encontra-se corrigido na versão 1903 do Windows 10 e mais recente.  
- A implantação do Autopilot Hybrid Azure AD com ESP demora mais tempo do que a duração do tempo definido no perfil ESP. Nas implementações híbridas azure ad autopiloto, o ESP demorará 40 minutos mais longo do que o valor estabelecido no perfil ESP. Este atraso dá tempo ao conector AD on-prem para criar o novo registo do dispositivo para a AD Azure. 
- A página de início de sessão do Windows não é pré-povoada com o nome de utilizador no Modo Autopilot User Driven. Se houver um reboot durante a fase de configuração do dispositivo da ESP:
    - as credenciais do utilizador não são preservadas
    - o utilizador deve voltar a introduzir as credenciais antes de proceder da fase de configuração do dispositivo para a fase de configuração da Conta
- A ESP está presa durante muito tempo ou nunca completa a fase de "Identificação". Intune calcula as políticas do ESP durante a fase de identificação. Um dispositivo pode nunca completar as políticas de ESP de computação se o utilizador atual não tiver um Intune licenciado atribuído.  
- Configurar o Controlo de Aplicações do Microsoft Defender provoca uma rápida reinicialização durante o Autopilot. Configurar a aplicação Microsoft Defender (AppLocker CSP) requer um reboot. Quando esta política estiver configurada, pode fazer com que um dispositivo reinicie durante o Autopilot. Atualmente, não há como suprimir ou adiar o reboot.
- Quando a política DeviceLock (https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) estiver ativada como parte de um perfil ESP, o autologon OOBE ou do ambiente de trabalho do utilizador pode falhar sem expectante por duas razões.
  - Se o dispositivo não tiver sido reiniciado antes de sair da fase de configuração do Dispositivo ESP, o utilizador poderá ser solicitado a introduzir as suas credenciais De AD Azure. Esta solicitação ocorre em vez de um autologon bem sucedido onde o utilizador vê a primeira animação de login do Windows.
  - O autologon falhará se o dispositivo tiver sido reiniciado após o utilizador ter introduzido as suas credenciais De AD Azure, mas antes de sair da fase de configuração do Dispositivo ESP. Esta falha ocorre porque a fase de configuração do Dispositivo ESP nunca foi concluída. A supõeção é redefinir o dispositivo.

## <a name="next-steps"></a>Próximos passos
Depois de configurar as suas páginas de inscrição do Windows, saiba como gerir dispositivos Windows. Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](../remote-actions/device-management.md)
