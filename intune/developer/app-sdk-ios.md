---
title: Guia para programadores do SDK da Aplicação Microsoft Intune para iOS
description: O SDK da Aplicação do Microsoft Intune para iOS permite-lhe incorporar as políticas de proteção de aplicações do Intune (também conhecidas como políticas de APLICAÇÕES ou MAM) na sua aplicação iOS nativa.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6edf3fd8d6c6aeefeb1e34c5b390360e7215f21
ms.sourcegitcommit: 822a70c61f5d644216ccc401b8e8949bc39e8d4a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76125298"
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Guia para programadores do SDK da Aplicação Microsoft Intune para iOS

> [!NOTE]
> Considere ler o artigo [Guia de Introdução ao SDK da Aplicação do Intune](app-sdk-get-started.md), que explica como preparar a integração em cada plataforma suportada.

O SDK da Aplicação do Microsoft Intune para iOS permite-lhe incorporar as políticas de proteção de aplicações do Intune (também conhecidas como políticas de APLICAÇÕES ou MAM) na sua aplicação iOS nativa. Uma aplicação preparada para MAM é uma integrada com o SDK da Aplicação Intune. Os administradores de TI podem implementar políticas de proteção de aplicações na aplicação móvel quando o Intune está a gerir a aplicação de forma ativa.

## <a name="prerequisites"></a>Pré-requisitos

* Você precisará de um computador Mac OS que execute o OS X 10.8.5 ou posterior e também tenha o Xcode 9 ou posterior instalado.

* Seu aplicativo deve ser direcionado para o iOS 11 ou superior.

* Consulte os [Termos de Licenciamento do SDK da Aplicação do Intune para iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS.pdf). Imprima e guarde uma cópia dos termos de licenciamento nos seus registos. Ao transferir e utilizar o SDK da Aplicação do Intune para iOS, aceita esses termos de licenciamento.  Caso não aceite os termos, não utilize o software.

* Transfira os ficheiros para o SDK da Aplicação do Intune para iOS no [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios).

## <a name="whats-in-the-sdk-repository"></a>O que há no repositório do SDK

Os arquivos a seguir são relevantes para aplicativos/extensões que não contêm nenhum código Swift ou são compilados com uma versão do Xcode antes de 10,2:

* **IntuneMAM.framework**: estrutura do SDK da Aplicação do Intune. É recomendável que você vincule essa estrutura ao seu aplicativo/extensões para habilitar o gerenciamento de aplicativos cliente do Intune. No entanto, alguns desenvolvedores podem preferir os benefícios de desempenho da biblioteca estática. Consulte o seguinte.

* **libIntuneMAM.a**: biblioteca estática do SDK da Aplicação do Intune. Os desenvolvedores podem optar por vincular a biblioteca estática em vez da estrutura. Como as bibliotecas estáticas são inseridas diretamente no binário do aplicativo/extensão no momento da compilação, há alguns benefícios de desempenho de tempo de inicialização para usar a biblioteca estática. No entanto, integrá-lo ao seu aplicativo é um processo mais complicado. Se seu aplicativo incluir qualquer extensão, vincular a biblioteca estática ao aplicativo e às extensões resultará em um tamanho de pacote de aplicativo maior, pois a biblioteca estática será inserida em cada aplicativo/binário de extensão. Ao usar a estrutura, os aplicativos e as extensões podem compartilhar o mesmo binário do SDK do Intune, resultando em um tamanho de aplicativo menor.

* **IntuneMAMResources. Bundle**: um pacote de recursos que contém recursos dos quais o SDK depende. O pacote de recursos é necessário apenas para aplicativos que integram a biblioteca estática (libIntuneMAM. a).

Os arquivos a seguir são relevantes para aplicativos/extensões que contêm código Swift e são compilados com o Xcode 10.2 +:

* **IntuneMAMSwift. Framework**: a estrutura Swift do SDK de aplicativo do Intune. Essa estrutura contém todos os cabeçalhos para APIs que seu aplicativo chamará. Vincule essa estrutura ao seu aplicativo/extensões para habilitar o gerenciamento de aplicativos cliente do Intune.

* **IntuneMAMSwiftStub. Framework**: a estrutura de stub Swift do SDK de aplicativo do Intune. Essa é uma dependência necessária do IntuneMAMSwift. Framework que os aplicativos/extensões devem vincular.


Os seguintes arquivos são relevantes para todos os aplicativos/extensões:

* **IntuneMAMConfigurator**: uma ferramenta usada para configurar o info. plist do aplicativo ou da extensão com as alterações mínimas necessárias para o gerenciamento do Intune. Dependendo da funcionalidade de seu aplicativo ou extensão, talvez seja necessário fazer alterações manuais adicionais no info. plist.

* **Cabeçalhos**: expõe as APIs públicas do SDK de aplicativo do Intune. Esses cabeçalhos estão incluídos nas estruturas IntuneMAM/IntuneMAMSwift, de modo que os desenvolvedores que consomem qualquer uma das estruturas não precisam adicionar manualmente os cabeçalhos ao seu projeto. Os desenvolvedores que optam por vincular-se à biblioteca estática (libIntuneMAM. a) precisarão incluir manualmente esses cabeçalhos em seu projeto.

Os seguintes ficheiros de cabeçalho incluem as APIs, tipos de dados e protocolos que o SDK da Aplicação Intune disponibiliza aos programadores:

-  IntuneMAMAppConfig.h
-  IntuneMAMAppConfigManager.h
-  IntuneMAMDataProtectionInfo.h
-  IntuneMAMDataProtectionManager.h
-  IntuneMAMDefs.h
-  IntuneMAMDiagnosticConsole.h
-  IntuneMAMEnrollmentDelegate.h
-  IntuneMAMEnrollmentManager.h
-  IntuneMAMEnrollmentStatus.h
-  IntuneMAMFileProtectionInfo.h
-  IntuneMAMFileProtectionManager.h
-  IntuneMAMLogger.h
-  IntuneMAMPolicy.h
-  IntuneMAMPolicyDelegate.h
-  IntuneMAMPolicyManager.h
-  IntuneMAMVersionInfo.h

Os desenvolvedores podem tornar o conteúdo de todos os cabeçalhos anteriores disponíveis simplesmente importando IntuneMAM. h


## <a name="how-the-intune-app-sdk-works"></a>Como funciona o SDK da Aplicação Intune

O objetivo do SDK da Aplicação do Intune para iOS consiste em adicionar capacidades de gestão para aplicações iOS com alterações de código mínimas. Quanto menos o código for alterado, menor o tempo de colocação no mercado, mas sem afetar a consistência e a estabilidade do seu aplicativo móvel.


## <a name="build-the-sdk-into-your-mobile-app"></a>Criar o SDK na sua aplicação móvel

Para ativar o SDK da Aplicação Intune, siga estes passos:

1. **Opção 1-estrutura (recomendado)** : se você estiver usando o Xcode 10.2 + e seu aplicativo/extensão contiver código Swift, vincule `IntuneMAMSwift.framework` e `IntuneMAMSwiftStub.framework` ao seu destino: arraste `IntuneMAMSwift.framework` e `IntuneMAMSwiftStub.framework` para a lista de **binários inseridos** do destino do projeto.

    Caso contrário, vincule `IntuneMAM.framework` ao seu destino: arraste `IntuneMAM.framework` para a lista de **binários inseridos** do destino do projeto.

   > [!NOTE]
   > Se utilizar a estrutura, terá de retirar manualmente as arquiteturas do simulador da estrutura universal antes de submeter a sua aplicação na App Store. Veja [Enviar a aplicação à App Store](#submit-your-app-to-the-app-store) para obter mais detalhes.

   **Opção 2-biblioteca estática**: essa opção só está disponível para aplicativos/extensões que não contêm nenhum código Swift ou foram criadas com o Xcode < 10,2. Link para a biblioteca de `libIntuneMAM.a`. Arraste a biblioteca `libIntuneMAM.a` para a lista **Estruturas e Bibliotecas Ligadas** do destino do projeto.

    ![SDK da Aplicação do Intune para iOS: estruturas e bibliotecas ligadas](./media/app-sdk-ios/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    Adicione `-force_load {PATH_TO_LIB}/libIntuneMAM.a` a qualquer um dos seguintes, substituindo `{PATH_TO_LIB}` pela localização do SDK da Aplicação do Intune:
   * A definição de configuração do `OTHER_LDFLAGS` Build do projeto.
   * Os **outros sinalizadores do vinculador**da interface do usuário do Xcode.

     > [!NOTE]
     > Para localizar `PATH_TO_LIB`, selecione o ficheiro `libIntuneMAM.a` e escolha **Informações** a partir do menu **Ficheiro**. Copie e cole as informações **Onde** (o caminho) na secção **Geral** da janela **Informações**.

     Adicione o pacote de recursos `IntuneMAMResources.bundle` ao projeto, ao arrastar o pacote de recursos em **Copiar Recursos do Pacote** em **Fases de Criação**.

     ![SDK da Aplicação do Intune para iOS: copiar recursos do pacote](./media/app-sdk-ios/intune-app-sdk-ios-copy-bundle-resources.png)
         
2. Adicione estas estruturas de iOS ao projeto:  
-  MessageUI.framework  
-  Security.framework  
-  MobileCoreServices.framework  
-  SystemConfiguration.framework  
-  libsqlite3.tbd  
-  libc++.tbd  
-  ImageIO.framework  
-  LocalAuthentication.framework  
-  AudioToolbox.framework  
-  QuartzCore.framework  
-  WebKit.framework

3. Ative a partilha de keychain (se não estiver já ativada) ao selecionar **Capacidades** no destino de cada projeto e ao ativar o comutador **Partilha de Keychain**. A partilha de keychain é necessária para avançar para o passo seguinte.

   > [!NOTE]
   > O perfil de aprovisionamento tem de suportar os novos valores de partilha de keychain. Os grupos de acesso de keychain devem suportar um caráter universal. Você pode verificar isso abrindo o arquivo. mobileprovision em um editor de texto, procurando por **keychain-Access-groups**e garantindo que você tenha um caractere curinga. Por exemplo:
   >
   >  ```xml
   >  <key>keychain-access-groups</key>
   >  <array>
   >  <string>YOURBUNDLESEEDID.*</string>
   >  </array>
   >  ```

4. Depois de habilitar o compartilhamento de conjunto de chaves, siga as etapas para criar um grupo de acesso separado no qual o SDK do aplicativo do Intune armazenará seus dados. Pode criar um grupo de acesso de keychain com a IU ou o ficheiro de elegibilidade. Se você estiver usando a interface do usuário para criar o grupo de acesso do conjunto de chaves, certifique-se de seguir estas etapas:

     a. Se seu aplicativo móvel não tiver grupos de acesso do conjunto de chaves definidos, adicione a ID do pacote do aplicativo como o **primeiro** grupo.
    
    b. Adicione o grupo de keychain partilhado `com.microsoft.intune.mam` aos seus grupos de acesso existentes. O SDK da Aplicação do Intune utiliza este grupo de acesso para armazenar dados.
    
    c. Adicione `com.microsoft.adalcache` aos seus grupos de acesso existentes.
    
      ![SDK da Aplicação do Intune para iOS: partilha de keychain](./media/app-sdk-ios/intune-app-sdk-ios-keychain-sharing.png)
    
    d. Se estiver a editar diretamente o ficheiro de elegibilidade, em vez de utilizar a IU do Xcode mostrada acima para criar grupos de acesso de keychain, inclua o acesso de keychain no início com `$(AppIdentifierPrefix)` (o Xcode processa o ficheiro automaticamente). Por exemplo:
    
      - `$(AppIdentifierPrefix)com.microsoft.intune.mam`
      - `$(AppIdentifierPrefix)com.microsoft.adalcache`
    
      > [!NOTE]
      > Um ficheiro de elegibilidade é um ficheiro XML exclusivo para a sua aplicação móvel. Serve para especificar permissões e capacidades especiais na aplicação iOS. Se a aplicação não tinha anteriormente nenhum ficheiro de elegibilidade, a ativação da partilha de keychain (passo 3) deverá levar à geração de um ficheiro de elegibilidade pelo Xcode para a aplicação. Verifique se a ID do pacote do aplicativo é a primeira entrada na lista.

5. Inclua cada protocolo transmitido pela aplicação a `UIApplication canOpenURL` na matriz `LSApplicationQueriesSchemes` do ficheiro Info.plist da aplicação. Não se esqueça de guardar as alterações antes de prosseguir para o passo seguinte.

6. Se a sua aplicação ainda não utilizar o FaceID, garanta que a [chave Info.plist NSFaceIDUsageDescription](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW75) está configurada com uma mensagem predefinida. Isto é necessário para que o iOS possa informar o utilizador sobre como é que a aplicação pretende utilizar o FaceID. Uma definição de política de proteção de aplicações do Intune permite que o FaceID seja utilizado como um método para aceder a aplicações quando configurado pelo administrador de TI.

7. Utilize a ferramenta IntuneMAMConfigurator, incluída no [repositório do SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios), para concluir a configuração do ficheiro Info.plist da aplicação. A ferramenta tem três parâmetros:

   |Propriedade|Como a utilizar|
   |---------------|--------------------------------|
   |- i |  `<Path to the input plist>` |
   |- e | `<Path to the entitlements file>` |
   |- o |  (Opcional) `<Path to the output plist>` |

Se o parâmetro “-o” não for especificado, o ficheiro de entrada será modificado no local. A ferramenta é idempotent e deve ser executada novamente sempre que forem feitas alterações ao ficheiro Info.plist da aplicações ou tenham sido criadas elegibilidades. Deverá também transferir e executar a versão mais recente da ferramenta ao atualizar o SDK do Intune, caso os requisitos de configuração do ficheiro Info.plist tenham sido alterados na versão mais recente.

## <a name="configure-adalmsal"></a>Configurar ADAL/MSAL

O SDK de aplicativos do Intune pode usar a [biblioteca de autenticação do Azure Active Directory](https://github.com/AzureAD/azure-activedirectory-library-for-objc) ou a biblioteca de autenticação da [Microsoft](https://github.com/AzureAD/microsoft-authentication-library-for-objc) para seus cenários de inicialização condicional e autenticação. Ele também se baseia no ADAL/MSAL para registrar a identidade do usuário no serviço de MAM para gerenciamento sem cenários de registro de dispositivo.

Normalmente, o ADAL/MSAL exige que os aplicativos se registrem com Azure Active Directory (AAD) e criem uma ID de cliente e um URI de redirecionamento exclusivos para garantir a segurança dos tokens concedidos ao aplicativo. Se seu aplicativo já usa ADAL ou MSAL para autenticar usuários, o aplicativo deve usar seus valores de registro existentes e substituir os valores padrão do SDK de aplicativo do Intune. Isto garante que os utilizadores não recebem um pedido de autenticação duas vezes (uma vez pelo SDK da Aplicação Intune e uma vez pela aplicação).

Se seu aplicativo ainda não usar ADAL ou MSAL e você não precisar acessar nenhum recurso do AAD, você não precisará configurar um registro de aplicativo cliente no AAD se optar por integrar a ADAL. Se você decidir integrar o MSAL, precisará configurar um registro de aplicativo e substituir a ID do cliente do Intune e o URI de redirecionamento padrão.  

É recomendável que seu aplicativo se vincule à versão mais recente do [Adal](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) ou [MSAL](https://github.com/AzureAD/microsoft-authentication-library-for-objc/releases).

### <a name="link-to-adal-or-msal-binaries"></a>Link para os binários ADAL ou MSAL

**Opção 1-** Siga [estas etapas](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download) para vincular seu aplicativo aos binários da Adal.

**Opção 2-** Como alternativa, você pode seguir [estas instruções](https://github.com/AzureAD/microsoft-authentication-library-for-objc#installation) para vincular seu aplicativo aos binários do MSAL.

1. Se a sua aplicação não tiver nenhum grupo de acesso de keychain definido, adicione o ID do pacote da aplicação como primeiro grupo.

2. Habilite o SSO (logon único) do ADAL/MSAL adicionando `com.microsoft.adalcache` aos grupos de acesso do conjunto de chaves.

3. Caso esteja explicitamente a definir o grupo de keychain da cache partilhada da ADAL, certifique-se de que está definido como `<appidprefix>.com.microsoft.adalcache`. A ADAL define isto automaticamente, a menos que efetue uma substituição. Se quiser especificar um grupo de keychain personalizado para substituir o `com.microsoft.adalcache`, especifique-o no ficheiro Info.plist, em IntuneMAMSettings, com a chave `ADALCacheKeychainGroupOverride`.

### <a name="configure-adalmsal-settings-for-the-intune-app-sdk"></a>Definir as configurações de ADAL/MSAL para o SDK de aplicativos do Intune

Se seu aplicativo já usa ADAL ou MSAL para autenticação e tem suas próprias configurações de Azure Active Directory, você pode forçar o SDK de aplicativo do Intune a usar as mesmas configurações durante a autenticação no AAD. Esta ação garante que a aplicação não solicita a autenticação ao utilizador duas vezes. Veja [Configurar as definições para o SDK da Aplicação do Intune](#configure-settings-for-the-intune-app-sdk) para obter mais informações sobre o preenchimento das seguintes informações:  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

Se seu aplicativo já usa ADAL ou MSAL, as seguintes configurações são necessárias:

1. No ficheiro Info.plist do projeto, no dicionário **IntuneMAMSettings** com o nome de chave `ADALClientId`, especifique o ID de Cliente a utilizar nas chamadas da ADAL.

2. Também no dicionário **IntuneMAMSettings** com o nome de chave `ADALAuthority`, especifique a autoridade do Azure AD.

3. Também no dicionário **IntuneMAMSettings** com o nome de chave `ADALRedirectUri`, especifique o URI de redirecionamento a utilizar nas chamadas da ADAL. Em alternativa, pode especificar `ADALRedirectScheme` se o URI de redirecionamento da aplicação estiver no formato `scheme://bundle_id`.

Além disso, as aplicações podem substituir estas definições do Azure AD no runtime. Para tal, basta definir as propriedades `aadAuthorityUriOverride`, `aadClientIdOverride` e `aadRedirectUriOverride` na instância `IntuneMAMPolicyManager`.

4. Verifique se as etapas para dar permissões ao aplicativo iOS para o serviço de política de proteção de aplicativo (aplicativo) foram seguidas. Use as instruções no [guia Introdução ao SDK do Intune](app-sdk-get-started.md#next-steps-after-integration) em "Dê ao[seu aplicativo acesso ao serviço de proteção de aplicativo do Intune (opcional)](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)".  

> [!NOTE]
> Para todas as definições que são estáticas e que não precisam de ser determinadas no runtime, recomenda-se a abordagem do ficheiro Info.plist. Os valores atribuídos às propriedades `IntuneMAMPolicyManager` têm precedência sobre quaisquer valores correspondentes especificados no ficheiro Info.plist e serão mantidos, mesmo depois de a aplicação ser reiniciada. O SDK continuará a utilizá-los para os registos da política até que a inscrição do utilizador seja anulada ou os valores sejam limpos ou alterados.

### <a name="if-your-app-does-not-use-adal-or-msal"></a>Se seu aplicativo não usar ADAL ou MSAL

Como mencionado anteriormente, o SDK de aplicativo do Intune pode usar a [biblioteca de autenticação Azure Active Directory](https://github.com/AzureAD/azure-activedirectory-library-for-objc) ou a [biblioteca de autenticação da Microsoft](https://github.com/AzureAD/microsoft-authentication-library-for-objc) para seus cenários de autenticação e de inicialização condicional. Ele também se baseia no ADAL/MSAL para registrar a identidade do usuário no serviço de MAM para gerenciamento sem cenários de registro de dispositivo. Se **seu aplicativo não usar a Adal ou a MSAL para seu próprio mecanismo de autenticação**, talvez seja necessário definir configurações personalizadas do AAD, dependendo da biblioteca de autenticação que você optar por integrar:   

ADAL – o SDK de aplicativo do Intune fornecerá valores padrão para parâmetros de ADAL e tratará a autenticação no Azure AD. Os desenvolvedores não precisam especificar nenhum valor para as configurações de ADAL mencionadas anteriormente. 

MSAL-os desenvolvedores precisam criar um registro de aplicativo no AAD com um URI de redirecionamento personalizado no formato especificado [aqui](https://github.com/AzureAD/microsoft-authentication-library-for-objc/wiki/Migrating-from-ADAL-Objective-C-to-MSAL-Objective-C#app-registration-migration). Os desenvolvedores devem definir as configurações de `ADALClientID` e `ADALRedirectUri` mencionadas anteriormente ou as propriedades equivalentes `aadClientIdOverride` e `aadRedirectUriOverride` na instância de `IntuneMAMPolicyManager`. Os desenvolvedores também devem garantir que sigam a etapa 4 na seção anterior, para dar acesso ao registro do aplicativo ao serviço de proteção de aplicativo do Intune.

### <a name="special-considerations-when-using-msal"></a>Considerações especiais ao usar o MSAL 

1. **Verifique seu WebView** -é recomendável que os aplicativos não usem SFSafariViewController, SFAuthSession ou ASWebAuthSession como seu WebView para todas as operações de autenticação interativa do MSAL iniciadas pelo aplicativo. Se, por algum motivo, seu aplicativo precisar usar uma dessas exibições de todas as operações de autenticação MSAL interativas, ele também deverá definir `SafariViewControllerBlockedOverride` como `true` no dicionário de `IntuneMAMSettings` no info. plist do aplicativo. Aviso: Isso desativará os ganchos de SafariViewController do Intune para habilitar a sessão de autenticação. Isso faz o risco de vazamentos de dados em outro lugar no aplicativo se o aplicativo usar o SafariViewController para exibir dados corporativos, para que o aplicativo não mostre dados corporativos em nenhum desses tipos de WebView.
2. **Vinculando a Adal e a MSAL** -os desenvolvedores devem optar se desejarem que o INTUNE prefira MSAL sobre a Adal nesse cenário. Por padrão, o Intune preferirá as versões de ADAL com suporte para versões do MSAL com suporte, se ambas estiverem vinculadas em tempo de execução. O Intune só preferirá uma versão do MSAL com suporte quando, no momento da primeira operação de autenticação do Intune, `IntuneMAMUseMSALOnNextLaunch` for `true` no `NSUserDefaults`. Se `IntuneMAMUseMSALOnNextLaunch` for `false` ou não definido, o Intune fará o fallback para o comportamento padrão. Como o nome sugere, uma alteração em `IntuneMAMUseMSALOnNextLaunch` entrará em vigor na próxima inicialização.


## <a name="configure-settings-for-the-intune-app-sdk"></a>Configurar as definições para o SDK da Aplicação do Intune

Pode utilizar o dicionário **IntuneMAMSettings** no ficheiro Info.plist da aplicação para preparar e configurar o SDK da Aplicação do Intune. Se o dicionário IntuneMAMSettings não estiver no ficheiro Info.plist, deverá criá-lo.

No dicionário IntuneMAMSettings, pode adicionar as seguintes definições suportadas para configurar o SDK da Aplicação do Intune.

Algumas destas definições podem ter sido abordadas nas secções anteriores e outras não são aplicáveis a todas as aplicações.

Definição  | Type  | Definition | Obrigatório?
--       |  --   |   --       |  --
ADALClientId  | Cadeia  | Identificador do cliente Azure AD da aplicação. | Necessário para todos os aplicativos que usam MSAL e qualquer aplicativo ADAL que acesse um recurso do AAD não Intune. |
ADALAuthority | Cadeia | Autoridade do Azure AD da aplicação em utilização. Deve utilizar o seu ambiente onde foram configuradas contas do AAD. | Necessário se o aplicativo usar ADAL ou MSAL para acessar um recurso do AAD que não seja do Intune. Se este valor estiver ausente, será utilizado um valor predefinido do Intune.|
ADALRedirectUri  | Cadeia  | URI de redirecionamento do Azure AD da aplicação. | ADALRedirectUri ou ADALRedirectScheme é necessário para todos os aplicativos que usam MSAL e qualquer aplicativo ADAL que acesse um recurso do AAD não Intune.  |
ADALRedirectScheme  | Cadeia  | O esquema de redirecionamento do Azure AD da aplicação. Pode ser utilizado em vez do ADALRedirectUri se o URI de redirecionamento da aplicação estiver no formato `scheme://bundle_id`. | ADALRedirectUri ou ADALRedirectScheme é necessário para todos os aplicativos que usam MSAL e qualquer aplicativo ADAL que acesse um recurso do AAD não Intune. |
ADALLogOverrideDisabled | Booleano  | Especifica se o SDK irá rotear todos os logs de ADAL/MSAL (incluindo chamadas de ADAL do aplicativo, se houver) para seu próprio arquivo de log. Assume a predefinição de NO. Defina como Sim se o aplicativo definir seu próprio retorno de chamada de log ADAL/MSAL. | Opcional. |
ADALCacheKeychainGroupOverride | Cadeia  | Especifica o grupo de conjunto de chaves a ser usado para o cache ADAL/MSAL, em vez de "com. Microsoft. adalcache". Tenha em atenção que isto não tem o prefixo app-id. Será adicionado como prefixo à cadeia fornecida no tempo de execução. | Opcional. |
AppGroupIdentifiers | matriz de cadeias de caracteres  | Matriz de grupos de aplicações da secção de elegibilidade com.apple.security.application-groups. | Necessário se a aplicação utilizar grupos de aplicações. |
ContainingAppBundleId | Cadeia | Especifica o ID do pacote da aplicação que contém a extensão. | Necessário para as extensões de iOS. |
DebugSettingsEnabled| Booleano | Se for definido como YES, as políticas de teste no pacote de Definições podem ser aplicadas. As aplicações *não* devem ser fornecidas com esta definição ativada. | Opcional. Assume a predefinição de NO. |
AutoEnrollOnLaunch| Booleano| Especifica se a aplicação deve tentar inscrever-se automaticamente quando inicia se for detetada uma identidade gerida existente e ainda não o tiver feito. Assume a predefinição de NO. <br><br> Observações: se nenhuma identidade gerenciada for encontrada ou nenhum token válido para a identidade estiver disponível no cache ADAL/MSAL, a tentativa de registro falhará silenciosamente sem solicitar credenciais, a menos que o aplicativo também tenha definido MAMPolicyRequired como Sim. | Opcional. Assume a predefinição de NO. |
MAMPolicyRequired| Booleano| Especifica se a aplicação será impedida de iniciar se não tiver uma política de proteção de aplicação do Intune. Assume a predefinição de NO. <br><br> Notas: as aplicações não podem ser submetidas à App Store com a MAMPolicyRequired definida como YES. Ao definir a MAMPolicyRequired como YES, a AutoEnrollOnLaunch também deve ser definida como YES. | Opcional. Assume a predefinição de NO. |
MAMPolicyWarnAbsent | Booleano| Especifica se a aplicação irá avisar o utilizador ao iniciar se a aplicação não tiver uma política de proteção de aplicação do Intune. <br><br> Nota: os utilizadores ainda poderão utilizar a aplicação sem a política após ignorarem o aviso. | Opcional. Assume a predefinição de NO. |
MultiIdentity | Booleano| Especifica se a aplicação tem conhecimento de identidades múltiplas. | Opcional. Assume a predefinição de NO. |
SafariViewControllerBlockedOverride | Booleano| Desabilita os ganchos de SafariViewController do Intune para habilitar a autenticação MSAL via SFSafariViewController, SFAuthSession ou ASWebAuthSession. | Opcional. Assume a predefinição de NO. Aviso: pode resultar em perda de dados se for usado de forma inadequada. Habilitar somente se absolutamente necessário. Consulte [considerações especiais ao usar o MSAL](#special-considerations-when-using-msal) para obter detalhes.  |
SplashIconFile <br>SplashIconFile~ipad | Cadeia  | Especifica o ficheiro de ícone de ecrã inicial (arranque) do Intune. | Opcional. |
SplashDuration | Número | Quantidade mínima de tempo, em segundos, durante a qual será mostrado o ecrã de arranque do Intune na iniciação da aplicação. Assume a predefinição de 1,5. | Opcional. |
BackgroundColor| Cadeia| Especifica a cor do plano de fundo dos componentes da interface do usuário do SDK do Intune. Aceita uma cadeia RGB hexadecimal sob a forma de "#XXXXXX", sendo que X pode ir de 0 a 9 ou de A a F. O sinal de cardinal pode ser omitido.   | Opcional. O padrão é a cor do plano de fundo do sistema, que pode variar entre as versões do iOS e de acordo com a configuração de modo escuro do iOS. |
ForegroundColor| Cadeia| Especifica a cor de primeiro plano para os componentes de interface do usuário do SDK do Intune, como cor do texto. Aceita uma cadeia RGB hexadecimal sob a forma de "#XXXXXX", sendo que X pode ir de 0 a 9 ou de A a F. O sinal de cardinal pode ser omitido.  | Opcional. O padrão é a cor do rótulo do sistema, que pode variar entre as versões do iOS e de acordo com a configuração do modo escuro do iOS. |
AccentColor | Cadeia| Especifica a cor de destaque dos componentes da interface do usuário do SDK do Intune, como cor do texto do botão e cor de realce da caixa do PIN. Aceita uma cadeia RGB hexadecimal sob a forma de "#XXXXXX", sendo que X pode ir de 0 a 9 ou de A a F. O sinal de cardinal pode ser omitido.| Opcional. Assume a predefinição de azul de sistema. |
SupportsDarkMode| Booleano | Especifica se o esquema de cores da interface do usuário do SDK do Intune deve observar a configuração do modo escuro do sistema, se nenhum valor explícito tiver sido definido para BackgroundColor/ForegroundColor/AccentColor | Opcional. O padrão é sim. |
MAMTelemetryDisabled| Booleano| Especifica se o SDK não envia dados de telemetria de volta para o respetivo back-end.| Opcional. Assume a predefinição de NO. |
MAMTelemetryUsePPE | Booleano | Especifica se o SDK de MAM envia dados para o back-end de telemetria do PPE. Utilize esta opção ao testar as suas aplicações com a política do Intune, para que os dados de telemetria de teste não se misturem com os dados de clientes. | Opcional. Assume a predefinição de NO. |
MaxFileProtectionLevel | Cadeia | Opcional. Permite que a aplicação especifique o `NSFileProtectionType` máximo que pode suportar. Este valor irá substituir a política enviada pelo serviço se o nível for superior ao que a aplicação consegue suportar. Valores possíveis: `NSFileProtectionComplete`, `NSFileProtectionCompleteUnlessOpen`, `NSFileProtectionCompleteUntilFirstUserAuthentication`, `NSFileProtectionNone`.|
OpenInActionExtension | Booleano | Defina como YES para extensões de Ação Abrir em. Veja a secção Partilhar dados através de UIActivityViewController para obter mais informações. |
WebViewHandledURLSchemes | Matriz de Cadeias | Especifica os esquemas de URL processados pela WebView da sua aplicação. | Necessário se a sua aplicação utilizar uma WebView que processa URLs através de ligações e/ou javascript. |

## <a name="receive-app-protection-policy"></a>Receber a política de proteção de aplicações

### <a name="overview"></a>Overview

Para receber a política de proteção de aplicações do Intune, as aplicações têm de iniciar um pedido de inscrição com o serviço MAM do Intune. As aplicações podem ser configuradas na consola do Intune para obterem a política de proteção de aplicações, com ou sem a inscrição de dispositivos. A política de proteção de aplicações sem a inscrição de dispositivos, também conhecida como **APP-WE** ou MAM-WE, permite que as aplicações sejam geridas pelo Intune sem a necessidade de o dispositivo ser inscrito na gestão de dispositivos móveis (MDM) do Intune. Em ambos os casos, precisa da inscrição com o serviço MAM do Intune para receber a política.

> [!Important]
> O SDK de aplicativos do Intune para iOS usa chaves de criptografia de 256 bits quando a criptografia é habilitada pelas políticas de proteção de aplicativo. Todos os aplicativos precisarão ter uma versão atual do SDK para permitir o compartilhamento de dados protegidos.

### <a name="apps-that-already-use-adal-or-msal"></a>Aplicativos que já usam ADAL ou MSAL

Os aplicativos que já usam a ADAL ou MSAL devem chamar o método `registerAndEnrollAccount` na instância `IntuneMAMEnrollmentManager` depois que o usuário tiver sido autenticado com êxito:

```objc
/*
 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;
```

Ao chamar o método `registerAndEnrollAccount`, o SDK irá registar a conta de utilizador e tentar inscrever a aplicação em nome desta conta. Se a inscrição falhar por algum motivo, o SDK irá automaticamente voltar a tentar a inscrição após 24 horas. Para fins de depuração, a aplicação pode receber [notificações](#status-result-and-debug-notifications), através de um delegado, sobre os resultados de pedidos de inscrição.

Depois de esta API ser invocada, a aplicação pode continuar a funcionar normalmente. Se a inscrição for bem-sucedida, o SDK irá informar o utilizador de que é preciso reiniciar a aplicação. Nessa altura, o utilizador pode reiniciar a aplicação imediatamente.

```objc
[[IntuneMAMEnrollmentManager instance] registerAndEnrollAccount:@”user@foo.com”];
```

### <a name="apps-that-do-not-use-adal-or-msal"></a>Aplicativos que não usam ADAL ou MSAL

Os aplicativos que não entram no usuário usando a ADAL ou MSAL ainda podem receber a política de proteção do aplicativo do serviço de MAM do Intune chamando a API para que o SDK manipule essa autenticação. As aplicações devem utilizar esta técnica quando não tiverem autenticado um utilizador com o Azure AD, mas ainda precisam de obter a política de proteção de aplicações para ajudar a proteger dados. A título de exemplo, quando outro serviço de autenticação está a ser utilizado para início de sessão na aplicação ou a aplicação não suporta o início sessão em nenhuma situação. Para tal, a aplicação pode chamar o método `loginAndEnrollAccount` na instância `IntuneMAMEnrollmentManager`:

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;
```

Ao chamar este método, o SDK pedirá ao utilizador as credenciais se não encontrar nenhum token. O SDK tentará, em seguida, inscrever a aplicação com o serviço MAM do Intune em nome da conta do utilizador indicada. O método pode ser chamado com "nil" como identidade. Neste caso, o SDK será inscrito com o utilizador gerido existente no dispositivo (no caso da MDM) ou solicitará um nome de utilizador ao utilizador, se não for encontrado um utilizador existente.

Se a inscrição falhar, a aplicação deverá considerar chamar esta API novamente numa altura posterior, consoante os detalhes da falha. A aplicação pode receber [notificações](#status-result-and-debug-notifications), através de um delegado, sobre os resultados de pedidos de inscrição.

Depois de esta API ser invocada, a aplicação poderá continuar a funcionar normalmente. Se a inscrição for bem-sucedida, o SDK irá informar o utilizador de que é preciso reiniciar a aplicação.

Exemplo:

```objc
[[IntuneMAMEnrollmentManager instance] loginAndEnrollAccount:@”user@foo.com”];
```

### <a name="let-intune-handle-authentication-and-enrollment-at-launch"></a>Permitir que o Intune processe a autenticação e a inscrição na iniciação

Se você quiser que o SDK do Intune manipule toda a autenticação usando a ADAL/MSAL e o registro antes que seu aplicativo termine de ser iniciado e seu aplicativo sempre precise de uma política de aplicativo, você não precisará usar `loginAndEnrollAccount` API. Pode simplesmente configurar as duas definições abaixo como YES no dicionário IntuneMAMSettings no ficheiro Info.plist.

Definição  | Type  | Definition |
--       |  --   |   --       |  
AutoEnrollOnLaunch| Booleano| Especifica se a aplicação deve tentar inscrever-se automaticamente quando inicia se for detetada uma identidade gerida existente e ainda não o tiver feito. Assume a predefinição de NO. <br><br> Observação: se nenhuma identidade gerenciada for encontrada ou nenhum token válido para a identidade estiver disponível no cache ADAL/MSAL, a tentativa de registro falhará silenciosamente sem solicitar credenciais, a menos que o aplicativo também tenha definido MAMPolicyRequired como Sim. |
MAMPolicyRequired| Booleano| Especifica se a aplicação será impedida de iniciar se não tiver uma política de proteção de aplicação do Intune. Assume a predefinição de NO. <br><br> Nota: as aplicações não podem ser submetidas à App Store com a MAMPolicyRequired definida como YES. Ao definir a MAMPolicyRequired como YES, a AutoEnrollOnLaunch também deve ser definida como YES. |

Se escolher esta opção para a sua aplicação, não tem de processar o reinício da sua aplicação após a inscrição.

### <a name="deregister-user-accounts"></a>Anular o registo de contas de utilizadores

Para que a sessão de um utilizador numa aplicação seja terminada, a aplicação deverá anular o registo do utilizador a partir do SDK. Isto garante que:

1. Deixarão de ocorrer novas tentativas de inscrição na conta do utilizador.

2. A política de proteção de aplicações será removida.

3. Se a aplicação iniciar uma eliminação seletiva (opcional), todos os dados empresariais serão eliminados.

Antes de o utilizador terminar a sessão, a aplicação deve chamar o seguinte método na instância `IntuneMAMEnrollmentManager`:

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune APP AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */
(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

Este método tem de ser chamado antes de os tokens Azure AD da conta de utilizador serem eliminados. O SDK necessita do(s) token(s) do AAD da conta do utilizador para fazer pedidos específicos ao serviço MAM do Intune em nome do utilizador.

Se a aplicação eliminar os dados do utilizador empresariais automaticamente, o sinalizador `doWipe` poderá ser definido como falso. Caso contrário, a aplicação pode indicar ao SDK para iniciar uma eliminação seletiva. Isto resultará numa chamada para o delegado de eliminação seletiva da aplicação.

Exemplo:

```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

## <a name="status-result-and-debug-notifications"></a>Notificações de estado, de resultado e de depuração

A aplicação pode receber notificações de estado, de resultado e de depuração relativas aos seguintes pedidos ao serviço MAM do Intune:

* Pedidos de inscrição
* Pedidos de atualização da política
* Pedidos de anulação de inscrição

As notificações são apresentadas através de métodos de delegado no `IntuneMAMEnrollmentDelegate.h`:

```objc
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

Estes métodos delegados devolvem um objeto `IntuneMAMEnrollmentStatus` com as seguintes informações:

* A identidade da conta associada ao pedido
* Um código de estado que indica o resultado do pedido
* Cadeia de erro com uma descrição do código de estado
* Um objeto `NSError`. Este objeto é definido em `IntuneMAMEnrollmentStatus.h`, juntamente com os códigos de estado específicos que podem ser devolvidos.

### <a name="sample-code"></a>Código de exemplo

Estes são exemplos de implementações dos métodos delegados:

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}
```

## <a name="application-restart"></a>Reinício da aplicação

Quando uma aplicação receber políticas de MAM pela primeira vez, deve reiniciar para aplicar os hooks obrigatórios. Para notificar a aplicação de que é obrigatório reiniciar, o SDK disponibiliza um método delegado em `IntuneMAMPolicyDelegate.h`.

```objc
 - (BOOL) restartApplication
```

O valor deste método devolvido indica ao SDK se a aplicação terá de processar o reinício obrigatório:

* Se o valor devolvido for verdadeiro, a aplicação terá de processar o reinício.

* Se o valor devolvido for False, o SDK irá reiniciar a aplicação após este método ser devolvido. O SDK irá mostrar imediatamente uma caixa de diálogo que indica ao utilizador para reiniciar a aplicação.

## <a name="customize-your-apps-behavior-with-apis"></a>Personalizar o comportamento da sua aplicação com APIs

O SDK da Aplicação do Intune tem várias APIs que pode chamar para obter informações sobre a política APP aplicada à aplicação. Pode utilizar estes dados para personalizar o comportamento da sua aplicação. A tabela a seguir fornece informações sobre algumas classes essenciais do Intune que serão usadas.

Classe | Description
----- | -----------
IntuneMAMPolicyManager.h | A classe IntuneMAMPolicyManager expõe a política APP do Intune implementada na aplicação. Em particular, expõe as APIs que são úteis para [Ativar identidades múltiplas](app-sdk-ios.md#enable-multi-identity-optional). |
IntuneMAMPolicy.h | A classe IntuneMAMPolicy expõe algumas definições da política MAM que se aplicam à aplicação. Estas definições de política são expostas para que a aplicação possa personalizar a respetiva IU. A maioria das definições de política é imposta pelo SDK e não pela aplicação. A única que a aplicação deve implementar é o controlo de Guardar Como. Esta classe expõe algumas APIs necessárias para implementar o Guardar Como. |
IntuneMAMFileProtectionManager.h | A classe IntuneMAMFileProtectionManager expõe APIs que a aplicação pode utilizar para proteger explicitamente ficheiros e diretórios com base numa identidade fornecida. A identidade pode ser gerida pelo Intune ou pode não ser gerida e o SDK irá aplicar a política MAM adequada. A utilização desta classe é opcional. |
IntuneMAMDataProtectionManager.h | A classe IntuneMAMDataProtectionManager expõe APIs que a aplicação pode utilizar para proteger memórias intermédias de dados aos quais foram fornecidas identidades. A identidade pode ser gerida pelo Intune ou pode não ser gerida e o SDK irá aplicar a encriptação adequada. |

## <a name="implement-save-as-and-open-from-controls"></a>Implementar controles Save-as e Open-from

O Intune permite que os administradores de ti selecionem em quais locais de armazenamento um aplicativo gerenciado pode salvar dados ou abrir dados. Os aplicativos podem consultar o SDK do MAM do Intune em busca de locais de armazenamento permitidos para salvar em, usando a API `isSaveToAllowedForLocation`, definida em `IntuneMAMPolicy.h`. Os aplicativos também podem consultar o SDK do MAM do Intune para obter os locais de armazenamento permitidos abertos, usando a API `isOpenFromAllowedForLocation`, definida em `IntuneMAMPolicy.h`.

Antes de as aplicações poderem guardar dados geridos em localizações locais ou de armazenamento na cloud, estas têm de verificar a API `isSaveToAllowedForLocation` para saber se o administrador de TI permitiu que os dados fossem guardados nessas localizações.
Antes de abrir dados em um aplicativo de um armazenamento em nuvem ou local local, o aplicativo deve verificar com a API de `isOpenFromAllowedForLocation` para saber se o administrador de ti permitiu que os dados sejam abertos a partir daí.

Quando os aplicativos usam as APIs `isSaveToAllowedForLocation` ou `isOpenFromAllowedForLocation`, eles devem passar o UPN para o local de armazenamento, se ele estiver disponível.

### <a name="supported-save-locations"></a>Localizações para guardar suportadas

A API `isSaveToAllowedForLocation` disponibiliza constantes para verificar se o administrador de TI permite que os dados sejam guardados na seguintes localizações, definidas na `IntuneMAMPolicy.h`:

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive
* IntuneMAMSaveLocationAccountDocument

As aplicações devem utilizar as constantes na API `isSaveToAllowedForLocation` para verificar se os dados podem ser guardados em localizações consideradas "geridas," como o OneDrive para Empresas, ou "pessoais". Além disso, a API deve ser utilizada quando a aplicação não consegue determinar se uma localização é "gerida" ou "pessoal".

A constante `IntuneMAMSaveLocationLocalDrive` deve ser utilizada quando a aplicação guarda dados numa localização no dispositivo local.

Se a conta do local de destino for desconhecida, `nil` deverá ser passado. O local de `IntuneMAMSaveLocationLocalDrive` deve ser sempre emparelhado com uma conta de `nil`.

### <a name="supported-open-locations"></a>Locais abertos com suporte

A API de `isOpenFromAllowedForLocation` fornece constantes para verificar se o administrador de ti permite que os dados sejam abertos nos seguintes locais definidos em `IntuneMAMPolicy.h`.

* IntuneMAMOpenLocationOther
* IntuneMAMOpenLocationOneDriveForBusiness
* IntuneMAMOpenLocationSharePoint
* IntuneMAMOpenLocationCamera
* IntuneMAMOpenLocationLocalStorage
* IntuneMAMOpenLocationAccountDocument

Os aplicativos devem usar as constantes em `isOpenFromAllowedForLocation` para verificar se os dados podem ser abertos de locais considerados "gerenciados", como o OneDrive for Business ou "pessoal". Além disso, a API deve ser usada quando o aplicativo não pode verificar se um local é "gerenciado" ou "pessoal".

A constante `IntuneMAMOpenLocationCamera` deve ser usada quando o aplicativo estiver abrindo dados da câmera ou do álbum de fotos.

A constante `IntuneMAMOpenLocationLocalStorage` deve ser usada quando o aplicativo estiver abrindo dados de qualquer local no dispositivo local.

A constante `IntuneMAMOpenLocationAccountDocument` deve ser usada quando o aplicativo estiver abrindo um documento que tenha uma identidade de conta gerenciada (consulte a seção "dados compartilhados" abaixo)

Se a conta do local de origem for desconhecida, `nil` deverá ser passado. Os locais de `IntuneMAMOpenLocationLocalStorage` e `IntuneMAMOpenLocationCamera` devem ser sempre emparelhados com uma conta de `nil`.

### <a name="unknown-or-unlisted-locations"></a>Locais desconhecidos ou não listados

Quando o local desejado não estiver listado no `IntuneMAMSaveLocation` ou `IntuneMAMOpenLocation` enums ou for desconhecido, um dos dois locais deverá ser usado.
* Se o local de salvamento estiver sendo acessado com uma conta gerenciada, o local de `IntuneMAMSaveLocationAccountDocument` deverá ser usado (`IntuneMAMOpenLocationAccountDocument` para aberto).
* Caso contrário, use o local de `IntuneMAMSaveLocationOther` (`IntuneMAMOpenLocationOther` para aberto).

É importante fazer a distinção clara entre a conta gerenciada e uma conta que compartilha o UPN da conta gerenciada. Por exemplo, uma conta gerenciada com o UPN "user@contoso.com" conectado ao OneDrive não é a mesma que uma conta com o UPN "user@contoso.com" conectado ao dropbox. Se um serviço desconhecido ou não listado for acessado entrando na conta gerenciada (por exemplo, "user@contoso.com" conectado ao OneDrive), ele deverá ser representado pelo local do `AccountDocument`. Se o serviço desconhecido ou não listado entrar por meio de outra conta (por exemplo, "user@contoso.com" conectado ao dropbox), ele não está acessando o local com uma conta gerenciada e deve ser representado pelo local do `Other`.

### <a name="sharing-blocked-alert"></a>Compartilhamento de alertas bloqueados

Uma função auxiliar de interface do usuário pode ser usada quando a API `isSaveToAllowedForLocation` ou `isOpenFromAllowedForLocation` é chamada e encontrada para bloquear a ação salvar/abrir. Se o aplicativo quiser notificar o usuário de que a ação foi bloqueada, ele poderá chamar a API de `showSharingBlockedMessage` definida em `IntuneMAMUIHelper.h` apresentar um modo de exibição de alerta com uma mensagem genérica.

## <a name="share-data-via-uiactivityviewcontroller"></a>Partilhar dados através de UIActivityViewController

A partir da versão 8.0.2, o SDK da Aplicação do Intune poderá filtrar ações de `UIActivityViewController` para que apenas as localizações de partilha geridas pelo Intune estejam disponíveis para seleção. Este comportamento será controlado pela política de transferência de dados de aplicações.

### <a name="copy-to-actions"></a>Ações “Copiar Para”

Ao partilhar documentos através de `UIActivityViewController` e de `UIDocumentInteractionController`, o iOS apresenta as ações "Copiar para" para cada aplicação que suporte abrir o documento que está a ser partilhado. As aplicações declaram os tipos de documentos que suportam através da definição `CFBundleDocumentTypes` no ficheiro Info.plist. Este tipo de partilha já não estará disponível se a política proibir a partilha com aplicações não geridas. Em substituição, o utilizador terá de adicionar uma extensão de Ação que não faça parte da IU à aplicação e ligá-la ao SDK da Aplicação do Intune. A extensão de Ação é apenas um stub. O SDK implementará o comportamento de partilha de ficheiros. Siga os passos abaixo:

1. A aplicação tem de ter pelo menos um schemeURL definido nos `CFBundleURLTypes` de Info.plist.

2. A extensão da ação e a aplicação têm de partilhar pelo menos um Grupo de Aplicações e este tem de estar listado na matriz de `AppGroupIdentifiers` nos dicionários IntuneMAMSettings da extensão e da aplicação.

3. Atribua um nome à extensão da ação “Abrir em” seguido do nome da aplicação. Localize o ficheiro Info.plist conforme necessário.

4. Forneça um ícone de modelo para a extensão, conforme descrito no artigo [Apple’s developer documentation](https://developer.apple.com/ios/human-interface-guidelines/extensions/sharing-and-actions/)(Documentação do programador da Apple). Em alternativa, a ferramenta IntuneMAMConfigurator pode servir para gerar estas imagens do diretório .app da aplicação. Para fazê-lo, execute:

    ```bash
    IntuneMAMConfigurator -generateOpenInIcons /path/to/app.app -o /path/to/output/directory
    ```

5. Em IntuneMAMSettings, no ficheiro Info.plist da extensão, adicione uma definição Booleana denominada `OpenInActionExtension` com o valor YES.

6. Configure a `NSExtensionActivationRule` para que suporte um único ficheiro e todos os tipos de `CFBundleDocumentTypes` da aplicação com o prefixo `com.microsoft.intune.mam`. Por exemplo, se a aplicação suportar public.text e public.image, a regra de ativação será:

    ```objc
    SUBQUERY (
        extensionItems,
        $extensionItem,
        SUBQUERY (
            $extensionItem.attachments,
            $attachment,
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.text” ||
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image”).@count == 1
    ).@count == 1
    ```

### <a name="update-existing-share-and-action-extensions"></a>Atualizar extensões Partilhar e Ação existentes

Se a sua aplicação já tiver as extensões Partilhar ou Ação, a respetiva `NSExtensionActivationRule` terá de ser modificada para permitir os tipos do Intune. Para cada tipo suportado pela extensão, adicione um tipo com o prefixo `com.microsoft.intune.mam`. Por exemplo, se a regra de ativação existente for:  

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data"
    ).@count > 0
).@count > 0
```

Deverá ser alterada para:

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.data"
    ).@count > 0
).@count > 0
```

> [!NOTE]
> A ferramenta IntuneMAMConfigurator pode servir para adicionar os tipos do Intune à regra de ativação. Se a regra de ativação existente utilizar as constantes de cadeia predefinidas (por exemplo, NSExtensionActivationSupportsFileWithMaxCount NSExtensionActivationSupportsText, etc.), a sintaxe de predicado poderá ficar bastante complexa. A ferramenta IntuneMAMConfigurator também pode servir para converter a regra de ativação das constantes de cadeia para uma cadeia de predicado ao adicionar os tipos de Intune.

### <a name="what-the-ui-should-look-like"></a>O aspeto que a IU deve ter

Antiga IU:

![Compartilhando dados-interface do usuário de compartilhamento antigo do iOS](./media/app-sdk-ios/sharing-UI-old.png)

Nova IU:

![Compartilhando dados-nova interface do usuário de compartilhamento](./media/app-sdk-ios/sharing-UI-new.png)

## <a name="enable-targeted-configuration-appmam-app-config-for-your-ios-applications"></a>Permitir a configuração direcionada (configuração de aplicação APP/MAM) para as suas aplicações iOS

A configuração de MAM direcionada (também denominada configuração de aplicação MAM) permite que uma aplicação receba dados de configuração através do SDK do Intune. O formato e as variantes destes dados têm de ser definidos e comunicados aos clientes do Intune pelo proprietário/programador da aplicação.

Os administradores do Intune podem direcionar e implementar dados de configuração através do portal do Intune no Azure e do Graph API do Intune. A partir da versão 7.0.1 do SDK da Aplicação Intune para iOS, pode proporcionar dados de configuração de MAM direcionada às aplicações que participem na configuração de MAM direcionada através do Serviço MAM. Os dados de configuração de aplicações são emitidos através do nosso Serviço de MAM diretamente para a aplicação em vez de através do canal de MDM. O SDK da Aplicação Intune fornece uma classe para aceder aos dados obtidos através destas consolas. Os seguintes itens são pré-requisitos:

* A aplicação tem de estar inscrita com o serviço MAM do Intune para poder aceder à IU de configuração de MAM direcionada. Para obter mais informações, veja [Receber a política de proteção de aplicações](#receive-app-protection-policy).

* Inclua `IntuneMAMAppConfigManager.h` no ficheiro de origem da sua aplicação.

* Chame `[[IntuneMAMAppConfigManager instance] appConfigForIdentity:]` para apresentar o Objeto Configuração da Aplicação.

* Chame o seletor adequado no objeto `IntuneMAMAppConfig`. Por exemplo, se a chave da aplicação for uma cadeia, é aconselhável utilizar `stringValueForKey` ou `allStringsForKey`. Veja `IntuneMAMAppConfig.h` para obter uma descrição detalhada dos valores devolvidos e das condições de erro.

Para obter mais informações sobre as funcionalidades da Graph API, veja [Referência da Graph API](https://developer.microsoft.com/graph/docs/concepts/overview).

Para obter mais informações sobre como criar uma política de configuração de aplicações de MAM direcionada no iOS, veja a secção na configuração de aplicação de MAM direcionada em [Como utilizar políticas de configuração da aplicação Microsoft Intune para iOS](../apps/app-configuration-policies-use-ios.md).

## <a name="telemetry"></a>Telemetria

Por predefinição, o SDK da Aplicação do Intune para iOS recolhe dados telemétricos dos seguintes tipos de eventos:

* **Iniciação da aplicação**: para ajudar o Microsoft Intune a saber mais informações sobre a utilização de aplicações ativadas para MAM por tipo de gestão (MAM com MDM, MAM sem inscrição MDM, entre outros).

* **Chamadas de inscrição**: para ajudar o Microsoft Intune a conhecer a taxa de êxito e outras métricas de desempenho das chamadas de inscrição no lado do cliente.

* **Ações do Intune**: para ajudar a diagnosticar problemas e garantir a funcionalidade do Intune, recolhemos informações sobre as ações do SDK do Intune.

> [!NOTE]
> Se optar por não enviar os dados telemétricos do SDK da Aplicação Intune para o Microsoft Intune a partir da sua aplicação móvel, deve desativar a captura de telemetria do SDK da Aplicação Intune. Defina a propriedade `MAMTelemetryDisabled` como YES no dicionário IntuneMAMSettings.

## <a name="enable-multi-identity-optional"></a>Ativar identidades múltiplas (opcional)

Por predefinição, o SDK aplica a política à aplicação como um todo. As identidades múltiplas são uma funcionalidade de MAM que pode ativar para aplicar uma política por identidade. Esta opção requer uma maior participação da aplicação do que outras funcionalidades de MAM.

A aplicação deve informar ao SDK da aplicação quando tenciona alterar a identidade ativa. O SDK também notifica a aplicação quando for necessária uma alteração de identidade. Atualmente, apenas é suportada uma identidade gerida. Depois de o utilizador inscrever o dispositivo ou a aplicação, o SDK utiliza esta identidade e considera-a a identidade gerida primária. Os outros utilizadores na aplicação serão tratados como não geridos, com definições de política não restrita.

Note que uma identidade é simplesmente definida como uma cadeia. As identidades são sensíveis a maiúsculas e minúsculas. Os pedidos de identidade ao SDK podem não devolver a mesma utilização de maiúsculas e minúsculas que tinha sido originalmente utilizada quando a identidade foi definida.

### <a name="identity-overview"></a>Descrição geral de identidade

Uma identidade é apenas o nome de utilizador de uma conta (por exemplo, user@contoso.com). Os programadores podem definir a identidade da aplicação nos seguintes níveis:

* **Identidade de processo**: define a identidade em todo o processo e é maioritariamente utilizada em aplicações de identidade única. Esta identidade afeta todas as tarefas, os ficheiros e a IU.

* **Identidade da IU**: determina que políticas são aplicadas às tarefas de IU no thread principal, como cortar/copiar/colar, PIN, autenticação e partilha de dados. A identidade da IU não afeta as tarefas de ficheiros, tal como encriptação e cópia de segurança.

* **Identidade do thread**: afeta as políticas aplicadas ao thread atual. Esta identidade afeta todas as tarefas, os ficheiros e a IU.

A aplicação é responsável por definir as identidades de forma adequada, independentemente de o utilizador ser gerido ou não.

A qualquer altura, todos os threads têm uma identidade eficaz para tarefas de IU e tarefas de ficheiros. Esta é a identidade que serve para verificar que políticas devem ser aplicadas (se forem aplicadas políticas). Se a identidade for "no identity" ou se o utilizador não for gerido, não serão aplicadas políticas. Os diagramas abaixo mostram como são determinadas as identidades em vigor.

  ![SDK do Intune app para iOS: processo de determinação de identidade](./media/app-sdk-ios/ios-thread-identities.png)

### <a name="thread-queues"></a>Filas de threads

As aplicações emitem muitas vezes tarefas assíncronas e síncronas para filas de threads. O SDK interceta chamadas do Grand Central Dispatch (GCD) e associa a atual identidade do thread às tarefas emitidas. Quando as tarefas são concluídas, o SDK altera temporariamente a identidade do thread para a identidade associada às tarefas, conclui as tarefas e, em seguida, restaura a identidade do thread original.


Como o `NSOperationQueue` é criado sobre o GCD, o `NSOperations` será executado na identidade do thread na altura em que as tarefas são adicionadas ao `NSOperationQueue`. O `NSOperations` ou as funções emitidas diretamente através do GCD também podem alterar a identidade do thread atual durante a execução. Esta identidade substitui a identidade herdada do thread emissor.

### <a name="file-owner"></a>Proprietário do ficheiro

O SDK controla as identidades dos proprietários dos ficheiros locais e aplica as políticas de acordo com a mesma. Um proprietário do ficheiro é estabelecido quando um ficheiro é criado ou quando um ficheiro é aberto em modo truncado. O proprietário está definido para a identidade da tarefa do ficheiro efetiva do thread que executa a tarefa.

Em alternativa, as aplicações podem definir a identidade de proprietário do ficheiro explicitamente, ao utilizar o `IntuneMAMFilePolicyManager`. As aplicações podem utilizar o `IntuneMAMFilePolicyManager` para obter o proprietário do ficheiro e definir a identidade de IU antes de mostrarem os conteúdos dos ficheiros.

### <a name="shared-data"></a>Dados partilhados

Se a aplicação criar ficheiros com dados de utilizadores geridos e não geridos, é da responsabilidade da aplicação encriptar os dados do utilizador gerido. Pode encriptar dados com as APIs `protect` e `unprotect` no `IntuneMAMDataProtectionManager`.

O método `protect` aceita uma identidade que pode ser um utilizador gerido ou não gerido. Se o utilizador for gerido, os dados serão encriptados. Se o utilizador for não gerido, será adicionado um cabeçalho aos dados a codificar a identidade, mas os dados não serão encriptados. Pode utilizar o método `protectionInfo` para obter o proprietário dos dados.

### <a name="share-extensions"></a>Extensões de partilha

Se a aplicação tem uma extensão de partilha, o proprietário do item partilhado pode ser obtido com recurso ao método `protectionInfoForItemProvider` no `IntuneMAMDataProtectionManager`. Se o item partilhado for um ficheiro, o SDK processará a definição do proprietário do ficheiro. Se o item partilhado consistir em dados, a aplicação é responsável por definir o proprietário do ficheiro se estes dados forem persistentes num ficheiro e chamar a API `setUIPolicyIdentity` antes de mostrar estes dados na IU.

### <a name="turn-on-multi-identity"></a>Ativar múltiplas identidades

Por predefinição, as aplicações são consideradas de identidade única. O SDK define a identidade de processo para o utilizador inscrito. Para ativar o suporte de identidades múltiplas, adicione uma definição booleana com o nome `MultiIdentity` e um valor YES ao dicionário IntuneMAMSettings no ficheiro Info.plist da aplicação.

> [!NOTE]
> Quando as identidades múltiplas estiverem ativadas, as identidades de processo, de IU e de thread são definidas como nulas. A aplicação é responsável pela sua definição adequada.

### <a name="switch-identities"></a>Mudar de identidade

* **Mudança de identidade iniciada pela aplicação**:

    Ao iniciar, considera-se que as aplicações de identidades múltiplas estão a ser executadas numa conta desconhecida e não gerida. A IU de iniciação condicional não será executada e não serão aplicadas políticas na aplicação. A aplicação é responsável por notificar o SDK sempre que a identidade deva ser alterada. Normalmente, este processo ocorre sempre que a aplicação estiver prestes a mostrar os dados de uma conta de utilizador específica.

    Um exemplo desta situação é quando o utilizador tenta abrir um documento, uma caixa de correio ou um separador num bloco de notas. A aplicação tem de notificar o SDK antes que o ficheiro, a caixa de correio ou o separador sejam efetivamente abertos. Este processo é realizado através da API `setUIPolicyIdentity` no `IntuneMAMPolicyManager`. Esta API deve ser chamada quer o utilizador seja gerido ou não. Se o utilizador for gerido, o SDK irá executar as verificações de inicialização condicional, como deteção de jailbreak, PIN e autenticação.

    O resultado da mudança de identidade é devolvido à aplicação de forma assíncrona através de um processador de conclusão. A aplicação deverá adiar a abertura do documento, da caixa de correio ou do separador até que um código de resultado de sucesso seja devolvido. Se a mudança de identidade tiver falhado, a aplicação deverá cancelar a tarefa.

* **Mudança de identidade iniciada pelo SDK**:

    Por vezes, o SDK precisa de pedir à aplicação que mude para uma identidade específica. As aplicações de identidades múltiplas têm de implementar o método `identitySwitchRequired` no `IntuneMAMPolicyDelegate` para processar este pedido.

    Aquando da chamada deste método, se a aplicação conseguir processar o pedido de mudança para a identidade especificada, esta deverá passar o `IntuneMAMAddIdentityResultSuccess` para o processador de conclusão. Se não conseguir processar a mudança de identidade, a aplicação deverá passar o `IntuneMAMAddIdentityResultFailed` para o processador de conclusão.

    A aplicação não tem de chamar o `setUIPolicyIdentity` em resposta a esta chamada. Se o SDK necessitar da aplicação para mudar para uma conta de utilizador não gerida, a cadeia vazia será passada para a chamada do `identitySwitchRequired`.

* **Eliminação seletiva**:

    Quando for efetuada uma eliminação seletiva na aplicação, o SDK chamará o método `wipeDataForAccount` no `IntuneMAMPolicyDelegate`. A aplicação é responsável por remover a conta do utilizador especificado, bem como quaisquer dados associados à mesma. O SDK é capaz de remover todos os ficheiros do utilizador e realizará esta ação se a aplicação devolver FALSE da chamada do `wipeDataForAccount`.

    Tenha em atenção que este método é chamado a partir de um thread de segundo plano. A aplicação não deve devolver um valor até que todos os dados para o utilizador tenham sido removidos (com a exceção dos ficheiros, se a aplicação devolver FALSE).

## <a name="ios-best-practices"></a>Melhores práticas de iOS

Eis algumas melhores práticas recomendadas para desenvolver para iOS:

* O sistema de ficheiros iOS é sensível às maiúsculas e minúsculas. Confirme que as maiúsculas e minúsculas estão corretas nos nomes dos ficheiros, como `libIntuneMAM.a` e `IntuneMAMResources.bundle`.

* Se o Xcode tiver problemas a localizar `libIntuneMAM.a`, pode corrigir o problema ao adicionar o caminho a esta biblioteca nos caminhos de pesquisa do linker.

## <a name="faqs"></a>Perguntas mais Frequentes

### <a name="are-all-of-the-apis-addressable-through-native-swift-or-the-objective-c-and-swift-interoperability"></a>As APIs são todas endereçáveis através do Swift nativo ou da interoperabilidade do Objective-C e do Swift?

As APIs do SDK da Aplicação do Intune estão apenas no Objective-C e não suportam o Swift **nativo**. Precisa da interoperabilidade do Swift com o Objective-C.

### <a name="do-all-users-of-my-application-need-to-be-registered-with-the-app-we-service"></a>Todos os utilizadores da minha aplicação têm de estar registados no serviço APP-WE?

Não. De facto, apenas as contas do trabalho ou escolares devem ser registadas no SDK da Aplicação do Intune. As aplicações são responsáveis por determinar se uma conta é utilizada num contexto profissional ou escolar.

### <a name="what-about-users-that-have-already-signed-in-to-the-application-do-they-need-to-be-enrolled"></a>E os utilizadores que já iniciaram sessão na aplicação? Precisam de ser inscritos?

A aplicação é responsável por inscrever os utilizadores após terem sido autenticados com êxito. A aplicação é também responsável por inscrever quaisquer contas existentes que podem ter estado presentes antes de a aplicação possuir a funcionalidades MDM sem MAM.

Para tal, a aplicação deve utilizar o método `registeredAccounts:`. Este método devolve um NSDictionary com todas as contas registadas no serviço MAM do Intune. Se existirem contas na aplicação que não estejam na lista, a aplicação deverá registar e inscrever as respetivas contas através do `registerAndEnrollAccount:`.

### <a name="how-often-does-the-sdk-retry-enrollments"></a>Com que frequência é que o SDK volta a tentar inscrições?

O SDK volta a tentar automaticamente todas as inscrições anteriormente falhadas a cada 24 horas. O SDK realiza este procedimento para garantir que, se a organização de um utilizador tiver ativado o MAM após o utilizador ter iniciado sessão na aplicação, o utilizador será inscrito com êxito e receberá as políticas.

O SDK deixará de voltar a tentar quando detetar que um utilizador se inscreveu na aplicação com êxito. Isto deve-se ao facto de apenas um utilizador poder inscrever uma aplicação num determinado momento. Se a inscrição do utilizador for anulada, as novas tentativas começarão de novo no mesmo intervalo de 24 horas.

### <a name="why-does-the-user-need-to-be-deregistered"></a>Por que motivo tem o registo do utilizador de ser anulado?

O SDK realizará estas ações em segundo plano de forma periódica:

* Se a aplicação ainda não estiver inscrita, esta tentará inscrever todas as contas registadas de 24 em 24 horas.
* Se a aplicação estiver inscrita, o SDK irá procurar atualizações à política de MAM de 8 em 8 horas.

A anulação do registo de um utilizador notifica o SDK que o utilizador deixará de utilizar a aplicação e este pode parar qualquer um dos eventos periódicos da respetiva conta de utilizador. Também aciona uma anulação de inscrição da aplicação e eliminação seletiva, se for preciso.

### <a name="should-i-set-the-dowipe-flag-to-true-in-the-deregister-method"></a>Devo definir o sinalizador doWipe como True no método de anulação do registo?

Este método deve ser chamado antes de o utilizador terminar a sessão na aplicação.  Se os dados do utilizador forem eliminados da aplicação ao terminar a sessão, o `doWipe` pode ser definido como False. Contudo, se a aplicação não remover os dados do utilizador, `doWipe` deverá defini-lo como True, para que o SDK possa eliminar os dados.

### <a name="are-there-any-other-ways-that-an-application-can-be-un-enrolled"></a>Existem outras formas de anular o registo de uma aplicação?

Sim, o administrador de TI pode enviar um comando de eliminação seletiva para a aplicação. Esta ação vai anular o registo e anular a inscrição do utilizador e apagar os dados do utilizador. O SDK processa este cenário automaticamente e envia uma notificação através do método de delegação de anulação de inscrição.

### <a name="is-there-a-sample-app-that-demonstrates-how-to-integrate-the-sdk"></a>Existe uma aplicação de exemplo que demonstre como integrar o SDK?

Sim! Recentemente, renovámos a nossa aplicação de exemplo open source [Wagr para iOS](https://github.com/Microsoft/Wagr-Sample-Intune-iOS-App). Esta aplicação está ativada para a política de proteção de aplicações com o SDK da Aplicação do Intune.

### <a name="how-can-i-troubleshoot-my-app"></a>Como posso solucionar problemas do meu aplicativo?

O SDK do Intune para iOS 9.0.3 + dá suporte à capacidade de adicionar um console de diagnóstico no aplicativo móvel para testar políticas e registrar erros. `IntuneMAMDiagnosticConsole.h` define a interface da classe `IntuneMAMDiagnosticConsole`, que os desenvolvedores podem usar para exibir o console de diagnóstico do Intune. Isso permite que os usuários finais ou desenvolvedores durante o teste coletem e compartilhem logs do Intune para ajudar a diagnosticar qualquer problema que possa ter. Essa API é opcional para integradores.

## <a name="submit-your-app-to-the-app-store"></a>Envie a sua aplicação à App Store

Tanto a biblioteca estática como as compilações de estrutura do SDK da Aplicação do Intune são binários universais. Isto significa que têm código para todas as arquiteturas de dispositivo e simulador. A Apple rejeita as aplicações submetidas à App Store se estas tiverem código de simulador. Ao compilar com a biblioteca estática em compilações apenas de dispositivo, o linker retira o código de simulador automaticamente. Siga os passos abaixo para garantir que todo o código de simulador é removido antes de carregar a aplicação para a App Store.

1. Confirmar que o `IntuneMAM.framework` está no seu ambiente de trabalho.

2. Execute estes comandos:

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```

    O primeiro comando retira as arquiteturas de simulador do ficheiro DYLIB da estrutura. O segundo comando copia o ficheiro DYLIB apenas para dispositivo de volta para o diretório da estrutura.
