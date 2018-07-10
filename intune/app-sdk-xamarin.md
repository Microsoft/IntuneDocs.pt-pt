---
title: Enlaces Xamarin do SDK da Aplicação Microsoft Intune
description: Os Enlaces Xamarin do SDK da Aplicação Intune ativam a política de proteção de aplicações do Intune em aplicações iOS e Android criadas com o Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 06/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f8f5e397c314088c7b26edba486f9cbaf9718096
ms.sourcegitcommit: 1eddded65ae9e442dd3bebd16b9428af76a67f34
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2018
ms.locfileid: "35250949"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Enlaces Xamarin do SDK da Aplicação Microsoft Intune

> [!NOTE]
> Pode ler primeiro o artigo [Introdução ao SDK da Aplicação Intune](app-sdk-get-started.md), que explica como preparar a integração em cada plataforma suportada.

## <a name="overview"></a>Descrição geral
Os [Enlaces Xamarin do SDK da Aplicação Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) ativam a [política de proteção de aplicações do Intune](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) em aplicações iOS e Android criadas com o Xamarin. Os enlacem permitem aos programadores criar facilmente funcionalidades de proteção de aplicações do Intune na respetiva aplicação baseada no Xamarin.

Os Enlaces Xamarin do SDK da Aplicação Microsoft Intune permitem-lhe incorporar as políticas de proteção de aplicações do Intune (também conhecidas como políticas de APLICAÇÕES ou MAM) nas suas aplicações desenvolvidas com o Xamarin. Uma aplicação preparada para MAM é uma aplicação que está integrada com o SDK da Aplicação do Intune. Os administradores de TI podem implementar políticas de proteção de aplicações na aplicação móvel quando o Intune está a gerir a aplicação de forma ativa.

## <a name="whats-supported"></a>O que é suportado?

### <a name="developer-machines"></a>Máquinas do programador
* Windows
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

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Ativar as políticas de proteção de aplicações do Intune na sua aplicação móvel iOS
1. Adicione o [pacote NuGet Microsoft.Intune.MAM.Xamarin.iOS](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) ao seu projeto Xamarin.iOS.
2.  Siga os passos gerais necessários para integrar o SDK da Aplicação Intune numa aplicação móvel iOS. Pode começar com o passo 3 das instruções de integração do [Guia para Programadores do SDK da Aplicação Intune para iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). Pode ignorar o passo final na secção na qual executa o IntuneMAMConfigurator, sendo que esta ferramenta está incluída no pacote Microsoft.Intune.MAM.Xamarin.iOS e será executada automaticamente aquando a compilação.
    **Importante**: a ativação da partilha de keychain para uma aplicação é ligeiramente diferente no Visual Studio a partir do Xcode. Abra a plist de Elegibilidade da aplicação e garanta que a opção “Ativar Keychain” está ativada e que são adicionados os grupos de partilha de keychain adequados nessa secção. Em seguida, garanta que a plist de Elegibilidade está especificada no campo “Elegibilidades Personalizadas” das opções “Assinatura de Pacotes iOS” do projeto para todas as combinações de Configuração/Plataforma adequadas.
3.  Após os enlaces serem adicionados e a aplicação estar configurada corretamente, a sua aplicação pode começar a utilizar as APIs do SDK do Intune. Para tal, tem de incluir o seguinte espaço de nomes:

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. Para começar a receber políticas de proteção de aplicações, tem de inscrever a aplicação no serviço do Intune MAM. Se a sua aplicação já utilizar a Azure Active Directory Authentication Library (ADAL) para autenticar os utilizadores, a aplicação deverá disponibilizar o UPN do utilizador ao método registerAndEnrollAccount do IntuneMAMEnrollmentManager depois de ter realizado a autenticação com êxito:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **Importante**: não se esqueça de substituir as predefinições da ADAL do SDK da Aplicação Intune pelas predefinições da sua aplicação. Pode fazê-lo através do dicionário IntuneMAMSettings no ficheiro Info.plist da aplicação, tal como mencionado no [Guia para Programadores do SDK da Aplicação Intune para iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk), ou pode utilizar as propriedades de substituição do AAD da instância IntuneMAMPolicyManager. A abordagem do ficheiro Info.plist é recomendada para aplicações cujas definições da ADAL sejam estáticas, enquanto as propriedades de substituição são recomendadas para aplicações que determinem esses valores no runtime. 
      
      Se a aplicação não utilizar a ADAL e quiser que o SDK do Intune processe a autenticação, a aplicação deverá chamar o método loginAndEnrollAccount do IntuneMAMEnrollmentManager:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```
      
> [!NOTE] 
> Não há nenhum remapeamento para iOS. A integração numa aplicação Xamarin.Forms deve ser igual à de um projeto normal Xamarin.iOS. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Ativar as políticas de proteção de aplicações do Intune na sua aplicação móvel para Android

### <a name="xamarinandroid-integration"></a>Integração do projeto Xamarin.Android

1. Adicione a última versão do [pacote NuGet Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) ao seu projeto Xamarin.Android. Isto irá fornecer-lhe as referências necessárias para que o Intune ative a sua aplicação.

2. Leia e siga na totalidade o [Guia para Programadores do SDK da Aplicação Intune para Android](app-sdk-android.md), com especial atenção para:
    1. A [secção de substituições de classes e métodos inteira](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent). 
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

2.  Adicione uma chamada a `Xamarin.Forms.Forms.Init(Context, Bundle)` na função `OnMAMCreate` da classe `MAMApplication` que criou no passo 2.2 acima. Isto é necessário porque, com a gestão do Intune, a sua aplicação pode ser iniciada em segundo plano.

> [!NOTE]
> Dado que esta operação reescreve a dependência utilizada pelo Visual Studio para a conclusão automática do Intellisense, poderá ter de reiniciar o Visual Studio após a execução do primeiro remapeamento para que o Intellisense reconheça corretamente as alterações. 


## <a name="support"></a>Support

Se a sua organização for um cliente do Intune existente, trabalhe com o seu representante de suporte da Microsoft para abrir um pedido de suporte e criar um problema [na página de problemas do Github](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) e iremos ajudar assim que possível. 
