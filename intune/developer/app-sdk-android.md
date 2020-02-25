---
title: Guia para programadores do SDK da Aplicação do Microsoft Intune para Android
description: O SDK da Aplicação do Microsoft Intune para Android permite incorporar a gestão de aplicações móveis (MAM) do Intune na sua aplicação Android.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/19/2020
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
ms.openlocfilehash: d5ea77eb3f5ab93573c68325d34eca40a1158ef8
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569426"
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
* **Microsoft.Intune.MAM.SDK.DownlevelStubs.aar**: Esta ArA contém canhotos para classes de sistemas Android que estão presentes apenas em dispositivos mais recentes, mas que são referenciados por métodos em `MAMActivity`. Os dispositivos mais recentes ignorarão estas classes de stub. Esta ArA só é necessária se a sua aplicação realizar reflexão sobre aulas provenientes de `MAMActivity`, e a maioria das aplicações não precisa de a incluir. A ArA contém regras ProGuard para excluir todas as suas classes.
* **com.microsoft.Intune.mam.Build.JAR**: um plug-in do Gradle que [ajuda a integrar o SDK](#build-tooling).
* **CHANGELOG.txt**: fornece um registo das alterações feitas em cada versão do SDK.
* **THIRDPARTYNOTICES.TXT**: aviso de atribuição que reconhece código de terceiros e/ou OSS que será compilado na sua aplicação.

## <a name="requirements"></a>Requisitos

### <a name="android-versions"></a>Versões Android
O SDK suporta o Android API 19 (Android 4.4+) através do Android API 28 (Android 9.0).

### <a name="company-portal-app"></a>Aplicação do Portal da Empresa
O SDK da Aplicação do Intune para Android baseia-se na presença da aplicação [Portal da Empresa](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) no dispositivo para ativar as políticas de proteção. O Portal da Empresa obtém as políticas de proteção de aplicações do serviço Intune. Quando a aplicação é inicializada, é carregada a política e o código para impor essa política a partir do Portal da Empresa.

> [!NOTE]
> Quando a aplicação Portal da Empresa não está no dispositivo, uma aplicação gerida pelo Intune tem o mesmo comportamento que uma aplicação normal que não suporta as políticas de proteção de aplicações do Intune.

Para a proteção de aplicações sem inscrição de dispositivos, o utilizador _**não**_ é obrigado a inscrever o dispositivo através da aplicação Portal da Empresa.

## <a name="sdk-integration"></a>Integração do SDK

### <a name="sample-app"></a>App de amostras
Um exemplo de como integrar-se corretamente com o Intune App SDK está disponível no [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App). Este exemplo utiliza o [plugin de construção Gradle](#gradle-build-plugin).

### <a name="referencing-intune-app-libraries"></a>Fazer referência a bibliotecas da Aplicação do Intune

O SDK da Aplicação do Intune é uma biblioteca do Android padrão sem dependências externas. O **Microsoft.Intune.MAM.SDK.aar** contém as interfaces necessárias para a ativação da política de proteção de aplicações e o código necessário para interagir com a aplicação Portal da Empresa do Microsoft Intune.

O **Microsoft.Intune.MAM.SDK.aar** tem de ser especificado como uma referência da biblioteca do Android. Para tal, abra o projeto de aplicação no Android Studio e aceda a **Ficheiro > Novo > Novo módulo** e selecione **Importar Pacote .JAR/.AAR**. Em seguida, selecione o nosso pacote de arquivo Android Microsoft.Intune.MAM.SDK.aar para criar um módulo para o . AAR. Clique com o botão direito do rato no módulo ou módulos que contêm o código da aplicação e aceda a **Definições do Módulo** > **separador Dependências** > **ícone +** > **Dependência do módulo** > Selecione o módulo de AAR do SDK de MAM que acabou de criar > **OK**. Esta ação irá garantir que o seu módulo é compilado com o SDK de MAM quando criar o seu projeto.

Além disso, as bibliotecas do **Microsoft.Intune.MAM.SDK.Support.XXX.jar** contêm variantes do Intune das bibliotecas do `android.support.XXX` correspondentes. Não são compiladas no Microsoft.Intune.MAM.SDK.aar, caso uma aplicação não necessite de depender das bibliotecas de suporte.

#### <a name="proguard"></a>ProGuard

Se o [ProGuard](http://proguard.sourceforge.net/) (ou qualquer outro mecanismo de redução/ocultação) for utilizado como um passo de compilação, o SDK tem regras de configuração adicionais que têm de ser incluídas. Ao incluir o . AAR na sua construção, as nossas regras são automaticamente integradas no passo de proguarda e os ficheiros de classe necessários são mantidos.

As Azure Active Directory Authentication Libraries (ADAL) podem ter as suas próprias restrições ProGuard. Se a sua aplicação integrar a ADAL, terá de seguir a documentação da ADAL referente a essas restrições.

### <a name="policy-enforcement"></a>Imposição de políticas
O SDK da Aplicação do Intune é uma biblioteca do Android que permite que a sua aplicação suporte e participe na imposição de políticas do Intune. 

A maioria das políticas são aplicadas semi-automaticamente, mas certas políticas requerem [a participação explícita da sua app para fazer cumprir](#enable-features-that-require-app-participation).
Independentemente de realizar a integração de fontes ou utilizar ferramentas de construção para integração, as políticas que requerem participação explícita terão de ser codificadas.

Para políticas que são automaticamente aplicadas, as aplicações são necessárias para substituir a herança de várias classes base Android por herança de equivalentes MAM e substituir similarmente chamadas para certas classes de serviços do sistema Android por chamadas para equivalentes MAM. As substituições específicas necessárias são detalhadas [abaixo](#class-and-method-replacements) e podem ser realizadas manualmente com integração de fontes ou realizadas automaticamente através da ferramenta de construção.

### <a name="build-tooling"></a>Ferramentas de compilação
O SDK fornece ferramentas de construção (um plugin para construções gradle e uma ferramenta de linha de comando para construções não Gradle) que executam substituições equivalentes MAM automaticamente. Estas ferramentas transformam os ficheiros de classe gerados pela compilação de Java e não modificam o código fonte original.

As ferramentas realizam [apenas substituições diretas.](#class-and-method-replacements) Não efetuam quaisquer integrações de SDK mais complexas, como a [Política Guardar Como](#enable-features-that-require-app-participation), a [Identidades Múltiplas](#multi-identity-optional), o [registo App-WE](#app-protection-policy-without-device-enrollment), [modificações AndroidManifest](#manifest-replacements) ou a [configuração da ADAL](#configure-azure-active-directory-authentication-library-adal), pelo que estes têm de ser concluídos antes de a sua aplicação estar totalmente compatível com o Intune. Leia atentamente o resto deste documento para ver os pontos de integração relevantes para a sua aplicação.

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
* `zap.jar`**não** é reescrito porque não é um projeto e não está incluído em `includeExternalLibraries`
* `com.contoso.foo:zap-artifact:1.0.0` é reescrito porque está incluído em `includeExternalLibraries`
* `com.microsoft.bar:baz:1.0.0` é reescrito porque está incluído em `includeExternalLibraries` através de um caráter universal (`com.microsoft.*`).
* `com.microsoft.qux:foo:2.0` não é reescrita, mesmo que corresponda ao mesmo wildcard que o item anterior porque é explicitamente excluído através de um padrão de negação.

#### <a name="usage-of-includeexternallibraries"></a>Utilização de includeExternalLibraries

Uma vez que, por predefinição, o plug-in só funciona em dependências do projeto (geralmente fornecidas pela função `project()`), todas as dependências especificadas por `fileTree(...)` ou obtidas a partir do Maven ou de outras origens de pacote (por exemplo, "`com.contoso.bar:baz:1.2.0`") têm de ser fornecidas à propriedade `includeExternalLibraries`, caso o processamento de MAM das mesmas seja necessário com base nos critérios explicados abaixo. São suportados carateres universais ("*"). Um item que começa com `!` é uma negação e pode ser usado para excluir bibliotecas que de outra forma seriam incluídas por um wildcard.

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
O plugin de construção pode gerar um relatório html das mudanças que faz. Para solicitar a geração deste relatório, especifique `report = true` no bloco de configuração `intunemam`. Se gerado, o relatório será escrito para `outputs/logs` no diretório de construção.

```groovy
intunemam {
    report = true
}
```

#### <a name="verification"></a>Verificação
O plugin de construção pode executar verificação adicional para procurar possíveis erros nas aulas de processamento. Para solicitar isto, especifique `verify = true` no bloco de configuração `intunemam`. Note que isto pode adicionar alguns segundos ao tempo tomado pela tarefa do plugin.

```groovy
intunemam {
    verify = true
}
```

#### <a name="incremental-builds"></a>Construções incrementais
Para permitir o suporte para a construção de forma incremental, especifique `incremental = true` no bloco de configuração `intunemam`.  Esta é uma funcionalidade experimental destinada a aumentar o desempenho da construção, processando apenas os ficheiros de entrada que mudaram.  A configuração predefinida é `false`.

```groovy
intunemam {
    incremental = true
}
```

#### <a name="dependencies"></a>Dependências

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
> Em sistemas unix-like semi-cólon é um separador de comando. Para evitar que o reservatório se separe dos comandos, certifique-se de escapar de cada semi-cólon com '\' ou embrulhe o parâmetro completo em aspas.

#### <a name="example-command-line-tool-invocation"></a>Invocação de exemplo da Ferramenta de Linha de Comandos

``` batch
> BuildTool\bin\BuildTool.bat --input build\product-foo-project;libs\bar.jar --output mam-build\product-foo-project;mam-build\libs\bar.jar --classpath build\zap.jar;libs\Microsoft.Intune.MAM.SDK\classes.jar;%ANDROID_SDK_ROOT%\platforms\android-27\android.jar --excludeClasses com.contoso.SplashActivity
```

Este exemplo teria os seguintes efeitos:

* O diretório `product-foo-project` é reescrito para `mam-build\product-foo-project`
* `bar.jar` é reescrito para `mam-build\libs\bar.jar`
* `zap.jar`**não** é reescrito porque é apenas apresentado em `--classpath`
* A classe `com.contoso.SplashActivity`**não** é reescrita, mesmo que se encontre em `--input`

> [!NOTE] 
> Atualmente, a ferramenta de compilação não suporta ficheiros aar. Se o seu sistema de compilação não extrair o `classes.jar` ao processar ficheiros aar, terá de fazê-lo antes de invocar a ferramenta de compilação.


## <a name="class-and-method-replacements"></a>Substituições de classes e métodos

As classes base Android têm de ser substituídas pelos respetivos equivalentes de MAM para ativar a gestão do Intune. As classes do SDK estão entre a classe base Android e a própria versão derivada da aplicação dessa classe. Por exemplo, a atividade de uma aplicação poderá terminar com uma hierarquia de herança semelhante à seguinte: `Activity` > `MAMActivity` >
`AppSpecificActivity`. A camada MAM filtra chamadas para operações do sistema, para fornecer uma vista gerida global à sua aplicação de forma totalmente integrada.

Além das classes base, algumas classes que a sua aplicação pode utilizar sem derivação (por exemplo, `MediaPlayer`) também exigem equivalentes de MAM e [algumas chamadas de método também têm de ser substituídas](#wrapped-system-services). Os detalhes exatos são indicados abaixo.

> [!NOTE] 
> Se a sua aplicação estiver a integrar-se com a ferramenta de [construção](#build-tooling)SDK, as seguintes substituições de classe e método são realizadas automaticamente.

| Classe base Android | Substituição do SDK da Aplicação do Intune |
|--|--|
| android.app.Activity | MAMActivity |
| android.app.ActivityGroup | MAMActivityGroup |
| android.app.AliasActivity | MAMAliasActivity |
| android.app.Application | MAMApplication |
| android.app.Dialog | MAMDialog |
| android.app.AlertDialog.Builder | MAMAlertDialogBuilder |
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
| android.support.v7.app.AlertDialog.Builder | MAMAlertDialogBuilder |
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
| android.content.ContentProviderClient | MAMContentProviderClientManagement |
| android.content.ContentResolver | MAMContentResolverManagement |
| android.content.pm.PackageManager | MAMPackageManagement |
| android.app.DownloadManager | MAMDownloadManagement |
| android.print.PrintManager | MAMPrintManagement |
| android.support.v4.print.PrintHelper | MAMPrintHelperManagement |
| android.view.View | MAMViewManagement |
| android.view.DragEvent | MAMDragEventManagement |
| android.app.NotificationManager | Gestão de Notificações mAM |
| android.support.v4.app.NotificationManagerCompat | MAMNotificationCompatManagement |

Algumas aulas têm a maioria dos seus métodos embrulhados, por exemplo, `ClipboardManager`, `ContentProviderClient`, `ContentResolver`e `PackageManager`, enquanto outras aulas têm apenas um ou dois métodos embrulhados, por exemplo, `DownloadManager`, `PrintManager`, `PrintHelper`, `View`, `DragEvent`, `NotificationManager` e `NotificationManagerCompat`. Consulte as APIs expostas pelas classes equivalentes MAM para obter o método exato se não utilizar o BuildPlugin.

### <a name="manifest-replacements"></a>Substituições do manifesto
Poderá ser preciso realizar algumas das substituições de classe indicadas acima no manifesto, bem como no código Java. De destacar:
* As referências do manifesto a `android.support.v4.content.FileProvider` devem ser substituídas por `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider`.

## <a name="androidx-libraries"></a>Bibliotecas AndroidX
Com o Android P, a Google anunciou um novo conjunto (com um novo nome) de bibliotecas de suporte chamado AndroidX e a versão 28 é a versão principal mais recente das bibliotecas android.support existentes.

Ao contrário das bibliotecas de suporte do Android, não fornecemos variantes de MAM das bibliotecas AndroidX. Em alternativa, o AndroidX deve ser tratado como qualquer outra biblioteca externa e configurado para ser reescrito com o plug-in/ferramenta de compilação. Para as construções gradle, isso pode ser feito incluindo `androidx.*` no campo `includeExternalLibraries` do plugin config. As invocações da ferramenta de linhas de comando devem listar explicitamente todos os ficheiros do frasco.

### <a name="pre-androidx-architecture-components"></a>Componentes de arquitetura pré-AndroidX
Muitos componentes de arquitetura Android, incluindo Room, ViewModel e WorkManager foram reembalados para AndroidX. Se a sua aplicação utilizar as variantes pré-AndroidX destas bibliotecas, certifique-se de que as reescritas são aplicadas, incluindo `android.arch.*` no campo `includeExternalLibraries` do plugin config. Em alternativa, atualize as bibliotecas para os seus equivalentes AndroidX.

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

Muitas aplicações implementam funcionalidades que permitem ao utilizador final guardar os ficheiros localmente ou num serviço de armazenamento na nuvem. O SDK da Aplicação do Intune permite aos administradores de TI aplicar restrições de políticas que considerem mais adequadas na organização, para proteger contra fugas de dados.  Uma das políticas que o administrador de TI pode controlar é se o utilizador final pode guardar num arquivo de dados "pessoal" não gerido. Isto inclui guardar numa localização local, num cartão SD ou em serviços de cópias de segurança de terceiros.

**A participação da aplicação é necessária para ativar a funcionalidade.** Se a aplicação permitir guardar em localizações pessoais ou na cloud diretamente a partir da aplicação, tem de implementar esta funcionalidade para garantir que o administrador de TI pode controlar se a gravação numa localização é permitida. A API abaixo permite à aplicação saber se a gravação num arquivo pessoal é permitida pela política do administrador do Intune atual. Em seguida, a aplicação pode impor a política, uma vez que tem conhecimento do arquivo de dados pessoal disponível para o utilizador final através da aplicação.  

Para determinar se a política é imposta, faça a seguinte chamada:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

O parâmetro `service` deve ser um dos seguintes valores `SaveLocation`:


- `SaveLocation.ONEDRIVE_FOR_BUSINESS`
- `SaveLocation.SHAREPOINT`
- `SaveLocation.LOCAL`
- `SaveLocation.OTHER`

O `username` deve ser o UPN/username/email associado ao serviço de nuvem a que o serviço de nuvem está a ser guardado (*não* necessariamente o mesmo que o utilizador que possui o documento a ser guardado). Utilize nulo se não existir um mapeamento entre o AAD UPN e o nome de utilizador do serviço na nuvem ou se não for conhecido o nome de utilizador. `SaveLocation.LOCAL` não é um serviço na nuvem e por isso deve ser sempre utilizado com um parâmetro `null` nome de utilizador.

O método anterior para determinar se uma política de utilizador permitia guardar dados em várias localizações era `getIsSaveToPersonalAllowed()`, dentro da mesma classe **AppPolicy**. Esta função é agora **preterida** e não deve ser utilizada, a invocação seguinte é equivalente a `getIsSaveToPersonalAllowed()`:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(SaveLocation.LOCAL, null);
```

>[!NOTE]
> Utilize `SaveLocation.OTHER` se a localização em questão não estiver listada no enum **SaveLocations**.

### <a name="example-determine-if-notifications-with-organization-data-need-to-be-restricted"></a>Exemplo: Determinar se as notificações com dados da organização precisam de ser restringidas

Se a sua aplicação apresentar notificações, deve verificar a política de restrição de notificação do utilizador associado à notificação antes de apresentar a notificação. Para determinar se a política é aplicada, faça a seguinte chamada.

```java
NotificationRestriction notificationRestriction =
    MAMPolicyManager.getPolicyForIdentity(notificationIdentity).getNotificationRestriction();
```

Se a restrição for `BLOCKED`, a aplicação não deve apresentar notificações para o utilizador associado a esta política. Se `BLOCK_ORG_DATA`, a aplicação deve apresentar uma notificação modificada que não contenha dados da organização. Se `UNRESTRICTED`, todas as notificações são permitidas.

Se `getNotificationRestriction` não for invocada, o MAM SDK fará o melhor esforço para restringir automaticamente as notificações para aplicações de identidade única. Se o bloqueio automático estiver ativado e `BLOCK_ORG_DATA` estiver definido, a notificação não será mostrada de todo. Para obter um controlo mais fino, verifique o valor da `getNotificationRestriction` e modifique adequadamente as notificações da aplicação.

## <a name="register-for-notifications-from-the-sdk"></a>Registar para obter notificações do SDK

### <a name="overview"></a>Descrição geral
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

* **WIPE_USER_DATA**: esta notificação é enviada numa classe `MAMUserNotification`. Quando esta notificação for recebida, a aplicação *deve* eliminar todos os dados associados à identidade gerida (de `MAMUserNotification.getUserIdentity()`). A notificação pode ocorrer por diversas razões, incluindo quando a sua aplicação chama `unregisterAccountForMAM`, quando um administrador de TI inicia uma limpeza, ou quando as políticas de acesso condicional exigidas pela administração não estão satisfeitas. Se a sua aplicação não se registar para esta notificação, será realizado um comportamento de limpeza predefinida. O comportamento padrão irá eliminar todos os ficheiros para uma aplicação de identidade única ou todos os ficheiros marcados com a identidade gerida para uma aplicação multi-identidade. Esta notificação nunca será enviada no fio UI.

* **WIPE_USER_AUXILIARY_DATA**: as aplicações poderão registar-se para obter esta notificação se quiserem utilizar o SDK da Aplicação do Intune para executar o comportamento predefinido de eliminação seletiva, mas ainda quiserem remover alguns dados auxiliares quando ocorrer a eliminação. Esta notificação não está disponível para aplicações de identidade únicas -- que só será enviada para aplicações multi-identidade. Esta notificação nunca será enviada no fio UI.

* **REFRESH_POLICY**: esta notificação é enviada numa `MAMUserNotification`. Quando esta notificação for recebida, quaisquer decisões políticas intune em cache pela sua app devem ser invalidadas e atualizadas. Se a sua aplicação não armazenar quaisquer pressupostos de política, não precisa de se registar para esta notificação. Não são dadas garantias sobre em que fio esta notificação será enviada.

* **REFRESH_APP_CONFIG**: Esta notificação é enviada num `MAMUserNotification`. Quando esta notificação for recebida, quaisquer dados de Configuração de Aplicação em cache devem ser invalidados e atualizados. Não são dadas garantias sobre em que fio esta notificação será enviada.

* **MANAGEMENT_REMOVED**: esta notificação é enviada numa `MAMUserNotification` e informa a aplicação que está prestes a deixar de ser gerida. Quando já não for gerida, a aplicação deixará de conseguir ler ficheiros encriptados, ler dados encriptados com MAMDataProtectionManager, interagir com a área de transferência encriptada ou participar no ecossistema de aplicações geridas. Veja mais detalhes abaixo. Esta notificação nunca será enviada no fio UI.

* **MAM_ENROLLMENT_RESULT**: Esta notificação é enviada numa `MAMEnrollmentNotification` informar a app de que uma tentativa de inscrição APP-WE foi concluída e fornecer o estado dessa tentativa. Não são dadas garantias sobre em que fio esta notificação será enviada.

* **COMPLIANCE_STATUS**: Esta notificação é enviada numa `MAMComplianceNotification` para informar a aplicação do resultado de uma tentativa de reparação de conformidade. Não são dadas garantias sobre em que fio esta notificação será enviada.

> [!NOTE]
> Uma aplicação nunca se deverá registar para as notificações `WIPE_USER_DATA` e `WIPE_USER_AUXILIARY_DATA`.

### <a name="management_removed"></a>MANAGEMENT_REMOVED

A notificação `MANAGEMENT_REMOVED` indica que um utilizador anteriormente gerido por políticas deixará de ser gerido pela política Intune MAM. Isto não requer limpar os dados do utilizador ou assinar o utilizador (se fosse necessária uma limpeza, seria enviada uma notificação `WIPE_USER_DATA`). Muitas aplicações podem não precisar de lidar com esta notificação, no entanto as aplicações que utilizam `MAMDataProtectionManager` devem [tomar nota especial desta notificação.](#data-protection)

Quando a MAM ligar para o recetor `MANAGEMENT_REMOVED` da aplicação, o seguinte será verdade:
* A MAM já desencripta ficheiros previamente encriptados (mas não protegidos) que pertencem à aplicação. Os ficheiros em locais públicos no sdcard que não pertencem diretamente à aplicação (por exemplo, os Documentos ou as pastas de descarregamento) não são desencriptados.
* Novos ficheiros ou amortecedores de dados protegidos criados pelo método recetor (ou qualquer outro código que esteja a funcionar após o arranque do recetor) não serão encriptados.
* A aplicação ainda tem acesso a chaves de encriptação, pelo que operações como tampão de dados de desencriptação terão sucesso.

Assim que o recetor da sua aplicação regressar, deixará de ter acesso às chaves de encriptação.

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

* **ClientID** é o AAD ClientID (também conhecido como ID de aplicação) a ser usado. Deverá utilizar o ClientID da sua própria aplicação se estiver registado no Azure AD ou alavancar a [Inscrição Padrão](#default-enrollment-optional) se não integrar a ADAL.

* **NonBrokerRedirectURI** é o URI de redirecionamento do AAD para utilizar em casos sem mediador. Se não for especificado nenhum, será utilizado um valor predefinido de `urn:ietf:wg:oauth:2.0:oob`. Esta predefinição é adequada para a maioria das aplicações.

  * O NonBrokerRedirectURI só é utilizado quando o SkipBroker é "verdadeiro".

* **SkipBroker** é usado para anular o comportamento de participação padrão ADAL SSO. O SkipBroker só deve ser especificado para aplicações que especifiquem um ClientID **e** não suportem a autenticação/SSO mediada em todo o dispositivo. Neste caso, deve ser definido como "verdadeiro". A maioria das aplicações não deve definir o parâmetro SkipBroker.

  * Um ClientID **deve** ser especificado no manifesto para especificar um valor SkipBroker.

  * Quando um ClienteID é especificado, o valor predefinido é "falso".

  * Quando o SkipBroker for "verdadeiro", será utilizado o NonBrokerRedirectURI. As aplicações que não integrarem o ADAL (e, portanto, não têm ClientID) também não serão "verdadeiras".

### <a name="common-adal-configurations"></a>Configurações comuns da ADAL

Seguem-se algumas formas comuns através das quais uma aplicação pode ser configurada com a ADAL. Localize a configuração da sua aplicação e confirme que define os parâmetros de metadados da ADAL (explicado acima) para os valores necessários. Em todos os casos, a Autoridade pode ser especificada se desejar para ambientes não predefinidos. Se não for especificado, será utilizada a autoridade adidendede de produção pública.

#### <a name="1-app-does-not-integrate-adal"></a>1. App não integra a ADAL
Os metadados ADAL **não devem** estar presentes no manifesto.

#### <a name="2-app-integrates-adal"></a>2. App integra ADAL

|Parâmetro necessário da ADAL| Valor |
|--|--|
| ClientID | O ClientID da aplicação (gerado pelo Azure AD quando a aplicação é registada) |

A autoridade pode ser especificada se necessário.

Deve registar a sua aplicação com o Azure AD e dar à sua aplicação acesso ao serviço de política de proteção de aplicações:
* Veja [esta página](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) para obter informações sobre como registar uma aplicação com o Azure AD.
* Certifique-se de que são seguidos os passos para dar permissões à sua aplicação Android para o serviço de política de proteção de aplicações (APP). Utilize as instruções no [início com o guia Intune SDK](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration) em "Dar à sua aplicação acesso ao serviço de proteção de aplicações Intune (opcional)". 

Veja também os requisitos para [Acesso Condicional](#conditional-access) abaixo.


#### <a name="3-app-integrates-adal-but-does-not-support-brokered-authenticationdevice-wide-sso"></a>3. App integra ADAL mas não suporta autenticação/SSO mediada em todo o dispositivo

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
5. Uma vez que a sua aplicação tenha enviado integração Intune APP SDK, o contacto msintuneappsdk@microsoft.com a ser adicionado à lista de aplicações aprovadas para [acesso condicional baseado em aplicações](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use#app-based-conditional-access)
6. Assim que a aplicação tiver sido adicionada à lista aprovada, valide ao [Configurar o AC com base nas aplicações](https://docs.microsoft.com/intune/app-based-conditional-access-intune-create) e certifique-se de que o início de sessão na sua aplicação é concluído com êxito.

## <a name="app-protection-policy-without-device-enrollment"></a>Política de proteção de aplicações sem inscrição de dispositivos

### <a name="overview"></a>Descrição geral
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
    > Certifique-se de que a sua aplicação utiliza os parâmetros `resourceId` e `aadId` passados para `acquireToken()` para que o símbolo correto seja adquirido.

    ```java
    class MAMAuthCallback implements MAMServiceAuthenticationCallback {
        public String acquireToken(String upn, String aadId, String resourceId) {
            return mAuthContext.acquireTokenSilentSync(resourceId, ClientID, aadId).getAccessToken();
        }
    }
    ```

3. Caso a aplicação não consiga fornecer um token quando o SDK chama o `acquireToken()`, por exemplo, se a autenticação silenciosa falhar e, sendo um período de tempo inconveniente para mostrar uma IU, a aplicação poderá fornecer um token num momento posterior ao chamar o método `updateToken()`. Os mesmos UPN, ID de UPN, ID do AAD e ID de recurso solicitados pela chamada anterior para `acquireToken()` têm de ser transmitidos para `updateToken()`, juntamente com o token que foi, finalmente, adquirido. A aplicação deve invocar este método com o máximo de brevidade possível após ser devolvido o valor nulo da chamada de retorno fornecida.

    > [!NOTE]
    > O SDK ligará para o `acquireToken()` periodicamente para obter o token; por isso, não é estritamente necessário ligar para o `updateToken()`. No entanto, é fortemente recomendado, uma vez que pode ajudar as inscrições e os check-ins da política de proteção de aplicações a completar em tempo útil.


### <a name="account-registration"></a>Registo da Conta
Esta secção descreve os métodos da API do registo da conta no `MAMEnrollmentManager` e como utilizá-los.

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. Para registar uma conta de gestão, a aplicação deve chamar `registerAccountForMAM()`. Uma conta de utilizador é identificada pelos seus UPN e ID de utilizador do AAD. O ID do inquilino também é necessário para associar os dados de inscrição com o inquilino do AAD do utilizador. A autoridade do utilizador também pode ser fornecida para permitir a inscrição contra nuvens soberanas específicas; para mais informações consulte [Registo soberano de Nuvem.](#sovereign-cloud-registration)  O SDK pode tentar inscrever a aplicação para o utilizador especificado no serviço MAM. Se a inscrição falhar, esta tentará realizar periodicamente a inscrição até que a conta fique não registada. Por norma, o período de repetição é de 12 a 24 horas. O SDK fornece o estado das tentativas de inscrição de modo assíncrono através de notificações.

2. Uma vez que é necessária a autenticação AAD, a melhor altura para registar a conta de utilizador é depois de o utilizador ter assinado na app e ser autenticado com sucesso através da ADAL. O ID AAD do utilizador e o ID do inquilino são devolvidos da chamada de autenticação ADAL como parte do objeto [`AuthenticationResult`.](https://github.com/AzureAD/azure-activedirectory-library-for-android)
    * O ID do inquilino provém do método `AuthenticationResult.getTenantID()`.
    * Pode encontrar informações sobre o utilizador num subobjeto do tipo `UserInfo` proveniente de `AuthenticationResult.getUserInfo()` e o utilizador do AAD ID é obtido a partir desse objeto ao chamar `UserInfo.getUserId()`.

3. Para anular o registo de uma conta da gestão do Intune, a aplicação deve chamar `unregisterAccountForMAM()`. Se a conta tiver sido inscrita com êxito e for gerida, o SDK anulará a inscrição da conta e eliminará os seus dados. As tentativas periódicas de inscrição da conta serão interrompidas. O SDK fornece o estado do pedido de não inscrição asincronizadamente através da notificação.

### <a name="sovereign-cloud-registration"></a>Registo em Clouds Soberanas
As aplicações que são [conscientes](https://www.microsoft.com/trustcenter/cloudservices/nationalcloud) da nuvem soberana **devem** fornecer o `authority` a `registerAccountForMAM()`.  Isto pode ser obtido ao fornecer `instance_aware=true` em acquireToken extraQueryParameters na [versão 1.14.0+](https://github.com/AzureAD/azure-activedirectory-library-for-android/releases/tag/v1.14.0) do ADAL e ao invocar `getAuthority()` em AuthenticationCallback AuthenticationResult.

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
> Não detete o `com.microsoft.intune.mam.aad.Authority` item de metadados em AndroidManifest.xml.

> [!NOTE]
> Certifique-se de que a autoridade está corretamente definida no seu método `MAMServiceAuthenticationCallback::acquireToken()`.

#### <a name="currently-supported-sovereign-clouds"></a>Cloud Soberanas Suportadas Atualmente

1. Nuvem do Governo dos EUA Azure

### <a name="important-implementation-notes"></a>Notas de implementação importantes

#### <a name="authentication"></a>Autenticação
* Quando a aplicação chama `registerAccountForMAM()`, esta pode receber uma chamada de retorno na sua interface `MAMServiceAuthenticationCallback` pouco tempo depois, num thread diferente. Idealmente, a app adquiriu o seu próprio símbolo à ADAL antes de registar a conta para acelerar a aquisição do token solicitado. Se a aplicação devolver um token válido da chamada, a inscrição prosseguirá e a aplicação obterá o resultado final através de uma notificação.

* Se a aplicação não devolver um token do AAD válido, o resultado final da tentativa de inscrição será `AUTHENTICATION_NEEDED`. Se a aplicação receber este Resultado através de notificação, é fortemente recomendado agilizar o processo de inscrição adquirindo o símbolo para o utilizador e recurso anteriormente solicitado a partir de `acquireToken()` e chamando o método `updateToken()` para iniciar novamente o processo de inscrição.

* O `MAMServiceAuthenticationCallback` registado da aplicação também será chamado para adquirir um símbolo para a política periódica de proteção de aplicações atualização de check-ins. Se a aplicação não puder fornecer um sinal quando solicitada, não receberá uma notificação, mas deverá tentar adquirir um token e chamar `updateToken()` na próxima hora conveniente para acelerar o processo de check-in. Se não for fornecido um token, a chamada de retorno será realizada na mesma na próxima tentativa de registo.

* O suporte para cloud soberanas requer que forneça a autoridade.

#### <a name="registration"></a>Registo
* Para sua comodidade, os métodos de registo são idempotentes, por exemplo, `registerAccountForMAM()` registará apenas uma conta e uma tentativa de inscrição da aplicação se a conta ainda não estiver registada e `unregisterAccountForMAM()` apenas anulará o registo de uma conta se esta estiver atualmente registada. As chamadas subsequentes efetuadas são não operativas, por isso, não há qualquer problema em chamar esses métodos mais do que uma vez. Além disso, a correspondência entre as chamadas para esses métodos e as notificações dos resultados não são garantidas, isto é, se `registerAccountForMAM()` for chamado para uma identidade que já esteja registada, a notificação poderá não ser enviada novamente para essa identidade. É possível que sejam enviadas notificações que não correspondem a qualquer chamada para esses métodos, dado que o SDK pode tentar periodicamente realizar inscrições em segundo plano. Adicionalmente, podem ser acionadas anulações de inscrições com a eliminação dos pedidos recebidos do serviço Intune.

* Os métodos de registo podem ser chamados para um qualquer número de identidades diferentes, mas, atualmente, apenas uma conta de utilizador pode ser inscrita com êxito. Se estiverem registadas várias contas de utilizador licenciadas para o Intune e estas forem visadas pela política de proteção de aplicações na mesma altura ou próxima desta, não haverá qualquer garantia sobre qual será a escolhida.

* Por fim, pode consultar o `MAMEnrollmentManager` para ver se uma determinada conta está registada e para obter o seu estado atual com recurso ao método `getRegisteredAccountStatus()`. Se a conta fornecida não estiver registada, este método devolverá **nulo**. Se a conta estiver registada, este método devolverá o estado da conta como um dos membros da enumeração `MAMEnrollmentManager.Result`.

### <a name="result-and-status-codes"></a>Códigos de estados e de resultados
Quando uma conta é registada pela primeira vez, esta começa no estado `PENDING`, o qual indica que a tentativa inicial de inscrição do serviço MAM está incompleta. Depois de concluída a tentativa de inscrição, será enviada uma notificação com um dos Códigos de resultados da tabela abaixo. Além disso, o método `getRegisteredAccountStatus()` devolverá o estado da conta para que a aplicação possa determinar sempre se o acesso ao conteúdo empresarial está bloqueado para esse utilizador. Se a tentativa de inscrição falhar, o estado da conta poderá mudar ao longo do tempo, uma vez que o SDL volta a tentar a inscrição em segundo plano.

|Código do resultado | Explicação |
| -- | -- |
| `AUTHORIZATION_NEEDED` | Este resultado indica que um símbolo não foi fornecido pela instância `MAMServiceAuthenticationCallback` registada da aplicação, ou que o token fornecido era inválido.  A aplicação deve adquirir um token válido e chamar `updateToken()`, se possível. |
| `NOT_LICENSED` | O utilizador não está licenciado para o Intune ou a tentativa de contacto do serviço da MAM do Intune falhou.  A aplicação deve continuar num estado não gerido (normal) e o utilizador não deve estar bloqueado.  As tentativas de inscrição serão repetidas periodicamente caso o utilizador se torne licenciado no futuro. |
| `ENROLLMENT_SUCCEEDED` | A tentativa de inscrição foi concluída com êxito ou o utilizador já está inscrito.  No caso de uma inscrição com êxito, será enviada uma notificação de atualização da política antes desta notificação.  O acesso a dados empresariais deve ser permitido. |
| `ENROLLMENT_FAILED` | A tentativa de inscrição falhou.  Pode encontrar mais detalhes nos registos do dispositivo.  A aplicação não deve permitir o acesso a dados corporativos neste estado, uma vez que foi previamente determinado que o utilizador está licenciado para a Intune.|
| `WRONG_USER` | Apenas um utilizador por dispositivo pode inscrever uma aplicação com o serviço MAM. Este resultado indica que o utilizador para quem este resultado foi entregue (o segundo utilizador) é direcionado para a política de MAM, mas um utilizador diferente já está inscrito. Uma vez que a política de MAM não pode ser aplicada para o segundo utilizador, a sua aplicação não deve permitir o acesso aos dados deste utilizador (possivelmente removendo o utilizador da sua aplicação) a menos que/até que a inscrição para este utilizador tenha sucesso mais tarde. Simultaneamente com a entrega deste resultado `WRONG_USER`, o MAM solicitará a opção de remover a conta existente. Se o utilizador humano responder afirmativamente, será possível inscrever o segundo utilizador pouco tempo depois. Enquanto o segundo utilizador permanecer registado, o MAM voltará a tentar a inscrição periodicamente. |
| `UNENROLLMENT_SUCCEEDED` | Anulação da inscrição concluída com êxito.|
| `UNENROLLMENT_FAILED` | O pedido de anulação da inscrição falhou.  Pode encontrar mais detalhes nos registos do dispositivo. Em geral, isto não ocorrerá enquanto a aplicação passar uma UPN válida (nem nula nem vazia). Não há remediação direta e fiável que a app possa levar. Se este valor for recebido ao não registar uma UPN válida, por favor, reporte como um bug para a equipa Intune MAM.|
| `PENDING` | A tentativa inicial de inscrição do utilizador está em curso.  A aplicação pode bloquear o acesso a dados empresariais até que o resultado da inscrição seja conhecido, mas não é necessário fazê-lo. |
| `COMPANY_PORTAL_REQUIRED` | O utilizador está licenciado para o Intune, mas a aplicação não pode ser inscrita até que a aplicação Portal da Empresa seja instalada no dispositivo. O SDK da Aplicação do Intune tentará bloquear o acesso à aplicação ao utilizador especificado e direcioná-lo para a instalação da aplicação Portal da Empresa (veja abaixo para obter detalhes). |


### <a name="company-portal-requirement-prompt-override-optional"></a>Ignorar pedido de requisito do Portal da Empresa (opcional)
Se receber o Resultado `COMPANY_PORTAL_REQUIRED`, o SDK bloqueará a utilização das atividades que utilizam a identidade para a qual a inscrição foi solicitada. Em vez disso, o SDK fará com que essas atividades apresentem um pedido para transferir o Portal da Empresa. Se pretender evitar este comportamento na sua aplicação, as atividades poderão implementar `MAMActivity.onMAMCompanyPortalRequired`.

Este método é chamado antes de o SDK apresentar as suas IUs de bloqueio predefinidas. Se a aplicação alterar a identidade da atividade ou anular o registo do utilizador que tentou inscrever-se, o SDK não bloqueará a atividade. Nesta situação, cabe à aplicação evitar a fuga de dados empresariais. Apenas as aplicações de várias identidades (abordadas mais tarde) poderão alterar a identidade de atividade.

Se não herdar explicitamente de `MAMActivity` (uma vez que as ferramentas de compilação farão essa alteração), mas ainda tiver de processar esta notificação, pode implementar `MAMActivityBlockingListener` como alternativa.

### <a name="notifications"></a>Notificações
Se a aplicação se registar para notificações de tipo **MAM_ENROLLMENT_RESULT**, será enviada uma `MAMEnrollmentNotification` para informar a app de que o pedido de inscrição já foi concluído. `MAMEnrollmentNotification` será recebida através da interface `MAMNotificationReceiver`, conforme descrito na secção [Registar para obter notificações do SDK](#register-for-notifications-from-the-sdk).

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}
```

O método `getEnrollmentResult()` devolve o resultado do pedido de inscrição.  Uma vez que `MAMEnrollmentNotification` expande `MAMUserNotification`, a identidade do utilizador para o qual foi tentada a inscrição também está disponível. A aplicação deve implementar a interface `MAMNotificationReceiver` para receber estas notificações, detalhadas na secção [Registar para obter notificações do SDK](#register-for-notifications-from-the-sdk).

O estado da conta de utilizador registado pode alterar-se quando uma notificação de inscrição é recebida, mas não se altera rá em todos os casos (por exemplo, se `AUTHORIZATION_NEEDED` notificação for recebida após um resultado mais informativo, como `WRONG_USER`, o resultado mais informativo será mantido como o estado da conta).  Uma vez que a conta esteja inscrita com sucesso, o estado permanecerá como `ENROLLMENT_SUCCEEDED` até que a conta não esteja matriculada ou limpa.

## <a name="app-ca-with-policy-assurance"></a>APP CA com Garantia de Política

### <a name="overview"></a>Descrição geral
Com app CA (Acesso Condicional) com Garantia de Política, o acesso aos recursos é condicionado na aplicação de Políticas de Proteção de Aplicações Intune.  A AAD aplica-o exigindo que a app seja matriculada e gerida pela APP antes de conceder um símbolo para aceder a uma APP CA com recurso protegido por Garantia de Política.  A aplicação é obrigada a utilizar o corretor ADAL para aquisição simbólica, e a configuração é a mesma descrita acima no [Acesso Condicional](#conditional-access).

### <a name="adal-changes"></a>Alterações ADAL
A biblioteca ADAL tem um novo código de erro informando a app de que a falha na aquisição de um token foi causada pelo incumprimento da gestão da APP.  Se a aplicação receber este código de erro, tem de chamar o SDK para tentar remediar a conformidade, matriculando a app e aplicando a política. Uma exceção será recebida pelo método `onError()` da `AuthenticationCallback`ADAL , e terá o código de erro `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED`.  Neste caso, a exceção pode ser lançada a um `IntuneAppProtectionPolicyRequiredException`, a partir do qual podem ser extraídos parâmetros adicionais para utilização na reparação da conformidade (ver amostra de código abaixo). Uma vez que a reparação seja bem sucedida, a aplicação pode voltar a tentar a aquisição simbólica através da ADAL.

> [!NOTE]
> Este novo código de erro e outro suporte para APP CA com Garantia de Política requerem a versão 1.15.0 (ou maior) da biblioteca ADAL.

### <a name="mamcompliancemanager"></a>MAMComplianceManager
A interface `MAMComplianceManager` é utilizada quando o erro exigido pela apólice é recebido da ADAL.  Contém o método `remediateCompliance()` que deve ser chamado para tentar colocar a app num estado conforme. Pode obter uma referência do `MAMComplianceManager` da seguinte forma:

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

O método `remediateCompliance()` é chamado a tentar colocar a app sob gestão para satisfazer as condições para a AAD conceder o token solicitado.  Os primeiros quatro parâmetros podem ser extraídos da exceção recebida pelo método ADAL `AuthenticationCallback.onError()` (ver amostra de código abaixo).  O parâmetro final é um booleano que controla se um UX é mostrado durante a tentativa de conformidade.  Esta é uma simples interface de estilo de progresso de bloqueio fornecida como padrão para apps que não têm necessidade de mostrar UX personalizado durante esta operação.  Só bloqueará enquanto a reparação de conformidade estiver em curso e não apresentará o resultado final.  A aplicação deve registar um recetor de notificação para lidar com o sucesso ou falha da tentativa de reparação de conformidade (ver abaixo).

O método `remediateCompliance()` pode fazer uma inscrição em MAM como parte do estabelecimento do cumprimento.  A aplicação pode receber uma notificação de inscrição se tiver registado um recetor de notificação para notificações de inscrição.  O `MAMServiceAuthenticationCallback` registado da aplicação terá o seu método `acquireToken()` chamado para obter um símbolo para a inscrição do MAM. `acquireToken()` serão chamados antes de a app ter adquirido o seu próprio token, pelo que quaisquer tarefas de contabilidade ou criação de conta que a app faz após uma aquisição simbólica bem sucedida podem ainda não ter sido feitas.  A chamada deve ser capaz de adquirir um símbolo neste caso.  Se não puder devolver um símbolo de `acquireToken()`, a tentativa de reparação de conformidade falhará.  Se ligar para `updateToken()` mais tarde com um símbolo válido para o recurso solicitado, a reparação de conformidade será novamente tentada imediatamente com o token dado.

> [!NOTE]
> A aquisição de token silenciosa ainda será possível em `acquireToken()` porque o utilizador já terá sido guiado para instalar o corretor e registar o dispositivo antes de `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED` erro ser recebido.  Isto resulta em que o corretor tenha um token de atualização válido na sua cache, permitindo que a aqisição silenciosa do token solicitado tenha sucesso.

Aqui está uma amostra de receção do erro exigido pela política no método `AuthenticationCallback.onError()`, e chamando a `MAMComplianceManager` para lidar com o erro.

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

### <a name="status-notifications"></a>Notificações de Estado
Se a aplicação se registar para notificações de tipo **COMPLIANCE_STATUS,** será enviada uma `MAMComplianceNotification` para informar a aplicação do estado final da tentativa de reparação de conformidade. `MAMComplianceNotification` será recebida através da interface `MAMNotificationReceiver`, conforme descrito na secção [Registar para obter notificações do SDK](#register-for-notifications-from-the-sdk).

```java
public interface MAMComplianceNotification extends MAMUserNotification {
    MAMCAComplianceStatus getComplianceStatus();
    String getComplianceErrorTitle();
    String getComplianceErrorMessage();
}
```

O método `getComplianceStatus()` devolve o resultado da tentativa de reparação de conformidade como um valor do `MAMCAComplianceStatus` enum.

|Código de estado | Explicação |
| -- | -- |
| DESCONHECIDO | O estado é desconhecido. Isto pode indicar uma razão de falha inesperada. Informações adicionais podem ser encontradas nos registos do Portal da Empresa. |
| CONFORME | A reparação de conformidade foi bem sucedida e a aplicação está agora em conformidade com a política. A aquisição de fichas DaDaL deve ser novamente julgada. |
| NOT_COMPLIANT | A tentativa de remediar o cumprimento falhou.  A aplicação não está em conformidade e a aquisição de token ADAL não deve ser novamente tentada até que a condição de erro seja corrigida.  As informações adicionais de erro são enviadas com o MAMComplianceNotification. |
| SERVICE_FAILURE | Houve uma falha enquanto tentava recuperar os dados de conformidade do Serviço Intune. Informações adicionais podem ser encontradas nos registos do Portal da Empresa. |
| NETWORK_FAILURE | Houve um erro de ligação ao Serviço Intune. A aplicação deve tentar novamente a sua aquisição simbólica quando a ligação à rede for restaurada. |
| CLIENT_ERROR | A tentativa de remediar o cumprimento falhou por alguma razão relacionada com o cliente.  Por exemplo, nenhum utilizador simbólico ou errado. As informações adicionais de erro são enviadas com o MAMComplianceNotification. |
| PENDING | A tentativa de remediar o cumprimento falhou porque a resposta ao estado ainda não tinha sido recebida do serviço quando o prazo foi ultrapassado. A aplicação deverá tentar a sua aquisição simbólica novamente mais tarde. |
| COMPANY_PORTAL_REQUIRED | O Portal da Empresa deve ser instalado no dispositivo para que a reparação de conformidade seja bem sucedida.  Se o Portal da Empresa já estiver instalado no dispositivo, a aplicação precisa de ser reiniciada.  Neste caso, será mostrado um diálogo a pedir ao utilizador que reinicie a aplicação. |

Se o estado de conformidade for `MAMCAComplianceStatus.COMPLIANT`, a aplicação deverá reiniciar a sua aquisição original (para o seu próprio recurso). Se a tentativa de reparação de conformidade falhar, os métodos `getComplianceErrorTitle()` e `getComplianceErrorMessage()` devolverão as cordas localizadas que a aplicação pode apresentar ao utilizador final, se assim o desejar.  A maioria dos casos de erro não são remediados pela aplicação, pelo que, para o caso geral, pode ser melhor falhar na criação de conta ou no login e permitir que o utilizador tente novamente mais tarde.  Se uma falha for persistente, os registos mAM podem ajudar a determinar a causa.  O utilizador final pode submeter os registos utilizando as instruções [aqui](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android "Enviar registos ao suporte da empresa por e-mail")encontradas .

Uma vez que `MAMComplianceNotification` estende `MAMUserNotification`, a identidade do utilizador para quem foi tentada a reparação também está disponível.

Aqui está um exemplo de registo de um recetor usando uma classe anónima para implementar a interface MAMNotificationReceiver:

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
> O recetor de notificação deve ser registado antes de ligar para `remediateCompliance()` evitar uma condição de corrida que possa resultar na falta da notificação.

### <a name="implementation-notes"></a>Notas de implementação
> [!NOTE]
> **Mudança importante!**  <br>
> O método `MAMServiceAuthenticationCallback.acquireToken()` da aplicação deve passar *falso* para que a nova bandeira de `forceRefresh` `acquireTokenSilentSync()`.
> Anteriormente, recomendamos *que* se tratasse de um problema com fichas refrescantes do corretor, mas foi encontrado um problema com a ADAL que poderia impedir a aquisição de fichas em alguns cenários se esta bandeira for *verdadeira.*
```java
AuthenticationResult result = acquireTokenSilentSync(resourceId, clientId, userId, /* forceRefresh */ false);
```

> [!NOTE]
> Se quiser mostrar um UX de bloqueio personalizado durante a tentativa de reparação, deve passar *falso* para o parâmetro showUX para `remediateCompliance()`. Deve certificar-se de que mostra o seu UX e registe primeiro o seu ouvinte de notificação antes de ligar para `remediateCompliance()`.  Isto evitará uma condição de corrida em que a notificação possa ser perdida se `remediateCompliance()` falhar muito rapidamente.  Por exemplo, o método `onCreate()` ou `onMAMCreate()` de uma subclasse Atividade é o local ideal para registar o ouvinte de notificação e, em seguida, ligar `remediateCompliance()`.  Os parâmetros para `remediateCompliance()` podem ser passados para o seu UX como extras de intenção.  Quando a notificação do estado de conformidade for recebida, pode apresentar o resultado ou simplesmente terminar a atividade.

> [!NOTE]
> `remediateCompliance()` registará a conta e tentará a inscrição.  Uma vez adquirido o símbolo principal, não é necessário chamar `registerAccountForMAM()`, mas não há mal nenhum em fazê-lo. Por outro lado, se a app não adquirir o seu símbolo e pretender remover a conta de utilizador, deve chamar `unregisterAccountForMAM()` para remover a conta e impedir a retenção de matrículas de fundo.

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

1. Você deve usar um loop `while(data.readNextHeader())` para passar pelas entidades de backup. No código anterior, `data` é o nome variável local para o **MAMBackupDataInput** que é passado para a sua app após o restauro.

2. Deve ligar para `data.skipEntityData()` se `data.getKey()` não corresponder à chave que escreveu no `onBackup`. Sem realizar este passo, os seus restauros podem não ter êxito. No código anterior, `data` é o nome variável local para o **MAMBackupDataInput** que é passado para a sua app após o restauro.

3. Evite voltar enquanto consome entidades de backup na construção `while(data.readNextHeader())`, uma vez que as entidades que automaticamente escrevemos perder-se-ão. No código anterior, `data` é o nome variável local para o **MAMBackupDataInput** que é passado para a sua app após o restauro.

## <a name="multi-identity-optional"></a>Multi-Identidade (opcional)

### <a name="overview"></a>Descrição geral
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
  2. `Context` (geralmente `Activity`)
  3. Nível de processo

Uma identidade definida no nível de thread prevalece sobre uma identidade definida no nível `Context`, que prevalece sobre uma identidade definida no nível de processo. Uma identidade definida num `Context` só é utilizada em cenários associados apropriados. As operações de Ficheiro IO, por exemplo, não têm uma `Context`associada . Mais comummente, as aplicações definirão a identidade `Context` numa `Activity`. Uma aplicação não *deve* apresentar dados para uma identidade gerida a menos que a identidade `Activity` seja definida para essa mesma identidade. Em geral, a identidade ao nível do processo só é útil se a aplicação funcionar apenas com um utilizador de cada vez em todos os threads. É possível que muitas das aplicações não precisem de a utilizar.

Se a sua aplicação utilizar o contexto `Application` para adquirir serviços de sistema, certifique-se de que a identidade de fio ou processo foi definida ou que definiu a identidade de UI no contexto `Application` da sua aplicação.

Para lidar com casos especiais ao atualizar a identidade da UI com `setUIPolicyIdentity` ou `switchMAMIdentity`, ambos os métodos podem ser aprovados num conjunto de valores `IdentitySwitchOption`.

* `IGNORE_INTENT`: Utilize se solicitar um interruptor de identidade que ignore a intenção associada à atividade atual.
  Por exemplo:

  1. A sua aplicação recebe uma intenção de uma identidade gerida que contém um documento gerido, e a sua aplicação exibe o documento.
  2. O utilizador muda para a sua identidade pessoal, pelo que a sua aplicação solicita um interruptor de identidade UI. Na identidade pessoal, a sua aplicação já não está a apresentar o documento, pelo que utiliza `IGNORE_INTENT` ao solicitar o interruptor de identidade.

  Se não for definido, o SDK assumirá que a intenção mais recente ainda está a ser usada na aplicação. Isto fará com que a nova identidade trate a intenção como dados recebidos e utilize a sua identidade.

>[!NOTE]
> Como o `CLIPBOARD_SERVICE` é utilizado para operações de UI, o SDK utiliza a identidade ui da atividade de primeiro plano para operações `ClipboardManager`.
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
| `NOT_ALLOWED`  | A alteração de identidade não é permitida. Isto ocorre se for feita uma tentativa de definir a identidade ui (`Context`) quando uma identidade diferente é definida no fio atual. |
| `CANCELLED`    | O utilizador cancelou a alteração de identidade, geralmente ao premir o botão Anterior num pedido de PIN ou autenticação. |
| `FAILED`       | A alteração de identidade falhou por um motivo não especificado.|

A aplicação deve garantir que um interruptor de identidade é bem sucedido antes de exibir ou utilizar dados corporativos. Atualmente, as alterações de identidade de processos e threads serão sempre concluídas com êxito numa aplicação com várias identidades. No entanto, reservamos o direito de adicionar condições de falha. A alteração de identidade da IU poderá falhar no caso de argumentos inválidos, se a mesma entrar em conflito com a identidade do thread ou se o utilizador cancelar os requisitos de início condicional (por exemplo, o utilizador prime o botão Anterior no ecrã de PIN). O comportamento padrão para um interruptor de identidade ui falhado em uma atividade é terminar a atividade (ver `onSwitchMAMIdentityComplete` abaixo).

No caso de estabelecer uma identidade `Context` via `setUIPolicyIdentity`, o resultado é relatado de forma assíncrona. Se o `Context` for um `Activity`, o SDK não sabe se a mudança de identidade foi bem sucedida até após o lançamento condicional ser realizado -- o que pode exigir que o utilizador introduza um PIN ou credenciais corporativas. A aplicação pode implementar um `MAMSetUIIdentityCallback` para receber este resultado, ou pode passar nulo para o objeto de chamada. Note que se for feita uma chamada para `setUIPolicyIdentity` enquanto o resultado de uma chamada anterior para `setUIPolicyIdentity` *no mesmo contexto* ainda não foi entregue, o novo callback substituirá o antigo e o backback original nunca receberá um resultado.

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

Se não substituir `onSwitchMAMIdentityComplete` (ou chamar o método `super`), um interruptor de identidade falhado numa atividade resultará na sua terminação da atividade. Se anular o método, deve ter cuidado para que os dados corporativos não sejam apresentados após um interruptor de identidade falhado.

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

* `reportIdentitySwitchResult(FAILURE)` quando a razão é `RESUME_CANCELLED`.

* `reportIdentitySwitchResult(SUCCESS)` em todos os outros casos.

  Não é esperado que a maioria das aplicações precise de bloquear ou atrasar uma mudança de identidade numa forma diferente, mas se uma aplicação precisar de o fazer, os seguintes pontos têm de ser tidos em conta:

  * Se a alteração de identidade é bloqueada, o resultado é o mesmo como se as definições de partilha de `Receive` tivessem proibido a entrada de dados.

  * Se um Serviço estiver em execução na linha principal, `reportIdentitySwitchResult` **deve** ser chamado sincronizadamente ou o fio UI será pendurado.

  * Para **`Activity`** criação, `onMAMIdentitySwitchRequired` serão chamados antes de `onMAMCreate`. Se a aplicação tiver de mostrar a IU para determinar se a mudança de identidade deve ser permitida, a IU terá de ser apresentada com uma identidade *diferente*.

  * Numa **`Activity`**, quando é solicitada uma mudança para a identidade vazia com a razão `RESUME_CANCELLED`, a aplicação deve modificar a atividade retomada para exibir dados consistentes com esse interruptor de identidade.  Se tal não for possível, a aplicação deverá recusar a mudança e será novamente pedido ao utilizador que fique em conformidade com a política da identidade retomada (por exemplo, ao ver o ecrã de introdução de PIN da aplicação).

    > [!NOTE]
    > Uma aplicação com várias identidades irá sempre receber dados de aplicações geridas e não geridas. É da responsabilidade da aplicação tratar dados de identidades geridas de forma gerida.

  Se uma identidade solicitada for gerida (utilize `MAMPolicyManager.getIsIdentityManaged` para verificar), mas a aplicação não puder utilizar essa conta (por exemplo, porque primeiro têm de ser configuradas contas na aplicação, como contas de e-mail), a mudança de identidade deverá ser recusada.

#### <a name="build-plugin--tool-considerations"></a>Considerações sobre o plug-in/ferramenta de compilação
Se não herdar explicitamente de `MAMActivity`, `MAMService`ou `MAMContentProvider` (porque permite que a ferramenta de construção faça essa alteração), mas ainda precisa de processar interruptores de identidade, pode, em vez disso, implementar `MAMActivityIdentityRequirementListener` (por um `Activity`) ou `MAMIdentityRequirementListener` (por um `Service` ou `ContentProviders`).
O comportamento predefinido para `MAMActivity.onMAMIdentitySwitchRequired` pode ser acedido ao chamar o método estático `MAMActivity.defaultOnMAMIdentitySwitchRequired(activity, identity,
reason, callback)`.

Da mesma forma, se necessitar de substituir `MAMActivity.onSwitchMAMIdentityComplete`, poderá implementar `MAMActivityIdentitySwitchListener` sem herdar explicitamente de `MAMActivity`.

### <a name="preserving-identity-in-async-operations"></a>Preservar a Identidade em Operações Assíncronas
É comum as operações na thread de IU distribuírem tarefas em segundo plano para outra thread. Uma aplicação com várias identidades quererá confirmar que estas tarefas em segundo plano operam com a identidade adequada. Muitas vezes, essa é a mesma identidade que foi utilizada pela atividade que as distribuiu. O SDK de MAM fornece o `MAMAsyncTask` e o `MAMIdentityExecutors` como conveniência para ajudar a preserva a identidade.
Estes devem ser utilizados se a operação assíncrona puder escrever dados corporativos a um ficheiro ou se comunicar com outras aplicações.

#### <a name="mamasynctask"></a>MAMAsyncTask
Para utilizar `MAMAsyncTask`, simplesmente herdar dele em vez de `AsyncTask` e substituir as substituições de `doInBackground` e `onPreExecute` por `doInBackgroundMAM` e `onPreExecuteMAM` respectivamente. O construtor `MAMAsyncTask` adquire um contexto de atividade. Por exemplo:

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
* O utilizador seleciona um documento para abrir na aplicação.
  * Durante o fluxo aberto, antes de ler dados do disco, a aplicação confirma a identidade que deve ser usada para exibir o conteúdo:

    ```java
    MAMFileProtectionInfo info = MAMFileProtectionManager.getProtectionInfo(docPath)
    if (info != null)
        MAMPolicyManager.setUIPolicyIdentity(activity, info.getIdentity(), callback, EnumSet.noneOf<IdentitySwitchOption.class>)
    ```

  * A aplicação aguarda até que um resultado seja reportado para o regresso.
  * Se o resultado comunicado for uma falha, a aplicação não apresentará o documento.
* A aplicação abre e torna o ficheiro.
  
#### <a name="single-identity-to-multi-identity-transition"></a>Identidade única para transição multi-identidade
Se uma aplicação que anteriormente lançada com integração Intune de identidade única integrar mais tarde as aplicações multi-identidade, previamente instaladas, experimentará uma transição (não visível para o utilizador, não existe UX associado). A aplicação não é *obrigada* a fazer nada explícito para lidar com esta transição. Todos os ficheiros criados antes da transição continuarão a ser considerados como geridos (para que permaneçam encriptados se a política de encriptação estiver em jogo). Se desejar, pode detetar a atualização e utilizar `MAMFileProtectionManager.protect` para etiquetar ficheiros ou diretórios específicos com a identidade vazia (que removerá a encriptação se forem encriptadas).

#### <a name="offline-scenarios"></a>Cenários Offline
A etiquetagem de identidade de ficheiros é sensível ao modo offline. Os seguintes pontos deverão ser levados em consideração:

* Se o Portal da Empresa não estiver instalado, a etiquetagem de identidade dos ficheiros não poderá ser efetuada.

* Se o Portal da Empresa estiver instalado, mas a aplicação não estiver a política da MAM do Intune instalada, os ficheiros não poderão ter uma etiquetagem de identidade de forma fiável.

* Quando a etiquetagem de identidade for disponibilizada, todos os ficheiros anteriormente criados serão tratados como pessoais/não geridos (pertencentes à identidade de cadeia vazia), a menos que a aplicação tenha sido anteriormente instalada como aplicação gerida com identidade única. Nesse caso, serão tratados como pertencentes ao utilizador inscrito.

### <a name="directory-protection"></a>Proteção de Diretório
Os diretórios podem ser protegidos com recurso ao mesmo método `protect` utilizado para proteger ficheiros. A proteção do diretório é aplicada recursivamente a todos os ficheiros e subdiretórios contidos no diretório e a novos ficheiros criados no diretório. Como a proteção de diretório é aplicada recursivamente, a chamada `protect` pode demorar algum tempo a concluir no caso de diretórios grandes. Por esse motivo, as aplicações a aplicar proteção num diretório que contém um grande número de ficheiros poderão querer executar a função `protect` de modo assíncrono no thread de segundo plano.

### <a name="data-protection"></a>Proteção de dados
Não é possível etiquetar um ficheiro como pertencente a identidades múltiplas. As aplicações que têm de armazenar dados pertencentes a utilizadores diferentes no mesmo ficheiro podem fazê-lo manualmente ao utilizar as funcionalidades fornecidas por `MAMDataProtectionManager`. Isto permite à aplicação encriptar dados e associá-los a um utilizador específico. Os dados encriptados são adequados para armazenamento no disco de um ficheiro. Pode consultar os dados associados à identidade e os dados podem ser desencriptados posteriormente.

As aplicações que utilizam o `MAMDataProtectionManager` devem implementar um recetor para a notificação `MANAGEMENT_REMOVED`. Após a conclusão desta notificação, as memórias intermédias que estavam protegidas através desta classe deixarão de ser legíveis caso a encriptação de ficheiros tenha sido ativada quando as memórias intermédias foram protegidas. Uma aplicação pode remediar esta situação ligando para `MAMDataProtectionManager.unprotect` em todos os amortecedores durante esta notificação. Também é seguro chamar a função proteger durante esta notificação se quiser manter as informações de identidade – a encriptação desativada é garantida durante a notificação.

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
Se a aplicação fornecer dados corporativos que não sejam um `ParcelFileDescriptor` através de um `ContentProvider`, a aplicação deve chamar o método `isProvideContentAllowed(String)` em `MAMContentProvider`, passando a UPN (nome principal do utilizador) para o conteúdo. Se esta função devolver "falso", os conteúdos *não podem* ser devolvidos ao chamador. Os descritores de ficheiros devolvidos através de um fornecedor de conteúdos são processados automaticamente, com base na identidade do ficheiro.

Se não herdar explicitamente `MAMContentProvider` e, em vez disso, permitir que a ferramenta de construção faça essa alteração, pode chamar uma versão estática do mesmo método: `MAMContentProvider.isProvideContentAllowed(provider,
contentIdentity)`.

### <a name="selective-wipe"></a>eliminação seletiva
Se uma aplicação de várias identidades se registar para a notificação `WIPE_USER_DATA`, é da responsabilidade da aplicação remover todos os dados do utilizador que está a ser eliminado, incluindo todos os ficheiros que foram identificados como pertencentes a esse utilizador. Se a aplicação remover os dados do utilizador de um ficheiro, mas quiser deixar outros dados no ficheiro, esta *tem* de alterar a identidade do ficheiro (através de `MAMFileProtectionManager.protect` para um utilizador pessoal ou identidade vazia). Se estiver a ser utilizada uma política de encriptação, os ficheiros restantes pertencentes ao utilizador que está a ser eliminado não serão desencriptados e ficarão inacessíveis para a aplicação após a eliminação.

Se uma aplicação se registar para `WIPE_USER_DATA`, não terá o benefício do comportamento predefinido de eliminação seletiva por parte do SDK. Para aplicações com conhecimento de várias identidades, esta perda pode ser mais significativa, dado que a eliminação seletiva predefinida da MAM elimina apenas os ficheiros cuja identidade é visada para eliminação. Se uma aplicação com conhecimento de várias identidades pretender que a eliminação seletiva predefinida da MAM seja realizada _**e**_ pretender realizar as suas próprias ações na eliminação, esta deverá registar-se para as notificações de `WIPE_USER_AUXILIARY_DATA`. Esta notificação será enviada imediatamente pelo SDK antes de executar a eliminação seletiva predefinida do SDK. Uma aplicação nunca deve ser inscrita tanto para `WIPE_USER_DATA` como para `WIPE_USER_AUXILIARY_DATA`.

A limpeza seletiva padrão fechará a app graciosamente, terminando atividades e matando o processo da aplicação. Se a sua aplicação ultrapassar a limpeza seletiva predefinida, deverá considerar o encerramento manual da sua aplicação para evitar que o utilizador aceda a dados de memória após a limpeza.

## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>Ativar a configuração de MAM direcionada para aplicações Android (opcional)
Os pares de valor-chave específicos para aplicações podem ser configurados na consola Intune para [MAM-WE](https://docs.microsoft.com/intune/app-configuration-policies-managed-app) e [Android Enterprise](https://docs.microsoft.com/intune/app-configuration-policies-use-android).
Estes pares chave-valor não são interpretados pelo Intune, mas são enviados para a aplicação. As aplicações que querem receber esse tipo de configuração podem utilizar as classes `MAMAppConfigManager` e `MAMAppConfig` para o efeito. Se houver múltiplas políticas direcionadas para a mesma aplicação, poderão existir múltiplos valores em conflito disponíveis para a mesma chave.

> [!NOTE] 
> As configurações configuradas para entrega via MAM-WE não podem ser delicacadas em `offline` (quando o Portal da Empresa não está instalado).  Apenas as Aplicações Da Empresa Android Serão entregues através de um `MAMUserNotification` sobre uma identidade vazia neste caso.

### <a name="get-the-app-config-for-a-user"></a>Obtenha a App Config para um utilizador
A consola de aplicações pode ser recuperada da seguinte forma:
```java
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
```

Se não houver um utilizador registado em MAM, mas a sua aplicação ainda gostaria de recuperar a configuração do Android Enterprise (que não será direcionada a um utilizador específico), pode passar uma corda nula ou vazia.

### <a name="conflicts"></a>Conflitos
Um valor definido na app MAM config irá sobrepor-se a um valor com a mesma chave definida no Config Android Enterprise. 

Se um administrador configura valores contraditórios para a mesma chave (por exemplo, direcionando diferentes conjuntos de config de aplicações com a mesma chave para vários grupos que contêm o mesmo utilizador), intune não tem nenhuma maneira de resolver este conflito automaticamente e fará todos os valores disponível para a sua aplicação. 

A sua aplicação pode solicitar todos os valores para uma determinada chave a partir de um objeto `MAMAppConfig`:
```java
List<Boolean> getAllBooleansForKey(String key)
List<Long> getAllIntegersForKey(final String key)
List<Double> getAllDoublesForKey(final String key)
List<String> getAllStringsForKey(final String key)
```

ou solicitar um valor a escolher:
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

A sua aplicação também pode solicitar os dados brutos como uma lista de conjuntos de pares de valor-chave.

```java
List<Map<String, String>> getFullData()
```

### <a name="full-example"></a>Exemplo Completo
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

### <a name="further-reading"></a>Continuar a ler
Para obter mais informações sobre como criar uma política de configuração de aplicações de MAM direcionada no Android, veja a secção na configuração de aplicação de MAM direcionada em [Como utilizar as políticas de configuração de aplicações do Microsoft Intune para Android](https://docs.microsoft.com/intune/app-configuration-policies-managed-app).

A config da aplicação também pode ser configurada usando o Gráfico API. Para obter informações, consulte os [docs da API de Gráfico para Config direcionado](https://docs.microsoft.com/graph/api/resources/intune-mam-targetedmanagedappconfiguration)para MAM .

## <a name="custom-themes-optional"></a>Temas Personalizados (opcional)
Um tema personalizado pode ser fornecido ao MAM SDK que será aplicado a todos os ecrãs e diálogos MAM. Se não for fornecido um tema, será utilizado um tema Padrão MAM.

### <a name="how-to-provide-a-theme"></a>Como fornecer um tema
Para fornecer um tema a uma aplicação utilizando o MAM SDK, é necessário adicionar a seguinte linha de código no método `onCreate` da aplicação:

```java
MAMThemeManager.setAppTheme(R.style.AppTheme);
```

No exemplo acima, é necessário substituir `R.style.AppTheme` pelo tema de estilo que pretende que o SDK se aplique.

## <a name="style-customization-deprecated"></a>Personalização do estilo (depreciado)

Isto é agora premeditado e temas personalizados (acima) é a forma preferida de personalizar vistas.

## <a name="default-enrollment-optional"></a>Inscrição predefinida (opcional)
Seguem-se orientações para exigir pedidos de início de sessão ao utilizador ao iniciar aplicações para uma inscrição automática no serviço APP-WE (isto é denominado **inscrição predefinida** nesta secção), exigir políticas de proteção de aplicações do Intune para permitir que apenas os utilizadores protegidos pelo Intune utilizem a sua aplicação LOB para Android integrada com SDK. Também abrangem a ativação do SSO para a sua aplicação LOB para Android integrada com SDK. Tal **não** é suportado pelas aplicações da loja que podem ser utilizadas por utilizadores sem Intune.

> [!NOTE] 
> As vantagens da **inscrição predefinida** incluem um método simplificado de obtenção de políticas do serviço APP-WE para uma aplicação no dispositivo.

> [!NOTE] 
> **A inscrição por defeito** é consciente da nuvem soberana.

Ativar a inscrição por defeito com os seguintes passos:

1. Se a sua aplicação integrar o ADAL ou precisar de ativar o SSO, configure o [ADAL](#configure-azure-active-directory-authentication-library-adal) seguindo a [configuração ADAL comum](#common-adal-configurations) #2. Caso contrário, pode saltar este passo.
   
2. Ativar a inscrição por defeito colocando o seguinte valor no manifesto:
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

* **Utilizar Resoluções de Conteúdos**: a política do Intune de “transferência ou receção” pode bloquear ou bloquear parcialmente a utilização de uma resolução de conteúdos para aceder ao fornecedor de conteúdos noutra aplicação. Isto fará com que `ContentResolver` métodos de devolução nulos ou de saque de um valor de falha (por exemplo, `openOutputStream` lançará `FileNotFoundException` se estiver em bloco). A aplicação pode determinar se uma falha ao escrever dados através de uma resolução de conteúdos foi causada pela política (ou seria causada pela política) ao efetuar a chamada:

    ```java
    MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(contentURI);
    ```

    ou se não houver atividade associada:

    ```java
    MAMPolicyManager.getPolicy().getIsSaveToLocationAllowed(contentURI);
    ```

    No segundo caso, as aplicações com várias identidades devem definir corretamente a identidade do thread (ou passar uma identidade explícita para a chamada `getPolicy`).

### <a name="exported-services"></a>Serviços exportados
O ficheiro AndroidManifest.xml incluído no SDK da Aplicação Intune contém **MAMNotificationReceiverService**, que tem de ser um serviço exportado para permitir ao Portal da Empresa enviar notificações para uma aplicação gerida. O serviço verifica o autor da chamada para assegurar que apenas o Portal da Empresa está autorizado a enviar notificações.

### <a name="reflection-limitations"></a>Limitações da reflexão
Algumas das classes base mam (por exemplo, `MAMActivity`, `MAMDocumentsProvider`) contêm métodos (baseados nas classes base originais do Android) que utilizam parâmetros ou tipos de retorno apenas apresentam acima de certos níveis de API. Por este motivo, poderá nem sempre ser possível utilizar reflexões para enumerar todos os métodos de componentes de aplicações. Esta restrição não está limitada a MAM. É a mesma restrição que seria aplicada caso a própria aplicação implementasse estes métodos a partir de classes base de Android.

### <a name="robolectric"></a>Robolectric
Não é suportado testar o comportamento do SDK de MAM no Robolectric. Existem questões conhecidas que executam o MAM SDK sob robolectrico devido a comportamentos presentes sob robolectrico que não imitam com precisão aqueles em dispositivos reais ou emuladores.

Se necessitar de testar a sua aplicação sob robolectric, a seleção recomendada é mover a lógica da sua classe de aplicação para um ajudante e produzir o seu apk de teste unitário com uma classe de aplicação que não herda da MAMApplication.

## <a name="expectations-of-the-sdk-consumer"></a>Expectativas do consumidor do SDK
O SDK do Intune mantém o contrato fornecido pela API Android, embora possam ser acionadas condições de falha mais frequentemente como resultado da imposição de políticas. Estas melhores práticas para Android reduzirão a probabilidade de falhas:

* As funções do SDK Android que podem devolver valores nulos têm uma maior probabilidade de ter um valor nulo agora.  Para minimizar os problemas, certifique-se de que as verificações de valores nulos estão nos locais corretos.

* As funcionalidades que podem ser verificadas têm de o ser através das respetivas APIs de substituição da MAM.

* As funções derivadas têm de fazer chamadas através das respetivas versões de superclasses.

* Evitar utilizar qualquer API de uma forma ambígua. Por exemplo, utilizar `Activity.startActivityForResult` sem verificar o requestCode causará um comportamento estranho.

## <a name="telemetry"></a>Telemetria

O SDK da Aplicação Intune para Android não controla a coleção de dados da sua aplicação. A aplicação do Portal da Empresa regista dados gerados pelo sistema por padrão. Estes dados são enviados para o Microsoft Intune. De acordo com a Política da Microsoft, não recolhemos quaisquer dados pessoais.

> [!NOTE]
> Se os utilizadores finais não enviarem estes dados, têm de desativar a telemetria em Definições na aplicação Portal da Empresa. Para saber mais, veja [Desativar a recolha de dados da Microsoft](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android). 

## <a name="recommended-android-best-practices"></a>Melhores práticas recomendadas para Android

* Todos os projetos de biblioteca devem partilhar o mesmo android:package sempre que possível. Assim, não falhará esporadicamente no tempo de execução, uma vez que se trata puramente de um problema de tempo de compilação. As versões mais recentes do SDK da Aplicação do Intune irão remover algumas das redundâncias.

* Utilizar as ferramentas de compilação do SDK Android.

* Remover todas as bibliotecas desnecessárias e não utilizadas (por exemplo, android.support.v4)

## <a name="testing"></a>Testes
Consulte o Guia de [Testes](app-sdk-android-testing-guide.md).
