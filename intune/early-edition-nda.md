---
title: Edição antecipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ab6c808fc860491ddece5751983071d40864c8dd
ms.sourcegitcommit: 8f68cd3112a71d1cd386da6ecdae3cb014d570f2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39575088"
---
# <a name="the-early-edition-for-microsoft-intune---august-2018"></a>A edição antecipada do Microsoft Intune – agosto de 2018

> [!Note]
> Notificação de contrato de confidencialidade: as seguintes alterações estão em desenvolvimento para o Intune. Estas informações são partilhadas ao abrigo de um contrato de confidencialidade numa base muito limitada. Não publique estas informações em redes sociais ou em sites públicos como o Twitter, UserVoice, Reddit, entre outros. 

A **edição antecipada** oferece uma lista de funcionalidades, partilhadas ao abrigo de um contrato de confidencialidade, que estarão disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida numa base limitada e está sujeita a alterações. Não publique no Twitter nem no UserVoice, nem partilhe estas informações de nenhuma outra forma com pessoas fora da sua empresa. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu contacto do grupo de produtos da Microsoft se tiver dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure

<!-- 1808 start -->

### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>O Windows Hello destina-se a utilizadores e dispositivos <!-- 1106609 -->
Quando cria uma política [Windows Hello para Empresas](windows-hello.md), esta aplica-se a todos os utilizadores numa organização (ao nível dos inquilinos). Com esta atualização, a política também pode ser aplicada a utilizadores ou dispositivos específicos através de uma política de configuração de dispositivos (**Configuração do Dispositivo** > **Perfis** > **Criar perfil** > **Identity Protection** > **Windows Hello para Empresas**).

No Intune no portal do Azure, a configuração e as definições do Windows Hello vão estar presentes tanto na **Inscrição de dispositivos** como na **Configuração do dispositivo**. A **Inscrição de dispositivos** destina-se a toda a organização (ao nível dos inquilinos) e suporta o Windows AutoPilot (OOBE). A **Configuração do dispositivo** destina-se a dispositivos e utilizadores através de uma política aplicada durante o registo.

Aplica-se a:  
- Windows 10 e posterior
- Windows Holographic for Business

### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Controle o modo S nos dispositivos Windows 10 e posteriores – pré-visualização pública <!-- 1958649 -->
Poderá criar um perfil de configuração de dispositivos que retira um dispositivo Windows 10 do modo S ou que impeça os utilizadores de retirarem o dispositivo do modo S. Esta funcionalidade estará em Intune > **Configuração do dispositivo** > **Perfis** >  **Windows 10 e posterior** > **Atualização de edição e interruptor de modo**.
[Introdução ao Windows 10 no modo S](https://www.microsoft.com/windows/s-mode) fornece mais informações sobre o modo S.
Aplica-se a: Windows 10 e posterior (1809 e posterior)

### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>A VPN moderna suporta atualizações para iOS <!-- 2459928, 1819876, and 2650856 -->
Uma atualização futura irá suportar os seguintes clientes VPN de iOS: 
- F5 Access (versão 3.0.1 e superior)
- Citrix SSO
- Palo Alto Networks GlobalProtect (versão 5.0 e superior). Também numa futura atualização:
- Os nomes dos tipos de ligação **F5 Access** existentes serão alterados para **F5 Access Legacy** (por atualizações da imagem corporativa F5)
- Os nomes dos tipos de ligação **Palo Alto Networks GlobalProtect** serão alterados para **Legacy Palo Alto Networks GlobalProtect** (por atualizações da imagem corporativa Palo Alto). 

Os perfis existentes com estes tipos de ligações continuam a funcionar com o cliente VPN legado. Se estiver a utilizar o Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN ou Legacy Palo Alto Networks GlobalProtect com iOS, deve avançar para as novas aplicações. Faça-o assim que possível para garantir que o acesso VPN está disponível para dispositivos iOS, conforme os mesmos são atualizados para iOS 12.

### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Bloquear o Portal da Empresa no modo de aplicação única até o utilizador iniciar sessão <!--1067692 --> 
Terá a opção de executar o Portal da Empresa no modo de Aplicação Única se autenticar um utilizador através do Portal da Empresa em vez do Assistente de Configuração durante a inscrição de DEP. Esta opção bloqueia o dispositivo imediatamente após a conclusão do Assistente de Configuração, para que um utilizador tenha de iniciar sessão para aceder ao dispositivo. Este processo assegura que o dispositivo conclui a inclusão e não fica órfão num estado sem qualquer utilizador ligado.

### <a name="scope-tags-for-policies---1081974-eeready--"></a>Etiquetas de âmbito para políticas <!--1081974 eeready-->

Poderá criar etiquetas de âmbito para limitar o acesso aos recursos do Intune. Adicione uma etiqueta de âmbito a uma atribuição de função e, em seguida, adicione a etiqueta de âmbito a um perfil de configuração. A função apenas terá acesso aos recursos com perfis de configuração com etiquetas de âmbito correspondentes (ou nenhuma etiqueta de âmbito).
Para criar uma etiqueta de âmbito, escolha **Funções do Intune** > **Âmbito (Etiquetas)** > **Criar**.
Para adicionar uma etiqueta de âmbito a uma atribuição de função, escolha **Funções do Intune** > **Todas as funções** > **Gestor de Políticas e Perfis** > **Atribuições** > **Âmbito (Etiquetas)**.
Para adicionar uma etiqueta de âmbito a um perfil de configuração, escolha **Configuração do dispositivo** > **Perfis** > escolha um perfil > **Propriedades** > **Âmbito (Etiquetas)**.

### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Atribuir um utilizador e um nome amigável a um dispositivo do AutoPilot <!--1346521 -->
Uma pré-visualização pública futura permitirá aos administradores atribuir um utilizador a um único dispositivo do Autopilot.  Os administradores também serão capazes de atribuir nomes amigáveis para dar as boas-vindas ao utilizador quando estão a configurar o dispositivo com o Autopilot.

Aplica-se a: Windows Insider 1809 ou uma versão posterior (durante a pré-visualização).

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token Apple VPP utilizado por outra MDM <!-- 1488946 -->
O Intune irá detetar e mostrar detalhes se um token de programa de compras em volume (VPP) da Apple estiver a ser utilizado pelo Intune e outra MDM.

### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Suporte de túnel de pacotes para perfis VPN por aplicação iOS para tipos de ligações personalizadas e Pulse Secure <!-- 1520957 -->
Ao utilizar perfis VPN por aplicação iOS, poderá utilizar o túnel de camada de aplicação (proxy de aplicação) ou o túnel de nível do pacote (túnel do pacote). Estas opções estarão disponíveis com os seguintes tipos de ligação:
- VPN Personalizada
- Pulse Secure, se não tiver a certeza sobre o valor a utilizar, consulte a documentação do seu fornecedor de VPN.
Aplica-se a: iOS

### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858-eeready---"></a>Zscaler é uma ligação disponível para perfis VPN em dispositivos iOS <!-- 1769858 eeready -->
Quando cria um perfil de configuração de dispositivo VPN de iOS (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **iOS** plataforma > **VPN** tipo de perfil), existem vários tipos de ligação, incluindo Cisco, Citrix e muito mais. Uma atualização futura adiciona Zscaler como um tipo de ligação. 
A página [Definições de VPN para dispositivos com iOS](vpn-settings-ios.md) lista os tipos de ligação disponíveis.

### <a name="block-windows-personal-device-enrollments----1849498---"></a>Bloquear inscrições de dispositivos pessoais do Windows <!-- 1849498 -->
Poderá impedir que os dispositivos pessoais do Windows se inscrevam com a [gestão de dispositivos móveis](windows-enroll.md) no Intune. A inscrição de dispositivos com o [agente de PC do Intune](manage-windows-pcs-with-microsoft-intune.md) não pode ser bloqueada com esta funcionalidade.
Para ver esta funcionalidade, escolha **Inscrição de dispositivos** > **Restrições de dispositivos**.
A ativação desta restrição não tem qualquer efeito nos dispositivos já inscritos.
Após a ativação da restrição, o Intune irá verificar se cada novo pedido de inscrição do Windows foi autorizado como uma inscrição empresarial. Os seguintes métodos estão qualificados como autorizados como uma inscrição empresarial:
- A inscrição de utilizadores está a utilizar uma [conta do gestor de inscrição de dispositivos]( device-enrollment-manager-enroll.md).

- O dispositivo é inscrito através do [Windows AutoPilot](enrollment-autopilot.md).
- O número IMEI do dispositivo é listado na **Inscrição de dispositivos** > **[Identificadores de dispositivos da empresa]( corporate-identifiers-add.md)**).
- O dispositivo é inscrito através de um [pacote de aprovisionamento em massa](windows-bulk-enroll.md).
- O dispositivo é inscrito através da [inscrição automática do SCCM para cogestão](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management).
As inscrições não autorizadas serão bloqueadas.
As inscrições seguintes estão marcadas como empresariais pelo Intune, mas uma vez que não oferecem ao administrador do Intune controlo por dispositivo, serão bloqueadas:
- [Inscrição na MDM automática](windows-enroll.md#enable-windows-10-automatic-enrollment) com [associação do Azure Active Directory durante a configuração do Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md).
- [Inscrição na MDM automática](windows-enroll.md#enable-windows-10-automatic-enrollment) com [associação do Azure Active Directory a partir da configuração do Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md).
Os seguintes métodos de inscrição pessoal também serão bloqueados:
- [Inscrição na MDM automática](windows-enroll.md#enable-windows-10-automatic-enrollment) com [Adicionar Conta Profissional a partir das Definições do Windows](https://docs.microsoft.com/azure/active-directory/user-help/device-management-azuread-registered-devices-windows10-setup).

- Opção [Apenas inscrição na MDM]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) a partir das Definições do Windows.

### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Especifique os padrões de nome de computador num perfil AutoPIlot <!--1849855-->
Poderá especificar um modelo de nome do computador para gerar e definir o [nome do computador](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) durante a inscrição do AutoPilot. Terá de especificar isso no perfil do AutoPilot localizado em **Inscrição de dispositivos** > **Inscrição Windows** > **Serviço do Windows Autopilot Deployment** > **Perfis**. Apenas podem ser utilizados carateres alfanuméricos e o hífen.
Aplica-se a: Windows Insider 1809 ou uma versão posterior (durante a pré-visualização).

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>O número da versão do iOS e o número de compilação são apresentados <!-- 1892471 -->
Em **Conformidade do dispositivo** > **Conformidade do dispositivo**, é apresentada a versão do sistema operativo iOS. Numa atualização futura, também será apresentado o número de compilação.
Quando as atualizações de segurança são lançadas, normalmente, a Apple não altera o número da versão, mas atualiza o número de compilação. Ao apresentar o número de compilação, pode verificar facilmente se foi instalada uma atualização da vulnerabilidade.

### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Para os perfis do Windows AutoPilot, oculte as opções de alteração de conta na página de início de sessão da empresa e na página de erro do domínio <!--1901669 -->
Uma pré-visualização pública incluirá novas opções de perfil do Windows AutoPilot para os administradores ocultarem as opções de alteração de conta nas páginas de início de sessão da empresa e de erro do domínio. Para ocultar essas opções, é preciso configurar a Imagem Corporativa da Empresa no Azure Active Directory. Aplica-se a: Windows Insider 1809 ou uma versão posterior (durante a pré-visualização).

### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Atrasar quando as atualizações de software iOS são apresentadas no dispositivo <!-- 1949583 -->
Em Intune > **Atualizações de Software** > **Atualizar políticas para iOS**, pode configurar os dias e as horas em que não pretende que os dispositivos instalem as atualizações. Numa atualização futura, poderá atrasar a apresentação de uma atualização de software no dispositivo, entre 1 a 90 dias. 
[Configurar as políticas de atualização de iOS no Microsoft Intune](software-updates-ios.md) lista as definições atuais.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivos extintos no dashboard de conformidade do dispositivo <!-- 1981119 -->
Numa atualização futura, os dispositivos extintos serão removidos do dashboard de conformidade do dispositivo. Tal irá alterar os seus números de conformidade.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Nova atualização da experiência de utilizador do site do Portal da Empresa <!--2000968 -->
Serão adicionadas novas funcionalidades ao site do Portal da Empresa com base no feedback dos clientes. Irá ver uma melhoria significativa na usabilidade e funcionalidades existentes nos seus dispositivos Android, iOS e Windows. As áreas do site – tal como detalhes, feedback, suporte e descrição geral do dispositivo – irão receber uma nova estrutura moderna e responsiva. A atualização inclui ainda:
- Fluxos de trabalho simplificados em todas as plataformas de dispositivos
- Fluxos de inscrição e identificação de dispositivos melhorados
- Mensagens de erro mais úteis
- Linguagem mais simples, menos termos técnicos
- Capacidade de partilhar ligações diretas para as aplicações
- Desempenho melhorado para grandes catálogos de aplicações
- Acessibilidade melhorada para todos os utilizadores

### <a name="office-365-proplus-version----2213968-eeready---"></a>Office 365 versão ProPlus <!-- 2213968 eeready -->
Ao atribuir as aplicações do Office 365 ProPlus a dispositivos Windows 10 com o Intune, poderá selecionar a versão do Office. No portal do Azure, selecione **Microsoft Intune** > **Aplicações** > **Adicionar Aplicações**. Em seguida, selecione **Conjunto de Aplicações Office 365 ProPlus (Windows 10)** na lista suspensa **Tipo**. Selecione **Definições do conjunto de aplicações** para apresentar o painel associado. Defina **Atualizar Canal** para um valor, como **Mensal**. Opcionalmente, remova a outra versão do Office (msi) dos dispositivos de utilizador final ao selecionar **Sim**. Selecione **Específico** para instalar uma versão específica do Office no canal selecionado em dispositivos de utilizador final. Agora, pode selecionar a **Versão específica** do Office a utilizar. As versões disponíveis serão alteradas ao longo do tempo. Por conseguinte, ao criar uma nova implementação, as versões disponíveis podem ser mais recentes e não ter determinadas versões mais antigas disponíveis. As implementações atuais continuarão a implementar a versão mais antiga, mas a lista de versões será constantemente atualizada por canal. Para obter mais informações, veja [Overview of update channels for Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus) (Descrição geral dos canais de atualização do Office 365 ProPlus).

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Configurar o perfil para ignorar alguns ecrãs durante o Assistente de Configuração <!-- 2276470 -->
Quando cria um perfil de inscrição do macOS, poderá configurá-lo para ignorar qualquer um dos ecrãs seguintes quando um utilizador executar o Assistente de Configuração:
- Migração de Android
- Sinal de Exibição
- Privacidade
- iCloudStorage

### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Alteração no processo de atualização de conectores no local <!-- 2277554 -->
Com base no feedback dos clientes, a forma como as atualizações são realizadas nos conectores no local será alterada. Depois da instalação inicial de um conector no local, as atualizações serão automáticas. Esta alteração começará com o novo PFX Certificate Connector para o Microsoft Intune e, em seguida, estender-se-á a outros tipos de conectores no local. 

### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Suporte para a definição do Registo de DNS para VPN do Windows 10 <!-- 2282852 -->
Será capaz de configurar perfis de VPN do Windows 10 para registar dinamicamente os endereços IP atribuídos à interface de VPN com o DNS interno, sem a necessidade de utilizar perfis personalizados.
[Definições de VPN do Windows 10](vpn-settings-windows-10.md) lista as definições de perfil VPN atuais disponíveis. 

### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-for-work-devices----2451462---"></a>Restringir aplicações e bloquear o acesso aos recursos da empresa em dispositivo iOS e Android for Work <!-- 2451462 -->
Em **Conformidade do dispositivo** > **Políticas** > **Criar política** > **Android for Work**  >  **Segurança do Sistema**, haverá uma nova definição de **Aplicações restritas**. Esta nova definição utiliza uma política de conformidade para bloquear o acesso aos recursos da empresa, caso determinadas aplicações estejam instaladas no dispositivo. O dispositivo é considerado não compatíveis até que as aplicações restritas sejam removidas do dispositivo.
Aplica-se a: 
- iOS

### <a name="export-azure-classic-portal-compliance-policies-to-csv-file----2469637---"></a>Exportar políticas de conformidade do portal clássico do Azure para um ficheiro .csv <!-- 2469637 -->
As políticas de conformidade que criou no portal clássico do Azure serão preteridas.  Quando isto acontecer, pode rever e eliminar as políticas existentes, mas não pode atualizá-las. Pode exportar as políticas como um ficheiro separado por vírgulas (ficheiro .csv). Em seguida, utilize os detalhes no ficheiro para recriar estas políticas no portal do Azure no Intune.
> [!IMPORTANT]
> Quando o portal clássico do Azure for extinguido, não poderá aceder às suas políticas nem as poderá ver. Desta forma, confirme que as exporta e recria no portal do Azure antes do portal clássico do Azure ser extinguido.

<!-- 1807 start -->

### <a name="more-sync-opportunities-in-the-company-portal-app-for-windows----2683177---"></a>Mais oportunidades de sincronização na aplicação Portal da Empresa para Windows <!-- 2683177 -->
A aplicação Portal da Empresa para Windows irá adicionar uma ação de sincronização de dispositivos à barra de tarefas do Windows e às listas de atalhos do menu Iniciar. Clique em qualquer uma das localizações para sincronizar rapidamente os seus dispositivos e obter acesso a recursos empresariais.  

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Repor códigos de acesso de dispositivos a partir da aplicação Portal da Empresa para Windows 10 <!-- 2101282 --> 
Em breve, os seus colaboradores poderão repor o PIN ou o código de acesso dos respetivos dispositivos diretamente a partir da aplicação Portal da Empresa para Windows 10. Esta funcionalidade estará disponível em dispositivos remotos e locais geridos pelo Intune que suportem a reposição de códigos de acesso. Consoante o tipo de dispositivo, um pedido feito para um dispositivo remoto irá remover o código de acesso atual do dispositivo ou criar um código de acesso temporário. Os utilizadores que efetuarem um pedido de reposição para um dispositivo local serão redirecionados para a aplicação Definições do dispositivo.  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>Novas experiências de navegação na aplicação Portal da Empresa para Windows <!-- 2317227 -->  
Ao navegar ou procurar aplicações na aplicação Portal da Empresa para Windows, terá a possibilidade de alternar entre a vista **Mosaicos** existente e a vista **Detalhes** recentemente adicionada. A nova vista apresenta os detalhes das aplicações, como o nome, o publicador, a data de publicação e o estado da instalação.  

A página **Aplicações** irá apresentar uma vista **Instalado** que lhe permite ver detalhes sobre as instalações de aplicações concluídas e em curso. Quer partilhar feedback ou ideias sobre as novas alterações? Envie-nos o seu feedback na aplicação Portal da Empresa.

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Experiência da aplicação Portal da Empresa melhorada para gestores de inscrições de dispositivos <!-- 675800 -->
Quando um gestor de inscrições de dispositivos (DEM) inicia sessão na aplicação Portal da Empresa para Windows, a aplicação só apresentará o dispositivo atual do DEM. Esta melhoria irá reduzir os erros de tempo limite que ocorriam quando a aplicação tentava carregar todos os dispositivos inscritos pelo DEM.  

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Utilizar licenças de dispositivos VPP para aprovisionar previamente o Portal da Empresa durante a inscrição do DEP <!-- 1608345 -->
Poderá utilizar licenças de dispositivos do Programa de Compras em Volume (VPP) para aprovisionar previamente o Portal da Empresa durante as inscrições do Programa de Registo de Aparelho (DEP). Para tal, ao criar ou editar um perfil de inscrição, especifique o token VPP que pretende utilizar para instalar o Portal da Empresa. Certifique-se de que o token não expira e que tem licenças suficientes para a aplicação Portal da Empresa. Nos casos em que o token expirar ou esgotar as licenças, o Intune irá iniciar o Portal da Empresa a partir da App Store (esta ação irá exigir um ID Apple).

###  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Extensões de ficheiros de aplicações de linha de negócio (LOB) do Windows <!-- 1884873 -->
As extensões de ficheiros de aplicações de linha de negócio do Windows agora incluirão *.msi*, *.appx*, *.appxbundle*, *.msix* e *.msixbundle*. Pode adicionar uma aplicação no Microsoft Intune ao selecionar **Aplicações móveis** > **Aplicações** > **Adicionar**. O painel **Adicionar aplicação** é apresentado, o qual lhe permite selecionar o **Tipo de aplicação**. Para aplicações LOB do Windows, selecione o tipo de aplicação **Linha de negócio**, selecione o **Ficheiro de pacote de aplicação** e, em seguida, introduza um ficheiro de instalação com a extensão adequada.

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Pacote de configuração do Windows Defender ATP adicionado automaticamente ao perfil de configuração <!-- 2144658 -->
Agora, ao utilizar dispositivos de [Proteção Avançada Contra Ameaças e inclusão](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) no Intune, irá transferir um pacote de configuração e adicioná-lo ao seu perfil de configuração. Numa atualização futura, o Intune passará a obter automaticamente o pacote a partir do Centro de Segurança do Windows Defender e a adicioná-lo ao seu perfil.

Aplica-se ao Windows 10 e posterior.

### <a name="check-for-sccm-compliance----2192052---"></a>Verificar a conformidade com o SCCM <!-- 2192052 -->
Uma futura atualização irá incluir uma nova definição de conformidade do System Center Configuration Manager (SCCM) (**Conformidade do dispositivo** > **Políticas** > **Criar política** > **Windows 10**). O SCCM envia sinais de conformidade ao Intune. Com a definição do Intune, pode exigir que todos os sinais do SCCM devolvam o estado "compatível".

Por exemplo, pode exigir que todas as atualizações do software sejam instaladas nos dispositivos. No SCCM, este requisito apresenta o estado "Instalado". Se algum dos programas no dispositivo apresentar um estado desconhecido, o dispositivo será marcado como não compatível no Intune.

Aplica-se ao Windows 10 e posterior

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertas de token VPP prestes a expirar ou de licenças do Portal da Empresa que se estão a esgotar <!-- 2237572 -->
Se utilizar o Programa de Compras em Volume (VPP) para aprovisionar previamente o Portal da Empresa durante a inscrição do DEP, o Intune irá alertá-lo quando o token VPP estiver prestes a expirar e quando as licenças do Portal da Empresa se estiverem a esgotar.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Confirmação necessária para eliminar o token VPP que está a ser utilizado para aprovisionar previamente o Portal da Empresa <!-- 2237634 -->
Será pedida uma confirmação para eliminar um token de Programa de Compras em Volume (VPP) se o mesmo estiver a ser utilizado para aprovisionar previamente o Portal da Empresa durante a inscrição do DEP.

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Definições de segurança adicionais para o Windows Installer <!-- 2282430 -->
Poderá permitir que os utilizadores controlem a instalação de aplicações. Se estiver ativada, esta definição permite continuar as instalações que, caso contrário, seriam interrompidas devido a uma violação de segurança. Poderá configurar o Windows Installer para utilizar permissões elevadas ao instalar programas num sistema. Além disso, poderá ativar os itens do Windows Information Protection (WIP) para serem indexados e os metadados acerca dos mesmos para serem armazenados numa localização não encriptada. Quando a política estiver desativada, os itens protegidos pelo WIP não serão indexados e não serão apresentados nos resultados na Cortana ou no explorador de ficheiros. A funcionalidade destas opções estará desativada por predefinição. 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Os teclados de terceiros podem ser bloqueados por definições de APP no iOS <!-- 1248481 -->
Em dispositivos iOS, os administradores do Intune poderão bloquear a utilização de teclados de terceiros ao aceder a dados da organização em aplicações protegidas por políticas. Quando a Política de Proteção de Aplicações (APP) estiver definida para bloquear teclados de terceiros, o utilizador do dispositivo irá receber uma mensagem da primeira vez que interagir com dados da empresa ao utilizar um teclado de terceiros. Todas as opções, além do teclado nativo, serão bloqueadas e os utilizadores de dispositivos não irão vê-las. Os utilizadores de dispositivos só verão a mensagem de diálogo uma vez. 

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Exigir código de acesso não biométrico na inicialização da aplicação e após o tempo limite <!-- 1506985 -->

Ao exigir um código de acesso não biométrico na inicialização da aplicação e após o tempo limite especificado pelo administrador, o Intune irá fornecer segurança melhorada para aplicações com Gestão de Aplicações Móveis (MAM) ativada ao restringir a utilização da identificação biométrica para aceder a dados da empresa. As definições irão afetar os utilizadores que dependem do Touch ID (iOS), Face ID (iOS), Android Biometric ou outros métodos de autenticação biométricos futuros para aceder a aplicações com APP/MAM ativada. Estas definições poderão permitir que os administradores do Intune tenham um controlo mais abrangente sobre o acesso do utilizador, eliminando os casos em que um dispositivo com múltiplas impressões digitais ou outros métodos de acesso biométrico pode revelar dados da empresa a um utilizador errado. No portal do Azure, abra o **Microsoft Intune**. Selecione **Aplicações móveis** > **Políticas de proteção de aplicações** > **Adicionar uma política** > **Definições**. Localize a secção **Acesso** para obter definições específicas.

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Pacotes de Idiomas do Office 365 Pro Plus <!-- 1833450 -->
Enquanto administrador do Intune, poderá implementar idiomas adicionais para aplicações do Office 365 Pro Plus geridas através do Intune. A lista de idiomas disponíveis inclui o **Tipo** do pacote de idiomas (núcleo, parcial e verificação). No portal do Azure, selecione **Microsoft Intune** > **Aplicações móveis** > **Aplicações** > **Adicionar**. Na lista **Tipo de aplicação**, no painel **Adicionar aplicação**, selecione **Windows 10** em **Office 365 Suite**. Selecione **Idiomas** no painel **Definições do Conjunto de Aplicações**.

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>Pré-visualização de uma nova atualização da experiência de utilizador do site do Portal da Empresa <!--2000968 -->
Estamos a adicionar novas funcionalidades ao site do Portal da Empresa/catálogo de aplicações iOS com base no feedback dos clientes. Irá ver uma melhoria significativa na usabilidade e funcionalidades existentes nos seus dispositivos Android, iOS e Windows. As áreas do site – tal como detalhes, feedback, suporte e descrição geral do dispositivo – irão receber uma nova estrutura moderna e responsiva. A atualização inclui ainda:

- Fluxos de trabalho simplificados em todas as plataformas de dispositivos
- Fluxos de inscrição e identificação de dispositivos melhorados
- Mensagens de erro mais úteis
- Linguagem mais simples, menos termos técnicos
- Capacidade de partilhar ligações diretas para as aplicações
- Desempenho melhorado para grandes catálogos de aplicações
- Acessibilidade melhorada para todos os utilizadores

A atualização está atualmente em pré-visualização. Pode registar-se para aderir à pré-visualização em http://aka.ms/webcpflighting

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Exigir código de acesso não biométrico na inicialização da aplicação progressiva e tempo limite <!-- 1506985 --> 

Ao exigir um código de acesso não biométrico na inicialização da aplicação progressiva e após o tempo limite especificado pelo administrador, o Intune irá fornecer segurança melhorada para aplicações com Gestão de Aplicações Móveis (MAM) ativada ao restringir a utilização da identificação biométrica para aceder a dados da empresa. As definições irão afetar os utilizadores que dependem do Touch ID (iOS), Face ID (iOS), Android Biometric ou outros métodos de autenticação biométricos futuros para aceder a aplicações com APP/MAM ativada. Estas definições poderão permitir que os administradores do Intune tenham um controlo mais abrangente sobre o acesso do utilizador, eliminando os casos em que um dispositivo com múltiplas impressões digitais ou outros métodos de acesso biométrico pode revelar dados da empresa a um utilizador errado. No portal do Azure, abra o **Microsoft Intune**. Selecione **Aplicações móveis** > **Políticas de proteção de aplicações** > **Adicionar uma política** > **Definições**. Localize a secção **Acesso** para obter definições específicas.

<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacidade de implementar as aplicações de linha de negócio (LOB) necessárias em Todos os Utilizadores com computadores com o Windows 10 <!-- 1627835 RS4 -->
Os clientes poderão implementar as aplicações do Windows 10 de linha de negócio necessárias para as instalar em dispositivos. Isto permitirá que estas aplicações fiquem disponíveis para todos os utilizadores no dispositivo. Isto só é aplicável a computadores com o Windows 10.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Atualizar a experiência de Ajuda e Feedback na aplicação Portal da Empresa para Android <!--1631531 -->

A experiência de Ajuda e Feedback na aplicação Portal da Empresa para Android será atualizada para estarmos alinhados com as melhores práticas para aplicações Android. A aplicação Portal da Empresa para Android será atualizada nos próximos meses para dividir o item de menu **Ajuda e Feedback** em itens de menu **Ajuda** e **Enviar Feedback** separados. A página **Ajuda** terá uma secção de **Perguntas Frequentes** e o botão **Suporte por E-mail** para que os utilizadores finais carreguem registos para a Microsoft e enviem e-mails para a empresa de suporte com a descrição do problema. O menu **Enviar Feedback** orientará o utilizador ao longo do processo padrão de submissão de feedback da Microsoft, que lhe pedirá para escolher entre "Gosto de algumas coisas", "Não de gosto de algumas coisas" ou "Tenho uma ideia".

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Políticas de Proteção de Aplicações <!-- 679615 -->
As Políticas de Proteção de Aplicações do Intune permitirão criar políticas predefinidas globais para ativar rapidamente a proteção em todos os utilizadores em todo o inquilino.

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Avisos

Neste momento, não existem avisos ativos.

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.



