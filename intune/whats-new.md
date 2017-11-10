---
title: Novidades do Microsoft Intune
titlesuffix: Azure portal
description: Descobrir as novidades do Intune no portal do Azure
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 11/2/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a683fcf96b09a19a84f429d8ccfab6788983d6d2
ms.sourcegitcommit: 0f877251e6adf4e45b918cc8dc9193626727f2d9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/03/2017
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

## <a name="week-of-october-30-2017"></a>Semana de 30 de outubro de 2017

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>O número da versão da aplicação de linha de negócio para iOS e Android está visível <!-- 1380712 -->

As aplicações no Intune apresentam agora o número da versão de aplicações de linha de negócio para iOS e Android. O número é apresentado no portal do Azure na lista de aplicações e no painel de descrição geral da aplicação. Os utilizadores finais podem ver o número da aplicação na aplicação Portal da Empresa e no portal Web.

#### <a name="full-version-number"></a>Número da versão completo

O número da versão completo identifica uma versão específica da aplicação. O número é apresentado como _Versão_(_Compilação_), por exemplo, 2.2(2.2.17560800).

O número da versão completo tem dois componentes:

 - **Versão**  
   O número da versão é o número da versão legível por humanos da aplicação. Este número é utilizado pelos utilizadores finais para identificar diferentes versões da aplicação.

 - **Número de Compilação**  
    O número de compilação é um número interno que pode ser utilizado para detetar aplicações e gerir a aplicação de forma programática. O número de compilação refere-se a uma iteração da aplicação que faz referência a alterações no código.

Saiba mais sobre os números de versão e o desenvolvimento de aplicações de linha de negócio em [Introdução ao SDK da Aplicação Microsoft Intune](app-sdk-get-started.md#line-of-business-app-version-numbers).

### <a name="device-and-app-management-integration----677972---"></a>Integração da gestão de dispositivos e aplicações <!-- 677972 -->   
Agora que tanto a gestão de dispositivos móveis (MDM) do Intune como a gestão de aplicações móveis (MAM) se encontram acessíveis no portal do Azure, o Intune iniciou a integração da experiência de administradores de TI em torno da gestão de aplicações e dispositivos. Estas alterações foram concebidas de modo a simplificar a sua experiência de gestão de dispositivos e aplicações.

Saiba mais sobre as alterações de MDM e MAM anunciadas no [blogue da equipa de suporte do Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Novos alertas de inscrição para dispositivos da Apple <!---1471790--->
A página de descrição geral para inscrição apresentará alertas úteis para os administradores de TI sobre a gestão de dispositivos da Apple. Os alertas serão apresentados na página Descrição Geral quando o certificado push de MDM da Apple estiver prestes a expirar ou já tiver expirado, quando o token do Programa de Registo de Aparelho estiver prestes a expirar ou já tiver expirado e quando existirem dispositivos não atribuídos no Programa de Registo de Aparelho.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>Substituição do token de suporte para a configuração de aplicações sem inscrição de dispositivos <!-- 1080364 -->

Pode utilizar tokens para valores dinâmicos em configurações da aplicação para aplicações em dispositivos que não estejam inscritos. Para obter mais informações, veja [Adicionar políticas de configuração da aplicação para aplicações geridas sem inscrição de dispositivos](app-configuration-policies-managed-app.md).

## <a name="week-of-october-23-2017"></a>Semana de 23 de outubro de 2017

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Suporte para a autenticação baseada em certificados no Portal da Empresa para iOS <!--1029830-->
Adicionámos o suporte para a autenticação baseada em certificados (CBA) na aplicação Portal da Empresa para iOS. Os utilizadores com CBA devem introduzir o seu nome de utilizador e, em seguida, tocar na ligação "Iniciar sessão com um certificado". A CBA já é suportada na aplicação Portal da Empresa para Android e Windows. Pode obter mais informações na página [Iniciar sessão na aplicação Portal da Empresa](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

## <a name="week-of-october-16-2017"></a>Semana de 16 de outubro de 2017

### <a name="device-enrollment"></a>Inscrição de dispositivos
#### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Suporte do Programa Windows AutoPilot Deployment no Microsoft Intune <!-- 747617  -->
Agora pode utilizar o Microsoft Intune com o Programa Windows AutoPilot Deployment para permitir que os utilizadores aprovisionem os respetivos dispositivos da empresa sem envolver o departamento de TI. Pode personalizar a configuração inicial (OOBE) e guiar os utilizadores para associarem os respetivos dispositivos ao Azure AD e inscrevê-los no Intune. Ao trabalharem em conjunto, o Microsoft Intune e o Windows AutoPilot eliminam a necessidade de implementar, manter e gerir imagens de sistema operativo. Para obter detalhes, veja [Enroll Windows devices using Windows AutoPilot Deployment Program (Inscrever dispositivos Windows com o Programa Windows AutoPilot Deployment)](https://docs.microsoft.com/intune/enrollment-autopilot).

#### <a name="quick-start-for-device-enrollment-----1425655---"></a>Guia de introdução da inscrição de dispositivos <!-- 1425655 --> 
O guia de introdução está disponível em **Inscrição de dispositivos** e fornece uma tabela de referência para gerir plataformas e configurar o processo de inscrição. Uma breve descrição de cada item e as ligações para documentos com instruções passo a passo fornecem documentos úteis para simplificar a introdução.

#### <a name="device-categorization----1427491---"></a>Categorização de dispositivos <!-- 1427491 -->
O gráfico da plataforma de dispositivos inscritos do painel **Dispositivos > Descrição Geral** organiza os dispositivos por plataforma, incluindo Android, iOS, macOS, Windows e Windows Mobile.  Os dispositivos com outros sistemas operativos são agrupados em "Outro".  Isto inclui dispositivos fabricados pela Blackberry, NOKIA, entre outros.  

Para saber quais são os dispositivos afetados no seu inquilino, selecione **Gerir > Todos os dispositivos** e, em seguida, utilize o **Filtro** para limitar o campo **SO**.

### <a name="device-management"></a>Gestão de dispositivos
#### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis <!-- 954681 -->  
Pode controlar o acesso aos recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Zimperium, uma solução de Defesa Contra Ameaças para Dispositivos Móveis que está integrada com o Microsoft Intune.

##### <a name="how-integration-with-intune-works"></a>Como funciona a integração com o Intune
O risco é avaliado com base na telemetria recolhida dos dispositivos a executar o Zimperium. Pode configurar políticas de acesso condicional de EMS baseadas na avaliação de riscos do Zimperium, que é ativada através de políticas de conformidade do dispositivo do Intune, as quais pode utilizar para permitir ou impedir que os dispositivos não conformes acedam aos recursos empresariais com base em ameaças detetadas.

#### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Novas definições para o perfil de restrição de dispositivos Windows 10 <!--- 978575, 1308849, -->  
Estamos a adicionar novas definições ao perfil de restrição de dispositivos com o Windows 10 na categoria Windows Defender SmartScreen.

Para obter detalhes sobre o perfil de restrição de dispositivos com o Windows 10, veja [Windows 10 and later device restriction settings (Definições de restrição de dispositivos com o Windows 10 e posterior)]( device-restrictions-windows-10.md).

#### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Suporte remoto para dispositivos Windows e Windows Mobile <!-- 1070473 -->  
O Intune pode utilizar o software [TeamViewer](https://www.teamviewer.com), comprado separadamente, para lhe permitir disponibilizar assistência remota aos utilizadores com o Windows e dispositivos Windows Mobile.

#### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Analisar dispositivos com o Windows Defender <!-- 1280988  1280990   -->
Pode executar uma **Análise rápida**, **Análise completa** e **Atualizar assinaturas** com o Antivírus do Windows Defender em dispositivos Windows 10 geridos. No painel de descrição geral do dispositivo, escolha a ação a executar no dispositivo. Ser-lhe-á pedido para confirmar a ação antes do comando ser enviado para o dispositivo. 

**Análise rápida**: uma análise rápida analisa as localizações onde se inicia o registo do software maligno, tais como chaves do registo e pastas de arranque conhecidas do Windows. Uma análise rápida demora cerca de cinco minutos. Combinada com a definição **Proteção em tempo real sempre ativada**, que analisa os ficheiros quando são abertos, quando são fechados e sempre que um utilizador navega para uma pasta, a análise rápida ajuda a fornecer proteção contra software maligno que poderá estar no sistema ou no kernel. Os utilizadores veem os resultados da análise nos dispositivos ao terminar. 

**Análise completa**: pode ser útil uma análise completa em dispositivos que encontraram uma ameaça de software maligno para identificar se existem componentes inativos que requerem uma limpeza mais detalhada- É também útil para executar análises a pedido. Uma análise completa pode demorar cerca de uma hora. Os utilizadores veem os resultados da análise nos dispositivos ao terminar. 

**Atualizar assinaturas**: o comando de atualização de assinaturas atualiza as definições e as assinaturas do software maligno do Windows Defender Antivirus. Este comando ajuda a garantir que o Windows Defender Antivirus é eficaz na deteção de software maligno. Esta funcionalidade destina-se apenas a dispositivos Windows 10, com ligação à Internet dos dispositivos pendente. 

#### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>O botão Ativar/Desativar é removido da página Autoridade de Certificação do Intune do portal do Azure no Intune <!-- 1400455 -->
 Vamos eliminar um passo extra na configuração do Certificate Connector no Intune. Neste momento, pode transferir o Certificate Connector e, em seguida, ativá-lo na consola do Intune. No entanto, se desativar o conector na consola do Intune, este continuará a emitir certificados.

##### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
A partir de outubro, o botão Ativar/Desativar deixará de ser apresentado na página Autoridade de Certificação no portal do Azure. A funcionalidade do conector permanece igual. Os certificados continuam a ser implementados nos dispositivos inscritos no Intune. Pode continuar a transferir e instalar o Certificate Connector. Para interromper a emissão de certificados, desinstale o Certificate Connector em vez de o desativar.

##### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Se tiver o Certificate Connector desativado, deve desinstalá-lo.



### <a name="device-configuration"></a>Configuração do dispositivo
#### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Novas definições para o perfil de restrição de dispositivos Windows 10 Team <!--- 1308838 -->
Nesta versão, adicionámos muitas definições novas ao perfil de restrição de dispositivos Windows 10 Team para ajudar a controlar os dispositivos Surface Hub.

Para obter mais informações sobre este perfil, veja [Definições de restrição de dispositivos Windows 10 Team](device-restrictions-windows-10-teams.md).

#### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Impedir que os utilizadores de dispositivos Android alterem a data e hora dos dispositivos <!-- 1333292 -->
Pode utilizar uma [política de dispositivo personalizada do Android](custom-settings-android.md) para impedir que os utilizadores de dispositivos Android alterem a data e a hora do dispositivo.

Para tal, configure uma política personalizada do Android com a definição URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange. Defina esta opção como **TRUE**e, em seguida, atribua-a aos grupos necessários.

#### <a name="bitlocker-device-configuration----1397398---"></a>Configuração do dispositivo BitLocker <!-- 1397398 -->
A opção **Encriptação Windows > Definições Base** inclui uma nova definição **Aviso para a encriptação de outro disco**, que permitirá desativar o [pedido de aviso](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) para a encriptação de outro disco que poderá estar em utilização no dispositivo do utilizador.  O pedido de aviso necessita de consentimento do utilizador final para configurar o BitLocker no dispositivo e bloqueia a configuração do BitLocker até confirmação do utilizador final.  A nova definição desativa o aviso do utilizador final.


### <a name="app-management"></a>Gestão de aplicações
#### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>As aplicações do Volume Purchase Program for Business irão sincronizar com o seu Inquilino do Intune <!-- 800882 -->  
Os programadores de terceiros podem distribuir em privado aplicações aos membros autorizados do Volume Purchase Program (VPP) for Business especificados no iTunes Connect. Estes membros do VPP for Business podem iniciar sessão na Loja de Aplicações do Volume Purchase Program e comprar as suas aplicações.

Com esta versão, as aplicações do VPP for Business compradas pelo utilizador final começarão a sincronizar com os respetivos inquilinos do Intune.

#### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Selecionar a loja do país da Apple para sincronizar aplicações VPP <!-- 1332311 -->  
Pode configurar o Volume Purchase Program (VPP) ao carregar o token VPP. O Intune sincroniza as aplicações VPP para todas as regiões a partir da loja do país do VPP especificada.

> [!NOTE]  
> Atualmente, o Intune só sincroniza as aplicações VPP a partir da loja do país do VPP que corresponda à região do Intune na qual foi criado o inquilino do Intune.




### <a name="intune-apps"></a>Aplicações do Intune
#### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Bloquear ações de copiar e colar entre perfis de trabalho e pessoais no Android for Work <!-- 1098994 -->
Com esta versão, pode configurar o perfil de trabalho do Android for Work para bloquear as ações de copiar e colar entre aplicações pessoais e de trabalho. Pode encontrar esta nova definição no perfil **Restrições do dispositivo** da Plataforma **Android for Work** em **Definições do perfil de trabalho**.

#### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Criar aplicações iOS limitadas a Lojas de Aplicações da Apple regionais específicas <!-- 1281692 -->
Poderá especificar a região do país durante a criação de uma aplicação gerida pela Loja de Aplicações da Apple.

> [!Note]  
> Atualmente, só pode criar aplicações geridas pela Apple App Store que estejam presentes na loja dos E.U.A.

####  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Atualizar o utilizador do VPP para iOS e as aplicações licenciadas de dispositivos <!-- 1305564 -->  
Poderá configurar o token VPP para iOS para atualizar todas as aplicações compradas para esse token através do serviço Intune. O Intune vai detetar as atualizações de aplicações VPP no interior da loja de aplicações e emiti-las automaticamente para o dispositivo quando este entra.

Para obter passos para configurar um token do VPP e ativar as atualizações automáticas, veja [Como gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune] (/intune/vpp-apps-ios).



### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas
#### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Coleção de entidades de associação de dispositivos do utilizador adicionada ao modelo de dados do Armazém de Dados do Intune <!-- 1187917 -->
Agora pode criar relatórios e visualizações de dados com as informações de associação de dispositivos do utilizador que associam o utilizador às coleções de dispositivos de entidades. Pode aceder ao modelo de dados através do ficheiro do Power BI (PBIX) obtido na página do Intune do Armazém de Dados, através do ponto final do OData ou ao desenvolver um cliente personalizado.

#### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Rever a conformidade das políticas das cadências de atualização do Windows 10 <!-- 1067886 -->
Poderá rever um relatório das políticas das cadências de atualização do Windows 10 em Atualizações de software > Por estado de implementação da cadência de atualização. O relatório das políticas inclui o estado de implementação das cadências de atualização configuradas. 

#### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Novo relatório que indica os dispositivos iOS com versões mais antigas do iOS <!-- 1352223 -->
O relatório **Dispositivos iOS desatualizados** está disponível na área de trabalho **Atualizações de software**. No relatório, poderá ver uma lista dos dispositivos iOS supervisionados que foram abrangidos por uma política de atualização iOS com atualizações disponíveis. Pode ver o estado com o motivo pelo qual cada um dos dispositivos não foi atualizado automaticamente. 

#### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Ver as atribuições de políticas de proteção de aplicações para resolução de problemas <!--  1475003 -->
Nesta versão futura, a opção **Política de proteção de aplicações** será adicionada a **Atribuições**, na lista pendente disponível no painel de resolução de problemas. Agora, pode selecionar as políticas de proteção de aplicações para ver as políticas de proteção de aplicações que foram atribuídas aos utilizadores selecionados.



## <a name="week-of-october-2-2017"></a>Semana de 2 de outubro de 2017

### <a name="intune-apps"></a>Aplicações do Intune
#### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Melhorias no fluxo de trabalho da configuração de dispositivos no Portal da Empresa <!--1490692-->
Melhorámos o fluxo de trabalho da configuração de dispositivos na aplicação Portal da Empresa para Android. O tipo de linguagem é mais simples e específico para a sua empresa. Além disso, combinámos os ecrãs sempre que possível. Pode ver estas melhorias na página [Novidades na IU da aplicação](whats-new-app-ui.md#week-of-october-2-2017).

#### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Orientação melhorada no pedido de acesso aos contactos em dispositivos Android <!--1484985-->

A aplicação Portal da Empresa para Android exige frequentemente que o utilizador final aceite as permissões de Contactos. Se um utilizador final recusar este acesso, verá agora uma notificação na aplicação que o alerta para o conceder para acesso condicional. 

#### <a name="secure-startup-remediation-for-android---1490712--"></a>Remediação de arranque seguro para Android <!--1490712-->

Os utilizadores finais com dispositivos Android poderão tocar no motivo de não conformidade na aplicação Portal da Empresa. Sempre que possível, esta ação irá reencaminhá-lo para a localização correta na aplicação de definições para resolver o problema. 

#### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Notificações push adicionais para utilizadores finais na aplicação Portal da Empresa para Android Oreo <!--1475932-->

Os utilizadores finais receberão notificações adicionais a indicar quando a aplicação Portal da Empresa para Android Oreo está a efetuar tarefas em segundo plano, como a obtenção de políticas do serviço do Intune. Isto aumenta a transparência para os utilizadores finais sobre quando o Portal da Empresa está a efetuar tarefas administrativas nos respetivos dispositivos. Isto faz parte da [otimização geral da IU do Portal da Empresa](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) para a aplicação Portal da Empresa para Android Oreo. 

Existem mais otimizações para novos elementos da IU que estão ativadas no Android Oreo.  Os utilizadores finais receberão notificações adicionais a indicar quando o Portal da Empresa está a efetuar tarefas em segundo plano, como a obtenção de políticas do serviço do Intune.  Isto aumenta a transparência para os utilizadores finais sobre quando o Portal da Empresa está a efetuar tarefas administrativas no dispositivo.

#### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Novo comportamentos para a aplicação Portal da Empresa para Android com perfis de trabalho <!---1485783--->

Quando inscreve um dispositivo Android for Work num perfil de trabalho, é a aplicação Portal da Empresa no perfil de trabalho que executa as tarefas de gestão no dispositivo. 

Se estiver a utilizar uma aplicação ativada para MAM no perfil pessoal, a aplicação Portal da Empresa para Android já não terá qualquer utilidade. Para melhorar a experiência do perfil de trabalho, o Intune ocultará automaticamente a aplicação Portal da Empresa depois de inscrever com sucesso o perfil de trabalho.

A aplicação Portal da Empresa para Android pode ser ativada em qualquer altura no perfil pessoal. para tal, navegue para o [Portal da Empresa na Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) e toque em **Ativar**.

#### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Mudança do Portal da Empresa para Windows 8.1 e do Windows Phone 8.1 para modo de suporte <!--1428681-->

A partir de outubro de 2017, as aplicações Portal da Empresa para Windows 8.1 e o Windows Phone 8.1 irão passar para o modo de suporte, o que significa que as aplicações e os cenários existentes, tais como inscrição e conformidade, continuarão a ter suporte nestas plataformas. Estas aplicações continuarão a estar disponíveis para transferência através dos canais de lançamento existentes, tais como a Loja Microsoft. 

Quando estiverem no modo de suporte, estas aplicações receberão apenas atualizações de segurança críticas. Não haverá quaisquer atualizações ou funcionalidades adicionais para estas aplicações. Para obter novas funcionalidades, recomendamos que atualize os dispositivos para Windows 10 ou Windows 10 Mobile. 


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="block-unsupported-samsung-knox-device-enrollment------1490695----"></a>Bloquear a inscrição de dispositivos Samsung Knox não suportados <!--- 1490695 --->

A aplicação Portal da Empresa apenas tenta inscrever dispositivos Samsung Knox suportados. Para evitar erros de ativação KNOX que impeçam a inscrição MDM, a tentativa de inscrição do dispositivo só é efetuada se o dispositivo aparecer na [lista de dispositivos publicados pela Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Os dispositivos Samsung poderão ter números de modelo compatíveis ou não com o KNOX. Verifique a compatibilidade com o Knox junto do revendedor do seu dispositivo antes da compra e implementação. Poderá encontrar a lista completa de dispositivos verificados nas [Definições da política para Android e Samsung KNOX Standard](/intune/supported-devices-browsers.md#intune-supported-devices).

#### <a name="end-of-support-for-android-43-and-lower----1171126-1326920----"></a>Fim do suporte para Android 4.3 e anterior <!---1171126, 1326920 --->
As aplicações geridas e a aplicação Portal da Empresa para Android precisarão do Android 4.4 e superior para aceder a recursos empresariais. Até dezembro, todos os dispositivos inscritos serão retirados à força, resultando na perda do acesso aos recursos empresariais. Se estiver a utilizar políticas de proteção de aplicações sem MDM, as aplicações não receberão atualizações e a qualidade da experiência irá diminuir ao longo do tempo.

#### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>Informe os utilizadores finais acerca das informações do dispositivo que podem ser vistas em dispositivos inscritos <!--1165314-->
Iremos adicionar o **Tipo de Propriedade** ao ecrã Detalhes do Dispositivo em todas as aplicações Portal da Empresa. Isto permitirá aos utilizadores saber mais sobre a privacidade diretamente a partir do artigo [Que informações pode a sua empresa ver?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune). Isto será implementado em todas as aplicações Portal da Empresa brevemente. Anunciámos esta funcionalidade para iOS em [setembro](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017).


## <a name="week-of-september-25-2017"></a>Semana de 25 de setembro de 2017

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="intune-supports-ios-11---1428975--"></a>O Intune suporta o iOS 11 <!--1428975-->
O Intune suporta o iOS 11. Isto foi anteriormente anunciado no [blogue de Suporte do Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

#### <a name="end-of-support-for-ios-80----1164477---"></a>Fim do suporte para iOS 8.0 <!---1164477--->
As aplicações geridas e a aplicação Portal da Empresa para iOS precisarão do iOS 9.0 e superior para aceder aos recursos empresariais. Os dispositivos que não forem atualizados antes de setembro deixarão de poder aceder ao Portal da Empresa ou a essas aplicações. 

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Ação de atualizar adicionada à aplicação Portal da Empresa para Windows 10 <!--1132468-->
A aplicação Portal da Empresa para Windows 10 permite aos utilizadores atualizar os dados na aplicação, ao pedir para atualizar ou, em computadores, ao premir F5.



## <a name="notices"></a>Avisos

### <a name="new-path-for-managed-devices-in-graph-api----1586728---"></a>Novo caminho para dispositivos geridos na Graph API <!-- 1586728 -->
Estamos a alterar o caminho utilizado para aceder a dispositivos geridos na versão beta da Graph API. 

| | |
|--|--|
| Caminho atual |  https://graph.microsoft.com/beta/managedDevices |
| Novo caminho | https://graph.microsoft.com/beta/deviceManagement/managedDevices |

Ambos os caminhos estarão a funcionar ao longo do mês de outubro. Após a versão de serviço de outubro, apenas o novo caminho estará funcional.  Se estiver a utilizar a Graph API para aceder a dispositivos geridos, atualize e verifique os seus scripts e aplicações através do novo caminho. Para ver alterações adicionais, veja o [registo de alterações da Graph API](https://developer.microsoft.com/graph/docs/concepts/changelog) mensal.


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acesso direto aos cenários de inscrição da Apple <!--951869-->
Para as contas do Intune criadas depois de janeiro de 2017, o Intune ativou o acesso direto aos cenários de inscrição da Apple através da carga de trabalho Inscrever Dispositivos no portal do Azure. Anteriormente, a pré-visualização da inscrição da Apple apenas estava acessível a partir de ligações no portal do Intune clássico. As contas do Intune criadas antes de janeiro de 2017 precisam de uma única migração antes de estas funcionalidades ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder ao portal do Azure.

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Substituição das funções de administração no portal do Azure
As funções de administração de gestão de aplicações móveis (MAM) existentes (Contribuidor, Proprietário e Só de leitura) utilizadas no portal clássico do Intune (Silverlight) estão a ser substituídas por um conjunto completo de novos controlos de administração baseados em funções (RBAC) no portal do Azure no Intune. Após concluir a migração para o portal do Azure, terá de atribuir novamente os administradores a estas novas funções de administração. Para obter mais informações sobre as RBAC e as novas funções, veja [Controlo de acesso baseado em funções do Microsoft Intune](/intune/role-based-access-control).



## <a name="whats-coming"></a>Novidades futuras

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

## <a name="see-also"></a>Veja também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novidades na IU do Portal da Empresa](whats-new-app-ui.md)
* [Novidades nos meses anteriores](whats-new-archive.md)
