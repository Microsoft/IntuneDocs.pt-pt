---
title: Adicionar scripts do PowerShell para dispositivos Windows 10 no Microsoft Intune – Azure | Documentos da Microsoft
description: Criar e executar scripts do PowerShell, atribua a política de script para grupos do Active Directory do Azure, utilizar relatórios para monitorizar os scripts e veja os passos para eliminar scripts que adicionar em dispositivos Windows 10 no Microsoft Intune. Também pode ver alguns problemas comuns e as resoluções.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/20/2019
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
ms.openlocfilehash: 90b3e858a06a6f3a34de6ec8102e1a6c458369a2
ms.sourcegitcommit: cd451ac487c7ace18ac9722a28b9facfba41f6d3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298407"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>Utilizar scripts do PowerShell em dispositivos Windows 10 no Intune

Utilize a extensão de gestão do Microsoft Intune para carregar scripts do PowerShell no Intune para executar em dispositivos Windows 10. A extensão de gestão melhora a gestão de dispositivos móveis (MDM) do Windows 10 e torna mais fácil de mover para a gestão moderna.

Esta funcionalidade aplica-se a:

- Windows 10 e posterior

## <a name="move-to-modern-management"></a>Mover para a gestão moderna

A computação de utilizador final está a passar por uma transformação digital. Clássicas e tradicionais focam-se numa única plataforma de dispositivo, dispositivos pertencentes à empresa, os utilizadores que trabalham a partir de processos de TI reativos o office e o manual de diferente. A área de trabalho moderna usa muitas plataformas de utilizador e de negócios pertencentes à empresa, permite que os utilizadores trabalhem em qualquer lugar e fornece processos de TI automatizado e proativos.

Serviços MDM, como o Microsoft Intune, podem gerir dispositivos móveis e de Desktops com o Windows 10. O cliente de gestão do Windows 10 incorporado comunica com o Intune para executar tarefas de gestão de empresa. Existem algumas tarefas que poderá ser necessário, por exemplo, a configuração do dispositivo avançadas e resolução de problemas. Para a gestão de aplicações do Win32, pode utilizar o [gestão de aplicações de Win32](apps-win32-app-management.md) funcionalidade nos seus dispositivos Windows 10.

A extensão de gestão do Intune complementa as funcionalidades de MDM do Windows 10 na caixa. Pode criar scripts do PowerShell para ser executado nos dispositivos Windows 10. Por exemplo, pode criar um script do PowerShell que faz as configurações de dispositivo avançados, carrega o script para o Intune, atribui o script a um grupo do Azure Active Directory (AD) e executa o script. Em seguida, pode monitorizar o estado de execução do script do início ao fim.

## <a name="prerequisites"></a>Pré-requisitos

A extensão de gestão do Intune tem os seguintes pré-requisitos. Quando estes forem atendidos, a extensão de gestão do Intune é instalada automaticamente quando um script do PowerShell ou aplicação de Win32 é atribuída ao utilizador ou dispositivo.

- Dispositivos com o Windows 10 versão 1607 ou posterior. Se o dispositivo é inscrito através de [auto-inscrição em massa](windows-bulk-enroll.md), dispositivos têm de executar com o Windows 10 versão 1703 ou posterior. A extensão de gestão do Intune não é suportada no Windows 10 no modo de S, como o modo de S não permite a execução de aplicações da loja não. 
  
- Dispositivos associados ao Azure Active Directory (AD), incluindo:  
  
  - Azure híbrido associado ao AD: Dispositivos associados ao Azure Active Directory (AD) e também associado ao local do Active Directory (AD). Ver [planear a implementação de associação do Azure Active Directory híbrida](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan) para obter orientações.

- Dispositivos inscritos no Intune, incluindo:

  - Os dispositivos inscritos numa política de grupo (GPO). Ver [inscrever um dispositivo Windows 10 automaticamente usando a diretiva de grupo](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) para obter orientações.
  
  - Dispositivos inscritos manualmente no Intune, que é quando:
  
    - [Inscrição automática para o Intune](quickstart-setup-auto-enrollment.md) está ativado no Azure AD. O utilizador final inicia sessão no dispositivo com uma conta de utilizador local, associe manualmente o dispositivo para o Azure AD e, em seguida, inicia sessão no dispositivo com a respetiva conta do Azure AD.
    
    OU  
    
    - Utilizador inicia sessão no dispositivo com a respetiva conta do Azure AD e, em seguida, é inscrito no Intune.

  - Dispositivos cogeridos que utilizam o Configuration Manager e o Intune. Certifique-se a **aplicações de cliente** carga de trabalho está definida como **Intune piloto** ou **Intune**. Veja o seguinte para obter orientações sobre: 
  
    - [O que é a cogestão](https://docs.microsoft.com/sccm/comanage/overview) 
    - [Carga de trabalho de aplicações de cliente](https://docs.microsoft.com/sccm/comanage/workloads#client-apps)
    - [Cargas de trabalho do Gestor de configuração do comutador para o Intune](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads)
  
> [!TIP]
> Certifique-se de que os dispositivos estão [associados a um](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) para o Azure AD. Dispositivos que só estão [registado](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) no Azure AD não irão receber seus scripts.

## <a name="create-a-script-policy"></a>Criar uma política de script 

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Scripts do PowerShell** > **Adicionar**.
3. Introduza as seguintes propriedades:
    - **Nome**: Introduza um nome para o script do PowerShell. 
    - **Descrição**: Introduza uma descrição para o script do PowerShell. Esta definição é opcional, mas recomendada. 
    - **Localização do script**: Navegue para o script do PowerShell. O script tem de ser inferior a 200 KB (ASCII).
4. Escolher **configurar**e introduza as seguintes propriedades:
    - **Executar este script utilizando o com sessão iniciada nas credenciais**: Selecione **Sim** para executar o script com as credenciais do utilizador no dispositivo. Escolher **não** (predefinição) para executar o script no contexto do sistema. Escolha de muitos administradores **Sim**. Se o script é necessário para executar no contexto do sistema, escolha **não**.
    - **Impor a verificação de assinatura de script**: Selecione **Sim** se o script deve ser assinado por um fabricante fidedigno. Selecione **não** (predefinição), se não existir um requisito para o script seja assinado. 
    - **Executar script num anfitrião do PowerShell de 64 bits**: Selecione **Sim** para executar o script num host de PowerShell (PS) de 64 bits numa arquitetura de cliente de 64 bits. Selecione **não** (predefinição) executa o script num host do PowerShell de 32 bits.

      Ao definir como **Sim** ou **não**, utilize a seguinte tabela para novos e existentes o comportamento da política:

      | Executar script num anfitrião de PS de 64 bits | Arquitetura do cliente | Novo script PS | Política existente PS script |
      | --- | --- | --- | --- | 
      | Não | 32 bits  | anfitrião de PS de 32 bits suportado | É executado apenas num anfitrião de PS de 32 bits, que funciona em arquiteturas de 32 bits e 64 bits. |
      | Sim | 64 bits | Executa o script no anfitrião de PS de 64 bits para arquiteturas de 64 bits. Quando executados de 32 bits, o script é executado num host de PS de 32 bits. | Executa o script no anfitrião de PS de 32 bits. Se esta definição é alterado para 64 bits, o script é aberto (ele não é executado) num host de PS de 64 bits e os resultados de relatórios. Quando executados de 32 bits, o script é executado no anfitrião de PS de 32 bits. |

    ![Adicionar e utilizar scripts do PowerShell no Microsoft Intune](./media/mgmt-extension-add-script.png)
5. Selecione **OK** > **criar** para guardar o script.

> [!NOTE]
> Quando os scripts estão definidos para o contexto de utilizador e o utilizador final tem direitos de administrador, por predefinição, o script do PowerShell é executado sob o privilégio de administrador.

## <a name="assign-the-policy"></a>Atribuir a política

1. Em **Scripts do PowerShell**, selecione o script a atribuir e, em seguida, selecione **Gerir** > **Atribuições**.

    ![Atribuir ou implementar o script do PowerShell para grupos de dispositivos no Microsoft Intune](./media/mgmt-extension-assignments.png)

2. Escolha **Selecionar Grupos** para uma lista dos grupos disponíveis do Azure AD. 
3. Selecione um ou mais grupos que incluam os utilizadores cujos dispositivos irão receber o script. Clique em **Selecionar** para atribuir a política aos grupos selecionados.

> [!NOTE]
> - Os utilizadores finais não são necessários para iniciar sessão no dispositivo para executar scripts do PowerShell.
> - Scripts do PowerShell no Intune podem ser direcionadas para grupos de segurança de dispositivos do Azure AD ou grupos de segurança do utilizador do Azure AD.

O cliente de extensão de gestão do Intune verifica uma vez por hora e a cada reinicialização com o Intune para qualquer novos scripts ou as alterações. Depois de atribuir a política aos grupos do Azure AD, o script do PowerShell será executado e os resultados de execução serão comunicados. Assim que o script for executado, ele não é executado novamente, exceto se houver uma alteração no script ou de política.

## <a name="monitor-run-status"></a>Monitor de estado de execução

Pode monitorizar o estado de execução de scripts do PowerShell para utilizadores e dispositivos no portal do Azure.

Em **Scripts do PowerShell**, selecione o script que pretende monitorizar, selecione **Monitorizar** e, em seguida, selecione um dos seguintes relatórios:

- **Estado do dispositivo**
- **Estado de utilizador**

## <a name="troubleshoot-scripts"></a>Resolver problemas de scripts

Registos do agente no computador cliente são normalmente em `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Pode usar [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) para ver estes ficheiros de registo. 

![Registos do agente de cmtrace de captura de ecrã ou de exemplo no Microsoft Intune](./media/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>Eliminar um script

Em **Scripts do PowerShell**, clique com o botão direito no script e selecione **Eliminar**.

## <a name="common-issues-and-resolutions"></a>Problemas comuns e resoluções

#### <a name="issue-intune-management-extension-doesnt-download"></a>Problema: Extensão de gestão do Intune não é transferido

**As possíveis resoluções**:

- O dispositivo não está associado ao Azure AD. Certifique-se de que os dispositivos cumprem os [pré-requisitos](#prerequisites) (neste artigo). 
- Não há scripts do PowerShell ou aplicações de Win32 atribuídas aos grupos que o utilizador ou dispositivo pertence.
- O dispositivo não é possível dar entrada no serviço do Intune, devido a sem acesso à internet, sem acesso à Windows Push Notification Services (WNS) e assim por diante.
- O dispositivo está no modo de S. A extensão de gestão do Intune não é suportada em dispositivos em execução no modo de S. 

Para ver se o dispositivo estiver inscrito automática, pode:

  1. Aceda a **configurações** > **contas** > **acesso profissional ou escolar**.
  2. Selecione a conta associada ao > **informações**.
  3. Sob **relatório de diagnóstico avançadas**, selecione **criar relatório**.
  4. Abra o `MDMDiagReport` num navegador da web.
  5. Procure o **MDMDeviceWithAAD** propriedade. Se a propriedade existir, o dispositivo está inscrito para automática. Se esta propriedade não existir, o dispositivo não estiver inscrito para automática.

[Ativar a inscrição automática do Windows 10](windows-enroll.md#enable-windows-10-automatic-enrollment) inclui os passos para configurar a inscrição automática no Intune.

#### <a name="issue-powershell-scripts-do-not-run"></a>Problema: Não execute scripts do PowerShell

**As possíveis resoluções**:

- Os scripts do PowerShell não são executados em cada início de sessão. Eles são executados:

  - Quando o script é atribuído a um dispositivo
  - Se alterar o script, carregue-o e atribuir o script a um utilizador ou dispositivo
  
    > [!TIP]
    > O **extensão de gestão do Microsoft Intune** é um serviço que é executada no dispositivo, tal como qualquer outro serviço listado na aplicação de serviços (Services. msc). Depois de um dispositivo é reiniciado, este serviço pode também reiniciar e verificar a existência de quaisquer scripts do PowerShell atribuídas com o serviço Intune. Se o **extensão de gestão do Microsoft Intune** serviço está definido como Manual, em seguida, o serviço pode não reiniciar depois do dispositivo é reiniciado.

- Certifique-se de que os dispositivos estão [associados ao Azure AD](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network). Dispositivos que só estão associados à sua área de trabalho ou a organização ([registado](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) no Azure AD) não irão receber os scripts.
- O cliente de extensão de gestão do Intune verifica uma vez por hora para todas as alterações no script ou de política no Intune.
- Confirmar a extensão de gestão do Intune é transferida para `%ProgramFiles(x86)%\Microsoft Intune Management Extension`.
- Os scripts não executados no Surface Hubs ou Windows 10 no modo de S.
- Reveja os registos para quaisquer erros. Ver [resolver problemas relacionados com scripts](#troubleshoot-scripts) (neste artigo).
- Para problemas de permissão possível, não se esqueça das propriedades do script do PowerShell são definidas como `Run this script using the logged on credentials`. Também pode verificar que o utilizador com sessão iniciada tem as permissões adequadas para executar o script.

- Para isolar problemas, efetue o seguinte:

  - Reveja a configuração de execução do PowerShell nos seus dispositivos. Consulte a [política de execução do PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6) para obter orientações.
  - Execute um script de exemplo com a extensão de gestão do Intune. Por exemplo, criar o `C:\Scripts` directory e conceder controle total. Execute o seguintes script:

    ```powershell
    write-output "Script worked" | out-file c:\Scripts\output.txt
    ```

    Se tiver êxito, output.txt devem ser criados e deve incluir o texto "Script trabalhou".

  - Para testar a execução do script sem o Intune, execute os scripts na conta de sistema através da [psexec ferramenta](https://docs.microsoft.com/sysinternals/downloads/psexec) localmente:

    `psexec -i -s`

## <a name="next-steps"></a>Passos Seguintes

[Monitor](device-profile-monitor.md) e [resolver](device-profile-troubleshoot.md) seus perfis.
