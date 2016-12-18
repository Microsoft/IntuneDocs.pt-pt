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

<!--Existing Intune customers can use this feature in production once their tenant has been migrated. Existing customers are welcome to create a trial Intune account to plan for and test this feature until their tenant has been migrated. Any questions on grouping and targeting timelines, please contact our [migration team](mailto:intunegrps@microsoft.com).-->

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

Os utilizadores finais de dispositivos em não conformidade receberão um pedido para os inscrever e terão de instalar a aplicação Lookout for Work em dispositivos Android, ativar a aplicação e corrigir as ameaças comunicadas na mesma para obterem acesso. Para saber mais, consulte [Restringir o acesso com base no dispositivo, na rede e no risco da aplicação](https://docs.microsoft.com/en-us/intune/deploy-use/restrict-access-based-on-device-network-app-risk).


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

## <a name="july-2016"></a>Julho de 2016
### <a name="app-management"></a>Gestão de aplicações

__Melhorar a experiência de atualização de perfis de aprovisionamento de aplicações__ As aplicações móveis de linha de negócio iOS da Apple são criadas com um perfil de aprovisionamento incluído e o respetivo código assinado com um certificado. Quando as aplicações são executadas num dispositivo iOS, o iOS confirma a integridade das mesmas e aplica as políticas definidas pelo perfil de aprovisionamento.

Geralmente, o certificado de assinatura da empresa que utiliza para assinar as aplicações dura três anos. No entanto, o perfil de aprovisionamento expira após um ano. Com esta atualização, o Intune proporciona-lhe as ferramentas para implementar proativamente uma nova política de perfil de aprovisionamento em dispositivos que tenham aplicações prestes a expirar enquanto o certificado ainda é válido. Para obter mais informações, consulte [Use iOS mobile provisioning profile policies to keep your line of business apps up to date (Utilizar políticas de perfis de aprovisionamento móvel de iOS para manter as aplicações de linha de negócio atualizadas)](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->

__Está disponível o SDK para Xamarin para aplicações do Intune__ O componente Xamarin do SDK da Aplicação Intune permite-lhe ativar as funcionalidades de gestão de aplicações móveis do Intune nas suas aplicações móveis iOS e Android criadas com Xamarin. Pode obter o componente no [arquivo Xamarin](https://components.xamarin.com/view/Microsoft.Intune.MAM) ou na [página do Microsoft Intune no Github](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

### <a name="device-management"></a>Gestão de dispositivos
__Aumento nos limites de inscrição de dispositivos__ O Intune aumentou o limite máximo de inscrição de dispositivos configuráveis de 5 para 15 dispositivos por utilizador.
<!---TFS 1289896 --->

__Integração do TeamViewer para PCs Windows com o software de cliente Intune__
 A integração do [TeamViewer](https://www.teamviewer.com) para PCs Windows que executem o cliente do Intune vai permitir estabelecer sessões de assistência remota com PCs Windows para ajudar a dar apoio aos departamentos de suporte técnico ao utilizador final. Isto inclui o Windows 7, 8, 8.1 e o Windows 10. Para obter mais informações, consulte [Tarefas de gestão comuns do PC Windows com o computador cliente do Microsoft Intune](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).
<!---TFS 1284856--->

### <a name="company-portal-updates"></a>Atualizações ao Portal da Empresa

__Site do Portal da Empresa__
- **Experiência do utilizador melhorada na inscrição de dispositivos Windows**<br/>
Se estiver a utilizar o acesso condicional, os passos de inscrição para Windows 8.1, dispositivos com o Windows 10 e o Windows 10 Mobile foram clarificados no Web site do Portal da Empresa. Agora, os utilizadores vão ver dois passos separados, “Inscrição de dispositivos” e “Workplace Join”, o que lhes permite ver mais facilmente o estado dos respetivos dispositivos e concluir o processo se se depararem com falhas na Workplace Join (WPJ). Espera-se que os passos separados também simplifiquem o processo de resolução de problemas para os administradores de TI. Anteriormente, quando os utilizadores finais tentavam inscrever e todos os passos da inscrição eram bem-sucedidos, menos a WPJ, o dispositivo inscrito não aparecia na lista de dispositivos para os utilizadores identificarem, confundindo-os.

__Android__
- **Aplicação do Portal da Empresa para Android**<br/>
Se os utilizadores finais do Azure virem uma mensagem de erro a dizer que falta um certificado necessário nos respetivos dispositivos, podem tocar num botão chamado “Como resolver isto” para obter [passos](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) para instalar o certificado em falta. Se os utilizadores concluírem os passos, mas virem uma mensagem de erro “certificado em falta” adicional, é-lhes pedido que contactem o administrador de TI e lhe forneçam esta [ligação](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues), que contém os passos que os administradores de TI podem utilizar para corrigir o problema do certificado.

- **Restringir instalações de aplicações sideload em dispositivos inscritos**<br/>
Os dispositivos Android já não podem instalar aplicações através do Web site do Portal da Empresa, a não ser que esses dispositivos tenham sido inscritos no Intune com a aplicação do Portal da Empresa para Android do Intune.
<!---TFS 1299082--->

__iOS__
- **Alterações às contas de Gestores de Inscrição de Dispositivos na aplicação do Portal da Empresa para iOS**<br/>
Para melhorar o desempenho e o dimensionamento, o Intune deixa de mostrar todos os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel **Os Meus Dispositivos** da aplicação do Portal da Empresa para iOS. Apenas é apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa.

O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só pode ser efetuada a partir da consola de administração do Intune. Além disso, o Intune está a descontinuar a utilização de contas DEM com o Programa de registo de dispositivos da Apple ou com a ferramenta Apple Configurator. Ambos os métodos de inscrição já suportam a inscrição sem a ação do utilizador para dispositivos iOS partilhados.

Utilize apenas contas DEM quando a inscrição sem a ação do utilizador para dispositivos partilhados não estiver disponível. Para obter mais informações, consulte [Inscrever dispositivos pertencentes à empresa com o Gestor de Inscrição de Dispositivos no Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

### <a name="change-of-names-for-windows-features"></a>Alteração de nomes de funcionalidades do Windows
- O [Microsoft Passport para Windows](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) é agora conhecido como **Windows Hello para Empresas**.
- A [Proteção de dados da empresa](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) é agora conhecida como **Windows Information Protection**.

## <a name="june-2016"></a>Junho de 2016
### <a name="intune-service-health"></a>Estado de funcionamento do serviço do Intune
As informações de estado de funcionamento do serviço do Intune foram movidas para uma localização central com outros serviços Microsoft. Agora, pode encontrar estas informações no portal de gestão do Office 365, em Estado de Funcionamento do Serviço. Para obter mais informações, consulte [esta mensagem do blogue](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### <a name="app-management"></a>Gestão de aplicações
- **Experiência de configuração da política de dados empresariais do Windows 10 melhorada.** Efetuamos melhoramentos para a experiência de configuração da política de proteção de dados empresariais do Windows 10 sobre a criação de regras de aplicação, como especificar a definição de limites de rede e outras definições de proteção de dados empresariais. Para saber mais, consulte [Criar uma política de proteção de dados empresariais (EDP) através do Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


### <a name="device-management"></a>Gestão de dispositivos
- **Definição de política do Windows Defender contra aplicações potencialmente indesejáveis.** Uma nova definição do Windows Defender com o nome **Deteção de Aplicação Potencialmente Indesejável** foi adicionado à política de configuração geral para dispositivos com o Windows 10 e o Windows 10 Mobile. Pode utilizar esta definição para proteger computadores de secretária Windows inscritos contra software em execução classificado pelo Windows Defender como potencialmente indesejado. Pode proteger contra estas aplicações em execução ou utilizar o modo de auditoria para relatar quando uma aplicação potencialmente indesejável é instalada. Para obter mais informações, consulte [Definições de política do Windows 10 no Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

### <a name="conditional-access"></a>Acesso condicional
- **Política de controlo de acesso à rede Cisco ISE para o Intune.**  Os clientes que utilizam o Motor de Serviço de Identidade Cisco (ISE) 2.1 e que também utilizam o Microsoft Intune podem definir uma política de controlo de acesso de rede no ISE.

    Ao utilizar esta política, os dispositivos que precisa de ligar à rede através de Wi-Fi ou VPN devem cumprir seguintes condições antes de lhes ser concedido acesso:

    * Deve ser gerido pelo Intune
    * Deve ser compatível com todas políticas de conformidade do Intune implementadas

 Os utilizadores finais de dispositivos não conformes serão solicitados para inscrever-se e para retificar quaisquer problemas de compatibilidade para obter acesso.
- **Acesso condicional para browser.** Pode definir uma política de acesso condicional para o [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) e o [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) para que apenas os dispositivos iOS e Android geridos e compatíveis possam ser acedidos a partir de Web browsers suportados. Aos utilizadores finais que tentarem iniciar sessão no Outlook Web Access (OWA) e em sites do SharePoint com dispositivos iOS e Android será pedido que inscrevam o respetivo dispositivo no Intune, bem como que corrijam quaisquer problemas de não conformidade, para poderem concluir o início de sessão.
<!---TFS 1175844--->

- **O Dynamics CRM Online suporta o acesso condicional.** Pode definir uma política de acesso condicional para o [Dynamics CRM Online](/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) para que apenas dispositivos iOS e Android geridos e compatíveis possam aceder ao mesmo. Aos utilizadores finais que tentarem iniciar sessão na aplicação móvel Dynamics CRM Online em dispositivos iOS e Android será pedido que se inscrevam primeiro no Intune e que corrijam quaisquer problemas de não conformidade para que o início de sessão possa ser concluído.
<!---TFS1295358--->

### <a name="intune-company-portal-updates"></a>Atualizações ao Portal da Empresa do Intune

__Aplicação do Portal da Empresa para Android__

- Quando os administradores de TI aplicam a nova política "Exigir que os dispositivos não permitam a instalação de aplicações a partir de origens desconhecidas (Android 4.0 +)", os utilizadores finais com Android 4.0 ou dispositivos posteriores irão ver a mensagem "A instalação tem de ser desativada a partir de origens desconhecidas." Os utilizadores terão de ir para **Definições** > **Segurança** e desativar **Origens desconhecidas**. Uma ligação na mensagem de compatibilidade permite aos utilizadores obterem mais [informações](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) sobre a mensagem e por que motivo é necessário desativar a definição.

- Quando os administradores de TI aplicam a nova política "Exigir que os dispositivos ativem a análise de ameaças de segurança em aplicações (Android 4.0 +)", os utilizadores finais com Android 4.0 ou dispositivos posteriores irão ver a mensagem "Analisar se o dispositivo apresenta ameaças de segurança." Os utilizadores terão de ir para **Definições** > **Google** > **Segurança** e ativar **Analisar se o dispositivo apresenta ameaças de segurança**. Uma ligação na mensagem de compatibilidade permite aos utilizadores obterem mais [informações](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sobre a mensagem e por que motivo é necessário ativar a definição.

- Quando os administradores de TI aplicam a nova política "Exigir a desativação da depuração de USB (Android 4.2 +)", os utilizadores finais com Android 4.2 ou dispositivos posteriores irão ver a mensagem "A depuração de USB deve ser desativada." Os utilizadores terão de ir para **Definições** > **Opções de programador** e desativar **Depuração de USB**." Uma ligação na mensagem de compatibilidade permite aos utilizadores obterem mais [informações](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) sobre a mensagem e por que motivo é necessário desativar a definição.

- Quando os administradores de TI aplicam a nova política "Nível mínimo de patch de segurança do Android (Android 6.0 +)", os utilizadores finais com Android 6.0 ou dispositivos posteriores irão ver a mensagem "Este dispositivo não cumpre o nível mínimo de patch de segurança do Android." Os utilizadores têm de instalar o patch de segurança necessário. Uma ligação na mensagem de compatibilidade permite aos utilizadores obter [informações](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sobre como instalar o patch de segurança necessário e ver que patch de segurança está atualmente instalado.

__Aplicação do Portal da Empresa para iOS__

- Quando os utilizadores finais estiverem a instalar aplicações de linha de negócio, irão ver agora uma experiência de instalação de aplicações melhorada. Se a instalação da aplicação estiver a demorar muito tempo, os utilizadores podem sincronizar manualmente os respetivos dispositivos para forçar a continuação do processo de sincronização. Para ver as instruções para utilizadores finais, consulte [Sincronizar o dispositivo iOS manualmente](/Intune/EndUser/sync-your-device-manually-ios).

- A aplicação do Portal da Empresa do Microsoft Intune para iOS foi atualizada para suportar a versão 8.0 do iOS e posteriores. Esta atualização significa que os utilizadores finais só podem instalar a aplicação do Portal da Empresa e inscrever dispositivos novos no Intune se estes executarem a versão 8.0 do iOS ou posterior. Os utilizadores que já inscreveram dispositivos que executem uma versão não suportada do iOS podem continuar a utilizar a aplicação Portal da Empresa que está nos dispositivos deles.


<!--HONumber=Dec16_HO1-->


