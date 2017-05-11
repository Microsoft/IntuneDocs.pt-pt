---
title: Novidades | Documentos da Microsoft
description: "Saiba quais são as novidades deste mês e as versões anteriores do Microsoft Intune"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: a9748a0ad6b9bbe10e36ba133ba74edb6aa6e09a
ms.openlocfilehash: ed51f7ff7b6fd5a3234eb699234c6ad5fb3bdbc2
ms.contentlocale: pt-pt
ms.lasthandoff: 05/05/2017


---
# <a name="whats-new-in-microsoft-intune---april-2017"></a>Novidades do Microsoft Intune – abril de 2017
Saiba quais são as novidades nesta versão do Microsoft Intune. Pode também descobrir quais são as alterações futuras que deve planear, bem como informações sobre versões anteriores.

> [!Note]
> Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Novas funcionalidades

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>My Apps disponível para o Managed Browser <!--822308, 822303-->

O Microsoft My Apps agora tem melhor suporte no Managed Browser. Os utilizadores do Managed Browser que não forem geridos poderão aceder diretamente ao serviço My Apps e às aplicações SaaS aprovisionadas pelo administrador. Os utilizadores geridos através do Intune poderão continuar a aceder ao My Apps a partir do marcador incorporado no Managed Browser.

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Novos ícones para o Managed Browser e o Portal da Empresa <!--918433, 918431, 971473-->

O Managed Browser receberá ícones atualizados nas versões para Android e iOS da aplicação. O novo ícone incluirá o emblema do Intune atualizado para o tornar mais consistente com as outras aplicações no Enterprise Mobility + Security (EM+S). Pode ver o novo ícone do Managed Browser na [página Novidades na IU da aplicação Intune](whats-new-in-intune-app-ui.md).

O Portal da Empresa também receberá ícones atualizados para as versões para Android, iOS e Windows da aplicação para melhorar a consistência com as outras aplicações no EM+S. Estes ícones serão lançados gradualmente nas plataformas a partir de abril até finais de maio.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Indicador de progresso de início de sessão no Portal da Empresa para Android <!--953374-->

Uma atualização à aplicação Portal da Empresa para Android mostra um indicador de progresso de início de sessão quando o utilizador inicia ou retoma a aplicação. O indicador mostra novos estados de progresso, a começar com “A ligar...”, “A iniciar sessão...” e “A verificar os requisitos de segurança...” antes de o utilizador poder aceder à aplicação. Pode ver os novos ecrãs da aplicação Portal da Empresa para Android na [página Novidades na IU da aplicação Intune](whats-new-in-intune-app-ui.md).

### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>Impedir que as aplicações acedam ao SharePoint Online<!-- 679339 -->

Agora, pode criar uma política de acesso condicional com base na aplicação para impedir que as aplicações que não têm políticas de proteção aplicadas acedam ao [SharePoint Online](/InTune/deploy-use/mam-ca-for-sharepoint-online). No cenário de acesso condicional baseado em aplicações, pode especificar as aplicações que pretende que tenham acesso ao SharePoint Online através do portal do Azure.

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Suporte de início de sessão único a partir do Portal da Empresa para iOS para o Outlook para iOS <!--834012-->
Os utilizadores já não precisam de iniciar sessão na aplicação Outlook se já tiverem sessão iniciada no Portal da Empresa para iOS no mesmo dispositivo com a mesma conta. Quando os utilizadores iniciarem o Outlook, poderão selecionar a conta e iniciar sessão automaticamente. Também estamos a trabalhar no sentido de adicionar esta funcionalidade a outras aplicações da Microsoft.

### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>Mensagem de estado melhorada na aplicação Portal da Empresa para iOS <!--744866-->
Serão apresentadas novas mensagens mais específicas na aplicação Portal da Empresa para iOS para fornecer informações mais acessíveis sobre as ocorrências nos dispositivos. Estes erros eram anteriormente incluídos numa mensagem de erro geral que informava "O Portal da Empresa Está Temporariamente Indisponível". Além disso, se um utilizador iniciar o Portal da Empresa em iOS sem estar ligado à Internet, verá uma barra de estado persistente na home page a informar "Sem Ligação à Internet."

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Estado da instalação de aplicações melhorado para a aplicação Portal da Empresa do Windows 10 <!--676495-->

Os novos melhoramentos das instalações de aplicações iniciadas na aplicação do Portal da Empresa do Windows 10 incluem:
-    Relatórios mais rápidos do progresso da instalação para pacotes MSI
-    Relatórios mais rápidos do progresso da instalação para aplicações modernas em dispositivos com a Atualização de Aniversário do Windows 10 e versões superiores
-    Nova barra de progresso para as instalações de aplicações modernas em dispositivos com a Atualização de Aniversário do Windows 10 e versões superiores

Pode ver a nova barra de progresso na [página Novidades na IU da aplicação Intune](whats-new-in-intune-app-ui.md).

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Inscrever dispositivos Windows 10 em volume <!-- 747607 -->

Agora, pode juntar-se a um grande número de dispositivos que executam a atualização para Criativos do Windows 10 para o Azure Active Directory e o Intune com o Windows Configuration Designer (WCD). Para ativar a [inscrição na MDM em massa](/intune/deploy-use/bulk-enroll-windows) para o seu inquilino do Azure AD, crie um pacote de aprovisionamento que associe dispositivos ao seu inquilino do Azure AD através do Windows Configuration Designer e aplique o pacote aos dispositivos pertencentes à empresa que pretende inscrever e gerir em massa. Assim que o pacote for aplicado aos dispositivos, estes são associados ao Azure AD, inscritos no Intune e estarão prontos para os seus utilizadores do Azure AD iniciarem sessão.  Os utilizadores do Azure AD são utilizadores padrão nestes dispositivos e obtêm as políticas atribuídas e as aplicações necessárias. De momento, os cenários Self-service e Portal da Empresa não são suportados.

## <a name="notices"></a>Avisos

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acesso direto aos cenários de inscrição da Apple <!--951869-->

Para as contas do Intune criadas depois de janeiro de 2017, o Intune ativou o acesso direto aos cenários de inscrição da Apple através da carga de trabalho Inscrever Dispositivos no portal de pré-visualização do Azure. Anteriormente, a pré-visualização da inscrição da Apple apenas estava acessível a partir de ligações no portal do Intune clássico. As contas do Intune criadas antes de Janeiro de 2017 precisam de uma única migração antes de estas funcionalidades ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder à pré-visualização.

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Novidades futuras para Appx no Intune no Azure <!-- 1000270 -->

Como parte da migração do Intune para o Azure, estamos a efetuar três alterações a appx:

1. Adicionar um novo tipo de aplicação appx na consola clássica do Intune que só pode ser implementada em dispositivos inscritos em MDM.
2. Alterar o tipo de aplicação appx existente para apenas ser direcionada para PCs geridos através do agente do Intune para PC.
3. Converter todas as appxs existentes em appxs de MDM com a migração.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?

Não irá afetar as suas implementações existentes em dispositivos geridos através do agente do Intune para PC. No entanto, após a migração, não poderá implementar appxs migradas em novos dispositivos geridos através do agente do Intune para PC que não tenham sido abrangidas anteriormente.

#### <a name="what-action-do-i-need-to-take"></a>Que medidas tenho de tomar

Após a migração, terá de voltar a carregar a appx como uma appx para PC, se quiser efetuar novas implementações em PC. Para saber mais, veja [Appx changes in Intune on Azure (Alterações a appx no Intune no Azure)](https://aka.ms/appxchange) no blogue da Equipa de Suporte do Intune.  

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novidades na pré-visualização pública da experiência de administrador do Intune no Azure<!--736542-->

No início de 2017 iremos migrar toda a nossa experiência de administrador para o Azure, permitindo uma gestão poderosa e integrada de fluxos de trabalho de EMS principais numa plataforma de serviço moderna extensível com Graph API.

Os novos inquilinos de avaliação começarão a ver a pré-visualização pública da nova experiência de administrador no portal do Azure este mês. Enquanto estiverem no estado de pré-visualização, as capacidades e a paridade com a consola do Intune existente serão proporcionadas iterativamente.

A experiência de administração no portal do Azure irá utilizar a já anunciada nova funcionalidade de agrupamento e filtragem; quando o seu inquilino existente é migrado para a nova experiência de agrupamento, o utilizador também será migrado para pré-visualizar a nova experiência de administração do inquilino. Entretanto, se pretende testar ou observar qualquer uma das novas funcionalidades até que o seu inquilino seja migrado, inscreva-se para uma nova conta de avaliação do Intune ou veja a [nova documentação](/intune-azure/introduction/whats-new).

> [!Note]
> Para a pré-visualização do portal do Azure, estamos a implementar as atualizações deste mês. No entanto, as alterações poderão não estar disponíveis imediatamente devido à forma como o serviço do Intune é implementado.  Vários componentes do serviço têm de ser atualizados sequencialmente antes de as novas funcionalidades do portal estarem disponíveis. Procure as alterações na pré-visualização do portal do Azure à medida que são implementadas durante este mês. Para obter a lista completa das alterações, veja [Novidades na pré-visualização do Microsoft Intune](/intune-azure/introduction/whats-new).

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Substituição das funções de administração no portal do Azure

As funções de administração de gestão de aplicações móveis (MAM) existentes (Contribuidor, Proprietário e Só de leitura) utilizadas no portal clássico do Intune (Silverlight) estão a ser substituídas por um conjunto completo de novos controlos de administração baseados em funções (RBAC) no portal do Azure no Intune. Após concluir a migração para o portal do Azure, terá de atribuir novamente os seus administradores a estas novas funções de administração. Para obter mais informações sobre as RBAC e as novas funções, veja [Controlo de acesso baseado em funções do Microsoft Intune](/intune-azure/access-control/role-based-access-control).

## <a name="whats-coming"></a>Novidades futuras

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Experiência de início de sessão melhorada nas aplicações Portal da Empresa para todas as plataformas<!--User Story 1132123-->

Anunciamos uma alteração que ficará disponível nos próximos meses e irá melhorar a experiência de início de sessão nas aplicações do Portal da Empresa do Intune para Android, iOS e Windows. A nova experiência de utilizador será apresentada automaticamente em todas as plataformas da aplicação Portal da Empresa quando o Azure AD fizer esta alteração. Além disso, os utilizadores podem agora iniciar sessão no Portal da Empresa a partir de outro dispositivo com um código gerado, de utilização única. Tal é especialmente útil nos casos em que os utilizadores precisam de iniciar sessão sem credenciais.

Pode encontrar capturas de ecrã da experiência de início de sessão anterior, a nova experiência de início de sessão com credenciais e a experiência de início de sessão a partir de outro dispositivo na página [Novidades na IU da aplicação](whats-new-in-intune-app-ui.md).

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Planear a alteração: o Intune vai alterar a experiência do Portal de Parceiros do Intune <!-- 1050016 -->

A partir da atualização de serviço que se realizará em meados de maio de 2017, iremos remover a página Parceiro do Intune de manage.microsoft.com.  

Se for um administrador parceiro, já não poderá ver e agir em nome dos clientes a partir da página Parceiro do Intune. Em vez disso, terá de iniciar sessão num dos dois outros portais de parceiro da Microsoft.

Poderá iniciar sessão nas contas de cliente que gere a partir do [Centro de Parceiros da Microsoft](https://partnercenter.microsoft.com/) e do [Centro de Administração do Microsoft Office 365 para Parceiros](https://portal.office.com/). De futuro, utilize um destes sites para gerir os seus clientes.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>A Apple passará a exigir atualizações para a Segurança de Transporte de Aplicações <!--748318-->

A Apple anunciou que irá impor requisitos específicos para a Segurança de Transporte de Aplicações (ATS). A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Esta alteração irá afetar os clientes do Intune que utilizam as aplicações do Portal da Empresa para iOS.

Disponibilizamos uma versão da aplicação do Portal da Empresa para iOS através do programa TestFlight da Apple que impõe os novos requisitos da ATS. Se gostaria de a experimentar para testar a sua conformidade com a ATS, envie um e-mail para <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app"> CompanyPortalBeta@microsoft.com </a> com o seu nome próprio, apelido, endereço de e-mail e o nome da empresa. Consulte o nosso [blogue de suporte do Intune](https://aka.ms/compportalats) para obter mais detalhes.

### <a name="see-also"></a>Veja também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novidades na pré-visualização do Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Novidades na IU do Portal da Empresa](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [Novidades – Arquivo](whats-new-archive.md)

