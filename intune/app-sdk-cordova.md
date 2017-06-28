---
title: "Plug-in Cordova do SDK da Aplicação Microsoft Intune"
description: 
keywords: sdk, Cordova, intune
author: oydang
manager: angrobe
ms.author: oydang
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb940cb9-d43f-45ca-b065-ac0adc61dc6f
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 0329720b6f02c718ef27a59e6efc5f3a76eed1c5
ms.contentlocale: pt-pt
ms.lasthandoff: 06/08/2017


---
# <a name="microsoft-intune-app-sdk-cordova-plugin"></a>Plug-in Cordova do SDK da Aplicação Microsoft Intune

> [!NOTE]
> Pode ler primeiro o artigo [Introdução ao SDK da Aplicação Intune](app-sdk-get-started.md), que explica como preparar a integração em cada plataforma suportada.

## <a name="overview"></a>Descrição geral

O [Plug-in Cordova do SDK da Aplicação Intune](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) em aplicações Android e iOS criadas com o Cordova. O plug-in permite aos programadores integrar funcionalidades de proteção de aplicações e dados do Intune na respetiva aplicação baseada no Cordova.

Verá que pode ativar funcionalidades SDK sem alterar o comportamento da aplicação. Após incorporar o plug-in na aplicação para iOS ou Android, o administrador do Microsoft Intune poderá implementar a política de proteção de aplicações do Intune, que consiste numa variedade de funcionalidades de proteção de dados. O plug-in foi criado para que a maioria dos passos seja executada automaticamente no processo de compilação do Cordova. Por conseguinte, deverá poder ativar rapidamente a aplicação para a proteção de aplicações do Intune. Para começar, siga os passos abaixo, com base na sua plataforma de destino.

## <a name="supported-platforms"></a>Plataformas Suportadas

* O plug-in funciona no SO Windows, Mac e Linux
* O plug-in funciona em aplicações Android com `minSdkVersion` >= 14 e `targetSdkVersion` <= 24
* O plug-in funciona em aplicações iOS orientadas para o iOS 9.0 e superiores.

## <a name="intune-mobile-application-management-scenarios"></a>Cenários de Gestão de Aplicações Móveis do Intune

* Dispositivos inscritos na MDM do Intune
* Dispositivos inscritos na EMM de terceiros
* Dispositivos não geridos (não inscritos com qualquer MDM)

As aplicações Cordova compiladas com o plug-in Cordova do SDK da Aplicação Intune podem agora receber políticas de proteção de aplicações do Intune em dispositivos inscritos na gestão de dispositivos móveis (MDM) do Intune e em dispositivos não inscritos.

## <a name="prerequisites"></a>Pré-requisitos

### <a name="android"></a>Android

* A mais recente aplicação do Portal da Empresa do Microsoft Intune tem de ser sempre instalada no dispositivo.
* No mínimo, o Java 7 tem de estar no caminho onde executará a compilação Cordova quando utilizar o plug-in.

### <a name="ios"></a>iOS

* A mais recente aplicação do Portal da Empresa do Microsoft Intune tem de ser instalada no dispositivo para as funcionalidades de MDM. *Não* é precisa para a política de proteção de aplicações do Intune sem funcionalidades de inscrição de dispositivos.

### <a name="both-platforms"></a>Ambas as plataformas

* É necessária a versão 0.8.0+ do [plug-in Azure Active Directory Authentication Libraries (ADAL) para Cordova](https://github.com/AzureAD/azure-activedirectory-library-for-cordova).

> [!NOTE]
> Devido a um erro do Cordova no Apache, arquivado [aqui](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22), as aplicações que já têm a dependência de plug-in não irão atualizar automaticamente o plug-in para a versão solicitada.



## <a name="quick-start"></a>Guia de Introdução

1. Atualize a versão do ADAL:

  ```shell
  cordova plugin remove cordova-plugin-ms-adal
  cordova plugin add cordova-plugin-ms-adal@0.8.x
  ```

2. Adicione o SDK da Aplicação Intune para o plug-in Cordova:

  ```shell
  cordova plugin add cordova-plugin-ms-intune-mam
  ```

## <a name="build-the-plugin-into-your-ios-app"></a>Incorporar o plug-in na aplicação iOS

Terá de concluir alguns passos para que a aplicação fique ativada para a política de proteção de aplicações do Intune. Para sua comodidade, os seguintes passos são efetuados automaticamente no processo de compilação do Cordova como hook de pré-compilação. Por conseguinte, os passos automáticos modificarão os ficheiros `*.pbxproj`, `*-Info.plist` e `*.entitlements` associados uma configuração de projeto. Se o projeto não contiver um ficheiro de elegibilidades, o plug-in irá criar um automaticamente.

Esta configuração suporta apenas um único destino e será efetuada no primeiro destino encontrado se existirem múltiplos destinos. Se o processo falhar, verifique se:

1. O projeto Xcode da sua aplicação é `[name].xcodeproj`, em que `[name]` é o valor definido em `config.xml`
2. O projeto utiliza a [estrutura de diretórios de aplicações padrão do Cordova](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure).

## <a name="build-the-plugin-into-your-android-app"></a>Incorporar o plug-in na aplicação para Android

1. Importe este plug-in com as ferramentas do Cordova mais recentes. O plug-in será invocado automaticamente como um passo `after_compile`.

2. O plug-in criará uma versão ativada para Intune de um ficheiro apk compilado (Android API 14 e superior) no fim do processo de compilação. O resultado da compilação irá conter um `[Project]-intunewrapped-[Build_Configuration].apk` (por exemplo, `helloWorld-intunewrapped-debug.apk`).

> [!NOTE]
> O plug-in só suporta compilações do Gradle.

Devido a um erro do Cordova arquivado [aqui](https://issues.apache.org/jira/browse/CB-9434) que faz com que determinados hooks do Cordova sejam ignorados em `cordova run`, para executar a aplicação encapsulada na linha de comandos, tem de fazer o seguinte:

```shell
$ cordova build
$ cordova run --nobuild
```

## <a name="sign-your-android-app"></a>Assinar a aplicação Android

O plug-in reconhece automaticamente as informações de assinatura que facultou ao Cordova nas seguintes localizações:

* platforms/android/debug-signing.properties
* platforms/android/release-signing.properties
* res/native/android/ant.properties

Veja as [informações de assinatura do Gradle do Cordova ](https://cordova.apache.org/docs/en/latest/guide/platforms/android/#using-gradle) para obter mais informações sobre o formato esperado.

Atualmente, não suportamos a capacidade de facultar informações de assinatura em `build.json` ou em localizações arbitrárias facultadas através de parâmetros para a compilação do Cordova.

## <a name="debugging-from-visual-studio"></a>Depuração no Visual Studio

Depois de iniciar a aplicação pela primeira vez, deverá ver uma caixa de diálogo a notificá-lo de que a aplicação é gerida pelo Intune. Clique em "Não voltar a mostrar" e clique novamente no botão de depuração/execução do VS para obter os pontos de interrupção a clicar.

## <a name="known-limitations"></a>Limitações conhecidas

### <a name="android"></a>Android

* O suporte para MultiDex é incompleto.
* A aplicação tem de ter `minSdkVersion` de 14 e `targetSdkVersion` de 24 ou abaixo. Atualmente, não suportamos aplicações orientadas para a API 25
* Não podemos voltar a assinar aplicações que tenham sido assinadas com o Esquema de Assinatura V2. Quando as aplicações assinadas com o V2 são encapsuladas pelo plug-in, a assinatura do .apk de saída encapsulada será cancelada.
*
  * Pode desativar a Assinatura V2 predefinida do Cordova ao adicionar o seguinte ao ficheiro `build-extras.gradle`:

  ```gradle
  android {
      signingConfigs {
          release {
              v2SigningEnabled false
          }
          debug {
              v2SigningEnabled false
          }
      }
      buildTypes {
          release {
              signingConfig signingConfigs.release
          }
          debug {
              signingConfig signingConfigs.debug
          }
      }
  }
  ```

### <a name="ios"></a>iOS

* Sempre que modificar a lista de UTIs no nó **CFBundleDocumentTypes** do ficheiro **Info.plist**, tem de limpar os UTIs do Intune na secção UTIs Importados do mesmo ficheiro plist (nó **UTImportedTypeDeclarations**), antes de compilar novamente. Todos os UTIs do Intune serão iniciados com o prefixo `com.microsoft.intune.mam`.

* Se quiser remover o plug-in do SDK da Aplicação Intune para Cordova do seu projeto Cordova, terá de remover também a plataforma iOS e voltar a adicioná-la para anular algumas das configurações do Intune nos ficheiros .xcodeproj e .plist.

