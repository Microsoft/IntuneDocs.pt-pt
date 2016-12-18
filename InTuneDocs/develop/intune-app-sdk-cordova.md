---
title: "Plug-in Cordova do SDK da Aplicação Microsoft Intune | Documentos da Microsoft"
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
translationtype: Human Translation
ms.sourcegitcommit: 613e293d9bd853d6de7cdc0d753cc8473afc180b
ms.openlocfilehash: 9ef09f43e6c878af689a500457bab578149de499


---
# <a name="microsoft-intune-app-sdk-cordova-plugin"></a>Plug-in Cordova do SDK da Aplicação Microsoft Intune

> [!NOTE]
> Pode ler primeiro o artigo [Introdução ao SDK da Aplicação Intune](intune-app-sdk-get-started.md), que explica como preparar a integração em cada plataforma suportada.


## <a name="overview"></a>Descrição geral

O [Plug-in Cordova do SDK da Aplicação Intune](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam) proporciona [funcionalidades de gestão de aplicações móveis do Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) em aplicações iOS e Android compiladas com o Cordova. O plug-in permite aos programadores integrar funcionalidades de proteção de aplicações e dados do Intune na respetiva aplicação baseada no Cordova.

Verá que pode ativar funcionalidades SDK sem alterar o comportamento da sua aplicação. Depois de incorporar o plug-in na sua aplicação móvel para iOS ou Android, o administrador de TI poderá implementar a política através da Gestão de Aplicações Móveis (MAM) do Microsoft Intune com uma variedade de funcionalidades de proteção de dados. Criámos o plug-in para que a maioria dos passos seja executada automaticamente no processo de compilação do Cordova. Por conseguinte, deverá poder ativar rapidamente a sua aplicação para gestão. Para começar, siga os passos abaixo, com base na sua plataforma de destino.




## <a name="whats-supported"></a>O que é suportado?

### <a name="developer-machines"></a>Máquinas do programador
* Windows
* Mac OS


### <a name="mobile-app-platforms"></a>Plataformas de aplicações móveis
* Android 4.0+
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Cenários de Gestão de Aplicações Móveis do Intune

* Dispositivos inscritos na MDM do Intune
* Dispositivos inscritos na EMM de terceiros
* Dispositivos não geridos (não inscritos com qualquer MDM)

As aplicações Cordova compiladas com o plug-in Cordova do SDK da Aplicação Intune podem agora receber políticas de gestão de aplicações móveis (MAM) do Intune em dispositivos inscritos na gestão de dispositivos móveis (MDM) do Intune e em dispositivos não inscritos.



## <a name="prerequisites"></a>Pré-requisitos

### <a name="technical-prerequisites"></a>Pré-requisitos técnicos

* **[Apenas Android]** A mais recente aplicação do Portal da Empresa do Microsoft Intune tem de ser sempre instalada no dispositivo.


* É necessária a versão 0.8.0+ do [plug-in Azure Active Directory Authentication Libraries (ADAL) para Cordova](https://github.com/AzureAD/azure-activedirectory-library-for-cordova).
  * **Importante:** devido a um erro do Cordova no Apache arquivado [aqui](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22), as aplicações que já têm a dependência de plug-in não irão atualizar automaticamente o plug-in para a versão solicitada.


### <a name="before-you-install-and-use-microsoft-intune-app-sdk-cordova-plugin-you-must"></a>Antes de instalar e utilizar o plug-in Cordova do SDK da Aplicação Microsoft Intune, **tem de**:

* Consultar os [Termos de Licenciamento do Plug-in Cordova do SDK da Aplicação do Intune](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam/blob/master/Intune_App_SDK_Cordova_plugin_RTM_license.pdf).

* Imprimir e guardar uma cópia dos termos de licenciamento nos seus registos. Ao transferir e utilizar o plug-in Cordova do SDK da Aplicação Intune para iOS aceita esses termos de licenciamento.  Caso não aceite os termos, não deverá utilizar o software.


## <a name="quick-start"></a>Guia de Introdução

1. Atualize a versão do ADAL:

    ```
    cordova plugin remove cordova-plugin-ms-adal
    cordova plugin add cordova-plugin-ms-adal@0.8.x
    ```

2. Adicione o SDK da Aplicação Intune para o plug-in Cordova:

    ```
    cordova plugin add cordova-plugin-ms-intune-mam
    ```

## <a name="how-to-build-the-plugin-into-your-ios-app"></a>Como incorporar o plug-in na aplicação iOS

Terá de concluir alguns passos para que a sua aplicação fique ativada para a MAM do Intune. Para sua comodidade, os seguintes passos são efetuados automaticamente no processo de compilação do Cordova como hook de pré-compilação. Por conseguinte, os passos automáticos modificarão os ficheiros `*.pbxproj`, `*-Info.plist` e `*.entitlements` associados uma configuração de projeto. Se o projeto não contiver um ficheiro de elegibilidades, o plug-in irá criar um automaticamente.

Esta configuração suporta apenas um único destino e será efetuada no primeiro destino encontrado se existirem múltiplos destinos. Se o processo falhar, verifique se:

1. O projeto Xcode da sua aplicação é `[name].xcodeproj`, em que `[name]` é o valor definido em `config.xml`
2. O projeto utiliza a [estrutura de diretórios de aplicações padrão do Cordova](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure).

## <a name="how-to-build-the-plugin-into-your-android-app"></a>Como incorporar o plug-in na sua aplicação para Android

1. Importe este plug-in com as ferramentas do Cordova mais recentes. O plug-in será invocado automaticamente como um passo `after_compile`.

2. O plug-in irá criar uma versão ativada para MAM de um ficheiro apk compilado (Android API 14+) no fim do processo de compilação. O resultado da compilação irá conter um `[Project]-intunewrapped-[Build_Configuration].apk` (por exemplo, `helloWorld-intunewrapped-debug.apk`).

O plug-in só suporta compilações do Gradle.

Devido a um erro do Cordova arquivado [aqui](https://issues.apache.org/jira/browse/CB-9434) que faz com que determinados hooks do Cordova sejam ignorados em `cordova run`, para executar a aplicação encapsulada na linha de comandos, tem de fazer o seguinte:

```
$ cordova build
$ cordova run --nobuild
```


### <a name="signing-your-android-app"></a>Assinar a sua aplicação Android
Para adicionar informações de assinatura ao ficheiro apk encapsulado, modifique `build.json` como faria normalmente para adicionar informações de assinatura. Por exemplo:
```json
{
  "android": {
    "release": {
      "keystore": "your.keystore",
      "storePassword": "yourpassword",
      "alias": "youralias",
      "password" : "yourpassword",
      "keystoreType": ""
    }
  }
}
```

### <a name="build-for-android-test-only"></a>Compilar apenas para testar em Android

1. Adicione `android:testOnly="true"` ao nó da aplicação do ficheiro `AndroidManifest.xml`.


2. **Cordova 6.x.x:** em `[PROJECT_ROOT]/platforms/android/cordova/lib/Adb.js`, altere a linha 60 de

    ```javascript
    var args = ['-s', target, 'install'];
    ```
    como
    ```javascript
    var args = ['-s', target, 'install', '-t'];
    ```

O efeito desta ação é executar `adb install` com o sinalizador "-t", uma vez que as aplicações `testOnly` não podem ser instaladas sem o mesmo.

### <a name="debugging-from-visual-studio"></a>Depuração no Visual Studio
Depois de iniciar a aplicação pela primeira vez, deverá ver uma caixa de diálogo a notificá-lo de que a aplicação é gerida pelo Intune. Clique em "Não voltar a mostrar" e clique novamente no botão de depuração/execução do VS para obter os pontos de interrupção a clicar.

## <a name="known-limitations"></a>Limitações conhecidas
### <a name="android"></a>Android
* O suporte para MultiDex é incompleto.
* A aplicação tem de se destinar ao Android 4.0 (API 14 do Android) ou superior.

### <a name="ios"></a>iOS
* Sempre que modificar a lista de UTIs no nó **CFBundleDocumentTypes** do ficheiro **Info.plist**, tem de limpar os UTIs do Intune na secção UTIs Importados do mesmo ficheiro plist (nó **UTImportedTypeDeclarations**), antes de compilar novamente. Todos os UTIs do Intune serão iniciados com o prefixo `com.microsoft.intune.mam`.

* Se quiser remover o plug-in do Intune do projeto Cordova, tem de remover também a plataforma iOS e voltar a adicioná-la para anular algumas das configurações do Intune nos ficheiros .xcodeproj e .plist.



<!--HONumber=Dec16_HO2-->


