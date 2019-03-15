---
title: Adicionar scripts do PowerShell para dispositivos Windows 10 no Microsoft Intune – Azure | Documentos da Microsoft
description: Criar e executar scripts do PowerShell, atribua a política de script para grupos do Active Directory do Azure, utilizar relatórios para monitorizar os scripts e veja os passos para eliminar scripts que adicionar em dispositivos Windows 10 no Microsoft Intune. Também pode ver alguns problemas comuns e as resoluções.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f02b8849b626715471e5cabea937f89a08ab540c
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57390656"
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

A extensão de gestão do Intune tem os seguintes pré-requisitos:

- Dispositivos tem de ser associados a um ou registados no Azure AD e o Azure AD está configurado para [inscrição automática no Intune](windows-enroll.md#enable-windows-10-automatic-enrollment). A extensão de gestão do Intune suporta associados ao Azure AD, associados a um domínio híbrida e conjuntamente geridos os dispositivos Windows inscritos.
- Dispositivos têm de executar com o Windows 10 versão 1607 ou posterior.
- O agente de extensão de gestão do Intune é instalado quando um script do PowerShell ou uma aplicação Win32 for implementada para um utilizador ou grupo de segurança do dispositivo.

## <a name="create-a-script-policy"></a>Criar uma política de script 

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Selecione **Configuração do dispositivo** > **Scripts do PowerShell** > **Adicionar**.
3. Introduza as seguintes propriedades:
    - **Nome**: Introduza um nome para o script do PowerShell. 
    - **Descrição**: Introduza uma descrição para o script do PowerShell. Esta definição é opcional, mas recomendada. 
    - **Localização do script**: Navegue para o script do PowerShell. O script tem de ser inferior a 200 KB (ASCII).
4. Escolher **configurar**e introduza as seguintes propriedades:
    - **Executar este script utilizando o com sessão iniciada nas credenciais**: Selecione **Sim** para executar o script com as credenciais do utilizador no dispositivo. Escolher **não** (predefinição) para executar o script no contexto do sistema. Selecione **Sim** a menos que o script tenha de ser executado no contexto do sistema.
    - **Impor a verificação de assinatura de script**: Selecione **Sim** se o script deve ser assinado por um fabricante fidedigno. Selecione **não** (predefinição), se não existir um requisito para o script seja assinado. 
    - **Executar script num anfitrião do PowerShell de 64 bits**: Selecione **Sim** para executar o script num host de PowerShell (PS) de 64 bits numa arquitetura de cliente de 64 bits. Selecione **não** (predefinição) executa o script num host do PowerShell de 32 bits.

      Ao definir como **Sim** ou **não**, utilize a seguinte tabela para novos e existentes o comportamento da política:

      | Executar script num anfitrião de PS de 64 bits | Arquitetura do cliente | Novo script PS | Política existente PS script |
      | --- | --- | --- | --- | 
      | Não | 32 bits  | anfitrião de PS de 32 bits suportado | É executado apenas num anfitrião de PS de 32 bits, que funciona em arquiteturas de 32 bits e 64 bits. |
      | Sim | 64 bits | Executa o script no anfitrião de PS de 64 bits para arquiteturas de 64 bits. Quando executados de 32 bits, o script é executado num host de PS de 32 bits. | Executa o script no anfitrião de PS de 32 bits. Se esta definição é alterado para 64 bits, o script é aberto (ele não é executado) num host de PS de 64 bits e os resultados de relatórios. Quando executados de 32 bits, o script é executado no anfitrião de PS de 32 bits. |

    ![Adicionar e utilizar scripts do PowerShell no Microsoft Intune](./media/mgmt-extension-add-script.png)
5. Selecione **OK** > **criar** para guardar o script.

## <a name="assign-the-policy"></a>Atribuir a política

1. Em **Scripts do PowerShell**, selecione o script a atribuir e, em seguida, selecione **Gerir** > **Atribuições**.

    ![Atribuir ou implementar o script do PowerShell para grupos de dispositivos no Microsoft Intune](./media/mgmt-extension-assignments.png)

2. Escolha **Selecionar Grupos** para uma lista dos grupos disponíveis do Azure AD. 
3. Selecione um ou mais grupos que incluam os utilizadores cujos dispositivos irão receber o script. Clique em **Selecionar** para atribuir a política aos grupos selecionados.

> [!NOTE]
> - Os utilizadores finais não são necessários para iniciar sessão no dispositivo para executar scripts do PowerShell.
> - Scripts do PowerShell no Intune podem ser direcionadas para grupos de segurança de dispositivos do Azure AD.
> - Scripts do PowerShell no Intune podem ser direcionadas para grupos de segurança do utilizador do Azure AD.

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

Os scripts do PowerShell não são executados em cada início de sessão. Eles são executados apenas após os reinícios, ou se o **extensão de gestão do Microsoft Intune** serviço for reiniciado. A Intune gestão extensão verificação de cliente uma vez por hora para todas as alterações no script ou de política no Intune.

#### <a name="issue-intune-management-extension-doesnt-download"></a>Problema: Extensão de gestão do Intune não é transferido

**As possíveis resoluções**:

- Certifique-se de que os dispositivos são inscritos automaticamente no Azure AD. Para confirmar, no dispositivo: 

  1. Aceda a **configurações** > **contas** > **acesso profissional ou escolar**.
  2. Selecione a conta associada ao > **informações**.
  3. Sob **relatório de diagnóstico avançadas**, selecione **criar relatório**.
  4. Abra o `MDMDiagReport` num navegador da web e vá para o **inscrito origens de configuração** secção.
  5. Procure o **MDMDeviceWithAAD** propriedade. Se esta propriedade não existir, o dispositivo não é automaticamente inscritos.

    [Ativar a inscrição automática do Windows 10](windows-enroll.md#enable-windows-10-automatic-enrollment) inclui os passos.

#### <a name="issue-powershell-scripts-do-not-run"></a>Problema: Não execute scripts do PowerShell

**As possíveis resoluções**:

- Confirmar a extensão de gestão do Intune é transferida para `%ProgramFiles(x86)%\Microsoft Intune Management Extension`.
- Scripts não são executados nos Surface Hubs.
- Verifique os registos `\ProgramData\Microsoft\IntuneManagementExtension\Logs` para quaisquer erros.
- Para problemas de permissão possível, não se esqueça das propriedades do script do PowerShell são definidas como `Run this script using the logged on credentials`. Também pode verificar que o utilizador com sessão iniciada tem as permissões adequadas para executar o script.
- Para isolar problemas de criação de scripts, execute um script de exemplo. Por exemplo, criar o `C:\Scripts` directory e conceder controle total. Execute o seguintes script:

  ```powershell
  write-output "Script worked" | out-file c:\Scripts\output.txt
  ```

  Se tiver êxito, output.txt devem ser criados e deve incluir o texto "Script trabalhou".

- Para testar a execução do script sem o Intune, execute os scripts sob o contexto do sistema utilizando o [psexec ferramenta](https://docs.microsoft.com/sysinternals/downloads/psexec) localmente:

  `psexec -i -s`

## <a name="next-steps"></a>Passos Seguintes

[Monitor](device-profile-monitor.md) e [resolver](device-profile-troubleshoot.md) seus perfis.
