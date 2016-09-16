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
ms.sourcegitcommit: 952cfa4f23f8ba080ce53f6785baceb8a0a367c6
ms.openlocfilehash: 9adcf9ce1c2c6e40b3fcbb6c733585bb73a5cc01


---

# Introdução ao SDK da Aplicação Microsoft Intune

Este Guia de introdução ajuda-o a ativar rapidamente a sua aplicação móvel para Gestão de Aplicações Móveis com o Microsoft Intune. Será útil compreender primeiro os benefícios do SDK da Aplicação do Intune, conforme enumerado na [Descrição Geral do SDK da ](intune-app-sdk.md).

Este guia explica os principais passos necessários para ativar a gestão de aplicações móveis na sua aplicação com o Microsoft Intune. O SDK da Aplicação do Intune suporta cenários semelhantes entre plataformas e destina-se a criar uma experiência consistente transversalmente entre as plataformas para administradores de TI. No entanto, existem pequenas diferenças no suporte de determinadas funcionalidades devido às limitações das plataformas.

# Introdução

## Registar-se no Microsoft Connect

O SDK da Aplicação do Intune está atualmente acessível através do Microsoft Connect e requer inscrição. Para tal, registe-se numa [Conta Microsoft](https://connect.microsoft.com/ConfigurationManagervnext/InvitationUse.aspx?ProgramID=8967&InvitationID=8967-YJYJ-8G6X) com o seu e-mail empresarial.

O estado do seu registo estará pendente até a equipa do Intune analisar o pedido. O tempo de resposta típico é entre 2 a 3 dias úteis. Quando for aprovado, receberá uma notificação por e-mail com as ligações para transferir o SDK da Aplicação do Intune para as suas plataformas e todos os guias relacionados. Também pode aceder a estes guias no site MSDN.

## Registar a aplicação da loja no Microsoft Intune

**Se a aplicação ativada for interna da sua empresa e não for disponibilizada nas lojas de aplicações da Apple ou da Google**: não é necessário registar a aplicação. Estas aplicações internas são carregadas pelo administrador de TI diretamente na consola do Microsoft Intune para implementação; o Intune vai detetar que foram criadas com o SDK e apresentará ao administrador de TI a opção para aplicar a política de MAM às mesmas. Pode avançar para a secção intitulada [Ativar a aplicação móvel iOS ou Android para MAM com o SDK](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk).

**Se for um ISV e estiver a desenvolver uma aplicação que será disponibilizada para clientes através das lojas de aplicações da Apple ou da Google**: primeiro, tem de registar a sua aplicação no Microsoft Intune e aceitar os termos de registo. Pode fornecer a ligação avançada da aplicação neste momento. Mais tarde, um administrador de TI pode aplicar a política de MAM do Intune à aplicação. Até o registo ser concluído e confirmado pela equipa do Microsoft Intune, a ligação avançada da aplicação não terá a opção de aplicar a política de MAM na consola de administração. A Microsoft também tem um Web site de Parceiros do Microsoft Intune, onde a aplicação será registada para que os clientes saibam que suporta a política de MAM do Microsoft Intune.

Para iniciar o processo de registo, **reveja e assine** o [Contrato para Parceiros do Microsoft Intune](https://connect.microsoft.com/ConfigurationManagervnext/Survey/Survey.aspx?SurveyID=17806). Este contrato descreve os termos que a sua empresa tem de aceitar antes de se tornar parceira de aplicações do Microsoft Intune. Terá de iniciar sessão antes de poder ver este documento. Pode encontrar o contrato no site Microsoft Connect do SDK da Aplicação do Intune no separador Inquéritos ou aqui. Também vamos pedir o nome da aplicação, o nome da sua empresa, bem como a ligação avançada da loja da Google ou do iTunes da aplicação.

![Microsoft Connect](../media/microsoft-connect.png)

Utilizaremos o seu endereço de e-mail de registo para confirmar e concluir a receção do processo de registo. Além disso, utilizamos o seu endereço de e-mail de registo para contactá-lo se tivermos alguma dúvida.

**O que pode esperar do processo de registo**: depois de ter submetido o formulário, será contactado pela Microsoft através do seu endereço de e-mail de registo para confirmar a receção bem-sucedida ou para pedir informações adicionais para concluir o registo. Também será contactado quando a sua aplicação for registada com êxito no Microsoft Intune e estiver em destaque no site dos parceiros do Microsoft Intune. Após a confirmação da receção das informações, a ligação avançada da aplicação será incluída na próxima atualização mensal do serviço do Intune. Por exemplo, se as informações de registo estiverem concluídas em julho, a ligação avançada da aplicação será suportada em meados de agosto. Se a ligação avançada da aplicação da loja for alterada no futuro, terá de voltar a registar a aplicação. Além disso, informe-nos se atualizar a sua aplicação com uma nova versão do SDK da Aplicação do Intune.

**Nota**: todas as informações recolhidas no formulário acima e através de correspondência de e-mail com a equipa do Intune respeitarão a [Declaração de Privacidade da Microsoft](https://www.microsoft.com/en-us/privacystatement/default.aspx).

## Ativar a aplicação móvel iOS ou Android para MAM com o SDK

Para ativar a sua aplicação móvel iOS, necessitará do seguinte:

1. **[Guia para Programadores do SDK da Aplicação do Intune para iOS](intune-app-sdk-ios.md)**: este documento irá guiá-lo passo a passo através da ativação da aplicação móvel iOS com o SDK da Aplicação do Intune. Pode encontrar este documento na pasta de documentação que transferiu como parte do pacote do SDK da Aplicação do Intune.
2. **SDK da Aplicação do Intune para iOS**: como parte do pacote do SDK da Aplicação do Intune transferido a partir do Microsoft Intune, vai encontrar uma pasta "SDK da Aplicação do Intune para iOS" assinada. Esta pasta tem todos os conteúdos do SDK da Aplicação do Intune para iOS.

Para ativar a sua aplicação móvel Android com o SDK da Aplicação do Intune, necessitará do seguinte:

1. **[Guia para Programadores do SDK da Aplicação do Intune para Android](intune-app-sdk-android.md)**: este documento irá guiá-lo passo a passo através da ativação da aplicação móvel Android com o SDK da Aplicação do Intune. Pode encontrar este documento na pasta de documentação que transferiu como parte do pacote do SDK da Aplicação do Intune.
2. **SDK da Aplicação do Intune para Android**: como parte do pacote do SDK da Aplicação do Intune transferido a partir do Microsoft Intune, vai encontrar uma pasta "SDK da Aplicação do Intune para Android" assinada. Esta pasta tem todos os conteúdos do SDK da Aplicação do Intune para Android.

## Desativar a telemetria na sua aplicação

**SDK da Aplicação para iOS**: o SDK regista dados telemétricos do SDK sobre eventos de utilização por predefinição. Estes dados são enviados para o Microsoft Intune.

Se optar por não enviar os dados telemétricos do SDK para o Microsoft Intune a partir da sua aplicação, **terá de desativar** a transmissão de telemetria do SDK ao definir a propriedade `MAMTelemetryDisabled` como ’‘YES’’, em `IntuneMAMSettings`.

**SDK da Aplicação do Intune para Android**: os dados telemétricos do SDK não são registados através do SDK.

## Testar a aplicação ativada para MAM com o Microsoft Intune

Depois de concluir os passos necessários para otimizar (integrar o SDK da Aplicação do Intune) o SDK da Aplicação do Intune para iOS ou Android, terá de garantir que todas as políticas de gestão de aplicações estão ativadas e a funcionar no utilizador final e no administrador de TI. Para testar a aplicação otimizada, necessitará do seguinte:

1. **Testar a aplicação ativada para MAM com o Microsoft Intune**: este documento irá guiá-lo passo a passo para saber como testar as suas aplicações para iOS ou Android ativadas para MAM com o Microsoft Intune. Pode encontrar este documento na pasta de documentação que transferiu como parte do pacote do SDK da Aplicação do Intune.
2. **Conta do Microsoft Intune**: para testar as suas aplicações ativadas para MAM com o Microsoft Intune, vai precisar de uma conta do Microsoft Intune. Se for um ISV e estiver a ativar as suas aplicações de loja iOS ou Android para MAM, vai receber um código promocional depois de concluir o registo no Microsoft Intune, conforme descrito no passo de registo. O código promocional vai permitir-lhe inscrever-se para obter uma versão de avaliação do Microsoft Intune de 1 ano de utilização expandida. Se estiver a desenvolver uma aplicação de linha de negócio que não será enviada para a loja, é esperado que tenha acesso ao Microsoft Intune através da sua organização. Também pode inscrever-se para obter uma versão de avaliação gratuita de 1 mês com o [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).




<!--HONumber=Sep16_HO2-->


