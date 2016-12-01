---
title: "Componente Xamarin do SDK da Aplicação Microsoft Intune | Microsoft Intune"
description: 
keywords: sdk, Xamarin, intune
author: oydang
manager: karthikaraman
ms.author: oydang
ms.date: 11/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: karthikaraman
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ca4623db80d711f3543b6d688fb1bb1ef228c62c
ms.openlocfilehash: e2d43fff8772046fe7426b267e39d53b278d4e5c


---

# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Componente Xamarin do SDK da Aplicação Microsoft Intune

## <a name="overview"></a>Descrição Geral
O [Componente Xamarin do SDK da Aplicação Intune](https://components.xamarin.com/view/microsoft.intune.mam) proporciona [funcionalidades de gestão de aplicações móveis do Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) em aplicações para iOS e Android compiladas com o Xamarin. O componente permite aos programadores compilar facilmente em funcionalidades de restrição de aplicações e de proteção de dados na respetiva aplicação baseada no Xamarin.

Verá que pode ativar funcionalidades SDK sem alterar o comportamento da sua aplicação. Depois de incorporar o componente na sua aplicação móvel para iOS ou Android, o administrador de TI poderá implementar a política através do Microsoft Intune com uma variedade de funcionalidades que permitem a proteção de dados.

## <a name="supported-scenarios"></a>Cenários Suportados

### <a name="platforms"></a>Plataformas
* Android
* iOS


### <a name="emm-scenarios"></a>Cenários de EMM

* MAM do Intune em dispositivos inscritos na MDM do Intune
* MAM do Intune em dispositivos inscritos na EMM de terceiros
* MAM do Intune em dispositivos não inscritos e não geridos

As aplicações Xamarin compiladas com o Componente Xamarin do SDK da Aplicação Intune podem agora receber políticas de gestão de aplicações móveis (MAM) do Intune em dispositivos inscritos na gestão de dispositivos móveis (MDM) do Intune e em dispositivos não inscritos.

## <a name="prerequisites"></a>Pré-requisitos

* **[Apenas Android]** A mais recente aplicação do Portal da Empresa do Microsoft Intune tem de ser sempre instalada no dispositivo.

## <a name="get-started"></a>Introdução

1.  Transfira o ficheiro **Xamarin component.exe** a partir [daqui](https://components.xamarin.com/submit/xpkg) e extraia-o.

2. Leia os [termos de licenciamento](https://components.xamarin.com/license/microsoft.intune.mam) do Componente Xamarin da MAM do Microsoft Intune.

3.  Transfira a pasta do Componente Xamarin do SDK da Aplicação Intune a partir do [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) ou do [Xamarin](https://components.xamarin.com/license/microsoft.intune.mam) e extraia-a. Ambos os ficheiros transferidos nos passos 1 e 2 devem estar no mesmo nível de diretório.

4.  Na linha de comandos como administrador, execute o ficheiro `Xamain.Component.exe install <.xam> file`.

5.  No Visual Studio, clique com o botão direito do rato em **componentes** no projeto Xamarin criado anteriormente.

6.  Selecione **Editar Componentes** e adicione o componente do SDK da Aplicação Intune transferido localmente para o seu computador.



## <a name="enabling-intune-mam-in-your-ios-mobile-app"></a>Ativar a MAM do Intune na aplicação móvel para iOS
1.  Para inicializar o SDK da Aplicação Intune, terá de efetuar uma chamada para qualquer API na classe `AppDelegate.cs`. Por exemplo:

      ```csharp
      public override bool FinishedLaunching (UIApplication application, NSDictionary launchOptions)
      {
            Console.WriteLine ("Is Managed: {0}", IntuneMAMPolicyManager.Instance.PrimaryUser != null);
            return true;
      }

      ```

2.  Agora que o componente foi adicionado e inicializado, pode seguir os passos gerais necessários para incorporar o SDK da Aplicação numa aplicação móvel para iOS. Pode encontrar a documentação completa para ativar as aplicações iOS nativas no [Guia para Programadores do SDK da Aplicação Intune para iOS](intune-app-sdk-ios).
3. **Importante**: existem vários modificações específicas de aplicações para iOS baseadas no Xamarin. Por exemplo, ao ativar os grupos de keychain, terá de adicionar o seguinte para incluir o exemplo de aplicação Xamarin que incluímos no componente. Segue-se um exemplo dos grupos que teria de ter nos seus grupos de Acesso Keychain:

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

Concluiu os passos necessários para incorporar o componente na aplicação para iOS baseada no Xamarin. Se estiver a utilizar o Xcode para compilar o projeto, pode utilizar o `Intune App SDK Settings.bundle`. Isto permitir ativar e desativar as definições de política do Intune enquanto compila o projeto para testar e depurar. Para tirar partido deste pacote, siga os passos indicados no [Guia para Programadores do SDK da Aplicação Intune para iOS](intune-app-sdk-ios) e consulte a secção sobre [depuração no Xcode](intune-app-sdk-ios#debug-information).

## <a name="enabling-mam-in-your-android-mobile-app"></a>Ativar a MAM na aplicação móvel para Android
Para aplicações para Android baseadas no Xamarin que não utilizam uma estrutura de IU, terá de consultar e seguir o [Guia para Programadores do SDK da Aplicação Intune para Android]. Para a sua aplicação para Android baseada no Xamarin, terá de substituir a classe, os métodos e as atividades na respetiva MAM equivalente com base na [tabela](intune-app-sdk-android#replace-classes-methods-and-activities-with-their-mam-equivalent-required) incluída no guia. Se a aplicação não definir uma classe `android.app.Application`, terá de criar uma e garantir que é herdada de `MAMApplication`.

Para Xamarin.Forms e outras estruturas de IU, fornecemos uma ferramenta denominada `MAM.Remapper`. A ferramenta irá efetuar a substituição da classe. No entanto, terá de executar os seguintes passos:

1.  Adicione uma referência à versão 0.1.0.0 ou superior do pacote NuGet ` Microsoft.Intune.MAM.Remapper.Tasks`.

2.  Adicione a seguinte linha ao csproj para Android:
  ```xml
  <Import
  Project="$(NugetPack)\\Microsoft.Intune.MAM.Remapper.Tasks.0.1.X.X\\build\\MonoAndroid10\\Microsoft.Intune.MAM.Remapper.targets" />
  ```

3.  Defina a ação de compilação do ficheiro `remapping-config.json` adicionado para **RemappingConfigFile**. O `remapping-config.json` incluído só funciona com Xamarin.Forms. Para outras estruturas de IU, consulte o ficheiro Readme incluído no pacote NuGet Remapper.

## <a name="test-your-app"></a>Testar a sua aplicação

Concluiu os passos básicos de incorporação do componente na aplicação. Agora, pode seguir os passos incluídos no exemplo de aplicação Xamarin para Android. Fornecemos dois exemplos, um para Xamarin.Forms e outro para Android.



<!--HONumber=Nov16_HO3-->


