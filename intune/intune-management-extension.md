---
title: Adicionar scripts do PowerShell no Microsoft Intune para dispositivos com o Windows 10 – Azure | Microsoft Docs
description: Adicione scripts do PowerShell, atribua a política de script a grupos do Azure Active Directory, utilize relatórios para monitorizar os scripts e veja os passos para eliminar scripts que adicionou em dispositivos com o Windows 10 no Microsoft Intune. Também pode ver alguns problemas comuns e as resoluções.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 063a5cbbe18efc5c406c9dc7f2fa40d614b2e48a
ms.sourcegitcommit: d3b1e3fffd3e0229292768c7ef634be71e4736ae
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/04/2018
ms.locfileid: "52860967"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Gerir scripts do PowerShell no Intune para dispositivos Windows 10

Utilize a extensão de gestão do Intune para carregar scripts do PowerShell no Intune para executar em dispositivos Windows 10. A extensão de gestão melhora a gestão de dispositivos móveis (MDM) do Windows 10 e torna mais fácil de mover para a gestão moderna.

## <a name="moving-to-modern-management"></a>Mudar para a gestão moderna

A computação de utilizador final está a passar por uma transformação digital. As TI clássicas e tradicionais focam-se numa única plataforma de dispositivo, em dispositivos pertencentes à empresa, em utilizadores que trabalham num escritório e numa variedade de processos de TI reativos e manuais. A área de trabalho moderna usa muitas plataformas de utilizador e de negócios pertencentes à empresa, permite que os utilizadores trabalhem em qualquer lugar e fornece processos de TI automatizado e proativos.

Serviços MDM, como o Microsoft Intune, podem gerir dispositivos móveis e de Desktops com o Windows 10. O cliente de gestão do Windows 10 incorporado comunica com o Intune para executar tarefas de gestão de empresa. Existem algumas tarefas que poderá ser necessário, por exemplo, a configuração do dispositivo avançadas, resolução de problemas e gestão de aplicações de Win32 legada que não está disponível no Windows 10 MDM. Para estas capacidades, pode executar o cliente de software do Intune nos seus dispositivos Windows 10. [Comparar a gestão de Windows PCs como computadores ou dispositivos móveis](pc-management-comparison.md) é um ótimo recurso.

A extensão de gestão do Intune complementa as funcionalidades de MDM do Windows 10 na caixa. Pode criar scripts do PowerShell para ser executado nos dispositivos Windows 10. Por exemplo, pode criar um script do PowerShell que instala uma aplicação Win32 legada, carrega o script para o Intune, atribui o script a um grupo do Azure Active Directory (AD) e executa o script. Em seguida, pode monitorizar o estado de execução do script do início ao fim.

## <a name="prerequisites"></a>Pré-requisitos

A extensão de gestão do Intune tem os seguintes pré-requisitos:

- Dispositivos têm de estar associados ao Azure AD e [inscritos automaticamente](windows-enroll.md#enable-windows-10-automatic-enrollment). A extensão de gestão do Intune suporta associados ao Azure AD, associados a um domínio híbrida e comanaged os dispositivos Windows inscritos. Dispositivos inscritos no GPO não são suportados.
- Dispositivos têm de executar com o Windows 10 versão 1607 ou posterior.
- O agente de extensão de gestão do Intune é instalado quando um script do PowerShell ou uma aplicação Win32 for implementada para um utilizador ou grupo de segurança do dispositivo.

## <a name="create-a-powershell-script-policy"></a>Criar uma política de script do PowerShell 

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Scripts do PowerShell** > **Adicionar**.
3. Introduza um **Nome** e uma **Descrição** para o script do PowerShell. Para **Localização do script**, navegue até ao script do PowerShell. O script tem de ser inferior a 200 KB (ASCII) ou o tamanho de 100 KB (Unicode).
4. Escolha **Configurar**. Em seguida, opte por executar o script com as credenciais do utilizador no dispositivo (**Sim**) ou no contexto do sistema (**Não**). Por predefinição, o script é executado no contexto do sistema. Selecione **Sim** a menos que o script tenha de ser executado no contexto do sistema. 
  ![Painel Adicionar o script do PowerShell](./media/mgmt-extension-add-script.png)
5. Selecione se o script tem de ser assinado por um fabricante fidedigno (**Sim**). Por predefinição, não existe um requisito para que o script seja assinado. 
6. Selecione **OK** e, em seguida, **Criar** para guardar o script.

## <a name="assign-a-powershell-script-policy"></a>Atribuir uma política de script do PowerShell

1. Em **Scripts do PowerShell**, selecione o script a atribuir e, em seguida, selecione **Gerir** > **Atribuições**.

    ![Adicionar o painel de script do PowerShell](./media/mgmt-extension-assignments.png)

2. Escolha **Selecionar Grupos** para uma lista dos grupos disponíveis do Azure AD. 
3. Selecione um ou mais grupos que incluam os utilizadores cujos dispositivos irão receber o script. Clique em **Selecionar** para atribuir a política aos grupos selecionados.

> [!NOTE]
> - Os scripts do PowerShell não podem ser aplicados a grupos de computadores.
> - Os utilizadores finais não são necessários para iniciar sessão no dispositivo para executar scripts do PowerShell.
> - Scripts do PowerShell no Intune podem ser direcionadas para grupos de segurança de dispositivos do Azure AD.

O cliente de extensão de gestão do Intune verifica uma vez por hora com o Intune. Depois de atribuir a política aos grupos do Azure AD, o script do PowerShell será executado e os resultados de execução serão comunicados.

## <a name="monitor-run-status-for-powershell-scripts"></a>Monitorizar o estado de execução de scripts do PowerShell

Pode monitorizar o estado de execução de scripts do PowerShell para utilizadores e dispositivos no portal do Azure.

Em **Scripts do PowerShell**, selecione o script que pretende monitorizar, selecione **Monitorizar** e, em seguida, selecione um dos seguintes relatórios:

- **Estado do dispositivo**
- **Estado de utilizador**

## <a name="troubleshoot-powershell-scripts"></a>Resolver problemas relacionados com scripts do PowerShell

Registos do agente no computador cliente são normalmente em `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Pode usar [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) para ver estes ficheiros de registo. 

![Captura de ecrã dos registos de agente](./media/apps-win32-app-10.png)  

## <a name="delete-a-powershell-script"></a>Eliminar um script do PowerShell

Em **Scripts do PowerShell**, clique com o botão direito no script e selecione **Eliminar**.

## <a name="common-issues-and-resolutions"></a>Problemas comuns e resoluções

Os scripts do PowerShell não são executados em cada início de sessão. Eles são executados apenas após os reinícios, ou se o **extensão de gestão do Microsoft Intune** serviço for reiniciado. A Intune gestão extensão verificação de cliente uma vez por hora para todas as alterações no script ou de política no Intune.

#### <a name="issue-intune-management-extension-doesnt-download"></a>Problema: A extensão de gestão do Intune não é transferido

**As possíveis resoluções**:

- Certifique-se de que os dispositivos são inscritos automaticamente no Azure AD. Para confirmar, no dispositivo: 

  1. Aceda a **configurações** > **contas** > **acesso profissional ou escolar**.
  2. Selecione a conta associada ao > **informações**.
  3. Sob **relatório de diagnóstico avançadas**, selecione **criar relatório**.
  4. Abra o `MDMDiagReport` num navegador da web e vá para o **inscrito origens de configuração** secção.
  5. Procure o **MDMDeviceWithAAD** propriedade. Se esta propriedade não existir, o dispositivo não é automaticamente inscritos.

    [Ativar a inscrição automática do Windows 10](windows-enroll.md#enable-windows-10-automatic-enrollment) inclui os passos.

#### <a name="issue-the-powershell-scripts-do-not-run"></a>Problema: Não são executados os scripts do PowerShell

**As possíveis resoluções**:

- Confirmar a extensão de gestão do Intune é transferida para `%ProgramFiles(x86)%\Microsoft Intune Management Extension`.
- Scripts não são executados nos Surface Hubs.
- Verifique os registos `\ProgramData\Microsoft\IntuneManagementExtension\Logs` para quaisquer erros.
- Para problemas de permissão possível, não se esqueça das propriedades do script do PowerShell são definidas como `Run this script using the logged on credentials`. Também pode verificar que o utilizador com sessão iniciada tem as permissões adequadas para executar o script.
- Para isolar problemas de criação de scripts, execute um script de exemplo. Por exemplo, criar o `C:\Scripts` directory e conceder controle total. Execute o seguinte script:

  ```powershell
  write-output "Script worked" | out-file c:\Scripts\output.txt
  ```

  Se tiver êxito, output.txt devem ser criados e deve incluir o texto "Script trabalhou".

- Para testar a execução do script sem o Intune, execute os scripts sob o contexto do sistema utilizando o [psexec ferramenta](https://docs.microsoft.com/sysinternals/downloads/psexec) localmente:

  `psexec -i -s`

## <a name="next-steps"></a>Passos Seguintes

[Monitor](device-profile-monitor.md) e [resolver](device-profile-troubleshoot.md) seus perfis.
