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


---

# Introdução ao SDK da Aplicação Microsoft Intune

Este Guia de introdução ajuda-o a ativar rapidamente a sua aplicação móvel para Gestão de Aplicações Móveis com o Microsoft Intune. Será útil compreender primeiro os benefícios do SDK da Aplicação do Intune, conforme enumerado na [Descrição Geral do SDK da ](intune-app-sdk.md).

Este guia explica os principais passos necessários para ativar a gestão de aplicações móveis na sua aplicação com o Microsoft Intune. O SDK da Aplicação do Intune suporta cenários semelhantes entre plataformas e destina-se a criar uma experiência consistente transversalmente entre as plataformas para administradores de TI. No entanto, existem pequenas diferenças no suporte de determinadas funcionalidades devido às limitações das plataformas.

# Introdução

## Registar a aplicação da loja no Microsoft

**Se a sua aplicação é interna da sua empresa e não será disponibilizada numa loja de aplicações pública**:

**Não é necessário** registar a sua aplicação. Para aplicações de linha de negócio internas, o administrador de TI irá implementar a aplicação internamente utilizando o Microsoft Intune. O Intune deteta que a aplicação foi criada com o SDK e permite ao administrador de TI aplicar definições de política MAM à mesma. Pode avançar para a secção [Ativar a aplicação móvel iOS ou Android para MAM com o SDK](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk).

**Se a sua aplicação será lançada numa loja de aplicações pública, como a Apple App Store ou o Google Play**: 

Primeiro, **tem** de registar a sua aplicação com o Microsoft Intune e aceitar os termos de registo. Depois de a registar, os administradores de TI poderão aplicar as definições de política de MAM do Intune à aplicação otimizada, que será listada como parceira de aplicações do Intune. Até o registo ser concluído e confirmado pela equipa do Microsoft Intune os administradores do Intune não terão a opção de aplicar a política de MAM na ligação avançada da sua aplicação. A Microsoft também irá adicionar a sua aplicação à [página de Parceiros do Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners), onde o ícone da aplicação será apresentado para mostrar que suporta a política de MAM do Microsoft Intune.

Para iniciar o processo de registo, **reveja e assine** o [Contrato para Parceiros do Microsoft Intune](https://connect.microsoft.com/ConfigurationManagervnext/Survey/Survey.aspx?SurveyID=17806). Este contrato descreve os termos que a sua empresa tem de aceitar antes de se tornar parceira de aplicações do Microsoft Intune. Terá de iniciar sessão antes de poder ver este documento. Pode encontrar o contrato no site Microsoft Connect do SDK da Aplicação do Intune no separador Inquéritos ou aqui. Também vamos pedir o nome da aplicação, o nome da sua empresa, bem como a ligação avançada da loja da Google ou do iTunes da aplicação.

![Microsoft Connect](../media/microsoft-connect.png)

Utilizaremos o seu endereço de e-mail de registo para confirmar e concluir a receção do processo de registo. Além disso, utilizamos o seu endereço de e-mail de registo para contactá-lo se tivermos alguma dúvida.

**O que pode esperar no processo de registo**: 

Depois de ter submetido o formulário, será contactado pela Microsoft através do seu endereço de e-mail de registo, para confirmar a receção bem-sucedida ou para pedir informações adicionais para concluir o registo. Também será contactado quando a sua aplicação for registada com êxito no Microsoft Intune e estiver em destaque no site dos parceiros do Microsoft Intune. Após a confirmação da receção das informações, a ligação avançada da aplicação será incluída na próxima atualização mensal do serviço do Intune. Por exemplo, se as informações de registo estiverem concluídas em julho, a ligação avançada da aplicação será suportada em meados de agosto. Se a ligação avançada da aplicação da loja for alterada no futuro, terá de voltar a registar a aplicação. Além disso, informe-nos se atualizar a sua aplicação com uma nova versão do SDK da Aplicação do Intune.

**Nota**: todas as informações recolhidas no formulário acima e através de correspondência de e-mail com a equipa do Intune respeitarão a [Declaração de Privacidade da Microsoft](https://www.microsoft.com/en-us/privacystatement/default.aspx).

## Transferir os ficheiros do SDK

Os SDKs da Aplicação do Intune para iOS e Android estão alojados numa conta Microsoft GitHub. Os seguintes repositórios públicos contêm os ficheiros do SDK para iOS e Android, respetivamente:

* [SDK da Aplicação do Intune para iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [SDK da Aplicação do Intune para Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

Recomendamos que se inscreva numa conta do GitHub que pode utilizar para bifurcar e obter dados dos nossos repositórios. O GitHub permite aos programadores comunicar com a nossa equipa de produto, colocar questões e receber respostas rápidas, ver notas de versão e fornecer feedback à Microsoft. Se tiver perguntas sobre os repositórios e a conta do GitHub, contacte msintuneappsdk@microsoft.com.

## Ativar a aplicação móvel iOS ou Android para MAM com o SDK

Para integrar o SDK da Aplicação do Intune na sua aplicação iOS, terá de fazer o seguinte: 

* **[Guia para Programadores do SDK da Aplicação do Intune para iOS](intune-app-sdk-ios.md)**: este documento irá guiá-lo passo a passo através da ativação da aplicação móvel iOS com o SDK da Aplicação do Intune. 


Para integrar o SDK da Aplicação do Intune na sua aplicação Android, terá de fazer o seguinte:

* **[Guia para Programadores do SDK da Aplicação do Intune para Android](intune-app-sdk-android.md)**: este documento irá guiá-lo passo a passo através da ativação da aplicação móvel Android com o SDK da Aplicação do Intune. 



## Configurar a Telemetria na sua aplicação

O Microsoft Intune recolhe dados sobre estatísticas de utilização da sua aplicação.

* **SDK da Aplicação para iOS**: o SDK regista dados telemétricos do SDK sobre eventos de utilização por predefinição. Estes dados são enviados para o Microsoft Intune.

    * Se optar por não enviar os dados telemétricos do SDK para o Microsoft Intune a partir da sua aplicação, terá de desativar a transmissão de telemetria ao definir a propriedade `MAMTelemetryDisabled` como "YES" no dicionário IntuneMAMSettings.

* **SDK da Aplicação do Intune para Android**: os dados telemétricos não são registados através do SDK.

## Testar a aplicação ativada para MAM com o Microsoft Intune

Depois de concluir os passos necessários para integrar a aplicação iOS ou Android com o SDK da Aplicação do Intune, terá de garantir que todas as políticas de gestão de aplicações estão ativadas e a funcionar no utilizador final e no administrador de TI. Para testar a aplicação integrada, necessitará do seguinte:

<!--TODO-->

* **Testar a aplicação ativada para MAM com o Microsoft Intune**: este documento irá guiá-lo passo a passo para saber como testar as suas aplicações para iOS ou Android ativadas para MAM com o Microsoft Intune. Pode encontrar este documento nos repositórios do GitHub dos SDKs.

* **Conta do Microsoft Intune**: para testar as suas aplicações ativadas para MAM com o Microsoft Intune, vai precisar de uma conta do Microsoft Intune. 
    * Se for um ISV e estiver a ativar as suas aplicações de loja iOS ou Android para MAM do Intune, receberá um código promocional depois de concluir o registo no Microsoft Intune, conforme descrito no passo de registo. O código promocional vai permitir-lhe inscrever-se para obter uma versão de avaliação do Microsoft Intune de 1 ano de utilização expandida. 
    * Se estiver a desenvolver uma aplicação de linha de negócio que não será enviada para a loja, é esperado que tenha acesso ao Microsoft Intune através da sua organização. Também pode inscrever-se para obter uma versão de avaliação gratuita de 1 mês com o [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).




<!--HONumber=Sep16_HO4-->


