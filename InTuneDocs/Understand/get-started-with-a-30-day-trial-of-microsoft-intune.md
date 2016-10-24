---
title: "Guia de avaliação do Intune | Microsoft Intune"
description: "Introdução e pré-requisitos sobre como configurar uma avaliação gratuita de 30 dias do Intune"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 08/09/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 581e880fa4308ec627f5b2c1242fb5b30b713743
ms.openlocfilehash: 3973ac11d4734b17f905e88259863d7ddb59c1f4


---

# Guia de avaliação do Intune
Configurar uma avaliação gratuita de 30 dias do Intune para gerir os seus dispositivos móveis e computadores é um processo rápido e fácil. Com apenas alguns passos simples na avaliação, pode adicionar até 100 utilizadores e dispositivos, configurar grupos, configurar políticas de conformidade, bem como inscrever e gerir dispositivos móveis e computadores.

Neste tópico, irá aprender as noções básicas para ter acesso a uma avaliação do Intune operacional e obter uma descrição geral do serviço que lhe permitirá avaliar as funcionalidades e capacidades do Intune.

Veja o seguinte vídeo de demonstração de cinco minutos para saber como é fácil dar os primeiros passos com uma avaliação gratuita do Microsoft Intune e como gerir os seus dispositivos. A primeira parte do vídeo refere um portal que foi "extinto", pelo que, embora vá utilizar um portal diferente, os passos são essencialmente iguais. Pode ler mais sobre o portal [aqui](https://docs.microsoft.com/intune/deploy-use/account-portal-merged-with-Office-365).

<iframe width="675" height="480" src="https://www.youtube.com/embed/ltcZvm4VOFU" frameborder="0" allowfullscreen></iframe>

## Antes de começar
Antes de começar com o Intune, irá precisar do seguinte:

-   Um dispositivo com um Web browser com capacidade para Silverlight que possa ser utilizado para aceder aos sites nos quais irá criar contas de utilizador do Intune (o **centro de administração do Office 365**) e onde irá gerir dispositivos, grupos e políticas (a **consola de administração do Intune**).

-   Um segundo dispositivo com um browser que será utilizado para testar a forma como os utilizadores do Intune irão inscrever e gerir os respetivos dispositivos através do Portal da Empresa. Também irá testar a forma como os utilizadores localizam e instalam as aplicações, e pedem ajuda aos administradores. Se não tiver um segundo dispositivo, pode utilizar a definição "modo de privacidade" no mesmo browser que utiliza para fins de administração do Intune (por exemplo, no Internet Explorer, pode selecionar **Ferramentas** &gt; **Navegação InPrivate**).

-   Se tiver uma conta existente do Microsoft Online Services, irá precisar das credenciais de administrador dessa conta. Se não tiver uma conta deste género ou se quiser utilizar este inquilino Intune para fins de avaliação apenas, não precisa destas credenciais de administrador.

-   Se pretender gerir dispositivos iOS ou Windows Phone 8.1 com a avaliação do Intune, irá precisar de certificados (ou chaves) e contas para obter os certificados em questão (consulte a tabela seguinte). Os dispositivos Android não precisam de certificados adicionais.

    |Plataforma|Requisitos de Certificados|Mais informações|
    |------------|----------------------------|--------------------|
    |Windows Phone 8.1 |Os utilizadores do Windows Phone 8.1 que instalem a aplicação Portal da Empresa a partir da Loja não precisam de certificados. |Este documento de orientação pressupõe que os utilizadores obtêm a aplicação Portal da Empresa a partir da Loja em dispositivos Windows Phone 8.1 ou posteriores. |
    |Dispositivos Windows 10, Windows RT 8.1 ou Windows 8.1|Não existem requisitos de certificados para inscrever dispositivos Windows RT e Windows.|[Instalar o cliente do PC Windows com o Microsoft Intune](/Intune/Deploy-Use/install-the-windows-pc-client-with-microsoft-intune).|
    |iOS 7.1 ou posterior|Obtenha um certificado do serviço Apple Push Notification.|Peça um certificado de serviço Apple Push Notification da Apple, conforme descrito aqui: [Configurar a gestão de iOS e Mac com o Microsoft Intune](/Intune/Deploy-Use/set-up-ios-and-mac-management-with-microsoft-intune).|

## Passos para concluir uma avaliação de 30 dias do Intune
- [Passo 1: Iniciar sessão ou inscrever-se numa avaliação de 30 dias](get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md). Antes de se inscrever ou iniciar sessão no Intune, deve considerar se pretende iniciar sessão com uma conta existente ou criar uma conta temporária para ser utilizada apenas para a avaliação de 30 dias do Microsoft Intune.
- [Passo 2: Adicionar utilizadores](get-started-with-a-30-day-trial-of-microsoft-intune-step-2.md). Agora que configurou a sua conta, irá adicionar contas de utilizador individuais ao Intune ou adicionar utilizadores em volume (consulte as instruções nesta secção). Antes de começar, é importante que compreenda a forma como o Intune processa as contas de administrador.
- [Passo 3: Criar grupos para organizar utilizadores e dispositivos](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md). Os Grupos no Intune dão-lhe uma grande flexibilidade na gestão dos seus dispositivos e utilizadores. Pode configurar os grupos conforme as suas necessidades organizacionais (por exemplo, por localização geográfica, por departamento ou por características de hardware) e utilizá-los para efetuar uma variedade de tarefas administrativas em escala, desde definir políticas para um conjunto de utilizadores a implementar aplicações num conjunto de dispositivos.
- [Passo 4: Criar políticas e publicar aplicações](get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md). As políticas do Intune disponibilizam definições que o ajudam a controlar as definições de segurança nos dispositivos móveis, a gerir as definições de Endpoint Protection e Firewall do Windows de computadores e a implementar aplicações.
- [Passo 5: Inscrever dispositivos móveis e instalar aplicações](get-started-with-a-30-day-trial-of-microsoft-intune-step-5.md). Para configurar a gestão de dispositivos móveis com o Intune, tem de definir a autoridade de gestão de dispositivos móveis, ativar a gestão para plataformas de dispositivos específicas e inscrever os dispositivos com a aplicação Portal da Empresa. Depois, pode implementar a aplicação Microsoft Skype que publicou.
- [Passo 6: Outras opções e extras](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md). Escolha como pretende utilizar alertas, relatórios e outras funcionalidades do Intune para satisfazer as suas necessidades empresariais.
- [Passo 7: Passos seguintes](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md). Prepare-se para mudar para uma subscrição paga do Intune e tirar partido do Benefício do FastTrack Center para o Intune.


### Passos seguintes
Está na altura de começar a utilizar a sua subscrição de avaliação de 30 dias!

>[!div class="step-by-step"]
[**Inscrever-se no Intune** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)

### Consulte também
[Guia de introdução do Intune](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune)



<!--HONumber=Oct16_HO2-->


