---
title: Introdução ao SDK da Aplicação Microsoft Intune
description: Ative rapidamente a sua aplicação móvel para a gestão de aplicações móveis (MAM) com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune
ms.openlocfilehash: 2c05912e62f9887ff7af0532dc759c2e852c1b29
ms.sourcegitcommit: 4d5e811d451aeb6307e0f64818e182e471ae1ed4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2018
ms.locfileid: "51619029"
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Introdução ao SDK da Aplicação Microsoft Intune

Este guia ajuda-o a ativar rapidamente a sua aplicação móvel para as políticas de proteção de aplicações com o Microsoft Intune. Será útil compreender primeiro os benefícios do SDK da Aplicação Intune, conforme explicado na [Descrição Geral do SDK da Aplicação Intune](app-sdk.md).

O SDK da Aplicação Intune suporta cenários semelhantes entre iOS e Android e destina-se a criar uma experiência consistente para os administradores de TI entre as plataformas. Porém, existem pequenas diferenças no suporte de determinadas funcionalidades devido às limitações das plataformas.

## <a name="register-your-store-app-with-microsoft"></a>Registar a aplicação da loja no Microsoft

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>Se a sua aplicação for interna da organização e não estiver publicamente disponível:

*Não é necessário* registar a sua aplicação. Para aplicações de linha de negócio internas, o administrador de TI irá implementar a aplicação internamente. O Intune detetará que a aplicação foi criada com o SDK e permitirá que o administrador de TI aplique a política de proteção de aplicações à mesma. Pode avançar para a secção [Integrar a política de proteção de aplicações na sua aplicação iOS ou Android](#enable-your-iOS-or-Android-app-for-app-protection-policy).

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Se a sua aplicação for lançada numa loja de aplicações pública, como a Apple App Store ou o Google Play:

Primeiro, _**tem**_ de registar a sua aplicação com o Microsoft Intune e aceitar os termos de registo. Os administradores de TI poderão assim aplicar a política de proteção de aplicações à aplicação gerida, que será listada como parceira de aplicações do Intune.

Até o registo ser concluído e confirmado pela equipa do Microsoft Intune, os administradores do Intune não terão a opção de aplicar a política de proteção de aplicações na ligação avançada da sua aplicação. A Microsoft também vai adicionar a sua aplicação à respetiva [página de Parceiros do Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps). Nesta página, o ícone da aplicação será apresentado para mostrar que suporta políticas de proteção de aplicações do Intune.

Para iniciar o processo de registo, e se ainda não estiver a trabalhar com um contacto da Microsoft, preencha o [Microsoft Intune App Partner Questionnaire](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u) (Questionário para Parceiros de Aplicação do Microsoft Intune).

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

* **[Guia para Programadores do SDK da Aplicação Intune para iOS](app-sdk-ios.md)**: este documento descreve os passos para ativar a aplicação iOS nativa com o SDK da Aplicação Intune.

* **[Guia para Programadores do SDK da Aplicação Intune para Android](app-sdk-android.md)**: este documento descreve os passos para a ativação da aplicação Android nativa com o SDK da Aplicação Intune.

* **[Guia de Enlaces Xamarin do SDK da Aplicação Intune](app-sdk-xamarin.md)**: este documento ajuda-o a criar aplicações iOS e Android com políticas de proteção de aplicações do Xamarin para Intune.



## <a name="enable-your-ios-or-android-app-for-app-based-conditional-access"></a>Ativar o acesso condicional com base na aplicação iOS ou Android
 
 Além de ativar a política de proteção na aplicação, é preciso o seguinte para a sua aplicação funcionar corretamente com o acesso condicional com base na aplicação do Azure ActiveDirectory (AAD):
 
 * A aplicação é criada com a [Azure ActiveDirectory Authentication Library](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) e ativada para a autenticação de mediador do AAD.
 
 * O [ID de Cliente do AAD](https://docs.microsoft.com/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#optional-configure-a-native-client-application) da aplicação tem de ser exclusivo nas plataformas iOS e Android.
 
## <a name="configure-telemetry-for-your-app"></a>Configurar a Telemetria na sua aplicação

O Microsoft Intune recolhe dados sobre estatísticas de utilização da sua aplicação.

* **SDK da Aplicação para iOS**: o SDK regista dados telemétricos do SDK sobre eventos de utilização por predefinição. Estes dados são enviados para o Microsoft Intune.

    * Se optar por não enviar os dados telemétricos do SDK para o Microsoft Intune a partir da sua aplicação, terá de desativar a transmissão de telemetria ao definir a propriedade `MAMTelemetryDisabled` como "YES" no dicionário IntuneMAMSettings.

* **SDK da Aplicação Intune para Android**: o SDK da Aplicação Intune para Android não controla a recolha de dados da sua aplicação. Por predefinição, a aplicação Portal da Empresa regista os dados telemétricos. Estes dados são enviados para o Microsoft Intune. De acordo com a Política da Microsoft, não recolhemos informações pessoais (PII). 

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
Número de compilação|CFBundleVersion|PackageVersionCode |Este número é utilizado para indicar uma iteração no código da aplicação.|

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

### <a name="test-your-app"></a>Testar a sua aplicação
Após ter concluído os passos necessários para integrar a aplicação iOS ou Android com o SDK da Aplicação Intune, terá de garantir que todas as políticas de proteção de aplicações estão ativadas e a funcionar para o utilizador e o administrador de TI. Para testar a aplicação integrada, necessitará do seguinte:

* **Conta de teste do Microsoft Intune**: para testar a sua aplicação gerida pelo Intune com as funcionalidades de proteção de aplicações do Intune, precisa de ter uma conta do Microsoft Intune.

    * Se for um ISV e estiver a ativar a política de proteção de aplicações do Intune nas suas aplicações da loja iOS ou Android, receberá um código promocional após ter concluído o registo no Microsoft Intune, conforme descrito no passo de registo. O código promocional vai permitir-lhe inscrever-se para obter uma versão de avaliação do Microsoft Intune de um ano de utilização expandida.

    * Se estiver a desenvolver uma aplicação de linha de negócio que não será enviada para a loja, é esperado que tenha acesso ao Microsoft Intune através da sua organização. Também pode inscrever-se para obter uma versão de avaliação gratuita de um mês com o [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).

* **Políticas de proteção de aplicações do Intune**: para testar a aplicação com todas as políticas de proteção de aplicações do Intune, deve saber qual é o comportamento esperado em cada definição de política. Consulte as descrições para [políticas de proteção de aplicações para iOS](app-protection-policy-settings-ios.md) e [políticas de proteção de aplicações para Android](app-protection-policy-settings-android.md).

* **Resolução de problemas**: se tiver problemas ao testar manualmente a experiência de utilizador de instalação da sua aplicação, veja [Resolver problemas com a instalação de aplicações](troubleshoot-app-install.md). 

### <a name="give-your-app-access-to-the-intune-app-protection-service-optional"></a>Permitir o acesso a aplicações ao serviço de proteção de aplicações do Intune (opcional)

Se seu aplicativo está usando suas próprias definições personalizadas do Azure Active Directory (AAD) para autenticação, os seguintes passos devem ser levados para as aplicações da loja pública, bem como aplicações LOB internas. Os passos **não tem de ser efetuada se a sua aplicação está a utilizar o ID de cliente predefinida do SDK do Intune**. 

Depois de ter registado a sua aplicação dentro de um inquilino do Azure e está a aparecer sob **todos os aplicativos**, tem de dar o acesso a aplicações para o serviço de proteção de aplicações do Intune (anteriormente conhecido como o serviço MAM). No portal do Azure:

1.  Aceda ao painel **Azure Active Directory**.
2.  Selecione a configuração **Registo de aplicações** para a aplicação.
3.  Em **Definições** abaixo do cabeçalho **Acesso à API**, selecione **Permissão obrigatória**. 
4.  Clique em **+ Adicionar**.
5.  Clique em **Selecionar uma API**. 
6.  Na caixa de pesquisa, introduza **Gestão de Aplicações Móveis da Microsoft**.
7.  Selecione **Gestão de Aplicações Móveis da Microsoft** na lista de APIs e clique em Selecionar.
8.  Selecione **Read and Write the User's App Management Data** (Ler e Escrever os Dados de Gestão de Aplicação do Utilizador).
9.  Clique em **Concluído**.
10. Clique em **Conceder permissões** e, em seguida, clique em **Sim**. 

### <a name="badge-your-app-optional"></a>Colocar um distintivo na aplicação (opcional)

Após verificar que as políticas de proteção de aplicações do Intune funcionam na sua aplicação, pode colocar um distintivo com o logótipo de proteção de aplicações do Intune no ícone da aplicação.

Este distintivo indica a administradores de TI, utilizadores finais e potenciais clientes do Intune que a sua aplicação funciona com as políticas de proteção de aplicações do Intune. Encoraja a utilização e a adesão à sua aplicação por parte dos clientes do Intune.

Este distintivo é um ícone de mala e pode ser visto nos exemplos abaixo:

![Exemplo de distintivo 1](./media/badge-example-1.png) ![Exemplo de distintivo 2](./media/badge-example-2.png)

**O que necessita para colocar um distintivo na aplicação**:

* Uma aplicação de manipulação de imagens que possa ler ficheiros **.eps** ou uma aplicação do Adobe que possa ler ficheiros **.ai**.

* Pode encontrar os [itens e diretrizes de distintivos da aplicação Intune](https://github.com/msintuneappsdk/intune-app-partner-badge) no GitHub do Microsoft Intune.
