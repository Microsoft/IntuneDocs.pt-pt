---
title: Configurar o acesso do dispositivo iOS aos recursos da empresa | Microsoft Docs
description: Descreve como fazer com que o dispositivo iOS seja gerido pelo Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
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
ms.openlocfilehash: 50fc19410b280e984c8dc3abe620baad7c3267de
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959541"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configurar o acesso do dispositivo iOS aos recursos da empresa

Inscreva o seu dispositivo iOS na aplicação Portal da Empresa do Intune para obter acesso seguro ao e-mail, ficheiros e aplicações da sua organização.

Antes de ter permissão para aceder a dados proprietários de um dispositivo pessoal ou empresarial, tem de ter o dispositivo gerido. Depois de o seu dispositivo se tornar gerido, a sua organização irá atribuir políticas e aplicações ao dispositivo através do respetivo fornecedor de gestão de dispositivos móveis (MDM). 

Para manter o acesso às informações do trabalho ou da escola a partir do seu dispositivo, tem de o configurar para corresponder às definições preferenciais da sua organização. Este artigo descreve como o Portal da Empresa o ajuda a inscrever, configurar e manter o seu dispositivo para cumprir estes requisitos.

> [!NOTE]
> Se tentou aceder ao e-mail da empresa na aplicação Mail e recebeu uma mensagem para ter o dispositivo gerido, está no sítio certo. Siga as instruções abaixo para obter acesso ao seu e-mail e a outros recursos empresariais no seu dispositivo iOS.

## <a name="what-to-expect-from-the-company-portal-app"></a>O que esperar da aplicação Portal da Empresa

### <a name="security"></a>Segurança
Durante a configuração inicial, a aplicação requer que se autentique na sua organização. Em seguida, informa-o de quaisquer definições do dispositivo que tenha de atualizar. Muitas vezes, por exemplo, as organizações definem requisitos de palavra-passe com limites de carateres mínimos e máximos que terá de cumprir.    

### <a name="protection"></a>Protection
Após a inscrição do seu dispositivo, a aplicação Portal da Empresa irá continuar a garantir que o mesmo se encontra protegido. Se, por exemplo, instalar uma aplicação de uma origem não fidedigna, a aplicação Portal da Empresa irá alertá-lo e, por vezes, revogar o acesso aos dados da empresa. Políticas de proteção de aplicações como esta são comuns nas organizações. Exigem frequentemente a desinstalação da aplicação não fidedigna antes de poder recuperar o acesso.

### <a name="setting-notifications"></a>Definir as notificações
Se, após a inscrição, a sua organização aplicar um novo requisito de segurança, como a autenticação multifator, a aplicação Portal da Empresa irá notificá-lo. Terá a oportunidade de ajustar as suas definições para que possa continuar a trabalhar a partir do seu dispositivo.  

Para obter mais informações sobre a inscrição, veja [O que acontece quando instalo a aplicação Portal da Empresa e inscrevo o meu dispositivo?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios) 

## <a name="before-you-start"></a>Antes de começar

- Depois de começar a inscrição, certifique-se de que conclui todo o processo. Se colocar o processo em pausa durante vários minutos, a configuração poderá terminar e ser necessário começar de novo.  
- Se este processo falhar, regresse à aplicação Portal da Empresa e tente novamente.  
- Verifique se o Wi-Fi está a funcionar e se o Safari funciona no dispositivo.
- Transfira e instale a [aplicação Portal da Empresa do Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md).  


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>Utilizar a aplicação Portal da Empresa para configurar o acesso aos recursos da empresa

|O que vê|Explicação|
|---|---|
|![O ecrã de início de sessão do Portal da Empresa, com o botão "Iniciar sessão" na parte inferior.](./media/ios-01-cp-enroll-1802.PNG)|Abra a aplicação Portal da Empresa e toque em **Iniciar Sessão**.|
|![Pedido de início de sessão do Azure AD.](./media/ios-02-cp-enroll-1802.PNG)|Introduza o endereço de e-mail da empresa e toque em **Seguinte**.|
|![Pedido de palavra-passe do Azure AD.](./media/ios-03-cp-enroll-1802.PNG)|Introduza a palavra-passe e toque em **Iniciar sessão**.|
|![A carregar o ecrã de recursos da empresa.](./media/ios-04-cp-enroll-1802.PNG)|Aguarde o carregamento deste ecrã.|
|![Página de termos e condições.](./media/ios-05-cp-enroll-1802.PNG)|Leia e **Aceite Todos** os Termos e Condições.|
|![Ecrã Configuração de acesso à empresa. Atualmente, a gestão e as definições precisam de resolução.](./media/ios-06-cp-enroll-1802.PNG)|Toque em **Começar** para iniciar o processo de fazer com que o seu dispositivo consiga aceder aos recursos da empresa. Se não conseguir fazê-lo agora, poderá **Adiar** o processo, mas não conseguirá obter o e-mail, documentos e etc.|
|![Ecrã O que a minha empresa pode ver.](./media/ios-07-cp-enroll-1802.PNG)|**Saiba mais** sobre o que a sua empresa pode ver ao tocar na ligação na parte inferior. Caso contrário, toque em **Continuar**.|
|![Ecrã O que se segue.](./media/ios-08-cp-enroll-1802.PNG)|Este ecrã explica o que está a acontecer na configuração. Vai passar algum tempo no Safari, na aplicação Definições e na aplicação Portal da Empresa. Toque em **Continuar**.|
|![A carregar o ecrã após tocar em Seguinte no ecrã O que se segue.](./media/ios-09-cp-enroll-1802.PNG)|Aguarde o carregamento deste ecrã.|
|![Mudou para o Safari para a inscrição.](./media/ios-cp-sent-to-safari-1808.png)|É enviado para o Safari para obter informações de gestão do seu dispositivo.|
|![Pedido do sistema para abrir a aplicação Definições.](./media/ios-8-cp-enroll-1711.PNG)|Toque em **Permitir** para abrir a aplicação Definições para transferir o perfil de configuração. Instale esta opção para permitir à sua empresa gerir informações empresariais no dispositivo.|
|![Captura do ecrã Instalar Perfil nas definições do dispositivo.](./media/ios-9-cp-enroll-1711.PNG)|Toque em **Instalar**.|
|![Diálogo modal A instalar perfil na parte inferior do ecrã.](./media/ios-10-cp-enroll-1711.PNG)|Toque em **Instalar**.|
|![Ecrã de carregamento O perfil está a ser instalado.](./media/ios-11-cp-enroll-1711.PNG)|Aguarde o carregamento deste ecrã.|
|![Ecrã de aviso Gestão de perfis.](./media/ios-12-cp-enroll-1711.PNG)|Este aviso, escrito pela Apple, permite-lhe saber mais sobre os tipos de ações que podem ser realizadas num dispositivo sob gestão. Saiba mais sobre [as informações que a sua empresa pode ver](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).|
|![Pedido do sistema sobre a confiança na gestão remota.](./media/ios-13-cp-enroll-1711.PNG)|Toque em **Confiar** para permitir à sua empresa gerir as informações empresariais e definições no dispositivo.|
|![Ecrã de carregamento A terminar a instalação do perfil.](./media/ios-14-cp-enroll-1711.PNG)|Aguarde o carregamento deste ecrã.|
|![Ecrã Perfil instalado.](./media/ios-15-cp-enroll-1711.PNG)|O perfil foi instalado e as definições e as informações empresariais do dispositivo estão muito mais próximas de serem geridas.|
|![Mudou para o Safari para a inscrição.](./media/ios-16-cp-enroll-1711.PNG)|É enviado novamente para o Safari para terminar a obtenção de informações de gestão para o dispositivo. |
|![Pedido do sistema para abrir o portal da empresa.](./media/ios-17-cp-enroll-1711.PNG)|Toque em **Abrir**.|
|![Ecrã A carregar recursos da empresa.](./media/ios-21-cp-enroll-1802.PNG)|Aguarde o carregamento deste ecrã.|
|![Selecione a categoria de dispositivo na aplicação do portal da empresa.](./media/ios-22-cp-enroll-1802.PNG)|Selecione a melhor categoria para o seu dispositivo. Normalmente, está relacionada com quem é o proprietário do dispositivo ou onde este se encontra na maior parte do tempo.|
|![Categoria selecionada.](./media/ios-23-cp-enroll-1802.PNG)||
|![Gestão de dispositivos com êxito. Agora tem de atualizar as definições.](./media/ios-24-cp-enroll-1802.PNG)|Conseguiu fazer com o que o seu dispositivo passe a ser gerido. Provavelmente, ainda existem definições, como o comprimento da palavra-passe, que a sua empresa lhe poderá pedir para atualizar. Toque em **Continuar** para continuar.|
|![A confirmar definições do dispositivo.](./media/ios-25-cp-enroll-1802.PNG)|O Portal da Empresa verificará se as definições precisam de ser atualizadas.|
|![Verificação de definições concluída, com uma versão incorreta do SO](./media/ios-26-cp-enroll-1802.PNG)|O Portal da Empresa apresentará as instruções sobre como pode corrigir os eventuais problemas com as definições. Depois de corrigir os problemas, toque em **Verificar Definições**.|
|![Ecrã de carregamento A confirmar definições do dispositivo](./media/ios-27-cp-enroll-1802.PNG)|O dispositivo verificará se as definições são suficientemente seguras para aceder aos recursos da empresa.|
|![Definições inscritas e atualizadas com êxito](./media/ios-28-cp-enroll-1802.PNG)|Parabéns! O dispositivo está agora inscrito no Intune.|

> [!Note]
> Pode ter de realizar mais alguns passos antes de o dispositivo estar totalmente gerido. Saiba mais sobre a [inscrição do seu dispositivo através da gestão de despesas de telecomunicações](enroll-your-device-with-telecom-expense-management-ios.md). Se a sua organização estiver a utilizar o Programa de Registo de Aparelho da Apple, descubra mais informações [aqui](enroll-your-device-dep-ios.md).

Ainda precisa de ajuda? Contacte o suporte da empresa. Pode encontrar as informações de contacto no [Site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
