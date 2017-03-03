---
title: "Edição antecipada | Documentos da Microsoft"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d0b3a883bb307fb06cb8d16500798086f328314a
ms.openlocfilehash: eeebf8b6b3bc5c7c35386eb20c96097af1f6769c
ms.lasthandoff: 02/14/2017


---


# <a name="the-early-edition-for-microsoft-intune---february-2017"></a>Edição antecipada do Microsoft Intune – Fevereiro de 2017

O **Edição Antecipada** oferece uma lista de funcionalidades disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida ao abrigo de um contrato de confidencialidade numa base extremamente limitada e está sujeita a alterações. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu camarada do Intune/PM se tiver quaisquer dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

> [!Note]
> As seguintes alterações estão em desenvolvimento para o Intune. Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Novas Funcionalidades

### <a name="modernizing-the-company-portal-website---753980--"></a>Modernizar o site do Portal da Empresa <!--753980-->
A partir de fevereiro, o design do site do Portal da Empresa estará alinhado com o de outros produtos e serviços Microsoft através de um novo esquema de cores contrastante, ilustrações dinâmicas e de um "menu de opções" ![Pequena imagem do menu de opções adicionado ao canto superior esquerdo do site do Portal da Empresa](./media/CP_hamburger_menu.png), que irá conter os detalhes e informações de contacto do suporte técnico nos dispositivos geridos existentes. A página de destino será reorganizada de forma a realçar as aplicações que estão disponíveis para os utilizadores, com carrosséis para aplicações Em Destaque e Recentemente Atualizadas. Poderá encontrar imagens de antes e depois na [página de atualizações de IU](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Nova experiência orientada para o Portal da Empresa do Windows 10 <!--713927-->
A partir de março, o Portal da Empresa para Windows 10 vai incluir uma experiência de instruções orientada do Intune para dispositivos que não foram identificados ou inscritos. A nova experiência disponibiliza instruções passo a passo, personalizadas para a compilação do Windows 10 do utilizador, que orienta os utilizadores no processo de registo do AAD (obrigatório para a identificação nas funcionalidades de Acesso Condicional) e de inscrição MDM (obrigatória para as funcionalidades de gestão de dispositivos). A experiência orientada estará acessível na home page do Portal da Empresa e é opcional; os utilizadores poderão continuar a utilizar a aplicação se não concluírem o registo e a inscrição, mas podem terão funcionalidades limitadas.

###

## <a name="notices"></a>Avisos

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>A migração de grupos não irá necessitar de atualizações de grupos ou políticas para dispositivos iOS <!--898837-->
Para cada grupo de dispositivos do Intune previamente atribuído por um perfil de Inscrição de Dispositivos da Empresa, será criado um grupo de dispositivos dinâmicos correspondente no AAD com base no nome do perfil de Inscrição de Dispositivos da Empresa, durante a migração para os grupos de dispositivos do Azure Active Directory. Essa ação irá garantir que, à medida que os dispositivos forem inscritos, os mesmos serão agrupados automaticamente e receberão as mesmas políticas e aplicações que o grupo original do Intune.

Quando um inquilino iniciar o processo de migração para agrupamento e direcionamento, o Intune irá criar automaticamente um grupo dinâmico do AAD para corresponder a um grupo do Intune visado por um perfil de Inscrição de Dispositivos da Empresa. Se o Administrador do Intune eliminar o grupo visado do Intune, o grupo dinâmico do AAD correspondente não será eliminado. A consulta dinâmica e os membros do grupo serão desmarcados, mas o grupo em si permanecerá até o Administrador de TI o eliminar através do portal do AAD.

Do mesmo modo, se o Administrador de TI alterar o grupo do Intune visado por um perfil de Inscrição de Dispositivos da Empresa, o Intune irá criar um grupo dinâmico novo que reflita a nova atribuição de perfil, mas não irá eliminar o grupo dinâmico criado para a atribuição antiga.

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Novo endereço do servidor MDM para dispositivos Windows <!--893007-->
Os utilizadores do Windows e do Windows Phone não conseguirão inscrever um dispositivo se introduzirem __manage.microsoft.com__ como endereço do servidor MDM (se solicitado). O endereço do servidor MDM será alterado de __manage.microsoft.com__ para __enrollment.manage.microsoft.com__. Informe o seu utilizador para utilizar __enrollment.manage.microsoft.com__ como endereço do servidor MDM, se solicitado durante a inscrição de um dispositivo Windows ou Windows Phone. Esta atualização requer que qualquer CNAME no DNS que redirecione __EnterpriseEnrollment.contoso.com__ para __manage.microsoft.com__, seja substituído por um CNAME no DNS que redirecione __EnterpriseEnrollment.contoso.com__ para __EnterpriseEnrollment-s.manage.microsoft.com__. Para obter mais informações sobre esta alteração, visite [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nova experiência de utilizador da aplicação Portal da Empresa para Android<!--621622-->
A partir de março, a aplicação Portal da Empresa para Android seguirá as [diretrizes de conceção do material](https://material.io/guidelines/material-design/introduction.html) para criar um aspeto e funcionalidade mais modernos. Esta experiência de utilizador melhorada inclui:

* __Cores__: os cabeçalhos dos separadores podem ser coloridos de acordo com a sua paleta de cores personalizada.
* __Interface__: os botões Aplicações em Destaque e Todas as Aplicações foram atualizados no separador Aplicações. O botão Procurar é agora um botão de ação flutuante.
* __Navegação__: a secção Todas as Aplicações mostra uma vista com os separadores Em destaque, Todas e Categorias para uma navegação mais fácil.
* __Serviço__: os separadores Os Meus Dispositivos e Contactar TI foram melhorados para facilitar a leitura.

Poderá encontrar imagens de antes e depois na [página de atualizações de IU](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>Associar várias ferramentas de gestão à Loja Windows para Empresas <!--926135-->
Se estiver a utilizar mais do que uma ferramenta de gestão para implementar aplicações da Loja Windows para Empresas, antes só podia associar uma destas com a Loja Windows para Empresas. Agora, pode associar várias ferramentas de gestão com a loja, como o Intune e o Configuration Manager. Para obter mais detalhes, veja [Gerir aplicações compradas na Loja Windows para Empresas com o Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune).

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Pré-visualização pública da nova experiência de administrador do Intune no Azure <!--736542-->

No início de 2017 iremos migrar toda a nossa experiência de administrador para o Azure, permitindo uma gestão poderosa e integrada de fluxos de trabalho de EMS principais numa plataforma de serviço moderna extensível com Graph API.

Os novos inquilinos de avaliação começarão a ver a pré-visualização pública da nova experiência de administrador no portal do Azure este mês. Enquanto estiverem no estado de pré-visualização, as capacidades e a paridade com a consola do Intune existente serão proporcionadas iterativamente.

A experiência de administração no portal do Azure irá utilizar a já anunciada nova funcionalidade de agrupamento e filtragem; quando o seu inquilino existente é migrado para a nova experiência de agrupamento, o utilizador também será migrado para pré-visualizar a nova experiência de administração do inquilino. Entretanto, se pretende testar ou observar qualquer uma das novas funcionalidades até que o seu inquilino seja migrado, inscreva-se para uma nova conta de avaliação do Intune ou veja a [nova documentação](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune).

Se tiver dúvidas sobre a linha cronológica para a migração do inquilino, contacte a nossa equipa de migração através do e-mail [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="february-2017"></a>Fevereiro de 2017

#### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Capacidade para restringir a inscrição de dispositivos móveis<!--747600, 795782-->
O Intune está a adicionar novas restrições de inscrição que controlam as plataformas de dispositivos móveis autorizadas a inscrever. O Intune separa plataformas de dispositivos móveis como iOS, macOS, Android, Windows e Windows Mobile.

* A restrição da inscrição de dispositivos móveis não restringe a inscrição do cliente de PC.  
* Existe uma opção adicional para bloquear a inscrição de dispositivos pessoais apenas para iOS e Android.

O Intune marca todos os novos dispositivos como pessoais, a menos que o administrador de TI os marque como pertencentes à empresa, conforme explicado [neste artigo](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).

#### <a name="view-all-actions-on-managed-devices---677150--"></a>Ver todas as ações em dispositivos geridos <!--677150-->
Um novo relatório __Ações de Dispositivos__ mostra quem efetuou ações remotas como a reposição de dados de fábrica em dispositivos e o estado dessas ações.

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Os dispositivos não geridos podem aceder a aplicações atribuídas <!--664691-->
Como parte das alterações de estrutura no site do Portal da Empresa, os utilizadores de iOS e Android poderão instalar aplicações atribuídas a eles próprios como "disponíveis sem inscrição" nos seus dispositivos não geridos. Com as suas credenciais do Intune, os utilizadores poderão iniciar sessão no site do Portal da Empresa e ver as listas de aplicações atribuídas a eles próprios. Os pacotes de aplicações das aplicações "disponíveis sem inscrição" estão disponíveis para transferência através do site do Portal da Empresa. As aplicações que requerem inscrição para instalação não são afetadas por esta alteração, uma vez que será solicitado aos utilizadores que inscrevam o seu dispositivo se quiserem instalar essas aplicações.

#### <a name="custom-app-categories---748805--"></a>Categorias de aplicações personalizadas <!--748805-->
Agora pode criar, editar e atribuir categorias às aplicações que adicionar ao Intune. Atualmente, as categorias só podem ser especificadas em inglês.
Veja [Como adicionar uma aplicação ao Intune](/intune-azure/manage-apps/add-apps).

#### <a name="display-device-categories---814654--"></a>Mostrar categorias dos dispositivos <!--814654-->
Agora pode ver a categoria do dispositivo como uma coluna na lista de dispositivos. Também pode editar a categoria a partir da secção de propriedades do painel de propriedades do dispositivo.

### <a name="january-2017"></a>Janeiro de 2017

#### <a name="custom-app-categories---748805--"></a>Categorias de aplicações personalizadas <!--748805-->
Agora pode criar, editar e atribuir categorias às aplicações que adicionar ao Intune. Atualmente, as categorias só podem ser especificadas em inglês.

#### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748803--"></a>Atribuir aplicações de linha de negócio se os dispositivos estiverem ou não inscritos <!--748803-->
Pode agora atribuir aplicações de linha de negócio a partir da loja aos utilizadores se os respetivos dispositivos estiverem ou não inscritos no Intune. Se o dispositivo do utilizador não estiver inscrito no Intune, este tem de aceder ao site do Portal da Empresa para instalá-lo, em vez da aplicação Portal da Empresa.

### <a name="december-2016"></a>Dezembro de 2016

#### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integração da gestão de despesas de telecomunicações na pré-visualização pública do portal do Azure<!--747605-->
Estamos agora a começar a pré-visualizar a integração com os serviços de gestão de despesas de telecomunicações (TEM) de terceiros no portal do Azure. Pode utilizar o Intune para impor limites de utilização de dados nacionais e itinerantes. Estamos a começar essas integrações com [Saaswedo](http://www.saaswedo.com). Para ativar esta funcionalidade no seu inquilino de avaliação, [contacte o suporte da Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

### <a name="see-also"></a>Veja também
Veja [Novidades do Microsoft Intune](whats-new-in-microsoft-intune.md) para obter detalhes sobre os desenvolvimentos recentes.

