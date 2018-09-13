---
title: Inscrever o seu dispositivo macOS no Intune com o Portal da Empresa | Documentos da Microsoft
description: Descreve como inscrever um dispositivo macOS no Intune com a aplicação Portal da Empresa
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/08/2018
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
ms.openlocfilehash: af5c7492563c8df0168eff3250ae1bbad2cc323e
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/29/2018
ms.locfileid: "43147722"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>Inscrever o seu dispositivo macOS no Intune com a aplicação Portal da Empresa

Inscreva o seu dispositivo macOS na aplicação Portal da Empresa do Intune para obter acesso seguro ao e-mail, ficheiros e aplicações da sua organização.

Muitas vezes, as organizações requerem que o seu dispositivo seja gerido antes de poder aceder a dados proprietários a partir do mesmo. Depois de um dispositivo se tornar gerido, as organizações podem enviar políticas e aplicações para o dispositivo através do respetivo fornecedor de gestão de dispositivos móveis. Para obter acesso contínuo às informações do trabalho ou da escola a partir do seu dispositivo, tem de o configurar para corresponder às definições de política.  

Este artigo descreve como a aplicação Portal da Empresa do Intune para macOS o ajuda a inscrever, configurar e manter o seu dispositivo para cumprir os requisitos da sua organização.

## <a name="what-to-expect-from-the-company-portal-app"></a>O que esperar da aplicação Portal da Empresa

Durante a configuração inicial, a aplicação requer que se autentique na sua organização. Em seguida, informa-o de quaisquer definições do dispositivo que tenha de efetuar. Muitas vezes, por exemplo, as organizações definem requisitos de palavra-passe com limites de carateres mínimos e máximos que terá de cumprir.    

Após a inscrição do seu dispositivo, a aplicação Portal da Empresa irá continuar a garantir que o mesmo se encontra protegido. Se, por exemplo, instalar uma aplicação de uma origem não fidedigna, a aplicação Portal da Empresa irá alertá-lo e, por vezes, revogar o acesso aos dados da empresa. Políticas de proteção de aplicações como esta são comuns nas organizações e, muitas vezes, requerem que desinstale aplicações não fidedignas para poder recuperar o acesso.

Se, após a inscrição, a sua organização aplicar um novo requisito de segurança, como a autenticação multifator, a aplicação Portal da Empresa irá notificá-lo. Terá a oportunidade de ajustar as suas definições para que possa continuar a trabalhar a partir do seu dispositivo.  

Para obter mais informações sobre a inscrição, veja [O que acontece quando instalo a aplicação Portal da Empresa e inscrevo o meu dispositivo?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md)  

## <a name="get-your-device-managed"></a>Gerir o seu dispositivo  
Utilize os passos seguintes para inscrever dispositivos macOS com o OS X El Capitan 10.11 e posterior.   


1. Para aceder ao site do Portal da Empresa, abra uma nova janela no __Safari__ e aceda a https://portal.manage.microsoft.com.  

2. Inicie sessão no site do Portal da Empresa com a sua conta escolar ou profissional.

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. No canto superior esquerdo da página, clique em **Menu** > **Dispositivos**.  

4. A página __Dispositivos__ irá apresentar uma lista de dispositivos geridos ou uma faixa. O que é apresentado varia em função de já ter ou não um dispositivo gerido. 
    * Para adicionar um dispositivo que não esteja apresentado, selecione a faixa com a mensagem **Toque aqui para indicar que dispositivo está a utilizar ou adicionar um novo dispositivo**.
    * Se não tiver nenhum dispositivo, a faixa mostrará a mensagem **Não tem dispositivos geridos. Adicione este dispositivo ao tocar aqui.** Clique na faixa para adicionar o seu dispositivo.  

     ![Uma captura de ecrã da página Dispositivos, com um quadrado vermelho à volta da opção de faixa para realçar a opção a clicar.](./media/CP-enroll-MACOS-1808.png)  
5.  Conclua o passo abaixo que corresponder à mensagem atualmente apresentada no Portal da Empresa.  
    * Se estiver a adicionar um dispositivo pela primeira vez, ser-lhe-á pedido que transfira a aplicação Portal da Empresa no mesmo. Clique em **Transferir** para continuar.  

         ![Captura de ecrã de exemplo do ecrã de pedido para transferir a aplicação Portal da Empresa para macOS. O utilizador tem a opção de clicar no botão azul Transferir no canto inferior esquerdo do pedido ou no botão cinzento Cancelar no canto inferior direito.](./media/CP-enroll-download-macOS-1808.png)  

    * Se já tiver um dispositivo macOS gerido, será apresentada uma mensagem com uma lista dos seus dispositivos macOS atualmente geridos. Selecione **O meu dispositivo não está na lista** > **Transferir** para transferir a aplicação Portal da Empresa no dispositivo que está a adicionar.  

         ![Captura de ecrã de exemplo do ecrã de pedido para transferir a aplicação Portal da Empresa para macOS. O utilizador tem a opção de selecionar *O meu dispositivo não está na lista* ou um dispositivo específico a meio da página. O botão azul Transferir é apresentado no canto inferior esquerdo do pedido e o botão cinzento Cancelar é apresentado no canto inferior direito](./media/cp-mac-os-device-isnt-here-1808.png)  

6. O seu dispositivo irá verificar se o ficheiro de instalação **CompanyPortal.pkg** pode ser aberto em segurança. Após a conclusão dessa operação, abra o instalador e conclua a instalação.  

7. Quando o instalador concluir a operação, aceda ao **Launchpad** e abra o **Portal da Empresa**.  

8. O seu dispositivo macOS irá pedir-lhe que confirme se pretende abrir a aplicação Portal da Empresa. Clique em **Abrir**.  

   > [!TIP]
   > O Intune precisa de aceder ao seu computador para confirmar que o dispositivo é suficientemente seguro para aceder aos recursos da sua organização. Se o seu computador se recusar a abrir a aplicação Portal da Empresa, [desative o Gatekeeper](https://support.apple.com/HT202491). Em seguida, abra a aplicação.

9. O primeiro ecrã apresentado na aplicação Portal da Empresa pede-lhe para **Iniciar Sessão**. Utilize a mesma conta escolar ou profissional que utilizou para iniciar sessão no site do Portal da Empresa.

10. O Portal da Empresa confirma as suas informações de conta e apresenta o estado da sua **Inscrição de Dispositivo** e da **Conformidade do Dispositivo**. Os triângulos amarelos realçam as ações que tem de efetuar para proteger o seu dispositivo macOS para a escola ou o trabalho. Clique em **Iniciar** para iniciar a inscrição. Saiba mais sobre [o que sua organização pode ver](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md) quando inscreve um dispositivo.

11. Poderá ser-lhe pedido que forneça as informações de início de sessão do seu computador. A inscrição do seu dispositivo na gestão poderá demorar alguns minutos. Durante este tempo, poderá fazer outras coisas no seu dispositivo. Irá receber uma mensagem após a conclusão da Configuração de Acesso da Empresa para o informar de que está pronto.  

Ainda precisa de ajuda? Contacte o suporte da empresa. Pode encontrar as informações de contacto no [Site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
