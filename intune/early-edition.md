---
title: "Edição antecipada"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f7cc595655950ef1bf2586e939b6f02e270e7afc
ms.sourcegitcommit: 5279a0bb8c5aef79aa57aa247ad95888ffe5a12b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/08/2017
---
# <a name="the-early-edition-for-microsoft-intune---november-2017"></a>A edição antecipada do Microsoft Intune – novembro de 2017

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


### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Atribuir aplicações móveis do Office 365 a dispositivos iOS e Android ao utilizar o tipo de aplicação incorporada <!-- 1332318 -->
O tipo de aplicação **Incorporada** permite-lhe criar e atribuir aplicações do Office 365 mais facilmente aos dispositivos iOS e Android que está a gerir. Estas aplicações incluem aplicações do O365, tais como o Word, Excel, PowerPoint e OneDrive. Pode atribuir aplicações específicas ao tipo de aplicação e editar a configuração de informações da aplicação.

### <a name="single-sign-on-support-for-ios----1333645---"></a>Suporte de Início de Sessão Único para iOS <!-- 1333645 -->  
Poderá utilizar o Início de Sessão Único para utilizadores do iOS. As aplicações iOS que estão codificadas para procurar as credenciais dos utilizadores no payload de Início de Sessão Único são compatíveis com esta atualização de configuração do payload. Também pode utilizar o UPN e o ID de Dispositivo do Intune para configurar o Nome Principal e o Realm.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API do inventário de aplicações para iOS 11 para a Deteção de Ameaças para Dispositivos Móveis <!-- 1391759 -->
O Intune recolhe informações do inventário de aplicações de dispositivos pessoais e empresariais e disponibiliza-as aos fornecedores de Deteção de Ameaças para Dispositivos Móveis (MTD), como o Lookout for Work. Poderá recolher o inventário de aplicações dos utilizadores de dispositivos com o iOS 11 ou uma versão superior.

**Inventário de aplicações**  
Os inventários de dispositivos iOS pessoais ou empresariais com o iOS 11 ou uma versão superior são enviados para o seu fornecedor de serviços de MTD. Os dados no inventário de aplicações incluem:

 - ID da Aplicação
 - Versão da Aplicação
 - Versão Abreviada da Aplicação
 - Nome da Aplicação
 - Tamanho da Coleção de Pacotes de Aplicação
 - Tamanho Dinâmico da Aplicação
 - A aplicação é ou não validada
 - A aplicação é ou não gerida

### <a name="audit-updates----1412961---"></a>Atualizações de auditoria <!-- 1412961 -->  
A auditoria do Intune fornece um registo das operações de alteração relacionadas com o Intune.  Todas as operações de criação, atualização, eliminação e realização de tarefas remotas são capturadas e retidas durante um ano.  O portal do Azure fornece uma vista dos dados de auditoria dos últimos 30 dias em cada carga de trabalho e podem ser filtrados.  A Graph API correspondente permite a obtenção dos dados de auditoria armazenados do último ano. 

A Auditoria está localizada no grupo **MONITORIZAÇÃO**. Existe um item de menu **Registos de Auditoria** para cada carga de trabalho.   

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocolo de texto autorizado a partir de Aplicações geridas <!-- 1414050  -->
As aplicações geridas pelo SDK da Aplicação Intune poderão enviar mensagens SMS.

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Reiniciar dispositivos iOS remotamente (apenas supervisionado) <!-- 1424595 -->
Poderá acionar o reinício de um dispositivo supervisionado com o iOS 10.3 ou uma versão superior ao utilizar uma ação de dispositivo. Para obter mais informações sobre como utilizar a ação de reinício de dispositivos, veja [Reiniciar remotamente dispositivos com o Intune](device-restart.md).

> [!Note]  
> Este comando necessita de um dispositivo supervisionado e do direito de acesso **Bloqueio do Dispositivo**. O dispositivo é reiniciado imediatamente. Os dispositivos iOS bloqueados por código de acesso não voltarão a ligar-se a uma rede Wi-Fi após o reinício. Após o reinício, estes dispositivos poderão não conseguir comunicar com o servidor.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Bloquear remotamente dispositivos macOS geridos com o Intune <!-- 1437691 -->
Poderá bloquear um dispositivo macOS perdido e definir um PIN de recuperação de 6 dígitos. Se estiver bloqueado, o painel **Descrição geral do dispositivos** apresenta o PIN até que seja enviada outra ação de dispositivo.

Para obter mais informações, veja [Bloquear remotamente dispositivos geridos com o Intune](device-remote-lock.md).

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings------1455974-----"></a>Definições da frequência de relatórios de Proteção Avançada Contra Ameaças do Windows Defender <!--- 1455974  --->
O serviço de Proteção Avançada Contra Ameaças do Windows Defender (WDATP) permite aos administradores gerir a frequência de relatórios dos dispositivos geridos. Com a nova opção **Acelerar a frequência do relatório de telemetria**, o WDATP recolhe os dados e avalia os riscos com mais frequência. A predefinição dos relatórios otimiza a velocidade e o desempenho. O aumento da frequência de relatórios pode ser útil para dispositivos de alto risco. Poderá encontrar esta definição no perfil **Windows Defender ATP** nas **Configurações do dispositivo**.

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

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Suporte para múltiplos conectores do Serviço de Inscrição de Dispositivos de Rede (NDES) <!-- 1528104 -->
O NDES permite a execução de dispositivos móveis sem credenciais de domínio para obter certificados com base no protocolo SCEP (Simple Certificate Enrollment Protocol). Com esta atualização, serão suportados múltiplos conectores do NDES.

### <a name="new-scep-profile-details-supported----1559808---"></a>Suporte para novos detalhes do perfil SCEP <!-- 1559808 -->
Os administradores poderão configurar definições adicionais ao criar um perfil SCEP em plataformas Windows, iOS, macOS e Android.  Os administradores podem definir o IMEI, o número de série ou o nome comum, incluindo o e-mail, no formato do nome do requerente.

### <a name="configure-an-ios-app-pin----1586774---"></a>Configurar um PIN da aplicação para iOS <!-- 1586774 -->
Em breve poderá exigir um PIN para aplicações específicas para iOS. Pode configurar a data de expiração em dias e a obrigatoriedade de introdução de PIN através do portal do Azure. Quando for necessário, um utilizador terá de definir e utilizar um PIN novo para ter acesso a uma aplicação iOS. Apenas as aplicações iOS que têm ativada a proteção de aplicações com o SDK da Aplicação Intune suportarão esta funcionalidade.

### <a name="retain-data-during-a-factory-reset-----1588489---"></a>Reter dados durante uma reposição de fábrica <!-- 1588489 -->
Estamos a adicionar suporte para uma nova capacidade de Reposição de fábrica do Windows. Atualmente, os administradores podem especificar se a inscrição de dispositivos e outros dados aprovisionados são retidos num dispositivo através de uma reposição de fábrica. 
 
Os seguintes dados são retidos através de uma reposição de fábrica:
- Contas de utilizador associadas ao dispositivo
- Estado da máquina (associação a um domínio, AADJ)
- Inscrição na MDM
- Aplicações OEM instaladas (aplicações Win32 e da loja)
- Perfil de utilizador
- Dados de utilizador fora do perfil de utilizador
- Início de sessão automático de utilizador
 
Os dados seguintes não são preservados:
- Ficheiros do utilizador
- Aplicações instaladas pelo utilizador (aplicações Win32 e da loja)
- Definições do dispositivo não predefinidas 

### <a name="app-install-status-report-now-a-bar-chart----1249446---"></a>Relatório do estado de instalação de aplicação agora em gráfico de barras <!-- 1249446 -->  
O relatório **Estado de instalação de aplicação** acessível para cada aplicação através da lista **Aplicação** na carga de trabalho **Aplicações móveis** será em breve convertido em gráfico de barras.

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Adicionar "Encontrar iPhone" para dispositivos pessoais <!--1427287-->
Poderá ver se os dispositivos iOS têm o Bloqueio de Ativação ativado. Esta funcionalidade estava anteriormente disponível no portal clássico do Intune.

### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restrições de inscrição atribuídas a grupos <!-- 747598 -->
Enquanto administrador do Intune, poderá criar restrições de inscrição personalizadas de Tipo de Dispositivo e Limite de Dispositivo para grupos de utilizadores.
 
O Portal do Azure do Intune permite-lhe criar até 25 instâncias de cada tipo de restrição que podem depois ser atribuídas a grupos de utilizadores. As restrições atribuídas a grupos substituem as restrições predefinidas.
 
Todas as instâncias de um tipo de restrição são mantidas numa lista estritamente ordenada. Esta ordem define um valor de prioridade para a resolução do conflito. Um utilizador afetado por mais do que uma instância de restrição só é restringido pela instância com o valor de prioridade mais elevada. Pode alterar a prioridade de uma determinada instância ao arrastá-la para uma posição diferente na lista. 
 
Esta funcionalidade será lançada com a migração das definições do Android for Work do menu de inscrição do Android for Work para o menu Restrições de Inscrição. Como esta migração pode demorar vários dias, poderão ser atualizadas outras partes da sua conta no lançamento de novembro antes da ativação da atribuição de grupos nas Restrições de Inscrição.

### <a name="windows-10-update-ring-assignments-are-displayed----1621837---"></a>Atribuições de cadência de atualização do Windows 10 são apresentadas <!-- 1621837 -->
Durante a **Resolução de problemas** do utilizador que está a ver, poderá ver todas as atribuições de cadências de atualização do Windows 10.  



<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Os sites do Azure Active Directory podem exigir a aplicação Intune Managed Browser e o suporte do Início de Sessão Único do Managed Browser (Pré-visualização Pública) <!-- 710595 -->   
Com o Azure Active Directory (Azure AD), poderá restringir o acesso a sites em dispositivos móveis na aplicação Intune Managed Browser. No Managed Browser, os dados dos sites permanecerão protegidos e separados dos dados pessoais dos utilizadores finais. Além disso, o Managed Browser suporta as funcionalidades de Início de Sessão Único para sites protegidos pelo Azure AD. Iniciar sessão no Managed Browser ou utilizá-lo num dispositivo com outra aplicação gerida pelo Intune permite que o Managed Browser aceda a sites empresariais protegidos pelo Azure AD sem que o utilizador tenha de introduzir as suas credenciais. Esta funcionalidade aplica-se a sites como o Outlook Web Access (OWA) e o SharePoint Online, bem como a outros sites empresariais como recursos de intranet acedidos através do Proxy de Aplicações do Azure.

### <a name="troubleshoot-enrollment-issues------746324----"></a>Resolução de problemas de inscrição <!--- 746324 --->  
A área de trabalho Resolução de Problemas irá apresentar problemas de inscrição de utilizadores. Os detalhes acerca do problema e os passos de remediação sugeridos podem ajudar os administradores e os operadores de suporte técnico a resolver problemas. Existem determinados problemas de inscrição que não são detetados e é possível que não existam sugestões de remediação para alguns erros.


















<!-- the following are present prior to 1710 -->



### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Suporte para a política de atualização da edição do Windows 10 <!-- 903672(archived), 1119689 -->  
Poderá criar uma política de atualização da edição do Windows 10 que atualize os dispositivos Windows 10 para Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education e Windows 10 Professional Education N. Para obter detalhes sobre as atualizações da edição do Windows 10, veja [Como configurar atualizações da edição do Windows 10](edition-upgrade-configure-windows-10.md).




<!-- the following are present prior to 1709 -->



### <a name="android-for-work-support-for-lookout----1087312---"></a>Suporte do Android for Work para Lookout <!-- 1087312 -->   
O conector do Intune com o Lookout suportará dispositivos Android for Work ao utilizar a aplicação Lookout for Work. Pode implementar a aplicação Lookout dentro ou fora do contentor.

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Proteção de Aplicações Intune e Citrix MDX Development Tools <!-- 709185 -->
Pode gerir dispositivos e aplicações ao combinar o Citrix XenMobile MDX e o Microsoft Intune. Isto permite-lhe gerir aplicações com a política de proteção da aplicação Intune ao utilizar a tecnologia mVPN da Citrix.

Pode encontrar um repositório de códigos que contém a Ferramenta de Encapsulamento de Aplicações do Intune para iOS e Android, integrada com a tecnologia Citrix MDX mVPN.


### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Suporte de elevada disponibilidade do conector do Exchange no local <!-- 676614 -->   
Pode ter múltiplas funções de Servidor de Acesso de Cliente (CAS) para o conector do Exchange no local. Por exemplo, se o CAS principal falhar, o conector do Exchange receberá uma consulta para reverter para outros CASs. Esta funcionalidade garante que o serviço não é interrompido.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Pacote de gestão do System Center Operations Manager para o conector do Exchange <!-- 885457 -->   
O pacote de gestão do System Center Operations Manager para o conector do Exchange estará disponível para ajudá-lo a analisar os registos do conector do Exchange. Esta pacote de gestão proporciona formas diferentes de monitorizar o Intune quando precisar de resolver problemas.





## <a name="intune-apps"></a>Aplicações do Intune

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Ajudar os utilizadores a resolver problemas com a aplicação Portal da Empresa para Android <!---1573324, 1573150, 1558616, 1564878--->
A aplicação Portal da Empresa para Android está a adicionar instruções para ajudar os utilizadores a compreender e, sempre que possível, a resolver autonomamente novos casos de utilização. 

- Será apresentada uma nova mensagem que explica que foi implementada uma política de conformidade para encriptação, mas o [fabricante do dispositivo não está a encriptar o dispositivo](/intune-user-help/your-device-appears-encrypted-but-cp-says-otherwise-android), de acordo com as [diretrizes recomendadas da Google] (https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setStorageEncryption(android.content.ComponentName, boolean).
- Os utilizadores finais serão encaminhados para o (portal do Azure Active Directory) [https://account.activedirectory.windowsazure.com/r/#/profile] para remover um dispositivo se tiverem atingido o número máximo de dispositivos que estão autorizados a adicionar. 
- Os utilizadores finais recebem uma lista de passos a seguir para os ajudar a [corrigir erros de ativação em dispositivos Samsung KNOX](https://go.microsoft.com/fwlink/?linkid=859718) ou a [desativar o modo de poupança de energia](/intune-user-help/power-saving-mode-android). Se nenhuma dessas soluções resolver o problema, forneceremos uma explicação sobre como [enviar registos para a Microsoft](/intune-user-help/send-logs-to-microsoft-ios). 


### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Nova ação "Resolver" disponível para dispositivos Android <!---1583480--->
A aplicação Portal da Empresa para Android está a introduzir a ação "Resolver" na página _Atualizar definições do dispositivo_. A seleção desta opção levará o utilizador diretamente para a definição que está a fazer com que o dispositivo não esteja em conformidade. A aplicação Portal da Empresa para Android suporta atualmente esta ação para as definições de [código de acesso do dispositivo](/intune-user-help/set-your-pin-or-password-android), [encriptação de dispositivos](/intune-user-help/encrypt-your-device-android), [depuração de USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) e [Origens Desconhecidas](/intune-user-help/you-need-to-turn-off-unknown-sources-android). 




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Redirecionar utilizadores do macOS para a nova aplicação Portal da Empresa <!--1380728-->   
Quando um utilizador final inicia sessão no site do Portal da Empresa para inscrever o seu dispositivo macOS, este será direcionado para transferir a nova aplicação Portal da Empresa para macOS para concluir o processo. Isto ocorre nos dispositivos macOS que utilizam o OS X El Capitan 10.11 ou posterior. 


<!-- the following are present prior to 1710 -->



### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>As aplicações que estão disponíveis com ou sem inscrição podem agora ser instaladas sem qualquer pedido de inscrição. <!-- 1334712 -->
As aplicações da empresa que foram disponibilizadas com ou sem inscrição na aplicação Portal da Empresa para Android podem ser instaladas sem qualquer pedido de inscrição.


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Suporte do Intune Managed Browser para iOS e Android <!-- 1374196 -->
A partir de outubro de 2017, a aplicação Intune Managed Browser no Android irá suportar apenas dispositivos a executar o Android 4.4 e posterior. A aplicação Intune Managed Browser no iOS irá suportar apenas dispositivos a executar o iOS 9.0 e posterior. As versões anteriores do Android e iOS poderão continuar a utilizar o Managed Browser, mas não poderão instalar novas versões da aplicação e poderão não conseguir aceder a todas as funcionalidades da aplicação. Aconselhamos que atualize estes dispositivos para uma versão do sistema operativo suportada.


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensagem de erro melhorada para quando um utilizador atinge o número máximo de dispositivos que é permitido inscrever <!-- 1270370 -->
Em vez de uma mensagem de erro genérica, os utilizadores veem uma mensagem de erro acionável amigável: "Inscreveu o número máximo de dispositivos permitidos pela sua equipa de TI. Remova um dispositivo inscrito ou peça ajuda ao seu administrador de TI."




## <a name="notices"></a>Avisos

Neste momento, não existem avisos ativos.




### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.
