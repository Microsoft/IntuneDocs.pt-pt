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
ms.sourcegitcommit: 952cfa4f23f8ba080ce53f6785baceb8a0a367c6
ms.openlocfilehash: 0d69d0b230771a87c1103682b17336dc47d26622


---

# Guia para Programadores do SDK da Aplicação Microsoft Intune para iOS

> [!NOTE]
> Pode ler primeiro o [Guia de Introdução ao SDK da Aplicação do Intune](intune-app-sdk-get-started.md), que explica como preparar a integração em cada plataforma suportada.* 

O SDK da Aplicação Microsoft Intune para iOS permite incorporar a Gestão de Aplicações Móveis do Intune (MAM) na sua aplicação iOS. Uma aplicação preparada para MAM está integrada no SDK da Aplicação Intune e permite aos administradores de TI implementar políticas na sua aplicação móvel quando a aplicação é gerida ativamente.

## O que está no SDK

O SDK da Aplicação Intune para iOS inclui uma biblioteca estática, ficheiros de recursos, cabeçalhos de API, um plist de definições de Depuração e uma ferramenta de configurador. As aplicações móveis podem simplesmente incluir os ficheiros de recursos e ligar estaticamente às bibliotecas para a maioria das imposições de políticas. As funcionalidades avançadas de MAM do Intune são impostas através de APIs.
Este guia irá abranger o seguinte quando utilizar quando integrar o SDK da Aplicação Intune para iOS:

* **`libIntuneMAM.a`**: a biblioteca do SDK da Aplicação Intune. Ligue esta biblioteca ao seu projeto para tornar a sua aplicação móvel preparada para MAM. Pode encontrar instruções na secção "Criar uma aplicação com o SDK da Aplicação Intune".

* **`IntuneMAMResources.Bundle`**: um pacote de recursos que contém o SDK do qual depende. 

* **Cabeçalhos**: expõe as APIs do SDK da Aplicação Intune. Se utilizar uma API, terá de incluir o ficheiro de cabeçalho que contém a API. 

## Como funciona o SDK da Aplicação Intune

O objetivo do SDK da Aplicação Intune para iOS consiste em adicionar capacidades de gestão para aplicações iOS com alterações de código mínimas. Reduzir a quantidade de alterações de código diminui o tempo de comercialização, aumentando a consistência e a estabilidade da sua aplicação móvel. 

A aplicação tem de ser ligada à biblioteca estática e incluir o pacote de recursos. O ficheiro MAMDebugSettings.plist é opcional e pode ser incluído no pacote para simular políticas de MAM a serem aplicadas à aplicação sem necessidade de implementar a aplicação através do Microsoft Intune. Além das compilações de depuração, as políticas no ficheiro MAMDebugSettings.plist podem ser aplicadas transferindo o ficheiro MAMDebugSettings.plist para o diretório Documentos da aplicação através da partilha de ficheiros do iTunes.

## Criar a sua aplicação com o SDK da Aplicação Intune 

Conclua os passos abaixo para ativar o SDK da Aplicação Intune:

1. Ligue à biblioteca `libIntuneMAM.a` efetuando o seguinte procedimento:

    Arraste e largue a biblioteca libIntuneMAM.a na lista "Linked Frameworks and Libraries" (Estruturas e Bibliotecas Ligadas) do destino do projeto.  

    ![SDK da Aplicação Intune para iOS - estruturas e bibliotecas ligadas](../media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)
 
    **Nota**: quando disponibilizar na app store, utilize a versão do libIntuneMAM.a criada para lançamento e não a versão de depuração. A versão de lançamento estará na pasta "release". A versão de depuração tem uma saída verbosa ideal para problemas de depuração com o SDK da Aplicação Intune.

2. Adicione as seguinte estruturas de iOS ao projeto (se estiverem em falta).
    * `MessageUI.framework`
    * `Security.framework`
    * `MobileCoreServices.framework`
    * `SystemConfiguration.framework`
    * `libsqlite3.dylib`
    * `libc++.dylib`
    * `ImageIO.framework`
    * `LocalAuthentication.Framework`
    * `AudioToolbox.framework`<br>

    **Nota**: se a aplicação se destinar ao iOS7, defina o atributo ''Status'' de `LocalAuthentication.Framework` para "Opcional". 

    Se ''Status'' não estiver definido, a aplicação não será iniciada no iOS7.

    **Nota**: Xcode 7 mudou as extensões `.dylib` para `.tbd`.

3. Adicione o pacote de recursos `IntuneMAMResources.bundle` ao projeto arrastando o pacote de recursos em "Copiar Recursos do Pacote" em "Fases de Criação". 

    ![SDK da Aplicação Intune para iOS - copiar recursos do pacote](../media/intune-app-sdk-ios-copy-bundle-resources.png)

4. Adicione `-force_load {PATH_TO_LIB}/libIntuneMAM.a` a qualquer um dos seguintes, substituindo `{PATH_TO_LIB}` pela localização do SDK da Aplicação Intune:
    * Definição de configuração da compilação OTHER_LDFLAGS do projeto 
    * "Outros Sinalizadores do Linker" da IU<br>

    **Nota**: para localizar `PATH_TO_LIB`, selecione o ficheiro `libIntuneMAM.a` e escolha ''Informações'' a partir do menu ''Ficheiro''. Copie e cole as informações "Onde" (o caminho) na secção "Geral" da janela ''Informações''.

5. Se a sua aplicação móvel define um Nib ou Guião Gráfico principal no respetivo ficheiro `info.plist`, remova os campos dos ficheiros Guião Gráfico Principal ou Nib Principal. Adicione os valores de Guião Gráfico ou Nib que removeu anteriormente a um novo dicionário com o nome `IntuneMAMSettings` com os seguintes nomes de chaves, conforme aplicável:
    * `MainStoryboardFile`
    * `MainStoryboardFile~ipad`
    * `MainNibFile`
    * `MainNibFile~ipad `
    
    Se a sua aplicação móvel não definir um Nib ou Guião Gráfico principal no respetivo ficheiro `info.plist`, estas definições **não são necessárias**. 

    **Nota**: pode ver o ficheiro `info.plist` em formato não processado (para ver os nomes de chaves) clicando com o botão direito do rato em qualquer parte do corpo do documento e alterando o tipo de vista para "Mostrar Chaves/Valores Não Processados".

6. Ative a partilha de keychain (se ainda não estiver ativada) clicando em ''Capacidades'' no destino de cada projeto e ativando o comutador Partilha de Keychain. A partilha de keychain tem de avançar para o passo seguinte.

    **Nota**: o perfil de aprovisionamento tem de suportar os novos valores de partilha de keychain. Os grupos de acesso de keychain devem suportar um caráter universal. Pode verificar isto abrindo o ficheiro `.mobileprovision` num editor de texto, procurando ''keychain-access-groups'' e assegurando que tem um caráter universal, por exemplo: 

       <key>keychain-access-groups</key>
       <array>
       <string>YOURBUNDLESEEDID.*</string>
       </array>

7. Depois de ativar a partilha de keychain, siga estes passos para criar um grupo de acesso separado no qual serão armazenados os dados do SDK da Aplicação Intune. Pode criar um grupo de acesso de keychain utilizando a IU ou o ficheiro de elegibilidade:

    Utilizar a IU para criar um grupo de acesso de keychain: 
    
    * Se a sua aplicação móvel não tiver nenhum grupo de acesso de keychain definido, adicione o ID do pacote da aplicação como primeiro grupo.
    * Adicione o grupo da keychain partilhado com.microsoft.intune.mam. Este grupo de acesso é utilizado pelo SDK da Aplicação Intune para armazenar dados.  
    * Adicione o pacote de recursos `com.microsoft.adalcache` aos grupos de acesso existentes. 
 
    ![SDK da Aplicação do Intune para iOS - partilha de keychain](../media/intune-app-sdk-ios-keychain-sharing.png)

    Se estiver a utilizar o ficheiro de elegibilidade para criar o grupo de acesso de keychain, em vez da IU normal, terá de preceder o grupo de acesso de keychain com `$(AppIdentifierPrefix)` no ficheiro de elegibilidade. Por exemplo: `$(AppIdentifierPrefix)com.microsoft.intune.mam` e `$(AppIdentifierPrefix)com.microsoft.adalcache`.

    **Nota**: um ficheiro de elegibilidade é um ficheiro XML exclusivo da aplicação móvel utilizado para especificar permissões e capacidades especiais na sua aplicação iOS.

8. Para as aplicações móveis que estão a ser desenvolvidas para o iOS 9+, tem de incluir cada protocolo transmitido pela aplicação móvel a `UIApplication canOpenURL` na matriz `LSApplicationQueriesSchemes` do ficheiro `info.plist` da aplicação móvel. Além disso, para cada protocolo listado, é necessário adicionar e acrescentar `-intunemam`. Também tem de incluir `http-intunemam`, `https-intunemam`e `ms-outlook-intunemam` na matriz. 

9. Se a aplicação definir esquemas de URL no respetivo `info.plist file`, adicione outro esquema, com um sufixo `-intunemam` , a cada esquema de URL.

10. Se a aplicação tiver grupos de aplicações definidos nas respetivas elegibilidades, adicione estes grupos ao dicionário `IntuneMAMSettings` na chave `AppGroupIdentitifiers` como uma matriz de cadeias.

11. Ligue a sua aplicação móvel à biblioteca ADAL. A biblioteca ADAL para Objective C está [disponível no Github](https://github.com/AzureAD/azure-activedirectory-library-for-objc).

    **Nota**: o SDK da Aplicação Intune tem sido testada relativamente ao código do ramo de mediador da ADAL desde 19/6/2015. Certifique-se de que está a ligar à versão mais recente/em funcionamento da biblioteca ADAL.

12. Inclua o pacote `ADALiOSBundle.bundle resource` no projeto arrastando o pacote de recursos em "Copiar Recursos do Pacote" em "Fases de Criação".

13. Utilize a opção do linker `-force_load PATH_TO_ADAL_LIBRARY` quando ligar à biblioteca.

    Adicione `-force_load {PATH_TO_LIB}/libADALiOS.a` à definição de configuração da compilação OTHER_LDFLAGS do projeto ou "Outros Sinalizadores do Linker" na IU. "PATH_TO_LIB" deve ser substituído pela localização dos binários da ADAL. 

Se a sua aplicação móvel utilizar a ADAL para a sua própria autenticação, consulte a secção em "Configurar Definições da Biblioteca de Autenticação do Azure Directory" localizada aqui.

### Telemetria 

Por predefinição, o SDK da Aplicação Intune para iOS regista dados telemétricos de eventos de utilização, os quais são enviados para o Microsoft Intune.

Os dados são registados nos seguintes eventos de utilização: 

1. Iniciação da aplicação para ajudar o Microsoft Intune a saber mais sobre a utilização de aplicações ativadas para MAM por tipo de gestão.

2. Chamada da API EnrollApplication para ajudar o Microsoft Intune a saber mais sobre a taxa de êxito e várias outras métricas de desempenho da chamada enrollApplication no lado do cliente.

**Nota**: se optar por não enviar os dados telemétricos do SDK da Aplicação Intune para o Microsoft Intune a partir da sua aplicação móvel, **terá de desativar** a captura de telemetria do SDK da Aplicação Intune definindo a propriedade `MAMTelemetryDisabled` como ’‘YES’’ em `IntuneMAMSettings`.

## Configurar a Biblioteca de Autenticação do Azure Directory (ADAL) (opcional)

O SDK da Aplicação Intune utiliza a ADAL para o cenário de autenticação e iniciação condicional. Normalmente, a ADAL requer que as aplicações registem e obtenham um ID exclusivo, conhecido como `ClientID`, e outros identificadores, para garantir a segurança dos tokens concedidos à aplicação. O SDK da Aplicação Intune utiliza valores de registo predefinidos ao contactar o Azure Active Directory.  Se a aplicação utilizar a ADAL para o cenário de autenticação, a aplicação tem de utilizar os valores de registo existentes e substituir a predefinição do SDK da Aplicação Intune para assegurar que não é pedida a autenticação duas vezes aos utilizadores finais (uma vez pelo SDK da Aplicação Intune e outra pela aplicação). 

São necessários os passos seguintes se a aplicação utilizar a ADAL para autenticação. Se a sua aplicação móvel não depender da ADAL, não é necessária nenhuma ação adicional. 

1. No ficheiro `Info.plist`do projeto, num dicionário `IntuneMAMSettings` com o nome de chave `ADALClientId`, especifique o `ClientID` a utilizar nas chamadas da ADAL. 

2. No ficheiro `Info.plist`do projeto, no dicionário `IntuneMAMSettings` com o nome de chave `ADALRedirectUri`, especifique o URI de Redirecionamento a utilizar nas chamadas da ADAL. Também poderá ter de especificar o `ADALRedirectScheme` consoante o formato do URI de Redirecionamento da sua aplicação.

### Criar Extensões (opcional) 

Quando criar extensões, siga as mesmas instruções para criar a sua aplicação móvel conforme descrito na secção em "Criar a sua aplicação com o SDK da Aplicação Intune" localizada aqui. Além disso, atualize o ficheiro info.plist de cada extensão para adicionar uma chave ContainingAppBundleId no dicionário IntuneMAMSettings com o valor do ID do pacote da aplicação.

### Criar Estruturas (opcional)

Com as alterações mais recentes ao SDK da Aplicação Intune, não tem de compilar a sua aplicação móvel com sinalizadores de linker específicos se esta contiver estruturas de aplicações incorporadas. 

### Ficheiros de Imagem no Arranque (opcional)

Quando uma aplicação ativada para MAM for gerida ativamente pelo Microsoft Intune, o SDK da Aplicação Intune apresentará um ecrã de arranque na iniciação da aplicação para indicar ao utilizador que a aplicação é gerida. Opcionalmente, pode adicionar ficheiros de imagem para serem apresentados na página de arranque "Gerido pela sua empresa". Utilize as seguintes orientações para imagens:

* Adicione os nomes de ficheiro no dicionário `IntuneMAMSettings` no ficheiro info.plist da aplicação com os nomes de chave `SplashIconFile` e `SplashIconFile~ipad`. 

* Tamanho e requisitos de imagens:

    * 180x180 para o iPhone 6s Plus e iPhone 6 Plus, 120x120 para outros modelos de iPhone e 152x152 para iPad. 
    
    * Remova a extensão `.png` dos nomes de ficheiro 
    
    * Utilize a opção do linker `@2x` para versões de escala 2x e o sufixo `@3x` para versões de escala 3x dos ficheiros de imagem. Se as imagens não tiverem o tamanho correto, serão dimensionadas para se ajustarem. Se os valores de SplashIconFile não forem especificados, o SDK da Aplicação Intune seleciona um dos ícones da aplicação (60x60 para todos os iPhones, 76x76 para iPad).

**Nota**: este ecrã é acionado pela iniciação, mas pode ser dispensado permanentemente pelo utilizador.

## Configurar as Definições do SDK da Aplicação Intune

O dicionário `IntuneMAMSettings` contido no ficheiro `info.plist` da aplicação é utilizado para configurar o SDK da Aplicação Intune. Segue-se uma lista de todas as definições suportadas. 

Algumas destas definições poderão ter sido abordadas nas secções anteriores e outras não são aplicáveis a todas as aplicações. 

Definição  | Tipo  | Definição | Obrigatório?
--|--|--|--
ADALClientId  | Cadeia  | Identificador do cliente AAD da aplicação. | Necessário se a aplicação utilizou a ADAL.
ADALRedirectUri  | Cadeia  | URI de redirecionamento do AAD da aplicação. | Necessário se a aplicação utilizou a ADAL. 
AppGroupIdentifier | Matriz da Cadeia  | Matriz de grupos de aplicações da secção de elegibilidade com.apple.security.application-groups. | Necessário se a aplicação utilizar grupos de aplicações.
ContainingAppBundleId  | Cadeia | Especifica o ID do pacote da aplicação que contém a extensão. | Necessário para as extensões de iOS.
MainNibFile<br>MainNibFile~ipad  | Cadeia  | Esta definição deve conter o nome de ficheiro nib principal da aplicação.  | Necessário se a aplicação definir MainNibFile no respetivo ficheiro info.plist.
MainStoryboardFile<br>MainStoryboardFile~ipad  | Cadeia  | Esta definição deve conter o nome de ficheiro de guião gráfico principal da aplicação. | Necessário se a aplicação definir UIMainStoryboardFile no respetivo ficheiro info.plist
SplashIconFile <br>SplashIconFile~ipad  | Cadeia  | Especifica o ficheiro de ícone de ecrã inicial do Intune. Consulte a secção em "Ficheiros de Imagem no Arranque" aqui para obter mais detalhes. | Opcional.
SplashDuration | Número | Quantidade mínima de tempo em segundos durante o qual será apresentado o Ecrã Inicial do Intune na iniciação da aplicação. Assume a predefinição de 1,5. | Opcional.
ADALLogOverrideDisabled | Booleano  | Especifica se o SDK encaminhará todos os registos da ADAL (incluindo chamadas da ADAL a partir da aplicação, caso existam) para o seu próprio ficheiro de registo. Assume a predefinição de NO. Definido como YES se a aplicação pretender definir a sua própria chamada de retorno de registo da ADAL. | Opcional.

## Cabeçalhos do SDK da Aplicação Intune 

Os Cabeçalhos seguintes incluem as chamadas de função da API necessárias para ativar a funcionalidade do SDK da Aplicação Intune. 

    IntuneMAMAsyncResult.h
    IntuneMAMDataProtectionInfo.h
    IntuneMAMDataProtectionManager.h
    IntuneMAMFileProtectionInfo.h
    IntuneMAMFileProtectionManager.h
    IntuneMAMPolicyDelegate.h
    IntuneMAMLogger.h

## Depurar o SDK da Aplicação Intune em Xcode

Antes de testar a sua aplicação ativada para MAM com o Microsoft Intune, pode utilizar `Settings.bundle` enquanto estiver no Xcode. Isto permitirá definir políticas de teste sem necessidade de uma ligação ao Intune. Para ativá-la:

* Adicione um `Settings.bundle` clicando com o botão direito do rato na pasta de nível superior do seu projeto. Selecione "Adicionar -> Novo Ficheiro" no menu. Selecione o modelo "Pacote de Definições" em "Recursos" a adicionar.

* Apenas nas compilações de depuração, copie `MAMDebugSettings.plist` para `Settings.bundle`.

* Em `Root.plist` (em Settings.bundle), adicione uma preferência do Painel de Subordinados "Type", "FileName" `MAMDebugSettings`.

* Em "Definições -> Nome da Aplicação", acione "Ativar Políticas de Teste".

* Inicie a aplicação (dentro ou fora do Xcode). 

* Em "Definições -> Nome da Aplicação -> Ativar Políticas de Teste", acione uma política, por exemplo, ''PIN''.

* Inicie a aplicação (dentro ou fora do Xcode). Verifique se o PIN funciona conforme esperado.

> [!NOTE]
> Pode agora utilizar "Definições -> Nome da Aplicação -> Ativar Políticas de Teste" para ativar e acionar definições.

## Melhores Práticas Recomendadas para iOS

Seguem-se algumas melhores práticas recomendadas para quando desenvolver para iOS:

O sistema de ficheiros iOS é sensível às maiúsculas e minúsculas. Certifique-se de que as maiúsculas e minúsculas estão corretas para os nomes de ficheiro, como `libIntuneMAM.a` e `IntuneMAMResources.bundle`.

Se o Xcode tiver problemas a localizar `libIntuneMAM.a`, pode corrigir o problema ao adicionar o caminho a esta biblioteca nos caminhos de pesquisa do linker.




<!--HONumber=Sep16_HO2-->


