---
# required metadata

title: Descrição do Serviço | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Descrição do serviço Microsoft Intune

O Microsoft Intune é um serviço baseado na nuvem que o ajuda a gerir PCs Windows e dispositivos móveis iOS, Mac OS X, Android e Windows. O Intune também ajuda a proteger os dados e as aplicações da empresa. Pode utilizar o Intune individualmente ou pode integrá-lo no System Center 2012 R2 Configuration Manager para expandir as capacidades de gestão.

A Microsoft oferece o benefício de Integração do Intune para serviços qualificáveis nos planos elegíveis. O benefício de Integração permite-lhe trabalhar remotamente com especialistas da Microsoft no sentido de estabelecer um ambiente do Intune pronto a ser usado. Para mais informações, consulte a [Descrição do Benefício de Integração do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=619281).

Pode começar a utilizar o Intune com uma avaliação gratuita de 30 dias que inclui 100 licenças de utilizador. Para iniciar a avaliação gratuita, [clique aqui para visitar a página de Inscrição do Intune](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/). Se a sua organização tiver um Enterprise Agreement ou contrato de licenciamento em volume equivalente, contacte o seu representante da Microsoft para configurar a sua avaliação gratuita.

> [!NOTE]
> Se a sua organização tiver uma conta escolar ou profissional do Microsoft Online Services e pretender continuar com esta subscrição do Intune em funcionamento após terminar o período de avaliação, clique na opção **Iniciar sessão** nessa página e autentique-se utilizando a conta de Administrador Global da sua empresa. Esta ação irá assegurar que a sua avaliação do Intune se liga à sua conta escolar ou profissional existente.

Para obter uma lista de definições que pode configurar nos seus dispositivos móveis, consulte:

-   [Funcionalidades de gestão de dispositivos móveis no Microsoft Intune](mobile-device-management-capabilities-in-microsoft-intune.md)

-   [Definições Gerais para Dispositivos Móveis no Configuration Manager](https://technet.microsoft.com/en-us/library/dn376523.aspx)

Para obter informações sobre o System Center 2012 R2 Configuration Manager, consulte [Biblioteca de Documentação do System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx).

## Compreender a forma como as atualizações do serviço Intune o afetam
Uma vez que o Intune é um serviço online, a Microsoft pode atualizá-lo regularmente.

Utilize as informações deste tópico para o ajudar a compreender a frequência destas atualizações de serviço e a notificação antecipada que lhe damos quando uma atualização possa afetar a utilização do serviço.

Para saber mais sobre as alterações no serviço Intune, consulte [Novidades do Microsoft Intune](/intune/deploy-use/Whats-new-in-microsoft-intune.md). O [Blogue do Microsoft Intune](http://blogs.technet.com/b/microsoftintune/) também descreve as alterações no serviço e fornece sugestões úteis para que obtenha o máximo partido do Intune.

As atualizações de serviço importantes também lhe serão comunicadas no Centro de Mensagens do [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx). Se instalar o complemento [aplicação móvel Office 365 Admin](https://support.office.com/en-us/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a), pode receber notificações no seu dispositivo móvel.

> [!NOTE] Pode monitorizar o estado de funcionamento do serviço do Intune no [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx). Escolha **Estado de Funcionamento do Serviço** no painel esquerdo.  

Seguem-se os tipos de notificações que a Microsoft fornece sobre o serviço Intune:
-   Para ajudá-lo a planear as alterações do serviço, notificamo-lo pelo menos 30 a 90 dias antes da atualização de serviço, consoante o impacto da alteração. Isto irá acontecer através dos canais de comunicação no produto, como alertas do quadro. Estas alterações podem incluir:
* Atualizações que podem ter impacto na conformidade ou regulamentação
* Alterações à experiência de utilizador, interface de utilizador e fluxos de trabalho
* APIs novas ou alteradas – Notificam que tem de testar para garantir a retrocompatibilidade de aplicações personalizadas
* Alterações aos requisitos de sistema, por exemplo, a versão mínima do browser necessária
* As atualizações que exijam uma ação para ativar a funcionalidade ou evitar a interrupção do serviço para a funcionalidade.
-   A Microsoft fornece informações sobre novas funcionalidades e melhoramentos às funcionalidades existentes na nossa atualização de serviço mensal. Geralmente, a Microsoft lança atualizações de serviço em meados de cada mês. As atualizações estão descritas em [Novidades do Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune.md).
-   Em caso de extinção do serviço Intune, seria notificado com uma antecedência de 12 meses.

## Selecione a solução de gestão que mais se adequa à sua situação
Pode configurar o Intune de várias maneiras para gerir e ajudar a proteger os dispositivos móveis e os computadores da sua empresa (denominados **dispositivos** neste documento).

-   **Configuração autónoma do Intune.** Utilize a consola de administração baseada na Web no Intune para gerir dispositivos na sua organização. O Intune pode ser utilizado sem qualquer infraestrutura de TI no local, mas se o utilizar com os Serviços de Domínio do Active Directory, pode utilizar contas de utilizador de domínio que administra com os Serviços de Domínio com o Intune.

-   **Intune com o System Center Configuration Manager.** Utilize a consola de gestão do Configuration Manager para gerir computadores e dispositivos móveis na sua empresa. Esta configuração pode ajudá-lo a gerir todos os dispositivos da sua organização através de uma única consola, a Consola de Administração do Configuration Manager. O Configuration Manager suporta um grande número de dispositivos móveis, servidores e computadores. Para mais informações, consulte [Como Gerir Dispositivos Móveis com o Configuration Manager e o Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=271118), na [Biblioteca de Documentação do System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx).  Para obter ajuda para decidir qual a melhor abordagem para si, consulte [Formas de gerir a mobilidade empresarial](/intune/plan-design/ways-to-do-enterprise-mobility.md)

-   Gestão de dispositivos móveis fornecida pelo Office 365, conforme descrito em [Formas de gerir a mobilidade empresarial](/intune/plan-design/ways-to-do-enterprise-mobility.md)

## Saber mais sobre o Intune
Utilize estes recursos para obter mais informações sobre o Intune:

-   O [Centro de Confiança do Microsoft Intune](http://www.microsoft.com/en-us/server-cloud/products/intune-trust-center/) fornece informações sobre as práticas de segurança, privacidade e conformidade do Intune, e descreve algumas das certificações do Intune.

-   [Funcionalidades de gestão de dispositivos móveis no Microsoft Intune](/intune/understand-explore/mobile-device-management-capabilities-in-microsoft-intune.md)

### Consulte também
[Microsoft Intune](https://docs.microsoft.com/intune/)
[Biblioteca de Documentação do System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx)

[Novidades do Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune.md)


<!--HONumber=May16_HO3-->


