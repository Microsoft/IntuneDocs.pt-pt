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
ms.openlocfilehash: 421dede4b0da71fe04649e21bfcf7c15d2270507
ms.sourcegitcommit: 399f34cd169e2e352b49aad1dcb7e88294a4a9f1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37869360"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Enlaces Xamarin do SDK da Aplicação Microsoft Intune

> [!NOTE]
> Pode ler primeiro o artigo [Introdução ao SDK da Aplicação Intune](app-sdk-get-started.md), que explica como preparar a integração em cada plataforma suportada.

## <a name="overview"></a>Descrição geral
Os [Enlaces Xamarin do SDK da Aplicação Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) ativam a [política de proteção de aplicações do Intune](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) em aplicações iOS e Android criadas com o Xamarin. Os enlacem permitem aos programadores criar facilmente funcionalidades de proteção de aplicações do Intune na respetiva aplicação baseada no Xamarin.

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

* **[Apenas Android]** A mais recente aplicação do Portal da Empresa do Microsoft Intune tem de ser instalada no dispositivo.

## <a name="get-started"></a>Introdução

1. Leia os [termos de licenciamento](https://components.xamarin.com/license/microsoft.intune.mam) do Componente Xamarin da MAM do Microsoft Intune.

2.  Transfira a pasta do Componente Xamarin do SDK da Aplicação Intune a partir do [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) ou do [Nuget.org](https://www.nuget.org/profiles/msintuneappsdk) e extraia-a. Ambos os ficheiros transferidos nos passos 1 e 3 devem estar no mesmo nível de diretório.

3.  Na linha de comandos como administrador, execute o ficheiro `Xamarin.Component.exe install <.xam> file`.

4.  No Visual Studio, clique com o botão direito do rato em **componentes** no projeto Xamarin criado anteriormente.

5.  Selecione **Editar Componentes** e adicione o componente do SDK da Aplicação Intune transferido localmente para o seu computador.

Reveja os [termos de licenciamento](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf). Imprimir e guardar uma cópia dos termos de licenciamento nos seus registos. Ao transferir e utilizar os Enlaces Xamarin do SDK da Aplicação Intune, aceita esses termos de licenciamento. Caso não aceite os termos, não deverá utilizar o software.

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

Para aplicações para Android baseadas no Xamarin que não utilizam uma estrutura de IU, tem de consultar e seguir o [Guia para Programadores do SDK da Aplicação Intune para Android](app-sdk-android.md). Para a sua aplicação para Android baseada no Xamarin, tem de substituir a classe, os métodos e as atividades na respetiva MAM equivalente com base na [tabela](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent) incluída no guia. Se a aplicação não definir uma classe `android.app.Application`, tem de criar uma e garantir que é herdada de `MAMApplication`.

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

Concluiu os passos básicos de incorporação do componente na aplicação. Agora, pode seguir os passos incluídos no exemplo de aplicação Xamarin para Android. Fornecemos dois exemplos, um para Xamarin.Forms e outro para Android.

## <a name="requiring-intune-app-protection-policies-in-order-to-use-your-xamarin-based-android-lob-app-optional"></a>Exigir políticas de proteção de aplicações do Intune de forma a utilizar a sua aplicação LOB para Android baseada no Xamarin (opcional) 

Seguem-se orientações para garantir que as aplicações LOB para Android baseadas no Xamarin só podem ser utilizadas por utilizadores protegidos pelo Intune nos respetivos dispositivos. 

### <a name="general-requirements"></a>Requisitos Gerais
* A equipa do SDK do Intune irá exigir o ID da Aplicação da sua aplicação. Essa informação encontra-se no [Portal do Azure](https://portal.azure.com/), em **Todas as Aplicações**, na coluna do **ID da Aplicação**. Uma excelente forma de contactar a equipa do SDK do Intune é através do envio de um e-mail para msintuneappsdk@microsoft.com.
     
### <a name="working-with-the-intune-sdk"></a>Trabalhar com o SDK do Intune
Estas instruções são específicas para todas as aplicações Android e Xamarin que pretendam exigir políticas de proteção de aplicações do Intune para utilização num dispositivo de utilizador final.

1. Configure a ADAL através dos passos definidos no [guia do SDK do Intune para Android](https://docs.microsoft.com/en-us/intune/app-sdk-android#configure-azure-active-directory-authentication-library-adal).
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
> [!NOTE] 
> A próxima versão que a ADAL .NET lançará (3.17.4) deverá ter a correção necessária para que isto funcione.

Se a sua organização for um cliente do Intune existente, trabalhe com o seu representante de suporte da Microsoft para abrir um pedido de suporte e criar um problema [na página de problemas do GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) e iremos ajudar assim que possível. 

