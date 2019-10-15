---
title: Guia do desenvolvedor do SDK do Microsoft Intune app para Android
description: O SDK do aplicativo Microsoft Intune para Android permite que você incorpore o MAM (gerenciamento de aplicativo móvel) do Intune em seu aplicativo Android.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b4316c155645ad8e956cfd89c448da688ac133b3
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314554"
---
# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Guia do desenvolvedor do SDK do Microsoft Intune app para Android

> [!NOTE]
> Você talvez queira ler primeiro a [visão geral do SDK de aplicativo do Intune](app-sdk.md), que aborda os recursos atuais do SDK e descreve como se preparar para a integração em cada plataforma com suporte.

O SDK do aplicativo Microsoft Intune para Android permite que você incorpore políticas de proteção de aplicativo do Intune (também conhecidas como políticas de **aplicativo** ou MAM) em seu aplicativo Android nativo. Um aplicativo gerenciado pelo Intune é um que é integrado ao SDK de aplicativos do Intune. Os administradores do Intune podem implantar facilmente políticas de proteção de aplicativo em seu aplicativo gerenciado pelo Intune quando o Intune gerencia ativamente o aplicativo.


## <a name="whats-in-the-sdk"></a>O que há no SDK

O SDK de aplicativos do Intune consiste nos seguintes arquivos:

* **Microsoft. Intune. Mam. Sdk. aar**: os componentes do SDK, com exceção dos arquivos JAR da biblioteca de suporte.
* **Microsoft. Intune. Mam. Sdk. support. v4. jar**: as classes necessárias para habilitar o MAM em aplicativos que usam a biblioteca de suporte do Android v4.
* **Microsoft. Intune. Mam. Sdk. support. v7. jar**: as classes necessárias para habilitar o MAM em aplicativos que usam a biblioteca de suporte do Android v7.
* **Microsoft. Intune. Mam. Sdk. support. v17. jar**: as classes necessárias para habilitar o MAM em aplicativos que usam a biblioteca de suporte do v17 do Android. 
* **Microsoft. Intune. Mam. Sdk. support. Text. jar**: as classes necessárias para habilitar o MAM em aplicativos que usam classes de biblioteca de suporte do Android no pacote `android.support.text`.
* **Microsoft. Intune. Mam. Sdk. DownlevelStubs. aar**: este AAR contém stubs para classes do sistema Android que estão presentes somente em dispositivos mais recentes, mas que são referenciados por métodos no `MAMActivity`. Os dispositivos mais recentes ignorarão essas classes de stub. Esse AAR será necessário apenas se o aplicativo executar a reflexão em classes derivadas de `MAMActivity` e a maioria dos aplicativos não precisar incluí-la. O AAR contém regras do PROGuard para excluir todas as suas classes.
* **com. Microsoft. Intune. Mam. Build. jar**: um plug-in gradle que [ajuda na integração do SDK](#build-tooling).
* **Changelog. txt**: fornece um registro de alterações feitas em cada versão do SDK.
* **THIRDPARTYNOTICES. TXT**: um aviso de atribuição que reconhece o código de terceiros e/ou OSS que será compilado em seu aplicativo.

## <a name="requirements"></a>Requisitos

### <a name="android-versions"></a>Versões do Android
O SDK dá suporte à API do Android 19 (Android 4.4 +) por meio da API do Android 28 (Android 9,0).

### <a name="company-portal-app"></a>Portal da Empresa aplicativo
O SDK de aplicativo do Intune para Android depende da presença do aplicativo [portal da empresa](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) no dispositivo para habilitar as políticas de proteção do aplicativo. O Portal da Empresa recupera as políticas de proteção do aplicativo do serviço do Intune. Quando o aplicativo é inicializado, ele carrega a política e o código para impor essa política do Portal da Empresa.

> [!NOTE]
> Quando o aplicativo Portal da Empresa não está no dispositivo, um aplicativo gerenciado pelo Intune se comporta da mesma forma que um aplicativo normal que não oferece suporte a políticas de proteção de aplicativo do Intune.

Para a proteção de aplicativo sem registro de dispositivo, o usuário _**não**_ precisa registrar o dispositivo usando o aplicativo portal da empresa.

## <a name="sdk-integration"></a>Integração do SDK

### <a name="sample-app"></a>Aplicativo de exemplo
Um exemplo de como integrar com o SDK de aplicativo do Intune corretamente está disponível no [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App). Este exemplo usa o [plug-in de compilação gradle](#gradle-build-plugin).

### <a name="referencing-intune-app-libraries"></a>Referenciando bibliotecas de aplicativos do Intune

O SDK de aplicativos do Intune é uma biblioteca padrão do Android sem dependências externas. **Microsoft. Intune. Mam. Sdk. aar** contém ambas as interfaces necessárias para a habilitação de uma política de proteção de aplicativo e o código necessário para interoperar com o aplicativo Microsoft Intune portal da empresa.

**Microsoft. Intune. Mam. Sdk. aar** deve ser especificado como uma referência de biblioteca do Android. Para fazer isso, abra seu projeto de aplicativo no Android Studio e vá para **arquivo > novo > novo módulo** e selecione **importar. JAR/. Pacote AAR**. Em seguida, selecione nosso pacote de arquivamento do Android Microsoft. Intune. MAM. SDK. aar para criar um módulo para o. AAR. Clique com o botão direito do mouse no módulo ou módulos que contêm o código do aplicativo e vá para **configurações de módulo** > **guia dependências** >  **+ ícone** **dependência de módulo**  >  > selecione o módulo AAR do SDK do MAM que você acabou de criar > **OK**. Isso garantirá que o módulo seja compilado com o SDK do MAM quando você compilar seu projeto.

Além disso, as bibliotecas **Microsoft. Intune. Mam. Sdk. support. xxx. jar** contêm variantes do Intune das bibliotecas `android.support.XXX` correspondentes. Eles não são criados em Microsoft. Intune. MAM. SDK. aar caso um aplicativo não precise depender das bibliotecas de suporte.

#### <a name="proguard"></a>ProGuard

Se o [PROGuard](http://proguard.sourceforge.net/) (ou qualquer outro mecanismo de redução/ofuscação) for usado como uma etapa de compilação, o SDK terá regras de configuração adicionais que devem ser incluídas. Ao incluir o. AAR em sua compilação, nossas regras são integradas automaticamente à etapa do PROGuard e os arquivos de classe necessários são mantidos.

As bibliotecas de autenticação de Azure Active Directory (ADAL) podem ter suas próprias restrições de proteção. Se seu aplicativo integrar a ADAL, você deverá seguir a documentação do ADAL sobre essas restrições.

### <a name="policy-enforcement"></a>Aplicação da política
O SDK de aplicativos do Intune é uma biblioteca Android que permite que seu aplicativo dê suporte e participe da imposição de políticas do Intune. 

A maioria das políticas é imposta semiautomaticamente, mas determinadas políticas exigem [a participação explícita do seu aplicativo para impor](#enable-features-that-require-app-participation).
Independentemente de você executar a integração de origem ou utilizar ferramentas de Build para integração, as políticas que exigem a participação explícita precisarão ser codificadas para o.

Para políticas que são automaticamente impostas, é necessário que os aplicativos substituam a herança de várias classes base do Android por herança de equivalentes de MAM e, da mesma forma, substituem chamadas para determinadas classes de serviço do sistema Android com chamadas para equivalentes de MAM. As substituições específicas necessárias são detalhadas [abaixo](#class-and-method-replacements) e podem ser executadas manualmente com a integração de origem ou executadas automaticamente por meio de ferramentas de compilação.

### <a name="build-tooling"></a>Ferramentas de Build
O SDK fornece ferramentas de compilação (um plug-in para Builds do gradle e uma ferramenta de linha de comando para compilações não gradle) que executam substituições equivalentes de MAM automaticamente. Essas ferramentas transformam os arquivos de classe gerados pela compilação Java e não modificam o código-fonte original.

As ferramentas executam apenas [substituições diretas](#class-and-method-replacements) . Eles não executam integrações mais complexas do SDK, como [política de salvamento](#enable-features-that-require-app-participation), [várias identidades](#multi-identity-optional), [registro do aplicativo](#app-protection-policy-without-device-enrollment), modificações de [AndroidManifest](#manifest-replacements) ou configuração de [Adal](#configure-azure-active-directory-authentication-library-adal) para que eles devam ser concluídos antes do o aplicativo está totalmente habilitado para o Intune. Examine atentamente o restante desta documentação para obter os pontos de integração relevantes para seu aplicativo.

> [!NOTE]
> É bom executar as ferramentas em um projeto que já realizou a integração parcial ou completa da origem do SDK do MAM por meio de substituições manuais. Seu projeto ainda deve listar o SDK do MAM como uma dependência.

### <a name="gradle-build-plugin"></a>Plug-in de compilação gradle
Se seu aplicativo não for criado com o gradle, pule para a [integração com a ferramenta de linha de comando](#command-line-build-tool). 

O plug-in SDK do aplicativo é distribuído como parte do SDK como **GradlePlugin/com. Microsoft. Intune. Mam. Build. jar**. Para que o gradle possa localizar o plug-in, ele deve ser adicionado ao classpath buildscript. O plug-in depende de [Javassist](https://jboss-javassist.github.io/javassist/), que também deve ser adicionado. Para adicioná-los ao classpath, adicione o seguinte à sua raiz `build.gradle`

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

Em seguida, no arquivo `build.gradle` para seu projeto APK, basta aplicar o plug-in como
```groovy
apply plugin: 'com.microsoft.intune.mam'
```

Por padrão, o plug-in funcionará **somente** em dependências `project`.
Compilação de teste não afetada. A configuração pode ser fornecida à lista
*  Projetos a serem excluídos
*  [Dependências externas a serem incluídas](#usage-of-includeexternallibraries) 
*  Classes específicas a serem excluídas do processamento
*  Variantes a serem excluídas do processamento. Eles podem se referir a um nome de variante completo ou a um único tipo. Por exemplo
     * Se seu aplicativo tiver tipos de compilação `debug` e `release` com tipos {`savory`, `sweet`} e {`vanilla`, `chocolate`}, você poderá especificar
     * `savory` para excluir todas as variantes com o flavor savory ou `savoryVanillaRelease` para excluir somente essa variante exata.

#### <a name="example-partial-buildgradle"></a>Exemplo de Build parcial. gradle

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

Isso teria os seguintes efeitos:
* `:product:FooLib` não é reescrito porque está incluído no `excludeProjects`
* `:product:foo-project` é reescrito, exceto para `com.contoso.SplashActivity` que é ignorado porque está em `excludeClasses`
* `bar.jar` é reescrito porque está incluído no `includeExternalLibraries`
* `zap.jar` **não** é reescrito porque não é um projeto e não está incluído no `includeExternalLibraries`
* `com.contoso.foo:zap-artifact:1.0.0` é reescrito porque está incluído no `includeExternalLibraries`
* `com.microsoft.bar:baz:1.0.0` é reescrito porque está incluído em `includeExternalLibraries` por meio de um curinga (`com.microsoft.*`).
* `com.microsoft.qux:foo:2.0` não é reescrito, mesmo que corresponda ao mesmo caractere curinga que o item anterior, pois ele é explicitamente excluído por meio de um padrão de negação.

#### <a name="usage-of-includeexternallibraries"></a>Uso de includeExternalLibraries

Como o plug-in só opera em dependências de projeto (geralmente fornecidas pela função `project()`), por padrão, todas as dependências especificadas por `fileTree(...)` ou obtidas do Maven ou de outras fontes de pacote (por exemplo, "`com.contoso.bar:baz:1.2.0`") devem ser fornecidas à propriedade `includeExternalLibraries` se MAM o processamento deles é necessário com base nos critérios explicados abaixo. Há suporte para caracteres curinga ("*"). Um item que começa com `!` é uma negação e pode ser usado para excluir bibliotecas que, de outra forma, seriam incluídas por um curinga.

Ao especificar dependências externas com notação de artefato, é recomendável omitir o componente de versão no valor `includeExternalLibraries`. Se você incluir a versão, ela deverá ser uma versão exata. Não há suporte para especificações de versão dinâmica (por exemplo, `1.+`).

A regra geral que você deve usar para determinar se você precisa incluir bibliotecas no `includeExternalLibraries` é baseada em duas perguntas:
1. A biblioteca tem classes para as quais há equivalentes de MAM? Exemplos: `Activity`, `Fragment`, `ContentProvider`, `Service` etc.
2. Em caso afirmativo, seu aplicativo faz uso dessas classes?

Se você responder ' Sim ' a ambas as perguntas, deverá incluir essa biblioteca em `includeExternalLibraries`. 

| Cenário | Deve incluir? |
|--|--|
| Você inclui uma biblioteca do Visualizador de PDF em seu aplicativo e usa o visualizador `Activity` em seu aplicativo quando os usuários tentam exibir PDFs | Sim |
| Você inclui uma biblioteca HTTP em seu aplicativo para um desempenho aprimorado na Web | Não |
| Você inclui uma biblioteca como reagir nativo que contém classes derivadas de `Activity`, `Application` e `Fragment` e usar ou derivar ainda mais essas classes em seu aplicativo | Sim |
| Você inclui uma biblioteca como reagir nativo que contém classes derivadas de `Activity`, `Application` e `Fragment`, mas só usa auxiliares estáticos ou classes de utilitário | Não |
| Você inclui uma biblioteca que contém classes de exibição derivadas de `TextView` e você usa ou deriva ainda mais essas classes em seu aplicativo | Sim |

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

#### <a name="dependencies"></a>Dependências

O plug-in gradle tem uma dependência em [Javassist](https://jboss-javassist.github.io/javassist/), que deve estar disponível para a resolução de dependência do gradle (conforme descrito acima). Javassist é usado somente no momento da compilação ao executar o plug-in. Nenhum código Javassist será adicionado ao seu aplicativo.

> [!NOTE] 
> Você deve estar usando a versão 3,0 ou mais recente do plug-in do Android gradle e gradle 4,1 ou mais recente.

### <a name="command-line-build-tool"></a>Ferramenta de criação de linha de comando
Se sua compilação usar gradle, pule para a [próxima seção](#class-and-method-replacements).

A ferramenta de criação de linha de comando está disponível na pasta `BuildTool` do SDK soltar. Ele executa a mesma função que o plug-in gradle detalhado acima, mas pode ser integrado a sistemas de compilação personalizados ou não gradle. Como é mais genérico, é mais complexo invocar, portanto, o plug-in gradle deve ser usado quando for possível fazer isso.

#### <a name="using-the-command-line-tool"></a>Usando a ferramenta de linha de comando

A ferramenta de linha de comando pode ser chamada usando os scripts auxiliares fornecidos localizados no diretório `BuildTool\bin`.

A ferramenta espera os seguintes parâmetros.

| Parâmetro | Descrição |
| -- | -- |
| `--input` | Uma lista delimitada por ponto e vírgula de arquivos jar e diretórios de arquivos de classe a serem modificados. Isso deve incluir todos os jars/diretórios que você pretende reescrever. |
| `--output` | Uma lista delimitada por ponto e vírgula de diretórios e arquivos jar para armazenar as classes modificadas. Deve haver uma entrada de saída por entrada de entrada e elas devem ser listadas na ordem. |
| `--classpath` | O classpath da compilação. Isso pode conter jars e diretórios de classe. |
| `--excludeClasses`| Uma lista delimitada por ponto e vírgula contendo os nomes das classes que devem ser excluídas da regravação. |

Todos os parâmetros são necessários, exceto `--excludeClasses`, que é opcional.

> [!NOTE]
> Em sistemas semelhantes a UNIX, o ponto-e-vírgula é um separador de comando. Para evitar que o Shell divida os comandos, certifique-se de escapar cada ponto-e-vírgula com ' \' ' ou encapsule o parâmetro completo entre aspas.

#### <a name="example-command-line-tool-invocation"></a>Invocação de ferramenta de linha de comando de exemplo

``` batch
> BuildTool\bin\BuildTool.bat --input build\product-foo-project;libs\bar.jar --output mam-build\product-foo-project;mam-build\libs\bar.jar --classpath build\zap.jar;libs\Microsoft.Intune.MAM.SDK\classes.jar;%ANDROID_SDK_ROOT%\platforms\android-27\android.jar --excludeClasses com.contoso.SplashActivity
```

Isso teria os seguintes efeitos:

* o diretório `product-foo-project` é regravado em `mam-build\product-foo-project`
* `bar.jar` é reescrito para `mam-build\libs\bar.jar`
* `zap.jar` **não** é reescrito porque está listado somente no `--classpath`
* A classe `com.contoso.SplashActivity` **não** é reescrita, mesmo que esteja em `--input`

> [!NOTE] 
> Atualmente, a ferramenta de compilação não dá suporte a arquivos AAR. Se o seu sistema de compilação ainda não extrair `classes.jar` ao lidar com arquivos AAR, você precisará fazer isso antes de invocar a ferramenta de compilação.


## <a name="class-and-method-replacements"></a>Substituições de classe e método

As classes base do Android devem ser substituídas pelos respectivos equivalentes de MAM para habilitar o gerenciamento do Intune. As classes do SDK residem entre a classe base do Android e a versão derivada do próprio aplicativo dessa classe. Por exemplo, uma atividade de aplicativo pode acabar com uma hierarquia de herança semelhante a: `Activity` @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4. A camada de MAM filtra as chamadas para as operações do sistema a fim de fornecer diretamente ao seu aplicativo uma visão gerenciada do mundo.

Além das classes base, algumas classes que seu aplicativo pode usar sem derivar (por exemplo, `MediaPlayer`) também têm equivalentes a MAM, e [algumas chamadas de método também devem ser substituídas](#wrapped-system-services). Os detalhes precisos são fornecidos abaixo.

> [!NOTE] 
> Se seu aplicativo estiver se integrando com [ferramentas de Build](#build-tooling)do SDK, as seguintes substituições de classe e método serão executadas automaticamente.

| Classe base do Android | Substituição do SDK de aplicativo do Intune |
|--|--|
| Android. app. Activity | MAMActivity |
| Android. app. Activity | MAMActivityGroup |
| Android. app. AliasActivity | MAMAliasActivity |
| Android. app. Application | MAMApplication |
| Android. app. Dialog | MAMDialog |
| Android. app. AlertDialog. Builder | MAMAlertDialogBuilder |
| Android. app. DialogFragment | MAMDialogFragment |
| Android. app. ExpandableListActivity | MAMExpandableListActivity |
| Android. app. Fragment | MAMFragment |
| Android. app. IntentService | MAMIntentService |
| Android. app. LauncherActivity | MAMLauncherActivity |
| Android. app. ListActivity | MAMListActivity |
| Android. app. ListFragment | MAMListFragment |
| Android. app. NativeActivity | MAMNativeActivity |
| Android. app. PendingIntent | MAMPendingIntent (veja a [intenção pendente](#pendingintent)) |
| Android. app. Service | MAMService |
| Android. app. TabActivity | MAMTabActivity |
| Android. app. TaskStackBuilder | MAMTaskStackBuilder |
| Android. app. backup. BackupAgent | MAMBackupAgent |
| Android. app. backup. BackupAgentHelper | MAMBackupAgentHelper |
| Android. app. backup. FileBackupHelper | MAMFileBackupHelper |
| Android. app. backup. SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| Android. Content. BroadcastReceiver | MAMBroadcastReceiver |
| Android. Content. ContentProvider | MAMContentProvider |
| Android. os. Binder | MAMBinder (necessário somente se o associador não for gerado a partir de uma interface AIDL) do Android |
| Android. Media. MediaPlayer | MAMMediaPlayer |
| Android. Media. MediaMetadataRetriever | MAMMediaMetadataRetriever |
| Android. Provider. Documentprovider | MAMDocumentsProvider |
| Android. preference. PreferenceActivity | MAMPreferenceActivity |
| Android. support. multidex. MultiDexApplication | MAMMultiDexApplication |
| Android. widget. TextView | MAMTextView |
| Android. widget. AutoCompleteTextView | MAMAutoCompleteTextView |
| Android. widget. CheckedTextView | MAMCheckedTextView |
| Android. widget. EditText | MAMEditText |
| Android. inputmethodservice. ExtractEditText | MAMExtractEditText |
| Android. widget. MultiAutoCompleteTextView | MAMMultiAutoCompleteTextView |

> [!NOTE]
> Mesmo que seu aplicativo não tenha a necessidade de sua própria classe derivada `Application`, [consulte `MAMApplication` abaixo](#mamapplication)

### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft. Intune. MAM. SDK. support. v4. jar:

| Classe do Android | Substituição do SDK de aplicativo do Intune |
|--|--|
| Android. support. v4. app. DialogFragment | MAMDialogFragment
| Android. support. v4. app. FragmentActivity | MAMFragmentActivity
| Android. support. v4. app. Fragment | MAMFragment
| Android. support. v4. app. JobIntentService | MAMJobIntentService
| Android. support. v4. app. TaskStackBuilder | MAMTaskStackBuilder
| Android. support. v4. Content. FileProvider | MAMFileProvider
| Android. support. v4. Content. WakefulBroadcastReceiver | MAMWakefulBroadcastReceiver

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft. Intune. MAM. SDK. support. v7. jar:

|Classe do Android | Substituição do SDK de aplicativo do Intune |
|--|--|
| Android. support. v7. app. AlertDialog. Builder | MAMAlertDialogBuilder |
| Android. support. v7. app. AppCompatActivity | MAMAppCompatActivity |
| Android. support. v7. widget. AppCompatAutoCompleteTextView | MAMAppCompatAutoCompleteTextView |
| Android. support. v7. widget. AppCompatCheckedTextView | MAMAppCompatCheckedTextView |
| Android. support. v7. widget. AppCompatEditText | MAMAppCompatEditText |
| Android. support. v7. widget. AppCompatMultiAutoCompleteTextView | MAMAppCompatMultiAutoCompleteTextView |
| Android. support. v7. widget. AppCompatTextView | MAMAppCompatTextView |

### <a name="microsoftintunemamsdksupportv17jar"></a>Microsoft. Intune. MAM. SDK. support. v17. jar:
|Classe do Android | Substituição do SDK de aplicativo do Intune |
|--|--|
| Android. support. v17. Leanback. widget. SearchEditText | MAMSearchEditText |

### <a name="microsoftintunemamsdksupporttextjar"></a>Microsoft. Intune. MAM. SDK. support. Text. jar:
|Classe do Android | Substituição do SDK de aplicativo do Intune |
|--|--|
| Android. support. Text. Emoji. widget. EmojiAppCompatEditText | MAMEmojiAppCompatEditText |
| Android. support. Text. Emoji. widget. EmojiAppCompatTextView | MAMEmojiAppCompatTextView |
| Android. support. Text. Emoji. widget. EmojiEditText | MAMEmojiEditText |
| Android. support. Text. Emoji. widget. EmojiTextView | MAMEmojiTextView |

### <a name="renamed-methods"></a>Métodos renomeados
Em muitos casos, um método disponível na classe Android foi marcado como final na classe de substituição de MAM. Nesse caso, a classe de substituição de MAM fornece um método nomeado de forma semelhante (geralmente sufixado com `MAM`) que você deve substituir em vez disso. Por exemplo, ao derivar de `MAMActivity`, em vez de substituir `onCreate()` e chamar `super.onCreate()`, `Activity` deve substituir `onMAMCreate()` e chamar `super.onMAMCreate()`. O compilador Java deve impor as restrições finais para impedir a substituição acidental do método original, em vez de um equivalente a MAM.

### <a name="mamapplication"></a>MAMApplication
Se seu aplicativo criar uma subclasse de `android.app.Application`, você **deverá** criar uma subclasse de `com.microsoft.intune.mam.client.app.MAMApplication` em vez disso. Se seu aplicativo não for subclasse `android.app.Application`, você **deverá** definir `"com.microsoft.intune.mam.client.app.MAMApplication"` como o atributo `"android:name"` na marca `<application>` de AndroidManifest. xml.

### <a name="pendingintent"></a>PendingIntent
Em vez de `PendingIntent.get*`, você deve usar o método `MAMPendingIntent.get*`. Depois disso, você pode usar o @no__t resultante-0 como de costume.

### <a name="wrapped-system-services"></a>Serviços de sistema encapsulados
Para algumas classes de serviço do sistema, é necessário chamar um método estático em uma classe de wrapper MAM em vez de invocar diretamente o método desejado na instância do serviço. Por exemplo, uma chamada para `getSystemService(ClipboardManager.class).getPrimaryClip()` deve se tornar uma chamada para `MAMClipboardManager.getPrimaryClip(getSystemService(ClipboardManager.class)`. Não é recomendável fazer essas substituições manualmente. Em vez disso, deixe o BuildPlugin fazer isso.

| Classe do Android | Substituição do SDK de aplicativo do Intune |
|--|--|
| Android. Content. Clipboardmanager | MAMClipboard |
| Android. Content. ContentProviderClient | MAMContentProviderClientManagement |
| Android. Content. ContentResolver retornem | MAMContentResolverManagement |
| Android. Content. pm. PackageManager | MAMPackageManagement |
| Android. app. DownloadManager | MAMDownloadManagement |
| Android. Print. Gerenciador de impressão | MAMPrintManagement |
| Android. support. v4. Print. myhelper | MAMPrintHelperManagement |
| Android. View. View | MAMViewManagement |
| Android. View. DragEvent | MAMDragEventManagement |
| Android. app. Notificationmanager | MAMNotificationManagement |
| Android. support. v4. app. NotificationManagerCompat | MAMNotificationCompatManagement |

Algumas classes têm a maioria de seus métodos encapsulados, por exemplo, `ClipboardManager`, `ContentProviderClient`, `ContentResolver` e `PackageManager`, enquanto outras classes têm apenas um ou dois métodos encapsulados, por exemplo, `DownloadManager`, `PrintManager`, `PrintHelper`, `View`, `DragEvent`, `NotificationManager` e 0. Consulte as APIs expostas pelas classes equivalentes do MAM para o método exato se você não usar o BuildPlugin.

### <a name="manifest-replacements"></a>Substituições de manifesto
Pode ser necessário executar algumas das substituições de classe acima no manifesto, bem como no código Java. De observação especial:
* Referências de manifesto a `android.support.v4.content.FileProvider` devem ser substituídas por `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider`.

## <a name="androidx-libraries"></a>Bibliotecas AndroidX
Com o Android P, o Google anunciou um novo conjunto (renomeado) de bibliotecas de suporte chamado AndroidX, e a versão 28 é a última versão principal das bibliotecas Android. support existentes.

Ao contrário do bibliotecas de suporte do Android, não fornecemos variantes de MAM das bibliotecas AndroidX. Em vez disso, AndroidX deve ser tratado como qualquer outra biblioteca externa e deve ser configurado para ser reescrito pelo plug-in/ferramenta de compilação. Para compilações do gradle, isso pode ser feito incluindo `androidx.*` no campo `includeExternalLibraries` da configuração do plug-in. As invocações da ferramenta de linhas de comando devem listar todos os arquivos jar explicitamente.

### <a name="pre-androidx-architecture-components"></a>Componentes de arquitetura AndroidX
Muitos componentes de arquitetura do Android, incluindo o Room, o ViewModel e o Gerenciador de trabalho, foram reempacotados para AndroidX. Se seu aplicativo usar as variantes AndroidX dessas bibliotecas, verifique se as regravações se aplicam incluindo `android.arch.*` no campo `includeExternalLibraries` da configuração do plug-in. Como alternativa, atualize as bibliotecas para seus equivalentes AndroidX.

## <a name="sdk-permissions"></a>Permissões do SDK

O SDK de aplicativos do Intune requer três [permissões do sistema Android](https://developer.android.com/guide/topics/security/permissions.html) em aplicativos que o integram:

* `android.permission.GET_ACCOUNTS` (solicitado em tempo de execução, se necessário)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

A[Adal](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)(biblioteca de autenticação Azure Active Directory) exige essas permissões para executar a autenticação orientada. Se essas permissões não forem concedidas ao aplicativo ou forem revogadas pelo usuário, os fluxos de autenticação que exigem o agente (o aplicativo Portal da Empresa) serão desabilitados.

## <a name="logging"></a>Registo

O registro em log deve ser inicializado antecipadamente para obter o máximo do valor dos dados registrados. o `Application.onMAMCreate()` normalmente é o melhor lugar para inicializar o registro em log.

Para receber logs de MAM em seu aplicativo, crie um [manipulador Java](https://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html) e adicione-o ao `MAMLogHandlerWrapper`. Isso invocará `publish()` no manipulador de aplicativos para cada mensagem de log.

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

## <a name="enable-features-that-require-app-participation"></a>Habilitar recursos que exigem a participação do aplicativo

Há várias políticas de proteção de aplicativo que o SDK não pode implementar por conta própria. O aplicativo pode controlar seu comportamento para obter esses recursos usando várias APIs que você pode encontrar na interface `AppPolicy` a seguir. Para recuperar uma instância `AppPolicy`, use `MAMPolicyManager.getPolicy`.

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
> `MAMPolicyManager.getPolicy` sempre retornará uma política de aplicativo não nula, mesmo que o dispositivo ou aplicativo não esteja sob uma política de gerenciamento do Intune.

### <a name="example-determine-if-pin-is-required-for-the-app"></a>Exemplo: determinar se o PIN é necessário para o aplicativo

Se o aplicativo tiver sua própria experiência de usuário de PIN, talvez você queira desabilitá-lo se o administrador de TI tiver configurado o SDK para solicitar um PIN de aplicativo. Para determinar se o administrador de ti implantou a política de PIN do aplicativo para esse aplicativo, para o usuário final atual, chame o seguinte método:

```java

MAMPolicyManager.getPolicy(currentActivity).getIsPinRequired();
```

### <a name="example-determine-the-primary-intune-user"></a>Exemplo: determinar o usuário principal do Intune

Além das APIs expostas em AppPolicy, o**UPN**(nome principal do usuário) também é exposto pela API `getPrimaryUser()` definida dentro da interface `MAMUserInfo`. Para obter o UPN, chame o seguinte:

```java
MAMComponents.get(MAMUserInfo.class).getPrimaryUser();
```

A definição completa da interface MAMUserInfo está abaixo:

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

### <a name="example-determine-if-saving-to-device-or-cloud-storage-is-permitted"></a>Exemplo: determinar se é permitido salvar no dispositivo ou no armazenamento em nuvem

Muitos aplicativos implementam recursos que permitem ao usuário final salvar arquivos localmente ou em um serviço de armazenamento em nuvem. O SDK de aplicativos do Intune permite que os administradores de ti se protejam contra vazamento de dados aplicando restrições de política, pois eles se ajustam à sua organização.  Uma das políticas que ele pode controlar é se o usuário final pode salvar em um armazenamento de dados "pessoal" não gerenciado. Isso inclui salvar em um local local, cartão SD ou serviços de backup de terceiros.

**A participação do aplicativo é necessária para habilitar o recurso.** Se seu aplicativo permite salvar em locais pessoais ou de nuvem diretamente do aplicativo, você deve implementar esse recurso para garantir que o administrador de ti possa controlar se é permitido salvar em um local. A API abaixo permite que o aplicativo saiba se é permitido salvar em um repositório pessoal pela política do administrador do Intune atual. O aplicativo pode, então, impor a política, já que está ciente do armazenamento de dados pessoais disponível para o usuário final por meio do aplicativo.  

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

O método anterior para determinar se a política de um usuário permitia salvar dados em vários locais foi `getIsSaveToPersonalAllowed()` na mesma classe **AppPolicy** . Esta função foi **preterida** e não deve ser usada, a seguinte invocação é equivalente a `getIsSaveToPersonalAllowed()`:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(SaveLocation.LOCAL, null);
```

>[!NOTE]
> Use `SaveLocation.OTHER` se o local em questão não estiver listado na enumeração **SaveLocations** .

### <a name="example-determine-if-notifications-with-organization-data-need-to-be-restricted"></a>Exemplo: determinar se as notificações com dados da organização precisam ser restritas

Se seu aplicativo exibir notificações, você deverá verificar a política de restrição de notificação para o usuário associado à notificação antes de mostrar a notificação. Para determinar se a política é imposta, faça a chamada a seguir.

```java
NotificationRestriction notificationRestriction =
    MAMPolicyManager.getPolicyForIdentity(notificationIdentity).getNotificationRestriction();
```

Se a restrição for `BLOCKED`, o aplicativo não deverá mostrar nenhuma notificação para o usuário associado a essa política. Se `BLOCK_ORG_DATA`, o aplicativo deverá mostrar uma notificação modificada que não contém dados da organização. Se `UNRESTRICTED`, todas as notificações serão permitidas.

Se `getNotificationRestriction` não for invocado, o SDK do MAM fará um melhor esforço para restringir as notificações automaticamente para aplicativos de identidade única. Se o bloqueio automático estiver habilitado e `BLOCK_ORG_DATA` estiver definido, a notificação não será mostrada. Para um controle mais refinado, verifique o valor de `getNotificationRestriction` e modifique as notificações do aplicativo adequadamente.

## <a name="register-for-notifications-from-the-sdk"></a>Registrar-se para notificações do SDK

### <a name="overview"></a>Visão geral
O SDK de aplicativos do Intune permite que seu aplicativo controle o comportamento de determinadas políticas, como apagamento seletivo, quando elas são implantadas pelo administrador de ti. Quando um administrador de ti implanta tal política, o serviço do Intune envia uma notificação para o SDK.

Seu aplicativo deve se registrar para notificações do SDK criando um `MAMNotificationReceiver` e registrando-o com `MAMNotificationReceiverRegistry`. Isso é feito fornecendo o receptor e o tipo de notificação desejado no `App.onCreate`, como mostra o exemplo a seguir:

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

A interface `MAMNotificationReceiver` simplesmente recebe notificações do serviço do Intune. Algumas notificações são tratadas diretamente pelo SDK, enquanto outras exigem a participação do aplicativo. Um aplicativo **deve** retornar true ou false de uma notificação. Ele sempre deve retornar true, a menos que alguma ação que ele tentou executar como resultado da notificação tenha falhado.

* Essa falha pode ser relatada ao serviço do Intune. Um exemplo de um cenário a ser relatado é se o aplicativo não apagar os dados do usuário depois que o administrador de ti iniciar um apagamento.

>[!NOTE]
> É seguro Bloquear em `MAMNotificationReceiver.onReceive` porque seu retorno de chamada não está em execução no thread da interface do usuário.

A interface `MAMNotificationReceiver`, conforme definido no SDK, está incluída abaixo:

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

As notificações a seguir são enviadas para o aplicativo e algumas delas podem exigir a participação do aplicativo:

* **WIPE_USER_DATA**: essa notificação é enviada em uma classe `MAMUserNotification`. Quando essa notificação é recebida, o aplicativo *deve* excluir todos os dados associados à identidade gerenciada (do `MAMUserNotification.getUserIdentity()`). A notificação pode ocorrer por vários motivos, incluindo quando o aplicativo chama `unregisterAccountForMAM`, quando um administrador de ti inicia um apagamento ou quando as políticas de acesso condicional exigidas pelo administrador não são satisfeitas. Se seu aplicativo não se registrar para essa notificação, o comportamento de apagamento padrão será executado. O comportamento padrão excluirá todos os arquivos de um aplicativo de identidade única ou todos os arquivos marcados com a identidade gerenciada para um aplicativo de várias identidades. Essa notificação nunca será enviada no thread da interface do usuário.

* **WIPE_USER_AUXILIARY_DATA**: os aplicativos podem se registrar para essa notificação se quiserem que o SDK do aplicativo do Intune execute o comportamento de apagamento seletivo padrão, mas ainda gostaria de remover alguns dados auxiliares quando o apagamento ocorrer. Essa notificação não está disponível para aplicativos de identidade única--ela só será enviada para aplicativos de várias identidades. Essa notificação nunca será enviada no thread da interface do usuário.

* **REFRESH_POLICY**: essa notificação é enviada em um `MAMUserNotification`. Quando essa notificação é recebida, todas as decisões de política do Intune armazenadas em cache por seu aplicativo devem ser invalidadas e atualizadas. Se seu aplicativo não armazenar nenhuma suposição de política, ele não precisará se registrar para essa notificação. Nenhuma garantia é feita com a qual thread essa notificação será enviada.

* **REFRESH_APP_CONFIG**: essa notificação é enviada em um `MAMUserNotification`. Quando essa notificação é recebida, todos os dados de configuração de aplicativo em cache devem ser invalidados e atualizados. Nenhuma garantia é feita com a qual thread essa notificação será enviada.

* **MANAGEMENT_REMOVED**: essa notificação é enviada em um `MAMUserNotification` e informa ao aplicativo que ele está prestes a ficar não gerenciado. Uma vez não gerenciado, não será mais possível ler arquivos criptografados, ler dados criptografados com MAMDataProtectionManager, interagir com a área de transferência criptografada ou participar do ecossistema de aplicativo gerenciado. Veja mais detalhes abaixo. Essa notificação nunca será enviada no thread da interface do usuário.

* **MAM_ENROLLMENT_RESULT**: essa notificação é enviada em um `MAMEnrollmentNotification` para informar ao aplicativo que uma tentativa de registro de aplicativo foi concluída e para fornecer o status dessa tentativa. Nenhuma garantia é feita com a qual thread essa notificação será enviada.

* **COMPLIANCE_STATUS**: essa notificação é enviada em um `MAMComplianceNotification` para informar o aplicativo sobre o resultado de uma tentativa de correção de conformidade. Nenhuma garantia é feita com a qual thread essa notificação será enviada.

> [!NOTE]
> Um aplicativo nunca deve se registrar para as notificações `WIPE_USER_DATA` e `WIPE_USER_AUXILIARY_DATA`.

### <a name="management_removed"></a>MANAGEMENT_REMOVED

A notificação `MANAGEMENT_REMOVED` indica que um usuário gerenciado anteriormente por política não será mais gerenciado pela política de MAM do Intune. Isso não exige a limpeza dos dados do usuário nem a desconexão do usuário (se um apagamento fosse necessário, uma notificação `WIPE_USER_DATA` seria enviada). Muitos aplicativos podem não precisar lidar com essa notificação, no entanto, os aplicativos que usam `MAMDataProtectionManager` devem [tomar nota especial dessa notificação](#data-protection).

Quando o MAM chamar o receptor `MANAGEMENT_REMOVED` do aplicativo, o seguinte será verdadeiro:
* O MAM já descriptografau os arquivos criptografados anteriormente (mas não os buffers de dados protegidos) pertencentes ao aplicativo. Os arquivos em locais públicos no sdcard que não pertencem diretamente ao aplicativo (por exemplo, os documentos ou pastas de download) não são descriptografados.
* Novos arquivos ou buffers de dados protegidos criados pelo método receptor (ou qualquer outro código executado após o início do receptor) não serão criptografados.
* O aplicativo ainda tem acesso às chaves de criptografia, portanto, operações como buffers de dados de descriptografia serão bem sucedidos.

Depois que o receptor do aplicativo retornar, ele não terá mais acesso às chaves de criptografia.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Configurar a ADAL (biblioteca de autenticação de Azure Active Directory)

Primeiro, leia as diretrizes de integração do ADAL encontradas no [repositório da Adal no GitHub](https://github.com/AzureAD/azure-activedirectory-library-for-android).

O SDK depende da [Adal](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) para seus cenários de [autenticação](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) e de inicialização condicional, que exigem que os aplicativos sejam configurados com [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). Os valores de configuração são comunicados ao SDK por meio de metadados do AndroidManifest.

Para configurar seu aplicativo e habilitar a autenticação adequada, adicione o seguinte ao nó do aplicativo em AndroidManifest. xml. Algumas dessas configurações só serão necessárias se seu aplicativo usar a ADAL para autenticação em geral; Nesse caso, você precisará dos valores específicos que seu aplicativo usa para se registrar no AAD. Isso é feito para garantir que o usuário final não seja solicitado a autenticar duas vezes, devido ao AAD reconhecer dois valores de registro separados: um do aplicativo e um do SDK.

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

* **Authority** é a autoridade do AAD em uso. Se esse valor estiver ausente, o ambiente público do AAD será usado.
    > [!NOTE]
    > Não defina esse campo se seu aplicativo tiver reconhecimento de nuvem soberanas.

* **ClientID** é o do AAD ClientID (também conhecido como ID do aplicativo) a ser usado. Você deve usar o ClientID do seu próprio aplicativo se ele estiver registrado no Azure AD ou utilizar o [registro padrão](#default-enrollment-optional) se ele não integrar a Adal.

* **NonBrokerRedirectURI** é o URI de redirecionamento do AAD a ser usado em casos sem agente. Se nenhum for especificado, um valor padrão de `urn:ietf:wg:oauth:2.0:oob` será usado. Esse padrão é adequado para a maioria dos aplicativos.

  * O NonBrokerRedirectURI é usado apenas quando O skipbroker é "true".

* **O skipbroker** é usado para substituir o comportamento de participação de SSO do Adal padrão. O skipbroker deve ser especificado somente para aplicativos que especificam um ClientID **e** não dão suporte a autenticação orientada/SSO de todo o dispositivo. Nesse caso, ele deve ser definido como "true". A maioria dos aplicativos não deve definir o parâmetro O skipbroker.

  * Um ClientID **deve** ser especificado no manifesto para especificar um valor de o skipbroker.

  * Quando um ClientID é especificado, o valor padrão é "false".

  * Quando O skipbroker for "true", o NonBrokerRedirectURI será usado. Os aplicativos que não integram a ADAL (e, portanto, não têm ClientID) também serão padronizados como "true".

### <a name="common-adal-configurations"></a>Configurações comuns de ADAL

Veja a seguir maneiras comuns de que um aplicativo pode ser configurado com a ADAL. Localize a configuração do aplicativo e certifique-se de definir os parâmetros de metadados ADAL (explicados acima) para os valores necessários. Em todos os casos, a autoridade pode ser especificada se desejado para ambientes não padrão. Se não for especificado, a autoridade do AAD de produção pública será usada.

#### <a name="1-app-does-not-integrate-adal"></a>1. o aplicativo não integra a ADAL
Os metadados de ADAL **não devem** estar presentes no manifesto.

#### <a name="2-app-integrates-adal"></a>2. o aplicativo integra a ADAL

|Parâmetro ADAL necessário| Valor |
|--|--|
| ClientID | O ClientID do aplicativo (gerado pelo Azure AD quando o aplicativo é registrado) |

A autoridade pode ser especificada se necessário.

Você deve registrar seu aplicativo com o Azure AD e dar acesso ao aplicativo para o serviço de política de proteção de aplicativo:
* Consulte [aqui](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) para obter informações sobre como registrar um aplicativo com o Azure AD.
* Certifique-se de que as etapas para fornecer permissões de aplicativo Android para o serviço de política de proteção de aplicativo (aplicativo) sejam seguidas. Use as instruções no [guia Introdução ao SDK do Intune](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration) em "Dê ao seu aplicativo acesso ao serviço de proteção de aplicativo do Intune (opcional)". 

Consulte também os requisitos para [acesso condicional](#conditional-access) abaixo.


#### <a name="3-app-integrates-adal-but-does-not-support-brokered-authenticationdevice-wide-sso"></a>3. o aplicativo integra o ADAL, mas não dá suporte a autenticação orientada/SSO de todo o dispositivo

|Parâmetro ADAL necessário| Valor |
|--|--|
| ClientID | O ClientID do aplicativo (gerado pelo Azure AD quando o aplicativo é registrado) |
| O skipbroker | **True** |

Authority e NonBrokerRedirectURI podem ser especificados, se necessário.

### <a name="conditional-access"></a>Acesso Condicional
O acesso condicional (CA) é um [recurso](https://docs.microsoft.com/azure/active-directory/develop/active-directory-conditional-access-developer) Azure Active Directory que pode ser usado para controlar o acesso aos recursos do AAD. [Os administradores do Intune podem definir regras de CA](https://docs.microsoft.com/intune/conditional-access) que permitem o acesso a recursos somente de dispositivos ou aplicativos que são gerenciados pelo Intune. Para garantir que seu aplicativo seja capaz de acessar recursos quando apropriado, é necessário seguir as etapas abaixo. Se seu aplicativo não adquirir nenhum token de acesso do AAD ou acessar apenas os recursos que não podem ser protegidos por CA, você poderá ignorar essas etapas.

1. Siga as [diretrizes de integração do Adal](https://github.com/AzureAD/azure-activedirectory-library-for-android#how-to-use-this-library). 
   Consulte a etapa 11 especialmente para uso do agente.
2. [Registre seu aplicativo com o Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-app-registration). 
   O URI de redirecionamento pode ser encontrado nas diretrizes de integração do ADAL acima.
3. Defina os parâmetros de meta-dados do manifesto por [configurações comuns de Adal](#common-adal-configurations), item 2, acima.
4. Testar se tudo está configurado corretamente habilitando a [AC baseada em dispositivo](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use) do [portal do Azure](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExchangeConnectorMenu/aad/connectorType/2) e confirmando
    - Essa entrada em seu aplicativo solicita a instalação e o registro do Portal da Empresa do Intune
    - Após o registro, a entrada em seu aplicativo é concluída com êxito.
5. Depois que seu aplicativo tiver enviado a integração do SDK de aplicativo do Intune, entre em contato com msintuneappsdk@microsoft.com para ser adicionado à lista de aplicativos aprovados para [acesso condicional baseado em aplicativo](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use#app-based-conditional-access)
6. Depois que seu aplicativo tiver sido adicionado à lista aprovada, valide [Configurando a AC baseada em aplicativo](https://docs.microsoft.com/intune/app-based-conditional-access-intune-create) e garantindo que a entrada em seu aplicativo seja concluída com êxito.

## <a name="app-protection-policy-without-device-enrollment"></a>Política de proteção de aplicativo sem registro de dispositivo

### <a name="overview"></a>Visão geral
A política de proteção de aplicativo do Intune sem registro de dispositivo, também conhecida como APP-WE ou MAM-WE, permite que os aplicativos sejam gerenciados pelo Intune sem a necessidade de o dispositivo ser registrado no MDM do Intune. APP-trabalha com ou sem registro de dispositivo. O Portal da Empresa ainda precisa ser instalado no dispositivo, mas o usuário não precisa entrar no Portal da Empresa e registrar o dispositivo.

> [!NOTE]
> Todos os aplicativos são necessários para dar suporte à política de proteção de aplicativo sem registro de dispositivo.

### <a name="workflow"></a>Fluxo de Trabalho

Quando um aplicativo cria uma nova conta de usuário, ele deve registrar a conta para gerenciamento com o SDK de aplicativo do Intune. O SDK manipulará os detalhes do registro do aplicativo no serviço APP-WE; se necessário, ele tentará novamente quaisquer registros em intervalos de tempo apropriados se ocorrerem falhas.

O aplicativo também pode consultar o SDK do aplicativo do Intune para obter o status de um usuário registrado para determinar se o usuário deve ser impedido de acessar o conteúdo corporativo. Várias contas podem ser registradas para gerenciamento, mas no momento apenas uma conta pode ser inscrita ativamente com o serviço APP-WE de cada vez. Isso significa que apenas uma conta no aplicativo pode receber a política de proteção de aplicativo por vez.

O aplicativo é necessário para fornecer um retorno de chamada para adquirir o token de acesso apropriado da ADAL (biblioteca de autenticação de Azure Active Directory) em nome do SDK. Supõe-se que o aplicativo já usa a ADAL para autenticação de usuário e para adquirir seus próprios tokens de acesso.

Quando o aplicativo remove uma conta completamente, ele deve cancelar o registro dessa conta para indicar que o aplicativo não deve mais aplicar a política para esse usuário. Se o usuário tiver sido registrado no serviço MAM, o registro do usuário será cancelado e o aplicativo será apagado.

### <a name="overview-of-app-requirements"></a>Visão geral dos requisitos do aplicativo

Para implementar a integração do APP-WE, seu aplicativo deve registrar a conta de usuário com o SDK do MAM:

1. O aplicativo _deve_ implementar e registrar uma instância da interface `MAMServiceAuthenticationCallback`. A instância de retorno de chamada deve ser registrada o mais cedo possível no ciclo de vida do aplicativo (normalmente no método `onMAMCreate()` da classe de aplicativo).

2. Quando uma conta de usuário é criada e o usuário entra com êxito com a ADAL, o aplicativo _deve_ chamar o `registerAccountForMAM()`.

3. Quando uma conta de usuário é removida, o aplicativo deve chamar `unregisterAccountForMAM()` para remover a conta do gerenciamento do Intune.

    > [!NOTE]
    > Se um usuário sair do aplicativo temporariamente, o aplicativo não precisará chamar `unregisterAccountForMAM()`. A chamada pode iniciar um apagamento para remover completamente os dados corporativos do usuário.


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager
Todas as APIs de autenticação e registro necessárias podem ser encontradas na interface `MAMEnrollmentManager`. Uma referência ao `MAMEnrollmentManager` pode ser obtida da seguinte maneira:

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr
```

A instância `MAMEnrollmentManager` retornada é garantida para não ser nula. Os métodos de API se enquadram em duas categorias: **autenticação** e **registro de conta**.

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

### <a name="account-authentication"></a>Autenticação de conta
Esta seção descreve os métodos de API de autenticação no `MAMEnrollmentManager` e como usá-los.

```java
interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
}
void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
void updateToken(String upn, String aadId, String resourceId, String token);
```

1. O aplicativo deve implementar a interface `MAMServiceAuthenticationCallback` para permitir que o SDK solicite um token ADAL para o usuário e a ID de recurso fornecidos. A instância de retorno de chamada deve ser fornecida para o `MAMEnrollmentManager` chamando seu método `registerAuthenticationCallback()`. Um token pode ser necessário no início do ciclo de vida do aplicativo para tentativas de registro ou check-ins de atualização de política de proteção de aplicativo; portanto, o lugar ideal para registrar o retorno de chamada está no método `onMAMCreate()` da subclasse `MAMApplication` do aplicativo.

2. O método `acquireToken()` deve adquirir o token de acesso para a ID de recurso solicitada para o usuário especificado. Se ele não puder adquirir o token solicitado, ele deverá retornar NULL.

    > [!NOTE]
    > Verifique se seu aplicativo utiliza os parâmetros `resourceId` e `aadId` passados para `acquireToken()` para que o token correto seja adquirido.

    ```java
    class MAMAuthCallback implements MAMServiceAuthenticationCallback {
        public String acquireToken(String upn, String aadId, String resourceId) {
            return mAuthContext.acquireTokenSilentSync(resourceId, ClientID, aadId).getAccessToken();
        }
    }
    ```

3. Caso o aplicativo não possa fornecer um token quando o SDK chamar `acquireToken()`--por exemplo, se a autenticação silenciosa falhar e for um tempo inconveniente para mostrar uma interface do usuário – o aplicativo poderá fornecer um token em um momento posterior chamando o método `updateToken()`. O mesmo UPN, ID do AAD e ID de recurso que foram solicitados pela chamada anterior para `acquireToken()` devem ser passados para `updateToken()`, juntamente com o token que finalmente foi adquirido. O aplicativo deve chamar esse método assim que possível depois de retornar NULL do retorno de chamada fornecido.

    > [!NOTE]
    > O SDK chamará `acquireToken()` periodicamente para obter o token, portanto, chamar `updateToken()` não é estritamente necessário. No entanto, é altamente recomendável, pois pode ajudar os registros e os check-ins de política de proteção de aplicativo a serem concluídos oportunamente.


### <a name="account-registration"></a>Registro de conta
Esta seção descreve os métodos de API de registro de conta no `MAMEnrollmentManager` e como usá-los.

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. Para registrar uma conta para gerenciamento, o aplicativo deve chamar `registerAccountForMAM()`. Uma conta de usuário é identificada por seu UPN e sua ID de usuário do AAD. A ID do locatário também é necessária para associar os dados de registro ao locatário do AAD do usuário. A autoridade do usuário também pode ser fornecida para permitir o registro em nuvens soberanas específicas; para obter mais informações, consulte [registro em nuvem soberanas](#sovereign-cloud-registration).  O SDK pode tentar registrar o aplicativo para o usuário determinado no serviço de MAM; Se o registro falhar, ele tentará novamente o registro periodicamente até que a conta tenha o registro cancelado. O período de repetição normalmente será de 12-24 horas. O SDK fornece o status de tentativas de registro de forma assíncrona por meio de notificações.

2. Como a autenticação do AAD é necessária, o melhor momento para registrar a conta de usuário é depois que o usuário entrou no aplicativo e é autenticado com êxito usando a ADAL. A ID do AAD do usuário e a ID do locatário são retornadas da chamada de autenticação da ADAL como parte do objeto [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android) .
    * A ID do locatário vem do método `AuthenticationResult.getTenantID()`.
    * As informações sobre o usuário são encontradas em um subobjeto do tipo `UserInfo` que vem de `AuthenticationResult.getUserInfo()`, e a ID de usuário do AAD é recuperada desse objeto chamando `UserInfo.getUserId()`.

3. Para cancelar o registro de uma conta do gerenciamento do Intune, o aplicativo deve chamar `unregisterAccountForMAM()`. Se a conta tiver sido registrada com êxito e for gerenciada, o SDK cancelará o registro da conta e apagará seus dados. As tentativas de registro periódicas para a conta serão interrompidas. O SDK fornece o status de solicitação de cancelamento de registro de forma assíncrona via notificação.

### <a name="sovereign-cloud-registration"></a>Registro em nuvem do soberanas
Os aplicativos que são [soberanas na nuvem](https://www.microsoft.com/trustcenter/cloudservices/nationalcloud) **devem** fornecer o `authority` a `registerAccountForMAM()`.  Isso pode ser obtido fornecendo `instance_aware=true` no [1.14.0 +](https://github.com/AzureAD/azure-activedirectory-library-for-android/releases/tag/v1.14.0) acquireToken EXTRAQUERYPARAMETERS da Adal, seguido invocando `getAuthority()` no AuthenticationCallback AuthenticationResult.

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
> Verifique se a autoridade está definida corretamente no seu método `MAMServiceAuthenticationCallback::acquireToken()`.

#### <a name="currently-supported-sovereign-clouds"></a>Nuvens soberanas com suporte no momento

1. Nuvem do governo dos EUA do Azure

### <a name="important-implementation-notes"></a>Notas de implementação importantes

#### <a name="authentication"></a>Autenticação
* Quando o aplicativo chama `registerAccountForMAM()`, ele pode receber um retorno de chamada em sua interface `MAMServiceAuthenticationCallback` logo depois, em um thread diferente. O ideal é que o aplicativo adquirisse seu próprio token do ADAL antes de registrar a conta para agilizar a aquisição do token solicitado. Se o aplicativo retornar um token válido do retorno de chamada, o registro continuará e o aplicativo receberá o resultado final por meio de uma notificação.

* Se o aplicativo não retornar um token válido do AAD, o resultado final da tentativa de registro será `AUTHENTICATION_NEEDED`. Se o aplicativo receber esse resultado por meio de notificação, é altamente recomendável agilizar o processo de registro adquirindo o token para o usuário e o recurso solicitado anteriormente do `acquireToken()` e chamando o método `updateToken()` para iniciar o processo de registro outra.

* O `MAMServiceAuthenticationCallback` registrado do aplicativo também será chamado para adquirir um token para check-ins de atualização de política de proteção de aplicativo periódico. Se o aplicativo não puder fornecer um token quando solicitado, ele não receberá uma notificação, mas deverá tentar adquirir um token e chamar `updateToken()` no próximo momento conveniente para agilizar o processo de check-in. Se um token não for fornecido, o retorno de chamada ainda será chamado na próxima tentativa de check-in.

* O suporte para nuvens soberanas requer o fornecimento da autoridade.

#### <a name="registration"></a>Registo
* Para sua conveniência, os métodos de registro são idempotentes; por exemplo, `registerAccountForMAM()`will registrar apenas uma conta e tentar registrar o aplicativo se a conta ainda não estiver registrada, e `unregisterAccountForMAM()` cancelará o registro de uma conta somente se ela estiver registrada no momento. As chamadas subsequentes são sem operações, portanto, não há nenhum dano na chamada desses métodos mais de uma vez. Além disso, a correspondência entre chamadas para esses métodos e notificações de resultados não é garantida: ou seja, se `registerAccountForMAM()` for chamado para uma identidade que já está registrada, a notificação poderá não ser enviada novamente para essa identidade. É possível que as notificações sejam enviadas que não correspondam a nenhuma chamada para esses métodos, pois o SDK pode periodicamente tentar inscrições em segundo plano, e os cancelamentos de registro podem ser disparados por solicitações de apagamento recebidas do serviço do Intune.

* Os métodos de registro podem ser chamados para qualquer número de identidades diferentes, mas atualmente apenas uma conta de usuário pode ser registrada com êxito. Se várias contas de usuário que são licenciadas para o Intune e direcionadas pela política de proteção de aplicativo são registradas ao mesmo tempo, não há nenhuma garantia sobre qual delas ganhará a corrida.

* Por fim, você pode consultar o `MAMEnrollmentManager` para ver se uma conta específica está registrada e obter seu status atual usando o método `getRegisteredAccountStatus()`. Se a conta fornecida não estiver registrada, esse método retornará **NULL**. Se a conta for registrada, esse método retornará o status da conta como um dos membros da enumeração `MAMEnrollmentManager.Result`.

### <a name="result-and-status-codes"></a>Resultados e códigos de status
Quando uma conta é registrada pela primeira vez, ela começa no estado `PENDING`, indicando que a tentativa inicial de registro do serviço MAM está incompleta. Após a conclusão da tentativa de registro, uma notificação será enviada com um dos códigos de resultado na tabela a seguir. Além disso, o método `getRegisteredAccountStatus()` retornará o status da conta para que o aplicativo sempre possa determinar se o acesso ao conteúdo corporativo está bloqueado para esse usuário. Se a tentativa de registro falhar, o status da conta poderá mudar ao longo do tempo à medida que o SDK tentar novamente o registro em segundo plano.

|Código de resultado | Explicação |
| -- | -- |
| `AUTHORIZATION_NEEDED` | Esse resultado indica que um token não foi fornecido pela instância `MAMServiceAuthenticationCallback` registrada do aplicativo ou o token fornecido era inválido.  O aplicativo deve adquirir um token válido e chamar `updateToken()`, se possível. |
| `NOT_LICENSED` | O usuário não está licenciado para o Intune ou houve falha na tentativa de contatar o serviço de MAM do Intune.  O aplicativo deve continuar em um estado não gerenciado (normal) e o usuário não deve ser bloqueado.  Os registros serão repetidos periodicamente caso o usuário se torne licenciado no futuro. |
| `ENROLLMENT_SUCCEEDED` | A tentativa de registro foi bem-sucedida ou o usuário já está registrado.  No caso de um registro bem-sucedido, uma notificação de atualização de política será enviada antes desta notificação.  O acesso a dados corporativos deve ser permitido. |
| `ENROLLMENT_FAILED` | Falha na tentativa de registro.  Mais detalhes podem ser encontrados nos logs do dispositivo.  O aplicativo não deve permitir o acesso a dados corporativos nesse estado, pois foi anteriormente determinado que o usuário está licenciado para o Intune.|
| `WRONG_USER` | Somente um usuário por dispositivo pode registrar um aplicativo com o serviço de MAM. Esse resultado indica que o usuário para o qual esse resultado foi entregue (o segundo usuário) é direcionado com a política de MAM, mas um usuário diferente já está registrado. Como a política de MAM não pode ser imposta para o segundo usuário, seu aplicativo não deve permitir o acesso a esses dados do usuário (possivelmente removendo o usuário do seu aplicativo) a menos que/até que o registro desse usuário tenha sucesso em um momento posterior. Simultâneo com o fornecimento desse `WRONG_USER` resultado, o MAM solicitará a opção de remover a conta existente. Se o usuário humano responder no afirmativo, será possível registrar o segundo usuário um pouco mais tarde. Desde que o segundo usuário permaneça registrado, o MAM tentará registrar o registro periodicamente. |
| `UNENROLLMENT_SUCCEEDED` | O cancelamento do registro foi bem-sucedido.|
| `UNENROLLMENT_FAILED` | Falha na solicitação de cancelamento de registro.  Mais detalhes podem ser encontrados nos logs do dispositivo. Em geral, isso não ocorrerá enquanto o aplicativo passar um UPN válido (nem nulo ou vazio). Não há nenhuma correção direta e confiável que o aplicativo possa tomar. Se esse valor for recebido ao cancelar o registro de um UPN válido, informe-o como um bug para a equipe de MAM do Intune.|
| `PENDING` | A tentativa de registro inicial para o usuário está em andamento.  O aplicativo pode bloquear o acesso a dados corporativos até que o resultado do registro seja conhecido, mas não é necessário fazê-lo. |
| `COMPANY_PORTAL_REQUIRED` | O usuário é licenciado para o Intune, mas o aplicativo não pode ser registrado até que o aplicativo Portal da Empresa seja instalado no dispositivo. O SDK do aplicativo do Intune tentará bloquear o acesso ao aplicativo para o usuário fornecido e direcioná-lo para instalar o aplicativo Portal da Empresa (consulte abaixo para obter detalhes). |


### <a name="company-portal-requirement-prompt-override-optional"></a>Substituição do prompt de requisito de Portal da Empresa (opcional)
Se o resultado de `COMPANY_PORTAL_REQUIRED` for recebido, o SDK bloqueará o uso de atividades que usam a identidade para a qual o registro foi solicitado. Em vez disso, o SDK fará com que essas atividades exibam um prompt para baixar o Portal da Empresa. Se você quiser evitar esse comportamento em seu aplicativo, as atividades podem implementar `MAMActivity.onMAMCompanyPortalRequired`.

Esse método é chamado antes de o SDK exibir sua interface do usuário de bloqueio padrão. Se o aplicativo alterar a identidade da atividade ou cancelar o registro do usuário que tentou se registrar, o SDK não bloqueará a atividade. Nessa situação, cabe ao aplicativo evitar vazamento de dados corporativos. Somente aplicativos de várias identidades (discutidos posteriormente) poderão alterar a identidade da atividade.

Se você não herdar explicitamente `MAMActivity` (porque as ferramentas de compilação farão essa alteração), mas ainda precisarão lidar com essa notificação, em vez disso, você poderá implementar `MAMActivityBlockingListener`.

### <a name="notifications"></a>Notificações
Se o aplicativo se registrar para notificações do tipo **MAM_ENROLLMENT_RESULT**, um `MAMEnrollmentNotification` será enviado para informar ao aplicativo que a solicitação de registro foi concluída. O `MAMEnrollmentNotification` será recebido por meio da interface `MAMNotificationReceiver`, conforme descrito na seção [registrar-se para notificações do SDK](#register-for-notifications-from-the-sdk) .

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}
```

O método `getEnrollmentResult()` retorna o resultado da solicitação de registro.  Como `MAMEnrollmentNotification` estende `MAMUserNotification`, a identidade do usuário para quem o registro foi tentado também está disponível. O aplicativo deve implementar a interface `MAMNotificationReceiver` para receber essas notificações, detalhadas na seção [registrar-se para notificações do SDK](#register-for-notifications-from-the-sdk) .

O status da conta de usuário registrado pode ser alterado quando uma notificação de registro é recebida, mas não será alterada em todos os casos (por exemplo, se a notificação de `AUTHORIZATION_NEEDED` for recebida após um resultado mais informativo, como `WRONG_USER`, o resultado mais informativo será mantido como o status da conta).  Depois que a conta for inscrita com êxito, o status permanecerá como `ENROLLMENT_SUCCEEDED` até que a conta tenha o registro ou apagamento cancelado.

## <a name="app-ca-with-policy-assurance"></a>AC de aplicativo com garantia de política

### <a name="overview"></a>Visão geral
Com a AC do aplicativo (acesso condicional) com a garantia de política, o acesso aos recursos é condicional no aplicativo de políticas de Proteção de Aplicativo do Intune.  O AAD impõe isso exigindo que o aplicativo seja registrado e gerenciado pelo aplicativo antes de conceder um token para acessar uma AC de aplicativo com o recurso protegido de garantia de política.  O aplicativo é necessário para usar o agente ADAL para aquisição de token e a configuração é a mesma descrita acima em [acesso condicional](#conditional-access).

### <a name="adal-changes"></a>Alterações de ADAL
A biblioteca ADAL tem um novo código de erro informando ao aplicativo que a falha na aquisição de um token foi causada pela não conformidade com o gerenciamento de aplicativos.  Se o aplicativo receber esse código de erro, ele precisará chamar o SDK para tentar corrigir a conformidade registrando o aplicativo e aplicando a política. Uma exceção será recebida pelo método `onError()` da ADAL `AuthenticationCallback` e terá o código de erro `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED`.  Nesse caso, a exceção pode ser convertida em um `IntuneAppProtectionPolicyRequiredException`, do qual parâmetros adicionais podem ser extraídos para uso na conformidade de correção (consulte o exemplo de código abaixo). Depois que a correção for bem-sucedida, o aplicativo poderá tentar novamente a aquisição do token por meio da ADAL.

> [!NOTE]
> Esse novo código de erro e outro suporte para a AC de aplicativo com garantia de política exigem a versão 1.15.0 (ou superior) da biblioteca ADAL.

### <a name="mamcompliancemanager"></a>MAMComplianceManager
A interface `MAMComplianceManager` é usada quando o erro de política necessária é recebido da ADAL.  Ele contém o método `remediateCompliance()` que deve ser chamado para tentar colocar o aplicativo em um estado compatível. Uma referência ao `MAMComplianceManager` pode ser obtida da seguinte maneira:

```java
MAMComplianceManager mgr = MAMComponents.get(MAMComplianceManager.class);

// make use of mgr
```

A instância `MAMComplianceManager` retornada é garantida para não ser nula.

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
Se o aplicativo se registrar para notificações do tipo **COMPLIANCE_STATUS**, um `MAMComplianceNotification` será enviado para informar o aplicativo do status final da tentativa de correção de conformidade. O `MAMComplianceNotification` será recebido por meio da interface `MAMNotificationReceiver`, conforme descrito na seção [registrar-se para notificações do SDK](#register-for-notifications-from-the-sdk) .

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
| PENDENTE | Falha na tentativa de corrigir a conformidade porque a resposta de status ainda não foi recebida do serviço quando o limite de tempo foi excedido. O aplicativo deve tentar sua aquisição de token novamente mais tarde. |
| COMPANY_PORTAL_REQUIRED | O Portal da Empresa deve ser instalado no dispositivo para que a correção de conformidade tenha sucesso.  Se o Portal da Empresa já estiver instalado no dispositivo, o aplicativo precisará ser reiniciado.  Nesse caso, será exibida uma caixa de diálogo solicitando que o usuário reinicie o aplicativo. |

Se o status de conformidade for `MAMCAComplianceStatus.COMPLIANT`, o aplicativo deverá reinicializar sua aquisição de token original (para seu próprio recurso). Se a tentativa de correção de conformidade falhar, os métodos `getComplianceErrorTitle()` e `getComplianceErrorMessage()` retornarão cadeias de caracteres localizadas que o aplicativo pode exibir para o usuário final se escolher.  A maioria dos casos de erro não é remediable pelo aplicativo, portanto, para o caso geral, pode ser melhor falhar na criação ou no logon da conta e permitir que o usuário tente novamente mais tarde.  Se uma falha for persistente, os logs de MAM poderão ajudar a determinar a causa.  O usuário final pode enviar os logs usando as instruções encontradas [aqui](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android "Enviar logs por email para o suporte de sua empresa").

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

## <a name="protecting-backup-data"></a>Protegendo dados de backup
A partir do Android marshmallow (API 23), o Android tem duas maneiras de um aplicativo fazer backup de seus dados. Cada opção está disponível para seu aplicativo e requer etapas diferentes para garantir que a proteção de dados do Intune seja implementada corretamente. Você pode examinar a tabela abaixo nas ações correspondentes necessárias para o comportamento correto de proteção de dados.  Você pode ler mais sobre os métodos de backup no [guia da API do Android](https://developer.android.com/guide/topics/data/backup.html).

### <a name="auto-backup-for-apps"></a>Backup automático para aplicativos
O Android começou a oferecer [backups completos automáticos](https://developer.android.com/guide/topics/data/autobackup.html) para o Google Drive para aplicativos em dispositivos Android marshmallow, independentemente da API de destino do aplicativo. No AndroidManifest. xml, se você definir explicitamente `android:allowBackup` como **false**, seu aplicativo nunca será colocado em fila para backups pelo Android e dados "corporativos" permanecerão dentro do aplicativo. Nesse caso, nenhuma ação adicional é necessária.

No entanto, por padrão, o atributo `android:allowBackup` é definido como true, mesmo que `android:allowBackup` não seja especificado no arquivo de manifesto. Isso significa que todos os dados do aplicativo são submetidos a backup automaticamente na conta do Google Drive do usuário, um comportamento padrão que representa um **risco de perda de dados**. Portanto, o SDK requer as alterações descritas abaixo para garantir que a proteção de dados seja aplicada.  É importante seguir as diretrizes abaixo para proteger os dados do cliente corretamente se você quiser que seu aplicativo seja executado em dispositivos Android marshmallow.  

O Intune permite que você utilize todos os [recursos de backup automático](https://developer.android.com/guide/topics/data/autobackup.html) disponíveis no Android, incluindo a capacidade de definir regras personalizadas em XML, mas você deve seguir as etapas abaixo para proteger seus dados:

1. Se seu aplicativo não **usar seu** próprio BackupAgent personalizado, use o MAMBackupAgent padrão para permitir backups completos automáticos que são compatíveis com a política do Intune. Coloque o seguinte no manifesto do aplicativo:

    ```xml
    android:fullBackupOnly="true"
    android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```
    
2. **[Opcional]** Se você implementou um BackupAgent personalizado opcional, precisará se certificar de usar MAMBackupAgent ou MAMBackupAgentHelper. Consulte as seções a seguir. Considere a possibilidade de alternar para o uso do **MAMDefaultFullBackupAgent** do Intune (descrito na etapa 1), que fornece backup fácil no Android M e superior.

3. Ao decidir qual tipo de backup completo seu aplicativo deve receber (não filtrado, filtro ou nenhum), você precisará definir o atributo `android:fullBackupContent` como true, false ou um recurso XML em seu aplicativo.

4. Em seguida, você _**deve**_ copiar tudo o que você colocar em `android:fullBackupContent` em uma marca de metadados denominada `com.microsoft.intune.mam.FullBackupContent` no manifesto.

    **Exemplo 1**: se você quiser que seu aplicativo tenha backups completos sem exclusões, defina o atributo `android:fullBackupContent` e a marca de metadados `com.microsoft.intune.mam.FullBackupContent` como **true**:

    ```xml
    android:fullBackupContent="true"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />  
    ```

    **Exemplo 2**: se você quiser que seu aplicativo use seu BackupAgent personalizado e recusar a todos os backups automáticos em conformidade com a política do Intune, você deve definir o atributo e a marca de metadados como **false**:

    ```xml
    android:fullBackupContent="false"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="false" />  
    ```

    **Exemplo 3**: se você quiser que seu aplicativo tenha backups completos de acordo com suas regras personalizadas definidas em um arquivo XML, defina o atributo e a marca de metadados para o mesmo recurso XML:

    ```xml
    android:fullBackupContent="@xml/my_scheme"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```

### <a name="keyvalue-backup"></a>Backup de chave/valor
A opção [backup de chave/valor](https://developer.android.com/guide/topics/data/keyvaluebackup.html) está disponível para todas as APIs 8 + e carrega dados de aplicativo para o [serviço de backup do Android](https://developer.android.com/google/backup/index.html). A quantidade de dados por usuário do seu aplicativo é limitada a 5 MB. Se você usar o backup de chave/valor, deverá usar um **BackupAgentHelper** ou um **BackupAgent**.

### <a name="backupagenthelper"></a>BackupAgentHelper
O BackupAgentHelper é mais fácil de implementar do que o BackupAgent em termos de funcionalidade nativa do Android e da integração de MAM do Intune. O BackupAgentHelper permite que o desenvolvedor Registre arquivos inteiros e preferências compartilhadas em um **FileBackupHelper** e **SharedPreferencesBackupHelper** (respectivamente) que são adicionados ao BackupAgentHelper na criação. Siga as etapas abaixo para usar um BackupAgentHelper com o MAM do Intune:

1. Para utilizar o backup de várias identidades com um BackupAgentHelper, siga o guia do Android para [estender o BackupAgentHelper](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgentHelper).

2. Faça sua classe estender o equivalente de MAM de BackupAgentHelper, FileBackupHelper e SharedPreferencesBackupHelper.

|Classe do Android | Equivalente a MAM |
|--|--|
|BackupAgentHelper |MAMBackupAgentHelper |
|FileBackupHelper | MAMFileBackupHelper
|SharedPreferencesBackupHelper| MAMSharedPreferencesBackupHelper|

Seguir essas diretrizes levará a um backup e restauração com várias identidades bem-sucedidas.

### <a name="backupagent"></a>BackupAgent

Um BackupAgent permite que você seja muito mais explícito sobre quais dados são copiados em backup. Como o desenvolvedor é razoavelmente responsável pela implementação, há mais etapas necessárias para garantir a proteção de dados apropriada do Intune. Como a maior parte do trabalho é enviada para você, o desenvolvedor, integração com o Intune, é um pouco mais envolvida.

**Integrar MAM:**

1. Leia atentamente o guia do Android para [backup de chave/valor](https://developer.android.com/guide/topics/data/keyvaluebackup.html) e [estendendo](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) especificamente o BackupAgent para garantir que sua implementação de BackupAgent siga as diretrizes do Android.

2. Faça com que sua classe estenda `MAMBackupAgent`.

**Backup de várias identidades:**

1. Antes de iniciar o backup, verifique se os arquivos ou os buffers de dados que você planeja fazer backup são realmente **permitidos pelo administrador de ti para fazer** backup em cenários de várias identidades. Fornecemos a função `isBackupAllowed` em `MAMFileProtectionManager` e `MAMDataProtectionManager` para determinar isso. Se não for permitido fazer backup do arquivo ou do buffer de dados, você não deverá continuar a incluí-lo em seu backup.

2. Em algum momento durante o backup, se você quiser fazer backup das identidades dos arquivos que você verificou na etapa 1, deverá chamar `backupMAMFileIdentity(BackupDataOutput data, File … files)` com os arquivos dos quais planeja extrair os dados. Isso criará automaticamente novas entidades de backup e as gravará no `BackupDataOutput` para você. Essas entidades serão consumidas automaticamente após a restauração.

**Restauração de várias identidades:**

O guia de backup de dados especifica um algoritmo geral para restaurar os dados do aplicativo e fornece um exemplo de código na seção [estendendo BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) . Para ter uma restauração de várias identidades bem-sucedida, você deve seguir a estrutura geral fornecida neste exemplo de código com atenção especial para o seguinte:

1. Você deve utilizar um loop `while(data.readNextHeader())` para percorrer as entidades de backup. No código anterior, `data` é o nome da variável local para o **MAMBackupDataInput** que é passado para seu aplicativo durante a restauração.

2. Você deve chamar `data.skipEntityData()` se `data.getKey()` não corresponder à chave que você escreveu em `onBackup`. Sem executar essa etapa, suas restaurações podem não ter sucesso. No código anterior, `data` é o nome da variável local para o **MAMBackupDataInput** que é passado para seu aplicativo durante a restauração.

3. Evite retornar enquanto estiver consumindo entidades de backup na construção `while(data.readNextHeader())`, pois as entidades que escrevemos automaticamente serão perdidas. No código anterior, `data` é o nome da variável local para o **MAMBackupDataInput** que é passado para seu aplicativo durante a restauração.

## <a name="multi-identity-optional"></a>Várias identidades (opcional)

### <a name="overview"></a>Visão geral
Por padrão, o SDK do aplicativo do Intune aplicará a política ao aplicativo como um todo. Várias identidades é um recurso opcional de proteção de aplicativo do Intune que pode ser habilitado para permitir que a política seja aplicada em um nível por identidade. Isso requer uma participação de aplicativo significativamente maior do que outros recursos de proteção de aplicativo.

> [!NOTE]
> A falta da participação correta do aplicativo pode resultar em vazamentos de dados e outros problemas de segurança.

Depois que o usuário registrar o dispositivo ou o aplicativo, o SDK registrará essa identidade e a considerará a identidade gerenciada primária do Intune. Outros usuários no aplicativo serão tratados como não gerenciados, com configurações de política irrestritas.

> [!NOTE]
> Atualmente, há suporte apenas para uma identidade gerenciada do Intune por dispositivo.

Uma identidade é definida como uma cadeia de caracteres. As identidades não diferenciam **maiúsculas de minúsculas**e as solicitações para o SDK de uma identidade podem não retornar a mesma maiúsculas e minúsculas usadas originalmente ao definir a identidade.

O aplicativo *deve* informar o SDK quando pretender alterar a identidade ativa. Em alguns casos, o SDK também notificará o aplicativo quando uma alteração de identidade for necessária. Na maioria dos casos, no entanto, o MAM não pode saber quais dados estão sendo exibidos na interface do usuário ou usados em um thread em um determinado momento e se baseia no aplicativo para definir a identidade correta a fim de evitar o vazamento de dados. Nas seções a seguir, alguns cenários específicos que exigem a ação do aplicativo serão chamados.

### <a name="enabling-multi-identity"></a>Habilitando várias identidades
Por padrão, todos os aplicativos são considerados aplicativos de identidade única. Você pode declarar um aplicativo para ter reconhecimento de várias identidades colocando os seguintes metadados em AndroidManifest. xml.

```xml
  <meta-data
    android:name="com.microsoft.intune.mam.MAMMultiIdentity"
    android:value="true" />
```

### <a name="setting-the-identity"></a>Definindo a identidade
Os desenvolvedores podem definir a identidade do usuário do aplicativo nos seguintes níveis em prioridade decrescente:

  1. Nível de thread
  2. nível `Context` (geralmente `Activity`)
  3. Nível de processo

Uma identidade definida no nível de thread substitui uma identidade definida no nível `Context`, que substitui uma identidade definida no nível do processo. Uma identidade definida em um `Context` é usada somente em cenários associados apropriados. As operações de e/s de arquivo, por exemplo, não têm um `Context` associado. Normalmente, os aplicativos definirão a identidade `Context` em um `Activity`. Um aplicativo não *deve* exibir dados para uma identidade gerenciada, a menos que a identidade `Activity` seja definida com a mesma identidade. Em geral, a identidade de nível de processo só será útil se o aplicativo funcionar apenas com um único usuário por vez em todos os threads. Muitos aplicativos podem não precisar usá-lo.

Se seu aplicativo usa o contexto `Application` para adquirir serviços do sistema, verifique se a identidade do processo ou thread foi definida ou se você definiu a identidade da interface do usuário no contexto `Application` do seu aplicativo.

Para lidar com casos especiais ao atualizar a identidade da interface do usuário com `setUIPolicyIdentity` ou `switchMAMIdentity`, ambos os métodos podem ser passados como um conjunto de valores `IdentitySwitchOption`.

* `IGNORE_INTENT`: use se estiver solicitando uma opção de identidade que deve ignorar a intenção associada à atividade atual.
  Por exemplo:

  1. Seu aplicativo recebe uma intenção de uma identidade gerenciada que contém um documento gerenciado e seu aplicativo exibe o documento.
  2. O usuário alterna para sua identidade pessoal, para que seu aplicativo solicite uma opção de identidade de interface do usuário. Na identidade pessoal, seu aplicativo não está mais exibindo o documento, portanto, você usa `IGNORE_INTENT` ao solicitar a troca de identidade.

  Se não estiver definido, o SDK assumirá que a intenção mais recente ainda está sendo usada no aplicativo. Isso fará com que a política de recebimento para a nova identidade trate a intenção como dados de entrada e use sua identidade.

>[!NOTE]
> Como o `CLIPBOARD_SERVICE` é usado para operações de interface do usuário, o SDK usa a identidade da interface do usuário da atividade de primeiro plano para operações `ClipboardManager`.
> Os métodos a seguir no `MAMPolicyManager` podem ser usados para definir a identidade e recuperar os valores de identidade definidos anteriormente.

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
> Você pode limpar a identidade do aplicativo definindo-o como nulo.
>
> A cadeia de caracteres vazia pode ser usada como uma identidade que nunca terá a política de proteção do aplicativo.

#### <a name="results"></a>Resultados
Todos os métodos usados para definir o relatório de identidade retornam valores de resultado via `MAMIdentitySwitchResult`. Há quatro valores que podem ser retornados:

| Valor de retorno | Cenário |
|--            |--        |
| `SUCCEEDED`    | A alteração de identidade foi bem-sucedida. |
| `NOT_ALLOWED`  | A alteração de identidade não é permitida. Isso ocorre se for feita uma tentativa de definir a identidade da interface do usuário (`Context`) quando uma identidade diferente for definida no thread atual. |
| `CANCELLED`    | O usuário cancelou a alteração de identidade, geralmente pressionando o botão voltar em um prompt de PIN ou de autenticação. |
| `FAILED`       | A alteração de identidade falhou por um motivo não especificado.|

O aplicativo deve garantir que uma troca de identidade seja bem-sucedida antes de exibir ou usar dados corporativos. Atualmente, os comutadores de identidade de processo e thread sempre terão êxito para um aplicativo habilitado para várias identidades, no entanto, reservamos o direito de adicionar condições de falha. A opção de identidade da interface do usuário pode falhar por argumentos inválidos, se entrar em conflito com a identidade do thread, ou se o usuário cancelar os requisitos de inicialização condicional (por exemplo, pressionar o botão voltar na tela do PIN). O comportamento padrão para uma opção de identidade de interface do usuário com falha em uma atividade é concluir a atividade (consulte `onSwitchMAMIdentityComplete` abaixo).

No caso da definição de uma identidade `Context` via `setUIPolicyIdentity`, o resultado é relatado de forma assíncrona. Se o `Context` for um `Activity`, o SDK não saberá se a alteração de identidade foi bem-sucedida até que a inicialização condicional seja executada, o que pode exigir que o usuário insira um PIN ou credenciais corporativas. O aplicativo pode implementar um `MAMSetUIIdentityCallback` para receber esse resultado ou pode passar NULL para o objeto de retorno de chamada. Observe que, se uma chamada for feita para `setUIPolicyIdentity`, embora o resultado de uma chamada anterior para `setUIPolicyIdentity` *no mesmo contexto* ainda não tenha sido entregue, o novo retorno de chamada substituirá o antigo e o retorno de chamada original nunca receberá um resultado.

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

Você também pode definir a identidade de uma atividade diretamente por meio de um método em `MAMActivity` em vez de chamar `MAMPolicyManager.setUIPolicyIdentity`. Use o método a seguir para fazer isso:

```java
     public final void switchMAMIdentity(final String newIdentity, final EnumSet<IdentitySwitchOption> options);
```

Você também pode substituir um método em `MAMActivity` se desejar que o aplicativo seja notificado do resultado de tentativas de alterar a identidade dessa atividade.

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

Se você não substituir `onSwitchMAMIdentityComplete` (ou chamar o método `super`), uma mudança de identidade com falha em uma atividade fará com que a atividade seja concluída. Se você substituir o método, deverá cuidar de que os dados corporativos não são exibidos após uma mudança de identidade com falha.

>[!NOTE]
> A alternância da identidade pode exigir a recriação da atividade. Nesse caso, o retorno de chamada `onSwitchMAMIdentityComplete` será entregue à nova instância da atividade.


### <a name="implicit-identity-changes"></a>Alterações de identidade implícitas
Além da capacidade do aplicativo de definir a identidade, um thread ou uma identidade de contexto pode mudar com base na entrada de dados de outro aplicativo gerenciado pelo Intune que tem a política de proteção do aplicativo.

#### <a name="examples"></a>Exemplos
1. Se uma atividade for iniciada de um `Intent` enviado por outro aplicativo de MAM, a identidade da atividade será definida com base na identidade efetiva no outro aplicativo no ponto em que o `Intent` foi enviado.

2. Para serviços, a identidade do thread será definida de forma semelhante à duração de uma chamada `onStart` ou `onBind`. Chamadas para o `Binder` retornado de `onBind` também definirão temporariamente a identidade do thread.

3. Chamadas em um `ContentProvider`, de maneira semelhante, definirão a identidade do thread para sua duração.


    Além disso, a interação do usuário com uma atividade pode causar uma troca de identidade implícita.

    **Exemplo:** Um usuário Cancelando um prompt de autorização durante o `Resume` resultará em um comutador implícito para uma identidade vazia.

    O aplicativo recebe uma oportunidade de ser informado sobre essas alterações e, se necessário, o aplicativo pode proibi-las. `MAMService` e `MAMContentProvider` expõem o seguinte método que as subclasses podem substituir:

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

    * O `AppIdentitySwitchReason` captura a origem do comutador implícito e pode aceitar os valores `CREATE`, `RESUME_CANCELLED` e `NEW_INTENT`.  O motivo `RESUME_CANCELLED` é usado quando a atividade retomar faz com que o PIN, a autenticação ou outra interface de usuário de conformidade seja exibida e o usuário tente cancelar a interface do usuário, geralmente, embora use o botão voltar.


    * O `AppIdentitySwitchResultCallback` é o seguinte:

      ```java
      public interface AppIdentitySwitchResultCallback {
          /**
            * @param result
            *            whether the identity switch can proceed.
            */
          void reportIdentitySwitchResult(AppIdentitySwitchResult result);
        }
        ```

      Onde ```AppIdentitySwitchResult``` é `SUCCESS` ou `FAILURE`.

O método `onMAMIdentitySwitchRequired` é chamado para todas as alterações de identidade implícitas, exceto aquelas feitas por meio de um associador retornado de `MAMService.onMAMBind`. As implementações padrão de `onMAMIdentitySwitchRequired` chamam imediatamente:

* `reportIdentitySwitchResult(FAILURE)` quando o motivo é `RESUME_CANCELLED`.

* `reportIdentitySwitchResult(SUCCESS)` em todos os outros casos.

  Não se espera que a maioria dos aplicativos precise bloquear ou atrasar uma mudança de identidade de maneira diferente, mas se um aplicativo precisar fazer isso, os seguintes pontos deverão ser considerados:

  * Se uma opção de identidade for bloqueada, o resultado será o mesmo que se `Receive` as configurações de compartilhamento tivessem proibido a entrada de dados.

  * Se um serviço estiver em execução no thread principal, `reportIdentitySwitchResult` **deverá** ser chamado de forma síncrona ou o thread da interface do usuário será interrompido.

  * Para a criação de **`Activity`** , `onMAMIdentitySwitchRequired` será chamado antes de `onMAMCreate`. Se o aplicativo precisar mostrar a interface do usuário para determinar se deseja permitir a alternância de identidade, essa interface do usuário deverá ser mostrada usando uma atividade *diferente* .

  * Em um **`Activity`** , quando uma mudança para a identidade vazia é solicitada com o motivo como `RESUME_CANCELLED`, o aplicativo deve modificar a atividade retomada para exibir dados consistentes com essa opção de identidade.  Se isso não for possível, o aplicativo deverá recusar a opção, e o usuário será solicitado novamente a cumprir a política para retomar a identidade (por exemplo, apresentando a tela de entrada do PIN do aplicativo).

    > [!NOTE]
    > Um aplicativo com várias identidades sempre receberá dados de entrada de aplicativos gerenciados e não gerenciados. É responsabilidade do aplicativo tratar dados de identidades gerenciadas de maneira gerenciada.

  Se uma identidade solicitada for gerenciada (use `MAMPolicyManager.getIsIdentityManaged` para verificar), mas o aplicativo não for capaz de usar essa conta (por exemplo, porque contas, como contas de email, devem ser configuradas no aplicativo primeiro), a opção de identidade deverá ser recusada.

#### <a name="build-plugin--tool-considerations"></a>Considerações de plug-in/ferramenta de Build
Se você não herdar explicitamente de `MAMActivity`, `MAMService` ou `MAMContentProvider` (porque permite que as ferramentas de compilação façam essa alteração), mas ainda precisa processar os comutadores de identidade, em vez disso, você pode implementar `MAMActivityIdentityRequirementListener` (para um `Activity`) ou `MAMIdentityRequirementListener` (para `Service` ou `ContentProviders`) .
O comportamento padrão para `MAMActivity.onMAMIdentitySwitchRequired` pode ser acessado chamando o método estático `MAMActivity.defaultOnMAMIdentitySwitchRequired(activity, identity,
reason, callback)`.

Da mesma forma, se você precisar substituir `MAMActivity.onSwitchMAMIdentityComplete`, poderá implementar `MAMActivityIdentitySwitchListener` sem herdar explicitamente de `MAMActivity`.

### <a name="preserving-identity-in-async-operations"></a>Preservando a identidade em operações assíncronas
É comum que as operações no thread da interface do usuário expeçam tarefas em segundo plano para outro thread. Um aplicativo de várias identidades desejará garantir que essas tarefas em segundo plano operem com a identidade apropriada, que geralmente é a mesma identidade usada pela atividade que as Expedia. O SDK do MAM fornece `MAMAsyncTask` e `MAMIdentityExecutors` como uma conveniência para ajudar a preservar a identidade.
Eles devem ser usados se a operação assíncrona puder gravar dados corporativos em um arquivo ou se se comunicar com outros aplicativos.

#### <a name="mamasynctask"></a>MAMAsyncTask
Para usar `MAMAsyncTask`, simplesmente herde dele em vez de `AsyncTask` e substitua as substituições de `doInBackground` e `onPreExecute` por `doInBackgroundMAM` e `onPreExecuteMAM`, respectivamente. O Construtor `MAMAsyncTask` usa um contexto de atividade. Por exemplo:

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
`MAMIdentityExecutors` permite encapsular uma instância existente `Executor` ou `ExecutorService` como uma preservação de identidade `Executor` @ no__t-4 @ no__t-5 com os métodos `wrapExecutor` e `wrapExecutorService`. Por exemplo

```java
  Executor wrappedExecutor = MAMIdentityExecutors.wrapExecutor(originalExecutor, activity);
  ExecutorService wrappedService = MAMIdentityExecutors.wrapExecutorService(originalExecutorService, activity);
```

### <a name="file-protection"></a>Proteção de arquivo
Cada arquivo tem uma identidade associada a ele no momento da criação, com base na identidade do processo e thread. Essa identidade será usada para a criptografia de arquivo e o apagamento seletivo. Somente arquivos cuja identidade é gerenciada e têm a política que exige criptografia serão criptografados. O apagamento de funcionalidade seletiva padrão do SDK apagará apenas os arquivos associados à identidade gerenciada para a qual um apagamento foi solicitado. O aplicativo pode consultar ou alterar a identidade de um arquivo usando a classe `MAMFileProtectionManager`.

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

#### <a name="app-responsibility"></a>Responsabilidade do aplicativo
O MAM não pode inferir automaticamente uma relação entre arquivos que estão sendo lidos e dados sendo exibidos em um `Activity`. Os aplicativos *devem* definir a identidade da interface do usuário adequadamente antes de exibir dados corporativos. Isso inclui dados lidos de arquivos. Se um arquivo vier de fora do aplicativo (de um `ContentProvider` ou lido em um local publicamente gravável), o aplicativo *deverá* tentar determinar a identidade do arquivo (usando `MAMFileProtectionManager.getProtectionInfo`) antes de exibir as informações lidas do arquivo. Se `getProtectionInfo` reportar uma identidade não nula e não vazia, a identidade da interface do usuário *deverá* ser definida para corresponder a essa identidade (usando `MAMActivity.switchMAMIdentity` ou `MAMPolicyManager.setUIPolicyIdentity`). Se a alternância de identidade falhar, os dados do arquivo *não deverão* ser exibidos.

Um fluxo de exemplo pode ser semelhante ao seguinte:
* O usuário seleciona um documento para abrir no aplicativo.
  * Durante o fluxo aberto, antes de ler dados do disco, o aplicativo confirma a identidade que deve ser usada para exibir o conteúdo:

    ```java
    MAMFileProtectionInfo info = MAMFileProtectionManager.getProtectionInfo(docPath)
    if (info != null)
        MAMPolicyManager.setUIPolicyIdentity(activity, info.getIdentity(), callback, EnumSet.noneOf<IdentitySwitchOption.class>)
    ```

  * O aplicativo aguarda até que um resultado seja relatado para o retorno de chamada.
  * Se o resultado relatado for uma falha, o aplicativo não exibirá o documento.
* O aplicativo abre e renderiza o arquivo.
  
#### <a name="single-identity-to-multi-identity-transition"></a>Única identidade para transição de várias identidades
Se um aplicativo que foi lançado anteriormente com a integração do Intune de identidade única mais tarde integrar várias identidades, os aplicativos instalados anteriormente passarão por uma transição (não visível para o usuário, não há nenhuma UX associada). O aplicativo não *precisa* fazer nada explícito para lidar com essa transição. Todos os arquivos criados antes da transição continuarão sendo considerados gerenciados (portanto, permanecerão criptografados se a política de criptografia estiver ativada). Se desejar, você pode detectar a atualização e usar `MAMFileProtectionManager.protect` para marcar arquivos ou diretórios específicos com a identidade vazia (o que removerá a criptografia se elas foram criptografadas).

#### <a name="offline-scenarios"></a>Cenários offline
A marcação de identidade do arquivo é sensível ao modo offline. Os seguintes pontos devem ser levados em conta:

* Se o Portal da Empresa não estiver instalado, os arquivos não poderão ser marcados com identidade.

* Se o Portal da Empresa estiver instalado, mas o aplicativo não tiver a política de MAM do Intune, os arquivos não poderão ser marcados de forma confiável com a identidade.

* Quando a marcação de identidade do arquivo se torna disponível, todos os arquivos criados anteriormente são tratados como pessoais/não gerenciados (que pertencem à identidade de cadeia de caracteres vazia), a menos que o aplicativo tenha sido instalado anteriormente como um aplicativo gerenciado de identidade única, caso em que eles são tratados como pertencente ao usuário registrado.

### <a name="directory-protection"></a>Proteção de diretório
Os diretórios podem ser protegidos usando o mesmo método `protect` usado para proteger arquivos. A proteção de diretório aplica-se recursivamente a todos os arquivos e subdiretórios contidos no diretório e a novos arquivos criados dentro do diretório. Como a proteção de diretório é aplicada recursivamente, a chamada `protect` pode levar algum tempo para ser concluída para diretórios grandes. Por esse motivo, os aplicativos que aplicam proteção a um diretório que contém um grande número de arquivos podem querer executar `protect` de forma assíncrona em um thread em segundo plano.

### <a name="data-protection"></a>Data Protection
Não é possível marcar um arquivo como pertencente a várias identidades. Os aplicativos que devem armazenar dados pertencentes a diferentes usuários no mesmo arquivo podem fazer isso manualmente, usando os recursos fornecidos pelo `MAMDataProtectionManager`. Isso permite que o aplicativo criptografe os dados e vincule-os a um usuário específico. Os dados criptografados são adequados para armazenar em disco em um arquivo. Você pode consultar os dados associados à identidade e os dados podem ser descriptografados mais tarde.

Os aplicativos que fazem uso de `MAMDataProtectionManager` devem implementar um receptor para a notificação de `MANAGEMENT_REMOVED`. Após a conclusão dessa notificação, os buffers que foram protegidos por meio dessa classe não serão mais legíveis se a criptografia de arquivo tiver sido habilitada quando os buffers foram protegidos. Um aplicativo pode corrigir essa situação chamando `MAMDataProtectionManager.unprotect` em todos os buffers durante essa notificação. Também é seguro chamar a proteção durante essa notificação se for desejado preservar informações de identidade. a criptografia é garantida para ser desabilitada durante a notificação.

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

### <a name="content-providers"></a>Provedores de conteúdo
Se o aplicativo fornecer dados corporativos diferentes de um `ParcelFileDescriptor` por meio de um `ContentProvider`, o aplicativo deverá chamar o método `isProvideContentAllowed(String)` no `MAMContentProvider`, passando o UPN da identidade do proprietário (nome UPN) para o conteúdo. Se essa função retornar false, o conteúdo *não deverá* ser retornado ao chamador. Os descritores de arquivo retornados por meio de um provedor de conteúdo são manipulados automaticamente com base na identidade do arquivo.

Se você não herdar `MAMContentProvider` explicitamente e, em vez disso, permitir que as ferramentas de compilação façam essa alteração, você pode chamar uma versão estática do mesmo método: `MAMContentProvider.isProvideContentAllowed(provider,
contentIdentity)`.

### <a name="selective-wipe"></a>Apagamento seletivo
Se um aplicativo de várias identidades for registrado para a notificação `WIPE_USER_DATA`, será responsabilidade do aplicativo remover todos os dados do usuário que está sendo apagado, incluindo todos os arquivos que tenham sido marcados com identidade como pertencentes a esse usuário. Se o aplicativo remover dados do usuário de um arquivo, mas desejar deixar outros dados no arquivo, ele *deverá* alterar a identidade do arquivo (via `MAMFileProtectionManager.protect` para um usuário pessoal ou a identidade vazia). Se a política de criptografia estiver em uso, todos os arquivos restantes que pertencem ao usuário que está sendo apagado não serão descriptografados e ficarão inacessíveis para o aplicativo após o apagamento.

Um registro de aplicativo para `WIPE_USER_DATA` não receberá o benefício do comportamento de apagamento seletivo padrão do SDK. Para aplicativos com reconhecimento de várias identidades, essa perda pode ser mais significativa, uma vez que o apagamento seletivo padrão de MAM apagará apenas os arquivos cuja identidade é destinada por um apagamento. Se um aplicativo com reconhecimento de várias identidades quiser que o apagamento seletivo padrão de MAM seja feito _**e**_ desejar executar suas próprias ações no apagamento, ele deverá se registrar para notificações `WIPE_USER_AUXILIARY_DATA`. Essa notificação será enviada imediatamente pelo SDK antes de executar o apagamento seletivo padrão de MAM. Um aplicativo nunca deve se registrar para `WIPE_USER_DATA` e `WIPE_USER_AUXILIARY_DATA`.

O apagamento seletivo padrão fechará o aplicativo normalmente, concluindo as atividades e eliminando o processo do aplicativo. Se seu aplicativo substituir o apagamento seletivo padrão, convém considerar fechar seu aplicativo manualmente para impedir que o usuário acesse dados na memória após a ocorrência de um apagamento.

## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>Habilitando a configuração direcionada para o MAM para seus aplicativos Android (opcional)
Pares chave-valor específicos do aplicativo podem ser configurados no console do Intune para [Mam-nós](https://docs.microsoft.com/intune/app-configuration-policies-managed-app) e [Android Enterprise](https://docs.microsoft.com/intune/app-configuration-policies-use-android).
Esses pares chave-valor não são interpretados pelo Intune, mas são passados para o aplicativo. Os aplicativos que desejam receber essa configuração podem usar as classes `MAMAppConfigManager` e `MAMAppConfig` para fazer isso. Se várias políticas forem direcionadas ao mesmo aplicativo, pode haver vários valores conflitantes disponíveis para a mesma chave.

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

### <a name="conflicts"></a>Conflitos
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
A configuração do aplicativo adiciona um novo tipo de notificação:
* **REFRESH_APP_CONFIG**: essa notificação é enviada em um `MAMUserNotification` e informa ao aplicativo que novos dados de configuração de aplicativo estão disponíveis.

### <a name="further-reading"></a>Leitura adicional
Para obter mais informações sobre como criar uma política de configuração de aplicativo direcionada para MAM no Android, consulte a seção sobre configuração de aplicativo direcionado para MAM em [como usar Microsoft Intune políticas de configuração de aplicativo para Android](https://docs.microsoft.com/intune/app-configuration-policies-managed-app).

A configuração do aplicativo também pode ser configurada usando o API do Graph. Para obter informações, consulte a [configuração direcionada API do Graph docs for Mam](https://docs.microsoft.com/graph/api/resources/intune-mam-targetedmanagedappconfiguration).

## <a name="style-customization-optional"></a>Personalização de estilo (opcional)
As exibições geradas pelo SDK do MAM podem ser personalizadas visualmente para corresponder melhor ao aplicativo no qual ele está integrado. Você pode personalizar as cores primárias, secundárias e de segundo plano, bem como o tamanho do logotipo do aplicativo. Essa personalização de estilo é opcional e os padrões serão usados se nenhum estilo personalizado estiver configurado.

### <a name="how-to-customize"></a>Como personalizar
Para que as alterações de estilo se apliquem às exibições de MAM do Intune, você deve primeiro criar um arquivo XML de substituição de estilo. Esse arquivo deve ser colocado no diretório "/res/XML" do seu aplicativo e você pode nomeá-lo como desejar. Abaixo está um exemplo do formato que esse arquivo precisa seguir.

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

Você deve reutilizar os recursos que já existem em seu aplicativo. Por exemplo, você deve definir a cor verde no arquivo Colors. xml e referenciá-la aqui. Você não pode usar o código de cor hex "#0000ff". O tamanho máximo do logotipo do aplicativo é 110 DIP (DP). Você pode usar uma imagem de logotipo menor, mas obedecer ao tamanho máximo gerará os melhores resultados. Se você exceder o limite de DIP de 110, a imagem será reduzida e possivelmente causará o desfoque.

Abaixo está a lista completa de atributos de estilo permitidos, os elementos da interface do usuário que eles controlam, seus nomes de item de atributo XML e o tipo de recurso esperado para cada um.

|Atributo de estilo | Elementos da interface do usuário afetados | Nome do item de atributo | Tipo de recurso esperado |
| -- | -- | -- | -- |
| Cor do plano de fundo | Cor do plano de fundo da tela do PIN <Br>Cor de preenchimento da caixa de PIN | background_color | Cor |
| Cor do primeiro plano | Cor do texto em primeiro plano <br> FIXAR borda da caixa no estado padrão <br> Caracteres (incluindo caracteres ofuscados) na caixa de PIN quando o usuário insere um PIN| foreground_color | Cor|
| Cor de destaque | FIXAR borda da caixa quando realçado <br> Hiperlinks |accent_color | Cor |
| Logotipo do aplicativo | Ícone grande que aparece na tela de PIN do aplicativo do Intune | logo_image | Desenháveis |

## <a name="default-enrollment-optional"></a>Registro padrão (opcional)
Veja a seguir as diretrizes para exigir o prompt do usuário na inicialização do aplicativo para um registro de serviço APP-WE automático (chamamos esse **registro padrão** nesta seção), exigindo políticas de proteção de aplicativo do Intune para permitir que somente usuários protegidos pelo Intune usem seu Aplicativo de LOB Android integrado ao SDK. Ele também aborda como habilitar o SSO para seu aplicativo de LOB Android integrado ao SDK. Isso **não** tem suporte para aplicativos da loja que podem ser usados por usuários que não são do Intune.

> [!NOTE] 
> Os benefícios do **registro padrão** incluem um método simplificado para obter a política do serviço app-We para um aplicativo no dispositivo.

> [!NOTE] 
> O **registro padrão** tem reconhecimento de nuvem soberanas.

Habilite o registro padrão com as seguintes etapas:

1. Se seu aplicativo integrar a ADAL ou você precisar habilitar o SSO, [Configure a Adal](#configure-azure-active-directory-authentication-library-adal) seguindo #2 de [configuração comuns do Adal](#common-adal-configurations) . Caso contrário, você pode ignorar esta etapa.
   
2. Habilite o registro padrão colocando o seguinte valor no manifesto:
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />
   ```
   > [!NOTE] 
   > Essa deve ser a única integração MAM-WE no aplicativo. Se houver outras tentativas de chamar as APIs MAMEnrollmentManager, ocorrerão conflitos.

3. Habilite a política de MAM necessária ao colocar o seguinte valor no manifesto:
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />
   ```
   > [!NOTE] 
   > Isso força o usuário a baixar o Portal da Empresa no dispositivo e concluir o fluxo de registro padrão antes de usar.

## <a name="limitations"></a>Limitações

### <a name="policy-enforcement-limitations"></a>Limitações de imposição de política

* **Usando resolvedores de conteúdo**: a política do Intune "transferir ou receber" pode bloquear ou bloquear parcialmente o uso de um resolvedor de conteúdo para acessar o provedor de conteúdo em outro aplicativo. Isso fará com que os métodos `ContentResolver` retornem nulo ou lance um valor de falha (por exemplo, `openOutputStream` lançará `FileNotFoundException` se estiver bloqueado). O aplicativo pode determinar se uma falha de gravação de dados por meio de um resolvedor de conteúdo foi causada pela política (ou deve ser causada pela política) fazendo a chamada:

    ```java
    MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(contentURI);
    ```

    ou se não houver nenhuma atividade associada:

    ```java
    MAMPolicyManager.getPolicy().getIsSaveToLocationAllowed(contentURI);
    ```

    Nesse segundo caso, os aplicativos com várias identidades devem tomar cuidado para definir a identidade do thread adequadamente (ou passar uma identidade explícita para a chamada `getPolicy`).

### <a name="exported-services"></a>Serviços exportados
O arquivo AndroidManifest. XML incluído no SDK de aplicativo do Intune contém **MAMNotificationReceiverService**, que deve ser um serviço exportado para permitir que o portal da empresa envie notificações para um aplicativo gerenciado. O serviço verifica o chamador para garantir que apenas o Portal da Empresa tenha permissão para enviar notificações.

### <a name="reflection-limitations"></a>Limitações de reflexão
Algumas das classes base de MAM (por exemplo, `MAMActivity`, `MAMDocumentsProvider`) contêm métodos (com base nas classes base Android originais) que usam tipos de parâmetro ou de retorno somente presentes acima de determinados níveis de API. Por esse motivo, talvez nem sempre seja possível usar a reflexão para enumerar todos os métodos de componentes do aplicativo. Essa restrição não está limitada ao MAM, é a mesma restrição que se aplicaria se o próprio aplicativo implementasse esses métodos das classes base do Android.

### <a name="robolectric"></a>Robolectric
Não há suporte para o teste do comportamento do SDK do MAM em Robolectric. Há problemas conhecidos ao executar o SDK do MAM em Robolectric devido a comportamentos presentes em Robolectric que não imitam com precisão aqueles em dispositivos reais ou emuladores.

Se você precisar testar seu aplicativo em Robolectric, a solução alternativa recomendada é mover a lógica de classe do aplicativo para um auxiliar e produzir seu apk de teste de unidade com uma classe de aplicativo que não herda de MAMApplication.

## <a name="expectations-of-the-sdk-consumer"></a>Expectativas do consumidor do SDK
O SDK do Intune mantém o contrato fornecido pela API do Android, embora as condições de falha possam ser disparadas com mais frequência como resultado da imposição de políticas. Essas práticas recomendadas do Android reduzirão a probabilidade de falha:

* SDK do Android funções que podem retornar NULL têm uma maior probabilidade de ser NULL agora.  Para minimizar os problemas, verifique se as verificações nulas estão nos lugares certos.

* Os recursos que podem ser verificados devem ser verificados por meio de suas APIs de substituição de MAM.

* Todas as funções derivadas devem chamar para suas versões de superclasse.

* Evite o uso de qualquer API de forma ambígua. Por exemplo, usar `Activity.startActivityForResult` sem verificar o requestCode causará um comportamento estranho.

## <a name="telemetry"></a>Telemetria

O SDK de aplicativos do Intune para Android não controla a coleta de dados do seu aplicativo. Por padrão, o aplicativo Portal da Empresa registra os dados gerados pelo sistema. Esses dados são enviados para Microsoft Intune. De acordo com a política da Microsoft, não coletamos dados pessoais.

> [!NOTE]
> Se os usuários finais optarem por não enviar esses dados, eles deverão desativar a telemetria em configurações no aplicativo Portal da Empresa. Para saber mais, consulte [desligar a coleta de dados de uso da Microsoft](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android). 

## <a name="recommended-android-best-practices"></a>Práticas recomendadas do Android

* Todos os projetos de biblioteca devem compartilhar o mesmo Android: Package sempre que possível. Isso não falhará de forma esporádica em tempo de execução; Isso é puramente um problema de tempo de compilação. As versões mais recentes do SDK de aplicativos do Intune removerão algumas das redundâncias.

* Use as ferramentas de Build de SDK do Android mais recentes.

* Remover todas as bibliotecas desnecessárias e não utilizadas (por exemplo, Android. support. v4)

## <a name="testing"></a>Testes
Consulte o [Guia de testes](app-sdk-android-testing-guide.md).
