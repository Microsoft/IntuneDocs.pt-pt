---
title: "Introdução ao SDK da Aplicação do Microsoft Intune | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.author: oydang
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ca4623db80d711f3543b6d688fb1bb1ef228c62c
ms.openlocfilehash: 2a65ae79a0bba21d555dbed9f1bc40e01452f08c


---

# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Introdução ao SDK da Aplicação Microsoft Intune

Este guia ajuda-o a ativar rapidamente a sua aplicação móvel para a gestão de aplicações móveis (MAM) com o Microsoft Intune. Será útil compreender primeiro os benefícios do SDK da Aplicação do Intune, conforme explicado na [Descrição Geral do SDK da Aplicação do Intune](intune-app-sdk.md).

Este guia explica os principais passos para ativar a MAM na sua aplicação com o Microsoft Intune. O SDK da Aplicação do Intune suporta cenários semelhantes entre plataformas e destina-se a criar uma experiência consistente para os administradores de TI entre as plataformas. Porém, existem pequenas diferenças no suporte de determinadas funcionalidades devido às limitações das plataformas.

## <a name="register-your-store-app-with-microsoft"></a>Registar a aplicação da loja no Microsoft

**Se a sua aplicação é interna da sua empresa e não será disponibilizada numa loja de aplicações pública**:

*Não é necessário* registar a sua aplicação. Para aplicações de linha de negócio internas, o administrador de TI deverá implementar a aplicação internamente. O Intune detetará que a aplicação foi criada com o SDK e permitirá que o administrador de TI aplique as definições de política de MAM à mesma. Pode avançar para a secção [Ativar a aplicação móvel iOS ou Android para MAM com o SDK](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk).

**Se a sua aplicação for lançada numa loja de aplicações pública, como a Apple App Store ou o Google Play**:

Primeiro, *tem* de registar a sua aplicação com o Microsoft Intune e aceitar os termos de registo. Os administradores de TI poderão aplicar as definições de política de MAM do Intune à aplicação otimizada, que será listada como parceira de aplicações do Intune. Até o registo ser concluído e confirmado pela equipa do Microsoft Intune, os administradores do Intune não poderão aplicar a política de MAM à ligação avançada da sua aplicação. A Microsoft também vai adicionar a sua aplicação à respetiva [página de Parceiros do Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps). Nesta página, o ícone da aplicação será apresentado para mostrar que suporta a política de MAM do Microsoft Intune.

Para iniciar o processo de registo, preencha o [Microsoft Intune App Partner Questionnaire (Questionário dos Parceiros da Aplicação do Microsoft Intune)](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u).

Utilizaremos os endereços de e-mail listados nas suas respostas do questionário para entrar em contacto e continuar o processo de registo. Além disso, utilizamos o seu endereço de e-mail de registo para contactá-lo caso surja alguma questão.

> [!NOTE]
> Todas as informações recolhidas no questionário e através da correspondência por e-mail com a equipa do Microsoft Intune respeitarão a [Declaração de Privacidade da Microsoft](https://www.microsoft.com/en-us/privacystatement/default.aspx).

**O que pode esperar no processo de registo**:

1. Após submeter o questionário, vamos contactá-lo através do seu endereço de e-mail de registo, para confirmar a receção bem-sucedida ou para pedir informações adicionais para concluir o registo.
2. Depois de recebermos todas as informações necessárias, ser-lhe-á enviado o Contrato de Parceiro de Aplicações do Microsoft Intune para assinar. Este contrato descreve os termos que a sua empresa tem de aceitar antes de se tornar parceira de aplicações do Microsoft Intune.
3. Também receberá uma notificação quando a sua aplicação for registada com êxito no serviço Microsoft Intune e estiver em destaque no site dos [parceiros do Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps).
4. Por fim, a ligação avançada da sua aplicação será adicionada à próxima atualização mensal do Serviço Intune. Por exemplo, se as informações de registo estiverem concluídas em julho, a ligação avançada será suportada em meados de agosto.

Se a ligação avançada da aplicação for alterada no futuro, terá de voltar a registar a sua aplicação. Além disso, informe-nos se atualizar a sua aplicação com uma nova versão do SDK da Aplicação do Intune.



## <a name="download-the-sdk-files"></a>Transferir os ficheiros do SDK

Os SDKs da Aplicação do Intune para iOS e Android nativos estão alojados numa conta do Microsoft GitHub. Estes repositórios públicos contêm os ficheiros do SDK para iOS e Android, respetivamente:

* [SDK da Aplicação do Intune para iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [SDK da Aplicação do Intune para Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

Se a sua aplicação for uma aplicação Xamarin ou Cordova, utilize estas ferramentas de programador:

* [Componente Xamarin do SDK da Aplicação do Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Plugin Cordova do SDK da Aplicação do Intune](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

Recomendamos que se inscreva numa conta do GitHub que pode utilizar para bifurcar e obter dados dos nossos repositórios. O GitHub permite que os programadores comuniquem com a nossa equipa do produto, coloquem questões e recebam respostas rápidas, vejam notas de versão e enviem feedback à Microsoft. Se tiver perguntas sobre os repositórios e a conta do GitHub, contacte msintuneappsdk@microsoft.com.





## <a name="enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk"></a>Ativar a aplicação móvel iOS ou Android para MAM com o SDK

Para integrar o SDK da Aplicação do Intune na sua aplicação iOS nativa, terá de fazer o seguinte:

* **[Guia para Programadores do SDK da Aplicação do Intune para iOS](intune-app-sdk-ios.md)**: este documento descreve os passos para ativar a aplicação móvel iOS com o SDK da Aplicação do Intune.


Para integrar o SDK da Aplicação do Intune na sua aplicação Android nativa, terá de fazer o seguinte:

* **[Guia para Programadores do SDK da Aplicação do Intune para Android](intune-app-sdk-android.md)**: este documento descreve os passos para a ativação da aplicação móvel Android com o SDK da Aplicação do Intune.

Para criar aplicações Cordova com o Plug-in Cordova do SDK da Aplicação Intune, vai precisar do seguinte:

* **[Guia do Plug-in Cordova do SDK da Aplicação Intune](intune-app-sdk-cordova)**: este documento ajuda-o a criar aplicações para iOS e Android com o Cordova para a gestão de aplicações móveis do Intune.

Para criar aplicações Xamarin com o Componente Xamarin do SDK da Aplicação Intune, vai precisar do seguinte:

* **[Guia do Componente Xamarin do SDK da Aplicação Intune](intune-app-sdk-xamarin)**: este documento ajuda-o a criar aplicações para iOS e Android com o Cordova para a gestão de aplicações móveis do Intune.




## <a name="configure-telemetry-for-your-app"></a>Configurar a Telemetria na sua aplicação

O Microsoft Intune recolhe dados sobre estatísticas de utilização da sua aplicação.

* **SDK da Aplicação para iOS**: o SDK regista dados telemétricos do SDK sobre eventos de utilização por predefinição. Estes dados são enviados para o Microsoft Intune.

    * Se optar por não enviar os dados telemétricos do SDK para o Microsoft Intune a partir da sua aplicação, terá de desativar a transmissão de telemetria ao definir a propriedade `MAMTelemetryDisabled` como "YES" no dicionário IntuneMAMSettings.

* **SDK da Aplicação do Intune para Android**: os dados telemétricos não são registados através do SDK.

## <a name="test-your-mam-enabled-app-with-microsoft-intune"></a>Testar a aplicação ativada para MAM com o Microsoft Intune

Após ter concluído os passos necessários para integrar a aplicação iOS ou Android com o SDK da Aplicação do Intune, terá de garantir que todas as políticas de gestão de aplicações estão ativadas e a funcionar no utilizador e no administrador de TI. Para testar a aplicação integrada, necessitará do seguinte:

<!--TODO-->

* **Testar a aplicação ativada para MAM com o Microsoft Intune**: este documento descreve os passos para testar as suas aplicações para iOS ou Android ativadas para MAM com o Microsoft Intune. Pode encontrar este documento nos repositórios do GitHub dos SDKs.

* **Conta do Microsoft Intune**: para testar as suas aplicações ativadas para MAM com o Microsoft Intune, vai precisar de uma conta do Microsoft Intune.
    * Se for um ISV e estiver a ativar as suas aplicações da loja iOS ou Android para MAM do Intune, receberá um código promocional após ter concluído o registo no Microsoft Intune, conforme descrito no passo de registo. O código promocional vai permitir-lhe inscrever-se para obter uma versão de avaliação do Microsoft Intune de um ano de utilização expandida.
    * Se estiver a desenvolver uma aplicação de linha de negócio que não será enviada para a loja, é esperado que tenha acesso ao Microsoft Intune através da sua organização. Também pode inscrever-se para obter uma versão de avaliação gratuita de um mês com o [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).



<!--HONumber=Nov16_HO3-->


