---
title: "Guia para Programadores do SDK da Aplicação do Microsoft Intune para Android | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2915cca314b489bbcb590d01b03a0b38134fa619
ms.openlocfilehash: d2e4b6903d86b79edd9c758b2ce51733831e785a


---

# Guia para Programadores do SDK da Aplicação do Microsoft Intune para Android

> [!NOTE]
> Pode ser útil ler primeiro a [Descrição Geral do SDK da Aplicação do Intune](intune-app-sdk.md), que abrange as funcionalidades atuais do SDK e descreve como preparar a integração em cada plataforma suportada. 

# O que está no SDK 

O SDK da Aplicação do Intune para Android é uma biblioteca do Android padrão sem dependências externas. O SDK é composto por:  

* **`Microsoft.Intune MAM.SDK.jar`**: as interfaces necessárias para ativar o MAM numa aplicação, além de permitir a interoperabilidade com a aplicação Portal da Empresa do Microsoft Intune. As aplicações têm de especificá-lo como referência da biblioteca do Android.

*  **`Microsoft.Intune.MAM.SDK.Support.v4.jar`**: as interfaces necessárias para ativar o MAM nas aplicações que tiram partido da biblioteca de suporte v4 do Android.  As aplicações que precisam deste suporte têm de referenciar diretamente o ficheiro jar. 

* **`Microsoft.Intune.MAM.SDK.Support.v7.jar`**: as interfaces necessárias para ativar o MAM nas aplicações que tiram partido da biblioteca de suporte v7 do Android.   As aplicações que precisam deste suporte têm de referenciar diretamente o ficheiro jar

* **Diretório de recursos**: os recursos (como, por exemplo, cadeias) nos quais se baseiam o SDK. 

* **`Microsoft.Intune.MAM.SDK.aar`**: os componentes do SDK, à exceção dos ficheiros jars Support.V4 e Support.V7. Este ficheiro pode ser utilizado em vez dos componentes individuais se o sistema de compilação suportar ficheiros AAR.

* **`AndroidManifest.xml`**: os pontos de entrada adicionais e os requisitos da biblioteca. 

* **`THIRDPARTYNOTICES.TXT`**: aviso de atribuição que reconhece código de terceiros e/ou OSS que será compilado na sua aplicação. 

# Requisitos 

O SDK da Aplicação do Intune é um projeto Android compilado. Como resultado, é amplamente agnóstico relativamente à versão do Android que a aplicação utiliza nas respetivas versões de API mínimas ou de destino. O SDK suporta a API Android 14 (Android 4.0+) para Android 24. 

# Como funciona o SDK da Aplicação Intune 

Para ativar políticas de gestão de aplicações, o SDK da Aplicação do Intune requer alterações ao código fonte da aplicação. Estas alterações são feitas através da substituição das classes base Android por classes geridas equivalentes, referidas no documento com o prefixo `MAM`. As classes do SDK estão entre a classe base Android e a própria versão derivada da aplicação dessa classe.  Utilizando uma atividade como exemplo, pode ficar com uma hierarquia de herança semelhante a: `Activity ->MAMActivity->AppSpecificActivity`.

Quando `AppSpecificActivity` pretende interagir com o respetivo elemento principal, por exemplo, `super.onCreate())`, `MAMActivity` é a superclasse apesar de estar na hierarquia de herança e de substituir alguns métodos. As aplicações Android têm um único modo e têm acesso a todo o sistema através do respetivo objeto de Contexto.  Por outro lado, as aplicações que tenham incorporado o SDK da Aplicação do Intune têm modos duplos, uma vez que as aplicações continuam a aceder ao sistema através do objeto de Contexto, mas, dependendo da Atividade base utilizada, o objeto de Contexto será fornecido pelo Android ou será multiplexado inteligentemente entre uma vista restrita do sistema e o Contexto fornecido pelo Android.

O SDK da Aplicação do Intune para Android baseia-se na presença da aplicação Portal da Empresa no dispositivo para ativar políticas de MAM. Se a aplicação Portal da Empresa não estiver presente, o comportamento da aplicação ativada pelo MAM não será alterado e funcionará como qualquer outra aplicação móvel. Se o Portal da Empresa estiver instalado e tiver uma política para o utilizador, os pontos de entrada do SDK são inicializados de forma assíncrona. A inicialização só é necessária se o processo for criado inicialmente pelo Android. Durante a inicialização, é estabelecida uma ligação à aplicação Portal da Empresa e é transferida a política de restrição de aplicações.  

# Como integrar no SDK da Aplicação do Intune
 
Conforme realçado anteriormente, o SDK requer alterações ao código fonte da aplicação para ativar políticas de gestão de aplicações. Seguem-se os passos necessários para ativar o MAM na sua aplicação: 

## Substitua as classes, os métodos e as atividades pelos respetivos MAM equivalentes (obrigatório) 

* As classes base Android têm de ser substituídas pelo respetivo MAM equivalente. Para fazê-lo, localize todas as instâncias das classes apresentadas na tabela abaixo e substitua-as pelo SDK da Aplicação do Intune equivalente.  

    | Classe Android | Substituição do SDK da Aplicação do Intune |
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
    | android.app.PendingIntent | MAMPendingIntent |
    | android.app.Service | MAMService |
    | android.app.TabActivity | MAMTabActivity |
    | android.app.TaskStackBuilder | MAMTaskStackBuilder |
    | android.app.backup.BackupAgent | MAMBackupAgent |
    | android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
    | android.app.backup.FileBackupHelper | MAMFileBackupHelper |
    | android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
    | android.content.BroadcastReceiver | MAMBroadcastReceiver |
    | android.content.ContentProvider | MAMContentProvider |
    | android.os.Binder | MAMBinder* |
    | android.provider.DocumentsProvider | MAMDocumentsProvider |
    | android.preference.PreferenceActivity | MAMPreferenceActivity |

    *Só é necessário substituir Binder por MAMBinder se Binder não for gerado a partir de uma interface AIDL.

    **Microsoft.Intune.MAM.SDK.Suppout.v4.jar**:

    | MAM do Intune da Classe Android | Substituição do SDK |
    |--|--|
    | android.support.v4.app.DialogFragment | MAMDialogFragment
    | android.support.v4.app.FragmentActivity | MAMFragmentActivity
    | android.support.v4.app.Fragment | MAMFragment
    | android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
    | android.support.v4.content.FileProvider | MAMFileProvider
    
    **Microsoft.Intune.MAM.SDK.Suppout.v7.jar**:

    |Classe Android | Substituição do SDK de MAM do Intune |
    |--|--|
    |android.support.v7.app.ActionBarActivity | MAMActionBarActivity |


* Se utilizar um ponto de entrada Android que foi substituído pelo MAM equivalente, tem de ser utilizada uma versão alternativa do ciclo de vida do ponto de entrada (à exceção da classe `MAMApplication`).

    Por exemplo, quando efetuar a derivação de `MAMActivity`, em vez de substituir `onCreate` e chamar `super.onCreate`, a Atividade tem de substituir `onMAMCreate` e chamar`uper.onMAMCreate`. Isto permite a restrição do início da Atividade (entre outras) em determinados casos. 

# Ativar funcionalidades que requerem a participação da aplicação 

Existem algumas políticas que o SDK não pode implementar por si só. Para permitir à aplicação controlar o respetivo comportamento no âmbito destas funcionalidades, expomos várias APIs que pode encontrar na interface `AppPolicy` , incluída abaixo.  

    /**
     * External facing app policies.
     */
    public interface AppPolicy {
        /**
         * Restrict where an app can save personal data.
         * 
         * @return True if the app is allowed to save to personal data stores;
         *         false otherwise.
         */
        boolean getIsSaveToPersonalAllowed();
    
        /**
         * Check if policy prohibits saving to a content provider location.
         * 
         * @param location
         *            a content URI to check
         * @return True if location is not a content URI or if policy does not 
         *         prohibit saving to the content location.
         */
        boolean getIsSaveToLocationAllowed(android.net.Uri location); 
    
        /**
         * Whether the SDK PIN prompt is enlightened for the app.
         * 
         * @return True if the PIN is enabled. False otherwise.
         */
        boolean getIsPinRequired();
        /**
         * Whether the Intune Managed Browser is required to open web links.
         *
         * @return True if the Managed Browser is required, false otherwise
         */
        boolean getIsManagedBrowserRequired();
    }

## Permitir o controlo de administração de TI sobre o comportamento de gravação das aplicações

Muitas aplicações implementam funcionalidades que permitem ao utilizador final guardar os ficheiros localmente ou noutro serviço. O SDK da Aplicação do Intune permite aos administradores de TI aplicar restrições de políticas que considerem mais adequadas na organização, para proteger contra fugas de dados.  Uma das políticas que o administrador pode controlar é se o utilizador final pode guardar num arquivo de dados pessoal. Isto inclui guardar numa localização local, num cartão SD ou em serviços de cópias de segurança. A participação da aplicação é necessária para ativar a funcionalidade. Se a aplicação permitir guardar em localizações pessoais ou na nuvem diretamente a partir da aplicação, tem de implementar esta funcionalidade para garantir que o administrador de TI pode controlar se a gravação numa localização é permitida ou não. A API abaixo permite à aplicação saber se a gravação num arquivo pessoal é permitida pela política de administração atual. Em seguida, a aplicação pode impor a política, uma vez que tem conhecimento do arquivo de dados pessoal disponível para o utilizador final através da aplicação.  

Para determinar se a política é imposta, a aplicação pode efetuar a seguinte chamada: 

    MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();

**Nota**: MAMComponents.get(AppPolicy.class) devolverá sempre uma Política de Aplicação não nula, mesmo se o dispositivo ou aplicação não estiver sob gestão. 

## Permitir à aplicação detetar se é necessária uma Política de PIN
 
 Existem políticas adicionais em que a aplicação pode pretender desativar algumas das suas funcionalidades, de modo a não duplicar funcionalidades no SDK da Aplicação do Intune. Por exemplo, se a aplicação tiver a sua própria experiência de utilizador de PIN, pode querer desativá-la caso o SDK esteja configurado para exigir que o utilizador final introduza um PIN. 

Para determinar se está configurada uma política de PIN para exigir a introdução do PIN periodicamente, a aplicação pode efetuar a seguinte chamada: 

    MAMComponents.get(AppPolicy.class).getIsPinRequired();

## Registar para obter notificações do SDK  

O SDK da Aplicação do Intune permite à sua aplicação ter controlo sobre o comportamento quando o administrador de TI utiliza determinadas políticas, como, por exemplo, uma política de eliminação remota. Para fazê-lo, terá de se registar para obter notificações do SDK ao criar uma classe `MAMNotificationReceiver` e registando-a em `MAMNotificationReceiverRegistry`. Isto é feito ao indicar o recetor e o tipo de notificação que este pretende receber em  `App.onCreate`, como ilustra o exemplo abaixo:
 
    @Override
      public void onCreate() {
            super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class).registerReceiver(
    new ToastNotificationReceiver(), MAMNotificationType.WIPE_USER_DATA);
    }

`MAMNotificationReceiver` recebe simplesmente notificações. Algumas notificações são processadas diretamente pelo SDK, ao passo que outras requerem a participação da aplicação. A aplicação tem de devolver verdadeiro ou falso a partir de uma notificação. Deve sempre devolver verdadeiro, a menos que qualquer ação que tentou fazer como resultado da notificação tenha falhado. Esta falha pode ser comunicada ao serviço do Intune, como, por exemplo, se a aplicação indicar que não conseguiu eliminar os dados do utilizador. É seguro bloquear em `MAMNotificationReceiver.onReceive`; a chamada de retorno não está em execução no thread da IU. 

A interface MAMNotificationReceiver está incluída abaixo, conforme definida no SDK: 

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

As notificações que se seguem são enviadas para a aplicação e algumas delas podem requerer a participação da aplicação: 

* **Notificação `WIPE_USER_DATA`**: esta notificação é enviada numa classe `MAMUserNotification`. Quando esta notificação é recebida, a aplicação deve eliminar todos os dados associados à identidade transmitida com `MAMUserNotification`. Atualmente, esta notificação é enviada durante a anulação da inscrição do serviço do Intune. Geralmente, o nome principal do utilizador é especificado durante o processo de inscrição. Se se tiver registado para obter esta notificação, a sua aplicação tem de garantir que todos os dados do utilizador foram eliminados. Se não se registar para obtê-la, será aplicado o comportamento de eliminação seletiva predefinido. 

* **Notificação `WIPE_USER_AUXILIARY_DATA`**: as aplicações podem registar-se para obter esta notificação se quiserem utilizar o SDK da Aplicação do Intune para fazer a eliminação predefinida, mas ainda pretenderem remover alguns dados auxiliares quando ocorrer a eliminação.  

* **Notificação `REFRESH_POLICY`**: esta notificação é enviada numa MAMNotification sem informações adicionais. Quando esta notificação é recebida, qualquer política em cache deve deixar de ser considerada inválida e, por conseguinte, deve verificar qual é a política. Regra geral, isto é processado pelo SDK; no entanto, deve ser processado pela aplicação se a política for utilizada de qualquer forma persistente. 

## Tipos e métodos pendentes 

Depois de derivar de um dos pontos de entrada de MAM, pode utilizar o Contexto tal como faria normalmente, em Atividades de inícios, através do respetivo `PackageManager`, etc.  `PendingIntents` são uma exceção a esta regra. Quando chamar estas classes, terá de alterar o nome da classe. Por exemplo, em vez de utilizar `PendingIntent.get*`, `MAMPendingIntents.get*` . 

Em alguns casos, um método disponível na classe Android foi marcado como final na classe de substituição de MAM. Neste caso, a classe de substituição de MAM fornece um método com um nome semelhante (geralmente, com o sufixo "MAM"), que deve ser substituído. Por exemplo, em vez de substituir `ContentProvider.query`, substituirá `MAMContentProvider.queryMAM`. O compilador de Java deve impor as restrições finais para impedir a substituição acidental do método original em vez do MAM equivalente. 

# Proteger dados de cópias de segurança 

A partir do Android Marshmallow (API 23), o Android disponibiliza agora duas formas de as aplicações fazerem cópias de segurança dos dados. Estas opções estão disponíveis para utilização na sua aplicação e requerem vários passos para assegurar que a proteção de dados de MAM é aplicada adequadamente. Pode ver a tabela abaixo para obter uma descrição geral rápida das ações correspondentes necessárias para o comportamento de proteção de dados correto.  Também pode encontrar mais informações sobre as cópias de segurança do Android no [Guia de Cópia de Segurança de Dados para Programadores Android](http://developer.android.com/guide/topics/data/backup.html.). 

## Cópia de segurança completa automática

No Android M, o Android começou a disponibilizar cópias de segurança completas automáticas para aplicações, independentemente da API de destino, quando são executadas em dispositivos Android M. Desde que o atributo `android:allowBackup` não seja falso, a aplicação receberá cópias de segurança completas e não filtradas da respetiva aplicação. Esta opção origina um risco de fuga de dados, pelo que o SDK precisa das alterações descritas na tabela abaixo para assegurar que a proteção de dados é aplicada.  É importante seguir as diretrizes indicadas abaixo para proteger corretamente os dados dos clientes.  Se definir `android:allowBackup=false` , a sua aplicação nunca será colocada em fila de espera para cópias de segurança pelo sistema operativo e não terá mais ações para MAM, uma vez que não existirá nenhuma cópia de segurança
 
 ## Cópias de segurança “chave/valor”

Esta opção está disponível para todas as APIs e utiliza `BackupAgent` e `BackupAgentHelper`. 

### Utilizar BackupAgentHelper

`BackupAgentHelper` é muito mais simples de implementar do que o `BackupAgent`, tanto em termos de funcionalidade Android nativa, como de integração de MAM. `BackupAgentHelper` permite ao programador registar ficheiros completos e preferências partilhadas no `FileBackupHelper` ou no `SharedPreferencesBackupHelper`, respetivamente, os quais são adicionados em seguida ao `BackupAgentHelper` após a criação. 

### Utilizar BackupAgent

`BackupAgent` permite-lhe ser muito mais explícito sobre os dados que farão parte da cópia de segurança. No entanto, esta opção significa que não poderá tirar partido da estrutura de cópias de segurança do Android.  Uma vez que a si lhe cabe uma boa parte de responsabilidade quanto à implementação, existem mais passos necessários para garantir a proteção de dados adequada a partir do MAM. Uma vez que a maior parte do trabalho é feita por si, o programador, a integração do MAM é ligeiramente mais envolvida. 

#### A aplicação não tem um agente de cópia de segurança
  
Estas são as opções do programador quando `Android:allowbBackup =true`:

##### Cópia de segurança completa de acordo com um ficheiro de configuração: 

Forneça um recurso na etiqueta de metadados `com.microsoft.intune.mam.FullBackupContent` no seu manifesto. Por exemplo,
    `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

Adicione o atributo seguinte na etiqueta `<application>` : `android:fullBackupContent="@xml/my_scheme"`, em que `my_scheme` é um recurso XML da sua aplicação. 

##### Cópia de segurança completa sem exclusões 

Fornecer uma etiqueta no manifesto como `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />` 
 
Adicione o atributo seguinte na etiqueta `<application>`: `android:fullBackupContent="true"`.

#### A aplicação tem um agente de cópia de segurança

Siga as recomendações nas secções `BackupAgent` e `BackupAgentHelper` , conforme descrito acima 

Considere mudar para utilizar o nosso `MAMDefaultFullBackupAgent`, o qual fornece uma cópia de segurança fácil no Android M. 

### Antes de fazer a cópia de segurança

Antes de iniciar a cópia de segurança, tem de verificar se é realmente permitido fazê-la para os ficheiros ou memórias intermédias de dados pretendidos. Disponibilizámos-lhe uma função `isBackupAllowed` em `MAMFileProtectionManager` e `MAMDataProtectionManager` para confirmar isso mesmo. Se não for permitida a cópia de segurança de ficheiros ou memórias intermédias de dados, não deve tentar continuar a utilizá-los na sua cópia de segurança.

Se em algum momento durante a cópia de segurança pretender fazer uma cópia de segurança das identidades dos ficheiros selecionados no passo 1, tem de chamar `backupMAMFileIdentity(BackupDataOutput data, File … files)`. Esta ação irá criar automaticamente novas entidades de cópia de segurança e escrevê-las em `BackupDataOutput` por si. Estas entidades serão consumidas automaticamente após o restauro. 

## Configurar a Azure Directory Authentication Library (ADAL)  

O SDK depende da ADAL nos cenários de autenticação e início condicional, os quais requerem que as aplicações tenham alguma quantidade de configuração do Azure Active Directory. Os valores de configuração são comunicados ao SDK através de metadados `AndroidManifest` . Para configurar a sua aplicação e ativar uma autenticação adequada, adicione o seguinte ao nó da aplicação em `AndroidManifest`. Algumas destas configurações apenas são necessárias se a aplicação utilizar a ADAL para autenticação no geral; nesse caso, necessitará dos valores específicos que a aplicação utiliza para se registar no AAD. Esta configuração é feita para garantir que o utilizador final não recebe o pedido de autenticação duas vezes devido ao facto de o AAD reconhecer dois valores de registo separados: um da aplicação e outro do SDK. 

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

### Configurações comuns da ADAL 

Abaixo são apresentadas as configurações comuns para os valores explicados acima. 

#### A aplicação não integra a ADAL

* A autoridade tem de ser definida para o ambiente pretendido onde foram configuradas contas do AAD.

* SkipBroker tem de ser definido como verdadeiro.

#### A aplicação integra a ADAL

* A autoridade tem de ser definida para o ambiente pretendido onde foram configuradas contas do AAD.

* O ID de cliente tem de ser definido como o ID de cliente da aplicação.

* `NonBrokerRedirectURI` deve ser definido como um URI de redirecionamento válido para a aplicação.
    * Or `urn:ietf:wg:oauth:2.0:oob` tem de ser configurado como um URI de redirecionamento do AAD válido.

* SkipBroker tem de ser definido como falso (ou estar ausente)

* O AAD tem de ser configurado para aceitar o URI de redirecionamento do mediador.

#### A aplicação integra a ADAL, mas não suporta a aplicação AAD Authenticator.

* A autoridade tem de ser definida para o ambiente pretendido onde foram configuradas contas do AAD.

* O ID de cliente tem de ser definido como o ID de cliente da aplicação.

* `NonBrokerRedirectURI` tem de ser definido como um URI de redirecionamento válido para a aplicação.

    * Or `urn:ietf:wg:oauth:2.0:oob` deve ser configurado como um URI de redirecionamento do AAD válido.

## Como ativar o registo no SDK 

O registo é feito através da estrutura `java.util.logging` . Para receber os registos, configure o registo global conforme descrito em [Java technical guide](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html). Consoante a aplicação, `App.onCreate` é, normalmente, o melhor local para iniciar o registo. Tenha em atenção que as mensagens do Registo são codificadas pelo nome de classe, o qual poderá estar ocultado.

# Limitações de Plataforma Conhecidas 

## Limitações de Tamanho de Ficheiro 

No Android, as limitações do formato de ficheiro executável Dalvik podem tornar-se um problema para bases de códigos grandes executadas sem o ProGuard. Mais concretamente, podem ocorrer as seguintes limitações: 

* O limite de 65K nos campos.

* O limite de 65K nos métodos.

Se forem incluídos muitos projetos, cada android:package obterá uma cópia de R que irá aumentar, significativamente, o número de campos à medida que forem adicionadas bibliotecas. As seguintes recomendações podem ajudar a atenuar esta limitação:
 
* Todos os projetos de biblioteca devem partilhar o mesmo android:package sempre que possível. Isto não falhará esporadicamente no campo, uma vez que se trata puramente de um problema de tempo de compilação.   Além disso, as versões mais recentes do SDK Android irão pré-processar os ficheiros DEX para remover parte da redundância. Desta forma, a distância dos campos é reduzida ainda mais.

* Utilizar as ferramentas de compilação mais recentes do SDK Android.

* Remover todas as bibliotecas desnecessárias e não utilizadas (por exemplo, `android.support.v4`)

## Limitações de Imposição de Políticas

**Captura de Ecrã**: o SDK não consegue impor um novo valor de definição de captura de ecrã em Atividades já ocorridas em Activity.onCreate, o que pode resultar num período de tempo em que a aplicação foi configurada para desativar capturas de ecrã, mas em que estas ainda podem ser criadas.

**Utilizar Resoluções de Conteúdos*: a política de transferência ou receção pode bloquear ou bloquear parcialmente a utilização de uma resolução de conteúdos para aceder ao fornecedor de conteúdos noutra aplicação. Isto fará com que os métodos ContentResolver devolvam um valor nulo ou gerem um valor de falha (por exemplo, `openOutputStream` irá gerar `FileNotFoundException` em caso de bloqueio). A aplicação pode determinar se uma falha ao escrever dados através de uma resolução de conteúdos foi causada pela política (ou seria causada pela política) ao efetuar a chamada:

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**Serviços Exportados**: o ficheiro `AndroidManifest.xml` incluído no SDK da Aplicação do Intune contém `MAMNotificationReceiverService`, o qual tem de ser um serviço exportado para permitir ao Portal da Empresa enviar notificações para uma aplicação otimizada. O serviço verifica o autor da chamada para assegurar que apenas o Portal da Empresa está autorizado a enviar notificações. 

# Melhores Práticas Recomendadas para Android 

O SDK do Intune mantém o contrato fornecido pela API Android, embora possam ser acionadas condições de falha mais frequentemente como resultado da imposição de políticas. Estas melhores práticas para Android reduzirão a probabilidade de falhas: 

* As funções do SDK Android que podem devolver valores nulos têm uma maior probabilidade de ter um valor nulo agora.  Para minimizar os problemas, certifique-se de que as verificações de valores nulos estão nos locais corretos.

* As funcionalidades que podem ser verificadas têm de o ser através das respetivas APIs de SDK.

* As funções derivadas têm de fazer chamadas através das respetivas versões de superclasses.

* Evitar utilizar qualquer API de uma forma ambígua. Por exemplo, `Activity.startActivityForResult/onActivityResult` sem verificar o requestCode causará um comportamento estranho.



<!--HONumber=Jun16_HO4-->


