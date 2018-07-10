---
title: Novidades no Microsoft Intune – Azure | Microsoft Docs
titlesuffix: ''
description: Descobrir as novidades do Intune no portal do Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/29/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: 229c97723c5774b6823699c7d0b0bc9f9b194690
ms.sourcegitcommit: d786eb18147a12fbc8cb97a157467f88591f1bc5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37134025"
---
# <a name="whats-new-in-microsoft-intune"></a>Novidades do Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Saiba mais sobre as novidades todas as semanas no Microsoft Intune. Pode também descobrir quais são as [alterações futuras](#whats-coming), os [avisos importantes](#notices) sobre o serviço e as informações sobre [versões anteriores](whats-new-archive.md). É possível que algumas funcionalidades sejam implementadas durante várias semanas e que não estejam disponíveis para todos os clientes na primeira semana.

> [!Note]
> Para obter informações sobre novas funcionalidades na gestão de dispositivos móveis (MDM) híbrida, veja a nossa página [Hybrid What’s New (Novidades nas Implementações Híbridas)](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
### App management
### Device enrollment
### Device management
### Device configuration
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->   
## <a name="week-of-june-25-2018"></a>Semana de 25 de junho de 2018

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis <!-- 1169249 -->

Pode controlar o acesso a recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Pradeo, uma solução de Defesa Contra Ameaças para Dispositivos Móveis que está integrada com o Microsoft Intune.

## <a name="week-of-june-18-2018"></a>Semana de 18 de junho de 2018

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Suporte móvel para o Microsoft Edge para políticas de proteção de aplicações do Intune <!-- 1817882 -->

O browser Microsoft Edge para dispositivos móveis agora suporta as políticas de proteção de aplicações definidas no Intune.

## <a name="week-of-june-11-2018"></a>Semana de 11 de junho de 2018

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>Utilizar o modo FIPS com o conector do Certificado NDES <!-- 1333688 -->
Ao instalar o conector do Certificado NDES num computador com o modo FIPS (Federal Information Processing Standard) ativado, a emissão e a revogação de certificados não funcionaram como esperado. Com esta atualização, é incluído suporte para FIPS com o conector do Certificado NDES. 

Esta atualização também inclui:

- O conector do Certificado NDES precisa do .NET 4.5 Framework, que é incluído automaticamente com o Windows Server 2016 e o Windows Server 2012 R2. Anteriormente, a versão mínima necessária era o .NET 3.5 Framework.
- É incluído suporte para o TLS 1.2 com o Certificate Connector do NDES. Assim, se o servidor com o Certificate Connector do NDES instalado suportar o TLS 1.2, será utilizado o TLS 1.2. Se o servidor não suportar o TLS 1.2, será utilizado o TLS 1.1. Atualmente, é utilizado o TLS 1.1 para a autenticação entre os dispositivos e o servidor.

Para obter mais informações, veja [Configurar e utilizar certificados SCEP](certificates-scep-configure.md) e [Configurar e utilizar certificados PKCS](certficates-pfx-configure.md).

## <a name="week-of-june-4-2018"></a>Semana de 4 de junho de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Obter o ID do modelo do utilizador da aplicação (AUMID) associada para aplicações da Microsoft Store para Empresas no modo de quiosque <!-- 1560077 ! -->
O Intune pode obter o IDs do modelo do utilizador da aplicação (AUMIDs) para aplicações da Microsoft Store para Empresas (WSfB) para proporcionar uma configuração melhorada do perfil de quiosque.

Para obter mais informações sobre aplicações da Microsoft Store para Empresas, veja [Gerir aplicações a partir da Microsoft Store para Empresas](windows-store-for-business.md).

#### <a name="new-company-portal-branding-page----1916370---"></a>Nova página de imagem corporativa do Portal da Empresa <!-- 1916370 -->
A página de imagem corporativa do Portal da Empresa tem um novo esquema, mensagens e descrições.


### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Suporte para perfis de VPN do GlobalProtect da Palo Alto Networks <!-- 1333680 eeready ! -->
Com esta atualização, pode escolher o GlobalProtect da Palo Alto Networks como um tipo de ligação VPN para perfis de VPN no Intune (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Tipo de perfil** > **VPN**). Neste lançamento, são suportadas as seguintes plataformas: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Adições às definições de Opções de Segurança do Dispositivo Local <!-- 1403702 -->
Agora é possível configurar definições adicionais de Opções de Segurança do Dispositivo Local para dispositivos com o Windows 10. As definições adicionais estão disponíveis nas áreas do Cliente de Rede da Microsoft, Servidor de Rede da Microsoft, Segurança e acesso à rede e Início de sessão interativo. Estas definições encontram-se na categoria Endpoint Protection durante a criação de uma política de configuração de dispositivo Windows 10.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Ativar o modo de quiosque em dispositivos com o Windows 10 <!-- 1560072 ! -->
Nos dispositivos com o Windows 10, pode criar um perfil de configuração e ativar o modo de quiosque (**Configuração do Dispositivo** > **Perfis** > **Criar perfil** > **Windows 10** > **Restrições do Dispositivo** > **Quiosque**). Nesta atualização, o nome da definição **Quiosque (pré-visualização)** irá mudar para **Quiosque (obsoleto)**. A utilização da definição **Quiosque (obsoleto)** deixará de ser recomendada, embora continue a estar funcional até à atualização de julho. A definição **Quiosque (obsoleto)** será substituída pelo novo tipo de perfil de **Quiosque** (**Criar perfil** > **Windows 10** > **Quiosque (pré-visualização)**), que incluirá as definições para configurar Quiosques no Windows 10 RS4 e posterior.

Aplica-se ao Windows 10 e posterior.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>O gráfico de utilizadores de perfis de dispositivos está de volta <!-- 2160133 -->
Durante a melhoria das contagens apresentadas no gráfico de utilizadores do perfil do dispositivo (**Configuração do dispositivo** > **Perfis** > selecione um perfil existente > **Descrição geral**), este gráfico foi removido temporariamente.

Com esta atualização, o gráfico de utilizadores está de volta e é apresentado no portal do Azure.

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118-wnready---"></a>Suporte para a inscrição do Windows Autopilot sem autenticação de utilizador <!-- 1165118 wnready -->
O Intune suporta a inscrição do Windows Autopilot sem autenticação de utilizador. Esta é uma opção nova no perfil de implementação do Windows Autopilot "Modo de implementação do Autopilot" definido para "Implementação Automática".  O dispositivo tem de estar a executar a Versão 17672 do Windows 10 Insider Preview ou posterior e ter um chip do TPM 2.0 para concluir este tipo de inscrição com êxito. Uma vez que não é necessária a autenticação de utilizador, só deve atribuir esta opção a dispositivos sobre os quais tenha o controlo físico.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766-eeready---"></a>Nova definição de idioma/região ao configurar o OOBE para o AutoPilot <!-- 1821766 eeready -->
É disponibilizada uma nova configuração para definir o idioma e a região de perfis AutoPilot durante a experiência OOBE (Out of Box Experience). Para ver a nova definição, selecione **Inscrição de dispositivos** > **Inscrição do Windows** > **Perfis de implementação** > **Criar perfil** > **Modo de implementação** = **Implementação automática** > **Predefinições configuradas**.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Nova definição para configurar o teclado do dispositivo <!-- 1821768 -->
Será disponibilizada uma nova definição para configurar o teclado de perfis AutoPilot durante a experiência OOBE (Out of Box Experience). Para ver a nova definição, selecione **Inscrição de dispositivos** > **Inscrição do Windows** > **Perfis de implementação** > **Criar perfil** > **Modo de implementação** = **Implementação automática** > **Predefinições configuradas**.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Mudança dos perfis do Autopilot para a filtragem de grupo <!-- 1877935 -->
Os perfis de implementação AutoPilot podem ser atribuídos a grupos do Azure AD com contenham dispositivos AutoPilot.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="set-compliance-by-device-location----851881----"></a>Definir a conformidade pela localização do dispositivo <!-- 851881 ! -->
Em algumas situações, pode ser útil restringir o acesso a recursos empresariais para uma localização específica, definida por uma ligação de rede. Pode criar uma política de conformidade (**Conformidade do dispositivo** > **Localizações**) baseada no endereço IP do dispositivo. Se o dispositivo estiver fora do intervalo de IP, não conseguirá aceder a recursos empresariais.

Aplica-se a: dispositivos com o Android 6.0 e superior, com a aplicação Portal da Empresa atualizada

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Impedir as experiências e aplicações de consumidor em dispositivos AutoPilot com o Windows 10 Enterprise RS4<!-- 1621980 -->
Poderá impedir a instalação de experiências e aplicações de consumidor nos seus dispositivos AutoPilot com o Windows 10 Enterprise RS4. Para ver esta funcionalidade, aceda a **Intune** > **Configuração de dispositivos** > **Perfis** > **Criar perfil** > **Plataforma** = **Windows 10 ou posterior** > **Tipo de perfil** = **Restrições de dispositivos** > **Configurar** > **Windows Spotlight** > **Funcionalidades do consumidor**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948-eeready---"></a>Desinstalar as atualizações de software mais recentes do Windows 10 <!-- 1732948 eeready -->
Se detetar um problema de interrupção em computadores com Windows 10, pode optar por desinstalar (reverter) a atualização mais recente da funcionalidade ou a atualização mais recente de qualidade. A desinstalação de uma atualização da funcionalidade ou qualidade só está disponível para o canal de serviço onde o dispositivo está ativado. A desinstalação irá acionar uma política para restaurar a atualização anterior em computadores com Windows 10. Especificamente para atualizações da funcionalidade, pode limitar o tempo de 2 a 60 dias em que pode ser aplicada uma desinstalação da versão mais recente. Para definir as opções de desinstalação da atualização do software, selecione **Atualizações do software** do painel **Microsoft Intune** no portal do Azure. Em seguida, selecione **Anéis de Atualização do Windows 10**, a partir do painel **Atualizações do software**. Em seguida, pode selecionar a opção **Desinstalar** na secção **Descrição geral**.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Procurar IMEI e número de série em todos os dispositivos <!-- 1793685 -->
Pode procurar por IMEI e números de série no painel Todos os dispositivos (e-mail, UPN, nome do dispositivo e nome de gestão ainda estão disponíveis). No Intune, selecione **Dispositivos** > **Todos os dispositivos** > introduza a sua pesquisa na caixa de pesquisa.

#### <a name="management-name-field-will-be-editable----1875989---"></a>O campo Nome de gestão passará a ser editável <!-- 1875989 -->
Pode editar o campo Nome de gestão no painel **Propriedades** de um dispositivo. Para editar este campo, selecione **Dispositivos** > **Todos os dispositivos** > selecione o dispositivo > **Propriedades**. Pode utilizar o campo Nome de gestão para identificar um dispositivo de forma exclusiva.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Novo filtro Todos os dispositivos: categoria de dispositivos <!-- 1878520 -->
Pode filtrar a lista **Todos os dispositivos** por categoria de dispositivo. Para tal, selecione **Dispositivos** > **Todos os dispositivos** > **Filtro** > **Categoria de dispositivo**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Utilizar o TeamViewer para partilhar ecrãs de dispositivos iOS e MacOS <!-- 1985547 -->
Os administradores podem estabelecer ligação ao [TeamViewer](device-profile-android-teamviewer.md) e iniciar uma sessão de partilha de ecrã com dispositivos iOS e macOS. Os utilizadores de dispositivos iPhone, iPad e macOS podem partilhar os seus ecrãs em direto com qualquer outro computador ou dispositivo. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Suporte múltiplo do Exchange Connector <!-- 2070451 -->
Deixará de ficar limitado a um Microsoft Intune Exchange Connector por inquilino. O Intune suporta agora múltiplos Exchange Connectors para que possa configurar o acesso condicional do Intune com múltiplas organizações do Exchange no local.

Com um Exchange Connector no local do Intune, pode gerir o acesso de dispositivos a caixas de correio do Exchange no local com base no facto de um dispositivo estar ou não inscrito no Intune e estar ou não em conformidade com as políticas de conformidade de dispositivos do Intune. Para configurar um conector, transfira o Exchange Connector no local do Intune a partir do portal do Azure e instale-o num servidor na sua organização do Exchange. No dashboard do Microsoft Intune, selecione **Acesso no local** e, em **Configuração**, selecione **Conector do Exchange ActiveSync**. Transfira o Exchange Connector no local e instale-o num servidor na sua organização do Exchange. Como deixou de estar limitado a um Exchange Connector por inquilino, se tiver mais organizações do Exchange, pode seguir este processo para transferir e instalar um conector para cada organização do Exchange adicional.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Detalhes de hardware do novo dispositivo: CCID <!-- 2156657 -->
As informações de Dispositivo de Interface de Cartão de Circuito Integrado (CCID) estão agora incluídas para cada dispositivo. Para vê-las, selecione **Dispositivos** > **Todos os dispositivos** > selecione um dispositivo > **Hardware**> verifique em **Detalhes da rede**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Atribuir todos os utilizadores e dispositivos como grupos de âmbito <!-- 2196803 -->
Pode agora atribuir todos os utilizadores, todos os dispositivos e todos os utilizadores e dispositivos em grupos de âmbito. Para o fazer, selecione **Funções do Intune** > **Todas as funções** > **Gestor de políticas e perfis** > **Atribuições** > selecione uma atribuição > **Âmbito (grupos)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806-wnready--"></a>Informações de UDID incluídas para dispositivos iOS e macOS <!-- 2219806 wnready-->
Para ver o Identificador Único do Dispositivo (UDID) para dispositivos iOS e macOS, aceda a **Dispositivos** > **Todos os dispositivos** > selecione um dispositivo > **Hardware**. O UDID só está disponível para dispositivos empresariais (como definido em **Dispositivos** > **Todos os dispositivos** > selecione um dispositivo > **Propriedades** > **Propriedade do dispositivo**).

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Melhorias na resolução de problemas de instalação de aplicações <!-- 928990 -->
Por vezes, a instalação de aplicações em dispositivos geridos por MDM do Microsoft Intune pode falhar. Quando uma instalação de aplicações falha, pode ser difícil compreender o motivo da falha ou resolver o problema. Vamos lançar uma Pré-visualização Pública das nossas funcionalidades de Resolução de Problemas de Aplicações. Verá um novo nó em cada dispositivo denominado **Aplicações Geridas**. Este nó apresenta as aplicações que foram enviadas através do Intune MDM. Dentro do nó, verá uma lista de estados de instalação das aplicações. Se selecionar uma única aplicação, ser-lhe-á apresentada a vista de resolução de problemas dessa aplicação específica. Na vista de resolução de problemas, verá o ciclo de vida ponto a ponto da aplicação, por exemplo quando é que a aplicação foi criada, modificada, visada e enviada para um dispositivo. Além disso, se a instalação da aplicação não tiver sido concluída com êxito, ser-lhe-á apresentado o código de erro e uma mensagem útil sobre a causa do erro. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Políticas de proteção de aplicações do Intune e Microsoft Edge <!-- 1818968 -->
Agora o browser Microsoft Edge para dispositivos móveis (iOS e Android) suporta as políticas de proteção de aplicações do Microsoft Intune. Os utilizadores de dispositivos iOS e Android que iniciarem sessão com as suas contas empresariais do Azure AD na aplicação Edge passarão a ser protegidos pelo Intune. Em dispositivos iOS, a política **Exigir browser gerido para conteúdo Web** permitirá aos utilizadores abrir ligações no Edge quando é gerido.

## <a name="week-of-may-14-2018"></a>Semana de 14 de maio de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Exigir a instalação de políticas, aplicações, perfis de certificado e de rede <!-- 1553555 -->

Os administradores podem impedir os utilizadores finais de aceder ao ambiente de trabalho do Windows 10 RS4 até que o Intune instale as políticas, aplicações e perfis de certificado e de rede durante o aprovisionamento de dispositivos AutoPilot. Para obter mais informações, veja [Configurar uma página de estado de inscrição](windows-enrollment-status.md).

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>Configurar as suas políticas de proteção de aplicações<!-- 2144597 Part 2 -->

Agora, no portal do Azure, em vez de aceder ao painel do serviço de Proteção de Aplicações do Intune, acede diretamente ao Intune. Só existe uma localização para as políticas de proteção de aplicações no Intune. Tenha em atenção que todas as suas políticas de proteção de aplicações se encontram no painel **Aplicação móvel** no Intune, em **Políticas de proteção de aplicações**. Esta integração ajuda a simplificar a sua administração da gestão da cloud. Tenha em atenção que todas as políticas de proteção de aplicações já se encontram no Intune e pode modificar as suas políticas configuradas anteriormente. A Política de Proteção de Aplicações (APP) do Intune e as políticas de Acesso Condicional (CA) estão em **Acesso condicional**, na secção **Gerir** do painel **Microsoft Intune**, ou na secção **Segurança** do painel **Azure Active Directory**. Para obter mais informações sobre a modificação de políticas de acesso condicional, veja [Acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Para obter informações adicionais, veja [O que são as políticas de proteção de aplicações?](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>Semana de 7 de maio de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Suporte do Knox Mobile Enrollment da Samsung<!--1112863-->

Ao utilizar o Intune com o Knox Mobile Enrollment (KME) da Samsung, pode inscrever um grande número de dispositivos Android da empresa. Os utilizadores em redes Wi-Fi ou redes móveis podem inscrever com apenas alguns toques os respetivos dispositivos quando os ligarem pela primeira vez. Ao utilizarem a Aplicação Knox Deployment, os dispositivos podem ser inscritos através de Bluetooth ou NFC. Para obter mais informações, consulte [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md) (Inscrever automaticamente dispositivos Android através do Knox Mobile Enrollment da Samsung).

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Pedir ajuda no Portal da Empresa para Windows 10 <!-- 1874137 -->

O Portal da Empresa para Windows 10 irá agora enviar registos de aplicações diretamente para a Microsoft quando o utilizador iniciar o fluxo de trabalho para obter ajuda com um problema. Isto facilitará a resolução dos problemas colocados à Microsoft.

## <a name="week-of-april-23-2018"></a>Semana de 23 de abril de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Suporte de código de acesso para o PIN de MAM no Android<!-- 1438086 -->

Os administradores do Intune podem definir um requisito de execução da aplicação para impor um código de acesso em vez de um PIN numérico de MAM. Caso esteja configurado, é pedido ao utilizador que defina e utilize um código de acesso antes de poder aceder a aplicações otimizadas para a MAM. Os códigos de acesso são definidos como um PIN numérico com, pelo menos, um caráter especial ou letras em maiúsculas/minúsculas. O Intune suporta um código de acesso de forma semelhante ao PIN numérico existente, sendo capaz de definir um comprimento mínimo e de permitir sequências e carateres repetidos através da consola de administrador. Esta funcionalidade necessita da versão mais recente do Portal da Empresa no Android. Esta funcionalidade já se encontra disponível para iOS.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Suporte de aplicações de linha de negócio (LOB) para macOS <!-- 1473977 -->
O Microsoft Intune irá oferecer a capacidade de instalar aplicações LOB para macOS a partir do portal do Azure. Poderá adicionar uma aplicação LOB para macOS ao Intune depois de a mesma ter sido previamente processada pela ferramenta disponível no GitHub. No portal do Azure, selecione **Aplicações móveis** no painel **Intune**. No painel **Aplicações móveis**, selecione **Aplicações** > **Adicionar**. No painel **Adicionar Aplicação**, selecione **Aplicação de linha de negócio**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Grupos Todos os Utilizadores e Todos os Dispositivos incorporados para a atribuição de aplicações Android for Work (AFW) <!-- 1813073 -->
Pode tirar partido dos grupos incorporados **Todos os Utilizadores** e **Todos os Dispositivos** para a atribuição de aplicações AFW. Para obter mais informações, veja [Incluir e excluir atribuições de aplicações no Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>O Intune irá reinstalar as aplicações necessárias que foram desinstaladas pelos utilizadores <!-- 1947010 -->
Se um utilizador final desinstalar uma aplicação necessária, o Intune reinstalará automaticamente a aplicação no prazo de 24 horas em vez de aguardar o ciclo de reavaliação de 7 dias.

### <a name="device-configuration"></a>Configuração do dispositivo

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>O gráfico de perfis de dispositivos e a lista de estados mostra todos os dispositivos num grupo <!-- 1449153 eeready -->
Quando configurar um perfil de dispositivo (**Configuração do dispositivo** > **Perfis**), selecione o perfil de dispositivo que pretende, como iOS. Atribua este perfil a um grupo que inclua dispositivos iOS e dispositivos não iOS. A contagem do gráfico mostra que o perfil é aplicado a dispositivos iOS *e* não iOS (**Configuração do dispositivo** > **Perfis** > selecione um perfil existente > **Descrição Geral**). Quando seleciona o gráfico no separador **Descrição Geral**, o **Estado do dispositivo** apresenta uma lista de todos os dispositivos no grupo, em vez de mostrar apenas os dispositivos iOS. 

Com esta atualização, o gráfico (**Configuração do dispositivo** > **Perfis** > selecione um perfil existente > **Descrição Geral**) mostra apenas a contagem do perfil do dispositivo específico. Por exemplo, se o perfil de configuração do dispositivo se aplicar a dispositivos iOS, o gráfico só apresentará a contagem de dispositivos iOS. Ao selecionar o gráfico e abrir o **Estado do dispositivo** só serão apresentados os dispositivos iOS.

Enquanto esta atualização estiver a ser efetuada, o gráfico de utilizadores será temporariamente removido. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>Funcionalidade AlwaysOn através de VPN no Windows 10 <!--1333666 -->

Atualmente, a funcionalidade [AlwaysOn](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) pode ser utilizada em dispositivos com o Windows 10 através da utilização de um perfil de rede privada virtual (VPN) personalizada criada com o OMA-URI.

Com esta atualização, os administradores podem ativar a funcionalidade AlwaysOn para perfis VPN do Windows 10 diretamente no Intune, no portal do Azure. Os perfis VPN AlwaysOn irão ligar automaticamente quando:

- Os utilizadores iniciarem sessão nos respetivos dispositivos
- A rede no dispositivo for alterada
- O ecrã do dispositivo se ligar novamente após o ter desligado

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Novas definições de impressora para perfis de educação <!-- 1308900 -->

Para os perfis de educação, as novas definições estão disponíveis na categoria **Impressoras**: **Impressoras**, **Impressora predefinida**, **Adicionar novas impressoras**.

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>Mostrar o ID do autor da chamada no perfil pessoal – Android for Work <!--1098984 -->
Quando utiliza um perfil pessoal num dispositivo, os utilizadores finais podem não ver os detalhes do ID do autor da chamada de um contacto de trabalho. 

Com esta atualização, existe uma nova definição em **Android for Work** > **Restrições do dispositivo** > **Definições do perfil de trabalho**:
- Apresentar o ID do autor da chamada do contacto de trabalho no perfil pessoal

Quando a opção está ativada (não configurada), os detalhes do autor da chamada do contacto de trabalho são apresentados no perfil pessoal. Quando a opção está bloqueada, o número do autor da chamada do contacto de trabalho não é apresentado no perfil pessoal. 

Aplica-se a: dispositivos de perfil de trabalho Android no Android OS v6.0 e mais recentes

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Novas definições do Windows Defender Credential Guard foram adicionadas às definições de proteção de ponto final <!--1102252 --><!--from 1802 and 1804-->

Com esta atualização, o [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Configuração do dispositivo** > **Perfis** > **Proteção de ponto final**) inclui as seguintes definições: 

- **Windows Defender Credential Guard**: ativa o Credential Guard com a segurança baseada em virtualização. Se ativar esta funcionalidade, ajudará a proteger as credenciais no próximo reinício quando o **Nível de Segurança da Plataforma com o Arranque Seguro** e a **Segurança Baseada em Virtualização** estiverem ativados. As opções incluem:
  - **Desativado**: se o Credential Guard tiver sido ativado anteriormente com a opção “**Ativada sem bloqueio**”, desativa o Credential Guard remotamente.

  - **Ativada com bloqueio UEFI**: garante que o Credential Guard não pode ser desativado com a chave de registo ou através da utilização da Política de Grupo. Para desativar o Credential Guard depois de utilizar esta definição, tem de definir a Política de Grupo como “Desativada”. Em seguida, remova a funcionalidade de segurança de cada computador, com um utilizador fisicamente presente. Estes passos limpam a configuração persistente na UEFI. Enquanto a configuração da UEFI persistir, o Credential Guard estará ativado.

  - **Ativada sem bloqueio**: permite que o Credential Guard seja desativado remotamente através da utilização da Política de Grupo. Os dispositivos que utilizam esta definição têm de ter, pelo menos, o Windows 10 (Versão 1511).

As seguintes tecnologias dependentes são ativadas automaticamente ao configurar o Credential Guard: 

  - **Ativar a Segurança baseada na Virtualização (VBS)**: ativa a segurança baseada na virtualização (VBS) no próximo reinício. A segurança baseada na virtualização utiliza o Windows Hypervisor para dar suporte aos serviços de segurança e requer o Arranque Seguro.
  - **Reinício Seguro com o Acesso Direto à Memória (DMA)**: ativa a VBS com o Arranque Seguro e o acesso direto à memória. As proteções de DMA precisam de suporte de hardware e serão ativadas apenas em dispositivos configurados corretamente. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Utilize um nome de requerente personalizado no certificado SCEP <!-- 2064190 -->
Poderá utilizar o nome comum **OnPremisesSamAccountName** num requerente personalizado num perfil de certificado SCEP. Por exemplo, pode utilizar `CN={OnPremisesSamAccountName})`.

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Bloquear a câmara e as capturas de ecrã no Android for Work <!-- 1098977 eeready-->
Estão disponíveis duas propriedades novas para o bloqueio ao configurar as restrições dos dispositivos Android: 
- Câmara: bloqueia o acesso a todas as câmaras do dispositivo
- Captura de ecrã: bloqueia a captura de ecrã e também impede que os conteúdos presentes sejam apresentados em dispositivos de visualização que não tenham uma saída de vídeo segura

Aplica-se ao Android for Work.


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Novos passos de inscrição para os utilizadores em dispositivos com o macOS High Sierra 10.13.2 ou superior <!--1734567 -->
O macOS High Sierra 10.13.2 introduziu um conceito de inscrição "Aprovado Pelo Utilizador" na MDM. As inscrições aprovadas permitem que o Intune faça a gestão de algumas definições relacionadas com a segurança. Para obter mais informações, veja a documentação de suporte da Apple aqui: https://support.apple.com/HT208019.

Os dispositivos inscritos através do Portal da Empresa do macOS são considerados “Não Aprovados Pelo Utilizador”, a menos que o utilizador final abra as Preferências do Sistema e conceda a aprovação manualmente. Para tal, o Portal da Empresa do macOS agora direciona os utilizadores no macOS 10.13.2 e superior para que acedam e aprovem manualmente a inscrição no final do processo de inscrição. A consola de administrador do Intune irá indicar se um dispositivo inscrito for aprovado pelo utilizador.



### <a name="device-management"></a>Gestão de dispositivos

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----eeready-1629303---"></a>A Proteção Avançada Contra Ameaças (ATP) e o Intune estão totalmente integrados <!-- EEready 1629303 -->

A [Proteção Avançada Contra Ameaças (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) mostra o nível de risco dos dispositivos com o Windows 10. No Centro de Segurança do Windows Defender (portal ATP), pode criar uma ligação para o Microsoft Intune. Depois de a criar, uma política de conformidade do Intune serve para determinar um nível de ameaça aceitável. Se o nível de ameaça for excedido, uma política de acesso condicional do Azure Active Directory (AD) poderá bloquear o acesso a aplicações diferentes dentro da sua organização.

Esta funcionalidade permite ao ATP analisar ficheiros, detetar ameaças e reportar qualquer risco nos dispositivos Windows 10.

Veja [Enable ATP with conditional access in Intune](advanced-threat-protection.md) (Ativar o ATP com acesso condicional no Intune).

#### <a name="support-for-user-less-devices----1637553---"></a>Suporte para dispositivos sem utilizador <!-- 1637553 -->
O Intune permite avaliar a conformidade num dispositivo sem utilizadores, tal como o Microsoft Surface Hub. A política de conformidade pode ser aplicada a dispositivos específicos. Portanto, a conformidade e não conformidade podem ser determinadas para dispositivos que não tenham um utilizador associado.

#### <a name="delete-autopilot-devices----1713650---"></a>Eliminar dispositivos Autopilot <!-- 1713650 -->
Os administradores do Intune podem [eliminar dispositivos Autopilot](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Experiência de eliminação de dispositivos melhorada <!--1832333 -->
Já não será obrigado a remover os dados da empresa ou a fazer uma reposição de fábrica do dispositivo antes de [eliminar um dispositivo do Intune](devices-wipe.md#delete-devices-from-the-intune-portal).

Para ver a nova experiência, inicie sessão no Intune e selecione **Dispositivos** > **Todos os Dispositivos** > o nome do dispositivo > **Eliminar**.

Se quiser continuar com a confirmação de eliminação/extinção, pode utilizar a rota de ciclo de vida do dispositivo padrão ao executar a opção **Remover dados da empresa** e **Reposição de Fábrica** antes de **Eliminar**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Reproduzir sons no iOS quando está no Modo perdido <!-- 1947769 -->
Quando os dispositivos iOS supervisionados estiverem no [Modo perdido](device-lost-mode.md) na Gestão de Dispositivos Móveis (MDM), poderá [reproduzir um som](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Dispositivos** > **Todos os Dispositivos** > selecione um dispositivo iOS > **Descrição Geral** > **Mais**). O som continuará a ser reproduzido até que o dispositivo seja removido do Modo perdido ou que um utilizador desative o som no dispositivo. Aplica-se aos dispositivos iOS 9.3 e mais recentes.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Bloquear ou permitir resultados da Web em pesquisas realizadas num dispositivo Intune <!--1972804-->

Os administradores podem agora bloquear resultados da Web em pesquisas realizadas num dispositivo.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Mensagens de erro melhoradas da falha de carregamento do Certificado Push de MDM da Apple <!-- 2172331 -->

A mensagem de erro explica que tem de utilizar o mesmo ID Apple ao renovar um certificado de MDM existente.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Testar o Portal da Empresa para macOS em máquinas virtuais <!-- 2216679 -->

Publicamos orientações para ajudar os administradores de TI a testar a aplicação Portal da Empresa para macOS em máquinas virtuais no Parallels Desktop e na VMware Fusion. Saiba mais em [Inscrever máquinas virtuais macOS para teste](macos-enroll.md#enroll-virtual-macos-machines-for-testing).


### <a name="user-interface"></a>Interface de utilizador

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Mosaicos de dispositivos melhorados no Portal da Empresa do Windows 10 <!--2213364 -->

Os mosaicos foram atualizados para serem mais acessíveis a utilizadores de visão reduzida e para terem um melhor desempenho nas ferramentas de leitura de ecrãs.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Enviar relatórios de diagnóstico na aplicação Portal da Empresa para macOS <!-- 2216677 -->
A aplicação do Portal da Empresa para dispositivos macOS foi atualizada para melhorar a forma como os utilizadores comunicam erros relacionados com o Intune. Na aplicação Portal da Empresa, os funcionários podem:

- Carregar os relatórios de diagnóstico diretamente para a equipa de programadores da Microsoft.
- Enviar o ID do incidente por e-mail para a equipa de suporte de TI da sua empresa.

Para obter mais informações, veja [Enviar erros do macOS](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>O Intune adapta-se ao Fluent Design System na aplicação Portal da Empresa para Windows 10 <!-- 1195010 WNready -->
A aplicação Portal da Empresa do Intune para Windows 10 foi atualizada com a [vista de navegação do Fluent Design System](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics). Na parte lateral da aplicação, verá uma lista vertical estática de todas as páginas de nível superior. Clique em qualquer ligação para ver e alternar entre páginas rapidamente. Esta é a primeira de várias atualizações que verá como parte do nosso esforço contínuo para criar uma experiência mais adaptável, agradável e familiar no Intune. Para ver a versão atualizada, aceda a [Novidades na IU da aplicação](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Semana de 16 de abril de 2018

#### <a name="use-cisco-anyconnect-client-for-ios----eeready-1333708---"></a>Utilizar o cliente Cisco AnyConnect para iOS <!-- EEready 1333708 -->

Quando cria um novo perfil VPN para iOS, existem agora duas opções: **Cisco AnyConnect** e **Cisco Legacy AnyConnect**. Os perfis do Cisco AnyConnect suportam a versão 4.0.7x e versões mais recentes. Os perfis VPN existentes do Cisco AnyConnect para iOS são identificados como **Cisco Legacy AnyConnect** e continuarão a funcionar com a versão 4.0.5x e mais antigas do Cisco AnyConnect, tal como atualmente.

> [!NOTE]
> Esta alteração só se aplica ao iOS. Continua a existir apenas uma opção Cisco AnyConnect para as plataformas Android, Android for Work e macOS.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Os dispositivos macOS inscritos com Jamf podem agora registar-se com o Intune <!-- 2370684 -->

As versões 1.3 e 1.4 do portal da empresa do macOS não conseguiam registar dispositivos com Jamf com o Intune. A versão 1.4.2 do portal do macOS corrige este problema.


## <a name="week-of-april-9-2018"></a>Semana de 9 de agosto de 2018

#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Experiência de ajuda atualizada na aplicação Portal da Empresa para Android <!-- 1631531 -->

Atualizámos a experiência de ajuda na aplicação Portal da Empresa para Android para estarmos alinhados com as melhores práticas para a plataforma Android. Agora, quando os utilizadores detetarem um problema na aplicação, podem tocar em **Menu** > **Ajuda** e:
- Carregar registos de diagnóstico para a Microsoft.
- Enviar um e-mail a descrever o problema e o ID do incidente para um membro da equipa de suporte da empresa.  

Para experimentar a experiência de ajuda atualizada, aceda a [Enviar registos por e-mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android) e [Enviar erros para a Microsoft](/intune-user-help/send-logs-to-microsoft-android).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Novo gráfico de tendências de falhas e tabela de motivos de falhas em novas inscrições <!-- 1471783 -->

Na página Descrição Geral de Inscrições, pode ver as tendências de falhas de inscrições e as cinco principais causas de falhas. Ao clicar no gráfico ou na tabela, pode pormenorizar os detalhes para encontrar conselhos de resolução de problemas e sugestões de remediação.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Atualização do local de configuração das políticas de proteção de aplicações <!-- 2144597 -->

No portal do Azure no serviço do Microsoft Intune, iremos redirecioná-lo temporariamente do painel do serviço **Proteção de Aplicações do Intune** para o painel **Aplicação móvel**. Tenha em atenção que todas as suas políticas de proteção de aplicações já se encontram no painel **Aplicação móvel** no Intune, em Configuração da aplicação. Em vez de aceder à Proteção de Aplicações do Intune, acederá simplesmente ao Intune. Em abril de 2018, iremos interromper o redirecionamento e remover completamente o painel do serviço **Proteção de Aplicações do Intune**, de modo a que só exista uma única localização para políticas de proteção de aplicações no Intune. 

**Como é que isto me afeta?**
Esta alteração afetará os clientes autónomos e os clientes híbridos (Intune com o Configuration Manager) do Intune. Esta integração irá ajudar a simplificar a sua administração da gestão da cloud.

**O que preciso de fazer para me preparar para esta alteração?**
Adicione o **Intune** como um favorito em vez do painel do serviço **Proteção de Aplicações do Intune** e certifique-se de que está familiarizado com o fluxo de trabalho da Política de proteção de aplicações no painel **Aplicação móvel** no Intune. Iremos redirecionar os utilizadores durante um breve período de tempo e, em seguida, remover o painel **Proteção de Aplicações**. Tenha em atenção que todas as políticas de proteção de aplicações já se encontram no Intune e pode modificar as suas políticas de acesso condicional. Para obter mais informações sobre a modificação de políticas de acesso condicional, veja [Acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Para obter informações adicionais, veja [O que são as políticas de proteção de aplicações?](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>Semana de 2 de abril de 2018

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Atualização da experiência de utilizador da aplicação Portal da Empresa para iOS <!--1412866 -->
Lançámos uma atualização importante da experiência de utilizador para a aplicação Portal da Empresa para iOS. A atualização consiste numa reestruturação visual completa que inclui um aspeto e funcionalidade mais modernos. Mantivemos a funcionalidade da aplicação, mas aumentámos a facilidade de utilização e acessibilidade da mesma.  

A atualização inclui ainda:
- Suporte para iPhone X.
- Respostas de início e carregamento de aplicações mais rápidas, que poupam tempo aos utilizadores.
- Barras de progresso adicionais que mostram as informações de estado mais recentes aos utilizadores.
- Melhorias à forma como os utilizadores carregam os registos, para facilitar o envio de relatórios em caso de falha.  

Para ver a versão atualizada, aceda a [Novidades na IU da aplicação](whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Proteger dados do Exchange no local com a Política de Proteção de Aplicações e o Acesso Condicional do Intune <!-- 1056954 -->
Agora pode utilizar a Política de Proteção de Aplicações (APP) e o Acesso Condicional (AC) do Intune para proteger o acesso a dados do Exchange no local com o Outlook Mobile. Para adicionar ou modificar uma política de proteção de aplicações no portal do Azure, selecione **Microsoft Intune** > **Aplicações móveis** > **Políticas de proteção de aplicações**. Antes de utilizar esta funcionalidade, certifique-se de que cumpre os [requisitos do Outlook para iOS e Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx).

## <a name="week-of-march-26-2018"></a>Semana de 26 de março de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Alertas de aplicações de linha de negócio (LOB) prestes a expirar para o Microsoft Intune <!-- 748789 -->

No portal do Azure, o Intune irá alertá-lo para as aplicações de linha de negócio do iOS que estão prestes a expirar. Após o carregamento de uma nova versão da aplicação de linha de negócio do iOS, o Intune remove a notificação de expiração da lista de aplicações. Esta notificação de expiração só estará ativa para as aplicações de linha de negócio do iOS carregadas recentemente. Será apresentado um aviso 30 dias antes de o perfil de aprovisionamento de aplicações LOB do iOS expirar. Quando o perfil expirar, o estado do alerta será alterado para Expirado.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Personalizar os seus temas do Portal da Empresa com códigos hexadecimais <!--1049561 -->

Pode personalizar a cor do tema nas aplicações do Portal da Empresa com códigos hexadecimais. Ao introduzir o seu código hexadecimal, o Intune determina a cor do texto que fornece o maior nível de contraste entre a cor do texto e a cor de fundo. Pode pré-visualizar a cor do texto e o logótipo da empresa relativamente à cor em **Aplicações móveis** > **Portal da Empresa**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Incluir e excluir a atribuição de aplicações com base nos grupos do Android Enterprise <!-- 1813081 -->

O Android Enterprise (anteriormente conhecido como Android for Work) suporta incluir e excluir grupos, mas não suporta os grupos incorporados **Todos os Utilizadores** e **Todos os Dispositivos** pré-criados. Para obter mais informações, veja [Incluir e excluir atribuições de aplicações no Microsoft Intune](apps-inc-exl-assignments.md).


### <a name="device-management"></a>Gestão de dispositivos

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Novas melhorias de segurança no serviço do Intune <!-- 1637539 -->   

Introduzimos um botão no Intune no Azure que os clientes do Intune autónomo podem utilizar para marcar dispositivos sem qualquer política atribuída como **Compatível** (a funcionalidade de segurança fica desativada) ou como **Não compatível** (a funcionalidade de segurança fica ativada). Isto garante que os recursos só podem ser acedidos após a avaliação da conformidade do dispositivo.

A forma como esta funcionalidade o afeta varia consoante existam ou não políticas de conformidade atribuídas.

- Se tiver uma conta nova ou existente e não tiver políticas de conformidade atribuídas aos seus dispositivos, o botão estará automaticamente definido para **Compatível**. A funcionalidade está desativada por predefinição na consola. O utilizador final não é afetado.
- Se tiver uma conta existente e tiver dispositivos com políticas de conformidade atribuídas, o botão estará automaticamente definido para **Não compatível**. A funcionalidade estará ativada por predefinição quando a atualização de março for implementada.

Se utilizar políticas de conformidade com Acesso Condicional (AC) e tiver a funcionalidade ativada, os dispositivos sem pelo menos uma política de conformidade atribuída serão bloqueados pela AC. Os utilizadores finais associados a estes dispositivos, que tinham anteriormente permissão de acesso ao e-mail, perderão o acesso a menos que atribua pelo menos uma política de conformidade a todos os dispositivos.   

Tenha em atenção que, embora o estado predefinido do botão seja logo apresentado na IU com as atualizações do serviço do Intune de março, este estado não será imposto de imediato. As alterações que fizer ao botão não afetarão a conformidade do dispositivo até que implementemos um botão funcional na sua conta. Informá-lo-emos através do Centro de Mensagens quando terminarmos a implementação na sua conta. Este processo poderá demorar alguns dias após as atualizações de março terem sido aplicadas ao seu serviço do Intune.

**Informações Adicionais**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>Deteção de jailbreak avançada <!-- 846515 -->

A deteção de jailbreak avançada é uma nova definição de conformidade que melhora a forma como o Intune avalia os dispositivos com jailbreak. A definição faz com que o dispositivo se ligue ao Intune com mais frequência, o que resulta na utilização dos serviços de localização e afeta a duração da bateria.

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Repor palavras-passe de dispositivos Android O <!-- 1238299 -->
Poderá repor as palavras-passe de dispositivos com o Android 8.0 inscritos com perfis de trabalho. Quando envia um pedido "Repor palavra-passe" para um dispositivo com o Android 8.0, este define uma nova palavra-passe de desbloqueio de dispositivo ou um desafio de perfil gerido para o utilizador atual. A palavra-passe ou desafio é enviado e entra imediatamente em vigor.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Filtrar políticas de conformidade em dispositivos nos grupos de dispositivos <!--1307012 -->

Pode direcionar as políticas de conformidade de destino para utilizadores em grupos de utilizadores. Com esta atualização, pode filtrar políticas de conformidade para os dispositivos nos grupos de dispositivos. Os dispositivos filtrados como parte de grupos de dispositivos não serão contemplados por ações de conformidade.

#### <a name="new-management-name-column----1333586---"></a>Nova coluna Nome de gestão <!-- 1333586 -->
 Está disponível uma nova coluna denominada **Nome de gestão** no painel de dispositivos. Trata-se de um nome gerado automaticamente, não editável e atribuído por dispositivo com base na seguinte fórmula:
- Nome predefinido para todos os dispositivos: <username><em><devicetype></em><enrollmenttimestamp>
- Para dispositivos adicionados em massa: <IDDoPacote/IDDoPerfil><em><DeviceType></em><EnrollmentTime>

Esta é uma coluna opcional no painel de dispositivos. Esta não está disponível por predefinição e só pode aceder-lhe através do seletor de colunas. O nome do dispositivo não é afetado por esta nova coluna.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>Os dispositivos iOS recebem um pedido de PIN a cada 15 minutos <!--1550837 -->
Após ser aplicada uma política de conformidade ou de configuração para um dispositivo iOS, os utilizadores recebem um pedido de PIN a cada 15 minutos. Os utilizadores continuam a receber pedidos até que seja definido um PIN.

#### <a name="schedule-your-automatic-updates---1805514---"></a>Agendar as suas atualizações automáticas <!--1805514 -->
O Intune dá-lhe controlo sobre quando instalar as atualizações automáticas com as [definições da Cadência de Atualizações do Windows](windows-update-for-business-configure.md). Com esta atualização, pode agendar atualizações recorrentes, incluindo a semana, o dia e a hora das mesmas.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>Utilize um nome único completo como nome do requerente num certificado SCEP <!--2221763 -->
Quando cria um perfil de certificado SCEP, tem de introduzir um Nome do Requerente. Com esta atualização, pode utilizar um nome único completo como nome do requerente. Para **Nome do Requerente**, selecione **Personalizado** e, em seguida, escreva `CN={{OnPrem_Distinguished_Name}}`. Para utilizar a variável `{{OnPrem_Distinguished_Name}}`, certifique-se de que sincroniza o atributo de utilizador `onpremisesdistingishedname` com o [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) com o seu Azure AD.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Permitir a partilha de contactos através do Bluetooth – Android for Work <!--1098983 -->
Por predefinição, o Android impede que os contactos do perfil de trabalho sincronizem com dispositivos Bluetooth. Como resultado, os contactos do perfil de trabalho não são apresentados no ID do autor da chamada em dispositivos Bluetooth.

Com esta atualização, existe uma nova definição em **Android for Work** > **Restrições do dispositivo** > **Definições do perfil de trabalho**:
- Partilha de contactos através de Bluetooth

O administrador do Intune pode configurar estas definições para permitir a partilha. É um procedimento útil para emparelhar um dispositivo com outro dispositivo Bluetooth utilizado em automóveis que apresente o ID do autor da chamada e permita uma utilização mãos-livres. Quando ativada, os contactos do perfil de trabalho são apresentados. Quando desativada, os contactos do perfil de trabalho não são apresentados.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>Configurar o Controlador de Chamadas para controlar a origem de transferência da aplicação para macOS <!-- 1690459 -->

Pode configurar o Controlador de Chamadas para proteger os seus dispositivos das aplicações ao controlar os locais donde as aplicações podem ser transferidas. Pode configurar as seguintes origens de transferência: **Mac App Store**, **Mac App Store e programadores identificados** ou **Em qualquer lado**. Pode configurar a possibilidade de os utilizadores instalarem uma aplicação ao manterem a tecla Ctrl premida e clicarem para ignorar estes controlos do Controlador de Chamadas.

Estas definições podem ser encontradas em **Configuração do dispositivo** -> **Criar perfil** -> **macOS** -> **Proteção de ponto final**.

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Configurar a firewall da aplicação para Mac <!-- 1690461 -->

Pode configurar a firewall da aplicação para Mac. Pode utilizar esta opção para controlar as ligações por aplicação em vez de por porta. Desta forma, é mais fácil beneficiar da proteção da firewall e contribuir para impedir que aplicações indesejáveis controlem portas de rede abertas para aplicações legítimas.

Esta funcionalidade encontra-se em **Configuração do dispositivo** -> **Criar perfil** -> **macOS** -> **Proteção de ponto final**.

Depois de ativar a definição da Firewall, pode configurar a firewall através de duas estratégias:

- Bloquear todas as ligações a receber

   Pode bloquear todas as ligações a receber para os dispositivos direcionados. Se optar por fazê-lo, as ligações a receber serão bloqueadas para todas as aplicações.

- Permitir ou bloquear aplicações específicas

   Pode permitir ou bloquear a receção de ligações a receber provenientes de aplicações específicas. Também pode ativar o modo furtivo para impedir respostas a pedidos de pesquisa.

####  <a name="detailed-error-codes-and-messages----1376342---"></a>Mensagens e códigos de erro detalhados <!-- 1376342 -->

Na Configuração do Dispositivo, poderá ver mensagens e códigos de erro mais detalhados. Este relatório melhorado mostra as definições, o estado destas definições e os detalhes sobre como resolver problemas.

##### <a name="more-information"></a>Mais informações

- Bloquear todas as ligações a receber

   Permite bloquear a receção de ligações a receber por parte de todos os serviços de partilha (tal como a Partilha de Ficheiros e a Partilha de Ecrãs). Os serviços do sistema que continuam a ter permissão para a receção de ligações a receber são:
  - configd – implementa o protocolo DHCP e outros serviços de configuração de rede
  - mDNSResponder – implementa Bonjour
  - racoon – implementa IPSec

    Para utilizar os serviços de partilha, certifique-se de que a opção **Ligações a receber** está definida como **Não configurada** (e não como **Bloquear**).

- Modo furtivo

   Ative esta opção para impedir que o computador responda aos pedidos de pesquisa. O computador continua a responder a pedidos recebidos de aplicações autorizadas. São ignorados pedidos inesperados, tais como o protocolo ICMP (ping).

#### <a name="disable-checks-on-device-restart---1805490---"></a>Desativar as verificações no reinício do dispositivo <!--1805490 -->
O Intune dá-lhe controlo para [gerir atualizações de software]](windows-update-for-business-configure.md). Com esta atualização, a propriedade <strong>Verificações de reinício</strong> está disponível e ativada por predefinição. Para ignorar as verificações habituais que ocorrem ao reiniciar um dispositivo (como as verificações de utilizadores ativos, níveis de bateria, entre outras), selecione <strong>Ignorar</strong>.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>Novos canais do Windows 10 Insider Preview disponíveis para cadências de implementação <!-- 1746293 -->
Agora pode selecionar os seguintes canais de serviço do Windows 10 Insider Preview ao criar uma cadência de implementação do Windows 10:
- Compilação do Windows Insider - Rápida
- Compilação do Windows Insider - Lenta
- Versão da compilação do Windows Insider 

Para obter mais informações sobre estes canais, veja [Manage Insider Preview Builds](https://insider.windows.com/en-us/for-business-organization-admin/) (Gerir Compilações do Insider Preview).   
Para obter mais informações sobre a criação de canais de implementação no Intune, veja [Gerir atualizações de software no Intune](windows-update-for-business-configure.md).

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>Registo no Portal da Empresa melhorado <!-- 1874230 eeready-->
Os utilizadores que inscreverem um dispositivo através do Portal da Empresa com a compilação 1703 e posteriores do Windows 10 poderão concluir o primeiro passo de inscrição sem sair da aplicação.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>O HoloLens e o SurfaceHub são agora apresentados em listas de dispositivos <!--1725868 -->
Incluímos suporte adicional para mostrar dispositivos HoloLens e SurfaceHub inscritos no Intune na aplicação Portal da Empresa para Android.

#### <a name="custom-book-categories-for-volume-purchase-progream-vpp-ebooks----1488911---"></a>Personalizar categorias de livros para eBooks do programa comprado em volume (VPP) <!-- 1488911 -->
Pode criar categorias de eBook personalizadas e depois atribuir eBooks do VPP a essas categorias. Os utilizadores finais podem depois ver as categorias de eBook recentemente criadas e os livros atribuídos às categorias. Para obter mais informações, veja [Gerir aplicações e livros comprados em grandes volumes com o Microsoft Intune](vpp-apps.md).  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>Alterações de suporte da opção Enviar Feedback na aplicação Portal da Empresa para Windows <!-- 2070166 -->
A partir de 30 de abril de 2018, a opção **Enviar Feedback** na aplicação Portal da Empresa para Windows funcionará apenas em dispositivos com a Atualização de Aniversário do Windows 10 (1607) e versões posteriores. A opção para enviar feedback já não é suportada ao utilizar a aplicação Portal da Empresa para Windows com a:  
- Versão 1507 do Windows 10  
- Versão 1511 do Windows 10  
- Windows Phone 8.1 

Se o seu dispositivo estiver a executar o Windows 10 RS1 ou posterior, transfira a versão mais recente da aplicação Portal da Empresa para Windows a partir da Store. Se estiver a executar uma versão não suportada, continue a enviar feedback através dos seguintes canais: 
- Aplicação Hub de Comentários no Windows 10
- E-mail (WinCPfeedback@microsoft.com)  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Novas definições do Windows Defender Application Guard <!-- 1631890 -->

- **Ativar a aceleração de gráficos**: os administradores podem ativar um processador de gráficos virtual para o Windows Defender Application Guard. Esta definição permite que o CPU descarregue a composição dos gráficos para o vGPU. Isto pode melhorar o desempenho ao trabalhar com sites de gráficos intensos ou ao ver um vídeo no contentor.

- **SaveFilestoHost**: os administradores podem permitir que os ficheiros passem do Microsoft Edge a ser executado no contentor para o sistema de ficheiros anfitrião. Ativar esta definição permite que os utilizadores transfiram ficheiros do Microsoft Edge no contentor para o sistema de ficheiros anfitrião.

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>Políticas de proteção MAM direcionadas com base no estado de gestão <!-- 1665993 -->
Pode direcionar políticas MAM com base no estado de gestão do dispositivo:
- **Dispositivos Android** – pode abranger dispositivos não geridos, dispositivos geridos pelo Intune e perfis do Android Enterprise (anteriormente Android for Work) geridos pelo Intune.
- **Dispositivos iOS** – pode abranger dispositivos não geridos (apenas MAM) ou dispositivos geridos pelo Intune.

    > [!NOTE]
    > - O suporte para esta funcionalidade em dispositivos iOS será implementado ao longo de abril de 2018.

Para obter mais informações, veja [Direcionar políticas de proteção de aplicações com base no estado de gestão do dispositivo](app-protection-policies.md).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Melhorias à linguagem na aplicação Portal da Empresa para Windows <!-- 1683758 -->
Melhorámos a linguagem no Portal da Empresa para Windows 10 de forma a torná-lo mais fácil de utilizar e adequado à sua empresa. Para ver algumas imagens de exemplo das alterações que fizemos, veja as [novidades na IU da aplicação](whats-new-app-ui.md).

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>Novas atualizações nos nossos documentos sobre a privacidade dos utilizadores <!-- 1440709 -->
Como parte do nosso compromisso em dar maior controlo aos utilizadores finais sobre os respetivos dados e privacidade, publicámos atualizações nos nossos documentos que explicam como ver e remover dados armazenados localmente pelas aplicações do Portal da Empresa. Pode encontrar estas atualizações em:

- **Android**: [How to remove your Android device from Intune (Como remover o seu dispositivo Android do Intune)](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **Android, se o utilizador tiver recusado os termos de utilização**: [Remove your device management if you declined "Terms of Use" (Remover a sua gestão de dispositivos se tiver rejeitado os "Termos de Utilização")](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS**: [Remove your iOS device from Intune (Remover o seu dispositivo iOS do Intune)](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows**: [Remove your Windows device from Intune (Remover o seu dispositivo Windows do Intune)](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## <a name="week-of-march-19-2018"></a>Semana de 19 de março de 2018

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>Exportar todos os dispositivos para ficheiros CSV no IE, Microsoft Edge ou Chrome <!-- 2258071 -->
Em **Dispositivos** > **Todos os dispositivos**, pode **Exportar** os dispositivos para uma lista com formatação CSV. Os utilizadores do Internet Explorer (IE) com mais de 10 000 dispositivos podem exportar os seus dispositivos com êxito para múltiplos ficheiros. Cada ficheiro contém um máximo de 10 000 dispositivos.

Os utilizadores do Microsoft Edge e Chrome com mais de 30 000 dispositivos podem exportar os seus dispositivos com êxito para múltiplos ficheiros. Cada ficheiro contém um máximo de 30 000 dispositivos.

O artigo [Gerir dispositivos](device-management.md) fornece mais detalhes sobre o que pode fazer com os dispositivos que gere.

## <a name="week-of-march-12-2018"></a>Semana de 12 de março de 2018

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Os sites do Azure Active Directory podem exigir a aplicação Intune Managed Browser e o suporte do Início de Sessão Único do Managed Browser (Pré-visualização Pública) <!-- 710595 -->

Com o Azure Active Directory (Azure AD), pode restringir o acesso a sites em dispositivos móveis na aplicação Intune Managed Browser. No Managed Browser, os dados dos sites permanecerão protegidos e separados dos dados pessoais dos utilizadores finais. Além disso, o Managed Browser suporta as funcionalidades de Início de Sessão Único para sites protegidos pelo Azure AD. Iniciar sessão no Managed Browser ou utilizá-lo num dispositivo com outra aplicação gerida pelo Intune permite que o Managed Browser aceda a sites empresariais protegidos pelo Azure AD sem que o utilizador tenha de introduzir as suas credenciais. Esta funcionalidade aplica-se a sites como o Outlook Web Access (OWA) e o SharePoint Online, bem como a outros sites empresariais como recursos de intranet acedidos através do Proxy de Aplicações do Azure. Para obter informações adicionais, veja [Access controls in Azure Active Directory conditional access](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls) (Controlos de acesso no acesso condicional do Azure Active Directory).

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Atualizações visuais da aplicação Portal da Empresa para Android <!--976944 -->

Atualizámos a aplicação Portal da Empresa para Android para seguir as diretrizes de [Conceção do Material](https://material.io/) do Android. Pode ver as imagens dos novos ícones no artigo [Novidades na IU da aplicação](whats-new-app-ui.md).

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>Novas definições do Windows Defender Exploit Guard <!-- 1631893 -->

Estão agora disponíveis seis novas definições de <strong>Redução da Superfície de Ataque</strong> e funcionalidades expandidas de <strong>Acesso a pastas controladas: proteção de pastas</strong>. Estas definições encontram-se em: Configuração do dispositivo\Perfis\
Criar perfil\Proteção de ponto final\Windows Defender Exploit Guard.

#### <a name="attack-surface-reduction"></a>Redução da Superfície de Ataque

|Nome da definição  |Opções da definição  |Descrição  |
|---------|---------|---------|
|Proteção de ransomware avançada|Ativado, Auditar, Não configurado|Utilize proteção contra ransomware intensiva.|
|Sinalizar o roubo de credenciais do subsistema de autoridade de segurança local do Windows|Ativado, Auditar, Não configurado|Sinalize o roubo de credenciais do subsistema de autoridade de segurança local do Windows (Lsass.exe).|
|Criação de processos com os comandos PsExec e WMI|Bloquear, Auditar, Não configurado|Bloqueie a criação de processos provenientes de comandos PsExec e WMI.|
|Processos não fidedignos e não assinados executados a partir de USB|Bloquear, Auditar, Não configurado|Bloqueie processos não fidedignos e não assinados executados a partir de USB.|
|Ficheiros executáveis que não cumprem uma lista de critérios de prevalência, idade ou fidedignidade|Bloquear, Auditar, Não configurado|Impeça ficheiros executáveis de serem executados a menos que cumpram uma lista de critérios de prevalência, idade ou fidedignidade.|

#### <a name="controlled-folder-access"></a>Acesso a pastas controladas

|              Nome da definição               |                                                              Opções da definição                                                              | Descrição |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Proteção de pastas (já implementada) | Não configurado, Ativar, Apenas auditoria (já implementada)<br><br> <strong>Novidade</strong><br>Bloquear modificação do disco, Auditar modificação do disco |             |

Proteja ficheiros e pastas contra alterações não autorizadas por aplicações não fidedignas.<br><br>**Ativar**: impede que aplicações não fidedignas modifiquem ou eliminem ficheiros em pastas protegidas e escrevam em setores do disco.<br><br>
**Bloquear apenas a modificação do disco**:<br>Impeça que aplicações não fidedignas escrevam em setores do disco. As aplicações não fidedignas continuam a poder modificar ou eliminar ficheiros em pastas protegidas.|

## <a name="week-of-february-19-2018"></a>Semana de 19 de fevereiro de 2018

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Suporte do Intune para várias contas do DEP da Apple/Apple School Manager <!-- 747685 -->

O Intune agora suporta a inscrição de dispositivos com até 100 contas diferentes do [Programa de Inscrição de Dispositivos (DEP) da Apple](device-enrollment-program-enroll-ios.md) ou do [Apple School Manager](apple-school-manager-set-up-ios.md). Cada token carregado pode ser gerido separadamente para dispositivos e perfis de inscrição. Um perfil de inscrição diferente pode ser automaticamente atribuído por token do DEP/School Manager carregado. Se forem carregados vários tokens do School Manager, só um poderá ser partilhado com a School Data Sync da Microsoft de cada vez.

Após a migração, as Graph APIs beta e os scripts publicados para gerir o DEP da Apple ou o ASM através do Graph deixarão de funcionar. Estão em desenvolvimento novas Graph APIs beta e serão lançadas após a migração.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Ver restrições de inscrição por utilizador <!-- 1634444 eeready wnready -->
No painel **Resolução de problemas**, pode agora ver as [restrições de inscrição](enrollment-restrictions-set.md) de cada utilizador ao selecionar **Restrições de inscrição** na lista **Atribuições**.

### <a name="device-management"></a>Gestão de dispositivos
#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Relatórios de estado da ameaça e estado de funcionamento do Windows Defender <!--854704 -->

Compreender o funcionamento e o estado do Windows Defender é fundamental para gerir PCs Windows.  Com esta atualização, o Intune adiciona novos relatórios e ações ao estado e estado de funcionamento do agente Windows Defender. Através de um relatório geral do estado na [carga de trabalho de Conformidade do Dispositivo](compliance-policy-monitor.md), pode ver os dispositivos que necessitam de:
- atualização de assinatura
- Reiniciar
- intervenção manual
- análise completa
- outros estados de agente a precisar de intervenção

Um relatório de agregação para cada categoria de estado indica os PCs individuais que precisam de atenção ou os que estão registados como **Limpar**.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Novas definições de privacidade para restrições do dispositivo <!--1308926 -->
Estão agora disponíveis [duas novas definições de privacidade](device-restrictions-windows-10.md#privacy) para os dispositivos:
- **Publicar as atividades do utilizador**: defina esta opção para **Bloquear** para impedir que as experiências e a deteção de recursos utilizados recentemente sejam partilhadas no comutador de tarefas.
- **Apenas atividades locais**: defina esta opção para **Bloquear** para impedir que as experiências e a deteção de recursos utilizados recentemente sejam partilhadas no comutador de tarefas com base na atividade local.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Novas definições no browser Microsoft Edge <!--1469166 -->
Estão agora disponíveis [duas novas definições](device-restrictions-windows-10.md#edge-browser) de privacidade para os dispositivos com o browser Microsoft Edge: **Caminho para o ficheiro de favoritos** e **Alterações aos Favoritos**.

### <a name="app-management"></a>Gestão de aplicações
#### <a name="protocol-exceptions-for-applications---1035509---"></a>Exceções de protocolo para aplicações <!--1035509 -->

Agora pode criar exceções para a política de transferência de dados da Gestão de Aplicações Móveis (MAM) do Intune para abrir determinadas aplicações não geridas. Estas aplicações têm de ser consideradas fidedignas pelas TI. Além das exceções que criar, a transferência de dados ainda será restrita a aplicações geridas pelo Intune quando a sua política de transferência de dados estiver definida para **apenas aplicações geridas**. Pode criar as restrições ao utilizar protocolos (iOS) ou pacotes (Android).

Por exemplo, pode adicionar o pacote WebEx como uma exceção à política de transferência de dados da MAM. Isto permite que as ligações WebEx numa mensagem de e-mail do Outlook gerido sejam abertas diretamente na aplicação WebEx. A transferência de dados será restrita noutras aplicações não geridas. Para obter mais informações, veja [Data transfer policy exceptions for apps](app-protection-policies-exception.md) (Exceções da política de transferência de dados).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Dados encriptados da Windows Information Protection (WIP) nos resultados da pesquisa do Windows<!-- 1469193 -->
Uma definição na política do Windows Information Protection (WIP) agora permite-lhe controlar se os dados encriptados pelo WIP são incluídos nos resultados da pesquisa do Windows. Pode definir esta opção de política de proteção de aplicações ao selecionar **Permitir que o Indexador do Windows Search procure itens encriptados** nas **Definições avançadas** da política do Windows Information Protection. A política de proteção de aplicações tem de ser definida para a plataforma do *Windows 10* e a política de aplicação **Estado da inscrição** tem de ser definida para **Com inscrição**. Para obter mais informações, veja [Permitir que o Indexador do Windows Search procure itens encriptados](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Configurar uma aplicação móvel MSI de atualização automática <!-- 1740840 -->
Pode configurar uma aplicação MSI móvel de atualização automática conhecida para ignorar o processo de verificação da versão. Esta funcionalidade é útil para evitar que ocorra uma condição race. Por exemplo, este tipo de condição race poderia ocorrer quando a aplicação de atualização automática por parte do programador também é atualizada pelo Intune. Ambos podem tentar impor uma versão da aplicação no cliente Windows, o que pode criar um conflito. Para estas aplicações MSI atualizadas automaticamente, pode configurar a definição **Ignorar versão da aplicação** no painel **Informações da aplicação**. Quando esta opção está definida para **Sim**, o Microsoft Intune irá ignorar a versão da aplicação instalada no cliente Windows.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Conjuntos relacionados de licenças de aplicações suportadas no Intune <!-- 1864117 -->
O Intune no portal do Azure agora suporta conjuntos relacionados de licenças de aplicações como um único item de aplicação na IU. Além disso, todas as aplicações com Licença Offline sincronizadas a partir da Microsoft Store para Empresas serão consolidadas numa única entrada de aplicação e todos os detalhes de implementação dos pacotes individuais serão migrados para uma única entrada. Para ver conjuntos relacionados de licenças de aplicações no portal do Azure, selecione **Licenças de aplicações** no painel **Aplicações móveis**.

### <a name="device-configuration"></a>Configuração do dispositivo
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Extensões de ficheiro do Windows Information Protection (WIP) para encriptação automática <!-- 1463582 -->
Uma definição na política do Windows Information Protection (WIP) agora permite-lhe especificar que extensões de ficheiros são automaticamente encriptadas ao copiar de uma partilha do Server Message Block (SMB) no vínculo empresarial, conforme definido na política do WIP.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Configurar definições de contas de recurso para Surface Hubs

Agora pode configurar definições de contas de recurso para Surface Hubs remotamente.

A conta de recurso é utilizada por um Surface Hub para efetuar a autenticação com o Skype/Exchange para que possa participar numa reunião.
Poderá querer criar uma conta de recurso exclusiva para que o Surface Hub seja apresentado na reunião como a sala de conferência.
Por exemplo, uma conta de recurso como **Sala de Conferência B41/6233**.

> [!NOTE]
> - Se deixar campos em branco, irá substituir atributos configurados anteriormente no dispositivo.
>
> - As propriedades da Conta de Recurso podem ser alteradas de forma dinâmica no Surface Hub. Por exemplo, caso a rotação da palavra-passe esteja ativada. Por isso, é possível que os valores na consola do Azure demorem algum tempo a refletir a realidade no dispositivo.
>
>   Para perceber o que está configurado atualmente no Surface Hub, as informações da Conta de Recurso podem ser incluídas no inventário de hardware (que já tem um intervalo de 7 dias) ou como propriedades só de leitura. Para melhorar a precisão após ser efetuada uma ação remota, pode obter o estado dos parâmetros imediatamente após a execução da ação para atualizar a conta/os parâmetros no Surface Hub.


##### <a name="attack-surface-reduction"></a>Redução da Superfície de Ataque


|Nome da definição  |Opções da definição  |Descrição  |
|---------|---------|---------|
|Execução de conteúdos executáveis protegidos por palavra-passe a partir do e-mail|Bloquear, Auditar, Não configurado|Impeça a execução de ficheiros executáveis protegidos por palavra-passe transferidos do e-mail.|
|Proteção de ransomware avançada|Ativado, Auditar, Não configurado|Utilize proteção contra ransomware intensiva.|
|Sinalizar o roubo de credenciais do subsistema de autoridade de segurança local do Windows|Ativado, Auditar, Não configurado|Sinalize o roubo de credenciais do subsistema de autoridade de segurança local do Windows (Lsass.exe).|
|Criação de processos com os comandos PsExec e WMI|Bloquear, Auditar, Não configurado|Bloqueie a criação de processos provenientes de comandos PsExec e WMI.|
|Processos não fidedignos e não assinados executados a partir de USB|Bloquear, Auditar, Não configurado|Bloqueie processos não fidedignos e não assinados executados a partir de USB.|
|Ficheiros executáveis que não cumprem uma lista de critérios de prevalência, idade ou fidedignidade|Bloquear, Auditar, Não configurado|Impeça ficheiros executáveis de serem executados a menos que cumpram uma lista de critérios de prevalência, idade ou fidedignidade.|

##### <a name="controlled-folder-access"></a>Acesso a pastas controladas

|              Nome da definição               |                                                              Opções da definição                                                              | Descrição |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Proteção de pastas (já implementada) | Não configurado, Ativar, Apenas auditoria (já implementada)<br><br> <strong>Novidade</strong><br>Bloquear modificação do disco, Auditar modificação do disco |             |

Proteja ficheiros e pastas contra alterações não autorizadas por aplicações não fidedignas.<br><br>**Ativar**: impede que aplicações não fidedignas modifiquem ou eliminem ficheiros em pastas protegidas e escrevam em setores do disco.<br><br>
**Bloquear apenas a modificação do disco**:<br>Impeça que aplicações não fidedignas escrevam em setores do disco. As aplicações não fidedignas continuam a poder modificar ou eliminar ficheiros em pastas protegidas.|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Adições às definições de políticas de conformidade da Segurança do Sistema do Windows 10 e posterior <!--1704133-->

Estão agora disponíveis adições às definições de conformidade do Windows 10, incluindo a obrigatoriedade da Firewall e do Antivírus do Windows Defender.


### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções
### <a name="intune-apps"></a>Aplicações do Intune
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Suporte para aplicações offline na Loja Microsoft para Empresas <!--1222672-->
As aplicações offline que comprou na Microsoft Store para Empresas são agora sincronizadas com o portal do Azure. Pode implementar estas aplicações em grupos de dispositivos ou de utilizadores. As aplicações offline são instaladas pelo Intune, não pela loja.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Impedir os utilizadores de adicionarem ou removerem contas manualmente no perfil de trabalho <!-- 1728700 -->

Ao implementar a aplicação Gmail num perfil do Android for Work, agora pode impedir os utilizadores finais de adicionarem ou removerem contas manualmente no perfil de trabalho através da definição **Adicionar e remover contas** no perfil Restrições do dispositivo Android for Work.

## <a name="week-of-february-5-2018"></a>Semana de 5 de fevereiro de 2018

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Nova opção para a autenticação do utilizador na inscrição em massa da Apple<!-- 747625 eeready -->

> [!NOTE]
> Os novos inquilinos veem esta opção de imediato. Para inquilinos existentes, esta funcionalidade será implementada durante o mês de abril. Até esta implementação estar concluída, poderá não ter acesso a estas novas funcionalidades.

O Intune agora dá-lhe a opção de autenticar dispositivos através da aplicação Portal da Empresa para os seguintes métodos de inscrição:

- Programa de Inscrição de Dispositivos da Apple
- Gestor Escolar da Apple
- Inscrição no Apple Configurator

Ao utilizar a opção do Portal da Empresa, a autenticação multifator do Azure Active Directory pode ser imposta sem bloquear estes métodos de inscrição.

Quando utilizar a opção do Portal da empresa, o Intune ignora a autenticação do utilizador no Assistente de Configuração iOS para a inscrição de afinidade do utilizador. Tal significa que o dispositivo está inscrito inicialmente como um dispositivo sem utilizador e, como tal, não receberá configurações ou políticas de grupos de utilizadores. Só recebe configurações e políticas de grupos de dispositivos. No entanto, o Intune instalará automaticamente a aplicação Portal da Empresa no Dispositivo. O primeiro utilizador a abrir e a iniciar sessão na aplicação Portal da Empresa será associado ao dispositivo no Intune. Neste momento, o utilizador receberá configurações e políticas dos grupos de utilizadores. A associação do utilizador não pode ser alterada sem a reinscrição.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Suporte do Intune para várias contas do DEP da Apple/Apple School Manager <!-- 747685 eeready -->

O Intune agora suporta a inscrição de dispositivos com até 100 contas diferentes do Programa de Inscrição de Dispositivos (DEP) da Apple ou do Apple School Manager. Cada token carregado pode ser gerido separadamente para dispositivos e perfis de inscrição. Um perfil de inscrição diferente pode ser automaticamente atribuído por token do DEP/School Manager carregado. Se forem carregados vários tokens do School Manager, só um poderá ser partilhado com a School Data Sync da Microsoft de cada vez.

Após a migração, as Graph APIs beta e os scripts publicados para gerir o DEP da Apple ou o ASM através do Graph deixarão de funcionar. Estão em desenvolvimento novas Graph APIs beta e serão lançadas após a migração.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Impressão remota através de uma rede segura <!-- 1709994  -->
As soluções de impressão móveis sem fios da PrinterOn irão permitir aos utilizadores imprimir remotamente a partir de qualquer lugar e em qualquer altura através de uma rede segura. A PrinterOn será integrada com o SDK da Aplicação Intune para iOS e Android. Conseguirá filtrar políticas de proteção de aplicações para esta aplicação através do painel **Políticas de proteção de aplicações** do Intune na consola de administração. Os utilizadores finais conseguirão transferir a aplicação “PrinterOn para Microsoft” através da Play Store ou do iTunes para utilizar no seu ecossistema do Intune.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Suporte do Portal da Empresa do macOS para inscrições que utilizam o Gestor de Inscrições de Dispositivos <!-- 1352411 -->

Os utilizadores agora podem utilizar o Gestor de Inscrições de Dispositivos ao inscrever-se no Portal da Empresa do macOS.

## <a name="week-of-january-29-2018"></a>Semana de 29 de janeiro de 2018

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Alertas para tokens expirados e tokens que irão expirar em breve <!-- 1639263 -->
A página de descrição geral agora mostra alertas sobre tokens expirados e tokens prestes a expirar. Ao clicar num alerta com um único token, acederá à página de detalhes do token.  Se clicar num alerta com vários tokens, acederá a uma lista de todos os tokens com o estado deles. Os administradores devem renovar os tokens antes da data de expiração.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>Suporte para o comando "Apagar" remoto para dispositivos macOS <!-- 1438084 -->

Os administradores podem executar um comando Apagar remotamente para dispositivos macOS.

> [!IMPORTANT]
> O comando apagar não pode ser invertido e deve ser utilizado com cuidado.

O comando apagar remove todos os dados, incluindo o sistema operativo, de um dispositivo. Esta operação também remove o dispositivo da gestão do Intune. Nenhum aviso é apresentado ao utilizador e a eliminação ocorre imediatamente após a emissão do comando.

Tem de configurar um PIN de recuperação de seis dígitos. Este PIN pode servir para desbloquear o dispositivo apagado, altura em que irá iniciar a reinstalação do sistema operativo. Depois de a eliminação começar, o PIN é apresentado numa barra de estado no painel de descrição geral do dispositivo no Intune. O PIN será mantido enquanto a eliminação estiver em curso. Depois de concluída a eliminação, o dispositivo desaparece totalmente da gestão do Intune. Não se esqueça de registar o PIN de recuperação para que quem estiver a restaurar o dispositivo o possa utilizar.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Revogar licenças para um token de Programa Comprado em Volume para iOS<!-- 820870 -->
Pode revogar a licença de todas as aplicações VPP (Volume Purchase Program) para iOS para um Token VPP específico.

### <a name="app-management"></a>Gestão de aplicações

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Revogar aplicações Programa Comprado em Volume para iOS <!-- 820863 -->
Para um dispositivo específico com uma ou mais aplicações VPP (Volume Purchase Program) para iOS, pode revogar a licença da aplicação baseada em dispositivos associada do dispositivo. Revogar a licença de uma aplicação não desinstala a aplicação VPP relacionada do dispositivo. Para desinstalar uma aplicação VPP, tem de alterar a ação de atribuição para **Desinstalar**. Para obter mais informações, veja [Como gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune](vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Atribuir aplicações móveis do Office 365 a dispositivos iOS e Android ao utilizar o tipo de aplicação incorporada <!-- 1332318 -->
O tipo de aplicação **Incorporada** torna mais fácil criar e atribuir aplicações do Office 365 nos dispositivos iOS e Android que gere. Estas aplicações incluem aplicações do O365, tais como o Word, Excel, PowerPoint e OneDrive. Pode atribuir aplicações específicas ao tipo de aplicação e editar a configuração de informações da aplicação.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Incluir e excluir a atribuição de aplicações com base nos grupos <!-- 1406920 -->

Durante a atribuição de aplicações e após selecionar um tipo de atribuição, pode selecionar os grupos a incluir e os grupos a excluir.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>Pode atribuir uma política de configuração de aplicações a grupos ao incluir e excluir atribuições  <!-- 1480316 -->

Pode atribuir uma política de configuração de aplicações a um grupo de utilizadores e dispositivos ao incluir e excluir atribuições. As atribuições podem ser seleções personalizadas de grupos ou um grupo virtual. Um grupo virtual pode incluir **Todos os utilizadores**, **Todos os Dispositivos** ou **Todos os Utilizadores e Todos os Dispositivos**.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Suporte para a política de atualização da edição do Windows 10 <!-- 903672(archived), 1119689 -->  
Pode criar uma política de atualização da edição do Windows 10 que atualize os dispositivos com o Windows 10 para o Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education e Windows 10 Professional Education N. Para obter detalhes sobre as atualizações da edição do Windows 10, veja [Como configurar atualizações da edição do Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>As políticas de Acesso Condicional do Intune só estão disponíveis no portal do Azure <!-- 1737088 1634311 -->

A partir desta versão, tem de configurar e gerir as políticas de Acesso Condicional no [portal do Azure](https://portal.azure.com) a partir de **Azure Active Directory** > **Acesso Condicional**. Para a sua comodidade, também pode aceder a este painel a partir do Intune no portal do Azure em **Intune** > **Acesso Condicional**.

#### <a name="updates-to-compliance-emails---1637547---"></a>Atualizações em e-mails de conformidade <!--1637547 -->

Quando é enviado um e-mail para comunicar um dispositivo não conforme, são incluídos detalhes sobre o mesmo.


## <a name="week-of-january-22-2018"></a>Semana de 22 de janeiro de 2018

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Nova funcionalidade para a ação "Resolver" para dispositivos Android <!--1583480-->

A aplicação Portal da Empresa para Android irá expandir a ação "Resolver" de **Atualizar definições do dispositivo** para também resolver [problemas de encriptação de dispositivos](/intune-user-help/encrypt-your-device-android).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Bloqueio remoto disponível na aplicação Portal da Empresa para Windows 10 <!--676506-->
Agora os utilizadores finais podem bloquear remotamente os seus dispositivos a partir da aplicação Portal da Empresa para Windows 10. Isto não será apresentado no dispositivo local que estejam a utilizar atualmente.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Resolução de problemas de conformidade mais fácil na aplicação do Portal da Empresa para Windows 10 <!--676546-->
Os utilizadores finais com dispositivos Windows poderão tocar no motivo de não conformidade na aplicação Portal da Empresa. Sempre que possível, esta ação irá reencaminhá-lo para a localização correta na aplicação de definições para resolver o problema.

## <a name="week-of-december-11-2017"></a>Semana de 11 de dezembro de 2017

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="new-automatic-redeployment-setting----1469168---"></a>Nova definição de reimplementação automática <!-- 1469168 -->
A definição **Reimplementação automática** permite aos utilizadores com direitos administrativos eliminar todos os dados do utilizador e as definições através de **CTRL + Win + R** no ecrã de bloqueio do dispositivo. O dispositivo é automaticamente reconfigurado e reinscrito na gestão. Esta definição encontra-se em Windows 10 > Restrições do dispositivo > Geral > Reimplementação automática. Para obter mais detalhes, veja [Definições de restrição de dispositivos Windows 10 no Intune](device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Suporte para edições de origem adicionais na política de atualização de edição do Windows 10<!-- 903672,  1119689 -->
Agora, pode utilizar a política de atualização de edição do Windows 10 para atualizar a partir de edições do Windows 10 adicionais (Windows 10 Pro, Windows 10 Pro for Education, Windows 10 Cloud e etc.). Antes desta versão, os caminhos de atualização de edição suportados eram mais limitados. Para obter detalhes, veja [Como configurar atualizações de edição do Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Novas definições do perfil de configuração do dispositivo do Centro de Segurança do Windows Defender (WDSC) <!-- 1335507 -->

O Intune adiciona uma nova secção de definições do perfil de configuração do dispositivo na Endpoint Protection com o nome **Centro de Segurança do Windows Defender**. Os administradores de TI podem configurar os pilares aos quais os utilizadores finais da aplicação do Centro de Segurança do Windows Defender podem aceder. Se um administrador de TI ocultar um pilar na aplicação do Centro de Segurança do Windows Defender, nenhuma das notificações relacionadas com o pilar oculto serão apresentadas no dispositivo do utilizador.

Estes são os pilares que os administradores podem ocultar das definições do perfil de configuração do dispositivo do Centro de Segurança do Windows Defender:
- Proteção contra vírus e ameaças
- Desempenho e funcionamento do dispositivo
- Proteções de rede e de firewall
- Controlo de aplicações e browsers
- Opções de famílias

Os administradores de TI também podem personalizar as notificações que os utilizadores recebem. Por exemplo, pode configurar se os utilizadores recebem todas as notificações geradas por pilares visíveis no WDSC ou apenas as notificações críticas. As notificações não críticas incluem resumos periódicos da atividade e das notificações do Antivírus do Windows Defender quando as análises estiverem concluídas. Todas as outras notificações são consideradas críticas. Além disso, também pode personalizar o próprio conteúdo da notificação, por exemplo, pode proporcionar as informações de contacto de TI para incorporar nas notificações que são apresentadas nos dispositivos dos utilizadores.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>Suporte para vários conectores para o processamento de certificados PFX e SCEP <!-- 1361755 -->

Os clientes que utilizam o conector do NDES no local para entregar certificados aos dispositivos podem agora configurar múltiplos conectores num único inquilino.

Esta nova capacidade suporta o seguinte cenário:

- **Elevada disponibilidade**

Cada conector do NDES obtém os pedidos de certificados do Intune.  Se um conector do NDES ficar offline, o outro conector poderá continuar a processar pedidos.

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>Nome do requerente do cliente pode utilizar a variável AAD_DEVICE_ID <!-- 1468599 -->

Quando cria um perfil de certificado SCEP no Intune, agora, pode utilizar a variável AAD_DEVICE_ID ao criar o nome do requerente personalizado.   Quando o certificado é solicitado através deste perfil SCEP, a variável é substituída pelo ID de dispositivo do AAD do dispositivo que faz o pedido de certificado.


### <a name="device-management"></a>Gestão de dispositivos

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Gerir dispositivos macOS inscritos com Jamf através do motor de conformidade de dispositivo do Intune <!-- 1592747 -->
Agora, pode utilizar o Jamf para enviar informações sobre o estado do dispositivo macOS ao Intune que, em seguida, avaliará a conformidade com as políticas definidas na consola do Intune. Com base no estado de conformidade do dispositivo, bem como outras condições (como a localização, risco do utilizador, etc.), o acesso condicional estabelecerá a conformidade dos dispositivos macOS que tentem aceder a aplicações na cloud e no local ligadas com o Azure Active Directory, incluindo o Office 365. Saiba mais sobre como [configurar a integração do Jamf](conditional-access-integrate-jamf.md) e [impor a conformidade para dispositivos geridos pelo Jamf](conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action------1424701---"></a>Nova ação do dispositivo iOS <!-- 1424701 -->

Agora, pode encerrar os dispositivos iOS 10.3 supervisionados. Esta ação encerra o dispositivo imediatamente sem avisar o utilizador final. A ação **Encerrar (apenas os supervisionados)** encontra-se nas propriedades do dispositivo ao selecionar um dispositivo na carga de trabalho **Dispositivo**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Não permitir alterações de data/hora em dispositivos Samsung Knox <!-- 1468103 -->

Adicionamos uma nova funcionalidade que lhe permite bloquear alterações de data e hora em dispositivos Samsung Knox. Pode encontrá-la em **Perfis de configuração de dispositivos** > **Restrições de dispositivos (Android)** > **Geral**.

#### <a name="surface-hub-resource-account-supported----1566442----"></a>Conta de recurso Surface Hub suportada <!-- 1566442  -->

Foi adicionada uma nova ação do dispositivo para que os administradores possam definir e atualizar a conta de recurso associada a um Surface Hub.

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

   - **Exchange Server**

     Só é preciso quando a autodiscovery falhar.

   - **Sincronização do calendário**

     Especifica se a sincronização do calendário e outros serviços do Exchange Server estão ativados. Por exemplo: reunião de sincronização.

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>Instalar aplicações do Office em dispositivos macOS <!-- 1494311 -->
A partir de agora, vai poder instalar aplicações do Office em dispositivos macOS. Este novo tipo de aplicação permitirá a instalação do Word, Excel, PowerPoint, Outlook e OneNote. Estas aplicações também vêm com o Microsoft AutoUpdate (MAU) para ajudar a manter as aplicações protegidas e atualizadas.

### <a name="app-management"></a>Gestão de aplicações

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>Eliminar um token de Programa Comprado em Volume para iOS <!-- 820879 -->
Poderá eliminar o token VPP (Volume Purchasing Program) para iOS através da consola. Tal poderá ser preciso quando tiver ocorrências duplicadas de um token de VPP.

### <a name="intune-apps"></a>Aplicações do Intune


### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>A nova coleção de entidades com o nome Utilizador Atual está limitada aos dados dos utilizadores atualmente ativos<!-- 1667026 -->

A coleção de entidades **Utilizadores** contém todos os utilizadores do Azure Active Directory (Azure AD) com licenças atribuídas na empresa. Por exemplo, um utilizador pode ser adicionado ao Intune e, em seguida, removido no decorrer do mês anterior. Apesar de este utilizador não estar presente no momento do relatório, o utilizador e o estado estão presentes nos dados. Pode criar um relatório que mostrará a duração da presença no histórico do utilizador nos seus dados.

Em contrapartida, a nova coleção de entidades **Utilizador Atual** contém apenas os utilizadores que não foram removidos. A coleção de entidades **Utilizador Atual** contém apenas os utilizadores atualmente ativos. Para obter informações sobre a coleção de entidades **Utilizador Atual**, veja [Reference for current user entity (Referência para a entidade utilizador atual)](reports-ref-current-user.md).


### <a name="updated-graph-apis----1736360---"></a>Graph APIs atualizadas <!-- 1736360 -->

Nesta versão, atualizamos algumas das Graph APIs do Intune que estão na versão beta. Veja o [registo de alterações da Graph API](https://developer.microsoft.com/graph/docs/concepts/changelog) mensal para obter mais informações.

## <a name="week-of-december-4-2017"></a>Semana de 4 de dezembro de 2017

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>O Intune suporta as aplicações negadas do Windows Information Protection (WIP) <!-- 1479103 -->
Pode especificar aplicações negadas no Intune. Se uma aplicação for negada, não poderá aceder a informações empresariais, ao contrário do que acontece com a lista de aplicações permitidas. Para obter mais informações, veja [Recommended deny list for Windows Information Protection (Lista de negações recomendadas para o Windows Information Protection)](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection).



## <a name="notices"></a>Avisos

### <a name="plan-for-change-intune-moving-to-tls-12"></a>Planear a Alteração: o Intune vai mudar para o TLS 1.2
A partir de 31 de outubro de 2018, o Intune irá suportar a versão 1.2 do protocolo TLS (Transport Layer Security) para fornecer a melhor encriptação, garantir que o nosso serviço é mais seguro por predefinição e alinhá-lo com outros serviços da Microsoft, como o Microsoft Office 365. O Office comunicou esta alteração na mensagem MC128929.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
A partir de 31 de outubro de 2018, o Intune deixará de suportar as versões 1.0 e 1.1 do protocolo TLS. Todas as combinações cliente-servidor e browser-servidor devem utilizar a versão 1.2 do TLS para garantir uma ligação sem problemas ao Intune. Tenha em atenção que esta alteração irá afetar os dispositivos dos utilizadores finais que já não são suportados pelo Intune, mas continuam a receber políticas através do Intune, e não podem utilizar a versão 1.2 do TLS. Isto inclui os dispositivos com o Android 4.3 ou anterior. Para consultar uma lista dos dispositivos e browsers afetados, veja as Informações Adicionais abaixo.

A partir de 31 de outubro de 2018, se tiver um problema relacionado com a utilização de uma versão antiga do TLS, terá de atualizar para o TLS 1.2 ou mudar para um dispositivo que suporte o TLS 1.2 como parte da resolução.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Recomendamos que remova de forma proativa as dependências do TLS 1.0 e 1.1 nos seus ambientes e que desative o TLS 1.0 e 1.1 ao nível do sistema operativo, se tal for possível. Comece já a planear a sua migração para o TLS 1.2. Veja a mensagem de blogue de suporte abaixo para consultar uma lista dos dispositivos que não são suportados atualmente pelo Intune, mas que poderão continuar a receber políticas e não poderão comunicar através da versão 1.2 do TLS. Poderá ter de notificar esses utilizadores finais de que irão perder o acesso aos recursos empresariais.

**Informações Adicionais**: [o Intune irá mudar para o TLS 1.2 para encriptação](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/)

### <a name="plan-for-change-new-windows-10-setting-for-kiosk-configuration-in-intune----1560072---"></a>Plano de Alteração: Nova Definição do Windows 10 para a Configuração do Quiosque no Intune <!-- 1560072 -->
Estamos a alterar a forma e o local onde pode configurar os ambientes de trabalho 10 1709 e posteriores (RS3 e posteriores) do Windows, no Intune no portal do Azure.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta? 
Os nossos registos indicam que está a utilizar a definição a definição Windows 10 > Restrições do dispositivo > Quiosque (Pré-visualização). A partir de maio, esta definição passará a ter o nome Windows 10 > Restrições do Dispositivo > Quiosque (obsoleto) na IU para indicar que a sua utilização deixou de ser recomendada. No entanto, a mesma continuará a funcionar até à atualização do Intune em julho. Depois disso, a definição tornar-se-á obsoleta no back-end e deixará de funcionar. Em alternativa, iremos lançar um novo Perfil de configuração de dispositivos a em maio: Windows 10 > Quiosque, que contém definições para configurar Quiosques no Windows 10 RS4 e posterior.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?  
Quando o Intune lançar a atualização do serviço de maio à volta do final do mês, divulgaremos as instruções necessárias para que possa testar e verificar se consegue migrar a sua configuração do Quiosque do Windows 10 RS3 para o Windows 10 RS4. Utilize estas instruções para configurar os seus dispositivos como Quiosques com o novo perfil de configuração de dispositivos para Quiosques.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Esta alteração afetará os clientes autónomos e os clientes híbridos (Intune com o Configuration Manager) do Intune. Esta integração irá ajudar a simplificar a sua administração da gestão da cloud. Agora terá apenas um painel para aceder no Azure – o painel do Intune – para gerir grupos, políticas, aplicações e qualquer gestão de dispositivos móveis.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Adicione o Intune como um favorito em vez do painel do serviço Proteção de Aplicações do Intune e certifique-se de que está familiarizado com o fluxo de trabalho da Política de proteção de aplicações no painel Aplicação móvel no Intune. Iremos redirecionar os utilizadores durante um breve período de tempo e, em seguida, remover o painel Proteção de Aplicações. Tenha em conta que todas as políticas da Proteção de Aplicações já se encontram no Intune e pode modificar as suas políticas de acesso condicional ao seguir esta documentação: [https://aka.ms/azuread_ca](https://aka.ms/azuread_ca).

**Informações Adicionais**: [https://aka.ms/intuneapppolicy](https://aka.ms/intuneapppolicy)

### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>Planear a Alteração: alteração no suporte do plug-in Cordova do SDK da Aplicação Microsoft Intune
O Intune irá descontinuar o suporte do [plug-in Cordova do SDK da Aplicação Microsoft Intune](app-sdk-cordova.md) no dia 1 de maio de 2018. Recomendamos que utilize a Ferramenta de Encapsulamento de Aplicações do Intune como alternativa para preparar as suas aplicações baseadas em Cordova para gestão e disponibilidade no Intune. Quando esta alteração entrar em vigor, o plug-in Cordova do SDK da Aplicação Microsoft Intune já não será gerido nem receberá atualizações. Os programadores de aplicações não poderão utilizar este plug-in. O Intune planeia continuar a suportar as aplicações criadas com Cordova. Contudo, as aplicações criadas com o plug-in Cordova do SDK da Aplicação Microsoft Intune terão as funcionalidades reduzidas no Intune. Após serem encapsuladas com a Ferramenta de Encapsulamento de Aplicações do Intune, as aplicações podem ser implementadas para os utilizadores finais como aconteceria normalmente. Para as aplicações Android baseadas em Cordova lançadas na Google Play Store:
- Serão pedidas credenciais aos utilizadores finais para receberem a política do Intune quando as aplicações forem iniciadas pela primeira vez.
- As aplicações deverão ser lançadas na loja de aplicações especificamente para os utilizadores do Intune, por exemplo "Aplicação Contoso para Intune".

Para obter mais informações sobre a Ferramenta de Encapsulamento de Aplicações, veja [Ferramenta de Encapsulamento de Aplicações para iOS](app-wrapper-prepare-ios.md) e [Ferramenta de Encapsulamento de Aplicações para Android](app-wrapper-prepare-android.md). Caso tenha perguntas ou se depare com problemas, contacte [msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com).

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Planear a Alteração: Utilizar agora o Intune no Azure para a sua gestão da MDM <!-- 1227338 -->
Há mais de um ano, anunciámos a [pré-visualização pública do Intune no Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) e, há seis meses, lançámos a [disponibilidade geral da nova experiência de administrador](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/) para o Intune. A partir de 31 de agosto de 2018, vamos desativar a gestão de dispositivos móveis (MDM) na consola Silverlight clássica para os clientes que utilizam o Intune autónomo. No seu lugar, pode utilizar o [Intune no Azure](https://aka.ms/Intune_on_Azure) para as suas necessidades de MDM. Se continua a utilizar a consola clássica para a MDM, pare e familiarize-se com o Intune no Azure. Não esperamos nenhum impacto no utilizador final com esta alteração. A gestão clássica do PC irá permanecer no Silverlight. Pode saber mais sobre esta alteração e como ela o afeta [aqui](https://aka.ms/Intune_on_Azure_mdm).

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acesso direto aos cenários de inscrição da Apple <!--951869-->
Para as contas do Intune criadas depois de janeiro de 2017, o Intune ativou o acesso direto aos cenários de inscrição da Apple através da carga de trabalho Inscrever Dispositivos no portal do Azure. Anteriormente, a pré-visualização da inscrição da Apple apenas estava acessível a partir de ligações no portal do Intune clássico. As contas do Intune criadas antes de janeiro de 2017 precisam de uma única migração antes de estas funcionalidades ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder ao portal do Azure.

## <a name="whats-coming"></a>Novidades futuras

### <a name="local-device-security-option-settings----1251887---"></a>Definições da opção de segurança do dispositivo local <!-- 1251887 -->
Poderá ativar definições de segurança em dispositivos com o Windows 10 com as novas definições da Opção de Segurança do Dispositivo Local. Estas definições encontram-se na categoria Endpoint Protection durante a criação de uma política de configuração de dispositivo Windows 10.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968--"></a>Nova atualização da experiência de utilizador do site do Portal da Empresa <!--2000968-->

Em abril, apresentamos uma nova experiência do site do Portal da Empresa, com atualizações à IU, fluxos de trabalho simplificados e melhorias de acessibilidade. Isto inclui melhorias orientadas para o cliente, como a partilha de aplicações e o desempenho global melhorado, para lhe oferecer uma experiência mais simples.
Adicionámos algumas funcionalidades novas com base no seu feedback, que irão melhorar significativamente a facilidade de utilização e as funcionalidades existentes:

-   Melhorias na IU do site
-   Capacidade de partilhar ligações diretas para as aplicações
- Desempenho melhorado para grandes catálogos de aplicações

Não precisa de tomar medidas para se preparar para esta alteração. Iremos informá-lo quando o site do Portal da empresa atualizado estiver disponível para si. No entanto, poderá ter de atualizar os documentos de utilizador final com capturas de ecrã atualizadas. Tenha em atenção que também poderá ter de atualizar a documentação da aplicação Portal da Empresa no iOS, uma vez que o site ativa a secção **Aplicações** da aplicação para iOS. Pode ver uma imagem de exemplo na página [Novidades na IU da aplicação](whats-new-app-ui.md).

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>A Apple passará a exigir atualizações para a Segurança de Transporte de Aplicações <!--748318-->
A Apple anunciou que irá impor requisitos específicos para a Segurança de Transporte de Aplicações (ATS). A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Esta alteração irá afetar os clientes do Intune que utilizam as aplicações do Portal da Empresa para iOS. Continuaremos a fornecer mais detalhes no nosso [blogue de suporte do Intune](https://aka.ms/compportalats).



## <a name="see-also"></a>Consulte também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](https://www.microsoft.com/cloud-platform/roadmap)
* [Novidades na IU do Portal da Empresa](whats-new-app-ui.md)
* [Novidades nos meses anteriores](whats-new-archive.md)
