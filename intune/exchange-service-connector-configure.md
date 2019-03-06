---
title: Exchange connector do Intune para o Exchange Online | Microsoft Intune
description: Ligue o Intune ao serviço do Exchange do Office 365 para suportar a gestão de dispositivos móveis (MDM) do Exchange Active Sync.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 828cd17c320bd13b1b7fcce6578727015be3a77b
ms.sourcegitcommit: fb2ca28ab0cf89202c935da3f9d98adcea20566d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/06/2019
ms.locfileid: "57460449"
---
# <a name="configure-the-exchange-service-connector-for-intune-and-exchange-online"></a>Configurar o conector do serviço do Exchange para o Intune e Exchange Online
Este artigo mostra-lhe como ligar o serviço do Microsoft Intune ao Exchange Online ou o novo serviço do Exchange Online Dedicado. Para determinar se o seu ambiente do Exchange Online Dedicado é a versão **nova** ou **legada**, contacte o seu gestor de conta.

Com o **Conector de Serviços**, pode gerir o Exchange ActiveSync (EAS) e os dispositivos geridos do Intune a partir de uma única consola administrativa.  Não precisa do conector para ativar o Acesso Condicional para o Exchange Online.

Quando planear uma implementação de acesso condicional, muitas vezes, é importante compreender quais usuários e o número de utilizadores terá a nova experiência. O Centro de administração do Microsoft 365 fornece isso na forma de um relatório de utilização de aplicação de correio eletrónico Exchange Online como parte da funcionalidade de relatórios de atividade desse portal. Estes relatórios podem ser utilizados para compreender a adoção de e-mail do dispositivo móvel no seu ambiente antes e após a implementação do acesso condicional.

## <a name="service-to-service-connector-requirements"></a>Requisitos do Conector de Serviços
O **Conector de Serviços** suporta apenas o Exchange Online ou o Exchange Online Dedicado e não possui requisitos para uma infraestrutura no local. 


|              Requisito               |                                                                                                            Mais informações                                                                                                            |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange Online configurado e em execução |                                                                                 [Exchange Online](https://technet.microsoft.com/library/jj200580.aspx)                                                                                 |
|   Autoridade de gestão de dispositivos móveis   |                                                       [Definir o Microsoft Intune como a autoridade de gestão de dispositivos móveis](mdm-authority-set.md)                                                       |
|       Versão do Microsoft Exchange       |                                                                                      Exchange Online ou o novo serviço do Exchange Online Dedicado                                                                                      |
|    Sincronização do Active Directory    | Antes de poder utilizar o Conector do Intune, tem de [configurar a sincronização do Active Directory](/intune/users-add), para que os seus utilizadores e grupos de segurança locais sejam sincronizados com a instância do Azure Active Directory. |

### <a name="exchange-cmdlet-requirements"></a>Requisitos de cmdlets do Exchange

Tem de criar uma conta de utilizador do Exchange Online utilizada pelo conector do serviço Exchange do Intune. A conta tem de ter permissão para executar os seguintes cmdlets necessários do Windows PowerShell do Exchange:

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>Configurar o Conector de Serviços

1. Inicie sessão no [portal do Azure](https://portal.azure.com) com uma conta de utilizador com direitos de administração do Exchange, permissões para os cmdlets [descritos anteriormente](#exchange-cmdlet-requirements), uma licença do Intune válida e a função Administrador Global. O Microsoft Intune utiliza o endereço de e-mail do utilizador que tem atualmente sessão iniciada para configurar a ligação.

2. Selecione **Todos os serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3. Selecione **Intune** para abrir o dashboard do Microsoft Intune. Selecione **acesso ao Exchange**e, em **configuração** selecionar **conector do Exchange online**.

4.  Sobre o **acesso - conector do Exchange online do Exchange** página, selecione **configurar conector serviço a serviço**. 

O Conector de Serviços configura e sincroniza automaticamente o seu Exchange Online ou o novo ambiente do Exchange Online Dedicado.

## <a name="validate-your-exchange-connection"></a>Validar a sua ligação ao Exchange

Depois de ter configurado com êxito o conector de serviços do Exchange, valida as informações de servidor do Exchange Connector no **acesso - conector do Exchange online do Exchange** página.

Também pode ver o **Estado da ligação** e a data e hora da última tentativa de sincronização efetuada com êxito.

 
