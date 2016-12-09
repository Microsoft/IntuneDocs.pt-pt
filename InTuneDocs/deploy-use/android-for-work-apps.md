---
title: "Implementar aplicações em dispositivos Android for Work | Microsoft Intune"
description: "Utilize este tópico para sincronizar e, em seguida, implementar aplicações em dispositivos Android for Work a partir da Google Play for Work Store."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/6/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd0bbd90-d3fe-4efc-83fd-d1f3f86800d4
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 35ee89248e42c67f48d4607f5d415896e35b90e9


---

# <a name="how-to-deploy-apps-to-android-for-work-devices-with-intune"></a>Como implementar aplicações em dispositivos Android for Work com o Intune

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

As aplicações em dispositivos Android for Work são implementadas de forma diferente da implementação em dispositivos Android padrão. Todas as aplicações que instala para o Android for Work provêm da Google Play for Work Store. Deve iniciar sessão na loja, procurar as aplicações pretendidas e aprová-las.
Em seguida, a aplicação aparece no nó **Aplicações Compradas em Volume** da consola do Intune. A partir daqui, pode gerir a implementação da aplicação da mesma forma que implementaria qualquer outra aplicação.
Além disso, se tiver criado a as suas próprias aplicações de linha de negócio (LOB), pode implementá-las. Para o fazer, tem de se inscrever numa conta Google Developer que lhe permita publicar aplicações numa área privada na Google Play Store e, em seguida, sincronizá-las com o Intune.

## <a name="before-you-start"></a>Antes de começar

1. Certifique-se de que configurou o Intune e o Android for Work para trabalharem em conjunto no separador **Administrador** da consola do Intune.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Sincronizar uma aplicação a partir da Google Play for Work Store


1. Aceda à [Google Play for Work Store.](https://play.google.com/work). Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work.
2. Procure na loja a aplicação que pretende implementar através do Intune.
3. Na página da aplicação que escolheu, selecione **Aprovar**. Neste exemplo, escolheu a aplicação Microsoft Excel.<br>
  ![Exemplo de aprovação de aplicação](/intune/deploy-use/media/approve.png)
4. É aberta uma janela da aplicação a pedir-lhe para dar permissões para a aplicação efetuar diversas operações. Tem de selecionar **Aprovar** para continuar.<br>
  ![Exemplo de permissões de aprovação de aplicações](/intune/deploy-use/media/approve-app-permissions.png)
5. Após alguns momentos, verá uma mensagem a confirmar que a aplicação foi aprovada e está disponível na consola de administração de TI.

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>Publicar e sincronizar uma aplicação de linha de negócio a partir da Google Play for Work Store

1. Aceda ao Google Play Developer Console, [play.google.com/apps/publish](https://play.google.com/apps/publish).
2. Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work. Se estiver a iniciar sessão pela primeira vez, tem de se registar e pagar uma taxa para se tornar um membro do programa Google Developer.
3. Na consola, selecione **Adicionar nova aplicação**.
4. Deve carregar e fornecer informações sobre a sua aplicação da mesma forma que publica qualquer aplicação na Google Play Store. No entanto, tem de selecionar a definição **Apenas disponibilizar esta aplicação para a minha organização (<*nome da organização*>)** conforme apresentado abaixo.<br>
  ![Opção para apenas disponibilizar a aplicação para a sua organização](/intune/deploy-use/media/restrict.png)<br>
Esta ação garante que a aplicação só está disponível para a sua organização e não está disponível na Google Play Store pública.
Para mais informações sobre como carregar e publicar aplicações Android, consulte a [Ajuda do Google Developer Console](https://support.google.com/googleplay/android-developer/answer/113469).
5. Assim que publicar a sua aplicação, aceda à [Google Play for Work Store](https://play.google.com/work). Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work.
6. No nó **Aplicações** da loja, verifique se consegue ver a aplicação que publicou. Tenha em atenção que foi aprovada automaticamente para ser sincronizada com o Intune.

## <a name="deploy-an-android-for-work-app"></a>Implementar uma aplicação do Android for Work

Normalmente, o Intune irá sincronizar duas vezes por dia com a Google Play for Work Store. Se tiver aprovado uma aplicação a partir da loja e ainda não a vir no nó **Aplicações Compradas em Volume** da área de trabalho **Aplicações**, pode forçar uma sincronização imediata da seguinte forma:

1. Na [Consola de administração do Intune](https://manage.microsoft.com), selecione **Admin** > **Mobile Device Management** > **Android for Work**.
2. Na página **Configuração de Gestão de Dispositivos Móveis Android for Work**, selecione **Sincronizar Agora**.
3. A página também apresenta a hora e o estado da última sincronização.

Quando a aplicação é apresentada no nó **Aplicações Compradas em Volume** da área de trabalho **Aplicações**, pode [implementá-la tal como implementaria outra aplicação](deploy-apps-in-microsoft-intune.md). Só pode implementar a aplicação em grupos de utilizadores. Atualmente, só pode selecionar as ações **Necessário** e **Desinstalar**. A partir de outubro de 2016, iremos começar a adicionar a ação de implementação **Disponível** aos novos inquilinos.

Após implementar a aplicação, esta será instalada nos dispositivos direcionados. Não será pedida aprovação ao utilizador do dispositivo.



<!--HONumber=Dec16_HO2-->


