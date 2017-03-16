---
title: "Como repor o código de acesso a partir do site do Portal da Empresa | Documentos da Microsoft"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: 
ms.reviewer: mamoriss
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: f293901d3865f0b10ed876e83b151cf59a046cba
ms.openlocfilehash: 68725bb63ae2750e89a03c16027f8b4fd9111255
ms.lasthandoff: 02/24/2017


---

# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>Como repor o código de acesso do dispositivo a partir do site do Portal da Empresa

Se perder o PIN ou a palavra-passe de um dispositivo que tenha inscrito no Intune, pode utilizar o [site do Portal da Empresa](http://portal.manage.microsoft.com) para efetuar a reposição. Pode utilizar o site do Portal da Empresa para gerir computadores e dispositivos que tenha inscrito no Intune e para realizar a maioria das tarefas que pode fazer com a aplicação Portal da Empresa.

> [!NOTE]
> É possível que não veja o botão **Repor Código de Acesso** no site do Portal da Empresa. Se não o vir, terá de contactar o seu administrador de TI para obter suporte através do site do Portal da Empresa.

Para repor o código de acesso:

1.    No [site do Portal da Empresa](http://portal.manage.microsoft.com), toque no botão __menu__ ![Uma pequena imagem do botão menu, três barras horizontais paralelas empilhadas.](/Intune/whats-new/media/CP_hamburger_menu.png) e, em seguida, selecione __Os Meus Dispositivos__.

2. Na página __Os Meus Dispositivos__, selecione o nome do dispositivo cujo código de acesso quer repor.

  ![Captura de ecrã a mostrar a página Os Meus Dispositivos, com alguns dispositivos não identificados, acima da faixa de aviso para inscrever dispositivos não listados ou identificar os dispositivos não identificados.](./media/macOS_enroll_002_tap_here_banner.png)

3.    O dispositivo será aberto numa janela de pop-up. Selecione o botão **Repor Código de Acesso**.

    ![Todas as opções para um dispositivo selecionado no site do Portal da Empresa, incluindo Mudar o Nome, Remover, Repor Dispositivo, Repor Código de Acesso e Bloqueio Remoto. ](./media/iwp-screen-with-all-options.png)

4.  Será apresentada uma faixa a pedir-lhe para confirmar que pretende repor o código de acesso e que a sua sessão irá terminar no dispositivo depois de esta ação ser efetuada. Em seguida, terá de aguardar 5 minutos antes de iniciar sessão novamente.

  ![A faixa de reposição do código de acesso com o aviso sobre a reposição do código de acesso do dispositivo e como a sessão do utilizador irá terminar. Os botões de intervenção do utilizador são Terminar Sessão e Cancelar.](./media/iwp-reset-passcode-popup.png)

4.  Selecione **Terminar sessão** e receberá uma mensagem no final a informar sobre a remoção do código de acesso do dispositivo. Se não tiver o dispositivo consigo, não remova o código de acesso, pois quem tiver acesso físico ao dispositivo poderá aceder à maioria das informações pessoais ou empresariais no mesmo.

  ![A segunda faixa de reposição do código de acesso com o aviso sobre a reposição do código de acesso do dispositivo e como o código de acesso será removido do dispositivo. Também informa sobre como definir um novo código de acesso ao aceder às definições do dispositivo.](./media/iwp-reset-passcode-2nd-popup.png)


Como os dispositivos têm diferentes tipos de código de acesso, pode descobrir como a reposição do código de acesso poderá afetar o seu dispositivo específico na tabela abaixo. 

    |Tipo de Dispositivo|O Que Acontece Quando Repõe|
    |------------|-----------|
    |Android|Remove o código de acesso existente e cria um código de acesso alfanumérico temporário|
    |iOS|Remove o código de acesso existente e não cria um código de acesso temporário. Se estiver a utiliza a deteção de impressão digital do Touch ID para abrir o dispositivo ou efetuar compras, terá de voltar a configurá-la.|
    |Windows 10 Mobile|Remove o código de acesso existente e cria um código de acesso alfanumérico temporário. Se estiver a utilizar o reconhecimento de rosto do Windows Hello para iniciar sessão, este continuará a ser suportado.|
    |Windows Phone 8.1|Remove o código de acesso existente e cria um código de acesso numérico temporário.|

    5.  Desbloqueie o dispositivo e defina um novo código de acesso ou altere o código de acesso temporário ao aceder a **Definições** no seu dispositivo.

    Para ver uma notificação a confirmar que a palavra-passe foi reposta com êxito, clique no sinalizador de notificação na parte superior direita do site do Portal da Empresa.

Ainda precisa de ajuda? Contacte o administrador de TI. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](http://portal.manage.microsoft.com).
