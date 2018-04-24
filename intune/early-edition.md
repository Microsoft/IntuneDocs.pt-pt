---
title: Edição antecipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b6ca8108924c6c062da0d0ef56ab5b68635dd9ca
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="the-early-edition-for-microsoft-intune---april-2018"></a>A edição antecipada do Microsoft Intune – abril de 2018

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

<!-- 1804 start -->

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802--"></a>Novas definições do Windows Defender Credential Guard foram adicionadas às definições de proteção de ponto final <!--1102252 --><!--from 1802-->

Serão adicionadas novas definições do [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) a **Configuração do dispositivo** > **Perfis** > **Proteção de ponto final**. Serão adicionadas as seguintes definições:

- Nível de Segurança da Plataforma: especifique se o Nível de Segurança da Plataforma está ativado no próximo reinício. A segurança baseada em virtualização necessita do Arranque Seguro. Opcionalmente, a segurança baseada em virtualização pode ser ativada com a utilização de proteções de acesso direto à memória (DMA). As proteções de DMA necessitam de suporte de hardware e serão ativadas apenas em dispositivos configurados corretamente.
- Segurança Baseada em Virtualização: especifique se a segurança baseada em virtualização está ativada no próximo reinício.
- Windows Defender Credential Guard: ative o Credential Guard com a segurança baseada em virtualização para ajudar a proteger as credenciais no próximo reinício quando o Nível de Segurança da Plataforma com o Arranque Seguro e a Segurança Baseada em Virtualização estiverem ativados. As opções disponíveis incluem **Desativada**, **Ativada com bloqueio UEFI**, **Ativada sem bloqueio** e **Não configurado**.
  - A opção "Desativada" desativa o Credential Guard remotamente se este tiver sido ativado antes através da opção "Ativada sem bloqueio".

  - A opção "Ativada com bloqueio UEFI" garante que o Credential Guard não pode ser desativado com a chave de registo ou através da utilização da Política de Grupo. Para desativar o Credential Guard após a utilização desta definição, terá de definir a Política de Grupo para "Desativada" e remover a funcionalidade de segurança de cada computador, com um utilizador fisicamente presente, para limpar a configuração persistente na UEFI. Enquanto a configuração da UEFI persistir, o Credential Guard estará ativado.

  - A opção "Ativada sem bloqueio" permite que o Credential Guard seja desativado remotamente através da utilização da Política de Grupo. Os dispositivos que utilizam esta definição têm de ter, pelo menos, o Windows 10 (Versão 1511).

  - A opção "Não Configurado" deixa a definição de política indefinida. A Política de Grupo não escreve a definição de política no registo, pelo que não tem qualquer impacto nos computadores ou utilizadores. Se existir uma definição atual no registo, não será modificada.

### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Suporte de código de acesso para o PIN de MAM no Android<!-- 1438086 -->

Os administradores do Intune poderão definir um requisito de execução da aplicação para impor um código de acesso em vez de um PIN numérico de MAM. Caso esteja configurado, será pedido ao utilizador que defina e utilize um código de acesso antes de este poder aceder a aplicações otimizadas para MAM. Os códigos de acesso são definidos como um PIN numérico com, pelo menos, um caráter especial ou letras em maiúsculas/minúsculas. O Intune suporta um código de acesso de forma semelhante ao PIN numérico existente, sendo capaz de definir um comprimento mínimo e de permitir sequências e carateres repetidos através da consola de administrador. Esta funcionalidade necessita da versão mais recente do Portal da Empresa no Android. Esta funcionalidade já se encontra disponível para iOS.

###  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Bloquear a câmara e as capturas de ecrã no Android for Work <!-- 1098977 eeready-->
Duas novas propriedades estarão disponíveis para o bloqueio ao configurar as restrições de dispositivo para dispositivos Android: 
- Câmara: bloqueia o acesso a todas as câmaras do dispositivo
- Captura de ecrã: bloqueia a captura de ecrã e também impede que os conteúdos presentes sejam apresentados em dispositivos de visualização que não tenham uma saída de vídeo segura

Aplica-se ao Android for Work.

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Suporte de aplicações de linha de negócio (LOB) para macOS <!-- 1473977 -->
O Microsoft Intune irá oferecer a capacidade de instalar aplicações LOB para macOS a partir do portal do Azure. Poderá adicionar uma aplicação LOB para macOS ao Intune depois de a mesma ter sido previamente processada pela ferramenta disponível no GitHub. No portal do Azure, selecione **Aplicações móveis** no painel **Intune**. No painel **Aplicações móveis**, selecione **Aplicações** > **Adicionar**. No painel **Adicionar Aplicação**, selecione **Aplicação de linha de negócio**. 

### <a name="support-for-user-less-devices----1637553---"></a>Suporte para dispositivos sem utilizador <!-- 1637553 -->
O Intune irá suportar a capacidade de avaliar a conformidade num dispositivo sem utilizadores, tal como o Microsoft Surface Hub. A política de conformidade pode ser aplicada a dispositivos específicos. Portanto, a conformidade e não conformidade podem ser determinadas para dispositivos que não tenham um utilizador associado.

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Adições às definições de Opções de Segurança do Dispositivo Local <!-- 1403702 -->
Poderá configurar definições adicionais de Opções de Segurança do Dispositivo Local para dispositivos com o Windows 10. As definições adicionais estarão disponíveis nas áreas do Cliente de Rede da Microsoft, Servidor de Rede da Microsoft, Segurança e acesso à rede e Início de sessão interativo. Estas definições encontram-se na categoria Endpoint Protection durante a criação de uma política de configuração de dispositivo com o Windows 10.

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Exigir a instalação de políticas, aplicações, perfis de certificado e de rede <!-- 1553555 -->
Os administradores poderão impedir os utilizadores finais de aceder ao ambiente de trabalho do Windows 10 RS4 até que o Intune instale as políticas, aplicações e perfis de certificado e de rede durante o aprovisionamento de dispositivos AutoPilot.

### <a name="rules-for-removing-devices----1609459---"></a>Regras para remover dispositivos <!-- 1609459 -->
Estarão disponíveis novas regras que lhe permitem remover automaticamente dispositivos que não se tenham registado durante o número de dias que definir. Para ver a nova regra, aceda ao painel **Intune**, selecione **Dispositivos** e selecione **Regras de remoção de dispositivo**.

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Impedir as experiências e aplicações de consumidor em dispositivos AutoPilot com o Windows 10 Enterprise RS4<!-- 1621980 -->
Poderá impedir a instalação de experiências e aplicações de consumidor nos seus dispositivos AutoPilot com o Windows 10 Enterprise RS4. Para ver esta funcionalidade, aceda a **Intune** > **Inscrição de dispositivos** > **Inscrição no Windows** > **Perfis do Windows AutoPilot** > **Criar Novo** > **Definições de inscrição**. 

### <a name="advanced-threat-protection-integrated-with-intune----1629303---"></a>Proteção Avançada Contra Ameaças integrada no Intune <!-- 1629303 -->
A [Proteção Avançada Contra Ameaças (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) mostra o nível de risco dos dispositivos com o Windows 10. Quando o Intune avalia o estado de conformidade de dispositivos com o Windows 10, a classificação de risco da ATP é incluída na avaliação. Pode utilizar a ATP com acesso condicional para ajudar a proteger a sua rede.

### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Novos passos de inscrição para os utilizadores em dispositivos com o macOS High Sierra 10.13.2 ou superior <!--1734567 -->
O macOS High Sierra 10.13.2 introduziu um conceito de inscrição "Aprovado Pelo Utilizador" na MDM. No futuro, as inscrições aprovadas irão permitir que o Intune faça a gestão de algumas definições relacionadas com a segurança. Para obter mais informações, veja a documentação de suporte da Apple aqui: https://support.apple.com/HT208019.

Os dispositivos inscritos através do Portal da Empresa do macOS serão considerados "Não Aprovados Pelo Utilizador", a menos que o utilizador final abra as Preferências do Sistema e conceda a aprovação manualmente. Para tal, o Portal da Empresa do macOS agora direciona os utilizadores no macOS 10.13.2 e superior para que acedam e aprovem manualmente a inscrição no final do processo de inscrição. A consola de administrador do Intune irá indicar se um dispositivo inscrito for aprovado pelo utilizador.

### <a name="delete-autopilot-devices----1713650---"></a>Eliminar dispositivos Autopilot <!-- 1713650 -->
Os administradores do Intune poderão eliminar dispositivos Autopilot.

### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Grupos Todos os Utilizadores e Todos os Dispositivos incorporados para a atribuição de aplicações Android for Work (AFW) <!-- 1813073 -->
Poderá tirar partido dos grupos incorporados **Todos os Utilizadores** e **Todos os Dispositivos** para a atribuição de aplicações AFW. Para obter mais informações, veja [Incluir e excluir atribuições de aplicações no Microsoft Intune](apps-inc-exl-assignments.md).

### <a name="improved-device-deletion-experience---1832333---"></a>Experiência de eliminação de dispositivos melhorada <!--1832333 -->
Já não será obrigado a remover os dados da empresa ou a fazer uma reposição de fábrica do dispositivo antes de eliminar um dispositivo do Intune.

Para ver a nova experiência, inicie sessão no Intune e selecione **Dispositivos** > **Todos os Dispositivos** > o nome do dispositivo > **Eliminar**.

 Se quiser continuar com a confirmação de eliminação/extinção, pode utilizar a rota de ciclo de vida do dispositivo padrão ao executar a opção **Remover dados da empresa** e **Reposição de Fábrica** antes de **Eliminar**. 

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Mudança dos perfis do Autopilot para a filtragem de grupo <!-- 1877935 -->
Atualmente, os perfis de implementação do AutoPilot podem ser atribuídos aos dispositivos selecionados. No fim de abril, irá passar a atribuir estes perfis ao:
- Criar grupos (Azure AD) que contenham dispositivos AutoPilot
- Atribuir os perfis pretendidos a um grupo do Azure AD. O perfil do AutoPilot será atribuído aos dispositivos AutoPilot nesse grupo.

### <a name="play-sounds-on-ios-when-in-lost-mode----1629303---"></a>Reproduzir sons no iOS quando está no Modo perdido <!-- 1629303 -->
Quando os dispositivos iOS supervisionados estiverem no [Modo perdido](device-lost-mode.md) na Gestão de Dispositivos Móveis (MDM) , poderá reproduzir um som (**Dispositivos** > **Todos os Dispositivos** > selecione um dispositivo iOS > **Descrição Geral** > **Mais**). O som continuará a ser reproduzido até que o dispositivo seja removido do Modo perdido ou que um utilizador desative o som no dispositivo. Aplica-se aos dispositivos iOS 9.3 e mais recentes.

### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Utilize um nome de requerente personalizado no certificado SCEP <!-- 2064190 -->
Poderá utilizar o nome comum **OnPremisesSamAccountName** num requerente personalizado num perfil de certificado SCEP. Por exemplo, pode utilizar `CN={OnPremisesSamAccountName})`.

### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Enviar relatórios de diagnóstico na aplicação Portal da Empresa para macOS <!-- 2216677 -->
A aplicação do Portal da Empresa para dispositivos macOS será atualizada para melhorar a forma como os utilizadores comunicam erros relacionados com o Intune. A partir da aplicação Portal da Empresa, os seus funcionários conseguirão:
- Carregar os relatórios de diagnóstico diretamente para a equipa de programadores da Microsoft.
- Enviar o ID do incidente por e-mail para a equipa de suporte de TI da sua empresa.

### <a name="always-on-vpn-for-windows-10---1333666---"></a>Funcionalidade AlwaysOn através de VPN no Windows 10 <!--1333666 -->

Atualmente, a funcionalidade [AlwaysOn](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) pode ser utilizada em dispositivos com o Windows 10 através da utilização de um perfil de rede privada virtual (VPN) personalizada criada com o OMA-URI.

Com esta atualização, os administradores poderão ativar a funcionalidade AlwaysOn para perfis VPN do Windows 10 diretamente no Intune, no portal do Azure. Os perfis VPN AlwaysOn irão ligar automaticamente quando:

- Os utilizadores iniciarem sessão nos respetivos dispositivos
- A rede no dispositivo for alterada
- O ecrã do dispositivo se ligar novamente após o ter desligado

### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Mensagens de erro melhoradas da falha de carregamento do Certificado Push de MDM da Apple <!-- 2172331 -->

A mensagem de erro explicará que tem de utilizar o mesmo ID Apple ao renovar um certificado de MDM existente.

###  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>O gráfico de perfis de dispositivos e a lista de estados mostra todos os dispositivos num grupo <!-- 1449153 eeready -->
Quando configurar um perfil de dispositivo (**Configuração do dispositivo** > **Perfis**), selecione o perfil de dispositivo que pretende, como iOS. Atribua este perfil a um grupo que inclua dispositivos iOS e dispositivos não iOS. A contagem do gráfico mostra que o perfil é aplicado a dispositivos iOS *e* não iOS (**Configuração do dispositivo** > **Perfis** > selecione um perfil existente > **Descrição Geral**). Quando seleciona o gráfico no separador **Descrição Geral**, o **Estado do dispositivo** apresenta uma lista de todos os dispositivos no grupo, em vez de mostrar apenas os dispositivos iOS. 

Com esta atualização, o gráfico (**Configuração do dispositivo** > **Perfis** > selecione um perfil existente > **Descrição Geral**) irá mostrar apenas a contagem do perfil do dispositivo específico. Por exemplo, se o perfil de configuração do dispositivo se aplicar a dispositivos iOS, o gráfico só apresentará a contagem de dispositivos iOS. Ao selecionar o gráfico e abrir o **Estado do dispositivo** só serão apresentados os dispositivos iOS.

Enquanto esta atualização estiver a ser efetuada, o gráfico de utilizadores será temporariamente removido. 


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

<!-- 1802 start -->

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Novas definições de impressora para perfis de educação <!-- 1308900 -->

Para os perfis de educação, as novas definições estarão disponíveis na categoria **Impressoras**: **Impressoras**, **Impressora predefinida**, **Adicionar novas impressoras**.

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


