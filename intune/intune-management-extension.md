---
title: Adicionar scripts do PowerShell a dispositivos Windows 10 no Microsoft Intune-Azure | Microsoft Docs
description: Crie e execute scripts do PowerShell, atribua a política de script a grupos de Azure Active Directory, use relatórios para monitorar os scripts e veja as etapas para excluir os scripts adicionados a dispositivos Windows 10 no Microsoft Intune. Consulte também alguns problemas comuns e resoluções.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cf3a3735688d12e69dc297aa42ab2869c69bfc9
ms.sourcegitcommit: 05139901411d14a85c2340c0ebae02d2c178a851
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70904970"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>Usar scripts do PowerShell em dispositivos Windows 10 no Intune

Use a extensão de gerenciamento de Microsoft Intune para carregar scripts do PowerShell no Intune para serem executados em dispositivos Windows 10. A extensão de gerenciamento aprimora o MDM (gerenciamento de dispositivo móvel) do Windows 10 e torna mais fácil mudar para o gerenciamento moderno.

Esta funcionalidade aplica-se a:

- Windows 10 e posterior

## <a name="move-to-modern-management"></a>Mover para o gerenciamento moderno

A computação de utilizador final está a passar por uma transformação digital. O clássico, o setor de ti tradicional se concentra em uma única plataforma de dispositivo, dispositivos de negócios, usuários que trabalham no escritório e processos de ti manuais e reativos diferentes. O local de trabalho moderno usa muitas plataformas que são de Propriedade do usuário e da empresa, permite que os usuários trabalhem de qualquer lugar e fornece processos de ti automatizados e proativos.

Os serviços de MDM, como o Microsoft Intune, podem gerenciar dispositivos móveis e de desktop que executam o Windows 10. O cliente de gerenciamento interno do Windows 10 se comunica com o Intune para executar tarefas de gerenciamento corporativo. Há algumas tarefas que podem ser necessárias, como configuração avançada de dispositivo e solução de problemas. Para o gerenciamento de aplicativos do Win32, você pode usar o recurso de [Gerenciamento de aplicativo do Win32](apps-win32-app-management.md) em seus dispositivos Windows 10.

A extensão de gerenciamento do Intune complementa os recursos de MDM do Windows 10 na caixa. Você pode criar scripts do PowerShell para serem executados em dispositivos Windows 10. Por exemplo, crie um script do PowerShell que faça configurações avançadas do dispositivo. Em seguida, carregue o script no Intune, atribua o script a um grupo de Azure Active Directory (AD) e execute o script. Em seguida, você pode monitorar o status de execução do script do início ao fim.

## <a name="prerequisites"></a>Pré-requisitos

A extensão de gerenciamento do Intune tem os seguintes pré-requisitos. Depois que os pré-requisitos forem atendidos, a extensão de gerenciamento do Intune será instalada automaticamente quando um script do PowerShell ou um aplicativo Win32 for atribuído ao usuário ou dispositivo.

- Dispositivos que executam o Windows 10 versão 1607 ou posterior. Se o dispositivo for registrado usando o [registro automático em massa](windows-bulk-enroll.md), os dispositivos devem executar o Windows 10 versão 1703 ou posterior. Não há suporte para a extensão de gerenciamento do Intune no modo S do Windows 10, pois o modo S não permite a execução de aplicativos que não são da loja. 
  
- Dispositivos ingressados no Azure Active Directory (AD), incluindo:  
  
  - Ingressado no Azure AD híbrido: Dispositivos ingressados no Azure Active Directory (AD) e também ingressaram no Active Directory local (AD). Consulte [planejar sua implementação de junção de Azure Active Directory híbrida](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan) para obter diretrizes.

- Dispositivos registrados no Intune, incluindo:

  - Dispositivos registrados em uma política de grupo (GPO). Consulte [registrar um dispositivo Windows 10 automaticamente usando política de grupo](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) para obter diretrizes.
  
  - Dispositivos registrados manualmente no Intune, que é quando:
  
    - O [registro automático no Intune](quickstart-setup-auto-enrollment.md) está habilitado no Azure AD. O usuário final entra no dispositivo usando uma conta de usuário local, une manualmente o dispositivo ao Azure AD e, em seguida, entra no dispositivo usando sua conta do Azure AD.
    
    OU  
    
    - O usuário entra no dispositivo usando sua conta do Azure AD e, em seguida, registra-se no Intune.

  - Dispositivos cogerenciados que usam o Configuration Manager e o Intune. Verifique se a carga de trabalho **aplicativos cliente** está definida como **piloto do Intune** ou **Intune**. Consulte os seguintes artigos para obter orientação: 
  
    - [O que é cogerenciamento](https://docs.microsoft.com/sccm/comanage/overview) 
    - [Carga de trabalho de aplicativos cliente](https://docs.microsoft.com/sccm/comanage/workloads#client-apps)
    - [Alternar cargas de trabalho de Configuration Manager para o Intune](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads)
  
> [!TIP]
> Verifique se os dispositivos [ingressaram](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) no Azure AD. Os dispositivos que são [registrados](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) somente no Azure ad não receberão seus scripts.

## <a name="create-a-script-policy-and-assign-it"></a>Criar uma política de script e atribuí-la

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Scripts do PowerShell** > **Adicionar**.

    ![Adicionar e usar scripts do PowerShell no Microsoft Intune](./media/mgmt-extension-add-script.png)

3. Em **noções básicas**, insira as seguintes propriedades e selecione **Avançar**:
    - **Nome**: Insira um nome para o script do PowerShell. 
    - **Descrição**: Insira uma descrição para o script do PowerShell. Esta definição é opcional, mas recomendada.
4. Em **configurações de script**, insira as seguintes propriedades e selecione **Avançar**:
    - **Local do script**: Navegue até o script do PowerShell. O script deve ser inferior a 200 KB (ASCII).
    - **Execute este script usando as credenciais conectadas**: Selecione **Sim** para executar o script com as credenciais do usuário no dispositivo. Escolha **não** (padrão) para executar o script no contexto do sistema. Muitos administradores escolhem **Sim**. Se o script for necessário para ser executado no contexto do sistema, escolha **não**.
    - **Impor verificação de assinatura de script**: Selecione **Sim** se o script precisar ser assinado por um fornecedor confiável. Selecione **não** (padrão) se não houver um requisito para que o script seja assinado. 
    - **Execute o script no host do PowerShell de 64 bits**: Selecione **Sim** para executar o script em um host do PowerShell de 64 bits (PS) em uma arquitetura de cliente de 64 bits. Selecionar **não** (padrão) executa o script em um host do PowerShell de 32 bits.

      Ao definir como **Sim** ou **não**, use a tabela a seguir para um comportamento de política novo e existente:

      | Executar o script no host PS de 64 bits | Arquitetura do cliente | Novo script do PS | Script de PS de política existente |
      | --- | --- | --- | --- | 
      | Não | 32 bits  | host PS de 32 bits com suporte | É executado somente no host PS de 32 bits, que funciona em arquiteturas de 32 bits e de 64 bits. |
      | Sim | 64 bits | Executa o script no host PS de 64 bits para arquiteturas de 64 bits. Quando executado em 32 bits, o script é executado em um host PS de 32 bits. | Executa o script no host PS de 32 bits. Se essa configuração mudar para 64 bits, o script será aberto (ele não é executado) em um host do PS de 64 bits e relatará os resultados. Quando executado em 32 bits, o script é executado no host do PS de 32 bits. |

5. Selecione **marcas de escopo**. Marcas de escopo são opcionais. [Use o controle de acesso baseado em função (RBAC) e as marcas de escopo para distribuído ele](scope-tags.md) tem mais informações.

    Para adicionar uma marca de escopo:

    1. Escolha **selecionar marcas de escopo** > selecione uma marca de escopo existente na lista > **selecione**.

    2. Quando terminar, selecione **Avançar**.

6. Selecione **atribuições** > **Selecionar grupos a serem incluídos**. Uma lista existente de grupos do Azure AD é mostrada.

    1. Selecione um ou mais grupos que incluam os usuários cujos dispositivos recebem o script. Escolha **Selecionar**. Os grupos escolhidos são mostrados na lista e receberão sua política.

        > [!NOTE]
        > Os scripts do PowerShell no Intune podem ser destinados a grupos de segurança de dispositivo do Azure AD ou a grupos de segurança de usuário do Azure AD.

    2. Selecione **Seguinte**.

        ![Atribuir ou implantar script do PowerShell em grupos de dispositivos no Microsoft Intune](./media/mgmt-extension-assignments.png)

7. Em **examinar + adicionar**, é mostrado um resumo das configurações que você configurou. Selecione **Adicionar** para salvar o script. Quando você seleciona **Adicionar**, a política é implantada nos grupos escolhidos.

## <a name="important-considerations"></a>Considerações importantes

- Quando os scripts são definidos para o contexto do usuário e o usuário final tem direitos de administrador, por padrão, o script do PowerShell é executado sob o privilégio de administrador.

- Os usuários finais não precisam entrar no dispositivo para executar scripts do PowerShell.

- O cliente de extensão de gerenciamento do Intune verifica com o Intune uma vez a cada hora e depois de cada reinicialização para novos scripts ou alterações. Depois de atribuir a política aos grupos do Azure AD, o script do PowerShell será executado e os resultados de execução serão comunicados. Depois que o script é executado, ele não é executado novamente, a menos que haja uma alteração no script ou na política.

## <a name="monitor-run-status"></a>Status de execução do monitor

Pode monitorizar o estado de execução de scripts do PowerShell para utilizadores e dispositivos no portal do Azure.

Em **Scripts do PowerShell**, selecione o script que pretende monitorizar, selecione **Monitorizar** e, em seguida, selecione um dos seguintes relatórios:

- **Estado do dispositivo**
- **Estado de utilizador**

## <a name="intune-management-extension-logs"></a>Logs de extensão de gerenciamento do Intune

Os logs de agente no computador cliente normalmente estão `\ProgramData\Microsoft\IntuneManagementExtension\Logs`em. Você pode usar [CMTrace. exe](https://docs.microsoft.com/sccm/core/support/tools) para exibir esses arquivos de log. 

![Captura de tela ou logs do agente cmtrace de exemplo em Microsoft Intune](./media/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>Excluir um script

Em **Scripts do PowerShell**, clique com o botão direito no script e selecione **Eliminar**.

## <a name="common-issues-and-resolutions"></a>Problemas comuns e resoluções

### <a name="issue-intune-management-extension-doesnt-download"></a>Problema: A extensão de gerenciamento do Intune não é baixada

**Possíveis resoluções**:

- O dispositivo não ingressou no Azure AD. Verifique se os dispositivos atendem aos [pré-requisitos](#prerequisites) (neste artigo). 
- Não há nenhum script do PowerShell ou aplicativos Win32 atribuídos aos grupos que o usuário ou o dispositivo pertence.
- O dispositivo não pode fazer check-in com o serviço do Intune, devido a nenhum acesso à Internet, sem acesso ao Windows Push Notification Services (WNS) e assim por diante.
- O dispositivo está no modo S. A extensão de gerenciamento do Intune não tem suporte em dispositivos em execução no modo S. 

Para ver se o dispositivo está registrado automaticamente, você pode:

  1. Vá para **configurações** > **contas** > **acesso corporativo ou de estudante**.
  2. Selecione a conta unida > **informações**.
  3. Em **relatório de diagnóstico avançado**, selecione **criar relatório**.
  4. Abra o `MDMDiagReport` em um navegador da Web.
  5. Procure a propriedade **MDMDeviceWithAAD** . Se a propriedade existir, o dispositivo será registrado automaticamente. Se essa propriedade não existir, o dispositivo não será registrado automaticamente.

[Habilitar o registro automático do Windows 10](windows-enroll.md#enable-windows-10-automatic-enrollment) inclui as etapas para configurar o registro automático no Intune.

### <a name="issue-powershell-scripts-do-not-run"></a>Problema: Os scripts do PowerShell não são executados

**Possíveis resoluções**:

- Os scripts do PowerShell não são executados em todas as entradas. Eles são executados:

  - Quando o script é atribuído a um dispositivo
  - Se você alterar o script, carregá-lo e atribuir o script a um usuário ou dispositivo
  
    > [!TIP]
    > A **extensão de gerenciamento de Microsoft Intune** é um serviço executado no dispositivo, assim como qualquer outro serviço listado no aplicativo de serviços (Services. msc). Após a reinicialização de um dispositivo, esse serviço também pode ser reiniciado e verificar se há scripts do PowerShell atribuídos com o serviço do Intune. Se o serviço de **extensão de gerenciamento de Microsoft Intune** estiver definido como manual, o serviço poderá não ser reiniciado após a reinicialização do dispositivo.

- Verifique se os dispositivos [ingressaram no Azure ad](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network). Os dispositivos que só ingressaram em seu local de trabalho ou organização ([registrado](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) no Azure AD) não receberão os scripts.
- O cliente de extensão de gerenciamento do Intune verifica uma vez por hora em busca de qualquer alteração no script ou na política no Intune.
- Confirme se a extensão de gerenciamento do Intune `%ProgramFiles(x86)%\Microsoft Intune Management Extension`foi baixada para.
- Os scripts não são executados em Surface hubs ou no modo S do Windows 10.
- Examine os logs para verificar se há erros. Consulte [logs de extensão de gerenciamento do Intune](#intune-management-extension-logs) (neste artigo).
- Para possíveis problemas de permissão, verifique se as propriedades do script do PowerShell estão definidas `Run this script using the logged on credentials`como. Verifique também se o usuário conectado tem as permissões apropriadas para executar o script.

- Para isolar problemas de script, execute as seguintes etapas:

  - Examine a configuração de execução do PowerShell em seus dispositivos. Consulte a [política de execução do PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6) para obter diretrizes.
  - Execute um script de exemplo usando a extensão de gerenciamento do Intune. Por exemplo, crie o `C:\Scripts` diretório e conceda a todos controle total. Execute o seguintes script:

    ```powershell
    write-output "Script worked" | out-file c:\Scripts\output.txt
    ```

    Se tiver sucesso, o output. txt deverá ser criado e deverá incluir o texto "script trabalhado".

  - Para testar a execução do script sem o Intune, execute os scripts na conta do sistema usando a [ferramenta PsExec](https://docs.microsoft.com/sysinternals/downloads/psexec) localmente:

    `psexec -i -s`  
    
  - Se a execução de script relatar um sucesso, mas o resultado não estiver acontecendo (por exemplo, o script acima não cria um arquivo), o antivírus poderá estar em área restrita AgentExecutor. O script a seguir sempre deve relatar uma falha no Intune – se ele reportar um êxito, consulte AgentExecutor. log para confirmar a saída de erro-o comprimento deve ser > 2 se o script estiver sendo executado de forma alguma:

    ```powershell
    Write-Error -Message "Forced Fail" -Category OperationStopped
    mkdir "c:\temp" 
    echo "Forced Fail" | out-file c:\temp\Fail.txt
    ```
    
  - Se você precisar capturar o. Error e. Output, o trecho a seguir executará o script por meio de AgentExecutor para PSx86 e deixará os logs por trás da coleção (já que a extensão de gerenciamento do Intune limpa os logs após a execução):
  
    ```powershell
    $scriptPath = read-host "Enter the path to the script file to execute"
    $logFolder = read-host "Enter the path to a folder to output the logs to"
    $outputPath = $logFolder+"\output.output"
    $errorPath =  $logFolder+"\error.error"
    $timeoutPath =  $logFolder+"\timeout.timeout"
    $timeoutVal = 60000 
    $PSFolder = "C:\Windows\SysWOW64\WindowsPowerShell\v1.0"
    $AgentExec = "C:\Program Files (x86)\Microsoft Intune Management Extension\agentexecutor.exe"
    &$AgentExec -powershell  $scriptPath $outputPath $errorPath $timeoutPath $timeoutVal $PSFolder 0 0
    ```

## <a name="next-steps"></a>Passos Seguintes

[Monitore](device-profile-monitor.md) e [solucione problemas](device-profile-troubleshoot.md) de seus perfis.
