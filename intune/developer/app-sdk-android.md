---
title: Guia para programadores do SDK da Aplicação do Microsoft Intune para Android
description: O SDK da Aplicação do Microsoft Intune para Android permite incorporar a gestão de aplicações móveis (MAM) do Intune na sua aplicação Android.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c8c5be1d7a02c2c8329afe05dcdce22f48c49d05
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503485"
---
# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Guia para programadores do SDK da Aplicação do Microsoft Intune para Android

> [!NOTE]
> Pode ser útil ler primeiro a [Descrição geral do SDK da Aplicação do Intune](app-sdk.md), que abrange as funcionalidades atuais do SDK e descreve como preparar a integração em cada plataforma suportada.

O SDK da Aplicação do Microsoft Intune para Android permite-lhe incorporar as políticas de proteção de aplicações do Intune (também conhecidas como políticas de **APLICAÇÕES** ou MAM) na aplicação Android nativa. Uma aplicação gerida pelo Intune é uma aplicação que está integrada com o SDK da Aplicação Intune. Os administradores do Intune podem facilmente implementar políticas de proteção de aplicações na sua aplicação gerida pelo Intune quando este está a gerir a aplicação de forma ativa.


## <a name="whats-in-the-sdk"></a>O que está no SDK

O SDK da Aplicação do Intune é constituído pelos seguintes ficheiros:

* **Microsoft.Intune.MAM.SDK.aar**: os componentes do SDK, com exceção dos ficheiros JAR da Biblioteca de Suporte.
* **Microsoft.Intune.MAM.SDK.Support.v4.jar**: as classes necessárias para ativar a MAM nas aplicações que utilizam a biblioteca de suporte v4 do Android.
* **Microsoft.Intune.MAM.SDK.Support.v7.jar**: as classes necessárias para ativar a MAM nas aplicações que utilizam a biblioteca de suporte v7 do Android.
* **Microsoft.Intune.MAM.SDK.Support.v17.jar**: as classes necessárias para ativar a MAM nas aplicações que utilizam a biblioteca de suporte v17 do Android. 
* **Microsoft.Intune.MAM.SDK.Support.Text.jar**: as classes necessárias para ativar a MAM nas aplicações que utilizam classes da biblioteca de suporte do Android no pacote `android.support.text`.
* **Microsoft. Intune. Mam. Sdk. DownlevelStubs. aar**: este AAR contém stubs para classes do sistema Android que estão presentes somente em dispositivos mais recentes, mas que são referenciados por métodos no `MAMActivity`. Os dispositivos mais recentes ignorarão estas classes de stub. Esse AAR será necessário apenas se o aplicativo executar a reflexão em classes derivadas de `MAMActivity` e a maioria dos aplicativos não precisar incluí-la. O AAR contém regras do PROGuard para excluir todas as suas classes.
* **com.microsoft.Intune.mam.Build.JAR**: um plug-in do Gradle que [ajuda a integrar o SDK](#build-tooling).
* **CHANGELOG.txt**: fornece um registo das alterações feitas em cada versão do SDK.
* **THIRDPARTYNOTICES.TXT**: aviso de atribuição que reconhece código de terceiros e/ou OSS que será compilado na sua aplicação.

## <a name="requirements"></a>Requisitos

### <a name="android-versions"></a>Versões do Android
O SDK dá suporte à API do Android 19 (Android 4.4 +) por meio da API do Android 28 (Android 9,0).

### <a name="company-portal-app"></a>Aplicação Portal da Empresa
O SDK da Aplicação do Intune para Android baseia-se na presença da aplicação [Portal da Empresa](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) no dispositivo para ativar as políticas de proteção. O Portal da Empresa obtém as políticas de proteção de aplicações do serviço Intune. Quando a aplicação é inicializada, é carregada a política e o código para impor essa política a partir do Portal da Empresa.

> [!NOTE]
> Quando a aplicação Portal da Empresa não está no dispositivo, uma aplicação gerida pelo Intune tem o mesmo comportamento que uma aplicação normal que não suporta as políticas de proteção de aplicações do Intune.

Para a proteção de aplicações sem inscrição de dispositivos, o utilizador _**não**_ é obrigado a inscrever o dispositivo através da aplicação Portal da Empresa.

## <a name="sdk-integration"></a>Integração do SDK

### <a name="sample-app"></a>Aplicativo de exemplo
Um exemplo de como integrar com o SDK de aplicativo do Intune corretamente está disponível no [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App). Este exemplo usa o [plug-in de compilação gradle](#gradle-build-plugin).

### <a name="referencing-intune-app-libraries"></a>Fazer referência a bibliotecas da Aplicação do Intune

O SDK da Aplicação do Intune é uma biblioteca do Android padrão sem dependências externas. O **Microsoft.Intune.MAM.SDK.aar** contém as interfaces necessárias para a ativação da política de proteção de aplicações e o código necessário para interagir com a aplicação Portal da Empresa do Microsoft Intune.

O **Microsoft.Intune.MAM.SDK.aar** tem de ser especificado como uma referência da biblioteca do Android. Para tal, abra o projeto de aplicação no Android Studio e aceda a **Ficheiro > Novo > Novo módulo** e selecione **Importar Pacote .JAR/.AAR**. Em seguida, selecione nosso pacote de arquivamento do Android Microsoft. Intune. MAM. SDK. aar para criar um módulo para o. AAR. Clique com o botão direito do rato no módulo ou módulos que contêm o código da aplicação e aceda a **Definições do Módulo** > **separador Dependências** > **ícone +**  > **Dependência do módulo** > Selecione o módulo de AAR do SDK de MAM que acabou de criar > **OK**. Esta ação irá garantir que o seu módulo é compilado com o SDK de MAM quando criar o seu projeto.

Além disso, as bibliotecas do **Microsoft.Intune.MAM.SDK.Support.XXX.jar** contêm variantes do Intune das bibliotecas do `android.support.XXX` correspondentes. Não são compiladas no Microsoft.Intune.MAM.SDK.aar, caso uma aplicação não necessite de depender das bibliotecas de suporte.

#### <a name="proguard"></a>ProGuard

Se o [ProGuard](http://proguard.sourceforge.net/) (ou qualquer outro mecanismo de redução/ocultação) for utilizado como um passo de compilação, o SDK tem regras de configuração adicionais que têm de ser incluídas. Ao incluir o. AAR em sua compilação, nossas regras são integradas automaticamente à etapa do PROGuard e os arquivos de classe necessários são mantidos.

As Azure Active Directory Authentication Libraries (ADAL) podem ter as suas próprias restrições ProGuard. Se a sua aplicação integrar a ADAL, terá de seguir a documentação da ADAL referente a essas restrições.

### <a name="policy-enforcement"></a>Imposição de políticas
O SDK da Aplicação do Intune é uma biblioteca do Android que permite que a sua aplicação suporte e participe na imposição de políticas do Intune. 

A maioria das políticas é imposta semiautomaticamente, mas determinadas políticas exigem [a participação explícita do seu aplicativo para impor](#enable-features-that-require-app-participation).
Independentemente de você executar a integração de origem ou utilizar ferramentas de Build para integração, as políticas que exigem a participação explícita precisarão ser codificadas para o.

Para políticas que são automaticamente impostas, é necessário que os aplicativos substituam a herança de várias classes base do Android por herança de equivalentes de MAM e, da mesma forma, substituem chamadas para determinadas classes de serviço do sistema Android com chamadas para equivalentes de MAM. As substituições específicas necessárias são detalhadas [abaixo](#class-and-method-replacements) e podem ser executadas manualmente com a integração de origem ou executadas automaticamente por meio de ferramentas de compilação.

### <a name="build-tooling"></a>Ferramentas de compilação
O SDK fornece ferramentas de compilação (um plug-in para Builds do gradle e uma ferramenta de linha de comando para compilações não gradle) que executam substituições equivalentes de MAM automaticamente. Estas ferramentas transformam os ficheiros de classe gerados pela compilação de Java e não modificam o código fonte original.

As ferramentas executam apenas [substituições diretas](#class-and-method-replacements) . Não efetuam quaisquer integrações de SDK mais complexas, como a [Política Guardar Como](#enable-features-that-require-app-participation), a [Identidades Múltiplas](#multi-identity-optional), o [registo App-WE](#app-protection-policy-without-device-enrollment), [modificações AndroidManifest](#manifest-replacements) ou a [configuração da ADAL](#configure-azure-active-directory-authentication-library-adal), pelo que estes têm de ser concluídos antes de a sua aplicação estar totalmente compatível com o Intune. Leia atentamente o resto deste documento para ver os pontos de integração relevantes para a sua aplicação.

> [!NOTE]
> Pode executar as ferramentas num projeto que já realizou a integração da origem parcial ou completa do SDK de MAM através de substituições manuais. O seu projeto tem de continuar a apresentar o SDK de MAM como uma dependência.

### <a name="gradle-build-plugin"></a>Plug-in de Compilação do Gradle
Se a compilação da sua aplicação não for efetuada com o Gradle, avance para [Integrar com a Ferramenta de Linha de Comandos](#command-line-build-tool). 

O plug-in do SDK da Aplicação é distribuído integrado no SDK como **GradlePlugin/com.microsoft.intune.mam.build.jar**. Para que o Gradle possa localizar o plug-in, este tem de ser adicionado ao caminho da classe (classpath) do script de compilação (buildscript). O plug-in depende do [Javassist](https://jboss-javassist.github.io/javassist/), que também tem de ser adicionado. Para adicionar ambos ao caminho da classe, adicione o seguinte ao seu `build.gradle` de raiz

```groovy
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath "org.javassist:javassist:3.22.0-GA"
        classpath files("$PATH_TO_MAM_SDK/GradlePlugin/com.microsoft.intune.mam.build.jar")
    }
}
```

Em seguida, no ficheiro `build.gradle` do seu projeto APK, aplique simplesmente o plug-in como
```groovy
apply plugin: 'com.microsoft.intune.mam'
```

Por predefinição, o plug-in irá funcionar **apenas** em dependências do `project`.
A compilação de teste não é afetada. Poderá ser fornecida uma configuração para apresentar o seguinte:
*  Projetos a excluir
*  [Dependências externas a incluir](#usage-of-includeexternallibraries) 
*  Classes específicas a excluir do processamento
*  Variantes a excluir do processamento. Estas podem ser referentes a um nome de variante completo ou a um único tipo. Por exemplo
     * Se a sua aplicação tiver os tipos de compilação `debug` e `release` com os tipos {`savory`, `sweet`} e {`vanilla`, `chocolate`} poderá especificar
     * `savory` para excluir todas as variantes com o tipo savory ou `savoryVanillaRelease` para excluir apenas esta variante específica.

#### <a name="example-partial-buildgradle"></a>Exemplo de build.gradle parcial

```groovy

apply plugin: 'com.microsoft.intune.mam'

dependencies {
    implementation project(':product:FooLib')
    implementation project(':product:foo-project')
    implementation fileTree(dir: "libs", include: ["bar.jar"])
    implementation fileTree(dir: "libs", include: ["zap.jar"])
    implementation "com.contoso.foo:zap-artifact:1.0.0"
    implementation "com.microsoft.bar:baz:1.0.0"
    implementation "com.microsoft.qux:foo:2.0"

    // Include the MAM SDK
    implementation files("$PATH_TO_MAM_SDK/Microsoft.Intune.MAM.SDK.aar")
}
intunemam {
    excludeProjects = [':product:FooLib']
    includeExternalLibraries = ['bar.jar', "com.contoso.foo:zap-artifact", "com.microsoft.*", "!com.microsoft.qux*"]
    excludeClasses = ['com.contoso.SplashActivity']
    excludeVariants=['savory']
}
```

Este exemplo teria os seguintes efeitos:
* `:product:FooLib` não é reescrito porque está incluído em `excludeProjects`
* `:product:foo-project` é reescrito, exceto para `com.contoso.SplashActivity`, que é ignorado porque está em `excludeClasses`
* `bar.jar` é reescrito porque está incluído em `includeExternalLibraries`
* `zap.jar` **não** é reescrito porque não é um projeto e não está incluído em `includeExternalLibraries`
* `com.contoso.foo:zap-artifact:1.0.0` é reescrito porque está incluído em `includeExternalLibraries`
* `com.microsoft.bar:baz:1.0.0` é reescrito porque está incluído em `includeExternalLibraries` através de um caráter universal (`com.microsoft.*`).
* `com.microsoft.qux:foo:2.0` não é reescrito, mesmo que corresponda ao mesmo caractere curinga que o item anterior, pois ele é explicitamente excluído por meio de um padrão de negação.

#### <a name="usage-of-includeexternallibraries"></a>Utilização de includeExternalLibraries

Uma vez que, por predefinição, o plug-in só funciona em dependências do projeto (geralmente fornecidas pela função `project()`), todas as dependências especificadas por `fileTree(...)` ou obtidas a partir do Maven ou de outras origens de pacote (por exemplo, "`com.contoso.bar:baz:1.2.0`") têm de ser fornecidas à propriedade `includeExternalLibraries`, caso o processamento de MAM das mesmas seja necessário com base nos critérios explicados abaixo. São suportados carateres universais ("*"). Um item que começa com `!` é uma negação e pode ser usado para excluir bibliotecas que, de outra forma, seriam incluídas por um curinga.

Ao especificar dependências externas com a notação de artefacto, é aconselhável omitir o componente da versão no valor `includeExternalLibraries`. Se decidir incluir a versão, esta tem de ser exata. Não são suportadas especificações de versão dinâmicas (por exemplo, `1.+`).

A regra geral que deve utilizar para determinar se tem de incluir as bibliotecas em `includeExternalLibraries` baseia-se em duas perguntas:
1. A biblioteca tem classes para as quais existem equivalentes de MAM? Exemplos: `Activity`, `Fragment`, `ContentProvider`, `Service`, etc.
2. Se sim, a sua aplicação utiliza essas classes?

Se responder "sim" a ambas as perguntas, tem de incluir essa biblioteca em `includeExternalLibraries`. 

| Cenário | Deve Incluir-se? |
|--|--|
| Inclui uma biblioteca de visualizador de PDFs na sua aplicação e utiliza o visualizador `Activity` na aplicação quando os utilizadores tentam ver PDFs | Sim |
| Inclui uma biblioteca HTTP na sua aplicação para obter um melhor desempenho na Web | Não |
| Inclui uma biblioteca, como o React Native, que contém classes derivadas de `Activity`, `Application` e `Fragment`, e utiliza ou efetua uma derivação adicional dessas classes na sua aplicação | Sim |
| Inclui uma biblioteca, como o React Native, que contém classes derivadas de `Activity`, `Application` e `Fragment`, mas utiliza apenas auxiliares estáticos ou classes de utilitários | Não |
| Inclui uma biblioteca que contém classes derivadas de `TextView` e utiliza ou efetua uma derivação adicional dessas classes na sua aplicação | Sim |

#### <a name="reporting"></a>Relatórios
O plug-in de compilação pode gerar um relatório HTML das alterações feitas por ele. Para solicitar a geração desse relatório, especifique `report = true` no bloco de configuração `intunemam`. Se gerado, o relatório será gravado em `outputs/logs` no diretório de Build.

```groovy
intunemam {
    report = true
}
```

#### <a name="verification"></a>Verificação
O plug-in de compilação pode executar verificação adicional para procurar possíveis erros em classes de processamento. Para solicitar isso, especifique `verify = true` no bloco de configuração `intunemam`. Observe que isso pode adicionar vários segundos ao tempo gasto pela tarefa do plug-in.

```groovy
intunemam {
    verify = true
}
```

#### <a name="incremental-builds"></a>Compilações incrementais
Para habilitar o suporte para criação incremental, especifique `incremental = true` no bloco de configuração `intunemam`.  Esse é um recurso experimental destinado a aumentar o desempenho da compilação processando apenas os arquivos de entrada que foram alterados.  A configuração padrão é `false`.

```groovy
intunemam {
    incremental = true
}
```

#### <a name="dependencies"></a>Depend

O plug-in do Gradle tem uma dependência no [Javassist](https://jboss-javassist.github.io/javassist/) que tem de estar disponível para a resolução de dependências do Gradle (conforme descrito acima). O Javassist é utilizado apenas no momento da compilação ao executar o plug-in. Não será adicionado nenhum código do Javassist à sua aplicação.

> [!NOTE] 
> Tem de utilizar a versão 3.0 ou mais recente do plug-in do Gradle para Android e o Gradle 4.1 ou mais recente.

### <a name="command-line-build-tool"></a>Ferramenta de Compilação de Linha de Comandos
Se a sua compilação utilizar o Gradle, avance para a [secção seguinte](#class-and-method-replacements).

A ferramenta de compilação de linha de comandos está disponível na pasta `BuildTool` do menu pendente do SDK. Executa a mesma função do plug-in do Gradle detalhado acima, mas pode ser integrada em sistemas de compilação personalizados ou que não sejam do Gradle. Uma vez que é mais genérica, é mais complexo invocá-la, pelo que o plug-in do Gradle deve ser utilizado sempre que possível.

#### <a name="using-the-command-line-tool"></a>Utilizar a Ferramenta de Linha de Comandos

A ferramenta de linha de comandos pode ser invocada com os scripts auxiliares fornecidos no diretório `BuildTool\bin`.

A ferramenta espera os parâmetros seguintes.

| Parâmetro | Description |
| -- | -- |
| `--input` | Uma lista delimitada por pontos e vírgulas de ficheiros jar e diretórios de ficheiros de classe a modificar. Esta lista deve incluir todos os jars/diretórios que pretende reescrever. |
| `--output` | Uma lista delimitada por pontos e vírgulas de ficheiros jar e diretórios nos quais as classes modificadas devem ser armazenadas. Deve existir um valor de saída por cada valor de entrada, com apresentação por ordem. |
| `--classpath` | O caminho de classe de compilação. Pode conter jars e diretórios de classe. |
| `--excludeClasses`| Uma lista delimitada por pontos e vírgulas que contém os nomes das classes que devem ser excluídas do processo de reescrita. |

Todos os parâmetros são necessários, com exceção de `--excludeClasses`, que é opcional.

> [!NOTE]
> Em sistemas semelhantes a UNIX, o ponto-e-vírgula é um separador de comando. Para evitar que o Shell divida os comandos, certifique-se de escapar cada ponto-e-vírgula com ' \' ' ou encapsule o parâmetro completo entre aspas.

#### <a name="example-command-line-tool-invocation"></a>Invocação de exemplo da Ferramenta de Linha de Comandos

``` batch
> BuildTool\bin\BuildTool.bat --input build\product-foo-project;libs\bar.jar --output mam-build\product-foo-project;mam-build\libs\bar.jar --classpath build\zap.jar;libs\Microsoft.Intune.MAM.SDK\classes.jar;%ANDROID_SDK_ROOT%\platforms\android-27\android.jar --excludeClasses com.contoso.SplashActivity
```

Este exemplo teria os seguintes efeitos:

* O diretório `product-foo-project` é reescrito para `mam-build\product-foo-project`
* `bar.jar` é reescrito para `mam-build\libs\bar.jar`
* `zap.jar` **não** é reescrito porque é apenas apresentado em `--classpath`
* A classe `com.contoso.SplashActivity` **não** é reescrita, mesmo que se encontre em `--input`

> [!NOTE] 
> Atualmente, a ferramenta de compilação não suporta ficheiros aar. Se o seu sistema de compilação não extrair o `classes.jar` ao processar ficheiros aar, terá de fazê-lo antes de invocar a ferramenta de compilação.


## <a name="class-and-method-replacements"></a>Substituições de classes e métodos

As classes base Android têm de ser substituídas pelos respetivos equivalentes de MAM para ativar a gestão do Intune. As classes do SDK estão entre a classe base Android e a própria versão derivada da aplicação dessa classe. Por exemplo, a atividade de uma aplicação poderá terminar com uma hierarquia de herança semelhante à seguinte: `Activity` > `MAMActivity` >
`AppSpecificActivity`. A camada MAM filtra chamadas para operações do sistema, para fornecer uma vista gerida global à sua aplicação de forma totalmente integrada.

Além das classes base, algumas classes que a sua aplicação pode utilizar sem derivação (por exemplo, `MediaPlayer`) também exigem equivalentes de MAM e [algumas chamadas de método também têm de ser substituídas](#wrapped-system-services). Os detalhes exatos são indicados abaixo.

> [!NOTE] 
> Se seu aplicativo estiver se integrando com [ferramentas de Build](#build-tooling)do SDK, as seguintes substituições de classe e método serão executadas automaticamente.

| Classe base Android | Substituição do SDK da Aplicação do Intune |
|--|--|
| android.app.Activity | MAMActivity |
| android.app.ActivityGroup | MAMActivityGroup |
| android.app.AliasActivity | MAMAliasActivity |
| android.app.Application | MAMApplication |
| Android. app. Dialog | MAMDialog |
| Android. app. AlertDialog. Builder | MAMAlertDialogBuilder |
| android.app.DialogFragment | MAMDialogFragment |
| android.app.ExpandableListActivity | MAMExpandableListActivity |
| android.app.Fragment | MAMFragment |
| android.app.IntentService | MAMIntentService |
| android.app.LauncherActivity | MAMLauncherActivity |
| android.app.ListActivity | MAMListActivity |
| android.app.ListFragment | MAMListFragment |
| android.app.NativeActivity | MAMNativeActivity |
| android.app.PendingIntent | MAMPendingIntent (veja [PendingIntent](#pendingintent)) |
| android.app.Service | MAMService |
| android.app.TabActivity | MAMTabActivity |
| android.app.TaskStackBuilder | MAMTaskStackBuilder |
| android.app.backup.BackupAgent | MAMBackupAgent |
| android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
| android.app.backup.FileBackupHelper | MAMFileBackupHelper |
| android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| android.content.BroadcastReceiver | MAMBroadcastReceiver |
| android.content.ContentProvider | MAMContentProvider |
| android.os.Binder | MAMBinder (Necessário apenas se o Enlaçamento não for gerado a partir de uma interface Android Interface Definition Language (AIDL)) |
| android.media.MediaPlayer | MAMMediaPlayer |
| android.media.MediaMetadataRetriever | MAMMediaMetadataRetriever |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |
| android.support.multidex.MultiDexApplication | MAMMultiDexApplication |
| android.widget.TextView | MAMTextView |
| android.widget.AutoCompleteTextView | MAMAutoCompleteTextView |
| android.widget.CheckedTextView | MAMCheckedTextView |
| android.widget.EditText | MAMEditText |
| android.inputmethodservice.ExtractEditText | MAMExtractEditText |
| android.widget.MultiAutoCompleteTextView | MAMMultiAutoCompleteTextView |

> [!NOTE]
> Mesmo que a sua aplicação não tenha necessidade da sua própria classe `Application` derivada, [veja `MAMApplication` abaixo](#mamapplication)

### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft.Intune.MAM.SDK.Suppout.v4.jar:

| Classe Android | Substituição do SDK da Aplicação do Intune |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.JobIntentService | MAMJobIntentService
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider
| android.support.v4.content.WakefulBroadcastReceiver | MAMWakefulBroadcastReceiver

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft.Intune.MAM.SDK.Suppout.v7.jar:

|Classe Android | Substituição do SDK da Aplicação do Intune |
|--|--|
| Android. support. v7. app. AlertDialog. Builder | MAMAlertDialogBuilder |
| android.support.v7.app.AppCompatActivity | MAMAppCompatActivity |
| android.support.v7.widget.AppCompatAutoCompleteTextView | MAMAppCompatAutoCompleteTextView |
| android.support.v7.widget.AppCompatCheckedTextView | MAMAppCompatCheckedTextView |
| android.support.v7.widget.AppCompatEditText | MAMAppCompatEditText |
| android.support.v7.widget.AppCompatMultiAutoCompleteTextView | MAMAppCompatMultiAutoCompleteTextView |
| android.support.v7.widget.AppCompatTextView | MAMAppCompatTextView |

### <a name="microsoftintunemamsdksupportv17jar"></a>Microsoft.Intune.MAM.SDK.Support.v17.jar:
|Classe Android | Substituição do SDK da Aplicação do Intune |
|--|--|
| android.support.v17.leanback.widget.SearchEditText | MAMSearchEditText |

### <a name="microsoftintunemamsdksupporttextjar"></a>Microsoft.Intune.MAM.SDK.Support.Text.jar:
|Classe Android | Substituição do SDK da Aplicação do Intune |
|--|--|
| android.support.text.emoji.widget.EmojiAppCompatEditText | MAMEmojiAppCompatEditText |
| android.support.text.emoji.widget.EmojiAppCompatTextView | MAMEmojiAppCompatTextView |
| android.support.text.emoji.widget.EmojiEditText | MAMEmojiEditText |
| android.support.text.emoji.widget.EmojiTextView | MAMEmojiTextView |

### <a name="renamed-methods"></a>Métodos renomeados
Em muitos casos, um método disponível na classe Android foi marcado como final na classe de substituição da MAM. Neste caso, a classe de substituição de MAM proporciona um método com um nome semelhante (geralmente, com o sufixo `MAM`), que deve ser substituído. Por exemplo, quando executar a derivação de `MAMActivity`, em vez de substituir `onCreate()` e chamar `super.onCreate()`, `Activity` tem de substituir `onMAMCreate()` e chamar `super.onMAMCreate()`. O compilador de Java deve impor as restrições finais para impedir a substituição acidental do método original em vez do MAM equivalente.

### <a name="mamapplication"></a>MAMApplication
Se a sua aplicação criar uma subclasse de `android.app.Application`, **tem** de criar uma subclasse de `com.microsoft.intune.mam.client.app.MAMApplication`. Se a sua aplicação não criar uma subclasse de `android.app.Application`, **tem** de definir `"com.microsoft.intune.mam.client.app.MAMApplication"` como o atributo `"android:name"` na etiqueta `<application>` de AndroidManifest.xml.

### <a name="pendingintent"></a>PendingIntent
Em vez de `PendingIntent.get*`, tem de utilizar o método `MAMPendingIntent.get*`. Depois disto, pode utilizar o `PendingIntent` resultante como habitualmente.

### <a name="wrapped-system-services"></a>Serviços de Sistema Encapsulados
Para algumas classes de serviço de sistema, é necessário chamar um método estático numa classe de wrapper de MAM em vez de invocar diretamente o método pretendido na instância de serviço. Por exemplo, uma chamada para `getSystemService(ClipboardManager.class).getPrimaryClip()` tem de se tornar uma chamada para `MAMClipboardManager.getPrimaryClip(getSystemService(ClipboardManager.class)`. Não é recomendado efetuar estas substituições manualmente. Em alternativa, utilize o BuildPlugin para o fazer.

| Classe Android | Substituição do SDK da Aplicação do Intune |
|--|--|
| android.content.ClipboardManager | MAMClipboard |
| Android. Content. ContentProviderClient | MAMContentProviderClientManagement |
| Android. Content. ContentResolver retornem | MAMContentResolverManagement |
| android.content.pm.PackageManager | MAMPackageManagement |
| android.app.DownloadManager | MAMDownloadManagement |
| Android. Print. Gerenciador de impressão | MAMPrintManagement |
| Android. support. v4. Print. myhelper | MAMPrintHelperManagement |
| Android. View. View | MAMViewManagement |
| Android. View. DragEvent | MAMDragEventManagement |
| Android. app. Notificationmanager | MAMNotificationManagement |
| Android. support. v4. app. NotificationManagerCompat | MAMNotificationCompatManagement |

Algumas classes têm a maioria de seus métodos encapsulados, por exemplo, `ClipboardManager`, `ContentProviderClient`, `ContentResolver` e `PackageManager`, enquanto outras classes têm apenas um ou dois métodos encapsulados, por exemplo, `DownloadManager`, `PrintManager`, `PrintHelper`, `View`, `DragEvent`, `NotificationManager` e 0. Consulte as APIs expostas pelas classes equivalentes do MAM para o método exato se você não usar o BuildPlugin.

### <a name="manifest-replacements"></a>Substituições do manifesto
Poderá ser preciso realizar algumas das substituições de classe indicadas acima no manifesto, bem como no código Java. De destacar:
* As referências do manifesto a `android.support.v4.content.FileProvider` devem ser substituídas por `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider`.

## <a name="androidx-libraries"></a>Bibliotecas AndroidX
Com o Android P, a Google anunciou um novo conjunto (com um novo nome) de bibliotecas de suporte chamado AndroidX e a versão 28 é a versão principal mais recente das bibliotecas android.support existentes.

Ao contrário das bibliotecas de suporte do Android, não fornecemos variantes de MAM das bibliotecas AndroidX. Em alternativa, o AndroidX deve ser tratado como qualquer outra biblioteca externa e configurado para ser reescrito com o plug-in/ferramenta de compilação. Para compilações do gradle, isso pode ser feito incluindo `androidx.*` no campo `includeExternalLibraries` da configuração do plug-in. As invocações da ferramenta de linhas de comando devem listar todos os arquivos jar explicitamente.

### <a name="pre-androidx-architecture-components"></a>Componentes de arquitetura AndroidX
Muitos componentes de arquitetura do Android, incluindo o Room, o ViewModel e o Gerenciador de trabalho, foram reempacotados para AndroidX. Se seu aplicativo usar as variantes AndroidX dessas bibliotecas, verifique se as regravações se aplicam incluindo `android.arch.*` no campo `includeExternalLibraries` da configuração do plug-in. Como alternativa, atualize as bibliotecas para seus equivalentes AndroidX.

## <a name="sdk-permissions"></a>Permissões de SDK

O SDK da Aplicação do Intune requer três [permissões do sistema Android](https://developer.android.com/guide/topics/security/permissions.html) em aplicações que o integrem:

* `android.permission.GET_ACCOUNTS` (pedido durante o runtime, se for preciso)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

A Azure Active Directory Authentication Library ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) requer estas permissões para executar a autenticação mediada. Se estas permissões não forem concedidas pela aplicação ou forem revogadas pelo utilizador, os fluxos de autenticação que exigirem o mediador (a aplicação Portal da Empresa) serão desativados.

## <a name="logging"></a>Registo

O registo deve ser inicializado antecipadamente para obter o maior valor dos dados registados. `Application.onMAMCreate()` é normalmente o melhor local para inicializar o registo.

Para receber registos MAM na sua aplicação, crie um [Processador Java](https://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html) e adicione-o ao `MAMLogHandlerWrapper`. Este procedimento invocará `publish()` no processador da aplicação para todas as mensagens de registo.

```java
/**
 * Global log handler that enables fine grained PII filtering within MAM logs.  
 *
 * To start using this you should build your own log handler and add it via
 * MAMComponents.get(MAMLogHandlerWrapper.class).addHandler(myHandler, false);  
 *
 * You may also remove the handler entirely via
 * MAMComponents.get(MAMLogHandlerWrapper.class).removeHandler(myHandler);
 */
public interface MAMLogHandlerWrapper {
    /**
     * Add a handler, PII can be toggled.
     *
     * @param handler handler to add.
     * @param wantsPII if PII is desired in the logs.    
     */
    void addHandler(final Handler handler, final boolean wantsPII);

    /**
     * Remove a handler.
     *
     * @param handler handler to remove.
     */
    void removeHandler(final Handler handler);
}
```

## <a name="enable-features-that-require-app-participation"></a>Ativar funcionalidades que requerem a participação da aplicação

Existem várias políticas de proteção de aplicações que o SDK não pode implementar por si só. A aplicação pode controlar o respetivo comportamento para cumprir estas funcionalidades através de várias APIs que pode encontrar na seguinte interface `AppPolicy`. Para obter uma instância `AppPolicy`, utilize o comando `MAMPolicyManager.getPolicy`.

```java
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
  * This function is now deprecated. Use getIsSaveToLocationAllowed(SaveLocation, String) instead
 * @return True if the app is allowed to save to personal data stores; false otherwise.
 */
@Deprecated
boolean getIsSaveToPersonalAllowed();

/**
 * Check if policy prohibits saving to a content provider location.
 *
 * @param location
 *            a content URI to check
 * @return True if location is not a content URI or if policy does not prohibit saving to the content location.
 */
boolean getIsSaveToLocationAllowed(Uri location);

/**
 * Determines if the SaveLocation passed in can be saved to by the username associated with the cloud service.
 *
 * @param service
 *           see {@link SaveLocation}.
 * @param username
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between
 *           the AAD username and the cloud service username does not exist or the username is not known.
 * @return true if the location can be saved to by the identity, false if otherwise.
 */
boolean getIsSaveToLocationAllowed(SaveLocation service, String username);

/**
 * Checks whether any activities which could handle the given intent are allowed by policy. Returns false only if all
 * activities which could otherwise handle the intent are blocked. If there are no activities which could handle the intent
 * regardless of policy, returns true. If some activities are allowed and others blocked, returns true. Note that it is not
 * necessary to use this method for policy enforcement. If your app attempts to launch an intent for which there are no
 * allowed activities, MAM will display a dialog explaining the situation to the user.
 *
 * @param intent
 *         intent to check
 *
 * @return whether any activities which could handle this intent are allowed.
*/
boolean areIntentActivitiesAllowed(Intent intent);

/**
 * Whether the SDK PIN prompt is enabled for the app.
 *
 * @return True if the PIN is enabled. False otherwise.
 */
boolean getIsPinRequired();

/**
 * Whether the Intune Managed Browser is required to open web links.
 * @return True if the Managed Browser is required, false otherwise
 */
boolean getIsManagedBrowserRequired();

/**
 * Check if policy allows taking screenshots.
 *
 * @return True if screenshots will be blocked, false otherwise
 */
boolean getIsScreenCaptureAllowed();

/**
 * Check if policy allows Contact sync to local contact list.
 *
 * @return True if Contact sync is allowed to save to local contact list; false otherwise.
 */
boolean getIsContactSyncAllowed();

/**
 * Get the notification restriction. If {@link NotificationRestriction#BLOCKED BLOCKED}, the app must not show any notifications
 * for the user associated with this policy. If {@link NotificationRestriction#BLOCK_ORG_DATA BLOCK_ORG_DATA}, the app must show
 * a modified notification that does not contain organization data. If {@link NotificationRestriction#UNRESTRICTED
 * UNRESTRICTED}, all notifications are allowed.
 *
 * @return The notification restriction.
 */
NotificationRestriction getNotificationRestriction();

/**
 * This method is intended for diagnostic/telemetry purposes only. It can be used to discover whether file encryption is in use.
 * File encryption is transparent to the app and the app should not need to make any business logic decisions based on this.
 * @return True if file encryption is in use.
 */
boolean diagnosticIsFileEncryptionInUse();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();

}
```

> [!NOTE]
> `MAMPolicyManager.getPolicy` devolverá sempre uma Política de Aplicação não nula, mesmo se o dispositivo ou aplicação não estiver sob uma política de gestão do Intune.

### <a name="example-determine-if-pin-is-required-for-the-app"></a>Exemplo: determinar se o PIN é necessário para a aplicação

Se a aplicação tiver a sua própria experiência de utilizador de PIN, poderá querer desativá-la caso o administrador de TI tenha configurado o SDK para solicitar um PIN da aplicação. Para determinar se o administrador de TI implementou a política de PIN da aplicação para esta aplicação, para o utilizador final atual, chame o método seguinte:

```java

MAMPolicyManager.getPolicy(currentActivity).getIsPinRequired();
```

### <a name="example-determine-the-primary-intune-user"></a>Exemplo: determinar o utilizador primário do Intune

Além das APIs expostas na AppPolicy, o nome principal do utilizador (**UPN**) também é exposto pela API `getPrimaryUser()` definida na interface `MAMUserInfo`. Para obter o UPN, chame o seguinte:

```java
MAMComponents.get(MAMUserInfo.class).getPrimaryUser();
```

A definição completa da interface MAMUserInfo pode ser vista abaixo:

```java
/**
 * External facing user information.
 *
 */
public interface MAMUserInfo {
       /**
        * Get the primary user name.
        *
        * @return the primary user name or null if neither the device nor app is enrolled.
        */
       String getPrimaryUser();
}
```

### <a name="example-determine-if-saving-to-device-or-cloud-storage-is-permitted"></a>Exemplo: determinar se é permitido guardar no dispositivo ou armazenar na cloud

Muitas aplicações implementam funcionalidades que permitem ao utilizador final guardar os ficheiros localmente ou num serviço de armazenamento na cloud. O SDK da Aplicação do Intune permite aos administradores de TI aplicar restrições de políticas que considerem mais adequadas na organização, para proteger contra fugas de dados.  Uma das políticas que o administrador de TI pode controlar é se o utilizador final pode guardar num arquivo de dados "pessoal" não gerido. Isto inclui guardar numa localização local, num cartão SD ou em serviços de cópias de segurança de terceiros.

**A participação da aplicação é necessária para ativar a funcionalidade.** Se a aplicação permitir guardar em localizações pessoais ou na cloud diretamente a partir da aplicação, tem de implementar esta funcionalidade para garantir que o administrador de TI pode controlar se a gravação numa localização é permitida. A API abaixo permite à aplicação saber se a gravação num arquivo pessoal é permitida pela política do administrador do Intune atual. Em seguida, a aplicação pode impor a política, uma vez que tem conhecimento do arquivo de dados pessoal disponível para o utilizador final através da aplicação.  

Para determinar se a política é imposta, faça a seguinte chamada:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

O parâmetro `service` deve ser um dos seguintes valores de `SaveLocation`:


- `SaveLocation.ONEDRIVE_FOR_BUSINESS`
- `SaveLocation.SHAREPOINT`
- `SaveLocation.LOCAL`
- `SaveLocation.OTHER`

O `username` deve ser o UPN/nome de usuário/email associado ao serviço de nuvem que está sendo salvo (*não* necessariamente o mesmo que o usuário que possui o documento que está sendo salvo). Use NULL se um mapeamento entre o UPN do AAD e o nome de usuário do serviço de nuvem não existir ou se o nome de usuário não for conhecido. `SaveLocation.LOCAL` não é um serviço de nuvem e, portanto, deve sempre ser usado com um parâmetro de nome de usuário `null`.

O método anterior para determinar se uma política de utilizador permitia guardar dados em várias localizações era `getIsSaveToPersonalAllowed()`, dentro da mesma classe **AppPolicy**. Esta função é agora **preterida** e não deve ser utilizada, a invocação seguinte é equivalente a `getIsSaveToPersonalAllowed()`:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(SaveLocation.LOCAL, null);
```

>[!NOTE]
> Utilize `SaveLocation.OTHER` se a localização em questão não estiver listada no enum **SaveLocations**.

### <a name="example-determine-if-notifications-with-organization-data-need-to-be-restricted"></a>Exemplo: determinar se as notificações com dados da organização precisam ser restritas

Se seu aplicativo exibir notificações, você deverá verificar a política de restrição de notificação para o usuário associado à notificação antes de mostrar a notificação. Para determinar se a política é imposta, faça a chamada a seguir.

```java
NotificationRestriction notificationRestriction =
    MAMPolicyManager.getPolicyForIdentity(notificationIdentity).getNotificationRestriction();
```

Se a restrição for `BLOCKED`, o aplicativo não deverá mostrar nenhuma notificação para o usuário associado a essa política. Se `BLOCK_ORG_DATA`, o aplicativo deverá mostrar uma notificação modificada que não contém dados da organização. Se `UNRESTRICTED`, todas as notificações serão permitidas.

Se `getNotificationRestriction` não for invocado, o SDK do MAM fará um melhor esforço para restringir as notificações automaticamente para aplicativos de identidade única. Se o bloqueio automático estiver habilitado e `BLOCK_ORG_DATA` estiver definido, a notificação não será mostrada. Para um controle mais refinado, verifique o valor de `getNotificationRestriction` e modifique as notificações do aplicativo adequadamente.

## <a name="register-for-notifications-from-the-sdk"></a>Registar para obter notificações do SDK

### <a name="overview"></a>Overview
O SDK da Aplicação do Intune permite à sua aplicação ter controlo sobre determinadas políticas, como a eliminação seletiva, quando são implementadas pelo administrador de TI. Quando um administrador de TI implementar uma destas políticas, o serviço do Intune transmite uma notificação para o SDK.

A sua aplicação tem de estar registada para obter notificações do SDK ao criar uma `MAMNotificationReceiver` e ao registá-la em `MAMNotificationReceiverRegistry`. Isto é feito ao indicar o recetor e o tipo de notificação desejados em `App.onCreate`, como ilustra o exemplo abaixo:

```java
@Override
public void onCreate() {
  super.onCreate();
  MAMComponents.get(MAMNotificationReceiverRegistry.class)
    .registerReceiver(
      new ToastNotificationReceiver(),
      MAMNotificationType.WIPE_USER_DATA);
  }
```

### <a name="mamnotificationreceiver"></a>MAMNotificationReceiver

A interface `MAMNotificationReceiver` recebe simplesmente notificações do serviço Intune. Algumas notificações são processadas diretamente pelo SDK, ao passo que outras requerem a participação da aplicação. A aplicação **tem** de devolver verdadeiro ou falso a partir de uma notificação. Deve sempre devolver verdadeiro, a menos que qualquer ação que tentou fazer como resultado da notificação tenha falhado.

* Esta falha pode ser reportada ao serviço do Intune. Um exemplo de cenário a comunicar é se a aplicação não conseguir eliminar os dados de utilizadores após o administrador de TI iniciar uma eliminação.

>[!NOTE]
> É seguro bloquear no `MAMNotificationReceiver.onReceive`, uma vez que a chamada de retorno não está em execução no thread da IU.

A interface `MAMNotificationReceiver`, conforme definido no SDK, é incluída abaixo:

```java
/**
 * The SDK is signaling that a MAM event has occurred.
 *
 */
public interface MAMNotificationReceiver {

    /**
     * A notification was received.
     *
     * @param notification
     *            The notification that was received.
     * @return The receiver should return true if it handled the
     *   notification without error (or if it decided to ignore the
     *   notification). If the receiver tried to take some action in
     *   response to the notification but failed to complete that
     *   action it should return false.
     */
    boolean onReceive(MAMNotification notification);
}
```

### <a name="types-of-notifications"></a>Tipos de notificações

As notificações que se seguem são enviadas para a aplicação e algumas delas podem requerer a participação da aplicação:

* **WIPE_USER_DATA**: esta notificação é enviada numa classe `MAMUserNotification`. Quando essa notificação é recebida, o aplicativo *deve* excluir todos os dados associados à identidade gerenciada (do `MAMUserNotification.getUserIdentity()`). A notificação pode ocorrer por vários motivos, incluindo quando o aplicativo chama `unregisterAccountForMAM`, quando um administrador de ti inicia um apagamento ou quando as políticas de acesso condicional exigidas pelo administrador não são satisfeitas. Se seu aplicativo não se registrar para essa notificação, o comportamento de apagamento padrão será executado. O comportamento padrão excluirá todos os arquivos de um aplicativo de identidade única ou todos os arquivos marcados com a identidade gerenciada para um aplicativo de várias identidades. Essa notificação nunca será enviada no thread da interface do usuário.

* **WIPE_USER_AUXILIARY_DATA**: as aplicações poderão registar-se para obter esta notificação se quiserem utilizar o SDK da Aplicação do Intune para executar o comportamento predefinido de eliminação seletiva, mas ainda quiserem remover alguns dados auxiliares quando ocorrer a eliminação. Essa notificação não está disponível para aplicativos de identidade única--ela só será enviada para aplicativos de várias identidades. Essa notificação nunca será enviada no thread da interface do usuário.

* **REFRESH_POLICY**: esta notificação é enviada numa `MAMUserNotification`. Quando essa notificação é recebida, todas as decisões de política do Intune armazenadas em cache por seu aplicativo devem ser invalidadas e atualizadas. Se seu aplicativo não armazenar nenhuma suposição de política, ele não precisará se registrar para essa notificação. Nenhuma garantia é feita com a qual thread essa notificação será enviada.

* **REFRESH_APP_CONFIG**: essa notificação é enviada em um `MAMUserNotification`. Quando essa notificação é recebida, todos os dados de configuração de aplicativo em cache devem ser invalidados e atualizados. Nenhuma garantia é feita com a qual thread essa notificação será enviada.

* **MANAGEMENT_REMOVED**: esta notificação é enviada numa `MAMUserNotification` e informa a aplicação que está prestes a deixar de ser gerida. Quando já não for gerida, a aplicação deixará de conseguir ler ficheiros encriptados, ler dados encriptados com MAMDataProtectionManager, interagir com a área de transferência encriptada ou participar no ecossistema de aplicações geridas. Veja mais detalhes abaixo. Essa notificação nunca será enviada no thread da interface do usuário.

* **MAM_ENROLLMENT_RESULT**: essa notificação é enviada em um `MAMEnrollmentNotification` para informar ao aplicativo que uma tentativa de registro de aplicativo foi concluída e para fornecer o status dessa tentativa. Nenhuma garantia é feita com a qual thread essa notificação será enviada.

* **COMPLIANCE_STATUS**: essa notificação é enviada em um `MAMComplianceNotification` para informar o aplicativo sobre o resultado de uma tentativa de correção de conformidade. Nenhuma garantia é feita com a qual thread essa notificação será enviada.

> [!NOTE]
> Uma aplicação nunca se deverá registar para as notificações `WIPE_USER_DATA` e `WIPE_USER_AUXILIARY_DATA`.

### <a name="management_removed"></a>MANAGEMENT_REMOVED

A notificação `MANAGEMENT_REMOVED` indica que um usuário gerenciado anteriormente por política não será mais gerenciado pela política de MAM do Intune. Isso não exige a limpeza dos dados do usuário nem a desconexão do usuário (se um apagamento fosse necessário, uma notificação `WIPE_USER_DATA` seria enviada). Muitos aplicativos podem não precisar lidar com essa notificação, no entanto, os aplicativos que usam `MAMDataProtectionManager` devem [tomar nota especial dessa notificação](#data-protection).

Quando o MAM chamar o receptor `MANAGEMENT_REMOVED` do aplicativo, o seguinte será verdadeiro:
* O MAM já descriptografau os arquivos criptografados anteriormente (mas não os buffers de dados protegidos) pertencentes ao aplicativo. Os arquivos em locais públicos no sdcard que não pertencem diretamente ao aplicativo (por exemplo, os documentos ou pastas de download) não são descriptografados.
* Novos arquivos ou buffers de dados protegidos criados pelo método receptor (ou qualquer outro código executado após o início do receptor) não serão criptografados.
* O aplicativo ainda tem acesso às chaves de criptografia, portanto, operações como buffers de dados de descriptografia serão bem sucedidos.

Depois que o receptor do aplicativo retornar, ele não terá mais acesso às chaves de criptografia.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Configurar a Azure Active Directory Authentication Library (ADAL)

Em primeiro lugar, leia as diretrizes de integração da ADAL presentes no [Repositório da ADAL no GitHub](https://github.com/AzureAD/azure-activedirectory-library-for-android).

O SDK depende da [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) nos cenários de [autenticação](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) e início condicional, os quais requerem que as aplicações sejam configuradas com o [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). Os valores de configuração são comunicados ao SDK através de metadados AndroidManifest.

Para configurar a sua aplicação e ativar uma autenticação adequada, adicione o seguinte ao nó da aplicação em AndroidManifest.xml. Algumas destas configurações serão apenas necessárias se a aplicação utilizar a ADAL para autenticação no geral; nesse caso, necessitará dos valores específicos que a aplicação utiliza para se registar no AAD. Esta configuração é feita para garantir que o utilizador final não recebe o pedido de autenticação duas vezes, devido ao facto de o AAD reconhecer dois valores de registo separados: um da aplicação e outro do SDK.

```xml
<meta-data
    android:name="com.microsoft.intune.mam.aad.Authority"
    android:value="https://AAD authority/" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.ClientID"
    android:value="your-client-ID-GUID" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.NonBrokerRedirectURI"
    android:value="your-redirect-URI" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.SkipBroker"
    android:value="[true | false]" />
```

### <a name="adal-metadata"></a>Metadados da ADAL

* **Autoridade** é a autoridade do ADD em utilização. Se este valor estiver em falta, será utilizado o ambiente público do ADD.
    > [!NOTE]
    > Não defina este campo se a sua aplicação tiver deteção de clouds soberanas.

* **ClientID** é o do AAD ClientID (também conhecido como ID do aplicativo) a ser usado. Você deve usar o ClientID do seu próprio aplicativo se ele estiver registrado no Azure AD ou utilizar o [registro padrão](#default-enrollment-optional) se ele não integrar a Adal.

* **NonBrokerRedirectURI** é o URI de redirecionamento do AAD para utilizar em casos sem mediador. Se não for especificado nenhum, será utilizado um valor predefinido de `urn:ietf:wg:oauth:2.0:oob`. Esta predefinição é adequada para a maioria das aplicações.

  * O NonBrokerRedirectURI é usado apenas quando O skipbroker é "true".

* **O skipbroker** é usado para substituir o comportamento de participação de SSO do Adal padrão. O skipbroker deve ser especificado somente para aplicativos que especificam um ClientID **e** não dão suporte a autenticação orientada/SSO de todo o dispositivo. Nesse caso, ele deve ser definido como "true". A maioria dos aplicativos não deve definir o parâmetro O skipbroker.

  * Um ClientID **deve** ser especificado no manifesto para especificar um valor de o skipbroker.

  * Quando um ClientID é especificado, o valor padrão é "false".

  * Quando O skipbroker for "true", o NonBrokerRedirectURI será usado. Os aplicativos que não integram a ADAL (e, portanto, não têm ClientID) também serão padronizados como "true".

### <a name="common-adal-configurations"></a>Configurações comuns da ADAL

Seguem-se algumas formas comuns através das quais uma aplicação pode ser configurada com a ADAL. Localize a configuração da sua aplicação e confirme que define os parâmetros de metadados da ADAL (explicado acima) para os valores necessários. Em todos os casos, a autoridade pode ser especificada se desejado para ambientes não padrão. Se não for especificado, a autoridade do AAD de produção pública será usada.

#### <a name="1-app-does-not-integrate-adal"></a>1. o aplicativo não integra a ADAL
Os metadados de ADAL **não devem** estar presentes no manifesto.

#### <a name="2-app-integrates-adal"></a>2. o aplicativo integra a ADAL

|Parâmetro necessário da ADAL| Valor |
|--|--|
| ClientID | O ClientID da aplicação (gerado pelo Azure AD quando a aplicação é registada) |

A autoridade pode ser especificada se necessário.

Você deve registrar seu aplicativo com o Azure AD e dar acesso ao aplicativo para o serviço de política de proteção de aplicativo:
* Veja [esta página](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) para obter informações sobre como registar uma aplicação com o Azure AD.
* Certifique-se de que as etapas para fornecer permissões de aplicativo Android para o serviço de política de proteção de aplicativo (aplicativo) sejam seguidas. Use as instruções no [guia Introdução ao SDK do Intune](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration) em "Dê ao seu aplicativo acesso ao serviço de proteção de aplicativo do Intune (opcional)". 

Veja também os requisitos para [Acesso Condicional](#conditional-access) abaixo.


#### <a name="3-app-integrates-adal-but-does-not-support-brokered-authenticationdevice-wide-sso"></a>3. o aplicativo integra o ADAL, mas não dá suporte a autenticação orientada/SSO de todo o dispositivo

|Parâmetro necessário da ADAL| Valor |
|--|--|
| ClientID | O ClientID da aplicação (gerado pelo Azure AD quando a aplicação é registada) |
| SkipBroker | **Verdadeiro** |

Autoridade e NonBrokerRedirectURI podem ser especificados se for necessário.

### <a name="conditional-access"></a>Conditional Access
O Acesso Condicional (AC) é uma [funcionalidade](https://docs.microsoft.com/azure/active-directory/develop/active-directory-conditional-access-developer) do Azure Active Directory que pode ser utilizada para controlar o acesso aos recursos do AAD. [Os administradores do Intune podem definir regras de AC](https://docs.microsoft.com/intune/conditional-access) que permitem aceder aos recursos apenas a partir de dispositivos ou aplicações que são geridos pelo Intune. Para garantir que a sua aplicação pode aceder aos recursos quando for adequado, tem de seguir os passos abaixo. Se a aplicação não adquirir tokens de acesso do AAD, ou aceder apenas a recursos que não podem ser protegidos por AC, pode ignorar estes passos.

1. Siga as [diretrizes de integração do ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-android#how-to-use-this-library). 
   Veja o Passo 11 para Utilização de mediador.
2. [Registe a sua aplicação com o Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-app-registration). 
   O URI de redirecionamento encontra-se nas diretrizes de integração do ADAL acima.
3. Defina os parâmetros de metadados de manifesto por [Configurações comuns do ADAL](#common-adal-configurations), item 2, acima.
4. Teste se tudo está configurado corretamente ao ativar a opção [AC baseado no dispositivo](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use) a partir do [portal do Azure](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExchangeConnectorMenu/aad/connectorType/2) e ao confirmar
    - Que o início de sessão na aplicação pede a instalação e inscrição do Portal da Empresa do Intune
    - Que, após a inscrição, o início de sessão na sua aplicação é concluído com êxito.
5. Depois que seu aplicativo tiver enviado a integração do SDK de aplicativo do Intune, entre em contato com msintuneappsdk@microsoft.com para ser adicionado à lista de aplicativos aprovados para [acesso condicional baseado em aplicativo](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use#app-based-conditional-access)
6. Assim que a aplicação tiver sido adicionada à lista aprovada, valide ao [Configurar o AC com base nas aplicações](https://docs.microsoft.com/intune/app-based-conditional-access-intune-create) e certifique-se de que o início de sessão na sua aplicação é concluído com êxito.

## <a name="app-protection-policy-without-device-enrollment"></a>Política de proteção de aplicações sem inscrição de dispositivos

### <a name="overview"></a>Overview
A política de proteção de aplicações do Intune sem a inscrição de dispositivos, também conhecida como APP-WE ou MAM-WE, permite que as aplicações sejam geridas pelo Intune sem a necessidade de o dispositivo ser inscrito no Intune MDM. O APP-WE funciona com ou sem a inscrição do dispositivo. Apesar de ser necessário ter o Portal da Empresa instalado no dispositivo, o utilizador não precisa de iniciar sessão no Portal da Empresa e inscrever o dispositivo.

> [!NOTE]
> Todas as aplicações devem suportar a política de proteção de aplicações sem a inscrição de dispositivos.

### <a name="workflow"></a>Fluxo de Trabalho

Quando uma aplicação cria uma nova conta de utilizador, esta deve registar a conta de gestão com o SDK da Aplicação do Intune. O SDK processará os detalhes da inscrição da aplicação no serviço APP-WE. Se necessário, este repetirá qualquer inscrição em intervalos de tempo adequados caso ocorra alguma falha.

A aplicação também pode consultar o SDK da Aplicação do Intune para obter o estado de um utilizador registado para determinar se este deve ser impedido de aceder ao conteúdo empresarial. Pode registar várias contas de gestão; contudo, de momento, pode apenas inscrever ativamente uma conta com o serviço APP-WE de cada vez. Tal significa que apenas uma conta na aplicação pode receber a política de proteção de aplicações de cada vez.

A aplicação é necessária para fornecer uma chamada de retorno para adquirir o token de acesso adequado a partir do Azure Active Directory Authentication Library (ADAL) em nome do SDK. Assume-se que a aplicação já utiliza a ADAL para autenticação de utilizador e para adquirir os seus próprios tokens de acesso.

Quando a aplicação remove uma conta por completo, esta deve anular o registo dessa conta para indicar que a aplicação já não deve aplicar a política para esse utilizador. Se o utilizador estava inscrito no serviço MAM, a inscrição do utilizador será anulada e a aplicação será apagada.

### <a name="overview-of-app-requirements"></a>Descrição geral dos requisitos da aplicação

Para implementar a integração APP-WE, a aplicação tem de registar a conta de utilizador com o SDK MAM:

1. A aplicação _tem_ de implementar e registar uma instância da interface `MAMServiceAuthenticationCallback`. A instância da chamada de retorno deve ser registada o mais cedo possível no ciclo de vida da aplicação (normalmente no método `onMAMCreate()` da classe de aplicação).

2. Quando é criada uma conta de utilizador e este inicia a sessão com êxito com a ADAL, a aplicação _tem_ de chamar o `registerAccountForMAM()`.

3. Quando uma conta de utilizador é removida, a aplicação deve chamar `unregisterAccountForMAM()` para remover a conta da gestão do Intune.

    > [!NOTE]
    > Se um utilizador terminar a sessão temporariamente na aplicação, a aplicação não precisará chamar `unregisterAccountForMAM()`. A chamada pode iniciar uma eliminação para remover por completo os dados empresariais do utilizador.


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager
Todas as APIs de autenticação e registo necessárias podem ser encontradas na interface `MAMEnrollmentManager`. Pode obter uma referência do `MAMEnrollmentManager` da seguinte forma:

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr
```

Está garantido que a instância `MAMEnrollmentManager` devolvida não é nula. Os métodos API enquadram-se em duas categorias: **autenticação** e **registo de conta**.

```java
package com.microsoft.intune.mam.policy;

public interface MAMEnrollmentManager {
    public enum Result {
        AUTHORIZATION_NEEDED,
        NOT_LICENSED,
        ENROLLMENT_SUCCEEDED,
        ENROLLMENT_FAILED,
        WRONG_USER,
        MDM_ENROLLED,
        UNENROLLMENT_SUCCEEDED,
        UNENROLLMENT_FAILED,
        PENDING,
        COMPANY_PORTAL_REQUIRED;
    }

    //Authentication methods
    interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
    }
    void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
    void updateToken(String upn, String aadId, String resourceId, String token);

    //Registration methods
    void registerAccountForMAM(String upn, String aadId, String tenantId);
    void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
    void unregisterAccountForMAM(String upn);
    Result getRegisteredAccountStatus(String upn);
}
```

### <a name="account-authentication"></a>Autenticação da conta
Esta secção descreve os métodos de autenticação da API no `MAMEnrollmentManager` e como utilizá-los.

```java
interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
}
void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
void updateToken(String upn, String aadId, String resourceId, String token);
```

1. A aplicação tem de implementar a interface `MAMServiceAuthenticationCallback` para permitir que o SDK peça um token da ADAL para o utilizador especificado e o ID de recurso. A instância da chamada de retorno tem de ser fornecida ao `MAMEnrollmentManager` ao chamar o respetivo método `registerAuthenticationCallback()`. Poderá ser preciso um token cedo no ciclo de vida da aplicação para tentativas de inscrição ou registos de atualização da política de proteção de aplicações, para que o local ideal para registar a chamada de retorno esteja no método `onMAMCreate()` da subclasse `MAMApplication` da aplicação.

2. O método `acquireToken()` deve adquirir o token de acesso do ID de recurso pedido para o utilizador especificado. Se não conseguir adquirir o token pedido, este deverá devolver nulo.

    > [!NOTE]
    > Verifique se seu aplicativo utiliza os parâmetros `resourceId` e `aadId` passados para `acquireToken()` para que o token correto seja adquirido.

    ```java
    class MAMAuthCallback implements MAMServiceAuthenticationCallback {
        public String acquireToken(String upn, String aadId, String resourceId) {
            return mAuthContext.acquireTokenSilentSync(resourceId, ClientID, aadId).getAccessToken();
        }
    }
    ```

3. Caso a aplicação não consiga fornecer um token quando o SDK chama o `acquireToken()`, por exemplo, se a autenticação silenciosa falhar e, sendo um período de tempo inconveniente para mostrar uma IU, a aplicação poderá fornecer um token num momento posterior ao chamar o método `updateToken()`. Os mesmos UPN, ID de UPN, ID do AAD e ID de recurso solicitados pela chamada anterior para `acquireToken()` têm de ser transmitidos para `updateToken()`, juntamente com o token que foi, finalmente, adquirido. A aplicação deve invocar este método com o máximo de brevidade possível após ser devolvido o valor nulo da chamada de retorno fornecida.

    > [!NOTE]
    > O SDK ligará para o `acquireToken()` periodicamente para obter o token; por isso, não é estritamente necessário ligar para o `updateToken()`. No entanto, é altamente recomendável, pois pode ajudar os registros e os check-ins de política de proteção de aplicativo a serem concluídos oportunamente.


### <a name="account-registration"></a>Registo da Conta
Esta secção descreve os métodos da API do registo da conta no `MAMEnrollmentManager` e como utilizá-los.

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. Para registar uma conta de gestão, a aplicação deve chamar `registerAccountForMAM()`. Uma conta de utilizador é identificada pelos seus UPN e ID de utilizador do AAD. O ID do inquilino também é necessário para associar os dados de inscrição com o inquilino do AAD do utilizador. A autoridade do usuário também pode ser fornecida para permitir o registro em nuvens soberanas específicas; para obter mais informações, consulte [registro em nuvem soberanas](#sovereign-cloud-registration).  O SDK pode tentar inscrever a aplicação para o utilizador especificado no serviço MAM. Se a inscrição falhar, esta tentará realizar periodicamente a inscrição até que a conta fique não registada. Por norma, o período de repetição é de 12 a 24 horas. O SDK fornece o estado das tentativas de inscrição de modo assíncrono através de notificações.

2. Como a autenticação do AAD é necessária, o melhor momento para registrar a conta de usuário é depois que o usuário entrou no aplicativo e é autenticado com êxito usando a ADAL. A ID do AAD do usuário e a ID do locatário são retornadas da chamada de autenticação da ADAL como parte do objeto [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android) .
    * O ID do inquilino provém do método `AuthenticationResult.getTenantID()`.
    * Pode encontrar informações sobre o utilizador num subobjeto do tipo `UserInfo` proveniente de `AuthenticationResult.getUserInfo()` e o utilizador do AAD ID é obtido a partir desse objeto ao chamar `UserInfo.getUserId()`.

3. Para anular o registo de uma conta da gestão do Intune, a aplicação deve chamar `unregisterAccountForMAM()`. Se a conta tiver sido inscrita com êxito e for gerida, o SDK anulará a inscrição da conta e eliminará os seus dados. As tentativas periódicas de inscrição da conta serão interrompidas. O SDK fornece o status de solicitação de cancelamento de registro de forma assíncrona via notificação.

### <a name="sovereign-cloud-registration"></a>Registo em Clouds Soberanas
As aplicações [com deteção de clouds soberanas](https://www.microsoft.com/trustcenter/cloudservices/nationalcloud) **têm** de fornecer a `authority` para `registerAccountForMAM()`.  Isto pode ser obtido ao fornecer `instance_aware=true` em acquireToken extraQueryParameters na [versão 1.14.0+](https://github.com/AzureAD/azure-activedirectory-library-for-android/releases/tag/v1.14.0) do ADAL e ao invocar `getAuthority()` em AuthenticationCallback AuthenticationResult.

```java
mAuthContext.acquireToken(this, RESOURCE_ID, CLIENT_ID, REDIRECT_URI, PromptBehavior.FORCE_PROMPT, "instance_aware=true",
        new AuthenticationCallback<AuthenticationResult>() {
            @Override
            public void onError(final Exception exc) {
                // authentication failed
            }

            @Override
            public void onSuccess(final AuthenticationResult result) {
                mAuthority = result.getAuthority();
                // handle other parts of the result
            }
        });
```

> [!NOTE]
> Não defina o item de metadados `com.microsoft.intune.mam.aad.Authority` em AndroidManifest. xml.

> [!NOTE]
> Certifique-se de que a autoridade está corretamente definida no seu método `MAMServiceAuthenticationCallback::acquireToken()`.

#### <a name="currently-supported-sovereign-clouds"></a>Cloud Soberanas Suportadas Atualmente

1. Nuvem do governo dos EUA do Azure

### <a name="important-implementation-notes"></a>Notas de implementação importantes

#### <a name="authentication"></a>Autenticação
* Quando a aplicação chama `registerAccountForMAM()`, esta pode receber uma chamada de retorno na sua interface `MAMServiceAuthenticationCallback` pouco tempo depois, num thread diferente. O ideal é que o aplicativo adquirisse seu próprio token do ADAL antes de registrar a conta para agilizar a aquisição do token solicitado. Se o aplicativo retornar um token válido do retorno de chamada, o registro continuará e o aplicativo receberá o resultado final por meio de uma notificação.

* Se a aplicação não devolver um token do AAD válido, o resultado final da tentativa de inscrição será `AUTHENTICATION_NEEDED`. Se o aplicativo receber esse resultado por meio de notificação, é altamente recomendável agilizar o processo de registro adquirindo o token para o usuário e o recurso solicitado anteriormente do `acquireToken()` e chamando o método `updateToken()` para iniciar o processo de registro outra.

* O `MAMServiceAuthenticationCallback` registrado do aplicativo também será chamado para adquirir um token para check-ins de atualização de política de proteção de aplicativo periódico. Se o aplicativo não puder fornecer um token quando solicitado, ele não receberá uma notificação, mas deverá tentar adquirir um token e chamar `updateToken()` no próximo momento conveniente para agilizar o processo de check-in. Se não for fornecido um token, a chamada de retorno será realizada na mesma na próxima tentativa de registo.

* O suporte para cloud soberanas requer que forneça a autoridade.

#### <a name="registration"></a>Registo
* Para sua comodidade, os métodos de registo são idempotentes, por exemplo, `registerAccountForMAM()` registará apenas uma conta e uma tentativa de inscrição da aplicação se a conta ainda não estiver registada e `unregisterAccountForMAM()` apenas anulará o registo de uma conta se esta estiver atualmente registada. As chamadas subsequentes efetuadas são não operativas, por isso, não há qualquer problema em chamar esses métodos mais do que uma vez. Além disso, a correspondência entre as chamadas para esses métodos e as notificações dos resultados não são garantidas, isto é, se `registerAccountForMAM()` for chamado para uma identidade que já esteja registada, a notificação poderá não ser enviada novamente para essa identidade. É possível que sejam enviadas notificações que não correspondem a qualquer chamada para esses métodos, dado que o SDK pode tentar periodicamente realizar inscrições em segundo plano. Adicionalmente, podem ser acionadas anulações de inscrições com a eliminação dos pedidos recebidos do serviço Intune.

* Os métodos de registo podem ser chamados para um qualquer número de identidades diferentes, mas, atualmente, apenas uma conta de utilizador pode ser inscrita com êxito. Se estiverem registadas várias contas de utilizador licenciadas para o Intune e estas forem visadas pela política de proteção de aplicações na mesma altura ou próxima desta, não haverá qualquer garantia sobre qual será a escolhida.

* Por fim, pode consultar o `MAMEnrollmentManager` para ver se uma determinada conta está registada e para obter o seu estado atual com recurso ao método `getRegisteredAccountStatus()`. Se a conta fornecida não estiver registada, este método devolverá **nulo**. Se a conta estiver registada, este método devolverá o estado da conta como um dos membros da enumeração `MAMEnrollmentManager.Result`.

### <a name="result-and-status-codes"></a>Códigos de estados e de resultados
Quando uma conta é registada pela primeira vez, esta começa no estado `PENDING`, o qual indica que a tentativa inicial de inscrição do serviço MAM está incompleta. Depois de concluída a tentativa de inscrição, será enviada uma notificação com um dos Códigos de resultados da tabela abaixo. Além disso, o método `getRegisteredAccountStatus()` devolverá o estado da conta para que a aplicação possa determinar sempre se o acesso ao conteúdo empresarial está bloqueado para esse utilizador. Se a tentativa de inscrição falhar, o estado da conta poderá mudar ao longo do tempo, uma vez que o SDL volta a tentar a inscrição em segundo plano.

|Código do resultado | Explicação |
| -- | -- |
| `AUTHORIZATION_NEEDED` | Esse resultado indica que um token não foi fornecido pela instância `MAMServiceAuthenticationCallback` registrada do aplicativo ou o token fornecido era inválido.  A aplicação deve adquirir um token válido e chamar `updateToken()`, se possível. |
| `NOT_LICENSED` | O utilizador não está licenciado para o Intune ou a tentativa de contacto do serviço da MAM do Intune falhou.  A aplicação deve continuar num estado não gerido (normal) e o utilizador não deve estar bloqueado.  As tentativas de inscrição serão repetidas periodicamente caso o utilizador se torne licenciado no futuro. |
| `ENROLLMENT_SUCCEEDED` | A tentativa de inscrição foi concluída com êxito ou o utilizador já está inscrito.  No caso de uma inscrição com êxito, será enviada uma notificação de atualização da política antes desta notificação.  O acesso a dados empresariais deve ser permitido. |
| `ENROLLMENT_FAILED` | A tentativa de inscrição falhou.  Pode encontrar mais detalhes nos registos do dispositivo.  O aplicativo não deve permitir o acesso a dados corporativos nesse estado, pois foi anteriormente determinado que o usuário está licenciado para o Intune.|
| `WRONG_USER` | Apenas um utilizador por dispositivo pode inscrever uma aplicação com o serviço MAM. Esse resultado indica que o usuário para o qual esse resultado foi entregue (o segundo usuário) é direcionado com a política de MAM, mas um usuário diferente já está registrado. Como a política de MAM não pode ser imposta para o segundo usuário, seu aplicativo não deve permitir o acesso a esses dados do usuário (possivelmente removendo o usuário do seu aplicativo) a menos que/até que o registro desse usuário tenha sucesso em um momento posterior. Simultâneo com o fornecimento desse `WRONG_USER` resultado, o MAM solicitará a opção de remover a conta existente. Se o usuário humano responder no afirmativo, será possível registrar o segundo usuário um pouco mais tarde. Desde que o segundo usuário permaneça registrado, o MAM tentará registrar o registro periodicamente. |
| `UNENROLLMENT_SUCCEEDED` | Anulação da inscrição concluída com êxito.|
| `UNENROLLMENT_FAILED` | O pedido de anulação da inscrição falhou.  Pode encontrar mais detalhes nos registos do dispositivo. Em geral, isso não ocorrerá enquanto o aplicativo passar um UPN válido (nem nulo ou vazio). Não há nenhuma correção direta e confiável que o aplicativo possa tomar. Se esse valor for recebido ao cancelar o registro de um UPN válido, informe-o como um bug para a equipe de MAM do Intune.|
| `PENDING` | A tentativa inicial de inscrição do utilizador está em curso.  A aplicação pode bloquear o acesso a dados empresariais até que o resultado da inscrição seja conhecido, mas não é necessário fazê-lo. |
| `COMPANY_PORTAL_REQUIRED` | O utilizador está licenciado para o Intune, mas a aplicação não pode ser inscrita até que a aplicação Portal da Empresa seja instalada no dispositivo. O SDK da Aplicação do Intune tentará bloquear o acesso à aplicação ao utilizador especificado e direcioná-lo para a instalação da aplicação Portal da Empresa (veja abaixo para obter detalhes). |


### <a name="company-portal-requirement-prompt-override-optional"></a>Ignorar pedido de requisito do Portal da Empresa (opcional)
Se receber o Resultado `COMPANY_PORTAL_REQUIRED`, o SDK bloqueará a utilização das atividades que utilizam a identidade para a qual a inscrição foi solicitada. Em vez disso, o SDK fará com que essas atividades apresentem um pedido para transferir o Portal da Empresa. Se pretender evitar este comportamento na sua aplicação, as atividades poderão implementar `MAMActivity.onMAMCompanyPortalRequired`.

Este método é chamado antes de o SDK apresentar as suas IUs de bloqueio predefinidas. Se a aplicação alterar a identidade da atividade ou anular o registo do utilizador que tentou inscrever-se, o SDK não bloqueará a atividade. Nesta situação, cabe à aplicação evitar a fuga de dados empresariais. Apenas as aplicações de várias identidades (abordadas mais tarde) poderão alterar a identidade de atividade.

Se não herdar explicitamente de `MAMActivity` (uma vez que as ferramentas de compilação farão essa alteração), mas ainda tiver de processar esta notificação, pode implementar `MAMActivityBlockingListener` como alternativa.

### <a name="notifications"></a>Notificações
Se o aplicativo se registrar para notificações do tipo **MAM_ENROLLMENT_RESULT**, um `MAMEnrollmentNotification` será enviado para informar ao aplicativo que a solicitação de registro foi concluída. `MAMEnrollmentNotification` será recebida através da interface `MAMNotificationReceiver`, conforme descrito na secção [Registar para obter notificações do SDK](#register-for-notifications-from-the-sdk).

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}
```

O método `getEnrollmentResult()` devolve o resultado do pedido de inscrição.  Uma vez que `MAMEnrollmentNotification` expande `MAMUserNotification`, a identidade do utilizador para o qual foi tentada a inscrição também está disponível. A aplicação deve implementar a interface `MAMNotificationReceiver` para receber estas notificações, detalhadas na secção [Registar para obter notificações do SDK](#register-for-notifications-from-the-sdk).

O status da conta de usuário registrado pode ser alterado quando uma notificação de registro é recebida, mas não será alterada em todos os casos (por exemplo, se a notificação de `AUTHORIZATION_NEEDED` for recebida após um resultado mais informativo, como `WRONG_USER`, o resultado mais informativo será mantido como o status da conta).  Depois que a conta for inscrita com êxito, o status permanecerá como `ENROLLMENT_SUCCEEDED` até que a conta tenha o registro ou apagamento cancelado.

## <a name="app-ca-with-policy-assurance"></a>AC de aplicativo com garantia de política

### <a name="overview"></a>Overview
Com a AC do aplicativo (acesso condicional) com a garantia de política, o acesso aos recursos é condicional no aplicativo de políticas de Proteção de Aplicativo do Intune.  O AAD impõe isso exigindo que o aplicativo seja registrado e gerenciado pelo aplicativo antes de conceder um token para acessar uma AC de aplicativo com o recurso protegido de garantia de política.  O aplicativo é necessário para usar o agente ADAL para aquisição de token e a configuração é a mesma descrita acima em [acesso condicional](#conditional-access).

### <a name="adal-changes"></a>Alterações de ADAL
A biblioteca ADAL tem um novo código de erro informando ao aplicativo que a falha na aquisição de um token foi causada pela não conformidade com o gerenciamento de aplicativos.  Se o aplicativo receber esse código de erro, ele precisará chamar o SDK para tentar corrigir a conformidade registrando o aplicativo e aplicando a política. Uma exceção será recebida pelo método `onError()` da ADAL `AuthenticationCallback` e terá o código de erro `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED`.  Nesse caso, a exceção pode ser convertida em um `IntuneAppProtectionPolicyRequiredException`, do qual parâmetros adicionais podem ser extraídos para uso na conformidade de correção (consulte o exemplo de código abaixo). Depois que a correção for bem-sucedida, o aplicativo poderá tentar novamente a aquisição do token por meio da ADAL.

> [!NOTE]
> Esse novo código de erro e outro suporte para a AC de aplicativo com garantia de política exigem a versão 1.15.0 (ou superior) da biblioteca ADAL.

### <a name="mamcompliancemanager"></a>MAMComplianceManager
A interface `MAMComplianceManager` é usada quando o erro de política necessária é recebido da ADAL.  Ele contém o método `remediateCompliance()` que deve ser chamado para tentar colocar o aplicativo em um estado compatível. Pode obter uma referência do `MAMComplianceManager` da seguinte forma:

```java
MAMComplianceManager mgr = MAMComponents.get(MAMComplianceManager.class);

// make use of mgr
```

Está garantido que a instância `MAMComplianceManager` devolvida não é nula.

```java
package com.microsoft.intune.mam.policy;

public interface MAMComplianceManager {
    void remediateCompliance(String upn, String aadId, String tenantId, String authority, boolean showUX);
}
```

O método `remediateCompliance()` é chamado para tentar colocar o aplicativo sob gerenciamento para atender às condições do AAD para conceder o token solicitado.  Os quatro primeiros parâmetros podem ser extraídos da exceção recebida pelo método ADAL `AuthenticationCallback.onError()` (consulte o exemplo de código abaixo).  O parâmetro final é um booliano que controla se uma UX é mostrada durante a tentativa de conformidade.  Essa é uma interface de estilo de progresso de bloqueio simples fornecida como padrão para aplicativos que não têm a necessidade de mostrar UX personalizado durante essa operação.  Ele só será bloqueado enquanto a correção de conformidade estiver em andamento e não exibirá o resultado final.  O aplicativo deve registrar um receptor de notificação para lidar com o êxito ou a falha da tentativa de correção de conformidade (veja abaixo).

O método `remediateCompliance()` pode fazer um registro de MAM como parte do estabelecimento da conformidade.  O aplicativo poderá receber uma notificação de registro se tiver registrado um receptor de notificação para notificações de registro.  O `MAMServiceAuthenticationCallback` registrado do aplicativo terá seu método `acquireToken()` chamado para obter um token para o registro de MAM. `acquireToken()` será chamado antes que o aplicativo tenha adquirido seu próprio token, portanto, qualquer tarefa de criação de conta ou de escrituração que o aplicativo faz após uma aquisição de token bem-sucedida pode não ter sido feita ainda.  O retorno de chamada deve ser capaz de adquirir um token nesse caso.  Se você não puder retornar um token de `acquireToken()`, a tentativa de correção de conformidade falhará.  Se você chamar `updateToken()` posteriormente com um token válido para o recurso solicitado, a correção de conformidade será repetida imediatamente com o token fornecido.

> [!NOTE]
> A aquisição de token silenciosa ainda será possível em `acquireToken()` porque o usuário já terá sido guiado para instalar o agente e registrar o dispositivo antes que o erro `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED` seja recebido.  Isso faz com que o agente tenha um token de atualização válido em seu cache, permitindo que acqisition silenciosa do token solicitado seja realizada com sucesso.

Aqui está um exemplo de como receber o erro de política necessária no método `AuthenticationCallback.onError()` e chamar o `MAMComplianceManager` para manipular o erro.

```java
public void onError(@Nullable Exception exc) {
    if (exc instanceof AuthenticationException && 
        ((AuthenticationException) exc).getCode() == ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED) {

        final IntuneAppProtectionPolicyRequiredException policyRequiredException = 
            (IntuneAppProtectionPolicyRequiredException) ex;

        final String upn = policyRequiredException.getAccountUpn();
        final String aadId = policyRequiredException.getAccountUserId();
        final String tenantId = policyRequiredException.getTenantId();
        final String authority = policyRequiredException.getAuthorityURL();

        MAMComplianceManager complianceManager = MAMComponents.get(MAMComplianceManager.class);
        complianceManager.remediateCompliance(upn, aadId, tenantId, authority, showUX);
    }
}
```

### <a name="status-notifications"></a>Notificações de status
Se o aplicativo se registrar para notificações do tipo **COMPLIANCE_STATUS**, um `MAMComplianceNotification` será enviado para informar o aplicativo do status final da tentativa de correção de conformidade. `MAMComplianceNotification` será recebida através da interface `MAMNotificationReceiver`, conforme descrito na secção [Registar para obter notificações do SDK](#register-for-notifications-from-the-sdk).

```java
public interface MAMComplianceNotification extends MAMUserNotification {
    MAMCAComplianceStatus getComplianceStatus();
    String getComplianceErrorTitle();
    String getComplianceErrorMessage();
}
```

O método `getComplianceStatus()` retorna o resultado da tentativa de correção de conformidade como um valor da enumeração `MAMCAComplianceStatus`.

|Código de estado | Explicação |
| -- | -- |
| CONHECIDOS | O status é desconhecido. Isso pode indicar um motivo de falha não previsto. Informações adicionais podem ser encontradas nos logs de Portal da Empresa. |
| EM conformidade | A correção de conformidade foi bem-sucedida e o aplicativo agora está em conformidade com a política. A aquisição do token ADAL deve ser repetida. |
| NOT_COMPLIANT | Falha na tentativa de corrigir a conformidade.  O aplicativo não está em conformidade e a aquisição de token ADAL não deve ser repetida até que a condição de erro seja corrigida.  Informações de erro adicionais são enviadas com o MAMComplianceNotification. |
| SERVICE_FAILURE | Houve uma falha ao tentar recuperar os dados de conformidade do serviço Intune. Informações adicionais podem ser encontradas nos logs de Portal da Empresa. |
| NETWORK_FAILURE | Erro ao conectar ao serviço do Intune. O aplicativo deve tentar sua aquisição de token novamente quando a conexão de rede for restaurada. |
| CLIENT_ERROR | Falha na tentativa de corrigir a conformidade por algum motivo relacionado ao cliente.  Por exemplo, sem token ou usuário errado. Informações de erro adicionais são enviadas com o MAMComplianceNotification. |
| PENDING | Falha na tentativa de corrigir a conformidade porque a resposta de status ainda não foi recebida do serviço quando o limite de tempo foi excedido. O aplicativo deve tentar sua aquisição de token novamente mais tarde. |
| COMPANY_PORTAL_REQUIRED | O Portal da Empresa deve ser instalado no dispositivo para que a correção de conformidade tenha sucesso.  Se o Portal da Empresa já estiver instalado no dispositivo, o aplicativo precisará ser reiniciado.  Nesse caso, será exibida uma caixa de diálogo solicitando que o usuário reinicie o aplicativo. |

Se o status de conformidade for `MAMCAComplianceStatus.COMPLIANT`, o aplicativo deverá reinicializar sua aquisição de token original (para seu próprio recurso). Se a tentativa de correção de conformidade falhar, os métodos `getComplianceErrorTitle()` e `getComplianceErrorMessage()` retornarão cadeias de caracteres localizadas que o aplicativo pode exibir para o usuário final se escolher.  A maioria dos casos de erro não é remediable pelo aplicativo, portanto, para o caso geral, pode ser melhor falhar na criação ou no logon da conta e permitir que o usuário tente novamente mais tarde.  Se uma falha for persistente, os logs de MAM poderão ajudar a determinar a causa.  O usuário final pode enviar os logs usando as instruções encontradas [aqui](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android "Enviar registos ao suporte da empresa por e-mail").

Como `MAMComplianceNotification` estende `MAMUserNotification`, a identidade do usuário para a qual a correção foi tentada também está disponível.

Aqui está um exemplo de registro de um receptor usando uma classe anônima para implementar a interface MAMNotificationReceiver:

```java
final MAMNotificationReceiverRegistry notificationRegistry = MAMComponents.get(MAMNotificationReceiverRegistry.class);
// create a receiver
final MAMNotificationReceiver receiver = new MAMNotificationReceiver() {
    public boolean onReceive(MAMNotification notification) {
        if (notification.getType() == MAMNotificationType.COMPLIANCE_STATUS) {
            MAMComplianceNotification complianceNotification = (MAMComplianceNotification) notification;
            
            // take appropriate action based on complianceNotification.getComplianceStatus()
            
            // unregister this receiver if no longer needed
            notificationRegistry.unregisterReceiver(this, MAMNotificationType.COMPLIANCE_STATUS);
        }
        return true;
    }
};
// register the receiver
notificationRegistry.registerReceiver(receiver, MAMNotificationType.COMPLIANCE_STATUS);
```

> [!NOTE]
> O receptor de notificação deve ser registrado antes de chamar `remediateCompliance()` para evitar uma condição de corrida que pode resultar na perda da notificação.

### <a name="implementation-notes"></a>Notas de implementação
> [!NOTE]
> **Alteração importante!**  <br>
> O método `MAMServiceAuthenticationCallback.acquireToken()` do aplicativo deve passar *false* para o novo sinalizador de `forceRefresh` para `acquireTokenSilentSync()`.
> Anteriormente, recomendamos a passagem de *true* para resolver um problema com a atualização de tokens do agente, mas foi encontrado um problema com a Adal que poderia impedir a aquisição de tokens em alguns cenários se esse sinalizador for *verdadeiro*.
```java
AuthenticationResult result = acquireTokenSilentSync(resourceId, clientId, userId, /* forceRefresh */ false);
```

> [!NOTE]
> Se você quiser mostrar um UX de bloqueio personalizado durante a tentativa de correção, deverá passar *false* para o parâmetro showUX para `remediateCompliance()`. Você deve garantir que você mostre seu UX e Registre seu ouvinte de notificação primeiro antes de chamar `remediateCompliance()`.  Isso impedirá uma condição de corrida em que a notificação poderá ser perdida se `remediateCompliance()` falhar muito rapidamente.  Por exemplo, o método `onCreate()` ou `onMAMCreate()` de uma subclasse Activity é o lugar ideal para registrar o ouvinte de notificação e, em seguida, chamar `remediateCompliance()`.  Os parâmetros para `remediateCompliance()` podem ser passados para sua UX como extras de intenção.  Quando a notificação de status de conformidade é recebida, você pode exibir o resultado ou simplesmente concluir a atividade.

> [!NOTE]
> `remediateCompliance()` registrará a conta e tentará o registro.  Depois que o token principal é adquirido, chamar `registerAccountForMAM()` não é necessário, mas não há nenhum dano ao fazer isso. Por outro lado, se o aplicativo não conseguir adquirir seu token e desejar remover a conta de usuário, ele deverá chamar `unregisterAccountForMAM()` para remover a conta e impedir novas tentativas de registro em segundo plano.

## <a name="protecting-backup-data"></a>Proteger dados de cópias de segurança
A partir do Android Marshmallow (API 23), o Android disponibiliza duas formas de as aplicações fazerem cópias de segurança dos dados. Cada opção está disponível para a sua aplicação e requer passos diferentes para garantir que a proteção de dados do Intune é implementada corretamente. Pode ver na tabela abaixo as ações correspondentes necessárias para o comportamento de proteção de dados correto.  Pode ler mais informações sobre os métodos de cópia de segurança no [Guia de API do Android](https://developer.android.com/guide/topics/data/backup.html).

### <a name="auto-backup-for-apps"></a>Cópia de Segurança Automática para Aplicações
O Android começou a disponibilizar [cópias de segurança automáticas completas](https://developer.android.com/guide/topics/data/autobackup.html) para o Google Drive aplicações em dispositivos Android Marshmallow, independentemente da API de destino da aplicação. Em AndroidManifest.xml, se definir explicitamente `android:allowBackup` como **falso**, a sua aplicação nunca será colocada em fila de espera para cópias de segurança pelo Android e os dados "empresariais" permanecerão na aplicação. Neste caso, não são necessárias mais ações.

No entanto, por predefinição, o atributo `android:allowBackup` é definido como verdadeiro, mesmo que `android:allowBackup` não seja especificado no ficheiro de manifesto. Isto significa que todos os dados de aplicações são automaticamente colocados em cópia de segurança na conta do Google Drive do utilizador, um comportamento predefinido que constitui um **risco de fuga de dados**. Por essa razão, o SDK precisa das alterações descritas abaixo para assegurar que a proteção de dados é aplicada.  É importante seguir as orientações abaixo para proteger devidamente os dados de clientes, se quiser que a aplicação seja executada em dispositivos Android Marshmallow.  

O Intune permite-lhe utilizar todas as [funcionalidades da Cópia de Segurança Automática](https://developer.android.com/guide/topics/data/autobackup.html) disponíveis em Android, incluindo a capacidade de definir regras personalizadas no XML, mas tem de seguir os passos abaixo para proteger os seus dados:

1. Se a sua aplicação **não** utilizar o seu próprio BackupAgent personalizado, utilize o MAMBackupAgent predefinido para permitir cópias de segurança automáticas completas, que estejam em conformidade com a política do Intune. Coloque o seguinte no manifesto da aplicação:

    ```xml
    android:fullBackupOnly="true"
    android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```
    
2. **[Opcional]** Se tiver implementado um BackupAgent personalizado opcional, terá de se certificar de que utiliza um MAMBackupAgent ou MAMBackupAgentHelper. Veja as secções seguintes. Considere mudar para utilizar o **MAMDefaultFullBackupAgent** do Intune (descrito no passo 1), o qual disponibiliza uma cópia de segurança fácil no Android M e posterior.

3. Quando decidir que tipo de cópia de segurança completa a sua aplicação deve receber (não filtrada, filtrada ou nenhuma), terá de definir o atributo `android:fullBackupContent` para verdadeiro, falso ou um recurso XML na sua aplicação.

4. Assim, _**deve**_ copiar o que colocar em `android:fullBackupContent` para uma etiqueta de metadados com o nome `com.microsoft.intune.mam.FullBackupContent` no manifesto.

    **Exemplo 1**: se pretender que a aplicação possua cópias de segurança completas sem exclusões, defina o atributo `android:fullBackupContent` e a etiqueta de metadados `com.microsoft.intune.mam.FullBackupContent` como **verdadeiro**:

    ```xml
    android:fullBackupContent="true"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />  
    ```

    **Exemplo 2**: se pretender que a aplicação utilize o seu BackupAgent personalizado e recuse a utilização de cópias de segurança automáticas em total conformidade com a política do Intune, terá de definir o atributo e a etiqueta de metadados como **falso**:

    ```xml
    android:fullBackupContent="false"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="false" />  
    ```

    **Exemplo 3**: se quiser que a sua aplicação tenha cópias de segurança completas de acordo com as suas regras personalizadas definidas num ficheiro XML, defina o atributo e a etiqueta de metadados para o mesmo recurso XML:

    ```xml
    android:fullBackupContent="@xml/my_scheme"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```

### <a name="keyvalue-backup"></a>Cópia de segurança Chave/Valor
A opção [Key/Value Backup (Cópia de Segurança Chave/Valor)](https://developer.android.com/guide/topics/data/keyvaluebackup.html) está disponível para todas as APIs 8 e posterior e carrega dados da aplicação para o [Android Backup Service (Serviço de Cópia de Segurança do Android)](https://developer.android.com/google/backup/index.html). A quantidade de dados por utilizador da aplicação está limitada a 5 MB. Se utilizar a Cópia de Segurança Chave/Valor, terá de utilizar um **BackupAgentHelper** ou um **BackupAgent**.

### <a name="backupagenthelper"></a>BackupAgentHelper
O BackupAgentHelper é muito mais fácil de implementar do que o BackupAgent, tanto em termos de funcionalidade Android nativa, como de integração da MAM do Intune. O BackupAgentHelper permite ao programador registar ficheiros completos e as preferências partilhadas num **FileBackupHelper** e **SharedPreferencesBackupHelper** (respetivamente), os quais são adicionados em seguida ao BackupAgentHelper após a criação. Siga os passos abaixo para utilizar um BackupAgentHelper com a MAM do Intune:

1. Para utilizar a cópia de segurança de várias identidades com um BackupAgentHelper, siga a secção [Extending BackupAgentHelper (Expandir o BackupAgentHelper)](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgentHelper) no guia do Android.

2. Recorra à sua classe para expandir a MAM equivalente ao BackupAgentHelper, FileBackupHelper e SharedPreferencesBackupHelper.

|Classe Android | MAM equivalente |
|--|--|
|BackupAgentHelper |MAMBackupAgentHelper |
|FileBackupHelper | MAMFileBackupHelper
|SharedPreferencesBackupHelper| MAMSharedPreferencesBackupHelper|

Se seguir estas orientações obterá uma cópia de segurança e um restauro de várias identidades com êxito.

### <a name="backupagent"></a>BackupAgent

Um BackupAgent permite-lhe ser muito mais explícito sobre os dados que farão parte da cópia de segurança. Uma vez que cabe ao programador uma boa parte de responsabilidade quanto à implementação, existem mais passos necessários para garantir a proteção de dados adequada a partir do Intune. Uma vez que a maior parte do trabalho é feita por si, o programador, a integração do Intune é ligeiramente mais envolvida.

**Integrar a MAM:**

1. Leia atentamente [Key/Value Backup](https://developer.android.com/guide/topics/data/keyvaluebackup.html) (Cópia de Segurança Chave/Valor) no guia Android, mais concretamente, [Extending BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) (Expandir o BackupAgent) para garantir que a sua implementação do BackupAgent segue as diretrizes do Android.

2. Recorra à sua classe para expandir o `MAMBackupAgent`.

**Cópia de segurança de várias identidades:**

1. Antes de iniciar a cópia de segurança, verifique se os ficheiros ou as memórias intermédias pretendidas têm efetivamente **permissão do administrador de TI para serem guardados em cópia de segurança** em cenários de várias identidades. Disponibilizamos-lhe a função `isBackupAllowed` em `MAMFileProtectionManager` e `MAMDataProtectionManager` para confirmar isso mesmo. Se não for permitida a cópia de segurança de ficheiros ou memórias intermédias de dados, não deverá continuar a inclui-los na sua cópia de segurança.

2. Se em algum momento durante a cópia de segurança pretender fazer uma cópia de segurança das identidades dos ficheiros selecionados no passo 1, terá de chamar `backupMAMFileIdentity(BackupDataOutput data, File … files)` com os ficheiros a partir dos quais planeia extrair dados. Esta ação irá criar automaticamente novas entidades de cópia de segurança e escrevê-las em `BackupDataOutput` por si. Estas entidades serão consumidas automaticamente após o restauro.

**Restauro de várias identidades:**

O guia de Cópia de Segurança de Dados especifica um algoritmo geral para restaurar os dados da aplicação e fornece um exemplo de código na secção [Extending BackupAgent (Expandir o BackupAgent)](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent). Para realizar um restauro de várias identidades com êxito, tem de seguir a estrutura geral fornecida neste exemplo de código dando especial atenção ao seguinte:

1. Você deve utilizar um loop `while(data.readNextHeader())` para percorrer as entidades de backup. No código anterior, `data` é o nome da variável local para o **MAMBackupDataInput** que é passado para seu aplicativo durante a restauração.

2. Você deve chamar `data.skipEntityData()` se `data.getKey()` não corresponder à chave que você escreveu em `onBackup`. Sem realizar este passo, os seus restauros podem não ter êxito. No código anterior, `data` é o nome da variável local para o **MAMBackupDataInput** que é passado para seu aplicativo durante a restauração.

3. Evite retornar enquanto estiver consumindo entidades de backup na construção `while(data.readNextHeader())`, pois as entidades que escrevemos automaticamente serão perdidas. No código anterior, `data` é o nome da variável local para o **MAMBackupDataInput** que é passado para seu aplicativo durante a restauração.

## <a name="multi-identity-optional"></a>Várias identidades (opcional)

### <a name="overview"></a>Overview
Por predefinição, o SDK da Aplicação do Intune aplica a política à aplicação como um todo. As várias identidades são uma funcionalidade de proteção opcional da aplicação do Intune que pode ser ativada para permitir que a política seja aplicada num nível por identidade. Esta opção requer uma participação da aplicação significativamente maior do que outras funcionalidades de proteção da aplicação.

> [!NOTE]
> A falta de participação correta da aplicação pode resultar na perda de dados e noutros problemas de segurança.

Quando o utilizador inscrever o dispositivo ou a aplicação, o SDK regista esta identidade e considera-a a identidade gerida primária do Intune. Os outros utilizadores na aplicação serão tratados como não geridos, com definições de política não restrita.

> [!NOTE]
> Atualmente, apenas é suportada uma identidade gerida do Intune por dispositivo.

Uma identidade é definida como uma cadeia de carateres. As identidades são **sensíveis às maiúsculas e minúsculas** e os pedidos de identidade ao SDK podem não devolver a mesma utilização de maiúsculas e minúsculas que tinha sido originalmente utilizada ao definir a identidade.

A aplicação *tem* de informar o SDK quando tenciona alterar a identidade ativa. Em alguns casos, o SDK também notifica a aplicação quando é necessária uma alteração de identidade. No entanto, na maioria dos casos, a MAM não consegue reconhecer os dados que são apresentados na IU ou que são utilizados a dada altura num thread e baseia-se na aplicação para definir a identidade correta, de forma a evitar a fuga de dados. Nas secções seguintes, serão destacados alguns cenários específicos que requerem uma ação por parte da aplicação.

### <a name="enabling-multi-identity"></a>Ativar Identidades Múltiplas
Por predefinição, todas as aplicações são consideradas aplicações de identidade única. Pode declarar que uma aplicação tem conhecimento de várias identidades ao colocar os seguintes metadados no ficheiro AndroidManifest.xml.

```xml
  <meta-data
    android:name="com.microsoft.intune.mam.MAMMultiIdentity"
    android:value="true" />
```

### <a name="setting-the-identity"></a>Definir a Identidade
Os programadores podem definir a identidade do utilizador da aplicação nos seguintes níveis por ordem decrescente de prioridade:

  1. Nível de thread
  2. nível `Context` (geralmente `Activity`)
  3. Nível de processo

Uma identidade definida no nível de thread prevalece sobre uma identidade definida no nível `Context`, que prevalece sobre uma identidade definida no nível de processo. Uma identidade definida em um `Context` é usada somente em cenários associados apropriados. As operações de e/s de arquivo, por exemplo, não têm um `Context` associado. Normalmente, os aplicativos definirão a identidade `Context` em um `Activity`. Um aplicativo não *deve* exibir dados para uma identidade gerenciada, a menos que a identidade `Activity` seja definida com a mesma identidade. Em geral, a identidade ao nível do processo só é útil se a aplicação funcionar apenas com um utilizador de cada vez em todos os threads. É possível que muitas das aplicações não precisem de a utilizar.

Se seu aplicativo usa o contexto `Application` para adquirir serviços do sistema, verifique se a identidade do processo ou thread foi definida ou se você definiu a identidade da interface do usuário no contexto `Application` do seu aplicativo.

Para lidar com casos especiais ao atualizar a identidade da interface do usuário com `setUIPolicyIdentity` ou `switchMAMIdentity`, ambos os métodos podem ser passados como um conjunto de valores `IdentitySwitchOption`.

* `IGNORE_INTENT`: use se estiver solicitando uma opção de identidade que deve ignorar a intenção associada à atividade atual.
  Por exemplo:

  1. Seu aplicativo recebe uma intenção de uma identidade gerenciada que contém um documento gerenciado e seu aplicativo exibe o documento.
  2. O usuário alterna para sua identidade pessoal, para que seu aplicativo solicite uma opção de identidade de interface do usuário. Na identidade pessoal, seu aplicativo não está mais exibindo o documento, portanto, você usa `IGNORE_INTENT` ao solicitar a troca de identidade.

  Se não estiver definido, o SDK assumirá que a intenção mais recente ainda está sendo usada no aplicativo. Isso fará com que a política de recebimento para a nova identidade trate a intenção como dados de entrada e use sua identidade.

>[!NOTE]
> Como o `CLIPBOARD_SERVICE` é usado para operações de interface do usuário, o SDK usa a identidade da interface do usuário da atividade de primeiro plano para operações `ClipboardManager`.
> Os seguintes métodos no `MAMPolicyManager` podem ser utilizados para definir a identidade e obter os valores de identidade anteriormente definidos.

```java
public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback, final EnumSet<IdentitySwitchOption> options);

  public static String getUIPolicyIdentity(final Context context);

  public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

  public static String getProcessIdentity();

  public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

  public static String getCurrentThreadIdentity();

/**
   * Get the current app policy. This does NOT take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use the overload below.
   */
  public static AppPolicy getPolicy();

  /**
  * Get the current app policy. This DOES take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use this function.
   */
  public static AppPolicy getPolicy(final Context context);


  public static AppPolicy getPolicyForIdentity(final String identity);

  public static boolean getIsIdentityManaged(final String identity);
  ```

>[!NOTE]
> Pode limpar a identidade da aplicação ao defini-la como nula.
>
> A cadeia vazia pode ser utilizada como uma identidade que nunca terá uma política de proteção de aplicações.

#### <a name="results"></a>Resultados
Todos os métodos utilizados para definir a identidade comunicam os valores de resultado através do `MAMIdentitySwitchResult`. Existem quatro valores que podem ser devolvidos:

| Valor devolvido | Cenário |
|--            |--        |
| `SUCCEEDED`    | A alteração de identidade foi concluída com êxito. |
| `NOT_ALLOWED`  | A alteração de identidade não é permitida. Isso ocorre se for feita uma tentativa de definir a identidade da interface do usuário (`Context`) quando uma identidade diferente for definida no thread atual. |
| `CANCELLED`    | O utilizador cancelou a alteração de identidade, geralmente ao premir o botão Anterior num pedido de PIN ou autenticação. |
| `FAILED`       | A alteração de identidade falhou por um motivo não especificado.|

O aplicativo deve garantir que uma troca de identidade seja bem-sucedida antes de exibir ou usar dados corporativos. Atualmente, as alterações de identidade de processos e threads serão sempre concluídas com êxito numa aplicação com várias identidades. No entanto, reservamos o direito de adicionar condições de falha. A alteração de identidade da IU poderá falhar no caso de argumentos inválidos, se a mesma entrar em conflito com a identidade do thread ou se o utilizador cancelar os requisitos de início condicional (por exemplo, o utilizador prime o botão Anterior no ecrã de PIN). O comportamento padrão para uma opção de identidade de interface do usuário com falha em uma atividade é concluir a atividade (consulte `onSwitchMAMIdentityComplete` abaixo).

No caso da definição de uma identidade `Context` via `setUIPolicyIdentity`, o resultado é relatado de forma assíncrona. Se o `Context` for um `Activity`, o SDK não saberá se a alteração de identidade foi bem-sucedida até que a inicialização condicional seja executada, o que pode exigir que o usuário insira um PIN ou credenciais corporativas. O aplicativo pode implementar um `MAMSetUIIdentityCallback` para receber esse resultado ou pode passar NULL para o objeto de retorno de chamada. Observe que, se uma chamada for feita para `setUIPolicyIdentity`, embora o resultado de uma chamada anterior para `setUIPolicyIdentity` *no mesmo contexto* ainda não tenha sido entregue, o novo retorno de chamada substituirá o antigo e o retorno de chamada original nunca receberá um resultado.

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

Também pode definir a identidade de uma atividade diretamente através de um método `MAMActivity` em vez de chamar `MAMPolicyManager.setUIPolicyIdentity`. Utilize o método seguinte para tal:

```java
     public final void switchMAMIdentity(final String newIdentity, final EnumSet<IdentitySwitchOption> options);
```

Poderá também substituir um método no `MAMActivity` se pretender que a aplicação seja notificada do resultado de tentativas para alterar a identidade dessa atividade.

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

Se você não substituir `onSwitchMAMIdentityComplete` (ou chamar o método `super`), uma mudança de identidade com falha em uma atividade fará com que a atividade seja concluída. Se você substituir o método, deverá cuidar de que os dados corporativos não são exibidos após uma mudança de identidade com falha.

>[!NOTE]
> Alterar a identidade pode requerer a recriação da atividade. Neste caso, a chamada de retorno `onSwitchMAMIdentityComplete` será entregue na nova instância da atividade.


### <a name="implicit-identity-changes"></a>Alterações de Identidade Implícitas
Além da capacidade da aplicação de definir a identidade, a identidade de um contexto ou thread poderá mudar com base na entrada de dados de outra aplicação gerida pelo Intune com uma política de proteção de aplicações.

#### <a name="examples"></a>Exemplos
1. Se uma atividade for iniciada a partir de um `Intent` enviado por outra aplicação para MAM, a identidade da atividade será definida com base na identidade real na outra aplicação no ponto em que o `Intent` foi enviado.

2. Para serviços, a identidade do thread será definida de forma semelhante durante uma chamada `onStart` ou `onBind`. As chamadas para `Binder` devolvidas do `onBind` também irão definir temporariamente a identidade do thread.

3. De forma semelhante, as chamadas para um `ContentProvider` irão definir a identidade do thread na duração das mesmas.


    Além disso, interação do utilizador com uma atividade poderá causar uma mudança de identidade implícita.

    **Exemplo:** um utilizador que desista de um pedido de autorização durante `Resume` resultará numa mudança implícita para uma identidade vazia.

    Esta aplicação tem uma oportunidade de ter conhecimento destas alterações e, se necessário, a aplicação pode proibi-las. `MAMService` e `MAMContentProvider` expõem o seguinte método, que as subclasses podem substituir:

    ```java
    public void onMAMIdentitySwitchRequired(final String identity,
      final AppIdentitySwitchResultCallback callback);
    ```

    Na classe `MAMActivity`, um parâmetro adicional está presente no método:

    ```java
    public void onMAMIdentitySwitchRequired(final String identity,
      final AppIdentitySwitchReason reason,
      final AppIdentitySwitchResultCallback callback);
    ```

    * O `AppIdentitySwitchReason` captura a origem da mudança implícita e pode aceitar os valores `CREATE`, `RESUME_CANCELLED` e `NEW_INTENT`.  O motivo `RESUME_CANCELLED` é utilizado quando a retoma da atividade gera a apresentação de PIN, autenticação ou outra IU de conformidade e o utilizador tenta desistir dessa IU, normalmente através do botão de retrocesso.


    * `AppIdentitySwitchResultCallback` encontra-se da seguinte forma:

      ```java
      public interface AppIdentitySwitchResultCallback {
          /**
            * @param result
            *            whether the identity switch can proceed.
            */
          void reportIdentitySwitchResult(AppIdentitySwitchResult result);
        }
        ```

      Sendo que ```AppIdentitySwitchResult``` é `SUCCESS` ou `FAILURE`.

O método `onMAMIdentitySwitchRequired` é chamado para todas as alterações de identidade implícitas, exceto nas que forem efetuadas através de um Enlaçamento devolvido de `MAMService.onMAMBind`. As implementações predefinidas de `onMAMIdentitySwitchRequired` chamam de imediato:

* `reportIdentitySwitchResult(FAILURE)` quando o motivo é `RESUME_CANCELLED`.

* `reportIdentitySwitchResult(SUCCESS)` em todos os outros casos.

  Não é esperado que a maioria das aplicações precise de bloquear ou atrasar uma mudança de identidade numa forma diferente, mas se uma aplicação precisar de o fazer, os seguintes pontos têm de ser tidos em conta:

  * Se a alteração de identidade é bloqueada, o resultado é o mesmo como se as definições de partilha de `Receive` tivessem proibido a entrada de dados.

  * Se um Serviço estiver em execução no thread principal, `reportIdentitySwitchResult` **terá** de ser chamado de forma síncrona ou o thread da IU será bloqueado.

  * Para a criação de **`Activity`** , `onMAMIdentitySwitchRequired` será chamado antes de `onMAMCreate`. Se a aplicação tiver de mostrar a IU para determinar se a mudança de identidade deve ser permitida, a IU terá de ser apresentada com uma identidade *diferente*.

  * Em um **`Activity`** , quando uma mudança para a identidade vazia é solicitada com o motivo como `RESUME_CANCELLED`, o aplicativo deve modificar a atividade retomada para exibir dados consistentes com essa opção de identidade.  Se tal não for possível, a aplicação deverá recusar a mudança e será novamente pedido ao utilizador que fique em conformidade com a política da identidade retomada (por exemplo, ao ver o ecrã de introdução de PIN da aplicação).

    > [!NOTE]
    > Uma aplicação com várias identidades irá sempre receber dados de aplicações geridas e não geridas. É da responsabilidade da aplicação tratar dados de identidades geridas de forma gerida.

  Se uma identidade solicitada for gerida (utilize `MAMPolicyManager.getIsIdentityManaged` para verificar), mas a aplicação não puder utilizar essa conta (por exemplo, porque primeiro têm de ser configuradas contas na aplicação, como contas de e-mail), a mudança de identidade deverá ser recusada.

#### <a name="build-plugin--tool-considerations"></a>Considerações sobre o plug-in/ferramenta de compilação
Se você não herdar explicitamente de `MAMActivity`, `MAMService` ou `MAMContentProvider` (porque permite que as ferramentas de compilação façam essa alteração), mas ainda precisa processar os comutadores de identidade, em vez disso, você pode implementar `MAMActivityIdentityRequirementListener` (para um `Activity`) ou `MAMIdentityRequirementListener` (para `Service` ou `ContentProviders`) .
O comportamento predefinido para `MAMActivity.onMAMIdentitySwitchRequired` pode ser acedido ao chamar o método estático `MAMActivity.defaultOnMAMIdentitySwitchRequired(activity, identity,
reason, callback)`.

Da mesma forma, se necessitar de substituir `MAMActivity.onSwitchMAMIdentityComplete`, poderá implementar `MAMActivityIdentitySwitchListener` sem herdar explicitamente de `MAMActivity`.

### <a name="preserving-identity-in-async-operations"></a>Preservar a Identidade em Operações Assíncronas
É comum as operações na thread de IU distribuírem tarefas em segundo plano para outra thread. Uma aplicação com várias identidades quererá confirmar que estas tarefas em segundo plano operam com a identidade adequada. Muitas vezes, essa é a mesma identidade que foi utilizada pela atividade que as distribuiu. O SDK de MAM fornece o `MAMAsyncTask` e o `MAMIdentityExecutors` como conveniência para ajudar a preserva a identidade.
Eles devem ser usados se a operação assíncrona puder gravar dados corporativos em um arquivo ou se se comunicar com outros aplicativos.

#### <a name="mamasynctask"></a>MAMAsyncTask
Para usar `MAMAsyncTask`, simplesmente herde dele em vez de `AsyncTask` e substitua as substituições de `doInBackground` e `onPreExecute` por `doInBackgroundMAM` e `onPreExecuteMAM`, respectivamente. O construtor `MAMAsyncTask` adquire um contexto de atividade. Por exemplo:

```java
  AsyncTask<Object, Object, Object> task = new MAMAsyncTask<Object, Object, Object>(thisActivity) {

    @Override
    protected Object doInBackgroundMAM(final Object[] params) {
        // Do operations.
    }

    @Override
    protected void onPreExecuteMAM() {
        // Do setup.
    };
}
```

### <a name="mamidentityexecutors"></a>MAMIdentityExecutors
O `MAMIdentityExecutors` permite-lhe encapsular uma instância existente do `Executor` ou do `ExecutorService` como um `Executor`/`ExecutorService` que preserva a identidade com métodos `wrapExecutor` e `wrapExecutorService`. Por exemplo

```java
  Executor wrappedExecutor = MAMIdentityExecutors.wrapExecutor(originalExecutor, activity);
  ExecutorService wrappedService = MAMIdentityExecutors.wrapExecutorService(originalExecutorService, activity);
```

### <a name="file-protection"></a>Proteção de Ficheiros
Todos os ficheiros têm uma identidade associada na altura da criação, com base na identidade de processo e thread. Esta identidade será utilizada para encriptação de ficheiros e eliminação seletiva. Apenas os ficheiros cuja identidade é gerida e tenha uma política que requeira encriptação serão encriptados. A funcionalidade de eliminação seletiva predefinida do SDK irá eliminar apenas ficheiros associados à identidade gerida para a qual uma eliminação tenha sido solicitada. A aplicação poderá consultar ou alterar a identidade de um ficheiro ao utilizar a classe `MAMFileProtectionManager`.

```java
public final class MAMFileProtectionManager {

   /**
    * Protect a file or directory. This will synchronously trigger whatever protection is required for the file, and will tag the
    * file for future protection changes. If an identity is set on a directory, it is set recursively on all files and
    * subdirectories. New files or directories will inherit their parent directory's identity. If MAM is operating in offline mode,
    * this method will silently do nothing.
    *
    * @param identity
    *       Identity to set.
    * @param file
    *       File to protect.
    *
    * @throws IOException
    *       If the file cannot be protected.
    */
   public static void protect(final File file, final String identity) throws IOException;

   /**
     * Protect a file obtained from a content provider. This is intended to be used for
     * sdcard (whether internal or removable) files accessed through the Storage Access Framework.
     * It may also be used with descriptors referring to private files owned by this app.
     * It is not intended to be used for files owned by other apps and such usage will fail. If
     * creating a new file via a content provider exposed by another MAM-integrated app, the new
     * file identity will automatically be set correctly if the ContentResolver in use was
     * obtained via a Context with an identity or if the thread identity is set.
     *
     * This will synchronously trigger whatever protection is required for the file, and will tag
     * the file for future protection changes. If an identity is set on a directory, it is set
     * recursively on all files and subdirectories. If MAM is operating in offline mode, this
     * method will silently do nothing.
     *
     * @param identity
     *            Identity to set.
     * @param file
     *            File to protect.
     *
     * @throws IOException
     *             If the file cannot be protected.
     */
    public static void protect(final ParcelFileDescriptor file, final String identity) throws IOException;

   /**
    * Get the protection info on a file.
    *
    * @param file
    *            File or directory to get information on.
    * @return File protection info, or null if there is no protection info.
    * @throws IOException
    *             If the file cannot be read or opened.
    */
    public static MAMFileProtectionInfo getProtectionInfo(final File file) throws IOException;

   /**
    * Get the protection info on a file.
    *
    * @param file
    *            File or directory to get information on.
    * @return File protection info, or null if there is no protection info.
    * @throws IOException
    *             If the file cannot be read or opened.
    */
    public static MAMFileProtectionInfo getProtectionInfo(final ParcelFileDescriptor file) throws IOException;

}

public interface MAMFileProtectionInfo {
    String getIdentity();
}
 ```

#### <a name="app-responsibility"></a>Responsabilidade da Aplicação
A MAM não consegue inferir uma relação entre ficheiros que estão a ser lidos e dados a serem apresentados numa `Activity`. As aplicações *têm* de definir a identidade da IU corretamente antes de apresentarem dados da empresa. Isto inclui os dados lidos em ficheiros. Se um ficheiro vier de uma origem externa à aplicação (quer venha de um `ContentProvider` ou seja lido a partir de uma localização pública que permita a escrita), a aplicação *tem* de tentar determinar a identidade do ficheiro (através do comando `MAMFileProtectionManager.getProtectionInfo`) antes de apresentar as informações lidas a partir do ficheiro. Se o comando `getProtectionInfo` comunicar uma identidade que não seja nula nem vazia, a identidade da IU *tem* de ser definida de modo a corresponder a esta identidade (através do comando `MAMActivity.switchMAMIdentity` ou `MAMPolicyManager.setUIPolicyIdentity`). Se a alteração de identidade falhar, os dados do ficheiro *não podem* ser apresentados.

Um fluxo de exemplo deverá ser semelhante ao seguinte:
* O usuário seleciona um documento para abrir no aplicativo.
  * Durante o fluxo aberto, antes de ler dados do disco, o aplicativo confirma a identidade que deve ser usada para exibir o conteúdo:

    ```java
    MAMFileProtectionInfo info = MAMFileProtectionManager.getProtectionInfo(docPath)
    if (info != null)
        MAMPolicyManager.setUIPolicyIdentity(activity, info.getIdentity(), callback, EnumSet.noneOf<IdentitySwitchOption.class>)
    ```

  * O aplicativo aguarda até que um resultado seja relatado para o retorno de chamada.
  * Se o resultado comunicado for uma falha, a aplicação não apresentará o documento.
* O aplicativo abre e renderiza o arquivo.
  
#### <a name="single-identity-to-multi-identity-transition"></a>Única identidade para transição de várias identidades
Se um aplicativo que foi lançado anteriormente com a integração do Intune de identidade única mais tarde integrar várias identidades, os aplicativos instalados anteriormente passarão por uma transição (não visível para o usuário, não há nenhuma UX associada). O aplicativo não *precisa* fazer nada explícito para lidar com essa transição. Todos os arquivos criados antes da transição continuarão sendo considerados gerenciados (portanto, permanecerão criptografados se a política de criptografia estiver ativada). Se desejar, você pode detectar a atualização e usar `MAMFileProtectionManager.protect` para marcar arquivos ou diretórios específicos com a identidade vazia (o que removerá a criptografia se elas foram criptografadas).

#### <a name="offline-scenarios"></a>Cenários Offline
A etiquetagem de identidade de ficheiros é sensível ao modo offline. Os seguintes pontos deverão ser levados em consideração:

* Se o Portal da Empresa não estiver instalado, a etiquetagem de identidade dos ficheiros não poderá ser efetuada.

* Se o Portal da Empresa estiver instalado, mas a aplicação não estiver a política da MAM do Intune instalada, os ficheiros não poderão ter uma etiquetagem de identidade de forma fiável.

* Quando a etiquetagem de identidade for disponibilizada, todos os ficheiros anteriormente criados serão tratados como pessoais/não geridos (pertencentes à identidade de cadeia vazia), a menos que a aplicação tenha sido anteriormente instalada como aplicação gerida com identidade única. Nesse caso, serão tratados como pertencentes ao utilizador inscrito.

### <a name="directory-protection"></a>Proteção de Diretório
Os diretórios podem ser protegidos com recurso ao mesmo método `protect` utilizado para proteger ficheiros. A proteção do diretório é aplicada recursivamente a todos os ficheiros e subdiretórios contidos no diretório e a novos ficheiros criados no diretório. Como a proteção de diretório é aplicada recursivamente, a chamada `protect` pode demorar algum tempo a concluir no caso de diretórios grandes. Por esse motivo, as aplicações a aplicar proteção num diretório que contém um grande número de ficheiros poderão querer executar a função `protect` de modo assíncrono no thread de segundo plano.

### <a name="data-protection"></a>Proteção de dados
Não é possível etiquetar um ficheiro como pertencente a identidades múltiplas. As aplicações que têm de armazenar dados pertencentes a utilizadores diferentes no mesmo ficheiro podem fazê-lo manualmente ao utilizar as funcionalidades fornecidas por `MAMDataProtectionManager`. Isto permite à aplicação encriptar dados e associá-los a um utilizador específico. Os dados encriptados são adequados para armazenamento no disco de um ficheiro. Pode consultar os dados associados à identidade e os dados podem ser desencriptados posteriormente.

As aplicações que utilizam o `MAMDataProtectionManager` devem implementar um recetor para a notificação `MANAGEMENT_REMOVED`. Após a conclusão desta notificação, as memórias intermédias que estavam protegidas através desta classe deixarão de ser legíveis caso a encriptação de ficheiros tenha sido ativada quando as memórias intermédias foram protegidas. Um aplicativo pode corrigir essa situação chamando `MAMDataProtectionManager.unprotect` em todos os buffers durante essa notificação. Também é seguro chamar a função proteger durante esta notificação se quiser manter as informações de identidade – a encriptação desativada é garantida durante a notificação.

```java

public final class MAMDataProtectionManager {
    /**
     * Protect a stream. This will return a stream containing the protected
     * input.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect, read sequentially. This function
     *            will change the position of the stream but may not have
     *            read the entire stream by the time it returns. The
     *            returned stream will wrap this one. Calls to read on the
     *            returned stream may cause further reads on the original
     *            input stream. Callers should not expect to read directly
     *            from the input stream after passing it to this method.
     *            Calling close on the returned stream will close this one.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static InputStream protect(final InputStream input, final String identity);

    /**
     * Protect a byte array. This will return protected bytes.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static byte[] protect(final byte[] input, final String identity) throws IOException;

    /**
     * Unprotect a stream. This will return a stream containing the
     * unprotected input.
     *
     * @param input
     *            Input data to protect, read sequentially.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static InputStream unprotect(final InputStream input) throws IOException;

    /**
     * Unprotect a byte array. This will return unprotected bytes.
     *
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static byte[] unprotect(final byte[] input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input stream to get information on. Either this input
     *            stream must have been returned by a previous call to
     *            protect OR input.markSupported() must return true.
     *            Otherwise it will be impossible to get protection info
     *            without advancing the stream position. The stream must be
     *            positioned at the beginning of the protected data.
     * @return Data protection info, or null if there is no protection
     *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final InputStream input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input bytes to get information on. These must be bytes
     *            returned by a previous call to protect() or a copy of
     *            such bytes.
     * @return Data protection info, or null if there is no protection
     *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final byte[] input) throws IOException;
}
```

### <a name="content-providers"></a>Fornecedores de Conteúdo
Se o aplicativo fornecer dados corporativos diferentes de um `ParcelFileDescriptor` por meio de um `ContentProvider`, o aplicativo deverá chamar o método `isProvideContentAllowed(String)` no `MAMContentProvider`, passando o UPN da identidade do proprietário (nome UPN) para o conteúdo. Se esta função devolver "falso", os conteúdos *não podem* ser devolvidos ao chamador. Os descritores de ficheiros devolvidos através de um fornecedor de conteúdos são processados automaticamente, com base na identidade do ficheiro.

Se você não herdar `MAMContentProvider` explicitamente e, em vez disso, permitir que as ferramentas de compilação façam essa alteração, você pode chamar uma versão estática do mesmo método: `MAMContentProvider.isProvideContentAllowed(provider,
contentIdentity)`.

### <a name="selective-wipe"></a>Eliminação Seletiva
Se uma aplicação de várias identidades se registar para a notificação `WIPE_USER_DATA`, é da responsabilidade da aplicação remover todos os dados do utilizador que está a ser eliminado, incluindo todos os ficheiros que foram identificados como pertencentes a esse utilizador. Se a aplicação remover os dados do utilizador de um ficheiro, mas quiser deixar outros dados no ficheiro, esta *tem* de alterar a identidade do ficheiro (através de `MAMFileProtectionManager.protect` para um utilizador pessoal ou identidade vazia). Se estiver a ser utilizada uma política de encriptação, os ficheiros restantes pertencentes ao utilizador que está a ser eliminado não serão desencriptados e ficarão inacessíveis para a aplicação após a eliminação.

Se uma aplicação se registar para `WIPE_USER_DATA`, não terá o benefício do comportamento predefinido de eliminação seletiva por parte do SDK. Para aplicações com conhecimento de várias identidades, esta perda pode ser mais significativa, dado que a eliminação seletiva predefinida da MAM elimina apenas os ficheiros cuja identidade é visada para eliminação. Se uma aplicação com conhecimento de várias identidades pretender que a eliminação seletiva predefinida da MAM seja realizada _**e**_ pretender realizar as suas próprias ações na eliminação, esta deverá registar-se para as notificações de `WIPE_USER_AUXILIARY_DATA`. Esta notificação será enviada imediatamente pelo SDK antes de executar a eliminação seletiva predefinida do SDK. Um aplicativo nunca deve se registrar para `WIPE_USER_DATA` e `WIPE_USER_AUXILIARY_DATA`.

O apagamento seletivo padrão fechará o aplicativo normalmente, concluindo as atividades e eliminando o processo do aplicativo. Se seu aplicativo substituir o apagamento seletivo padrão, convém considerar fechar seu aplicativo manualmente para impedir que o usuário acesse dados na memória após a ocorrência de um apagamento.

## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>Ativar a configuração de MAM direcionada para aplicações Android (opcional)
Pares chave-valor específicos do aplicativo podem ser configurados no console do Intune para [Mam-nós](https://docs.microsoft.com/intune/app-configuration-policies-managed-app) e [Android Enterprise](https://docs.microsoft.com/intune/app-configuration-policies-use-android).
Estes pares chave-valor não são interpretados pelo Intune, mas são enviados para a aplicação. As aplicações que querem receber esse tipo de configuração podem utilizar as classes `MAMAppConfigManager` e `MAMAppConfig` para o efeito. Se houver múltiplas políticas direcionadas para a mesma aplicação, poderão existir múltiplos valores em conflito disponíveis para a mesma chave.

> [!NOTE] 
> Configuração de configurações para entrega por meio de MAM-não podemos ser delievered em `offline` (quando o Portal da Empresa não está instalado).  Somente Android Enterprise AppRestrictions será entregue por meio de um `MAMUserNotification` em uma identidade vazia nesse caso.

### <a name="get-the-app-config-for-a-user"></a>Obter a configuração do aplicativo para um usuário
A configuração do aplicativo pode ser recuperada da seguinte maneira:
```java
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
```

Se não houver nenhum usuário registrado no MAM, mas seu aplicativo ainda quiser recuperar a configuração do Android Enterprise (que não será direcionada a um usuário específico), você poderá passar uma cadeia de caracteres nula ou vazia.

### <a name="conflicts"></a>Entrar
Um valor definido na configuração do aplicativo MAM substituirá um valor com o mesmo conjunto de chaves na configuração do Android Enterprise. 

Se um administrador configurar valores conflitantes para a mesma chave (por exemplo, direcionando conjuntos de configuração de aplicativo diferentes com a mesma chave para vários grupos que contêm o mesmo usuário), o Intune não terá nenhuma maneira de resolver esse conflito automaticamente e fará todos os valores disponível para seu aplicativo. 

Seu aplicativo pode solicitar todos os valores de uma determinada chave de um objeto `MAMAppConfig`:
```java
List<Boolean> getAllBooleansForKey(String key)
List<Long> getAllIntegersForKey(final String key)
List<Double> getAllDoublesForKey(final String key)
List<String> getAllStringsForKey(final String key)
```

ou solicite um valor a ser escolhido:
```java
Boolean getBooleanForKey(String key, BooleanQueryType queryType)
Long getIntegerForKey(String key, NumberQueryType queryType)
Double getDoubleForKey(String key, NumberQueryType queryType)
String getStringForKey(String key, StringQueryType queryType)

enum BooleanQueryType {
    /**
     * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
     */
    Any,
    /**
     * In case of conflict, returns true if any of the values are true.
     */
    Or,
    /**
     * In case of conflict, returns false if any of the values are false.
     */
    And
}

enum NumberQueryType {
    /**
     * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
     */
    Any,
    /**
     * In case of conflict, returns the minimum Integer.
     */
    Min,
    /**
     * In case of conflict, returns the maximum Integer.
     */
    Max
}

enum StringQueryType {
    /**
     * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
     */
    Any,
    /**
     * In case of conflict, returns the first result ordered alphabetically.
     */
    Min,

    /**
     * In case of conflict, returns the last result ordered alphabetically.
     */
    Max
}
```

Seu aplicativo também pode solicitar os dados brutos como uma lista de conjuntos de pares chave-valor.

```java
List<Map<String, String>> getFullData()
```

### <a name="full-example"></a>Exemplo completo
```java
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
String fooValue = null;
if (appConfig.hasConflict("foo")) {
    List<String> values = appConfig.getAllStringsForKey("foo");
    fooValue = chooseBestValue(values);
} else {
    valueToUse = appConfig.getStringForKey("foo", MAMAppConfig.StringQueryType.Any);
}
Long barValue = appConfig.getIntegerForKey("bar", MAMAppConfig.NumberQueryType.Min);
```

### <a name="notification"></a>Notificação
A configuração da aplicação adiciona um novo tipo de notificação:
* **REFRESH_APP_CONFIG**: esta notificação é enviada numa `MAMUserNotification` e informa a aplicação de que os novos dados de configuração da aplicação estão disponíveis.

### <a name="further-reading"></a>Leitura adicional
Para obter mais informações sobre como criar uma política de configuração de aplicações de MAM direcionada no Android, veja a secção na configuração de aplicação de MAM direcionada em [Como utilizar as políticas de configuração de aplicações do Microsoft Intune para Android](https://docs.microsoft.com/intune/app-configuration-policies-managed-app).

A configuração do aplicativo também pode ser configurada usando o API do Graph. Para obter informações, consulte a [configuração direcionada API do Graph docs for Mam](https://docs.microsoft.com/graph/api/resources/intune-mam-targetedmanagedappconfiguration).

## <a name="style-customization-optional"></a>Personalização de Estilo (opcional)
As vistas geradas pelo SDK da MAM podem ser personalizadas visualmente para ficarem mais parecidos com a aplicação na qual este está integrado. Pode personalizar as cores primárias, secundárias e de fundo, assim como o tamanho do logótipo da aplicação. Esta personalização do estilo é opcional e serão utilizadas as predefinições caso não seja configurado qualquer estilo personalizado.

### <a name="how-to-customize"></a>Como personalizar
Para aplicar alterações de estilo às vistas da MAM do Intune, deve primeiro criar um ficheiro XML de substituição do estilo. Este ficheiro deve ser colocado no diretório “/ res/xml” da aplicação e poderá atribuir-lhe um nome se preferir. Abaixo pode ver um exemplo de formato que este ficheiro tem de seguir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<styleOverrides>
    <item
        name="foreground_color"
        resource="@color/red"/>
    <item
        name="accent_color"
        resource="@color/blue"/>
    <item
        name="background_color"
        resource="@color/green"/>
    <item
        name="logo_image"
        resource="@drawable/app_logo"/>
</styleOverrides>
```

Tem de reutilizar os recursos já existentes na sua aplicação. Por exemplo, tem de definir a cor verde no ficheiro colors.xml e mencioná-la aqui. Não é possível utilizar o código de cor hexadecimal “#0000ff”. O tamanho máximo do logótipo da aplicação é de 110 dip (dp). Pode utilizar uma imagem do logótipo mais pequena, mas ao manter o tamanho máximo obterá os melhores resultados. Se exceder o limite de 110 dip, a qualidade da imagem será reduzida e, possivelmente, ficará esbatida.

Abaixo pode ver uma lista completa de atributos de estilo permitidos, os elementos de IU que estes controlam, os seus nomes de item do atributo XML e o tipo de recursos esperados de cada um.

|Atributo do estilo | Elementos da IU afetados | Nome do item do atributo | Tipo de recurso esperado |
| -- | -- | -- | -- |
| Cor de fundo | Cor de fundo do ecrã de PIN <Br>Cor de preenchimento da caixa do PIN | background_color | Cor |
| Cor de primeiro plano | Cor do texto de primeiro plano <br> Limite da caixa do PIN no estado predefinido <br> Carateres (incluindo carateres oculto) na caixa do PIN quando o utilizador introduz um PIN| foreground_color | Cor|
| Cor do ambiente | Limite da caixa do PIN quando realçado <br> Hiperligações |accent_color | Cor |
| Logótipo da aplicação | Ícone grande que aparece no ecrã de PIN da aplicação Intune | logo_image | Desenhável |

## <a name="default-enrollment-optional"></a>Inscrição predefinida (opcional)
Seguem-se orientações para exigir pedidos de início de sessão ao utilizador ao iniciar aplicações para uma inscrição automática no serviço APP-WE (isto é denominado **inscrição predefinida** nesta secção), exigir políticas de proteção de aplicações do Intune para permitir que apenas os utilizadores protegidos pelo Intune utilizem a sua aplicação LOB para Android integrada com SDK. Também abrangem a ativação do SSO para a sua aplicação LOB para Android integrada com SDK. Tal **não** é suportado pelas aplicações da loja que podem ser utilizadas por utilizadores sem Intune.

> [!NOTE] 
> As vantagens da **inscrição predefinida** incluem um método simplificado de obtenção de políticas do serviço APP-WE para uma aplicação no dispositivo.

> [!NOTE] 
> O **registro padrão** tem reconhecimento de nuvem soberanas.

Habilite o registro padrão com as seguintes etapas:

1. Se seu aplicativo integrar a ADAL ou você precisar habilitar o SSO, [Configure a Adal](#configure-azure-active-directory-authentication-library-adal) seguindo #2 de [configuração comuns do Adal](#common-adal-configurations) . Caso contrário, você pode ignorar esta etapa.
   
2. Habilite o registro padrão colocando o seguinte valor no manifesto:
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />
   ```
   > [!NOTE] 
   > Esta tem de ser a única integração da MAM-WE na aplicação. Irão surgir conflitos se existirem outras tentativas de chamar as APIs MAMEnrollmentManager.

3. Ative a política de MAM necessária ao colocar o valor seguinte no manifesto:
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />
   ```
   > [!NOTE] 
   > Esta ação força o utilizador a transferir o Portal da Empresa para o dispositivo e a concluir o fluxo da inscrição predefinida antes da utilização.

## <a name="limitations"></a>Limitações

### <a name="policy-enforcement-limitations"></a>Limitações de imposição de políticas

* **Utilizar Resoluções de Conteúdos**: a política do Intune de “transferência ou receção” pode bloquear ou bloquear parcialmente a utilização de uma resolução de conteúdos para aceder ao fornecedor de conteúdos noutra aplicação. Isso fará com que os métodos `ContentResolver` retornem nulo ou lance um valor de falha (por exemplo, `openOutputStream` lançará `FileNotFoundException` se estiver bloqueado). A aplicação pode determinar se uma falha ao escrever dados através de uma resolução de conteúdos foi causada pela política (ou seria causada pela política) ao efetuar a chamada:

    ```java
    MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(contentURI);
    ```

    ou se não houver nenhuma atividade associada:

    ```java
    MAMPolicyManager.getPolicy().getIsSaveToLocationAllowed(contentURI);
    ```

    No segundo caso, as aplicações com várias identidades devem definir corretamente a identidade do thread (ou passar uma identidade explícita para a chamada `getPolicy`).

### <a name="exported-services"></a>Serviços exportados
O ficheiro AndroidManifest.xml incluído no SDK da Aplicação Intune contém **MAMNotificationReceiverService**, que tem de ser um serviço exportado para permitir ao Portal da Empresa enviar notificações para uma aplicação gerida. O serviço verifica o autor da chamada para assegurar que apenas o Portal da Empresa está autorizado a enviar notificações.

### <a name="reflection-limitations"></a>Limitações da reflexão
Algumas das classes base de MAM (por exemplo, `MAMActivity`, `MAMDocumentsProvider`) contêm métodos (com base nas classes base Android originais) que usam tipos de parâmetro ou de retorno somente presentes acima de determinados níveis de API. Por este motivo, poderá nem sempre ser possível utilizar reflexões para enumerar todos os métodos de componentes de aplicações. Esta restrição não está limitada a MAM. É a mesma restrição que seria aplicada caso a própria aplicação implementasse estes métodos a partir de classes base de Android.

### <a name="robolectric"></a>Robolectric
Não é suportado testar o comportamento do SDK de MAM no Robolectric. Há problemas conhecidos ao executar o SDK do MAM em Robolectric devido a comportamentos presentes em Robolectric que não imitam com precisão aqueles em dispositivos reais ou emuladores.

Se você precisar testar seu aplicativo em Robolectric, a solução alternativa recomendada é mover a lógica de classe do aplicativo para um auxiliar e produzir seu apk de teste de unidade com uma classe de aplicativo que não herda de MAMApplication.

## <a name="expectations-of-the-sdk-consumer"></a>Expectativas do consumidor do SDK
O SDK do Intune mantém o contrato fornecido pela API Android, embora possam ser acionadas condições de falha mais frequentemente como resultado da imposição de políticas. Estas melhores práticas para Android reduzirão a probabilidade de falhas:

* As funções do SDK Android que podem devolver valores nulos têm uma maior probabilidade de ter um valor nulo agora.  Para minimizar os problemas, certifique-se de que as verificações de valores nulos estão nos locais corretos.

* As funcionalidades que podem ser verificadas têm de o ser através das respetivas APIs de substituição da MAM.

* As funções derivadas têm de fazer chamadas através das respetivas versões de superclasses.

* Evitar utilizar qualquer API de uma forma ambígua. Por exemplo, utilizar `Activity.startActivityForResult` sem verificar o requestCode causará um comportamento estranho.

## <a name="telemetry"></a>Telemetria

O SDK da Aplicação Intune para Android não controla a coleção de dados da sua aplicação. Por padrão, o aplicativo Portal da Empresa registra os dados gerados pelo sistema. Estes dados são enviados para o Microsoft Intune. De acordo com a política da Microsoft, não coletamos dados pessoais.

> [!NOTE]
> Se os utilizadores finais não enviarem estes dados, têm de desativar a telemetria em Definições na aplicação Portal da Empresa. Para saber mais, veja [Desativar a recolha de dados da Microsoft](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android). 

## <a name="recommended-android-best-practices"></a>Melhores práticas recomendadas para Android

* Todos os projetos de biblioteca devem partilhar o mesmo android:package sempre que possível. Assim, não falhará esporadicamente no tempo de execução, uma vez que se trata puramente de um problema de tempo de compilação. As versões mais recentes do SDK da Aplicação do Intune irão remover algumas das redundâncias.

* Utilizar as ferramentas de compilação do SDK Android.

* Remover todas as bibliotecas desnecessárias e não utilizadas (por exemplo, android.support.v4)

## <a name="testing"></a>Testado
Consulte o [Guia de testes](app-sdk-android-testing-guide.md).