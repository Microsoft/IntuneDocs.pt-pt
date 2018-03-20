---
title: "Edição antecipada"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9a2c104200518af31fd05e6b8abe853377767aa9
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/09/2018
---
# <a name="the-early-edition-for-microsoft-intune---march-2018"></a>A edição antecipada do Microsoft Intune – março de 2018

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

### <a name="enhanced-jailbreak-detection----846515---"></a>Deteção de jailbreak avançada <!-- 846515 -->

A deteção de jailbreak avançada é uma nova definição de conformidade que melhorará a forma como o Intune avalia os dispositivos com jailbreak. A definição permitirá que o dispositivo entre no Intune com mais frequência. A ativação desta definição resultará na utilização dos serviços de localização do dispositivo e afetará a autonomia da bateria.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacidade de implementar as aplicações de linha de negócio (LOB) necessárias em Todos os Utilizadores com computadores com o Windows 10 <!-- 1627835 RS4 -->
Os clientes poderão implementar as aplicações do Windows 10 de linha de negócio necessárias para as instalar em dispositivos. Isto permitirá que estas aplicações fiquem disponíveis para todos os utilizadores no dispositivo. Isto só é aplicável a computadores com o Windows 10. 

### <a name="expiring-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Aplicações de linha de negócio (LOB) prestes a expirar para o Microsoft Intune <!-- 748789 -->
No portal do Azure, o Intune irá alertá-lo para as aplicações de linha de negócio que estão prestes a expirar. Após o carregamento de uma nova versão da aplicação de linha de negócio, o Intune removerá a notificação de expiração da lista de aplicações.

### <a name="company-portal-enrollment-improved----1874230--"></a>Registo no Portal da Empresa melhorado <!-- 1874230-->
Os utilizadores que inscrevam um dispositivo ao utilizar o Portal da Empresa com a compilação 1703 e posteriores do Windows 10 poderão concluir o primeiro passo de inscrição sem sair da aplicação.

### <a name="new-management-name-column----1333586---"></a>Nova coluna Nome de gestão <!-- 1333586 -->
Será adicionada uma nova coluna com o nome **Nome de gestão** ao painel de dispositivos. Trata-se de um nome gerado automaticamente, não editável e atribuído por dispositivo com base na seguinte fórmula: 
- Nome predefinido para todos os dispositivos: <username>_<devicetype>_<enrollmenttimestamp>
- Para dispositivos adicionados em massa: <IDDoPacote/IDDoPerfil>_<DeviceType>_<EnrollmentTime> 
 
Esta é uma coluna opcional no painel de dispositivos. Não estará disponível por predefinição e é acessível através do seletor de colunas. O nome do dispositivo não é afetado por esta nova coluna.

### <a name="new-settings-for-windows-defender-security-center-notifications-device-configuration-profile----1631906---"></a>Novas definições do perfil de configuração do dispositivo de notificações do Centro de Segurança do Windows Defender <!-- 1631906 -->

Serão adicionadas três novas definições ao perfil de configuração do dispositivo de notificações do Centro de Segurança do Windows Defender (WDSC).

Os administradores poderão:

- Ocultar o pilar Identidade
- Ocultar o pilar Hardware e as respetivas subdefinições
- Ocultar o pilar Ransomware (restauro de ficheiros do OneDrive para Empresas)

Quando oculta estes pilares da aplicação WDSC, os utilizadores finais não poderão configurar estas definições e todas as notificações associadas aos componentes ocultos não serão geradas.

### <a name="mam-policies-targeted-based-on-management-state----1665993---"></a>Políticas MAM visadas com base no estado de gestão <!-- 1665993 -->

Poderá visar políticas MAM com base no estado de gestão do dispositivo:

- **Dispositivos iOS** – poderá visar dispositivos não geridos (apenas MAM) ou dispositivos geridos pelo Intune.
- **Dispositivos Android** – poderá visar dispositivos não geridos, dispositivos geridos pelo Intune e perfis do Android Enterprise (anteriormente Android for Work) geridos pelo Intune.

### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459--"></a>Configurar o Controlador de Chamadas para controlar a origem de transferência da aplicação para macOS <!-- 1690459-->

Poderá configurar o Controlador de Chamadas para proteger os seus dispositivos das aplicações ao controlar os locais donde as aplicações podem ser transferidas. Poderá configurar as seguintes origens de transferência: **Mac App Store**, **Mac App Store e programadores identificados** ou **Em qualquer lugar**. Também poderá configurar a possibilidade de os utilizadores instalarem uma aplicação ao clicar com a tecla Ctrl premida para ignorar estes controlos do Controlador de Chamadas.

Estas definições podem ser encontradas em **Configuração do dispositivo** -> **Criar perfil** -> **macOS** -> **Proteção de ponto final**.

### <a name="configure-the-mac-application-firewall----1690461---"></a>Configurar a firewall da aplicação para Mac <!-- 1690461 -->

Poderá configurar a firewall da aplicação para Mac. Pode utilizar esta opção para controlar as ligações por aplicação em vez de por porta. Desta forma, é mais fácil beneficiar da proteção da firewall e contribuir para impedir que aplicações indesejáveis controlem portas de rede abertas para aplicações legítimas.
 
Esta funcionalidade encontra-se em **Configuração do dispositivo** -> **Criar perfil** -> **macOS** -> **Proteção de ponto final**.

Depois de ativar a definição da Firewall, pode configurar a firewall através de duas estratégias:

- Bloquear todas as ligações a receber

   Pode bloquear todas as ligações a receber para os dispositivos direcionados. Se optar por fazê-lo, as ligações a receber serão bloqueadas para todas as aplicações. 

- Permitir ou bloquear aplicações específicas

   Pode permitir ou bloquear a receção de ligações a receber provenientes de aplicações específicas. Também pode ativar o modo furtivo para impedir respostas a pedidos de pesquisa.
 
#### <a name="more-information"></a>Mais informações

- Bloquear todas as ligações a receber

   Permite bloquear a receção de ligações a receber por parte de todos os serviços de partilha (tal como a Partilha de Ficheiros e a Partilha de Ecrãs). Os serviços do sistema que continuam a ter permissão para a receção de ligações a receber são:
   - configd – implementa o protocolo DHCP e outros serviços de configuração de rede
   - mDNSResponder – implementa Bonjour
   - racoon – implementa IPSec

   Para utilizar os serviços de partilha, certifique-se de que a opção **Ligações a receber** está definida como **Não configurada** (e não como **Bloquear**).

- Modo furtivo

   Ative esta opção para impedir que o computador responda aos pedidos de pesquisa. O computador continua a responder a pedidos recebidos de aplicações autorizadas. São ignorados pedidos inesperados, tais como o protocolo ICMP (ping).
 

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Atualizar a experiência de Ajuda e Feedback na aplicação Portal da Empresa para Android <!--1631531 -->

Iremos atualizar a experiência de Ajuda e Feedback na aplicação Portal da Empresa para Android para estarmos alinhados com as melhores práticas para aplicações Android. Iremos atualizar a aplicação Portal da Empresa para Android nos próximos meses para dividir o item de menu **Ajuda e Feedback** em itens de menu **Ajuda** e **Enviar Feedback** separados. A página **Ajuda** terá uma secção de **Perguntas Frequentes** e o botão **Suporte por E-mail** para que os utilizadores finais carreguem registos para a Microsoft e enviem e-mails para a empresa de suporte com a descrição do problema. O menu **Enviar Feedback** orientará o utilizador ao longo do processo padrão de submissão de feedback da Microsoft, que lhe pedirá para escolher entre "Gosto de algumas coisas", "Não de gosto de algumas coisas" ou "Tenho uma ideia".

### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>Personalizar categorias de livros para eBooks do programa comprado em volume (VPP) <!-- 1488911 -->
Poderá criar categorias de eBook personalizadas e depois atribuir eBooks do VPP a essas categorias. Os utilizadores finais podem depois ver as categorias de eBook recentemente criadas e os livros atribuídos às categorias.

#### <a name="company-portal-for-android-visual-updates---976944---"></a>Atualizações visuais do Portal da Empresa para Android <!--976944 -->

Iremos atualizar a aplicação Portal da Empresa para Android para seguir as diretrizes de [Conceção do Material](https://material.io/) do Android. Iremos publicar imagens dos ícones novos no artigo [Novidades na IU da aplicação](whats-new-app-ui.md) aquando do lançamento da aplicação. 


<!-- 1802 start -->

### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Novo gráfico de tendências de falhas e tabela de motivos de falhas em novas inscrições <!-- 1471783 -->

Na página Descrição Geral de Inscrições, poderá ver as tendências de falhas de inscrições e as cinco principais causas de falhas. Ao clicar no gráfico ou na tabela, poderá pormenorizar os detalhes para encontrar conselhos de resolução de problemas e sugestões de remediação.

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Personalizar os seus temas do Portal da Empresa com códigos hexadecimais <!--1049561 -->

Poderá personalizar a cor do tema nas aplicações do Portal da Empresa com códigos hexadecimais. Ao introduzir o seu código hexadecimal, o Intune irá determinar a cor do texto que fornece o maior nível de contraste entre a cor do texto e a cor de fundo segundo os [padrões do WCAG 2.0](http://www.w3.org/TR/WCAG20). Pode pré-visualizar a cor do texto e o logótipo da empresa relativamente à cor em **Aplicações móveis** > **Portal da Empresa**. 

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>Novas definições do Windows Defender Credential Guard foram adicionadas às definições de proteção de ponto final <!--1102252 --> 

As novas definições do [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) serão adicionadas a **Configuração de dispositivos** > **Perfis** > **Proteção de ponto final**. Serão adicionadas as seguintes definições: 

- Nível de Segurança da Plataforma: especifique se o Nível de Segurança da Plataforma está ativado no próximo reinício. A segurança baseada em virtualização necessita do Arranque Seguro. Opcionalmente, a segurança baseada em virtualização pode ser ativada com a utilização de proteções de acesso direto à memória (DMA). As proteções de DMA necessitam de suporte de hardware e serão ativadas apenas em dispositivos configurados corretamente.
- Segurança Baseada em Virtualização: especifique se a segurança baseada em virtualização está ativada no próximo reinício. 
- Windows Defender Credential Guard: ative o Credential Guard com a segurança baseada em virtualização para ajudar a proteger as credenciais no próximo reinício quando o Nível de Segurança da Plataforma com o Arranque Seguro e a Segurança Baseada em Virtualização estiverem ativados. As opções disponíveis incluem **Desativada**, **Ativada com bloqueio UEFI**, **Ativada sem bloqueio** e **Não configurado**. 
  - A opção "Desativada" desativa o Credential Guard remotamente se este tiver sido ativado antes através da opção "Ativada sem bloqueio".

  - A opção "Ativada com bloqueio UEFI" garante que o Credential Guard não pode ser desativado com a chave de registo ou através da utilização da Política de Grupo. Para desativar o Credential Guard após a utilização desta definição, terá de definir a Política de Grupo para "Desativada" e remover a funcionalidade de segurança de cada computador, com um utilizador fisicamente presente, para limpar a configuração persistente na UEFI. Enquanto a configuração da UEFI persistir, o Credential Guard estará ativado.

  - A opção "Ativada sem bloqueio" permite que o Credential Guard seja desativado remotamente através da utilização da Política de Grupo. Os dispositivos que utilizam esta definição têm de ter, pelo menos, o Windows 10 (Versão 1511).

  - A opção "Não Configurado" deixa a definição de política indefinida. A Política de Grupo não escreve a definição de política no registo, pelo que não tem qualquer impacto nos computadores ou utilizadores. Se existir uma definição atual no registo, não será modificada.

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Repor palavras-passe de dispositivos Android O <!-- 1238299 -->
Poderá repor as palavras-passe de dispositivos Android O inscritos. Quando envia um pedido "Repor palavra-passe" para um dispositivo Android O, este define uma nova palavra-passe de desbloqueio de dispositivo ou um desafio de perfil gerido para o utilizador atual. A palavra-passe ou o desafio é enviado consoante o dispositivo tiver um proprietário de perfil ou proprietário de dispositivo e entra em vigor imediatamente.

### <a name="local-device-security-option-settings----1251887---"></a>Definições da opção de segurança do dispositivo local <!-- 1251887 -->
Poderá ativar definições de segurança em dispositivos Windows 10 com as novas definições da Opção de Segurança do Dispositivo Local. Estas definições encontram-se na categoria Endpoint Protection durante a criação de uma política de configuração de dispositivo Windows 10.

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Novas definições de impressora para perfis de educação <!-- 1308900 -->

Para os perfis de educação, as novas definições estarão disponíveis na categoria **Impressoras**: **Impressoras**, **Impressora predefinida**, **Adicionar novas impressoras**. 

### <a name="ios-app-provisioning-configuration----1581650---"></a>Configuração do aprovisionamento de aplicações iOS <!-- 1581650 -->
Poderá atribuir perfis de aprovisionamento de aplicações iOS para impedir que as suas aplicações expirem ao incluir ou excluir grupos de segurança.

### <a name="new-windows-defender-exploit-guard-settings----631893---"></a>Novas definições do Windows Defender Exploit Guard <!-- 631893 -->

Estarão disponíveis seis novas definições de **Redução da Superfície de Ataque** e funcionalidades expandidas de **Acesso a pastas controladas: proteção de pastas**. Estas definições encontram-se em: Configuração do dispositivo\Perfis\
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

|Nome da definição  |Opções da definição  |Descrição  |
|---------|---------|---------|
|Proteção de pastas (já implementada)|Não configurado, Ativar, Apenas auditoria (já implementada)<br><br> **Novidade**<br>Bloquear modificação do disco, Auditar modificação do disco|
Proteja ficheiros e pastas contra alterações não autorizadas por aplicações não fidedignas.<br><br>**Ativar**: impede que aplicações não fidedignas modifiquem ou eliminem ficheiros em pastas protegidas e escrevam em setores do disco.<br><br>
**Bloquear apenas a modificação do disco**:<br>Impeça que aplicações não fidedignas escrevam em setores do disco. As aplicações não fidedignas continuam a poder modificar ou eliminar ficheiros em pastas protegidas.|

### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Novas definições do Windows Defender Application Guard <!-- 1631890 -->

- **Ativar a aceleração de gráficos**

Os administradores poderão ativar um processador de gráficos virtual para o Windows Defender Application Guard. Esta definição permite que o CPU descarregue a composição dos gráficos para o vGPU. Isto pode melhorar o desempenho ao trabalhar com sites de gráficos intensos ou ao ver um vídeo no contentor.

- **SaveFilestoHost**

Os administradores poderão permitir que os ficheiros passem do Microsoft Edge a ser executado no contentor para o sistema de ficheiros anfitrião. Ativar esta definição irá permitir que os utilizadores transfiram ficheiros do Microsoft Edge no contentor para o sistema de ficheiros anfitrião.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Incluir e excluir a atribuição de aplicações com base nos grupos do Android Enterprise <!-- 1813081 -->
Durante a atribuição de aplicações e após selecionar um tipo de atribuição, o Android Enterprise (anteriormente conhecido como Android for Work) irá suportar a funcionalidade de exclusão.

<!-- the following are present prior to 1802 -->

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Filtrar políticas de conformidade em dispositivos nos grupos de dispositivos <!--1307012 -->

Será capaz de filtrar políticas de conformidade de destino para os utilizadores nos grupos de utilizadores. Será capaz de filtrar políticas de conformidade para os dispositivos nos grupos de dispositivos.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Políticas de Proteção de Aplicações <!-- 679615 -->
As Políticas de Proteção de Aplicações do Intune permitirão criar políticas predefinidas globais para ativar rapidamente a proteção em todos os utilizadores em todo o inquilino.

### <a name="configure-an-ios-app-pin----1586774---"></a>Configurar um PIN da aplicação para iOS <!-- 1586774 -->
Em breve poderá exigir um PIN para aplicações específicas para iOS. Pode configurar a data de expiração em dias e a obrigatoriedade de introdução de PIN através do portal do Azure. Quando for necessário, um utilizador terá de definir e utilizar um PIN novo para ter acesso a uma aplicação iOS. Apenas as aplicações iOS que têm ativada a proteção de aplicações com o SDK da Aplicação Intune suportarão esta funcionalidade.

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Os sites do Azure Active Directory podem exigir a aplicação Intune Managed Browser e o suporte do Início de Sessão Único do Managed Browser (Pré-visualização Pública) <!-- 710595 -->   
Com o Azure Active Directory (Azure AD), poderá restringir o acesso a sites em dispositivos móveis na aplicação Intune Managed Browser. No Managed Browser, os dados dos sites permanecerão protegidos e separados dos dados pessoais dos utilizadores finais. Além disso, o Managed Browser suporta as funcionalidades de Início de Sessão Único para sites protegidos pelo Azure AD. Iniciar sessão no Managed Browser ou utilizá-lo num dispositivo com outra aplicação gerida pelo Intune permite que o Managed Browser aceda a sites empresariais protegidos pelo Azure AD sem que o utilizador tenha de introduzir as suas credenciais. Esta funcionalidade aplica-se a sites como o Outlook Web Access (OWA) e o SharePoint Online, bem como a outros sites empresariais como recursos de intranet acedidos através do Proxy de Aplicações do Azure.

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-the-new-company-portal-app---1380728--"></a>Redirecionar utilizadores do macOS para a nova aplicação Portal da Empresa <!--1380728-->   
Quando um utilizador final inicia sessão no site do Portal da Empresa para inscrever o seu dispositivo macOS, este será direcionado para transferir a nova aplicação Portal da Empresa para macOS para concluir o processo. Isto ocorre nos dispositivos macOS que utilizam o OS X El Capitan 10.11 ou posterior. 

<!-- the following are present prior to 1709 -->

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensagem de erro melhorada para quando um utilizador atinge o número máximo de dispositivos que é permitido inscrever <!-- 1270370 -->
Em vez de uma mensagem de erro genérica, os utilizadores finais com dispositivos Android verão uma mensagem de erro amigável acionável: “Inscreveu o número máximo de dispositivos permitidos pelo administrador de TI. Remova um dispositivo inscrito ou peça ajuda ao seu administrador de TI."



## <a name="notices"></a>Avisos

Neste momento, não existem avisos ativos.



### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.


