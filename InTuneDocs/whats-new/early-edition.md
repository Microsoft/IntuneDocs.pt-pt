---
title: "A Edição Antecipada | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f287a0ad082fa20a2e84abbf8f5585117aae6f57
ms.openlocfilehash: e604b8809bd444d9069d449a6c691a8444296623


---

# <a name="the-early-edition-for-microsoft-intune---december"></a>A Edição Antecipada do Microsoft Intune – dezembro

O **Edição Antecipada** oferece uma lista de funcionalidades disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida ao abrigo de um contrato de confidencialidade numa base extremamente limitada e está sujeita a alterações. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu camarada do Intune/PM se tiver quaisquer dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

As seguintes alterações estão em desenvolvimento para o Intune. Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

<!--736542-->
## <a name="public-preview-of-the-new-intune-admin-experience-on-azure"></a>Pré-visualização pública da nova experiência de administrador do Intune no Azure

No início de 2017 iremos migrar toda a nossa experiência de administrador para o Azure, permitindo uma gestão poderosa e integrada de fluxos de trabalho de EMS principais numa plataforma de serviço moderna extensível com Graph API.

Os novos inquilinos de avaliação começarão a ver a pré-visualização pública da nova experiência de administrador no portal do Azure este mês. Enquanto estiverem no estado de pré-visualização, as capacidades e a paridade com a consola do Intune existente serão proporcionadas iterativamente.

A experiência de administração no portal do Azure irá utilizar a já anunciada nova funcionalidade de agrupamento e filtragem; quando o seu inquilino existente é migrado para a nova experiência de agrupamento, o utilizador também será migrado para pré-visualizar a nova experiência de administração do inquilino. Entretanto, se pretende testar ou observar qualquer uma das novas funcionalidades até que o seu inquilino seja migrado, inscreva-se para uma nova conta de avaliação do Intune ou veja a nova documentação.

Se tiver dúvidas sobre a linha cronológica para a migração do inquilino, contacte a nossa equipa de migração através do e-mail [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integração da gestão de despesas de telecomunicações na pré-visualização pública do portal do Azure<!--747605-->
Estamos agora a começar a pré-visualizar a integração com os serviços de gestão de despesas de telecomunicações (TEM) de terceiros no portal do Azure. Pode utilizar o Intune para impor limites de utilização de dados nacionais e itinerantes. Estamos a começar essas integrações com [Saaswedo](http://www.saaswedo.com).

## <a name="new-capabilities"></a>Novas Funcionalidades

### <a name="multi-factor-authentication-across-all-platforms---747590--"></a>Autenticação multifator em todas as plataformas <!--747590-->
Agora pode impor a autenticação multifator (MFA) num grupo selecionado de utilizadores quando estes inscrevem um dispositivo iOS, Android, Windows 8.1+ ou Windows Phone 8.1+ a partir do Portal de Gestão do Azure ao configurar a MFA na aplicação de Inscrição do Microsoft Intune no Azure Active Directory.

### <a name="conditional-access-for-mam-with-sharepoint-online---vso-679339--"></a>Acesso condicional para MAM com o SharePoint Online <!--VSO 679339-->
Pode bloquear o acesso ao SharePoint Online de aplicações não suportadas pelas políticas de gestão de aplicações móveis (MAM) do Intune.  Pode começar a utilizar a gestão de aplicações móveis do Intune no portal do Azure. Procure a secção __Acesso Condicional__ no painel __Definições__, que incluirá a opção para o SharePoint Online. Esta funcionalidade será enviada separadamente do restante serviço.

## <a name="notices"></a>Avisos

### <a name="multi-factor-authentication-on-enrollment-moving-to-the-azure-portal---vso-750545--"></a>Multi-Factor Authentication na Inscrição ao mover para o portal do Azure <!--VSO 750545-->
Anteriormente, os administradores utilizariam a consola do Intune ou a consola do Gestor de Configuração (anterior à versão 1610) para configurar a MFA para inscrições no Intune. Com esta funcionalidade atualizada, irá agora iniciar a sessão no [portal do Microsoft Azure](https://manage.windowsazure.com) com as suas credenciais do Intune e configurar as definições da MFA através do Azure AD. Saiba mais sobre o assunto [aqui](https://aka.ms/mfa_ad).

### <a name="company-portal-app-for-android-now-available-in-china---vso-658093--"></a>Aplicação do Portal da Empresa para Android, agora disponível na China <!--VSO 658093-->
Estamos a disponibilizar a aplicação do Portal da Empresa para Android para transferência na China. Devido à ausência da Google Play Store na China, os dispositivos Android têm de obter aplicações a partir de mercados de aplicações chineses. A aplicação do Portal da Empresa para Android estará disponível para transferência através da 360, Tencent, Xiaomi, Wandoujia e Huawei. 

A aplicação do Portal da Empresa para Android utiliza os Serviços do Google Play para comunicar com o serviço Microsoft Intune. Uma vez que os Serviços do Google Play ainda não estão disponíveis na China, pode demorar até 8 horas a concluir a realização de qualquer uma das seguintes tarefas. 

|Consola de Administração do Intune| Aplicação do Portal da Empresa do Intune para Android |Site do Portal da Empresa do Intune|   
|---|---|---|
|Eliminação completa| Remover um dispositivo remoto| Remover dispositivo (local e remoto)|
|Eliminação seletiva| Repor dispositivo| Repor dispositivo|
|Implementações de aplicações novas ou atualizadas| Instalar aplicações de linha de negócio disponíveis| Repor código de acesso do dispositivo|
|Bloqueio remoto|||
|Repor código de acesso|||

## <a name="deprecations"></a>Depreciação

### <a name="removal-of-exchange-online-mobile-inbox-policies---770687--"></a>Remoção das políticas da pasta a receber móvel do Exchange Online <!--770687-->
A partir de dezembro, os administradores deixarão de ser capazes de ver ou configurar políticas de caixa de correio móvel do Exchange Online (EAS) na consola do Intune. Esta alteração vai ser implementada em todos os inquilinos do Intune entre dezembro e janeiro. Todas as políticas existentes permanecerão tal como configuradas. Para configurar novas políticas, utilize a Shell de Gestão do Exchange. Saiba mais informações [aqui](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx).

### <a name="intune-av-player-image-viewer-and-pdf-viewer-apps-are-no-longer-supported-on-android---747553--"></a>As aplicações Leitor do Intune AV, Visualizador de Imagens e o Visualizador de PDFs já não são suportadas nos sistemas Android <!--747553-->
A partir de meados de dezembro de 2016, os utilizadores já não poderão utilizar as aplicações Leitor do Intune AV, Visualizador de Imagens e Visualizador de PDFs. Estas aplicações foram substituídas pela aplicação Azure Information Protection. Saiba mais sobre a aplicação Azure Information Protection [aqui](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq).

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new-in-microsoft-intune.md) para obter detalhes sobre os desenvolvimentos recentes.



<!--HONumber=Nov16_HO4-->


