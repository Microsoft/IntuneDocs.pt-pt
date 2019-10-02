---
title: Enlaces Xamarin do SDK da Aplicação Microsoft Intune
description: Os Enlaces Xamarin do SDK da Aplicação Intune ativam a política de proteção de aplicações do Intune em aplicações iOS e Android criadas com o Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: de367f28f3f1c7731e5ab67d904aec799925cc03
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730300"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Enlaces Xamarin do SDK da Aplicação Microsoft Intune

> [!NOTE]
> Pode ler primeiro o artigo [Introdução ao SDK da Aplicação Intune](app-sdk-get-started.md), que explica como preparar a integração em cada plataforma suportada.

## <a name="overview"></a>Descrição geral
Os [Enlaces Xamarin do SDK da Aplicação Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) ativam a [política de proteção de aplicações do Intune](../apps/app-protection-policy.md) em aplicações iOS e Android criadas com o Xamarin. Os enlacem permitem aos programadores criar facilmente funcionalidades de proteção de aplicações do Intune na respetiva aplicação baseada no Xamarin.

Os Enlaces Xamarin do SDK da Aplicação Microsoft Intune permitem-lhe incorporar as políticas de proteção de aplicações do Intune (também conhecidas como políticas de APLICAÇÕES ou MAM) nas suas aplicações desenvolvidas com o Xamarin. Uma aplicação preparada para MAM é uma aplicação que está integrada com o SDK da Aplicação do Intune. Os administradores de TI podem implementar políticas de proteção de aplicações na aplicação móvel quando o Intune está a gerir a aplicação de forma ativa.

## <a name="whats-supported"></a>O que é suportado?

### <a name="developer-machines"></a>Máquinas do programador
* Windows (versão Visual Studio 15.7+)
* macOS

### <a name="mobile-app-platforms"></a>Plataformas de aplicações móveis
* Android
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Cenários de Gestão de Aplicações Móveis do Intune

* Intune APP-WE (sem a inscrição de dispositivos)
* Dispositivos inscritos na MDM do Intune
* Dispositivos inscritos na EMM de terceiros

As aplicações Xamarin criadas com os Enlaces Xamarin do SDK da Aplicação Intune podem agora receber políticas de proteção de aplicações do Intune em dispositivos inscritos na gestão de dispositivos móveis (MDM) do Intune e em dispositivos não inscritos.

## <a name="prerequisites"></a>Pré-requisitos

Reveja os [termos de licenciamento](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf). Imprimir e guardar uma cópia dos termos de licenciamento nos seus registos. Ao transferir e utilizar os Enlaces Xamarin do SDK da Aplicação Intune, aceita esses termos de licenciamento. Caso não aceite os termos, não deverá utilizar o software.

O SDK do Intune depende de [biblioteca de autenticação do Active Directory (Adal)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) para seus cenários de inicialização condicional e [autenticação](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) , que exigem que os aplicativos sejam configurados com [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). 

Se seu aplicativo já estiver configurado para usar a ADAL ou MSAL e tiver sua própria ID de cliente personalizada usada para autenticar com Azure Active Directory, verifique se as etapas para conceder as permissões do aplicativo Xamarin ao serviço de gerenciamento de aplicativo móvel (MAM) do Intune estão subsequente. Use as instruções na seção "[fornecer ao seu aplicativo acesso ao serviço de proteção de aplicativo do Intune](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)" do [Guia de introdução ao SDK do Intune](app-sdk-get-started.md).



## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Ativar as políticas de proteção de aplicações do Intune na sua aplicação móvel iOS
1. Adicione o [pacote NuGet Microsoft.Intune.MAM.Xamarin.iOS](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) ao seu projeto Xamarin.iOS.
2. Siga os passos gerais necessários para integrar o SDK da Aplicação Intune numa aplicação móvel iOS. Pode começar com o passo 3 das instruções de integração do [Guia para Programadores do SDK da Aplicação Intune para iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). Pode ignorar o passo final na secção na qual executa o IntuneMAMConfigurator, sendo que esta ferramenta está incluída no pacote Microsoft.Intune.MAM.Xamarin.iOS e será executada automaticamente aquando a compilação.
    **Importante**: Habilitar o compartilhamento de conjunto de chaves para um aplicativo é um pouco diferente no Visual Studio do Xcode. Abra a plist de Elegibilidade da aplicação e garanta que a opção “Ativar Keychain” está ativada e que são adicionados os grupos de partilha de keychain adequados nessa secção. Em seguida, garanta que a plist de Elegibilidade está especificada no campo “Elegibilidades Personalizadas” das opções “Assinatura de Pacotes iOS” do projeto para todas as combinações de Configuração/Plataforma adequadas.
3. Após os enlaces serem adicionados e a aplicação estar configurada corretamente, a sua aplicação pode começar a utilizar as APIs do SDK do Intune. Para tal, tem de incluir o seguinte espaço de nomes:

      ```csharp
      using Microsoft.Intune.MAM;
      ```

4. Para começar a receber políticas de proteção de aplicações, tem de inscrever a aplicação no serviço do Intune MAM. Se a sua aplicação não utilizar a [Biblioteca de Autenticação do Azure Active Directory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) nem a [Biblioteca de Autenticação da Microsoft](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) para autenticar utilizadores e quiser que o SDK do Intune processe a autenticação, a sua aplicação deve fornecer o UPN do utilizador ao método LoginAndEnrollAccount de IntuneMAMEnrollmentManager:

      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

      As aplicações poderão transmitir "nulo" se o UPN do utilizador for desconhecido no momento da chamada. Neste caso, pedir-se-á aos utilizadores para introduzirem o respetivo endereço de e-mail e palavra-passe.
      
      Se a sua aplicação já utilizar a ADAL ou a MSAL para autenticar utilizadores, pode configurar uma experiência de início de sessão único (SSO) entre a aplicação e o SDK do Intune. Em primeiro lugar, terá de configurar a ADAL/MSAL para armazenar tokens no mesmo grupo de acesso de keychain utilizado pelos Enlaces Xamarin do Intune para iOS (com.microsoft.adalcache). Para a ADAL, você pode fazer isso [definindo a propriedade iOSKeychainSecurityGroup de AuthenticationContext](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/iOS-Keychain-Access). Para MSAL, você precisará [definir a propriedade iOSKeychainSecurityGroup de PublicClientApplication](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/Xamarin-iOS-specifics#enable-keychain-access). Em seguida, terá de substituir as predefinições do AAD utilizadas pelo SDK do Intune pelas da sua aplicação. Pode fazê-lo através do dicionário IntuneMAMSettings no ficheiro Info.plist da aplicação, tal como mencionado no [Guia para Programadores do SDK da Aplicação Intune para iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk), ou pode utilizar as propriedades de substituição do AAD da instância IntuneMAMPolicyManager. A abordagem do ficheiro Info.plist é recomendada para aplicações cujas definições da ADAL sejam estáticas, enquanto as propriedades de substituição são recomendadas para aplicações que determinem esses valores no runtime. Depois de configurar todas as definições do SSO, a sua aplicação deve fornecer o UPN do utilizador ao método RegisterAndEnrollAccount de IntuneMAMEnrollmentManager após a autenticação bem-sucedida:

      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```

      As aplicações podem determinar o resultado de uma tentativa de inscrição ao implementar o método EnrollmentRequestWithStatus numa subclasse de IntuneMAMEnrollmentDelegate e ao definir a propriedade Delegate do IntuneMAMEnrollmentManager para uma instância dessa classe. 

      Após uma inscrição bem-sucedida, as aplicações podem determinar o UPN da conta inscrita (se este fosse previamente desconhecido) ao consultar a seguinte propriedade: 

      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
### <a name="sample-applications"></a>Aplicativos de exemplo
Aplicativos de exemplo destacando a funcionalidade de MAM em aplicativos Xamarin. iOS estão disponíveis no [GitHub](https://github.com/msintuneappsdk/sample-intune-xamarin-ios).

> [!NOTE] 
> Não há nenhum remapeamento para iOS. A integração numa aplicação Xamarin.Forms deve ser igual à de um projeto normal Xamarin.iOS. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Ativar as políticas de proteção de aplicações do Intune na sua aplicação móvel para Android
1. Adicione o [pacote NuGet Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) ao seu projeto Xamarin.Android.
    1. Para um aplicativo Xamarin. Forms, adicione o [pacote NuGet Microsoft. Intune. Mam. remapper. Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) ao seu projeto Xamarin. Android também. 
2. Siga as etapas gerais necessárias para [integrar o SDK de aplicativo do Intune](app-sdk-android.md) em um aplicativo móvel Android ao fazer referência a este documento para obter detalhes adicionais.

### <a name="xamarinandroid-integration"></a>Integração do projeto Xamarin.Android

Uma visão geral completa para a integração do SDK de aplicativos do Intune pode ser encontrada no [Guia do desenvolvedor Microsoft Intune app SDK para Android](app-sdk-android.md). Conforme você lê o guia e integra o SDK de aplicativo do Intune com seu aplicativo Xamarin, as seções a seguir destinam-se a destacar as diferenças entre a implementação de um aplicativo Android nativo desenvolvido em C#Java e um aplicativo Xamarin desenvolvido no. Essas seções devem ser tratadas como complementares e não podem agir como um substituto para a leitura integral do guia.

#### <a name="remapper"></a>Remapper
A partir da versão 1.4428.1, o pacote `Microsoft.Intune.MAM.Remapper` pode ser adicionado a um aplicativo Xamarin. Android como [ferramentas de compilação](app-sdk-android.md#build-tooling) para executar a classe MAM, o método e as substituições dos serviços de sistemas. Se o remapeador for incluído, as seções de substituição equivalentes de MAM dos métodos renomeados e de aplicativo MAM serão executadas automaticamente quando o aplicativo for compilado.

Para excluir uma classe de MAM-unificação pelo remapeador, a seguinte propriedade pode ser adicionada em seu arquivo de projetos `.csproj`.

```xml
  <PropertyGroup>
    <ExcludeClasses>Semicolon separated list of relative class paths to exclude from MAM-ification</ExcludeClasses>
  </PropertyGroup>
```

> [!NOTE]
> Neste momento, um problema com o remapeador impede a depuração em aplicativos Xamarin. Android. A integração manual é recomendada para depurar seu aplicativo até que esse problema seja resolvido.

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[Métodos renomeados](app-sdk-android.md#renamed-methods)
Em muitos casos, um método disponível na classe Android foi marcado como final na classe de substituição da MAM. Neste caso, a classe de substituição de MAM proporciona um método com um nome semelhante (com o sufixo `MAM`), que deve ser substituído. Por exemplo, quando executar a derivação de `MAMActivity`, em vez de substituir `OnCreate()` e chamar `base.OnCreate()`, `Activity` tem de substituir `OnMAMCreate()` e chamar `base.OnMAMCreate()`.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[Aplicativo MAM](app-sdk-android.md#mamapplication)
Seu aplicativo deve definir uma classe `Android.App.Application`. Se você estiver integrando o MAM manualmente, ele deverá herdar de `MAMApplication`. Certifique-se de que aplicou corretamente o atributo `[Application]` à sua subclasse e que esta substitui o construtor `(IntPtr, JniHandleOwnership)`.

```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```

> [!NOTE]
> Um problema com as associações do Xamarin do MAM pode fazer com que o aplicativo falhe quando implantado no modo de depuração. Como alternativa, o atributo `Debuggable=false` deve ser adicionado à classe `Application` e o sinalizador `android:debuggable="true"` deve ser removido do manifesto se ele tiver sido definido manualmente.

#### <a name="enable-features-that-require-app-participationapp-sdk-androidmdenable-features-that-require-app-participation"></a>[Habilitar recursos que exigem a participação do aplicativo](app-sdk-android.md#enable-features-that-require-app-participation)
Exemplo: Determinar se o PIN é necessário para o aplicativo

```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```

Exemplo: Determinar o usuário principal do Intune

```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```

Exemplo: Determine se é permitido salvar no dispositivo ou no armazenamento em nuvem

```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdkapp-sdk-androidmdregister-for-notifications-from-the-sdk"></a>[Registrar-se para notificações do SDK](app-sdk-android.md#register-for-notifications-from-the-sdk)
Seu aplicativo deve se registrar para notificações do SDK criando um `MAMNotificationReceiver` e registrando-o com `MAMNotificationReceiverRegistry`. Isso é feito fornecendo o receptor e o tipo de notificação desejado no `App.OnMAMCreate`, como mostra o exemplo a seguir:

```csharp
public override void OnMAMCreate()
{
    // Register the notification receivers
    IMAMNotificationReceiverRegistry registry = MAMComponents.Get<IMAMNotificationReceiverRegistry>();
    foreach (MAMNotificationType notification in MAMNotificationType.Values())
    {
        registry.RegisterReceiver(new ToastNotificationReceiver(this), notification);
    }
    ...
```

#### <a name="mam-enrollment-managerapp-sdk-androidmdmamenrollmentmanager"></a>[Gerenciador de registro de MAM](app-sdk-android.md#mamenrollmentmanager)

```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Integração do componente Xamarin.Forms

Para aplicativos `Xamarin.Forms`, o pacote `Microsoft.Intune.MAM.Remapper` executa a substituição da classe MAM automaticamente injetando classes `MAM` na hierarquia de classes das classes `Xamarin.Forms` usadas com frequência. 

> [!NOTE]
> A integração do Xamarin. Forms deve ser feita além da integração do Xamarin. Android detalhadamente acima. O remapeador se comporta de forma diferente para aplicativos Xamarin. Forms, de modo que as substituições de MAM manuais ainda precisarão ser feitas.

Depois que o remapeador for adicionado ao seu projeto, você precisará executar as substituições equivalentes do MAM. Por exemplo, `FormsAppCompatActivity` e `FormsApplicationActivity` podem continuar sendo usados em suas substituições fornecidas pelo aplicativo para `OnCreate` e `OnResume` são substituídos pelos equivalentes de MAM `OnMAMCreate` e `OnMAMResume`, respectivamente.

```csharp
    public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsAppCompatActivity
    {
        protected override void OnMAMCreate(Bundle savedInstanceState)
        {
            base.OnMAMCreate(savedInstanceState);
            global::Xamarin.Forms.Forms.Init(this, savedInstanceState);
            LoadApplication(new App());
        }
```

Se as substituições não forem feitas, você poderá encontrar os seguintes erros de compilação até fazer as substituições:
* [Erro do compilador CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). Esse erro geralmente é visto neste formulário ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
Isso é esperado porque quando o remapeador modifica a herança de classes do Xamarin, determinadas funções serão feitas `sealed` e uma nova variante de MAM será adicionada para substituir em vez disso.
* [CS0507 de erro do compilador](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): Esse erro geralmente é visto neste formulário ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. Quando o remapeador altera a herança de algumas das classes do Xamarin, determinadas funções de membro serão alteradas para `public`. Se você substituir qualquer uma dessas funções, será necessário alterar esses modificadores de acesso para que essas substituições sejam `public` também.

> [!NOTE]
> O remapeador reescreve uma dependência que o Visual Studio usa para a conclusão automática do IntelliSense. Portanto, talvez seja necessário recarregar e recompilar o projeto quando o remapeador for adicionado para que o IntelliSense reconheça corretamente as alterações.

#### <a name="troubleshooting"></a>Resolução de problemas
* Se você estiver encontrando uma tela branca em branco em seu aplicativo na inicialização, talvez seja necessário forçar as chamadas de navegação a serem executadas no thread principal.
* As associações do Xamarin SDK do Intune não oferecem suporte a aplicativos que usam uma estrutura de plataforma cruzada, como MvvmCross, devido a conflitos entre MvvmCross e classes MAM do Intune. Embora alguns clientes possam ter tido sucesso com a integração depois de mover seus aplicativos para o Xamarin. Forms, não fornecemos orientações ou plugins explícitos para desenvolvedores de aplicativos usando o MvvmCross.

### <a name="company-portal-app"></a>Aplicação Portal da Empresa
As associações do Xamarin SDK do Intune dependem da presença do aplicativo [portal da empresa](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) Android no dispositivo para habilitar as políticas de proteção do aplicativo. O Portal da Empresa obtém as políticas de proteção de aplicações do serviço Intune. Quando a aplicação é inicializada, é carregada a política e o código para impor essa política a partir do Portal da Empresa. O usuário não precisa estar conectado.

> [!NOTE]
> Quando o aplicativo Portal da Empresa não está no dispositivo **Android** , um aplicativo gerenciado pelo Intune se comporta da mesma forma que um aplicativo normal que não dá suporte a políticas de proteção de aplicativo do Intune.

Para a proteção de aplicações sem inscrição de dispositivos, o utilizador _**não**_ é obrigado a inscrever o dispositivo através da aplicação Portal da Empresa.

### <a name="sample-applications"></a>Aplicativos de exemplo
Aplicativos de exemplo destacando a funcionalidade de MAM nos aplicativos Xamarin. Android e Xamarin. Forms estão disponíveis no [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps).

## <a name="support"></a>Suporte
Se sua organização for um cliente existente do Intune, trabalhe com seu representante de suporte da Microsoft para abrir um tíquete de suporte e criar um problema [na página problemas do GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues). Ajudaremos assim que for possível. 
