---
title: Enlaces Xamarin do SDK da Aplicação Microsoft Intune
description: Os Enlaces Xamarin do SDK da Aplicação Intune ativam a política de proteção de aplicações do Intune em aplicações iOS e Android criadas com o Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10f3d4c54d9a8fcb797ae3359b1a833ac9080548
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912704"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Enlaces Xamarin do SDK da Aplicação Microsoft Intune

> [!NOTE]
> Pode ler primeiro o artigo [Introdução ao SDK da Aplicação Intune](app-sdk-get-started.md), que explica como preparar a integração em cada plataforma suportada.

## <a name="overview"></a>Overview
Os [Enlaces Xamarin do SDK da Aplicação Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) ativam a [política de proteção de aplicações do Intune](../apps/app-protection-policy.md) em aplicações iOS e Android criadas com o Xamarin. Os enlacem permitem aos programadores criar facilmente funcionalidades de proteção de aplicações do Intune na respetiva aplicação baseada no Xamarin.

Os Enlaces Xamarin do SDK da Aplicação Microsoft Intune permitem-lhe incorporar as políticas de proteção de aplicações do Intune (também conhecidas como políticas de APLICAÇÕES ou MAM) nas suas aplicações desenvolvidas com o Xamarin. Uma aplicação preparada para MAM é uma integrada com o SDK da Aplicação Intune. Os administradores de TI podem implementar políticas de proteção de aplicações na aplicação móvel quando o Intune está a gerir a aplicação de forma ativa.

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

Reveja os [termos de licenciamento](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf). Imprima e guarde uma cópia dos termos de licenciamento nos seus registos. Ao transferir e utilizar os Enlaces Xamarin do SDK da Aplicação Intune, aceita esses termos de licenciamento. Caso não aceite os termos, não utilize o software.

O Intune SDK conta com a Biblioteca de Autenticação de [Diretórios Ativos (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) para os cenários de [autenticação](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) e lançamento condicional, que exigem que as aplicações sejam configuradas com [o Diretório Ativo do Azure.](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) 

Se a sua aplicação já estiver configurada para utilizar a ADAL ou a MSAL, e tiver o seu próprio ID de cliente personalizado usado para autenticar com o Azure Ative Directory, certifique-se de que os passos para dar permissões à sua aplicação Xamarin para o serviço Intune Mobile Application Management (MAM) são seguido. Utilize as instruções na secção " Dar à sua aplicação acesso ao serviço de proteção de[aplicações Intune](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)" do [início com o guia Intune SDK](app-sdk-get-started.md).

## <a name="security-considerations"></a>Considerações de Segurança

Para impedir potenciais ataques de spoofing, divulgação de informações e ataques de elevação de privilégios:

* Certifique-se de que o desenvolvimento da aplicação Xamarin é realizado numa estação de trabalho segura.
* Certifique-se de que as encadernações são de uma fonte válida da Microsoft:
  * [MS Intune App SDK NuGet Profile](https://www.nuget.org/profiles/msintuneappsdk)
  * [Intune App SDK Xamarin GitHub Repositório](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* Configure o seu config NuGet para que o seu projeto confie em pacotes NuGet assinados e não modificados.
Consulte [a instalação de pacotes assinados](https://docs.microsoft.com/nuget/consume-packages/installing-signed-packages) para obter mais informações.
* Proteja o diretório de saída que contém a aplicação Xamarin. Considere utilizar um diretório de nível de utilizador para a saída.


## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Ativar as políticas de proteção de aplicações do Intune na sua aplicação móvel iOS
1. Adicione o [pacote NuGet Microsoft.Intune.MAM.Xamarin.iOS](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) ao seu projeto Xamarin.iOS.
2. Siga os passos gerais necessários para integrar o SDK da Aplicação Intune numa aplicação móvel iOS. Pode começar com o passo 3 das instruções de integração do [Guia para Programadores do SDK da Aplicação Intune para iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). Pode ignorar o passo final na secção na qual executa o IntuneMAMConfigurator, sendo que esta ferramenta está incluída no pacote Microsoft.Intune.MAM.Xamarin.iOS e será executada automaticamente aquando a compilação.
    **Importante**: a ativação da partilha de keychain para uma aplicação é ligeiramente diferente no Visual Studio a partir do Xcode. Abra a plist de Elegibilidade da aplicação e garanta que a opção “Ativar Keychain” está ativada e que são adicionados os grupos de partilha de keychain adequados nessa secção. Em seguida, garanta que a plist de Elegibilidade está especificada no campo “Elegibilidades Personalizadas” das opções “Assinatura de Pacotes iOS” do projeto para todas as combinações de Configuração/Plataforma adequadas.
3. Após os enlaces serem adicionados e a aplicação estar configurada corretamente, a sua aplicação pode começar a utilizar as APIs do SDK do Intune. Para tal, tem de incluir o seguinte espaço de nomes:

      ```csharp
      using Microsoft.Intune.MAM;
      ```

4. Para começar a receber políticas de proteção de aplicações, tem de inscrever a aplicação no serviço do Intune MAM. Se a sua aplicação não utilizar a [Biblioteca de Autenticação do Azure Active Directory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) nem a [Biblioteca de Autenticação da Microsoft](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) para autenticar utilizadores e quiser que o SDK do Intune processe a autenticação, a sua aplicação deve fornecer o UPN do utilizador ao método LoginAndEnrollAccount de IntuneMAMEnrollmentManager:

      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

      As aplicações poderão transmitir "nulo" se o UPN do utilizador for desconhecido no momento da chamada. Neste caso, pedir-se-á aos utilizadores para introduzirem o respetivo endereço de e-mail e palavra-passe.
      
      Se a sua aplicação já utilizar a ADAL ou a MSAL para autenticar utilizadores, pode configurar uma experiência de início de sessão único (SSO) entre a aplicação e o SDK do Intune. Em primeiro lugar, terá de anular as definições padrão de AAD utilizadas pelo Intune SDK com as da sua aplicação. Pode fazê-lo através do dicionário IntuneMAMSettings na lista info.plist da aplicação, conforme mencionado no [Intune App SDK para o iOS Developer Guide,](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)ou pode fazê-lo em código através da propriedade de substituição de AAD da classe IntuneMAMSettings. A abordagem do ficheiro Info.plist é recomendada para aplicações cujas definições da ADAL sejam estáticas, enquanto as propriedades de substituição são recomendadas para aplicações que determinem esses valores no runtime. Depois de configurar todas as definições do SSO, a sua aplicação deve fornecer o UPN do utilizador ao método RegisterAndEnrollAccount de IntuneMAMEnrollmentManager após a autenticação bem-sucedida:

      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```

      As aplicações podem determinar o resultado de uma tentativa de inscrição ao implementar o método EnrollmentRequestWithStatus numa subclasse de IntuneMAMEnrollmentDelegate e ao definir a propriedade Delegate do IntuneMAMEnrollmentManager para uma instância dessa classe. 

      Após uma inscrição bem-sucedida, as aplicações podem determinar o UPN da conta inscrita (se este fosse previamente desconhecido) ao consultar a seguinte propriedade: 

      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
### <a name="sample-applications"></a>Aplicações de amostras
As aplicações de amostra que destacam a funcionalidade MAM nas aplicações Xamarin.iOS estão disponíveis no [GitHub.](https://github.com/msintuneappsdk/sample-intune-xamarin-ios)

> [!NOTE] 
> Não há nenhum remapeamento para iOS. A integração numa aplicação Xamarin.Forms deve ser igual à de um projeto normal Xamarin.iOS. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Ativar as políticas de proteção de aplicações do Intune na sua aplicação móvel para Android
1. Adicione o [pacote NuGet Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) ao seu projeto Xamarin.Android.
    1. Para uma aplicação Xamarin.Forms, adicione o [pacote Microsoft.Intune.MAM.Remapper.Tasks NuGet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) ao seu projeto Xamarin.Android também. 
2. Siga os passos gerais necessários para [integrar o Intune App SDK](app-sdk-android.md) numa aplicação móvel Android, referindo-se a este documento para mais detalhes.

### <a name="xamarinandroid-integration"></a>Integração do projeto Xamarin.Android

Uma visão geral completa para integrar o Intune App SDK pode ser encontrada no [Microsoft Intune App SDK para guia](app-sdk-android.md)de desenvolvedores Android . Ao ler através do guia e integrar o Intune App SDK com a sua aplicação Xamarin, as seguintes secções destinam-se a C#destacar diferenças entre a implementação de uma aplicação nativa do Android desenvolvida em Java e uma aplicação Xamarin desenvolvida em . Estas secções devem ser tratadas como suplementares e não podem funcionar como um substituto para ler o guia na sua totalidade.

#### <a name="remapper"></a>Remapper
A partir do lançamento de 1.4428.1, o pacote `Microsoft.Intune.MAM.Remapper` pode ser adicionado a uma aplicação Xamarin.Android como ferramenta de [construção](app-sdk-android.md#build-tooling) para realizar as substituições da classe MAM, método e serviços de sistemas. Se o Remapper for incluído, as partes de substituição equivalentes do MAM das secções de aplicação Renomeado seleções e aplicação MAM serão executadas automaticamente quando a aplicação for construída.

Para excluir uma classe da MAM-ification pelo Remapper, o seguinte imóvel pode ser adicionado nos seus projetos `.csproj` arquivo.

```xml
  <PropertyGroup>
    <ExcludeClasses>Semicolon separated list of relative class paths to exclude from MAM-ification</ExcludeClasses>
  </PropertyGroup>
```

> [!NOTE]
> O Remapper atualmente evita a depuração em aplicações Xamarin.Android. Recomenda-se a integração manual para desinserção da sua aplicação.

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[Métodos renomeados](app-sdk-android.md#renamed-methods)
Em muitos casos, um método disponível na classe Android foi marcado como final na classe de substituição da MAM. Neste caso, a classe de substituição de MAM proporciona um método com um nome semelhante (com o sufixo `MAM`), que deve ser substituído. Por exemplo, quando executar a derivação de `MAMActivity`, em vez de substituir `OnCreate()` e chamar `base.OnCreate()`, `Activity` tem de substituir `OnMAMCreate()` e chamar `base.OnMAMCreate()`.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[Aplicação MAM](app-sdk-android.md#mamapplication)
A sua aplicação deve definir uma aula de `Android.App.Application`. Se integrar manualmente o MAM, deve herdar de `MAMApplication`. Certifique-se de que aplicou corretamente o atributo `[Application]` à sua subclasse e que esta substitui o construtor `(IntPtr, JniHandleOwnership)`.

```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```

> [!NOTE]
> Um problema com as ligações MAM Xamarin pode causar a queda da aplicação quando implantada no modo Debug. Como sutique, o atributo `Debuggable=false` deve ser adicionado à classe `Application` e a bandeira `android:debuggable="true"` deve ser retirada do manifesto se for manualmente definida.

#### <a name="enable-features-that-require-app-participationapp-sdk-androidmdenable-features-that-require-app-participation"></a>[Ativar funcionalidades que requerem participação na app](app-sdk-android.md#enable-features-that-require-app-participation)
Exemplo: determinar se o PIN é necessário para a aplicação

```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```

Exemplo: determinar o utilizador primário do Intune

```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```

Exemplo: determinar se é permitido guardar no dispositivo ou armazenar na cloud

```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdkapp-sdk-androidmdregister-for-notifications-from-the-sdk"></a>[Registo de notificações do SDK](app-sdk-android.md#register-for-notifications-from-the-sdk)
A sua aplicação deve registar-se para notificações do SDK, criando uma `MAMNotificationReceiver` e registando-a com `MAMNotificationReceiverRegistry`. Isto é feito fornecendo o recetor e o tipo de notificação desejado em `App.OnMAMCreate`, como o exemplo abaixo ilustra:

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

#### <a name="mam-enrollment-managerapp-sdk-androidmdmamenrollmentmanager"></a>[Gestor de Inscrição do MAM](app-sdk-android.md#mamenrollmentmanager)

```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Integração do componente Xamarin.Forms

Para aplicações `Xamarin.Forms`, o pacote `Microsoft.Intune.MAM.Remapper` realiza automaticamente a substituição da classe MAM injetando `MAM` classes na hierarquia de classe das classes `Xamarin.Forms` geralmente utilizadas. 

> [!NOTE]
> A integração Xamarin.Forms deve ser feita para além da integração Xamarin.Android detalhada acima. O Remapper comporta-se de forma diferente para as aplicações Xamarin.Forms, pelo que as substituições mam manuais ainda devem ser feitas.

Assim que o Remapper for adicionado ao seu projeto, terá de realizar as substituições equivalentes do MAM. Por exemplo, `FormsAppCompatActivity` e `FormsApplicationActivity` podem continuar a ser utilizados na sua aplicação, desde que `OnCreate` e `OnResume` sejam substituídos pelos equivalentes MAM `OnMAMCreate` e `OnMAMResume` respectivamente.

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

Se as substituições não forem efetuadas, poderá encontrar os seguintes erros de compilação até efetuar as substituições:
* [Erro do compilador CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). Este erro é comumente visto desta forma ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
Isto é esperado porque quando o Remapper modificar a herança das classes Xamarin, certas funções serão feitas `sealed` e uma nova variante mam é adicionada para substituir.
* [Erro do compilador CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): Este erro é comumente visto desta forma ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. Quando o Remapper alterar a herança de algumas das classes Xamarin, certas funções dos membros serão alteradas para `public`. Se anular qualquer uma destas funções, terá de alterar as modificações de acesso para que essas substituições sejam `public` também.

> [!NOTE]
> O Remapper reescreve uma dependência que o Visual Studio usa para a conclusão automática do IntelliSense. Por isso, poderá ter de recarregar e reconstruir o projeto quando o Remapper for adicionado para que o IntelliSense reconheça corretamente as alterações.

#### <a name="troubleshooting"></a>Resolução de Problemas
* Se encontrar um ecrã branco e em branco na sua aplicação no lançamento, poderá ser necessário forçar as chamadas de navegação a executar na linha principal.
* As Ligações Intune SDK Xamarin não suportam aplicações que estão a usar um quadro de plataformas cruzadas, como o MvvmCross devido a conflitos entre as classes MvvmCross e Intune MAM. Embora alguns clientes possam ter tido sucesso com a integração depois de moveras as suas apps para xamarin.Forms simples, não fornecemos orientação explícita ou plugins para desenvolvedores de aplicações usando MvvmCross.

### <a name="company-portal-app"></a>Aplicação Portal da Empresa
Os Intune SDK Xamarin Bindings contam com a presença da aplicação Portal da [Empresa](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) Android no dispositivo para permitir políticas de proteção de aplicações. O Portal da Empresa obtém as políticas de proteção de aplicações do serviço Intune. Quando a aplicação é inicializada, é carregada a política e o código para impor essa política a partir do Portal da Empresa. O utilizador não precisa de ser inscrito.

> [!NOTE]
> Quando a aplicação Portal da Empresa não está no dispositivo **Android,** uma aplicação gerida pelo Intune comporta-se da mesma forma que uma aplicação normal que não suporta as políticas de proteção de aplicações Intune.

Para a proteção de aplicações sem inscrição de dispositivos, o utilizador _**não**_ é obrigado a inscrever o dispositivo através da aplicação Portal da Empresa.

### <a name="sample-applications"></a>Aplicações de amostras
Aplicações de amostra sintetizadas que destacam a funcionalidade MAM em Xamarin.Android e Xamarin.Forms aplicações estão disponíveis no [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps).

## <a name="support"></a>Support
Se a sua organização for um cliente Intune existente, trabalhe com o seu representante de suporte da Microsoft para abrir um bilhete de suporte e criar um problema na página de [problemas do GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues). Ajudaremos assim que pudermos. 
