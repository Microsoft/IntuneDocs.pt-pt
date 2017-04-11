---
title: Novidades | Documentos da Microsoft
description: "Saiba quais são as novidades deste mês e as versões anteriores do Microsoft Intune"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: c473a1f05b0a7b0ce5205598b2b9a9b86bfe6c1d
ms.openlocfilehash: bddd8c0dc74835f74a71af1d900d43d84aab894c
ms.lasthandoff: 03/29/2017


---
# <a name="whats-new-in-microsoft-intune---march-2017"></a>Novidades do Microsoft Intune – março de 2017
Saiba quais são as novidades nesta versão do Microsoft Intune. Pode também descobrir quais são as alterações futuras que deve planear, bem como informações sobre versões anteriores.

> [!Note]
> Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Novas Funcionalidades

### <a name="support-for-skycure"></a>Suporte para Skycure

Pode controlar o acesso a recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Skycure, uma solução de defesa contra ameaças para dispositivos móveis que está integrada com o Microsoft Intune. O risco é avaliado com base na telemetria recolhida dos dispositivos através do Skycure, incluindo:

- Defesa física
- Defesa da rede
- Defesa da aplicação
- Defesa contra vulnerabilidades

Pode configurar políticas de acesso condicional de EMS com base na avaliação de riscos do Skycure ativada através de políticas de conformidade de dispositivos do Intune. Pode utilizar estas políticas para permitir ou bloquear o acesso de dispositivos não conformes aos recursos empresariais com base em ameaças detetadas. Para obter mais informações, veja[Conector de Defesa Contra Ameaças para Dispositivos Móveis do Skycure](/intune/deploy-use/skycure-mobile-threat-defense-connector).

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nova experiência de utilizador da aplicação Portal da Empresa para Android<!--621622-->

A aplicação Portal da Empresa para Android irá atualizar a respetiva interface de utilizador para obter um aspeto mais moderno e a melhor experiência de utilizador. As atualizações relevantes são:

- Cores: os cabeçalhos dos separadores do Portal da Empresa têm as cores da imagem corporativa definida pelas TI.
- Aplicações: no separador **Aplicações**, os botões **Aplicações em Destaque** e **Todas as Aplicações** são atualizados.
- Pesquisar: no separador **Aplicações**, o botão **Pesquisar** é um botão de ação flutuante.
- Navegar em Aplicações: a vista **Todas as Aplicações** mostra uma vista com os separadores **Em Destaque**, **Todas** e **Categorias** para uma navegação mais fácil.
- Suporte: os separadores **Os Meus Dispositivos** e **Contactar TI** são atualizados para melhorar a legibilidade.

Para obter mais detalhes sobre estas alterações, veja [Atualização da IU para aplicações de utilizadores finais do Intune](whats-new-in-intune-app-ui.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Os dispositivos não geridos podem aceder a aplicações atribuídas <!--664691-->

Como parte das alterações de estrutura no site do Portal da Empresa, os utilizadores de iOS e Android poderão instalar aplicações atribuídas a eles próprios como "disponíveis sem inscrição" nos seus dispositivos não geridos. Com as suas credenciais do Intune, os utilizadores poderão iniciar sessão no site do Portal da Empresa e ver as listas de aplicações atribuídas a eles próprios. Os pacotes de aplicações das aplicações "disponíveis sem inscrição" estão disponíveis para transferência através do site do Portal da Empresa. As aplicações que requerem inscrição para instalação não são afetadas por esta alteração, uma vez que será solicitado aos utilizadores que inscrevam o seu dispositivo se quiserem instalar essas aplicações.

### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Script de Assinatura para o Portal da Empresa do Windows 10 <!--941642-->

Se precisar de transferir e de carregar em sideload a aplicação Portal da Empresa do Windows 10, poderá agora utilizar um script para simplificar e otimizar o processo de assinatura de aplicações para a sua organização.   Para transferir o script e as instruções para o utilizar, veja [Microsoft Intune Signing Script for Windows 10 Company Portal (Script de Assinatura do Microsoft Intune para o Portal da Empresa do Windows 10)](https://aka.ms/win10cpscript) na Galeria do TechNet. Para obter mais detalhes sobre este anúncio, veja [Updating your Windows 10 Company Portal app (Atualizar a aplicação do Portal da Empresa do Windows 10)](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) no Blogue da Equipa de Suporte do Intune.


## <a name="notices"></a>Avisos

### <a name="support-for-ios-103"></a>Suporte para iOS 10.3

A versão do iOS 10.3 começou a ser implementada a 27 de março de 2017 para os utilizadores de iOS. Todos os cenários MDM e MAM existentes do Intune são compatíveis com a versão mais recente do SO da Apple. Prevemos que todas as funcionalidades existentes do Intune atualmente disponíveis para gerir dispositivos iOS continuem a funcionar quando os utilizadores atualizarem os seus dispositivos e aplicações para o iOS 10.3.

Não existem atualmente problemas conhecidos para partilhar. Caso se depare com problemas com o iOS 10.3, contacte a [equipa de suporte do Intune](/intune/troubleshoot/contact-assisted-phone-support-for-microsoft-intune).

### <a name="improved-support-for-android-users-based-in-china---720444--"></a>Suporte melhorado para os utilizadores do Android sediados na China<!--720444-->

Devido à ausência da Google Play Store na China, os dispositivos Android têm de obter aplicações a partir de mercados chineses. O Portal da Empresa suportará este fluxo de trabalho ao redirecionar os utilizadores do Android na China para transferirem as aplicações Portal da Empresa e Outlook a partir de lojas de aplicações locais. Deste modo, irá melhorar a experiência do utilizador quando as políticas de Acesso Condicional são ativadas, tanto para a Gestão de Dispositivos Móveis como para a Gestão de Aplicações Móveis. As aplicações Portal da Empresa e Outlook para Android estão disponíveis nas seguintes lojas de aplicações chinesas:

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>Melhor prática: confirme se as aplicações do Portal da Empresa estão atualizadas <!--879465-->

Em dezembro de 2016, lançamos uma atualização que permitia a imposição da autenticação multifator (MFA) num grupo de utilizadores no momento da inscrição de um dispositivo iOS, Android, Windows 8.1 e superior ou Windows Phone 8.1 e superior. Esta funcionalidade não pode funcionar sem determinadas versões de linha de base da aplicação Portal da Empresa para Android (v5.0.3419.0+) e iOS (v2.1.17+).

A Microsoft está continuamente a melhorar o Intune ao adicionar novas funções à consola e às aplicações Portal da Empresa em todas as plataformas suportadas. Como resultado, a Microsoft apenas lança correções para problemas que encontramos na versão atual da aplicação Portal da Empresa. Como tal, recomendamos que utilize as versões mais recentes das aplicações Portal da Empresa para obter a melhor experiência de utilizador.

>[!Tip]
> Solicite aos seus utilizadores que configurem os dispositivos para atualizarem automaticamente as aplicações da loja de aplicações adequada. Se tiver disponibilizado a aplicação Portal da Empresa do Android numa partilha de rede, poderá transferir a versão mais recente a partir do [Centro de Transferências da Microsoft](https://www.microsoft.com/download/details.aspx?id=49140).

### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>O Microsoft Teams está agora ativado para a MAM no iOS e no Android

A Microsoft anunciou a disponibilidade geral do Microsoft Teams. As aplicações Microsoft Teams atualizadas para iOS e Android estão agora ativadas com capacidades de gestão de aplicações móveis (MAM) do Intune para permitir que as suas equipas trabalhem livremente em vários dispositivos, garantindo que as conversações e os dados empresariais estão sempre protegidos. Para obter mais detalhes, veja [o anúncio do Microsoft Teams](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) no blogue do Enterprise Mobility and Security.


## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novidades na pré-visualização pública da experiência de administrador do Intune no Azure<!--736542-->

No início de 2017 iremos migrar toda a nossa experiência de administrador para o Azure, permitindo uma gestão poderosa e integrada de fluxos de trabalho de EMS principais numa plataforma de serviço moderna extensível com Graph API.

Os novos inquilinos de avaliação começarão a ver a pré-visualização pública da nova experiência de administrador no portal do Azure este mês. Enquanto estiverem no estado de pré-visualização, as capacidades e a paridade com a consola do Intune existente serão proporcionadas iterativamente.

A experiência de administração no portal do Azure irá utilizar a já anunciada nova funcionalidade de agrupamento e filtragem; quando o seu inquilino existente é migrado para a nova experiência de agrupamento, o utilizador também será migrado para pré-visualizar a nova experiência de administração do inquilino. Entretanto, se pretende testar ou observar qualquer uma das novas funcionalidades até que o seu inquilino seja migrado, inscreva-se para uma nova conta de avaliação do Intune ou veja a [nova documentação](/intune-azure/introduction/whats-new).

> [!Note]
> Para a pré-visualização do portal do Azure, estamos a implementar as atualizações deste mês. No entanto, as alterações poderão não estar disponíveis imediatamente devido à forma como o serviço do Intune é implementado.  Vários componentes do serviço têm de ser atualizados sequencialmente antes de as novas funcionalidades do portal estarem disponíveis. Procure as alterações na pré-visualização do portal do Azure à medida que são implementadas durante este mês. Para obter a lista completa das alterações, veja [Novidades na pré-visualização do Microsoft Intune](/intune-azure/introduction/whats-new).

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Substituição das funções de administração no portal do Azure

As funções de administração de gestão de aplicações móveis (MAM) existentes (Contribuidor, Proprietário e Só de leitura) utilizadas no portal clássico do Intune (Silverlight) estão a ser substituídas por um conjunto completo de novos controlos de administração baseados em funções (RBAC) no portal do Azure no Intune. Após concluir a migração para o portal do Azure, terá de atribuir novamente os seus administradores a estas novas funções de administração. Para obter mais informações sobre as RBAC e as novas funções, veja [Controlo de acesso baseado em funções do Microsoft Intune](/intune-azure/access-control/role-based-access-control).


## <a name="whats-coming"></a>Novidades futuras

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>A Apple passará a exigir atualizações para a Segurança de Transporte de Aplicações <!--748318-->

A partir da primavera de 2017, a Apple anunciou que irá impor requisitos específicos para a Segurança de Transporte de Aplicações (ATS). A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Esta alteração irá afetar os clientes do Intune que utilizam as aplicações do Portal da Empresa para iOS. Consulte o nosso [blogue de suporte do Intune](https://aka.ms/compportalats) para obter mais detalhes.

### <a name="see-also"></a>Veja também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novidades na pré-visualização do Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Novidades na IU do Portal da Empresa](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [Novidades – Arquivo](whats-new-archive.md)

