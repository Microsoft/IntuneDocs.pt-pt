---
# required metadata

title: Inscrever o dispositivo Android no Intune | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Inscrever o dispositivo Android no Intune

Se a sua empresa ou escola utiliza o Microsoft Intune, pode inscrever o seu dispositivo Android para aceder a e-mails, ficheiros e outros recursos da empresa. A inscrição de dispositivos permite ao departamento de TI gerir esses recursos do trabalho ou da escola e mantê-los seguros, dando-lhe a liberdade de utilizar o seu dispositivo preferencial para realizar o seu trabalho. Para mais informações sobre a inscrição, consulte [O que acontece quando instalo a aplicação Portal da Empresa e inscrevo o meu dispositivo?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-android.md)

Estas instruções de inscrição destinam-se a dispositivos Samsung Knox Android e a dispositivos Android "nativos" (não Samsung Knox). Para determinar se tem um dispositivo Samsung Knox, aceda a **Definições** &gt; **Sobre telefone**. Se não vir a palavra "Knox" aí indicada, tem um dispositivo Android nativo.

Antes ou depois da inscrição, poderá ser-lhe pedido para escolher uma categoria que melhor descreve como utiliza o seu dispositivo. O administrador de TI utiliza esta categoria para ajudar a determinar as aplicações a que tem acesso.

Se obtiver um erro ao tentar inscrever o dispositivo no Intune, pode [enviar erros de inscrição ao administrador de TI](send-enrollment-errors-to-your-it-administrator-android.md)

**Para inscrever o seu dispositivo Android:**

1.  Instale a aplicação gratuita Portal da Empresa do Intune a partir do [Google Play](http://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)

2.  Abra a aplicação Portal da Empresa do Microsoft Intune.

3.  No ecrã **Bem-vindo** do Portal da Empresa, toque em **Iniciar sessão** e, em seguida, inicie sessão com a sua conta escolar ou profissional.

    ![android-company-portal-sign-in](./media/and-enroll-0-welcome-screen.png)   

4.  Se o administrador de TI configurar termos e condições empresariais, toque em **ACEITAR** para aceitar os termos.

    ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5.  Se estiver a utilizar o Android 6.0 ou posterior, efetue este passo. Caso contrário, avance para o passo seguinte. 

    Se o administrador de TI tiver configurado determinadas políticas, poderá ver as seguintes mensagens:
    -   **Permitir que o Portal da Empresa efetue e faça a gestão de chamadas telefónicas?**

    ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

    Se vir esta mensagem, toque em **PERMITIR**. É seguro tocar em PERMITIR, porque a **Microsoft nunca efetua ou gere as suas chamadas telefónicas**! A Google controla o texto da mensagem e a Microsoft não a pode alterar. Ao permitir o acesso, está a permitir que o seu dispositivo escreva registos de dados no cartão SD do dispositivo, o que lhe permite mover esses registos com um cabo USB. Poderá ter de utilizar esta capacidade para enviar registos ao administrador de TI se tiver um problema ao utilizar a aplicação Portal da Empresa. Saiba como [enviar erros de inscrição ao administrador de TI](send-enrollment-errors-to-your-it-administrator-android.md)

    Se negar o acesso, irá aparecer a mensagem quando iniciar sessão novamente no Portal da Empresa, mas pode desativar futuras mensagens ao tocar na caixa de verificação **Não voltar a perguntar**.  Se, posteriormente, o utilizador decidir permitir o acesso, aceda a **Definições** &gt; **Aplicações** &gt; **Portal da Empresa** &gt; **Permissões** &gt; **Telefone**, e, em seguida, ative a permissão.

    -   **Permitir que o Portal da Empresa aceda aos seus contactos?**

    ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

    Se vir esta mensagem, toque em **PERMITIR**. É seguro tocar em PERMITIR, porque a **Microsoft nunca acede aos seus contactos!** A Google controla o texto da mensagem e a Microsoft não a pode alterar. Quando permite o acesso, só permite que a aplicação Portal da Empresa aceda aos registos de dados para ajudar a resolver problemas no seu dispositivo.

    Se negar o acesso, irá aparecer a mensagem novamente quando tocar em **Enviar Dados**, mas pode desativar futuras mensagens ao tocar na caixa de verificação **Não voltar a perguntar**. Se, posteriormente, o utilizador decidir permitir o acesso, aceda a **Definições** &gt; **Aplicações** &gt; **Portal da Empresa** &gt; **Permissões** &gt; **Armazenamento**, e, em seguida, ative a permissão.

6.  Inicie sessão na aplicação Portal da Empresa utilizando a sua conta profissional ou escolar e a palavra-passe e, em seguida, toque em **Iniciar sessão**.

    ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

7.  No ecrã **Configuração de Acesso à Empresa**, toque em **COMEÇAR**

    ![Ecrã Configuração de acesso à empresa](./media/and-enroll-4a-comp-access-setup.png)

8.  No ecrã **Porquê inscrever o seu dispositivo?**, leia sobre o que pode fazer quando inscrever o seu dispositivo e, em seguida, toque em **CONTINUAR**

    ![Ecrã Porquê inscrever o seu dispositivo](./media/and-enroll-4b-why-enroll.png)

9.  Reveja uma lista do que o administrador de TI pode e não pode ver no seu dispositivo e toque em **CONTINUAR**

    ![Definições de privacidade](./media/and-enroll-4c-we-care-privacy.png)

10.  No ecrã **O que vem a seguir**, leia sobre o que acontece durante a inscrição e, em seguida, toque em **INSCREVER**

    ![Ecrã O que vem a seguir](./media/and-enroll-4d-what-comes-next.png)

11.  No ecrã **Ativar administrador de dispositivo**, toque em **Ativar**

    ![Ecrã Ativar administrador de dispositivo](./media/and-enroll-5-activate.png)

12.  Siga as indicações para introduzir um PIN ou palavra-passe. Se já configurou um PIN ou uma palavra-passe neste dispositivo, não verá este ecrã nem terá de introduzir um novo PIN ou palavra-passe.

    ![Introduzir PIN ou palavra-passe](./media/and-enroll-6-PIN-native.png)

13.  Siga as instruções abaixo que correspondem ao tipo de dispositivo que está a utilizar (Android nativo ou Samsung Knox). Para determinar se tem um dispositivo Samsung Knox, aceda a **Definições** &gt; **Sobre telefone**. Se não vir a palavra "Knox" aí listada, tem um dispositivo Android nativo.

    -   Dispositivo nativo (não Samsung Knox): no ecrã **Nomear o certificado**, toque em **OK** para aceitar o certificado predefinido.

    ![Ecrã Nomear o certificado](./media/and-enroll-7-cert-native.png)

    -   Dispositivo Samsung Knox: aceite a política de privacidade e toque em **CONFIRMAR**

    ![Política de privacidade do Samsung KNOX](./media/and-enroll-7-knox-privacy-policy.png)

    Verá a seguinte mensagem no ecrã quando o Intune inscrever o seu dispositivo.

    ![Ecrã Inscrever dispositivo](./media/and-enroll-8-device-enrolling.png)

14. Quando o ecrã **Configuração de Acesso à Empresa** aparece, toque em **CONTINUAR**. Se vir uma mensagem que indique que o seu dispositivo não está em conformidade, siga as instruções para corrigir o problema e, em seguida, toque em **CONTINUAR**

    ![Ecrã Configuração de acesso à empresa](./media/and-enroll-9-comp-access-setup.png)  

11. No ecrã **Configuração de Acesso à Empresa concluída**, toque em **CONCLUÍDO**. O dispositivo está agora inscrito.

    ![Ecrã Configuração de acesso à empresa concluída](./media/and-enroll-10-comp-access-setup-complete.png)

Antes de tentar instalar aplicações da empresa, aceda a **Definições** &gt; **Segurança** e ative os **Recursos desconhecidos**. Se não ativar esta opção antes de tentar instalar aplicações, verá a mensagem "Instalação bloqueada." Por motivos de segurança, o telemóvel está definido para bloquear as instalações de aplicações obtidas a partir de origens desconhecidas." Pode tocar em **Definições** no diálogo de erro, para ir para a opção **Origens desconhecidas**.


### Consulte também
[Utilizar o dispositivo Android com o Intune](using-your-android-device-with-intune.md)


<!--HONumber=May16_HO2-->

