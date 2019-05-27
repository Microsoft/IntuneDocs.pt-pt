---
title: Enlaces Xamarin do SDK da Aplicação Microsoft Intune
description: Os Enlaces Xamarin do SDK da Aplicação Intune ativam a política de proteção de aplicações do Intune em aplicações iOS e Android criadas com o Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
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
ms.openlocfilehash: 2f065849bd15a23558aa9bb7f82730dca9d4b3fa
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66043632"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Enlaces Xamarin do SDK da Aplicação Microsoft Intune

> [!NOTE]
> Pode ler primeiro o artigo [Introdução ao SDK da Aplicação Intune](app-sdk-get-started.md), que explica como preparar a integração em cada plataforma suportada.

## <a name="overview"></a>Descrição geral
Os [Enlaces Xamarin do SDK da Aplicação Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) ativam a [política de proteção de aplicações do Intune](app-protection-policy.md) em aplicações iOS e Android criadas com o Xamarin. Os enlacem permitem aos programadores criar facilmente funcionalidades de proteção de aplicações do Intune na respetiva aplicação baseada no Xamarin.

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

O SDK depende [Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) para seu [autenticação](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) cenários e iniciação condicional, que requerem as aplicações sejam configuradas com [Active Directory do Azure Diretório](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). 

Se seu aplicativo já está configurado para utilizar a ADAL ou MSAL e tem seu próprio ID utilizado para autenticar com o Azure Active Directory personalizadas de cliente, certifique-se os passos para conceder as permissões de aplicação Xamarin para o serviço de gestão de aplicações móveis (MAM) da Intune seguidas. Utilize as instruções na "[dar o acesso a aplicações para o serviço de proteção de aplicações do Intune](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)" secção a [introdução ao Guia do SDK do Intune](app-sdk-get-started.md).

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Ativar as políticas de proteção de aplicações do Intune na sua aplicação móvel iOS
1. Adicione o [pacote NuGet Microsoft.Intune.MAM.Xamarin.iOS](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) ao seu projeto Xamarin.iOS.
2.  Siga os passos gerais necessários para integrar o SDK da Aplicação Intune numa aplicação móvel iOS. Pode começar com o passo 3 das instruções de integração do [Guia para Programadores do SDK da Aplicação Intune para iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). Pode ignorar o passo final na secção na qual executa o IntuneMAMConfigurator, sendo que esta ferramenta está incluída no pacote Microsoft.Intune.MAM.Xamarin.iOS e será executada automaticamente aquando a compilação.
    **Importante**: Ativar para uma aplicação de partilha de keychain é ligeiramente diferente no Visual Studio do Xcode. Abra a plist de Elegibilidade da aplicação e garanta que a opção “Ativar Keychain” está ativada e que são adicionados os grupos de partilha de keychain adequados nessa secção. Em seguida, garanta que a plist de Elegibilidade está especificada no campo “Elegibilidades Personalizadas” das opções “Assinatura de Pacotes iOS” do projeto para todas as combinações de Configuração/Plataforma adequadas.
3.  Após os enlaces serem adicionados e a aplicação estar configurada corretamente, a sua aplicação pode começar a utilizar as APIs do SDK do Intune. Para tal, tem de incluir o seguinte espaço de nomes:

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. Para começar a receber políticas de proteção de aplicações, tem de inscrever a aplicação no serviço do Intune MAM. Se a sua aplicação não utilizar a [Biblioteca de Autenticação do Azure Active Directory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) nem a [Biblioteca de Autenticação da Microsoft](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) para autenticar utilizadores e quiser que o SDK do Intune processe a autenticação, a sua aplicação deve fornecer o UPN do utilizador ao método LoginAndEnrollAccount de IntuneMAMEnrollmentManager:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```
      As aplicações poderão transmitir "nulo" se o UPN do utilizador for desconhecido no momento da chamada. Neste caso, pedir-se-á aos utilizadores para introduzirem o respetivo endereço de e-mail e palavra-passe.
      
      Se a sua aplicação já utilizar a ADAL ou a MSAL para autenticar utilizadores, pode configurar uma experiência de início de sessão único (SSO) entre a aplicação e o SDK do Intune. Em primeiro lugar, terá de configurar a ADAL/MSAL para armazenar tokens no mesmo grupo de acesso de keychain utilizado pelos Enlaces Xamarin do Intune para iOS (com.microsoft.adalcache). No caso da ADAL, pode fazê-lo ao [definir a propriedade KeychainSecurityGroup de AuthenticationContext](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/Token-cache-serialization#enable-token-cache-sharing-across-ios-applications). No caso da MSAL, precisará de [definir a propriedade KeychainSecurityGroup de PublicClientApplication](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/msal-net-2-released#you-can-now-enable-sso-between-adal-and-msal-apps-on-xamarinios). Em seguida, terá de substituir as predefinições do AAD utilizadas pelo SDK do Intune pelas da sua aplicação. Pode fazê-lo através do dicionário IntuneMAMSettings no ficheiro Info.plist da aplicação, tal como mencionado no [Guia para Programadores do SDK da Aplicação Intune para iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk), ou pode utilizar as propriedades de substituição do AAD da instância IntuneMAMPolicyManager. A abordagem do ficheiro Info.plist é recomendada para aplicações cujas definições da ADAL sejam estáticas, enquanto as propriedades de substituição são recomendadas para aplicações que determinem esses valores no runtime. Depois de configurar todas as definições do SSO, a sua aplicação deve fornecer o UPN do utilizador ao método RegisterAndEnrollAccount de IntuneMAMEnrollmentManager após a autenticação bem-sucedida:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      As aplicações podem determinar o resultado de uma tentativa de inscrição ao implementar o método EnrollmentRequestWithStatus numa subclasse de IntuneMAMEnrollmentDelegate e ao definir a propriedade Delegate do IntuneMAMEnrollmentManager para uma instância dessa classe. Para ter acesso a um exemplo, veja o nosso [exemplo de aplicação Xamarin.iOS](https://github.com/msintuneappsdk/sample-intune-xamarin-ios).

      Após uma inscrição bem-sucedida, as aplicações podem determinar o UPN da conta inscrita (se este fosse previamente desconhecido) ao consultar a seguinte propriedade: 
      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
> [!NOTE] 
> Não há nenhum remapeamento para iOS. A integração numa aplicação Xamarin.Forms deve ser igual à de um projeto normal Xamarin.iOS. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Ativar as políticas de proteção de aplicações do Intune na sua aplicação móvel para Android

1. Adicione o [pacote NuGet Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) ao seu projeto Xamarin.Android.
    1. Para uma aplicação xamarin. Forms, adicione a [pacote Microsoft.Intune.MAM.Remapper.Tasks NuGet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) ao seu projeto xamarin. Android também. 
2. Siga os passos gerais necessários para [integrar o SDK da aplicação Intune](app-sdk-android.md) numa aplicação móvel Android ao mesmo tempo que faça referência a este documento para obter mais detalhes.

### <a name="xamarinandroid-integration"></a>Integração do projeto Xamarin.Android

Uma descrição geral completa para integrar o SDK da aplicação Intune pode ser encontrada no [Microsoft Intune App SDK para o guia de programação do Android](app-sdk-android.md). À medida que leia o guia e integrar o SDK da aplicação Intune com a sua aplicação Xamarin as secções seguintes destinam-se para destacar as diferenças entre a implementação para uma aplicação Android nativa desenvolvido em Java e uma aplicação Xamarin desenvolvido em C#. Estas secções devem ser tratadas como suplementares e não podem agir como um substituto para ler o guia na íntegra.

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[Métodos renomeados](app-sdk-android.md#renamed-methods)
Em muitos casos, um método disponível na classe Android foi marcado como final na classe de substituição da MAM. Neste caso, a classe de substituição de MAM proporciona um método com um nome semelhante (com o sufixo `MAM`), que deve ser substituído. Por exemplo, quando executar a derivação de `MAMActivity`, em vez de substituir `OnCreate()` e chamar `base.OnCreate()`, `Activity` tem de substituir `OnMAMCreate()` e chamar `base.OnMAMCreate()`.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[Aplicação de MAM](app-sdk-android.md#mamapplication)
A aplicação tem de definir uma `Android.App.Application` classe que herda de `MAMApplication`. Certifique-se de que aplicou corretamente o atributo `[Application]` à sua subclasse e que esta substitui o construtor `(IntPtr, JniHandleOwnership)`.
```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```
> [!NOTE]
> Um problema com os enlaces Xamarin da MAM pode fazer com que o aplicativo falhar quando são implementadas no modo de depuração. Como solução, o `Debuggable=false` atributo tem de ser adicionado para o `Application` classe e o `android:debuggable="true"` sinalizador tem de ser removido do manifesto se estivesse definido manualmente.

#### <a name="enable-features-that-require-app-participationapp-sdk-androidmdenable-features-that-require-app-participation"></a>[Ativar funcionalidades que requerem a participação da aplicação](app-sdk-android.md#enable-features-that-require-app-participation)
Exemplo: Determinar se o PIN é necessário para a aplicação
```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```
Exemplo: Determinar o utilizador primário do Intune
```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```
Exemplo: Determinar se a guardar no dispositivo ou armazenamento na cloud é permitido
```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdkapp-sdk-androidmdregister-for-notifications-from-the-sdk"></a>[Registre-se para notificações do SDK](app-sdk-android.md#register-for-notifications-from-the-sdk)
A aplicação tem de se registar para notificações do SDK ao criar um `MAMNotificationReceiver` e registando-a em `MAMNotificationReceiverRegistry`. Isso é feito ao indicar o recetor e o tipo de notificação desejados em `App.OnMAMCreate`, como ilustra o exemplo abaixo:
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

#### <a name="mam-enrollment-managerapp-sdk-androidmdmamenrollmentmanager"></a>[Gestor de inscrição da MAM](app-sdk-android.md#mamenrollmentmanager)
```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Integração do componente Xamarin.Forms

Para `Xamarin.Forms` aplicações, nós fornecemos a `Microsoft.Intune.MAM.Remapper` pacote para executar a substituição de classe MAM automaticamente injetando `MAM` classes para a hierarquia de classe de usadas `Xamarin.Forms` classes. 

> [!NOTE]
> A integração do xamarin. Forms está a ser feito, além disso, para a integração do xamarin. Android detalhada acima.

Depois do Remapper é adicionado ao seu projeto, que terá de efetuar as substituições de equivalentes MAM. Por exemplo, `FormsAppCompatActivity` e `FormsApplicationActivity` pode continuar a ser utilizado nas substituições seu aplicativo fornecido para `OnCreate` e `OnResume` são substituídos por equivalentes MAM `OnMAMCreate` e `OnMAMResume` , respetivamente.

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
Caso não sejam feitas as substituições, em seguida, pode encontrar os seguintes erros de compilação até fazer as substituições:
* [CS0239 de erro do compilador](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). Este erro é frequentemente visto neste formulário ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
Isso é esperado, porque quando o Remapper modifica a herança de classes do Xamarin, serão feitas determinadas funções `sealed` e uma nova variante MAM é adicionada ao substituir em vez disso.
* [CS0507 de erro do compilador](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): Este erro é frequentemente visto neste formulário ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. Quando o Remapper altera a herança de algumas das Xamarin classes, determinadas funções de membro serão alteradas para `public`. Se substituir qualquer uma destas funções, terá de alterar as substituições dos modificadores de acesso para aqueles para ser `public` também.

> [!NOTE]
> O Remapper reescreverá uma dependência que utiliza o Visual Studio para preenchimento automático do IntelliSense. Portanto, poderá ter de recarregar e reconstruir o projeto quando o Remapper é adicionado para IntelliSense reconhecer corretamente as alterações.

## <a name="support"></a>Suporte
Se a sua organização for um cliente do Intune existente, trabalhe em conjunto com o seu representante de suporte da Microsoft para abrir um pedido de suporte e criar um problema [no GitHub a página de problemas](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) e iremos ajudar assim que possível. 
