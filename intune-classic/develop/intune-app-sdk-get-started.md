---
title: "Introdução ao SDK da Aplicação do Microsoft Intune | Documentos da Microsoft"
description: "Ative rapidamente a sua aplicação móvel para a gestão de aplicações móveis (MAM) com o Microsoft Intune."
keywords: 
author: mtillman
manager: angrobe
ms.author: oydang
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 95c12111693e00fb6f67d20464dd159aeb4bb609
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Introdução ao SDK da Aplicação Microsoft Intune

Este guia ajuda-o a ativar rapidamente a sua aplicação móvel para as políticas de proteção de aplicações com o Microsoft Intune. Será útil compreender primeiro os benefícios do SDK da Aplicação Intune, conforme explicado na [Descrição Geral do SDK da Aplicação Intune](intune-app-sdk.md).

O SDK da Aplicação Intune suporta cenários semelhantes entre iOS e Android e destina-se a criar uma experiência consistente para os administradores de TI entre as plataformas. Porém, existem pequenas diferenças no suporte de determinadas funcionalidades devido às limitações das plataformas.

## <a name="register-your-store-app-with-microsoft"></a>Registar a aplicação da loja no Microsoft

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>Se a sua aplicação for interna da organização e não estiver publicamente disponível:

*Não é necessário* registar a sua aplicação. Para aplicações de linha de negócio internas, o administrador de TI irá implementar a aplicação internamente. O Intune detetará que a aplicação foi criada com o SDK e permitirá que o administrador de TI aplique a política de proteção de aplicações à mesma. Pode avançar para a secção [Integrar a política de proteção de aplicações na sua aplicação iOS ou Android](#enable-your-iOS-or-Android-app-for-app-protection-policy).

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Se a sua aplicação for lançada numa loja de aplicações pública, como a Apple App Store ou o Google Play:

Primeiro, _**tem**_ de registar a sua aplicação com o Microsoft Intune e aceitar os termos de registo. Os administradores de TI poderão aplicar a política de proteção de aplicações à aplicação otimizada, que será listada como parceira de aplicações do Intune.

Até o registo ser concluído e confirmado pela equipa do Microsoft Intune, os administradores do Intune não terão a opção de aplicar a política de proteção de aplicações na ligação avançada da sua aplicação. A Microsoft também vai adicionar a sua aplicação à respetiva [página de Parceiros do Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps). Nesta página, o ícone da aplicação será apresentado para mostrar que suporta políticas de proteção de aplicações do Intune.

Para iniciar o processo de registo, preencha o [Microsoft Intune App Partner Questionnaire (Questionário dos Parceiros da Aplicação do Microsoft Intune)](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u).

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

Se a sua aplicação for uma aplicação Xamarin ou Cordova, utilize estas variantes do SDK:

* [Componente Xamarin do SDK da Aplicação Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Plugin Cordova do SDK da Aplicação Intune](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

Recomendamos que se inscreva numa conta do GitHub que pode utilizar para bifurcar e obter dados dos nossos repositórios. O GitHub permite que os programadores comuniquem com a nossa equipa do produto, coloquem questões e recebam respostas rápidas, vejam notas de versão e enviem feedback à Microsoft. Se tiver perguntas sobre o GitHub do SDK da Aplicação Intune, contacte msintuneappsdk@microsoft.com.





## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>Integrar a política de proteção de aplicações na sua aplicação iOS ou Android

Irá precisar de um dos seguintes guias para programadores para o ajudar a integrar o SDK da Aplicação Intune na sua aplicação:

* **[Guia para Programadores do SDK da Aplicação Intune para iOS](intune-app-sdk-ios.md)**: este documento descreve os passos para ativar a aplicação iOS nativa com o SDK da Aplicação Intune.

* **[Guia para Programadores do SDK da Aplicação Intune para Android](intune-app-sdk-android.md)**: este documento descreve os passos para a ativação da aplicação Android nativa com o SDK da Aplicação Intune.

* **[Guia do Plug-in Cordova do SDK da Aplicação Intune](intune-app-sdk-cordova.md)**: este documento ajuda-o a criar aplicações para iOS e Android com políticas de proteção de aplicações do Cordova para Intune.

* **[Guia do Componente Xamarin do SDK da Aplicação Intune](intune-app-sdk-xamarin.md)**: este documento ajuda-o a criar aplicações para iOS e Android com políticas de proteção de aplicações do Cordova para Intune.




## <a name="configure-telemetry-for-your-app"></a>Configurar a Telemetria na sua aplicação

O Microsoft Intune recolhe dados sobre estatísticas de utilização da sua aplicação.

* **SDK da Aplicação para iOS**: o SDK regista dados telemétricos do SDK sobre eventos de utilização por predefinição. Estes dados são enviados para o Microsoft Intune.

    * Se optar por não enviar os dados telemétricos do SDK para o Microsoft Intune a partir da sua aplicação, terá de desativar a transmissão de telemetria ao definir a propriedade `MAMTelemetryDisabled` como "YES" no dicionário IntuneMAMSettings.


* **SDK da Aplicação Intune para Android**: os dados telemétricos não são registados através do SDK.

## <a name="next-steps-after-integration"></a>Passos seguintes após a integração

### <a name="test-your-app"></a>Testar a sua aplicação
Após ter concluído os passos necessários para integrar a aplicação iOS ou Android com o SDK da Aplicação Intune, terá de garantir que todas as políticas de proteção de aplicações estão ativadas e a funcionar para o utilizador e o administrador de TI. Para testar a aplicação integrada, necessitará do seguinte:

* **Conta de teste do Microsoft Intune**: para testar a sua aplicação otimizada para o Intune com as funcionalidades de proteção de aplicações do Intune, precisa de ter uma conta do Microsoft Intune.

    * Se for um ISV e estiver a ativar a política de proteção de aplicações do Intune nas suas aplicações da loja iOS ou Android, receberá um código promocional após ter concluído o registo no Microsoft Intune, conforme descrito no passo de registo. O código promocional vai permitir-lhe inscrever-se para obter uma versão de avaliação do Microsoft Intune de um ano de utilização expandida.

    * Se estiver a desenvolver uma aplicação de linha de negócio que não será enviada para a loja, é esperado que tenha acesso ao Microsoft Intune através da sua organização. Também pode inscrever-se para obter uma versão de avaliação gratuita de um mês com o [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).

* **Políticas de proteção de aplicações do Intune**: para testar a aplicação com todas as políticas de proteção de aplicações do Intune, deve saber qual é o comportamento esperado em cada definição de política. Consulte as descrições para [políticas de proteção de aplicações para iOS](../deploy-use/ios-mam-policy-settings.md) e [políticas de proteção de aplicações para Android](../deploy-use/android-mam-policy-settings.md).

* **Resolução de problemas**: se tiver problemas enquanto testa manualmente a experiência de utilizador da sua aplicação, consulte a [Resolução de problemas do MAM](../troubleshoot/troubleshoot-mam.md). Este artigo disponibiliza ajuda para problemas, caixas de diálogo e mensagens de erro frequentes que possa encontrar em aplicações otimizadas para o Intune. 

### <a name="badge-your-app-optional"></a>Colocar um distintivo na aplicação (opcional)

Após verificar que as políticas de proteção de aplicações do Intune funcionam na sua aplicação, pode colocar um distintivo com o logótipo de proteção de aplicações do Intune no ícone da aplicação.

Este distintivo indica a administradores de TI, utilizadores finais e potenciais clientes do Intune que a sua aplicação funciona com as políticas de proteção de aplicações do Intune. Encoraja a utilização e a adesão à sua aplicação por parte dos clientes do Intune.

Este distintivo é um ícone de mala e pode ser visto nos exemplos abaixo:

![Exemplo de distintivo 1](../media/intune-app-badge/example-1.png) ![Exemplo de distintivo 2](../media/intune-app-badge/example-2.png)

**O que necessita para colocar um distintivo na aplicação**:

* Uma aplicação de manipulação de imagens que possa ler ficheiros **.eps** ou uma aplicação do Adobe que possa ler ficheiros **.ai**.

* Pode encontrar os [itens e diretrizes de distintivos da aplicação Intune](https://github.com/msintuneappsdk/intune-app-partner-badge) no GitHub do Microsoft Intune.

