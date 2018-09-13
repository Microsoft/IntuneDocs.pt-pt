---
title: Ativar o acesso aos recursos da empresa | Microsoft Docs
description: Descreve como fazer com que o dispositivo iOS seja gerido pelo Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 51492c1a8d7e32ab7dbdd5d896e7726c877d62d5
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/29/2018
ms.locfileid: "43149588"
---
# <a name="set-up-access-to-your-company-resources"></a>Ativar o acesso aos recursos da empresa

Inscreva o seu dispositivo iOS na aplicação Portal da Empresa do Intune para obter acesso seguro ao e-mail, ficheiros e aplicações da sua organização.

Muitas vezes, as organizações requerem que o seu dispositivo seja gerido antes de poder aceder a dados proprietários a partir do mesmo. Depois de um dispositivo se tornar gerido, as organizações podem enviar políticas e aplicações para o dispositivo através do respetivo fornecedor de gestão de dispositivos móveis. 

Para obter acesso contínuo às informações do trabalho ou da escola a partir do seu dispositivo, tem de o configurar para corresponder às definições de política. Este artigo descreve como a aplicação Portal da Empresa do Intune para iOS o ajuda a inscrever, configurar e manter o seu dispositivo para cumprir os requisitos da organização.

> [!NOTE]
> Se estiver a tentar aceder ao e-mail da empresa na aplicação Mail, é provável que lhe tenha sido pedido para gerir o seu dispositivo de forma a mantê-lo seguro. Siga as instruções abaixo para obter acesso ao seu e-mail e a outros recursos empresariais no seu dispositivo iOS.

## <a name="what-to-expect-from-the-company-portal-app"></a>O que esperar da aplicação Portal da Empresa

### <a name="security"></a>Segurança
Durante a configuração inicial, a aplicação requer que se autentique na sua organização. Em seguida, informa-o de quaisquer definições do dispositivo que tenha de efetuar. Muitas vezes, por exemplo, as organizações definem requisitos de palavra-passe com limites de carateres mínimos e máximos que terá de cumprir.    

### <a name="protection"></a>Proteção
Após a inscrição do seu dispositivo, a aplicação Portal da Empresa irá continuar a garantir que o mesmo se encontra protegido. Se, por exemplo, instalar uma aplicação de uma origem não fidedigna, a aplicação Portal da Empresa irá alertá-lo e, por vezes, revogar o acesso aos dados da empresa. Políticas de proteção de aplicações como esta são comuns nas organizações e, muitas vezes, requerem que desinstale aplicações não fidedignas para poder recuperar o acesso.

### <a name="setting-notifications"></a>Definir as notificações
Se, após a inscrição, a sua organização aplicar um novo requisito de segurança, como a autenticação multifator, a aplicação Portal da Empresa irá notificá-lo. Terá a oportunidade de ajustar as suas definições para que possa continuar a trabalhar a partir do seu dispositivo.  

Para obter mais informações sobre a inscrição, veja [O que acontece quando instalo a aplicação Portal da Empresa e inscrevo o meu dispositivo?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md) 

## <a name="before-you-start"></a>Antes de começar

- Depois de começar, certifique-se de que conclui todo o processo. Se colocar o processo em pausa durante vários minutos, a configuração poderá terminar e ser necessário começar de novo.  
    - Se este processo falhar, regresse à aplicação Portal da Empresa e tente novamente.  
- Verifique se o Wi-Fi está a funcionar e se o Safari funciona no dispositivo.
- Transfira e instale a [aplicação Portal da Empresa do Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md).


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>Utilizar a aplicação Portal da Empresa para configurar o acesso aos recursos da empresa

|O que vê|Explicação|
|---|---|
|![O ecrã de início de sessão do Portal da Empresa, com o botão "Iniciar sessão" na parte inferior.](./media/ios-01-cp-enroll-1802.png)|Abra a aplicação Portal da Empresa e toque em **Iniciar Sessão**.|
|![Pedido de início de sessão do Azure AD.](./media/ios-02-cp-enroll-1802.png)|Introduza o endereço de e-mail da empresa e toque em **Seguinte**.|
|![Pedido de palavra-passe do Azure AD.](./media/ios-03-cp-enroll-1802.png)|Introduza a palavra-passe e toque em **Iniciar sessão**.|
|![A carregar o ecrã de recursos da empresa.](./media/ios-04-cp-enroll-1802.png)|Aguarde o carregamento deste ecrã.|
|![Página de termos e condições.](./media/ios-05-cp-enroll-1802.png)|Leia e **Aceite Todos** os Termos e Condições.|
|![Ecrã Configuração de acesso à empresa. Atualmente, a gestão e as definições precisam de resolução.](./media/ios-06-cp-enroll-1802.png)|Toque em **Começar** para iniciar o processo de fazer com que o seu dispositivo consiga aceder aos recursos da empresa. Se não conseguir fazê-lo agora, poderá **Adiar** o processo, mas não conseguirá obter o e-mail, documentos e etc.|
|![Ecrã O que a minha empresa pode ver.](./media/ios-07-cp-enroll-1802.png)|**Saiba mais** sobre o que a sua empresa pode ver ao tocar na ligação na parte inferior. Caso contrário, toque em **Continuar**.|
|![Ecrã O que se segue.](./media/ios-08-cp-enroll-1802.png)|Este ecrã explica o que está a acontecer na configuração. Vai passar algum tempo no Safari, na aplicação Definições e na aplicação Portal da Empresa para concluir este processo. Toque em **Continuar**.|
|![A carregar o ecrã após tocar em Seguinte no ecrã O que se segue.](./media/ios-09-cp-enroll-1802.png)|Aguarde o carregamento deste ecrã.|
|![Mudou para o Safari para a inscrição.](./media/ios-7-cp-enroll-1711.png)|É enviado para o Safari para obter informações de gestão do seu dispositivo.|
|![Pedido do sistema para abrir a aplicação Definições.](./media/ios-8-cp-enroll-1711.png)|Toque em **Permitir** para abrir a aplicação Definições para transferir o perfil de configuração. Instale esta opção para permitir à sua empresa gerir informações empresariais no dispositivo.|
|![O perfil abre as definições do dispositivo.](./media/ios-9-cp-enroll-1711.png)|Toque em **Instalar**.|
|![Diálogo modal A instalar perfil na parte inferior do ecrã.](./media/ios-10-cp-enroll-1711.png)|Toque em **Instalar**.|
|![Ecrã de carregamento O perfil está a ser instalado.](./media/ios-11-cp-enroll-1711.png)|Aguarde o carregamento deste ecrã.|
|![Ecrã de aviso Gestão de perfis.](./media/ios-12-cp-enroll-1711.png)|Este aviso, escrito pela Apple, permite-lhe saber mais sobre os tipos de ações que podem ser realizadas num dispositivo sob gestão. Saiba mais sobre [as informações que a sua empresa pode ver](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).|
|![Pedido do sistema sobre a confiança na gestão remota.](./media/ios-13-cp-enroll-1711.png)|Toque em **Confiar** para permitir à sua empresa gerir as informações empresariais e definições no dispositivo.|
|![Ecrã de carregamento A terminar a instalação do perfil.](./media/ios-14-cp-enroll-1711.png)|Aguarde o carregamento deste ecrã.|
|![Ecrã Perfil instalado.](./media/ios-15-cp-enroll-1711.png)|O perfil foi instalado e as definições e as informações empresariais do dispositivo estão muito mais próximas de serem geridas.|
|![Mudou para o Safari para a inscrição.](./media/ios-16-cp-enroll-1711.png)|É enviado novamente para o Safari para terminar a obtenção de informações de gestão para o dispositivo. |
|![Pedido do sistema para abrir o portal da empresa.](./media/ios-17-cp-enroll-1711.png)|Toque em **Abrir**.|
|![Ecrã A carregar recursos da empresa.](./media/ios-21-cp-enroll-1802.png)|Aguarde o carregamento deste ecrã.|
|![Selecione a categoria de dispositivo na aplicação do portal da empresa.](./media/ios-22-cp-enroll-1802.png)|Selecione a melhor categoria para o seu dispositivo. Normalmente, está relacionada com quem é o proprietário do dispositivo ou onde este se encontra na maior parte do tempo.|
|![Categoria selecionada.](./media/ios-23-cp-enroll-1802.png)||
|![Gestão de dispositivos com êxito. Agora tem de atualizar as definições.](./media/ios-24-cp-enroll-1802.png)|Conseguiu fazer com o que o seu dispositivo passe a ser gerido. Provavelmente, ainda existem definições, como o comprimento da palavra-passe, que a sua empresa lhe poderá pedir para atualizar. Toque em **Continuar** para continuar.|
|![A confirmar definições do dispositivo.](./media/ios-25-cp-enroll-1802.png)|O Portal da Empresa verificará se as definições precisam de ser atualizadas.|
|![Verificação de definições concluída, com uma versão incorreta do SO](./media/ios-26-cp-enroll-1802.png)|O Portal da Empresa apresentará as instruções sobre como pode corrigir os eventuais problemas com as definições. Depois de corrigir os problemas, toque em **Verificar Definições**.|
|![Ecrã de carregamento A confirmar definições do dispositivo](./media/ios-27-cp-enroll-1802.png)|O dispositivo verificará se as definições são suficientemente seguras para aceder aos recursos da empresa.|
|![Definições inscritas e atualizadas com êxito](./media/ios-28-cp-enroll-1802.png)|Parabéns! O dispositivo está agora inscrito no Intune.|

> [!Note]
> Pode ter de realizar mais alguns passos antes de o dispositivo estar totalmente gerido. Saiba mais sobre a [inscrição do seu dispositivo através da gestão de despesas de telecomunicações](enroll-your-device-with-telecom-expense-management-ios.md). Se a sua organização estiver a utilizar o Programa de Registo de Aparelho da Apple, descubra mais informações [aqui](enroll-your-device-dep-ios.md).

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
