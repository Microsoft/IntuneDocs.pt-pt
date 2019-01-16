---
title: Enlaces Xamarin do SDK da Aplicação Microsoft Intune
description: Os Enlaces Xamarin do SDK da Aplicação Intune ativam a política de proteção de aplicações do Intune em aplicações iOS e Android criadas com o Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: 65a461928c377dd4a674f8f3f2eeeef148ab56b2
ms.sourcegitcommit: 912aee714432c4a1e8efeee253ca2be4f972adaa
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54316904"
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

Para aplicações para Android baseadas no Xamarin que não utilizam uma estrutura de IU, tem de consultar e seguir o [Guia para Programadores do SDK da Aplicação Intune para Android](app-sdk-android.md). Para a sua aplicação Android baseada no Xamarin, terá de substituir a classe, métodos e as atividades na respetiva MAM equivalente com base na [tabela de substituições de classe e método](app-sdk-android.md#class-and-method-replacements) incluída no guia. Se a aplicação não definir uma classe `android.app.Application`, tem de criar uma e garantir que é herdada de `MAMApplication`. Os valores de configuração da ADAL são comunicados ao SDK através de metadados AndroidManifest. Leia a nossa documentação sobre a [configuração da ADAL para a sua aplicação](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal).

### <a name="xamarinandroid-integration"></a>Integração do projeto Xamarin.Android

1. Adicione a última versão do [pacote NuGet Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) ao seu projeto Xamarin.Android. Isto irá fornecer-lhe as referências necessárias para que o Intune ative a sua aplicação.

2. Leia e siga na totalidade o [Guia para Programadores do SDK da Aplicação Intune para Android](app-sdk-android.md), com especial atenção para:

    1. A [secção de substituições de classes e métodos inteira](app-sdk-android.md#class-and-method-replacements). 
    2. A [secção MAMApplication](app-sdk-android.md#mamapplication). Certifique-se de que aplicou corretamente o atributo `[Application]` à sua subclasse e que esta substitui o construtor `(IntPtr, JniHandleOwnership)`.
    3. A [secção de integração da ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal), se a sua aplicação fizer a autenticação através do AAD. 
    4. A [secção de inscrição da MAM-WE](app-sdk-android.md#app-protection-policy-without-device-enrollment), se quiser obter políticas do serviço MAM na sua aplicação.

> [!NOTE]
> Quando tentar encontrar APIs equivalentes do [Guia para Programadores do SDK da Aplicação Intune para Android](app-sdk-android.md) nos Enlaces `Microsoft.Intune.MAM.Xamarin.Android` ou quando converter fragmentos de código do guia, lembre-se de que o gerador de enlaces Xamarin modifica as APIs do Android das seguintes formas:
> * Todos os identificadores são convertidos em maiúsculas Pascal (com.foo.bar -> Com.Foo.Bar)
> * Todas as operações get/set são convertidas em operações de propriedade (por exemplo, Foo.getBar() -> Foo.Bar, Foo.setBar("zap") -> Foo.Bar = "zap")
> * Todas as interfaces têm o caráter "I" anexado no nome (FooInterface -> IFooInterface)

### <a name="xamarinforms-integration"></a>Integração do componente Xamarin.Forms

**Para além da execução de todos os passos acima**, para aplicações `Xamarin.Forms` fornecemos o pacote `Microsoft.Intune.MAM.Remapper`. Este pacote faz a substituição de classes ao injetar classes `MAM` na hierarquia de classes `Xamarin.Forms` utilizadas frequentemente, tais como `FormsAppCompatActivity` e `FormsApplicationActivity`, para que continue a poder utilizar essas classes através de substituições das funções MAM equivalentes, tais como `OnMAMCreate` e `OnMAMResume`. Para o utilizar, faça o seguinte:

1.  Adicione o pacote NuGet [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) ao seu projeto. Isto adicionará automaticamente os enlaces Xamarin do SDK da Aplicação Intune, caso ainda não os tenha incluído.

2.  Adicione uma chamada a `Xamarin.Forms.Forms.Init(Context, Bundle)` na função `OnMAMActivity` da classe `MAMApplication` que criou no passo 2.2 acima. Isto é necessário porque, com a gestão do Intune, a sua aplicação pode ser iniciada em segundo plano.

> [!NOTE]
> Dado que esta operação reescreve a dependência utilizada pelo Visual Studio para a conclusão automática do Intellisense, poderá ter de reiniciar o Visual Studio após a execução do primeiro remapeamento para que o Intellisense reconheça corretamente as alterações. 

## <a name="requiring-intune-app-protection-policies-in-order-to-use-your-xamarin-based-android-lob-app-optional"></a>Exigir políticas de proteção de aplicações do Intune de forma a utilizar a sua aplicação LOB para Android baseada no Xamarin (opcional) 

Seguem-se orientações para garantir que as aplicações LOB para Android baseadas no Xamarin só podem ser utilizadas por utilizadores protegidos pelo Intune nos respetivos dispositivos. 
    
### <a name="working-with-the-intune-sdk"></a>Trabalhar com o SDK do Intune
Estas instruções são específicas para todas as aplicações Android e Xamarin que pretendam exigir políticas de proteção de aplicações do Intune para utilização num dispositivo de utilizador final.

1. Configure a ADAL através dos passos definidos no [guia do SDK do Intune para Android](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal).
> [!NOTE] 
> O termo "ID de cliente" é o mesmo que o termo "ID de aplicação" do Portal do Azure associado à sua aplicação. 
* Para ativar o SSO, é preciso a "Configuração da ADAL comum" n.º 2.

2. Ative a inscrição predefinida ao colocar o valor seguinte no manifesto: ```xml <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />```
> [!NOTE] 
> Esta tem de ser a única integração da MAM-WE na aplicação. Poderão surgir conflitos se existirem outras tentativas de chamar as APIs MAMEnrollmentManager.

3. Ative a política de MAM exigida ao colocar o valor seguinte no manifesto: ```xml <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />```
> [!NOTE] 
> Esta ação força as aplicações a transferir o Portal da Empresa para o dispositivo e a concluir o fluxo da inscrição predefinida antes da utilização.

### <a name="working-with-adal"></a>Trabalhar com a ADAL
Estas instruções são um requisito para as aplicações .NET/Xamarin que pretendam exigir políticas de proteção de aplicações do Intune para utilização num dispositivo de utilizador final.

1. Siga todos os passos definidos na documentação ADAL em [Brokered Authentication for Android](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/tree/dev/adal#brokered-authentication-for-android) (Autenticação Mediada para Android).

## <a name="potential-compilation-errors"></a>Potenciais erros de compilação
Estes são alguns dos erros mais comuns de compilação quando desenvolver uma Xamarin com base em aplicações.

* [CS0239 de erro do compilador](https://docs.microsoft.com/en-us/dotnet/csharp/misc/cs0239): Este erro é frequentemente visto neste formulário ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
Quando o remapper modifica a herança de classes do Xamarin, serão feitas algumas funções `sealed` e uma nova variante MAM é adicionada ao substituir em vez disso. Simplesmente mudar o nome substituições conforme descrito [aqui](https://docs.microsoft.com/en-us/intune/app-sdk-android#renamed-methods). Por exemplo `MainActivity.OnCreate()` seria possível mudar o nome para `MainActivity.OnMAMCreate()`

* [CS0507 de erro do compilador](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/compiler-messages/cs0507): Este erro é frequentemente visto neste formulário ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. Como a ferramenta de remapper altera a herança de algumas das Xamarin classes, algumas das funções de membro serão alteradas para `public`. Se substituir qualquer uma destas funções, poderá ter de alterar as substituições para ser `public` também.

## <a name="support"></a>Suporte
Se a sua organização for um cliente do Intune existente, trabalhe com o seu representante de suporte da Microsoft para abrir um pedido de suporte e criar um problema [na página de problemas do Github](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) e iremos ajudar assim que possível. 
