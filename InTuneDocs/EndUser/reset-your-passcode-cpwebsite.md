---
title: "Repor o código de acesso do dispositivo a partir do site do Portal da Empresa | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
ms.author: stabar
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2aea845bc00c153f070e04abb67582a5d5a726ca
ms.openlocfilehash: 47b36616f7a8ee23d4d47b41a1db2c41c185c6f5


---


# Repor o código de acesso do dispositivo a partir do site do Portal da Empresa

Se perder o PIN ou a palavra-passe de um dispositivo que tenha inscrito no Intune, pode utilizar o [site do Portal da Empresa](http://portal.manage.microsoft.com) para efetuar a reposição. Pode utilizar o site do Portal da Empresa para gerir computadores e dispositivos que tenha inscrito no Intune e para realizar a maioria das tarefas que pode fazer com a aplicação Portal da Empresa.

> [!NOTE]
> Poderá não ver o botão **Repor Código de Acesso** no site do Portal da Empresa, dependendo de como o administrador de TI configurou o Intune. A reposição do código de acesso não é suportada em dispositivos Windows 8.1.

Para repor o código de acesso:

1.  Abra o [site do Portal da Empresa](http://portal.manage.microsoft.com) e selecione o dispositivo cujo código de acesso pretende repor.

2.  Selecione **Repor Código de Acesso**.

    ![Informações do dispositivo com o botão Repor Código de Acesso](./media/iwp-screen-with-all-options.png)

3.  Selecione **Terminar sessão** e, em seguida, volte a iniciar sessão com as credenciais da sua conta escolar ou profissional. Tem de voltar a iniciar sessão dentro de cinco minutos.

    ![Mensagem de reposição com botão para terminar sessão](./media/iwp-2-sign-out.png)

4.  Selecione **Repor Código de Acesso**.

    ![Mensagem a explicar o que acontece quando repõe o código de acesso](./media/iwp-3-tap-reset-passcode-after-signin.png)

    Consulte a tabela para ver como funciona a opção **Repor Código de Acesso** no seu dispositivo.

    |Plataforma|Support|
    |------------|-----------|
    |Android|Cria um código de acesso alfanumérico temporário.|
    |iOS|Remove o código de acesso do dispositivo e não cria um código de acesso temporário. Se estiver a utilizar o Touch ID, terá de configurá-lo novamente no seu dispositivo, porque este é removido quando o código de acesso for reposto.|
    |Windows 10 (apenas para dispositivos móveis)|Cria um código de acesso alfanumérico temporário. O Windows Hello é suportado.|
    |Windows Phone 8.1|Cria um código de acesso numérico temporário.|
    Depois de desbloquear o dispositivo, pode definir um novo código de acesso ao aceder a **Definições** no seu dispositivo.

5.  Desbloqueie o dispositivo e, em seguida, defina um novo código de acesso ou altere o código de acesso temporário, acedendo a **Definições** no seu dispositivo.

    Para ver uma notificação a confirmar que a palavra-passe foi reposta com êxito, clique no sinalizador de notificação na parte superior direita do site do Portal da Empresa.

Ainda precisa de ajuda? Contacte o administrador de TI. Para encontrar as informações de contacto dele, verifique o [Web site do Portal da Empresa](http://portal.manage.microsoft.com).



<!--HONumber=Oct16_HO3-->


