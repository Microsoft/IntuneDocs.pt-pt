---
title: "Guia para Programadores do SDK da Aplicação do Microsoft Intune para iOS | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 975708b5204ab83108a9174083bb87dfeb04a063
ms.openlocfilehash: 52ad28686fa279a7ec251d073283c3554d1c81fc


---

# Guia para Programadores do SDK da Aplicação Microsoft Intune para iOS

> [!NOTE]
> Pode ler primeiro o [Guia de Introdução ao SDK da Aplicação do Intune](intune-app-sdk-get-started.md), que explica como preparar a integração em cada plataforma suportada.* 

O SDK da Aplicação Microsoft Intune para iOS permite incorporar a Gestão de Aplicações Móveis do Intune (MAM) na sua aplicação iOS. Uma aplicação preparada para MAM está integrada no SDK da Aplicação do Intune e permite aos administradores de TI implementar políticas na sua aplicação móvel quando a aplicação é gerida ativamente pelo Intune.


# O que está no SDK 

O SDK da Aplicação do Intune para iOS inclui uma biblioteca estática, ficheiros de recursos, cabeçalhos de API, um plist de definições de Depuração e uma ferramenta de configurador. As aplicações móveis podem simplesmente incluir os ficheiros de recursos e ligar estaticamente às bibliotecas para a maioria das imposições de políticas. As funcionalidades avançadas de MAM do Intune são impostas através de APIs.

Este guia irá abranger a utilização dos seguintes componentes do SDK da Aplicação do Intune para iOS:

* **libIntuneMAM.a**: biblioteca estática do SDK da Aplicação do Intune. Se a aplicação não utilizar extensões, ligue esta biblioteca ao seu projeto de forma a ativar a aplicação para a gestão de aplicações móveis do Intune. Pode encontrar instruções na secção "Criar uma aplicação com o SDK da Aplicação do Intune".

* **IntuneMAM.framework**: estrutura do SDK da Aplicação do Intune. Ligue esta estrutura ao seu projeto de forma a ativar a aplicação para a gestão de aplicações móveis do Intune. Utilize a estrutura em vez da biblioteca estática, se a sua aplicação utilizar extensões, para que o projeto não crie múltiplas cópias da biblioteca estática.

* **IntuneMAMResources.bundle**: um pacote de recursos que contém os recursos dos quais o SDK depende. 

* **Cabeçalhos**: expõe as APIs do SDK da Aplicação do Intune. Se utilizar uma API, terá de incluir o ficheiro de cabeçalho que contém a API. Os seguintes ficheiros de cabeçalho incluem as chamadas de função da API necessárias para ativar a funcionalidade do SDK da Aplicação do Intune. 
    
    * IntuneMAMAsyncResult.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMLogger.h 


# Como funciona o SDK da Aplicação do Intune

O objetivo do SDK da Aplicação do Intune para iOS consiste em adicionar capacidades de gestão para aplicações iOS com alterações de código mínimas. Quanto menos alterações de código houver, menos tempo há para comercializar, mas a consistência e a estabilidade da sua aplicação móvel ficam garantidas. 

A aplicação tem de ser ligada à biblioteca estática e incluir o pacote de recursos. O ficheiro MAMDebugSettings.plist é opcional e pode ser incluído no pacote para simular políticas de MAM a serem aplicadas à aplicação sem necessidade de implementar a aplicação através do Microsoft Intune. Além disso, nas compilações de depuração, as políticas no ficheiro MAMDebugSettings.plist podem ser aplicadas transferindo o ficheiro para o diretório Documentos da aplicação através da partilha de ficheiros do iTunes.

# Criar o SDK na sua aplicação móvel 

Conclua os passos abaixo para ativar o SDK da Aplicação do Intune:

1. **Opção 1**: ligue à biblioteca `libIntuneMAM.a` ao fazer o seguinte:

    Arraste e largue a biblioteca `libIntuneMAM.a` para a lista "Linked Frameworks and Libraries" (Estruturas e Bibliotecas Ligadas) do destino do projeto.
    ![SDK da Aplicação do Intune para iOS - estruturas e bibliotecas ligadas](../media/intune-app-sdk-ios-linked-frameworks-and-libraries.png) 

    **Nota**: se planeia lançar a sua aplicação na App Store, utilize a versão do `libIntuneMAM.a` criada para lançamento e não a versão de depuração. A versão de lançamento estará na pasta "release". A versão de depuração tem uma saída verbosa ideal para resolver problemas com o SDK da Aplicação do Intune.
    
    **Opção 2**: ligue o `IntuneMAM.framework` ao seu projeto. Arraste e largue `IntuneMAM.framework` para a lista "Linked Frameworks and Libraries" (Estruturas e Bibliotecas Ligadas) do destino do projeto.
    
    **Nota**: se utilizar a estrutura, terá de retirar manualmente as arquiteturas do simulador da estrutura universal antes de submeter a sua aplicação à App Store. Consulte a secção intitulada "Submeter a sua aplicação à App Store".

2. Adicione as seguintes estruturas de iOS ao projeto:
    * MessageUI.framework
    * Security.framework
    * MobileCoreServices.framework
    * SystemConfiguration.framework
    * libsqlite3.dylib
    * libc++.dylib
    * ImageIO.framework
    * LocalAuthentication.framework
    * AudioToolbox.framework

    **Nota**: se a aplicação se destinar ao iOS 7, defina o atributo "Status" do `LocalAuthentication.framework` para "Optional". Se ''Status'' não estiver definido, a aplicação não será iniciada no iOS 7.

    **Nota**: Xcode 7 mudou as extensões `.dylib` para `.tbd`.

3. Adicione o pacote de recursos `IntuneMAMResources.bundle` ao projeto arrastando o pacote de recursos em "Copiar Recursos do Pacote" em "Fases de Criação".
![SDK da Aplicação do Intune para iOS - copiar recursos do pacote](../media/intune-app-sdk-ios-copy-bundle-resources.png)
 
4. Adicione `-force_load {PATH_TO_LIB}/libIntuneMAM.a` a qualquer um dos seguintes, substituindo `{PATH_TO_LIB}` pela localização do SDK da Aplicação do Intune:
    * definição de configuração da compilação `OTHER_LDFLAGS` do projeto 
    * "Outros Sinalizadores do Linker" da IU<br>

    **Nota**: para localizar `PATH_TO_LIB`, selecione o ficheiro `libIntuneMAM.a` e escolha ''Informações'' a partir do menu ''Ficheiro''. Copie e cole as informações "Onde" (o caminho) na secção "Geral" da janela ''Informações''.

5. Se a sua aplicação móvel define um Nib ou Guião Gráfico principal no respetivo ficheiro Info.plist, remova os campos dos ficheiros Guião Gráfico Principal ou Nib Principal. Adicione os valores de Guião Gráfico ou Nib que removeu anteriormente a um novo dicionário com o nome IntuneMAMSettings com os seguintes nomes de chaves, conforme aplicável:
    * MainStoryboardFile
    * MainStoryboardFile~ipad
    * MainNibFile
    * MainNibFile~ipad
    
   **Nota**: se a sua aplicação móvel não definir um Nib ou Guião Gráfico principal no respetivo ficheiro Info.plist, estas definições **não são necessárias**. 

    **Nota**: pode ver o ficheiro Info.plist em formato não processado (para ver os nomes de chaves) clicando com o botão direito do rato em qualquer parte do corpo do documento e alterando o tipo de vista para "Mostrar Chaves/Valores Não Processados".

6. Ative a partilha de keychain (se ainda não estiver ativada) clicando em ''Capacidades'' no destino de cada projeto e ativando o comutador "Partilha de Keychain". A partilha de keychain tem de avançar para o passo seguinte.

    **Nota**: o perfil de aprovisionamento tem de suportar os novos valores de partilha de keychain. Os grupos de acesso de keychain devem suportar um caráter universal. Pode verificar isto abrindo o ficheiro .mobileprovision num editor de texto, procurando ''keychain-access-groups'' e assegurando que tem um caráter universal, por exemplo: 
    ```
    <key>keychain-access-groups</key>
    <array>
    <string>YOURBUNDLESEEDID.*</string>
    </array>
    ```
7. Depois de ativar a partilha de keychain, siga estes passos para criar um grupo de acesso separado no qual serão armazenados os dados do SDK da Aplicação do Intune. Pode criar um grupo de acesso de keychain utilizando a IU ou o ficheiro de elegibilidade:

    Utilizar a IU para criar um grupo de acesso de keychain: 
    
    * Se a sua aplicação móvel não tiver nenhum grupo de acesso de keychain definido, adicione o ID do pacote da aplicação como primeiro grupo.
    * Adicione o grupo de keychain partilhado `com.microsoft.intune.mam`. Este grupo de acesso é utilizado pelo SDK da Aplicação do Intune para armazenar dados.  
    * Adicione `com.microsoft.adalcache` aos grupos de acesso existentes. 

    ![SDK da Aplicação do Intune para iOS - partilha de keychain](../media/intune-app-sdk-ios-keychain-sharing.png) 

    Se estiver a utilizar o ficheiro de elegibilidade para criar o grupo de acesso de keychain, em vez da IU normal, terá de preceder o grupo de acesso de keychain com `$(AppIdentifierPrefix)` no ficheiro de elegibilidade. Por exemplo:  
    * `$(AppIdentifierPrefix)com.microsoft.intune.mam` 
    * `$(AppIdentifierPrefix)com.microsoft.adalcache`

    **Nota**: um ficheiro de elegibilidade é um ficheiro XML exclusivo da aplicação móvel utilizado para especificar permissões e capacidades especiais na sua aplicação iOS.

8. Se a aplicação definir esquemas de URL no respetivo ficheiro Info.plist, adicione outro esquema, com um sufixo `-intunemam`, a cada esquema de URL.

9. Para as aplicações móveis desenvolvidas para o iOS 9+, tem de incluir cada protocolo transmitido pela aplicação a `UIApplication canOpenURL` na matriz `LSApplicationQueriesSchemes` do ficheiro Info.plist da aplicação. Além disso, para cada protocolo listado, é necessário adicionar e acrescentar `-intunemam`. Também tem de incluir `http-intunemam`, `https-intunemam`e `ms-outlook-intunemam` na matriz. 

10. Se a aplicação tiver grupos de aplicações definidos nas respetivas elegibilidades, adicione estes grupos ao dicionário IntuneMAMSettings na chave `AppGroupIdentitifiers` como uma matriz de cadeias.

11. Ligue a sua aplicação móvel à Azure Directory Authentication Library (ADAL). A biblioteca ADAL para Objective C está [disponível no Github](https://github.com/AzureAD/azure-activedirectory-library-for-objc).

    **Nota**: o SDK da Aplicação do Intune tem sido testada relativamente ao código do ramo de mediador da ADAL desde 19/6/2015. Certifique-se de que está a ligar à versão mais recente/em funcionamento da biblioteca ADAL.

12. Inclua o pacote de recursos `ADALiOSBundle.bundle` no projeto arrastando o pacote de recursos em "Copiar Recursos do Pacote" em "Fases de Criação".

13. Utilize a opção do linker `-force_load PATH_TO_ADAL_LIBRARY` quando ligar à biblioteca.

    Adicione `-force_load {PATH_TO_LIB}/libADALiOS.a` à definição de configuração da compilação `OTHER_LDFLAGS` do projeto ou "Outros Sinalizadores do Linker" na IU. `PATH_TO_LIB` deve ser substituído pela localização dos binários da ADAL. 

# Configurar as definições da Azure Directory Authentication Library (ADAL) na sua aplicação 

O SDK da Aplicação do Intune utiliza a ADAL para o cenário de autenticação e iniciação condicional. Também recorre à ADAL para registar a identidade do utilizador com o serviço MAM para uma gestão sem cenários de inscrição de dispositivos. 

Normalmente, a ADAL requer que as aplicações registem e obtenham um ID exclusivo, conhecido como ClientID, e outros identificadores, para garantir a segurança dos tokens concedidos à aplicação. O SDK da Aplicação do Intune utiliza valores de registo predefinidos ao contactar o Azure Active Directory.  

Se a aplicação utilizar a ADAL para o cenário de autenticação, a aplicação tem de utilizar os valores de registo existentes e substituir os valores predefinidos do SDK da Aplicação do Intune para assegurar que não é pedida a autenticação duas vezes aos utilizadores finais (uma vez pelo SDK da Aplicação do Intune e outra pela aplicação). 

##FAQ da ADAL

**Que binários da ADAL devo utilizar?** 

Atualmente, o SDK da Aplicação do Intune utiliza o ramo de mediação da [ADAL no GitHub](https://github.com/AzureAD/azure-activedirectory-library-for-objc) para suportar as aplicações que necessitam de Acesso Condicional (aplicações que, por conseguinte, dependem da aplicação Microsoft Authenticator). No entanto, o SDK ainda é compatível com o ramo principal da ADAL. Utilize o ramo que se destina à sua aplicação.

**Como posso ligar aos binários da ADAL?**

Adicione `-force_load {PATH_TO_LIB}/libADALiOS.a` à definição de configuração da compilação `OTHER_LDFLAGS` do projeto ou "Outros Sinalizadores do Linker" na IU. `PATH_TO_LIB` deve ser substituído pela localização dos binários da ADAL. Além disso, certifique-se de que copia o pacote da ADAL para a sua aplicação.  

Para obter mais detalhes, consulte as instruções em [ADAL no Github](https://github.com/AzureAD/azure-activedirectory-library-for-objc).


**Como posso partilhar a cache da ADAL com outras aplicações assinadas com o mesmo perfil de aprovisionamento?**

Se a sua aplicação não tiver nenhum grupo de acesso de keychain definido, adicione o ID do pacote da aplicação como primeiro grupo.
Ative o SSO da ADAL ao adicionar os grupos de acesso `com.microsoft.adalcache` e `com.microsoft.workplacejoin` nas elegibilidades de keychain. 

Caso esteja explicitamente a definir o grupo de keychain da cache partilhada da ADAL, certifique-se de que está definido como `<app_id_prefix>.com.microsoft.adalcache`. A ADAL define isto automaticamente, a menos que efetue uma substituição. Se quiser especificar um grupo de keychain personalizado para substituir `com.microsoft.adalcache`, especifique-o em Info.plist, em "IntuneMAMSettings", com a chave `ADALCacheKeychainGroupOverride`.

**Como posso forçar o SDK da Aplicação do Intune a utilizar as definições da ADAL que a minha aplicação já utiliza?** 

Se a sua aplicação já utiliza a ADAL, consulte a secção sobre IntuneMAMSettings mais abaixo para obter informações sobre o preenchimento das seguintes definições:  

* ADALClientId
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

**Como posso alternar entre a produção do AAD e os ambientes de teste internos?**

A definição `AadAuthorityURI` em `MAMPolicies.plist` pode ser utilizada para especificar o ambiente AAD utilizado em chamadas da ADAL. Atualmente, está predefinida para utilizar o Ambiente de Pré-Produção (PPE) do AAD, salvo em caso de substituição.
    
Para efetuar o teste com o PPE, pode utilizar um comutador de tempo de compilação ou tempo de execução. 

Para um comutador de ambiente de tempo de compilação do AAD e URLs do serviço MAM, defina o sinalizador Booleano `UsePPE` como True em MAMEnvironment.plist (**Nota**: não existe suporte para efetuar esta ação através de Info.plist). 

Num comutador de ambiente de tempo de execução, defina `com.microsoft.intune.mam.useppe` nas predefinições de utilizador padrão para "1" para utilizar o PPE. Esta definição substitui a definição `com.microsoft.intune.mam.AADAuthorityEnvironment` existente. 

**Como posso substituir o URL da autoridade do AAD por um URL específico de inquilino fornecido no tempo de execução?** 

Defina a propriedade `aadAuthorityUriOverride` na instância IntuneMAMPolicyManager.

**Nota**: isto é necessário no MAM sem o cenário de inscrição de dispositivos para permitir ao SDK reutilizar o token de atualização da ADAL obtido pela aplicação.

**Nota:** o SDK continuará a utilizar este URL de autoridade para a atualização da política e para futuros pedidos de inscrição, a menos que o valor seja limpo ou alterado.  Assim, é importante limpar o valor quando um utilizador empresarial terminar sessão na aplicação e reiniciar a mesma quando um novo utilizador empresarial voltar a iniciar sessão.


**O que devo fazer se a minha aplicação utilizar a ADAL para autenticação?**

Se a aplicação já utilizar a ADAL para autenticação, são necessários os passos abaixo. Se a sua aplicação não depender da ADAL, deve rever a secção sobre como se registar no serviço Intune se a sua aplicação não utilizar a ADAL.

* No ficheiro Info.plist do projeto, no dicionário IntuneMAMSettings com o nome de chave `ADALClientId`, especifique o ClientID a utilizar nas chamadas da ADAL. 

* No ficheiro Info.plist do projeto, no dicionário IntuneMAMSettings com o nome de chave `ADALRedirectUri`, especifique o URI de Redirecionamento a utilizar nas chamadas da ADAL. Também poderá ter de especificar o `ADALRedirectScheme` consoante o formato do URI de Redirecionamento da sua aplicação.



#Registar a sua aplicação com o serviço MAM 

## Utilizar as APIs
Agora, o SDK da Aplicação do Intune proporciona a capacidade de as aplicações iOS receberem políticas de MAM do Intune sem necessidade de estarem inscritas na MDM com o Intune. Para suportar esta nova funcionalidade, o SDK fornece novas APIs que permitem à aplicação receber políticas de MAM. Para utilizar as novas APIs, execute os seguintes passos:

1. Utilize a versão mais recente do SDK da Aplicação do Intune, que suporta a gestão de aplicações com ou sem a inscrição de dispositivos. Se a sua aplicação tiver utilizado uma versão mais antiga do SDK sem esta funcionalidade, terá de atualizar a biblioteca de MAM do Intune, bem como atualizar a pasta Cabeçalhos com os cabeçalhos do SDK mais recente.

2. Adicione o ficheiro IntuneMAMEnrollment.h aos ficheiros que irão chamar as APIs 

3. Para efetuar o teste com o PPE, pode incluir um comutador de tempo de compilação ou tempo de execução. 

    Para um comutador de ambiente de tempo de compilação do AAD e URLs do serviço MAM, defina o sinalizador Booleano `UsePPE` como True em MAMEnvironment.plist (**Nota**: não existe suporte para efetuar esta ação através de Info.plist). 

    Num comutador de ambiente de tempo de execução, defina `com.microsoft.intune.mam.useppe` nas predefinições de utilizador padrão para "1" para utilizar o PPE. Esta definição substitui a definição `com.microsoft.intune.mam.AADAuthorityEnvironment` existente. 


##Registar Contas 

Uma aplicação pode receber políticas de MAM do serviço Intune se a aplicação estiver inscrita em nome de uma conta de utilizador especificada.  A aplicação é responsável por registar utilizadores com sessão recentemente iniciada no SDK da Aplicação do Intune.  Após a nova conta de utilizador ser autenticada, a aplicação deverá chamar o método `registerAndEnrollAccount` localizado em Headers/IntuneMAMEnrollment.h: 

```
/** 


 *  This method will add the account to the list of registered accounts. 
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK 
 */ 

(void)registerAndEnrollAccount:(NSString *)identity; 

```
Ao chamar o método anteriormente mencionado, o SDK irá registar a conta de utilizador e tentar inscrever a aplicação em nome desta conta.  Se a inscrição falhar por algum motivo, o SDK irá automaticamente voltar a tentar a inscrição após 24 horas.  Para fins de depuração, a aplicação pode receber notificações, através de um delegado, sobre os resultados de pedidos de inscrição (consulte os detalhes abaixo).

Após esta API ser invocada, a aplicação poderá continuar a funcionar normalmente.  Se a inscrição for bem-sucedida, o SDK irá informar o utilizador de que é necessário reiniciar a aplicação.  Nessa altura, o utilizador pode reiniciar a aplicação imediatamente.


##Anular o registo de Contas 


Para que a sessão de um utilizador numa aplicação seja terminada, a aplicação deverá anular o registo do utilizador a partir do SDK.  Isto garante que: 

1. Deixarão de ocorrer novas tentativas de inscrição na conta do utilizador. 
2. Se o utilizador tiver inscrito a aplicação com êxito, a inscrição do utilizador e da aplicação serão anuladas do Serviço MAM do Intune e as políticas de MAM serão removidas.
3. Opcionalmente, pode iniciar uma eliminação seletiva para garantir a eliminação de todos os dados relacionados com o trabalho ou a escola. 

Antes de o utilizador terminar sessão, a aplicação deverá chamar a seguinte API que se encontra em Headers/IntuneMAMEnrollment.h: 

```
/*
 *  This method will remove the provided account from the list of 
 *  registered accounts.  Once removed, if the account has enrolled 
 *  the application, the account will be un-enrolled. 
 *  @note In the case where an un-enroll is required, this method will block 
 *  until the Intune MAM AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged 
 *  before this method is called). 
 *  @param identity The UPN of the account to be removed. 
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled 
 */ 

(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe; 
```

Este método tem de ser chamado antes de os tokens AAD da conta de utilizador serem eliminados.  O SDK necessita do token da aplicação do utilizador para efetuar pedidos específicos ao Serviço MAM do Intune em nome do utilizador. 

Se a aplicação for eliminar os dados de trabalho ou escola do utilizador automaticamente, o sinalizador `doWipe` pode ser definido como False.  Se não for o caso, a aplicação pode fazer com que o SDK inicie uma eliminação seletiva, cujo resultado será uma chamada para o delegado de eliminação seletiva da aplicação. 

```
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES]; 
```


##Inscrição Sem Início de Sessão Prévio 

Uma aplicação que não inicia a sessão do utilizador no Azure Active Directory pode receber políticas de MAM do Serviço Intune ao chamar a API abaixo para que o SDK processe essa autenticação. As aplicações devem recorrer a esta opção quando não tiverem autenticado um utilizador com o AAD mas precisarem, ainda assim, de obter as políticas de MAM para proteger os dados na respetiva aplicação. Por exemplo, se outro serviço de autenticação estiver a ser utilizado para iniciar sessão na aplicação ou se a aplicação não suportar qualquer início de sessão. Para tal, a aplicação deve chamar o método `loginAndEnrollAccount` que se encontra em Headers/IntuneMAMEnrollment.h:

```
/** 
 *  Creates an enrollment request which is started immediately. 
 *  If no token can be retrieved for the identity, the user will be prompted 
 *  to enter their credentials, after which enrollment will be retried. 
 *  @param identity The UPN of the account to be logged in and enrolled. 
 */ 
 (void)loginAndEnrollAccount: (NSString *)identity; 

```
Ao chamar este método, o SDK pede as credenciais ao utilizador se não for encontrado um token existente e, em seguida, tenta inscrever a aplicação em nome desta conta. O método pode ser chamado com "nil" como identidade e, se for o caso, o SDK inscreve com o utilizador de MAM existente no dispositivo ou solicita um nome de utilizador ao utilizador, se não for encontrado um utilizador existente. 

Se a inscrição falhar, a aplicação deverá considerar chamar esta API novamente numa altura posterior, consoante os detalhes da falha. A aplicação pode receber notificações, através de um delegado, sobre os resultados de pedidos de inscrição (consulte os detalhes). 

Após esta API ser invocada, a aplicação poderá continuar a funcionar normalmente.  Se a inscrição for efetuada com êxito, o SDK irá notificar o utilizador de que é necessário reiniciar a aplicação, conforme demonstrado na secção acima sobre o registo de contas. 

##Informações de Depuração 

A aplicação pode receber notificações de depuração relativas aos seguintes pedidos ao Serviço MAM do Intune: 

 - Pedidos de Inscrição 
 - Pedidos de Atualização da Política 
 - Pedidos de Anulação de Inscrição 

As notificações são apresentadas através de métodos delegados que pode encontrar em Headers/IntuneMAMEnrollmentDelegate.h: 

```
/** 
 *  Called when an enrollment request operation is completed. 
 * @param status status object containing debug information 
 */ 
 
(void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status; 

/** 
 *  Called when a MAM policy request operation is completed.
 *  @param status status object containing debug information 
 */ 
(void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status; 

/**
 *  Called when a un-enroll request operation is completed. 
 *  @Note: when a user is un-enrolled, the user is also de-registered with the SDK 
 *  @param status status object containing debug information 
 */ 

(void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status; 

```

Estes métodos delegados devolvem um objeto ```IntuneMAMEnrollmentStatus``` que contém as seguintes informações: 

- A identidade da conta associada ao pedido 
- Código de Estado que indica o resultado do pedido 
- Cadeia de erro com uma descrição do código de estado 
- Um objeto NSError 

Este objeto é definido em Headers/IntuneMAMEnrollmentStatus.h juntamente com os códigos de estado específicos que podem ser devolvidos. 

É importante ter em conta que estas informações se destinam a fins de depuração e que a lógica empresarial de aplicações não se deve basear nestas notificações.  O objetivo é a aplicação enviar estas informações para um serviço de telemetria, para fins de depuração ou monitorização. 


##Código de Exemplo 

Seguem-se exemplos de implementações dos métodos delegados: 

```
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status 


{ 


    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode); 


    NSLog(@"Debug Message: %@", status.errorString); 


} 


- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status 


{ 


    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode); 


    NSLog(@"Debug Message: %@", status.errorString); 


} 


- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status 


{ 


    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode); 



    NSLog(@"Debug Message: %@", status.errorString); 


} 

```


##Reinício da Aplicação 

Quando uma aplicação receber políticas de MAM pela primeira vez, terá de ser reiniciada para aplicar os hooks necessários.  Para notificar a aplicação de que é necessário reiniciar, o SDK fornece um método delegado em Headers/IntuneMAMPolicyDelegate.h. 
```
 - (BOOL) restartApplication 
```
O valor devolvido deste método indica ao SDK se a aplicação irá processar o reinício necessário.   

 - Se o valor devolvido for True, a aplicação será responsável por processar o reinício.   
 - Se o valor devolvido for False, o SDK irá reiniciar a aplicação após este método ser devolvido.  O SDK irá imediatamente mostrar uma caixa de diálogo a informar o utilizador de que é necessário reiniciar a aplicação. 



# Configurar as Definições do SDK da Aplicação do Intune

O dicionário IntuneMAMSettings contido no ficheiro Info.plist da aplicação é utilizado para configurar o SDK da Aplicação do Intune. Segue-se uma lista de todas as definições suportadas. 

Algumas destas definições poderão ter sido abordadas nas secções anteriores e outras não são aplicáveis a todas as aplicações. 

Definição  | Tipo  | Definição | Obrigatório?
--       |  --   |   --       |  --
ADALClientId  | Cadeia  | Identificador do cliente AAD da aplicação. | Necessário se a aplicação utilizar a ADAL.
ADALRedirectUri  | Cadeia  | URI de redirecionamento do AAD da aplicação. | Se a aplicação utilizar a ADAL, o ADALRedirectUri ou o ADALRedirectScheme são necessários. 
ADALRedirectScheme  | Cadeia  | O esquema de redirecionamento do AAD da aplicação. Pode ser utilizado em vez do ADALRedirectUri se o URI de redirecionamento da aplicação estiver no formato `scheme://bundle_id`. | Se a aplicação utilizar a ADAL, o ADALRedirectUri ou o ADALRedirectScheme são necessários. 
ADALLogOverrideDisabled | Booleano  | Especifica se o SDK encaminhará todos os registos da ADAL (incluindo chamadas da ADAL a partir da aplicação, caso existam) para o seu próprio ficheiro de registo. Assume a predefinição de NO. Definido como YES se a aplicação pretender definir a sua própria chamada de retorno de registo da ADAL. | Opcional.
ADALCacheKeychainGroupOverride | Cadeia  | Especifica o grupo de keychain a utilizar para a cache da ADAL em vez de "com.microsoft.adalcache". Note que isto não contém o prefixo app-id. Será adicionado como prefixo à cadeia fornecida no tempo de execução. | Opcional.
AppGroupIdentifiers | Matriz da Cadeia  | Matriz de grupos de aplicações da secção de elegibilidade com.apple.security.application-groups. | Necessário se a aplicação utilizar grupos de aplicações.
ContainingAppBundleId | Cadeia | Especifica o ID do pacote da aplicação que contém a extensão. | Necessário para as extensões de iOS.
DebugSettingsEnabled| Booleano | Se for definido como YES, as políticas de teste no pacote de Definições podem ser aplicadas. As aplicações **não** devem ser fornecidas com esta definição ativada. | Opcional.
MainNibFile<br>MainNibFile~ipad  | Cadeia  | Esta definição deve conter o nome de ficheiro nib principal da aplicação.  | Necessário se a aplicação definir MainNibFile no respetivo ficheiro Info.plist.
MainStoryboardFile<br>MainStoryboardFile~ipad  | Cadeia  | Esta definição deve conter o nome de ficheiro de guião gráfico principal da aplicação. | Necessário se a aplicação definir UIMainStoryboardFile no respetivo ficheiro Info.plist
MAMPolicyRequired| Booleano| Especifica se a aplicação será impedida de iniciar se não tiver a política de MAM do Intune. Assume a predefinição "no". 
MAMPolicyWarnAbsent | Booleano| Especifica se a aplicação avisa o utilizador, ao iniciar, se a aplicação não tiver a política de MAM do Intune. Nota: as aplicações não podem ser submetidas à loja com esta definição definida como YES | Opcional.
MultiIdentity | Booleano| Especifica se a aplicação tem ou não conhecimento de identidades múltiplas | Opcional.
SplashIconFile <br>SplashIconFile~ipad | Cadeia  | Especifica o ficheiro de ícone de ecrã inicial do Intune. Consulte a secção em "Ficheiros de Imagem no Arranque" aqui para obter mais detalhes. | Opcional.
SplashDuration | Número | Quantidade mínima de tempo em segundos durante o qual será apresentado o Ecrã Inicial do Intune na iniciação da aplicação. Assume a predefinição de 1,5. | Opcional.
BackgroundColor| Cadeia| Especifica a cor de fundo para os ecrãs inicial e de PIN. Aceita uma cadeia RGB hexadecimal sob a forma de "#XXXXXX", sendo que os "X"s podem ir de 0 a 9 ou de A a F. O sinal de cardinal pode ser omitido.   | Opcional, assume a predefinição de cinzento claro.
ForegroundColor| Cadeia| Especifica a cor de primeiro plano para os ecrãs inicial e de PIN, como a cor do texto. Aceita uma cadeia RGB hexadecimal sob a forma de "#XXXXXX", sendo que os "X"s podem ir de 0 a 9 ou de A a F. O sinal de cardinal pode ser omitido.  | Opcional, assume a predefinição de Preto.
AccentColor | Cadeia| Especifica a cor do ambiente do ecrã de PIN, como a cor do texto em botões e a cor de destaque em caixas.  Aceita uma cadeia RGB hexadecimal sob a forma de "#XXXXXX", sendo que os "X"s podem ir de 0 a 9 ou de A a F. O sinal de cardinal pode ser omitido.| Opcional, assume a predefinição de azul de sistema.
MAMTelemetryDisabled| Booleano| Especifica se o SDK não envia dados de telemetria de volta para o respetivo back-end| Opcional.
MAMTelemetryUsePPE | Booleano | Especifica se o SDK irá enviar dados para o back-end do Ambiente de Pré-Produção (PPE). Utilize esta opção ao testar as suas aplicações com a política do Intune, para que os dados de telemetria de teste não se misturem com os dados de clientes. | Opcional.

## Telemetria 

Por predefinição, o SDK da Aplicação do Intune para iOS regista dados telemétricos de eventos de utilização, os quais são enviados para o Microsoft Intune. Os dados são registados nos seguintes eventos de utilização: 

1. **Iniciação da aplicação**: para ajudar o Microsoft Intune a saber mais informações sobre a utilização de aplicações ativadas para MAM por tipo de gestão (MAM com MDM, MAM sem inscrição MDM, etc.).

2. **Chamada da API EnrollApplication**: para ajudar o Microsoft Intune a conhecer a taxa de êxito e várias outras métricas de desempenho das chamadas `enrollApplication` no lado do cliente.

**Nota**: se optar por não enviar os dados telemétricos do SDK da Aplicação do Intune para o Microsoft Intune a partir da sua aplicação móvel, terá de desativar a captura da telemetria do SDK da Aplicação do Intune definindo a propriedade `MAMTelemetryDisabled` como "YES" no dicionário IntuneMAMSettings.


## Criar o SDK na sua extensão (opcional) 

Quando criar extensões, siga as mesmas instruções para criar a sua aplicação móvel conforme descrito na secção em "Criar o SDK na sua aplicação móvel". Além disso, atualize o ficheiro Info.plist de cada extensão ao adicionar uma chave `ContainingAppBundleId` no dicionário IntuneMAMSettings com o valor do ID do pacote da aplicação.

## Criar o SDK na sua estrutura (opcional)

Com as atualizações mais recentes ao SDK da Aplicação do Intune, não tem de compilar a sua aplicação móvel com sinalizadores de linker específicos se esta contiver estruturas de aplicações incorporadas. 

## Ficheiros de Imagem no Arranque (opcional)

Quando uma aplicação ativada para MAM for gerida ativamente pelo Microsoft Intune, o SDK da Aplicação do Intune apresentará um ecrã de arranque na iniciação da aplicação para indicar ao utilizador que a aplicação é gerida. Opcionalmente, pode adicionar ficheiros de imagem para serem apresentados na página de arranque "Gerido pela sua empresa". Utilize as seguintes orientações para imagens:

* Adicione os nomes de ficheiro no dicionário IntuneMAMSettings no ficheiro Info.plist da aplicação com os nomes de chave `SplashIconFile` e `SplashIconFile~ipad`. 

* Tamanho e requisitos de imagens:

    * 180x180 para o iPhone 6s Plus e iPhone 6 Plus, 120x120 para outros modelos de iPhone e 152x152 para iPad. 
    
    * Remova a extensão .png dos nomes de ficheiro. 
    
    * Utilize a opção do linker `@2x` para versões de escala 2x e o sufixo `@3x` para versões de escala 3x dos ficheiros de imagem. Se as imagens não tiverem o tamanho correto, serão dimensionadas para se ajustarem. Se os valores de SplashIconFile não forem especificados, o SDK da Aplicação do Intune seleciona um dos ícones da aplicação (60x60 para todos os iPhones, 76x76 para iPad).

**Nota**: este ecrã é acionado pela iniciação, mas pode ser dispensado permanentemente pelo utilizador.



#Ativar Identidades Múltiplas (opcional)

Por predefinição, o SDK aplica a política à aplicação como um todo. As Identidades Múltiplas são uma funcionalidade de MAM que pode ser ativada para permitir que a política seja aplicada num nível por identidade.  Esta opção requer uma maior participação da aplicação do que outras funcionalidades de MAM. 

A aplicação tem de informar ao SDK da aplicação quando tenciona alterar a identidade ativa. O SDK também notifica a aplicação quando for necessária uma alteração de identidade. Atualmente, apenas é suportada uma identidade gerida. Quando o utilizador inscrever o dispositivo ou a aplicação, o SDK utiliza esta identidade e considera-a a identidade gerida primária. Os outros utilizadores na aplicação serão tratados como não geridos, com definições de política não restrita. 

Note que uma identidade é simplesmente definida como uma cadeia. As identidades são sensíveis às maiúsculas e minúsculas e os pedidos de identidade ao SDK podem não devolver a mesma utilização de maiúsculas e minúsculas que tinha sido originalmente utilizada ao definir a identidade.


##Compreender as Identidades 
  
Uma identidade é simplesmente o nome de utilizador de uma conta (por exemplo, utilizador@contoso.com). Os programadores podem definir a identidade da aplicação nos seguintes níveis: 

* **Identidade de processo**: a identidade de processo define a identidade em todo o processo e é maioritariamente utilizada em aplicações de identidade única. Esta identidade afeta todas as operações, os ficheiros e a IU.
* **Identidade da IU**: determina que políticas são aplicadas às operações de IU no thread principal, como cortar/copiar/colar, PIN, autenticação, partilha de dados, etc. A identidade da IU não afeta as operações de ficheiros (encriptação, cópia de segurança, etc.). 
* **Identidade do thread**: a identidade do thread afeta que políticas são aplicadas ao thread atual. Esta ação afeta todas as operações, os ficheiros e a IU.

É da responsabilidade da aplicação definir as identidades de forma adequada, independentemente de o utilizador ser gerido ou não.

A qualquer altura, todos os threads têm uma identidade eficaz para operações de IU e operações de ficheiros. Esta é a identidade utilizada para determinar que políticas devem ser aplicadas (se forem aplicadas políticas). Se a identidade for "no identity" ou se o utilizador não for gerido, não serão aplicadas políticas. 
 
 

##Filas de Threads
 
As aplicações emitem muitas vezes tarefas assíncronas e síncronas para filas de threads. O SDK interceta chamadas do Grand Central Dispatch (GCD) e associa a atual identidade do thread às tarefas emitidas. Quando as tarefas forem executadas, o SDK altera temporariamente a identidade do thread para a identidade associada à tarefa, executa as tarefas e, em seguida, restaura a identidade do thread original. Uma vez que o `NSOperationQueue` é criado sobre o GCD, o `NSOperations` será executado na identidade do thread na altura em que for adicionado ao `NSOperationQueue`. O `NSOperations` ou as funções emitidas utilizando diretamente o GCD também têm a capacidade de alterar a identidade do thread atual durante a execução. Esta identidade substitui a identidade herdada do thread emissor. 

##Proprietário do Ficheiro
 
O SDK acompanha a identidade do proprietário do ficheiro local e aplica as políticas de acordo com a mesma. O proprietário do ficheiro é estabelecido quando o ficheiro é criado ou quando o ficheiro é aberto em modo truncado. O proprietário está definido para a identidade de operação de ficheiro efetiva do thread que executa a operação. Em alternativa, as aplicações podem definir a identidade de proprietário do ficheiro explicitamente, ao utilizar o `IntuneMAMFilePolicyManager`. As aplicações podem utilizar o `IntuneMAMFilePolicyManager` para obter o proprietário do ficheiro e definir a identidade de IU antes de apresentar os conteúdos do ficheiro.


##Ficheiros de Dados Partilhados
 
Se a aplicação criar ficheiros com dados de utilizadores geridos e não geridos, é da responsabilidade da aplicação encriptar os dados do utilizador gerido. Os dados podem ser encriptados utilizando as APIs `protect` e `unprotect` do `IntuneMAMDataProtectionManager`. O método `protect` aceita uma identidade que pode ser um utilizador gerido ou não gerido. Se o utilizador for gerido, os dados serão encriptados. Se o utilizador for não gerido, será adicionado um cabeçalho aos dados de codificação da identidade, mas os dados não serão encriptados.  O método `protectionInfo` pode ser utilizado para obter o proprietário dos dados.

##Extensões de Partilha
 
Se a aplicação contiver uma Extensão de Partilha, o proprietário do item partilhado pode ser obtido com recurso ao método `protectionInfoForItemProvider` no `IntuneMAMDataProtectionManager`. Se o item partilhado for um ficheiro, o SDK irá processar a definição do proprietário do ficheiro. Se o item partilhado consistir em dados, será da responsabilidade da aplicação definir o proprietário do ficheiro, se estes dados forem persistentes num ficheiro, e chamar a API `setUIPolicyIdentity` (abaixo descrita) antes de apresentar estes dados na IU.
 
#Ativar Identidades Múltiplas
 
Por predefinição, as aplicações são consideradas de identidade única e a identidade do processo é definida pelo SDK para o utilizador inscrito. Para ativar o suporte para identidades múltiplas, uma definição booleana de nome "MultiIdentity", com o valor "YES", deverá ser adicionada ao dicionário IntuneMAMSettings no ficheiro Info.plist das aplicações. Quando as identidades múltiplas estiverem ativadas, as identidades de processo, IU e thread serão definidas como nulas e será responsabilidade da aplicação defini-las de forma adequada.

 
##Mudar Identidades
 
###Mudança de identidade iniciada pela aplicação
Ao iniciar, considera-se que as aplicações de identidades múltiplas estão a ser executadas numa conta desconhecida e não gerida. A IU de inicialização condicional não será executada e não serão aplicadas políticas na aplicação. É da responsabilidade da aplicação notificar o SDK sempre que a identidade deva ser alterada. Normalmente, este processo ocorre sempre que a aplicação estiver prestes a apresentar os dados de uma conta de utilizador específica.

Um exemplo desta situação é quando o utilizador tenta abrir um documento, uma caixa de correio ou um separador num bloco de notas. A aplicação tem de notificar o SDK antes que o ficheiro, a caixa de correio ou o separador sejam efetivamente abertos. Este processo é realizado através da API `setUIPolicyIdentity` no `IntuneMAMPolicyManager`. Esta API deve ser chamada quer o utilizador seja gerido ou não. Se o utilizador for gerido, o SDK irá executar as verificações de inicialização condicional (deteção de jailbreak, PIN, autenticação, etc.). O resultado da mudança de identidade é devolvido à aplicação de forma assíncrona através de um processador de conclusão. A aplicação deverá adiar a abertura do documento, caixa de correio, separador, etc. até que um código de resultado de sucesso seja devolvido. Se a mudança de identidade tiver falhado, a aplicação deverá cancelar a operação. 

###Mudança de identidade iniciada pelo SDK
Existem casos em que o SDK precisa de pedir à aplicação que mude para uma identidade específica. As aplicações de identidades múltiplas têm de implementar o método `identitySwitchRequired` no `IntuneMAMPolicyDelegate` para processar este pedido. Aquando da chamada, se a aplicação conseguir processar o pedido de mudança para a identidade especificada, deverá passar o `IntuneMAMAddIdentityResultSuccess` para o processador de conclusão. Se este não conseguir processar a mudança de identidade, a aplicação deverá passar o `IntuneMAMAddIdentityResultFailed` para o processador de conclusão. A aplicação não tem de chamar o `setUIPolicyIdentity` em resposta a esta chamada. Se o SDK necessitar da aplicação para mudar para uma conta de utilizador não gerida, a cadeia vazia será passada para a chamada do `identitySwitchRequired`. 
 
###Eliminação seletiva
Quando uma limpeza seletiva for efetuada na aplicação, o SDK irá ligar para o método `wipeDataForAccount` no `IntuneMAMPolicyDelegate`. É da responsabilidade da aplicação remover a conta do utilizador especificado, bem como quaisquer dados associados à mesma. O SDK é capaz de remover todos os ficheiros do utilizador e efetuará esta ação se a aplicação devolver "FALSE" da chamada do `wipeDataForAccount`. Note que este método é chamado de um thread em segundo plano e a aplicação não deverá regressar até todos os dados do utilizador serem removidos (com exceção dos ficheiros se a aplicação devolver o valor "FALSE").

# Depurar o SDK da Aplicação do Intune em Xcode

Antes de testar manualmente a sua aplicação ativada para MAM com o Microsoft Intune, pode utilizar um ficheiro **Settings.bundle** enquanto estiver no Xcode. Isto permitirá definir políticas de teste sem necessidade de uma ligação ao Intune. Para ativá-la:

* Adicione um ficheiro Settings.bundle clicando com o botão direito do rato na pasta de nível superior do seu projeto. Selecione "Adicionar -> Novo Ficheiro" no menu. Selecione o modelo "Pacote de Definições" em "Recursos" a adicionar.

* Apenas nas compilações de depuração, copie MAMDebugSettings.plist para Settings.bundle.

* Em Root.plist (que se encontra em Settings.bundle), adicione uma preferência com "Type" = Painel de Subordinados e "FileName" = MAMDebugSettings.

* Em **Definições -> Nome da Aplicação**, ative "Ativar Políticas de Teste".

* Inicie a aplicação (dentro ou fora do Xcode). 

* Em **Definições -> Nome da Aplicação -> Ativar Políticas de Teste**, ative uma política, por exemplo, ''PIN''.

* Inicie a aplicação (dentro ou fora do Xcode). Verifique se o PIN funciona conforme esperado.

> [!NOTE]
> Pode agora utilizar **Definições -> Nome da Aplicação -> Ativar Políticas de Teste** para ativar e acionar definições.

# Melhores Práticas Recomendadas para iOS

Seguem-se algumas melhores práticas recomendadas para quando desenvolver para iOS:

O sistema de ficheiros iOS é sensível às maiúsculas e minúsculas. Certifique-se de que as maiúsculas e minúsculas estão corretas para os nomes de ficheiro, como `libIntuneMAM.a` e `IntuneMAMResources.bundle`.

Se o Xcode tiver problemas a localizar `libIntuneMAM.a`, pode corrigir o problema ao adicionar o caminho a esta biblioteca nos caminhos de pesquisa do linker.



##FAQ 

 **Todos os utilizadores da minha aplicação têm de estar registados no serviço MAM?**

Não.  De facto, apenas as contas do trabalho ou escolares devem ser registadas no SDK da Aplicação do Intune.  As aplicações são responsáveis por determinar se uma conta é utilizada num contexto profissional ou escolar.   
 
**E os utilizadores que já iniciaram sessão na aplicação?  Precisam de ser inscritos?** 

Apesar de a aplicação ser responsável por inscrever os utilizadores após estes efetuarem a autenticação com êxito, a aplicação também é responsável por inscrever contas existentes que já existiam antes de a aplicação ter funcionalidade MAM sem MDM.   


Para tal, a aplicação deve utilizar o método `registeredAccounts:`.  Este método devolve um NSDictionary com todas as contas registadas no serviço MAM do Intune.  Se existirem contas na aplicação que não estejam presentes na lista, a aplicação deverá registar e inscrever as respetivas contas através do `registerAndEnrollAccount:`. 


 

**Com que frequência é que o SDK volta a tentar inscrições?** 

O SDK volta a tentar automaticamente todas as inscrições anteriormente falhadas a cada 24 horas.  O SDK efetua este procedimento para garantir que, se a organização de um utilizador tiver ativado o MAM após o utilizador ter iniciado sessão na aplicação, o utilizador será inscrito com êxito e receberá as políticas. 

O SDK deixará de voltar a tentar quando detetar que um utilizador se inscreveu na aplicação com êxito.  Isto deve-se ao facto de apenas um utilizador poder inscrever uma aplicação de cada vez. Se a inscrição do utilizador for anulada, as novas tentativas começarão de novo no mesmo intervalo de 24 horas. 


 
**Por que motivo o registo do utilizador tem de ser anulado?** 

O SDK efetua as seguintes ações em segundo plano de forma periódica:

 - Se a aplicação ainda não estiver inscrita, esta tentará inscrever todas as contas registadas de 24 em 24 horas. 
 - Se a aplicação estiver inscrita, o SDK irá procurar atualizações à política de MAM de 8 em 8 horas. 

Ao anular o registo de um utilizador, o SDK será notificado de que o utilizador deixará de utilizar a aplicação e poderá interromper qualquer um dos eventos periódicos anteriores para a respetiva conta de utilizador.  Também irá acionar uma anulação de inscrição da aplicação e limpeza seletiva, se necessário. 

**Devo definir o sinalizador doWipe como True no método de anulação do registo?** Este método deve ser chamado antes de o utilizador terminar a sessão na aplicação.  Se, ao terminar sessão, os dados do utilizador forem eliminados da aplicação, o `doWipe` pode ser definido como False.  No entanto, se a aplicação não remover efetivamente os dados do utilizador, deverá defini-lo como True, para que o SDK possa eliminar os dados manualmente. 

**Existem outras formas de anular o registo de uma aplicação?** Sim, o administrador de TI pode enviar um comando de limpeza seletiva para a aplicação, o que fará com que o utilizador tenha o registo e a inscrição anulados e os dados do utilizador sejam limpos.  O SDK processa este cenário automaticamente e irá enviar uma notificação através do método de delegação de anulação de inscrição. 

#Enviar a sua aplicação à App Store
Tanto a biblioteca estática como as compilações de estrutura do SDK da Aplicação do Intune são binários universais, o que significa que contêm código para todas as arquiteturas de dispositivo e simulador. A Apple rejeita as aplicações submetidas à App Store se estas contiverem código de simulador. Ao compilar com a biblioteca estática em compilações apenas de dispositivo, o linker retira o código de simulador automaticamente.

Se a sua aplicação utilizar a **compilação da estrutura** do SDK da Aplicação do Intune, terá de retirar manualmente as arquiteturas do simulador da estrutura universal antes de submeter a sua aplicação à App Store. As instruções abaixo ajudam-no a atingir este fim:

1. Certifique-se de que o `IntuneMAM.framework` está no seu Ambiente de Trabalho.
2. Execute os seguintes comandos:
    
    ```
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```
    O primeiro comando retira as arquiteturas de simulador do dylib da estrutura.
    ```
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM 
    ```
    O segundo comando copia o dylib apenas para dispositivo de volta para o diretório da estrutura.



<!--HONumber=Sep16_HO4-->


