---
title: Novidades do Microsoft Intune
titlesuffix: Azure portal
description: Descobrir as novidades do Intune no portal do Azure
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 09/18/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 08a22a1fa6829807860b6278181dd638f1049770
ms.sourcegitcommit: 0d9bfd92bf5958261ed83b1f150bf207b7ba7e56
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/21/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Novidades do Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Saiba mais sobre as novidades todas as semanas no Microsoft Intune. Pode também descobrir quais são as [alterações futuras](#whats-coming), os [avisos importantes](#notices) sobre o serviço e as informações sobre [versões anteriores](whats-new-archive.md).

> [!Note]
> Muitas destas funcionalidades também serão suportadas, em algum momento, em implementações híbridas com o Configuration Manager. Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   

## <a name="week-of-september-11-2017"></a>Semana de 11 de setembro de 2017

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo----1475932---"></a>Notificações push adicionais para utilizadores finais na aplicação Portal da Empresa para Android Oreo <!---1475932--->

Os utilizadores finais receberão notificações adicionais a indicar quando a aplicação Portal da Empresa para Android Oreo está a efetuar tarefas em segundo plano, como a obtenção de políticas do serviço do Intune. Isto aumenta a transparência para os utilizadores finais sobre quando o Portal da Empresa está a efetuar tarefas administrativas nos respetivos dispositivos. Isto faz parte da [otimização geral da IU do Portal da Empresa](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) para a aplicação Portal da Empresa para Android Oreo. 

#### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Informe os utilizadores finais acerca das informações do dispositivo que podem ser vistas para iOS <!--739894--> 

Adicionámos o **Tipo de Propriedade** ao ecrã Detalhes do Dispositivo na aplicação Portal da Empresa para iOS. Isto permite que os utilizadores obtenham mais informações sobre privacidade diretamente a partir desta página, através da documentação de utilizador final do Intune. Também poderão localizar estas informações no ecrã Acerca de. 

#### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Permitir que os utilizadores finais acedam à aplicação Portal da Empresa para Android sem inscrição <!---1169910--->

Em breve, os utilizadores finais não terão de inscrever os dispositivos para aceder à aplicação Portal da Empresa para Android. Os utilizadores finais em organizações que utilizam Políticas de Proteção de Aplicações deixarão de receber pedidos para inscrever os dispositivos quando abrem a aplicação Portal da Empresa. Os utilizadores finais também poderão instalar aplicações a partir do Portal da Empresa sem inscrever o dispositivo. 


#### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Linguagem de compreensão mais fácil na aplicação Portal da Empresa para Android <!---1396349--->  

O texto do processo de inscrição da aplicação Portal da Empresa para Android foi simplificado para facilitar a inscrição dos utilizadores finais. Se tiver documentação de inscrição personalizada, deve atualizá-la para refletir os novos ecrãs. Poderá encontrar imagens de exemplo na nossa página de [Atualização da IU para aplicações de utilizadores finais do Intune](whats-new-app-ui.md#week-of-september-11-2017).

#### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Aplicação Portal da Empresa do Windows 10 adicionada à política de permissão do Windows Information Protection <!-- 677129 -->

A aplicação Portal da Empresa do Windows 10 foi atualizada para suportar o Windows Information Protection (WIP). A aplicação pode ser adicionada à política de permissão do WIP. Com esta alteração, a aplicação já não tem de ser adicionada à lista **Excluídas**. 


## <a name="week-of-august-21-2017"></a>Semana de 21 de agosto de 2017

### <a name="device-enrollment"></a>Inscrição de dispositivos
#### <a name="improvements-to-device-overview----1404453---"></a>Melhorias na descrição geral do dispositivo <!-- 1404453 -->  
As melhorias na descrição geral do dispositivo apresentam agora os dispositivos inscritos, mas excluem os dispositivos geridos pelo Exchange ActiveSync. Os dispositivos do Exchange ActiveSync não têm as mesmas opções de gestão que os dispositivos inscritos. Para ver o número de dispositivos inscritos e o número de dispositivos inscritos por plataforma, no Intune, no portal do Azure, aceda a **Dispositivos** > **Descrição Geral**.

### <a name="device-management"></a>Gestão de dispositivos
#### <a name="improvements-to-device-inventory-collected-by-intune"></a>Melhorias no inventário de dispositivos recolhido pelo Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
Neste lançamento, fizemos as seguintes melhorias às informações do inventário recolhido pelos dispositivos que gere:
 
-   Em dispositivos Android, pode agora adicionar uma coluna ao inventário do dispositivo que mostra o nível de atualização mais recente para cada dispositivo. Adicione a coluna **Nível de atualização de segurança** à sua lista de dispositivos para ver isto.
-   Quando filtrar a vista do dispositivo, agora pode filtrar dispositivos pela sua data de inscrição. Por exemplo, pode apresentar apenas dispositivos que foram inscritos após uma data especificada por si.
-   Melhorámos o filtro utilizado pelo item **Data do Último Registo**.
-   Na lista de dispositivos, agora pode ver o número de telemóvel dos dispositivos pertencentes à empresa.
Além disso, pode utilizar o painel de filtros para procurar dispositivos por número de telemóvel.
 
Para obter mais detalhes sobre o inventário de dispositivos, veja [Como ver o inventário de dispositivos do Intune](device-inventory.md).

#### <a name="conditional-access-support-for-macos-devices"></a>Suporte de acesso condicional para dispositivos macOS 
<!-- 720172 -->
Agora pode definir uma política de acesso condicional que exige que os dispositivos Mac estejam inscritos no Intune e em conformidade com as políticas de conformidade do dispositivo. Por exemplo, os utilizadores podem transferir a aplicação Portal da Empresa do Intune para macOS e inscrever os dispositivos Mac no Intune. O Intune avalia se o dispositivo Mac está ou não em conformidade com os requisitos, tal como o PIN, versão do SO e Integridade do Sistema.

- Saiba mais sobre o [suporte de acesso condicional para dispositivos macOS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

#### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>A aplicação Portal da Empresa para macOS está em pré-visualização pública <!---1484796--->
A aplicação Portal da Empresa para macOS está agora disponível como parte da pré-visualização pública para acesso condicional no Enterprise Mobility + Security. Esta versão suporta o macOS 10.11 e posterior. Obtenha-a em [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


#### <a name="new-device-restriction-settings-for-windows-10"></a>Novas definições de restrição de dispositivos para Windows 10    
<!--1063965, 1308850  -->
Nesta versão, adicionámos novas definições ao [perfil de restrição de dispositivos Windows 10](/intune/device-restrictions-windows-10) nas seguintes categorias:

-   Windows Defender SmartScreen
-   Loja de aplicações

#### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Atualizações ao perfil de dispositivo de proteção de ponto final do Windows 10 para as definições do BitLocker
<!--1459533 -->    
Neste lançamento, fizemos as seguintes melhorias à forma como as definições do BitLocker funcionam num perfil de dispositivo de proteção de ponto final do Windows 10:
 
Em **Definições de unidades de SO do BitLocker**, na definição **BitLocker com chip do TPM não compatível**, selecionar **Bloquear** fazia anteriormente com que o BitLocker fosse permitido. Corrigimos isto para que o BitLocker seja bloqueado quando a opção é selecionada.
Em **Definições de unidades de SO do BitLocker**, na definição **Agente de recuperação de dados baseada em certificados**, pode agora bloquear explicitamente o agente de recuperação de dados baseada em certificados. No entanto, por predefinição, o agente é permitido.
Em **Definições de unidades de dados fixas do BitLocker**, na definição **Agente de recuperação de dados**, pode agora bloquear explicitamente o agente de recuperação de dados.
Para obter mais informações, veja [Endpoint protection settings for Windows 10 and later (Definições de proteção de ponto final para o Windows 10 e versões posteriores)](endpoint-protection-windows-10.md).


### <a name="app-management"></a>Gestão de aplicações
#### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nova experiência de início de sessão para utilizadores do Portal da Empresa para Android e das Políticas de Proteção de Aplicações <!-- 621669 -->
Os utilizadores finais podem agora procurar aplicações, gerir dispositivos e ver informações de contacto de TI com a aplicação Portal da Empresa para Android sem inscrever os respetivos dispositivos Android. Além disso, se um utilizador final já utilizar uma aplicação protegida por Políticas de Proteção de Aplicações do Intune e iniciar o Portal da Empresa para Android, deixará de receber um pedido para inscrever o dispositivo.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Nova definição para ativar e desativar a otimização da bateria na aplicação Portal da Empresa para Android <!--1405990-->
A página **Definições** na aplicação Portal da Empresa para Android tem uma nova definição para permitir aos utilizadores desativar facilmente a otimização da bateria para as aplicações Microsoft Authenticator e Portal da Empresa. O nome da aplicação apresentado na definição irá variar consoante a aplicação que gere a conta profissional. Recomendamos que os utilizadores desativem a otimização da bateria para melhorar o desempenho das aplicações de trabalho que sincronizam e-mails e dados. 

#### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>Suporte de várias identidades do OneNote para iOS      <!-- 1234281 -->
Os utilizadores finais podem agora utilizar contas diferentes (profissionais e pessoais) com o Microsoft OneNote para iOS. As políticas de proteção de aplicações podem ser aplicadas a dados empresariais em blocos de notas de trabalho sem afetar os blocos de notas pessoais. Por exemplo, uma política pode permitir que um utilizador encontre informações em blocos de notas de trabalho, mas impedir que o utilizador copie e cole dados empresariais do bloco de notas de trabalho num bloco de notas pessoal.
 
- Saiba mais sobre as aplicações que suportam a [proteção de aplicações e várias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) com o Intune.

#### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Novas definições para permitir e bloquear aplicações em dispositivos Samsung KNOX Standard
<!-- 1305423 822899-->  
Neste lançamento, estamos a adicionar novas [definições de restrição de dispositivos](device-restrictions-android.md) que lhe permitem especificar as seguintes listas de aplicações:
 
- Aplicações que os utilizadores têm permissão para instalar
- Aplicações que os utilizadores não têm permissão para executar
- Aplicações que estão ocultas do utilizador no dispositivo
 
Pode especificar a aplicação pelo URL, nome do pacote ou da lista de aplicações que gere.

#### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Nova ligação da IU da política de acesso condicional com base na aplicação Azure AD do Intune
<!-- 1016201 -->
Os administradores de TI podem agora definir políticas condicionais com base nas aplicações através da nova IU da política de acesso condicional na carga de trabalho do Azure AD. Por enquanto, o acesso condicional com base nas aplicações na secção Proteção de Aplicações do Intune no portal do Azure permanecerá no local e será imposto lado a lado. Também existe uma ligação útil para a nova IU da política de acesso condicional na carga de trabalho do Intune.

- Saiba mais sobre o [acesso condicional com base na aplicação no Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).


## <a name="notices"></a>Avisos

### <a name="ip-addresses-for-intune-updated----1175274---"></a>Endereços IP do Intune atualizados <!-- 1175274 -->
Uma [lista atualizada de nomes DNS e endereços IP](/intune/network-bandwidth-use) está disponível para as definições de proxy da firewall.

### <a name="use-azure-active-directory-for-conditional-access----967947---"></a>Utilizar o Azure Active Directory para acesso condicional <!-- 967947 -->
O acesso condicional está disponível na secção Azure Active Directory do portal do Azure e fornece uma arquitetura mais avançada e flexível para definir políticas para aplicações na cloud como o Office 365 Exchange Online e o SharePoint Online.  Utilize o painel **Acesso condicional no Azure Active Directory** para configurar políticas, em vez de utilizar o portal clássico do Intune. As políticas existentes na consola do Intune precisam de ser recriadas no portal do Azure. Para obter mais informações, veja [Criar políticas de Acesso condicional do Azure AD](/intune/conditional-access-exchange-create.md#create-azure-ad-conditional-access-policies-in-intune-azure-preview).

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acesso direto aos cenários de inscrição da Apple <!--951869-->
Para as contas do Intune criadas depois de janeiro de 2017, o Intune ativou o acesso direto aos cenários de inscrição da Apple através da carga de trabalho Inscrever Dispositivos no portal do Azure. Anteriormente, a pré-visualização da inscrição da Apple apenas estava acessível a partir de ligações no portal do Intune clássico. As contas do Intune criadas antes de janeiro de 2017 precisam de uma única migração antes de estas funcionalidades ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder ao portal do Azure.

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Substituição das funções de administração no portal do Azure
As funções de administração de gestão de aplicações móveis (MAM) existentes (Contribuidor, Proprietário e Só de leitura) utilizadas no portal clássico do Intune (Silverlight) estão a ser substituídas por um conjunto completo de novos controlos de administração baseados em funções (RBAC) no portal do Azure no Intune. Após concluir a migração para o portal do Azure, terá de atribuir novamente os administradores a estas novas funções de administração. Para obter mais informações sobre as RBAC e as novas funções, veja [Controlo de acesso baseado em funções do Microsoft Intune](/intune/role-based-access-control).



## <a name="whats-coming"></a>Novidades futuras

#### <a name="ios-11-mail-app-will-support-oauth----1196951---"></a>A aplicação Mail para o iOS 11 suportará o OAuth <!---1196951--->
O acesso condicional do Intune suporta uma autenticação mais segura em dispositivos iOS com o OAuth. Para suportar esta funcionalidade, haverá agora um fluxo diferente na aplicação Portal da Empresa para iOS, para permitir uma autenticação mais segura. Quando os utilizadores finais tentarem iniciar sessão numa nova conta do Exchange na aplicação Mail, verão uma mensagem na vista Web. Após a inscrição no Intune, os utilizadores verão uma mensagem para permitir que a aplicação Mail nativa aceda a um certificado. A maioria dos utilizadores finais não verá mais e-mails em quarentena. As contas de e-mail existentes continuarão a utilizar o protocolo de autenticação básico, por isso estes utilizadores continuarão a receber e-mails em quarentena. A experiência de início de sessão dos utilizadores finais é semelhante à das aplicações do Office para dispositivos móveis.

### <a name="end-of-support-for-ios-80----1164477---"></a>Fim do suporte para iOS 8.0 <!---1164477--->
As aplicações geridas e a aplicação Portal da Empresa para iOS precisarão do iOS 9.0 e superior para aceder aos recursos empresariais. Os dispositivos que não forem atualizados antes de setembro deixarão de poder aceder ao Portal da Empresa ou a essas aplicações. 

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>Atualização da IU do site do Portal da Empresa <!--1313244 part 2-->
__Atualização das Aplicações em Destaque__  
Adicionámos ao site uma página dedicada em que os utilizadores podem procurar aplicações que optou por destacar e otimizámos a IU da secção Destaques na home page. Pode ver o aspeto destas alterações na página [Novidades na IU da aplicação](whats-new-app-ui.md).


### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Fim do suporte para Android 4.3 e anterior <!---1171127, 1326920 --->
As aplicações geridas e a aplicação Portal da Empresa para Android precisarão do Android 4.4 e superior para aceder a recursos empresariais. Os dispositivos que não forem atualizados antes do início de outubro deixarão de poder aceder ao Portal da Empresa ou a essas aplicações. Até dezembro, todos os dispositivos inscritos serão retirados à força, resultando na perda do acesso aos recursos empresariais. Se estiver a utilizar políticas de proteção de aplicações sem MDM, as aplicações não receberão atualizações e a qualidade da experiência irá diminuir ao longo do tempo.


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>Lembrete de Suporte da Plataforma: o suporte base do Windows Phone 8.1 terminou a 11 de julho de 2017
<!-- 1327781 -->
A 11 de julho de 2017, o suporte base da plataforma do Windows Phone 8.1 chegou ao fim. O suporte de PCs com Windows 8.1 não será afetado.

Não existe impacto imediato nos dispositivos Windows Phone 8.1 que sejam geridos pelo serviço do Intune. Os dispositivos inscritos continuarão a funcionar e todas as políticas, configurações e aplicações continuarão a funcionar conforme esperado. Tenha em atenção que não existem melhorias para a plataforma do Windows Phone 8.1 no Serviço do Intune e para a aplicação Portal da Empresa do Windows Phone 8.1.

Recomendamos que atualize os dispositivos Windows Phone 8.1 elegíveis para o Windows 10 Mobile quando for possível. 

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Alterações ao suporte para a aplicação Portal da Empresa do Intune para iOS <!-- 1164474  -->
Em breve, será apresentada uma nova versão da aplicação Portal da Empresa do Microsoft Intune para iOS que suportará apenas dispositivos com o iOS 9.0 ou posterior. A versão do Portal da Empresa que suporta o iOS 8 continuará disponível durante um curto período de tempo. No entanto, tenha em atenção que, caso também utilize aplicações iOS com MAM ativada, suportamos o iOS 9.0 e posterior, pelo que deverá garantir que os seus utilizadores finais atualizam para a versão mais recente do SO. 

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Informamo-lo desta situação antecipadamente, mesmo sem termos datas específicas, para que tenha tempo para planear. Certifique-se de que os seus utilizadores atualizaram para o iOS 9 e posterior e, quando a aplicação Portal da Empresa for lançada, peça aos seus utilizadores que atualizem a mesma.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Incentive os utilizadores a atualizarem para o iOS 9.0 ou posterior, de modo a tirarem o máximo partido das novas funcionalidades do Intune.  Incentive os utilizadores a instalarem a nova versão do Portal da Empresa para tirarem partido das novas funcionalidades que oferece.

Aceda ao Intune no portal do Azure, vá para Dispositivos > Todos os Dispositivos e filtre pela versão do iOS para ver os dispositivos atuais com sistemas operativos anteriores ao iOS 9.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>A Apple passará a exigir atualizações para a Segurança de Transporte de Aplicações <!--748318-->
A Apple anunciou que irá impor requisitos específicos para a Segurança de Transporte de Aplicações (ATS). A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Esta alteração irá afetar os clientes do Intune que utilizam as aplicações do Portal da Empresa para iOS.

Disponibilizamos uma versão da aplicação do Portal da Empresa para iOS através do programa TestFlight da Apple que impõe os novos requisitos da ATS. Se gostaria de a experimentar para testar a sua conformidade com a ATS, envie um e-mail para <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app"> CompanyPortalBeta@microsoft.com </a> com o seu nome próprio, apelido, endereço de e-mail e o nome da empresa. Consulte o nosso [blogue de suporte do Intune](https://aka.ms/compportalats) para obter mais detalhes.

### <a name="see-also"></a>Veja também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novidades na IU do Portal da Empresa](whats-new-app-ui.md)
* [Novidades nos meses anteriores](whats-new-archive.md)
