---
title: Guia para programadores do SDK da Aplicação do Microsoft Intune para iOS
description: O SDK da Aplicação do Microsoft Intune para iOS permite-lhe incorporar as políticas de proteção de aplicações do Intune (também conhecidas como políticas de APLICAÇÕES ou MAM) na sua aplicação iOS nativa.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4877920821b2471f752f9fdb8941e87576d937ba
ms.sourcegitcommit: 9c06d8071b9affeda32e367bfe85d89bc524ed0b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67413865"
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Guia para programadores do SDK da Aplicação do Microsoft Intune para iOS

> [!NOTE]
> Considere ler o artigo [Guia de Introdução ao SDK da Aplicação do Intune](app-sdk-get-started.md), que explica como preparar a integração em cada plataforma suportada.

O SDK da Aplicação do Microsoft Intune para iOS permite-lhe incorporar as políticas de proteção de aplicações do Intune (também conhecidas como políticas de APLICAÇÕES ou MAM) na sua aplicação iOS nativa. Uma aplicação preparada para MAM é uma aplicação que está integrada com o SDK da Aplicação do Intune. Os administradores de TI podem implementar políticas de proteção de aplicações na aplicação móvel quando o Intune está a gerir a aplicação de forma ativa.

## <a name="prerequisites"></a>Pré-requisitos

* Irá precisar de um computador Mac OS que execute o OS X 10.8.5 ou posterior e também tem o Xcode 9 ou posterior instalado.

* A aplicação tem de ser destinada ao iOS 10 ou superior.

* Consulte os [Termos de Licenciamento do SDK da Aplicação do Intune para iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS.pdf). Imprimir e guardar uma cópia dos termos de licenciamento nos seus registos. Ao transferir e utilizar o SDK da Aplicação do Intune para iOS, aceita esses termos de licenciamento.  Caso não aceite os termos, não deverá utilizar o software.

* Transfira os ficheiros para o SDK da Aplicação do Intune para iOS no [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios).

## <a name="whats-in-the-sdk-repository"></a>O que está no repositório do SDK

Os seguintes ficheiros são relevantes para as aplicações/extensões que não contém nenhum código Swift, ou que são compiladas com uma versão do Xcode antes 10.2:

* **IntuneMAM.framework**: A estrutura do SDK da aplicação Intune. Recomenda-se que ligue esta estrutura a sua aplicação de extensões para ativar a gestão de aplicações de cliente do Intune. No entanto, alguns desenvolvedores podem preferir os benefícios de desempenho da biblioteca estática. Consulte o seguinte.

* **libIntuneMAM.a**: A biblioteca estática do SDK da aplicação Intune. Os desenvolvedores podem optar por ligar à biblioteca estática em vez do framework. Uma vez que bibliotecas estáticas são incorporadas diretamente na aplicação/extensão binária no momento da compilação, há alguns benefícios de desempenho de tempo de inicialização para utilizar a biblioteca estática. No entanto, a integrá-los na sua aplicação é um processo mais complexo. Se a aplicação inclui nenhuma extensão, a biblioteca estática de ligação para a aplicação e as extensões irão resultar num tamanho de pacote de aplicação maior, como a biblioteca estática é incorporada no cada binário de aplicação/extensão. Usando a estrutura, aplicações e extensões podem partilhar o mesmo binário do SDK do Intune, resultando num tamanho mais pequeno de aplicação.

* **IntuneMAMResources.bundle**: Um pacote de recursos contém recursos que o SDK depende. O pacote de recursos é necessário apenas para aplicações que se integram à biblioteca estática (libintunemam.).

Os seguintes ficheiros são relevantes para as aplicações/extensões que contêm código Swift e são compiladas com o Xcode 10.2 +:

* **IntuneMAMSwift.framework**: A estrutura do Intune App SDK Swift. Essa estrutura contém todos os cabeçalhos para APIs que chamará a sua aplicação. Ligue esta estrutura a sua aplicação de extensões para ativar a gestão de aplicações de cliente do Intune.

* **IntuneMAMSwiftStub.framework**: A estrutura do Intune App SDK Swift Stub. Esta é uma dependência necessária de IntuneMAMSwift.framework que tem de associar aplicações/extensões.


Os seguintes ficheiros são relevantes para todas as aplicações/extensões do:

* **IntuneMAMConfigurator**: Uma ferramenta usada para configurar a aplicação ou ficheiro info. plist de extensão com as mínimo alterações necessárias na gestão do Intune. Consoante a funcionalidade da sua aplicação ou a extensão, poderá ter de fazer alterações manuais adicionais para o ficheiro info. plist.

* **Cabeçalhos**: Expõe as APIs do SDK de aplicação pública do Intune. Esses cabeçalhos estão incluídos nas estruturas IntuneMAM/IntuneMAMSwift, para que os desenvolvedores que consumam qualquer uma das estruturas não é necessário adicionar manualmente os cabeçalhos aos seus projetos. Os desenvolvedores que optar por ligar-se a biblioteca estática (libintunemam.) tem de incluir manualmente estes cabeçalhos no seu projeto.

Os seguintes ficheiros de cabeçalho incluem as APIs, tipos de dados e protocolos que o SDK da Aplicação Intune disponibiliza aos programadores:

    * IntuneMAMAppConfig.h
    * IntuneMAMAppConfigManager.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMDefs.h
    * IntuneMAMEnrollmentDelegate.h
    * IntuneMAMEnrollmentManager.h
    * IntuneMAMEnrollmentStatus.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMLogger.h
    * IntuneMAMPolicy.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMPolicyManager.h
    * IntuneMAMVersionInfo.h

Os programadores podem disponibilizar o conteúdo de todos os cabeçalhos anteriores ao importar o intunemam. H


## <a name="how-the-intune-app-sdk-works"></a>Como funciona o SDK da Aplicação do Intune

O objetivo do SDK da Aplicação do Intune para iOS consiste em adicionar capacidades de gestão para aplicações iOS com alterações de código mínimas. Menos as alterações de código menos tempo de comercialização, mas sem afetar a consistência e a estabilidade da sua aplicação móvel.


## <a name="build-the-sdk-into-your-mobile-app"></a>Criar o SDK na sua aplicação móvel

Para ativar o SDK da Aplicação do Intune, siga estes passos:

1. **Opção 1 - estrutura (recomendado)** : Se estiver a utilizar o Xcode 10.2 + e sua aplicação/extensão contém código Swift, ligue `IntuneMAMSwift.framework` e `IntuneMAMSwiftStub.framework` para o seu destino: Arraste `IntuneMAMSwift.framework` e `IntuneMAMSwiftStub.framework` para o **binários incorporados** lista destino do projeto.

    Caso contrário, vincular `IntuneMAM.framework` para o seu destino: Arraste `IntuneMAM.framework` para a lista **Binários Incorporados** do destino do projeto.

   > [!NOTE]
   > Se utilizar a estrutura, terá de retirar manualmente as arquiteturas do simulador da estrutura universal antes de submeter a sua aplicação à App Store. Veja [Enviar a aplicação à App Store](#submit-your-app-to-the-app-store) para obter mais detalhes.

   **Opção 2 - biblioteca estática**: Esta opção só está disponível para aplicações/extensões que não contém nenhum código Swift, ou que foram criadas com o Xcode < 10.2. Ligação para o `libIntuneMAM.a` biblioteca. Arraste a biblioteca `libIntuneMAM.a` para a lista **Estruturas e Bibliotecas Ligadas** do destino do projeto.

    ![SDK da Aplicação do Intune para iOS: estruturas e bibliotecas ligadas](./media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    Adicione `-force_load {PATH_TO_LIB}/libIntuneMAM.a` a qualquer um dos seguintes, substituindo `{PATH_TO_LIB}` pela localização do SDK da Aplicação do Intune:
   * O projeto `OTHER_LDFLAGS` definição de configuração da compilação.
   * A IU do Xcode **outros sinalizadores do Linker**.

     > [!NOTE]
     > Para localizar `PATH_TO_LIB`, selecione o ficheiro `libIntuneMAM.a` e escolha **Informações** a partir do menu **Ficheiro**. Copie e cole as informações **Onde** (o caminho) na secção **Geral** da janela **Informações**.

     Adicione o pacote de recursos `IntuneMAMResources.bundle` ao projeto arrastando o pacote de recursos em **Copiar Recursos do Pacote** em **Fases de Criação**.

     ![SDK da Aplicação do Intune para iOS: copiar recursos do pacote](./media/intune-app-sdk-ios-copy-bundle-resources.png)
     
2. Se tiver de chamar qualquer uma das APIs do Intune a partir do Swift, sua/extensão da aplicação tem de importar os cabeçalhos necessários do SDK do Intune através de um cabeçalho de bridging Objective-C. Se a sua aplicação/extensão já não inclui um cabeçalho de bridging Objective-C, pode especificar uma através da `SWIFT_OBJC_BRIDGING_HEADER` Criar definição de configuração ou a IU do Xcode **cabeçalho de Bridging Objective-C** campo. O cabeçalho de bridging deve ter um aspeto semelhante ao seguinte:

   ```objc
      #import <IntuneMAMSwift/IntuneMAM.h>
   ```
   
   Isso fará com que todas as Intune APIs do SDK disponíveis ao longo de todos os ficheiros de origem Swift sua/extensão da aplicação. 
   
    > [!NOTE]
    > * Pode optar por apenas ponte específicos SDK do Intune cabeçalhos para Swift, em vez do intunemam. H que abrange
    > * Dependendo do que biblioteca de framework/estática que tive integrado, o caminho para o ficheiro ou ficheiros de cabeçalho pode ser diferentes.
    > * Disponibilizar as APIs de SDK do Intune no Swift através de uma instrução de importação do módulo (ex: Importar IntuneMAMSwift) não é atualmente suportada. Com um cabeçalho de bridging Objective-C é a abordagem recomendada.
    
3. Adicione estas estruturas de iOS ao projeto:  
    * MessageUI.framework  
    * Security.framework  
    * MobileCoreServices.framework  
    * SystemConfiguration.framework  
    * libsqlite3.tbd  
    * libc++.tbd  
    * ImageIO.framework  
    * LocalAuthentication.framework  
    * AudioToolbox.framework  
    * QuartzCore.framework  
    * WebKit.framework

4. Ative a partilha de keychain (se não estiver já ativada) ao selecionar **Capacidades** no destino de cada projeto e ao ativar o comutador **Partilha de Keychain**. A partilha de keychain é necessária para avançar para o passo seguinte.

   > [!NOTE]
   > O perfil de aprovisionamento tem de suportar os novos valores de partilha de keychain. Os grupos de acesso de keychain devem suportar um caráter universal. Pode verificar isto abrindo o ficheiro. mobileprovision num editor de texto, procurando **keychain-access-groups**e assegurando que tem um caráter universal. Por exemplo:
   >  ```xml
   >  <key>keychain-access-groups</key>
   >  <array>
   >  <string>YOURBUNDLESEEDID.*</string>
   >  </array>
   >  ```

5. Depois de ativar a partilha de keychain, siga os passos para criar um grupo de acesso separado no qual o SDK da aplicação Intune serão armazenados os dados. Pode criar um grupo de acesso de keychain com a IU ou o ficheiro de elegibilidade. Se estiver a utilizar a interface do Usuário para criar o grupo de acesso de keychain, certifique-se seguir estes passos:

     a. Se a sua aplicação móvel não tiver qualquer keychain aceder grupos definidos, adicionar a aplicação do pacote ID como o **primeiro** grupo.
    
    b. Adicione o grupo de keychain partilhado `com.microsoft.intune.mam` aos seus grupos de acesso existentes. O SDK da Aplicação do Intune utiliza este grupo de acesso para armazenar dados.
    
    c. Adicione `com.microsoft.adalcache` aos grupos de acesso existentes.
    
        ![Intune App SDK iOS: keychain sharing](./media/intune-app-sdk-ios-keychain-sharing.png)
    
    d. Se estiver a editar diretamente o ficheiro de elegibilidade, em vez de utilizar a IU do Xcode mostrada acima para criar grupos de acesso de keychain, inclua o acesso de keychain no início com `$(AppIdentifierPrefix)` (o Xcode processa o ficheiro automaticamente). Por exemplo:
    
        - `$(AppIdentifierPrefix)com.microsoft.intune.mam`
        - `$(AppIdentifierPrefix)com.microsoft.adalcache`
    
        > [!NOTE]
        > An entitlements file is an XML file that is unique to your mobile application. It is used to specify special permissions and capabilities in your iOS app. If your app did not previously have an entitlements file, enabling keychain sharing (step 3) should have caused Xcode to generate one for your app. Ensure the app's bundle ID is the first entry in the list.

6. Inclua cada protocolo transmitido pela aplicação a `UIApplication canOpenURL` na matriz `LSApplicationQueriesSchemes` do ficheiro Info.plist da aplicação. Não se esqueça de guardar as alterações antes de prosseguir para o passo seguinte.

7. Se a sua aplicação ainda não utilizar o FaceID, garanta que a [chave Info.plist NSFaceIDUsageDescription](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW75) está configurada com uma mensagem predefinida. Isto é necessário para que o iOS possa informar o utilizador sobre como é que a aplicação pretende utilizar o FaceID. Uma definição de política de proteção de aplicações do Intune permite que o FaceID seja utilizado como um método para aceder a aplicações quando configurado pelo administrador de TI.

8. Utilize a ferramenta IntuneMAMConfigurator, incluída no [repositório do SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios), para concluir a configuração do ficheiro Info.plist da aplicação. A ferramenta tem três parâmetros:

   |Propriedade|Como a utilizar|
   |---------------|--------------------------------|
   |- i |  `<Path to the input plist>` |
   |- e | `<Path to the entitlements file>` |
   |- o |  (Opcional) `<Path to the output plist>` |

Se o parâmetro “-o” não for especificado, o ficheiro de entrada será modificado no local. A ferramenta é idempotent e deve ser executada novamente sempre que forem feitas alterações ao ficheiro Info.plist da aplicações ou tenham sido criadas elegibilidades. Deverá também transferir e executar a versão mais recente da ferramenta ao atualizar o SDK do Intune, caso os requisitos de configuração do ficheiro Info.plist tenham sido alterados na versão mais recente.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Configurar a Azure Active Directory Authentication Library (ADAL)

O SDK da Aplicação do Intune utiliza a [Azure Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-objc) para os cenários de autenticação e iniciação condicional. Também recorre à ADAL para registar a identidade do utilizador com o serviço MAM para uma gestão sem cenários de inscrição de dispositivos.

Normalmente, a ADAL requer que as aplicações sejam registadas no Azure Active Directory (AAD) e obtenham um ID exclusivo (ID de Cliente) e outros identificadores para garantir a segurança dos tokens concedidos à aplicação. Salvo especificação em contrário, o SDK da Aplicação do Intune utiliza valores de registo predefinidos quando contacta o Azure AD.  

Se a sua aplicação já utilizar a ADAL para autenticar os utilizadores, esta deverá utilizar os seus valores de registo existentes e substituir os valores predefinidos do SDK da Aplicação do Intune. Isto garante que os utilizadores não recebem um pedido de autenticação duas vezes (uma vez pelo SDK da Aplicação do Intune e uma vez pela aplicação).

Recomenda-se que a aplicação se ligue à [versão mais recente da ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) no ramo principal. Atualmente, o SDK da aplicação Intune utiliza o ramo de Mediador da ADAL para suportar as aplicações que necessitam de acesso condicional. (Estas aplicações, por conseguinte, dependem da aplicação Microsoft Authenticator.) Porém, o SDK ainda é compatível com o ramo principal da ADAL. Utilize o ramo que se destina à sua aplicação.

### <a name="link-to-adal-binaries"></a>Ligar aos binários da ADAL

Siga os passos abaixo para ligar a aplicação aos binários da ADAL:

1. Transfira a [Azure Active Directory Authentication Library (ADAL) para Objective-C](https://github.com/AzureAD/azure-activedirectory-library-for-objc) a partir do GitHub e siga as [instruções](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download) sobre como transferir a ADAL através de submódulos Git ou CocoaPods.

2. Adicione a estrutura da ADAL (opção 1) ou uma biblioteca estática (opção 2) ao seu projeto.

3. Se a sua aplicação não tiver nenhum grupo de acesso de keychain definido, adicione o ID do pacote da aplicação como primeiro grupo.

4. Ative o início de sessão único (SSO) da ADAL ao adicionar `com.microsoft.adalcache` aos grupos de acesso de keychain.

5. Caso esteja explicitamente a definir o grupo de keychain da cache partilhada da ADAL, certifique-se de que está definido como `<appidprefix>.com.microsoft.adalcache`. A ADAL define isto automaticamente, a menos que efetue uma substituição. Se quiser especificar um grupo de keychain personalizado para substituir `com.microsoft.adalcache`, especifique-o no ficheiro Info.plist, em IntuneMAMSettings, com a chave `ADALCacheKeychainGroupOverride`.

### <a name="configure-adal-settings-for-the-intune-app-sdk"></a>Configurar as definições da ADAL para o SDK da Aplicação do Intune

Se a aplicação já utilizar a ADAL para autenticação e tiver as suas próprias definições da ADAL, poderá forçar o SDK da Aplicação do Intune a utilizar as mesmas definições durante a autenticação no Azure Active Directory. Esta ação garante que a aplicação não solicita a autenticação ao utilizador duas vezes. Veja [Configurar as definições para o SDK da Aplicação do Intune](#configure-settings-for-the-intune-app-sdk) para obter mais informações sobre o preenchimento das seguintes informações:  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

Se a aplicação já utilizar a ADAL, as configurações seguintes são obrigatórias:

1. No ficheiro Info.plist do projeto, no dicionário **IntuneMAMSettings** com o nome de chave `ADALClientId`, especifique o ID de Cliente a utilizar nas chamadas da ADAL.

2. Também no dicionário **IntuneMAMSettings** com o nome de chave `ADALAuthority`, especifique a autoridade do Azure AD.

3. Também no dicionário **IntuneMAMSettings** com o nome de chave `ADALRedirectUri`, especifique o URI de redirecionamento a utilizar nas chamadas da ADAL. Em alternativa, pode especificar `ADALRedirectScheme` se o URI de redirecionamento da aplicação estiver no formato `scheme://bundle_id`.

Além disso, as aplicações podem substituir estas definições do Azure AD no runtime. Para tal, basta definir as propriedades `aadAuthorityUriOverride`, `aadClientIdOverride` e `aadRedirectUriOverride` na instância `IntuneMAMPolicyManager`.

4. Certifique-se de que são seguidos os passos para conceder permissões de aplicações para o serviço de política (aplicação) de proteção de aplicações de iOS. Utilize as instruções no [introdução ao Guia do SDK do Intune](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration) em "permitir o acesso a aplicações ao serviço de proteção de aplicações do Intune (opcional)".  

> [!NOTE]
> Para todas as definições que são estáticas e que não precisam de ser determinadas no runtime, recomenda-se a abordagem do ficheiro Info.plist. Os valores atribuídos às propriedades `IntuneMAMPolicyManager` têm precedência sobre quaisquer valores correspondentes especificados no ficheiro Info.plist e serão mantidos, mesmo depois de a aplicação ser reiniciada. O SDK continuará a utilizá-los para os registos da política até que a inscrição do utilizador seja anulada ou os valores sejam limpos ou alterados.

### <a name="if-your-app-does-not-use-adal"></a>Se a aplicação não utilizar a ADAL

Conforme mencionado acima, o SDK da Aplicação do Intune utiliza a [Azure Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-objc) (Biblioteca de Autenticação do Azure Active Directory) para os cenários de autenticação e iniciação condicional. Também recorre à ADAL para registar a identidade do utilizador com o serviço MAM para uma gestão sem cenários de inscrição de dispositivos. Se **a sua aplicação não utilizar a ADAL no seu próprio mecanismo de autenticação**, o SDK da Aplicação do Intune irá disponibilizar valores predefinidos para os parâmetros da ADAL e processar a autenticação no Azure AD. Não precisa de especificar nenhum valor para as definições da ADAL listadas acima. Caso exista, qualquer mecanismo de autenticação utilizado pela sua aplicação será apresentado para além das mensagens da ADAL. 

## <a name="configure-settings-for-the-intune-app-sdk"></a>Configurar as definições para o SDK da Aplicação do Intune

Pode utilizar o dicionário **IntuneMAMSettings** no ficheiro Info.plist da aplicação para preparar e configurar o SDK da Aplicação do Intune. Se o dicionário IntuneMAMSettings não estiver no ficheiro Info.plist, deverá criá-lo.

No dicionário IntuneMAMSettings, pode adicionar as seguintes definições suportadas para configurar o SDK da Aplicação do Intune.

Algumas destas definições podem ter sido abordadas nas secções anteriores e outras não são aplicáveis a todas as aplicações.

Definição  | Type  | Definição | Obrigatório?
--       |  --   |   --       |  --
ADALClientId  | Cadeia  | Identificador do cliente Azure AD da aplicação. | Necessário se a aplicação utilizar a ADAL. |
ADALAuthority | Cadeia | Autoridade do Azure AD da aplicação em utilização. Deve utilizar o seu ambiente onde foram configuradas contas do AAD. | Necessário se a aplicação utilizar a ADAL. Se este valor estiver ausente, será utilizado um valor predefinido do Intune.|
ADALRedirectUri  | Cadeia  | URI de redirecionamento do Azure AD da aplicação. | Se a aplicação utilizar a ADAL, o ADALRedirectUri ou o ADALRedirectScheme são necessários.  |
ADALRedirectScheme  | Cadeia  | O esquema de redirecionamento do Azure AD da aplicação. Pode ser utilizado em vez do ADALRedirectUri se o URI de redirecionamento da aplicação estiver no formato `scheme://bundle_id`. | Se a aplicação utilizar a ADAL, o ADALRedirectUri ou o ADALRedirectScheme são necessários. |
ADALLogOverrideDisabled | Booleano  | Especifica se o SDK encaminhará todos os registos da ADAL (incluindo chamadas da ADAL a partir da aplicação, caso existam) para o seu próprio ficheiro de registo. Assume a predefinição de NO. Definido como YES se a aplicação for definir a sua própria chamada de retorno de registo da ADAL. | Opcional. |
ADALCacheKeychainGroupOverride | Cadeia  | Especifica o grupo de keychain a utilizar para a cache da ADAL em vez de "com.microsoft.adalcache". Tenha em atenção que isto não tem o prefixo app-id. Será adicionado como prefixo à cadeia fornecida no tempo de execução. | Opcional. |
AppGroupIdentifiers | Matriz de cadeias  | Matriz de grupos de aplicações da secção de elegibilidade com.apple.security.application-groups. | Necessário se a aplicação utilizar grupos de aplicações. |
ContainingAppBundleId | Cadeia | Especifica o ID do pacote da aplicação que contém a extensão. | Necessário para as extensões de iOS. |
DebugSettingsEnabled| Booleano | Se for definido como YES, as políticas de teste no pacote de Definições podem ser aplicadas. As aplicações *não* devem ser fornecidas com esta definição ativada. | Opcional. Assume a predefinição de NO.|
MainNibFile <br> MainNibFile~ipad  | Cadeia  | Esta definição deve ter o nome de ficheiro nib principal da aplicação.  | Obrigatório se a aplicação definir MainNibFile no ficheiro Info.plist. |
MainStoryboardFile <br> MainStoryboardFile~ipad  | Cadeia  | Esta definição deve ter o nome de ficheiro de guião gráfico principal da aplicação. | Obrigatório se a aplicação definir UIMainStoryboardFile no ficheiro Info.plist. |
MAMPolicyRequired| Booleano| Especifica se a aplicação será impedida de iniciar se não tiver uma política APP do Intune. Assume a predefinição de NO. <br><br> Nota: Aplicações não podem ser submetidas para o Store da aplicação com a MAMPolicyRequired definida como YES. | Opcional. Assume a predefinição de NO.|
MAMPolicyWarnAbsent | Booleano| Especifica se a aplicação irá avisar o utilizador ao iniciar se a aplicação não tiver uma política APP do Intune. <br><br> Nota: Os utilizadores ainda poderão utilizar a aplicação sem política após ignorarem o aviso. | Opcional. Assume a predefinição de NO. |
MultiIdentity | Booleano| Especifica se a aplicação tem conhecimento de identidades múltiplas. | Opcional. Assume a predefinição de NO. |
SplashIconFile <br> SplashIconFile~ipad | Cadeia  | Especifica o ficheiro de ícone de ecrã inicial (arranque) do Intune. | Opcional. |
SplashDuration | Número | Quantidade mínima de tempo, em segundos, durante a qual será mostrado o ecrã de arranque do Intune na iniciação da aplicação. Assume a predefinição de 1,5. | Opcional. |
BackgroundColor| Cadeia| Especifica a cor de fundo para os ecrãs de arranque e de PIN. Aceita uma cadeia RGB hexadecimal sob a forma de "#XXXXXX", sendo que X pode ir de 0 a 9 ou de A a F. O sinal de cardinal pode ser omitido.   | Opcional. Assume a predefinição de cinzento claro. |
ForegroundColor| Cadeia| Especifica a cor de primeiro plano para os ecrãs PIN, como a cor do texto e de inicialização. Aceita uma cadeia RGB hexadecimal sob a forma de "#XXXXXX", sendo que X pode ir de 0 a 9 ou de A a F. O sinal de cardinal pode ser omitido.  | Opcional. Assume a predefinição de preto. |
AccentColor | Cadeia| Especifica a cor de destaque para o ecrã de PIN, como cor do texto em botões e caixa. Aceita uma cadeia RGB hexadecimal sob a forma de "#XXXXXX", sendo que X pode ir de 0 a 9 ou de A a F. O sinal de cardinal pode ser omitido.| Opcional. Assume a predefinição de azul de sistema. |
MAMTelemetryDisabled| Booleano| Especifica se o SDK não envia dados de telemetria de volta para o respetivo back-end.| Opcional. Assume a predefinição de NO. |
MAMTelemetryUsePPE | Booleano | Especifica se o SDK de MAM envia dados para o back-end de telemetria do PPE. Utilize esta opção ao testar as suas aplicações com a política do Intune, para que os dados de telemetria de teste não se misturem com os dados de clientes. | Opcional. Assume a predefinição de NO. |
MaxFileProtectionLevel | Cadeia | Opcional. Permite que a aplicação especifique o `NSFileProtectionType` máximo que pode suportar. Este valor irá substituir a política enviada pelo serviço se o nível for superior ao que a aplicação consegue suportar. Valores possíveis: `NSFileProtectionComplete`, `NSFileProtectionCompleteUnlessOpen`, `NSFileProtectionCompleteUntilFirstUserAuthentication`, `NSFileProtectionNone`.|
OpenInActionExtension | Booleano | Defina como YES para extensões de Ação Abrir em. Veja a secção Partilhar dados através de UIActivityViewController para obter mais informações. |
WebViewHandledURLSchemes | Matriz de Cadeias | Especifica os esquemas de URL processados pela WebView da sua aplicação. | Necessário se a sua aplicação utilizar uma WebView que processa URLs através de ligações e/ou javascript. |

## <a name="receive-app-protection-policy"></a>Receber a política de proteção de aplicações

### <a name="overview"></a>Descrição geral

Para receber a política de proteção de aplicações do Intune, as aplicações têm de iniciar um pedido de inscrição com o serviço MAM do Intune. As aplicações podem ser configuradas na consola do Intune para obterem a política de proteção de aplicações, com ou sem a inscrição de dispositivos. A política de proteção de aplicações sem a inscrição de dispositivos, também conhecida como **APP-WE** ou MAM-WE, permite que as aplicações sejam geridas pelo Intune sem a necessidade de o dispositivo ser inscrito na gestão de dispositivos móveis (MDM) do Intune. Em ambos os casos, precisa da inscrição com o serviço MAM do Intune para receber a política.

### <a name="apps-that-use-adal"></a>Aplicações que utilizam a ADAL

As aplicações que já utilizam a ADAL devem chamar o método `registerAndEnrollAccount` na instância `IntuneMAMEnrollmentManager` depois de o utilizador ser autenticado com êxito:

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

### <a name="apps-that-do-not-use-adal"></a>Aplicações que não utilizam a ADAL

As aplicações que não iniciam a sessão do utilizador através da ADAL podem receber uma política de proteção de aplicações do serviço MAM do Intune ao chamar a API para que o SDK processe essa autenticação. As aplicações devem utilizar esta técnica quando não tiverem autenticado um utilizador com o Azure AD, mas ainda precisam de obter uma política de proteção de aplicação para ajudar a proteger os dados. A título de exemplo, quando outro serviço de autenticação está a ser utilizado para início de sessão na aplicação ou a aplicação não suporta o início sessão em nenhuma situação. Para tal, a aplicação pode chamar o método `loginAndEnrollAccount` na instância `IntuneMAMEnrollmentManager`:

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

Se quiser que o SDK do Intune processe a inscrição e toda a autenticação através da ADAL antes de iniciar a sua aplicação e a sua aplicação exigir sempre uma política APP, não tem de utilizar a API `loginAndEnrollAccount`. Pode simplesmente configurar as duas definições abaixo como YES no dicionário IntuneMAMSettings no ficheiro Info.plist.

Definição  | Type  | Definição |
--       |  --   |   --       |  
AutoEnrollOnLaunch| Booleano| Especifica se a aplicação deve tentar inscrever-se automaticamente quando inicia se for detetada uma identidade gerida existente e ainda não o tiver feito. Assume a predefinição de NO. <br><br> Nota: Não se for encontrada nenhuma identidade gerida ou não um token válido está disponível na cache da ADAL, a tentativa de inscrição irá falhar automaticamente sem pedir credenciais, a menos que a aplicação também tenha definido a MAMPolicyRequired como YES. |
MAMPolicyRequired| Booleano| Especifica se a aplicação será impedida de iniciar se não tiver uma política de proteção de aplicação do Intune. Assume a predefinição de NO. <br><br> Nota: Aplicações não podem ser submetidas para o Store da aplicação com a MAMPolicyRequired definida como YES. Ao definir a MAMPolicyRequired como YES, a AutoEnrollOnLaunch também deve ser definida como YES. |

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

> [!NOTE]
> Estas informações são apenas para fins de depuração. Nenhuma lógica de negócio na sua aplicação deve ser baseada nestas notificações. Estas informações podem ser enviadas para um serviço de telemetria, para fins de depuração ou monitorização.

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

O SDK da Aplicação do Intune tem várias APIs que pode chamar para obter informações sobre a política APP aplicada à aplicação. Pode utilizar estes dados para personalizar o comportamento da sua aplicação. A tabela seguinte fornece informações sobre algumas classes essenciais do Intune que irá utilizar.

Classe | Descrição
----- | -----------
IntuneMAMPolicyManager.h | A classe IntuneMAMPolicyManager expõe a política APP do Intune implementada na aplicação. Em particular, expõe as APIs que são úteis para [Ativar identidades múltiplas](app-sdk-ios.md#enable-multi-identity-optional). |
IntuneMAMPolicy.h | A classe IntuneMAMPolicy expõe algumas definições da política MAM que se aplicam à aplicação. Estas definições de política são expostas para que a aplicação possa personalizar a respetiva IU. A maioria das definições de política é imposta pelo SDK e não pela aplicação. A única que a aplicação deve implementar é o controlo de Guardar Como. Esta classe expõe algumas APIs necessárias para implementar o Guardar Como. |
IntuneMAMFileProtectionManager.h | A classe IntuneMAMFileProtectionManager expõe APIs que a aplicação pode utilizar para proteger explicitamente ficheiros e diretórios com base numa identidade fornecida. A identidade pode ser gerida pelo Intune ou pode não ser gerida e o SDK irá aplicar a política MAM adequada. A utilização desta classe é opcional. |
IntuneMAMDataProtectionManager.h | A classe IntuneMAMDataProtectionManager expõe APIs que a aplicação pode utilizar para proteger memórias intermédias de dados aos quais foram fornecidas identidades. A identidade pode ser gerida pelo Intune ou pode não ser gerida e o SDK irá aplicar a encriptação adequada. |

## <a name="implement-save-as-controls"></a>Implementar controlos de guardar como

O Intune permite que os administradores de TI selecionem as localizações de armazenamento onde uma aplicação gerida pode guardar dados. As aplicações podem consultar o SDK da Aplicação do Intune para obter as localizações de armazenamento através da API `isSaveToAllowedForLocation` definida na `IntuneMAMPolicy.h`.

Antes de as aplicações poderem guardar dados geridos em localizações locais ou de armazenamento na cloud, estas têm de verificar a API `isSaveToAllowedForLocation` para saber se o administrador de TI permitiu que os dados fossem guardados nessas localizações.

Quando as aplicações utilizam a API `isSaveToAllowedForLocation`, estas têm de introduzir o UPN para a localização de armazenamento, se o mesmo estiver disponível.

### <a name="supported-save-locations"></a>Localizações para guardar suportadas

A API `isSaveToAllowedForLocation` disponibiliza constantes para verificar se o administrador de TI permite que os dados sejam guardados na seguintes localizações, definidas na `IntuneMAMPolicy.h`:

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

As aplicações devem utilizar as constantes na API `isSaveToAllowedForLocation` para verificar se os dados podem ser guardados em localizações consideradas "geridas," como o OneDrive para Empresas, ou "pessoais". Além disso, a API deve ser utilizada quando a aplicação não consegue determinar se uma localização é "gerida" ou "pessoal".

As localizações reconhecidas como "pessoais" são representadas pela constante `IntuneMAMSaveLocationOther`.

A constante `IntuneMAMSaveLocationLocalDrive` deve ser utilizada quando a aplicação guarda dados numa localização no dispositivo local.

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
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.data
    ).@count > 0
).@count > 0
```

> [!NOTE]
> A ferramenta IntuneMAMConfigurator pode servir para adicionar os tipos do Intune à regra de ativação. Se a regra de ativação existente utilizar as constantes de cadeia predefinidas (por exemplo, NSExtensionActivationSupportsFileWithMaxCount NSExtensionActivationSupportsText, etc.), a sintaxe de predicado poderá ficar bastante complexa. A ferramenta IntuneMAMConfigurator também pode servir para converter a regra de ativação das constantes de cadeia para uma cadeia de predicado ao adicionar os tipos de Intune.

### <a name="what-the-ui-should-look-like"></a>O aspeto que a IU deve ter

Antiga IU:

![Partilha de dados - antigo da interface do Usuário de partilha do iOS](./media/sharing-UI-old.png)

Nova IU:

![Partilha de dados - nova interface do Usuário de partilha do iOS](./media/sharing-UI-new.png)

## <a name="enable-targeted-configuration-appmam-app-config-for-your-ios-applications"></a>Permitir a configuração direcionada (configuração de aplicação APP/MAM) para as suas aplicações iOS

A configuração de MAM direcionada (também denominada configuração de aplicação MAM) permite que uma aplicação receba dados de configuração através do SDK do Intune. O formato e as variantes destes dados têm de ser definidos e comunicados aos clientes do Intune pelo proprietário/programador da aplicação.

Os administradores do Intune podem direcionar e implementar dados de configuração através do portal do Intune no Azure e do Graph API do Intune. A partir da versão 7.0.1 do SDK da Aplicação Intune para iOS, pode proporcionar dados de configuração de MAM direcionada às aplicações que participem na configuração de MAM direcionada através do Serviço MAM. Os dados de configuração de aplicações são emitidos através do nosso Serviço de MAM diretamente para a aplicação em vez de através do canal de MDM. O SDK da Aplicação Intune fornece uma classe para aceder aos dados obtidos através destas consolas. Os seguintes itens são pré-requisitos:

* A aplicação tem de estar inscrita com o serviço MAM do Intune para poder aceder à IU de configuração de MAM direcionada. Para obter mais informações, veja [Receber a política de proteção de aplicações](#receive-app-protection-policy).

* Inclua `IntuneMAMAppConfigManager.h` no ficheiro de origem da sua aplicação.

* Chame `[[IntuneMAMAppConfigManager instance] appConfigForIdentity:]` para apresentar o Objeto Configuração da Aplicação.

* Chame o seletor adequado no objeto `IntuneMAMAppConfig`. Por exemplo, se a chave da aplicação for uma cadeia, é aconselhável utilizar `stringValueForKey` ou `allStringsForKey`. Veja `IntuneMAMAppConfig.h` para obter uma descrição detalhada dos valores devolvidos e das condições de erro.

Para obter mais informações sobre as funcionalidades da Graph API, veja [Referência da Graph API](https://developer.microsoft.com/graph/docs/concepts/overview).

Para obter mais informações sobre como criar uma política de configuração de aplicações de MAM direcionada no iOS, veja a secção na configuração de aplicação de MAM direcionada em [Como utilizar políticas de configuração da aplicação Microsoft Intune para iOS](https://docs.microsoft.com/intune/app-configuration-policies-use-ios).

## <a name="telemetry"></a>Telemetria

Por predefinição, o SDK da Aplicação do Intune para iOS recolhe dados telemétricos dos seguintes tipos de eventos:

* **Iniciação da aplicação**: Para ajudar a Microsoft Intune a saber mais sobre a utilização de aplicações ativadas para MAM por tipo de gestão (MAM com MDM), a MAM sem inscrição MDM e assim por diante.

* **Inscrição chamadas**: Para ajudar a saber mais sobre a taxa de êxito e outras métricas de desempenho das chamadas de inscrição do lado do cliente do Microsoft Intune.

* **Ações do Intune**: Para ajudar a diagnosticar problemas e certifique-se de funcionalidades do Intune, recolhemos informações sobre as ações do SDK do Intune.

> [!NOTE]
> Se optar por não enviar os dados telemétricos do SDK da Aplicação do Intune para o Microsoft Intune a partir da sua aplicação móvel, deve desativar a captura de telemetria do SDK da Aplicação do Intune. Defina a propriedade `MAMTelemetryDisabled` como YES no dicionário IntuneMAMSettings.

## <a name="enable-multi-identity-optional"></a>Ativar identidades múltiplas (opcional)

Por predefinição, o SDK aplica a política à aplicação como um todo. As identidades múltiplas são uma funcionalidade de MAM que pode ativar para aplicar uma política por identidade. Esta opção requer uma maior participação da aplicação do que outras funcionalidades de MAM.

A aplicação deve informar ao SDK da aplicação quando tenciona alterar a identidade ativa. O SDK também notifica a aplicação quando for necessária uma alteração de identidade. Atualmente, apenas é suportada uma identidade gerida. Depois de o utilizador inscrever o dispositivo ou a aplicação, o SDK utiliza esta identidade e considera-a a identidade gerida primária. Os outros utilizadores na aplicação serão tratados como não geridos, com definições de política não restrita.

Note que uma identidade é simplesmente definida como uma cadeia. As identidades são sensíveis a maiúsculas e minúsculas. Os pedidos de identidade ao SDK podem não devolver a mesma utilização de maiúsculas e minúsculas que tinha sido originalmente utilizada quando a identidade foi definida.

### <a name="identity-overview"></a>Descrição geral de identidade

Uma identidade é apenas o nome de utilizador de uma conta (por exemplo, user@contoso.com). Os programadores podem definir a identidade da aplicação nos seguintes níveis:

* **Identidade de processo**: Define a identidade de todo o processo e é maioritariamente utilizada em aplicações de identidade única. Esta identidade afeta todas as tarefas, os ficheiros e a IU.

* **Identidade da IU**: Determina que políticas são aplicadas às tarefas de IU no thread principal, como cortar/copiar/colar, PIN, autenticação e partilha de dados. A identidade da IU não afeta as tarefas de ficheiros, tal como encriptação e cópia de segurança.

* **Identidade do thread**: Afeta que políticas são aplicadas ao thread atual. Esta identidade afeta todas as tarefas, os ficheiros e a IU.

A aplicação é responsável por definir as identidades de forma adequada, independentemente de o utilizador ser gerido ou não.

A qualquer altura, todos os threads têm uma identidade eficaz para tarefas de IU e tarefas de ficheiros. Esta é a identidade que serve para verificar que políticas devem ser aplicadas (se forem aplicadas políticas). Se a identidade for "no identity" ou se o utilizador não for gerido, não serão aplicadas políticas. Os diagramas abaixo mostram como são determinadas as identidades em vigor.

  ![SDK da aplicação Intune para iOS: Processo de determinação de identidade](./media/ios-thread-identities.png)

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

Se a aplicação tem uma extensão de partilha, o proprietário do item partilhado pode ser obtido com recurso ao método `protectionInfoForItemProvider` no `IntuneMAMDataProtectionManager`. Se o item partilhado for um ficheiro, o SDK irá processar a definição do proprietário do ficheiro. Se o item partilhado consistir em dados, a aplicação é responsável por definir o proprietário do ficheiro se estes dados forem persistentes num ficheiro e chamar a API `setUIPolicyIdentity` antes de mostrar estes dados na IU.

### <a name="turn-on-multi-identity"></a>Ativar múltiplas identidades

Por predefinição, as aplicações são consideradas de identidade única. O SDK define a identidade de processo para o utilizador inscrito. Para ativar o suporte de identidades múltiplas, adicione uma definição booleana com o nome `MultiIdentity` e um valor YES ao dicionário IntuneMAMSettings no ficheiro Info.plist da aplicação.

> [!NOTE]
> Quando as identidades múltiplas estiverem ativadas, as identidades de processo, de IU e de thread são definidas como nulas. A aplicação é responsável pela sua definição adequada.

### <a name="switch-identities"></a>Mudar de identidade

* **Mudança de identidade iniciada pela aplicação**:

    Ao iniciar, considera-se que as aplicações de identidades múltiplas estão a ser executadas numa conta desconhecida e não gerida. A IU de inicialização condicional não será executada e não serão aplicadas políticas na aplicação. A aplicação é responsável por notificar o SDK sempre que a identidade deva ser alterada. Normalmente, este processo ocorre sempre que a aplicação estiver prestes a mostrar os dados de uma conta de utilizador específica.

    Um exemplo desta situação é quando o utilizador tenta abrir um documento, uma caixa de correio ou um separador num bloco de notas. A aplicação tem de notificar o SDK antes que o ficheiro, a caixa de correio ou o separador sejam efetivamente abertos. Este processo é realizado através da API `setUIPolicyIdentity` no `IntuneMAMPolicyManager`. Esta API deve ser chamada quer o utilizador seja gerido ou não. Se o utilizador for gerido, o SDK irá executar as verificações de inicialização condicional, como deteção de jailbreak, PIN e autenticação.

    O resultado da mudança de identidade é devolvido à aplicação de forma assíncrona através de um processador de conclusão. A aplicação deverá adiar a abertura do documento, da caixa de correio ou do separador até que um código de resultado de sucesso seja devolvido. Se a mudança de identidade tiver falhado, a aplicação deverá cancelar a tarefa.

* **Mudança de identidade iniciada pelo SDK**:

    Por vezes, o SDK precisa de pedir à aplicação que mude para uma identidade específica. As aplicações de identidades múltiplas têm de implementar o método `identitySwitchRequired` no `IntuneMAMPolicyDelegate` para processar este pedido.

    Aquando da chamada deste método, se a aplicação conseguir processar o pedido de mudança para a identidade especificada, esta deverá passar o `IntuneMAMAddIdentityResultSuccess` para o processador de conclusão. Se não conseguir processar a mudança de identidade, a aplicação deverá passar o `IntuneMAMAddIdentityResultFailed` para o processador de conclusão.

    A aplicação não tem de chamar o `setUIPolicyIdentity` em resposta a esta chamada. Se o SDK necessitar da aplicação para mudar para uma conta de utilizador não gerida, a cadeia vazia será passada para a chamada do `identitySwitchRequired`.

* **Eliminação seletiva**:

    Quando uma eliminação seletiva for efetuada na aplicação, o SDK irá ligar para o método `wipeDataForAccount` no `IntuneMAMPolicyDelegate`. A aplicação é responsável por remover a conta do utilizador especificado, bem como quaisquer dados associados à mesma. O SDK é capaz de remover todos os ficheiros do utilizador e realizará esta ação se a aplicação devolver FALSE da chamada do `wipeDataForAccount`.

    Tenha em atenção que este método é chamado a partir de um thread de segundo plano. A aplicação não deve devolver um valor até que todos os dados para o utilizador tenham sido removidos (com a exceção dos ficheiros, se a aplicação devolver FALSE).

## <a name="ios-best-practices"></a>Melhores práticas de iOS

Eis algumas melhores práticas recomendadas para desenvolver para iOS:

* O sistema de ficheiros iOS é sensível às maiúsculas e minúsculas. Confirme que as maiúsculas e minúsculas estão corretas nos nomes dos ficheiros, como `libIntuneMAM.a` e `IntuneMAMResources.bundle`.

* Se o Xcode tiver problemas a localizar `libIntuneMAM.a`, pode corrigir o problema ao adicionar o caminho a esta biblioteca nos caminhos de pesquisa do linker.

## <a name="faqs"></a>FAQs

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
