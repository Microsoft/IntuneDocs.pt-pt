---
title: Obter dados a partir da API do Armazém de Dados com um cliente REST
titlesuffix: Microsoft Intune
description: Este tópico descreve como recuperar dados do Microsoft Intune armazém de dados com uma API RESTful.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/10/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: D6D15039-4036-446C-A58F-A5E18175720A
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: f587fdf7c1690dbb0a31388a9c70b780179e541e
ms.sourcegitcommit: 513c59a23ca5dfa80a3ba6fc84068503a4158757
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/11/2019
ms.locfileid: "54210878"
---
# <a name="get-data-from-the-intune-data-warehouse-api-with-a-rest-client"></a>Obter dados a partir da API do Armazém de Dados do Intune com um cliente REST

Pode aceder ao modelo de dados do Armazém de Dados do Intune através de ponto finais RESTful. Para obter acesso aos seus dados, o seu cliente tem de conceder autorização com o Microsoft Azure Active Directory (Azure AD) com OAuth 2.0. Para ativar o acesso, configure uma aplicação nativa no Azure e conceda permissões à API do Microsoft Intune. O seu cliente local recebe a autorização e, em seguida, este pode comunicar com os pontos finais do Armazém de Dados através da aplicação nativa.

Para configurar um cliente para obter dados da API do Armazém de Dados, é necessário que:

1. Crie uma aplicação cliente como aplicação nativa no Azure
3. Conceda à aplicação cliente acesso à API do Microsoft Intune
3. Crie um cliente REST local para obter os dados

Utilize os passos seguintes para saber como autorizar e aceder à API com um cliente REST. Primeiro, verá como utilizar um cliente REST genérico com o Postman. O Postman é uma ferramenta frequentemente utilizada para resolver problemas e desenvolver clientes REST que funcionem com APIs. Para obter mais informações sobre o Postman, veja o site do [Postman](https://www.getpostman.com). Em seguida, pode ver um exemplo de código C#. Este fornece um exemplo de autorização de um cliente e obtenção de dados a partir da API.

## <a name="create-a-client-app-as-a-native-app-in-azure"></a>Crie uma aplicação cliente como aplicação nativa no Azure

Crie uma aplicação nativa no Azure. Esta aplicação nativa é a aplicação cliente. O cliente em execução no seu computador faz referência à API do Armazém de Dados do Intune quando o cliente local pede as credenciais.

1. Inicie sessão no portal do Azure do seu inquilino. Selecione **Azure Active Directory** > **Registos das Aplicações** para abrir o painel **Registos das aplicações**.
2. Selecione **Novo registo de aplicação**.
3. Escreva os detalhes da aplicação.
    1.  Escreva um nome amigável, como Cliente do Armazém de Dados do Intune, em **Nome**.
    2.  Selecione **Nativa** no **Tipo de aplicação**.
    3.  Escreva um URL em **URL de início de sessão**. O URL de início de sessão dependerá do cenário específico. No entanto, se pensa utilizar o Postman, escreva `https://www.getpostman.com/oauth2/callback`. Irá utilizar a chamada de retorno do passo de autenticação de cliente ao autenticar no Azure AD.
4.  Selecione **Criar**.

     ![Aplicação de cliente do armazém de dados do Intune](./media/reports-get_rest_data_client_overview.png)

5. Tenha em atenção o **ID da aplicação** desta aplicação. Irá utilizar o ID na próxima secção.

## <a name="grant-the-client-app-access-to-the-microsoft-intune-api"></a>Conceda à aplicação cliente acesso à API do Microsoft Intune

Agora tem uma aplicação definida no Azure. Conceda acesso à API do Microsoft Intune a partir da aplicação nativa.

1.  Selecione a aplicação nativa. Atribuiu um nome à aplicação, como **Cliente do Armazém de Dados do Intune**.
2.  Selecione **Permissões obrigatórias** a partir do painel **Definições**
3.  Selecione **Adicionar** no painel **Permissões obrigatórias**.
4.  Selecione **Selecionar uma API**.
5.  Procure o nome da aplicação Web. É denominada **API do Microsoft Intune**.
6.  Selecione a aplicação na lista.
7.  Selecione **Selecionar**.
8.  Selecione a caixa **Permissões Delegadas** para adicionar a opção **Obter informações do armazém de dados do Microsoft Intune**.

    ![Ativar o acesso – API do Microsoft Intune](./media/reports-get_rest_data_client_access.png)

9.  Selecione **Selecionar**.
10.  Selecione **Done** (Concluído).
11.  Opcionalmente, selecione **Conceder Permissões** no painel Permissões obrigatórias. Esta ação irá conceder acesso a todas as contas no diretório atual. Esta ação irá impedir a apresentação da caixa de diálogo de consentimento para cada utilizador no inquilino. Para obter mais informações, veja [Integrating applications with Azure Active Directory (Integrar aplicações com o Azure Active Directory)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications).
12.  Selecione **Sim**.

## <a name="get-data-from-the-microsoft-intune-api-with-postman"></a>Obter dados a partir da API do Microsoft Intune com o Postman

Pode trabalhar com a API do Armazém de Dados do Intune com um cliente REST genérico, como o Postman. O Postman pode fornecer informações sobre as funcionalidades da API, o modelo de dados OData subjacente e a resolução de problemas da sua ligação aos recursos da API. Nesta secção, pode encontrar informações sobre como gerar um token Auth2.0 para o seu cliente local. O cliente precisará do token para autenticar com o Azure AD e aceder aos recursos da API.

### <a name="information-you-will-need-to-make-the-call"></a>Informações de que precisa para efetuar a chamada

Precisa das seguintes informações para efetuar uma chamada REST através do Postman:

| Atributo        | Descrição                                                                                                                                                                          | Exemplo                                                                                       |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| URL de chamada de retorno     | Defina este como o URL de chamada de retorno na sua página de definições da aplicação.                                                                                                                              | https://www.getpostman.com/oauth2/callback                                                    |
| Nome do Token       | Uma cadeia utilizada para transferir as credenciais para a aplicação Azure. O processo gera o seu token para poder efetuar uma chamada para a API do Armazém de Dados.                          | Portador                                                                                        |
| URL Auth         | Este é o URL utilizado para autenticar. | https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com/ |
| URL do Token de Acesso | Este é o URL utilizado para conceder o token.                                                                                                                                              | https://login.microsoftonline.com/common/oauth2/token |
| ID de Cliente        | Você criou e anotou isto quando criou a aplicação nativa no Azure.                                                                                               | 4184c61a-e324-4f51-83d7-022b6a81b991                                                          |
| Âmbito (Opcional) | Em Branco                                                                                                                                                                               | Pode deixar o campo em branco.                                                                     |
| Tipo de Concessão       | O token é um código de autorização.                                                                                                                                                  | Código de autorização                                                                            |

### <a name="odata-endpoint"></a>Ponto final de OData

Também precisa do ponto final. Para obter o ponto final do Armazém de Dados, precisará do URL de feed personalizado. Pode obter o ponto final de OData no painel do Armazém de Dados.

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Selecione **Definir o Armazém de Dados do Intune** em **Outras tarefas**.
4. Copie o URL de feed personalizado em **Utilize os serviços de relatórios de terceiros**. Deverá ter o seguinte aspeto: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`

O ponto final segue o seguinte formato: `https://fef.{yourtenant}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity}?api-version={verson-number}`.

Por exemplo, a entidade **Datas** tem o seguinte aspeto: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`

Para obter mais informações, veja [Ponto final da API do Armazém de Dados do Intune](reports-api-url.md).

### <a name="make-the-rest-call"></a>Efetuar a chamada REST

Para obter um novo token de acesso do Postman, tem de adicionar o URL de autorização do Azure AD, adicionar o seu ID de Cliente e o Segredo do Cliente. O Postman irá carregar a página de autorização onde escrever as suas credenciais.

#### <a name="add-the-information-used-to-request-the-token"></a>Adicionar as informações utilizadas para pedir o token

1.  Transfira o Postman, se ainda não o tiver instalado. Para transferir o Postman, veja [www.getpostman](https://www.getpostman.com).
2.  Abra o Postman. Selecione **GET** da operação HTTP.
3.  Cole o URL do ponto final no endereço. Deverá ter o seguinte aspeto:  

    `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`
4.  Selecione o separador **Authorization (Autorização)** e **OAuth 2.0** a partir da lista **Type (Tipo)**.
5.  Selecione **Obter Novo Token de Acesso**.
6.  Certifique-se de que já adicionou o URL de Chamada de Retorno para a sua aplicação no Azure. O URL de Chamada de Retorno é `https://www.getpostman.com/oauth2/callback`.
7.  Escreva Portador no **Nome do Token**.
8.  Adicione o **URL Auth**. Deverá ter o seguinte aspeto:  

    `https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com/`
9.  Adicione o **URL do Token de Acesso**. Deverá ter o seguinte aspeto:  

     `https://login.microsoftonline.com/common/oauth2/token`

10. Adicione o **ID de Cliente** da aplicação nativa que criou no Azure e denominada `Intune Data Warehouse Client`. Deverá ter o seguinte aspeto:  

     `88C8527B-59CB-4679-A9C8-324941748BB4`

11. Selecione **Authorization Code (Código de Autorização)** e Request access token locally (Pedir o token de acesso localmente).

12. Selecione **Pedir Token**.

    ![Informações para o token de acesso](./media/reports-postman_getnewtoken.png)

13. Escreva as suas credenciais na página de autorização do Active AD. A lista de tokens no Postman agora contém o token denominado `Bearer`.
14. Selecione **Utilizar Token**. A lista de cabeçalhos inclui o novo valor de chave de Autorização e o valor `Bearer <your-authorization-token>`.

#### <a name="send-the-call-to-the-endpoint-using-postman"></a>Enviar a chamada para o ponto final através do Postman

1.  Selecione **Enviar**.
2.  Os dados devolvidos são apresentados no corpo de resposta do Postman.

    ![Estado do cliente de postman é igual a 200 OK](./media/reports-postman_200OK.png)

## <a name="create-a-rest-client-c-to-get-data-from-the-intune-data-warehouse"></a>Criar um cliente REST (C#) para obter dados do Armazém de Dados do Intune

O seguinte exemplo inclui um cliente REST simples. O código utiliza a classe **httpClient** da biblioteca .Net. Quando o cliente obtém credenciais para o Azure AD, constrói uma chamada REST GET para obter a entidade Datas da API do Armazém de Dados.

> [!Note]  
> Pode aceder ao seguinte [exemplo de código no GitHub](https://github.com/Microsoft/Intune-Data-Warehouse/blob/master/Samples/CSharp/Program.cs). Consulte o repositório do GitHub para obter as alterações e atualizações mais recentes ao exemplo.

1. Abra o **Microsoft Visual Studio**.
2. Selecione **Ficheiro** > **Novo Projeto**. Expanda o **Visual C#** e selecione **Aplicação de Consola (.Net Framework)**.
3. Atribua o nome ` IntuneDataWarehouseSamples` ao projeto, navegue até à localização onde pretende guardar o projeto e, em seguida, selecione **OK**.
4. Clique com o botão direito do rato no nome da solução no Explorador de Soluções e, em seguida, selecione **Manage NuGet Packages for Solution (Gerir Pacotes NuGet para Solução)**. Selecione **Procurar** e, em seguida, escreva `Microsoft.IdentityModel.Clients.ActiveDirectory` na caixa de pesquisa.
5. Escolha o pacote, selecione o projeto **IntuneDataWarehouseSamples** em Gerir Pacotes da Sua Solução e, em seguida, selecione **Instalar**.
6. Selecione **Aceito** para aceitar a licença do pacote NuGet.
7. Abra o `Program.cs` a partir do Explorador de Soluções.

    ![Progam.cs e o Explorador de soluções no Visual Studio](./media/reports-get_rest_data_in.png)

8. Substitua o código no Program.cs pelo seguinte:  
   ```csharp
   namespace IntuneDataWarehouseSamples
   {
   using System;
   using System.Net.Http;
   using System.Net.Http.Headers;
   using Microsoft.IdentityModel.Clients.ActiveDirectory;

   class Program
   {
    static void Main(string[] args)
   {
   /**
   * TODO: Replace the below values with your own.
   * emailAddress - The email address of the user that you will authenticate as.
   *
   * password  - The password for the above email address.
   *    This is inline only for simplicity in this sample. We do not
   *    recommend storing passwords in plaintext.
   *
   * applicationId - The application ID of the native app that was created in AAD.
   *
   * warehouseUrl   - The data warehouse URL for your tenant. This can be found in
   *      the Azure portal.
   *
   * collectionName - The name of the warehouse entity collection you would like to
   *      access.
   */
   var emailAddress = "intuneadmin@yourcompany.com";
   var password = "password_of(intuneadmin@yourcompany.com)";
   var applicationId = "<Application ID>";
   var warehouseUrl = "https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta";
   var collectionName = "dates";

   var adalContext = new AuthenticationContext("https://login.windows.net/common/oauth2/token");
   AuthenticationResult authResult = adalContext.AcquireTokenAsync(
   resource: "https://api.manage.microsoft.com/",
   clientId: applicationId,
   userCredential: new UserPasswordCredential(emailAddress, password)).Result;

   var httpClient = new HttpClient();
   httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);

   var uriBuilder = new UriBuilder(warehouseUrl);
   uriBuilder.Path += "/" + collectionName;

   HttpResponseMessage response = httpClient.GetAsync(uriBuilder.Uri).Result;

   Console.Write(response.Content.ReadAsStringAsync().Result);
   Console.ReadKey();
   }
   }
   ```

9. Atualize o `TODO` no exemplo de código.
10. Prima **Ctrl+F5** para criar e executar o cliente Intune.DataWarehouseAPIClient em Modo de Depuração.

    ![A entidade Data foi obtida no formato JSON.](./media/reports-get_rest_data_output.png)

11. Reveja o resultado da consola. O resultado inclui dados num formato JSON retirados da entidade **Datas** no seu inquilino do Intune.

## <a name="next-steps"></a>Passos Seguintes

Pode encontrar detalhes sobre a autorização, a estrutura do URL da API e os pontos finais OData em [Use the Intune Data Warehouse API (Utilizar a API do Armazém de Dados do Intune)](reports-api-url.md).

Também pode consultar o Modelo de Dados do Armazém de Dados do Intune para consultar as entidades de dados incluídas na API. Para obter mais informações, veja [Modelo de Dados da API do Armazém de Dados do Intune](reports-ref-data-model.md)
