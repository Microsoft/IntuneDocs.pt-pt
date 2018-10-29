---
title: Intune Exchange Connector para o Exchange Online
titleSuffix: ''
description: Ligue o Intune ao serviço do Exchange do Office 365 para suportar a gestão de dispositivos móveis (MDM) do Exchange Active Sync.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 46d28ba8d9d8c6ec2adf2b41adbb9e7336676811
ms.sourcegitcommit: 24d9ae0396ca410f72cc061a3c4c402835ef32a1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/22/2018
ms.locfileid: "49642996"
---
# <a name="configure-the-exchange-service-connector-for-intune-and-exchange-online"></a>Configurar o conector do serviço do Exchange para o Intune e Exchange Online
Este artigo mostra-lhe como ligar o serviço do Microsoft Intune ao Exchange Online ou o novo serviço do Exchange Online Dedicado. Para determinar se o seu ambiente do Exchange Online Dedicado é a versão **nova** ou **legada**, contacte o seu gestor de conta.

Com o **Conector de Serviços** pode gerir o Exchange ActiveSync (EAS) e os dispositivos geridos do Intune a partir de uma única consola administrativa.  Não precisa do conector para ativar o Acesso Condicional para o Exchange Online.

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

1. Inicie sessão no [portal do Azure](http://portal.azure.com) com uma conta de utilizador com direitos de administração do Exchange, permissões para os cmdlets [descritos anteriormente](#exchange-cmdlet-requirements), uma licença do Intune válida e a função Administrador Global. O Microsoft Intune utiliza o endereço de e-mail do utilizador que tem atualmente sessão iniciada para configurar a ligação.

2. Selecione **Todos os serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3. Selecione **Intune** para abrir o dashboard do Microsoft Intune. Selecione **Acesso condicional** e, em seguida, em **Configuração**, selecione **Conector do serviço do Exchange**.

4.  Na página **Acesso condicional – Conector do serviço do Exchange**, selecione **Configurar o Serviço com o Conector de Serviços**. 
   
     ![Imagem a mostrar a seleção da ligação Configurar o Serviço com o Conector de Serviços](media/exchange_service_connector.png)

O Conector de Serviços configura e sincroniza automaticamente o seu Exchange Online ou o novo ambiente do Exchange Online Dedicado.

## <a name="validate-your-exchange-connection"></a>Validar a sua ligação ao Exchange

Após configurar com êxito o Conector de Serviços do Exchange, valide as informações de Servidor do Conector do Exchange na página **Acesso condicional – Conector do serviço do Exchange**.

Também pode ver o **Estado da ligação** e a data e hora da última tentativa de sincronização efetuada com êxito.

 