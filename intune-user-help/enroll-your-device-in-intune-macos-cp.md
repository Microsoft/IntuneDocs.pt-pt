---
title: Inscrever o seu dispositivo macOS no Intune com o Portal da Empresa | Documentos da Microsoft
description: Descreve como inscrever um dispositivo macOS no Intune com a aplicação Portal da Empresa
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 3dac9446d7a1097f5be4d0851cd78e8cbb86cc4e
ms.sourcegitcommit: 2198a39ae48beca5fc74316976bc3fc9db363659
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38224766"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>Inscrever o seu dispositivo macOS no Intune com a aplicação Portal da Empresa

O acesso às aplicações, aos dados e aos recursos da sua organização permite-lhe fazer o seu trabalho mais facilmente. A sua organização está a utilizar o Intune para [gerir o acesso a esses recursos](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md), o que exige que transfira a aplicação Portal da Empresa para macOS. Estas instruções funcionam para dispositivos macOS em OS X El Capitan 10.11 e posterior.


1. Na sua __Dock__, procure o __Safari__, abra uma nova janela e, em seguida, abra o [site do Portal da Empresa](https://portal.manage.microsoft.com).

2. Inicie sessão no site do Portal da Empresa com a sua conta escolar ou profissional.

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. Após iniciar sessão, clique no **Menu** no canto superior esquerdo da página e selecione **Os Meus Dispositivos**.

   ![Uma captura de ecrã da página de destino do portal Web, com o mesmo a indicar que as aplicações ainda não podem ser instaladas e o botão Os Meus Dispositivos abaixo.](./media/macOS_enroll_001_landing_page.png)

4. Na página __Os Meus Dispositivos__, será apresentada uma lista de dispositivos inscritos ou simplesmente uma faixa. Isto varia consoante já tenha um dispositivo macOS ou outro inscrito. Para inscrever um dispositivo que não esteja listado, selecione a faixa __Se o seu dispositivo estiver listado, toque aqui para identificá-lo. Também pode tocar aqui para inscrever o seu dispositivo se não estiver listado__. Se não tiver nenhum dispositivo inscrito, a faixa mostrará a mensagem **Não tem dispositivos inscritos. Inscreva este dispositivo ao tocar aqui.**

    ![Captura de ecrã a mostrar a página Os Meus Dispositivos, com alguns dispositivos não identificados, acima da faixa de aviso para inscrever dispositivos não listados ou identificar os dispositivos não identificados.](./media/macOS_enroll_002_tap_here_banner.png)

5. Transferir a aplicação Portal da Empresa para o seu dispositivo macOS para continuar a inscrever.

    ![O aviso que pede ao utilizador para transferir a aplicação Portal da Empresa do macOS. Este aviso tem o texto apresentado no passo acima de um botão que indica "Transferir" no canto inferior direito.](./media/macOS_enroll_IWP_CP_app_notice.png)

6. O seu Mac irá verificar se a transferência do **CompanyPortal.pkg** pode ser aberta em segurança. Abra o instalador e siga o processo de instalação.

7. Quando o instalador concluir a operação, abra a pasta **Aplicações** ou o **Launchpad** e, em seguida, abra o **Portal da Empresa**.

8. O seu Mac apresentará a mensagem **"PortalDaEmpresa" é uma aplicação transferida da Internet. Tem a certeza de que pretende abri-la?** Clique em **Abrir**.

   > [!NOTE]
   > O Intune precisa de aceder ao seu computador para confirmar que o dispositivo é suficientemente seguro para aceder aos recursos da sua organização. Se o seu computador se recusar a abrir a aplicação Portal da Empresa, experimente [desativar o controlador de chamadas](https://support.apple.com/HT202491) e, em seguida, abrir a aplicação.

9. O primeiro ecrã que verá na aplicação Portal da Empresa pedir-lhe-á que **Inicie Sessão** com a mesma conta escolar ou profissional que utilizou para iniciar sessão no site do Portal da Empresa.

10. O Portal da Empresa confirma as suas informações de conta e, em seguida, apresenta-lhe o estado da sua **Inscrição de Dispositivo** e da **Conformidade do Dispositivo**. Existirão triângulos amarelos a informá-lo das ações que tem de efetuar para se certificar de que o Mac está seguro para utilizar no trabalho. Clique em **Começar** para iniciar a [inscrição do seu dispositivo para gestão](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).

11. O seu Mac iniciará a inscrição para gestão. Poderá ser-lhe pedido que forneça as informações de início de sessão do seu computador durante este tempo. A inscrição poderá demorar alguns minutos. Durante este tempo, poderá fazer outras coisas no seu computador. É apresentada uma mensagem assim que terminar a Configuração de Acesso da Empresa para o informar que está pronto.

Ainda precisa de ajuda? Contacte o suporte da empresa. Pode encontrar as informações de contacto no [Site do Portal da Empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
