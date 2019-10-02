---
title: Introdução ao SDK da Aplicação Microsoft Intune
description: Ative rapidamente a sua aplicação móvel para a gestão de aplicações móveis (MAM) com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: bfe84b9bff41a8f715a9288ee93a2e78e52f7d34
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730344"
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Introdução ao SDK da Aplicação Microsoft Intune

Este guia o ajudará a habilitar rapidamente seu aplicativo móvel para dar suporte a políticas de proteção de aplicativo com Microsoft Intune. Será útil compreender primeiro os benefícios do SDK da Aplicação Intune, conforme explicado na [Descrição Geral do SDK da Aplicação Intune](app-sdk.md).

O SDK da Aplicação Intune suporta cenários semelhantes entre iOS e Android e destina-se a criar uma experiência consistente para os administradores de TI entre as plataformas. Mas há pequenas diferenças no suporte a determinados recursos, devido às diferenças e às limitações da plataforma.

## <a name="register-your-store-app-with-microsoft"></a>Registar a aplicação da loja no Microsoft

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>Se a sua aplicação for interna da organização e não estiver publicamente disponível:

Você _**não precisa**_ registrar seu aplicativo. Para [aplicativos LOB (linha de negócios)](../apps/apps-add.md#app-types-in-microsoft-intune) internos que foram escritos por ou para sua empresa, o administrador de ti implantará o aplicativo internamente. O Intune detectará que o aplicativo foi criado com o SDK e permitirá que o administrador de ti aplique políticas de proteção de aplicativo a ele. Pode avançar para a secção [Integrar a política de proteção de aplicações na sua aplicação iOS ou Android](#enable-your-ios-or-android-app-for-app-protection-policy).

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Se a sua aplicação for lançada numa loja de aplicações pública, como a Apple App Store ou o Google Play:

Primeiro, _**tem**_ de registar a sua aplicação com o Microsoft Intune e aceitar os termos de registo. Os administradores de ti podem aplicar uma política de proteção de aplicativo ao aplicativo gerenciado, que será listado como um [aplicativo de parceiro protegido do Intune](../apps/apps-supported-intune-apps.md#partner-apps).

Até o registo ser concluído e confirmado pela equipa do Microsoft Intune, os administradores do Intune não terão a opção de aplicar a política de proteção de aplicações na ligação avançada da sua aplicação. A Microsoft também vai adicionar a sua aplicação à respetiva [página de Parceiros do Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps). Nesta página, o ícone da aplicação será apresentado para mostrar que suporta políticas de proteção de aplicações do Intune.

### <a name="the-registration-process"></a>O processo de registro
Para iniciar o processo de registo, e se ainda não estiver a trabalhar com um contacto da Microsoft, preencha o [Microsoft Intune App Partner Questionnaire](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR80SNPjnVA1KsGiZ89UxSdVUMEpZNUFEUzdENENOVEdRMjM5UEpWWjJFVi4u) (Questionário para Parceiros de Aplicação do Microsoft Intune).

Utilizaremos os endereços de e-mail listados na sua resposta do questionário para entrar em contacto e continuar o processo de registo. Além disso, utilizamos o seu endereço de e-mail de registo para contactá-lo caso surja alguma questão.

> [!NOTE]
> Todas as informações recolhidas no questionário e através da correspondência por e-mail com a equipa do Microsoft Intune respeitarão a [Declaração de Privacidade da Microsoft](https://www.microsoft.com/privacystatement/default.aspx).

**O que pode esperar no processo de registo**:

1. Após submeter o questionário, vamos contactá-lo através do seu endereço de e-mail de registo, para confirmar a receção bem-sucedida ou para pedir informações adicionais para concluir o registo.

2. Depois de recebermos todas as informações necessárias, ser-lhe-á enviado o Contrato de Parceiro de Aplicações do Microsoft Intune para assinar. Este contrato descreve os termos que a sua empresa tem de aceitar antes de se tornar parceira de aplicações do Microsoft Intune.

3. Também receberá uma notificação quando a sua aplicação for registada com êxito no serviço Microsoft Intune e estiver em destaque no site dos [parceiros do Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

4. Por fim, a ligação avançada da sua aplicação será adicionada à próxima atualização mensal do Serviço Intune. Por exemplo, se as informações de registo estiverem concluídas em julho, a ligação avançada será suportada em meados de agosto.

Se a ligação avançada da aplicação for alterada no futuro, terá de voltar a registar a sua aplicação.

> [!NOTE]
> Informe-nos se atualizar a sua aplicação com uma nova versão do SDK da Aplicação Intune.

## <a name="download-the-sdk-files"></a>Transferir os ficheiros do SDK

Os SDKs da Aplicação Intune para iOS e Android nativos estão alojados numa conta do Microsoft GitHub. Estes repositórios públicos contêm os ficheiros do SDK para iOS e Android nativo, respetivamente:

* [SDK da Aplicação Intune para iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [SDK da Aplicação Intune para Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

Se a sua aplicação for uma aplicação Xamarin, utilize esta variante do SDK:

* [Enlaces Xamarin do SDK da Aplicação Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)

Recomendamos que se inscreva numa conta do GitHub que pode utilizar para bifurcar e obter dados dos nossos repositórios. O GitHub permite que os programadores comuniquem com a nossa equipa do produto, coloquem questões e recebam respostas rápidas, vejam notas de versão e enviem feedback à Microsoft. Se tiver perguntas sobre o GitHub do SDK da Aplicação Intune, contacte msintuneappsdk@microsoft.com.

## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>Integrar a política de proteção de aplicações na sua aplicação iOS ou Android

Irá precisar de um dos seguintes guias para programadores para o ajudar a integrar o SDK da Aplicação Intune na sua aplicação:

* **[Guia do desenvolvedor do SDK de aplicativos do Intune para IOS](app-sdk-ios.md)** : Este documento orientará você passo a passo durante a habilitação de seu aplicativo iOS nativo com o SDK de aplicativos do Intune.

* **[Guia do desenvolvedor do SDK de aplicativos do Intune para Android](app-sdk-android.md)** : Este documento orientará você passo a passo pela habilitação de seu aplicativo Android nativo com o SDK de aplicativos do Intune.

* **[Guia de associações do Xamarin para SDK de aplicativo do Intune](app-sdk-xamarin.md)** : Este documento irá ajudá-lo a criar aplicativos iOS e Android usando o Xamarin para políticas de proteção de aplicativo do Intune.



## <a name="enable-your-ios-or-android-app-for-app-based-conditional-access"></a>Habilitar seu aplicativo iOS ou Android para acesso condicional baseado em aplicativo

Além de habilitar seu aplicativo para a política de proteção de aplicativo, o seguinte é necessário para que seu aplicativo funcione corretamente com o acesso condicional baseado em aplicativo do Azure ActiveDirectory (AAD):

* A aplicação é criada com a [Azure ActiveDirectory Authentication Library](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) e ativada para a autenticação de mediador do AAD.

* O [ID de Cliente do AAD](https://docs.microsoft.com/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#configure-a-native-client-application) da aplicação tem de ser exclusivo nas plataformas iOS e Android.

## <a name="configure-telemetry-for-your-app"></a>Configurar a Telemetria na sua aplicação

O Microsoft Intune recolhe dados sobre estatísticas de utilização da sua aplicação.

* **SDK de aplicativos do Intune para IOS**: O SDK registra em log os dados de telemetria do SDK em eventos de uso por padrão. Estes dados são enviados para o Microsoft Intune.

  * Se optar por não enviar os dados telemétricos do SDK para o Microsoft Intune a partir da sua aplicação, terá de desativar a transmissão de telemetria ao definir a propriedade `MAMTelemetryDisabled` como "YES" no dicionário IntuneMAMSettings.

* **SDK de aplicativos do Intune para Android**: O SDK da Aplicação Intune para Android não controla a coleção de dados da sua aplicação. Por predefinição, a aplicação Portal da Empresa regista os dados telemétricos. Estes dados são enviados para o Microsoft Intune. De acordo com a Política da Microsoft, não recolhemos informações pessoais (PII). 

  * Se os utilizadores finais não enviarem estes dados, têm de desativar a telemetria em Definições na aplicação Portal da Empresa. Para saber mais, veja [Desativar a recolha de dados da Microsoft](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android). 

## <a name="line-of-business-app-version-numbers"></a>Números de versões da aplicação de linha de negócio

As aplicações de linha de negócio no Intune apresentam agora o número da versão de aplicações iOS e Android. O número é apresentado no portal do Azure na lista de aplicações e no painel de descrição geral da aplicação. Os utilizadores finais podem ver o número da aplicação na aplicação Portal da Empresa e no portal Web.

### <a name="full-version-number"></a>Número da versão completo

O número da versão completo identifica uma versão específica da aplicação. O número é apresentado como _Versão_(_Compilação_), Por exemplo, 2.2(2.2.17560800). 

O número da versão completo tem dois componentes:

- **Versão**  
  O número da versão é o número da versão legível por humanos da aplicação. Este número é utilizado pelos utilizadores finais para identificar diferentes versões da aplicação.

- **Número de Compilação**  
  O número de compilação é um número interno que pode ser utilizado para detetar aplicações e gerir a aplicação de forma programática. O número de compilação refere-se a uma iteração da aplicação que faz referência a alterações no código.

### <a name="version-and-build-number-in-android-and-ios"></a>Número da versão e de compilação em dispositivos Android e iOS

Os dispositivos Android e iOS utilizam números de versão e de compilação no contexto das aplicações. No entanto, os dois sistemas operativos têm significados que são específicos de cada SO. A tabela seguinte explica como estes termos estão relacionados.

Quando estiver a desenvolver uma aplicação de linha de negócio para utilizar no Intune, lembre-se de utilizar o número da versão e da compilação. As funcionalidades de gestão da Aplicação Intune dependem de um **CFBundleVersion** (para iOS) e de um **PackageVersionCode** (para Android) relevantes. Estes números estão incluídos no manifesto da aplicação. 

Intune|iOS|Android|Descrição|
|---|---|---|---|
Número da versão|CFBundleShortVersionString|PackageVersionName |Este número indica uma versão específica da aplicação para os utilizadores finais.|
Número de Build|CFBundleVersion|PackageVersionCode |Este número é utilizado para indicar uma iteração no código da aplicação.|

#### <a name="ios"></a>iOS

- **CFBundleShortVersionString**  
  Especifica o número da versão de lançamento do pacote. Este número identifica uma versão de lançamento da aplicação. O número é utilizado pelos utilizadores finais para referenciar a aplicação.
- **CFBundleVersion**  
  A versão de compilação do pacote, que identifica uma iteração do pacote. O número pode identificar uma versão ou um pacote não lançado. O número é utilizado para detetar aplicações.

#### <a name="android"></a>Android

- **PackageVersionName**  
  O número da versão apresentado aos utilizadores. Este atributo pode ser definido como uma cadeia bruta ou como uma referência a um recurso de cadeia. A cadeia apenas se destina a ser apresentada aos utilizadores.
- **PackageVersionCode**  
  Um número de versão interno. Este número é utilizado apenas para determinar se uma versão é mais recente do que outra (se o número for superior, a versão é mais recente). Esta não é a versão 

## <a name="next-steps-after-integration"></a>Passos seguintes após a integração

### <a name="test-your-app"></a>Testar a aplicação
Após ter concluído os passos necessários para integrar a aplicação iOS ou Android com o SDK da Aplicação Intune, terá de garantir que todas as políticas de proteção de aplicações estão ativadas e a funcionar para o utilizador e o administrador de TI. Para testar a aplicação integrada, necessitará do seguinte:

* **Microsoft Intune conta de teste**: Para testar seu aplicativo gerenciado pelo Intune em relação aos recursos de proteção de aplicativo do Intune, você precisará de uma conta de Microsoft Intune.

  * Se for um ISV e estiver a ativar a política de proteção de aplicações do Intune nas suas aplicações da loja iOS ou Android, receberá um código promocional após ter concluído o registo no Microsoft Intune, conforme descrito no passo de registo. O código promocional vai permitir-lhe inscrever-se para obter uma versão de avaliação do Microsoft Intune de um ano de utilização expandida.

  * Se estiver a desenvolver uma aplicação de linha de negócio que não será enviada para a loja, é esperado que tenha acesso ao Microsoft Intune através da sua organização. Também pode inscrever-se para obter uma versão de avaliação gratuita de um mês com o [Microsoft Intune](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).

  * Se você estiver testando seu aplicativo em um dispositivo móvel usando uma conta de usuário final, certifique-se de que você tenha dado a essa conta uma licença do Intune no site Microsoft 365 Admin Center depois de fazer logon com uma conta de administrador, consulte [atribuir licença de Microsoft Intune](../fundamentals/licenses-assign.md).

* **Políticas de proteção de aplicativo do Intune**: Para testar seu aplicativo em todas as políticas de proteção de aplicativo do Intune, você deve saber qual é o comportamento esperado para cada configuração de política. Consulte as descrições para [políticas de proteção de aplicações para iOS](../apps/app-protection-policy-settings-ios.md) e [políticas de proteção de aplicações para Android](../apps/app-protection-policy-settings-android.md). Se seu aplicativo tiver integrado o SDK do Intune, mas não estiver listado no portal do Azure como um aplicativo de destino ainda, você poderá direcioná-lo com uma política selecionando a opção "+ mais aplicativos" e fornecendo a ID do pacote (iOS) ou o nome dos pacotes (Android) na caixa de texto.

* **Solucionar problemas**: Se você encontrar problemas durante o teste manual da experiência do usuário de instalação do aplicativo, consulte [solucionar problemas de instalação do aplicativo](../apps/troubleshoot-app-install.md). 

### <a name="give-your-app-access-to-the-intune-app-protection-service-optional"></a>Dar acesso ao aplicativo para o serviço de proteção de aplicativo do Intune (opcional)

Se seu aplicativo estiver usando suas próprias configurações do AAD (Azure Active Directory personalizadas) para autenticação, as etapas a seguir deverão ser executadas para os aplicativos da loja pública, bem como para os aplicativos LOB internos. As etapas **não precisarão ser executadas se seu aplicativo estiver usando a ID do cliente padrão do SDK do Intune**. 

Depois de registrar seu aplicativo em um locatário do Azure e ele estiver aparecendo em **todos os aplicativos**, você deverá dar acesso ao aplicativo para o serviço de proteção de aplicativo do Intune (anteriormente conhecido como serviço de MAM). No portal do Azure:

1. Vá para a folha **Azure Active Directory** .
2. Em **registros de aplicativo**, vá para a listagem configurada para o aplicativo.
3. Clique em **+ Adicionar uma permissão**.
4. Clique nas **APIs que minha organização usa**. 
5. Na caixa de pesquisa, introduza **Gestão de Aplicações Móveis da Microsoft**.
6. Em **permissões delegadas**, selecione o **DeviceManagementManagedApps. ReadWrite: Ler e gravar a caixa de seleção dados**de gerenciamento de aplicativo do usuário *.
7. Clique em **adicionar permissões**.

### <a name="badge-your-app-optional"></a>Colocar um distintivo na aplicação (opcional)

Após verificar que as políticas de proteção de aplicações do Intune funcionam na sua aplicação, pode colocar um distintivo com o logótipo de proteção de aplicações do Intune no ícone da aplicação.

Este distintivo indica a administradores de TI, utilizadores finais e potenciais clientes do Intune que a sua aplicação funciona com as políticas de proteção de aplicações do Intune. Encoraja a utilização e a adesão à sua aplicação por parte dos clientes do Intune.

Este distintivo é um ícone de mala e pode ser visto nos exemplos abaixo:

![Políticas de proteção de aplicativo do Intune – exemplo de notificação 1](./media/app-sdk-get-started/badge-example-1.png) ![Políticas de proteção de aplicativo do Intune – exemplo de notificação 2](./media/app-sdk-get-started/badge-example-2.png)

**O que necessita para colocar um distintivo na aplicação**:

* Uma aplicação de manipulação de imagens que possa ler ficheiros **.eps** ou uma aplicação do Adobe que possa ler ficheiros **.ai**.

* Pode encontrar os [itens e diretrizes de distintivos da aplicação Intune](https://github.com/msintuneappsdk/intune-app-partner-badge) no GitHub do Microsoft Intune.
