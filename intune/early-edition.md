---
title: "Edição antecipada"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 08/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5d5d8e0500a0ee928b1037a978f6d4dadab71495
ms.sourcegitcommit: 2ed8d1c39d4b3e3282111f1d758afb3a50f19f8f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/10/2017
---
# <a name="the-early-edition-for-microsoft-intune---august-2017"></a>A edição antecipada do Microsoft Intune – agosto de 2017

A **edição antecipada** oferece uma lista de funcionalidades disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida numa base limitada e está sujeita a alterações. Não partilhe estas informações fora da sua empresa. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu contacto do grupo de produtos da Microsoft se tiver dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

> [!Note]
>As seguintes alterações estão em desenvolvimento para o Intune. Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--

## What's coming to Intune on the Azure portal  
## What's coming to Intune apps
## Notices

-->



## <a name="intune-on-the-azure-portal"></a>Intune no portal do Azure

### <a name="actions-for-non-compliance----730266--"></a>Ações de não conformidade <!--730266-->     
*As ações de não conformidade* são uma nova funcionalidade de políticas de conformidade que lhe permite tomar medidas em dispositivos que não estejam em conformidade. Pode especificar uma ou múltiplas ações e o período de tempo em que devem ocorrer. Por exemplo, pode informar os utilizadores acerca dos dispositivos não conformes, imediatamente depois de estes se tornarem não conformes, por e-mail ou pode impedir os dispositivos não conformes de acederem aos recursos empresariais após um período de tolerância de 3 dias através do Acesso Condicional.

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Novo relatório que indica os dispositivos iOS com versões mais antigas do iOS <!-- 1352223 -->
O relatório **Dispositivos iOS desatualizados** estará disponível na área de trabalho **Atualizações de software**. No relatório, poderá ver uma lista dos dispositivos iOS supervisionados que foram abrangidos por uma política de atualização iOS com atualizações disponíveis. Pode ver o estado com o motivo pelo qual cada um dos dispositivos não foi atualizado automaticamente. 

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices-----822899--1305423--"></a>Novas definições para permitir e bloquear aplicações para dispositivos Samsung KNOX Standard <!-- 822899,  1305423-->   
Estamos a adicionar novas [definições de restrição de dispositivos](device-restrictions-android.md) que lhe permitem especificar as seguintes listas de aplicações:
  - Aplicações que os utilizadores têm permissão para instalar
  - Aplicações que os utilizadores não têm permissão para executar
  - Aplicações que estão ocultas do utilizador no dispositivo  

Pode especificar a aplicação pelo URL, nome do pacote ou da lista de aplicações que gere.

### <a name="new-settings-for-windows-10-device-restriction-profile"></a>Novas definições para o perfil de restrição de dispositivos Windows 10
<!--- 978575, 1308849, 1308850 -->
Estamos a adicionar novas definições ao perfil de restrição de dispositivos com o Windows 10 na categoria Windows Defender SmartScreen.

Para obter detalhes sobre o perfil de restrição de dispositivos com o Windows 10, veja [Windows 10 and later device restriction settings (Definições de restrição de dispositivos com o Windows 10 e posterior)]( device-restrictions-windows-10.md).

### <a name="new-device-restriction-settings-for-windows-10------1063965---"></a>Novas definições de restrição de dispositivos para Windows 10 <!-- 1063965 -->
Estamos a adicionar novas definições ao [perfil de restrição de dispositivos com o Windows 10](/intune/device-restrictions-windows-10) nas seguintes categorias:
- Windows Defender SmartScreen
- Loja de aplicações


### <a name="android-for-work-support-for-lookout----1087312---"></a>Suporte do Android for Work para Lookout <!-- 1087312 -->   
O conector do Intune com o Lookout suportará dispositivos Android for Work ao utilizar a aplicação Lookout for Work. Pode implementar a aplicação Lookout dentro ou fora do contentor.


### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Proteção de Aplicações Intune e Citrix MDX Development Tools <!-- 709185 -->
Pode gerir dispositivos e aplicações ao combinar o Citrix XenMobile MDX e o Microsoft Intune. Isto permite-lhe gerir aplicações com a política de proteção da aplicação Intune ao utilizar a tecnologia mVPN da Citrix.

Pode encontrar um repositório de códigos que contém a Ferramenta de Encapsulamento de Aplicações do Intune para iOS e Android, integrada com a tecnologia Citrix MDX mVPN.


### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis <!-- 954681 -->
Pode controlar o acesso aos recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Zimperium, uma solução de Defesa Contra Ameaças para Dispositivos Móveis que está integrada com o Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Como funciona a integração com o Intune?
O risco é avaliado com base na telemetria recolhida dos dispositivos a executar o Zimperium. Pode configurar políticas de acesso condicional de EMS baseadas na avaliação de riscos do Zimperium, que é ativada através de políticas de conformidade do dispositivo do Intune, as quais pode utilizar para permitir ou impedir que os dispositivos não conformes acedam aos recursos empresariais com base em ameaças detetadas.

### <a name="new-azure-ad-conditional-access-policy-ui-link-from-intune-----1016201---"></a>Nova ligação da IU da política de acesso condicional do Azure AD do Intune <!-- 1016201 -->
Os administradores de TI podem definir políticas condicionais com base nas aplicações através da nova IU da política de acesso condicional na carga de trabalho do Azure AD. Por enquanto, as políticas de acesso condicional com base nas aplicações presentes na secção Proteção de Aplicações do Intune no Azure permanecem no local e são impostas lado a lado. Também haverá uma ligação útil para a nova IU da política de acesso condicional no Azure AD, a partir da carga de trabalho do Intune.


### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Suporte de elevada disponibilidade do conector do Exchange no local <!-- 676614 -->   
Pode ter múltiplas funções de Servidor de Acesso de Cliente (CAS) para o conector do Exchange no local. Por exemplo, se o CAS principal falhar, o conector do Exchange receberá uma consulta para reverter para outros CASs. Esta funcionalidade garante que o serviço não é interrompido.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Pacote de gestão do System Center Operations Manager para o conector do Exchange <!-- 885457 -->   
O pacote de gestão do System Center Operations Manager para o conector do Exchange estará disponível para ajudá-lo a analisar os registos do conector do Exchange. Esta pacote de gestão proporciona formas diferentes de monitorizar o Intune quando precisar de resolver problemas.

### <a name="end-of-support-for-ios-80----1164477---"></a>Fim do suporte para iOS 8.0 <!---1164477--->
As aplicações geridas e a aplicação Portal da Empresa para iOS precisarão do iOS 9.0 e superior para aceder aos recursos empresariais. Os dispositivos que não forem atualizados antes de setembro deixarão de poder aceder ao Portal da Empresa ou a essas aplicações. Em dezembro, o acesso a recursos empresariais, incluindo e-mail, será bloqueado. 

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Fim do suporte para Android 4.3 e anterior <!---1171127, 1326920 --->
As aplicações geridas e a aplicação Portal da Empresa para Android precisarão do Android 4.4 e superior para aceder a recursos empresariais. Os dispositivos que não forem atualizados antes do início de outubro deixarão de poder aceder ao Portal da Empresa ou a essas aplicações. Até dezembro, todos os dispositivos inscritos serão retirados à força, resultando na perda do acesso aos recursos empresariais. Se estiver a utilizar políticas de proteção de aplicações sem MDM, as aplicações não receberão atualizações e a qualidade da experiência irá diminuir ao longo do tempo.


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>Lembrete de Suporte da Plataforma: o suporte base do Windows Phone 8.1 irá terminar a 11 de julho de 2017 <!-- 1327781 -->  
A 11 de julho de 2017, será o fim do suporte base da plataforma do Windows Phone 8.1. O suporte de PCs com Windows 8.1 não será afetado.

Não existe impacto imediato nos dispositivos Windows Phone 8.1 que sejam geridos pelo serviço do Intune. Os dispositivos inscritos continuam a funcionar e todas as políticas, configurações e aplicações continuarão a funcionar conforme esperado. Tenha em atenção que não existem melhorias para a plataforma do Windows Phone 8.1 no Serviço do Intune e para a aplicação Portal da Empresa do Windows Phone 8.1.

Recomendamos que atualize os dispositivos Windows Phone 8.1 elegíveis para o Windows 10 Mobile quando for possível. 

## <a name="intune-apps"></a>Aplicações do Intune

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Suporte do Intune Managed Browser para iOS e Android <!---1374196--->

A partir de outubro de 2017, a aplicação Intune Managed Browser no Android irá suportar apenas dispositivos a executar o Android 4.4 e posterior. A aplicação Intune Managed Browser no iOS irá suportar apenas dispositivos a executar o iOS 9.0 e posterior. As versões anteriores do Android e iOS poderão continuar a utilizar o Managed Browser, mas não poderão instalar novas versões da aplicação e poderão não conseguir aceder a todas as funcionalidades da aplicação. Aconselhamos que atualize estes dispositivos para uma versão do sistema operativo suportada.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Permitir que os utilizadores finais acedam à aplicação Portal da Empresa para Android sem inscrição <!---1169910--->  
Em breve, os utilizadores finais não terão de inscrever os dispositivos para aceder à aplicação Portal da Empresa para Android. Os utilizadores finais em organizações que utilizam Políticas de Proteção de Aplicações deixarão de receber pedidos para inscrever os dispositivos quando abrem a aplicação Portal da Empresa. Os utilizadores finais também poderão instalar aplicações a partir do Portal da Empresa sem inscrever o dispositivo. 

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensagem de erro melhorada para quando um utilizador atinge o número máximo de dispositivos que é permitido inscrever <!-- 1270370 -->
Em vez de uma mensagem de erro genérica, os utilizadores veem uma mensagem de erro acionável amigável: "Inscreveu o número máximo de dispositivos permitidos pela sua equipa de TI. Remova um dispositivo inscrito ou peça ajuda ao seu administrador de TI."

### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nova experiência de início de sessão para utilizadores do Portal da Empresa para Android e das Políticas de Proteção de Aplicações <!-- 621669 -->
Os utilizadores finais poderão procurar aplicações, gerir dispositivos e ver informações de contacto de TI através da aplicação Portal da Empresa para Android sem inscrever os respetivos dispositivos Android. Além disso, se um utilizador final já utilizar uma aplicação protegida por Políticas de Proteção de Aplicações do Intune e iniciar o Portal da Empresa para Android, deixará de receber um pedido para inscrever o dispositivo. 

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Informe os utilizadores finais acerca das informações do dispositivo que podem ser vistas para iOS <!--739894-->
Iremos adicionar o **Tipo de Propriedade** ao ecrã Detalhes do Dispositivo na aplicação Portal da Empresa para iOS. Isto permite que os utilizadores obtenham mais informações sobre privacidade diretamente a partir desta página, através da documentação de utilizador final do Intune. Também poderão localizar estas informações no ecrã Acerca de.

### <a name="apps-details-pages-display-new-information-for-android-devices---1287476--"></a>As páginas de detalhes das aplicações apresentam novas informações em dispositivos Android <!--1287476-->
A página de detalhes das aplicações da aplicação Portal da Empresa para Android apresentará as categorias da aplicação que o administrador de TI definir para a respetiva aplicação.

### <a name="intune-mobile-application-management-mam-dialog-boxes-now-have-a-modern-interface----1199015---"></a>As caixas de diálogo da Gestão de Aplicações Móveis (MAM) do Intune têm agora uma interface moderna <!-- 1199015 -->
As caixas de diálogo da Gestão de Aplicações Móveis (MAM) do Intune foram atualizadas para um aspeto e funcionalidade modernos. O estilo de funcionamento das caixas de diálogo permanece igual.

Em dispositivos Android modernos, as caixas de diálogo de erros ou notificações apresentadas pelo Intune terão um aspeto e funcionalidade atualizados.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Nova definição para ativar e desativar a otimização da bateria na aplicação Portal da Empresa para Android <!--1405990-->
A página **Definições** na aplicação Portal da Empresa terá uma nova definição para permitir aos utilizadores desativar facilmente a otimização da bateria para as aplicações do Microsoft Authenticator e do Portal da Empresa. O nome da aplicação apresentado na definição varia consoante a aplicação que gere a conta profissional. Recomendamos que os utilizadores desativem a otimização da bateria para melhorar o desempenho das aplicações de trabalho que sincronizam e-mails e dados. 




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
