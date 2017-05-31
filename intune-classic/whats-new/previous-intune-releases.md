---
title: "Versões anteriores | Documentos da Microsoft"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: fd1e154aed6b2afecb7a7b24b927f7a5f92acba9
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="previous-intune-releases"></a>Versões anteriores do Intune

Esta página é uma lista de anúncios realizados em [Novidades no Microsoft Intune](whats-new-in-microsoft-intune.md).

[!INCLUDE[wit_nextref](../includes/whats-new-last-six-months.md)]

## <a name="july-2016"></a>Julho de 2016

### <a name="app-management"></a>Gestão de aplicações

__Melhorar a experiência de atualização de perfis de aprovisionamento de aplicações__ As aplicações móveis de linha de negócio iOS da Apple são criadas com um perfil de aprovisionamento incluído e o respetivo código assinado com um certificado. Quando as aplicações são executadas num dispositivo iOS, o iOS confirma a integridade das mesmas e aplica as políticas definidas pelo perfil de aprovisionamento.

Geralmente, o certificado de assinatura da empresa que utiliza para assinar as aplicações dura três anos. No entanto, o perfil de aprovisionamento expira após um ano. Com esta atualização, o Intune proporciona-lhe as ferramentas para implementar proativamente uma nova política de perfil de aprovisionamento em dispositivos que tenham aplicações prestes a expirar enquanto o certificado ainda é válido. Para obter mais informações, veja [Use iOS mobile provisioning profile policies to keep your line of business apps up to date (Utilizar políticas de perfis de aprovisionamento móvel de iOS para manter as aplicações de linha de negócio atualizadas)](/intune-classic/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->

__Está disponível o SDK para Xamarin para aplicações do Intune__ O componente Xamarin do SDK da Aplicação Intune permite-lhe ativar as funcionalidades de gestão de aplicações móveis do Intune nas suas aplicações móveis iOS e Android criadas com Xamarin. Pode obter o componente no [arquivo Xamarin](https://components.xamarin.com/view/Microsoft.Intune.MAM) ou na [página do Microsoft Intune no Github](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

### <a name="device-management"></a>Gestão de dispositivos
__Aumento nos limites de inscrição de dispositivos__ O Intune aumentou o limite máximo de inscrição de dispositivos configuráveis de 5 para 15 dispositivos por utilizador.
<!---TFS 1289896 --->

__Integração do TeamViewer para PCs Windows com o software de cliente Intune__
[TeamViewer](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).
<!---TFS 1284856--->

### <a name="company-portal-updates"></a>Atualizações ao Portal da Empresa

__Site do Portal da Empresa__
- **Experiência do utilizador melhorada na inscrição de dispositivos Windows**<br/>
Se estiver a utilizar o acesso condicional, os passos de inscrição para Windows 8.1, dispositivos com o Windows 10 e o Windows 10 Mobile foram clarificados no Web site do Portal da Empresa. Agora, os utilizadores vão ver dois passos separados, “Inscrição de dispositivos” e “Workplace Join”, o que lhes permite ver mais facilmente o estado dos respetivos dispositivos e concluir o processo se se depararem com falhas na Workplace Join (WPJ). Espera-se que os passos separados também simplifiquem o processo de resolução de problemas para os administradores de TI. Anteriormente, quando os utilizadores finais tentavam inscrever e todos os passos da inscrição eram bem-sucedidos, menos a WPJ, o dispositivo inscrito não aparecia na lista de dispositivos para os utilizadores identificarem, confundindo-os.

__Android__
- **Aplicação do Portal da Empresa para Android**<br/>
Se os utilizadores finais de Android virem uma mensagem de erro a informar que os respetivos dispositivos não têm o certificado necessário, estes podem tocar no botão "Como resolver isto" para obterem os [passos](/intune-classic/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues) que os administradores de TI podem utilizar para resolver o problema do certificado.

- **Restringir instalações de aplicações sideload em dispositivos inscritos**<br/>
Os dispositivos Android já não podem instalar aplicações através do Web site do Portal da Empresa, a não ser que esses dispositivos tenham sido inscritos no Intune com a aplicação do Portal da Empresa para Android do Intune.
<!---TFS 1299082--->

__iOS__
- **Alterações às contas de Gestores de Inscrição de Dispositivos na aplicação do Portal da Empresa para iOS**<br/>
Para melhorar o desempenho e o dimensionamento, o Intune deixa de mostrar todos os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel **Os Meus Dispositivos** da aplicação do Portal da Empresa para iOS. Apenas é apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa.

O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só pode ser efetuada a partir da consola de administração do Intune. Além disso, o Intune está a descontinuar a utilização de contas DEM com o Programa de registo de dispositivos da Apple ou com a ferramenta Apple Configurator. Ambos os métodos de inscrição já suportam a inscrição sem a ação do utilizador para dispositivos iOS partilhados.

Utilize apenas contas DEM quando a inscrição sem a ação do utilizador para dispositivos partilhados não estiver disponível. Para obter mais informações, veja [Inscrever dispositivos pertencentes à empresa com o Gestor de Inscrição de Dispositivos no Microsoft Intune](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

### <a name="change-of-names-for-windows-features"></a>Alteração de nomes de funcionalidades do Windows
- O [Microsoft Passport para Windows](/intune-classic/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) é agora conhecido como **Windows Hello para Empresas**.
- A [Proteção de dados da empresa](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) é agora conhecida como **Windows Information Protection**.


## <a name="june-2016"></a>Junho de 2016
### <a name="intune-service-health"></a>Estado de funcionamento do serviço do Intune
As informações de estado de funcionamento do serviço do Intune foram movidas para uma localização central com outros serviços Microsoft. Agora, pode encontrar estas informações no portal de gestão do Office 365, em Estado de Funcionamento do Serviço. Para obter mais informações, veja [esta mensagem do blogue](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### <a name="app-management"></a>Gestão de aplicações
- **Experiência de configuração da política de dados empresariais do Windows 10 melhorada.** Efetuamos melhoramentos para a experiência de configuração da política de proteção de dados empresariais do Windows 10 sobre a criação de regras de aplicação, como especificar a definição de limites de rede e outras definições de proteção de dados empresariais. Para saber mais, veja [Criar uma política de proteção de dados empresariais (EDP) através do Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


### <a name="device-management"></a>Gestão de dispositivos
- **Definição de política do Windows Defender contra aplicações potencialmente indesejáveis.** Uma nova definição do Windows Defender com o nome **Deteção de Aplicação Potencialmente Indesejável** foi adicionado à política de configuração geral para dispositivos com o Windows 10 e o Windows 10 Mobile. Pode utilizar esta definição para proteger computadores de secretária Windows inscritos contra software em execução classificado pelo Windows Defender como potencialmente indesejado. Pode proteger contra estas aplicações em execução ou utilizar o modo de auditoria para relatar quando uma aplicação potencialmente indesejável é instalada. Para obter mais informações, veja [Definições de política do Windows 10 no Microsoft Intune](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

### <a name="conditional-access"></a>Acesso condicional
- **Política de controlo de acesso à rede Cisco ISE para o Intune.**  Os clientes que utilizam o Motor de Serviço de Identidade Cisco (ISE) 2.1 e que também utilizam o Microsoft Intune podem definir uma política de controlo de acesso de rede no ISE.

    Ao utilizar esta política, os dispositivos que precisa de ligar à rede através de Wi-Fi ou VPN devem cumprir seguintes condições antes de lhes ser concedido acesso:

    * Deve ser gerido pelo Intune
    * Deve ser compatível com todas políticas de conformidade do Intune implementadas

 Os utilizadores finais de dispositivos não conformes serão solicitados para inscrever-se e para retificar quaisquer problemas de compatibilidade para obter acesso.
- **Acesso condicional para browser.** Pode definir uma política de acesso condicional para o [Exchange Online](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) para que apenas os dispositivos iOS e Android geridos e compatíveis possam ser acedidos a partir de browsers suportados. Aos utilizadores finais que tentarem iniciar sessão no Outlook Web Access (OWA) e em sites do SharePoint com dispositivos iOS e Android será pedido que inscrevam o respetivo dispositivo no Intune, bem como que corrijam quaisquer problemas de não conformidade, para poderem concluir o início de sessão.
<!---TFS 1175844--->

- **O Dynamics CRM Online suporta o acesso condicional.** Pode definir uma política de acesso condicional para o [Dynamics CRM Online](/intune-classic/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) para que apenas dispositivos iOS e Android geridos e compatíveis possam aceder ao mesmo. Aos utilizadores finais que tentarem iniciar sessão na aplicação móvel Dynamics CRM Online em dispositivos iOS e Android será pedido que se inscrevam primeiro no Intune e que corrijam quaisquer problemas de não conformidade para que o início de sessão possa ser concluído.
<!---TFS1295358--->

### <a name="intune-company-portal-updates"></a>Atualizações ao Portal da Empresa do Intune

__Aplicação do Portal da Empresa para Android__

- Quando os administradores de TI aplicam a nova política "Exigir que os dispositivos não permitam a instalação de aplicações a partir de origens desconhecidas (Android 4.0 +)", os utilizadores finais com Android 4.0 ou dispositivos posteriores irão ver a mensagem "A instalação tem de ser desativada a partir de origens desconhecidas." Os utilizadores terão de ir para **Definições** > **Segurança** e desativar **Origens desconhecidas**. Uma ligação na mensagem de compatibilidade permite aos utilizadores obterem mais [informações](/intune-user-help/you-are-asked-to-turn-off-unknown-sources-android) sobre a mensagem e por que motivo é necessário desativar a definição.

- Quando os administradores de TI aplicam a nova política "Exigir que os dispositivos ativem a análise de ameaças de segurança em aplicações (Android 4.0 +)", os utilizadores finais com Android 4.0 ou dispositivos posteriores irão ver a mensagem "Analisar se o dispositivo apresenta ameaças de segurança." Os utilizadores terão de ir para **Definições** > **Google** > **Segurança** e ativar **Analisar se o dispositivo apresenta ameaças de segurança**. Uma ligação na mensagem de compatibilidade permite aos utilizadores obterem mais [informações](/intune-user-help/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sobre a mensagem e por que motivo é necessário ativar a definição.

- Quando os administradores de TI aplicam a nova política "Exigir a desativação da depuração de USB (Android 4.2 +)", os utilizadores finais com Android 4.2 ou dispositivos posteriores irão ver a mensagem "A depuração de USB deve ser desativada." Os utilizadores terão de ir para **Definições** > **Opções de programador** e desativar **Depuração de USB**." Uma ligação na mensagem de compatibilidade permite aos utilizadores obterem mais [informações](/intune-user-help/you-are-asked-to-turn-off-usb-debugging-android) sobre a mensagem e por que motivo é necessário desativar a definição.

- Quando os administradores de TI aplicam a nova política "Nível mínimo de patch de segurança do Android (Android 6.0 +)", os utilizadores finais com Android 6.0 ou dispositivos posteriores irão ver a mensagem "Este dispositivo não cumpre o nível mínimo de patch de segurança do Android." Os utilizadores têm de instalar o patch de segurança necessário. Uma ligação na mensagem de compatibilidade permite aos utilizadores obter [informações](/intune-user-help/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sobre como instalar o patch de segurança necessário e ver que patch de segurança está atualmente instalado.

__Aplicação do Portal da Empresa para iOS__

- Quando os utilizadores finais estiverem a instalar aplicações de linha de negócio, irão ver agora uma experiência de instalação de aplicações melhorada. Se a instalação da aplicação estiver a demorar muito tempo, os utilizadores podem sincronizar manualmente os respetivos dispositivos para forçar a continuação do processo de sincronização. Para ver as instruções para utilizadores finais, veja [Sincronizar o dispositivo iOS manualmente](/intune-user-help/sync-your-device-manually-ios).

- A aplicação do Portal da Empresa do Microsoft Intune para iOS foi atualizada para suportar a versão 8.0 do iOS e posteriores. Esta atualização significa que os utilizadores finais só podem instalar a aplicação do Portal da Empresa e inscrever dispositivos novos no Intune se estes executarem a versão 8.0 do iOS ou posterior. Os utilizadores que já inscreveram dispositivos que executem uma versão não suportada do iOS podem continuar a utilizar a aplicação Portal da Empresa que está nos dispositivos deles.

## <a name="may-2016"></a>Maio de 2016
Todas estas funcionalidades são também suportadas em implementações híbridas (Configuration Manager com o Intune). Para obter mais informações sobre as novas funcionalidades híbridas, consulte a página [Hybrid What’s New (Novidades nas Implementações Híbridas)](https://technet.microsoft.com/library/mt718155.aspx).

### <a name="documentation"></a>Documentação
Bem-vindo à versão de pré-visualização de [docs.microsoft.com](https://docs.microsoft.com/intune)!
Esta é uma plataforma de conteúdos completamente nova e moderna, concebida para ser mais fácil para si e para os nossos clientes compreenderem e utilizarem o Intune.
Para ler mais sobre todas as novas funcionalidades, veja [Introducing docs.microsoft.com (Introdução ao docs.microsoft.com)](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)

### <a name="intune-service-health"></a>Estado de funcionamento do serviço do Intune
As informações de estado de funcionamento do serviço do Intune foram movidas para uma localização central com outros serviços Microsoft. Agora, pode encontrar estas informações no [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx), em **Estado de Funcionamento do Serviço**.
Para obter mais informações, veja [esta mensagem do blogue](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### <a name="app-management"></a>Gestão de aplicações
- **SDK de MAM: suporta a configuração do comprimento do PIN.** Poderá especificar o comprimento do PIN para aplicações MAM, semelhante a um PIN de dispositivo. Isto irá necessitar que os utilizadores finais respeitem as novas restrições que definiu. Verão um ecrã de PIN ligeiramente modificado para caber a entrada mais longa. Para obter mais detalhes, veja [Definições da política de MAM para Android](/intune-classic/deploy-use/ios-mam-policy-settings).

- **Skype para Empresas para iOS e Android.** É agora possível segmentar o Skype para empresas com [MAM sem políticas de inscrição](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). Depois de os utilizadores iniciarem sessão, as políticas de MAM serão aplicadas.

- **Novas aplicações disponíveis para gestão com políticas de MAM.** As aplicações do Microsoft Word, Excel e PowerPoint para Android podem agora ser associadas a políticas de MAM em dispositivos que não estão inscritos no Intune. Para ver uma lista completa de aplicações suportadas, aceda à Galeria de aplicações móveis do Microsoft Intune, na página de [parceiros de aplicações do Microsoft Intune](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx).


### <a name="company-portal-updates"></a>Atualizações ao Portal da Empresa

#### <a name="android-company-portal-app"></a>Aplicação Portal da Empresa para Android
- **Notificações de alerta do utilizador final**: os utilizadores finais irão agora ver notificações de alerta da aplicação Portal da Empresa para Android quando estiverem a inscrever ou a remover os respetivos dispositivos do Portal da Empresa.

- **Alterações às contas de Gestores de Inscrição de Dispositivos na aplicação Portal da Empresa para Android.** Para melhorar o desempenho e o dimensionamento, o Intune já não mostra todos os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel Os Meus Dispositivos da aplicação Portal da Empresa para Android. Apenas é apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa. O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só pode ser efetuada a partir da consola de administração do Intune.

#### <a name="company-portal-website"></a>Site do Portal da Empresa
- **Site do Portal da Empresa: a faixa de identificação do dispositivo irá fornecer mais informações aos utilizadores finais.** Agora, os utilizadores finais podem identificar facilmente o dispositivo que selecionaram quando estão a utilizar o Web site do Portal da Empresa. Se for selecionado o dispositivo incorreto, poderão selecionar o dispositivo correto ao tocar na ligação **Tocar aqui** na faixa da página inicial.

### <a name="service-deprecation"></a>Depreciação de serviço
- **Aplicações do Visualizador do Intune.** Com o lançamento da nova aplicação de partilha RMS, estamos a remover as seguintes aplicações do Visualizador do Intune, a partir de agosto de 2016:
    - Visualizador AV do Intune
    - Visualizador de PDFs do Intune
    - Visualizador de Imagens do Intune para Android a partir do Google Play

  Em vez de utilizar as aplicações do Visualizador do Intune, recomendamos que utilize a nova aplicação Rights Management (partilha RMS) para Android, o que lhe permite implementar uma aplicação em vez de três aplicações separadas para ver com segurança os ficheiros empresariais em dispositivos Android. Saiba mais sobre a aplicação de partilha RMS (com ligação à documentação).

- **Remoção da Filtragem Personalizada de Grupo das Regras de Notificação.**
As regras de notificações do Intune definem a quem será enviado um alerta de e-mail a partir do Intune. Atualmente, pode configurar regras de notificação para enviar e-mails a todos os utilizadores de dispositivos num grupo de dispositivos do Intune criado por si. A partir de 1 de junho de 2016, a filtragem de grupos criados pelo utilizador já não será suportada.

    Atualmente, para filtrar uma regra de notificação para um grupo que criou a partir da consola de administração do Microsoft Intune, terá de efetuar os seguintes passos:

    Na área de trabalho **Administração**, clique em **Regras de Notificações** > **Criar Nova Regra**

    No passo dois do Assistente para Criar Regra de Notificação, selecione os grupos de dispositivos que a regra irá visar. Este passo, “selecionar grupos de dispositivos”, vai ser removido da Consola do Intune.

    O calendário preliminar para esta alteração é o seguinte:
    - Em junho de 2016, os novos inquilinos deixarão de ver o passo dois do Assistente para Criar Regra de Notificação. Os inquilinos existentes não serão afetados.
    - Por volta de agosto de 2016, alguns inquilinos existentes não verão “selecionar grupos de dispositivos” no assistente.
    - Por volta de outubro de 2016, esperamos que nenhum inquilino veja “selecionar grupos de dispositivos” no assistente.


- **Alterações ao suporte para a aplicação Portal da Empresa para iOS**. Nos próximos meses, existirá uma atualização para a aplicação Portal da Empresa do Microsoft Intune para iOS que só irá suportar dispositivos que executem o iOS 8.0 ou posterior. Os utilizadores não poderão inscrever novos dispositivos que executem versões anteriores ao iOS 8.0. Os dispositivos inscritos que executem versões anteriores ao iOS 8.0 continuarão a ser geridos e, durante um período de tempo limitado, será possível continuar a utilizar a aplicação Portal da Empresa. No entanto, os dispositivos devem ter o iOS 8.0 ou posterior para aceder às versões mais recentes da aplicação Portal da Empresa. Aconselhamo-lo a notificar os utilizadores para atualizarem para o iOS 8.0 ou posterior, de modo a tirarem o máximo partido das novas funcionalidades do Intune.  


## <a name="april-2016"></a>Abril de 2016
Todas estas funcionalidades também são suportadas em clientes híbridos (Configuration Manager com o Intune).

### <a name="app-management"></a>Gestão de aplicações
- **Conformidade de utilizadores MAM.**
Agora, pode ver o [estado](/intune-classic/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune) das suas políticas de gestão de aplicações para qualquer utilizador no inquilino do Azure Active Directory (AAD). Isto inclui:
   - Dispositivos
   - Aplicações no dispositivo

   Valores de estado:

   **Com entrada dada**: indica que a política foi implementada para o utilizador, a aplicação foi utilizada no contexto profissional e recebeu com êxito a política.

    **Sem entrada dada:** indica que a política foi implementada para o utilizador, mas a aplicação não foi utilizada no contexto profissional desde então.


- **Controlos de MAM para impedir a sincronização dos contactos do Outlook (Android).**
Está disponível uma nova definição para a [gestão de aplicações móveis](/intune-classic/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune). Os contactos que já foram guardados no livro de endereços nativo serão removidos. Esta nova definição é suportada inicialmente pela aplicação Outlook em dispositivos Android.

### <a name="device-management"></a>Gestão de dispositivos
- **Identificação de números de telefone para dispositivos pertencentes à empresa.** Os telefones que são classificados como "Empresa" estão agora identificados com o respetivo número de telefone completo quando, por exemplo, executa um relatório de inventário de dispositivos móveis. Os números de telefone BYOD continuam a ser mascarados com ****, com apenas os 4 últimos dígitos apresentados.


### <a name="company-portal-updates"></a>Atualizações ao portal da empresa
**Aplicação Portal da Empresa para Android** Os utilizadores que não inscreveram o seu dispositivo no Intune e que não tenham o certificado correto instalado não poderão iniciar sessão na aplicação Portal da Empresa para Android e verão a mensagem “Não é possível inscrever-se porque o dispositivo tem um certificado necessário em falta”. A mensagem inclui uma ligação "How to resolve this" na qual os utilizadores podem tocar para ver instruções para instalar o certificado. Para ver os passos que os utilizadores finais têm de seguir para resolver o problema, veja [O dispositivo tem um certificado necessário em falta](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**Aplicação Portal da Empresa para iOS** Foi adicionado suporte para a ação “puxe para atualizar”, para atualizar o conteúdo do ecrã principal, que inclui as aplicações listadas, os dispositivos listados e as informações de contacto de TI. A ação «puxe para atualizar» não verifica se existem informações de conformidade ou de política, o que pode ser efetuado selecionando o mosaico relativo ao seu dispositivo atual e tocando no botão **Sincronizar**.

**Aplicação Portal da Empresa para Windows 10 Mobile e Windows Phone 8.1** Quando os utilizadores finais estiverem a instalar aplicações de linha de negócio, irão ver agora uma experiência melhorada de instalação de aplicações. Se a instalação da aplicação estiver a demorar muito tempo, os utilizadores podem sincronizar manualmente os respetivos dispositivos para forçar a continuação do processo de sincronização. Para consultar as instruções do utilizador final, veja [Sincronizar o dispositivo manualmente para acelerar a instalação de aplicações](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Site do Portal da Empresa** Quando os utilizadores do Windows 10 Mobile e Windows Phone 8.1 estiverem a instalar aplicações de linha de negócio, irão ver agora os seguintes estados novos, que fornecem mais detalhes sobre o estado da instalação:

* **A aguardar sincronização do dispositivo** – o utilizador tocou em "Instalar" e o dispositivo tenta agora sincronizar com a infraestrutura do Intune. A sincronização é necessária para que a instalação possa ser concluída. A mensagem "A aguardar sincronização do dispositivo" é também uma ligação na qual os utilizadores podem tocar para ver [instruções](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) sobre como sincronizar manualmente o dispositivo com o Intune se o processo de sincronização estiver a demorar muito tempo ou ficar parado.
* **A transferir** – o pedido de transferência do utilizador está a ser processado e o dispositivo está a transferir e a instalar a aplicação.

Antes de estes estados terem sido adicionados, os utilizadores ficavam confusos se a instalação de uma aplicação demorava muito tempo, porque viam apenas um estado "A instalar", o qual podia permanecer no ecrã durante horas. Adicionar os novos estados significa que, em vez de contactar o suporte, os utilizadores podem agora tocar na ligação "A aguardar sincronização do dispositivo" e seguir as instruções para forçar a continuação do processo de sincronização.

>[!div class="step-by-step"]

>[&larr; **Novidades do Intune**](whats-new-in-microsoft-intune.md)    

