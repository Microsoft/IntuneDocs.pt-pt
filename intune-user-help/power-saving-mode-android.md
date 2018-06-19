---
title: A otimização de energia está a impedir o acesso ao e-mail | Documentos Microsoft
description: Descubra como desativar a otimização de energia em dispositivos Android de modo a ter acesso ao e-mail.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ad713f18-40a9-421f-aa2b-f8c21028d57c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 663da92e11befeae1f65467e887870a52640cbeb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31020576"
---
# <a name="outlook-wont-sync-managed-email-when-battery-optimization-for-android-is-turned-on"></a>O Outlook não sincroniza e-mails geridos quando a otimização da bateria em dispositivos Android está ativada

> [!IMPORTANT]
> Este problema foi documentado aqui porque temos sido contactados pelos clientes diversas vezes em relação ao mesmo. Se continuar a deparar-se com este problema após seguir estes passos, contacte [o suporte da empresa](https://portal.manage.microsoft.com#HelpDeskDialog) para obter ajuda adicional.

Inscrever o seu dispositivo no Intune permite-lhe obter acesso a recursos da empresa. Um dos recursos mais comuns é o acesso ao e-mail. Um problema que temos registado ao aceder ao e-mail através do Outlook para dispositivos Android ocorre quando a otimização da bateria está ativada. A otimização da bateria poderá ser ativada automaticamente de forma a ajudar o seu dispositivo a permanecer ligado durante mais tempo. A otimização da bateria poderá contribuir para este fim porque tenta parar as transferências de e-mail automáticas.

A equipa do Microsoft Intune está a trabalhar ativamente numa solução para este problema. Uma forma de impedir o dispositivo de entrar no modo de energia baixa consiste em certificar-se de que a bateria mantém uma carga superior a 30%. Para impedir que este problema ocorra quando entra no modo de energia baixa, tem de remover o Portal da Empresa e o Outlook da lista de aplicações que são afetadas pelas definições de otimização da bateria e de poupança de energia.

Existem vários dispositivos Android de diversos fabricantes. Não iremos documentar os passos exatos que precisa de efetuar para todos os dispositivos. Poderá ter de efetuar estas ações apenas nas suas definições do sistema ou também em algumas definições específicas a um fabricante. Disponibilizámos alguns exemplos comuns de como resolver este problema em dispositivos Android.

## <a name="unmodified-android-devices"></a>Dispositivos Android não modificados

Muitos fabricantes adicionam modificações aos respetivos dispositivos Android. Isto pode alterar algumas formas de interagir com o dispositivo, como temas e notificações. A Google geralmente não efetua este tipo de modificações aos telemóveis. Por exemplo, num dispositivo Google Pixel com o Android 7.0 ou superior, pode seguir estes passos para remover as aplicações da otimização de bateria:

1. Abra **Definições**.
2. Toque em **Bateria** > **Mais** > **Otimização da bateria**.
3. Toque na seta pendente e, em seguida, em **Não otimizada**.
4. Selecione as aplicações Portal da Empresa e Outlook e desative a otimização da bateria.

## <a name="samsung-devices"></a>Dispositivos Samsung

Para outros tipos de dispositivos Android, tal como os dispositivos Samsung com o Android 7.0 ou superior, terá de seguir outros passos para remover as aplicações Portal da Empresa e Outlook da otimização de bateria.

1. Abra **Definições**.
2. Toque em **Menu (...)** > **Acesso especial** > **Otimizar a utilização da bateria**.
3. Selecione **Todas as aplicações** a partir da lista pendente.
4. Ative o **botão** junto das aplicações Portal da Empresa e Outlook para desativar a otimização da bateria.

Para além disso, se estiver a utilizar um dispositivo Samsung com uma versão inferior do Android, terá de seguir estes passos para remover estas aplicações do modo de poupança de energia.

1. Abra **Definições**.
2. Toque em **Gestão do dispositivo** > **Bateria** > **Aplicações não monitorizadas**.
3. Toque em **Adicionar aplicações**.
4. Selecione as aplicações Portal da Empresa e Outlook e toque em **Concluído**.

## <a name="oneplus-devices"></a>Dispositivos OnePlus

Outra forma de localizar estas definições é através da pesquisa nas definições do sistema. Por exemplo, num OnePlus 3 com o Android 7.1.1, siga estes passos: 

1. Abra as **Definições do Sistema**. 
2. Toque no botão **Pesquisar**. Tem o aspeto de uma lupa no canto superior direito do ecrã. 
3. Escreva **otimização da bateria** na pesquisa e, em seguida, selecione a opção **Otimização da Bateria** no ecrã **Definições** que é apresentado. 
4. Toque em **Bateria** > **Otimização da bateria**.
5. Selecione as aplicações Portal da Empresa e Outlook e, em seguida, selecione **Não otimizar**. Toque em **Concluído**.

<!--On a OnePlus 5 device with Android 7.1.1, you would follow these steps to remove these apps from battery optimization:
1. Open **Settings**.
2. Tap **Battery** > **Battery optimization**.
3. Select the Company Portal and Outlook apps, then select **Don’t optimize**. Tap **Done**.-->

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
