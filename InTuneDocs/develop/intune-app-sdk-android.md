---
title: "Guia para programadores do SDK da Aplicação do Microsoft Intune para Android | Documentos da Microsoft"
description: "O SDK da Aplicação do Microsoft Intune para Android permite incorporar a gestão de aplicações móveis (MAM) do Intune na sua aplicação Android."
keywords: SDK
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 905be6a926dc5bab8e9b1016ba82751ee47313e5
ms.openlocfilehash: 178fbaeb1d3235a81cb4da49b7a955f6999c49a2
ms.lasthandoff: 02/18/2017


---


# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Guia para programadores do SDK da Aplicação do Microsoft Intune para Android

> [!NOTE]
> Pode ser útil ler primeiro a [Descrição geral do SDK da Aplicação do Intune](intune-app-sdk.md), que abrange as funcionalidades atuais do SDK e descreve como preparar a integração em cada plataforma suportada.

O SDK da Aplicação do Microsoft Intune para Android permite incorporar a gestão de aplicações móveis (MAM) do Intune na sua aplicação Android. Uma aplicação preparada para MAM é uma integrada com o SDK da Aplicação do Intune. Esta permite aos administradores de TI implementar políticas na sua aplicação móvel quando o Intune está a gerir a aplicação de forma ativa.

## <a name="whats-in-the-sdk"></a>O que está no SDK

O SDK da Aplicação do Intune para Android é uma biblioteca do Android padrão sem dependências externas. O SDK é constituído por:  

* **Microsoft.Intune.MAM.SDK.jar**: as interfaces necessárias para ativar o MAM e a interoperabilidade com a aplicação Portal da Empresa do Intune. As aplicações têm de especificá-lo como referência da biblioteca do Android.

* **Microsoft.Intune.MAM.SDK.Support.v4.jar**: as interfaces necessárias para ativar o MAM nas aplicações utilizam a biblioteca de suporte v4 do Android. As aplicações que precisam deste suporte têm de referenciar diretamente o ficheiro JAR.

* **Microsoft.Intune.MAM.SDK.Support.v7.jar**: as interfaces necessárias para ativar o MAM nas aplicações que utilizam a biblioteca de suporte v7 do Android. As aplicações que precisam deste suporte têm de referenciar diretamente o ficheiro JAR.

* **Diretório de recursos**: os recursos (como, por exemplo, cadeias) nos quais o SDK depende.

* **Microsoft.Intune.MAM.SDK.aar**: os componentes do SDK, à exceção dos ficheiros JAR Support.V4 e Support.V7. Este ficheiro pode ser utilizado em vez dos componentes individuais se o sistema de compilação suportar ficheiros AAR.

* **AndroidManifest.xml**: os pontos de entrada adicionais e os requisitos da biblioteca.

* **THIRDPARTYNOTICES.TXT**: aviso de atribuição que reconhece código de terceiros e/ou OSS que será compilado na sua aplicação.

## <a name="requirements"></a>Requisitos

O SDK da Aplicação do Intune é um projeto Android compilado. Como resultado, é amplamente não afetado pela versão do Android que a aplicação utiliza nas respetivas versões de API mínimas ou de destino. O SDK suporta a API Android 14 (Android 4.0+) para Android API 24.

O SDK da Aplicação do Intune para Android baseia-se na presença da aplicação [Portal da Empresa](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) no dispositivo para ativar políticas de MAM. Para MAM sem inscrição de dispositivos, o utilizador *não* é obrigado a inscrever o dispositivo através da aplicação Portal da Empresa.


## <a name="how-the-intune-app-sdk-works"></a>Como funciona o SDK da Aplicação do Intune

###<a name="entry-points"></a>Pontos de entrada

Para ativar políticas de gestão de aplicações do Intune, o SDK da Aplicação do Intune requer alterações ao código fonte da aplicação. Estas alterações são feitas através da substituição das classes base do Android por classes base do Intune equivalentes, cujos nomes têm o prefixo `MAM`. As classes do SDK estão entre a classe base Android e a própria versão derivada da aplicação dessa classe. Com uma atividade como exemplo, pode ficar com uma hierarquia de herança semelhante a: `Activity` > `MAMActivity` > `AppSpecificActivity`.

Por exemplo, quando `AppSpecificActivity` interage com o respetivo principal (por exemplo, ao chamar `super.onCreate()`), `MAMActivity` é a superclasse.

Normalmente, as aplicações Android têm um modo único e podem aceder ao sistema através do respetivo objeto [Context](https://developer.android.com/reference/android/content/Context.html). Por sua vez, as aplicações que incorporaram o SDK da Aplicação do Intune têm nós duplos. Estas aplicações continuam a aceder ao sistema através do objeto `Context`. Dependendo da base de `Activity` utilizada, o objeto `Context` será proporcionado pelo Android ou será multiplexado inteligentemente entre uma vista restrita do sistema e o `Context` proporcionado pelo Android.

Quando um [ponto de entrada](https://developer.android.com/guide/components/fundamentals.html) Android foi substituído pelo MAM equivalente, tem de ser utilizada a versão MAM do ciclo de vida do ponto de entrada (à exceção da classe `MAMApplication`).

Por exemplo, quando executar a derivação de `MAMActivity`, em vez de substituir `onCreate` e chamar `super.onCreate`, `Activity` tem de substituir `onMAMCreate` e chamar `super.onMAMCreate`. Tal permite ao Intune restringir a iniciação de `Activity` (entre outras) em certos casos.


###<a name="sdk-permissions"></a>Permissões de SDK

O SDK da Aplicação do Intune requer três [permissões do sistema Android](https://developer.android.com/guide/topics/security/permissions.html) em aplicações que o integrem:

* `android.permission.GET_ACCOUNTS` (pedido durante o runtime, se for preciso)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

A Azure Active Directory Authentication Library ([ADAL](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/)) requer estas permissões para executar a autenticação mediada. Se estas permissões não forem concedidas pela aplicação ou forem revogadas pelo utilizador, os fluxos de autenticação que exigirem o mediador (a aplicação Portal da Empresa) serão desativados.


###<a name="company-portal-app"></a>Aplicação Portal da Empresa

Porque é que a aplicação Portal da Empresa é necessária? Quando a aplicação Portal da Empresa for instalada no dispositivo e obtiver uma política de restrição da aplicação para o utilizador do serviço Intune, os pontos de entrada do SDK serão inicializados de forma assíncrona. A inicialização é obrigatória apenas quando o Android cria inicialmente o processo. Durante a inicialização, é estabelecida uma ligação à aplicação Portal da Empresa e a política é obtida da aplicação.  

> [!NOTE]
> Se a aplicação Portal da Empresa não estiver presente no dispositivo, o comportamento da aplicação ativada para Intune não irá mudar, sendo igual ao de uma aplicação normal.


## <a name="how-to-integrate-with-the-intune-app-sdk"></a>Como integrar no SDK da Aplicação do Intune

Conforme afirmado anteriormente, o SDK requer alterações ao código fonte da aplicação para ativar políticas de gestão de aplicações. Seguem-se os passos necessários para ativar o MAM na sua aplicação.

### <a name="replace-classes-methods-and-activities-with-their-mam-equivalent-required"></a>Substituir as classes, os métodos e as atividades pelos respetivos MAM equivalentes (obrigatório)

As classes base Android têm de ser substituídas pelos respetivos equivalentes MAM. Para fazê-lo, localize todas as instâncias das classes apresentadas na tabela seguinte e substitua-as pelo SDK da Aplicação do Intune equivalente.

| Classe base Android | Substituição do SDK da Aplicação do Intune |
|--|--|
| android.app.Activity | MAMActivity |
| android.app.ActivityGroup | MAMActivityGroup |
| android.app.AliasActivity | MAMAliasActivity |
| android.app.Application | MAMApplication |
| android.app.DialogFragment | MAMDialogFragment |
| android.app.ExpandableListActivity | MAMExpandableListActivity |
| android.app.Fragment | MAMFragment |
| android.app.IntentService | MAMIntentService |
| android.app.LauncherActivity | MAMLauncherActivity |
| android.app.ListActivity | MAMListActivity |
| android.app.NativeActivity | MAMNativeActivity |
| android.app.PendingIntent | MAMPendingIntent* |
| android.app.Service | MAMService |
| android.app.TabActivity | MAMTabActivity |
| android.app.TaskStackBuilder | MAMTaskStackBuilder |
| android.app.backup.BackupAgent | MAMBackupAgent |
| android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
| android.app.backup.FileBackupHelper | MAMFileBackupHelper |
| android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| android.content.BroadcastReceiver | MAMBroadcastReceiver |
| android.content.ContentProvider | MAMContentProvider |
| android.os.Binder | MAMBinder (necessário apenas se o Enlaçamento não for gerado a partir de uma interface de Android Interface Definition Language (AIDL)) |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |


**Microsoft.Intune.MAM.SDK.Suppout.v4.jar**:

| MAM do Intune da classe Android | Substituição do SDK da Aplicação do Intune |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider

**Microsoft.Intune.MAM.SDK.Suppout.v7.jar**:

|Classe Android | Substituição do SDK da Aplicação do Intune |
|--|--|
|android.support.v7.app.ActionBarActivity | MAMActionBarActivity |

>[!NOTE]
>Lembre-se: quando um [ponto de entrada](https://developer.android.com/guide/components/fundamentals.html) foi substituído pelo MAM equivalente, tem de ser utilizada a versão MAM do ciclo de vida do ponto de entrada (à exceção da classe `MAMApplication`).
>
>Por exemplo, quando executar a derivação de `MAMActivity`, em vez de substituir `onCreate` e chamar `super.onCreate`, `Activity` tem de substituir `onMAMCreate` e chamar `super.onMAMCreate`. Tal permite ao Intune restringir a iniciação de `Activity` (entre outras) em certos casos.

#### <a name="pendingintent-classes-and-renamed-methods"></a>Classes PendingIntent e métodos renomeados

Depois da deriva de um dos pontos de entrada MAM, é seguro utilizar `Context` como faria normalmente – por exemplo, para iniciar classes `Activity` e utilizar `PackageManager`.  

As classes `PendingIntent` são uma exceção a esta regra. Quando chamar estas classes, terá de alterar o nome da classe. Por exemplo, em vez de `PendingIntent.get*`, tem de utilizar o método `MAMPendingIntent.get*`. Depois disto, pode utilizar o `PendingIntent` resultante como habitualmente.

Em alguns casos, um método disponível na classe Android foi marcado como final na classe de substituição de MAM. Neste caso, a classe de substituição de MAM proporciona um método com um nome semelhante (geralmente, com o sufixo `MAM`), que deve ser substituído. Por exemplo, em vez de substituir `ContentProvider.query`, substituirá `MAMContentProvider.queryMAM`. O compilador de Java deve impor as restrições finais para impedir a substituição acidental do método original em vez do MAM equivalente.

###<a name="enable-features-that-require-app-participation"></a>Ativar funcionalidades que requerem a participação da aplicação

Existem algumas políticas que o SDK não pode implementar por si só. A aplicação pode controlar o respetivo comportamento para cumprir estas funcionalidades através de várias APIs que pode encontrar na seguinte interface `AppPolicy`.

```
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * <strong>This function is now deprecated. Please use {@link #getIsSaveToLocationAllowed(SaveLocation, String)} instead</strong>
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
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between the AAD username and the cloud service username does not exist or the username is not known.
 * @return true if the location can be saved to by the identity, false if otherwise.
 */
boolean getIsSaveToLocationAllowed(SaveLocation service, String username);

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
 * Check if policy allows Contact sync to local contact list.
 *
 * @return True if Contact sync is allowed to save to local contact list; false otherwise.
 */
boolean getIsContactSyncAllowed();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();


}

```

### <a name="enable-it-control-over-app-saving-behavior"></a>Permitir o controlo de TI sobre o comportamento de gravação das aplicações

Muitas aplicações implementam funcionalidades que permitem ao utilizador guardar os ficheiros localmente ou num serviço de armazenamento na cloud. O SDK da Aplicação do Intune ajuda os administradores de TI a aplicar restrições de políticas que considerem mais adequadas na organização, para proteger contra fugas de dados.  Uma das políticas que o administrador de TI pode controlar é se o utilizador pode guardar num arquivo de dados "pessoal" não gerido. Tal inclui guardar numa localização local, num cartão SD ou em serviços de cópias de segurança de terceiros.

A participação da aplicação é necessária para ativar a funcionalidade. Se a aplicação permitir guardar em localizações pessoais ou na cloud diretamente a partir da aplicação, tem de implementar esta funcionalidade para garantir que o administrador de TI possa controlar se a gravação numa localização é permitida.   

Para determinar se a política é imposta, a aplicação pode fazer a seguinte chamada. Esta chamada permite à aplicação saber se a atual política do administrador do Intune permite a gravação num arquivo pessoal. Em seguida, a aplicação pode impor a política porque tem conhecimento do arquivo de dados pessoal disponível para o utilizador através da aplicação.

```
MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();
```

> [!NOTE]
> `MAMComponents.get(AppPolicy.class)` devolverá sempre uma política de aplicação não nula, mesmo se o dispositivo ou aplicação não estiver sob uma política de gestão do Intune.

### <a name="let-the-app-detect-if-a-pin-policy-is-required"></a>Deixar a aplicação detetar se é precisa uma política de PIN

Para algumas restrições de aplicações do Intune, poderá querer que a sua aplicação desative algumas das funcionalidades, de modo a não duplicar funcionalidades no SDK da Aplicação do Intune. Por exemplo, se a aplicação tiver a sua própria experiência de utilizador de PIN, pode querer desativá-la caso o SDK esteja definido para exigir que o utilizador introduza um PIN.

Para determinar se, para o Intune, está definida uma política de PIN que exige um PIN de aplicação ao iniciar, a aplicação pode fazer esta chamada:

```
MAMComponents.get(AppPolicy.class).getIsPinRequired();
```

### <a name="register-for-notifications-from-the-sdk"></a>Registar para obter notificações do SDK  

O SDK da Aplicação do Intune deixa a sua aplicação ter controlo sobre determinadas políticas, como uma eliminação seletiva, quando são implementadas pelo administrador de TI. Quando um administrador de TI implementar uma destas políticas, o serviço do Intune transmite uma notificação para o SDK.

A sua aplicação tem de estar registada para obter notificações do SDK ao criar uma classe `MAMNotificationReceiver` e registando-a em `MAMNotificationReceiverRegistry`. Esta ação é feita ao indicar o recetor e o tipo de notificação desejados em `App.onCreate`, como ilustra este exemplo:

```
@Override
public void onCreate() {
    super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class)
.registerReceiver(
                new ToastNotificationReceiver(),
MAMNotificationType.WIPE_USER_DATA);
    }
```

`MAMNotificationReceiver` recebe simplesmente notificações do serviço do Intune. O SDK processa algumas notificações diretamente. Outras notificações requerem a participação da aplicação.

A aplicação *tem* de devolver verdadeiro ou falso a partir de uma notificação. Deve sempre devolver verdadeiro, a menos que alguma ação que tentou fazer como resultado da notificação tenha falhado. Esta falha pode ser comunicada ao serviço do Intune. Um exemplo de cenário a comunicar é se a aplicação não conseguir eliminar os dados de utilizadores após o administrador de TI iniciar uma eliminação.

É seguro bloquear no `MAMNotificationReceiver.onReceive`, uma vez que a chamada de retorno não está em execução no thread da IU.

A seguinte interface `MAMNotificationReceiver` está definida no SDK:

```
/**
 * The SDK is signaling that a WG event has occurred.
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

###<a name="types-of-notifications"></a>Tipos de notificações

As notificações que se seguem são enviadas para a aplicação. Algumas delas podem precisar da participação da aplicação.

* **`WIPE_USER_DATA`**: esta notificação é enviada numa classe `MAMUserNotification`. Quando esta notificação é recebida, a aplicação deve eliminar todos os dados associados à identidade "empresarial" transmitida com `MAMUserNotification`. Atualmente, esta notificação é enviada durante a anulação da inscrição do serviço do Intune. Geralmente, o nome principal do utilizador é especificado durante o processo de inscrição. Caso se tenha registado para obter esta notificação, a sua aplicação tem de garantir que todos os dados do utilizador foram eliminados. Se não se registar para obtê-la, a aplicação reagirá com o comportamento de eliminação seletiva predefinido.

* **`WIPE_USER_AUXILIARY_DATA`**: as aplicações podem registar-se para obter esta notificação se quiserem utilizar o SDK da Aplicação do Intune para desempenhar o comportamento predefinido de eliminação seletiva, mas ainda quiserem remover alguns dados auxiliares quando ocorrer a eliminação.  

* **`REFRESH_POLICY`**: esta notificação é enviada em `MAMUserNotification`. Quando esta notificação for recebida, qualquer política do Intune em cache tem de ser invalidada e atualizada. O SDK processa geralmente esta tarefa. Mas a aplicação deve processar esta tarefa se for utilizada a política de qualquer forma persistente.



### <a name="protection-of-backup-data"></a>Proteção de dados de cópia de segurança

A partir do Android Marshmallow (API 23), o Android disponibiliza duas formas de as aplicações fazerem cópias de segurança dos dados. Cada opção está disponível para a sua aplicação e requer passos diferentes para garantir que a proteção de dados do Intune é implementada corretamente. Pode ler mais informações sobre os métodos de cópia de segurança no [Guia de API do Android](http://developer.android.com/guide/topics/data/backup.html).

#### <a name="automatic-backup-for-apps"></a>Cópia de segurança automática para aplicações

O Android começou a disponibilizar [cópias de segurança automáticas completas](https://developer.android.com/guide/topics/data/autobackup.html) para aplicações em dispositivos Android Marshmallow, independentemente da API de destino da aplicação. Se definir explicitamente `android:allowBackup` como falso no seu ficheiro AndroidManifest.xml, a sua aplicação nunca será colocada em fila de espera para cópias de segurança pelo Android e os dados "empresariais" permanecerão na aplicação. Neste caso, não são necessárias mais ações.

Por predefinição, o atributo `android:allowBackup` é definido como verdadeiro, mesmo que `android:allowBackup` não seja especificado no ficheiro de manifesto. Isto significa que todos os dados de aplicações são automaticamente colocados em cópia de segurança na conta do Google Drive do utilizador, um comportamento predefinido que constitui um *risco de fuga de dados*. O SDK precisa das alterações descritas para assegurar que a proteção de dados é aplicada. É importante seguir estas orientações para proteger devidamente os dados de clientes, se quiser que a aplicação seja executada em dispositivos Android Marshmallow.  

Se não tiver escrito um agente de cópia de segurança para uma cópia de segurança da aplicação com a utilização de `MAMBackupAgent` ou `MAMBackupAgentHelper`, tem de considerar e controlar como a Cópia de Segurança Automática irá carregar os dados da sua aplicação. O Intune permite-lhe utilizar todas as [funcionalidades de Cópia de Segurança Automática](https://developer.android.com/guide/topics/data/autobackup.html) disponíveis do Android, incluindo a capacidade de definir regras personalizadas em XML. No entanto, tem de seguir estes passos para ajudar a proteger os dados:

1. Utilize o `MAMBackupAgent` predefinido para permitir cópias de segurança automáticas completas que estejam em conformidade com a política do Intune. Coloque `android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"` no seu manifesto da aplicação.

2. Quando decidir que tipo de cópia de segurança completa a sua aplicação deve receber (não filtrada, filtrada ou nenhuma), defina o atributo `android:fullBackupContent` como verdadeiro, falso ou recurso XML na sua aplicação. Copie o que colocar em `android:fullBackupContent` para uma etiqueta de metadados com o nome `com.microsoft.intune.mam.FullBackupContent`.

    Por exemplo: se quiser que a sua aplicação tenha cópias de segurança completas de acordo com as suas regras personalizadas num ficheiro XML, indique um recurso na etiqueta de metadados `com.microsoft.intune.mam.FullBackupContent` no seu manifesto, da seguinte forma:
    ```
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```



#### <a name="keyvalue-backup"></a>Cópia de segurança chave/valor

Esta opção de cópia de segurança chave/valor está disponível para todas as APIs e utiliza `BackupAgentHelper` e `BackupAgent`.

##### <a name="backupagenthelper"></a>BackupAgentHelper

`BackupAgentHelper` é muito mais simples de implementar do que `BackupAgent`, tanto em termos de funcionalidade Android nativa, como de integração de MAM. `BackupAgentHelper`permite-lhe registar ficheiros completos e preferências partilhadas quer em `FileBackupHelper`, quer em `SharedPreferencesBackupHelper`, respetivamente. Em seguida, estes são adicionados ao `BackupAgentHelper` após a criação.

##### <a name="backupagent"></a>BackupAgent

`BackupAgent` permite-lhe ser muito mais explícito sobre os dados que farão parte da cópia de segurança. No entanto, esta opção significa que não poderá tirar partido da estrutura de cópias de segurança do Android. Uma vez que é responsável pela implementação, existem mais passos obrigatórios para garantir a proteção de dados adequada a partir do MAM. Uma vez que a maior parte do trabalho é feita por si, o programador, a integração do MAM é ligeiramente mais envolvida.

###### <a name="app-does-not-have-a-backup-agent"></a>A aplicação não tem um agente de cópia de segurança

Estas são as opções do programador quando `android:allowBackup =true`.

####### <a name="full-backup-according-to-a-configuration-file"></a>Cópia de segurança completa de acordo com um ficheiro de configuração

Forneça um recurso na etiqueta de metadados `com.microsoft.intune.mam.FullBackupContent` no seu manifesto. Por exemplo:     `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

Adicione o atributo seguinte na etiqueta `<application>` : `android:fullBackupContent="@xml/my_scheme"`, em que `my_scheme` é um recurso XML da sua aplicação.

####### <a name="full-backup-without-exclusions"></a>Cópia de segurança completa sem exclusões

Indique uma etiqueta no manifesto, como `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />`.

Adicione o atributo seguinte na etiqueta `<application>`: `android:fullBackupContent="true"`.

###### <a name="app-has-a-backup-agent"></a>A aplicação tem um agente de cópia de segurança

Siga as recomendações apresentadas anteriormente neste guia para `BackupAgent` e `BackupAgentHelper`.

Considere mudar para utilizar `MAMDefaultFullBackupAgent`, o qual proporciona uma cópia de segurança fácil no Android Marshmallow.

##### <a name="before-your-backup"></a>Antes de fazer a cópia de segurança

Antes de iniciar a cópia de segurança, tem de verificar se é realmente permitido fazê-la para os ficheiros ou memórias intermédias de dados pretendidos. Foi-lhe concedida uma função `isBackupAllowed` em `MAMFileProtectionManager` e `MAMDataProtectionManager` para o verificar. Se não for permitida a cópia de segurança de ficheiros ou memórias intermédias de dados, não deve tentar continuar a utilizá-los na sua cópia de segurança.

Se em algum momento durante a cópia de segurança pretender fazer uma cópia de segurança das identidades dos ficheiros selecionados no passo 1, tem de chamar `backupMAMFileIdentity(BackupDataOutput data, File … files)` com os ficheiros dos quais planeia extrair dados. Esta ação irá criar automaticamente novas entidades de cópia de segurança e escrevê-las em `BackupDataOutput` por si. Estas entidades serão consumidas automaticamente após o restauro.

#### <a name="azure-directory-authentication-library-setup"></a>Configurar a Azure Directory Authentication Library  

O SDK depende da ADAL para os cenários de autenticação e iniciação condicional. Estes cenários requerem que as aplicações tenham alguma configuração do Azure Active Directory (Azure AD). Os valores de configuração são comunicados ao SDK através de metadados `AndroidManifest` .

Para configurar a sua aplicação e ativar uma autenticação adequada, adicione o seguinte ao nó da aplicação em `AndroidManifest`. Algumas das seguintes configurações são obrigatórias apenas se a sua aplicação utiliza ADAL para autenticação em geral. Nesse caso, precisará dos valores específicos utilizados pela sua aplicação para registar-se com o Azure AD. Tal garante que o utilizador não recebe o pedido de autenticação duas vezes porque o Azure AD reconhece dois valores de registo separados: um da aplicação e outro do SDK.

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

Os GUIDs não devem ter a chaveta de abertura ou de fecho.

##### <a name="common-adal-configurations"></a>Configurações comuns da ADAL

Seguem-se as configurações comuns para os valores explicados anteriormente.

###### <a name="app-does-not-integrate-adal"></a>A aplicação não integra a ADAL

* A autoridade tem de ser definida para o ambiente pretendido onde foram definidas contas do Azure AD.

* SkipBroker tem de ser definido como verdadeiro.

###### <a name="app-integrates-adal"></a>A aplicação integra a ADAL

* A autoridade tem de ser definida para o ambiente pretendido onde foram definidas contas do Azure AD.

* O ID de cliente tem de ser definido como o ID de cliente da aplicação.

* `NonBrokerRedirectURI` deve ser definido como um URI de redirecionamento válido para a aplicação. Em alternativa, `urn:ietf:wg:oauth:2.0:oob` tem de ser definido como um URI de redirecionamento válido para o Azure AD.

* O SkipBroker tem de ser definido como falso (ou estar ausente).

* O Azure AD tem de ser definido para aceitar o URI de redirecionamento do mediador.

###### <a name="app-integrates-adal-but-does-not-support-the-azure-ad-authenticator-app"></a>A aplicação integra a ADAL, mas não suporta a aplicação Authenticator do Azure AD

* A autoridade tem de ser definida para o ambiente pretendido onde foram definidas contas do Azure AD.

* O ID de cliente tem de ser definido como o ID de cliente da aplicação.

* `NonBrokerRedirectURI` tem de ser definido como um URI de redirecionamento válido para a aplicação. Em alternativa, `urn:ietf:wg:oauth:2.0:oob` tem de ser definido como um URI de redirecionamento válido para o Azure AD.

#### <a name="logging-in-the-sdk"></a>Registo no SDK

O registo é feito através da estrutura `java.util.logging` . Para receber os registos, configure o registo global conforme descrito em [Java technical guide](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html). Consoante a aplicação, `App.onCreate` é, normalmente, o melhor local para iniciar o registo. Tenha em atenção que as mensagens do registo são codificadas pelo nome de classe, o qual poderá estar ocultado.

###<a name="multi-identity"></a>Várias identidades

Por predefinição, o SDK da aplicação Intune aplica a política à aplicação como um todo. As identidades múltiplas são uma funcionalidade de MAM que pode ativar para aplicar uma política por identidade. Esta opção requer uma participação da aplicação significativamente maior do que outras funcionalidades de MAM. A aplicação tem de informar ao SDK da aplicação quando tenciona alterar a identidade ativa. O SDK também deve notificar a aplicação quando for precisa uma alteração de identidade.

Atualmente, apenas é suportada uma identidade gerida. Depois de o utilizador inscrever o dispositivo ou a aplicação, o SDK utiliza esta identidade e considera-a a identidade gerida primária. Os outros utilizadores na aplicação são tratados como não geridos, com definições de política não restrita.

Note que uma identidade é simplesmente definida como uma cadeia. As identidades são sensíveis a maiúsculas e minúsculas. Os pedidos de identidade ao SDK podem não devolver a mesma utilização de maiúsculas e minúsculas que tinha sido originalmente utilizada quando a identidade foi definida.

####<a name="enabling-multi-identity"></a>Ativar identidades múltiplas

Por predefinição, todas as aplicações são consideradas aplicações de identidade única. Uma aplicação declara que reconhece identidades múltiplas ao colocar os seguintes metadados no manifesto do Android.

```
<meta-data
            android:name="com.microsoft.intune.mam.MAMMultiIdentity"
            android:value="true" />
```
####<a name="setting-the-identity"></a>Definir a identidade

Pode definir a identidade da aplicação nos seguintes níveis:

1. Nível de processo

2. Nível de contexto (geralmente `Activity`)

3. Nível de thread

Uma identidade definida no nível de thread prevalece sobre uma identidade definida no nível `Context`, que prevalece sobre uma identidade definida no nível de processo. Uma identidade definida no `Context` é utilizada apenas quando for adequado. Por exemplo, as operações de E/S de ficheiros não têm `Context` associado. Os seguintes métodos no `MAMPolicyManager` podem ser utilizados para definir a identidade e obter os valores de identidade anteriormente definidos.

```
public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

public static String getUIPolicyIdentity(final Context context);

public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

public static String getProcessIdentity();

public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

public static String getCurrentThreadIdentity();

/**
 * Get the currently applicable app policy. Same as MAMComponents.get(AppPolicy.class). This method does
    not take the context identity into account.
 */
public static AppPolicy getPolicy();

/**
 * Get the currently applicable app policy, taking the context
 * identity into account.
 */
public static AppPolicy getPolicy(final Context context);


public static AppPolicy getPolicyForIdentity(final String identity);

public static boolean getIsIdentityManaged(final String identity);

```
Pode também limpar a identidade da aplicação ao defini-la como nula. A cadeia vazia pode ser utilizada como uma identidade que nunca terá restrições. Todos os métodos para definir a identidade comunicam os valores de resultado através do ``` MAMIdentitySwitchResult```. Podem ser devolvidos quatro valores:

* **SUCCEEDED**: a alteração de identidade foi concluída com êxito.

* **NOT_ALLOWED**: a alteração de identidade não é permitida. Tal irá ocorrer em caso de tentativa de mudar para um utilizador empresarial diferente que pertença à mesma empresa que o utilizador inscrito. Também irá ocorrer em caso de tentativa de definir a identidade de IU (`Context`) quando uma identidade diferente for definida no thread atual.

* **CANCELLED**: o utilizador cancelou a alteração de identidade, geralmente ao premir o botão de retrocesso num pedido de PIN/autenticação.

* **FAILED**: a alteração de identidade falhou por um motivo não especificado.

No caso de definir uma identidade de `Context`, o resultado é reportado de forma assíncrona. Se `Context` é uma classe `Activity`, este não será conhecido se a alteração da identidade foi concluída com êxito antes de ocorrer a iniciação condicional. Uma iniciação condicional poderá necessitar que utilizador introduza um PIN ou as respetivas credenciais empresariais completas. É esperado que a aplicação implemente ```MAMSetUIIdentityCallback``` para receber este resultado, embora seja permissível passar nulo para este parâmetro.

```
public interface MAMSetUIIdentityCallback {
    void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
}
```

Também pode definir a identidade de uma atividade diretamente através de um método `MAMActivity` em vez de chamar ```MAMPolicyManager.setUIPolicyIdentity```. Também pode fazê-lo através do seguinte método:

 ```public final void switchMAMIdentity(final String newIdentity);```

As aplicações também podem substituir um método no `MAMActivity` para serem notificadas do resultado de tentativas para alterar a identidade dessa atividade.

```public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);```

> [!NOTE]
> Alterar a identidade pode requerer a recriação da atividade. Neste caso, a chamada de retorno ```onSwitchMAMIdentityComplete``` será entregue na nova instância da atividade.


####<a name="implicit-identity-changes"></a>Alterações de identidade implícitas

Além da capacidade da aplicação de definir a identidade, a identidade de um contexto ou thread pode mudar com base na entrada de dados de outra aplicação ativada para MAM. Por exemplo, se uma atividade for iniciada a partir de uma classe `Intent` enviada por outra aplicação para MAM, a identidade da atividade será definida com base na identidade real na outra aplicação no ponto em que a classe `Intent` foi enviada.

Para serviços, a identidade do thread será definida de forma semelhante durante uma chamada `onStart` ou `onBind`. As chamadas para `Binder` devolvidas do `onBind` também irão definir temporariamente a identidade do thread. De forma semelhante, as chamadas para um ```ContentProvider``` irão definir a identidade do thread na duração das mesmas.

Além disso, a interação do utilizador com uma atividade poderá causar uma mudança de identidade implícita. Por exemplo, um utilizador que desista de um pedido de autorização durante ```Resume``` irá resultar numa mudança implícita para uma identidade vazia.
Esta aplicação tem uma oportunidade de ter conhecimento destas alterações e, em alguns casos, de as proibir se for necessário. ```MAMService``` e ```MAMContentProvider``` expõem o seguinte método, que as subclasses podem substituir:

```
public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchResultCallback callback);
```
No caso de ```MAMActivity```, um parâmetro adicional está presente no método:
```
public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchReason reason,
    final AppIdentitySwitchResultCallback callback);
```
A parte ```AppIdentitySwitchReason``` captura a origem da alteração implícita. Pode aceitar os valores ```CREATE```, ```RESUME_CANCELLED``` e ```NEW_INTENT```.  O motivo ```RESUME_CANCELLED``` é utilizado quando a retoma da atividade gera a apresentação de PIN, autenticação ou outra IU de conformidade e o utilizador tenta desistir dessa IU, normalmente através do botão de retrocesso.
```AppIdentitySwitchResultCallback``` encontra-se da seguinte forma:
```
public interface AppIdentitySwitchResultCallback {
    /**
     * @param result
     *            whether the identity switch can proceed.
     */
    void reportIdentitySwitchResult(AppIdentitySwitchResult result);
}
```
```AppIdentitySwitchResult``` é ```SUCCESS``` ou ```FAILURE```.

O método ```onMAMIdentitySwitchRequired``` é chamado para todas as alterações de identidade implícitas, exceto nas que forem efetuadas através de uma classe `Binder` devolvida de ```MAMService.onMAMBind```. A implementação predefinida de ```onMAMIdentitySwitchRequired``` chama ```reportIdentitySwitchResult(FAILURE)``` imediatamente quando o motivo é ```RESUME_CANCELLED```; e ```reportIdentitySwitchResult(SUCCESS)``` em todos os restantes casos.

A maioria das aplicações provavelmente não vai precisar de bloquear ou adiar uma mudança de identidade de forma diferente. Mas se uma aplicação precisar de fazê-lo, considere os seguintes pontos:

* Se a alteração de identidade é bloqueada, o resultado é o mesmo como se as definições de partilha de ```Receive``` tivessem proibido a entrada de dados.

* Se um serviço estiver em execução no thread principal, ```reportIdentitySwitchResult``` *tem* de ser chamado de forma síncrona ou o thread da IU será bloqueado.

* Para criação de ```Activity```, ```onMAMIdentitySwitchRequired``` será chamado antes de ```onMAMCreate```. Se a aplicação tiver de mostrar a IU para verificar se a mudança de identidade deve ser permitida, a IU tem de ser mostrada com uma atividade diferente.

* Em ```Activity```, quando uma alteração para a identidade vazia for pedida com motivo igual a ```RESUME_CANCELLED```, a aplicação terá de modificar a atividade retomada de forma a mostrar dados consistentes com a mudança de identidade. Se não for possível, a aplicação deve recusar a mudança. Além disso, será novamente pedido ao utilizador que fique em conformidade com a política da identidade retomada (por exemplo, ao ver o ecrã de introdução de PIN).

> [!NOTE]
> Uma aplicação com várias identidades irá sempre receber dados de aplicações geridas e não geridas. A aplicação é responsável por tratar dados de identidades geridas de forma gerida. Se uma identidade solicitada for gerida ```(MAMPolicyManager.getIsIdentityManaged)```, mas a aplicação não puder utilizar essa conta (por exemplo, porque primeiro têm de ser definidas contas na aplicação, como contas de e-mail), a mudança de identidade deverá ser recusada.

###<a name="file-protection"></a>Proteção de ficheiros

Todos os ficheiros têm uma identidade associada na altura da criação, com base na identidade de processo e thread. Esta identidade é utilizada para encriptação de ficheiros e eliminação seletiva. Apenas os ficheiros cuja identidade tenha uma política que requeira encriptação serão encriptados. A eliminação seletiva predefinida do SDK irá eliminar apenas ficheiros associados à identidade para a qual uma eliminação tenha sido solicitada. A aplicação poderá consultar ou alterar a identidade de um ficheiro ao utilizar ```MAMFileProtectionManager```.
```
public final class MAMFileProtectionManager {

    /**
     * Protect a file. This will synchronously trigger whatever protection is required for the file, and will tag the file for
     * future protection changes.
     *
     * @param identity
     *            Identity to set.
     * @param file
     *            File to protect.
     * @throws IOException
     *             If the file cannot be changed.
     */
    public static void protect(final File file, final String identity) throws IOException;

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
}

public interface MAMFileProtectionInfo {
String getIdentity();
}
```

> [!NOTE]
> A etiquetagem de identidade de ficheiros é sensível ao modo offline. Leve em consideração os seguintes pontos:
> * Se a aplicação Portal da Empresa não estiver instalada, a etiquetagem de identidade dos ficheiros não poderá ser feita.
>
> * Se a aplicação Portal da Empresa estiver instalada, mas a aplicação não tiver uma política, os ficheiros não poderão ter etiquetagem de identidade de forma fiável.
>
> * Quando a etiquetagem de identidade for disponibilizada, todos os ficheiros anteriormente criados serão tratados como pessoais (pertencentes à identidade de cadeia vazia), a menos que a aplicação tenha sido anteriormente instalada como aplicação gerida com identidade única. Nesse caso, serão tratados como pertencentes ao utilizador inscrito.

####<a name="data-protection"></a>Proteção de dados

Não é possível etiquetar um ficheiro como pertencente a identidades múltiplas. As aplicações que têm de armazenar dados pertencentes a utilizadores diferentes no mesmo ficheiro podem fazê-lo manualmente ao utilizar as funcionalidades proporcionadas por ```MAMDataProtectionManager```. Tal permite à aplicação encriptar dados e associá-los a um utilizador específico. Os dados encriptados são adequados para armazenamento no disco de um ficheiro. Pode consultar os dados associados à identidade e os ficheiros podem ser desencriptados posteriormente.

```
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
###<a name="content-providers"></a>Fornecedores de conteúdo

Se a aplicação estiver a proporcionar dados potencialmente empresariais que não ```ParcelFileDescriptor``` através de um ```ContentProvider```, a aplicação terá de chamar o ```MAMContentProvider``` método ```isProvideContentAllowed(String)```, com a passagem do proprietário ```UPN``` para o conteúdo. Se esta função devolver "falso", os conteúdos poderão não ser devolvidos ao chamador. Os descritores de ficheiros devolvidos através de um fornecedor de conteúdos são processados automaticamente, com base na identidade do ficheiro.

###<a name="selective-wipe"></a>Eliminação seletiva

Se uma aplicação se registar para a notificação ```WIPE_USER_DATA```, não receberá a vantagem do comportamento predefinido da eliminação seletiva por parte do SDK. Para aplicações com suporte para identidades múltiplas, pode ser mais significativo porque a eliminação seletiva de MAM elimina apenas os ficheiros correspondentes à identidade a ser limpa.

Se estiver a criar uma aplicação que tenha em conta várias identidades, pode registar para ```WIPE_USER_AUXILIARY_DATA```. Esta notificação permite-lhe tirar partido do comportamento de eliminação predefinido do SDK. Esta notificação será enviada imediatamente antes de executar a eliminação seletiva predefinida do SDK. Tenha em atenção que uma aplicação nunca se deverá registar para ```WIPE_USER_DATA```e ```WIPE_USER_AUXILIARY_DATA```.

### <a name="known-platform-limitations"></a>Limitações de plataforma conhecidas

#### <a name="file-size-limitations"></a>Limitações de tamanho de ficheiro

No Android, as limitações do formato de ficheiro executável Dalvik podem tornar-se um problema para bases de códigos grandes executadas sem o ProGuard. Mais concretamente, podem ocorrer as seguintes limitações:

* O limite de 65.000 nos campos

* O limite de 65.000 nos métodos

Se forem incluídos muitos projetos, cada `android:package` obterá uma cópia de R. Tal irá aumentar, significativamente, o número de campos à medida que forem adicionadas bibliotecas. As seguintes recomendações podem ajudar a atenuar esta limitação:

* Todos os projetos de biblioteca devem partilhar o mesmo `android:package` sempre que possível. Tal não falhará esporadicamente no campo porque se trata apenas de um problema de tempo de compilação. Além disso, as versões mais recentes do SDK Android irão pré-processar os ficheiros DEX para remover parte da redundância. Desta forma, a distância dos campos é reduzida ainda mais.

* Utilizar as ferramentas de compilação mais recentes do SDK Android.

* Remover todas as bibliotecas desnecessárias e não utilizadas (por exemplo, `android.support.v4`).

#### <a name="policy-enforcement-limitations"></a>Limitações de imposição de políticas

**Captura de ecrã**: o SDK não consegue impor um novo valor de definição de captura de ecrã nas classes `Activity` que já passaram por `Activity.onCreate`. Tal pode resultar num período de tempo em que a aplicação foi definida para desativar capturas de ecrã, mas em que estas ainda podem ser criadas.

**Resoluções de conteúdos**: a política de transferência ou receção pode bloquear ou bloquear parcialmente a utilização de uma resolução de conteúdos para aceder ao fornecedor de conteúdos noutra aplicação. Tal fará com que os métodos `ContentResolver` devolvam um valor nulo ou gerem um valor de falha. (Por exemplo, `openOutputStream` irá gerar `FileNotFoundException` se estiver bloqueado.) A aplicação pode fazer esta chamada para verificar se uma política causou (ou poderá causar) uma falha ao escrever dados através de uma resolução de conteúdo:

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**Serviços exportados**: o ficheiro `AndroidManifest.xml` incluído no SDK da aplicação do Intune tem `MAMNotificationReceiverService`. Tem de ser um serviço exportado para permitir que a aplicação Portal da Empresa envie notificações para uma aplicação otimizada. O serviço verifica o autor da chamada para assegurar que apenas a aplicação Portal da Empresa está autorizada a enviar notificações.

### <a name="android-best-practices"></a>Melhores práticas de Android

O SDK do Intune mantém o contrato proporcionado pela API Android, embora possam ser acionadas condições de falha mais frequentemente como resultado da imposição de políticas. Estas melhores práticas para Android reduzirão a probabilidade de falhas:

* As funções do SDK Android que podem devolver valores nulos têm uma maior probabilidade de ter um valor nulo agora. Para minimizar os problemas, confirme que as verificações de valores nulos estão nos locais corretos.

* Para as funcionalidades que pode verificar, utilize as suas APIs do SDK para essa verificação.

* As funções derivadas têm de fazer chamadas através das respetivas versões de superclasses.

* Evitar utilizar qualquer API de uma forma ambígua. Por exemplo, a utilização de `Activity.startActivityForResult/onActivityResult` sem verificar o `requestCode` causará um comportamento invulgar.

