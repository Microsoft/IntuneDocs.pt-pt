<<<<<<< HEAD
---
title: "Introdução ao SDK da Aplicação Microsoft Intune | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba9ba203c9ec173dafd1d6f9e4828d4a8a51e1ef
ms.openlocfilehash: 136dd127c5e0f1784746b973ebc5594573f07925

||||||| merged common ancestors
---
title: "Introdução ao SDK da Aplicação Microsoft Intune | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba9ba203c9ec173dafd1d6f9e4828d4a8a51e1ef
ms.openlocfilehash: 136dd127c5e0f1784746b973ebc5594573f07925

=======
---
title: "Introdução ao SDK da Aplicação Microsoft Intune | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed1008c786285821c608a8404805c6615c60507f
ms.openlocfilehash: c80868fdee79df62aae0aa64e378be5dcc9664ae

>>>>>>> 2cebb9c337e0b62262ed35e10437cf949bee5815

---
<<<<<<< HEAD

# Introdução ao SDK da Aplicação Microsoft Intune
||||||| merged common ancestors

# Introdução ao SDK da Aplicação Microsoft Intune
=======

# <a name="getting-started-with-the-microsoft-intune-app-sdk"></a>Introdução ao SDK da Aplicação Microsoft Intune
>>>>>>> 2cebb9c337e0b62262ed35e10437cf949bee5815

Este Guia de introdução ajuda-o a ativar rapidamente a sua aplicação móvel para Gestão de Aplicações Móveis com o Microsoft Intune. Será útil compreender primeiro os benefícios do SDK da Aplicação do Intune, conforme enumerado na [Descrição Geral do SDK da ](intune-app-sdk.md).

Este guia explica os principais passos necessários para ativar a gestão de aplicações móveis na sua aplicação com o Microsoft Intune. O SDK da Aplicação do Intune suporta cenários semelhantes entre plataformas e destina-se a criar uma experiência consistente transversalmente entre as plataformas para administradores de TI. No entanto, existem pequenas diferenças no suporte de determinadas funcionalidades devido às limitações das plataformas.

# <a name="getting-started"></a>Introdução

## <a name="register-your-store-app-with-microsoft"></a>Registar a aplicação da loja no Microsoft

**Se a sua aplicação é interna da sua empresa e não será disponibilizada numa loja de aplicações pública**:

**Não é necessário** registar a sua aplicação. Para aplicações de linha de negócio internas, o administrador de TI irá implementar a aplicação internamente. O Intune detetará que a aplicação foi criada com o SDK e permitirá ao administrador de TI aplicar as definições de política de MAM à mesma. Pode avançar para a secção [Ativar a aplicação móvel iOS ou Android para MAM com o SDK](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk).

**Se a sua aplicação será lançada numa loja de aplicações pública, como a Apple App Store ou o Google Play**: 

Primeiro, **tem** de registar a sua aplicação com o Microsoft Intune e aceitar os termos de registo. Depois de a registar, os administradores de TI poderão aplicar as definições de política de MAM do Intune à aplicação otimizada, que será listada como parceira de aplicações do Intune. Até o registo ser concluído e confirmado pela equipa do Microsoft Intune os administradores do Intune não terão a opção de aplicar a política de MAM na ligação avançada da sua aplicação. A Microsoft também irá adicionar a sua aplicação à [página de Parceiros do Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps), onde o ícone da aplicação será apresentado para mostrar que suporta a política de MAM do Microsoft Intune.

Para iniciar o processo de registo, preencha o **[Microsoft Intune App Partner Questionnaire (Questionário para Parceiros de Aplicação do Microsoft Intune – em inglês)](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u)**. 

A Microsoft utilizará os endereços de e-mail listados nas suas respostas do questionário para entrar em contacto e continuar o processo de registo. Além disso, utilizamos o seu endereço de e-mail de registo para contactá-lo se tivermos alguma dúvida.

> [!NOTE]
> Todas as informações recolhidas no formulário acima e através de correspondência de e-mail com a equipa do Microsoft Intune respeitarão a [Declaração de Privacidade da Microsoft](https://www.microsoft.com/en-us/privacystatement/default.aspx).

**O que pode esperar no processo de registo**: 

1. Após submeter o questionário, será contactado pela Microsoft através do seu endereço de e-mail de registo, para confirmar a receção bem-sucedida ou para pedir informações adicionais para concluir o registo. 
2. Depois de recebermos todas as informações necessárias, ser-lhe-á enviado o Contrato de Parceiro de Aplicações do Microsoft Intune para assinar. Este contrato descreve os termos que a sua empresa tem de aceitar antes de se tornar parceira de aplicações do Microsoft Intune. 
3. Também receberá uma notificação quando a sua aplicação for registada com êxito no serviço Microsoft Intune e estiver em destaque no site dos [parceiros do Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps). 
4. Por fim, a ligação avançada da sua aplicação será adicionada à próxima atualização mensal do Serviço do Intune. Por exemplo, se as informações de registo estiverem concluídas em julho, a ligação avançada da aplicação será suportada em meados de agosto. 

Se a ligação avançada da aplicação da loja for alterada no futuro, terá de voltar a registar a sua aplicação. Além disso, informe-nos se atualizar a sua aplicação com uma nova versão do SDK da Aplicação do Intune.



## <a name="download-the-sdk-files"></a>Transferir os ficheiros do SDK

Os SDKs da Aplicação do Intune para iOS e Android nativos estão alojados numa conta do Microsoft GitHub. Os seguintes repositórios públicos contêm os ficheiros do SDK para iOS e Android, respetivamente:

* [SDK da Aplicação do Intune para iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [SDK da Aplicação do Intune para Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

**Se a sua aplicação for uma aplicação Xamarin ou Cordova, utilize as ferramentas de programador abaixo**:

* [Componente Xamarin do SDK da Aplicação do Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Plugin Cordova do SDK da Aplicação do Intune](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

Recomendamos que se inscreva numa conta do GitHub que pode utilizar para bifurcar e obter dados dos nossos repositórios. O GitHub permite aos programadores comunicar com a nossa equipa de produto, colocar questões e receber respostas rápidas, ver notas de versão e fornecer feedback à Microsoft. Se tiver perguntas sobre os repositórios e a conta do GitHub, contacte msintuneappsdk@microsoft.com.





## <a name="enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk"></a>Ativar a aplicação móvel iOS ou Android para MAM com o SDK

Para integrar o SDK da Aplicação do Intune na sua aplicação iOS nativa, terá de fazer o seguinte: 

* **[Guia para Programadores do SDK da Aplicação do Intune para iOS](intune-app-sdk-ios.md)**: este documento irá guiá-lo passo a passo através da ativação da aplicação móvel iOS com o SDK da Aplicação do Intune. 


Para integrar o SDK da Aplicação do Intune na sua aplicação Android nativa, terá de fazer o seguinte:

* **[Guia para Programadores do SDK da Aplicação do Intune para Android](intune-app-sdk-android.md)**: este documento irá guiá-lo passo a passo através da ativação da aplicação móvel Android com o SDK da Aplicação do Intune. 

Encontrará documentação para o Componente Xamarin do SDK da Aplicação do Intune e o Plug-in do Cordova do SDK da Aplicação do Intune nos respetivos repositórios do GitHub. 


## <a name="configuring-telemetry-for-your-app"></a>Configurar a Telemetria na sua aplicação

O Microsoft Intune recolhe dados sobre estatísticas de utilização da sua aplicação.

* **SDK da Aplicação para iOS**: o SDK regista dados telemétricos do SDK sobre eventos de utilização por predefinição. Estes dados são enviados para o Microsoft Intune.

    * Se optar por não enviar os dados telemétricos do SDK para o Microsoft Intune a partir da sua aplicação, terá de desativar a transmissão de telemetria ao definir a propriedade `MAMTelemetryDisabled` como "YES" no dicionário IntuneMAMSettings.

* **SDK da Aplicação do Intune para Android**: os dados telemétricos não são registados através do SDK.

## <a name="test-your-mam-enabled-app-with-microsoft-intune"></a>Testar a aplicação ativada para MAM com o Microsoft Intune

Depois de concluir os passos necessários para integrar a aplicação iOS ou Android com o SDK da Aplicação do Intune, terá de garantir que todas as políticas de gestão de aplicações estão ativadas e a funcionar no utilizador final e no administrador de TI. Para testar a aplicação integrada, necessitará do seguinte:

<!--TODO-->

* **Testar a aplicação ativada para MAM com o Microsoft Intune**: este documento irá guiá-lo passo a passo para saber como testar as suas aplicações para iOS ou Android ativadas para MAM com o Microsoft Intune. Pode encontrar este documento nos repositórios do GitHub dos SDKs.

* **Conta do Microsoft Intune**: para testar as suas aplicações ativadas para MAM com o Microsoft Intune, vai precisar de uma conta do Microsoft Intune. 
    * Se for um ISV e estiver a ativar as suas aplicações de loja iOS ou Android para MAM do Intune, receberá um código promocional depois de concluir o registo no Microsoft Intune, conforme descrito no passo de registo. O código promocional vai permitir-lhe inscrever-se para obter uma versão de avaliação do Microsoft Intune de 1 ano de utilização expandida. 
    * Se estiver a desenvolver uma aplicação de linha de negócio que não será enviada para a loja, é esperado que tenha acesso ao Microsoft Intune através da sua organização. Também pode inscrever-se para obter uma versão de avaliação gratuita de 1 mês com o [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).




<!--HONumber=Nov16_HO1-->


