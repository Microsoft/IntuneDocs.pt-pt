---
title: Como repor o código de acesso a partir do site do Portal da Empresa | Documentos da Microsoft
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/28/2018
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
ms.openlocfilehash: 5e973e18a79c18af6b201194fc1a6534da5fa38a
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "55838041"
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>Como repor o código de acesso do dispositivo a partir do site do Portal da Empresa

Se perder o PIN ou a palavra-passe do seu dispositivo, pode utilizar o [site do Portal da Empresa](https://portal.manage.microsoft.com) para efetuar a reposição.  

Se estiver a utilizar um dispositivo pertencente à empresa, poderá não ser apresentada a opção para repor o código de acesso do dispositivo. Contacte o suporte da empresa para que este reponha o código de acesso.

   > [!NOTE]
   > Não pode repor o código de acesso para dispositivos com o Android 7.0 e versões posteriores. Caso se esqueça do código de acesso, terá de repor as definições de fábrica do dispositivo. 

## <a name="reset-your-passcode"></a>Repor o código de acesso

1.  Abra o [site do Portal da Empresa](https://portal.manage.microsoft.com) e selecione o botão __Menu__ > __Dispositivos__.  

2. Selecione o dispositivo que necessita de uma reposição do código de acesso.  

    ![Uma captura de ecrã da página Dispositivos, com dois mosaicos que mostram dispositivos não identificados com um nome genérico. Uma faixa cinzenta está diretamente abaixo dos dispositivos e pede ao utilizador que identifique o dispositivo que está a utilizar ou adicione um novo.](./media/rename-reset-device-step2-1808.png) 

3. Selecione **Repor Código de Acesso**. Se a opção de código de acesso não estiver visível na parte superior da sua página, selecione **Mais (…)** > **Repor Código de Acesso**.   

   ![A página de detalhes do dispositivo para um dispositivo selecionado no site do Portal da Empresa, com uma lista de ligações na parte superior que apresenta Mudar o Nome, Remover, Repor Dispositivo, Repor Código de Acesso e Bloqueio Remoto. ](./media/rename-reset-device-1808.png)   

    ![Vista ampliada do ícone Mais, realçado com uma seta vermelha.](./media/rename-reset-device-step3-more-1808.png)  

4. Quando lhe for pedido, clique em **Terminar Sessão**. Quando lhe for pedido novamente, volte a iniciar sessão. Tem de iniciar sessão novamente no site do Portal da Empresa dentro de cinco minutos, caso contrário o Portal da Empresa não irá repor o código de acesso do dispositivo.  

   > [!NOTE]
   > Tem de iniciar sessão novamente para confirmar a sua identidade. Este procedimento serve para impedir que o código de acesso do seu dispositivo seja reposto através de tentativas maliciosas.

   ![Capturas de ecrã de exemplo que mostram um pedido para terminar sessão no Portal da Empresa. Os botões de intervenção do utilizador são Terminar Sessão e Cancelar.](./media/iwp-reset-passcode-popup-1808.png)

5. É apresentada uma mensagem a avisá-lo de que o código de acesso do dispositivo existente está prestes a ser removido. Clique em **Repor Código de Acesso** para confirmar.  
    > [!WARNING]
    > Depois de repor o código de acesso, qualquer pessoa que tenha acesso físico ao dispositivo poderá aceder às informações mais pessoais e empresariais no mesmo. Se não tiver atualmente o dispositivo na sua posse, não reponha o código de acesso.  

   ![Captura de ecrã de exemplo que mostra a segunda mensagem de reposição do código de acesso. Inclui uma ligação para saber mais sobre como definir um novo código de acesso na documentação e botões individuais para repor o código de acesso e cancelar.](./media/iwp-reset-passcode-popup2-1808.png) 

6. Se estiver a repor o código de acesso de um dispositivo iOS, o respetivo código de acesso existente será removido. Para dispositivos Windows ou Android, será emitido um código de acesso temporário para desbloquear o dispositivo e definir um novo código de acesso. 

   > [!NOTE]
   > Pode encontrar a palavra-passe temporária para dispositivos Windows e Android no Portal da Empresa, na página de detalhes do dispositivo. Veja a secção [Configurar um novo código de acesso](reset-your-passcode-cpwebsite.md#set-up-a-new-passcode) para obter descrições de códigos de acesso mais específicas do sistema operativo.  
   
7. No seu dispositivo, aceda a **Definições** e altere o código de acesso temporário. 

8. É apresentado um sinalizador no canto superior direito do site do Portal da Empresa. Clique para ler a notificação e confirme se a palavra-passe foi reposta com êxito.  

## <a name="set-up-a-new-passcode"></a>Configurar um novo código de acesso  

Esta secção descreve a reposição do código de acesso e o comportamento da palavra-passe temporária para a plataforma de cada dispositivo.  

**Android**: Remove o código de acesso existente e cria um código de acesso temporário constituído por letras e números.

**iOS**: Remove o código de acesso existente e não cria um código de acesso temporário. Se utilizar o scanner de impressões digitais Touch ID para abrir o seu dispositivo ou fazer compras, terá de configurá-lo novamente.  

**Windows 10 Mobile**: Remove o código de acesso existente e cria um código de acesso temporário constituído por letras e números. Se estiver configurado, o reconhecimento facial do Windows Hello irá continuar a funcionar com o dispositivo.
    
**Windows Phone 8.1**: Remove o código de acesso existente e cria um código de acesso temporário constituído por números.  

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
