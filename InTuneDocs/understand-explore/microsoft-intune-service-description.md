---
title: "Descrição do Serviço | Documentos da Microsoft"
description: "O Intune é um serviço baseado na cloud que o ajuda a gerir dispositivos Windows, iOS, Mac OS X, Android e Windows Mobile."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 09/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0
ms.reviewer: cacamp
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f268cf29461447306d0f5c3ca06d541d9a03a49d
ms.openlocfilehash: 8e8257a426bd6b9a99e21e928b08c84f162d5da3


---

# <a name="microsoft-intune-service-description"></a>Descrição do serviço Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Microsoft Intune é um serviço baseado na cloud que o ajuda a gerir dispositivos com Windows, Mac OS X, iOS, Android ou Windows Mobile. O Intune também ajuda a proteger os dados e as aplicações da empresa. Pode utilizar o Intune individualmente ou pode integrá-lo no System Center Configuration Manager para expandir as funcionalidades de gestão.

A Microsoft oferece o benefício de Integração do Intune para serviços qualificáveis nos planos elegíveis. O benefício de Integração permite-lhe trabalhar remotamente com especialistas da Microsoft no sentido de estabelecer um ambiente do Intune pronto a ser usado. Para mais informações sobre o benefício de Integração, consulte [Descrição do Benefício de Integração do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=619281).

Pode começar a utilizar o Intune com uma avaliação gratuita de 30 dias que inclui 100 licenças de utilizador. Para começar a sua avaliação gratuita, [aceda à página de Inscrição do Intune](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/). Se a sua organização tiver um Contrato Enterprise ou contrato de licenciamento em volume equivalente, contacte o seu representante da Microsoft para configurar a sua avaliação gratuita.

> [!NOTE]
> Se a sua organização tiver uma conta escolar ou profissional do Microsoft Online Services e quiser continuar com esta subscrição do Intune em funcionamento após terminar o período de avaliação, selecione a opção **Iniciar sessão** nessa página e autentique-se através da conta de Administrador Global da sua empresa. Esta ação irá assegurar que a sua avaliação do Intune se liga à sua conta escolar ou profissional existente.

Para obter uma lista de definições que pode configurar nos dispositivos móveis, consulte:

-   [Funcionalidades de gestão de dispositivos inscritos do Microsoft Intune](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune)

-   [Gestão de dispositivos móveis híbridos (MDM) com o System Center Configuration Manager e o Microsoft Intune](https://technet.microsoft.com/library/mt627883.aspx)

Para mais informações sobre o System Center Configuration Manager, consulte [Documentação do System Center Configuration Manager](https://technet.microsoft.com/library/mt346023.aspx).

## <a name="learn-how-intune-service-updates-affect-you"></a>Saiba como as atualizações do serviço do Intune o afetam
Uma vez que o Intune é um serviço online, a Microsoft pode atualizá-lo regularmente.

Utilize as informações deste artigo para o ajudar a compreender a frequência destas atualizações de serviço e a notificação antecipada que lhe damos quando uma atualização pode afetar a utilização do serviço.

Para saber mais sobre as alterações no serviço Intune, consulte [Novidades do Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune). O [Blogue do Microsoft Intune](http://blogs.technet.com/b/microsoftintune/) também descreve as alterações no serviço e fornece sugestões úteis para o ajudar a tirar o máximo partido do Intune.

As atualizações de serviço importantes também lhe serão comunicadas no Centro de Mensagens do [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx). Se instalar o complemento [aplicação móvel Office 365 Admin](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a), pode receber notificações no seu dispositivo móvel.

> [!NOTE]
> Pode monitorizar o estado de funcionamento do serviço do Intune no [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx). Escolha **Estado de Funcionamento do Serviço** no painel esquerdo.  

Seguem-se os tipos de notificações que a Microsoft fornece sobre o serviço Intune:
-   Para ajudá-lo a planear as alterações do serviço, notificamo-lo pelo menos 30 a 90 dias antes da atualização de serviço, consoante o impacto da alteração. Isto irá acontecer através dos canais de comunicação no produto, como alertas do quadro. Estas alterações podem incluir:
    * Atualizações que podem ter impacto na conformidade ou regulamentação
    * Alterações à experiência de utilizador, interface de utilizador e fluxos de trabalho
    * APIs novas ou alteradas – Notificam que tem de testar para garantir a retrocompatibilidade de aplicações personalizadas
    * Alterações aos requisitos de sistema, por exemplo, a versão mínima do browser necessária
    * As atualizações que exijam uma ação para ativar a funcionalidade ou evitar a interrupção do serviço para a funcionalidade.
-   A Microsoft fornece informações sobre novas funcionalidades e melhoramentos às funcionalidades existentes na nossa atualização de serviço mensal. Geralmente, a Microsoft lança atualizações de serviço em meados de cada mês. As atualizações estão descritas em [Novidades do Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune).
    -   Em caso de extinção do serviço Intune, seria notificado com uma antecedência de 12 meses.

## <a name="choose-the-management-solution-thats-right-for-you"></a>Selecione a solução de gestão que mais se adequa à sua situação
Pode configurar o Intune de várias maneiras para gerir e ajudar a proteger os dispositivos móveis e os computadores da sua empresa (denominados **dispositivos** neste artigo).

-**Configuração autónoma do Intune.** Utilize a consola de administração baseada na Web no Intune para gerir dispositivos na sua organização. O Intune pode ser utilizado sem qualquer infraestrutura de TI no local. Se utilizar o Intune com o Active Directory Domain Services, pode utilizar as contas de utilizador de domínio que gere através dos Serviços de Domínio com o Intune.

-**Intune com o System Center Configuration Manager.** Utilize a consola de gestão do Configuration Manager para gerir computadores e dispositivos móveis na sua empresa. Esta configuração pode ajudá-lo a gerir todos os dispositivos da sua organização através de uma única consola, a Consola de Administração do Configuration Manager. O Configuration Manager suporta um elevado número de dispositivos móveis, servidores e computadores. Para obter mais informações sobre o Configuration Manager, consulte o artigo [Gestão híbrida de dispositivos móveis (MDM) com o System Center Configuration Manager e o Microsoft Intune](https://technet.microsoft.com/library/mt627883.aspx). Para obter mais ajuda para decidir qual é a melhor abordagem para si, consulte o artigo [Escolher entre o Microsoft Intune autónomo e a gestão híbrida de dispositivos móveis com o Configuration Manager](https://technet.microsoft.com/en-us/library/mt706478.aspx).


## <a name="learn-more-about-intune"></a>Saber mais sobre o Intune
Utilize estes recursos para obter mais informações sobre o Intune:

- O [Centro de Fidedignidade do Microsoft Intune](http://www.microsoft.com/en-us/server-cloud/products/intune-trust-center/) fornece informações sobre as práticas de segurança, privacidade e conformidade do Intune e descreve algumas das certificações do Intune.

- [Funcionalidades de gestão de dispositivos inscritos do Microsoft Intune](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune)

### <a name="see-also"></a>Consulte também
[Microsoft Intune](https://docs.microsoft.com/intune/)
[Biblioteca de Documentação do System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx)

[Novidades do Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune)



<!--HONumber=Dec16_HO3-->


