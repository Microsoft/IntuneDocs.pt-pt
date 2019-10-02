---
title: Autenticação apenas com a aplicação do Armazém de Dados do Intune
titleSuffix: Microsoft Intune
description: Este tópico descreve data warehouse autenticação somente de aplicativo para Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/27/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d7166563-6bb5-4624-b8c8-6b300a997c3a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2f70ca7d8d85853c38e2e8e88d06bae966431989
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730280"
---
# <a name="intune-data-warehouse-application-only-authentication"></a>Autenticação apenas com a aplicação do Armazém de Dados do Intune

Pode configurar uma aplicação com o Azure Active Directory (Azure AD) e autenticar para o Armazém de Dados do Intune. Este processo é útil para sites, aplicações e processos em segundo plano nos quais a aplicação não deve ter acesso às credenciais de utilizador. Através dos seguintes passos, está a autorizar a sua aplicação com o Azure AD com o OAuth 2.0.

## <a name="authorization"></a>Autorização

O Azure Active Directory (Azure AD) utiliza o OAuth 2.0 para lhe permitir autorizar o acesso a aplicações Web e a APIs Web no seu inquilino do Azure AD. Este guia mostra como autenticar a sua aplicação com C#. O fluxo do código de autorização de OAuth 2.0 é descrito na secção 4.1 da especificação de OAuth 2.0. Para obter mais informações, veja [Authorize access to web applications using OAuth 2.0 and Azure Active Directory (Autorizar o acesso a aplicações Web com o OAuth 2.0 e o Azure Active Directory)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).


## <a name="azure-keyvault"></a>Azure KeyVault

O seguinte processo utiliza um método privado para processar e converter uma chave da aplicação. Este método privado tem o nome SecureString. Em alternativa, pode utilizar o Azure KeyVault para armazenar a chave da aplicação. Para obter mais informações, veja [Key Vault](https://azure.microsoft.com/services/key-vault/).

## <a name="create-a-web-app"></a>Criar uma Aplicação Web

Nesta secção, proporcione os detalhes da aplicação Web que gostaria de apontar para o Intune. Uma aplicação Web é uma aplicação de servidor de cliente. O servidor proporciona a aplicação Web, que inclui a IU, conteúdos e funcionalidades. A manutenção deste tipo de aplicação é feita separadamente na Web. Utilize o Intune para conceder acesso à aplicação Web ao Intune. O fluxo de dados é iniciado através da aplicação Web. 

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Através do campo **Procurar recursos, serviços e documentos** junto à parte superior do portal do Azure, pesquise **Azure Active Directory**.
3. No menu pendente, selecione **do Azure Active Directory** em **Serviços**.
4. Selecione **Registos das aplicações**.
5. Clique em **Novo registo da aplicação** para apresentar o painel **Criar**.
6. No painel **Criar**, adicione os detalhes da aplicação:

    - O nome de uma aplicação, como *Autenticação apenas com a Aplicação do Intune*.
    - O **Tipo de aplicação**. Escolha **Aplicação Web/API** para adicionar uma aplicação que represente uma aplicação Web, uma API Web ou ambos.
    - O **URL de início de sessão** da aplicação. Esta é a localização para a qual os utilizadores navegam automaticamente durante o processo de autenticação. Os utilizadores são obrigados a comprovar a sua identidade. Para obter mais informações, veja [What is application access and single sign-on with Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis) (O que é o acesso à aplicação e o início de sessão único com o Azure Active Directory?)

7. Clique em **Criar** na parte inferior do painel **Criar**.

    >[!NOTE] 
    > Copie o **ID da Aplicação** do painel **Aplicação registada** para utilizar mais tarde.

## <a name="create-a-key"></a>Criar uma chave

Nesta secção, o Azure AD gera um valor de chave para a sua aplicação.

1. No painel **Registos das aplicações**, selecione a sua aplicação criada recentemente para apresentar o painel da aplicação.
2. Selecione **Definições** junto à parte superior do painel para apresentar o painel **Definições**.
3. Selecione **Chaves** no painel **Definições**.
4. Adicione a chave **Descrição**, uma duração **Expira** e um **Valor** para a chave.
5. Clique em **Guardar** para guardar e atualizar as chaves da aplicação.
6. Tem de copiar o valor da chave gerado (codificação base64).

    >[!NOTE] 
    > O valor da chave desaparece depois de sair do painel **chaves**. Não pode obter a chave a partir deste painel mais tarde. Copie-a para utilizar mais tarde.

## <a name="grant-application-permissions"></a>Conceder permissões da aplicação

Nesta secção, pode conceder permissões às aplicações.

1. Selecione **Permissões obrigatórias** no painel **Definições**.
2. Clique em **Adicionar**.
3. Selecione **Adicionar uma API** para apresentar o painel **Selecionar uma API**.
4. Selecione **API do Microsoft Intune (MicrosoftIntuneAPI)** e, em seguida, clique em **Selecionar** no painel **Selecionar uma API**. O passo **Selecionar permissões** está selecionado e o painel **Ativar Acesso** é apresentado.
5. Escolha a opção **Obter informações do armazém de dados do Microsoft Intune** da secção **Permissões da Aplicação**.
6. Clique em **Selecionar** no painel **Ativar Acesso**.
7. Clique em **Concluído** no painel **Adicionar acesso à API**.
8. Clique em **Conceder Permissões** no painel **Permissões obrigatórias** e clique em **Sim** quando lhe for pedido que atualize as permissões existentes que esta aplicação já tem.

## <a name="generate-token"></a>Gerar token

Com o Visual Studio, crie um projeto de Aplicação de Consola (.NET Framework) que suporte o .NET Framework e utilize C# como a linguagem de programação.

1. Selecione **Ficheiro** > **Novo** > **Projeto** para apresentar a caixa de diálogo **Novo Projeto**.
2. No lado esquerdo, selecione **Visual c#** para apresentar todos os projetos de .NET Framework.
3. Selecione **Aplicação de Consola (.Net Framework)** , adicione um nome da aplicação e, em seguida, clique em **OK** para criar a aplicação.
4. No **Explorador de Soluções**, selecione **Program.cs** para apresentar o código.
5. Em Gerenciador de Soluções, adicione uma referência ao assembly `System.Configuration`.
6. No menu de pop-up, selecione **Adicionar** > **Novo item**. É apresentada a caixa de diálogo **Adicionar Novo Item**.
7. No lado esquerdo, em **Visual C#** , selecione **Código**.
8. Selecione **Classe**, altere o nome da classe para *IntuneDataWarehouseClass.cs* e clique em **Adicionar**.
9. Adicione o seguinte código dentro do método <code>Main</code>:

    ``` csharp
         var applicationId = ConfigurationManager.AppSettings["appId"].ToString();
         SecureString applicationSecret = ConvertToSecureStr(ConfigurationManager.AppSettings["appKey"].ToString()); // Load as SecureString from configuration file or secret store (i.e. Azure KeyVault)
         var tenantDomain = ConfigurationManager.AppSettings["tenantDomain"].ToString();
         var adalContext = new AuthenticationContext($"https://login.windows.net/" + tenantDomain + "/oauth2/token");
    
         AuthenticationResult authResult = adalContext.AcquireTokenAsync(
             resource: "https://api.manage.microsoft.com/",
             clientCredential: new ClientCredential(
                 applicationId,
                 new SecureClientSecret(applicationSecret))).Result;
    ``` 

10. Adicione mais espaços de nomes ao adicionar o seguinte código à parte superior do ficheiro de código:

    ``` csharp
     using System.Security;
     using Microsoft.IdentityModel.Clients.ActiveDirectory;
     using System.Configuration;
    ``` 

11. Depois do método <code>Main</code>, adicione o seguinte método privado para processar e converter a chave da aplicação:

    ``` csharp
    private static SecureString ConvertToSecureStr(string appkey)
    {
        if (appkey == null)
            throw new ArgumentNullException("AppKey must not be null.");
    
        var secureAppKey = new SecureString();
    
        foreach (char c in appkey)
            secureAppKey.AppendChar(c);
    
        secureAppKey.MakeReadOnly();
        return secureAppKey;
    }
    ```

12. No **Explorador de Soluções**, clique com o botão direito do rato em **Referências** e, em seguida, selecione **Gerir Pacotes NuGet**.
13. Pesquise *Microsoft.IdentityModel.Clients.ActiveDirectory* e instale o pacote Microsoft NuGet relacionado.
14. No **Explorador de Soluções**, selecione e abra o ficheiro *App. config*.
15. Adicione a secção <code>appSettings</code> para que o xml apareça da seguinte forma:

    ``` xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup> 
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <appSettings>
          <add key="appId" value="App ID created from 'Create a Web App' procedure"/>
          <add key="appKey" value="Key created from 'Create a key' procedure" />
          <add key="tenantDomain" value="contoso.onmicrosoft.com"/>
        </appSettings>
    </configuration>
    ``` 

16. Atualize os valores <code>appId</code>, <code>appKey</code> e <code>tenantDomain</code> para corresponder ao valores exclusivos relacionados com a aplicação.
17. Crie a sua aplicação.

    >[!NOTE] 
    > Para ver código de implementação adicional, veja [Exemplo de código do Armazém de Dados do Intune](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/CSharp ).

## <a name="next-steps"></a>Próximos Passos
Saiba mais sobre o Azure Key Vault ao rever [O que é o Azure Key Vault?](https://docs.microsoft.com/azure/key-vault/key-vault-whatis)

