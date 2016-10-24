---
title: Novidades | Microsoft Intune
description: "Saiba quais são as novidades deste mês e as versões anteriores do Microsoft Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 503719953031bf5079b2bf5bc84a0497d708f79a
ms.openlocfilehash: 730809e0841a248b90f5fe157f2c6338bfd32b2d


---
# Novidades no Microsoft Intune – Outubro de 2016
Saiba quais são as novidades nesta versão do Microsoft Intune. Pode também descobrir quais são as alterações futuras que deve planear, bem como informações sobre versões anteriores.

Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Novidades nas Implementações Híbridas](https://technet.microsoft.com/library/mt718155.aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

## Novidades

### Acesso condicional para a gestão de aplicações móveis
Poderá restringir o acesso ao Exchange Online de modo a permitir o acesso apenas a partir de aplicações que suportam as políticas de gestão de aplicações móveis do Intune, como o Outlook. [Esta nova funcionalidade](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) é totalmente compatível com as políticas de gestão de aplicações móveis do Intune (MAM), uma vez que pode bloquear o acesso a clientes de e-mail incorporados ou a outras aplicações que não tenham sido configuradas com as políticas de MAM do Intune. Isto garante que os seus utilizadores acedem aos dados da sua organização através de aplicações que podem ser protegidas pelos serviços de MAM do Intune. Pode começar a utilizar a gestão de aplicações móveis do Intune através do portal do Azure. Localize a nova secção Acesso Condicional no painel "Definições".

### Acesso condicional para PCs Windows
Agora pode criar políticas de acesso condicional através da consola de administração do Intune para bloquear o acesso de PCs Windows ao [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) e ao [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune). Também pode criar políticas de acesso condicional para bloquear o acesso a aplicações universais e de ambiente de trabalho do Office.

### Suporte do Android for Work
O Intune faz agora parte do programa Android for Work. Iremos começar a implementar suporte para as funcionalidades do Android for Work no Intune a partir deste mês.
[Leia o anúncio da Microsoft sobre o suporte do Intune para o Android for Work](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/).

Os seguintes tópicos do Intune são novos ou foram atualizados com informações do Android for Work:

Para profissionais de TI:
- [Configurar o Android for Work](/intune/deploy-use/set-up-android-for-work)
<!--- [Nathan Bigman's resource access topics]()-->
- [Restringir o acesso ao e-mail no Exchange Online e no novo Exchange Online Dedicado com o Intune](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [Restringir o acesso ao e-mail no Exchange no local e no Exchange Online Dedicado legado com o Intune](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Definições de política de conformidade do Android for Work](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [Como implementar aplicações do Android for Work](/intune/deploy-use/android-for-work-apps)
- [Configurar as aplicações do Android for Work com as políticas de configuração de aplicações móveis](/intune/deploy-use/afw-app-configuration-policy)
- [Definições de política do Android for Work](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

Para utilizadores finais:
- [O que acontece quando cria um perfil de trabalho](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [Criar um perfil de trabalho e inscrever o seu dispositivo no Intune](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### Integração com a Lookout para a proteção de dispositivos iOS
Em outubro, a Microsoft está a integrar a solução de proteção da Lookout contra ameaças que afetam dispositivos móveis para proteger dispositivos móveis iOS através da deteção de software maligno, aplicações de risco e muito mais. A solução da Lookout ajuda-o a determinar o nível da ameaça, que é configurável. Pode criar uma regra de política de conformidade no Intune para determinar a conformidade dos dispositivos com base na avaliação de riscos feita pela Lookout. Ao utilizar políticas de acesso condicional, pode permitir ou bloquear o acesso a recursos da sua empresa com base no estado de conformidade do dispositivo.

Os utilizadores finais de dispositivos em não conformidade iOS receberão um pedido para os inscrever e terão de instalar a aplicação Lookout for Work nos seus dispositivos, ativar a aplicação e corrigir as ameaças comunicadas na mesma para obterem acesso aos dados da empresa. Saiba como [Configurar e implementar as aplicações do Lookout for Work](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps).
<!--TFS 1319493-->

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

### Ferramenta de Encapsulamento de Aplicações do Intune para Android
Pode utilizar a Ferramenta de Encapsulamento de Aplicações do Intune para ativar as suas aplicações para que utilizem políticas de gestão de aplicações móveis do Intune (MAM). O suporte para políticas de MAM do Intune sem necessidade de inscrição de dispositivos está agora disponível.

### Gerir a impressão a partir de aplicações geridas através de políticas de MAM
Já pode evitar a impressão de dados da empresa a partir de aplicações com políticas de MDM. Esta definição está disponível no [Portal do Azure](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) e é suportada em dispositivos [iOS](/Intune/deploy-use/ios-mam-policy-settings) e [Android](/Intune/deploy-use/android-mam-policy-settings).
<!--TFS 1014328-->

## Avisos

### Compatibilidade do Android Samsung KNOX com o Intune
Determinados modelos do telemóvel Samsung Galaxy Ace não podem ser geridos pelo Intune como dispositivos Samsung KNOX. Ao inscrever estes dispositivos com o Intune, serão geridos como dispositivos Android padrão.

Os números dos modelos afetados são:

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

Não é necessária nenhuma ação adicional sua ou dos utilizadores finais. Para mais informações, visite o site do [Samsung KNOX](https://www.samsungknox.com).

### A aplicação Portal da Empresa para Windows 8 foi preterida; o suporte para as plataformas do Windows Phone 8 e do Windows RT está a ser preterido
A partir de outubro de 2016, o Microsoft Intune irá preterir o suporte para o Portal da Empresa do Windows Phone 8. O Microsoft Intune irá também preterir o suporte para a plataforma do Windows Phone 8 e do Windows RT. Como resultado, não será capaz de inscrever ou atualizar dispositivos Windows Phone 8 e Windows RT.

Pode continuar a gerir dispositivos Windows Phone 8, Windows RT e Windows 8 que já tenham sido inscritos. Atualize dispositivos Windows Phone 8 e Windows 8 para Windows Phone 8.1 e Windows 8.1, e utilize as aplicações do Portal da Empresa para Windows 8.1 e Windows Phone 8.1 correspondentes para continuar a distribuir aplicações para estes dispositivos, sem interrupções.

A partir de novembro de 2016, iremos preterir o suporte para o Portal da Empresa do Windows Phone 8.
<!--TFS 1255391-->

## Novidades futuras

### Novo Portal da Empresa do Microsoft Intune disponível para dispositivos com o Windows 10
A Microsoft está a lançar um novo Portal da Empresa do Microsoft Intune para dispositivos com o Windows 10. Esta aplicação, que tira partido do novo formato do Windows 10 Universal, irá oferecer ao utilizador uma experiência atualizada na aplicação e experiências idênticas em todos os dispositivos, PC e dispositivos móveis semelhantes com o Windows 10, permitindo que todos tenham a mesma funcionalidade atual.

A nova aplicação também irá permitir aos utilizadores tirarem partido de funcionalidades de plataforma adicionais, como o início de sessão único (SSO) e a autenticação baseada em certificados em dispositivos com o Windows 10. A aplicação será disponibilizada como uma atualização das instalações existentes do Portal da Empresa do Windows 8.1 e do Portal da Empresa do Windows Phone 8.1 a partir da Loja Windows. Para mais detalhes, aceda a [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).
<!--TFS 1016502-->

### Consulte também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Versões anteriores do Intune](previous-intune-releases.md)



<!--HONumber=Oct16_HO3-->


