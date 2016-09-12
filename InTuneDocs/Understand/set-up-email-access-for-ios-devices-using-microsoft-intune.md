---
title: Configurar o acesso ao e-mail para dispositivos iOS | Microsoft Intune
description: configurar o acesso ao e-mail para dispositivos iOS com o Microsoft Intune
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3853673d-290a-400f-8e45-d55e39d42acd
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 60ee39a7eeeb9068a7350ec87f60e7148ccb7826
ms.openlocfilehash: f132266939b70e87ce7fb36e42ef8b8c0777d55d


---

# Configurar o acesso ao e-mail para dispositivos iOS com o Microsoft Intune
Quando os dispositivos são inscritos no Intune, pode configurar os dispositivos para que os utilizadores possam aceder ao e-mail da empresa. Uma forma de o fazer para tipos de dispositivos específicos é criar e implementar um **perfil de e-mail**. Os perfis de e-mail são um tipo de política do Intune que configura e liga o dispositivo de um utilizador ao serviço de e-mail da empresa.
A utilização de um perfil de e-mail torna o acesso ao e-mail automático para os dispositivos inscritos, o que evita que tenha de configurar manualmente o dispositivo. Um perfil de e-mail também garante que todos os utilizadores finais estão a configurar o acesso da mesma forma e com as mesmas definições básicas.

## Objetivos destas instruções

- Criar e implementar um perfil de e-mail para dispositivos iOS
- Verificar se a política de perfil de e-mail foi aplicada com êxito

## O que precisa antes de iniciar estas instruções

- Um Exchange Server, no local ou alojado no Azure como parte da sua subscrição do Office/E3.
- O nome de anfitrião do Exchange Server da sua empresa. Este é o nome de domínio totalmente qualificado (FQDN), por exemplo, **contosodemo55.onmicrosoft.com**.
- Um grupo de utilizadores no qual implementar o perfil de e-mail. Se concluiu as instruções do artigo [Iniciar uma versão de avaliação do Microsoft Intune e implementar a política de PIN para iOS](start-a-microsoft-intune-trial-and-deploy-ios-pin-policy.md), pode utilizar o grupo de utilizadores **GroupDemo** que criou para o mesmo.
- Os dispositivos iOS inscritos nos quais implementar o perfil. Mais uma vez, se concluiu as instruções do artigo [Iniciar uma versão de avaliação do Microsoft Intune e implementar a política de PIN para iOS](start-a-microsoft-intune-trial-and-deploy-ios-pin-policy.md), já inscreveu alguns dispositivos iOS.

## Passos para criar e implementar um perfil de e-mail para dispositivos iOS

Para estas instruções, vamos utilizar o Exchange Server alojado fornecido com uma subscrição de avaliação.
1. Na consola do Intune, clique em **Política** e, em seguida, clique em **Adicionar Política**.
![<add-policy>](./media/Email-Walkthrough/Email-Walkthrough-1.png)
2. Na caixa de diálogo **Criar uma nova política**, expanda **iOS**, selecione **Perfil de E-Mail** e, em seguida, clique em **Criar Política**.  
![<ios-email-profile-policy>](./media/Email-Walkthrough/Email-Walkthrough-2.png)
3. Na página de criação da política, introduza um nome para a política, como, por exemplo, **Perfil de e-mail iOS - palavra-passe do utilizador**, e uma descrição. Pode ter vários perfis de e-mail para diferentes tipos de dispositivos e diferentes métodos de autenticação, pelo que pode utilizar o nome para mostrar para que serve o perfil.
4. Introduza o nome de anfitrião do Exchange. Uma vez que está a utilizar o Exchange Server alojado no Azure, para nome de anfitrião, introduzimos simplesmente: **outlook.office365.com**
![<add-exchange-host-name>](./media/Email-Walkthrough/Email-Walkthrough-3.png)
5. Introduza o nome de conta que será apresentado aos utilizadores do dispositivo para ajudá-los a identificar o serviço de e-mail. Por exemplo, **E-Mail de Contoso**.
6. Uma vez que estamos a utilizar um nome de utilizador e uma palavra-passe para autenticar o utilizador no serviço do Exchange, deixe as definições de nome de utilizador e palavra-passe tal como estão.
7. Ajuste as definições de sincronização para satisfazer as suas necessidades. Por agora, utilize as predefinições, a menos que exista uma definição específica que queira alterar.  
8. Clique em **Guardar Política**.
9. É apresentada uma caixa de diálogo a perguntar se pretende implementar a política agora. Clique em **Sim**.
![<deploy-policy-now-dialog>](./media/Email-Walkthrough/Email-Walkthrough-4.png)
10. Na janela apresentada a seguir, selecione o grupo de utilizadores no qual pretende implementar o perfil de e-mail, clique em **Adicionar** e, em seguida, clique em **OK**.  
![<finish-add-policy>](./media/Email-Walkthrough/Email-Walkthrough-5.png)  
Depois de clicar em **OK**, a política irá começar a ser aplicada aos dispositivos inscritos num minuto ou dois.

## Passos para verificar se o perfil foi aplicado com êxito

Para verificar se o perfil foi aplicado, precisará de acesso a um dos dispositivos no qual implementou o perfil de e-mail.
1. No dispositivo iOS, abra a aplicação Correio.
A aplicação irá pedir que introduza o nome de utilizador e a palavra-passe de e-mail do utilizador.  
![<verify-policy-add-password>](./media/Email-Walkthrough/Email-Walkthrough-6.png)
2. Introduza o nome de utilizador e a palavra-passe da conta de e-mail do Exchange do utilizador e, em seguida, toque em **OK**.
 A aplicação Correio abre na conta do Exchange e o e-mail começa a ser sincronizado com o dispositivo.
![<exchange-account-opens>](./media/Email-Walkthrough/Email-Walkthrough-7.png)
3. Verifique as definições de conta da aplicação Correio para se certificar de que o nome da conta é o mesmo que introduziu no perfil de e-mail (por exemplo, **E-mail de Contoso**) e se as definições de sincronização estão definidas corretamente.
![<check-account-settings>](./media/Email-Walkthrough/Email-Walkthrough-8.png)
![<check-email-account-name>](./media/Email-Walkthrough/Email-Walkthrough-9.png)  
  Se parecer que o perfil de e-mail não foi automaticamente aplicado ao dispositivo, pode aplicar manualmente a política utilizando a aplicação Portal da Empresa no dispositivo.
1. Abra a aplicação Portal da Empresa.
2. Toque em **Os Meus Dispositivos**.
3. Toque no nome do seu dispositivo.
![<tap-device-name](./media/Email-Walkthrough/Email-Walkthrough-10.png)
4. Toque em **Sincronizar** > **Verificar Conformidade**.
![<tap-sync-check-device>](./media/Email-Walkthrough/Email-Walkthrough-11.png) Após alguns instantes, o perfil de e-mail é aplicado ao dispositivo. Depois disso, pode seguir os passos de verificação para se certificar de que o perfil foi aplicado corretamente.

## Consulte Também
[Guia de avaliação do Intune](get-started-with-a-30-day-trial-of-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


