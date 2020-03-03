---
title: Adicione scripts PowerShell aos dispositivos Windows 10 no Microsoft Intune - Azure Microsoft Docs
description: Criar e executar scripts PowerShell, atribuir a política de scripts aos grupos De Diretórios Ativos do Azure, utilizar relatórios para monitorizar os scripts e ver os passos para eliminar scripts que adiciona nos dispositivos Windows 10 no Microsoft Intune. Consulte também algumas questões e resoluções comuns.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8af7a756d95051be52a5380467cb4f9be2533b3
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216189"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>Utilize scripts PowerShell em dispositivos Windows 10 em Intune

Utilize a extensão de gestão Microsoft Intune para carregar scripts PowerShell em Intune para executar em dispositivos Windows 10. A extensão de gestão melhora a gestão de dispositivos móveis do Windows 10 (MDM) e facilita a mudança para uma gestão moderna.

Esta funcionalidade aplica-se a:

- Windows 10 e posterior

## <a name="move-to-modern-management"></a>Passar para a gestão moderna

A computação de utilizador final está a passar por uma transformação digital. O IT clássico e tradicional foca-se numa única plataforma de dispositivos, dispositivos de propriedade empresarial, utilizadores que trabalham a partir do escritório, e diferentes processos de TI reativos manuais e reativos. O local de trabalho moderno utiliza muitas plataformas que são de propriedade de utilizadores e negócios, permite que os utilizadores trabalhem a partir de qualquer lugar, e fornece processos de TI automatizados e proativos.

Os serviços de MDM, como o Microsoft Intune, podem gerir dispositivos móveis e desktop que executam o Windows 10. O cliente de gestão incorporado do Windows 10 comunica com a Intune para executar tarefas de gestão empresarial. Existem algumas tarefas que poderá necessitar, como configuração avançada do dispositivo e resolução de problemas. Para a gestão de aplicações Win32, pode utilizar a funcionalidade de gestão de [aplicações Win32](app-management.md) nos seus dispositivos Windows 10.

A extensão de gestão Intune complementa as funcionalidades de MDM do Windows 10 na caixa. Pode criar scripts PowerShell para executar em dispositivos Windows 10. Por exemplo, crie um script PowerShell que faça configurações avançadas do dispositivo. Em seguida, faça o upload do script para Intune, atribua o script a um grupo de Diretório Ativo Azure (AD) e execute o script. Em seguida, pode monitorizar o estado de execução do script do início ao fim.

## <a name="prerequisites"></a>Pré-requisitos

A extensão de gestão Intune tem os seguintes pré-requisitos. Uma vez cumpridos os pré-requisitos, a extensão de gestão Intune instala-se automaticamente quando um script PowerShell ou uma aplicação Win32 são atribuídos ao utilizador ou dispositivo.

- Dispositivos que executam a versão 1607 do Windows 10 ou mais tarde. Se o dispositivo estiver matriculado com a [inscrição automática](../enrollment/windows-bulk-enroll.md)a granel, os dispositivos devem executar a versão 1703 do Windows 10 ou posterior. A extensão de gestão Intune não é suportada no Windows 10 no modo S, uma vez que o modo S não permite executar aplicações não-store. 
  
- Dispositivos unidos ao Azure Ative Directory (AD), incluindo:  
  
  - Hybrid Azure AD-joined: Devices joined to Azure Ative Directory (AD), e também se juntou ao Ative Directory (AD) no local. Consulte [plana o seu diretório ativo híbrido Azure junte-se à implementação](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan) para orientação.

- Dispositivos matriculados em Intune, incluindo:

  - Dispositivos matriculados numa política de grupo (GPO). Consulte [O dispositivo De sintetizá-lo automaticamente utilizando](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) a Política de Grupo para obter orientação.
  
  - Dispositivos matriculados manualmente em Intune, que é quando:
  
    - [A inscrição automática para Intune](../enrollment/quickstart-setup-auto-enrollment.md) está ativada em Azure AD. O utilizador final entra no dispositivo utilizando uma conta de utilizador local, junta manualmente o dispositivo à AD Azure e, em seguida, insere-se no dispositivo utilizando a sua conta AD Azure.
    
    OU  
    
    - O utilizador insere-se no dispositivo utilizando a sua conta Azure AD e, em seguida, matricula-se em Intune.

  - Dispositivos cogeridos que utilizam O Gestor de Configuração e Intune. Certifique-se de que a carga de trabalho das **Apps** está definida para **Pilot Intune** ou **Intune**. Consulte os seguintes artigos para orientação: 
  
    - [O que é cogestão](https://docs.microsoft.com/configmgr/comanage/overview) 
    - [Carga de trabalho de aplicativos de cliente](https://docs.microsoft.com/configmgr/comanage/workloads#client-apps)
    - [Como mudar as cargas de trabalho do Gestor de Configuração para Intune](https://docs.microsoft.com/configmgr/comanage/how-to-switch-workloads)
  
> [!TIP]
> Certifique-se de que os dispositivos [estão unidos](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) ao Azure AD. Os dispositivos que só estão [registados](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) em Azure AD não receberão os seus scripts.

## <a name="create-a-script-policy-and-assign-it"></a>Crie uma política de scripte atribuí-la

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > **scripts PowerShell** > **Adicionar**.

    ![Adicione e use scripts PowerShell no Microsoft Intune](./media/intune-management-extension/mgmt-extension-add-script.png)

3. No Básico, introduza as **seguintes**propriedades e selecione **Seguinte:**
    - **Nome**: Introduza um nome para o script PowerShell. 
    - **Descrição**: Introduza uma descrição para o script PowerShell. Esta definição é opcional, mas recomendada.
4. Nas **definições do Script,** introduza as seguintes propriedades e selecione **Seguinte:**
    - **Localização**do script : Navegue no script PowerShell. O script deve ser inferior a 200 KB (ASCII).
    - **Executar este script utilizando as credenciais registadas**: Selecione **Sim** para executar o script com as credenciais do utilizador no dispositivo. Escolha **Não** (padrão) para executar o script no contexto do sistema. Muitos administradores escolhem **Sim.** Se o script for necessário para ser executado no contexto do sistema, escolha **Nº**.
    - **Faça a verificação**da assinatura do script : Selecione **Sim** se o script tiver de ser assinado por um editor de confiança. Selecione **Não** (predefinido) se não houver um requisito para que o script seja assinado. 
    - **Execute o script no anfitrião powerShell de 64 bits**: Selecione **Sim** para executar o script num anfitrião powerShell (PS) de 64 bits numa arquitetura de cliente de 64 bits. Selecione **No** (padrão) executa o script num anfitrião PowerShell de 32 bits.

      Ao definir para **Sim** ou **Não,** utilize a seguinte tabela para comportamentos políticos novos e existentes:

      | Executar roteiro em anfitrião PS de 64 bits | Arquitetura cliente | Novo roteiro do PS | Roteiro ps política existente |
      | --- | --- | --- | --- | 
      | Não | 32 bits  | Anfitrião ps de 32 bits apoiado | Funciona apenas em 32 bits de anfitrião ps, que trabalha em arquiteturas de 32 bits e 64 bits. |
      | Sim | 64 bits | Executa o guião em 64 bits de anfitrião ps para arquiteturas de 64 bits. Quando correu em 32-bits, o guião corre num anfitrião ps de 32 bits. | Executa o guião em 32 bits anfitrião ps. Se esta definição mudar para 64-bits, o script abre (não funciona) num anfitrião ps de 64 bits, e reporta os resultados. Quando correu em 32-bits, o guião corre em 32 bits anfitrião PS. |

5. Selecione **etiquetas de âmbito**. As etiquetas de âmbito são opcionais. [Utilize o controlo de acesso baseado em funções (RBAC) e as etiquetas](../fundamentals/scope-tags.md) de âmbito para TI distribuídos têm mais informações.

    Para adicionar uma etiqueta de âmbito:

    1. **Escolha Selecione etiquetas de âmbito e** gt; selecione uma etiqueta de âmbito existente na lista > **Selecione**.

    2. Quando terminar, selecione **Next**.

6. Selecione **Atribuições** > **Selecione grupos para incluir**. É apresentada uma lista existente de grupos da AD Azure.

    1. Selecione um ou mais grupos que incluam os utilizadores cujos dispositivos recebem o script. Clique em **Selecionar**. Os grupos que escolheu estão na lista e receberão a sua política.

        > [!NOTE]
        > Os scripts PowerShell em Intune podem ser direcionados para grupos de segurança de dispositivos AD Azure ou grupos de segurança de utilizadores Azure AD.

    2. Selecione **Seguinte**.

        ![Atribuir ou implementar script PowerShell para grupos de dispositivos no Microsoft Intune](./media/intune-management-extension/mgmt-extension-assignments.png)

7. Em **Review + add,** é mostrado um resumo das definições configuradas. Selecione **Adicionar** para salvar o script. Quando selecionar **Adicionar,** a política é implementada para os grupos que escolheu.

## <a name="important-considerations"></a>Considerações importantes

- Quando os scripts são definidos para o contexto do utilizador e o utilizador final tem direitos de administrador, por padrão, o script PowerShell é executado sob o privilégio do administrador.

- Os utilizadores finais não são obrigados a iniciar sessão no dispositivo para executar scripts PowerShell.

- A extensão de gestão Intune verifica o cliente com Intune uma vez a cada hora e após cada reboot para quaisquer novos scripts ou alterações. Depois de atribuir a política aos grupos do Azure AD, o script do PowerShell será executado e os resultados de execução serão comunicados. Uma vez que o script executa, não executa novamente a menos que haja uma mudança no script ou na política.

## <a name="monitor-run-status"></a>Monitorizar o estado da execução

Pode monitorizar o estado de execução de scripts do PowerShell para utilizadores e dispositivos no portal do Azure.

Em **Scripts do PowerShell**, selecione o script que pretende monitorizar, selecione **Monitorizar** e, em seguida, selecione um dos seguintes relatórios:

- **Estado do dispositivo**
- **Estado do utilizador**

## <a name="intune-management-extension-logs"></a>Registos de extensão de gestão insinados

Os registos de agentes na máquina cliente são normalmente `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Pode utilizar [CMTrace.exe](https://docs.microsoft.com/configmgr/core/support/cmtrace) para visualizar estes ficheiros de registo.

![Screenshot ou sample cmtrace agent logs in Microsoft Intune](./media/apps-win32-app-management/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>Apagar um script

Em **Scripts do PowerShell**, clique com o botão direito no script e selecione **Eliminar**.

## <a name="common-issues-and-resolutions"></a>Questões e resoluções comuns

### <a name="issue-intune-management-extension-doesnt-download"></a>Emissão: Extensão de gestão intune não descarrega

**Possíveis resoluções:**

- O dispositivo não está associado ao Azure AD. Certifique-se de que os dispositivos cumprem os [pré-requisitos](#prerequisites) (neste artigo). 
- Não existem scripts PowerShell ou aplicações Win32 atribuídas aos grupos que o utilizador ou dispositivo pertencem.
- O dispositivo não pode fazer o check-in com o serviço Intune, devido a nenhum acesso à Internet, sem acesso aos Serviços de Notificação push do Windows (WNS), e assim por diante.
- O dispositivo está no modo S. A extensão de gestão Intune não é suportada em dispositivos em funcionamento no modo S. 

Para ver se o dispositivo está matriculado automaticamente, pode:

  1. Vá a **Definições** > **Contas** > **Trabalho de acesso ou escola.**
  2. Selecione a conta unida > **Info**.
  3. Em **relatório de diagnóstico avançado,** selecione Criar **Relatório**.
  4. Abra o `MDMDiagReport` num navegador web.
  5. Procure a propriedade **MDMDeviceWithAAD.** Se a propriedade existir, o dispositivo está matriculado automaticamente. Se esta propriedade não existe, então o dispositivo não está matriculado automaticamente.

Ativar a [inscrição automática do Windows 10](../enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment) inclui os passos para configurar a inscrição automática em Intune.

### <a name="issue-powershell-scripts-do-not-run"></a>Edição: Os scripts PowerShell não funcionam

**Possíveis resoluções:**

- Os scripts powerShell não funcionam em todas as inscrições. Correm:

  - Quando o script é atribuído a um dispositivo
  - Se alterar o script, faça o upload e atribua o script a um utilizador ou dispositivo
  
    > [!TIP]
    > A Extensão de **Gestão Intune** da Microsoft é um serviço que funciona no dispositivo, tal como qualquer outro serviço listado na aplicação Services (services.msc). Depois de um dispositivo reiniciar, este serviço também pode reiniciar e verificar se há scripts PowerShell atribuídos com o serviço Intune. Se o serviço de extensão de **gestão intune** da Microsoft estiver definido para Manual, o serviço poderá não reiniciar após o reinício do dispositivo.

- Certifique-se de que os dispositivos [estão unidos ao Azure AD](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network). Os dispositivos que só estão unidos ao seu local de trabalho ou organização[(registados](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) em Azure AD) não receberão os scripts.
- A extensão de gestão Intune verifica o cliente uma vez por hora para quaisquer alterações no script ou na política em Intune.
- Confirme que a extensão de gestão Intune é transferida para `%ProgramFiles(x86)%\Microsoft Intune Management Extension`.
- Os scripts não funcionam em Surface Hubs ou Windows 10 no modo S.
- Reveja os registos para eventuais erros. Consulte os registos de [extensão de gestão Intune](#intune-management-extension-logs) (neste artigo).
- Para possíveis problemas de permissão, certifique-se de que as propriedades do script PowerShell estão definidas para `Run this script using the logged on credentials`. Verifique também se o utilizador assinado tem as permissões adequadas para executar o script.

- Para isolar problemas de script, pode:

  - Reveja a configuração de execução powerShell nos seus dispositivos. Consulte a política de [execução da PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6) para orientação.
  - Executar um script de amostra utilizando a extensão de gestão Intune. Por exemplo, criar o diretório `C:\Scripts` e dar a todos o controlo total. Execute o seguinte script:

    ```powershell
    write-output "Script worked" | out-file c:\Scripts\output.txt
    ```

    Se for bem sucedido, o output.txt deve ser criado e deve incluir o texto "Script worked".

  - Para testar a execução do script sem Intune, executar os scripts na conta System usando a [ferramenta psexec](https://docs.microsoft.com/sysinternals/downloads/psexec) localmente:

    `psexec -i -s`  
    
  - Se o guião relatar que foi bem sucedido, mas não foi bem sucedido, então é possível que o seu serviço antivírus possa ser o Agente executor de sandboxing. O seguinte guião relata sempre uma falha em Intune. Como teste, pode usar este guião:
  
    ```powershell
    Write-Error -Message "Forced Fail" -Category OperationStopped
    mkdir "c:\temp" 
    echo "Forced Fail" | out-file c:\temp\Fail.txt
    ```

    Se o guião reportar um sucesso, veja o `AgentExecutor.log` para confirmar a saída de erro. Se o guião executar, o comprimento deve ser >2.

  - Para capturar os ficheiros .error e .output, o seguinte snippet executa o script através do AgentExecutor para PSx86 (`C:\Windows\SysWOW64\WindowsPowerShell\v1.0`). Guarda os registos para a sua revisão. Lembre-se, a Extensão de Gestão Intune limpa os registos após a execução do script:
  
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

## <a name="next-steps"></a>Próximos passos

[Monitorize](../device-profile-monitor.md) e [atire problemas](../device-profile-troubleshoot.md) aos seus perfis.
