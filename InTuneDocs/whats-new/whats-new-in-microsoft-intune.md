---
title: Novidades | Microsoft Intune
description: "Saiba quais são as novidades deste mês e as versões anteriores do Microsoft Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9fd309a10d9eb020795c5ce46df124b13dc1a006
ms.openlocfilehash: d117c929fbde4dd0a39503b8da695aa9c9ea91ad


---
# <a name="whats-new-in-microsoft-intune---december-2016"></a>Novidades no Microsoft Intune – Dezembro de 2016
Saiba quais são as novidades nesta versão do Microsoft Intune. Pode também descobrir quais são as alterações futuras que deve planear, bem como informações sobre versões anteriores.

> [!Note]
> Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure--736542--"></a>Pré-visualização pública da nova experiência de administrador do Intune no Azure<!--736542-->
No início de 2017 iremos migrar toda a nossa experiência de administrador para o Azure, permitindo uma gestão poderosa e integrada de fluxos de trabalho de EMS principais numa plataforma de serviço moderna extensível com Graph APIs. Antes da disponibilidade geral deste portal para todos os inquilinos do Intune, estamos entusiasmados por anunciar que iremos começar a lançar uma pré-visualização desta nova experiência de administração ainda este mês para selecionar os inquilinos.

A experiência de administração no portal do Azure irá utilizar a já anunciada nova funcionalidade de agrupamento e filtragem; quando o seu inquilino existente é migrado para a nova experiência de agrupamento, o utilizador também será migrado para pré-visualizar a nova experiência de administração do inquilino. Entretanto, pode obter mais informações sobre o que temos reservado para o Microsoft Intune no portal do Azure na nossa [nova documentação](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

Se tiver dúvidas sobre a linha cronológica para a migração do inquilino, contacte a nossa equipa de migração através do e-mail [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integração da gestão de despesas de telecomunicações na pré-visualização pública do portal do Azure<!--747605-->
Estamos agora a começar a pré-visualizar a integração com os serviços de gestão de despesas de telecomunicações (TEM) de terceiros no portal do Azure. Pode utilizar o Intune para impor limites de utilização de dados nacionais e itinerantes. Estamos a começar essas integrações com [Saaswedo](http://www.saaswedo.com).

## <a name="new-capabilities"></a>Novas Funcionalidades

### <a name="multi-factor-authentication-across-all-platforms---747590--"></a>Autenticação multifator em todas as plataformas <!--747590-->
Agora pode impor a autenticação multifator (MFA) num grupo selecionado de utilizadores quando estes inscrevem um dispositivo iOS, Android, Windows 8.1+ ou Windows Phone 8.1+ a partir do Portal de Gestão do Azure ao configurar a MFA na aplicação de Inscrição do Microsoft Intune no Azure Active Directory.

<!--VSO 679339, awaiting chrisgre for go-live--><!--### Conditional access for MAM with SharePoint Online
Pode bloquear o acesso ao SharePoint Online de aplicações não suportadas pelas políticas de gestão de aplicações móveis (MAM) do Intune.  Pode começar a utilizar a gestão de aplicações móveis do Intune no portal do Azure. Procure a secção __Acesso Condicional__ no painel __Definições__, que incluirá a opção para o SharePoint Online. Esta funcionalidade será enviada separadamente do restante serviço. Saiba mais sobre esta nova funcionalidade [aqui](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="ability-to-restrict-mobile-device-enrollment--747596--"></a>Capacidade para restringir a inscrição de dispositivos móveis<!--747596-->
O Intune está a adicionar novas restrições de inscrição que controlam as plataformas de dispositivos móveis autorizadas a inscrever. O Intune separa plataformas de dispositivos móveis como iOS, macOS, Android, Windows e Windows Mobile.
* A restrição da inscrição de dispositivos móveis não restringe a inscrição do cliente de PC.
* Especificamente para iOS, existe uma opção adicional para bloquear a inscrição de dispositivos pessoais.

O Intune marca todos os novos dispositivos como pessoais, a menos que o administrador de TI os marque como pertencentes à empresa, conforme explicado [neste artigo](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).


## <a name="notices"></a>Avisos

### <a name="multi-factor-authentication-on-enrollment-moving-to-the-azure-portal---vso-750545--"></a>Multi-Factor Authentication na Inscrição ao mover para o portal do Azure <!--VSO 750545-->
Anteriormente, os administradores utilizariam a consola do Intune ou a consola do Gestor de Configuração (anterior à versão de outubro 2016) para configurar a MFA para inscrições no Intune. Com esta funcionalidade atualizada, irá agora iniciar a sessão no [portal do Microsoft Azure](https://manage.windowsazure.com) com as suas credenciais do Intune e configurar as definições da MFA através do Azure AD. Saiba mais sobre o assunto [aqui](https://aka.ms/mfa_ad).

### <a name="company-portal-app-for-android-now-available-in-china---vso-658093--"></a>Aplicação do Portal da Empresa para Android, agora disponível na China <!--VSO 658093-->
Estamos a disponibilizar a aplicação do Portal da Empresa para Android para transferência na China. Devido à ausência da Google Play Store na China, os dispositivos Android têm de obter aplicações a partir de mercados de aplicações chineses. A aplicação do Portal da Empresa para Android estará disponível para transferência através das seguintes lojas:
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

A aplicação do Portal da Empresa para Android utiliza os Serviços do Google Play para comunicar com o serviço Microsoft Intune. Uma vez que os Serviços do Google Play ainda não estão disponíveis na China, pode demorar até 8 horas a concluir a realização de qualquer uma das seguintes tarefas. 

|Consola de Administração do Intune| Aplicação do Portal da Empresa do Intune para Android |Site do Portal da Empresa do Intune|   
|---|---|---|
|Eliminação completa| Remover um dispositivo remoto| Remover dispositivo (local e remoto)|
|Eliminação seletiva| Repor dispositivo| Repor dispositivo|
|Implementações de aplicações novas ou atualizadas| Instalar aplicações de linha de negócio disponíveis| Repor código de acesso do dispositivo|
|Bloqueio remoto|||
|Repor código de acesso|||

## <a name="deprecations"></a>Depreciação

### <a name="firefox-to-no-longer-support-silverlight--vso-tba--"></a>O Firefox vai deixar de suportar o Silverlight<!--VSO TBA-->
A Mozilla vai remover o suporte do Silverlight na versão 52 do [browser Firefox](https://www.mozilla.org/firefox), a partir de março de 2017. Como resultado, já não será possível iniciar sessão na consola do Intune existente quando utilizar versões do Firefox superiores a 51. Recomendamos que utilize o Internet Explorer 10 ou 11 para aceder à consola de administração ou uma [versão do Firefox anterior à versão 52](https://ftp.mozilla.org/pub/firefox/releases/). A transição do Intune para o portal do Azure irá permitir suportar um número de [browsers modernos](https://docs.microsoft.com/en-us/azure/azure-preview-portal-supported-browsers-devices) sem dependência do Silverlight.

### <a name="removal-of-exchange-online-mobile-inbox-policies---770687--"></a>Remoção das políticas da pasta a receber móvel do Exchange Online <!--770687-->
A partir de dezembro, os administradores deixarão de ser capazes de ver ou configurar políticas de caixa de correio móvel do Exchange Online (EAS) na consola do Intune. Esta alteração vai ser implementada em todos os inquilinos do Intune entre dezembro e janeiro. Todas as políticas existentes permanecerão tal como configuradas. Para configurar novas políticas, utilize a Shell de Gestão do Exchange. Saiba mais informações [aqui](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx).

### <a name="intune-av-player-image-viewer-and-pdf-viewer-apps-are-no-longer-supported-on-android---747553--"></a>As aplicações Leitor do Intune AV, Visualizador de Imagens e o Visualizador de PDFs já não são suportadas nos sistemas Android <!--747553-->
A partir de meados de dezembro de 2016, os utilizadores já não poderão utilizar as aplicações Leitor do Intune AV, Visualizador de Imagens e Visualizador de PDFs. Estas aplicações foram substituídas pela aplicação Azure Information Protection. Saiba mais sobre a aplicação Azure Information Protection [aqui](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq).

### <a name="see-also"></a>Consulte também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Versões anteriores do Intune](whats-new-archive.md)



<!--HONumber=Dec16_HO2-->


