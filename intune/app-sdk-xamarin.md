---
title: "Componente Xamarin do SDK da Aplicação Microsoft Intune"
description: 
keywords: sdk, Xamarin, intune
author: erikre
manager: angrobe
ms.author: erikre
ms.date: 11/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 73caf124e94994acf816c98f0788efdabe024cc4
ms.sourcegitcommit: c3bd0d192d712fcfd52f64dd1377155796239fcb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Componente Xamarin do SDK da Aplicação Microsoft Intune

> [!NOTE]
> Pode ler primeiro o artigo [Introdução ao SDK da Aplicação Intune](app-sdk-get-started.md), que explica como preparar a integração em cada plataforma suportada.



## <a name="overview"></a>Descrição geral
O [Componente Xamarin do SDK da Aplicação Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) ativa a [política de proteção de aplicações do Intune](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) em aplicações para iOS e Android compiladas com o Xamarin. O componente permite aos programadores incorporar facilmente funcionalidades de proteção da aplicação do Intune na respetiva aplicação baseada no Xamarin.

> [!NOTE]
> O suporte para o SDK do Intune para Xamarin está atualmente disponível na pré-visualização. 

O Componente Xamarin do SDK da Aplicação Microsoft Intune permite-lhe incorporar as políticas de proteção de aplicações do Intune (também conhecidas como políticas de APLICAÇÕES ou MAM) nas suas aplicações desenvolvidas com o Xamarin. Uma aplicação preparada para MAM é uma aplicação que está integrada com o SDK da Aplicação do Intune. Os administradores de TI podem implementar políticas de proteção de aplicações na aplicação móvel quando o Intune está a gerir a aplicação de forma ativa.

## <a name="whats-supported"></a>O que é suportado?

### <a name="developer-machines"></a>Máquinas do programador
* macOS


### <a name="mobile-app-platforms"></a>Plataformas de aplicações móveis
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Cenários de Gestão de Aplicações Móveis do Intune

* Dispositivos inscritos na MDM do Intune
* Dispositivos inscritos na EMM de terceiros
* Dispositivos não geridos (não inscritos com qualquer MDM)

As aplicações Xamarin compiladas com o Componente Xamarin do SDK da Aplicação do Intune podem agora receber políticas de proteção de aplicações do Intune em dispositivos inscritos na gestão de dispositivos móveis (MDM) do Intune e em dispositivos não inscritos.

## <a name="prerequisites"></a>Pré-requisitos

* **[Apenas Android]** A mais recente aplicação do Portal da Empresa do Microsoft Intune tem de ser instalada no dispositivo.

## <a name="get-started"></a>Introdução

1.  Transfira o ficheiro **Xamarin component.exe** a partir [daqui](https://components.xamarin.com/submit/xpkg) e extraia-o.

2. Leia os [termos de licenciamento](https://components.xamarin.com/license/microsoft.intune.mam) do Componente Xamarin da MAM do Microsoft Intune.

3.  Transfira a pasta do Componente Xamarin do SDK da Aplicação Intune a partir do [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) ou do [Nuget.org](https://www.nuget.org/profiles/msintuneappsdk) e extraia-a. Ambos os ficheiros transferidos nos passos 1 e 3 devem estar no mesmo nível de diretório.

4.  Na linha de comandos como administrador, execute o ficheiro `Xamarin.Component.exe install <.xam> file`.

5.  No Visual Studio, clique com o botão direito do rato em **componentes** no projeto Xamarin criado anteriormente.

6.  Selecione **Editar Componentes** e adicione o componente do SDK da Aplicação Intune transferido localmente para o seu computador.



## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Ativar as políticas de proteção de aplicações do Intune na sua aplicação móvel iOS
1.  Siga os passos gerais necessários para integrar o SDK da Aplicação Intune numa aplicação móvel iOS. Pode começar com o passo 3 das instruções de integração do [Guia para Programadores do SDK da Aplicação Intune para iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app).
    **Importante**: a ativação da partilha de keychain para uma aplicação é ligeiramente diferente no Visual Studio a partir do Xcode. Abra a plist de Elegibilidade da aplicação e garanta que a opção “Ativar Keychain” está ativada e que são adicionados os grupos de partilha de keychain adequados nessa secção. Em seguida, garanta que a plist de Elegibilidade está especificada no campo “Elegibilidades Personalizadas” das opções “Assinatura de Pacotes iOS” do projeto para todas as combinações de Configuração/Plataforma adequadas.
2.  Depois de o componente ser adicionado e a aplicação estar configurada corretamente, a aplicação pode começar a utilizar as APIs do SDK do Intune. Para tal, tem de incluir o seguinte espaço de nomes:

      ```csharp
      using Microsoft.Intune.MAM;
      ```
3.    Para começar a receber políticas de proteção de aplicações, tem de inscrever a aplicação no serviço do Intune MAM. Se a sua aplicação já utilizar a Azure Active Directory Authentication Library (ADAL) para autenticar os utilizadores, a aplicação deverá disponibilizar o UPN do utilizador ao método registerAndEnrollAccount do IntuneMAMEnrollmentManager depois de ter realizado a autenticação com êxito:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **Importante**: não se esqueça de substituir as predefinições da ADAL do SDK da Aplicação Intune pelas predefinições da sua aplicação. Pode fazê-lo através do dicionário IntuneMAMSettings no ficheiro Info.plist da aplicação, tal como mencionado no [Guia para Programadores do SDK da Aplicação Intune para iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk), ou pode utilizar as propriedades de substituição do AAD da instância IntuneMAMPolicyManager. A abordagem do ficheiro Info.plist é recomendada para aplicações cujas definições da ADAL sejam estáticas, enquanto as propriedades de substituição são recomendadas para aplicações que determinem esses valores no runtime. 
      
      Se a aplicação não utilizar a ADAL e quiser que o SDK do Intune processe a autenticação, a aplicação deverá chamar o método loginAndEnrollAccount do IntuneMAMEnrollmentManager:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>Ativar as políticas de proteção de aplicações na sua aplicação móvel Android
Para aplicações para Android baseadas no Xamarin que não utilizam uma estrutura de IU, tem de consultar e seguir o [Guia para Programadores do SDK da Aplicação Intune para Android](app-sdk-android.md). Para a sua aplicação para Android baseada no Xamarin, tem de substituir a classe, os métodos e as atividades na respetiva MAM equivalente com base na [tabela](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent) incluída no guia. Se a aplicação não definir uma classe `android.app.Application`, tem de criar uma e garantir que é herdada de `MAMApplication`.

Para Xamarin.Forms e outras estruturas de IU, fornecemos uma ferramenta denominada `MAM.Remapper`. A ferramenta efetua a substituição da classe. No entanto, tem de executar os seguintes passos:

1.  Adicione uma referência à versão 0.1.0.0 ou superior do pacote NuGet `Microsoft.Intune.MAM.Remapper.Tasks`.

2.  Adicione a seguinte linha ao csproj para Android:
  ```xml
  <Import
  Project="$(NugetPack)\\Microsoft.Intune.MAM.Remapper.Tasks.0.1.X.X\\build\\MonoAndroid10\\Microsoft.Intune.MAM.Remapper.targets" />
  ```

3.  Defina a ação de compilação do ficheiro `remapping-config.json` adicionado para **RemappingConfigFile**. O `remapping-config.json` incluído só funciona com Xamarin.Forms. Para outras estruturas de IU, veja o ficheiro Readme incluído no pacote NuGet Remapper.

## <a name="next-steps"></a>Próximos passos

Concluiu os passos básicos de incorporação do componente na aplicação. Agora, pode seguir os passos incluídos no exemplo de aplicação Xamarin para Android. Fornecemos dois exemplos, um para Xamarin.Forms e outro para Android.
