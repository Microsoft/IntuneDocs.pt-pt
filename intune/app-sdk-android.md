---
title: "Guia para programadores do SDK da Aplicação do Microsoft Intune para Android"
description: "O SDK da Aplicação do Microsoft Intune para Android permite incorporar a gestão de aplicações móveis (MAM) do Intune na sua aplicação Android."
keywords: SDK
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: b5ad9cc6c03712090398cacb3d4bb653deb1d2a4
ms.openlocfilehash: 7dfcc0bf8f3da1e600df59927db6e78ec2021e0f
ms.contentlocale: pt-pt
ms.lasthandoff: 06/12/2017


---


# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Guia para programadores do SDK da Aplicação do Microsoft Intune para Android

> [!NOTE]
> Pode ser útil ler primeiro a [Descrição geral do SDK da Aplicação do Intune](app-sdk.md), que abrange as funcionalidades atuais do SDK e descreve como preparar a integração em cada plataforma suportada.

O SDK da Aplicação do Microsoft Intune para Android permite-lhe incorporar as políticas de proteção de aplicações do Intune (também conhecidas como políticas de **APLICAÇÕES** ou MAM) na aplicação Android nativa. Uma aplicação otimizada pelo Intune é uma aplicação que está integrada com o SDK da Aplicação do Intune. Os administradores do Intune podem facilmente implementar políticas de proteção de aplicações na aplicação otimizada pelo Intune quando este está a gerir a aplicação de forma ativa.


## <a name="whats-in-the-sdk"></a>O que está no SDK

O SDK da Aplicação do Intune é constituído pelos seguintes ficheiros:  

* **Microsoft.Intune.MAM.SDK.aar**: os componentes do SDK, à exceção dos ficheiros JAR Support.V4 e Support.V7. Este ficheiro pode ser utilizado em vez dos componentes individuais se o sistema de compilação suportar ficheiros AAR.
* **Microsoft.Intune.MAM.SDK.Support.v4.jar**: as interfaces necessárias para ativar o MAM nas aplicações utilizam a biblioteca de suporte v4 do Android. As aplicações que precisam deste suporte têm de referenciar diretamente o ficheiro JAR.
* **Microsoft.Intune.MAM.SDK.Support.v7.jar**: as interfaces necessárias para ativar o MAM nas aplicações que utilizam a biblioteca de suporte v7 do Android. As aplicações que precisam deste suporte têm de referenciar diretamente o ficheiro JAR.
* **proguard.txt**: contém regras ProGuard que devem ser aplicadas se estiver a criar com o ProGuard.
* **CHANGELOG.txt**: fornece um registo das alterações feitas em cada versão do SDK.
* **THIRDPARTYNOTICES.TXT**: aviso de atribuição que reconhece código de terceiros e/ou OSS que será compilado na sua aplicação.

Se o sistema de compilação não suportar ficheiros AAR, poderá utilizar os seguintes ficheiros em vez de Microsoft.Intune.MAM.SDK.aar.
* **Microsoft.Intune.MAM.SDK.jar**: as interfaces necessárias para ativar a MAM e a interoperabilidade com a aplicação Portal da Empresa do Intune. As aplicações têm de especificá-lo como referência da biblioteca do Android.
* **Diretório res**: os recursos (como, por exemplo, cadeias) nos quais se baseiam o SDK.
* **AndroidManifest.xml**: os pontos de entrada e os requisitos da biblioteca.


## <a name="requirements"></a>Requisitos

O SDK da Aplicação do Intune é um projeto Android compilado. Como resultado, não é praticamente afetado pela versão do Android que a aplicação utiliza nas suas versões de API mínimas ou de destino. O SDK suporta a API Android 14 (Android 4.0+) até Android API 25 (Android 7.1).



### <a name="company-portal-app"></a>Aplicação Portal da Empresa
O SDK da Aplicação do Intune para Android baseia-se na presença da aplicação [Portal da Empresa](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) no dispositivo para ativar as políticas de proteção. O Portal da Empresa obtém as políticas de proteção de aplicações do serviço Intune. Quando a aplicação é inicializada, é carregada a política e o código para impor essa política a partir do Portal da Empresa.

> [!NOTE]
> Quando a aplicação Portal da Empresa não está no dispositivo, uma aplicação otimizada pelo Intune tem o mesmo comportamento que uma aplicação normal que não suporta as políticas de proteção de aplicações do Intune.

Para a proteção de aplicações sem inscrição de dispositivos, o utilizador _**não**_ é obrigado a inscrever o dispositivo através da aplicação Portal da Empresa.

## <a name="sdk-integration"></a>Integração do SDK

### <a name="build-integration"></a>Integração da compilação

O SDK da Aplicação do Intune é uma biblioteca do Android padrão sem dependências externas. O **Microsoft.Intune.MAM.SDK.jar** contém ambas as interfaces necessárias para uma ativação da política de proteção de aplicações e o código necessário para interagir com a aplicação Portal da Empresa do Microsoft Intune.

O **Microsoft.Intune.MAM.SDK.jar** deve ser especificado como uma referência da biblioteca do Android. Para tal, abra o projeto de aplicação no Android Studio e aceda a **Ficheiro > Novo > Novo módulo** e selecione **Importar Pacote .JAR/.AAR**. Selecione o nosso pacote de arquivo Android Microsoft.Intune.MAM.SDK.aar.

Além disso, o **Microsoft.Intune.MAM.SDK.Support.v4** e o **Microsoft.Intune.MAM.SDK.Support.v7** contêm variantes do Intune de `android.support.v4` e `android.support.v7` respetivamente. Não são compiladas no Microsoft.Intune.MAM.SDK.aar, caso uma aplicação não pretenda incluir as bibliotecas de suporte. São ficheiros JAR padrão em vez de projetos de biblioteca Android.

#### <a name="proguard"></a>ProGuard

Se o [ProGuard](http://proguard.sourceforge.net/) (ou qualquer outro mecanismo de redução/ocultação) for utilizado como um passo de compilação, as classes do SDK do Intune deverão ser excluídas. Para o ProGuard, isto pode ser realizado ao incluir as regras do ficheiro proguard.txt distribuído com o SDK.

As Azure Active Directory Authentication Libraries (ADAL) podem ter as suas próprias restrições ProGuard. Se a sua aplicação integrar a ADAL, terá de seguir a documentação da ADAL referente a essas restrições.

### <a name="entry-points"></a>Pontos de entrada
======= A Azure Active Directory Authentication Library ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) requer estas permissões para executar a autenticação mediada. Se estas permissões não forem concedidas pela aplicação ou forem revogadas pelo utilizador, os fluxos de autenticação que exigirem o mediador (a aplicação Portal da Empresa) serão desativados.

Para ativar as políticas de proteção de aplicações do Intune, o SDK da Aplicação do Intune requer alterações ao código fonte da aplicação. Estas alterações são feitas através da substituição das classes base do Android por classes base do Intune equivalentes, referidas no documento com o prefixo **MAM**. As classes do SDK estão entre a classe base Android e a própria versão derivada da aplicação dessa classe. Com uma atividade como exemplo, pode ficar com uma hierarquia de herança semelhante a: `Activity` > `MAMActivity` > `AppSpecificActivity`.

Por exemplo, quando `AppSpecificActivity` interage com o respetivo principal (por exemplo, ao chamar `super.onCreate()`), `MAMActivity` é a superclasse.

Normalmente, as aplicações Android têm um modo único e podem aceder ao sistema através do objeto [**Context**](https://developer.android.com/reference/android/content/Context.html). Por sua vez, as aplicações que integraram o SDK da Aplicação do Intune têm nós duplos. Estas aplicações continuam a aceder ao sistema através do objeto `Context`. Dependendo da base de `Activity` utilizada, o objeto `Context` será proporcionado pelo Android ou será multiplexado inteligentemente entre uma vista restrita do sistema e o `Context` proporcionado pelo Android.


## <a name="replace-classes-methods-and-activities-with-their-mam-equivalent"></a>Substituir as classes, os métodos e as atividades pelas MAM equivalentes

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
| android.app.PendingIntent | MAMPendingIntent (ver notas abaixo) |
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
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |


### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft.Intune.MAM.SDK.Suppout.v4.jar:

| MAM do Intune da Classe Android | Substituição do SDK da Aplicação do Intune |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft.Intune.MAM.SDK.Suppout.v7.jar:

|Classe Android | Substituição do SDK da Aplicação do Intune |
|--|--|
|android.support.v7.app.ActionBarActivity | MAMActionBarActivity |


### <a name="renamed-methods"></a>Métodos renomeados
Após derivar de um dos pontos de entrada MAM, é seguro utilizar `Context`, como faria normalmente, por exemplo, para iniciar as classes `Activity` e utilizar `PackageManager`.

Em muitos casos, um método disponível na classe Android foi marcado como final na classe de substituição da MAM. Neste caso, a classe de substituição de MAM proporciona um método com um nome semelhante (geralmente, com o sufixo `MAM`), que deve ser substituído. Por exemplo, quando executar a derivação de `MAMActivity`, em vez de substituir `onCreate()` e chamar `super.onCreate()`, `Activity` tem de substituir `onMAMCreate()` e chamar `super.onMAMCreate()`. O compilador de Java deve impor as restrições finais para impedir a substituição acidental do método original em vez do MAM equivalente.

### <a name="pendingintent"></a>PendingIntent
Em vez de `PendingIntent.get*`, tem de utilizar o método `MAMPendingIntent.get*`. Depois disto, pode utilizar o `PendingIntent` resultante como habitualmente.

### <a name="manifest-replacements"></a>Substituições do manifesto
Tenha em atenção que poderá ser necessário realizar algumas das substituições de classe indicadas acima no manifesto, bem como no código Java. De destacar:
* As referências do manifesto a `android.support.v4.content.FileProvider` devem ser substituídas por `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider`.


## <a name="sdk-permissions"></a>Permissões de SDK

O SDK da Aplicação do Intune requer três [permissões do sistema Android](https://developer.android.com/guide/topics/security/permissions.html) em aplicações que o integrem:

* `android.permission.GET_ACCOUNTS` (pedido durante o runtime, se for preciso)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

A Azure Active Directory Authentication Library ([ADAL](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/)) requer estas permissões para executar a autenticação mediada. Se estas permissões não forem concedidas pela aplicação ou forem revogadas pelo utilizador, os fluxos de autenticação que exigirem o mediador (a aplicação Portal da Empresa) serão desativados.

## <a name="logging"></a>Registo

O registo deve ser inicializado antecipadamente para obter o maior valor dos dados registados. `Application.onMAMCreate()` é normalmente o melhor local para inicializar o registo.

Para receber registos MAM na sua aplicação, crie um [Processador Java](http://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html) e adicione-o ao `MAMLogHandlerWrapper`. Este procedimento invocará `publish()` no processador da aplicação para todas as mensagens de registo.

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

Existem várias políticas de proteção de aplicações que o SDK não pode implementar por si só. A aplicação pode controlar o respetivo comportamento para cumprir estas funcionalidades através de várias APIs que pode encontrar na seguinte interface `AppPolicy`.

```java
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * This function is now deprecated. Please use getIsSaveToLocationAllowed(SaveLocation, String) instead
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

> [!NOTE]
> `MAMComponents.get(AppPolicy.class)` devolverá sempre uma Política de Aplicação não nula, mesmo se o dispositivo ou aplicação não estiver sob uma política de gestão do Intune.

### <a name="example-determine-if-pin-is-required-for-the-app"></a>Exemplo: determinar se o PIN é necessário para a aplicação

Se a aplicação tiver a sua própria experiência de utilizador de PIN, poderá querer desativá-la caso o administrador de TI tenha configurado o SDK para solicitar um PIN da aplicação. Para determinar se o administrador de TI implementou a política de PIN da aplicação para esta aplicação, para o utilizador final atual, chame o método seguinte:

```java
MAMComponents.get(AppPolicy.class).getIsPinRequired();
```

### <a name="example-determine-the-primary-intune-user"></a>Exemplo: determinar o utilizador primário do Intune

Além das APIs expostas na AppPolicy, o nome principal do utilizador (**UPN**) também é exposto pela API `getPrimaryUser()` definida na interface `MAMUserInfo`. Para obter o UPN, chame o seguinte:

```java
MAMUserInfo info = MAMComponents.get(MAMUserInfo.class);
if (info != null) return info.getPrimaryUser();
```

A definição completa da interface MAMUserInfo pode ser vista abaixo:

```java
/**
 * External facing user informations.
 *
 */
public interface MAMUserInfo {
       /**
        * Get the primary user name.
        *
        * @return the primary user name or null if the device is not enrolled.
        */
       String getPrimaryUser();
}
```

### <a name="example-determine-if-saving-to-device-or-cloud-storage-is-permitted"></a>Exemplo: determinar se é permitido guardar no dispositivo ou armazenar na cloud

Muitas aplicações implementam funcionalidades que permitem ao utilizador final guardar os ficheiros localmente ou num serviço de armazenamento na nuvem. O SDK da Aplicação do Intune permite aos administradores de TI aplicar restrições de políticas que considerem mais adequadas na organização, para proteger contra fugas de dados.  Uma das políticas que o administrador de TI pode controlar é se o utilizador final pode guardar num arquivo de dados "pessoal" não gerido. Isto inclui guardar numa localização local, num cartão SD ou em serviços de cópias de segurança de terceiros.

**A participação da aplicação é necessária para ativar a funcionalidade.** Se a aplicação permitir guardar em localizações pessoais ou na nuvem diretamente a partir da aplicação, tem de implementar esta funcionalidade para garantir que o administrador de TI pode controlar se a gravação numa localização é permitida. A API abaixo permite à aplicação saber se a gravação num arquivo pessoal é permitida pela política do administrador do Intune atual. Em seguida, a aplicação pode impor a política, uma vez que tem conhecimento do arquivo de dados pessoal disponível para o utilizador final através da aplicação.  

Para determinar se a política é imposta, faça a seguinte chamada:

```java
MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

... em que `service` é uma das seguintes SaveLocations:


    * SaveLocation.ONEDRIVE_FOR_BUSINESS
    * SaveLocation.LOCAL
    * SaveLocation.OTHER

O método anterior para determinar se uma política de utilizador permitia guardar dados em várias localizações era `getIsSaveToPersonalAllowed()`, dentro da mesma classe **AppPolicy**. Esta função é agora **preterida** e não deve ser utilizada, a invocação seguinte é equivalente a `getIsSaveToPersonalAllowed()`:

```java

MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(SaveLocation.LOCAL, userNameInQuestion);
```

>[!NOTE]
> Utilize `SaveLocation.OTHER` se a localização em questão não estiver listada no enum **SaveLocations**.


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

* **WIPE_USER_DATA**: esta notificação é enviada numa classe `MAMUserNotification`. Quando esta notificação é recebida, a aplicação deve eliminar todos os dados associados à identidade “empresarial” transmitida com a `MAMUserNotification`. Atualmente, esta notificação é enviada durante a anulação da inscrição do serviço APP-WE. Geralmente, o nome principal do utilizador é especificado durante o processo de inscrição. Caso se tenha registado para obter esta notificação, a sua aplicação tem de garantir que todos os dados do utilizador foram eliminados. Se não se registar para obtê-la, será aplicado o comportamento de eliminação seletiva predefinido.

* **WIPE_USER_AUXILIARY_DATA**: as aplicações poderão registar-se para obter esta notificação se quiserem utilizar o SDK da Aplicação do Intune para executar o comportamento predefinido de eliminação seletiva, mas ainda quiserem remover alguns dados auxiliares quando ocorrer a eliminação.

* **REFRESH_POLICY**: esta notificação é enviada numa `MAMUserNotification`. Quando esta notificação for recebida, qualquer política do Intune em cache tem de ser invalidada e atualizada. Regra geral, isto é processado pelo SDK, mas deve ser processado pela aplicação se a política for utilizada de qualquer forma persistente.

* **MANAGEMENT_REMOVED**: esta notificação é enviada numa `MAMUserNotification` e informa a aplicação que está prestes a deixar de ser gerida. Quando já não for gerida, a aplicação deixará de conseguir ler ficheiros encriptados, ler dados encriptados com MAMDataProtectionManager, interagir com a área de transferência encriptada ou participar no ecossistema de aplicações geridas.


> [!NOTE]
> Uma aplicação nunca se deverá registar para as notificações `WIPE_USER_DATA` e `WIPE_USER_AUXILIARY_DATA`.


## <a name="configure-azure-active-directory-authentication-library-adal"></a>Configurar a Azure Active Directory Authentication Library (ADAL)

Em primeiro lugar, leia as diretrizes de integração da ADAL presentes no [Repositório da ADAL no GitHub](https://github.com/AzureAD/azure-activedirectory-library-for-android).

O SDK depende da [ADAL](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/) nos cenários de [autenticação](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-scenarios/) e início condicional, os quais requerem que as aplicações sejam configuradas com o [Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-whatis/). Os valores de configuração são comunicados ao SDK através de metadados AndroidManifest.

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

* **Autoridade** é a atual autoridade do AAD em utilização. Se estiver presente, deve utilizar o seu ambiente onde foram configuradas as contas do AAD. Se este valor estiver ausente, será utilizado um valor predefinido do Intune.

* O **ClientID** é o ClientID do AAD a ser utilizado. Deverá utilizar o ClientID da sua própria aplicação se este estiver registado com o Azure AD. Se este valor estiver ausente, será utilizado um valor predefinido do Intune.

* **NonBrokerRedirectURI** é o URI de redirecionamento do AAD para utilizar em casos sem mediador. Se não for especificado nenhum, será utilizado um valor predefinido de `urn:ietf:wg:oauth:2.0:oob`. Esta predefinição é adequada para a maioria das aplicações.

* **SkipBroker** é utilizado caso o ClientID não tenha sido configurado para utilizar o URI de redirecionamento do mediador. O valor predefinido é “falso”.
    * As aplicações que **não integram a ADAL** e **não pretendem participar na autenticação/SSO mediada em todos os dispositivos** devem ser definidas com o valor “verdadeiro”. Quando este valor estiver definido como “verdadeiro”, o único URI de redirecionamento que será utilizado é NonBrokerRedirectURI.

    * No caso das aplicações que suportam a mediação de SSO em todos os dispositivos, estas deverão ter o valor “falso”. Quando o valor está definido como “falso”, o SDK selecionará um mediador entre o resultado de [`com.microsoft.aad.adal.AuthenticationContext.getRedirectUriForBroker()`](https://github.com/AzureAD/azure-activedirectory-library-for-android) e NonBrokerRedirectURI, com base na disponibilidade do mediador do sistema. No geral, o mediador estará disponível na aplicação Portal da Empresa ou na aplicação Azure Authenticator.

### <a name="common-adal-configurations"></a>Configurações comuns da ADAL

Seguem-se algumas formas comuns através das quais uma aplicação pode ser configurada com a ADAL. Localize a configuração da sua aplicação e confirme que define os parâmetros de metadados da ADAL (explicado acima) para os valores necessários.

1. **A aplicação não integra a ADAL:**

    | Parâmetro necessário da ADAL | Valor |
    |--|--|
    | Autoridade | Ambiente pretendido onde foram configuradas contas do AAD |
    | SkipBroker | Verdadeiro |

2. **A aplicação integra a ADAL:**

    |Parâmetro necessário da ADAL| Valor |
    |--|--|
    | Autoridade | Ambiente pretendido onde foram configuradas contas do AAD |
    | ClientID | O ClientID da aplicação (gerado pelo Azure AD quando a aplicação é registada) |
    | NonBrokerRedirectURI | Um URI de redirecionamento da aplicação válido ou `urn:ietf:wg:oauth:2.0:oob`, por predefinição. <br><br> Confirme que configura o valor como um URI de redirecionamento aceitável para o ClientID da sua aplicação.
    | SkipBroker | Falso |


3. **A aplicação integra a ADAL, mas não suporta a autenticação mediada/SSO em todos os dispositivos:**

    |Parâmetro necessário da ADAL| Valor |
    |--|--|
    | Autoridade | Ambiente pretendido onde foram configuradas contas do AAD |
    | ClientID | O ClientID da aplicação (gerado pelo Azure AD quando a aplicação é registada) |
    | NonBrokerRedirectURI | Um URI de redirecionamento da aplicação válido ou `urn:ietf:wg:oauth:2.0:oob`, por predefinição. <br><br> Confirme que configura o valor como um URI de redirecionamento aceitável para o ClientID da sua aplicação.
    | SkipBroker | **Verdadeiro** |

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

3. Quando uma conta de utilizador é removida por completo, a aplicação deve chamar `unregisterAccountForMAM()` para remover a conta da gestão do Intune.

    > [!NOTE]
    > Se um utilizador terminar a sessão temporariamente na aplicação, a aplicação não precisará chamar `unregisterAccountForMAM()`. A chamada pode iniciar uma eliminação para remover por completo os dados empresariais do utilizador.


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager

Todas as APIs de autenticação e registo necessárias podem ser encontradas na interface `MAMEnrollmentManager`. Pode obter uma referência do `MAMEnrollmentManager` da seguinte forma:

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr

```

Está garantido que a instância `MAMEnrollmentManager` devolvida não é nula. Os métodos API enquadram-se em duas categorias: **autenticação** e **registo de conta**.

> [!NOTE]
> `MAMEnrollmentManager` contém alguns métodos da API que serão preteridos em breve. Para efeitos de clareza, apenas os métodos relevantes e os códigos de resultados são apresentados no bloco de código abaixo.

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

1. A aplicação tem de implementar a interface `MAMServiceAuthenticationCallback` para permitir que o SDK peça um token da ADAL para o utilizador especificado e o ID de recurso. A instância da chamada de retorno tem de ser fornecida ao `MAMEnrollmentManager` ao chamar o respetivo método `registerAuthenticationCallback()`. Poderá ser necessário um token muito cedo no ciclo de vida da aplicação para tentativas de inscrição ou registos de atualização da política de proteção de aplicações, para que o local ideal para registar a chamada de retorno esteja no método `onMAMCreate()` da subclasse `MAMApplication` da aplicação.

2. O método `acquireToken()` deve adquirir o token de acesso do ID de recurso pedido para o utilizador especificado. Se não conseguir adquirir o token pedido, este deverá devolver nulo.

3. Caso a aplicação não consiga fornecer um token quando o SDK chama o `acquireToken()`, por exemplo, se a autenticação silenciosa falhar e, sendo um período de tempo inconveniente para mostrar uma IU, a aplicação poderá fornecer um token num momento posterior ao chamar o método `updateToken()`. Os mesmos UPN, ID de UPN, ID do AAD e ID de recurso solicitados pela chamada anterior para `acquireToken()` têm de ser transmitidos para `updateToken()`, juntamente com o token que foi, finalmente, adquirido. A aplicação deve invocar este método com o máximo de brevidade possível após ser devolvido o valor nulo da chamada de retorno fornecida.

> [!NOTE]
> O SDK ligará para o `acquireToken()` periodicamente para obter o token; por isso, não é estritamente necessário ligar para o `updateToken()`. Contudo, é recomendado, na medida em que pode ajudar na conclusão das inscrições e nos registos da política de proteção de aplicações de forma atempada.


### <a name="account-registration"></a>Registo da conta

Esta secção descreve os métodos da API do registo da conta no `MAMEnrollmentManager` e como utilizá-los.

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. Para registar uma conta de gestão, a aplicação deve chamar `registerAccountForMAM()`. Uma conta de utilizador é identificada pelos seus UPN e ID de utilizador do AAD. O ID do inquilino também é necessário para associar os dados de inscrição com o inquilino do AAD do utilizador. O SDK pode tentar inscrever a aplicação para o utilizador especificado no serviço MAM. Se a inscrição falhar, esta tentará realizar periodicamente a inscrição até que a conta fique não registada. Por norma, o período de repetição é de 12 a 24 horas. O SDK fornece o estado das tentativas de inscrição de modo assíncrono através de notificações.

2. Como é necessário autenticar o AAD, a melhor altura para registar a conta de utilizador é depois deste ter iniciado a sessão e realizado a autenticação com êxito através da ADAL.
    * O ID do AAD do utilizador e o ID do inquilino são devolvidos na chamada de autenticação da ADAL como parte do objeto [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android). O ID do inquilino provém do método `AuthenticationResult.getTenantID()`.
    * Pode encontrar informações sobre o utilizador num subobjeto do tipo `UserInfo` proveniente de `AuthenticationResult.getUserInfo()` e o utilizador do AAD ID é obtido a partir desse objeto ao chamar `UserInfo.getUserId()`.

3. Para anular o registo de uma conta da gestão do Intune, a aplicação deve chamar `unregisterAccountForMAM()`. Se a conta tiver sido inscrita com êxito e for gerida, o SDK anulará a inscrição da conta e eliminará os seus dados. As tentativas periódicas de inscrição da conta serão interrompidas. O SDK fornece o estado dos pedidos de anulação da inscrição de modo assíncrono através de notificações.

### <a name="important-implementation-notes"></a>Notas de implementação importantes

#### <a name="authentication"></a>Autenticação

* Quando a aplicação chama `registerAccountForMAM()`, esta pode receber uma chamada de retorno na sua interface `MAMServiceAuthenticationCallback` pouco tempo depois, num thread diferente. Idealmente, a aplicação obteve o seu próprio token da ADAL antes de registar a conta para agilizar a aquisição do **token MAMService**. Se a aplicação devolver um token válido na chamada de retorno, a inscrição prosseguirá e a aplicação obterá o resultado final através de uma notificação.

* Se a aplicação não devolver um token do AAD válido, o resultado final da tentativa de inscrição será `AUTHENTICATION_NEEDED`. Se a aplicação receber este Resultado através de notificação, poderá agilizar o processo de inscrição ao adquirir o **token MAMService** e chamar o método `updateToken()` para iniciar novamente o processo de inscrição. Este _não_ é um requisito fixo; contudo, o SDK repetirá a inscrição periodicamente e invocará a chamada de retorno para adquirir o token.

* A `MAMServiceAuthenticationCallback` registada da aplicação também será chamada para adquirir um token para registos de atualizações periódicas da política de proteção de aplicações. Se a aplicação não conseguir fornecer um token, quando solicitado, esta não receberá nenhuma notificação, mas deverá tentar adquirir um token e chamar `updateToken()` numa altura conveniente para agilizar o processo de registo. Se não for fornecido um token, a chamada de retorno será realizada na mesma na próxima tentativa de registo.

#### <a name="registration"></a>Registo

* Para sua comodidade, os métodos de registo são idempotentes, por exemplo, `registerAccountForMAM()` registará apenas uma conta e uma tentativa de inscrição da aplicação se a conta ainda não estiver registada e `unregisterAccountForMAM()` apenas anulará o registo de uma conta se esta estiver atualmente registada. As chamadas subsequentes efetuadas são não operativas, por isso, não há qualquer problema em chamar esses métodos mais do que uma vez. Além disso, a correspondência entre as chamadas para esses métodos e as notificações dos resultados não são garantidas, isto é, se `registerAccountForMAM` for chamado para uma identidade que já esteja registada, a notificação poderá não ser enviada novamente para essa identidade. É possível que sejam enviadas notificações que não correspondem a qualquer chamada para esses métodos, dado que o SDK pode tentar periodicamente realizar inscrições em segundo plano. Adicionalmente, podem ser acionadas anulações de inscrições com a eliminação dos pedidos recebidos do serviço Intune.

* Os métodos de registo podem ser chamados para um qualquer número de identidades diferentes, mas, atualmente, apenas uma conta de utilizador pode ser inscrita com êxito. Se estiverem registadas várias contas de utilizador licenciadas para o Intune e estas forem visadas pela política de proteção de aplicações na mesma altura ou próxima desta, não haverá qualquer garantia sobre qual será a escolhida.

* Por fim, pode consultar o `MAMEnrollmentManager` para ver se uma determinada conta está registada e para obter o seu estado atual com recurso ao método `getRegisteredAccountStatus`. Se a conta fornecida não estiver registada, este método devolverá **nulo**. Se a conta estiver registada, este método devolverá o estado da conta como um dos membros da enumeração `MAMEnrollmentManager.Result`.

### <a name="result-and-status-codes"></a>Códigos de estados e de resultados

Quando uma conta é registada pela primeira vez, esta começa no estado `PENDING`, o qual indica que a tentativa inicial de inscrição do serviço MAM está incompleta. Depois de concluída a tentativa de inscrição, será enviada uma notificação com um dos Códigos de resultados da tabela abaixo. Além disso, o método `getRegisteredAccountStatus()` devolverá o estado da conta para que a aplicação possa determinar sempre se o acesso ao conteúdo empresarial está bloqueado para esse utilizador. Se a tentativa de inscrição falhar, o estado da conta poderá mudar ao longo do tempo, uma vez que o SDL volta a tentar a inscrição em segundo plano.

|Código do resultado | Explicação |
| -- | -- |
|AUTHORIZATION_NEEDED | Este resultado indica que não foi fornecido um token pela instância `MAMServiceAuthenticationCallback` registada da aplicação ou o token fornecido era inválido.  A aplicação deve adquirir um token válido e chamar `updateToken()`, se possível. |
| NOT_LICENSED | O utilizador não está licenciado para o Intune ou a tentativa de contacto do serviço da MAM do Intune falhou.  A aplicação deve continuar num estado não gerido (normal) e o utilizador não deve estar bloqueado.  As tentativas de inscrição serão repetidas periodicamente caso o utilizador se torne licenciado no futuro. |
| ENROLLMENT_SUCCEEDED | A tentativa de inscrição foi concluída com êxito ou o utilizador já está inscrito.  No caso de uma inscrição com êxito, será enviada uma notificação de atualização da política antes desta notificação.  O acesso a dados empresariais deve ser permitido. |
| ENROLLMENT_FAILED | A tentativa de inscrição falhou.  Pode encontrar mais detalhes nos registos do dispositivo.  A aplicação não deve permitir acesso a dados empresariais neste estado, uma vez que foi determinado anteriormente que o utilizador está licenciado para o Intune.|
| WRONG_USER | Apenas um utilizador por dispositivo pode inscrever uma aplicação com o serviço MAM.  Para realizar uma inscrição com êxito como um utilizador diferente, deve primeiro anular todas as inscrições das aplicações inscritas.  Caso contrário, esta aplicação tem de ser inscrita como o utilizador primário.  Esta verificação acontece após a verificação da licença, por isso, o utilizador deve ser impedido de aceder aos dados empresariais até que a aplicação seja inscrita com êxito.|
| UNENROLLMENT_SUCCEEDED | Anulação da inscrição concluída com êxito.|
| UNENROLLMENT_FAILED | O pedido de anulação da inscrição falhou.  Pode encontrar mais detalhes nos registos do dispositivo. |
| PENDING | A tentativa inicial de inscrição do utilizador está em curso.  A aplicação pode bloquear o acesso a dados empresariais até que o resultado da inscrição seja conhecido, mas não é necessário fazê-lo. |
| COMPANY_PORTAL_REQUIRED | O utilizador está licenciado para o Intune, mas a aplicação não pode ser inscrita até que a aplicação Portal da Empresa seja instalada no dispositivo. O SDK da Aplicação do Intune tentará bloquear o acesso à aplicação ao utilizador especificado e direcioná-lo para a instalação da aplicação Portal da Empresa (veja abaixo para obter detalhes). |


### <a name="company-portal-requirement-prompt-override-optional"></a>Ignorar pedido de requisito do Portal da Empresa (opcional)

Se receber o Resultado `COMPANY_PORTAL_REQUIRED`, o SDK bloqueará a utilização das atividades que utilizam a identidade para a qual a inscrição foi solicitada. Em vez disso, o SDK fará com que essas atividades apresentem um pedido para transferir o Portal da Empresa. Se pretender evitar este comportamento na sua aplicação, as atividades poderão implementar `MAMActivity.onMAMCompanyPortalRequired`.

Este método é chamado antes de o SDK apresentar as suas IUs de bloqueio predefinidas. Se a aplicação alterar a identidade da atividade ou anular o registo do utilizador que tentou inscrever-se, o SDK não bloqueará a atividade. Nesta situação, cabe à aplicação evitar a fuga de dados empresariais.

### <a name="notifications"></a>Notificações

Um novo tipo de `MAMNotification` foi adicionado para informar a aplicação que o pedido de inscrição foi concluído.  `MAMEnrollmentNotification` será recebida através da interface `MAMNotificationReceiver`, conforme descrito na secção [Registar para obter notificações do SDK](#register-for-notifications-from-the-sdk).

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}

```

O método `getEnrollmentResult()` devolve o resultado do pedido de inscrição.  Uma vez que `MAMEnrollmentNotification` expande `MAMUserNotification`, a identidade do utilizador para o qual foi tentada a inscrição também está disponível. A aplicação deve implementar a interface `MAMNotificationReceiver` para receber estas notificações, detalhadas na secção [Registar para obter notificações do SDK](#Register-for-notifications-from-the-SDK).

O estado da conta de utilizador registado pode ser alterado quando é recebida uma notificação de inscrição, mas, em alguns casos, não será alterado (por exemplo, se for recebida a notificação `AUTHORIZATION_NEEDED` após um resultado mais informativo como `WRONG_USER`, o resultado mais informativo será mantido como o estado da conta)


## <a name="protecting-backup-data"></a>Proteger dados de cópias de segurança

A partir do Android Marshmallow (API 23), o Android disponibiliza duas formas de as aplicações fazerem cópias de segurança dos dados. Cada opção está disponível para a sua aplicação e requer passos diferentes para garantir que a proteção de dados do Intune é implementada corretamente. Pode ver na tabela abaixo as ações correspondentes necessárias para o comportamento de proteção de dados correto.  Pode ler mais informações sobre os métodos de cópia de segurança no [Guia de API do Android](http://developer.android.com/guide/topics/data/backup.html).

### <a name="auto-backup-for-apps"></a>Cópia de Segurança Automática para Aplicações

O Android começou a disponibilizar [cópias de segurança automáticas completas](https://developer.android.com/guide/topics/data/autobackup.html) para o Google Drive aplicações em dispositivos Android Marshmallow, independentemente da API de destino da aplicação. Em AndroidManifest.xml, se definir explicitamente `android:allowBackup` como **falso**, a sua aplicação nunca será colocada em fila de espera para cópias de segurança pelo Android e os dados "empresariais" permanecerão na aplicação. Neste caso, não são necessárias mais ações.

No entanto, por predefinição, o atributo `android:allowBackup` é definido como verdadeiro, mesmo que `android:allowBackup` não seja especificado no ficheiro de manifesto. Isto significa que todos os dados de aplicações são automaticamente colocados em cópia de segurança na conta do Google Drive do utilizador, um comportamento predefinido que constitui um **risco de fuga de dados**. Por essa razão, o SDK precisa das alterações descritas abaixo para assegurar que a proteção de dados é aplicada.  É importante seguir as orientações abaixo para proteger devidamente os dados de clientes, se quiser que a aplicação seja executada em dispositivos Android Marshmallow.  

O Intune permite-lhe utilizar todas as [funcionalidades da Cópia de Segurança Automática](https://developer.android.com/guide/topics/data/autobackup.html) disponíveis em Android, incluindo a capacidade de definir regras personalizadas no XML, mas tem de seguir os passos abaixo para proteger os seus dados:

1. Se a sua aplicação **não** utilizar o seu próprio BackupAgent personalizado, utilize o MAMBackupAgent predefinido para permitir cópias de segurança automáticas completas, que estejam em conformidade com a política do Intune. Se fizer isto, pode ignorar o atributo do manifesto `android:fullBackupOnly`, dado que não é aplicável para o nosso agente de cópia de segurança. Coloque o seguinte no manifesto da aplicação:

    ```xml
android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```

2. **[Opcional]** Se tiver implementado um BackupAgent personalizado opcional, terá de se certificar de que utiliza um MAMBackupAgent ou MAMBackupAgentHelper. Veja as secções seguintes. Considere mudar para utilizar o **MAMDefaultFullBackupAgent** do Intune (descrito no passo 1), o qual fornece uma cópia de segurança fácil no Android M e posterior.

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

    **Exemplo 3**: se pretender que a sua aplicação tenha cópias de segurança completas de acordo com as suas regras personalizadas definidas num ficheiro XML, defina o atributo e a etiqueta de metadados para o mesmo recurso XML:

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

1. Leia atentamente [Key/Value Backup (Cópia de Segurança Chave/Valor)](https://developer.android.com/guide/topics/data/keyvaluebackup.html) no guia Android, mais concretamente, [xtending BackupAgent (Expandir o BackupAgent)](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) para garantir que a sua implementação do BackupAgent segue as diretrizes do Android.

2. Recorra à sua classe para expandir o `MAMBackupAgent`.

**Cópia de segurança de várias identidades:**

1. Antes de iniciar a cópia de segurança, verifique se os ficheiros ou as memórias intermédias pretendidas têm efetivamente **permissão do administrador de TI para serem guardados em cópia de segurança** em cenários de várias identidades. Disponibilizamos-lhe a função `isBackupAllowed` em `MAMFileProtectionManager` e `MAMDataProtectionManager` para confirmar isso mesmo. Se não for permitida a cópia de segurança de ficheiros ou memórias intermédias de dados, não deverá continuar a inclui-los na sua cópia de segurança.

2. Se em algum momento durante a cópia de segurança pretender fazer uma cópia de segurança das identidades dos ficheiros selecionados no passo 1, terá de chamar `backupMAMFileIdentity(BackupDataOutput data, File … files)` com os ficheiros a partir dos quais planeia extrair dados. Esta ação irá criar automaticamente novas entidades de cópia de segurança e escrevê-las em `BackupDataOutput` por si. Estas entidades serão consumidas automaticamente após o restauro.

**Restauro de várias identidades:**

O guia de Cópia de Segurança de Dados especifica um algoritmo geral para restaurar os dados da aplicação e fornece um exemplo de código na secção [Extending BackupAgent (Expandir o BackupAgent)](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent). Para realizar um restauro de várias identidades com êxito, tem de seguir a estrutura geral fornecida neste exemplo de código dando especial atenção ao seguinte:

1.  Deve utilizar um ciclo `while(data.readNextHeader())`* para percorrer as entidades de cópia de segurança.

2.  Terá de chamar `data.skipEntityData()`* se `data.getKey()`* não corresponder à chave que escreveu na `onBackup`. Sem realizar este passo, os seus restauros podem não ter êxito.

3.  Evite a devolução enquanto está a consumir entidades de cópia de segurança na construção `while(data.readNextHeader())`*, uma vez que as entidades com que escrevemos automaticamente serão perdidas.

* Em que `data` é o nome da variável local do **BackupDataInput** que é transmitido para a aplicação após o restauro.

## <a name="multi-identity-optional"></a>Várias identidades (opcional)

### <a name="overview"></a>Descrição geral
Por predefinição, o SDK da Aplicação do Intune aplica a política à aplicação como um todo. As várias identidades são uma funcionalidade de proteção opcional da aplicação do Intune que pode ser ativada para permitir que a política seja aplicada num nível por identidade. Esta opção requer uma participação da aplicação significativamente maior do que outras funcionalidades de proteção da aplicação.

A aplicação _deve_ informar o SDK sobre quando tenciona alterar a identidade ativa. O SDK também notifica a aplicação quando for necessária uma alteração de identidade. Quando o utilizador inscrever o dispositivo ou a aplicação, o SDK regista esta identidade e considera-a a identidade gerida primária do Intune. Os outros utilizadores na aplicação serão tratados como não geridos, com definições de política não restrita.

> [!NOTE]
> Atualmente, apenas é suportada uma identidade gerida do Intune por dispositivo.

Note que uma identidade é simplesmente definida como uma cadeia. As identidades são **sensíveis às maiúsculas e minúsculas** e os pedidos de identidade ao SDK podem não devolver a mesma utilização de maiúsculas e minúsculas que tinha sido originalmente utilizada ao definir a identidade.


### <a name="enabling-multi-identity"></a>Ativar várias identidades

Por predefinição, todas as aplicações são consideradas aplicações de identidade única. Pode declarar que uma aplicação tem conhecimento de várias identidades ao colocar os seguintes metadados no ficheiro AndroidManifest.xml.

```xml
  <meta-data
    android:name="com.microsoft.intune.mam.MAMMultiIdentity"
    android:value="true" />
```

### <a name="setting-the-identity"></a>Definir a Identidade

Os programadores podem definir a identidade do utilizador da aplicação nos seguintes níveis por ordem decrescente de prioridade:

  1. Nível de thread
  2. Nível de contexto (geralmente Atividade)
  3. Nível de processo

Uma identidade definida no nível de thread prevalece sobre uma identidade definida no nível de Contexto, que prevalece sobre uma identidade definida no nível de processo. Uma identidade definida num Contexto é utilizada apenas em operações de E/S de ficheiros de cenários associados adequados, por exemplo, não tem um Contexto associado. Os seguintes métodos no `MAMPolicyManager` podem ser utilizados para definir a identidade e obter os valores de identidade anteriormente definidos.

```java
  public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

  public static String getUIPolicyIdentity(final Context context);

  public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

  public static String getProcessIdentity();

  public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

  public static String getCurrentThreadIdentity();

  /**
   * Get the currently applicable app policy. Same as
   * MAMComponents.get(AppPolicy.class). This method does
   * not take the context identity into account.
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

>[!NOTE]
> Pode limpar a identidade da aplicação ao defini-la como nula.
>
> A cadeia vazia pode ser utilizada como uma identidade que nunca terá uma política de proteção de aplicações.

#### <a name="results"></a>Resultados
Todos os métodos utilizados para definir a identidade comunicam os valores de resultado através do `MAMIdentitySwitchResult`. Existem quatro valores que podem ser devolvidos:

| Valor devolvido | Cenário |
|--|--|
| SUCCEEDED | A alteração de identidade foi concluída com êxito. |
| NOT_ALLOWED | A alteração de identidade não é permitida. <br><br>Esta situação ocorre em caso de tentativa de mudar para um utilizador gerido diferente que pertença à mesma organização que o utilizador inscrito. Também ocorre em caso de tentativa de definir a identidade de IU (Contexto) quando uma identidade diferente for definida no thread atual. |
| CANCELLED | O utilizador cancelou a alteração de identidade, geralmente ao premir o botão de retrocesso num pedido de PIN ou autenticação. |
| FAILED | A alteração de identidade falhou por um motivo não especificado.|


No caso de definir uma identidade de Contexto, o resultado é reportado de forma assíncrona. Se o Contexto for uma Atividade, o SDK saberá se a alteração de identidade foi efetuada com êxito após a execução da iniciação condicional, o que poderá exigir que o utilizador introduza um PIN ou as credenciais empresariais. É esperado que a aplicação implemente um `MAMSetUIIdentityCallback` para receber este resultado, pode passar nulo para este parâmetro.

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

Também pode definir a identidade de uma atividade diretamente através de um método `MAMActivity` em vez de chamar `MAMPolicyManager.setUIPolicyIdentity`. Utilize o método seguinte para tal:

```java
     public final void switchMAMIdentity(final String newIdentity);
```

Podeeá também substituir um método no `MAMActivity` se pretender que a aplicação seja notificada do resultado de tentativas para alterar a identidade dessa atividade.

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

>[!NOTE]
> Alterar a identidade pode requerer a recriação da atividade. Neste caso, a chamada de retorno `onSwitchMAMIdentityComplete` será entregue na nova instância da atividade.


### <a name="implicit-identity-changes"></a>Alterações de Identidade Implícitas

Além da capacidade da aplicação de definir a identidade, a identidade de um contexto ou thread pode mudar com base na entrada de dados de outra aplicação otimizada pelo Intune com uma política de proteção de aplicações.

#### <a name="examples"></a>Exemplos

  1. Se uma atividade for iniciada a partir de um `Intent` enviado por outra aplicação para MAM, a identidade da atividade será definida com base na identidade real na outra aplicação no ponto em que o `Intent` foi enviado.

  2.  Para serviços, a identidade do thread será definida de forma semelhante durante uma chamada `onStart` ou `onBind`. As chamadas para `Binder` devolvidas do `onBind` também irão definir temporariamente a identidade do thread.

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

    Em que ```AppIdentitySwitchResult``` é SUCCESS ou FAILURE.

O método `onMAMIdentitySwitchRequired` é chamado para todas as alterações de identidade implícitas, exceto nas que forem efetuadas através de um Enlaçamento devolvido de `MAMService.onMAMBind`. As implementações predefinidas de `onMAMIdentitySwitchRequired` chamam de imediato:

*  `reportIdentitySwitchResult(FAILURE)` quando o motivo é RESUME_CANCELLED.

*  `reportIdentitySwitchResult(SUCCESS)` em todos os outros casos.

  Não é esperado que a maioria das aplicações precise de bloquear ou atrasar uma mudança de identidade numa forma diferente, mas se uma aplicação precisar de o fazer, os seguintes pontos têm de ser tidos em conta:

  * Se a alteração de identidade é bloqueada, o resultado é o mesmo como se as definições de partilha de `Receive` tivessem proibido a entrada de dados.

  * Se um Serviço estiver em execução no thread principal, `reportIdentitySwitchResult` **terá** de ser chamado de forma síncrona ou o thread da IU será bloqueado.

  * Para a criação de **Atividade**, `onMAMIdentitySwitchRequired` será chamado antes de `onMAMCreate`. Se a aplicação tiver de mostrar a IU para determinar se a mudança de identidade deve ser permitida, a IU terá de ser apresentada com uma identidade *diferente*.

  * Numa **Atividade**, quando uma alteração para a identidade vazia for pedida com o motivo RESUME_CANCELLED, a aplicação terá de modificar a atividade retomada de forma a mostrar dados consistentes com a mudança de identidade.  Se tal não for possível, a aplicação deverá recusar a mudança e será novamente pedido ao utilizador que fique em conformidade com a política da identidade retomada (por exemplo, ao ver o ecrã de introdução de PIN da aplicação).

    > [!NOTE]
    > Uma aplicação com várias identidades irá sempre receber dados de aplicações geridas e não geridas. É da responsabilidade da aplicação tratar dados de identidades geridas de forma gerida.

  Se uma identidade solicitada for gerida (utilize `MAMPolicyManager.getIsIdentityManaged` para verificar), mas a aplicação não puder utilizar essa conta (por exemplo, porque primeiro têm de ser configuradas contas na aplicação, como contas de e-mail), a mudança de identidade deverá ser recusada.



  ### <a name="file-protection"></a>Proteção de Ficheiros

  Todos os ficheiros têm uma identidade associada na altura da criação, com base na identidade de processo e thread. Esta identidade será utilizada para encriptação de ficheiros e eliminação seletiva. Apenas os ficheiros cuja identidade é gerida e tenha uma política que requeira encriptação serão encriptados. A funcionalidade de eliminação seletiva predefinida do SDK irá eliminar apenas ficheiros associados à identidade gerida para a qual uma eliminação tenha sido solicitada. A aplicação poderá consultar ou alterar a identidade de um ficheiro ao utilizar a classe `MAMFileProtectionManager`.

  ```java
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

        /**
         * Get the protection info on a file.
         *
         * @param file
         *            File to get information on.
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

A etiquetagem de identidade de ficheiros é sensível ao modo offline. Os seguintes pontos deverão ser levados em consideração:

  * Se o Portal da Empresa não estiver instalado, a etiquetagem de identidade dos ficheiros não poderá ser efetuada.

  * Se o Portal da Empresa estiver instalado, mas a aplicação não estiver a política da MAM do Intune instalada, os ficheiros não poderão ter uma etiquetagem de identidade de forma fiável.

  * Quando a etiquetagem de identidade for disponibilizada, todos os ficheiros anteriormente criados serão tratados como pessoais/não geridos (pertencentes à identidade de cadeia vazia), a menos que a aplicação tenha sido anteriormente instalada como aplicação gerida com identidade única. Nesse caso, serão tratados como pertencentes ao utilizador inscrito.

### <a name="directory-protection"></a>Proteção de Diretório

Os diretórios podem ser protegidos com recurso ao mesmo método `protect` utilizado para proteger ficheiros. Tenha em atenção que a proteção do diretório é aplicada recursivamente para todos os ficheiros e subdiretórios contidos no diretório e para novos ficheiros criados no diretório. Como a proteção de diretório é aplicada recursivamente, a chamada `protect` pode demorar algum tempo a concluir no caso de diretórios muito grandes. Por esse motivo, as aplicações a aplicar proteção num diretório que contém um grande número de ficheiros poderão querer executar a função `protect` de modo assíncrono no thread de segundo plano.

### <a name="data-protection"></a>Proteção de dados

Não é possível etiquetar um ficheiro como pertencente a identidades múltiplas. As aplicações que têm de armazenar dados pertencentes a utilizadores diferentes no mesmo ficheiro podem fazê-lo manualmente ao utilizar as funcionalidades fornecidas por `MAMDataProtectionManager`. Isto permite à aplicação encriptar dados e associá-los a um utilizador específico. Os dados encriptados são adequados para armazenamento no disco de um ficheiro. Pode consultar os dados associados à identidade e os ficheiros podem ser desencriptados posteriormente.

As aplicações que utilizam o `MAMDataProtectionManager` devem implementar um recetor para a notificação `MANAGEMENT_REMOVED`. Após a conclusão desta notificação, as memórias intermédias que estavam protegidas através desta classe deixarão de ser legíveis caso a encriptação de ficheiros tenha sido ativada quando as memórias intermédias foram protegidas. Uma aplicação pode corrigir esta situação ao chamar MAMDataProtectionManager.unprotect em todas as memórias intermédias durante esta notificação. Tenha em atenção que também é seguro chamar a função proteger durante esta notificação se pretender manter as informações de identidade – a encriptação desativada é garantida durante a notificação.

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

Se a aplicação fornecer dados empresariais além de um **ParcelFileDescriptor** através de um **ContentProvider**, a aplicação deverá chamar o método `isProvideContentAllowed(String)` no `MAMContentProvider` e transmitir o UPN da identidade do proprietário (nome principal do utilizador) para o conteúdo. Se esta função devolver “falso”, os conteúdos *poderão não* ser devolvidos ao chamador. Os descritores de ficheiros devolvidos através de um fornecedor de conteúdos são processados automaticamente, com base na identidade do ficheiro.

### <a name="selective-wipe"></a>Eliminação Seletiva

Se uma aplicação se registar para a notificação `WIPE_USER_DATA`, não receberá a vantagem do comportamento predefinido da eliminação seletiva por parte do SDK. Para aplicações com conhecimento de várias identidades, esta perda pode ser mais significativa, dado que a eliminação seletiva predefinida da MAM elimina apenas os ficheiros cuja identidade é visada para eliminação.

Se uma aplicação com conhecimento de várias identidades pretender que a eliminação seletiva predefinida da MAM seja realizada _**e**_ pretender realizar as suas próprias ações na eliminação, esta deverá registar-se para as notificações de `WIPE_USER_AUXILIARY_DATA`. Esta notificação será enviada imediatamente pelo SDK antes de executar a eliminação seletiva predefinida do SDK. Uma aplicação nunca deve ser registada para WIPE_USER_DATA e WIPE_USER_AUXILIARY_DATA em simultâneo.


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

## <a name="limitations"></a>Limitações

### <a name="file-size-limitations"></a>Limitações do tamanho do ficheiro

Para bases de códigos grandes executadas sem [ProGuard](http://proguard.sourceforge.net/), as limitações do formato de ficheiro executável Dalvik podem tornar-se um problema. Mais concretamente, podem ocorrer as seguintes limitações:

1.  O limite de 65K nos campos.
2.  O limite de 65K nos métodos.



### <a name="policy-enforcement-limitations"></a>Limitações de imposição de políticas

* **Captura de Ecrã**: o SDK não consegue impor um novo valor de definição de captura de ecrã em Atividades já ocorridas em Activity.onCreate, o que pode resultar num período de tempo em que a aplicação foi configurada para desativar capturas de ecrã, mas em que estas ainda podem ser criadas.

* **Utilizar Resoluções de Conteúdos**: a política do Intune de “transferência ou receção” pode bloquear ou bloquear parcialmente a utilização de uma resolução de conteúdos para aceder ao fornecedor de conteúdos noutra aplicação. Isto fará com que os métodos ContentResolver devolvam um valor nulo ou gerem um valor de falha (por exemplo, `openOutputStream` irá gerar `FileNotFoundException` em caso de bloqueio). A aplicação pode determinar se uma falha ao escrever dados através de uma resolução de conteúdos foi causada pela política (ou seria causada pela política) ao efetuar a chamada:

    ```java
    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI);
    ```

### <a name="exported-services"></a>Serviços exportados

 o ficheiro AndroidManifest.xml incluído no SDK da Aplicação do Intune contém **MAMNotificationReceiverService**, o qual tem de ser um serviço exportado para permitir ao Portal da Empresa enviar notificações para uma aplicação otimizada. O serviço verifica o autor da chamada para assegurar que apenas o Portal da Empresa está autorizado a enviar notificações.



## <a name="expectations-of-the-sdk-consumer"></a>Expectativas do consumidor do SDK

O SDK do Intune mantém o contrato fornecido pela API Android, embora possam ser acionadas condições de falha mais frequentemente como resultado da imposição de políticas. Estas melhores práticas para Android reduzirão a probabilidade de falhas:

* As funções do SDK Android que podem devolver valores nulos têm uma maior probabilidade de ter um valor nulo agora.  Para minimizar os problemas, certifique-se de que as verificações de valores nulos estão nos locais corretos.

* As funcionalidades que podem ser verificadas têm de o ser através das respetivas APIs de substituição da MAM.

* As funções derivadas têm de fazer chamadas através das respetivas versões de superclasses.

* Evitar utilizar qualquer API de uma forma ambígua. Por exemplo, utilizar `Activity.startActivityForResult` sem verificar o requestCode causará um comportamento estranho.

## <a name="recommended-android-best-practices"></a>Melhores práticas recomendadas para Android

* Todos os projetos de biblioteca devem partilhar o mesmo android:package sempre que possível. Assim, não falhará esporadicamente no tempo de execução, uma vez que se trata puramente de um problema de tempo de compilação. As versões mais recentes do SDK da Aplicação do Intune irão remover algumas da redundâncias.

* Utilizar as ferramentas de compilação do SDK Android.

* Remover todas as bibliotecas desnecessárias e não utilizadas (por exemplo, android.support.v4)
