---
title: "Enviar registos de dados de diagnóstico ao administrador de TI por e-mail | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: jeffgilb
ms.date: 05/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 85c868e7-8d63-480c-9770-4e99614a5c94
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0bb435b87c937ea118a0794c8332b9a8f268d36e
ms.openlocfilehash: 57646f103fb0520295729a89a30692c657896e55


---


# Enviar registos de dados de diagnóstico ao administrador de TI por e-mail

Se obtiver um erro no dispositivo Android enquanto está a trabalhar com as suas aplicações escolares ou empresariais ou enquanto está na aplicação Portal da Empresa, pode enviar registos de dados de diagnóstico para ajudar o administrador de TI a descobrir e corrigir o erro. Para incluir todos os detalhes nos registos, os quais tornarão mais fácil para o administrador de TI descobrir o problema, ative o Registo Verboso. pode ler mais sobre classes base em [registo verboso](use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android.md).

Para ativar o registo verboso:

1.  Abra a aplicação Portal da Empresa.

2.  Toque em **Menu** &gt;  **Definições**.

    > [!NOTE] 
    > **Menu** pode ser um botão de software ou um botão de hardware, consoante o tipo de dispositivo Android que tem.

3.  Em **Dados de Diagnóstico**, toque em **Enviar Dados**.

    > [!NOTE]
    > **Apenas se estiver a utilizar dispositivos Android 6.0 ou posteriores:** quando toca em **Enviar Dados**, aparece a mensagem **Permitir que o Portal da Empresa aceda a fotografias, multimédia e ficheiros no seu dispositivo?**. 

    Esta mensagem é enganosa, porque a **Microsoft nunca acede a fotografias, multimédia ou ficheiros no seu dispositivo!** A Google controla o texto da mensagem, pelo que a Microsoft não a pode alterar.  Ao permitir o acesso, está a permitir que o seu dispositivo escreva registos de dados no cartão SD do dispositivo, o que lhe permite mover esses registos com um cabo USB.

    Se negar o acesso, irá aparecer a mensagem novamente quando tocar em **Enviar Dados**, mas pode desativar futuras mensagens ao tocar na caixa de verificação **Não voltar a perguntar**.  Se, posteriormente, decidir permitir o acesso, aceda a **Definições** &gt; **Aplicações** &gt; **Portal da Empresa** &gt; **Permissões** &gt; **Armazenamento** e ative a permissão.

4.  Siga as indicações para escolher uma aplicação de e-mail a utilizar para enviar os registos ao administrador de TI. A aplicação criará um e-mail pré-endereçado com todos os registos anexados.


### Consulte também
[Utilizar o dispositivo Android com o Intune](using-your-android-device-with-intune.md)


<!--HONumber=Jun16_HO4-->


