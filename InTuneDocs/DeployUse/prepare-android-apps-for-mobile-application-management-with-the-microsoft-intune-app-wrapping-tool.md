---
title: "Encapsular aplicações Android com a Ferramenta de Encapsulamento de Aplicações | Microsoft Intune"
description: "Utilize as informações neste tópico para saber como pode encapsular as suas aplicações Android sem modificar os próprios códigos. Prepare as aplicações para que possa aplicar políticas de gestão de aplicações móveis."
keywords: 
author: karthikaraman
manager: arob98
ms.date: 07/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: matgates
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2038ed6219a94dc4285891d71ce00fd51310f3e3
ms.openlocfilehash: 15d0877f799c89e2a8af65c416c0e914f898641f


---

# Preparar as aplicações Android para gestão de aplicações móveis com a Ferramenta de Encapsulamento de Aplicações do Intune
Utilize a **Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para Android** para modificar o comportamento das suas aplicações Android internas, de forma a que possa configurar as funcionalidades das aplicações sem modificar os códigos.

A ferramenta é uma aplicação de linha de comandos do Windows executada no PowerShell, que cria um "wrapper" em torno da aplicação. Assim que a aplicação é processada, pode alterar as funcionalidades da mesma ao utilizar [políticas de gestão de aplicações móveis](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) configuradas por si.

Se a sua aplicação utilizar a Biblioteca de Autenticação do Azure Active Directory (ADAL), tem de concluir os passos em [Como moldar aplicações que utilizam a Biblioteca do Azure Active Directory](#how-to-wrap-apps-that-use-the-azure-active-directory-library) antes de moldar a sua aplicação. Caso não tenha a certeza se a sua aplicação utiliza esta biblioteca, contacte o programador da aplicação.

Antes de executar a ferramenta, consulte as [Considerações de segurança para executar a ferramenta de encapsulamento de aplicações](#security-considerations-for-running-the-app-wrapping-tool). Para transferir a ferramenta, veja [Microsoft Intune App Wrapping Tool for Android (Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para Android)](https://www.microsoft.com/download/details.aspx?id=47267).

## Passo 1: cumprir os pré-requisitos de utilização da ferramenta de encapsulamento de aplicações

-   Tem de executar a ferramenta de encapsulamento de aplicações num computador Windows com o Windows 7 ou posterior.

-   A aplicação de entrada tem de ser um pacote de aplicação Android válido com a extensão **.apk** e:

    -   Não pode ser encriptada

    -   Não pode ter sido encapsulada anteriormente pela ferramenta de encapsulamento de aplicações

    -   Tem de ter sido escrita para Android 4.0 ou posterior

-   A aplicação tem de ter sido programada pela sua empresa ou para a mesma. Não pode utilizar esta ferramenta para processar aplicações transferidas a partir da Google Play Store.

-   Para executar a ferramenta de encapsulamento de aplicações, tem de instalar a versão mais recente do [Ambiente de Tempo de Execução Java](http://java.com/download/) e, em seguida, certificar-se de que a variável de caminho Java foi definida como **C:\ProgramData\Oracle\Java\javapath** nas variáveis do seu ambiente do Windows. Para obter mais ajuda, consulte a [documentação do Java](http://java.com/download/help/).

    > [!NOTE]
    > Nalguns casos, a versão de 32 bits do Java pode originar problemas de memória. Recomendamos que instale a versão de 64 bits.

## Passo 2: instalar a ferramenta de encapsulamento de aplicações

1.  No Centro de Transferências da Microsoft, transfira e abra o ficheiro de instalação da ferramenta de encapsulamento de aplicações num computador Windows.

2.  Aceite o contrato de licença e conclua a instalação.

Não se esqueça da pasta na qual instalou a ferramenta. A localização predefinida é: **C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**.

## Passo 3: executar a ferramenta de encapsulamento de aplicações

1.  No computador Windows onde instalou a ferramenta de encapsulamento de aplicações, abra uma janela do PowerShell no modo de administrador.

2.  Na pasta onde instalou a ferramenta, importe o módulo do PowerShell da ferramenta de encapsulamento de aplicações:

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  Execute a ferramenta através do comando **invoke-AppWrappingTool** juntamente com os seguintes parâmetros. Os parâmetros que estão marcados como "opcional" destinam-se às aplicações que utilizam a Biblioteca do Active Directory do Azure (ADAL). Para obter mais informações, veja [Como encapsular aplicações que utilizam a Biblioteca do Azure Active Directory](#how-to-wrap-apps-that-use-the-azure-active-directory-library).

|Parâmetro|Mais informações|Exemplos|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|Caminho da aplicação Android de origem (.apk).| |
|**-OutputPath**&lt;String&gt;|Caminho para a aplicação Android de "saída". Se este for o mesmo caminho de diretório como o InputPath, o empacotamento irá falhar.| |
|**-KeyStorePath**&lt;String&gt;|Caminho para o ficheiro de keystore que contém o par de chaves pública/privada para assinatura.| |
|**-KeyStorePassword**&lt;SecureString&gt;|Palavra-passe utilizada para desencriptar o keystore. O Android requer que todos os pacotes de aplicações (. apk) estejam assinados. Utilize o Java Key Tool para gerar KeyStorePassword, conforme mostrado no exemplo. Leia mais sobre o [KeyStore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html).|keytool.exe -genkey -v -keystore keystorefile -alias ks -keyalg RSA -keysize 2048 -validity 50000 |
|**-KeyAlias**&lt;String&gt;|Nome da chave a ser utilizada para assinatura.| |
|**-KeyPassword**&lt;SecureString&gt;|Palavra-passe utilizada para desencriptar a chave privada que vai ser utilizada para assinatura.| |
|**-SigAlg**&lt;SecureString&gt;|Nome do algoritmo de assinatura a ser utilizado na assinatura. O algoritmo tem de ser compatível com a chave privada.|Exemplos: SHA256withRSA, SHA1withRSA, MD5withRSA|
|**-ClientID**&lt;GUID&gt;|ID de Cliente do Azure Active Directory da aplicação de entrada (opcional).| |
|**-AuthorityURI**&lt;Uri&gt;|URI de Autoridade do Azure Active Directory da aplicação de entrada (opcional).| |
|**-SkipBroker**&lt;Boolean&gt;|Indica se a aplicação de entrada suporta o início de sessão único mediado em todos os dispositivos (opcional). |**Verdadeiro** - a aplicação de entrada não suporta o início de sessão único mediado em todos os dispositivos. Utilize o parâmetro NonBrokerRedirectURI. **Falso** - a aplicação de entrada suporta o início de sessão único mediado em todos os dispositivos|
|**-NonBrokerRedirectURI**&lt;URI&gt;|URI de Redirecionamento do Azure Active Directory a utilizar se o SkipBroker for verdadeiro (opcional).|  |


**&lt;CommonParameters&gt;**
    (opcional – suporta parâmetros comuns do PowerShell, como, por exemplo, verboso, depuração, etc.)

- Para obter uma lista de parâmetros comuns, consulte o [Centro de Scripts da Microsoft](https://technet.microsoft.com/library/hh847884.aspx).

- Para ver a ajuda para a ferramenta, introduza o comando:

    ```
    Help Invoke-AppWrappingTool
    ```
- Para saber mais sobre a integração do Azure Active Directory (AAD), veja [Como encapsular aplicações que utilizam a biblioteca do Azure Active Directory](#how-to-wrap-apps-that-use-the-azure-active-directory-library).

**Exemplo:**


    Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
    invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app.wrapped\HelloWorld_wrapped2.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\keystorefile" -keyAlias ks -SigAlg SHA1withRSA -Verbose

Ser-lhe-ão solicitadas a **KeyStorePassword** e a **KeyPassword**.

A aplicação encapsulada é gerada e guardada juntamente com um ficheiro de registo no caminho de saída que tiver especificado.

## Considerações de segurança para executar a ferramenta de encapsulamento de aplicações
Para impedir potenciais ataques de spoofing, divulgação de informações e ataques de elevação de privilégios:

-   Certifique-se de que a aplicação de linha de negócio de entrada, a aplicação de saída e a Java KeyStore se encontram no computador onde é executada a ferramenta de encapsulamento de aplicações.

-   Importe a aplicação de saída para a consola do Intune no computador onde a ferramenta está a ser executada. Veja [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html) para obter mais informações sobre o Java keytool.

-   Se a aplicação de saída e a ferramenta estiverem num caminho UNC (Universal Naming Convention), mas não estiver a executar a ferramenta e os ficheiros de entrada no mesmo computador, configure o ambiente de forma a torná-lo seguro com a [Segurança IPsec](http://en.wikipedia.org/wiki/IPsec) ou a [assinatura do protocolo SMB (Server Message Block)](https://support.microsoft.com/en-us/kb/887429).

-   Certifique-se de que a aplicação vem de uma origem fidedigna, especialmente se estiver a utilizar o Azure Active Directory (AAD), o qual pode permitir que a aplicação aceda ao token do AAD durante o tempo de execução.

-   Proteja o diretório de saída que contém a aplicação encapsulada. Considere utilizar um diretório de nível de utilizador para a saída.

## Como moldar aplicações que utilizam a Biblioteca do Azure Active Directory
Se a sua aplicação utilizar a Biblioteca de Autenticação do Active Directory do Azure (ADAL), tem de concluir estes passos antes de moldar a sua aplicação.

### Passo 1: certificar-se de que cumpre os requisitos da ADAL
Para aplicações que utilizem a ADAL, tem de aplicar-se o seguinte:

-   A aplicação tem de incorporar uma versão da ADAL superior ou igual a 1.0.2.

-   O programador tem de conceder à aplicação o acesso ao recurso Gestão de Aplicações Móveis do Intune, conforme descrito em [Passo 3: configurar o acesso à gestão de aplicações móveis no AAD](#step-3-configure-access-to-mobile-app-management-in-aad)

### Passo 2: consultar os identificadores que tem de obter ao registar a aplicação
No próximo passo, irá utilizar o portal de gestão do Azure para registar as suas aplicações (que  utilizam a ADAL com o Azure Active Directory (AAD)) para obter os identificadores exclusivos listados na tabela seguinte. Em seguida, dê os identificadores ao programador quando integrar a ADAL com a aplicação.

|Identificador|Mais informações|Valor predefinido|
|--------------|--------------------|-----------------|
|**ID de Cliente**|Um identificador GUID exclusivo que é gerado para a aplicação após estar registado com o AAD.<br /><br />Se souber o ID de Cliente da aplicação, especifique esse valor. Caso contrário, utilize o valor predefinido.|6c7e8096-f593-4d72-807f-a5f86dcc9c77|
|**URI de Autoridade**|O valor do Uniform Resource Identifier (URI) da autoridade para objetos do AAD (por exemplo, os utilizadores e os grupos).<br /><br />O parâmetro AuthorityURI é opcional para a ferramenta de encapsulamento de aplicações. O URI predefinido é utilizado se não utilizar o parâmetro.||
|**SkipBroker**|Valor que indica se o portal da empresa será utilizado como um mediador.<br /><br />**Verdadeiro** – o portal da empresa não será utilizado para autenticação da ADAL.<br /><br />**Falso** – o portal da empresa será utilizado para autenticação da ADAL. O portal da empresa está a utilizar o utilizador inscrito para fins de Início de Sessão Único.||
|**URI de Redirecionamento Não-Mediador**|URI de Início de sessão a ser utilizado quando a ADAL não utiliza a aplicação de mediador (portal da empresa do Intune).|urn:ietf:wg:oauth:2.0:oob|
|**ID de Recurso**|Apontador para os recursos AAD da aplicação.||

### Passo 3: configurar o acesso à gestão de aplicações móveis no AAD
Antes de poder utilizar os valores de registo do AAD de uma aplicação na ferramenta de encapsulamento de aplicações, o programador da aplicação tem de conceder à aplicação o acesso ao recurso da Gestão de Aplicações Móveis do Intune, seguindo estes passos:

1.  Iniciar sessão numa conta existente do AAD no portal de gestão do Azure.

2.  Escolha **registo de aplicação LOB existente**.

3.  Na secção de **configuração** , selecionar **Configurar o Acesso a APIs Web noutras aplicações**.

4.  Na primeira lista pendente, na secção **Permissões para outras aplicações**, escolha **Gestão de Aplicações Móveis do Intune**.

Agora pode utilizar o ID de Cliente da aplicação na ferramenta de encapsulamento de aplicações. Pode encontrar o ID de Cliente no portal de gestão do Azure Active Directory, conforme descrito na tabela no [Passo 2: consultar os identificadores que tem de obter ao registar a aplicação](#step-2-review-the-identifiers-you-need-to-get-when-you-register-the-app).

### Passo 4: utilizar os valores de identificador do AAD na ferramenta de encapsulamento de aplicações
Utilizando os valores de identificador que recebeu do processo de registo, introduza os valores como propriedades da linha de comando na ferramenta de encapsulamento de aplicações. Tem de especificar todos os valores na tabela para que os utilizadores finais autentiquem a aplicação com êxito. Serão utilizados valores predefinidos se não especificar um valor.

|Identificador|Parâmetro|
|--------------|-------------|
|ID de Cliente|ClientID|
|URI de Autoridade|Autoridade-URI|
|SkipBroker|SkipBroker|
|URI de Redirecionamento Não-Mediador|NonBrokerRedirectURI|
|ID de Recurso|ResourceID|
Tenha em consideração os seguintes pontos ao encapsular a sua aplicação:

-   Para verificar se a autenticação foi bem-sucedida, o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] obtém o token do AAD que está associado ao ID de recurso de MAM. No entanto, o token não é utilizado em qualquer chamada que iria verificar a validade do token. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] lê apenas o nome do principal de utilizador (UPN) do utilizador com sessão iniciada para determinar o acesso da aplicação. O token do AAD não é utilizado para outras chamadas de serviço.

-   São impedidos pedidos de início de sessão duplos se fornecer o ID de Cliente e URI de Autoridade da aplicação cliente. Tem de registar o ID de Cliente para poder aceder ao ID de recurso do MAM do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] publicado no Dashboard do AAD. Se não registar o ID de Cliente, os utilizadores obtêm uma falha de início de sessão ao executarem a aplicação.


### Consulte também
- [Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Utilizar o SDK para ativar aplicações para gestão de aplicações móveis](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Jul16_HO4-->


