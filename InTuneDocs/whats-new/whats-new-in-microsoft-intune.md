---
title: Novidades | Documentos da Microsoft
description: "Saiba quais são as novidades deste mês e as versões anteriores do Microsoft Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: a9336e3d230de962d2623dd627e45c6e9262a822
ms.openlocfilehash: cfe4a0bb802956278387ac2a39d5316482e09332
ms.lasthandoff: 03/02/2017


---
# <a name="whats-new-in-microsoft-intune---february-2017"></a>Novidades do Microsoft Intune – fevereiro de 2017
Saiba quais são as novidades nesta versão do Microsoft Intune. Pode também descobrir quais são as alterações futuras que deve planear, bem como informações sobre versões anteriores.

> [!Note]
> Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Novas Funcionalidades

### <a name="modernizing-the-company-portal-website---753980--"></a>Modernizar o site do Portal da Empresa <!--753980-->
O site do Portal da Empresa irá suportar aplicações visadas para utilizadores que não têm dispositivos geridos. O site será alinhado com outros produtos e serviços Microsoft através de um novo esquema de cores contrastante, ilustrações dinâmicas e um menu de opções, ![Pequena imagem do menu de opções adicionado ao canto superior esquerdo do site do Portal da Empresa](./media/CP_hamburger_menu.png) que irá conter os detalhes e informações de contacto do suporte técnico nos dispositivos geridos existentes. A página de destino será reorganizada de forma a realçar as aplicações que estão disponíveis para os utilizadores, com carrosséis para aplicações Em Destaque e Recentemente Atualizadas. Poderá encontrar imagens de antes e depois na [página de atualizações de IU](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Nova experiência orientada para o Portal da Empresa do Windows 10 <!--713927-->
A partir de março, o Portal da Empresa para Windows 10 vai incluir uma experiência de instruções orientada do Intune para dispositivos que não foram identificados ou inscritos. A nova experiência disponibiliza instruções passo a passo, personalizadas para a compilação do Windows 10 do utilizador, que orienta os utilizadores no processo de registo do AAD (obrigatório para a identificação nas funcionalidades de Acesso Condicional) e de inscrição MDM (obrigatória para as funcionalidades de gestão de dispositivos). A experiência orientada estará acessível na home page do Portal da Empresa e é opcional; os utilizadores poderão continuar a utilizar a aplicação se não concluírem o registo e a inscrição, mas podem terão funcionalidades limitadas.

## <a name="notices"></a>Avisos

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>A migração de grupos não irá necessitar de atualizações de grupos ou políticas para dispositivos iOS <!--898837-->
Para cada grupo de dispositivos do Intune previamente atribuído por um perfil de Inscrição de Dispositivos da Empresa, será criado um grupo de dispositivos dinâmicos correspondente no AAD com base no nome do perfil de Inscrição de Dispositivos da Empresa, durante a migração para os grupos de dispositivos do Azure Active Directory. Essa ação irá garantir que, à medida que os dispositivos forem inscritos, os mesmos serão agrupados automaticamente e receberão as mesmas políticas e aplicações que o grupo original do Intune.

Quando um inquilino iniciar o processo de migração para agrupamento e direcionamento, o Intune irá criar automaticamente um grupo dinâmico do AAD para corresponder a um grupo do Intune visado por um perfil de Inscrição de Dispositivos da Empresa. Se o Administrador do Intune eliminar o grupo visado do Intune, o grupo dinâmico do AAD correspondente não será eliminado. A consulta dinâmica e os membros do grupo serão desmarcados, mas o grupo em si permanecerá até o Administrador de TI o eliminar através do portal do AAD.

Do mesmo modo, se o Administrador de TI alterar o grupo do Intune visado por um perfil de Inscrição de Dispositivos da Empresa, o Intune irá criar um grupo dinâmico novo que reflita a nova atribuição de perfil, mas não irá eliminar o grupo dinâmico criado para a atribuição antiga.

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Utilizar a predefinição para gerir computadores Windows através das definições do Windows<!--663050-->
O comportamento predefinido de inscrição de computadores com Windows 10 irá mudar. As novas inscrições seguirão o fluxo de inscrição do agente MDM normal, em vez de através do agente de PC. O site do Portal da Empresa irá fornecer aos utilizadores de computadores com Windows 10 instruções para ajudá-los durante o processo de adicionar computadores com Windows 10 como dispositivos móveis. Isto não afetará os PCs atualmente inscritos e a sua organização pode continuar a gerir os computadores com Windows 10 através do agente de PC, [se preferir](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Melhorar o suporte de gestão de aplicações móveis para eliminação seletiva <!--581242-->
Os utilizadores finais receberão orientações adicionais sobre como recuperar o acesso a dados escolares ou profissionais se esses dados forem automaticamente removidos devido à política "Intervalo offline antes de os dados da aplicação serem apagados".<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>As ligações do Portal da Empresa para iOS são abertas dentro da aplicação <!--665954-->
As ligações na aplicação Portal da Empresa para iOS, incluindo as referentes a documentação e aplicações, serão abertas diretamente na aplicação Portal da Empresa através de uma vista do Safari na aplicação. Esta atualização será fornecida separadamente da atualização do serviço em janeiro.

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Novo endereço do servidor MDM para dispositivos Windows <!--893007-->
Os utilizadores do Windows e do Windows Phone não conseguirão inscrever um dispositivo se introduzirem __manage.microsoft.com__ como endereço do servidor MDM (se solicitado). O endereço do servidor MDM será alterado de __manage.microsoft.com__ para __enrollment.manage.microsoft.com__. Informe o seu utilizador para utilizar __enrollment.manage.microsoft.com__ como endereço do servidor MDM, se solicitado durante a inscrição de um dispositivo Windows ou Windows Phone. Não necessita de efetuar alterações à configuração do seu CNAME. Para obter mais informações sobre esta alteração, visite [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nova experiência de utilizador da aplicação Portal da Empresa para Android<!--621622-->
A partir de março, a aplicação Portal da Empresa para Android seguirá as [diretrizes de conceção do material](https://material.io/guidelines/material-design/introduction.html) para criar um aspeto e funcionalidade mais modernos. Esta experiência de utilizador melhorada inclui:

* __Cores__: os cabeçalhos dos separadores podem ser coloridos de acordo com a sua paleta de cores personalizada.
* __Interface__: os botões Aplicações em Destaque e Todas as Aplicações foram atualizados no separador Aplicações. O botão Procurar é agora um botão de ação flutuante.
* __Navegação__: a secção Todas as Aplicações mostra uma vista com os separadores Em destaque, Todas e Categorias para uma navegação mais fácil.
* __Serviço__: os separadores Os Meus Dispositivos e Contactar TI foram melhorados para facilitar a leitura.

Poderá encontrar imagens de antes e depois na [página de atualizações de IU](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>Associar várias ferramentas de gestão à Loja Windows para Empresas <!--926135-->
Se estiver a utilizar mais do que uma ferramenta de gestão para implementar aplicações da Loja Windows para Empresas, antes só podia associar uma destas com a Loja Windows para Empresas. Agora, pode associar várias ferramentas de gestão com a loja, como o Intune e o Configuration Manager. Para obter mais detalhes, veja [Gerir aplicações compradas na Loja Windows para Empresas com o Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune).

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novidades na pré-visualização pública da experiência de administrador do Intune no Azure<!--736542-->

No início de 2017 iremos migrar toda a nossa experiência de administrador para o Azure, permitindo uma gestão poderosa e integrada de fluxos de trabalho de EMS principais numa plataforma de serviço moderna extensível com Graph API.

Os novos inquilinos de avaliação começarão a ver a pré-visualização pública da nova experiência de administrador no portal do Azure este mês. Enquanto estiverem no estado de pré-visualização, as capacidades e a paridade com a consola do Intune existente serão proporcionadas iterativamente.

A experiência de administração no portal do Azure irá utilizar a já anunciada nova funcionalidade de agrupamento e filtragem; quando o seu inquilino existente é migrado para a nova experiência de agrupamento, o utilizador também será migrado para pré-visualizar a nova experiência de administração do inquilino. Entretanto, se pretende testar ou observar qualquer uma das novas funcionalidades até que o seu inquilino seja migrado, inscreva-se para uma nova conta de avaliação do Intune ou veja a [nova documentação](https://docs.microsoft.com/intune-azure/introduction/whats-new).

Se tiver dúvidas sobre a linha cronológica para a migração do inquilino, contacte a nossa equipa de migração através do e-mail [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

Pode encontrar as novidades na pré-visualização do Intune no Azure [aqui](https://docs.microsoft.com/intune-azure/introduction/whats-new).

## <a name="whats-coming"></a>Novidades futuras

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>A Apple passará a exigir atualizações para a Segurança de Transporte de Aplicações <!--748318-->

A partir da primavera de 2017, a Apple anunciou que irá impor requisitos específicos para a Segurança de Transporte de Aplicações (ATS). A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Esta alteração irá afetar os clientes do Intune que utilizam as aplicações do Portal da Empresa para iOS. Consulte o nosso [blogue de suporte do Intune](https://aka.ms/compportalats) para obter mais detalhes. 

### <a name="see-also"></a>Veja também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novidades na pré-visualização do Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Novidades na IU do Portal da Empresa](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [Novidades – Arquivo](whats-new-archive.md)

