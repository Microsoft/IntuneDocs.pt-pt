---
title: Edição antecipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f3cbfad85e4a7a97d9bbf98e2ad239fda7cc29e4
ms.sourcegitcommit: d40bfb6af66f2ce7026c0151ace98ec23f1cf76e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
---
# <a name="the-early-edition-for-microsoft-intune---may-2018"></a>Edição antecipada do Microsoft Intune – maio de 2018

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

<!-- 1805 start -->

### <a name="set-compliance-by-device-location----851881----"></a>Definir a conformidade pela localização do dispositivo <!-- 851881 ! -->
Em algumas situações, pode ser útil restringir o acesso a recursos empresariais para uma localização específica, definida por uma ligação de rede. Poderá criar uma política de conformidade (**Conformidade do dispositivo** > **Localizações**) baseada no endereço IP do dispositivo. Se o dispositivo estiver fora do intervalo de IP, não conseguirá aceder a recursos empresariais.

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Melhorias na resolução de problemas de instalação de aplicações <!-- 928990 -->
Por vezes, a instalação de aplicações em dispositivos geridos por MDM do Microsoft Intune pode falhar. Quando uma instalação de aplicações falha, pode ser difícil compreender o motivo da falha ou resolver o problema. Vamos lançar uma Pré-visualização Pública das nossas funcionalidades de Resolução de Problemas de Aplicações. Verá um novo nó em cada dispositivo denominado **Aplicações Geridas**. Este nó apresenta as aplicações que foram enviadas através do Intune MDM. Dentro do nó, verá uma lista de estados de instalação das aplicações. Se selecionar uma única aplicação, ser-lhe-á apresentada a vista de resolução de problemas dessa aplicação específica. Na vista de resolução de problemas, verá o ciclo de vida ponto a ponto da aplicação, por exemplo quando é que a aplicação foi criada, modificada, visada e enviada para um dispositivo. Além disso, se a instalação da aplicação não tiver sido concluída com êxito, ser-lhe-á apresentado o código de erro e uma mensagem útil sobre a causa do erro. 

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
Brevemente, poderá configurar políticas de proteção de aplicações para avisar, apagar ou bloquear explicitamente dispositivos que não estiverem em conformidade. A ação mais recente, denominada *Apagar*, remove os seus dados empresariais de um dispositivo. Se ocorrer uma eliminação, o utilizador do dispositivo será notificado sobre os motivos da eliminação e os passos de remediação. Para algumas definições, como a versão mínima do SO, poderá realizar múltiplas ações, tais como bloquear e apagar.

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>Novas informações de inventário para dispositivos Windows <!-- 1333569 eeready -->

Para dispositivos Windows, as seguintes informações de inventário serão disponibilizadas em cada dispositivo no separador **Hardware** (**Grupos** > **Todos os dispositivos móveis** > **Dispositivos** > selecione o dispositivo do utilizador > **Ver Propriedades** > **Hardware**):
- TPM
- Antivírus
- Antisspyware
- Firewall
- UAC
- Bateria
- Nome de domínio

Para obter mais informações sobre como estes dados são obtidos pelo CSP, veja as entradas de DeviceGuard no artigo [DeviceStatus CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp) (CSP do DeviceStatus).

### <a name="intune-and-the-microsoft-edge-browser----1818969---"></a>O Intune e o browser Microsoft Edge <!-- 1818969 -->
Agora o browser Microsoft Edge para dispositivos móveis (iOS e Android) suporta as políticas de proteção de aplicações do Intune. Os utilizadores que iniciarem sessão com as suas contas empresariais do Azure AD no browser Edge passarão a ser protegidos pelo Intune. 

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
Poderá atribuir todos os utilizadores, todos os dispositivos ou todos os utilizadores e dispositivos em grupos de âmbito.

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Mudança dos perfis do Autopilot para a filtragem de grupo <!-- 1877935 -->
Atualmente, os perfis de implementação do AutoPilot podem ser atribuídos aos dispositivos selecionados. Depois do lançamento desta funcionalidade, eis o que deverá fazer para atribuir estes perfis:
- Criar grupos (Azure AD) que contenham dispositivos AutoPilot
- Atribuir os perfis pretendidos a um grupo do Azure AD. O perfil do AutoPilot será atribuído aos dispositivos AutoPilot nesse grupo.

### <a name="management-name-field-will-be-editable----1875989---"></a>O campo Nome de gestão passará a ser editável <!-- 1875989 -->
Poderá editar o campo Nome de gestão no painel **Propriedades** de um dispositivo. Para editar este campo, selecione **Dispositivos** > **Todos os dispositivos** > selecione o dispositivo > **Propriedades**. Pode utilizar o campo Nome de gestão para identificar um dispositivo de forma exclusiva.

<!-- 1804 start -->


### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Adições às definições de Opções de Segurança do Dispositivo Local <!-- 1403702 -->
Poderá configurar definições adicionais de Opções de Segurança do Dispositivo Local para dispositivos com o Windows 10. As definições adicionais estarão disponíveis nas áreas do Cliente de Rede da Microsoft, Servidor de Rede da Microsoft, Segurança e acesso à rede e Início de sessão interativo. Estas definições encontram-se na categoria Endpoint Protection durante a criação de uma política de configuração de dispositivo Windows 10.

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Exigir a instalação de políticas, aplicações, perfis de certificado e de rede <!-- 1553555 -->
Os administradores poderão impedir os utilizadores finais de aceder ao ambiente de trabalho do Windows 10 RS4 até que o Intune instale as políticas, aplicações e perfis de certificado e de rede durante o aprovisionamento de dispositivos AutoPilot.

### <a name="rules-for-removing-devices----1609459---"></a>Regras para remover dispositivos <!-- 1609459 -->
Estarão disponíveis novas regras que lhe permitem remover automaticamente dispositivos que não se tenham registado durante o número de dias que definir. Para ver a nova regra, aceda ao painel **Intune**, selecione **Dispositivos** e selecione **Regras de remoção de dispositivo**.

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Impedir as experiências e aplicações de consumidor em dispositivos AutoPilot com o Windows 10 Enterprise RS4<!-- 1621980 -->
Poderá impedir a instalação de experiências e aplicações de consumidor nos seus dispositivos AutoPilot com o Windows 10 Enterprise RS4. Para ver esta funcionalidade, aceda a **Intune** > **Inscrição de dispositivos** > **Inscrição no Windows** > **Perfis do Windows AutoPilot** > **Criar Novo** > **Definições de inscrição**. 

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>Suporte múltiplo do Exchange Connector <!-- 2070451 -->

Deixará de ficar limitado a um Exchange Connector no Microsoft Intune por inquilino. O Intune suportará múltiplos Exchange Connectors para que possa configurar o acesso condicional do Intune com múltiplas organizações do Exchange no local.

Com um Exchange Connector no local do Intune, pode gerir o acesso de dispositivos a caixas de correio do Exchange no local com base no facto de um dispositivo estar ou não inscrito no Intune e estar ou não em conformidade com as políticas de conformidade de dispositivos do Intune. Para configurar um conector, transfira o Exchange Connector no local do Intune a partir do portal do Azure e instale-o num servidor na sua organização do Exchange. No dashboard do Microsoft Intune, selecione **Acesso no local** e, em **Configuração**, selecione **Conector do Exchange ActiveSync**. Transfira o Exchange Connector no local e instale-o num servidor na sua organização do Exchange. Como deixou de estar limitado a um Exchange Connector por inquilino, se tiver mais organizações do Exchange, pode seguir este processo para transferir e instalar um conector para cada organização do Exchange adicional.

### <a name="support-coming-for-new-cisco-anyconnect-client-for-ios----1333708---"></a>Suporte disponível em breve para o novo cliente do Cisco AnyConnect para iOS <!-- 1333708 -->

Os novos perfis de VPN criados para o Cisco AnyConnect para iOS funcionarão com a versão Cisco AnyConnect 4.0.7x e posteriores. Os perfis de VPN existentes do Cisco AnyConnect para iOS serão identificados como **Cisco Legacy AnyConnect** e continuarão a funcionar com a versão Cisco AnyConnect 4.0.5x tal como atualmente.

> [!NOTE]
> Esta alteração diz respeito apenas a dispositivos iOS. Continuará a haver apenas uma opção Cisco AnyConnect para Android, Android for Work e macOS.

#### <a name="more-information"></a>Mais informações

Tem de criar um novo perfil de VPN do Cisco AnyConnect para iOS para suportar a nova aplicação porque a nova aplicação Cisco AnyConnect e a aplicação Cisco Legacy AnyConnect são aplicações separadas. Se estiver a gerir o cliente AnyConnect no seu ambiente, também terá de implementar a nova aplicação Cisco AnyConnect. Para concluir uma atualização, também tem de eliminar o seu perfil de VPN Cisco Legacy AnyConnect e remover a aplicação Cisco Legacy AnyConnect.

A integração de controlo de acesso à rede (NAC) não funcionará para o novo cliente AnyConnect na versão inicial. Estamos a trabalhar com a Cisco para fornecer a integração de NAC numa versão futura do Intune.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacidade de implementar as aplicações de linha de negócio (LOB) necessárias em Todos os Utilizadores com computadores com o Windows 10 <!-- 1627835 RS4 -->
Os clientes poderão implementar as aplicações do Windows 10 de linha de negócio necessárias para as instalar em dispositivos. Isto permitirá que estas aplicações fiquem disponíveis para todos os utilizadores no dispositivo. Isto só é aplicável a computadores com o Windows 10.

### <a name="company-portal-enrollment-improved----1874230--"></a>Registo no Portal da Empresa melhorado <!-- 1874230-->
Os utilizadores que inscrevam um dispositivo ao utilizar o Portal da Empresa com a compilação 1703 e posteriores do Windows 10 poderão concluir o primeiro passo de inscrição sem sair da aplicação.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Atualizar a experiência de Ajuda e Feedback na aplicação Portal da Empresa para Android <!--1631531 -->

Iremos atualizar a experiência de Ajuda e Feedback na aplicação Portal da Empresa para Android para estarmos alinhados com as melhores práticas para aplicações Android. Iremos atualizar a aplicação Portal da Empresa para Android nos próximos meses para dividir o item de menu **Ajuda e Feedback** em itens de menu **Ajuda** e **Enviar Feedback** separados. A página **Ajuda** terá uma secção de **Perguntas Frequentes** e o botão **Suporte por E-mail** para que os utilizadores finais carreguem registos para a Microsoft e enviem e-mails para a empresa de suporte com a descrição do problema. O menu **Enviar Feedback** orientará o utilizador ao longo do processo padrão de submissão de feedback da Microsoft, que lhe pedirá para escolher entre "Gosto de algumas coisas", "Não de gosto de algumas coisas" ou "Tenho uma ideia".

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Políticas de Proteção de Aplicações <!-- 679615 -->
As Políticas de Proteção de Aplicações do Intune permitirão criar políticas predefinidas globais para ativar rapidamente a proteção em todos os utilizadores em todo o inquilino.

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Os sites do Azure Active Directory podem exigir a aplicação Intune Managed Browser e o suporte do Início de Sessão Único do Managed Browser (Pré-visualização Pública) <!-- 710595 -->   
Com o Azure Active Directory (Azure AD), poderá restringir o acesso a sites em dispositivos móveis na aplicação Intune Managed Browser. No Managed Browser, os dados dos sites permanecerão protegidos e separados dos dados pessoais dos utilizadores finais. Além disso, o Managed Browser suporta as funcionalidades de Início de Sessão Único para sites protegidos pelo Azure AD. Iniciar sessão no Managed Browser ou utilizá-lo num dispositivo com outra aplicação gerida pelo Intune permite que o Managed Browser aceda a sites empresariais protegidos pelo Azure AD sem que o utilizador tenha de introduzir as suas credenciais. Esta funcionalidade aplica-se a sites como o Outlook Web Access (OWA) e o SharePoint Online, bem como a outros sites empresariais como recursos de intranet acedidos através do Proxy de Aplicações do Azure.


## <a name="notices"></a>Avisos

Neste momento, não existem avisos ativos.

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.
