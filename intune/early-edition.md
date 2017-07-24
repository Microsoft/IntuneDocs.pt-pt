---
title: "Edição antecipada"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b8d281e3af2458bd5ab343dfa5123b31075d28ed
ms.sourcegitcommit: 2a6ad3c233d15a9fb441362105f64b2bdd550c34
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/13/2017
---
# <a name="the-early-edition-for-microsoft-intune---july-2017"></a>Edição antecipada do Microsoft Intune – julho de 2017

A **edição antecipada** oferece uma lista de funcionalidades disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida numa base extremamente limitada e está sujeita a alterações. Não partilhe estas informações fora da sua empresa. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu contacto do grupo de produtos da Microsoft se tiver dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

> [!Note]
>As seguintes alterações estão em desenvolvimento para o Intune. Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--

## What's coming to Intune on the Azure portal  
## What's coming to Intune apps
## Notices

-->



## <a name="intune-on-the-azure-portal"></a>Intune no portal do Azure

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Instalação mais fácil das aplicações do Office 365 <!--- 1121362 --->
O novo tipo de aplicação do **Office 365 ProPlus** faz com que seja mais fácil para si atribuir aplicações do Office 365 ProPlus a dispositivos que gere e que executam a versão mais recente do Windows 10. Além disso, poderá instalar o Microsoft Project e o Microsoft Visio, se tiver licenças dos mesmos. As aplicações que pretende serão agrupadas e aparecerão como uma aplicação na lista de aplicações na consola do Intune.


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Nova ação de dispositivo para forçar os dispositivos a sincronizar com o Intune <!-- 711369 -->    
Estamos a adicionar uma nova ação de dispositivo que força o dispositivo selecionado a dar entrada imediatamente no Intune. Quando um dispositivo dá entrada, recebe imediatamente todas as ações ou políticas pendentes que foram atribuídas ao mesmo.  Esta ação pode ajudá-lo a validar e resolver imediatamente problemas de políticas que atribuiu, sem esperar pela próxima entrada agendada.

### <a name="actions-for-non-compliance----730266--"></a>Ações de não conformidade <!--730266-->     
As *ações de não conformidade* são uma nova funcionalidade de políticas de conformidade que lhe permitirá tomar medidas em dispositivos que não estejam em conformidade. Pode especificar uma ou múltiplas ações e o período de tempo em que devem ocorrer. Por exemplo, pode informar os utilizadores acerca dos dispositivos não conformes, imediatamente depois de estes se tornarem não conformes, por e-mail ou pode impedir os dispositivos não conformes de acederem aos recursos empresariais após um período de tolerância de 3 dias através do Acesso Condicional.

### <a name="new-app-configuration-settings-for-the-intune-managed-browser-----682951----"></a>Novas definições de configuração de aplicações para o Intune Managed Browser<!--- 682951 --->
Iremos adicionar mais configurações para a aplicação Intune Managed Browser. Poderá utilizar uma política de configuração de aplicações para configurar a página inicial predefinida e os marcadores para o browser.

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Restringir a inscrição de dispositivos Android e iOS pela versão do SO<!--- 1333256,  1245463 --->  
O Intune suporta agora a restrição da inscrição do iOS e Android pelo número da versão do sistema operativo. Em **Intune** > **Restrições de inscrição** > **Restrição do Tipo de Dispositivo** > **Predefinição** > **Restrições de plataforma**, o administrador de TI será capaz de definir uma configuração de plataforma para restringir a inscrição entre o valor do sistema operativo mínimo e o máximo. As versões do sistema operativo Android têm de ser especificadas como Major.Minor.Build.Rev, em que Build e Rev são opcionais. As versões do iOS têm de ser especificadas como Major.Minor.Build, em que Build é opcional.

>[!NOTE]
>Esta definição não restringe a inscrição através de programas de inscrição da Apple, que inclui o Programa de Inscrição de Dispositivos da Apple e o Apple School Manager ou o Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Restringir a inscrição de dispositivos pessoais Android, iOS e macOS <!--- 1333272,  1333275, 1245709 --->
Agora, o Intune suporta a restrição de inscrição de dispositivos pessoais para iOS, Android e macOS com números de série do dispositivo. Alguns dispositivos não reportam números de série. Consulte os fabricantes de dispositivos para obter detalhes. Ao carregar os números de série para o Intune, pode pré-declarar os dispositivos como pertencentes à empresa. Através das restrições de inscrição, pode bloquear dispositivos pessoais (BYOD), permitindo a inscrição apenas para dispositivos pertencentes à empresa.

Para importar números de série no portal do Intune, aceda a **Inscrição do dispositivo** > **Identificadores de dispositivo da empresa** e clique no cabeçalho **Adicionar**. Em seguida, carregue um ficheiro .CSV (nenhum cabeçalho, duas colunas para o número de série e detalhes como números IMEI).  Para restringir dispositivos pessoais, aceda a **Inscrição do dispositivo** > **Restrições de inscrição**. Em **Restrições de Tipos de Dispositivos**, selecione **Predefinição** e, em seguida, selecione **Configurações de Plataformas**. Pode **Permitir** ou **Bloquear** dispositivos pessoais para iOS, Android e macOS. 

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de software disponíveis mais recentes <!-- 777100 -->   
Uma nova política estará disponível a partir da área de trabalho Atualizações de software, onde pode forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de software disponíveis mais recentes. Também verá um novo relatório que indica dispositivos iOS com as versões mais antigas e um resumo do motivo pelo qual estão desatualizadas.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices-----822899--1305423--"></a>Novas definições para permitir e bloquear aplicações para dispositivos Samsung KNOX Standard <!-- 822899,  1305423-->   
Estamos a adicionar novas [definições de restrição de dispositivos](device-restrictions-android.md) que lhe permitem especificar as seguintes listas de aplicações:
  - Aplicações que os utilizadores têm permissão para instalar
  - Aplicações que os utilizadores não têm permissão para executar
  - Aplicações que estão ocultas do utilizador no dispositivo  

Pode especificar a aplicação pelo URL, nome do pacote ou da lista de aplicações que gere.

### <a name="android-for-work-support-for-lookout----1087312---"></a>Suporte do Android for Work para Lookout <!-- 1087312 -->   
O conector do Intune com o Lookout suportará dispositivos Android for Work ao utilizar a aplicação Lookout for Work. Poderá implementar a aplicação Lookout dentro ou fora do contentor.


### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651--and--1172027----"></a>Check Point SandBlast Mobile – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis <!-- 954651  and  1172027 ? -->  
Poderá controlar o acesso a recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Check Point SandBlast Mobile, uma solução de defesa contra ameaças para dispositivos móveis que está integrada com o Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Como funciona a integração com o Intune?
O risco é avaliado com base na telemetria recolhida dos dispositivos que executam o Check Point SandBlast Mobile. Pode configurar políticas de acesso condicional de EMS com base na avaliação de riscos do Check Point SandBlast Mobile ativada através de políticas de conformidade do dispositivo do Intune. Pode permitir ou bloquear o acesso dos dispositivos que não estejam em conformidade aos recursos empresariais, com base nas ameaças detetadas.

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis <!-- 954681 -->
Poderá controlar o acesso a recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Zimperium, uma solução de Defesa Contra Ameaças para Dispositivos Móveis que está integrada com o Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Como funciona a integração com o Intune?
O risco é avaliado com base na telemetria recolhida dos dispositivos a executar o Zimperium. Pode configurar políticas de acesso condicional de EMS baseadas na avaliação de riscos do Zimperium, que é ativada através de políticas de conformidade do dispositivo do Intune, as quais pode utilizar para permitir ou impedir que os dispositivos não conformes acedam aos recursos empresariais com base em ameaças detetadas.

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Suporte de elevada disponibilidade do conector do Exchange no local <!-- 676614 -->   
Poderá ter múltiplas funções de Servidor de Acesso de Cliente (CAS) para o conector do Exchange no local. Por exemplo, se o CAS principal falhar, o conector do Exchange receberá uma consulta para reverter para outros CASs. Esta funcionalidade garante que o serviço não é interrompido.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Pacote de gestão do System Center Operations Manager para o conector do Exchange <!-- 885457 -->   
O pacote de gestão do System Center Operations Manager para o conector do Exchange estará disponível para ajudá-lo a analisar os registos do conector do Exchange. Tal irá proporcionar-lhe diferentes formas de monitorizar o Intune quando precisar de resolver problemas.

### <a name="conditional-access-support-for-mac-devices-----720172---"></a>Suporte de acesso condicional para dispositivos Mac <!-- 720172 -->   
Em breve, poderá definir uma política de acesso condicional que exige que os dispositivos Mac estejam inscritos no Intune e em conformidade com as políticas de conformidade do dispositivo. Por exemplo, os utilizadores podem transferir a aplicação Portal da Empresa do Intune para macOS e inscrever os dispositivos Mac no Intune. O Intune avalia se o dispositivo Mac está ou não em conformidade com os requisitos, tal como o PIN, versão do SO e Integridade do Sistema.

### <a name="end-of-support-for-ios-80----1164477---"></a>Fim do suporte para iOS 8.0 <!---1164477--->
As aplicações geridas e a aplicação Portal da Empresa para iOS precisarão do iOS 9.0 e superior para aceder aos recursos empresariais. Os dispositivos que não forem atualizados antes de setembro deixarão de poder aceder ao Portal da Empresa ou a essas aplicações. Em dezembro, o acesso a recursos empresariais, incluindo e-mail, será bloqueado. 

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Fim do suporte para Android 4.3 e anterior <!---1171127, 1326920 --->
As aplicações geridas e a aplicação Portal da Empresa para Android precisarão do Android 4.4 e superior para aceder a recursos empresariais. Os dispositivos que não forem atualizados antes do início de outubro deixarão de poder aceder ao Portal da Empresa ou a essas aplicações. Até dezembro, todos os dispositivos inscritos serão retirados à força, resultando na perda do acesso aos recursos empresariais. Se estiver a utilizar políticas de proteção de aplicações sem MDM, as aplicações não receberão atualizações e a qualidade da experiência irá diminuir ao longo do tempo.





### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>Lembrete de Suporte da Plataforma: o suporte base do Windows Phone 8.1 irá terminar a 11 de julho de 2017 <!-- 1327781 -->  
A 11 de julho de 2017, será o fim do suporte base da plataforma do Windows Phone 8.1. O suporte de PCs com Windows 8.1 não será afetado.

Não existe impacto imediato nos dispositivos Windows Phone 8.1 que sejam geridos pelo serviço do Intune. Os dispositivos inscritos continuarão a funcionar e todas as políticas, configurações e aplicações continuarão a funcionar conforme esperado. Tenha em atenção que não existem melhorias para a plataforma do Windows Phone 8.1 no Serviço do Intune e para a aplicação Portal da Empresa do Windows Phone 8.1.

Recomendamos que atualize os dispositivos Windows Phone 8.1 elegíveis para o Windows 10 Mobile quando for possível. 




## <a name="intune-apps"></a>Aplicações do Intune

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Experiência de início de sessão melhorada nas aplicações Portal da Empresa para todas as plataformas<!--User Story 1132123-->    
Anunciamos uma alteração que ficará disponível nos próximos meses e irá melhorar a experiência de início de sessão nas aplicações do Portal da Empresa do Intune para Android, iOS e Windows. A nova experiência de utilizador será apresentada automaticamente em todas as plataformas da aplicação Portal da Empresa quando o Azure AD fizer esta alteração. Além disso, os utilizadores podem agora iniciar sessão no Portal da Empresa a partir de outro dispositivo com um código gerado, de utilização única. Tal é especialmente útil nos casos em que os utilizadores precisam de iniciar sessão sem credenciais.

Pode encontrar capturas de ecrã da experiência de início de sessão anterior, a nova experiência de início de sessão com credenciais e a experiência de início de sessão a partir de outro dispositivo na página [Novidades na IU da aplicação](whats-new-app-ui.md).

### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Modos claro e escuro disponíveis para a aplicação Portal da Empresa para Windows 10 <!---676547--->
Os utilizadores finais poderão personalizar o modo de cor da aplicação Portal da Empresa para Windows 10. O utilizador pode fazer a alteração na secção Definições da aplicação Portal da Empresa. A alteração será apresentada após o utilizador reiniciar a aplicação. Para o Windows 10 versão 1607 e posterior, o modo de aplicação será predefinido para a definição do sistema. Para computadores que executam a versão 1511 e anterior do Windows 10, o modo predefinido da aplicação será o modo claro.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Permitir que os utilizadores finais marquem o grupo de dispositivos na aplicação Portal da Empresa para Windows 10 <!---807046-->    
Os utilizadores finais poderão selecionar o grupo a que o dispositivo pertence ao marcá-lo diretamente na aplicação Portal da Empresa para Windows 10.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Permitir que os utilizadores finais acedam à aplicação Portal da Empresa para Android sem inscrição <!---1169910--->  
Em breve, os utilizadores finais não terão de inscrever os dispositivos para aceder à aplicação Portal da Empresa para Android. Os utilizadores finais em organizações que utilizam Políticas de Proteção de Aplicações deixarão de receber pedidos para inscrever os dispositivos quando abrem a aplicação Portal da Empresa. Os utilizadores finais também poderão instalar aplicações a partir do Portal da Empresa sem inscrever o dispositivo. 

### <a name="users-who-are-signed-in-to-exchange-can-automatically-access-the-company-portal-website-on-windows-10-devices---1323204--"></a>Os utilizadores que tiverem sessão iniciada no Exchange podem aceder automaticamente ao site do Portal da Empresa em dispositivos Windows 10 <!--1323204-->  
Os utilizadores do Windows 10 que já tiverem sido autenticados no Exchange, que receberem o e-mail de quarentena de acesso condicional e clicarem na ligação no e-mail não terão de ser autenticados novamente no browser antes de iniciarem a Configuração de Acesso da Empresa.


## <a name="notices"></a>Avisos

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>A Apple passará a exigir atualizações para a Segurança de Transporte de Aplicações <!--748318-->   
A partir da primavera de 2017, a Apple anunciou que irá impor requisitos específicos para a Segurança de Transporte de Aplicações (ATS). A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Esta alteração irá afetar os clientes do Intune que utilizam as aplicações do Portal da Empresa para iOS. Consulte o nosso [blogue de suporte do Intune](https://aka.ms/compportalats) para obter mais detalhes.

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acesso direto aos cenários de inscrição da Apple <!--951869-->   
Para as contas do Intune criadas depois de janeiro de 2017, o Intune ativou o acesso direto aos cenários de inscrição da Apple através da carga de trabalho Inscrever Dispositivos no portal de pré-visualização do Azure. Anteriormente, a pré-visualização da inscrição da Apple apenas estava acessível a partir de ligações no portal do Intune clássico. As contas do Intune criadas antes de Janeiro de 2017 precisam de uma única migração antes de estas funcionalidades ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder à pré-visualização.

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Planear a alteração: o Intune vai alterar a experiência do Portal de Parceiros do Intune <!-- 1050016 -->
A partir da atualização de serviço que se realizará em meados de maio de 2017, iremos remover a página Parceiro do Intune de manage.microsoft.com.  

Se for um administrador parceiro, já não poderá ver e agir em nome dos clientes a partir da página Parceiro do Intune. Em vez disso, terá de iniciar sessão num dos dois outros portais de parceiro da Microsoft.

Poderá iniciar sessão nas contas de cliente que gere a partir do [Centro de Parceiros da Microsoft](https://partnercenter.microsoft.com/) e do [Centro de Administração do Microsoft Office 365 para Parceiros](https://portal.office.com/). De futuro, utilize um destes sites para gerir os seus clientes.



### <a name="see-also"></a>Veja também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.
