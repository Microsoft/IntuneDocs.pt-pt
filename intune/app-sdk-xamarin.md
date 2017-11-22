---
title: "Componente Xamarin do SDK da Aplicação Microsoft Intune"
description: 
keywords: sdk, Xamarin, intune
author: mattbriggs
manager: angrobe
ms.author: mabriggs
ms.date: 11/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f50ecfbf5a0ac0b05de38e0ad29b27a729ab824b
ms.sourcegitcommit: 0f877251e6adf4e45b918cc8dc9193626727f2d9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/03/2017
---
# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Componente Xamarin do SDK da Aplicação Microsoft Intune

> [!NOTE]
> Pode ler primeiro o artigo [Introdução ao SDK da Aplicação Intune](app-sdk-get-started.md), que explica como preparar a integração em cada plataforma suportada.



## <a name="overview"></a>Descrição geral
O [Componente Xamarin do SDK da Aplicação Intune](https://components.xamarin.com/view/microsoft.intune.mam) ativa a [política de proteção de aplicações do Intune](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) em aplicações para iOS e Android compiladas com o Xamarin. O componente permite aos programadores incorporar facilmente funcionalidades de proteção da aplicação do Intune na respetiva aplicação baseada no Xamarin.

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

3.  Transfira a pasta do Componente Xamarin do SDK da Aplicação Intune a partir do [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) ou do [Xamarin](https://components.xamarin.com/license/microsoft.intune.mam) e extraia-a. Ambos os ficheiros transferidos nos passos 1 e 3 devem estar no mesmo nível de diretório.

4.  Na linha de comandos como administrador, execute o ficheiro `Xamarin.Component.exe install <.xam> file`.

5.  No Visual Studio, clique com o botão direito do rato em **componentes** no projeto Xamarin criado anteriormente.

6.  Selecione **Editar Componentes** e adicione o componente do SDK da Aplicação Intune transferido localmente para o seu computador.



## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Ativar as políticas de proteção de aplicações do Intune na sua aplicação móvel iOS
1.  Para inicializar o SDK da Aplicação Intune, tem de efetuar uma chamada para qualquer API na classe `AppDelegate.cs`. Por exemplo:

      ```csharp
      public override bool FinishedLaunching (UIApplication application, NSDictionary launchOptions)
      {
            Console.WriteLine ("Is Managed: {0}", IntuneMAMPolicyManager.Instance.PrimaryUser != null);
            return true;
      }

      ```

2.  Agora que o componente foi adicionado e inicializado, pode seguir os passos gerais necessários para incorporar o SDK da Aplicação numa aplicação móvel para iOS. Pode encontrar a documentação completa para ativar as aplicações iOS nativas no [Guia para Programadores do SDK da Aplicação Intune para iOS](app-sdk-ios.md).
3. **Importante**: existem vários modificações específicas de aplicações para iOS baseadas no Xamarin. Por exemplo, ao ativar os grupos de keychain, tem de adicionar o seguinte para incluir o exemplo de aplicação Xamarin que incluímos no componente. Segue-se um exemplo dos grupos que teria de ter nos seus grupos de Acesso Keychain:

      ```xml
      <?xml version="1.0" encoding="UTF-8"?>
      <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
      <plist version="1.0">
            <dict>
                  <key>keychain-access-groups</key>
                  <array>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample</string>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample.intunemam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.intune.mam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.adalcache</string>
                  </array>
            </dict>
      </plist>
      ```

Concluiu os passos necessários para incorporar o componente na aplicação para iOS baseada no Xamarin. Se estiver a utilizar o Xcode para compilar o projeto, pode utilizar o `Intune App SDK Settings.bundle`. Isto permite ativar e desativar as definições de política do Intune enquanto compila o projeto para testar e depurar. Para tirar partido deste pacote, siga os passos indicados no [Guia para Programadores do SDK da Aplicação Intune para iOS](app-sdk-ios.md) e consulte a secção sobre [depuração no Xcode](app-sdk-ios.md#status-result-and-debug-notifications).

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
