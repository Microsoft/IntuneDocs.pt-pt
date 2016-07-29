---
title: "Inscrever dispositivos móveis de avaliação | Microsoft Intune"
description: "Como inscrever dispositivos móveis e instalar uma aplicação quando se inscreve numa avaliação gratuita de 30 dias do Intune"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 60ee39a7eeeb9068a7350ec87f60e7148ccb7826
ms.openlocfilehash: d441bb68a28a18cf45c616271cb33556df9f67f3


---

# Inscrever dispositivos móveis de avaliação e instalar uma aplicação
Para configurar a gestão de dispositivos móveis com o Intune, tem de começar por definir a autoridade de gestão de dispositivos móveis, ativar a gestão para as plataformas de dispositivos e, em seguida, inscrever os dispositivos com a aplicação Portal da Empresa. Depois, pode implementar a aplicação Microsoft Skype que publicou.

## Preparar o serviço para a gestão de dispositivos

1.  **Tornar o Intune a autoridade de gestão de dispositivos móveis**

    Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), selecione **Administração** &gt; **Gestão de Dispositivos Móveis**. Escolha **Tarefas** > **Definir Autoridade de MDM** e escolha **Sim** na caixa de diálogo **Autoridade de MDM**.

2.  **Ativar MDM na plataforma de dispositivos**

    Ative a gestão de dispositivos móveis na plataforma de dispositivos que pretende gerir. Dependendo da sua plataforma, são necessários requisitos diferentes:

    -   **iOS e Mac OS X**: veja [Configurar a gestão de iOS e Mac com o Microsoft Intune](/Intune/Deploy-Use/set-up-ios-and-mac-management-with-microsoft-intune).

    -   **Android**: os dispositivos móveis Android permitem aos utilizadores utilizar a aplicação Portal da Empresa, disponível no Google Play, para se inscreverem. Não é necessária nenhuma configuração adicional no Intune.

    -   **Windows Phone**: veja [Configurar a gestão do Windows Phone com o Microsoft Intune](/Intune/Deploy-Use/set-up-windows-phone-management-with-microsoft-intune).

## Inscrever dispositivos de teste

### iOS e Mac OS X
Instale a aplicação **Portal da Empresa do Microsoft Intune**da Microsoft Corporation, disponível na App Store, e inicie sessão com as credenciais de utilizador do Intune adicionadas acima. Veja os **Dispositivos inscritos** para adicionar o seu dispositivo.

### Android
Instale a aplicação **Portal da Empresa do Intune**, da Microsoft Corporation, disponível no [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612), e inicie sessão com as credenciais de utilizador do Intune adicionadas acima.

### Windows Phone 8.1
Os utilizadores devem instalar a aplicação **Portal da Empresa**, da Microsoft Corporation, disponível na loja do Windows Phone, e iniciar sessão com as credenciais de utilizador do Intune adicionadas acima.  Veja os **Dispositivos inscritos** para adicionar o seu dispositivo.

 ### Windows Phone 8.0
 Os utilizadores devem clicar em **definições do sistema** &gt; **aplicações da empresa** e iniciar sessão com as credenciais de utilizador do Intune adicionadas acima. A aplicação Portal da Empresa é implementada no seu telemóvel.

Se for pedido o **Endereço do servidor**, escreva "manage.microsoft.com".


## Instalar a aplicação anteriormente implementada
Abra o Portal da Empresa no dispositivo móvel, escolha **Aplicações**e, em seguida, instale o **Microsoft Skype**.

Para saber mais sobre a gestão de dispositivos móveis através do Intune, consulte [Prepare-se para inscrever dispositivos no Microsoft Intune](/Intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune).

### Passos seguintes
Parabéns! Acabou de concluir o passo 5 das instruções da *avaliação do Microsoft Intune*.

>[!div class="step-by-step"]

>[&larr; **Criar Políticas**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)     [**Opções e extras** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)  



<!--HONumber=Jul16_HO4-->


