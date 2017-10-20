---
title: Inscrever o dispositivo macOS no Intune | Documentos da Microsoft
description: Descreve como encriptar dispositivos macOS no Intune
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58eb0e7a-1321-4c66-a281-88fb01e72c1c
searchScope: User help
ROBOTS: 
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: ec1120f8fe040227d513fa5de2c096b34611ed7a
ms.sourcegitcommit: 0ee9909fc041c2e49c0e0312ae05f40bbeb2ee51
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2017
---
# <a name="enroll-your-macos-device-in-intune"></a>Inscrever o dispositivo macOS no Intune

O acesso às aplicações, aos dados e aos recursos da sua organização permite-lhe fazer o seu trabalho. Se estiver a utilizar um dispositivo macOS no trabalho, precisa de instalar um __Perfil de Gestão__. Este é apenas um ficheiro configurado pelo suporte da empresa que carrega as definições e acede a informações no seu Mac. Quer saber mais? Saiba [o que acontece se instalar a aplicação do Portal da Empresa e inscrever o seu dispositivo no Intune](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md)

1. Na sua __Dock__, procure o __Safari__, abra uma nova janela e, em seguida, abra o [site do Portal da Empresa](https://portal.manage.microsoft.com).
2. Inicie sessão no site do Portal da Empresa com a sua conta escolar ou profissional.

  [!INCLUDE[wit_nextref](includes/end-user-password-guidance.md)]

3. Após iniciar sessão, clique no **Menu** no canto superior esquerdo da página e selecione **Os Meus Dispositivos**.

 ![Uma captura de ecrã da página de destino do portal Web, com o mesmo a indicar que as aplicações ainda não podem ser instaladas e o botão Os Meus Dispositivos abaixo.](./media/macOS_enroll_001_landing_page.png)

4. Na página __Os Meus Dispositivos__, será apresentada uma lista de dispositivos inscritos ou simplesmente uma faixa. Isto varia consoante já tenha um dispositivo macOS ou outro inscrito. Para inscrever um dispositivo que não esteja listado, selecione a faixa __Se o seu dispositivo estiver listado, toque aqui para identificá-lo. Também pode tocar aqui para inscrever o seu dispositivo se não estiver listado__. Se não tiver nenhum dispositivo inscrito, a faixa mostrará a mensagem **Não tem dispositivos inscritos. Inscreva este dispositivo ao tocar aqui.**

  ![Captura de ecrã a mostrar a página Os Meus Dispositivos, com alguns dispositivos não identificados, acima da faixa de aviso para inscrever dispositivos não listados ou identificar os dispositivos não identificados.](./media/macOS_enroll_002_tap_here_banner.png)

5. Será apresentada uma janela de pop-up com uma breve explicação sobre o motivo pelo qual vai __Identificar ou inscrever este dispositivo__. Analise-a e, em seguida, clique em __Inscrever__ para continuar.

 ![Identificar ou Inscrever este Dispositivo macOS](./media/macOS_enroll_003_IDenroll_popup.png)

6. Será apresentada uma segunda janela de pop-up com uma breve explicação sobre o que acontecerá quando __Inscrever este dispositivo__. Analise-a e, em seguida, clique em __Instalar__ para continuar.

 ![Inscrever este dispositivo macOS](./media/macOS_enroll_004_enroll_popup.png)

  > [!NOTE]
  > O Intune precisa de aceder ao seu computador para confirmar que o dispositivo é suficientemente seguro para aceder aos recursos da sua organização. Saiba [o que o acontece quando inscreve o dispositivo no Intune](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md).

7. A janela __Preferências do Sistema__ irá abrir e perguntar se pretende __Instalar o "Perfil de Gestão"?__ Clique em __Instalar__ para continuar ou clique em __Mostrar Perfil__ para obter mais detalhes.

 ![Instalar Perfil de Gestão](./media/macOS_enroll_005_sysprefs_mgmt_profile.png)

8. Será apresentada uma janela de pop-up do macOS. Confirme que pretende fazer alterações ao disponibilizar o __Nome de Utilizador__ e a __Palavra-passe__ do seu computador e, em seguida, clique em __OK__. Esta ação irá instalar o perfil de gestão no seu Mac.

 ![Pop-up de Instalação do Perfil do macOS](./media/macOS_enroll_006_sysprefs_admin_login.png)

9. Poderá ver algumas mensagens adicionais a partir do seu Mac com mais detalhes sobre o perfil ou se tem a certeza que quer __Instalar__. Clique em __Continuar__ e __Instalar__ nestes para continuar. Depois da conclusão da instalação, poderá ver o seu __Perfil de Gestão__ recém-instalado na lista de __Perfis de Dispositivo__.

 ![Perfil do macOS Instalado](./media/macOS_enroll_007_sysprefs_installed_profile.png)

Alguns perfis poderão ser apresentados como **Não verificado**. No entanto, desde que estes pertençam à sua empresa, esta situação é normal.

Ainda precisa de ajuda? Contacte o suporte da empresa. Pode encontrar as informações de contacto no [Site do Portal da Empresa](https://portal.manage.microsoft.com).
