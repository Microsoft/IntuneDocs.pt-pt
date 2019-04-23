---
title: Inscrever o dispositivo Android com o Portal da empresa do Intune | Documentos da Microsoft
description: Descreve como inscrever um dispositivo Android com o Portal da empresa do Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e9120110b1840d1f5075549737722328ef2551f
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61498384"
---
# <a name="enroll-your-device-with-company-portal"></a>Inscrever o seu dispositivo com o Portal da empresa  
Inscreva o seu dispositivo Android pessoal ou pertencentes à empresa para obter acesso seguro ao e-mail da empresa, aplicações e dados. Portal da empresa oferece suporte a dispositivos Android, incluindo o Samsung Knox, executar o Android 4.4 e posterior.  

> [!NOTE]
> Samsung Knox é um tipo de segurança utilizado por determinados dispositivos Samsung para proteção adicional fora o que proporciona o Android nativo. Para verificar se tem um dispositivo Samsung Knox, > aceda a **configurações** > **sobre o dispositivo**. Se não vir **versão Knox** aí listada, tem um dispositivo Android nativo.    

## <a name="enroll-device"></a>Inscrever o dispositivo  
Certifique-se de que [instalar a aplicação gratuita Portal de empresa do Intune a partir do Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). 

Durante a inscrição, poderá ser-lhe pedido para escolher uma categoria que melhor descreve como utilizar o seu dispositivo. O suporte da empresa utiliza a sua resposta para verificar as aplicações que têm acesso a.  

1. Abra a aplicação Portal da Empresa.  

3. No ecrã **Bem-vindo** do Portal da Empresa, toque em **Iniciar sessão** e, em seguida, inicie sessão com a sua conta escolar ou profissional.

   ![O ecrã de boas-vindas da aplicação Portal da Empresa para Android, que pede ao utilizador para iniciar sessão com a sua conta escolar ou profissional necessária. Tenha em atenção que as contas Microsoft e outras contas pessoais não são aceites.](./media/and-enroll-0-welcome-screen.png)   

4. Se lhe for pedido para aceitar os termos e condições da sua organização, toque em **ACCEPT**. Este ecrã poderá ser ligeiramente diferente do exemplo captura de ecrã abaixo. 

   ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5. Inicie sessão na aplicação Portal da Empresa com a sua conta e palavra-passe profissional ou escolar e, em seguida, toque em **Iniciar sessão**.

   ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6. No ecrã **Configuração de Acesso da Empresa**, toque em **CONTINUAR**.

   ![Ecrã Configuração de acesso à empresa](/intune/media/android_cp_enroll_01_1709_new.png)

   > [!NOTE]
   > Os triângulos amarelos não significam que já tem um erro. Esses ícones indicam que ainda existem passos a concluir no processo de inscrição.

7. Consulte uma lista do que o suporte da empresa pode e não pode ver no seu dispositivo e, em seguida, toque em **CONTINUAR**.

   ![Definições de privacidade](/intune/media/android_cp_enroll_02_after_1710.png)

8. No ecrã **O que se segue?**, leia sobre o que acontece durante a inscrição e, em seguida, toque em **INSCREVER**.

   ![Ecrã O que vem a seguir](/intune/media/android_cp_enroll_03_after_1710.png)

9. Se estiver a utilizar o Android 6.0 ou posterior, efetue este passo. Caso contrário, avance para o passo seguinte.

   Se o suporte da empresa tiver configurado determinadas políticas, poderá ver as seguintes mensagens:
   - **Permitir que o Portal da Empresa efetue e faça a gestão de chamadas telefónicas?**

     ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

   Se vir esta mensagem, toque em **PERMITIR**. É seguro tocar em PERMITIR, porque a **Microsoft nunca efetua ou gere as suas chamadas telefónicas.** A Google controla o texto da mensagem e a Microsoft não a pode alterar. Quando permite o acesso, está a permitir que o seu dispositivo envie o número de identidade internacional do equipamento móvel (IMEI) do seu dispositivo ao Intune. O número IMEI é como um número de série que identifica exclusivamente um dispositivo móvel.

   Se negar o acesso, a mensagem aparecerá novamente na próxima vez que iniciar sessão no Portal da empresa. Para desativar futuras mensagens, selecione **nunca voltar a perguntar**. Para reverter a permissão de acesso, aceda a **configurações** > **aplicações** > **Portal da empresa** > **permissões**   >  **Phone**e, em seguida, ative a permissão.  

   - **Permitir que o Portal da Empresa aceda aos seus contactos?**

     ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

     Se vir esta mensagem, toque em **PERMITIR**. É seguro tocar em PERMITIR, porque a **Microsoft nunca acede aos seus contactos.** A Google controla o texto da mensagem e a Microsoft não a pode alterar. Ao permitir o acesso, só permite à aplicação Portal da Empresa criar, utilizar e gerir a sua conta profissional.

     Se negar o acesso, a mensagem aparecerá quando iniciar sessão novamente no Portal da Empresa, mas pode desativar futuras mensagens ao tocar na caixa **Não voltar a perguntar**. Se, posteriormente, decidir permitir o acesso, aceda a **Definições** &gt; **Aplicações** &gt; **Portal da Empresa** &gt; **Permissões** &gt; **Telemóvel** e ative a permissão.

10. No ecrã **Ativar administrador de dispositivo**, toque em **Ativar**.

    ![Ecrã Ativar administrador de dispositivo](./media/and-enroll-5-activate.png)

    A função de administrador de dispositivos é uma função que o Portal da Empresa precisa para gerir o seu dispositivo. Permite ao administrador ver algumas coisas como, por exemplo, quantas vezes tentou desbloquear o ecrã e tomar algumas ações.    

    A Microsoft não controla esta mensagem e compreendemos que a respetiva formulação pode parecer um pouco drástica. Não há uma forma para o Portal da Empresa apresentar apenas as restrições e o acesso que são relevantes para a sua organização. Todos eles são concedidos em simultâneo neste ecrã. Contacte o suporte da empresa para obter mais informações, através das informações de contacto no [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980), se tiver questões específicas da utilização por parte da sua organização a título individual.  

11. Siga as indicações para introduzir um PIN ou palavra-passe. Se já configurou um PIN ou uma palavra-passe neste dispositivo, não verá este ecrã nem terá de introduzir um novo PIN ou palavra-passe.  

    ![Introduzir PIN ou palavra-passe](./media/and-enroll-6-PIN-native.png)

12. Se estiver a utilizar um dispositivo Samsung Knox, toque em **Confirmar** e verá uma mensagem a indicar que o dispositivo está a ser inscrito. Se estiver a utilizar um dispositivo Android nativo, repare apenas no ecrã seguinte que mostra que o dispositivo está a ser inscrito.

    ![Política de privacidade do Samsung Knox](./media/and-enroll-7-knox-privacy-policy.png)

    Este ecrã mostra que o dispositivo está a ser inscrito.

    ![Ecrã Inscrever dispositivo](./media/and-enroll-8-device-enrolling.png)

13. Quando o ecrã **Configuração de Acesso à Empresa** aparece, toque em **CONTINUAR**. Se uma mensagem indicar que o seu dispositivo não está em conformidade, siga as instruções para corrigir o problema e, em seguida, toque em **CONTINUAR**.

    ![O dispositivo não está conforme, mas está inscrito](/intune/media/android_cp_enroll_05_post_1709.png)

    ![Aparecem problemas de conformidade do dispositivo que precisam de resolução](/intune/media/android_cp_enroll_03_post_1709.png)

    Pode encontrar mais informações sobre os problemas ao tocar nos mesmos.

    ![Problemas de conformidade do dispositivo expandidos](/intune/media/android_cp_enroll_04_post_1709.png)

    ![Ecrã Configuração de acesso à empresa](./media/and-enroll-9d-comp-access-setup.png)  

14. No ecrã **Configuração de Acesso à Empresa concluída**, toque em **CONCLUÍDO**. O dispositivo está agora inscrito.

    ![Ecrã Configuração de acesso à empresa concluída](./media/and-enroll-10-comp-access-setup-complete.png)

## <a name="next-steps"></a>Passos Seguintes  

Antes de tentar instalar aplicações da empresa, aceda a **configurações** > **segurança**e ativar **origens desconhecidas**. Se não ativar esta opção antes de tentar instalar aplicações, verá a seguinte mensagem: "Instalação bloqueada. Por motivos de segurança, o dispositivo está definido para bloquear as instalações de aplicações obtidas a partir de origens desconhecidas." Pode tocar em **Definições**, na caixa de diálogo de erro, para ir para a opção **Origens desconhecidas**.  

> [!Note]
> Se a sua organização utilizar software de gestão de despesas de telecomunicações, terá de completar alguns passos adicionais antes de o dispositivo ficar totalmente inscrito. Saiba mais [aqui](enroll-your-device-with-telecom-expense-management-android.md).

Se obtiver um erro enquanto tenta inscrever o dispositivo no Intune, pode [o suporte da empresa de e-mail](send-logs-to-your-it-admin-by-email-android.md).  

Ainda precisa de ajuda? Contacte o suporte da empresa (verifique as informações de contacto no [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980)) ou escreva para a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">equipa Android da Microsoft</a>.
