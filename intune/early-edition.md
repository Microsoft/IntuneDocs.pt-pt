---
title: Edição antecipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 95ad588b084319cd8a0f5f5c5d92da0e892eed50
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745048"
---
# <a name="the-early-edition-for-microsoft-intune---june-2018"></a>Edição antecipada do Microsoft Intune – junho de 2018

A **edição antecipada** oferece uma lista de funcionalidades disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida numa base limitada e está sujeita a alterações. Não partilhe estas informações fora da sua empresa. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu contacto do grupo de produtos da Microsoft se tiver dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

> [!Note]
>As seguintes alterações estão em desenvolvimento para o Intune. Para obter mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure

<!-- 1806 start -->

### <a name="corporate-owned-single-use-cosu-support-for-android-devices----1630973---"></a>Suporte de utilização única, pertencente à empresa (COSU) para dispositivos Android <!-- 1630973 -->

O Intune irá suportar dispositivos Android ao estilo de quiosque, bloqueados e altamente geridos. Isto permite que os administradores bloqueiem a utilização de um dispositivo para uma única aplicação ou pequeno conjunto de aplicações e impede que os utilizadores ativem outras aplicações ou efetuem outras ações no dispositivo.

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Suporte do macOS para o Programa de Inscrição de Dispositivos da Apple <!-- 747651 -->

O Intune irá suportar a inscrição de dispositivos macOS no Programa de Inscrição de Dispositivos da Apple (DEP). Para tal:

1. Em deploy.apple.com, atribua números de série do macOS a um servidor MDM.
2. Importe os números de série para o Intune.
3. Crie um perfil do programa de inscrição específico para dispositivos macOS.

### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Alterações de nome da Google para Android for Work e Play for Work <!--842873 -->
O Intune irá atualizar a terminologia do "Android for Work" para refletir as alterações de imagem corporativa da Google.  Os termos "Android for Work" e "Play for Work" deixarão de ser utilizados. Será utilizada terminologia diferente consoante o contexto:

- "Android Enterprise" refere-se à pilha de gestão de Android global e moderna.
- "Perfil Profissional" ou "Proprietário do Perfil" refere-se a dispositivos BYOD geridos com perfis profissionais.
- "Google Play Gerido" refere-se à loja de aplicações da Google.

### <a name="monitor-ios--app-configuration-status-per-device----880037-eeready-eestaged---"></a>Monitorizar o estado de configuração da aplicação iOS por dispositivo <!-- 880037 eeready eestaged -->

Enquanto administrador do Microsoft Intune, poderá monitorizar o estado de configuração da aplicação iOS para cada dispositivo gerido. No **Microsoft Intune**, no portal do Azure, selecione **Dispositivos** > **Todos os dispositivos**. Na lista de dispositivos geridos, selecione um dispositivo específico para apresentar um painel do dispositivo. No painel do dispositivo, selecione **Configuração da aplicação**.  

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Os teclados de terceiros podem ser bloqueados por definições de APP no iOS <!-- 1248481 -->
Em dispositivos iOS, os administradores do Intune poderão bloquear a utilização de teclados de terceiros ao aceder a dados da organização em aplicações protegidas por políticas. Quando a Política de Proteção de Aplicações (APP) estiver definida para bloquear teclados de terceiros, o utilizador do dispositivo irá receber uma mensagem da primeira vez que interagir com dados da empresa ao utilizar um teclado de terceiros. Todas as opções, além do teclado nativo, serão bloqueadas e os utilizadores de dispositivos não irão vê-las. Os utilizadores de dispositivos só verão a mensagem de diálogo uma vez. 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Criar política de conformidade de dispositivos com as definições de firewall em dispositivos macOS <!-- 1497640 -->
Quando criar uma nova política de conformidade do macOS (**Conformidade do dispositivo** > **Políticas** > **Criar política** > **Plataforma: macOS** > **Segurança do sistema**), estarão disponíveis algumas definições de **Firewall** novas: 
- **Firewall**: configure a forma como as ligações de entrada são processadas no seu ambiente.
- **Ligações de entrada**: **bloqueia** todas as ligações de entrada, exceto as ligações necessárias para serviços básicos de Internet, tal como o DHCP, Bonjour e IPSec. Esta definição também bloqueia todos os serviços de partilha.
- **Modo invisível**: **ative** o modo invisível para impedir que o dispositivo responda aos pedidos de pesquisa. O dispositivo continua a responder a pedidos recebidos de aplicações autorizadas.

Aplica-se a: macOS 10.12 e posterior

### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Utilizar sAMAccountName como o nome de utilizador da conta para perfis de e-mail <!-- 1500307 -->

Poderá utilizar **sAMAccountName** no local como o nome de utilizador da conta para perfis de e-mail para Android, iOS e Windows 10. Também poderá obter o domínio do atributo `domain` ou `ntdomain` no Azure Active Directory (Azure AD). Em alternativa, introduza um domínio estático personalizado.

Para utilizar esta funcionalidade, tem de sincronizar o atributo `sAMAccountName` do seu ambiente do Active Directory no local com o Azure AD.

Aplica-se a: Android, iOS, Windows 10 e posterior

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Exigir código de acesso não biométrico na inicialização da aplicação e após o tempo limite <!-- 1506985 -->

Ao exigir um código de acesso não biométrico na inicialização da aplicação e após o tempo limite especificado pelo administrador, o Intune irá fornecer segurança melhorada para aplicações com Gestão de Aplicações Móveis (MAM) ativada ao restringir a utilização da identificação biométrica para aceder a dados da empresa. As definições irão afetar os utilizadores que dependem do Touch ID (iOS), Face ID (iOS), Android Biometric ou outros métodos de autenticação biométricos futuros para aceder a aplicações com APP/MAM ativada. Estas definições poderão permitir que os administradores do Intune tenham um controlo mais abrangente sobre o acesso do utilizador, eliminando os casos em que um dispositivo com múltiplas impressões digitais ou outros métodos de acesso biométrico pode revelar dados da empresa a um utilizador errado. No portal do Azure, abra o **Microsoft Intune**. Selecione **Aplicações móveis** > **Políticas de proteção de aplicações** > **Adicionar uma política** > **Definições**. Localize a secção **Acesso** para obter definições específicas.

### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Eliminação seletiva dos dados da aplicação da organização <!-- 1507030 -->
Os administradores poderão configurar uma eliminação seletiva dos dados da organização como uma nova ação quando as condições de definições de Acesso de Políticas de Proteção de Aplicações (APP) não são cumpridas.  Esta funcionalidade ajuda os administradores a proteger e remover automaticamente dados confidenciais da organização de aplicações com base em critérios pré-configurados.

### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Revogar uma aplicação iOS comprada através do VPP <!-- 1777384 -->
Enquanto administrador do Microsoft Intune, poderá revogar a licença de uma aplicação iOS selecionada comprada através do programa de compra em volume (VPP). Pode notificar os utilizadores quando uma aplicação já não estiver atribuída aos mesmos. Revogar a licença de uma aplicação não desinstala a aplicação VPP relacionada do dispositivo. Para desinstalar uma aplicação VPP, tem de alterar a ação de atribuição para **Desinstalar**. A contagem de licenças recuperadas será refletida no nó **Aplicações Licenciadas** na carga de trabalho **Aplicação** do Intune. Para obter mais informações relacionadas com aplicações iOS obtidas pelo VPP, veja [Como gerir aplicações iOS compradas através de um programa de compra em volume com o Microsoft Intune](vpp-apps-ios.md).

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Pacotes de Idiomas do Office 365 Pro Plus <!-- 1833450 -->
Enquanto administrador do Intune, poderá implementar idiomas adicionais para aplicações do Office 365 Pro Plus geridas através do Intune. A lista de idiomas disponíveis inclui o **Tipo** do pacote de idiomas (núcleo, parcial e verificação). No portal do Azure, selecione **Microsoft Intune** > **Aplicações móveis** > **Aplicações** > **Adicionar**. Na lista **Tipo de aplicação**, no painel **Adicionar aplicação**, selecione **Windows 10** em **Office 365 Suite**. Selecione **Idiomas** no painel **Definições do Conjunto de Aplicações**.

### <a name="revoke-ios-vpp-app-license----1863797---"></a>Revogar licença de aplicação iOS obtida pelo VPP <!-- 1863797 -->
Enquanto administrador, poderá recuperar uma licença de aplicação iOS obtida pelo VPP atribuída a um utilizador ou dispositivo. Desinstalar uma aplicação iOS obtida pelo VPP também permitirá recuperar a licença da aplicação. Em seguida, pode optar por atribuir a licença da aplicação a outro utilizador ou dispositivo. Para obter mais informações sobre licenças de aplicação iOS obtida pelo VPP, veja [Gerir aplicações iOS compradas em volume no Microsoft Intune](vpp-apps-ios.md).

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Nova atualização da experiência de utilizador do site do Portal da Empresa <!--2000968 -->
Estamos a adicionar novas funcionalidades ao site do Portal da Empresa com base no feedback dos clientes. Irá ver uma melhoria significativa na usabilidade e funcionalidades existentes nos seus dispositivos Android, iOS e Windows. As áreas do site – tal como detalhes, feedback, suporte e descrição geral do dispositivo – irão receber uma nova estrutura moderna e responsiva. A atualização inclui ainda:

- Fluxos de trabalho simplificados em todas as plataformas de dispositivos
- Fluxos de inscrição e identificação de dispositivos melhorados
- Mensagens de erro mais úteis
- Linguagem mais simples, menos termos técnicos
- Capacidade de partilhar ligações diretas para as aplicações
- Desempenho melhorado para grandes catálogos de aplicações
- Acessibilidade melhorada para todos os utilizadores

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Editar as implementações de aplicações do Office 365 Pro Plus <!-- 2150145 -->
Enquanto administrador do Microsoft Intune, terá maior capacidade de editar as suas implementações de aplicações do Office 365 Pro Plus. No portal do Azure, selecione **Microsoft Intune** > **Aplicações móveis** > **Aplicações**. A partir da lista de aplicações, selecione o Office 365 Pro Plus Suite.  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>Revisão por linha de identificadores de dispositivos da empresa duplicados carregados <!-- 2203794 -->
Ao carregar IDs empresariais, o Intune fornece uma lista de duplicados e dá-lhe a opção de substituir ou manter as informações existentes. O relatório será apresentado se existirem duplicados após selecionar **Inscrição do dispositivo** > **Identificadores de Dispositivo da Empresa** > **Adicionar Identificadores**. 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Adicionar manualmente identificadores de dispositivos da empresa <!-- 2203803 -->
Poderá adicionar manualmente IDs de dispositivos da empresa. Selecione **Inscrição de dispositivos** > **Identificadores de Dispositivo da Empresa** > **Adicionar**.

### <a name="new-status-for-devices-in-device-configuration----2308882---"></a>Novo estado de dispositivos na configuração de dispositivos <!-- 2308882 -->
Em **Configuração de dispositivos** > **Descrição geral**, serão adicionados os seguintes estados novos:
- com êxito
- erro
- conflito
- pendente
- não aplicável Também é apresentada uma imagem que mostra a contagem de dispositivos de uma plataforma diferente. Por exemplo, se observar um perfil iOS, o novo mosaico mostra a contagem de dispositivos não iOS atribuídos a este perfil. 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>A conformidade do dispositivo suporta soluções de antivírus de terceiros <!-- 2325484 -->
Quando cria uma política de conformidade do dispositivo (**Conformidade do dispositivo** > **Políticas** > **Criar política** > **Plataforma: Windows 10** > **Definições** > **Segurança do sistema**), estarão disponíveis novas opções de **Segurança do Dispositivo**: 
- **Antivírus**: quando estiver definido como **Exigir**, pode verificar a conformidade com soluções de antivírus registadas com o Centro de Segurança do Windows, tal como Symantec. 
- **Antisspyware**: quando estiver definido como **Exigir**, pode verificar a conformidade com soluções de antisspyware registadas com o Centro de Segurança do Windows, tal como Symantec. 

Aplica-se a: Windows 10 e posterior 

<!-- 1805 start -->

### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Suporte para perfis de VPN do GlobalProtect da Palo Alto Networks <!-- 1333680 eeready ! -->

Com esta atualização, pode escolher o GlobalProtect da Palo Alto Networks como um tipo de ligação VPN para perfis de VPN no Intune (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Tipo de perfil** > **VPN**). Neste lançamento, são suportadas as seguintes plataformas: 

- iOS
- Windows 10

### <a name="set-compliance-by-device-location----851881----"></a>Definir a conformidade pela localização do dispositivo <!-- 851881 ! -->
Em algumas situações, pode ser útil restringir o acesso a recursos empresariais para uma localização específica, definida por uma ligação de rede. Poderá criar uma política de conformidade (**Conformidade do dispositivo** > **Localizações**) baseada no endereço IP do dispositivo. Se o dispositivo estiver fora do intervalo de IP, não conseguirá aceder a recursos empresariais.

Aplica-se a: dispositivos com o Android 6.0 e superior, com a aplicação Portal da Empresa atualizada

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Melhorias na resolução de problemas de instalação de aplicações <!-- 928990 -->
Por vezes, a instalação de aplicações em dispositivos geridos por MDM do Microsoft Intune pode falhar. Quando uma instalação de aplicações falha, pode ser difícil compreender o motivo da falha ou resolver o problema. Vamos lançar uma Pré-visualização Pública das nossas funcionalidades de Resolução de Problemas de Aplicações. Verá um novo nó em cada dispositivo denominado **Aplicações Geridas**. Este nó apresenta as aplicações que foram enviadas através do Intune MDM. Dentro do nó, verá uma lista de estados de instalação das aplicações. Se selecionar uma única aplicação, ser-lhe-á apresentada a vista de resolução de problemas dessa aplicação específica. Na vista de resolução de problemas, verá o ciclo de vida ponto a ponto da aplicação, por exemplo quando é que a aplicação foi criada, modificada, visada e enviada para um dispositivo. Além disso, se a instalação da aplicação não tiver sido concluída com êxito, ser-lhe-á apresentado o código de erro e uma mensagem útil sobre a causa do erro.

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Exigir código de acesso não biométrico na inicialização da aplicação progressiva e tempo limite <!-- 1506985 --> 

Ao exigir um código de acesso não biométrico na inicialização da aplicação progressiva e após o tempo limite especificado pelo administrador, o Intune irá fornecer segurança melhorada para aplicações com Gestão de Aplicações Móveis (MAM) ativada ao restringir a utilização da identificação biométrica para aceder a dados da empresa. As definições irão afetar os utilizadores que dependem do Touch ID (iOS), Face ID (iOS), Android Biometric ou outros métodos de autenticação biométricos futuros para aceder a aplicações com APP/MAM ativada. Estas definições poderão permitir que os administradores do Intune tenham um controlo mais abrangente sobre o acesso do utilizador, eliminando os casos em que um dispositivo com múltiplas impressões digitais ou outros métodos de acesso biométrico pode revelar dados da empresa a um utilizador errado. No portal do Azure, abra o **Microsoft Intune**. Selecione **Aplicações móveis** > **Políticas de proteção de aplicações** > **Adicionar uma política** > **Definições**. Localize a secção **Acesso** para obter definições específicas.

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloquear o acesso a aplicações baseado em fornecedores e modelos de dispositivos não aprovados <!-- 1425689 ! -->
O administrador de TI do Intune poderá impor uma lista específica de fabricantes Android e/ou de modelos iOS nas Políticas de Proteção de Aplicações do Intune. O administrador de TI pode fornecer uma lista separada por ponto e vírgula de fabricantes para políticas para Android e de modelos de dispositivos para políticas iOS. As Políticas de Proteção de Aplicações do Intune destinam-se apenas a Android e iOS. Existirão duas ações separadas que podem ser realizadas na lista especificada:
- O bloqueio do acesso a aplicações em dispositivos não especificados.
- Uma eliminação seletiva de dados empresariais em dispositivos não especificados. 

O utilizador não conseguirá aceder à aplicação visada se os requisitos da política não forem cumpridos. Com base nas definições escolhidas, os dados empresariais do utilizador podem ser bloqueados ou eliminados seletivamente da aplicação. Em dispositivos iOS, esta funcionalidade requer que a participação das aplicações (por exemplo, o WXP, Outlook, Managed Browser, Yammer) integre o SDK da Aplicação Intune para que as definições de versão mínima sejam impostas nas aplicações visadas. Esta integração decorre de forma gradual e está dependente das equipas específicas da aplicação. No Android, esta funcionalidade necessita da versão mais recente do Portal da Empresa. 

Nos dispositivos dos utilizadores finais, o cliente do Intune toma medidas com base numa única correspondência das cadeias especificadas no painel Intune das Políticas de Proteção de Aplicações. Isto depende inteiramente do valor comunicado pelo dispositivo. Como tal, recomendamos que o administrador de TI se certifique de que o comportamento pretendido é preciso. Pode fazê-lo ao testar esta definição com base em vários fabricantes e modelos de dispositivos direcionados para um grupo de utilizadores pequeno. No Microsoft Intune, selecione **Aplicações móveis** > **Políticas de proteção de aplicações** para ver e adicionar políticas de proteção de aplicações. Para obter mais informações sobre políticas de proteção de aplicações, veja [What are app protection policies](app-protection-policy.md) (O que são as políticas de proteção de aplicações?).

### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Ativar o modo de quiosque em dispositivos com o Windows 10 <!-- 1560072 ! -->
Nos dispositivos com o Windows 10, pode criar um perfil de configuração e ativar o modo de quiosque (**Configuração do Dispositivo** > **Perfis** > **Criar perfil** > **Windows 10** > **Restrições do Dispositivo** > **Quiosque**). Nesta atualização, o nome da definição **Quiosque (pré-visualização)** irá mudar para **Quiosque (obsoleto)**. A utilização da definição **Quiosque (obsoleto)** deixará de ser recomendada, embora continue a estar funcional até à atualização de julho. A definição **Quiosque (obsoleto)** será substituída pelo novo tipo de perfil de **Quiosque** (**Criar perfil** > **Windows 10** > **Quiosque (pré-visualização)**), que incluirá as definições para configurar Quiosques no Windows 10 RS4 e posterior.

Aplica-se ao Windows 10 e posterior.

### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Obter o ID do modelo do utilizador da aplicação (AUMID) associada para aplicações da Microsoft Store para Empresas no modo de quiosque <!-- 1560077 ! -->
O Intune poderá obter o IDs do modelo do utilizador da aplicação (AUMIDs) para aplicações da Microsoft Store para Empresas (WSfB) para proporcionar uma configuração melhorada do perfil de quiosque.

Para obter mais informações sobre aplicações da Microsoft Store para Empresas, veja [Gerir aplicações a partir da Microsoft Store para Empresas](windows-store-for-business.md).

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>Ações de acesso das políticas de proteção de aplicações <!-- 1483510 EEready -->
Brevemente, poderá configurar políticas de proteção de aplicações para avisar, apagar ou bloquear explicitamente dispositivos que não estiverem em conformidade. A ação mais recente, denominada *Apagar*, remove os seus dados empresariais de um dispositivo. Se ocorrer uma eliminação, o utilizador do dispositivo será notificado sobre os motivos da eliminação e os passos de remediação. Para algumas definições, como a versão mínima do SO, poderá realizar múltiplas ações, tais como bloquear e apagar. Estas ações são acionadas quando a aplicação é iniciada.

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>Novas informações de inventário para dispositivos Windows <!-- 1333569 eeready -->

Para dispositivos Windows, as seguintes informações de inventário serão disponibilizadas em cada dispositivo no separador **Hardware** (**Grupos** > **Todos os dispositivos móveis** > **Dispositivos** > selecione o dispositivo do utilizador > **Ver Propriedades** > **Hardware**):
- TPM
- Antivírus
- Antisspyware
- Firewall
- UAC
- Bateria
- Nome de domínio

Para obter mais informações sobre como estes dados são obtidos pelo CSP, veja as entradas de DeviceStatus no artigo [DeviceStatus CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp) (CSP do DeviceStatus).

### <a name="intune-and-the-microsoft-edge-browser----1818969---"></a>O Intune e o browser Microsoft Edge <!-- 1818969 -->
Agora o browser Microsoft Edge para dispositivos móveis (iOS e Android) suporta as políticas de proteção de aplicações do Intune. Os utilizadores que iniciarem sessão com as suas contas empresariais do Azure AD no browser Edge serão protegidos pelo Intune. 

### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Nova definição de idioma/região ao configurar o OOBE para o AutoPilot <!-- 1821766 -->
Será disponibilizada uma nova configuração para definir o idioma e a região de perfis AutoPilot durante a experiência OOBE (Out of Box Experience).

### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Nova definição para configurar o teclado do dispositivo <!-- 1821768 -->
Será disponibilizada uma nova definição para configurar o teclado de perfis AutoPilot durante a experiência OOBE (Out of Box Experience).

### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Utilizar o TeamViewer para partilhar ecrãs de dispositivos iOS e MacOS <!-- 1985547 -->
Atualmente, pode utilizar o TeamViewer para administrar remotamente [dispositivos Android e Windows geridos pelo Intune](device-profile-android-teamviewer.md).

Os administradores poderão estabelecer ligação ao TeamViewer e iniciar uma sessão de partilha de ecrã com dispositivos iOS e macOS. Os utilizadores de dispositivos iPhone, iPad e macOS podem partilhar os seus ecrãs em direto com qualquer outro computador ou dispositivo. 

### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>O gráfico de utilizadores de perfis de dispositivos está de volta <!-- 2160133 -->
Durante a melhoria das contagens apresentadas no gráfico de utilizadores do perfil do dispositivo (**Configuração do dispositivo** > **Perfis** > selecione um perfil existente > **Descrição geral**), este gráfico foi removido temporariamente.

Com esta atualização, o gráfico de utilizadores está de volta e é apresentado no portal do Azure.

### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Atribuir todos os utilizadores e dispositivos como grupos de âmbito <!-- 2196803 -->
Poderá atribuir todos os utilizadores, todos os dispositivos ou todos os utilizadores e dispositivos em grupos de âmbito. Para o fazer, selecione **Funções do Intune** > **Todas as funções** > **Gestor de políticas e perfis** > **Atribuições** > selecione uma atribuição > **Âmbito (grupos)**.

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Mudança dos perfis do Autopilot para a filtragem de grupo <!-- 1877935 -->
Atualmente, os perfis de implementação do AutoPilot podem ser atribuídos aos dispositivos selecionados. Depois do lançamento desta funcionalidade, eis o que deverá fazer para atribuir estes perfis:
- Criar grupos (Azure AD) que contenham dispositivos AutoPilot
- Atribuir os perfis pretendidos a um grupo do Azure AD. O perfil do AutoPilot será atribuído aos dispositivos AutoPilot nesse grupo.

### <a name="management-name-field-will-be-editable----1875989---"></a>O campo Nome de gestão passará a ser editável <!-- 1875989 -->
Poderá editar o campo Nome de gestão no painel **Propriedades** de um dispositivo. Para editar este campo, selecione **Dispositivos** > **Todos os dispositivos** > selecione o dispositivo > **Propriedades**. Pode utilizar o campo Nome de gestão para identificar um dispositivo de forma exclusiva.

<!-- 1804 start -->

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Adições às definições de Opções de Segurança do Dispositivo Local <!-- 1403702 -->
Poderá configurar definições adicionais de Opções de Segurança do Dispositivo Local para dispositivos com o Windows 10. As definições adicionais estarão disponíveis nas áreas do Cliente de Rede da Microsoft, Servidor de Rede da Microsoft, Segurança e acesso à rede e Início de sessão interativo. Estas definições encontram-se na categoria Endpoint Protection durante a criação de uma política de configuração de dispositivo Windows 10.

### <a name="rules-for-removing-devices----1609459---"></a>Regras para remover dispositivos <!-- 1609459 -->
Estarão disponíveis novas regras que lhe permitem remover automaticamente dispositivos que não se tenham registado durante o número de dias que definir. Para ver a nova regra, aceda ao painel **Intune**, selecione **Dispositivos** e selecione **Regras de remoção de dispositivo**.

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Impedir as experiências e aplicações de consumidor em dispositivos AutoPilot com o Windows 10 Enterprise RS4<!-- 1621980 -->
Poderá impedir a instalação de experiências e aplicações de consumidor nos seus dispositivos AutoPilot com o Windows 10 Enterprise RS4. Para ver esta funcionalidade, aceda a **Intune** > **Inscrição de dispositivos** > **Inscrição no Windows** > **Perfis do Windows AutoPilot** > **Criar Novo** > **Definições de inscrição**. 

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>Suporte de múltiplos Exchange Connectors <!-- 2070451 -->

Deixará de ficar limitado a um Microsoft Intune Exchange Connector por inquilino. O Intune suportará múltiplos Exchange Connectors para que possa configurar o acesso condicional do Intune com múltiplas organizações do Exchange no local.

Com um Exchange Connector no local do Intune, pode gerir o acesso de dispositivos a caixas de correio do Exchange no local com base no facto de um dispositivo estar ou não inscrito no Intune e estar ou não em conformidade com as políticas de conformidade de dispositivos do Intune. Para configurar um conector, transfira o Exchange Connector no local do Intune a partir do portal do Azure e instale-o num servidor na sua organização do Exchange. No dashboard do Microsoft Intune, selecione **Acesso no local** e, em **Configuração**, selecione **Conector do Exchange ActiveSync**. Transfira o Exchange Connector no local e instale-o num servidor na sua organização do Exchange. Como deixou de estar limitado a um Exchange Connector por inquilino, se tiver mais organizações do Exchange, pode seguir este processo para transferir e instalar um conector para cada organização do Exchange adicional.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacidade de implementar as aplicações de linha de negócio (LOB) necessárias em Todos os Utilizadores com computadores com o Windows 10 <!-- 1627835 RS4 -->
Os clientes poderão implementar as aplicações do Windows 10 de linha de negócio necessárias para as instalar em dispositivos. Isto permitirá que estas aplicações fiquem disponíveis para todos os utilizadores no dispositivo. Isto só é aplicável a computadores com o Windows 10.

### <a name="company-portal-enrollment-improved----1874230--"></a>Registo no Portal da Empresa melhorado <!-- 1874230-->
Os utilizadores que inscrevam um dispositivo ao utilizar o Portal da Empresa com a compilação 1703 e posteriores do Windows 10 poderão concluir o primeiro passo de inscrição sem sair da aplicação.

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



