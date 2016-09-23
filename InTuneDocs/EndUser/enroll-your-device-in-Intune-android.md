---
title: Inscrever o dispositivo Android no Intune | Microsoft Intune
description: Descreve como encriptar dispositivos Android no Intune
keywords: 
author: staciebarker
manager: angrobe
ms.date: 09/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 47f9654af126d0e83890f797c321100f40ae497b
ms.openlocfilehash: 3d06e55607172d52538c7f4ec7aed843b64e3f53


---


# Inscrever o dispositivo Android no Intune

Se a sua empresa ou escola utiliza o Microsoft Intune, pode inscrever o seu dispositivo Android para aceder a e-mails, ficheiros e outros recursos da empresa. A inscrição de dispositivos permite ao departamento de TI gerir esses recursos do trabalho ou da escola e mantê-los seguros, dando-lhe a liberdade de utilizar o seu dispositivo preferencial para realizar o seu trabalho. Para saber mais sobre a inscrição, veja [What happens when I install and Company Portal app and enroll my device? (O que acontece quando instalo a aplicação Portal da Empresa e inscrevo o meu dispositivo?)](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-android.md).

Estas instruções de inscrição destinam-se a dispositivos Samsung Knox Android e a dispositivos Android "nativos" (não Samsung Knox). Para determinar se tem um dispositivo Samsung Knox, aceda a **Definições** &gt; **Acerca do dispositivo**. Se não vir a "versão KNOX" aí listada, tem um dispositivo Android nativo.

Antes ou depois da inscrição, poderá ser-lhe pedido para escolher uma categoria que melhor descreve como utiliza o seu dispositivo. O administrador de TI utiliza esta categoria para ajudar a determinar as aplicações a que tem acesso.

Se obtiver um erro ao tentar inscrever o dispositivo no Intune, pode [enviar erros de inscrição ao administrador de TI](send-enrollment-errors-to-your-it-administrator-android.md).

**Para inscrever o seu dispositivo Android:**

1.  Instale a aplicação gratuita do Portal da Empresa do Intune a partir do [Google Play](http://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal).

2.  Abra a aplicação Portal da Empresa do Microsoft Intune.

3.  No ecrã **Bem-vindo** do Portal da Empresa, toque em **Iniciar sessão** e, em seguida, inicie sessão com a sua conta escolar ou profissional.

    ![android-company-portal-sign-in](./media/and-enroll-0-welcome-screen.png)   

4.  Se o administrador de TI configurar termos e condições empresariais, toque em **ACEITAR** para aceitar os termos.

    ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5.  Inicie sessão na aplicação Portal da Empresa com a sua conta e palavra-passe profissional ou escolar e, em seguida, toque em **Iniciar sessão**.

    ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6.  No ecrã **Configuração de Acesso à Empresa**, toque em **COMEÇAR**.

    ![Ecrã Configuração de acesso à empresa](./media/and-enroll-4a-comp-access-setup.png)

7.  No ecrã **Porquê inscrever o seu dispositivo?**, leia sobre o que pode fazer quando inscrever o seu dispositivo e, em seguida, toque em **CONTINUAR**.

    ![Ecrã Porquê inscrever o seu dispositivo](./media/and-enroll-4b-why-enroll.png)

8.  Reveja uma lista do que o administrador de TI pode e não pode ver no seu dispositivo e toque em **CONTINUAR**.

    ![Definições de privacidade](./media/and-enroll-4c-we-care-privacy.png)

9.  No ecrã **O que vem a seguir**, leia sobre o que acontece durante a inscrição e, em seguida, toque em **INSCREVER**.

    ![Ecrã O que vem a seguir](./media/and-enroll-4d-what-comes-next.png)

10.  Se estiver a utilizar o Android 6.0 ou posterior, efetue este passo. Caso contrário, avance para o passo seguinte.

    Se o administrador de TI tiver configurado determinadas políticas, poderá ver as seguintes mensagens:
    -   **Permitir que o Portal da Empresa efetue e faça a gestão de chamadas telefónicas?**

    ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

    Se vir esta mensagem, toque em **PERMITIR**. É seguro tocar em PERMITIR, porque a **Microsoft nunca efetua ou gere as suas chamadas telefónicas**! A Google controla o texto da mensagem e a Microsoft não a pode alterar. Quando permite o acesso, o que está a fazer é permitir que o seu dispositivo envie o respetivo número IMEI para o Intune. O IMEI é um número, semelhante a um número de série, que identifica exclusivamente um dispositivo móvel.

    Se negar o acesso, irá aparecer a mensagem quando iniciar sessão novamente no Portal da Empresa, mas pode desativar futuras mensagens ao tocar na caixa de verificação **Não voltar a perguntar**.  Se, posteriormente, decidir permitir o acesso, aceda a **Definições** &gt; **Aplicações** &gt; **Portal da Empresa** &gt; **Permissões** &gt; **Telemóvel** e ative a permissão.

    -   **Permitir que o Portal da Empresa aceda aos seus contactos?**

    ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

    Se vir esta mensagem, toque em **PERMITIR**. É seguro tocar em PERMITIR, porque a **Microsoft nunca acede aos seus contactos!** A Google controla o texto da mensagem e a Microsoft não a pode alterar. Ao permitir o acesso, só permite à aplicação Portal da Empresa criar, utilizar e gerir a sua conta de trabalho.

    Se negar o acesso, irá aparecer a mensagem quando iniciar sessão novamente no Portal da Empresa, mas pode desativar futuras mensagens ao tocar na caixa de verificação **Não voltar a perguntar**.  Se, posteriormente, decidir permitir o acesso, aceda a **Definições** &gt; **Aplicações** &gt; **Portal da Empresa** &gt; **Permissões** &gt; **Telemóvel** e ative a permissão.

11.  No ecrã **Ativar administrador de dispositivo**, toque em **Ativar**.

    ![Ecrã Ativar administrador de dispositivo](./media/and-enroll-5-activate.png)

12.  Siga as indicações para introduzir um PIN ou palavra-passe. Se já configurou um PIN ou uma palavra-passe neste dispositivo, não verá este ecrã nem terá de introduzir um novo PIN ou palavra-passe.

    ![Introduzir PIN ou palavra-passe](./media/and-enroll-6-PIN-native.png)

13.  Se estiver a utilizar um dispositivo Samsung Knox, toque em **Confirmar** e verá uma mensagem a indicar que o dispositivo está a ser inscrito. Se estiver a utilizar um dispositivo Android nativo, repare apenas no ecrã abaixo que mostra que o dispositivo está a ser inscrito.

    ![Política de privacidade do Samsung KNOX](./media/and-enroll-7-knox-privacy-policy.png)

    Este ecrã mostra que o dispositivo está a ser inscrito.

    ![Ecrã Inscrever dispositivo](./media/and-enroll-8-device-enrolling.png)

14. Quando o ecrã **Configuração de Acesso à Empresa** aparece, toque em **CONTINUAR**. Se vir uma mensagem que indica que o seu dispositivo não está em conformidade, siga as instruções para corrigir o problema e, em seguida, toque em **CONTINUAR**.

    ![Ecrã Configuração de acesso à empresa](./media/and-enroll-9-comp-access-setup.png)  

11. No ecrã **Configuração de Acesso à Empresa concluída**, toque em **CONCLUÍDO**. O dispositivo está agora inscrito.

    ![Ecrã Configuração de acesso à empresa concluída](./media/and-enroll-10-comp-access-setup-complete.png)

Antes de tentar instalar aplicações da empresa, aceda a **Definições** &gt; **Segurança** e ative os **Recursos desconhecidos**. Se não ativar esta opção antes de tentar instalar aplicações, verá a mensagem "Instalação bloqueada." Por motivos de segurança, o dispositivo está definido para bloquear as instalações de aplicações obtidas a partir de origens desconhecidas." Pode tocar em **Definições** no diálogo de erro, para ir para a opção **Origens desconhecidas**.

Ainda precisa de ajuda? Contacte o se administrador de TI (verifique as informações de contacto no [Web site do Portal da Empresa](http://portal.manage.microsoft.com)) ou escreva para a equipa do Microsoft Android, através do endereço wintunedroidfbk@microsoft.com.






<!--HONumber=Sep16_HO2-->


