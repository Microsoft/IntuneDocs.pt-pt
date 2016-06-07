---
# required metadata

title: Enviar registos de dados de diagnóstico ao administrador de TI por e-mail | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 85c868e7-8d63-480c-9770-4e99614a5c94

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Enviar registos de dados de diagnóstico ao administrador de TI por e-mail

Se obtiver um erro no dispositivo Android enquanto está a trabalhar com as suas aplicações escolares ou empresariais ou enquanto está na aplicação Portal da Empresa, pode enviar registos de dados de diagnóstico para ajudar o administrador de TI a descobrir e corrigir o erro. Para incluir todos os detalhes nos registos, os quais tornarão mais fácil para o administrador de TI descobrir o problema, ative o Registo Verboso.

Para ativar o registo verboso:

1.  Abra a aplicação Portal da Empresa.

2.  Toque em **Menu** &gt;  **Definições**

    > **Menu** pode ser um botão de software ou um botão de hardware, consoante o tipo de dispositivo Android que tem.

3.  Em **Dados de Diagnóstico**, toque em **Enviar Dados**

    > **Apenas se estiver a utilizar dispositivos Android 6.0 ou posteriores:** ao tocar em **Enviar Dados**, verá a mensagem, **Permitir que o Portal da Empresa aceda a fotografias, multimédia e ficheiros no seu dispositivo?** 

    Esta mensagem é enganosa, porque a **Microsoft nunca acede a fotografias, multimédia ou ficheiros no seu dispositivo!** A Google controla o texto da mensagem, pelo que a Microsoft não a pode alterar.  Ao permitir o acesso, está a permitir que o seu dispositivo escreva registos de dados no cartão SD do dispositivo, o que lhe permite mover esses registos com um cabo USB.

    Se negar o acesso, irá aparecer a mensagem novamente quando tocar em **Enviar Dados**, mas pode desativar futuras mensagens ao tocar na caixa de verificação **Não voltar a perguntar**.  Se, posteriormente, o utilizador decidir permitir o acesso, aceda a **Definições** &gt; **Aplicações** &gt; **Portal da Empresa** &gt; **Permissões** &gt; **Armazenamento**, e, em seguida, ative a permissão.

4.  Siga as indicações para escolher uma aplicação de e-mail a utilizar para enviar os registos ao administrador de TI. A aplicação criará um e-mail pré-endereçado com todos os registos anexados.


### Consulte também
[Utilizar o dispositivo Android com o Intune](using-your-android-device-with-intune.md)

<!--HONumber=May16_HO2-->

