---
title: Registrar dispositivo Android com o Portal da Empresa do Intune | Microsoft Docs
description: Descreve como registrar um dispositivo Android com o Portal da Empresa do Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1670ddf9299d12312f09d188e4410d14ac40fbe7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506327"
---
# <a name="enroll-your-device-with-company-portal"></a>Registrar seu dispositivo com o Portal da Empresa  
Registre seu dispositivo Android pessoal ou de propriedade corporativa para obter acesso seguro a email, aplicativos e dados da empresa. O Portal da Empresa dá suporte a dispositivos Android, incluindo Samsung Knox, executando o Android 4,4 e posterior.  
</br>
> [!VIDEO https://www.youtube.com/embed/k0Q_sGLSx6o?rel=0]

> [!NOTE]
> O Samsung Knox é um tipo de segurança que determinados dispositivos Samsung usam para proteção adicional, fora do que o Android nativo fornece. Para verificar se você tem um dispositivo Samsung Knox, > vá para **configurações** > **sobre o dispositivo**. Se você não vir a **versão do Knox** listada, você terá um dispositivo Android nativo.

## <a name="enroll-device"></a>Registrar dispositivo  
Certifique-se de [instalar o aplicativo gratuito portal da empresa do Intune do Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). 

Durante o registro, você pode ser solicitado a escolher uma categoria que melhor descreva como você usa seu dispositivo. O suporte de sua empresa usa sua resposta para verificar os aplicativos aos quais você tem acesso.  

1. Abra a aplicação Portal da Empresa.  

3. No ecrã **Bem-vindo** do Portal da Empresa, toque em **Iniciar sessão** e, em seguida, inicie sessão com a sua conta escolar ou profissional.

   ![O ecrã de boas-vindas da aplicação Portal da Empresa para Android, que pede ao utilizador para iniciar sessão com a sua conta escolar ou profissional necessária. Tenha em atenção que as contas Microsoft e outras contas pessoais não são aceites.](./media/and-enroll-0-welcome-screen.png)   

4. Se for solicitado que você aceite os termos e condições da sua organização, toque em **aceitar**. Essa tela pode ser um pouco diferente do exemplo de captura abaixo. 

   ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5. Inicie sessão na aplicação Portal da Empresa com a sua conta e palavra-passe profissional ou escolar e, em seguida, toque em **Iniciar sessão**.

   ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6. No ecrã **Configuração de Acesso da Empresa**, toque em **CONTINUAR**.

   ![Ecrã Configuração de acesso à empresa](/intune/media/android_cp_enroll_01_1709_new.png)

   > [!NOTE]
   > Os triângulos amarelos não significam que já tem um erro. Esses ícones indicam que ainda existem passos a concluir no processo de inscrição.

7. Consulte uma lista do que o suporte da empresa pode e não pode ver no seu dispositivo e, em seguida, toque em **CONTINUAR**.

   ![Definições de privacidade](/intune/media/android_cp_enroll_02_after_1710.png)

8. No ecrã **O que se segue?** , leia sobre o que acontece durante a inscrição e, em seguida, toque em **INSCREVER**.

   ![Ecrã O que vem a seguir](/intune/media/android_cp_enroll_03_after_1710.png)

9. Se estiver a utilizar o Android 6.0 ou posterior, efetue este passo. Caso contrário, avance para o passo seguinte.

   Se o suporte da empresa tiver configurado determinadas políticas, poderá ver as seguintes mensagens:
   - **Permitir que o Portal da Empresa efetue e faça a gestão de chamadas telefónicas?**

     ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

   Se vir esta mensagem, toque em **PERMITIR**. É seguro tocar em PERMITIR, porque a **Microsoft nunca efetua ou gere as suas chamadas telefónicas.** A Google controla o texto da mensagem e a Microsoft não a pode alterar. Quando permite o acesso, está a permitir que o seu dispositivo envie o número de identidade internacional do equipamento móvel (IMEI) do seu dispositivo ao Intune. O número IMEI é como um número de série que identifica exclusivamente um dispositivo móvel.

   Se você negar o acesso, a mensagem será exibida novamente na próxima vez que você entrar no Portal da Empresa. Para desativar as mensagens futuras, selecione **nunca perguntar novamente**. Para reverter a permissão de acesso, vá para **configurações** > **aplicativos** > **Portal da Empresa** > **permissões** > **telefone**e, em seguida, ative a permissão.  

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

## <a name="next-steps"></a>Próximos passos  

Antes de tentar instalar os aplicativos da empresa, vá para configurações  > **segurança**e ative **as** **fontes desconhecidas**. Se não ativar esta opção antes de tentar instalar aplicações, verá a seguinte mensagem: "Instalação bloqueada. Por motivos de segurança, o dispositivo está definido para bloquear as instalações de aplicações obtidas a partir de origens desconhecidas." Pode tocar em **Definições**, na caixa de diálogo de erro, para ir para a opção **Origens desconhecidas**.  

> [!Note]
> Se a sua organização utilizar software de gestão de despesas de telecomunicações, terá de completar alguns passos adicionais antes de o dispositivo ficar totalmente inscrito. Saiba mais [aqui](enroll-your-device-with-telecom-expense-management-android.md).

Se você receber um erro ao tentar registrar seu dispositivo no Intune, poderá [enviar por email o suporte de sua empresa](send-logs-to-your-it-admin-by-email-android.md).  

Ainda precisa de ajuda? Contacte o suporte da empresa (verifique as informações de contacto no [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980)) ou escreva para a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">equipa Android da Microsoft</a>.
