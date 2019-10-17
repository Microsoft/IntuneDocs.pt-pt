---
title: Configurar uma página de status de registro
titleSuffix: Microsoft Intune
description: Configure uma página de saudação para os utilizadores que inscrevem dispositivos Windows 10.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2019
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
ms.openlocfilehash: d2a6b427552e545421e329b900833c889e67bf35
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503035"
---
# <a name="set-up-an-enrollment-status-page"></a>Configurar uma página de status de registro
 
[!INCLUDE [azure_portal](../includes/azure_portal.md)]
 
A página de status de registro (ESP) exibe informações de instalação sobre dispositivos Windows 10 (versão 1803 e posterior) durante o registro inicial do dispositivo. Por exemplo:
- ao usar o [Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/) 
- ou sempre que um dispositivo gerenciado for iniciado pela primeira vez depois que uma política de página de status de registro tiver sido aplicada. 

A página de status de registro ajuda os usuários a entender o status de seus dispositivos durante a configuração do dispositivo. Você pode criar vários perfis de página de status de registro e aplicá-los a grupos diferentes que contêm usuários. Os perfis podem ser definidos para:
- Ver o progresso da instalação.
- Bloquear a utilização até à conclusão da instalação.
- Especificar o que um utilizador pode fazer se a configuração do dispositivo falhar.

Você também pode definir a ordem de prioridade de cada perfil para considerar as atribuições de perfil conflitantes para o mesmo usuário.

> [!NOTE]
> A página de status de registro só pode ser destinada a um usuário que pertence a um grupo atribuído e a política é definida no dispositivo no momento do registro para todos os usuários que usam o dispositivo.  

## <a name="available-settings"></a>Configurações disponíveis

 As configurações a seguir podem ser definidas para personalizar o comportamento da página de status de registro:

<table>
<th align="left">Definição<th align="left">Sim<th align="left">Não
<tr><td>Mostrar o progresso da instalação do aplicativo e do perfil<td>A página status do registro é exibida.<td>A página status do registro não é exibida.
<tr><td>Bloquear o uso do dispositivo até que todos os aplicativos e perfis sejam instalados<td>As configurações nessa tabela são disponibilizadas para personalizar o comportamento da página de status de registro, para que o usuário possa resolver possíveis problemas de instalação.
<td>A página status do registro é exibida sem opções adicionais para tratar falhas de instalação.
<tr><td>Permitir que os usuários redefinam o dispositivo se ocorrer um erro de instalação<td>Um botão <b>Redefinir dispositivo</b> será exibido se houver uma falha na instalação.<td>O botão <b>Redefinir dispositivo</b> não será exibido se houver uma falha na instalação.
<tr><td>Permitir que os usuários usem o dispositivo se ocorrer um erro de instalação<td>Um botão <b>continuar qualquer assim</b> será exibido se houver uma falha na instalação.<td>O botão <b>continuar mesmo assim</b> não será exibido se houver uma falha na instalação.
<tr><td>Mostrar erro de tempo limite quando a instalação demorar mais do que o número especificado de minutos<td colspan="2">Especifique o número de minutos a aguardar a conclusão da instalação. Um valor padrão de 60 minutos é inserido.
<tr><td>Mostrar mensagem personalizada quando ocorrer um erro<td>Uma caixa de texto é fornecida onde você pode especificar uma mensagem personalizada para exibir se ocorrer um erro de instalação.<td>A mensagem padrão é exibida: <br><b>Installation excedeu o limite de tempo definido por sua organização. Tente novamente ou contate a pessoa de suporte de ti para obter ajuda. <b> @ no__t-1<tr><td>Permitir que os usuários coletem logs sobre erros de instalação<td>Se houver um erro de instalação, um botão <b>coletar logs</b> será exibido. <br>Se o usuário clicar nesse botão, será solicitado a escolher um local para salvar o arquivo de log <b>MDMDiagReport. cab</b><td>O botão <b>coletar logs</b> não será exibido se houver um erro de instalação.
<tr><td>Bloquear o uso do dispositivo até que esses aplicativos necessários sejam instalados se eles forem atribuídos ao usuário/dispositivo<td colspan="2">Escolha <b>tudo</b> ou <b>selecionado</b>. <br><br>Se <b>selecionado</b> for escolhido, um botão <b>selecionar aplicativos</b> será exibido, permitindo que você escolha quais aplicativos devem ser instalados antes de habilitar o dispositivo.
</table>

## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Ativar a página de status de registro padrão para todos os usuários

Para ativar a página status do registro, siga as etapas abaixo.
 
1. No [Intune](https://aka.ms/intuneportal), escolha **registro de dispositivo** > **registro do Windows** > **página status de registro**.
2. No painel **Página de Estado de Inscrição**, selecione **Predefinição** > **Definições**.
3. Para **Mostrar progresso de instalação de aplicações e perfis**, selecione **Sim**.
4. Selecione as outras definições que pretende ativar e, em seguida, selecione **Guardar**.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>Criar perfil de página de status de registro e atribuir a um grupo

1. No [Intune](https://aka.ms/intuneportal), escolha **registro de dispositivo**@no__t-**2 registro do Windows** > **página status de registro** > **Criar perfil**.
2. Forneça um **Nome** e uma **Descrição**.
3. Selecione **Criar**.
4. Selecione o novo perfil na lista **Página de Estado de Inscrição**.
5. Selecione **Atribuições** > **Selecionar grupos** > selecione os grupos que pretende que adotem este perfil > **Selecionar** > **Guardar**.
6. Selecione **Definições** > selecione as definições que pretende aplicar a este perfil > **Guardar**.

## <a name="set-the-enrollment-status-page-priority"></a>Definir a prioridade de página de estado de inscrição

Um usuário pode estar em muitos grupos e ter muitos perfis de página de status de registro. Para lidar com esses conflitos, você pode definir as prioridades para cada perfil. Ao registrar, se alguém tiver mais de um perfil de página de status de registro, somente o perfil de prioridade mais alta será aplicado ao dispositivo registrado.

1. No [Intune](https://aka.ms/intuneportal), escolha **registro de dispositivo** > **registro do Windows** > **página status de registro**.
2. Paire o cursor sobre o perfil na lista.
3. Utilize os três pontos verticais para arrastar o perfil para a posição pretendida na lista.

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>Bloquear o acesso a um dispositivo até que uma aplicação específica esteja instalada

Pode especificar que aplicações têm de ser instaladas para o utilizador poder aceder à área de trabalho.

1. No Intune, escolha **registro de dispositivo** > **registro do Windows** > **página status de registro**.
2. Escolha um perfil > **Definições**.
3. Escolha **Sim** para **Mostrar progresso de instalação de aplicações e perfis**.
4. Escolha **Sim** para **Bloquear a utilização de dispositivos até que todas as aplicações e perfis sejam instalados**.
5. Escolha **selecionado** para **bloquear o uso do dispositivo até que esses aplicativos necessários sejam instalados se eles forem atribuídos ao usuário/dispositivo**.
6. Escolha **Selecionar aplicações** > escolha as aplicações > **Selecionar** > **Guardar**.

## <a name="enrollment-status-page-tracking-information"></a>Informações de rastreamento de página de status de registro

Há três fases em que a página de status de registro rastreia informações; preparação do dispositivo, configuração do dispositivo e configuração da conta.

### <a name="device-preparation"></a>Preparação do dispositivo

Para a preparação do dispositivo, a página de status de registro acompanha:
- Atestado de chave de Trusted Platform Module (TPM) (quando aplicável)
- progresso ao ingressar no Azure Active Directory
- registrando no Intune
- instalação das extensões de gerenciamento do Intune

### <a name="device-setup"></a>Configuração do dispositivo

A página de status de registro acompanha os seguintes itens de configuração de dispositivo (se eles forem atribuídos a todos os dispositivos ou um grupo de dispositivos no qual o dispositivo de registro é um membro):
- Políticas de segurança
  - Um fornecedor de serviços de configuração (CSO) para todas as inscrições.
  - Os CSPs configurados pelo Intune não são controlados aqui.
- Aplicações
  - Aplicações de linha de negócio (LoB) por computador.
  - As aplicações da loja de linha de negócio com contexto de instalação = Dispositivo.
  - As aplicações da loja e aplicações offline de linha de negócio com contexto de instalação = Dispositivo.
  - Aplicativos Win32 (somente Windows 10 versão 1903 e mais recentes) 
- Perfis de conectividade
  - Perfis de VPN ou de Wi-Fi atribuídos a **Todos os Dispositivos** ou a um grupo de dispositivos em que o dispositivo que está a ser inscrito é membro, mas apenas para dispositivos do Autopilot
- Perfis de certificado Wi-Fi atribuídos a **Todos os Dispositivos** ou a um grupo de dispositivos em que o dispositivo que está a ser inscrito é membro, mas apenas para dispositivos do Autopilot

### <a name="account-setup"></a>Configuração da conta
Para a configuração da conta, a página status do registro acompanhará os seguintes itens se eles forem atribuídos ao usuário conectado no momento:
- Políticas de segurança
  - Um CSP para todas as inscrições.
  - Os CSPs configurados pelo Intune não são controlados aqui.
- Aplicações
  - Aplicações MSI de linha de negócio por utilizador atribuídas a Todos os Dispositivos, Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.
  - Aplicações MSI de linha de negócio por computador atribuídas a Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.
  - Aplicativos da loja de LoB, aplicativos da loja online e aplicativos da loja offline que são atribuídos a qualquer um dos seguintes objetos:
    - Todos os Dispositivos
    - Todos os Utilizadores
    - Um grupo de usuários no qual o usuário que está registrando o dispositivo é membro do contexto de instalação definido como usuário.
  - Aplicativos Win32 (somente Windows 10 versão 1903 e mais recentes) 
- Perfis de conectividade
  - Perfis de VPN e de Wi-Fi atribuídos a Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.
- Certificados
  - Perfis de certificados atribuídos a Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.

### <a name="troubleshooting"></a>Resolução de Problemas
Principais perguntas para solução de problemas.

- Por que meus aplicativos não foram instalados durante a fase de configuração do dispositivo durante a implantação do AutoPilot que está usando a página de status de registro?
  - Para garantir que os aplicativos sejam instalados durante uma fase de configuração de dispositivo do piloto automático, verifique se 
        1. O aplicativo é selecionado para bloquear o acesso na lista de aplicativos selecionados
        2. Você está direcionando os aplicativos para o mesmo grupo de dispositivos do Azure AD ao qual seu perfil do AutoPilot está atribuído. 

- Por que a página de status de registro é mostrada para implantações não autopiloto, por exemplo, quando um usuário faz logon pela primeira vez em um dispositivo registrado de cogerenciamento de Configuration Manager?  
  - A página status do registro lista o status da instalação para todos os métodos de registro, incluindo
      - AutoPilot
      - Configuration Manager cogerenciamento
      - Quando um novo usuário fizer logon no dispositivo que tem a política da página de status de registro aplicada pela primeira vez

- Como posso desabilitar a página status do registro se ela tiver sido configurada no dispositivo?
  - A política de página de status de registro está definida em um dispositivo no momento do registro. Para desabilitar a página de status de registro, você deve desabilitar as seções de página de status de registro de usuário e dispositivo. Desabilite as seções criando configurações personalizadas de OMA-URI com as seguintes configurações.

      Página desabilitar status de registro de usuário:

      ```
      Name:  Disable User ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipUserStatusPage
      Data type:  Boolean
      Value:  True 
      ```
      Página desabilitar status de registro de dispositivo:

      ```
      Name:  Disable Device ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipDeviceStatusPage
      Data type:  Boolean
      Value:  True 
      ```
- Como posso coletar arquivos de log?
  - Há duas maneiras de coletar os arquivos de log da página de status do registro:
      - Habilite a capacidade dos usuários de coletar logs na política ESP. Quando ocorre um tempo limite na página status do registro, o usuário final pode escolher a opção para **coletar logs**. Ao inserir uma unidade USB, os arquivos de log podem ser copiados para a unidade
      - Abra um prompt de comando inserindo a sequência de teclas Shift-F10 e, em seguida, insira a linha de comando a seguir para gerar os arquivos de log: 

      ```
      mdmdiagnosticstool.exe -area Autopilot -cab <pathToOutputCabFile>.cab 
      ```

### <a name="known-issues"></a>Problemas conhecidos
Abaixo estão os problemas conhecidos. 
- Desabilitar o perfil ESP não remove a política ESP de dispositivos e os usuários ainda obtêm o ESP ao fazer logon no dispositivo pela primeira vez. A política não é removida quando o perfil ESP está desabilitado. Você deve implantar o OMA-URI para desabilitar o ESP. Consulte acima para obter instruções sobre como desabilitar o ESP usando o OMA-URI. 
- Uma reinicialização pendente sempre causará um tempo limite. O tempo limite ocorre porque o dispositivo precisa ser reinicializado. A reinicialização é necessária para permitir que o item rastreado na página de status de registro seja concluído. Uma reinicialização fará com que a página status do registro saia e depois da reinicialização o dispositivo não entrará durante a configuração da conta após a reinicialização  Considere não exigir uma reinicialização com a instalação do aplicativo. 
- Uma reinicialização durante a instalação do dispositivo forçará o usuário a inserir suas credenciais antes de fazer a transição para a fase de configuração de conta. As credenciais do usuário não são preservadas durante a reinicialização. Faça com que o usuário insira suas credenciais e a página status do registro possa continuar. 
- Os certificados SCEP com as políticas do Windows Hello para empresas causarão tempo limite porque o usuário não pode concluir a configuração do PIN de saudação para permitir a competição da instalação do certificado SCEP.  Nenhuma solução alternativa. A correção ETA é o verão 2019. 
- A página de status de registro sempre atingirá o tempo limite durante uma adição de registro de conta corporativa e de estudante em versões do Windows 10 inferiores a 1903. A página de status de registro aguarda a conclusão do registro do Azure AD. O problema é corrigido no Windows 10 versão 1903 e mais recente.  
- A implantação do AutoPilot do Azure AD híbrido com ESP demora mais do que a duração do tempo limite definida no perfil ESP. Em implantações híbridas do Azure AD Pilot, o ESP levará 40 minutos por mais tempo do que o valor definido no perfil ESP. Esse atraso dá tempo para o AD Connector local criar o novo registro de dispositivo para o Azure AD. 
- A página de logon do Windows não é preenchida previamente com o nome de usuário no modo orientado por usuários do AutoPilot. Se houver uma reinicialização durante a fase de instalação do dispositivo do ESP:
    - as credenciais do usuário não são preservadas
    - o usuário deve inserir as credenciais novamente antes de prosseguir da fase de configuração do dispositivo para a fase de configuração da conta
- O ESP está preso por um longo tempo ou nunca conclui a fase de "identificação". O Intune computa as políticas ESP durante a fase de identificação. Um dispositivo pode nunca concluir a computação das políticas de ESP se o usuário atual não tiver um licenciamento do Intune atribuído.  
- Configurar o controle de aplicativos do Windows Defender faz com que uma solicitação seja reinicializada durante o piloto automático. Configurar o aplicativo do Windows Defender (AppLocker CSP) requer uma reinicialização. Quando essa política é configurada, ela pode fazer com que um dispositivo seja reinicializado durante o piloto automático. Atualmente, não há como suprimir ou adiar a reinicialização.
- Quando a política de DeviceLock (https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) é habilitada como parte de um perfil ESP, o OOBE ou o usuário da área de trabalho de logon automático pode falhar unexpectantly por dois motivos.
  - Se o dispositivo não for reinicializado antes de sair da fase de instalação do dispositivo ESP, o usuário poderá ser solicitado a inserir suas credenciais do Azure AD. Esse prompt ocorre em vez de um logon automático bem-sucedido em que o usuário vê a animação do primeiro logon do Windows.
  - O autologn falhará se o dispositivo for reinicializado depois que o usuário inserir suas credenciais do Azure AD, mas antes de sair da fase de instalação do dispositivo ESP. Essa falha ocorre porque a fase de instalação do dispositivo ESP nunca foi concluída. A solução alternativa é redefinir o dispositivo.

## <a name="next-steps"></a>Próximos passos
Depois de configurar as suas páginas de inscrição do Windows, saiba como gerir dispositivos Windows. Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](../remote-actions/device-management.md)
