---
title: Como utilizar o Azure AD para aceder às APIs do Intune no Microsoft Graph
titlesuffix: Microsoft Intune
description: Descreve os passos necessários para as aplicações utilizarem o Azure AD para acederem às APIs do Intune no Microsoft Graph.
keywords: funções de permissão da graph api do intune para c# powershell
author: dougeby
manager: dougeby
ms.author: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 79A67342-C06D-4D20-A447-678A6CB8D70A
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5129484a3cfea873be4009849b5989f9c2acd888
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187454"
---
# <a name="how-to-use-azure-ad-to-access-the-intune-apis-in-microsoft-graph"></a>Como utilizar o Azure AD para aceder às APIs do Intune no Microsoft Graph

A [Microsoft Graph API](https://developer.microsoft.com/graph/) suporta agora o Microsoft Intune com APIs específicas e funções de permissão.  A API do Microsoft Graph utiliza o Azure Active Directory (Azure AD) para a autenticação e o controlo de acesso.  
O acesso às APIs do Intune no Microsoft Graph exige:

- Um ID de aplicação com:

    - Permissão para chamar o Azure AD e as APIs do Microsoft Graph.
    - Âmbitos de permissão relevantes para as tarefas da aplicação específica.

- Credenciais de utilizador com:

    - Permissão para aceder ao inquilino do Azure AD associado à aplicação.
    - Permissões de função necessárias para suportar os âmbitos de permissão da aplicação.

- O utilizador final para conceder permissão à aplicação para executar as tarefas de aplicações para o respetivo inquilino do Azure.

Este artigo:

- Mostra como registar uma aplicação com acesso à API do Microsoft Graph e às funções de permissão relevantes.

- Descreve as funções de permissão da API do Intune.

- Fornece exemplos de autenticação da API do Intune para o C# e o PowerShell.

- Descreve como suportar vários inquilinos.

Para saber mais, veja:

- [Authorize access to web applications using OAuth 2.0 and Azure Active Directory (Autorizar o acesso a aplicações Web com o OAuth 2.0 e o Azure Active Directory)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)
- [Introdução à autenticação do Azure AD](https://www.visualstudio.com/docs/integrate/get-started/auth/oauth)
- [Integrating applications with Azure Active Directory (Integrar aplicações com o Azure Active Directory)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)
- [Compreender o OAuth 2.0](https://oauth.net/2/)

## <a name="register-apps-to-use-the-microsoft-graph-api"></a>Registar aplicações para utilizar a API do Microsoft Graph

Para registar uma aplicação para utilizar a API do Microsoft Graph:

1.  Inicie sessão no [portal do Azure](https://portal.azure.com) com credenciais administrativas.

    Conforme adequado, pode utilizar:
    - A conta de administrador de inquilino.
    - Uma conta de utilizador inquilino com a definição **Os utilizadores podem registar aplicações** ativada.

2.  No menu, escolha **Azure Active Directory** &gt; **Registos de Aplicações**.

    <img src="./media/azure-ad-app-reg.png" width="157" height="170" alt="The App registrations menu command" />

3.  Escolha **Novo registo de aplicação** para criar uma nova aplicação ou escolha uma aplicação existente.  (Se escolher uma aplicação existente, avance o próximo passo.)

4.  No painel **Criar**, especifique o seguinte:

    1.  Um **Nome** para a aplicação (apresentado quando os utilizadores iniciam sessão).

    2.  Os valores **Tipo de aplicação** e **URI de Redirecionamento**.

        Estes variam de acordo com os seus requisitos. Por exemplo, se estiver a utilizar uma [Biblioteca de Autenticação](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL) do Azure AD, defina o **Tipo de Aplicação** como `Native` e o **URI de Redirecionamento** como `urn:ietf:wg:oauth:2.0:oob`.

        <img src="media/azure-ad-app-new.png" width="209" height="140" alt="New app properties and values" />

        Para saber mais, consulte [Cenários de Autenticação do Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios).

5.  No painel da aplicação:

    1.  Tenha em conta o valor **ID da Aplicação**.

    2.  Escolha **Definições** &gt; **Acesso à API** &gt; **Permissões necessárias**.

    <img src="media/azure-ad-req-perm.png" width="483" height="186" alt="The Required permissions setting" />

6.  No painel **Permissões Necessárias**, escolha **Adicionar** &gt; **Adicionar acesso à API** &gt; **Selecionar uma API**.

    <img src="media/azure-ad-add-graph.png" width="436" height="140" alt="The Microsoft Graph setting" />

7.  No painel **Selecionar uma API**, escolha **Microsoft Graph** &gt; **Selecionar**.  O painel **Ativar acesso** é apresentado e indica os âmbitos de permissão disponíveis para a sua aplicação.

    <img src="media/azure-ad-perm-scopes.png" width="489" height="248" alt="Intune Graph API permission scopes" />

    Escolha as funções necessárias para a sua aplicação ao colocar uma marca de verificação à esquerda dos nomes relevantes.  Para saber mais sobre os âmbitos de permissão específicos do Intune, veja [Âmbitos de permissão do Intune](#intune-permission-scopes).  Para saber mais sobre outros âmbitos de permissão da Graph API, veja [Microsoft Graph permissions reference (Referência de permissões do Microsoft Graph)](https://developer.microsoft.com/graph/docs/concepts/permissions_reference).

    Para obter melhores resultados, escolha as funções mínimas necessárias para implementar a sua aplicação.

    Quando concluir, escolha **Selecionar** e **Concluído** para guardar as alterações.

Neste ponto, também poderá:

- Escolher conceder permissão a todas as contas de inquilinos para utilizar a aplicação sem fornecer credenciais.  

    Para tal, escolha **Conceder permissões** e aceite o pedido de confirmação.

    Quando executar a aplicação pela primeira vez, será pedido para conceder a permissão de aplicação para executar as funções selecionadas.

    <img src="media/azure-ad-grant-perm.png" width="351" height="162" alt="The Grant permissions button" />

- Tornar a aplicação disponível para utilizadores fora do seu inquilino.  (Normalmente, tal é apenas necessário para suportar vários inquilinos/organizações.)  

    Para tal:

  1. Escolha **Manifesto** no painel da aplicação, o qual abre o painel **Editar Manifesto**.

     <img src="media/azure-ad-edit-mft.png" width="295" height="114" alt="The Edit manifest blade" />

  2. Altere o valor da definição `availableToOtherTenants` para `true`.

  3. Guarde as suas alterações.

## <a name="intune-permission-scopes"></a>Âmbitos de permissão do Intune

O Azure AD e o Microsoft Graph utilizam âmbitos de permissão para controlarem o acesso aos recursos empresariais.  

Os âmbitos de permissão (também chamados _âmbitos do OAuth_) controlam o acesso a entidades específicas do Intune e às respetivas propriedades. Esta secção resume os âmbitos de permissão das funcionalidades da API do Intune.

Para saber mais:
- [Azure AD authentication (Autenticação do Azure AD)](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication)
- [Âmbitos de permissão de aplicações](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-scopes)

Quando concede permissão ao Microsoft Graph, pode especificar os seguintes âmbitos para controlar o acesso às funcionalidades do Intune: a tabela seguinte resume os âmbitos de permissão da API do Intune.  A primeira coluna mostra o nome da funcionalidade, conforme apresentado no portal do Azure, e a segunda coluna fornece o nome do âmbito de permissão.

Definição _Ativar Acesso_ | Nome do âmbito
:--|:--
__Executar ações remotas que afetam o utilizador em dispositivos do Microsoft Intune__ | [DeviceManagementManagedDevices.PrivilegedOperations.All](#mgd-po)
__Leitura e escrita de dispositivos do Microsoft Intune__ | [DeviceManagementManagedDevices.ReadWrite.All](#mgd-rw)
__Leitura de dispositivos do Microsoft Intune__ | [DeviceManagementManagedDevices.Read.All](#mgd-ro)
__Leitura e escrita de definições de RBAC do Microsoft Intune__ | [DeviceManagementRBAC.ReadWrite.All](#rac-rw)
__Leitura de definições de RBAC do Microsoft Intune__ | [DeviceManagementRBAC.Read.All](#rac=ro)
__Leitura e escrita de aplicações do Microsoft Intune__ | [DeviceManagementApps.ReadWrite.All](#app-rw)
__Leitura de aplicações do Microsoft Intune__ | [DeviceManagementApps.Read.All](#app-ro)
__Leitura e escrita da Configuração e Políticas de Dispositivos do Microsoft Intune__ | [DeviceManagementConfiguration.ReadWrite.All](#cfg-rw)
__Leitura da Configuração e Políticas de Dispositivos do Microsoft Intune__ | [DeviceManagementConfiguration.Read.All](#cfg-ro)
__Leitura e escrita da configuração do Microsoft Intune__ | [DeviceManagementServiceConfig.ReadWrite.All](#svc-rw)
__Leitura da configuração do Microsoft Intune__ | [DeviceManagementServiceConfig.Read.All](#svc-ra)

A tabela lista as definições tal como são apresentadas no portal do Azure. As secções a seguir descrevem os âmbitos por ordem alfabética.

Neste momento, todos os âmbitos de permissão do Intune exigem acesso de administrador.  Isto significa que precisa de ter credenciais correspondentes ao executar aplicações ou scripts que acedam aos recursos da API do Intune.

### <a name="app-ro"></a>DeviceManagementApps.Read.All

- Definição **Ativar Acesso**: __leitura de aplicações do Microsoft Intune__

- Permite o acesso de leitura às seguintes propriedades e estado da entidade:
    - Aplicações Cliente
    - Categorias de Aplicações Móveis
    - Políticas de Proteção de Aplicações
    - Configurações de Aplicações

### <a name="app-rw"></a>DeviceManagementApps.ReadWrite.All

- Definição **Ativar Acesso**: __leitura e escrita de aplicações do Microsoft Intune__

- Permite as mesmas operações de __DeviceManagementApps.Read.All__

- Também permite alterações às entidades a seguir:

    - Aplicações Cliente
    - Categorias de Aplicações Móveis
    - Políticas de Proteção de Aplicações
    - Configurações de Aplicações

### <a name="cfg-ro"></a>DeviceManagementConfiguration.Read.All

- Definição **Ativar Acesso**: __leitura da configuração e políticas de dispositivos do Microsoft Intune__

- Permite o acesso de leitura às seguintes propriedades e estado da entidade:
    - Configuração do Dispositivo
    - Política de Conformidade de Dispositivos
    - Mensagens de Notificação

### <a name="cfg-ra"></a>DeviceManagementConfiguration.ReadWrite.All

- Definição **Ativar Acesso**: __leitura e escrita da configuração e políticas de dispositivos do Microsoft Intune__

- Permite as mesmas operações de __DeviceManagementConfiguration.Read.All__

- As aplicações também podem criar, atribuir, eliminar e alterar as entidades a seguir:
    - Configuração do Dispositivo
    - Política de Conformidade de Dispositivos
    - Mensagens de Notificação

### <a name="mgd-po"></a>DeviceManagementManagedDevices.PrivilegedOperations.All

- Definição **Ativar Acesso**: __Executar ações remotas que afetam o utilizador em dispositivos do Microsoft Intune__

- Permite as seguintes ações remotas num dispositivo gerido:
    - Extinguir
    - Eliminação
    - Repor/Recuperar Código de Acesso
    - Bloqueio Remoto
    - Ativar/Desativar o Modo Perdido
    - Limpar o PC
    - Reiniciar
    - Eliminar o Utilizador do Dispositivo Partilhado

### <a name="mgd-ro"></a>DeviceManagementManagedDevices.Read.All

- Definição **Ativar Acesso**: __leitura de dispositivos do Microsoft Intune__

- Permite o acesso de leitura às seguintes propriedades e estado da entidade:
    - Dispositivo Gerido
    - Categoria de Dispositivo
    - Aplicação Detetada
    - Ações remotas
    - Informações de malware

### <a name="mgd-rw"></a>DeviceManagementManagedDevices.ReadWrite.All

- Definição **Ativar Acesso**: __leitura e escrita de dispositivos do Microsoft Intune__

- Permite as mesmas operações de __DeviceManagementManagedDevices.Read.All__

- As aplicações também podem criar, eliminar e alterar as entidades a seguir:
    - Dispositivo Gerido
    - Categoria de Dispositivo

- As seguintes ações remotas também são permitidas:
    - Localizar dispositivos
    - Ignorar o bloqueio de ativação
    - Pedir assistência remota

### <a name="rac-ro"></a>DeviceManagementRBAC.Read.All

- Definição **Ativar Acesso**: __leitura de definições de RBAC do Microsoft Intune__

- Permite o acesso de leitura às seguintes propriedades e estado da entidade:
    - Atribuições de Funções
    - Definições de Funções
    - Operações de Recursos

### <a name="rac-rw"></a>DeviceManagementRBAC.ReadWrite.All

- Definição **Ativar Acesso**: __leitura e escrita de definições de RBAC do Microsoft Intune__

- Permite as mesmas operações de __DeviceManagementRBAC.Read.All__

- As aplicações também podem criar, atribuir, eliminar e alterar as entidades a seguir:
    - Atribuições de Funções
    - Definições de Funções

### <a name="svc-ro"></a>DeviceManagementServiceConfig.Read.All

- Definição **Ativar Acesso**: __leitura da configuração do Microsoft Intune__

- Permite o acesso de leitura às seguintes propriedades e estado da entidade:
    - Inscrição de Dispositivos
    - Certificado Apple Push Notification
    - Programa de Inscrição de Dispositivos Apple
    - Apple Volume Purchase Program
    - Exchange Connector
    - Termos e Condições
    - Gestão de Despesas de Telecomunicações
    - PKI na Cloud
    - Imagem Corporativa
    - Defesa Contra Ameaças para Dispositivos Móveis

### <a name="svc-rw"></a>DeviceManagementServiceConfig.ReadWrite.All

- Definição **Ativar Acesso**: __leitura e escrita da configuração do Microsoft Intune__

- Permite as mesmas operações que o DeviceManagementServiceConfig.Read.All

- As aplicações também podem configurar as seguintes funcionalidades do Intune:
    - Inscrição de Dispositivos
    - Certificado Apple Push Notification
    - Programa de Inscrição de Dispositivos Apple
    - Apple Volume Purchase Program
    - Exchange Connector
    - Termos e Condições
    - Gestão de Despesas de Telecomunicações
    - PKI na Cloud
    - Imagem Corporativa
    - Defesa Contra Ameaças para Dispositivos Móveis

## <a name="azure-ad-authentication-examples"></a>Exemplos de autenticação do Azure AD

Esta secção mostra como incorporar o Azure AD com seus projetos do C# e PowerShell.

Em cada exemplo, precisará de especificar um ID de aplicação que tenha pelo menos o `DeviceManagementManagedDevices.Read.All` âmbito de permissão (discutido anteriormente).

Ao testar o exemplo, poderá receber erros de estado HTTP 403 (Proibido) semelhantes ao seguinte:

``` javascript
{
  "error": {
    "code": "Forbidden",
    "message": "Application is not authorized to perform this operation - Operation ID " +
       "(for customer support): 00000000-0000-0000-0000-000000000000 - " +
       "Activity ID: cc7fa3b3-bb25-420b-bfb2-1498e598ba43 - " +
       "Url: https://example.manage.microsoft.com/" +
       "Service/Resource/RESTendpoint?" +
       "api-version=2017-03-06 - CustomApiErrorPhrase: ",
    "innerError": {
      "request-id": "00000000-0000-0000-0000-000000000000",
      "date": "1980-01-0112:00:00"
    }
  }
}
```

Caso tal aconteça, verifique se:

- Atualizou o ID da aplicação para um autorizado para utilizar a API do Microsoft Graph e o âmbito de permissão `DeviceManagementManagedDevices.Read.All`.

- As suas credenciais de inquilino suportam funções administrativas.

- O seu código é semelhante aos exemplos apresentados.


### <a name="authenticate-azure-ad-in-c"></a>Autenticação do Azure AD no C\#

Este exemplo mostra como utilizar o C# para recuperar uma lista de dispositivos associados à sua conta do Intune.

1.  Inicie o Visual Studio e, em seguida, crie um novo projeto de aplicação da Consola do Visual C# (.NET Framework).

2.  Introduza um nome para o seu projeto e forneça outros detalhes conforme pretendido.

    <img src="media/aad-auth-cpp-new-console.png" width="624" height="433" alt="Creating a C# console app project in Visual Studio"  />

3.  Utilize o Explorador de Soluções para adicionar o pacote Microsoft ADAL NuGet ao projeto.

    1.  Clique com o botão direito do rato no Explorador de Soluções.
    2.  Escolha **Gerir Pacotes NuGet...** &gt;**Procurar**.
    3.  Selecione `Microsoft.IdentityModel.Clients.ActiveDirectory` e, em seguida, **Instalar**.

    <img src="media/aad-auth-cpp-install-package.png" width="624" height="458" alt="Selecting the Azure AD identity model module" />

4.  Adicione as seguintes instruções para a parte superior do **Program.cs**:

    ``` csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;</p>
    using System.Net.Http;
    ```

5.  Adicione um método para criar o cabeçalho de autorização:

    ``` csharp
    private static async Task<string> GetAuthorizationHeader()
    {
        string applicationId = "<Your Application ID>";
        string authority = "https://login.microsoftonline.com/common/";
        Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
        AuthenticationContext context = new AuthenticationContext(authority);
        AuthenticationResult result = await context.AcquireTokenAsync(
            "https://graph.microsoft.com",
            applicationId, redirectUri,
            new PlatformParameters(PromptBehavior.Auto));
        return result.CreateAuthorizationHeader();
    ```

    Lembre-se de alterar o valor de `application_ID` para corresponder a pelo menos um `DeviceManagementManagedDevices.Read.All` âmbito de permissão concedido, conforme descrito anteriormente.

6. Adicione um método para recuperar a lista de dispositivos:

    ``` csharp
    private static async Task<string> GetMyManagedDevices()
    {
        string authHeader = await GetAuthorizationHeader();
        HttpClient graphClient = new HttpClient();
        graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
        return await graphClient.GetStringAsync(
            "https://graph.microsoft.com/beta/me/managedDevices");
    }
    ```

7.  Atualize **Principal** para chamar **GetMyManagedDevices**:

    ``` csharp
    string devices = GetMyManagedDevices().GetAwaiter().GetResult();
    Console.WriteLine(devices);
    ```

8.  Compile e execute o programa.  

Ao executar o programa pela primeira vez, deve receber dois pedidos.  O primeiro pede as suas credenciais e o segundo concede permissões para o `managedDevices` pedido.  

Para referência, eis o programa concluído:

``` csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System;
using System.Net.Http;
using System.Threading.Tasks;

namespace IntuneGraphExample
{
    class Program
    {
        static void Main(string[] args)
        {
            string devices = GetMyManagedDevices().GetAwaiter().GetResult();
            Console.WriteLine(devices);
        }

        private static async Task<string> GetAuthorizationHeader()
        {
            string applicationId = "<Your Application ID>";
            string authority = "https://login.microsoftonline.com/common/";
            Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
            AuthenticationContext context = new AuthenticationContext(authority);
            AuthenticationResult result = await context.AcquireTokenAsync("https://graph.microsoft.com", applicationId, redirectUri, new PlatformParameters(PromptBehavior.Auto));
            return result.CreateAuthorizationHeader();
        }

        private static async Task<string> GetMyManagedDevices()
        {
            string authHeader = await GetAuthorizationHeader();
            HttpClient graphClient = new HttpClient();
            graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
            return await graphClient.GetStringAsync("https://graph.microsoft.com/beta/me/managedDevices");
        }
    }
}
```

### <a name="authenticate-azure-ad-powershell"></a>Autenticar o Azure AD (PowerShell)

O script do PowerShell a seguir utiliza o módulo AzureAD PowerShell para autenticação.  Para saber mais, veja [Azure Active Directory PowerShell Version 2 (Versão 2 do Azure Active Directory PowerShell)](https://docs.microsoft.com/powershell/azure/install-adv2?view=azureadps-2.0) e os [Exemplos do Intune PowerShell](https://github.com/microsoftgraph/powershell-intune-samples).

Neste exemplo, atualize o valor de `$clientID` para corresponder a um ID de aplicação válido.

``` powershell
function Get-AuthToken {
    [cmdletbinding()]
    param
    (
        [Parameter(Mandatory = $true)]
        $User
    )

    $userUpn = New-Object "System.Net.Mail.MailAddress" -ArgumentList $User
    $tenant = $userUpn.Host

    Write-Host "Checking for AzureAD module..."

    $AadModule = Get-Module -Name "AzureAD" -ListAvailable
    if ($AadModule -eq $null) {
        Write-Host "AzureAD PowerShell module not found, looking for AzureADPreview"
        $AadModule = Get-Module -Name "AzureADPreview" -ListAvailable
    }

    if ($AadModule -eq $null) {
        write-host
        write-host "AzureAD Powershell module not installed..." -f Red
        write-host "Install by running 'Install-Module AzureAD' or 'Install-Module AzureADPreview' from an elevated PowerShell prompt" -f Yellow
        write-host "Script can't continue..." -f Red
        write-host
        exit
    }

    # Getting path to ActiveDirectory Assemblies
    # If the module count is greater than 1 find the latest version

    if ($AadModule.count -gt 1) {
        $Latest_Version = ($AadModule | select version | Sort-Object)[-1]
        $aadModule = $AadModule | ? { $_.version -eq $Latest_Version.version }
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    else {
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    [System.Reflection.Assembly]::LoadFrom($adal) | Out-Null
    [System.Reflection.Assembly]::LoadFrom($adalforms) | Out-Null

    $clientId = "<Your Application ID>"
    $redirectUri = "urn:ietf:wg:oauth:2.0:oob"
    $resourceAppIdURI = "https://graph.microsoft.com"
    $authority = "https://login.microsoftonline.com/$Tenant"

    try {
        $authContext = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext" -ArgumentList $authority
        # https://msdn.microsoft.com/library/azure/microsoft.identitymodel.clients.activedirectory.promptbehavior.aspx
        # Change the prompt behaviour to force credentials each time: Auto, Always, Never, RefreshSession
        $platformParameters = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.PlatformParameters" -ArgumentList "Auto"
        $userId = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.UserIdentifier" -ArgumentList ($User, "OptionalDisplayableId")
        $authResult = $authContext.AcquireTokenAsync($resourceAppIdURI, $clientId, $redirectUri, $platformParameters, $userId).Result
        # If the accesstoken is valid then create the authentication header
        if ($authResult.AccessToken) {
            # Creating header for Authorization token
            $authHeader = @{
                'Content-Type' = 'application/json'
                'Authorization' = "Bearer " + $authResult.AccessToken
                'ExpiresOn' = $authResult.ExpiresOn
            }
            return $authHeader
        }
        else {
            Write-Host
            Write-Host "Authorization Access Token is null, please re-run authentication..." -ForegroundColor Red
            Write-Host
            break
        }
    }
    catch {
        write-host $_.Exception.Message -f Red
        write-host $_.Exception.ItemName -f Red
        write-host
        break
    }   
}

$authToken = Get-AuthToken -User "<Your AAD Username>"

try {
    $uri = "https://graph.microsoft.com/beta/me/managedDevices"
    Write-Verbose $uri
    (Invoke-RestMethod -Uri $uri –Headers $authToken –Method Get).Value
}
catch {
    $ex = $_.Exception
    $errorResponse = $ex.Response.GetResponseStream()
    $reader = New-Object System.IO.StreamReader($errorResponse)
    $reader.BaseStream.Position = 0
    $reader.DiscardBufferedData()
    $responseBody = $reader.ReadToEnd();
    Write-Host "Response content:`n$responseBody" -f Red
    Write-Error "Request to $Uri failed with HTTP Status $($ex.Response.StatusCode) $($ex.Response.StatusDescription)"
    write-host
    break
}
```

## <a name="support-multiple-tenants-and-partners"></a>Suportar vários inquilinos e parceiros

Se a sua organização suportar organizações com os seus próprios inquilinos do Azure AD, poderá querer permitir que os seus clientes utilizem a sua aplicação com os respetivos inquilinos.

Para tal:

1.  Verifique se a conta de cliente existe no inquilino do Azure AD de destino.

2.  Verifique se a sua conta de inquilino permite que os utilizadores registem aplicações (consulte **Configurações do utilizador**).

3.  Estabeleça uma relação entre cada inquilino.  

    Para tal:

    a. Utilize o [Microsoft Partner Center](https://partnercenter.microsoft.com/) para definir uma relação com o cliente e o respetivo endereço de e-mail.

    b. Convide utilizadores para se tornarem um convidado do seu inquilino.

Para convidar o utilizador para ser um convidado do seu inquilino:

1.  Escolha **Adicionar um utilizador convidado** no painel **Tarefas rápidas**.

    <img src="media/azure-ad-add-guest.png" width="448" height="138" alt="Use Quick Tasks to add a guest user" />

2.  Introduza o endereço de e-mail do cliente e (opcionalmente) adicione uma mensagem personalizada para o convite.

    <img src="media/azure-ad-guest-invite.png" width="203" height="106" alt="Inviting an external user as a guest" />

3.  Escolha **Convidar**.

Este procedimento envia um convite ao utilizador.

   <img src="media/aad-multiple-tenant-invitation.png" width="624" height="523" alt="A sample guest invitation" />

   O utilizador precisa de escolher a ligação **Começar Agora** para aceitar o convite.

Quando a relação for estabelecida (ou o seu convite tiver sido aceite), adicione a conta de utilizador à **Função de diretório**.

Lembre-se de adicionar o utilizador a outras funções, conforme necessário. Por exemplo, para permitir ao utilizador gerir as definições do Intune, aquele precisa de ser um **Administrador Global** ou um **Administrador de Serviço do Intune**.

Além disso:

- Utilize https://portal.office.com para atribuir uma licença do Intune à sua conta de utilizador.

- Atualize o código da aplicação para autenticar o domínio de inquilino do Azure AD do cliente em vez do seu próprio.

    Por exemplo, suponha que o seu domínio de inquilino é `contosopartner.onmicrosoft.com` e o domínio de inquilino do cliente é `northwind.onmicrosoft.com`, deve atualizar o seu código para autenticar o inquilino do cliente.

    Para fazer isso numa aplicação do C# com base no exemplo anterior, altere o valor da variável `authority`:

    ``` csharp
    string authority = "https://login.microsoftonline.com/common/";
    ```

    como

    ``` csharp
    string authority = "https://login.microsoftonline.com/northwind.onmicrosoft.com/";
    ```
