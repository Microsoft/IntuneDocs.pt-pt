---
title: "Edição antecipada"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 01/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ac9cb0ad7d1b5e2c29e80f16c172f41c08d3a15d
ms.sourcegitcommit: 5fd17a57989c6da3d325ed2e0018ce16fe20bb79
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2018
---
# <a name="the-early-edition-for-microsoft-intune---january-2018"></a>Edição antecipada do Microsoft Intune – janeiro de 2018

A **edição antecipada** oferece uma lista de funcionalidades disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida numa base limitada e está sujeita a alterações. Não partilhe estas informações fora da sua empresa. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu contacto do grupo de produtos da Microsoft se tiver dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

> [!Note]
>As seguintes alterações estão em desenvolvimento para o Intune. Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices 
-->


## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure

### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546---"></a>Resolução de problemas de conformidade mais fácil na aplicação do Portal da Empresa para Windows 10 <!--676546 -->

Os utilizadores finais com dispositivos Windows poderão tocar no motivo de não conformidade na aplicação Portal da Empresa. Sempre que possível, esta ação irá reencaminhá-lo para a localização correta na aplicação de definições para resolver o problema. 

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>Nova opção para a autenticação do utilizador na inscrição em massa da Apple<!-- 747625 -->
O Intune dar-lhe-á a opção para autenticar dispositivos através da aplicação Portal da Empresa para os seguintes métodos de inscrição:

- Programa de Inscrição de Dispositivos da Apple
- Gestor Escolar da Apple
- Inscrição no Apple Configurator

Ao utilizar a opção do Portal da Empresa, a autenticação multifator do Azure Active Directory pode ser imposta sem bloquear estes métodos de inscrição.

Quando utilizar a opção do Portal da empresa, o Intune ignora a autenticação do utilizador no Assistente de Configuração iOS para a inscrição de afinidade do utilizador. Tal significa que o dispositivo está inscrito inicialmente como um dispositivo sem utilizador e, como tal, não receberá configurações ou políticas de grupos de utilizadores. Receberá apenas configurações e políticas para grupos de dispositivos. No entanto, o Intune instalará automaticamente a aplicação Portal da Empresa no Dispositivo. O primeiro utilizador a abrir e a iniciar sessão na aplicação Portal da Empresa será associado ao dispositivo no Intune. Neste momento, o utilizador receberá configurações e políticas dos grupos de utilizadores. A associação do utilizador não pode ser alterada sem a reinscrição.

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Suporte do Intune para várias contas do DEP da Apple/Apple School Manager <!-- 747685 -->
O Intune suportará a inscrição de dispositivos de um máximo de 100 contas diferentes do Programa de Inscrição de Dispositivos (DEP) da Apple ou do Apple School Manager. Cada token carregado pode ser gerido separadamente para dispositivos e perfis de inscrição. Um perfil de inscrição diferente pode ser automaticamente atribuído por token do DEP/School Manager carregado. Se forem carregados vários tokens do School Manager, só um poderá ser partilhado com a School Data Sync da Microsoft de cada vez.

Após a migração, as Graph APIs beta e os scripts publicados para gerir o DEP da Apple ou o ASM através do Graph deixarão de funcionar. Estão em desenvolvimento novas Graph APIs beta e serão lançadas após a migração.

### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eeready---"></a>Selecionar as categorias de dispositivos através das definições de Acesso Profissional ou Escolar<!-- 1058963 eeready --> 
Se tiver ativado o [mapeamento do grupo de dispositivos](https://docs.microsoft.com/en-us/intune/device-group-mapping), será pedido aos utilizadores no Windows 10 que selecionem uma categoria de dispositivos após a inscrição através do botão **Ligar** em **Definições** > **Contas** > **Acesso profissional ou escolar** ou durante a configuração inicial.

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Filtrar políticas de conformidade em dispositivos nos grupos de dispositivos <!--1307012 -->

Será capaz de filtrar políticas de conformidade de destino para os utilizadores nos grupos de utilizadores. Será capaz de filtrar políticas de conformidade para os dispositivos nos grupos de dispositivos. 

### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Incluir e excluir a atribuição de aplicações com base nos grupos <!-- 1406920 -->

Durante a atribuição de aplicações e, depois de selecionar um tipo de atribuição, poderá selecionar os grupos a incluir, bem como os grupos a excluir. Também poderá utilizar os grupos previamente criados (Todos os Utilizadores, Todos os Dispositivos e Todos os Utilizadores + Dispositivos) como grupos incluídos.

### <a name="remote-erase-command-support----1438084---"></a>Suporte do comando “Apagar” remoto <!-- 1438084 -->

Os administradores poderão emitir um comando Apagar remotamente.

> [!IMPORTANT]
> O comando apagar não pode ser invertido e deve ser utilizado com cuidado.

O comando apagar remove todos os dados, incluindo o sistema operativo, de um dispositivo. Esta operação também remove o dispositivo da gestão do Intune. Nenhum aviso é apresentado ao utilizador e a eliminação ocorre imediatamente após a emissão do comando.

Poderá configurar um PIN de recuperação de 6 dígitos. Este PIN pode servir para desbloquear o dispositivo apagado, altura em que irá iniciar a reinstalação do sistema operativo. Depois de a eliminação começar, o PIN é apresentado numa barra de estado no painel de descrição geral do dispositivo no Intune. O PIN será mantido enquanto a eliminação estiver em curso. Depois de concluída a eliminação, o dispositivo desaparece totalmente da gestão do Intune. Não se esqueça de registar o PIN de recuperação para que quem estiver a restaurar o dispositivo o possa utilizar.

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Dados encriptados da Windows Information Protection (WIP) nos resultados da pesquisa do Windows<!-- 1469193 -->

Uma nova definição na política da Windows Information Protection (WIP) vai permitir-lhe controlar se os dados encriptados da WIP estão incluídos nos resultados da pesquisa do Windows.

### <a name="website-learning-mode----1631908---"></a>Modo de Aprendizagem do Site<!-- 1631908 -->

O Intune vai introduzir uma extensão do Modo de aprendizagem da Windows Information Protection (WIP). Além de ver informações sobre as aplicações com a WIP, poderá ver um resumo dos dispositivos que partilharam dados de trabalho com os sites. Com estas informações, pode determinar os sites que devem ser adicionados às políticas WIP dos grupos e dos utilizadores.

### <a name="updates-to-compliance-emails---1637547---"></a>Atualizações em e-mails de conformidade <!--1637547 -->

Quando um e-mail é enviado para comunicar um dispositivo não conforme, serão incluídos detalhes sobre o dispositivo não conforme. O seguinte artigo será atualizado para indicar este facto: [ações automáticas de não conformidade](#actions-for-noncompliance).

### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>As políticas de Acesso Condicional do Intune só estão disponíveis no portal do Azure <!-- 1737088 1634311 --> 
Vamos simplificar o local onde configura e gere o acesso condicional. Deverá configurar e gerir as políticas no [portal do Azure](https://portal.azure.com), em **Azure Active Directory** > **Acesso Condicional**. Para a sua comodidade, também poderá aceder a este painel a partir do Intune no portal do Azure em **Intune** > **Acesso Condicional**.

###  <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Alertas para tokens expirados e tokens que irão expirar em breve <!-- 1639263 -->
A página de descrição geral mostrará alertas para tokens expirados e tokens que irão expirar em breve. Ao clicar num alerta com um único token, acederá à página de detalhes do token.  Se clicar num alerta com vários tokens, acederá a uma lista de todos os tokens com o estado deles. Os administradores devem renovar os tokens antes da data de expiração.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Impressão remota através de uma rede segura <!-- 1709994  -->
As soluções de impressão móveis sem fios da PrinterOn irão permitir aos utilizadores imprimir remotamente a partir de qualquer lugar e em qualquer altura através de uma rede segura. A PrinterOn será integrada com o SDK da Aplicação Intune para iOS e Android. Conseguirá filtrar políticas de proteção de aplicações para esta aplicação através do painel **Políticas de proteção de aplicações** do Intune na consola de administração. Os utilizadores finais conseguirão transferir a aplicação “PrinterOn para Microsoft” através da Play Store ou do iTunes para utilizar no seu ecossistema do Intune.

### <a name="approve-the-company-portal-app-for-android-for-work---1797090---"></a>Aprovar a aplicação do Portal da Empresa para o Android for Work <!--1797090 -->
Se a sua organização utilizar o Android for Work, terá de aprovar manualmente a aplicação Portal da Empresa para Android para continuar a receber atualizações automáticas da Google Play Store gerida.

### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>Microsoft Graph API para o Intune – Disponibilidade Geral <!-- 1833289 -->
As APIs do Intune no Microsoft Graph irão conceder acesso programático aos dados e aos métodos para automatizar as ações administrativas do serviço do Intune.  Com a **Disponibilidade Geral** destas APIs, os clientes, os parceiros e os programadores conseguirão tirar partido das APIs para as integrar em soluções internas ou comerciais que exijam ou estejam relacionadas com o suporte do Intune ou outros serviços Microsoft disponíveis através do Microsoft Graph. 

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Políticas de Proteção de Aplicações <!-- 679615 -->
As Políticas de Proteção de Aplicações do Intune permitirão criar políticas predefinidas globais para ativar rapidamente a proteção em todos os utilizadores em todo o inquilino.

### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Revogar aplicações Programa Comprado em Volume para iOS <!-- 820863 -->
Para um determinado dispositivo que tenha uma ou mais aplicações Programa Comprado em Volume (VPP) para iOS, será capaz de revogar a licença de aplicação baseada em dispositivos associados do dispositivo. Revogar a licença de uma aplicação não desinstala a aplicação VPP relacionada do dispositivo. Para desinstalar uma aplicação VPP, tem de alterar a ação de atribuição para **Desinstalar**. Para obter mais informações, veja [Como gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune](vpp-apps-ios.md).

### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Revogar licenças para um token de Programa Comprado em Volume para iOS<!-- 820870 -->
Será capaz de revogar a licença de todas as aplicações Programa Comprado em Volume (VPP) para iOS para um determinado Token VPP.

### <a name="network-access-control-nac-device-check-in-reporting-----1232250---"></a>Relatórios de registo de dispositivos de Controlo de Acesso à Rede (NAC) <!-- 1232250 -->
Antes desta alteração, os administradores de TI não podiam determinar, do lado do Intune, se um dispositivo gerido pelo NAC estava a comunicar ou não com a solução de NAC. Quando um dispositivo gerido pelo NAC não está a comunicar com a solução de NAC, o dispositivo é considerado não conforme pela solução de NAC e, por conseguinte, é bloqueado pela mesma e subsequentemente bloqueado pelas políticas de acesso condicional que dependem do estado de conformidade do dispositivo.

Com esta alteração, os administradores de TI podem ver os dispositivos geridos pelo NAC que comunicaram com êxito com a solução de NAC. Esta nova capacidade consiste em duas novas funções de monitorização localizadas na carga de trabalho Conformidade do dispositivo no Intune. As estatísticas são apresentadas abaixo:
- **Média das chamadas do NAC na última hora**
- **Último pedido recebido do NAC (data/hora)**

### <a name="new-ios-device-action------1244701---"></a>Nova ação do dispositivo iOS <!-- 1244701 -->
Pode encerrar os dispositivos iOS 10.3 supervisionados. Esta ação encerra o dispositivo imediatamente sem avisar o utilizador final. A ação **Encerrar (apenas os supervisionados)** encontra-se nas propriedades do dispositivo ao selecionar um dispositivo na carga de trabalho **Dispositivo**.


### <a name="intune-now-provides-the-account-move-operation-----1573558-1579830---"></a>O Intune proporciona agora a operação Mover Conta <!-- 1573558, 1579830 -->
A operação **Mover Conta** migra um inquilino de uma Unidade de Escala do Azure (ASU) para outra. A operação **Mover Conta** pode ser utilizada para os cenários iniciados pelo cliente, quando telefona para a equipa de suporte do Intune para a pedir, e também pode ser um cenário impulsionado pela Microsoft onde a Microsoft tem de fazer ajustes ao serviço no back-end. Durante a operação **Mover Conta**, o inquilino entra no modo só de leitura (ROM). As operações do serviço, como inscrever, mudar o nome de dispositivos e atualizar o estado de conformidade, falharão durante o período do ROM.




<!-- the following are present prior to 1712 -->
### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Atribuir aplicações móveis do Office 365 a dispositivos iOS e Android ao utilizar o tipo de aplicação incorporada <!-- 1332318 -->
O tipo de aplicação **Incorporada** permite-lhe criar e atribuir aplicações do Office 365 mais facilmente aos dispositivos iOS e Android que está a gerir. Estas aplicações incluem aplicações do O365, tais como o Word, Excel, PowerPoint e OneDrive. Pode atribuir aplicações específicas ao tipo de aplicação e editar a configuração de informações da aplicação.


### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>A resolução de conflitos de atribuição mudou para as aplicações da loja iOS <!-- 1480316 -->
Os utilizadores finais poderão reparar numa alteração quanto à disponibilidade das aplicações da loja iOS. Atualmente, uma aplicação que tenha sido atribuída a dois grupos com um conflito entre **Necessário e Disponível** e **Não Aplicável** é resolvida para **Necessário e Disponível**. Com a alteração, uma aplicação com este conflito é resolvida para **Não Aplicável**.

A alteração diz respeito à confusão gerada quando uma aplicação é atribuída a múltiplos grupos com intenções diferentes no que diz respeito às aplicações.

Se pretender ter a sua aplicação disponível no Portal dos Técnicos de Informação e no Portal da Empresa antes do lançamento do serviço em novembro, tem duas opções:

1. Remova a atribuição **Não Aplicável** do seu grupo.
2. Crie um novo grupo que não inclua os membros com a intenção **Necessário e Disponível** atribuída e atribua a intenção **Não Aplicável** a esse grupo.

Para obter mais informações, veja [Como atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md).

> [!Note]
> Após o lançamento, deixará de poder ver ou modificar as atribuições de aplicação da Gestão de Dispositivos Móveis (MDM) na consola clássica do Intune. No entanto, pode utilizar a consola do Azure ou a Graph API do Intune para fazer as suas atribuições de aplicações.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731---"></a>Gerir dispositivos Android for Work de forma independente dos dispositivos Android <!-- 1490731 -->
O Intune suporta a gestão de inscrição de dispositivos Android for Work de forma independente da plataforma Android. Estas definições são geridas em **Inscrição de Dispositivos** > **Restrições de inscrição** > **Restrições de Tipos de Dispositivos**. (Estavam anteriormente localizadas em **Inscrição de Dispositivos** > **Inscrição do Android for Work** > **Definições de Inscrição do Android for Work**.)

Por predefinição, as definições dos dispositivos Android for Work serão as mesmas que as definições dos seus dispositivos Android. No entanto, depois de alterar as definições do Android for Work, este já não será o caso.
 
Se bloquear a inscrição pessoal do Android for Work, só será possível inscrever dispositivos Android empresariais como Android for Work.

Ao trabalhar com as novas definições, considere o seguinte:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Se nunca tiver integrado a inscrição do Android for Work
A nova plataforma do Android for Work está bloqueada nas Restrições de Tipos de Dispositivos predefinidas. Depois de integrar a funcionalidade, pode permitir que os dispositivos sejam inscritos com o Android for Work. Para tal, altere a predefinição ou crie uma nova Restrição de Tipo de Dispositivo para substituir a Restrição de Tipo de Dispositivo predefinida.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Se já tiver integrado a inscrição do Android for Work
Se já a tiver integrado, a sua situação depende da definição que escolher:

| Definição | Estado do Android for Work em Restrição de Tipo de Dispositivo predefinida | Notas |
| --- | --- | --- |
| **Gerir todos os dispositivos como Android** | Bloqueado | Todos os dispositivos Android têm de ser inscritos sem o Android for Work. |
| **Gerir dispositivos suportados como Android for Work** | Permitido | Todos os dispositivos Android que suportam o Android for Work têm de ser inscritos com o Android for Work. |
| **Gerir dispositivos suportados para utilizadores apenas nestes grupos como Android for Work** | Bloqueado | Foi criada uma política de Restrição de Tipo de Dispositivo separada para substituir a predefinição. Esta política define os grupos que selecionou anteriormente para permitir a inscrição do Android for Work. Os utilizadores nos grupos selecionados continuarão a poder inscrever os seus dispositivos Android for Work. Todos os outros utilizadores não efetuam a inscrição com o Android for Work. |

Em todos os casos, mantém-se o seu regulamento pretendido. Não é necessária nenhuma ação da sua parte para manter a permissão global ou por grupo do Android for Work no seu ambiente.

Estas alterações começarão a ser implementadas com a atualização de novembro, mas a execução na sua conta poderá demorar algum tempo. Receberá uma notificação de confirmação no portal do Office 365 quando estas alterações entrarem em vigor na sua conta.


### <a name="configure-an-ios-app-pin----1586774---"></a>Configurar um PIN da aplicação para iOS <!-- 1586774 -->
Em breve poderá exigir um PIN para aplicações específicas para iOS. Pode configurar a data de expiração em dias e a obrigatoriedade de introdução de PIN através do portal do Azure. Quando for necessário, um utilizador terá de definir e utilizar um PIN novo para ter acesso a uma aplicação iOS. Apenas as aplicações iOS que têm ativada a proteção de aplicações com o SDK da Aplicação Intune suportarão esta funcionalidade.


<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Os sites do Azure Active Directory podem exigir a aplicação Intune Managed Browser e o suporte do Início de Sessão Único do Managed Browser (Pré-visualização Pública) <!-- 710595 -->   
Com o Azure Active Directory (Azure AD), poderá restringir o acesso a sites em dispositivos móveis na aplicação Intune Managed Browser. No Managed Browser, os dados dos sites permanecerão protegidos e separados dos dados pessoais dos utilizadores finais. Além disso, o Managed Browser suporta as funcionalidades de Início de Sessão Único para sites protegidos pelo Azure AD. Iniciar sessão no Managed Browser ou utilizá-lo num dispositivo com outra aplicação gerida pelo Intune permite que o Managed Browser aceda a sites empresariais protegidos pelo Azure AD sem que o utilizador tenha de introduzir as suas credenciais. Esta funcionalidade aplica-se a sites como o Outlook Web Access (OWA) e o SharePoint Online, bem como a outros sites empresariais como recursos de intranet acedidos através do Proxy de Aplicações do Azure.


<!-- the following are present prior to 1710 -->



### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Suporte para a política de atualização da edição do Windows 10 <!-- 903672(archived), 1119689 -->  
Poderá criar uma política de atualização da edição do Windows 10 que atualize os dispositivos Windows 10 para Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education e Windows 10 Professional Education N. Para obter detalhes sobre as atualizações da edição do Windows 10, veja [Como configurar atualizações da edição do Windows 10](edition-upgrade-configure-windows-10.md).




<!-- the following are present prior to 1709 -->



### <a name="android-for-work-support-for-lookout----1087312---"></a>Suporte do Android for Work para Lookout <!-- 1087312 -->   
O conector do Intune com o Lookout suportará dispositivos Android for Work ao utilizar a aplicação Lookout for Work. Pode implementar a aplicação Lookout dentro ou fora do contentor.

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Proteção de Aplicações Intune e Citrix MDX Development Tools <!-- 709185 -->
Pode gerir dispositivos e aplicações ao combinar o Citrix XenMobile MDX e o Microsoft Intune. Isto permite-lhe gerir aplicações com a política de proteção da aplicação Intune ao utilizar a tecnologia mVPN da Citrix.

Pode encontrar um repositório de códigos que contém a Ferramenta de Encapsulamento de Aplicações do Intune para iOS e Android, integrada com a tecnologia Citrix MDX mVPN.




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Redirecionar utilizadores do macOS para a nova aplicação Portal da Empresa <!--1380728-->   
Quando um utilizador final inicia sessão no site do Portal da Empresa para inscrever o seu dispositivo macOS, este será direcionado para transferir a nova aplicação Portal da Empresa para macOS para concluir o processo. Isto ocorre nos dispositivos macOS que utilizam o OS X El Capitan 10.11 ou posterior. 



<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Suporte do Intune Managed Browser para iOS e Android <!-- 1374196 -->
A partir de outubro de 2017, a aplicação Intune Managed Browser no Android irá suportar apenas dispositivos a executar o Android 4.4 e posterior. A aplicação Intune Managed Browser no iOS irá suportar apenas dispositivos a executar o iOS 9.0 e posterior. As versões anteriores do Android e iOS poderão continuar a utilizar o Managed Browser, mas não poderão instalar novas versões da aplicação e poderão não conseguir aceder a todas as funcionalidades da aplicação. Aconselhamos que atualize estes dispositivos para uma versão do sistema operativo suportada.


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensagem de erro melhorada para quando um utilizador atinge o número máximo de dispositivos que é permitido inscrever <!-- 1270370 -->
Em vez de uma mensagem de erro genérica, os utilizadores finais com dispositivos Android verão uma mensagem de erro amigável acionável: “Inscreveu o número máximo de dispositivos permitidos pelo administrador de TI. Remova um dispositivo inscrito ou peça ajuda ao seu administrador de TI.”




## <a name="notices"></a>Avisos

Neste momento, não existem avisos ativos.




### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.
