---
title: Como repor o código de acesso a partir do site do Portal da Empresa | Documentos da Microsoft
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 690fb81350c0c264677c6c75b8942e9cdcd4e8f0
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71163367"
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>Como repor o código de acesso do dispositivo a partir do site do Portal da Empresa

Se perder o PIN ou a palavra-passe do seu dispositivo, pode utilizar o [site do Portal da Empresa](https://portal.manage.microsoft.com) para efetuar a reposição. 

A opção Redefinir senha pode não aparecer para um dispositivo registrado pela empresa. Nesse caso, entre em contato com o suporte de sua empresa para que ele seja redefinido para você.  

A redefinição de senha não está disponível para dispositivos que executam o Android 7,0 e posterior. Se você esquecer sua senha em um desses dispositivos, deverá redefini-la para as configurações de fábrica.  

## <a name="reset-your-passcode"></a>Repor o código de acesso

1. Abra o [site do Portal da Empresa](https://portal.manage.microsoft.com) e selecione o botão __Menu__ > __Dispositivos__.  

2. Selecione o dispositivo que necessita de uma reposição do código de acesso.  

    ![Uma captura de tela da página dispositivos, com dois blocos que mostram dispositivos não identificados, genericamente nomeados. Uma faixa cinza fica diretamente abaixo dos dispositivos e solicita que o usuário identifique o dispositivo que está usando ou adicione um novo.](./media/rename-reset-device-step2-1808.png) 

3. Selecione **Repor Código de Acesso**. Se a opção de código de acesso não estiver visível na parte superior da sua página, selecione **Mais (…)**  > **Repor Código de Acesso**.   

   ![A página de detalhes do dispositivo para um dispositivo selecionado no site do Portal da Empresa, com uma lista de ligações na parte superior que apresenta Mudar o Nome, Remover, Repor Dispositivo, Repor Código de Acesso e Bloqueio Remoto. ](./media/rename-reset-device-1808.png)   

    ![Captura de tela do ícone mais, realçado com uma seta vermelha.](./media/rename-reset-device-step3-more-1808.png)  

4. Quando lhe for pedido, clique em **Terminar Sessão**. Quando lhe for pedido novamente, volte a iniciar sessão. Entre novamente no site do Portal da Empresa em cinco minutos ou Portal da Empresa não redefinirá a senha do dispositivo.  

   > [!NOTE]
   > Tem de iniciar sessão novamente para confirmar a sua identidade. Este procedimento serve para impedir que o código de acesso do seu dispositivo seja reposto através de tentativas maliciosas.

   ![Capturas de ecrã de exemplo que mostram um pedido para terminar sessão no Portal da Empresa. Os botões de intervenção do utilizador são Terminar Sessão e Cancelar.](./media/iwp-reset-passcode-popup-1808.png)

5. É apresentada uma mensagem a avisá-lo de que o código de acesso do dispositivo existente está prestes a ser removido. Clique em **Repor Código de Acesso** para confirmar.  
    > [!WARNING]
    > Depois de repor o código de acesso, qualquer pessoa que tenha acesso físico ao dispositivo poderá aceder às informações mais pessoais e empresariais no mesmo. Se não tiver atualmente o dispositivo na sua posse, não reponha o código de acesso.  

   ![Captura de ecrã de exemplo que mostra a segunda mensagem de reposição do código de acesso. Inclui uma ligação para saber mais sobre como definir um novo código de acesso na documentação e botões individuais para repor o código de acesso e cancelar.](./media/iwp-reset-passcode-popup2-1808.png) 

6. Se estiver a repor o código de acesso de um dispositivo iOS, o respetivo código de acesso existente será removido. Para dispositivos Windows ou Android, você receberá uma senha temporária para desbloquear o dispositivo e definir uma nova senha. 

   > [!NOTE]
   > Pode encontrar a palavra-passe temporária para dispositivos Windows e Android no Portal da Empresa, na página de detalhes do dispositivo. Veja a secção [Configurar um novo código de acesso](reset-your-passcode-cpwebsite.md#set-up-a-new-passcode) para obter descrições de códigos de acesso mais específicas do sistema operativo.  
   
7. No seu dispositivo, aceda a **Definições** e altere o código de acesso temporário. 

8. É apresentado um sinalizador no canto superior direito do site do Portal da Empresa. Clique para ler a notificação e confirme se a palavra-passe foi reposta com êxito.  

## <a name="set-up-a-new-passcode"></a>Configurar um novo código de acesso  

Esta secção descreve a reposição do código de acesso e o comportamento da palavra-passe temporária para a plataforma de cada dispositivo.  

**Android**: Remove a senha existente e cria uma senha temporária composta por letras e números.

**iOS**: Remove a senha existente e não cria uma senha temporária. Se você usar o Touch ID para abrir o dispositivo ou fazer compras, deverá configurá-lo novamente.  

**Windows 10 Mobile**: Remove a senha existente e cria uma senha temporária composta por letras e números. Se estiver configurado, o reconhecimento facial do Windows Hello irá continuar a funcionar com o dispositivo.

**Windows Phone 8.1**: Remove a senha existente e cria uma senha temporária composta por números.  

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
