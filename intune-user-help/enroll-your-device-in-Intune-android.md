---
title: Inscrever o seu dispositivo Android no Intune | Documentos da Microsoft
description: Descreve como encriptar dispositivos Android no Intune
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 9e70ef08eabb1595804f84247fc1663c5c6f985e
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---


# <a name="enroll-your-android-device-in-intune"></a>Inscrever o seu dispositivo Android no Intune

Se a sua empresa ou escola utiliza o Microsoft Intune, pode inscrever o seu dispositivo Android para aceder a e-mails, ficheiros e outros recursos da empresa. Quando inscreve os seus dispositivos, o seu departamento de TI pode gerir esses recursos de trabalho ou da escola, mantê-los seguros e dar-lhe a liberdade para utilizar o seu dispositivo preferencial para realizar o seu trabalho. Para mais informações sobre a inscrição, consulte [O que acontece quando instalo a aplicação Portal da Empresa e inscrevo o meu dispositivo?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-android.md)

<iframe src="https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

Estas instruções de inscrição destinam-se a dispositivos nativos e a dispositivos Samsung KNOX Android. Samsung KNOX é um tipo de segurança utilizado por determinados dispositivos Samsung para proporcionar proteção adicional fora de o que proporciona o Android nativo. Para verificar se tem um dispositivo Samsung KNOX, aceda a **Definições** > **Acerca do dispositivo**. Se não vir a "versão KNOX" aí listada, tem um dispositivo Android nativo.

Antes ou depois da inscrição, poderá ser-lhe pedido para escolher uma categoria que melhor descreve como utiliza o seu dispositivo. O seu administrador de TI utiliza esta categoria para ajudar a verificar as aplicações a que tem acesso.

Se obtiver um erro enquanto tenta inscrever o dispositivo no Intune, pode [enviar erros de inscrição ao administrador de TI](send-enrollment-errors-to-your-it-admin-android.md).

**Para inscrever o seu dispositivo Android:**

1.  Instale a aplicação gratuita Portal da Empresa do Intune a partir do [Google Play](http://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal).

2.  Abra a aplicação Portal da Empresa do Microsoft Intune.

3.  No ecrã **Bem-vindo** do Portal da Empresa, toque em **Iniciar sessão** e, em seguida, inicie sessão com a sua conta escolar ou profissional.

    ![O ecrã de boas-vindas da aplicação Portal da Empresa para Android, que pede ao utilizador para iniciar sessão com a sua conta escolar ou profissional necessária. Tenha em atenção que as contas Microsoft e outras contas pessoais não são aceites.](./media/and-enroll-0-welcome-screen.png)   

4.  Se o seu administrador de TI configurar termos e condições empresariais, toque em **ACEITAR** para aceitar os termos. Este ecrã poderá ser ligeiramente diferente da imagem abaixo, com base na versão do Android que está a utilizar atualmente.

    ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5.  Inicie sessão na aplicação Portal da Empresa com a sua conta e palavra-passe profissional ou escolar e, em seguida, toque em **Iniciar sessão**.

    ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6.  No ecrã **Configuração de Acesso à Empresa**, toque em **COMEÇAR**.

    ![Ecrã Configuração de acesso à empresa](./media/and-enroll-4a-comp-access-setup.png)

    > [!NOTE]
    > Os triângulos amarelos não significam que já tem um erro. Esses ícones indicam que ainda existem passos a concluir no processo de inscrição.

7. No ecrã **Porquê inscrever o seu dispositivo?**, leia sobre o que pode fazer quando inscrever o seu dispositivo e, em seguida, toque em **CONTINUAR**.

    ![Ecrã Porquê inscrever o seu dispositivo](./media/and-enroll-4b-why-enroll.png)

8.  Reveja uma lista do que o administrador de TI pode e não pode ver no seu dispositivo e, em seguida, toque em **CONTINUAR**.

    ![Definições de privacidade](./media/and-enroll-4c-we-care-privacy.png)

9.  No ecrã **O que vem a seguir**, leia sobre o que acontece durante a inscrição e, em seguida, toque em **INSCREVER**.

    ![Ecrã O que vem a seguir](./media/and-enroll-4d-what-comes-next.png)

10.  Se estiver a utilizar o Android 6.0 ou posterior, efetue este passo. Caso contrário, avance para o passo seguinte.

    Se o administrador de TI tiver configurado determinadas políticas, poderá ver as seguintes mensagens:
    -    **Permitir que o Portal da Empresa efetue e faça a gestão de chamadas telefónicas?**

        ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

    Se vir esta mensagem, toque em **PERMITIR**. É seguro tocar em PERMITIR, porque a **Microsoft nunca efetua ou gere as suas chamadas telefónicas.** A Google controla o texto da mensagem e a Microsoft não a pode alterar. Quando permite o acesso, está a permitir que o seu dispositivo envie o número de identidade internacional do equipamento móvel (IMEI) do seu dispositivo ao Intune. O número IMEI é como um número de série que identifica exclusivamente um dispositivo móvel.

    Se negar o acesso, a mensagem aparecerá quando iniciar sessão novamente no Portal da Empresa, mas pode desativar futuras mensagens ao tocar na caixa **Não voltar a perguntar**. Se, posteriormente, decidir permitir o acesso, aceda a **Definições** &gt; **Aplicações** &gt; **Portal da Empresa** &gt; **Permissões** &gt; **Telemóvel** e ative a permissão.

    -    **Permitir que o Portal da Empresa aceda aos seus contactos?**

        ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

        Se vir esta mensagem, toque em **PERMITIR**. É seguro tocar em PERMITIR, porque a **Microsoft nunca acede aos seus contactos.** A Google controla o texto da mensagem e a Microsoft não a pode alterar. Ao permitir o acesso, só permite à aplicação Portal da Empresa criar, utilizar e gerir a sua conta profissional.

        Se negar o acesso, a mensagem aparecerá quando iniciar sessão novamente no Portal da Empresa, mas pode desativar futuras mensagens ao tocar na caixa **Não voltar a perguntar**. Se, posteriormente, decidir permitir o acesso, aceda a **Definições** &gt; **Aplicações** &gt; **Portal da Empresa** &gt; **Permissões** &gt; **Telemóvel** e ative a permissão.

11.  No ecrã **Ativar administrador de dispositivo**, toque em **Ativar**.

    ![Ecrã Ativar administrador de dispositivo](./media/and-enroll-5-activate.png)

    A função de administrador de dispositivos é uma função que o Portal da Empresa precisa para gerir o seu dispositivo. Permite ao administrador ver algumas coisas como, por exemplo, quantas vezes tentou desbloquear o ecrã e tomar algumas ações.

    O fundamental a recordar é que estas ações são executadas em nome da segurança. O administrador de TI não está a tentar violar a sua privacidade ou a apagar as suas informações sem motivo, mas quer confirmar se os dados da empresa estão seguros.

    A Microsoft não controla esta mensagem e compreendemos que a respetiva formulação pode parecer um pouco drástica. Não há uma forma para o Portal da Empresa apresentar apenas as restrições e o acesso que são relevantes para a sua organização. Todos eles são concedidos em simultâneo neste ecrã. Contacte o seu administrador de TI para obter mais informações, através das informações de contacto no [site do Portal da Empresa](http://portal.manage.microsoft.com), se tiver questões específicas para a utilização da sua organização individual.

12.  Siga as indicações para introduzir um PIN ou palavra-passe. Se já configurou um PIN ou uma palavra-passe neste dispositivo, não verá este ecrã nem terá de introduzir um novo PIN ou palavra-passe.

    ![Introduzir PIN ou palavra-passe](./media/and-enroll-6-PIN-native.png)

13.  Se estiver a utilizar um dispositivo Samsung KNOX, toque em **Confirmar** e verá uma mensagem a indicar que o dispositivo está a ser inscrito. Se estiver a utilizar um dispositivo Android nativo, repare apenas no ecrã seguinte que mostra que o dispositivo está a ser inscrito.

    ![Política de privacidade do Samsung KNOX](./media/and-enroll-7-knox-privacy-policy.png)

    Este ecrã mostra que o dispositivo está a ser inscrito.

    ![Ecrã Inscrever dispositivo](./media/and-enroll-8-device-enrolling.png)

14. Quando o ecrã **Configuração de Acesso à Empresa** aparece, toque em **CONTINUAR**. Se uma mensagem indicar que o seu dispositivo não está em conformidade, siga as instruções para corrigir o problema e, em seguida, toque em **CONTINUAR**.

    ![O dispositivo não está conforme, mas está inscrito](./media/and-enroll-9a-noncompliant-enrolled-device.png)

    ![Aparecem problemas de conformidade do dispositivo que precisam de resolução](./media/and-enroll-9b-resolve-compliance-issues.png)

    Pode encontrar mais informações sobre os problemas ao tocar nos mesmos.

    ![Problemas de conformidade do dispositivo expandidos](./media/and-enroll-9c-resolve-compliance-issues-expanded.png)

    ![Ecrã Configuração de acesso à empresa](./media/and-enroll-9d-comp-access-setup.png)  

15. No ecrã **Configuração de Acesso à Empresa concluída**, toque em **CONCLUÍDO**. O dispositivo está agora inscrito.

    ![Ecrã Configuração de acesso à empresa concluída](./media/and-enroll-10-comp-access-setup-complete.png)

Antes de tentar instalar aplicações da empresa, aceda a **Definições** &gt; **Segurança** e ative as **Origens desconhecidas**. Se não ativar esta opção antes de tentar instalar aplicações, verá a seguinte mensagem: "Instalação bloqueada. Por motivos de segurança, o dispositivo está definido para bloquear as instalações de aplicações obtidas a partir de origens desconhecidas." Pode tocar em **Definições**, na caixa de diálogo de erro, para ir para a opção **Origens desconhecidas**.

> [!Note]
> Se a sua organização utilizar software de gestão de despesas de telecomunicações, terá de completar alguns passos adicionais antes de o dispositivo ficar totalmente inscrito. Saiba mais [aqui](enroll-your-device-with-telecom-expense-management-android.md).

Ainda precisa de ajuda? Contacte o administrador de TI (verifique as informações de contacto no [site do Portal da Empresa](http://portal.manage.microsoft.com)) ou escreva para a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">equipa Android da Microsoft</a>.

