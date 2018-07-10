---
title: Adicionar scripts do PowerShell no Microsoft Intune para dispositivos com o Windows 10 – Azure | Microsoft Docs
description: Adicione scripts do PowerShell, atribua a política de script a grupos do Azure Active Directory, utilize relatórios para monitorizar os scripts e veja os passos para eliminar scripts que adicionou em dispositivos com o Windows 10 no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: eb7d8b35cb88223a3fbfa45e0ad8e2f8d2852a96
ms.sourcegitcommit: ab801d715aa26f6d97f1a0c42a07e55146a14e6f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35289028"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Gerir scripts do PowerShell no Intune para dispositivos Windows 10
A extensão de gestão do Intune permite-lhe carregar scripts do PowerShell no Intune para executar em dispositivos Windows 10. A extensão de gestão complementa as funcionalidades de gestão de dispositivos móveis (MDM) do Windows 10 e torna mais fácil mudar para a gestão moderna.

## <a name="moving-to-modern-management"></a>Mudar para a gestão moderna
A computação de utilizador final está a passar por uma transformação digital. As TI clássicas e tradicionais focam-se numa única plataforma de dispositivo, em dispositivos pertencentes à empresa, em utilizadores que trabalham num escritório e numa variedade de processos de TI reativos e manuais. Comparativamente, a área de trabalho moderna permite múltiplas plataformas de dispositivos pertencentes ao utilizador e à empresa, permite que os utilizadores trabalhem em qualquer lugar e fornece processos de TI proativos e automatizados. 

Os serviços de MDM, como o Microsoft Intune, podem gerir dispositivos Windows 10 com o protocolo de MDM. O cliente de gestão incorporado do Windows 10 consegue comunicar com o Intune para efetuar tarefas de gestão empresariais. Ajuda-o a mudar para a gestão moderna em dispositivos Windows 10. No entanto, existem determinadas funcionalidades que poderão ser necessárias, tal como a configuração avançada de dispositivos, a resolução de problemas e a gestão da aplicação Win32 legada que não está atualmente disponível na MDM do Windows 10. Para obter estas funcionalidades, poderá ter de executar o cliente de software do Intune nos seus dispositivos Windows 10. Como resultado, não poderá utilizar as novas funcionalidades que a MDM do Windows 10 fornece. [Compare as diferenças entre o cliente de software do Intune e a MDM do Windows 10](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison).

A extensão de gestão do Intune complementa as funcionalidades de MDM do Windows 10. Pode criar scripts do PowerShell para serem executados em dispositivos Windows 10 que fornecem as funcionalidades de que precisa. Por exemplo, pode criar um script do PowerShell que instala uma aplicação Win32 legada nos seus dispositivos Windows 10, carregar o script para o Intune, atribuir o script a um grupo do Azure Active Directory (AD) e executar o script em dispositivos Windows 10. Em seguida, pode monitorizar o estado de execução do script em dispositivos Windows 10 do início até ao fim.

## <a name="prerequisites"></a>Pré-requisitos
A extensão de gestão do Intune tem os seguintes pré-requisitos:
- Os dispositivos têm de estar associados ao Azure AD. Não se incluem os dispositivos associados ao AD Híbrido.
- Os dispositivos têm de executar o Windows 10, versão 1607 ou posterior.
- A inscrição automática de MDM tem de estar [ativada no Azure AD](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment) e os dispositivos têm de estar inscritos automaticamente no Intune.

## <a name="create-a-powershell-script-policy"></a>Criar uma política de script do PowerShell 
1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Configuração do dispositivo** > **Scripts do PowerShell** > **Adicionar**.
4. Introduza um **Nome** e uma **Descrição** para o script do PowerShell. Para **Localização do script**, navegue até ao script do PowerShell. O script tem de ter menos de 200 KB (ASCII) ou 100 KB (Unicode) de tamanho.
5. Escolha **Configurar**. Em seguida, opte por executar o script com as credenciais do utilizador no dispositivo (**Sim**) ou no contexto do sistema (**Não**). Por predefinição, o script é executado no contexto do sistema. Selecione **Sim** a menos que o script tenha de ser executado no contexto do sistema. 
  ![Painel Adicionar o script do PowerShell](./media/mgmt-extension-add-script.png)
6. Selecione se o script tem de ser assinado por um fabricante fidedigno (**Sim**). Por predefinição, não existe um requisito para que o script seja assinado. 
7. Selecione **OK** e, em seguida, **Criar** para guardar o script.

## <a name="assign-a-powershell-script-policy"></a>Atribuir uma política de script do PowerShell
1. Em **Scripts do PowerShell**, selecione o script a atribuir e, em seguida, selecione **Gerir** > **Atribuições**.
  ![Painel Adicionar o script do PowerShell](./media/mgmt-extension-assignments.png)
 
2. Escolha **Selecionar Grupos** para uma lista dos grupos disponíveis do Azure AD. 
3. Selecione um ou mais grupos que contêm os utilizadores cujos dispositivos recebem o script. Clique em **Selecionar** para atribuir a política aos grupos selecionados.

> [!NOTE]
> - Os scripts do PowerShell não podem ser aplicados a grupos de computadores.
> - Os scripts do PowerShell são executados em dispositivos apenas quando um utilizador do Azure Active Directory (AD) tem sessão iniciada no dispositivo.

A extensão de gestão do Intune sincroniza o Intune uma vez por hora. Depois de atribuir a política aos grupos do Azure AD, o script do PowerShell será executado e os resultados de execução serão comunicados. 
 
## <a name="monitor-run-status-for-powershell-scripts"></a>Monitorizar o estado de execução de scripts do PowerShell
Pode monitorizar o estado de execução de scripts do PowerShell para utilizadores e dispositivos no portal do Azure.

Em **Scripts do PowerShell**, selecione o script que pretende monitorizar, selecione **Monitorizar** e, em seguida, selecione um dos seguintes relatórios:
   - **Estado do dispositivo**
   - **Estado de utilizador**

## <a name="delete-a-powershell-script"></a>Eliminar um script do PowerShell
Em **Scripts do PowerShell**, clique com o botão direito no script e selecione **Eliminar**.
