---
title: Edição antecipada – Microsoft Intune
titlesuffix: ''
description: Edição antecipada do Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 92644eeed28911d0d49ec2aa20fcfed4a6553486
ms.sourcegitcommit: fddf90a6aa17b09005723653a0c9a520856bb2ea
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/06/2019
ms.locfileid: "55781509"
---
# <a name="the-early-edition-for-microsoft-intune---february-2019"></a>A edição antecipada do Microsoft Intune – Fevereiro de 2019

> [!Note]
> Notificação de contrato de confidencialidade: As seguintes alterações estão em desenvolvimento para o Intune. Estas informações são partilhadas ao abrigo de um contrato de confidencialidade numa base muito limitada. Não publique estas informações em redes sociais ou em sites públicos como o Twitter, UserVoice, Reddit, entre outros. 

A **edição antecipada** oferece uma lista de funcionalidades, partilhadas ao abrigo de um contrato de confidencialidade, que estarão disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida numa base limitada e está sujeita a alterações. Não publique no Twitter nem no UserVoice, nem partilhe estas informações de nenhuma outra forma com pessoas fora da sua empresa. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu contacto do grupo de produtos da Microsoft se tiver dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure
<!-- 1902 start-->

### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675----"></a>Scripts do PowerShell podem ser executado num host de 64 bits em dispositivos de 64 bits <!-- 1862675  -->
Quando adiciona um script do PowerShell para um perfil de configuração do dispositivo, o script é executado sempre de 32 bits, mesmo em sistemas de operativos de 64 bits. Com esta atualização, um administrador pode executar o script num host do PowerShell de 64 bits em dispositivos de 64 bits (**configuração do dispositivo** > **scripts do PowerShell**  >   **Adicione** > **configurar** > **executar script num anfitrião do PowerShell de 64 bits**).
Para obter mais detalhes sobre como utilizar o PowerShell, consulte [scripts do PowerShell no Intune](intune-management-extension.md).
Aplica-se a: Windows 10 e posterior

### <a name="rename-an-enrolled-windows-device----1911112----"></a>Mudar o nome de um dispositivo Windows inscrito <!-- 1911112  -->
Poderá mudar o nome de um dispositivo Windows 10 inscrito (RS4 ou posterior). Para fazer, escolha **Intune** > **dispositivos** > **todos os dispositivos** > Escolha um dispositivo > **mudança de nome de dispositivo**.

### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521-----"></a>Atribuir certificados SCEP para um dispositivo macOS sem utilizador    <!-- 2340521   -->
Será capaz de atribuir certificados Simple Certificate Enrollment Protocol (SCEP) para um dispositivo macOS sem utilizador e associar o certificado, Wi-Fi ou perfis VPN. Isso expande o suporte existente já temos a [atribuir certificados para dispositivos sem utilizador com o Windows, iOS e Android](certificates-scep-configure.md#create-a-scep-certificate-profile).

### <a name="intune-conditional-access-ui-update------2432313----"></a>Atualização de interface do Usuário de acesso condicional do Intune   <!-- 2432313  -->
Estamos a fazer melhorias na interface do usuário para o acesso condicional na consola do Intune. Estas incluem:
- Substitua o Intune *acesso condicional* painel com o painel do Azure Active Directory. Isto garante que terá acesso a uma gama completa de definições e configurações para o acesso condicional que permanece uma tecnologia do Azure AD.
- Reposicionar a *conector de serviço do Exchange* programa de configuração para o que está atualmente a *acesso no local* painel. Podemos também são renomear esse painel para *acesso ao Exchange*. Esta alteração irá consolidar pode configurar e monitorizar os detalhes relacionados com o Exchange online e no local.

### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355----"></a>Intune será tiram partido das APIs de proteger reproduzir da Google em dispositivos Android <!-- 2577355  -->
Alguns administradores de TI enfrentam um cenário BYOD onde os utilizadores finais podem acabar embota ou jailbreaking o celular. Este comportamento, embora às vezes, não mal-bem-intencionado, resulta numa omissão de muitas das políticas do Intune que estão definidas para proteger os dados da organização nos dispositivos do utilizador final. Assim, o Intune fornece deteção de raiz e jailbreak para dispositivos inscritos e não inscritos. Com esta versão, o Intune irá agora tirar Google Play proteger APIs para adicionar à nossa verificações existentes para a deteção de raiz para dispositivos não inscritos. Embora a Google não partilha a totalidade das verificações de deteção de raiz que ocorrem, esperamos que essas APIs para detetar os utilizadores que têm Root seus dispositivos por qualquer motivo de personalização do dispositivo para a capacidade de obter as atualizações de SO mais recente nos dispositivos mais antigos. Estes utilizadores, em seguida, podem ser impedidos de aceder a dados empresariais ou suas contas empresariais poderão ser eliminadas a partir das suas aplicações de política ativada. Para o valor adicional, o administrador de TI agora têm várias atualizações de geração de relatórios no painel de proteção de aplicações do Intune – o relatório de "Utilizadores sinalizados" irá mostrar os utilizadores que são detetados através do análise de SafetyNet API da Google Play Protect, o "potencialmente prejudicial aplicações" relatório irá mostre as aplicações são detetadas através verificar aplicações API da Google de verificação. Esta funcionalidade está disponível no Android. 

### <a name="win32-app-information-available-in-troubleshooting-blade----2617342------"></a>Informações da aplicação Win32 disponíveis no painel de resolução de problemas <!-- 2617342    -->
Poderá recolher ficheiros de registo de falha para uma instalação de aplicações de Win32 a partir da aplicação Intune **resolução de problemas** painel. Para obter mais informações sobre resolução de problemas de instalação de aplicação, consulte [resolver problemas de instalação de aplicações](troubleshoot-app-install.md).

### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135----"></a>Aplicações de Browser de local público e o Browser do Microsoft Edge podem ser executadas em dispositivos Windows 10 no modo de local público <!-- 2935135  -->
Pode utilizar dispositivos Windows 10 no modo de local público para executar uma aplicação ou várias aplicações. Esta atualização inclui várias alterações para utilizar aplicações de browser no modo de local público, incluindo:

- Adicionar o Browser do Microsoft Edge ou o Browser de local público para ser executado como aplicações no dispositivo local público (**configuração do dispositivo** > **perfis** > **novo perfil**  >  **Windows 10 e posterior** para a plataforma > **quiosque** para tipo de perfil).
- Restringir o Microsoft Edge para que ele pode (ou não) ser executado no modo de local público (**configuração do dispositivo** > **perfis** > **novo perfil**  >  **Windows 10 e posterior** para a plataforma > **restrições de dispositivos** para o tipo de perfil > **Browser do Microsoft Edge**). Quando não é executado no modo de quiosque, as definições do Microsoft Edge podem ser alteradas pelos usuários finais.

Para obter uma lista de definições atuais, veja:

- [Windows 10 e posteriores definições do dispositivo para ser executado como um quiosque](kiosk-settings-windows.md)
- [Restrições de dispositivos de Browser do Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser)

Aplica-se a: Windows 10 e posterior

### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Atribuir automaticamente etiquetas de âmbito para recursos criados por um administrador com esse âmbito <!-- 3173823  -->
Quando um administrador cria um recurso, quaisquer etiquetas de âmbito atribuídas para o administrador serão automaticamente atribuídas a esses novos recursos.

### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774---"></a>Novas definições de restrição de dispositivos para dispositivos iOS e macOS <!-- 3448774 -->
Pode restringir algumas definições e funcionalidades nos dispositivos que executam o iOS e macOS (**configuração do dispositivo** > **perfis** > **novo perfil**  >  **iOS** ou **macOS** para a plataforma > **restrições de dispositivos** para tipo de perfil). Esta atualização adiciona mais funcionalidades e as definições que pode controlar, incluindo o tempo de ecrã de configuração, alterar definições de eSIM e planos de celular, atrasando a visibilidade do usuário de atualizações de software, bloquear a colocação em cache conteúdo e muito mais.
Para ver os recursos atuais e configurações que pode restringir, consulte:
- [definições de restrição de dispositivos iOS](device-restrictions-ios.md)
- [definições de restrição de dispositivos macOS](device-restrictions-macos.md)

Aplica-se a:
- iOS
- macOS

### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202---"></a>Relatório de inscrição falha se move para o painel de inscrição de dispositivos <!-- 3560202 -->
O **falha inscrições** relatório irá mudar para o **Monitor** secção o **inscrição de dispositivos** painel. Também são adicionadas duas novas colunas (método de inscrição e versão do SO).

### <a name="change-kiosk-to-dedicated-devices----3598402----"></a>Alterar "Quiosque" para "Dispositivos dedicados" <!-- 3598402  -->
Para se alinhar a terminologia do Android, **quiosque** será alterado para **dispositivos dedicados** em perfis de configuração de dispositivos **Android enterprise**  >   **Proprietário do dispositivo** > **restrições de dispositivos**.

### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850--3803313----"></a>Safari e Delaying utilizador atualização de software iOS visibilidade definições estão a ser movidos na IU do Intune <!-- 3640850, , 3803313  -->
Para dispositivos iOS, pode configurar as definições do Safari e configurar atualizações de Software. Nesta atualização, estas definições estão a ser movidos para diferentes partes da IU do Intune:

- As definições do Safari estiver a mover de **Safari** (**configuração do dispositivo** > **perfis** > **novo perfil**  >  **iOS** para a plataforma > **restrições de dispositivo** para o tipo de perfil) para **aplicações incorporadas**. 
- O **atrasar a visibilidade de atualização de software de utilizador para supervisionado dispositivos iOS** definição (**atualizações de Software** > **atualizar políticas para iOS**) está a mudar para  **Restrições de dispositivos** > **geral**.

Para obter uma lista de definições atuais, veja [restrições de dispositivos iOS](device-restrictions-ios.md) e [atualizações de software iOS](software-updates-ios.md).

Aplica-se a: 
- iOS

### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164----"></a>Ativar restrições nas definições do dispositivo foi mudado para o tempo de tela em dispositivos iOS <!-- 3699164  -->
Pode configurar o **ativar restrições nas definições do dispositivo** no supervisionado dispositivos iOS (**configuração do dispositivo** > **perfis**  >  **Novo perfil** > **iOS** para a plataforma > **restrições de dispositivos** para o tipo de perfil > **geral**). Nesta atualização, esta definição foi mudada para **tempo de ecrã (apenas supervisionado)**. O comportamento é o mesmo. Especificamente: 

- iOS 11.4.1 e versões anteriores: **Bloco** impede que os utilizadores finais a definição de suas próprias restrições nas definições do dispositivo. 
- iOS 12.0 e posterior: **Bloco** impede que os utilizadores finais definir seus próprios **ecrã tempo** nas definições do dispositivo, incluindo restrições de privacidade & de conteúdo. Dispositivos atualizados para o iOS 12.0 não verão a guia restrições nas definições do dispositivo deixa de poder. Estas definições estão em **tempo de tela**. 

Para obter uma lista de definições atuais, veja [restrições de dispositivos iOS](device-restrictions-ios.md).

Aplica-se a: 
- iOS

### <a name="app-status-details-for-ios-apps----3761235----"></a>Detalhes do Estado da aplicação para aplicações iOS <!-- 3761235  -->
Haverá mensagens de erro de instalação de aplicação nova relacionadas ao seguinte:
- Falha de aplicações VPP durante a instalação num iPad partilhado
- Falha quando a loja de aplicações está desativada
- Falha ao localizar a licença do VPP para aplicação
- Falha ao instalar aplicações de sistemas com o fornecedor de MDM
- Falha ao instalar aplicações quando o dispositivo estiver no modo perdido ou o modo de local público
- Falha ao instalar a aplicação quando o utilizador não tem sessão iniciado na App Store

No Intune, selecione **aplicações de cliente** > **aplicações** > "Nome da aplicação" > **estado de instalação de dispositivo**. Novas mensagens de erro estará disponíveis na **detalhes do estado** coluna.

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Implementação de online licenciado Microsoft Store para aplicações de negócio <!-- 1672660  -->
Será capaz de atribuir necessário online licenciada Microsoft Store para aplicações de negócio no contexto do dispositivo. Implementar um Microsoft Store para a aplicação de negócios desta forma permitirá que a aplicação ser instalada para todos os utilizadores no dispositivo. Isto só é aplicável no Windows 10 RS4 + dispositivos de ambiente de trabalho. A opção para instalar no contexto do dispositivo está disponível na página de atribuição de aplicações de cliente para aplicações licenciadas Online do MSFB.

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Aplicação do Android Enterprise-implementação de aplicações, <!-- 1171203 -->
Para dispositivos Android num não inscritos proteção política sem inscrição de aplicações (APP-PODEMOS) cenário de implementação, poderá usar o Google Play gerido para implementar aplicações da loja e aplicações aos utilizadores LOB. Especificamente, o departamento de TI pode fornecer aos utilizadores finais uma experiência de instalação e de catálogo de aplicações que já não necessita que os utilizadores finais flexibilize as a postura de segurança dos seus dispositivos ao permitir que as instalações de origens desconhecidas. Além disso, neste cenário de implementação irá fornecer uma experiência de usuário aprimorada do fim.

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>As políticas do Intune atualizar o método de autenticação e a instalação da aplicação Portal da empresa  <!-- 1927359 -->
Nos dispositivos já inscritos através do Assistente de configuração através de um dos métodos de inscrição de dispositivos da empresa da Apple, o Intune suportará já não é o Portal da empresa quando é instalado manualmente pelos usuários finais da loja de aplicações. Esta alteração é relevante apenas quando se autenticar com o Assistente de configuração da Apple durante a inscrição. Esta alteração afeta também apenas dispositivos iOS inscritos através de:  
* Do Apple configurator
* Gerente de negócios da Apple
* Gestor Escolar da Apple
* Programa de inscrição de dispositivos Apple (DEP)

Se os utilizadores instalarem a aplicação Portal da empresa a partir da App store e, em seguida, tentar inscrever estes dispositivos através do mesmo, receberá um erro. Estes dispositivos serão esperados para utilizar o Portal da empresa apenas quando ele é foi emitido, automaticamente, pelo Intune durante a inscrição. Perfis de inscrição no Intune no portal do Azure serão atualizados para que pode especificar a forma como os dispositivos serão autenticados e se eles recebem a aplicação Portal da empresa. Se pretender que os utilizadores de dispositivos do DEP para o portal da empresa, terá de especificar as suas preferências num perfil de inscrição. Além disso, o **identificar o seu dispositivo** ecrã na aplicação Portal da empresa em breve se tornarão obsoleta.  
Para instalar o Portal da empresa em dispositivos DEP já inscrito, terá de ir para o Intune > aplicações de cliente e enviá-los como uma aplicação gerida com as políticas de configuração de aplicações. Detalhes sobre como efetuar estes passos irão ser descritos nos documentos futuros.

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Modelos administrativos estão em pré-visualização pública e movido para o seu próprio perfil de configuração <!-- 3322847 -->
Modelos administrativos no Intune (**configuração do dispositivo** > **modelos administrativos**) estão atualmente em pré-visualização privada. Com esta atualização: Modelos administrativos inclui aproximadamente 300 configurações que podem ser geridas no Intune. Anteriormente, estas definições só existiam no editor de políticas de grupo.
Modelos administrativos estão disponíveis em pré-visualização pública, administração estiver a mover de modelos **configuração do dispositivo** > **modelos administrativos** para **dispositivo configuração** > **perfis** >**criar perfil** > no **plataforma**, escolha  **Windows 10 e posterior**, na **tipo de perfil**, escolha **modelos administrativos**.
O relatório está ativado aplica-se a: Windows 10 e posterior

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>No modo escuro do Portal da empresa do Intune macOS <!-- 3300524 -->
O Portal da empresa do macOS do Intune agora suporta o modo escuro para macOS. Quando ativar o modo escuro num dispositivo macOS 10.14 +, o Portal da empresa irá ajustar sua aparência para as cores que refletem esse modo.

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Definições da Política de Proteção de Aplicações (APP) para dados da Web <!-- 2662995 -->
As definições da política APP para conteúdos da Web em dispositivos Android e iOS serão atualizadas para processar melhor ligações Web HTTP e HTTPS, bem como a transferência de dados através de Ligações Universais do iOS e Ligações de Aplicações do Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token Apple VPP utilizado por outra MDM <!-- 1488946 -->
O Intune irá detetar e mostrar detalhes se um token de programa de compras em volume (VPP) da Apple estiver a ser utilizado pelo Intune e outra MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivos extintos no dashboard de conformidade do dispositivo <!-- 1981119 -->
Numa atualização futura, os dispositivos extintos serão removidos do dashboard de conformidade do dispositivo. Tal irá alterar os seus números de conformidade.

## <a name="notices"></a>Avisos

Neste momento, não existem avisos ativos.

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.