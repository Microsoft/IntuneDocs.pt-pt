---
title: Solução de problemas de integração do JAMF pro com o Microsoft Intune
titleSuffix: Microsoft Intune
description: Sugestões para solucionar alguns dos problemas mais comuns ao integrar dispositivos JAMF pro para Mac, com Microsoft Intune.
keywords: ''
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
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 44733eb369e520d2d5f0ff548d4f1921abcb8758
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503574"
---
# <a name="troubleshoot-integration-of-jamf-pro-with-microsoft-intune"></a>Solucionar problemas de integração do JAMF pro com o Microsoft Intune

Este artigo ajuda os administradores do Intune a entender e solucionar problemas com a integração do JAMF pro para macOS com o Intune.

> [!TIP]  
> Grande parte das informações neste artigo apareceu originalmente na [solução de problemas ao integrar o JAMF com o Microsoft Intune](https://support.microsoft.com/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune) no support.Microsoft.com.

## <a name="prerequisites"></a>Pré-requisitos

Antes de iniciar a solução de problemas, colete algumas informações básicas para esclarecer o problema e reduzir o tempo para encontrar uma resolução. Por exemplo, quando você encontrar um problema relacionado à integração do JAMF-Intune, sempre verifique se os pré-requisitos foram atendidos. Examine as seguintes considerações antes de iniciar a solução de problemas:

- Examine os pré-requisitos em [integrar o JAMF pro ao Intune](conditional-access-integrate-jamf.md#prerequisites).
- Todos os usuários devem ter licenças Microsoft Intune e Microsoft AAD Premium P1 
- Você deve ter uma conta de usuário que tenha permissões de integração de Microsoft Intune no console do JAMF pro.
- Você deve ter uma conta de usuário que tenha permissões de administrador global no Azure.


Considere as seguintes informações ao investigar a integração do JAMF pro com o Intune: 
- Qual é a mensagem de erro exata?
- Onde está a mensagem de erro?
- Quando o problema foi iniciado?  A integração do JAMF pro com o Intune já funcionou?
- Quantos usuários são afetados? Todos os usuários foram afetados ou apenas alguns?
- Quantos dispositivos são afetados? Todos os dispositivos foram afetados ou apenas alguns?
 

## <a name="common-problems"></a>Problemas comuns 

As informações a seguir podem ajudá-lo a identificar e resolver problemas comuns de dispositivos depois de configurar a integração do Intune com o JAMF pro.  

| Problema   | Mais informações                  |
|-----------------|--------------------------|
| **Os dispositivos são marcados como sem resposta no JAMF pro**  | [Os dispositivos falham ao fazer check-in com o JAMF pro ou com o Azure AD](#devices-are-marked-as-unresponsive-in-jamf-pro) |
| **Os dispositivos Mac solicitam a entrada do conjunto de chaves quando você abre um aplicativo falha ao registrar**  | [Os usuários são solicitados a fornecer sua senha para permitir que os aplicativos se registrem no Azure ad](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app). |
| **Falha ao registrar dispositivos**  | As causas a seguir podem ser aplicáveis: <br> **-** [ ***causa 1*** -o aplicativo JAMF pro no Azure tem permissões incorretas](#cause-1) <br> **-** [ ***causa 2*** – há um problema para o *conector JAMF nativo do MacOS* no Azure AD](#cause-2) <br> **-** [ ***causa 3*** -o usuário não tem uma licença válida do Intune ou do JAMF](#cause-3) <br> **-** [ ***causa 4*** -o usuário não usou o autoatendimento JAMF para iniciar o aplicativo portal da empresa](#cause-4) <br> **-** [ ***causa 5*** -a integração do Intune está desativada](#cause-5) <br> **-** [ ***causa 6*** -o dispositivo foi registrado anteriormente no Intune ou o usuário tentou registrar o dispositivo várias vezes](#cause-6) <br> **-** [ ***fazer com que*** o JamfAAD solicite acesso a uma "chave do Microsoft Workplace Join" do conjunto de chaves dos usuários](#cause-7) |
|  **O dispositivo Mac mostra a conformidade no Intune, mas não está em conformidade no Azure** | [Problemas de registro de dispositivo](#mac-device-shows-compliant-in-intune-but-noncompliant-in-azure) |
| **Entradas duplicadas aparecem no console do Intune para dispositivos Mac registrados usando JAMF** | [Vários registros partir o mesmo dispositivo](#duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf) |
| **A política de conformidade não avalia o dispositivo** | [Grupos de dispositivos de destino de política](#compliance-policy-fails-to-evaluate-the-device) |
| **Não foi possível recuperar o token de acesso para a API de Microsoft Graph** | As causas a seguir podem ser aplicáveis: <br> -[permissões para o aplicativo JAMF pro no Azure](#theres-a-permission-issue-with-the-jamf-pro-application-in-azure) <br> - [Licença expirada para o JAMF ou o Intune](#a-license-required-for-jamf-intune-integration-has-expired) <br> **-** [portas não estão abertas](#the-required-ports-arent-open-on-your-network)|
 

### <a name="devices-are-marked-as-unresponsive-in-jamf-pro"></a>Os dispositivos são marcados como sem resposta no JAMF pro  

**Causa**: Estas são as causas comuns dos dispositivos que estão sendo marcados como sem *resposta* pelo JAMF pro:

- O dispositivo falha ao fazer check-in com o JAMF pro.  
  O JAMF pro espera que os dispositivos verifiquem a cada 15 minutos. Os dispositivos são marcados como sem resposta por JAMF quando falham ao fazer check-in em um período de 24 horas.  

- O dispositivo falha ao fazer check-in com o Azure AD.  
  Com o registro bem-sucedido no Azure AD, os dispositivos macOS recebem um token do Azure:
  - Esse token é atualizado a cada 12 horas.   
  - Quando a atualização do token falha por 24 horas ou mais, o JAMF pro marca o dispositivo como sem resposta.  
  - Se o token do Azure expirar, os usuários serão solicitados a entrar no Azure para obter um novo token. Um token de atualização para o acesso do Azure é gerado a cada sete dias.

**Resolução**  
Depois que um dispositivo é marcado como sem *resposta* pelo JAMF pro, o usuário registrado do dispositivo deve entrar para corrigir o estado não responsivo. Ele deve ser o usuário que ingressou na conta como tendo a identidade do Intune em seu conjunto de chaves de logon.



### <a name="mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app"></a>Dispositivos Mac solicitam a entrada do conjunto de chaves quando você abre um aplicativo  

Depois de configurar a integração do Intune e do JAMF pro e implantar políticas de acesso condicional, os usuários de dispositivos gerenciados com o JAMF pro receber solicitarão uma senha ao abrir Microsoft Office aplicativos 365, como equipes, Outlook e outros aplicativos que exigem o Azure Autenticação do AD. 

Por exemplo, um prompt com texto semelhante ao exemplo a seguir é exibido ao abrir o Microsoft Teams:

``` 
  Microsoft Teams wants to sign using key “Microsoft Workplace Join Key” in your keychain.  
  To allow this, enter the “login” keychain password 
```

**Causa**: esses prompts são gerados pelo JAMF pro para cada aplicativo aplicável que requer o registro do Azure AD. 

  de **resolução**  
No prompt, o usuário deve fornecer a senha do dispositivo para entrar no Azure AD. As opções incluem:
- **Deny** -não entrar e não usar o aplicativo.
- **Permitir** -um logon único. Na próxima vez em que o aplicativo for aberto, ele solicitará a entrada novamente.
- **Sempre permitir** -as credenciais de entrada são armazenadas em cache para o aplicativo. Na próxima vez em que o aplicativo for aberto, ele não solicitará a entrada.  

Selecionar *sempre permitir* para um aplicativo aprova apenas esse aplicativo para entrada futura. Aplicativos adicionais solicitam autenticação até que eles também sejam definidos como *sempre permitir*. As credenciais armazenadas em cache para um aplicativo não podem ser usadas por outro aplicativo.  

### <a name="devices-fail-to-register"></a>Falha ao registrar dispositivos  

Há várias causas comuns para dispositivos Mac que falham no registro.  

#### <a name="cause-1"></a>Causa 1  

**O aplicativo JAMF Pro Enterprise no Azure tem a permissão incorreta ou tem mais de uma permissão**  

  Ao criar o aplicativo no Azure, você deve remover todas as permissões de API padrão e atribuir ao Intune uma única permissão de *update_device_attributes*. 

  **Resolução**  
  Examine e, se necessário, corrija as permissões para o aplicativo JAMF que você criou no Azure AD. Consulte o procedimento para [criar um aplicativo para JAMF no Azure ad](conditional-access-integrate-jamf.md#create-an-application-in-azure-active-directory). 

#### <a name="cause-2"></a>Causa 2  

**O aplicativo **conector JAMF nativo do MacOS** não foi criado no seu locatário do Azure ad ou o consentimento para o conector foi assinado por uma conta que não tem direitos de administrador global**  

  **Resolução**  
  Consulte a seção *Configurando a integração do MacOS Intune* em [integrando com Microsoft Intune](https://docs.jamf.com/10.13.0/jamf-pro/administrator-guide/Integrating_with_Microsoft_Intune.html) no docs.JAMF.com. 

#### <a name="cause-3"></a>Causa 3

**O usuário não tem uma licença do Intune ou JAMF válida**  

  A falta de uma licença válida pode resultar no seguinte erro, que indica que a licença do JAMF expirou:  
  ```
    Unable to connect to Microsoft Intune.  
    
    Check your Microsoft Intune Integration configuration.
  ```  

  **Resolução**
  - Licença do JAMF: entre em contato com o JAMF para obter assistência para obter uma nova licença para o JAMF.  
  - Licença do Intune: atribua uma licença válida ao usuário ou entre em contato com a Microsoft ou com o seu parceiro para obter informações sobre como obter uma licença atual.

#### <a name="cause-4"></a>Causa 4  

**O usuário não usou o *JAMF self service* para iniciar o aplicativo portal da empresa**

Para que um dispositivo se registre e se registre com êxito no Intune por meio do JAMF, o usuário deve usar o JAMF Self Service para abrir o Portal da Empresa do Intune. Se o usuário abrir o portal da empresa manualmente, o dispositivo registrará e registrará sem sua conexão com o JAMF.  

Para determinar qual serviço o dispositivo usou para registrar e registrar, procure no aplicativo Portal da Empresa no dispositivo. Quando registrado por meio do JAMF, você deve receber uma notificação para abrir o aplicativo de autoatendimento para fazer alterações.

No aplicativo Portal da Empresa, o usuário pode ver **`Not registered`** e uma entrada semelhante ao exemplo a seguir pode aparecer nos logs de portal da empresa:  

```
   Line 7783: <DATE> <IP ADDRESS> INFO com.microsoft.ssp.application TID=1  
 
   WelcomeViewController.swift: 253 (startLogin()) Portal launched without WPJ only arg while account is under partner management
```

**Resolução**  
Para alterar a fonte de registro do Intune para JAMF:
1. [Cancelar o registro do dispositivo MacOS do Intune](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-macos). Para evitar mais complicações para dispositivos que não são totalmente removidos do Intune, consulte a [*causa 6*](#cause-6) nesta lista de causas.  

2. No dispositivo, use o autoatendimento do JAMF para abrir o aplicativo Portal da Empresa e, em seguida, registre o dispositivo com o Intune. Essa tarefa exige que você tenha [usado o JAMF para implantar o aplicativo de portal da empresa para MacOS](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)e ter [criado uma política no JAMF pro que registra o dispositivo de usuários com o Azure ad](conditional-access-assign-jamf.md#create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory).  

3. Quando o portal é aberto, a primeira tela que você vê solicita que você entre. Usar sua conta corporativa ou de estudante  

4. O Portal da Empresa confirma as informações da sua conta e mostra o registro do dispositivo e os status de conformidade do dispositivo. Os triângulos amarelos realçam as ações que tem de efetuar para proteger o seu dispositivo macOS para a escola ou o trabalho. Clique em Iniciar para iniciar o registro.  

5. Se lhe for pedido, escreva as informações de início de sessão do seu computador.  
     
A inscrição do seu dispositivo na gestão poderá demorar alguns minutos. Durante este tempo, poderá fazer outras coisas no seu dispositivo. Irá receber uma mensagem após a conclusão da Configuração de Acesso da Empresa para o informar de que está pronto.

#### <a name="cause-5"></a>Causa 5  

**A integração com o Intune está desativada**

Se a integração do Intune estiver desativada, os usuários receberão uma janela pop-up no Portal da Empresa com a seguinte mensagem quando tentarem registrar um dispositivo:  

```
   Invalid command line input
   
   Registration-only command line flag (-r) can only be used when partner management is enabled in Intune. Please contact your IT admin.
```  

O servidor JAMF pro envia um pulso para os servidores do Intune quando a integração é desativada que informa ao Intune que a integração está desabilitada. 

**Resolução**  
Habilite novamente a integração do Intune no JAMF pro. Consulte [Configurar a integração de Microsoft Intune no JAMF pro](conditional-access-integrate-jamf.md#enable-intune-to-integrate-with-jamf-pro).


#### <a name="cause-6"></a>Causa 6  

**O dispositivo foi registrado anteriormente no Intune ou o usuário tentou registrar o dispositivo várias vezes**

Se um dispositivo tiver o registro cancelado no JAMF, mas não tiver sido removido corretamente do Intune ou várias tentativas de registro forem feitas, você poderá ver várias instâncias do mesmo dispositivo no Portal. Isso faz com que o registro de JAMF falhe.

**Resolução**  
1. No Mac, inicie o **terminal**.
2. Execute **sudo JAMF removemdmprofile**.
3. Execute **sudo JAMF removeFramework**.
4. No servidor JAMF pro, exclua o registro de inventário do computador.
5. Exclua o dispositivo de AzureAD.
6. Se existirem, exclua os seguintes arquivos no dispositivo:
   - Suporte a/library/Application Support/com. Microsoft. CompanyPortal. UserContext. info
   - Suporte a/library/Application Support/com. Microsoft. CompanyPortal
   - Suporte a/library/Application Support/com. jamfsoftware. autoatendimento. Mac
   - Aplicativo/Library/Saved
   - State/com. jamfsoftware. autoatendimento. Mac. savedState
   - Estado do aplicativo/Library/Saved/com. Microsoft. CompanyPortal. savedState
   - /Library/Preferences/com.microsoft.CompanyPortal.plist
   - /Library/Preferences/com.jamfsoftware.selfservice.mac.plist
   - /Library/Preferences/com.jamfsoftware.management.jamfAAD.plist
   - /Users/<username>/Library/Cookies/com.microsoft.CompanyPortal.binarycookies
   - /Users/<username>/Library/Cookies/com.jamf.management.jamfAAD.binarycookies
   - com. Microsoft. CompanyPortal
   - com. Microsoft. CompanyPortal. HockeySDK
   - enterpriseregistration.windows.net
   - https://device.login.microsoftonline.com
   - https://device.login.microsoftonline.com/
   - Chave de transporte de sessão da Microsoft (chaves públicas e privadas)
   - Chave do Microsoft Workplace Join (chaves públicas e privadas)
7. Remova qualquer coisa do conjunto de chaves no dispositivo que faz referência à *Microsoft*, ao *Intune*ou ao *portal da empresa*, incluindo certificados DeviceLogin.Microsoft.com. Remova as referências *JAMF* , exceto para a chave pública e privada do JAMF. 
   > [!IMPORTANT]  
   > A remoção da chave pública e privada interromperá o registro do dispositivo.

8. Exclua qualquer uma das seguintes entradas que você encontrar:  
   - Tipo: senha do aplicativo; Conta: com. Microsoft. workplacejoin. Thumbprint
   - Tipo: senha do aplicativo; Conta: com. Microsoft. workplacejoin. registeredUserPrincipalName
   - Tipo: certificado; Emitido por: MS-Organization-Access
   - Espécie: preferência de identidade; Nome (URL do STS do ADFS, se presente): https://adfs\<DNSName>.com/adfs/ls
   - Espécie: preferência de identidade; Nome: https://enterpriseregistration.windows.net
   - Espécie: preferência de identidade; Nome: https://enterpriseregistration.windows.net/  
9. Reinicie o dispositivo Mac.
10. Desinstale Portal da Empresa do dispositivo.
11. Vá para portal.manage.microsoft.com e exclua todas as instâncias do dispositivo Mac. Aguarde pelo menos 30 minutos antes de ir para a próxima etapa.
12. Registre novamente o dispositivo no JAMF pro.
13. Reabra o autoatendimento e inicie a política de registro.


#### <a name="cause-7"></a>Causa 7  

**JamfAAD solicita o acesso a uma "chave de Workplace Join da Microsoft" do conjunto de chaves dos usuários**

Durante o registro, o usuário de um dispositivo macOS recebe a seguinte solicitação para permitir o acesso de JamfAAD a uma chave de seu conjunto de chaves: 

```
   JamfAAD wants to access key “Microsoft Workplace Join Key" in your keychain. 
    
   To allow this, enter the “login” keychain password
```

**Resolução**  
Para registrar o dispositivo com êxito no Azure AD, o JAMF exige que o usuário forneça a senha da conta e selecione **permitir**.

Essa solicitação é semelhante à solicitação de [dispositivos Mac prompt para entrada do conjunto de chaves quando você abre um aplicativo](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app), anteriormente neste artigo.  

 
### <a name="mac-device-shows-compliant-in-intune-but-noncompliant-in-azure"></a>O dispositivo Mac mostra a conformidade no Intune, mas não está em conformidade no Azure  

**Causa**: as seguintes condições podem fazer com que um dispositivo seja exibido como em conformidade no Intune, mas não como em conformidade no Azure:  
- O dispositivo não está registrado corretamente.  
- O dispositivo foi registrado várias vezes sem a limpeza necessária.

**Resolução**  
Para resolver esse problema, siga a resolução da [*causa 6*](#cause-6) para os *dispositivos falharem no registro*, anteriormente neste artigo. 


### <a name="duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf"></a>Entradas duplicadas aparecem no console do Intune para dispositivos Mac registrados usando JAMF  
 
**Causa**: um dispositivo é registrado com o Intune várias vezes, normalmente sendo registrado novamente após ser removido do Intune.  

Quando um dispositivo é removido da integração do Intune e do JAMF pro, alguns dados podem ser deixados para trás, o que pode causar registros sucessivos para criar entradas duplicadas.  

**Resolução**  
Para resolver esse problema, siga a resolução da [*causa 6*](#cause-6) para os *dispositivos falharem no registro*, anteriormente neste artigo. 

### <a name="compliance-policy-fails-to-evaluate-the-device"></a>A política de conformidade não avalia o dispositivo  

**Causa**: a integração do JAMF com o Intune não oferece suporte à política de conformidade direcionada a grupos de dispositivos. 

**Resolução**  
Modifique a política de conformidade para que os dispositivos macOS sejam atribuídos a grupos de usuários. 


### <a name="could-not-retrieve-the-access-token-for-microsoft-graph-api"></a>Não foi possível recuperar o token de acesso para a API de Microsoft Graph

Você recebe o seguinte erro:

```
   Could not retrieve the access token for Microsoft Graph API. Check the configuration for Microsoft Intune Integration.
```   

A origem desse erro pode ser uma das seguintes causas: 

#### <a name="theres-a-permission-issue-with-the-jamf-pro-application-in-azure"></a>Há um problema de permissão com o aplicativo JAMF pro no Azure

Ao registrar o aplicativo JAMF pro no Azure, uma das seguintes condições ocorreu:  
- O aplicativo recebeu mais de uma permissão.
- A opção **conceder consentimento de administrador para *\<sua empresa >***  não foi selecionada.  

**Resolução**  
Veja a resolução da causa 1 para os [dispositivos falharem no registro](#devices-fail-to-register), anteriormente neste artigo.

#### <a name="a-license-required-for-jamf-intune-integration-has-expired"></a>Uma licença necessária para a integração do JAMF-Intune expirou

**Resolução**: consulte a resolução para a causa 3 para os [dispositivos falharem ao registrar](#devices-fail-to-register). 

#### <a name="the-required-ports-arent-open-on-your-network"></a>As portas necessárias não estão abertas na sua rede

**Resolução**: examine as informações de portas de rede em [pré-requisitos](conditional-access-integrate-jamf.md#prerequisites) para integração do JAMF pro com o Intune.


## <a name="next-steps"></a>Próximos passos
Saiba mais sobre como [integrar o JAMF pro ao Intune](conditional-access-integrate-jamf.md)