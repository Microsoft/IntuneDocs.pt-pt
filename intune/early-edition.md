---
title: "Edição antecipada"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 11/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 35bf193563deb34ac59df245c622bbc011d80b76
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/08/2017
---
# <a name="the-early-edition-for-microsoft-intune---december-2017"></a>A edição antecipada do Microsoft Intune – dezembro de 2017

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

### <a name="app-protection-policies-----679615---"></a>Políticas de Proteção de Aplicações <!-- 679615 -->
As Políticas de Proteção de Aplicações do Intune permitirão criar políticas predefinidas globais para ativar rapidamente a proteção em todos os utilizadores em todo o inquilino.

### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Revogar aplicações Programa Comprado em Volume para iOS <!-- 820863 -->
Para um determinado dispositivo que tenha uma ou mais aplicações Programa Comprado em Volume (VPP) para iOS, será capaz de revogar a licença de aplicação baseada em dispositivos associados do dispositivo. Revogar a licença de uma aplicação não desinstala a aplicação VPP relacionada do dispositivo. Para desinstalar uma aplicação VPP, tem de alterar a ação de atribuição para **Desinstalar**. Para obter mais informações, veja [Como gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune](vpp-apps-ios.md).

### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Revogar licenças para um token de Programa Comprado em Volume para iOS<!-- 820870 -->
Será capaz de revogar a licença de todas as aplicações Programa Comprado em Volume (VPP) para iOS para um determinado Token VPP.

### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>Eliminar um token de Programa Comprado em Volume para iOS <!-- 820879 -->
Poderá eliminar o token de Programa Comprado em Volume (VPP) para iOS através da consola. Tal poderá ser preciso quando tiver ocorrências duplicadas de um token de VPP.

### <a name="network-access-control-nac-device-check-in-reporting-----1232250---"></a>Relatórios de registo de dispositivos de Controlo de Acesso à Rede (NAC) <!-- 1232250 -->
Antes desta alteração, os administradores de TI não podiam determinar, do lado do Intune, se um dispositivo gerido pelo NAC estava a comunicar ou não com a solução de NAC. Quando um dispositivo gerido pelo NAC não está a comunicar com a solução de NAC, o dispositivo é considerado não conforme pela solução de NAC e, por conseguinte, é bloqueado pela mesma e subsequentemente bloqueado pelas políticas de acesso condicional que dependem do estado de conformidade do dispositivo.

Com esta alteração, os administradores de TI podem ver os dispositivos geridos pelo NAC que comunicaram com êxito com a solução de NAC. Esta nova capacidade consiste em duas novas funções de monitorização localizadas na carga de trabalho Conformidade do dispositivo no Intune. As estatísticas são apresentadas abaixo:
- **Média das chamadas do NAC na última hora**
- **Último pedido recebido do NAC (data/hora)**

### <a name="new-ios-device-action------1244701---"></a>Nova ação do dispositivo iOS <!-- 1244701 -->
Pode encerrar os dispositivos iOS 10.3 supervisionados. Esta ação encerra o dispositivo imediatamente sem avisar o utilizador final. A ação **Encerrar (apenas os supervisionados)** encontra-se nas propriedades do dispositivo ao selecionar um dispositivo na carga de trabalho **Dispositivo**.

### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755-eeready---"></a>Suporte para vários conectores para o processamento de certificados PFX e SCEP <!-- 1361755 eeready -->
Os clientes que utilizam o conector do NDES no local para entregar certificados para os dispositivos poderão configurar vários conectores num único inquilino.

Esta nova capacidade suporta o seguinte cenário:

- **Elevada disponibilidade**

    Cada conector do NDES obtém os pedidos de certificados do Intune.  Se um conector do NDES ficar offline, o outro conector poderá continuar a processar pedidos.

### <a name="new-automatic-redeployment-setting----1469168---"></a>Nova definição de reimplementação automática <!-- 1469168 -->
Esta definição permite aos utilizadores com direitos administrativos eliminarem todos os dados do utilizador e as definições através de **CTRL + Win + R** no ecrã de bloqueio do dispositivo. O dispositivo será automaticamente reconfigurado e reinscrito na gestão.

Esta definição encontra-se em Windows 10 -> Restrições de dispositivos -> Geral -> Reimplementação automática.

### <a name="install-office-apps-on-macos-devices----1494311---"></a>Instalar aplicações do Office em dispositivos macOS <!-- 1494311 -->
Poderá instalar aplicações do Office em dispositivos macOS. Este novo tipo de aplicação permitirá a instalação do Word, Excel, PowerPoint, Outlook e OneNote. Estas aplicações também vêm com o Microsoft AutoUpdater (MAU) para ajudar a manter as suas aplicações protegidas e atualizadas.

### <a name="surface-hub-resource-account-supported----1566442-eeready---"></a>Conta de recurso Surface Hub suportada <!-- 1566442 eeready -->
Será adicionada uma nova ação do dispositivo para que os administradores possam definir e atualizar a conta de recurso associada a um Surface Hub.

A conta de recurso é utilizada por um Surface Hub para se autenticar com o Skype/Exchange para que possa participar numa reunião. Pode criar uma conta de recurso exclusiva para que o Surface Hub apareça na reunião como a sala de conferência. Por exemplo, a conta de recursos pode aparecer como a *Sala de Conferência B41/6233*. Normalmente, a conta de recurso (conhecida como a conta do dispositivo) do Surface Hub tem de ser configurada para a localização da sala de conferência e sempre que outros parâmetros da conta de recurso precisarem ser alterados.

Quando os administradores querem atualizar a conta de recurso num dispositivo, têm de indicar as credenciais do Active Directory/Azure Active Directory atuais associadas ao dispositivo. Se a rotação da palavra-passe estiver ativada no dispositivo, os administradores terão de aceder ao Azure Active Directory para localizar a palavra-passe.

> [!NOTE]
> Todos os campos são enviados para baixo num pacote e substituem todos os campos que foram anteriormente configurados. Os campos vazios também substituem os campos existentes.

Seguem-se as definições que os administradores podem configurar:

- **Conta de recurso**  

   - **Utilizador do Active Directory**   
   Nomedomínio\nomeutilizador ou Nome Principal de Utilizador (UPN): user@domainname.com
   - **Palavra-passe**


- **Parâmetros da conta de recurso opcionais** (têm de ser definidos com a conta de recurso especificada)
   - **Período de rotação da palavra-passe**   
     Garante que a palavra-passe da conta é atualizada automaticamente pelo Surface Hub todas as semanas por motivos de segurança. Para configurar quaisquer parâmetros depois de ativar esta opção, terá primeiro de repor a palavra-passe na conta no Azure Active Directory.

   - **Endereço do protocolo SIP (Session Initiation Protocol)**    
     Usado apenas quando a autodiscovery falhar.

   - **E-mail**    
     Endereço de e-mail da conta de recurso/dispositivo.

   - **Exchange server**    
     Só é preciso quando a autodiscovery falhar.

   - **Sincronização do calendário**    
     Especifica se a sincronização do calendário e outros serviços do Exchange Server estão ativados. Por exemplo: reunião de sincronização.

### <a name="intune-now-provides-the-account-move-operation-----1573558-1579830---"></a>O Intune proporciona agora a operação Mover Conta <!-- 1573558, 1579830 -->
A operação **Mover Conta** migra um inquilino de uma Unidade de Escala do Azure (ASU) para outra. A operação **Mover Conta** pode ser utilizada para os cenários iniciados pelo cliente, quando telefona para a equipa de suporte do Intune para a pedir, e também pode ser um cenário impulsionado pela Microsoft onde a Microsoft tem de fazer ajustes ao serviço no back-end. Durante a operação **Mover Conta**, o inquilino entra no modo só de leitura (ROM). As operações do serviço, como inscrever, mudar o nome de dispositivos e atualizar o estado de conformidade, falharão durante o período do ROM.

### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Novas definições do perfil de configuração do dispositivo do Centro de Segurança do Windows Defender (WDSC) <!-- 1335507 -->
O Intune adiciona uma nova secção de definições do perfil de configuração do dispositivo na Endpoint Protection com o nome **Centro de Segurança do Windows Defender**. Os administradores de TI podem configurar os pilares aos quais os utilizadores finais da aplicação do Centro de Segurança do Windows Defender podem aceder. Se um administrador de TI ocultar um pilar na aplicação do Centro de Segurança do Windows Defender, nenhuma das notificações relacionadas com o pilar oculto serão apresentadas no dispositivo do utilizador.

Estes são os pilares que os administradores podem ocultar das definições do perfil de configuração do dispositivo do Centro de Segurança do Windows Defender:
- Proteção contra vírus e ameaças
- Desempenho e funcionamento do dispositivo
- Proteções de rede e de firewall
- Controlo de aplicações e browsers
- Opções de famílias

Os administradores de TI também podem personalizar as notificações que os utilizadores recebem. Por exemplo, pode configurar se os utilizadores recebem todas as notificações geradas por pilares visíveis no WDSC ou apenas as notificações críticas. As notificações não críticas incluem resumos periódicos da atividade e das notificações do Antivírus do Windows Defender quando as análises estiverem concluídas. Todas as outras notificações são consideradas críticas. Além disso, também pode personalizar o próprio conteúdo da notificação, por exemplo, pode proporcionar as informações de contacto de TI para incorporar nas notificações que são apresentadas nos dispositivos dos utilizadores.




<!-- the following are present prior to 1712 -->
### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Atribuir aplicações móveis do Office 365 a dispositivos iOS e Android ao utilizar o tipo de aplicação incorporada <!-- 1332318 -->
O tipo de aplicação **Incorporada** permite-lhe criar e atribuir aplicações do Office 365 mais facilmente aos dispositivos iOS e Android que está a gerir. Estas aplicações incluem aplicações do O365, tais como o Word, Excel, PowerPoint e OneDrive. Pode atribuir aplicações específicas ao tipo de aplicação e editar a configuração de informações da aplicação.

### <a name="single-sign-on-support-for-ios----1333645---"></a>Suporte de Início de Sessão Único para iOS <!-- 1333645 -->  
Poderá utilizar o Início de Sessão Único para utilizadores do iOS. As aplicações iOS que estão codificadas para procurar as credenciais dos utilizadores no payload de Início de Sessão Único são compatíveis com esta atualização de configuração do payload. Também pode utilizar o UPN e o ID de Dispositivo do Intune para configurar o Nome Principal e o Realm.

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocolo de texto autorizado a partir de Aplicações geridas <!-- 1414050  -->
As aplicações geridas pelo SDK da Aplicação Intune poderão enviar mensagens SMS.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Bloquear remotamente dispositivos macOS geridos com o Intune <!-- 1437691 -->
Poderá bloquear um dispositivo macOS perdido e definir um PIN de recuperação de 6 dígitos. Se estiver bloqueado, o painel **Descrição geral do dispositivos** apresenta o PIN até que seja enviada outra ação de dispositivo.

Para obter mais informações, veja [Bloquear remotamente dispositivos geridos com o Intune](device-remote-lock.md).


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

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Adicionar "Encontrar iPhone" para dispositivos pessoais <!--1427287-->
Poderá ver se os dispositivos iOS têm o Bloqueio de Ativação ativado. Esta funcionalidade estava anteriormente disponível no portal clássico do Intune.

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
