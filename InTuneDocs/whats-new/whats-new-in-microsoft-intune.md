---
title: Novidades | Documentos da Microsoft
description: "Saiba quais são as novidades deste mês e as versões anteriores do Microsoft Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 053cf0a1b5d06496397b36cbd1a7ebdce420fed3
ms.openlocfilehash: 5158d58c32066ea720335a878fef87451542c195


---
# <a name="whats-new-in-microsoft-intune---january-2017"></a>Novidades no Microsoft Intune – Janeiro de 2017
Saiba quais são as novidades nesta versão do Microsoft Intune. Pode também descobrir quais são as alterações futuras que deve planear, bem como informações sobre versões anteriores.

> [!Note]
> Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Novas Funcionalidades

<!--### Actions for non-compliance <!--730266
_Actions for non-compliance_ is a new feature of compliance policies that lets you take action on devices that are out of compliance. You can specify single or multiple actions and specify the time period at which those actions must occur. For example, you can notify users of non-compliant devices immediately after the devices become non-compliant through email, or you can block non-compliant devices from accessing corporate resources after a 3-day grace period via Conditional Access.-->

### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>Relatórios na consola para MAM sem inscrição <!--677961-->
Foram adicionados novos relatórios de proteção de aplicações para dispositivos inscritos e não inscritos. Saiba mais sobre como [monitorizar políticas de gestão de aplicações móveis com o Intune aqui](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune).

<!--### Conditional access for MAM with SharePoint Online <!--679339
You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint Online.  You can get started using Intune mobile app management in the Azure portal. Look for the __Conditional Access__ section in the __Settings__ blade which will include the option for SharePoint Online. This feature will ship separately from the rest of the service release. <!--Find out more about this new feature [here](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="android-711-support---694397--"></a>Suporte para Android 7.1.1 <!--694397-->
Agora, o Intune suporta e gere totalmente o Android 7.1.1.

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>Resolver o problema no qual os dispositivos iOS estão inativos ou a consola de administração não consegue comunicar com os mesmos <!--unknown-->
Quando os dispositivos dos utilizadores perdem o contacto com o Intune, pode dar-lhes novos passos de resolução de problemas que os ajudem a recuperar o acesso aos recursos da empresa. Consulte [Os dispositivos estão inativos ou a consola de administração não consegue comunicar com os mesmos](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

## <a name="notices"></a>Avisos

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Utilizar a predefinição para gerir computadores Windows através das definições do Windows<!--663050-->
O comportamento predefinido de inscrição de computadores com Windows 10 irá mudar. As novas inscrições seguirão o fluxo de inscrição do agente MDM normal, em vez de através do agente de PC.

O site do Portal da Empresa irá fornecer aos utilizadores de computadores com Windows 10 instruções para ajudá-los durante o processo de adicionar computadores com Windows 10 como dispositivos móveis. Isto não afetará os PCs atualmente inscritos e a sua organização pode continuar a gerir os computadores com Windows 10 através do agente de PC, [se preferir](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

<!--### Company Portal for iOS links open inside the app <!--665954
Links inside of the Company Portal app for iOS, including those to documentation and apps, will open directly in the Company Portal app using an in-app view of Safari. This update will ship separately from the service update in January.-->

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Melhorar o suporte de gestão de aplicações móveis para eliminação seletiva <!--581242-->
Os utilizadores finais receberão orientações adicionais sobre como recuperar o acesso a dados escolares ou profissionais se esses dados forem automaticamente removidos devido à política "Intervalo offline antes de os dados da aplicação serem apagados".<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>As ligações do Portal da Empresa para iOS são abertas dentro da aplicação <!--665954-->
As ligações na aplicação Portal da Empresa para iOS, incluindo as referentes a documentação e aplicações, serão abertas diretamente na aplicação Portal da Empresa através de uma vista do Safari na aplicação. Esta atualização será fornecida separadamente da atualização do serviço em janeiro.

### <a name="modernizing-the-company-portal-website---753980--"></a>Modernizar o site do Portal da Empresa <!--753980-->
A partir de fevereiro, o site do Portal da Empresa irá suportar aplicações visadas para utilizadores que não têm dispositivos geridos. O site ficará alinhado com outros serviços e produtos da Microsoft ao utilizar um novo esquema de cores de contraste, ilustrações dinâmicas e um menu de opções, ![menu de opções do site do Portal da Empresa](./media/CP_hamburger_menu.png) que irá conter detalhes e informações de contacto de suporte técnico nos dispositivos geridos existentes. A página de destino será reorganizada de forma a realçar as aplicações que estão disponíveis para os utilizadores, com carrosséis para aplicações Em Destaque e Recentemente Atualizadas. Poderá encontrar imagens do aspeto antes e depois da alteração na [página Novidades na IU da Aplicação Intune](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui#January_2017).

### <a name="new-documentation-for-app-protection-policies---583398--"></a>Nova documentação para políticas de proteção de aplicações <!--583398-->
Atualizámos a nossa documentação para administradores e programadores de aplicações que querem ativar políticas de proteção de aplicações (conhecidas como políticas MAM) nas respetivas aplicações iOS e Android através da Ferramenta de Encapsulamento de Aplicações do Intune ou do SDK da Aplicação Intune.

Foram atualizados os seguintes artigos:

* [Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [Preparar as aplicações iOS para gestão de aplicações móveis com a Ferramenta de Encapsulamento de Aplicações do Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [Introdução ao SDK da Aplicação Microsoft Intune](https://docs.microsoft.com/intune/develop/intune-app-sdk-get-started)
* [Guia para Programadores do SDK da Aplicação Intune para iOS](https://docs.microsoft.com/intune/develop/intune-app-sdk-ios)

Os seguintes artigos são novas adições à biblioteca de documentos:

* [Plugin Cordova do SDK da Aplicação Intune](https://docs.microsoft.com/intune/develop/intune-app-sdk-cordova)
* [Componente Xamarin do SDK da Aplicação Intune](https://docs.microsoft.com/intune/develop/intune-app-sdk-xamarin)

<!--### Progress bar when launching the Company Portal on iOS <!--665978
The Company Portal for iOS is introducing a progress bar on the launch screen to provide the user with information about the loading processes that occur. There will be a phased rollout of the progress bar to replace the spinner. This means that some of your users will see the new progress bar while others will continue to see the spinner.-->

### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>Barra de progresso ao iniciar o Portal da Empresa no iOS <!--665978-->
O Portal da Empresa para iOS passará a apresentar uma barra de progresso no ecrã inicial para fornecer ao utilizador informações sobre os processos de carregamento que ocorrem. É possível que haja uma implementação faseada da barra de progresso para substituir a animação giratória. Isto significa que alguns dos seus utilizadores verão a nova barra de progresso enquanto outros continuarão a ver a animação giratória.

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novidades na pré-visualização pública da experiência de administrador do Intune no Azure<!--736542-->

No início de 2017 iremos migrar toda a nossa experiência de administrador para o Azure, permitindo uma gestão poderosa e integrada de fluxos de trabalho de EMS principais numa plataforma de serviço moderna extensível com Graph API.

Os novos inquilinos de avaliação começarão a ver a pré-visualização pública da nova experiência de administrador no portal do Azure este mês. Enquanto estiverem no estado de pré-visualização, as capacidades e a paridade com a consola do Intune existente serão proporcionadas iterativamente.

A experiência de administração no portal do Azure irá utilizar a já anunciada nova funcionalidade de agrupamento e filtragem; quando o seu inquilino existente é migrado para a nova experiência de agrupamento, o utilizador também será migrado para pré-visualizar a nova experiência de administração do inquilino. Entretanto, se pretende testar ou observar qualquer uma das novas funcionalidades até que o seu inquilino seja migrado, inscreva-se para uma nova conta de avaliação do Intune ou veja a [nova documentação](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

Se tiver dúvidas sobre a linha cronológica para a migração do inquilino, contacte a nossa equipa de migração através do e-mail [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

Pode encontrar as novidades na pré-visualização do Intune no Azure [aqui](https://docs.microsoft.com/intune-azure/introduction/whats-new).

### <a name="see-also"></a>Veja também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novidades na pré-visualização do Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Novidades na IU do Portal da Empresa](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [Novidades – Arquivo](whats-new-archive.md)



<!--HONumber=Feb17_HO1-->


