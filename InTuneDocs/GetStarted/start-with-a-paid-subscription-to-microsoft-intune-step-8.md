---
title: "Inscrever dispositivos móveis e instalar aplicações | Microsoft Intune"
description: "Explica como inscrever dispositivos móveis e instalar uma aplicação num dispositivo inscrito no Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3306d772b074ddcfd1bfcf7178b32f9b371321e7
ms.openlocfilehash: f57728bb41b750f53b021bed532de18187e764a0


---

# Inscrever dispositivos móveis e instalar aplicações
Para configurar a gestão de dispositivos móveis com o Intune, tem de começar por definir a autoridade de gestão de dispositivos móveis, ativar a gestão para as plataformas de dispositivos e, em seguida, inscrever os dispositivos com a aplicação Portal da Empresa. Em seguida, pode implementar a aplicação Microsoft Skype que publicou no passo 6.

## Ativar a gestão de dispositivos e inscrever dispositivos

1.  **Tornar o Intune a autoridade de gestão de dispositivos móveis** Na [consola de administração do Intune](https://manage.microsoft.com/), escolha **Administração**  >  **Gestão de Dispositivos Móveis** e escolha **Definir Autoridade MDM**, em **Tarefas**.  Escolha **Sim** na caixa de diálogo Autoridade de MDM.
    ![Consola de administração. Definir MDM para o Intune](./media/mdmAuthority.png)

2.  **Ativar MDM na plataforma de dispositivos** Ative a gestão de dispositivos móveis na plataforma de dispositivos que pretende gerir. Dependendo da sua plataforma, são necessários requisitos diferentes:

    -   **iOS e Mac OS X**: consulte [Configurar a gestão de iOS e Mac com o Microsoft Intune](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).

    -   **Windows Phone**: consulte [Configurar a gestão do Windows Phone com o Microsoft Intune](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune).

    -   **Android**: os dispositivos móveis Android permitem aos utilizadores utilizar a aplicação Portal da Empresa, disponível no [Google Play](https://play.google.com/store/apps/details?id=com.skype.raider), para se inscreverem. Não é necessária nenhuma configuração adicional no Intune.

3.  **Inscrever dispositivos**:

    -   **Android** - Instale a aplicação **Portal da Empresa do Intune**, da Microsoft Corporation, disponível no [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612), e inicie sessão com as credenciais de utilizador do Intune adicionadas acima.

    -   **iOS e Mac OS X** - Instale a aplicação **Portal da Empresa do Microsoft Intune**, da Microsoft Corporation, disponível na Loja de Aplicações, e inicie sessão com as credenciais de utilizador do Intune adicionadas acima. Veja os **Dispositivos inscritos** para adicionar o seu dispositivo.

    -   **Windows Phone 8.1** - Os utilizadores devem instalar a aplicação **Portal da Empresa**, da Microsoft Corporation, disponível na loja do Windows Phone, e iniciar sessão com as credenciais de utilizador do Intune adicionadas acima.  Veja os **Dispositivos inscritos** para adicionar o seu dispositivo.

    -   **Windows Phone 8.0** - os utilizadores devem escolher **definições do sistema** &gt; **aplicações da empresa** e iniciar sessão com as credenciais de utilizador do Intune adicionadas acima. A aplicação Portal da Empresa é implementada no seu telemóvel.

    Se for pedido o **Endereço do servidor**, escreva "manage.microsoft.com".

## Instalar uma aplicação num dispositivo inscrito
No [passo 6](start-with-a-paid-subscription-to-microsoft-intune-step-6.md) deste guia de introdução, publicou a aplicação Skype no grupo de Utilizadores do Intune personalizado. Agora, irá instalar a aplicação num dispositivo inscrito recentemente.

Abra o Portal da Empresa no dispositivo móvel inscrito, escolha **Aplicações**e, em seguida, instale o **Microsoft Skype**.

Para saber mais sobre a gestão de dispositivos móveis com o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], consulte [Pré-requisitos para a inscrição de dispositivos no Microsoft Intune](/intune/deploy-use/prerequisites-for-enrollment).


### Passos seguintes
Parabéns! Acabou de concluir o último passo do *Guia de introdução do Intune*. Agora que a configuração inicial está concluída, pode considerar a ativação da funcionalidade MDM adicional.

>[!div class="step-by-step"]

>[&larr;**Inscrever dispositivos**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)     [**Tarefas de pós-configuração**&rarr;](.\post-configuration-tasks.md)  



<!--HONumber=Oct16_HO3-->


