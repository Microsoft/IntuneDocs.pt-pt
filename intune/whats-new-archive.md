---
title: Novidades nos meses anteriores do Microsoft Intune
titlesuffix: Azure portal
description: "Veja os anúncios mais antigos na página Novidades do Intune"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 10/19/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5b935f4dc3def1c7b22298f3ec9105e0b2f306d8
ms.sourcegitcommit: 2b35c99ca7d3dbafe2dfe1e0b9de29573db403b9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/16/2017
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Novidades do Microsoft Intune – meses anteriores

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="september-2017"></a>Setembro de 2017

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Informe os utilizadores finais acerca das informações do dispositivo que podem ser vistas para iOS <!--739894-->

Adicionámos o **Tipo de Propriedade** ao ecrã Detalhes do Dispositivo na aplicação Portal da Empresa para iOS. Isto permite que os utilizadores obtenham mais informações sobre privacidade diretamente a partir desta página, através da documentação de utilizador final do Intune. Também poderão localizar estas informações no ecrã Acerca de.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Permitir que os utilizadores finais acedam à aplicação Portal da Empresa para Android sem inscrição <!---1169910--->

Em breve, os utilizadores finais não terão de inscrever os dispositivos para aceder à aplicação Portal da Empresa para Android. Os utilizadores finais em organizações que utilizam Políticas de Proteção de Aplicações deixarão de receber pedidos para inscrever os dispositivos quando abrem a aplicação Portal da Empresa. Os utilizadores finais também poderão instalar aplicações a partir do Portal da Empresa sem inscrever o dispositivo. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Linguagem de compreensão mais fácil na aplicação Portal da Empresa para Android <!---1396349--->  

O texto do processo de inscrição da aplicação Portal da Empresa para Android foi simplificado para facilitar a inscrição dos utilizadores finais. Se tiver documentação de inscrição personalizada, deve atualizá-la para refletir os novos ecrãs. Poderá encontrar imagens de exemplo na nossa página de [Atualização da IU para aplicações de utilizadores finais do Intune](whats-new-app-ui.md#week-of-september-11-2017).

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Aplicação Portal da Empresa do Windows 10 adicionada à política de permissão do Windows Information Protection <!-- 677129 -->

A aplicação Portal da Empresa do Windows 10 foi atualizada para suportar o Windows Information Protection (WIP). A aplicação pode ser adicionada à política de permissão do WIP. Com esta alteração, a aplicação já não tem de ser adicionada à lista **Excluídas**.


## <a name="august-2017"></a>Agosto de 2017

### <a name="improvements-to-device-overview----1404453---"></a>Melhorias na descrição geral do dispositivo <!-- 1404453 -->  
As melhorias na descrição geral do dispositivo apresentam agora os dispositivos inscritos, mas excluem os dispositivos geridos pelo Exchange ActiveSync. Os dispositivos do Exchange ActiveSync não têm as mesmas opções de gestão que os dispositivos inscritos. Para ver o número de dispositivos inscritos e o número de dispositivos inscritos por plataforma, no Intune, no portal do Azure, aceda a **Dispositivos** > **Descrição Geral**.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Melhorias no inventário de dispositivos recolhido pelo Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
Neste lançamento, fizemos as seguintes melhorias às informações do inventário recolhido pelos dispositivos que gere:
 
-   Em dispositivos Android, pode agora adicionar uma coluna ao inventário do dispositivo que mostra o nível de atualização mais recente para cada dispositivo. Adicione a coluna **Nível de atualização de segurança** à sua lista de dispositivos para ver isto.
-   Quando filtrar a vista do dispositivo, agora pode filtrar dispositivos pela sua data de inscrição. Por exemplo, pode apresentar apenas dispositivos que foram inscritos após uma data especificada por si.
-   Melhorámos o filtro utilizado pelo item **Data do Último Registo**.
-   Na lista de dispositivos, agora pode ver o número de telemóvel dos dispositivos pertencentes à empresa.
Além disso, pode utilizar o painel de filtros para procurar dispositivos por número de telemóvel.
 
Para obter mais detalhes sobre o inventário de dispositivos, veja [Como ver o inventário de dispositivos do Intune](device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Suporte de acesso condicional para dispositivos macOS 
<!-- 720172 -->
Agora pode definir uma política de acesso condicional que exige que os dispositivos Mac estejam inscritos no Intune e em conformidade com as políticas de conformidade do dispositivo. Por exemplo, os utilizadores podem transferir a aplicação Portal da Empresa do Intune para macOS e inscrever os dispositivos Mac no Intune. O Intune avalia se o dispositivo Mac está ou não em conformidade com os requisitos, tal como o PIN, versão do SO e Integridade do Sistema.

- Saiba mais sobre o [suporte de acesso condicional para dispositivos macOS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>A aplicação Portal da Empresa para macOS está em pré-visualização pública <!---1484796--->
A aplicação Portal da Empresa para macOS está agora disponível como parte da pré-visualização pública para acesso condicional no Enterprise Mobility + Security. Esta versão suporta o macOS 10.11 e posterior. Obtenha-a em [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### <a name="new-device-restriction-settings-for-windows-10"></a>Novas definições de restrição de dispositivos para Windows 10    
<!--1063965, 1308850  -->
Nesta versão, adicionámos novas definições ao [perfil de restrição de dispositivos Windows 10](/intune/device-restrictions-windows-10) nas seguintes categorias:

-   Windows Defender SmartScreen
-   Loja de aplicações

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Atualizações ao perfil de dispositivo de proteção de ponto final do Windows 10 para as definições do BitLocker
<!--1459533 -->    
Neste lançamento, fizemos as seguintes melhorias à forma como as definições do BitLocker funcionam num perfil de dispositivo de proteção de ponto final do Windows 10:
 
Em **Definições de unidades de SO do BitLocker**, na definição **BitLocker com chip do TPM não compatível**, selecionar **Bloquear** fazia anteriormente com que o BitLocker fosse permitido. Corrigimos isto para que o BitLocker seja bloqueado quando a opção é selecionada.
Em **Definições de unidades de SO do BitLocker**, na definição **Agente de recuperação de dados baseada em certificados**, pode agora bloquear explicitamente o agente de recuperação de dados baseada em certificados. No entanto, por predefinição, o agente é permitido.
Em **Definições de unidades de dados fixas do BitLocker**, na definição **Agente de recuperação de dados**, pode agora bloquear explicitamente o agente de recuperação de dados.
Para obter mais informações, veja [Endpoint protection settings for Windows 10 and later (Definições de proteção de ponto final para o Windows 10 e versões posteriores)](endpoint-protection-windows-10.md).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nova experiência de início de sessão para utilizadores do Portal da Empresa para Android e das Políticas de Proteção de Aplicações <!-- 621669 -->
Os utilizadores finais podem agora procurar aplicações, gerir dispositivos e ver informações de contacto de TI com a aplicação Portal da Empresa para Android sem inscrever os respetivos dispositivos Android. Além disso, se um utilizador final já utilizar uma aplicação protegida por Políticas de Proteção de Aplicações do Intune e iniciar o Portal da Empresa para Android, deixará de receber um pedido para inscrever o dispositivo.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Nova definição para ativar e desativar a otimização da bateria na aplicação Portal da Empresa para Android <!--1405990-->
A página **Definições** na aplicação Portal da Empresa para Android tem uma nova definição para permitir aos utilizadores desativar facilmente a otimização da bateria para as aplicações Microsoft Authenticator e Portal da Empresa. O nome da aplicação apresentado na definição irá variar consoante a aplicação que gere a conta profissional. Recomendamos que os utilizadores desativem a otimização da bateria para melhorar o desempenho das aplicações de trabalho que sincronizam e-mails e dados. 

### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>Suporte de várias identidades do OneNote para iOS      <!-- 1234281 -->
Os utilizadores finais podem agora utilizar contas diferentes (profissionais e pessoais) com o Microsoft OneNote para iOS. As políticas de proteção de aplicações podem ser aplicadas a dados empresariais em blocos de notas de trabalho sem afetar os blocos de notas pessoais. Por exemplo, uma política pode permitir que um utilizador encontre informações em blocos de notas de trabalho, mas impedir que o utilizador copie e cole dados empresariais do bloco de notas de trabalho num bloco de notas pessoal.
 
- Saiba mais sobre as aplicações que suportam a [proteção de aplicações e várias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) com o Intune.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Novas definições para permitir e bloquear aplicações em dispositivos Samsung KNOX Standard
<!-- 1305423 822899-->  
Neste lançamento, estamos a adicionar novas [definições de restrição de dispositivos](device-restrictions-android.md) que lhe permitem especificar as seguintes listas de aplicações:
 
- Aplicações que os utilizadores têm permissão para instalar
- Aplicações que os utilizadores não têm permissão para executar
- Aplicações que estão ocultas do utilizador no dispositivo
 
Pode especificar a aplicação pelo URL, nome do pacote ou da lista de aplicações que gere.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Nova ligação da IU da política de acesso condicional com base na aplicação Azure AD do Intune
<!-- 1016201 -->
Os administradores de TI podem agora definir políticas condicionais com base nas aplicações através da nova IU da política de acesso condicional na carga de trabalho do Azure AD. Por enquanto, o acesso condicional com base nas aplicações na secção Proteção de Aplicações do Intune no portal do Azure permanecerá no local e será imposto lado a lado. Também existe uma ligação útil para a nova IU da política de acesso condicional na carga de trabalho do Intune.

- Saiba mais sobre o [acesso condicional com base na aplicação no Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).



## <a name="july-2017"></a>Julho de 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Restringir a inscrição de dispositivos Android e iOS pela versão do SO<!--- 1333256,  1245463 --->
O Intune suporta agora a restrição da inscrição do iOS e Android pelo número da versão do sistema operativo. Em **Restrição do Tipo de Dispositivo**, o administrador de TI poderá definir uma configuração de plataforma para restringir a inscrição entre o valor do sistema operativo mínimo e o máximo. As versões do sistema operativo Android têm de ser especificadas como Major.Minor.Build.Rev, em que Minor, Build e Rev são opcionais. As versões iOS têm de ser especificadas como Major.Minor.Build em que Minor e Build são opcionais. Saiba mais sobre as [restrições de inscrição de dispositivos](enrollment-restrictions-set.md).

>[!NOTE]
>Não restringe a inscrição através dos programas de inscrição da Apple ou do Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Restringir a inscrição de dispositivos pessoais Android, iOS e macOS <!--- 1333272,  1333275, 1245709 --->
O Intune pode restringir a inscrição de dispositivos pessoais ao criar uma lista de permissões de números IMEI de dispositivos empresariais. O Intune expandiu esta funcionalidade para iOS, Android e macOS através de números de série de dispositivos. Ao carregar os números de série para o Intune, pode pré-declarar os dispositivos como pertencentes à empresa. Através das restrições de inscrição, pode bloquear dispositivos pessoais (BYOD), permitindo a inscrição apenas para dispositivos pertencentes à empresa. Saiba mais sobre as [restrições de inscrição de dispositivos](enrollment-restrictions-set.md).

Para importar números de série, aceda a **Inscrição de dispositivos** > **Identificadores de dispositivo da empresa** e clique em **Adicionar**. Em seguida, carregue um ficheiro .CSV (nenhum cabeçalho, duas colunas para o número de série e detalhes como números IMEI).  Para restringir dispositivos pessoais, aceda a **Inscrição do dispositivo** > **Restrições de inscrição**. Em **Restrições de Tipos de Dispositivos**, selecione **Predefinição** e, em seguida, selecione **Configurações de Plataformas**. Pode **Permitir** ou **Bloquear** dispositivos pessoais para iOS, Android e macOS. 


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Nova ação de dispositivo para forçar os dispositivos a sincronizar com o Intune <!-- 711369 -->
Nesta versão, adicionámos uma nova ação de dispositivo que força o dispositivo selecionado a dar entrada imediatamente no Intune. Quando um dispositivo dá entrada, recebe imediatamente todas as ações ou políticas pendentes que foram atribuídas ao mesmo.  Esta ação pode ajudá-lo a validar e resolver imediatamente problemas de políticas que atribuiu, sem esperar pela próxima entrada agendada.
Para obter detalhes, veja [Sincronizar dispositivos](device-sync.md)

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de software disponíveis mais recentes <!-- 777100 -->
Encontra-se disponível uma nova política a partir da área de trabalho Atualizações de software, onde pode forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de software disponíveis mais recentes. Para obter mais detalhes, veja [Configurar as políticas de atualização do iOS](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Check Point SandBlast Mobile – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis <!-- 954651, 1172027 -->
Pode controlar o acesso a recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo CheckPoint SandBlast Mobile, uma solução de defesa contra ameaças para dispositivos móveis que está integrada com o Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Como funciona a integração com o Intune?
O risco é avaliado com base na telemetria recolhida dos dispositivos que executam o CheckPoint SandBlast Mobile. Pode configurar políticas de acesso condicional de EMS com base na avaliação de riscos do CheckPoint SandBlast Mobile ativada através de políticas de conformidade do dispositivo do Intune. Pode permitir ou bloquear o acesso dos dispositivos que não estejam em conformidade aos recursos empresariais, com base nas ameaças detetadas.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>Implementar uma aplicação como disponível na Loja Microsoft para Empresas <!-- 748101 -->
Com esta versão, os administradores podem atribuir a Loja Microsoft para Empresas como disponível. Quando é definida como disponível, os utilizadores finais podem instalar a aplicação a partir da aplicação ou site do Portal da Empresa sem serem redirecionados para a Loja Microsoft.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>Atualização da IU do site do Portal da Empresa <!--1313244 part 1-->
Fizemos várias alterações à IU do [site do Portal da Empresa](https://portal.manage.microsoft.com) para melhorar a experiência do utilizador final.

- __Melhorias aos mosaicos das aplicações__: os ícones das aplicações são agora apresentados com um fundo gerado automaticamente com base na cor dominante do ícone (caso seja possível detetar uma). Quando aplicável, este fundo vem substituir o limite cinzento que era apresentado nos mosaicos das aplicações.

    O site do Portal da Empresa apresentará ícones grandes sempre que possível numa próxima versão. Recomendamos que os administradores de TI publiquem aplicações com ícones de alta resolução com o tamanho mínimo de 120 x 120 píxeis. 

- __Alterações de navegação__: os itens da barra de navegação foram movidos para o menu de opções no canto superior esquerdo. A página Categorias foi removida. Os utilizadores podem agora filtrar conteúdos por categoria enquanto navegam.

- __Atualização das Aplicações em Destaque:__ adicionámos ao site uma página dedicada em que os utilizadores podem procurar aplicações que optou por destacar e otimizámos a IU da secção Destaques na home page.

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>Suporte para iBooks no site do Portal da Empresa <!--1231841-->
Adicionámos uma página dedicada ao site do Portal da Empresa que permite aos utilizadores procurar e transferir iBooks. 


### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>Detalhes adicionais sobre a resolução de problemas para o suporte técnico<!---  Applies to 1263399, 1326964, 1341642 --->
O Intune atualizou o ecrã de resolução de problemas e acrescentou mais informações para a equipa de administradores e suporte técnico. Agora pode ver uma tabela **Atribuições**, que resume todas as atribuições do utilizador com base na associação a grupos. Esta lista inclui:
- Aplicações móveis
- Políticas de conformidade
- Perfis de configuração
 
Para além disso, a tabela **Dispositivos** agora inclui as colunas **Tipo de associação Azure AD** e **Em conformidade com o Azure AD**. Para obter mais informações, veja [Ajudar os utilizadores na resolução de problemas](help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Armazém de Dados do Intune (Pré-visualização Pública)
O Armazém de Dados do Intune copia dados diariamente para fornecer uma apresentação do histórico do seu inquilino. Pode aceder a dados através de um ficheiro do Power BI (PBIX), de uma ligação OData compatível com várias ferramentas de análise ou ao interagir com a API REST. Para obter mais informações, veja [Utilizar o Armazém de Dados do Intune](reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Modos claro e escuro disponíveis para a aplicação Portal da Empresa para Windows 10 <!---676547--->
Os utilizadores finais poderão personalizar o modo de cor da aplicação Portal da Empresa para Windows 10. O utilizador pode fazer a alteração na secção Definições da aplicação Portal da Empresa. A alteração será apresentada após o utilizador reiniciar a aplicação. Para a versão 1607 e posterior do Windows 10, o modo de aplicação será predefinido para a definição do sistema. Para a versão 1511 e anterior do Windows 10, o modo de aplicação será predefinido para o modo claro.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Permitir que os utilizadores finais marquem o grupo de dispositivos na aplicação Portal da Empresa para Windows 10 <!---807046-->
Os utilizadores finais podem agora selecionar o grupo a que o dispositivo pertence ao marcá-lo diretamente na aplicação Portal da Empresa para Windows 10.



## <a name="june-2017"></a>Junho de 2017

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Novo acesso de administração baseada em funções para administradores do Intune <!-- 1099990 -->  
Uma nova função de administrador de acesso condicional está a ser adicionada para ver, criar, modificar e eliminar as políticas de Acesso Condicional do Azure AD. Anteriormente, apenas os administradores globais e os administradores de segurança tinham essa permissão. Pode ser concedida esta permissão de função aos administradores do Intune para que tenham acesso às políticas de acesso condicional.


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>Marcar dispositivos da empresa com um número de série <!-- 1215070 -->  
Agora, o Intune suporta o carregamento de números de série Android, Mac OS e iOS como Identificadores de Dispositivo da Empresa. Neste momento, não pode utilizar números de série para bloquear a inscrição de dispositivos pessoais, porque os números de série não são verificados durante a inscrição. O bloqueio de dispositivos pessoais pelo número de série será lançado em breve.


### <a name="new-remote-actions-for-ios-devices----854689---"></a>Novas ações remotas para dispositivos iOS <!-- 854689 -->
Nesta versão, adicionámos duas novas ações de dispositivo remoto para dispositivos iPad partilhados que fazem a gestão da aplicação Sala de Aula da Apple:

-   [Terminar a sessão do utilizador atual](device-logout-user.md) – termina a sessão do utilizador atual do dispositivo iOS que selecionar.
-   [Remover utilizador](device-remove-user.md) – elimina o utilizador que selecionar da cache local num dispositivo iOS.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>Suporte para iPads partilhados com a aplicação Sala de Aula para iOS<!-- 1044681 -->
Nesta versão, expandimos o suporte da gestão da aplicação Sala de Aula para iOS para incluir alunos que iniciem sessão em iPads partilhados com o respetivo ID Apple gerido.


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Alterações às aplicações incorporadas do Intune <!-- 1332306 -->
Anteriormente, o Intune continha várias aplicações incorporadas que podia atribuir rapidamente. Com base no seu feedback, removemos esta lista e já não verá as aplicações incorporadas.
No entanto, se já tiver atribuído aplicações incorporadas, as mesmas continuarão visíveis na lista de aplicações. Pode continuar a atribuir estas aplicações conforme necessário.
Numa versão posterior, planeamos adicionar um método mais simples para selecionar e atribuir aplicações incorporadas a partir do portal do Azure.

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Instalação mais fácil das aplicações do Office 365 <!--- 1121362 --->
O novo tipo de aplicação do **Office 365 ProPlus** faz com que seja mais fácil atribuir aplicações do Office 365 ProPlus 2016 aos dispositivos que está a gerir que executem a versão mais recente do Windows 10. Além disso, também pode instalar o Microsoft Project e o Microsoft Visio, se tiver licenças dos mesmos. As aplicações que pretende são agrupadas e apresentadas como uma aplicação na lista de aplicações na consola do Intune.
Para obter mais informações, veja [Como adicionar aplicações do Office 365 para Windows 10](apps-add-office365.md).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>Suporte para aplicações offline na Loja Microsoft para Empresas <!--- 777044 --->
As aplicações offline compradas na Loja Microsoft para Empresas serão agora sincronizadas com o portal do Azure. Poderá então implementar essas aplicações para grupos de dispositivos ou grupos de utilizadores. As aplicações offline são instaladas pelo Intune e não pela loja.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>O Microsoft Teams faz agora parte da lista de aplicações aprovadas para acesso condicional com base em aplicações <!-- 1257019 -->
A aplicação Microsoft Teams para iOS e Android faz agora parte das aplicações aprovadas para políticas de acesso condicional com base em aplicações para o Exchange e o SharePoint Online. A aplicação pode ser configurada através do painel de Proteção de Aplicações do Intune no portal do Azure para todos os inquilinos que utilizam atualmente o acesso condicional com base em aplicações.

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Managed Browser e integração do proxy de aplicações <!-- 1287310 -->
O Intune Managed Browser pode agora ser integrado com o serviço do Proxy de Aplicações do Azure AD para permitir aos utilizadores acederem a sites internos mesmo quando trabalham remotamente. Basta que os utilizadores do browser entrem no URL do site como fariam normalmente e o Managed Browser encaminha o pedido através do gateway Web do proxy de aplicações. Para obter mais informações, veja [Manage Internet access using managed browser policies (Gerir o acesso à Internet através de políticas de browser gerido)](app-configuration-managed-browser.md).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Novas definições de configuração de aplicações para o Intune Managed Browser<!-- 682951 -->
Nesta versão, adicionámos mais configurações à aplicação Intune Managed Browser para iOS e Android. Agora, pode utilizar uma política de configuração de aplicações para configurar a página inicial predefinida e os marcadores para o browser.
Para obter mais informações, veja [Manage Internet access using managed browser policies (Gerir o acesso à Internet através de políticas de browser gerido)](app-configuration-managed-browser.md)

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Definições do BitLocker para Windows 10 <!-- 951707 -->
Agora, pode configurar as definições do BitLocker para dispositivos Windows 10 com um novo perfil de dispositivo do Intune. Por exemplo, pode exigir que os dispositivos sejam encriptados e também pode configurar definições adicionais que são aplicadas quando o BitLocker está ativado.
Para obter mais informações, veja [Endpoint protection settings for Windows 10 and later (Definições de proteção de ponto final para o Windows 10 e versões posteriores)](endpoint-protection-windows-10.md).

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Novas definições para o perfil de restrição de dispositivos Windows 10 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
Nesta versão, adicionámos novas definições ao perfil de restrição de dispositivos Windows 10 nas seguintes categorias:

-  Windows Defender
-  Rede móvel e conectividade
-  Experiência de ecrã bloqueado
-  Privacidade
-  Procura
-  Destaque do Windows
-  Browser Edge

Para obter mais informações sobre as definições do Windows 10, veja [Windows 10 and later device restriction settings (Definições de restrição de dispositivos Windows 10)](device-restrictions-windows-10.md).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>A aplicação Portal da Empresa para Android tem agora uma nova experiência de utilizador final para Políticas de Proteção de Aplicações <!--1305217-->
Com base no feedback dos clientes, modificámos a aplicação Portal da Empresa para Android para apresentar o botão **Aceder a Conteúdos da Empresa**. O objetivo é evitar que os utilizadores finais passem desnecessariamente pelo processo de inscrição quando apenas precisarem de acesso a aplicações que suportem Políticas de Proteção de Aplicações, uma funcionalidade da gestão de aplicações móveis do Intune. Pode ver estas alterações na página [Novidades na IU da aplicação](whats-new-app-ui.md).

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nova ação de menu para remover facilmente o Portal da Empresa <!--1164569-->
Com base nos comentários dos utilizadores, a aplicação Portal da Empresa para Android adicionou uma nova ação de menu para iniciar a remoção do Portal da Empresa do seu dispositivo. Esta ação remove o dispositivo da gestão do Intune para que a aplicação possa ser removida do dispositivo pelo utilizador. Pode ver estas alterações na página [Novidades na IU da aplicação](whats-new-app-ui.md) e na [Documentação do utilizador final do Android](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Melhorias na sincronização da aplicação com a Atualização para Criativos do Windows 10 <!--676505-->
A aplicação Portal da Empresa para Windows 10 iniciará agora automaticamente uma sincronização para pedidos de instalação de aplicações para dispositivos com a Atualização para Criativos do Windows 10 (versão 1703). Tal reduzirá o problema da interrupção da instalação de aplicações durante o estado “Sincronização Pendente”. Além disso, os utilizadores poderão iniciar manualmente uma sincronização a partir da própria aplicação. Pode ver estas alterações na página [Novidades na IU da aplicação](whats-new-app-ui.md).

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nova experiência orientada para o Portal da Empresa do Windows 10 <!---1058938--->
A aplicação Portal da Empresa para Windows 10 vai incluir uma experiência de instruções orientada do Intune para dispositivos que não foram identificados ou inscritos. A nova experiência disponibiliza instruções passo a passo que orientam o utilizador no registo do Azure Active Directory (obrigatório para as funcionalidades de Acesso Condicional) e na inscrição MDM (obrigatória para as funcionalidades de gestão de dispositivos). A experiência guiada estará acessível na página inicial do Portal da Empresa. Os utilizadores podem continuar a utilizar a aplicação se não concluírem o registo e a inscrição, mas terão funcionalidades limitadas.

Esta atualização só é visível em dispositivos com a Atualização de Aniversário do Windows 10 (compilação 1607) ou superior. Pode ver estas alterações na página [Novidades na IU da aplicação](whats-new-app-ui.md).


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>As consolas de administração do Microsoft Intune e do Acesso Condicional estão geralmente disponíveis
Estamos a anunciar a disponibilidade geral do novo Intune na consola de administração do portal do Azure e na consola de administração do Acesso Condicional. Através do Intune no portal do Azure, agora pode gerir todas as capacidades de MAM e MDM do Intune numa experiência de administração consolidada e tirar partido do agrupamento e do direcionamento do Azure AD. O acesso condicional no Azure junta capacidades avançadas no Azure AD e no Intune numa única consola unificada. E, a partir de uma experiência administrativa, a migração para a plataforma do Azure permite que utilize browsers modernos.

O Intune agora está visível sem a etiqueta **pré-visualização** no portal do Azure em portal.azure.com.

Não é necessária nenhuma ação para os clientes existentes no momento, exceto se tiver recebido uma de várias mensagens no centro de mensagens a pedir para tomar uma ação para que possamos migrar os seus grupos. Também pode ter recebido um aviso do centro de mensagens a informar que a migração está a demorar mais tempo devido a erros do nosso lado. Continuaremos a trabalhar diligentemente para migrar qualquer cliente afetado.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Melhorias dos mosaicos de aplicação na aplicação Portal da Empresa para iOS
Atualizamos a estrutura dos mosaicos de aplicação na home page para refletir a cor corporativa que definiu para o Portal da Empresa. Para mais obter informações, veja [Novidades na IU da aplicação](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Seletor de conta agora disponível para a aplicação Portal da Empresa para iOS
Os utilizadores de dispositivos iOS podem ver o nosso novo seletor de conta ao iniciar sessão no Portal da Empresa se utilizarem a conta profissional ou escolar para iniciar sessão noutras aplicações da Microsoft. Para mais obter informações, veja [Novidades na IU da aplicação](whats-new-app-ui.md).

## <a name="may-2017"></a>Maio de 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Alterar a sua autoridade MDM sem anular a inscrição dos dispositivos geridos <!--1103950-->
Pode agora alterar a autoridade MDM sem ter de contactar o Suporte da Microsoft e sem ter de anular a inscrição e inscrever novamente os seus dispositivos geridos existentes. Na consola do Gestor de Configuração, pode [alterar a sua autoridade MDM](/sccm/mdm/deploy-use/change-mdm-authority) com a opção Definir para o Gestor de Configuração (híbrido) para o Microsoft Intune (autónomo) ou vice-versa.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Notificação melhorada para PINs de arranque do Samsung KNOX <!--1087143-->
Quando os utilizadores finais têm de definir um PIN de arranque em dispositivos Samsung KNOX para ficarem em conformidade com a encriptação, a notificação apresentada aos utilizadores finais irá colocá-los no local exato na aplicação Definições quando toca na notificação.  Anteriormente, a notificação enviava o utilizador final para o ecrã de alteração da palavra-passe.

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>Suporte do Gestor de Escola da Apple (ASM) com iPad partilhado <!-- 748864, 770395-->

O Intune suporta agora a utilização do Gestor de Escola da Apple (ASM) em vez do Programa de Inscrição de Dispositivos Apple para fornecer uma inscrição inicial de dispositivos iOS. A integração do ASM é necessária para utilizar a aplicação Sala de Aula para iPads Partilhados e para ativar a sincronização de dados do ASM no Azure Active Directory através da School Data Sync (SDS) da Microsoft. Para obter mais informações, veja [Ativar a inscrição do dispositivo iOS com o Gestor de Escola da Apple](apple-school-manager-set-up-ios.md).

> [!NOTE]
> A configuração de iPads Partilhados para trabalhar com a aplicação Sala de Aula requer configurações do iOS Education no Azure que ainda não estão disponíveis.  Esta funcionalidade será adicionada em breve.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>Fornecer assistência remota em dispositivos Android através do TeamViewer <!-- 675418 -->

O Intune pode agora utilizar o software [TeamViewer](https://www.teamviewer.com), adquirido separadamente, para lhe permitir disponibilizar assistência remota aos seus utilizadores com dispositivos Android. Para obter mais informações, veja [Fornecer assistência remota em dispositivos Android geridos no Intune](device-profile-android-teamviewer.md).

### <a name="app-management"></a>Gestão de aplicações

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>Novas condições de políticas de proteção de aplicações para MAM <!-- 679864 -->

Agora pode definir um requisito para a MAM sem utilizadores de inscrição que impõe as seguintes políticas:

- Versão mínima da aplicação
- Versão mínima do sistema operativo
- Versão mínima do SDK da Aplicação Intune da aplicação de destino (apenas iOS)

Esta funcionalidade está disponível no Android e no iOS. O Intune suporta a imposição da versão mínima para versões de plataformas de SO, versões de aplicações e SDK da Aplicação Intune. No iOS, as aplicações com o SDK integrado podem também definir a imposição de uma versão mínima ao nível do SDK. O utilizador não poderá aceder à aplicação de destino se não forem cumpridos os requisitos mínimos através da política de proteção de aplicações nos três níveis diferentes mencionados acima. Neste momento, o utilizador pode remover a conta (para aplicações de várias identidades), fechar a aplicação ou atualizar a versão do SO ou da aplicação.

Também pode configurar definições adicionais para fornecer uma notificação sem bloqueios que recomenda uma atualização da versão do SO ou da aplicação. Esta notificação pode ser fechada e a aplicação pode ser utilizada normalmente.

Para obter mais informações, veja [Definições de políticas de proteção de aplicações iOS](app-protection-policy-settings-ios.md) e [Definições de políticas de proteção de aplicações Android](app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Configurar as configurações de aplicações para Android for Work <!-- 621621 -->
Algumas aplicações Android da loja suportam opções de configuração geridas que permitem a um administrador de TI controlar o modo como uma aplicação é executada no perfil de trabalho. Com o Intune, agora pode ver as configurações suportadas por uma aplicação e configurá-las a partir do portal do Azure com um estruturador de configuração ou um editor de JSON. Para obter mais informações, veja [Use app configurations for Android for Work (Utilizar configurações de aplicações para Android for Work)](app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>Nova capacidade de configuração de aplicações para MAM sem inscrição <!-- 677969 -->
Agora pode criar políticas de configuração de aplicações através do MAM sem canal de inscrição. Esta funcionalidade é equivalente às políticas de configuração de aplicações disponíveis na configuração de aplicações de gestão de dispositivos móveis (MDM). Para obter um exemplo de configuração de aplicações através do MAM sem inscrição, veja [Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Configurar listas de URLs permitidos e bloqueados para o Managed Browser <!-- 682960 -->
Agora pode configurar uma lista de domínios e URLs permitidos e bloqueados para o Intune Managed Browser utilizando definições de configuração de aplicações no portal do Azure. Estas definições podem ser configuradas independentemente de estarem a ser utilizadas num dispositivo gerido ou não gerido. Para obter mais informações, veja [Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>Vista do suporte técnico da política de proteção de aplicações <!-- 1069473 -->
Os utilizadores do Suporte Técnico de TI agora podem verificar o estado da licença do utilizador e o estado da política de proteção de aplicações atribuído aos utilizadores no painel Resolução de Problemas. Para obter detalhes, veja [Resolução de Problemas](./help-desk-operators.md).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="control-website-visits-on-ios-devices----723832---"></a>Controlar visitas de sites em dispositivos iOS <!-- 723832 -->
Agora pode controlar os sites que os utilizadores dos dispositivos iOS podem visitar através de um destes métodos:

- Adicionar URLs permitidos e bloqueados através do filtro de conteúdo Web incorporado da Apple.

- Permitir o acesso apenas a sites específicos no browser Safari. São criados marcadores no Safari para cada site que especificar.

Para obter mais informações, veja [Definições de filtros de conteúdo Web para dispositivos iOS](web-content-filter-settings-ios.md).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Permissões pré-configuradas de dispositivos para aplicações Android for Work <!-- 621614 -->
Para aplicações implementadas para perfis de trabalho de dispositivos Android for Work, pode agora configurar o estado das permissões para aplicações individuais.  Por predefinição, as aplicações Android que requerem permissões de dispositivos, tal como o acesso à localização ou à câmara do dispositivo, solicitarão aos utilizadores que aceitem ou recusem as permissões.  Por exemplo, se uma aplicação utilizar o microfone do dispositivo, o utilizador final ser solicitado a conceder permissão à aplicação para utilizar o microfone. Esta funcionalidade permite-lhe definir permissões em nome do utilizador final.  Pode configurar permissões para a) recusar automaticamente sem notificar o utilizador, b) aprovar automaticamente sem notificar o utilizador ou c) avisar o utilizador para aceitar ou recusar. Para obter mais informações, veja [Definições de restrição de dispositivos Android for Work no Microsoft Intune](device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Definir um PIN específico de cada aplicação para dispositivos Android for Work <!-- 728976, 1102534 -->
Os dispositivos Android 7.0 e superior com um perfil de trabalho gerido como um dispositivo Android for Work permitem ao administrador definir uma política de código de acesso aplicada apenas a aplicações no perfil de trabalho.  As opções incluem:

- Definir apenas uma política de código de acesso para todos os dispositivos – este é o código de acesso que o utilizador tem de utilizar para desbloquear os dispositivos completos.
- Definir apenas uma política de código de acesso do perfil de trabalho – será pedido aos utilizadores que introduzam um código de acesso sempre que qualquer aplicação no perfil de trabalho for aberta.
- Definir uma política de perfil de trabalho e de dispositivo – o administrador de TI tem a opção de definir uma política de código de acesso do dispositivo e uma política de código de acesso do perfil de trabalho com diferentes níveis de segurança (por exemplo, um PIN de quatro dígitos para desbloquear o dispositivo, mas um PIN de seis dígitos para abrir qualquer aplicação de trabalho).

Para obter mais informações, veja [Definições de restrição de dispositivos Android for Work no Microsoft Intune](device-restrictions-android-for-work.md).

> [!NOTE]
> Esta opção só está disponível para o Android 7.0 e superior.  Por predefinição, o utilizador final pode utilizar os dois PINs definidos separadamente ou pode optar por combinar os dois PINs definidos no mais forte dos dois.

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Novas definições para dispositivos Windows 10 <!-- 978585 -->
Adicionámos novas [Definições de restrição de dispositivos Windows](device-restrictions-windows-10.md) que controlam funcionalidades como ligação sem fios, deteção de dispositivos, mudança de tarefas e mensagens de erro do cartão SIM.

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>Atualizações à configuração do certificado <!-- 918991 and 823198 -->
Ao criar um perfil de certificado SCEP, para **Formato de nome do requerente**, a opção **Personalizado** está disponível para dispositivos iOS, Android e Windows. Antes desta atualização, o campo **Personalizado** estava disponível apenas para dispositivos iOS. Para obter mais informações, veja [Como criar um perfil de certificado SCEP] (certificates-scep-configure.md#how-to-create-a-scep-certificate-profile).

Ao criar um perfil de certificado PKCS, para **Nome alternativo do requerente**, o **atributo Personalizado do Azure AD** está disponível. A opção **Departamento** está disponível quando seleciona o **atributo Personalizado do Azure AD**. Para obter mais informações, veja [Como criar um perfil de certificado PKCS](certficates-pfx-configure.md#create-a-device-configuration-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Configurar várias aplicações que podem ser executadas quando um dispositivo Android está no modo de quiosque <!-- 662059 -->
Quando um dispositivo Android estava no modo de quiosque, podia apenas configurar anteriormente uma aplicação com permissão para ser executada. Agora pode configurar várias aplicações ao utilizar a ID da aplicação, o URL da loja ou ao selecionar uma aplicação Android que já gere. Para obter mais informações, veja [Definições do modo de quiosque](device-restrictions-android.md#kiosk).



## <a name="april-2017"></a>Abril de 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Suporte para gerir a aplicação Sala de Aula da Apple
Já pode gerir a aplicação Sala de Aula do iOS nos dispositivos iPad. Configure a aplicação Sala de Aula no iPad dos professores com os dados corretos da turma e dos estudantes e, em seguida, configure os iPads dos estudantes registados numa turma para que possa controlá-los através da aplicação.
Para obter detalhes, veja [Configure iOS education settings (Configurar as definições de educação do iOS)](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Suporte para opções de configuração gerida para aplicações Android <!-- 621621 -->
As aplicações Android na Play Store que suportam opções de configuração gerida podem agora ser configuradas pelo Intune.  Esta funcionalidade permite às TI ver a lista de valores de configuração suportados por uma aplicação e disponibiliza IU de primeira classe assistida para lhes permitir configurar os valores.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Nova política para PINs complexos em Android <!-- 722069 -->
Pode agora definir um tipo de [palavra-passe](device-restrictions-android.md#password) obrigatório de Numérica complexa num perfil de dispositivo Android para dispositivos com o Android 5.0 e superior.  Utilize esta definição para impedir que os utilizadores dos dispositivos criem um PIN que contenha números repetidos ou consecutivos, como 1111 ou 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Suporte adicional para dispositivos Android for Work
- **Gerir definições de palavra-passe e perfil de trabalho** <!-- 612808 -->

  Esta nova política de restrição para dispositivos Android for Work permite-lhe agora gerir as definições de palavra-passe e perfil de trabalho em dispositivos Android for Work geridos por si.

- **Permitir a partilha de dados entre perfis de trabalho e pessoais** <!-- 1045102 -->

Este perfil de restrição para dispositivos Android for Work tem agora novas opções para o ajudar a configurar a partilha de dados entre perfis de trabalho e perfis pessoais.

- **Restringir as ações de copiar e colar entre perfis de trabalho e pessoais** <!-- 1046094 -->

  Um novo perfil de dispositivo personalizado para dispositivos Android for Work permite-lhe agora decidir se as ações de copiar e colar entre aplicações de trabalho e pessoais são permitidas.

Para obter mais informações, veja [Restrições de dispositivos para Android for Work](device-restrictions-android-for-work.md).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Atribuir aplicações LOB a dispositivos iOS e Android <!-- 1057568 -->
Agora pode atribuir aplicações de linha de negócio (LOB) para [iOS](lob-apps-ios.md) (ficheiros .ipa) e [Android](lob-apps-android.md) (ficheiros .apk) a utilizadores ou dispositivos.


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Novas políticas de dispositivos para iOS <!-- 723774, 723815, 723826, 723830 -->
- **Aplicações no Ecrã principal** – controla as aplicações que os utilizadores veem no [Ecrã principal do dispositivo iOS](home-screen-settings-ios.md). Esta política altera o esquema do ecrã principal, mas não implementa aplicações.

- **Ligações a dispositivos AirPrint** – controla os [dispositivos AirPrint](air-print-settings-ios-macos.md) (impressoras de rede) aos quais os utilizadores finais do dispositivo iOS se podem ligar.

- **Ligações a dispositivos AirPlay** – controla os [dispositivos AirPlay](airplay-settings-ios.md) (como a Apple TV) aos quais os utilizadores finais do dispositivo iOS se podem ligar.

- **Mensagem de ecrã de bloqueio personalizada** – configura uma mensagem personalizada que os utilizadores verão no ecrã de bloqueio do dispositivo iOS, que substitui a mensagem de ecrã de bloqueio predefinida. Para mais informações, veja [Ativar o modo perdido em dispositivos iOS](device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Restringir notificações push para aplicações para iOS <!-- 723767 -->
Num perfil de restrição para dispositivos do Intune, pode agora configurar as seguintes [definições de notificação](app-notification-settings-ios.md) para dispositivos iOS:

- Ativar ou desativar notificações por completo para uma aplicação específica.
- Ativar ou desativar notificações para uma aplicação específica na central de notificações.
- Especificar o tipo de alerta: **Nenhum**, **Faixa** ou **Aviso Modal**.
- Especificar se são permitidos emblemas para esta aplicação.
- Especificar se são permitidos sons de notificação.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Configurar que aplicações iOS são executadas em modo de aplicação única autónomo <!-- 737837 -->
Pode agora utilizar um perfil de dispositivo do Intune para configurar os dispositivos iOS para executar aplicações específicas no [modo de aplicação única autónomo](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only). Quando este modo está configurado e a aplicação é executada, o dispositivo é bloqueado para que possa apenas executar essa aplicação. Um exemplo desta funcionalidade é quando configura uma aplicação que permite aos utilizadores fazer um teste no dispositivo. Quando as ações da aplicação forem concluídas ou quando remover esta política, o dispositivo regressa ao estado de funcionamento normal.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Configurar domínios de confiança para navegação Web e de e-mail em dispositivos iOS <!-- 723765 -->
Para um perfil de restrição para dispositivos iOS, pode agora configurar as seguintes [definições de domínio](device-restrictions-ios.md#domains):

- **Domínios de e-mail não marcados** – e-mails que o utilizador envia ou recebe que não correspondam aos domínios que especifica aqui serão marcados como não sendo de confiança.

- **Domínios Web geridos** – os documentos transferidos a partir dos URLs que especificar aqui serão considerados como geridos (apenas para Safari).  

- **Domínios de preenchimento automático da palavra-passe do Safari** – os utilizadores podem guardar palavras-passe no Safari apenas de URLs que correspondam aos padrões que especificar aqui. Para utilizar esta definição, o dispositivo tem de estar no modo supervisionado e não configurado para múltiplos utilizadores. (iOS 9.3 e superior)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>Aplicações do VPP disponíveis no Portal da Empresa para iOS <!-- 748782 -->
Pode agora atribuir aos utilizadores finais aplicações iOS compradas em grandes volumes (VPP) como instalações no modo **Disponível**. Os utilizadores finais precisarão de uma conta da Apple Store para instalar a aplicação.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Sincronizar eBooks a partir da Apple VPP Store <!-- 800878 -->
Agora pode [sincronizar livros](vpp-apps-ios.md) que tenha comprado na loja do Apple Volume Purchase Program com o Intune e atribuí-los aos utilizadores.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Gestão de vários utilizadores para dispositivos Samsung KNOX Standard <!-- 971988 -->
Os dispositivos que executem o Samsung KNOX Standard agora suportam a [gestão de vários utilizadores](android-enroll.md) do Intune. Isto significa que os utilizadores finais podem iniciar e terminar sessão no dispositivo com as credenciais do Azure Active Directory e o dispositivo será gerido centralmente quer esteja a ser utilizado ou não.  Quando os utilizadores finais iniciam sessão, têm acesso às aplicações e obtêm as políticas aplicadas às mesmas. Quando os utilizadores terminam sessão, todos os dados das aplicações são limpos.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Definições de restrição adicionais para dispositivos Windows <!-- 818566 -->
Adicionamos suporte para mais [definições de restrição para dispositivos Windows](device-restrictions-windows-10.md), tais como suporte adicional para o browser Edge, personalização do ecrã de bloqueio do dispositivo, personalizações do menu Iniciar, imagens de fundo definidas por pesquisas do Destaque do Windows e definição de proxy.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Suporte para múltiplos utilizadores da Atualização para Criativos do Windows 10 <!-- 822547 -->
Adicionamos suporte para a [gestão de vários utilizadores](windows-enroll.md) para dispositivos a executar a Atualização para Criativos do Windows 10 e que estejam associados ao domínio do Azure Active Directory. Tal significa que, quando outros utilizadores padrão iniciarem sessão no dispositivo com as credenciais do Azure AD, receberão as aplicações e as políticas atribuídas aos seus nomes de utilizador. Atualmente, os utilizadores não podem utilizar o Portal da Empresa para cenários de self-service, tais como instalar aplicações.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start para PCs com Windows 10 <!-- 1004830 -->
Está agora disponível uma [ação de dispositivo Fresh Start](device-fresh-start.md) para PCs com Windows 10.  Ao executar esta ação, as aplicações instaladas no PC são removidas e o PC é automaticamente atualizado para a versão mais recente do Windows. Esta ação pode ajudar a remover aplicações OEM que vêm frequentemente pré-instaladas num PC novo. Pode configurar se os dados de utilizador são retidos ao efetuar esta ação.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Caminhos de atualização do Windows 10 adicionais<!-- 903672 -->
Agora, pode criar uma [política de atualização de edição para atualizar os dispositivos](edition-upgrade-configure-windows-10.md) para as seguintes edições do Windows 10 adicionais:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Inscrever dispositivos Windows 10 em volume <!-- 747607 -->
Agora, pode juntar-se a um grande número de dispositivos que executam a atualização para Criativos do Windows 10 para o Azure Active Directory e o Intune com o Windows Configuration Designer (WCD). Para ativar a [inscrição na MDM em massa](windows-bulk-enroll.md) para o seu inquilino do Azure AD, crie um pacote de aprovisionamento que associe dispositivos ao seu inquilino do Azure AD através do Windows Configuration Designer e aplique o pacote aos dispositivos pertencentes à empresa que pretende inscrever e gerir em massa. Assim que o pacote for aplicado aos dispositivos, estes são associados ao Azure AD, inscritos no Intune e estarão prontos para os seus utilizadores do Azure AD iniciarem sessão.  Os utilizadores do Azure AD são utilizadores padrão nestes dispositivos e obtêm as políticas atribuídas e as aplicações necessárias. Os cenários Self-service e Portal da Empresa não são atualmente suportados.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Novas definições de MAM para PIN e localizações de armazenamento gerido <!-- 581122, 736644 -->
Estão agora disponíveis duas novas definições de aplicações para o ajudar em cenários de MAM (gestão de aplicações móveis):

- **Desativar o PIN da aplicação quando o PIN do dispositivo for gerido** – deteta se está presente um PIN no dispositivo inscrito e, caso esteja, ignora o PIN da aplicação acionado pelas políticas de proteção da aplicação. Esta definição permitirá reduzir o número de pedidos de PIN quando os utilizadores abrirem uma aplicação com MAM ativada num dispositivo inscrito. Esta funcionalidade está disponível para Android e iOS.

- **Selecionar em que serviços de armazenamento podem ser guardados os dados empresariais** – permite-lhe especificar as localizações de armazenamento onde podem ser guardados dados empresariais. Os utilizadores podem guardar nos serviços de localização de armazenamento selecionados, o que significa que todos os que não estiverem listados serão bloqueados.

  Lista dos serviços de localização de armazenamento:

  - OneDrive para Empresas
  - SharePoint Online
  - Armazenamento local

### <a name="help-desk-troubleshooting-portal----907448---"></a>Portal de resolução de problemas de suporte técnico <!-- 907448 -->
O novo [portal de resolução de problemas](help-desk-operators.md) permite aos operadores de suporte técnico e aos administradores do Intune verem os utilizadores e os seus dispositivos e executar tarefas para resolver problemas técnicos do Intune.

## <a name="march-2017"></a>Março de 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Suporte para o Modo Perdido no iOS <!--431695-->
Para os dispositivos iOS 9.3 e posteriores, o Intune adicionou o suporte para o **Modo Perdido**. Agora, pode bloquear um dispositivo para impedir toda a utilização e apresentar um número de telefone de contacto e uma mensagem no ecrã de bloqueio do dispositivo.

O utilizador final só poderá desbloquear o dispositivo quando um administrador desativar o Modo Perdido. Quando o Modo Perdido está ativado, pode utilizar a ação **Localizar dispositivo** para apresentar a localização geográfica do dispositivo num mapa na consola do Intune.

O dispositivo tem de ser um dispositivo iOS pertencente à empresa, inscrito através do DEP, que esteja no modo supervisionado.

Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](device-management.md)?

### <a name="improvements-to-device-actions-report---677150--"></a>Melhorias ao relatório de Ações de Dispositivos<!--677150-->
Melhoramos o relatório de Ações de Dispositivos para um melhor desempenho. Além disso, agora pode filtrar o relatório por estado. Por exemplo, pode filtrar o relatório para mostrar apenas as ações de dispositivo que foram concluídas.

### <a name="custom-app-categories---748805--"></a>Categorias de aplicações personalizadas <!--748805-->
Agora pode criar, editar e atribuir categorias às aplicações que adicionar ao Intune. Atualmente, as categorias só podem ser especificadas em inglês.
Veja [Como adicionar uma aplicação ao Intune](apps-add.md).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Atribuir aplicações de LOB a utilizadores com dispositivos não inscritos <!--748823-->
Agora pode atribuir aplicações de linha de negócio da loja aos utilizadores, quer os respetivos dispositivos estejam ou não inscritos no Intune. Se o dispositivo do utilizador não estiver inscrito no Intune, o utilizador terá de aceder ao site do Portal da Empresa para o instalar, em vez da aplicação Portal da Empresa.

### <a name="new-compliance-reports---846671--"></a>Novos relatórios de conformidade <!--846671-->
Tem agora relatórios de conformidade que lhe dão a postura de conformidade dos dispositivos na sua empresa e lhe permitem rapidamente resolver problemas relacionados com a conformidade encontrados pelos utilizadores. Pode ver informações sobre o

- Estado de conformidade geral dos dispositivos
- Estado de conformidade de uma definição individual
- Estado de conformidade de uma política individual

Também pode utilizar estes relatórios para desagregar um dispositivo individual e ver as definições e políticas específicas que afetam esse dispositivo.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acesso direto aos cenários de inscrição da Apple <!--951869-->
Para as contas do Intune criadas depois de janeiro de 2017, o Intune ativou o acesso direto aos cenários de inscrição da Apple através da carga de trabalho Inscrever Dispositivos no portal do Azure. Anteriormente, a pré-visualização da inscrição da Apple apenas estava acessível a partir de ligações no portal do Azure. As contas do Intune criadas antes de Janeiro de 2017 precisam de uma única migração antes de estas funcionalidades ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder à pré-visualização.


## <a name="february-2017"></a>Fevereiro de 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Capacidade para restringir a inscrição de dispositivos móveis<!--747600, 795782-->
O Intune está a adicionar novas restrições de inscrição que controlam as plataformas de dispositivos móveis autorizadas a inscrever. O Intune separa plataformas de dispositivos móveis como iOS, macOS, Android, Windows e Windows Mobile.

* A restrição da inscrição de dispositivos móveis não restringe a inscrição do cliente de PC.  
* Existe uma opção adicional para bloquear a inscrição de dispositivos pessoais apenas para iOS e Android.

O Intune marca todos os novos dispositivos como pessoais, a menos que o administrador de TI os marque como pertencentes à empresa, conforme explicado [neste artigo](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Ver todas as ações em dispositivos geridos <!--677150-->
Um novo relatório __Ações de Dispositivos__ mostra quem efetuou ações remotas como a reposição de dados de fábrica em dispositivos e o estado dessas ações. Veja [O que é a gestão de dispositivos?](device-management.md)

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Os dispositivos não geridos podem aceder a aplicações atribuídas <!--664691-->
Como parte das alterações de estrutura no site do Portal da Empresa, os utilizadores de iOS e Android poderão instalar aplicações atribuídas a eles próprios como "disponíveis sem inscrição" nos seus dispositivos não geridos. Com as suas credenciais do Intune, os utilizadores poderão iniciar sessão no site do Portal da Empresa e ver as listas de aplicações atribuídas a eles próprios. Os pacotes de aplicações das aplicações "disponíveis sem inscrição" estão disponíveis para transferência através do site do Portal da Empresa. As aplicações que requerem inscrição para instalação não são afetadas por esta alteração, uma vez que será solicitado aos utilizadores que inscrevam o seu dispositivo se quiserem instalar essas aplicações.

### <a name="custom-app-categories---748805--"></a>Categorias de aplicações personalizadas <!--748805-->
Agora pode criar, editar e atribuir categorias às aplicações que adicionar ao Intune. Atualmente, as categorias só podem ser especificadas em inglês.
Veja [Como adicionar uma aplicação ao Intune](apps-add.md).

### <a name="display-device-categories---814654--"></a>Mostrar categorias dos dispositivos <!--814654-->
Agora pode ver a categoria do dispositivo como uma coluna na lista de dispositivos. Também pode editar a categoria a partir da secção de propriedades do painel de propriedades do dispositivo. Veja [Como adicionar uma aplicação ao Intune](apps-add.md).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Configurar definições do Windows Update para Empresas <!--776716-->

O Windows como um Serviço é a nova forma de disponibilizar atualizações para o Windows 10. A partir do Windows 10, todas as novas Atualizações de Funcionalidades e Atualizações de Qualidade irão conter o conteúdo de todas as atualizações anteriores. Tal significa que, desde que instale a atualização mais recente, sabe que os dispositivos Windows 10 estão completamente atualizados. Ao contrário das versões anteriores do Windows, agora tem de instalar toda a atualização em vez de parte de uma atualização.

Ao utilizar o Windows Update para Empresas, pode simplificar a experiência de gestão de atualizações para não ter de aprovar atualizações individuais para grupos de dispositivos. Pode continuar a gerir o risco nos seus ambientes ao configurar uma estratégia de implementação de atualizações e o Windows Update irá garantir que as atualizações são instaladas no momento certo. O Microsoft Intune permite configurar definições de atualizações nos dispositivos e dá-lhe a capacidade de diferir a instalação de atualizações. O Intune não armazena as atualizações, mas apenas a atribuição da política de atualização. Os dispositivos acedem ao Windows Update diretamente para obterem as atualizações. Utilize o Intune para configurar e gerir **anéis de atualização do Windows 10**. Um anel de atualização contém um grupo de definições que configuram quando e como as atualizações do Windows 10 são instaladas. Para obter detalhes, veja [Configure Windows Update for Business settings (Configurar definições do Windows Update para Empresas)](windows-update-for-business-configure.md).
