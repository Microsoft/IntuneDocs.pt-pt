# <a name="february-2017"></a>Fevereiro de 2017

## <a name="new-capabilities"></a>Novas Funcionalidades

### <a name="modernizing-the-company-portal-website---753980--"></a>Modernizar o site do Portal da Empresa <!--753980-->
O site do Portal da Empresa irá suportar aplicações visadas para utilizadores que não têm dispositivos geridos. O site será alinhado com outros produtos e serviços Microsoft através de um novo esquema de cores contrastante, ilustrações dinâmicas e um menu de opções, ![Pequena imagem do menu de opções adicionado ao canto superior esquerdo do site do Portal da Empresa](/intune/whats-new/media/CP_hamburger_menu.png) que irá conter os detalhes e informações de contacto do suporte técnico nos dispositivos geridos existentes. A página de destino será reorganizada de forma a realçar as aplicações que estão disponíveis para os utilizadores, com carrosséis para aplicações Em Destaque e Recentemente Atualizadas. Poderá encontrar imagens de antes e depois na [página de atualizações de IU](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

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

Pode encontrar as novidades na pré-visualização do Intune no Azure [aqui](https://docs.microsoft.com/intune-azure/introduction/whats-new).

## <a name="january-2017"></a>Janeiro de 2017

### <a name="new-capabilities"></a>Novas Funcionalidades

<!--### Actions for non-compliance <!--730266
_Actions for non-compliance_ is a new feature of compliance policies that lets you take action on devices that are out of compliance. You can specify single or multiple actions and specify the time period at which those actions must occur. For example, you can notify users of non-compliant devices immediately after the devices become non-compliant through email, or you can block non-compliant devices from accessing corporate resources after a 3-day grace period via Conditional Access.-->

#### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>Relatórios na consola para MAM sem inscrição <!--677961-->
Foram adicionados novos relatórios de proteção de aplicações para dispositivos inscritos e não inscritos. Saiba mais sobre como [monitorizar políticas de gestão de aplicações móveis com o Intune aqui](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune).

<!--### Conditional access for MAM with SharePoint Online <!--679339
You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint Online.  You can get started using Intune mobile app management in the Azure portal. Look for the __Conditional Access__ section in the __Settings__ blade which will include the option for SharePoint Online. This feature will ship separately from the rest of the service release. <!--Find out more about this new feature [here](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

#### <a name="android-711-support---694397--"></a>Suporte para Android 7.1.1 <!--694397-->
Agora, o Intune suporta e gere totalmente o Android 7.1.1.

#### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>Resolver o problema no qual os dispositivos iOS estão inativos ou a consola de administração não consegue comunicar com os mesmos <!--unknown-->
Quando os dispositivos dos utilizadores perdem o contacto com o Intune, pode dar-lhes novos passos de resolução de problemas que os ajudem a recuperar o acesso aos recursos da empresa. Consulte [Os dispositivos estão inativos ou a consola de administração não consegue comunicar com os mesmos](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

### <a name="notices"></a>Avisos

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Utilizar a predefinição para gerir computadores Windows através das definições do Windows<!--663050-->
O comportamento predefinido de inscrição de computadores com Windows 10 irá mudar. As novas inscrições seguirão o fluxo de inscrição do agente MDM normal, em vez de através do agente de PC.

O site do Portal da Empresa irá fornecer aos utilizadores de computadores com Windows 10 instruções para ajudá-los durante o processo de adicionar computadores com Windows 10 como dispositivos móveis. Isto não afetará os PCs atualmente inscritos e a sua organização pode continuar a gerir os computadores com Windows 10 através do agente de PC, [se preferir](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Melhorar o suporte de gestão de aplicações móveis para eliminação seletiva <!--581242-->
Os utilizadores finais receberão orientações adicionais sobre como recuperar o acesso a dados escolares ou profissionais se esses dados forem automaticamente removidos devido à política "Intervalo offline antes de os dados da aplicação serem apagados".<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>As ligações do Portal da Empresa para iOS são abertas dentro da aplicação <!--665954-->
As ligações na aplicação Portal da Empresa para iOS, incluindo as referentes a documentação e aplicações, serão abertas diretamente na aplicação Portal da Empresa através de uma vista do Safari na aplicação. Esta atualização será fornecida separadamente da atualização do serviço em janeiro.

#### <a name="modernizing-the-company-portal-website---753980--"></a>Modernizar o site do Portal da Empresa <!--753980-->
A partir de fevereiro, o site do Portal da Empresa irá suportar aplicações visadas para utilizadores que não têm dispositivos geridos. O site ficará alinhado com outros serviços e produtos da Microsoft ao utilizar um novo esquema de cores de contraste, ilustrações dinâmicas e um menu de opções, ![menu de opções do site do Portal da Empresa](/Intune/whats-new/media/CP_hamburger_menu.png) que irá conter detalhes e informações de contacto de suporte técnico nos dispositivos geridos existentes. A página de destino será reorganizada de forma a realçar as aplicações que estão disponíveis para os utilizadores, com carrosséis para aplicações Em Destaque e Recentemente Atualizadas. Poderá encontrar imagens do aspeto antes e depois da alteração na [página Novidades na IU da Aplicação Intune](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>Nova documentação para políticas de proteção de aplicações <!--583398-->
Atualizámos a nossa documentação para administradores e programadores de aplicações que querem ativar políticas de proteção de aplicações (conhecidas como políticas MAM) nas respetivas aplicações iOS e Android através da Ferramenta de Encapsulamento de Aplicações do Intune ou do SDK da Aplicação Intune.

Foram atualizados os seguintes artigos:

* [Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [Preparar as aplicações iOS para gestão de aplicações móveis com a Ferramenta de Encapsulamento de Aplicações do Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [Introdução ao SDK da Aplicação Microsoft Intune](https://docs.microsoft.com/intune/develop/intune-app-sdk-get-started)
* [Guia para Programadores do SDK da Aplicação Intune para iOS](https://docs.microsoft.com/intune/develop/intune-app-sdk-ios)

Os seguintes artigos são novas adições à biblioteca de documentos:

* [Plugin Cordova do SDK da Aplicação Intune](https://docs.microsoft.com/intune/develop/intune-app-sdk-cordova)
* [Componente Xamarin do SDK da Aplicação Intune](https://docs.microsoft.com/intune/develop/intune-app-sdk-xamarin)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>Barra de progresso ao iniciar o Portal da Empresa no iOS <!--665978-->
O Portal da Empresa para iOS passará a apresentar uma barra de progresso no ecrã inicial para fornecer ao utilizador informações sobre os processos de carregamento que ocorrem. É possível que haja uma implementação faseada da barra de progresso para substituir a animação giratória. Isto significa que alguns dos seus utilizadores verão a nova barra de progresso enquanto outros continuarão a ver a animação giratória.

## <a name="december-2016"></a>Dezembro de 2016

### <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Pré-visualização pública da nova experiência de administrador do Intune no Azure <!--736542-->
No início de 2017 iremos migrar toda a nossa experiência de administrador para o Azure, permitindo uma gestão poderosa e integrada de fluxos de trabalho de EMS principais numa plataforma de serviço moderna extensível com Graph APIs. Antes da disponibilidade geral deste portal para todos os inquilinos do Intune, estamos entusiasmados por anunciar que iremos começar a lançar uma pré-visualização desta nova experiência de administração ainda este mês para selecionar os inquilinos.

A experiência de administração no portal do Azure irá utilizar a já anunciada nova funcionalidade de agrupamento e filtragem; quando o seu inquilino existente é migrado para a nova experiência de agrupamento, o utilizador também será migrado para pré-visualizar a nova experiência de administração do inquilino. Entretanto, pode obter mais informações sobre o que temos reservado para o Microsoft Intune no portal do Azure na nossa [nova documentação](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

__Integração da gestão de despesas de telecomunicações na pré-visualização pública do portal do Azure__ <!--747605--> Estamos agora a começar a pré-visualizar a integração com os serviços de gestão de despesas de telecomunicações (TEM) de terceiros no portal do Azure. Pode utilizar o Intune para impor limites de utilização de dados nacionais e itinerantes. Estamos a começar essas integrações com [Saaswedo](http://www.saaswedo.com). Para ativar esta funcionalidade no seu inquilino de avaliação, [contacte o suporte da Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

### <a name="new-capabilities"></a>Novas Funcionalidades

__Multi-factor authentication em todas as plataformas__ <!--747590--> Agora pode impor a multi-factor authentication (MFA) num grupo selecionado de utilizadores quando estes inscrevem um dispositivo iOS, Android, Windows 8.1+ ou Windows Phone 8.1+ a partir do Portal de Gestão do Azure ao configurar a MFA na aplicação de Inscrição do Microsoft Intune no Azure Active Directory.

__Capacidade de impedir a inscrição do dispositivo móvel__ <!--747596--> O Intune está a adicionar novas restrições de inscrição que controlam as plataformas de dispositivos móveis autorizadas a inscrever. O Intune separa plataformas de dispositivos móveis como iOS, macOS, Android, Windows e Windows Mobile.
* A restrição da inscrição de dispositivos móveis não restringe a inscrição do cliente de PC.
* Especificamente para iOS, existe uma opção adicional para bloquear a inscrição de dispositivos pessoais.

O Intune marca todos os novos dispositivos como pessoais, a menos que o administrador de TI os marque como pertencentes à empresa, conforme explicado [neste artigo](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).

### <a name="notices"></a>Avisos

__Multi-Factor Authentication na Inscrição ao mover para o portal do Azure__ <!--VSO 750545--> Anteriormente, os administradores utilizavam a consola do Intune ou a consola do Gestor de Configuração (anterior à versão de outubro de 2016) para configurar a MFA para inscrições no Intune. Com esta funcionalidade atualizada, irá agora iniciar a sessão no [portal do Microsoft Azure](https://manage.windowsazure.com) com as suas credenciais do Intune e configurar as definições da MFA através do Azure AD. Saiba mais sobre o assunto [aqui](https://aka.ms/mfa_ad).

__Aplicação do Portal da Empresa para Android, agora disponível na China__  <!--VSO 658093--> Estamos a publicar a aplicação do Portal da Empresa para Android para transferência na China. Devido à ausência da Google Play Store na China, os dispositivos Android têm de obter aplicações a partir de mercados de aplicações chineses. A aplicação do Portal da Empresa para Android estará disponível para transferência através das seguintes lojas:
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

A aplicação Portal da Empresa para Android utiliza os Serviços do Google Play para comunicar com o serviço Microsoft Intune. Uma vez que os Serviços do Google Play ainda não estão disponíveis na China, pode demorar até 8 horas a concluir a realização de qualquer uma das seguintes tarefas. 

|Consola de Administração do Intune| Aplicação Portal da Empresa do Intune para Android |Site do Portal da Empresa do Intune|   
|---|---|---|
|Eliminação completa| Remover um dispositivo remoto| Remover dispositivo (local e remoto)|
|Eliminação seletiva| Repor dispositivo| Repor dispositivo|
|Implementações de aplicações novas ou atualizadas| Instalar aplicações de linha de negócio disponíveis| Repor código de acesso do dispositivo|
|Bloqueio remoto|||
|Repor código de acesso|||

### <a name="deprecations"></a>Depreciação

__O Firefox vai deixar de suportar o Silverlight__ <!--VSO TBA--> A Mozilla vai remover o suporte do Silverlight na versão 52 do [browser Firefox](https://www.mozilla.org/firefox) a partir de março de 2017. Como resultado, já não será possível iniciar sessão na consola do Intune existente quando utilizar versões do Firefox superiores a 51. Recomendamos que utilize o Internet Explorer 10 ou 11 para aceder à consola de administração ou uma [versão do Firefox anterior à versão 52](https://ftp.mozilla.org/pub/firefox/releases/). A transição do Intune para o portal do Azure irá permitir suportar um número de [browsers modernos](https://docs.microsoft.com/en-us/azure/azure-preview-portal-supported-browsers-devices) sem dependência do Silverlight.

__Remoção das políticas da pasta a receber móvel do Exchange Online__ <!--770687--> A partir de dezembro, os administradores deixarão de ser capazes de ver ou configurar políticas de caixa de correio móvel do Exchange Online (EAS) na consola do Intune. Esta alteração vai ser implementada em todos os inquilinos do Intune entre dezembro e janeiro. Todas as políticas existentes permanecerão tal como configuradas. Para configurar novas políticas, utilize a Shell de Gestão do Exchange. Saiba mais informações [aqui](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx).

__As aplicações Leitor do Intune AV, Visualizador de Imagens e o Visualizador de PDFs já não são suportadas nos sistemas Android__ <!--747553--> A partir de meados de dezembro de 2016, os utilizadores já não poderão utilizar as aplicações Leitor do Intune AV, Visualizador de Imagens e Visualizador de PDFs. Estas aplicações foram substituídas pela aplicação Azure Information Protection. Saiba mais sobre a aplicação Azure Information Protection [aqui](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq).

## <a name="november-2016"></a>Novembro de 2016

### <a name="new-capabilities"></a>Novas funcionalidades

<!--### View App States for All Platforms in Real Time
App installation status is now shown in real-time in the console. When you previously deployed an app, you had to wait for a targeted device to report back before the app install status was displayed in the Intune console.

### Streamline iOS App Management for your End Users
Intune can now automatically take over management of the previously installed app and no end user action is required.

Previously, if the end user of an enrolled iOS device installed an app from the App Store before you deployed that same app with a deployment action of __Available__, then the end user had to:

1. Open the __Company Portal__.
2. Select the app.
3. Tap __Install__ to enable Intune to take over management of the app.-->

__Novo Portal da Empresa do Microsoft Intune disponível para dispositivos com o Windows 10__ A Microsoft lançou uma nova [aplicação do Portal da Empresa do Microsoft Intune para dispositivos com o Windows 10](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Esta aplicação, que tira partido do novo formato do Windows 10 Universal, irá oferecer ao utilizador uma experiência atualizada na aplicação e experiências idênticas em todos os dispositivos, PC e dispositivos móveis semelhantes com o Windows 10, permitindo que todos tenham a mesma funcionalidade atual.

A nova aplicação também irá permitir aos utilizadores tirarem partido de funcionalidades de plataforma adicionais, como o início de sessão único (SSO) e a autenticação baseada em certificados em dispositivos com o Windows 10. A aplicação será disponibilizada como uma atualização das instalações existentes do Portal da Empresa do Windows 8.1 e do Portal da Empresa do Windows Phone 8.1 a partir da Loja Windows. Para mais detalhes, aceda a [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).

<!--### Support for Windows Store for Business Apps Being Deployed as Available
You can now deploy apps you synchronized from the Windows Store for Business (WSfB) with a deployment action of __Available__ or __Required__. After syncing WSfB apps into Intune, administrators will be able to target those apps as available installs to groups of users. End users will see the deployed WSfB apps as available for install in the Universal Company Portal, where they can choose whether they would like to acquire the apps.

### Conditional Access for MAM with SharePoint Online

You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint online.  You can get started in Intune mobile app management via the Azure portal. Look for the  Conditional Access section in the “Settings” blade which now includes the option for SharePoint online.-->

> [!IMPORTANT]

> __Uma Atualização no Intune e Android for Work__

> Embora possa implementar aplicações Android for Work com uma ação de __Obrigatório__, só pode implementar aplicações como __Disponível__ se os seus grupos do Intune tiverem sido migrados para a nova experiência de grupos do Azure AD.

__O plug-in Cordova para o SDK da Aplicação Intune agora suporta MAM sem inscrição__ Os programadores de aplicações agora podem utilizar o SDK da Aplicação do Intune para o plug-in Cordova para ativar a funcionalidade MAM sem inscrição de dispositivos nas respetivas aplicações baseadas em Cordova para Android e iOS. Pode encontrar o SDK da Aplicação do Intune para o plug-in Cordova [aqui](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam).

__O componente Xamarin para o SDK da Aplicação Intune agora suporta MAM sem inscrição__ Os programadores de aplicações agora podem utilizar o componente Xamarin do SDK da Aplicação do Intune para ativar a funcionalidade MAM sem inscrição de dispositivos nas respetivas aplicações baseadas em Xamarin para Android e iOS. Pode encontrar o componente Xamarin do SDK da Aplicação do Intune [aqui](https://github.com/msintuneappsdk/intune-app-sdk-xamarin).

### <a name="notices"></a>Avisos

__O certificado de assinatura Symantec já não precisa do Portal da Empresa do Windows Phone 8 assinado para carregamento__ O carregamento do certificado de assinatura Symantec já não precisa de uma aplicação do Portal da Empresa do Windows Phone 8 assinado. O certificado pode ser carregado de forma independente.

###<a name="deprecations"></a>Depreciação

__Suporte para o Portal da Empresa do Windows Phone 8__ O suporte para o Portal da Empresa do Windows Phone 8 será preterido. O suporte para as plataformas do Windows Phone 8 e do WinRT foi preterido em outubro de 2016. O suporte para o Portal da Empresa do Windows 8 também foi preterido em outubro de 2016.

## <a name="october-2016"></a>Outubro de 2016

### <a name="conditional-access-for-mobile-application-management"></a>Acesso condicional para a gestão de aplicações móveis
Poderá restringir o acesso ao Exchange Online de modo a permitir o acesso apenas a partir de aplicações que suportam as políticas de gestão de aplicações móveis do Intune, como o Outlook. [Esta nova funcionalidade](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) é totalmente compatível com as políticas de gestão de aplicações móveis do Intune (MAM), uma vez que pode bloquear o acesso a clientes de e-mail incorporados ou a outras aplicações que não tenham sido configuradas com as políticas de MAM do Intune. Isto garante que os seus utilizadores acedem aos dados da sua organização através de aplicações que podem ser protegidas pelos serviços de MAM do Intune. Pode começar a utilizar a gestão de aplicações móveis do Intune através do portal do Azure. Localize a nova secção Acesso Condicional no painel "Definições".

### <a name="conditional-access-for-windows-pcs"></a>Acesso condicional para PCs Windows
Agora pode criar políticas de acesso condicional através da consola de administração do Intune para bloquear o acesso de PCs Windows ao [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) e ao [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune). Também pode criar políticas de acesso condicional para bloquear o acesso a aplicações universais e de ambiente de trabalho do Office.

### <a name="android-for-work-support"></a>Suporte do Android for Work

> [!IMPORTANT]

> Embora possa implementar aplicações Android for Work com uma ação de __Obrigatório__, só pode implementar aplicações como __Disponível__ se os seus grupos do Intune tiverem sido migrados para a nova experiência de grupos do Azure AD.

O Intune faz agora parte do programa Android for Work (AfW). Começaremos a implementar suporte para funcionalidades do AfW a partir deste mês, continuando nos próximos meses. Note que a implementação de aplicações disponíveis do AfW tira partido da nova experiência de agrupamento e filtragem. As contas do Serviço do Intune recentemente aprovisionadas poderão utilizar esta funcionalidade quando o AfW estiver disponível para as mesmas.

<!--Existing Intune customers can use this feature in production once their tenant has been migrated. Existing customers are welcome to create a trial Intune account to plan for and test this feature until their tenant has been migrated. -->

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

### <a name="lookout-integration-to-protect-ios-devices"></a>Integração com a Lookout para a proteção de dispositivos iOS
Em outubro, a Microsoft está a integrar a solução de proteção da Lookout contra ameaças que afetam dispositivos móveis para proteger dispositivos móveis iOS através da deteção de software maligno, aplicações de risco e muito mais. A solução da Lookout ajuda-o a determinar o nível da ameaça, que é configurável. Pode criar uma regra de política de conformidade no Intune para determinar a conformidade dos dispositivos com base na avaliação de riscos feita pela Lookout. Ao utilizar políticas de acesso condicional, pode permitir ou bloquear o acesso a recursos da sua empresa com base no estado de conformidade do dispositivo.

Os utilizadores finais de dispositivos em não conformidade iOS receberão um pedido para os inscrever e terão de instalar a aplicação Lookout for Work nos seus dispositivos, ativar a aplicação e corrigir as ameaças comunicadas na mesma para obterem acesso aos dados da empresa. Saiba como [Configurar e implementar as aplicações do Lookout for Work](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps).
<!--TFS 1319493-->

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

### <a name="intune-app-wrapping-tool-for-android"></a>Ferramenta de Encapsulamento de Aplicações do Intune para Android
Pode utilizar a Ferramenta de Encapsulamento de Aplicações do Intune para ativar as suas aplicações para que utilizem políticas de gestão de aplicações móveis do Intune (MAM). O suporte para políticas de MAM do Intune sem necessidade de inscrição de dispositivos está agora disponível.

### <a name="manage-printing-from-apps-managed-using-mam-policies"></a>Gerir a impressão a partir de aplicações geridas através de políticas de MAM
Já pode evitar a impressão de dados da empresa a partir de aplicações com políticas de MDM. Esta definição está disponível no [Portal do Azure](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) e é suportada em dispositivos [iOS](/Intune/deploy-use/ios-mam-policy-settings) e [Android](/Intune/deploy-use/android-mam-policy-settings).
<!--TFS 1014328-->

### <a name="support-for-fingerprints-on-android-devices"></a>Suporte para impressões digitais em dispositivos Android
Agora, as políticas de gestão de aplicações móveis (MAM) Android permitem que os utilizadores acedam a uma aplicação com a impressão digital, sem precisar de introduzir o PIN. Consulte esta e outras [definições da política de gestão de aplicações móveis para dispositivos Android aqui](/Intune/deploy-use/android-mam-policy-settings).

### <a name="notices"></a>Avisos

__Compatibilidade do Android Samsung KNOX com o Intune__ Determinados modelos do telemóvel Samsung Galaxy Ace não podem ser geridos pelo Intune como dispositivos Samsung KNOX. Ao inscrever estes dispositivos com o Intune, serão geridos como dispositivos Android padrão.

Os números dos modelos afetados são:

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

Não é necessária nenhuma ação adicional sua ou dos utilizadores finais. Para obter mais informações, visite o site do [Samsung KNOX](https://www.samsungknox.com).

__A aplicação do Portal da Empresa para o Windows 8 foi preterida. O suporte para as plataformas Windows Phone 8 e Windows RT está a ser preterido__ A partir de outubro de 2016, o Microsoft Intune irá preterir o suporte para o Portal da Empresa do Windows 8. O Microsoft Intune irá também preterir o suporte para a plataforma do Windows Phone 8 e do Windows RT. Como resultado, não será capaz de inscrever ou atualizar dispositivos Windows Phone 8 e Windows RT.

Pode continuar a gerir dispositivos Windows Phone 8, Windows RT e Windows 8 que já tenham sido inscritos. Atualize dispositivos Windows Phone 8 e Windows 8 para Windows Phone 8.1 e Windows 8.1, e utilize as aplicações do Portal da Empresa para Windows 8.1 e Windows Phone 8.1 correspondentes para continuar a distribuir aplicações para estes dispositivos, sem interrupções.

A partir de novembro de 2016, iremos preterir o suporte para o Portal da Empresa do Windows Phone 8.
<!--TFS 1255391-->

### <a name="whats-coming"></a>Novidades futuras

__Novo Portal da Empresa do Microsoft Intune disponível para dispositivos com o Windows 10__ A Microsoft está a lançar o novo Portal da Empresa do Microsoft Intune para dispositivos com o Windows 10. Esta aplicação, que tira partido do novo formato do Windows 10 Universal, irá oferecer ao utilizador uma experiência atualizada na aplicação e experiências idênticas em todos os dispositivos, PC e dispositivos móveis semelhantes com o Windows 10, permitindo que todos tenham a mesma funcionalidade atual.

A nova aplicação também irá permitir aos utilizadores tirarem partido de funcionalidades de plataforma adicionais, como o início de sessão único (SSO) e a autenticação baseada em certificados em dispositivos com o Windows 10. A aplicação será disponibilizada como uma atualização das instalações existentes do Portal da Empresa do Windows 8.1 e do Portal da Empresa do Windows Phone 8.1 a partir da Loja Windows. Para mais detalhes, aceda a [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).
<!--TFS 1016502-->

## <a name="september-2016"></a>Setembro de 2016
### <a name="new-features-announcements-and-information"></a>Novas funcionalidades, anúncios e informações
* [Acesso condicional do Windows](#windows-conditional-access)
* [Suporte do iOS 10](#ios-10-support)
* [A Ferramenta de Encapsulamento de Aplicações suporta serviços MAM para Android e iOS sem a inscrição de dispositivos](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [A transição de grupos do Intune para o Azure Active Directory terá início em setembro](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Integração com o Lookout para a proteção de dispositivos Android](#lookout-integration-to-protect-android-devices)
* [Atualizações ao Portal da Empresa para Android, iOS e Windows](#company-portal-updates)
* [Glossário do Intune](#intune-glossary)
* [Novidades futuras](#whats-coming)

### <a name="windows-conditional-access"></a>Acesso condicional do Windows
Agora pode criar políticas de acesso condicional através da consola de administrador do Intune para bloquear o acesso de PCs Windows ao Exchange Online e ao SharePoint Online. Também pode criar políticas de acesso condicional para bloquear o acesso a aplicações universais e de ambiente de trabalho do Office.

### <a name="ios-10-support"></a>Suporte do iOS 10
Os cenários MDM e MAM existentes do Intune são compatíveis com o iOS 10. Para obter sugestões, consulte o [Blogue da Equipa de Suporte do Intune (em inglês)](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/).

### <a name="app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios"></a>A Ferramenta de Encapsulamento de Aplicações suporta serviços MAM para Android e iOS sem a inscrição de dispositivos
A Ferramenta de Encapsulamento de Aplicações é uma ferramenta de linha de comandos utilizada para ativar aplicações de linha de negócio (LOB) MAM do Intune para iOS e Android. É a forma mais simples de incorporar o SDK de MAM do Intune na sua aplicação, de modo a que a mesma possa impor as políticas MAM implementadas através do Intune. Ao utilizar políticas de MAM, pode:

1. Encriptar os dados da aplicação.
2. Pedir ao técnico de informação que introduza um número PIN ao iniciar a aplicação.
3. Permitir que a aplicação transfira dados apenas para outras aplicações geridas.
4. Impedir que a aplicação crie cópias de segurança de dados no Android, no iTunes e no iCloud.
5. Permitir as ações Cortar, Copiar e Colar apenas com outras aplicações geridas.

A pré-visualização pública da Ferramenta de Encapsulamento de Aplicações suporta agora serviços de MAM para iOS e Android sem a inscrição de dispositivos em aplicações LOB internas. Isto significa que os seus utilizadores finais não terão de inscrever os respetivos dispositivos com o Intune para utilizar aplicações LOB preparadas para MAM.

Qualquer pessoa pode testar o software de pré-visualização pública e consultar documentos úteis que se encontram no GitHub de msintuneappsdk:

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

Antes de instalar e utilizar a Versão de Pré-lançamento da Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para Android e iOS, tem de:

* Ler os Termos de Licenciamento da Microsoft para a Versão de Pré-lançamento da Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para Android e iOS
* Imprimir e guardar uma cópia dos termos de licenciamento nos seus registos. Ao transferir e utilizar a Versão de Pré-lançamento da Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para Android, está a aceitar esses termos de licenciamento. Caso não aceite os termos, não deverá utilizar o software.
<!---TFS 1235607--->

### <a name="intune-groups-begin-transitioning-to-azure-active-directory-in-september"></a>A transição de grupos do Intune para o Azure Active Directory terá início em setembro
Algumas das novas contas do Intune utilizarão os grupos de segurança do Azure Active Directory em vez dos grupos de utilizadores do Intune. A página de grupos do portal do Intune terá uma ligação que o direciona para o portal de gestão do Azure e que lhe permite saber se está a trabalhar com grupos de segurança.

### <a name="lookout-integration-to-protect-android-devices"></a>Integração com a Lookout para a proteção de dispositivos Android
A Microsoft está a integrar a solução de proteção da Lookout contra ameaças que afetam dispositivos móveis para proteger dispositivos móveis Android através da deteção de malware, aplicações de risco e muito mais. A solução da Lookout ajuda-o a determinar o nível da ameaça, que é configurável. Pode criar uma regra de política de conformidade no Intune para determinar a conformidade dos dispositivos com base na avaliação de riscos feita pela Lookout. Ao utilizar políticas de acesso condicional, pode permitir ou bloquear o acesso a recursos da sua empresa com base no estado de conformidade do dispositivo.

Os utilizadores finais de dispositivos em não conformidade receberão um pedido para os inscrever e terão de instalar a aplicação Lookout for Work em dispositivos Android, ativar a aplicação e corrigir as ameaças comunicadas na mesma para obterem acesso. Para saber mais, consulte [Restringir o acesso com base no dispositivo, na rede e no risco da aplicação](https://docs.microsoft.com/en-us/intune/deploy-use/device-threat-protection).


### <a name="company-portal-updates"></a>Atualizações ao Portal da Empresa

__Android__

<p style="margin-left: 40px">**Inclusão de "Notificações" no Portal da Empresa para Android**<br/>
<p style="margin-left: 40px">Foi adicionado um novo ícone Notificações à homepage do Portal da Empresa para Android. Tocar neste ícone permite aceder à página Notificações, que mostra ao utilizador final todos os itens que necessitam de atenção na aplicação Portal da Empresa, como dispositivos que não estejam em conformidade, atualizações de inscrições e ativação de inscrições. A aplicação Portal da Empresa para iOS já tem esta experiência de notificações. A nova página Notificações permite que o utilizador não tenha de ver a página da Configuração do Acesso da Empresa sempre que iniciar ou retomar o Portal da Empresa, desde que o dispositivo já esteja inscrito. Se criar as suas próprias orientações para o utilizador final, poderá querer atualizar a sua documentação para que a mesma reflita esta alteração. Consulte as capturas de ecrã atualizadas [aqui](https://aka.ms/androidcpupdate).  

__iOS__
<p style="margin-left: 40px">**Alterações ao suporte para a aplicação do Portal da Empresa para iOS**<br/>
<p style="margin-left: 40px">Todos os utilizadores da aplicação Portal da Empresa do Microsoft Intune para iOS têm de utilizar agora a versão mais recente. Os novos utilizadores só poderão transferir a versão mais recente e aos utilizadores atuais será pedido que atualizem para a mesma. A versão mais recente necessita do iOS 8.0 ou posterior, pelo que os utilizadores com dispositivos com versões mais antigas do iOS não poderão utilizar o Portal da Empresa nem inscrevê-los até os atualizarem para o iOS 8.0 ou posterior e atualizarem a aplicação Portal da Empresa para a versão mais recente. Os dispositivos inscritos que tenham versões anteriores ao iOS 8.0 continuarão a ser geridos e listados na Consola de Administração do Intune.
<!---TFS 1283165--->

<p style="margin-left: 40px">**Melhorias na forma como os utilizadores finais de iOS obtêm as aplicações**<br/>
<p style="margin-left: 40px">As seguintes alterações foram feitas aos mosaicos de aplicações na aplicação Portal da Empresa para iOS, para direcionar os utilizadores para diferentes vistas numa única localização – o site do Portal da Empresa – em todas as respetivas aplicações. As restrições da Apple proíbem as aplicações geridas da App Store e de linha de negócio de serem listadas na aplicação Portal da Empresa e exigem também que os utilizadores acedam a vistas diferentes para localizar todas as suas aplicações.

<p style="margin-left: 40px">O mosaico **Aplicações da Empresa** apontava anteriormente para uma lista de todas as aplicações no separador TODOS do site do Portal da Empresa e irá continuar a funcionar da mesma forma. O nome do mosaico foi alterado para **Todas as Aplicações**.

<p style="margin-left: 40px">O mosaico **Outras Aplicações** apontava anteriormente para uma vista, dentro da aplicação Portal da Empresa, que indicava todas as aplicações que a Apple permite que a aplicação Portal da Empresa apresente. O nome do mosaico foi alterado para **Aplicações Em Destaque** e tocar no mosaico irá direcionar os utilizadores para o separador EM DESTAQUE do site do Portal da Empresa.

<p style="margin-left: 40px">O mosaico **Categorias** apontava anteriormente para uma vista, dentro da aplicação Portal da Empresa, que indicava categorias de aplicações. O nome do mosaico não foi alterado, mas aponta agora para o separador CATEGORIAS do site do Portal da Empresa. Pode encontrar capturas de ecrã atualizadas [aqui](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
  <!---TFS 1317133--->

<p style="margin-left: 40px">**Solicite a instalação da aplicação Managed Browser do iOS se o Profissional de TI definir esse requisito para uma aplicação**<br/>
<p style="margin-left: 40px">Se tiver configurado um Web Clip para ser aberto apenas no browser gerido e este não estiver instalado num dispositivo, a aplicação Portal da Empresa irá pedir ao utilizador para instalar o browser gerido antes de poder instalar o Web Clip.
  <!---TFS 1228570--->

__Windows__
<p style="margin-left: 40px">**Botão de feedback adicionado à aplicação Portal da Empresa para Windows Phone 8.1**<br/>
<p style="margin-left: 40px">A aplicação Portal da Empresa para Windows 8.1 permite que os utilizadores finais enviem feedback sobre a aplicação através do novo botão "enviar feedback". Para localizar o botão, os utilizadores têm de tocar no menu de "três pontos"que se encontra no canto inferior direito do ecrã da aplicação Portal da Empresa e, em seguida, tocar em **enviar feedback**. O feedback recolhido é anónimo e irá ajudar a Microsoft a melhorar a experiência da aplicação Portal da Empresa para os utilizadores.
<!---TFS 1317806--->

### <a name="intune-glossarybr"></a>Glossário do Intune</br>
Adicionámos um novo [tópico de glossário](https://docs.microsoft.com/intune/understand-explore/intune-glossary) à biblioteca para o ajudar a compreender alguns dos termos utilizados no produto Intune.

## <a name="august-2016"></a>Agosto de 2016
### <a name="app-management"></a>Gestão de aplicações
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

__Aplicações ocultas e apresentadas para iOS 9.3__ Para os dispositivos com o iOS 9.3 ou posterior, pode utilizar a lista das aplicações ocultas e apresentadas na política de configuração geral do iOS para:
- Especificar uma lista de aplicações que serão ocultas dos utilizadores. Os utilizadores não poderão ver ou iniciar estas aplicações.
- Especificar uma lista de aplicações que os utilizadores poderão ver e iniciar. Mais nenhuma outra aplicação pode ser vista ou lançada.

As aplicações que pode especificar incluem ambas as aplicações implementadas e as aplicações incorporadas do iOS como Mensagens e Notas. Para obter detalhes, consulte [Definições de política para iOS no Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)
<!---TFS 1279009 checked--->
__Política de aplicações permitidas e bloqueadas para dispositivos Samsung KNOX__ Agora pode configurar uma política personalizada para os dispositivos Samsung KNOX que lhe permite criar um dos seguintes:
- Uma lista de aplicações que estão bloqueadas de executar no dispositivo. Mesmo que esteja instalada, uma aplicação definida na lista de bloqueadas não pode ser ativada no dispositivo.
- Uma lista de aplicações que os utilizadores do dispositivo estão autorizados a instalar a partir da loja Google Play. Mais nenhuma outra aplicação pode ser instalada a partir da loja.

Estas definições só podem ser utilizadas por dispositivos que executem Samsung KNOX.
Para obter detalhes, consulte [Utilizar políticas personalizadas para permitir e bloquear aplicações para dispositivos Samsung KNOX](https://docs.microsoft.com/en-us/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps).
<!---TFS 1311629 checked --->

__Novas aplicações compatíveis com as políticas de gestão de aplicações móveis (MAM)__ A aplicação Yammer para [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) e [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) é agora compatível com as [políticas de gestão de aplicações móveis do Intune (MAM)](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), quer o dispositivo esteja inscrito ou não.

Para obter uma lista completa das aplicações compatíveis com o MAM, consulte o site dos [parceiros de aplicações do Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

__Aplicações do Visualizador do Intune__ Com o lançamento da nova aplicação de partilha RMS, iremos remover as seguintes aplicações do Visualizador do Intune, a partir de agosto de 2016:
- Visualizador AV do Intune
- Visualizador de PDFs do Intune
- Visualizador de Imagens do Intune para Android a partir do Google Play

Em vez de utilizar as aplicações do Visualizador do Intune, recomendamos que utilize a nova [aplicação Rights Management (partilha RMS) para Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app), o que lhe permite implementar uma aplicação em vez de três aplicações separadas para ver com segurança os ficheiros empresariais em dispositivos Android. Quando a aplicação do visualizador do Intune deixar de ser suportada, será removida da Google Store e indisponibilizada para utilização futura.

### <a name="device-management"></a>Gestão de dispositivos
__Suporte para Android 7.0__ O Intune fornece suporte no "dia 0" para o lançamento do sistema operativo Android 7.0 para dispositivos móveis.
<!---TFS 1262053--->
### <a name="google-removal-of-remote-passcode-reset-capability-on-android-70-devices"></a>A remoção da funcionalidade de reposição de códigos de acesso remotos por parte da Google em dispositivos com o Android 7.0
A Google está a remover a funcionalidade dos administradores de TI e os utilizadores finais poderem repor remotamente o código de acesso a dispositivos com o Android 7.0. Anteriormente, os administradores de TI podiam repor remotamente o código de acesso de um utilizador, assim como os utilizadores finais podiam repor os seus códigos de acesso a partir do site do Portal da Empresa.



### <a name="company-portal-updates"></a>Atualizações ao Portal da Empresa
__Site do Portal da Empresa__
- **Ligação de comentários do Portal da Empresa para a Microsoft** <br/>
O site do Portal da Empresa permite que os utilizadores finais toquem numa nova ligação de "Comentários", na parte inferior da página, para enviar comentários à Microsoft sobre as suas experiências com o site. Os comentários recolhidos são anónimos e vão ajudar a Microsoft a melhorar a experiência do site do Portal da Empresa para os utilizadores.
<!--- TFS 1313657 checked--->

__iOS__
- **Versão mínima do Managed Browser para iOS atualizada para 8.0**<br/>
A aplicação Microsoft Intune Managed Browser para iOS foi atualizada para suportar dispositivos com o iOS 8.0 ou posterior. Embora os dispositivos iOS 7.1 continuem a poder utilizar a aplicação Managed Browser atual, incentive os seus utilizadores a atualizarem para o iOS 8.0 ou posterior para aceder e tirar partido das novas funcionalidades do Managed Browser.  
<!---TFS 1313253 checked--->

### <a name="whats-coming"></a>Novidades futuras
__Os Grupos do Intune irão transitar para os Grupos do Azure Active Directory a partir de setembro de 2016__ O Intune está a criar uma nova experiência de gestão de grupos que utiliza os grupos de segurança do Azure Active Directory (AAD) como grupos de utilizadores e de dispositivos no Intune. Estes grupos vão ser utilizados para a gestão de todos os grupos, implementações de políticas e implementações de perfis **quando introduzirmos o novo portal de administração do Intune baseado no Azure**.

Esta experiência nova evita que tenha de duplicar grupos entre os serviços, **permite-lhe aceder a algumas funcionalidades novas dos grupos do Azure Active Directory Premium (AADP)** e proporciona extensibilidade através da utilização do PowerShell e do Graph. Esta alteração também vai unificar a experiência de gestão de grupos ao nível da gestão de mobilidade empresarial.

Para permitir a mudança para os Grupos de Segurança, a experiência na **consola de administração atual** vai sofrer algumas alterações. **Estas alterações e a utilização dos grupos de segurança do AAD serão registadas na documentação do Intune**.

Os clientes que só agora estão a utilizar o Intune verão **algumas das alterações aos grupos de segurança antes dos inquilinos atuais**.

Para além das alterações à gestão de grupos, **as funcionalidades seguintes vão ser preteridas**:
- Excluir membros ou grupos ao criar um novo grupo
- Grupos **Utilizadores desagrupados** e **Dispositivos desagrupados**
- **Gerir Grupos** na função Administrador de Serviço
- Alertas personalizados com base em grupos para Regras de Notificação
- Ordenar com grupos em relatórios
<!--- TFS 1295329--->

__Inclusão de "Notificações" no Portal da Empresa para Android__ Vamos lançar uma atualização para o Portal da Empresa para Android em setembro, que vai introduzir um ícone **Notificações** novo na home page. Tocar neste ícone vai permitir aceder à página **Notificações**, que mostrará ao utilizador final todos os itens que requerem atenção na aplicação do Portal da Empresa, como dispositivos não conformes, atualizações de inscrições e ativação de inscrições. Se também utilizar a aplicação do Portal da Empresa para iOS, já vai beneficiar da experiência de notificações. Com a introdução da página **Notificações**, não verá a página **Configuração do Acesso da Empresa** sempre que iniciar ou retomar o Portal da Empresa para Android, desde que o dispositivo já esteja inscrito. Sabemos que muitos dos nossos utilizadores criaram orientações para o utilizador final e agradecemos o aviso antecipado sempre que as suas orientações/capturas de ecrã precisem de ser atualizadas. Atualize a sua documentação de modo a refletir a alteração futura à experiência. Pode obter as capturas de ecrã atualizadas em https://aka.ms/androidcpupdate.  

### <a name="service-deprecation"></a>Depreciação de serviço
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **Alterações ao suporte para a aplicação do Portal da Empresa para iOS**<br/>
Em setembro, todos os utilizadores da aplicação do Portal da Empresa do Microsoft Intune para iOS terão de utilizar a última versão. Os novos utilizadores só conseguirão transferir a versão mais recente e os utilizadores atuais terão de atualizar para a mesma. A versão mais recente requer o iOS 8.0 ou posterior, pelo que os utilizadores com dispositivos com versões do iOS mais antigas não poderão utilizar o Portal da Empresa nem inscrever enquanto não os atualizarem para o iOS 8.0 ou posterior e atualizarem a aplicação do Portal da Empresa para a última versão. Os dispositivos inscritos que tenham versões anteriores ao iOS 8.0 continuarão a ser geridos e listados na Consola de Administração do Intune.  

- **Versão mínima do Managed Browser para iOS atualizada para 8.0**<br/>
Em agosto, o Intune vai lançar uma aplicação atualizada do Microsoft Intune Managed Browser para iOS que só irá suportar dispositivos com o iOS 8.0 ou posterior. Embora os dispositivos iOS 7.1 continuem a poder utilizar a aplicação Managed Browser atual, incentive os seus utilizadores a atualizarem para o iOS 8.0 ou posterior para acederem e tirarem partido das novas funcionalidades do Managed Browser.  
<!---TFS 1313253--->

- **As aplicações do Portal da Empresa para Windows 8 e Windows Phone 8 serão preteridas a partir de setembro de 2016** <br/>
A partir de setembro de 2016, o Microsoft Intune vai terminar o suporte para as aplicações do Portal da Empresa do Microsoft Intune nas plataformas Windows Phone 8 e Windows 8. Para continuar a distribuir aplicações para estes dispositivos, atualize-os para o Windows 8.1 e o Windows Phone 8.1 e utilize as aplicações do Portal da Empresa para Windows 8.1 e o Windows Phone 8.1 correspondentes.
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->
