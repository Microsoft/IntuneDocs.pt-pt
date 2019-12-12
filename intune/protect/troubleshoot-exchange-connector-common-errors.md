---
title: Solucionar erros comuns para o Intune Exchange Connector
titleSuffix: Microsoft Intune
description: Solucionar problemas e resolver erros comuns para o Microsoft Intune Exchange Connector local
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b30a7e843850d6918abc2e76f84397a1f197516f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72508853"
---
# <a name="resolve-common-errors-for-the-intune-exchange-connector"></a>Resolver erros comuns para o Intune Exchange Connector

Este artigo pode ajudar o administrador do Intune a resolver erros e mensagens específicas sobre a operação do Intune Exchange Connector.  

## <a name="configuration-failed-and-returned-error-code-0x0000001"></a>Falha na configuração e retornou o código de erro 0x0000001

**Problema**:  
Ao tentar configurar o Microsoft Intune Exchange Connector, você receberá a seguinte mensagem de erro:

```
   The Microsoft Intune Exchange Connector cannot connect to the Microsoft Exchange server.  
   The following Microsoft Exchange Server address could not be reached <Exchange server Name FQDN>  
   Verify that the FQDN of the exchange server address and credentials that you entered is correct and the server is running. The Microsoft Intune Exchange Connector does not support Exchange server arrays.  
   Error code: 0x0000001  
```

Esse problema pode ocorrer se as configurações de proxy da Internet estiverem configuradas incorretamente.

**Resolução**:  
Definir configurações de proxy:
1. Contate o administrador da rede local para certificar-se de que as configurações de proxy estão definidas corretamente. 
2. Use o comando **netsh WinHTTP** para configurar o servidor proxy e adicionar a lista de exclusão necessária. Por exemplo:  

   ```
   Netsh winhttp set proxy proxy-server="http=proxy.corp.domain.com" bypass-list"34*.*;134.132.*.*;10.*.*;localhost;*.corp.domain.com;*.staging.domain.com"
   ```

## <a name="configuration-failed-and-returned-error-code-0x000000b"></a>Falha na configuração e retornou o código de erro 0x000000b   

**Problema**:  
Ao tentar configurar o Microsoft Intune Exchange Connector, você receberá a seguinte mensagem de erro:  

```
   The Microsoft Intune Exchange Connector experienced an error:  
   CertEnroll::CX509PrivateKey::Create: The system cannot find the file specified. 0x80070002 (WIN32: 2  
   ERROR_FILE_NOT_FOUND  
   Error code: 0x000000b  
```
Esse problema pode ocorrer se a conta que você usou para entrar no Intune não for uma conta de administrador global do Intune.

**Resolução**:  
Entre no Intune com uma conta que seja um administrador global ou adicione sua conta ao grupo de administração global. Para obter mais informações, consulte [RBAC (controle de administração baseada em funções) com Microsoft Intune](../fundamentals/role-based-access-control.md).

## <a name="configuration-failed-and-returned-error-code-0x0000006"></a>Falha na configuração e retornou o código de erro 0x0000006

**Problema**:  
Ao tentar configurar o Microsoft Intune Exchange Connector, você receberá a seguinte mensagem de erro:  

```  
   The Microsoft Intune Exchange Connector cannot connect to Microsoft Intune  
   Verify that you are connected to the Internet, check the Microsoft Intune Service Status, and try to connect again.  
   Error code: 0x00000006  
```  
Esse erro pode ocorrer se um servidor proxy for usado para se conectar à Internet e estiver bloqueando o tráfego para o serviço do Intune. Para determinar se um proxy está em uso, vá para **painel de controle** > **Opções da Internet**, selecione a guia **conexão** e clique em **configurações de LAN**.

**Resolução**:  

- **Opção 1** -remova as configurações de proxy para permitir que o computador se conecte à Internet sem passar pelo proxy.  

- **Opção 2** -configure o servidor proxy para permitir a comunicação com o serviço do Intune, conforme documentado nos [requisitos do Intune Exchange Connector](exchange-connector-install.md#intune-exchange-connector-requirements).



## <a name="event-7000-or-7041-microsoft-intune-exchange-connector-service-wont-start"></a>Evento 7000 ou 7041: Microsoft Intune Exchange Connector serviço não será iniciado

**Problema**:  
Um dispositivo iOS falha ao registrar no Intune e gera uma das seguintes mensagens de erro:  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Task Category: None
   Level:               Error
   Keywords:        Classic
   User:                N/A
   Computer:      <computer>
   Description:
   The Microsoft Intune Exchange Connector Service service failed to start because of the following error:  
   The service did not start because of a logon failure.
```  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Event ID:          7041
   Task Category: None
   Level:               Error   
   Keywords:        Classic
   User:                N/A
   Computer:       <computer>
   Description:
   The WIEC service was unable to log on as .\WIEC_USER with the currently configured password because of the following error:
   Logon failure: the user has not been granted the requested logon type at this computer.
   Service: WIEC
   Domain and account: .\WIEC_USER
   This service account does not have the required user right "Log on as a service."  
```
Esse problema pode ocorrer se a conta de **WIEC_User** não tiver o direito de usuário **fazer logon como serviço** na política local.

**Resolução**:  
No computador que executa o Exchange Connector do Intune, atribua o direito de usuário **fazer logon como um serviço** à conta de serviço **WIEC_User** . Se o computador for um nó em um cluster, certifique-se de atribuir o direito de usuário *fazer logon como um serviço* à conta de serviço de cluster em todos os nós no cluster.  

Para atribuir o direito de usuário **fazer logon como um serviço** à conta de serviço **WIEC_User** no computador, siga estas etapas:

1. Faça logon no computador como administrador ou como membro do grupo Administradores.
2. Execute **secpol. msc** para abrir a política de segurança local.
3. Vá para **configurações de segurança** > **políticas locais**e, em seguida, selecione **atribuição de direitos de usuário**.
4. No painel direito, clique duas vezes em **fazer logon como um serviço**.
5. Selecione **Adicionar usuário ou grupo**, adicionar **WIEC_USER** à política e, em seguida, selecione **OK** duas vezes.

Se o direito de usuário **fazer logon como um serviço** foi atribuído a **WIEC_User** , mas foi removido posteriormente, contate o administrador do domínio para determinar se uma configuração de política de grupo está substituindo-a.  

## <a name="next-steps"></a>Próximos passos  

O artigo a seguir pode ajudar a resolver erros específicos:
- [Resolver problemas comuns do Intune Exchange Connector](troubleshoot-exchange-connector-common-problems.md). git 

Procure assistência do suporte ou da Comunidade do Intune.
- Consulte [obter suporte](../fundamentals/get-support.md) para usar o console do Intune para ajudar a solucionar o problema ou para abrir um caso de suporte com a Microsoft. 
- Poste seu problema nos [fóruns de Microsoft Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
