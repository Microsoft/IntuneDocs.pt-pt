---
title: "Versões anteriores | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 57570fcf2f738b68a01bb1c5fc8962c7ef117920
ms.openlocfilehash: 43546721245f92309d86c496dbcde7900a598ed0


---

# Versões anteriores do Intune
## Julho de 2016
### Gestão de aplicações
#### Melhorar a experiência de atualização de perfis de aprovisionamento de aplicações
As aplicações de linha de negócio iOS da Apple são criadas com um perfil de aprovisionamento incluído e o respetivo código assinado com um certificado. Quando as aplicações são executadas num dispositivo iOS, o iOS confirma a integridade das mesmas e aplica as políticas definidas pelo perfil de aprovisionamento.

Geralmente, o certificado de assinatura da empresa que utiliza para assinar as aplicações dura três anos. No entanto, o perfil de aprovisionamento expira após um ano. Com esta atualização, o Intune proporciona-lhe as ferramentas para implementar proativamente uma nova política de perfil de aprovisionamento em dispositivos que tenham aplicações prestes a expirar enquanto o certificado ainda é válido. Para obter mais informações, veja [Use iOS mobile provisioning profile policies to keep your line of business apps up to date (Utilizar políticas de perfis de aprovisionamento móvel de iOS para manter as aplicações de linha de negócio atualizadas)](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->
#### Está disponível o SDK para Xamarin para aplicações do Intune
O componente Xamarin do SDK da Aplicação Intune permite-lhe ativar as funcionalidades de gestão de aplicações móveis do Intune nas suas aplicações móveis iOS e Android criadas com Xamarin. Pode obter o componente no [arquivo Xamarin](https://components.xamarin.com/view/Microsoft.Intune.MAM) ou na [página do Microsoft Intune no Github](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

### Gestão de dispositivos
#### Aumento nos limites de inscrição de dispositivos
O Intune aumentou o limite máximo de inscrição de dispositivos configuráveis de cinco para 15 dispositivos por utilizador.
<!---TFS 1289896 --->

#### Integração do TeamViewer para PCs Windows com o software de cliente Intune
A integração do [TeamViewer](https://www.teamviewer.com) para PCs Windows que executem o cliente do Intune vai permitir estabelecer sessões de assistência remota com PCs Windows para ajudar a dar apoio aos departamentos de suporte técnico ao utilizador final. Isto inclui o Windows 7, 8, 8.1 e o Windows 10. Para obter mais informações, veja [Tarefas de gestão comuns do PC Windows com o computador cliente do Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).
<!---TFS 1284856--->

### Atualizações ao Portal da Empresa
#### Web site do Portal da Empresa
- **Experiência do utilizador na inscrição de dispositivos Windows melhorada**<br/>
Se estiver a utilizar o acesso condicional, os passos de inscrição para Windows 8.1, ambiente de trabalho do Windows 10 e Windows 10 Mobile foram clarificados no Web site do Portal da Empresa. Agora, os utilizadores vão ver dois passos separados, “Inscrição de dispositivos” e “Workplace Join”, o que lhes permite ver mais facilmente o estado dos respetivos dispositivos e concluir o processo se se depararem com falhas na Workplace Join (WPJ). Espera-se que os passos separados também simplifiquem o processo de resolução de problemas para os administradores de TI. Anteriormente, quando os utilizadores finais tentavam inscrever e todos os passos da inscrição eram bem-sucedidos, menos a WPJ, o dispositivo inscrito não aparecia na lista de dispositivos para os utilizadores identificarem, confundindo-os.

#### Android
- **Aplicação do Portal da Empresa para Android**<br/>
Se os utilizadores finais do Azure virem uma mensagem de erro a dizer que falta um certificado necessário nos respetivos dispositivos, podem tocar num botão chamado “Como resolver isto” para obter [passos](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) para instalar o certificado em falta. Se os utilizadores concluírem os passos, mas virem uma mensagem de erro “certificado em falta” adicional, é-lhes pedido que contactem o administrador de TI e lhe forneçam esta [ligação](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues), que contém os passos que os administradores de TI podem utilizar para corrigir o problema do certificado.

- **Restringir instalações de aplicações sideload em dispositivos inscritos**<br/>
Os dispositivos Android já não podem instalar aplicações através do Web site do Portal da Empresa, a não ser que esses dispositivos tenham sido inscritos no Intune com a aplicação do Portal da Empresa para Android do Intune.
<!---TFS 1299082--->

#### iOS
- **Alterações às contas de Gestores de Inscrição de Dispositivos na aplicação do Portal da Empresa para iOS**<br/>
Para melhorar o desempenho e o dimensionamento, o Intune deixa de mostrar todos os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel **Os Meus Dispositivos** da aplicação do Portal da Empresa para iOS. Apenas é apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa.

O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só pode ser efetuada a partir da consola de administração do Intune. Além disso, o Intune está a descontinuar a utilização de contas DEM com o Programa de registo de dispositivos da Apple ou com a ferramenta Apple Configurator. Ambos os métodos de inscrição já suportam a inscrição sem a ação do utilizador para dispositivos iOS partilhados.

Utilize apenas contas DEM quando a inscrição sem a ação do utilizador para dispositivos partilhados não estiver disponível. Para obter mais informações, veja [Inscrever dispositivos pertencentes à empresa com o Gestor de Inscrição de Dispositivos no Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

### Alteração de nomes de funcionalidades do Windows
- O [Microsoft Passport para Windows](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) é agora conhecido como **Windows Hello para Empresas**.
- A [Proteção de dados da empresa](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) é agora conhecida como **Windows Information Protection**.

## Junho de 2016
### Estado de funcionamento do serviço do Intune
As informações de estado de funcionamento do serviço do Intune foram movidas para uma localização central com outros serviços Microsoft. Agora, pode encontrar estas informações no portal de gestão do Office 365, em Estado de Funcionamento do Serviço. Para obter mais informações, veja [esta mensagem do blogue](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### Gestão de aplicações
- **Experiência de configuração de política de dados do Windows 10 enterprise melhorada.** Efetuamos melhoramentos para a experiência de configuração da política de proteção de dados empresariais do Windows 10 sobre a criação de regras de aplicação, como especificar a definição de limites de rede e outras definições de proteção de dados empresariais. Para saber mais, veja o artigo [Criar uma política de proteção de dados empresariais (EDP) através do Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


### Gestão de dispositivos
- **Definição de política do Windows Defender contra aplicações potencialmente indesejáveis.** Uma nova definição do Windows Defender com o nome **Deteção de Aplicação Potencialmente Indesejável** foi adicionado à política de configuração geral para computadores de secretária com o Windows 10 e para o telemóvel. Pode utilizar esta definição para proteger computadores de secretária Windows inscritos contra software em execução classificado pelo Windows Defender como potencialmente indesejado. Pode proteger contra estas aplicações em execução ou utilizar o modo de auditoria para relatar quando uma aplicação potencialmente indesejável é instalada. Para obter mais informações, veja [Definições de política do Windows 10 no Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

### Acesso condicional
- **Política de controlo de acesso da rede Cisco ISE para o Intune.**  Os clientes que utilizam o Motor de Serviço de Identidade Cisco (ISE) 2.1 e que também utilizam o Microsoft Intune podem definir uma política de controlo de acesso de rede no ISE.

    Ao utilizar esta política, os dispositivos que precisa de ligar à rede através de Wi-Fi ou VPN devem cumprir seguintes condições antes de lhes ser concedido acesso:

    * Deve ser gerido pelo Intune
    * Deve ser compatível com todas políticas de conformidade do Intune implementadas

 Os utilizadores finais de dispositivos não conformes serão solicitados para inscrever-se e para retificar quaisquer problemas de compatibilidade para obter acesso.
- **Acesso condicional para browser.** Pode definir uma política de acesso condicional para o [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md) e o [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md) para que apenas os dispositivos iOS e Android geridos e compatíveis possam ser acedidos a partir de Web browsers suportados. Aos utilizadores finais que tentarem iniciar sessão no Outlook Web Access (OWA) e em sites do SharePoint com dispositivos iOS e Android será pedido que inscrevam o respetivo dispositivo no Intune, bem como que corrijam quaisquer problemas de não conformidade, para poderem concluir o início de sessão.
<!---TFS 1175844--->

- **O Dynamics CRM Online suporta o acesso condicional.** Pode definir uma política de acesso condicional para o [Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md) para que apenas dispositivos iOS e Android geridos e compatíveis possam aceder ao mesmo. Aos utilizadores finais que tentarem iniciar sessão na aplicação móvel Dynamics CRM Online em dispositivos iOS e Android será pedido que se inscrevam primeiro no Intune e que corrijam quaisquer problemas de não conformidade para que o início de sessão possa ser concluído.
<!---TFS1295358--->

##Atualizações ao Portal da Empresa

#### Aplicação do Portal da Empresa para Android

- Quando os administradores de TI aplicam a nova política "Exigir que os dispositivos não permitam a instalação de aplicações a partir de origens desconhecidas (Android 4.0 +)", os utilizadores finais com Android 4.0 ou dispositivos posteriores irão ver a mensagem "A instalação tem de ser desativada a partir de origens desconhecidas." Os utilizadores terão de ir para **Definições** > **Segurança**, e desativar **Origens desconhecidas**. Uma ligação na mensagem de compatibilidade permite aos utilizadores obterem mais [informações](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) sobre a mensagem e por que motivo é necessário desativar a definição.

- Quando os administradores de TI aplicam a nova política "Exigir que os dispositivos ativem a análise de ameaças de segurança em aplicações (Android 4.0 +)", os utilizadores finais com Android 4.0 ou dispositivos posteriores irão ver a mensagem "Analisar se o dispositivo apresenta ameaças de segurança." Os utilizadores terão de ir para **Definições** > **Google** > **Segurança** e ativar **Analisar se o dispositivo apresenta ameaças de segurança**. Uma ligação na mensagem de compatibilidade permite aos utilizadores obterem mais [informações](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sobre a mensagem e por que motivo é necessário ativar a definição.

- Quando os administradores de TI aplicam a nova política "Exigir a desativação da depuração de USB (Android 4.2 +)", os utilizadores finais com Android 4.2 ou dispositivos posteriores irão ver a mensagem "A depuração de USB deve ser desativada." Os utilizadores terão de ir para **Definições** > **Opções de programador** e desativar **Depuração de USB**." Uma ligação na mensagem de compatibilidade permite aos utilizadores obterem mais [informações](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) sobre a mensagem e por que motivo é necessário desativar a definição.

- Quando os administradores de TI aplicam a nova política "Nível mínimo de patch de segurança do Android (Android 6.0 +)", os utilizadores finais com Android 6.0 ou dispositivos posteriores irão ver a mensagem "Este dispositivo não cumpre o nível mínimo de patch de segurança do Android." Os utilizadores têm de instalar o patch de segurança necessário. Uma ligação na mensagem de compatibilidade permite aos utilizadores obter [informações](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sobre como instalar o patch de segurança necessário e ver que patch de segurança está atualmente instalado.

#### Aplicação Portal da Empresa para iOS

- Quando os utilizadores finais estiverem a instalar aplicações de linha de negócio, irão ver agora uma experiência de instalação de aplicações melhorada. Se a instalação da aplicação estiver a demorar muito tempo, os utilizadores podem sincronizar manualmente os respetivos dispositivos para forçar a continuação do processo de sincronização. Para ver as instruções para utilizadores finais, veja [Sincronizar o dispositivo iOS manualmente](/Intune/EndUser/sync-your-device-manually-ios).

- A aplicação do Portal da Empresa do Microsoft Intune para iOS foi atualizada para suportar a versão 8.0 do iOS e posteriores. Esta atualização significa que os utilizadores finais só podem instalar a aplicação do Portal da Empresa e inscrever dispositivos novos no Intune se estes executarem a versão 8.0 do iOS ou posterior. Os utilizadores que já inscreveram dispositivos que executem uma versão não suportada do iOS podem continuar a utilizar a aplicação Portal da Empresa que está nos dispositivos deles.


## Maio de 2016

Todas estas funcionalidades são também suportadas em implementações híbridas (Configuration Manager com o Intune). Para obter mais informações sobre as novas funcionalidades híbridas, veja a página [Hybrid What’s New (Novidades nas Implementações Híbridas)](https://technet.microsoft.com/en-us/library/mt718155.aspx).

### Documentação
Bem-vindo à versão de pré-visualização de [docs.microsoft.com](https://docs.microsoft.com/en-us/intune)!
Esta é uma plataforma de conteúdos completamente nova e moderna, concebida para ser mais fácil para si e para os nossos clientes compreenderem e utilizarem o Intune.
Para ler mais sobre todas as novas funcionalidades, veja [Introducing docs.microsoft.com (Introdução ao docs.microsoft.com)](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)

### Estado de funcionamento do serviço do Intune
As informações de estado de funcionamento do serviço do Intune foram movidas para uma localização central com outros serviços Microsoft. Agora, pode encontrar estas informações no [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx), em **Estado de Funcionamento do Serviço**.
Para obter mais informações, veja [esta mensagem do blogue](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).


### Gestão de aplicações
- **MAM SDK: suporta a configuração do comprimento do PIN.** Poderá especificar o comprimento do PIN para aplicações MAM, semelhante a um PIN de dispositivo. Isto irá necessitar que os utilizadores finais respeitem as novas restrições que definiu. Verão um ecrã de PIN ligeiramente modificado para caber a entrada mais longa. Para obter mais detalhes, veja [Definições de política de MAM para Android](android-mam-policy-settings.md) e [Definições de política de MAM para iOS](ios-mam-policy-settings.md).

- **Skype para Empresas, para iOS e Android.** É agora possível segmentar o Skype para empresas com [MAM sem políticas de inscrição](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md). Depois de os utilizadores iniciarem sessão, as políticas de MAM serão aplicadas.

- **Novas aplicações disponíveis para gestão com políticas de MAM.** As aplicações do Microsoft Word, Excel e PowerPoint para Android podem agora ser associadas a políticas de MAM em dispositivos que não estão inscritos no Intune. Para ver uma lista completa de aplicações suportadas, aceda à Galeria de aplicações móveis do Microsoft Intune, na página de [parceiros de aplicações do Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).


### Atualizações ao Portal da Empresa

#### Aplicação do Portal da Empresa para Android
- **Notificações de alerta do utilizador final**: os utilizadores finais irão agora ver notificações de alerta da aplicação do Portal da Empresa para Android quando estiverem a inscrever ou a remover os respetivos dispositivos do Portal da Empresa.

- **Alterações às contas de Gestores de Inscrição de Dispositivos na aplicação do Portal da Empresa para Android.** Para melhorar o desempenho e o dimensionamento, o Intune já não mostra todos os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel Os Meus Dispositivos da aplicação do Portal da Empresa para Android. Apenas é apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa. O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só pode ser efetuada a partir da consola de administração do Intune.

#### Web site do Portal da Empresa
- **Web site do Portal da Empresa: a faixa de identificação do dispositivo vai dar mais informações aos utilizadores finais.** Agora, os utilizadores finais podem identificar facilmente o dispositivo que selecionaram quando estão a utilizar o Web site do Portal da Empresa. Se for selecionado o dispositivo incorreto, poderão selecionar o dispositivo correto ao tocar na ligação **Tocar aqui** na faixa da página inicial.

## Novidades futuras
- **Inclusão da IU do centro de mensagens**. Como parte da migração do Intune para o [portal de gestão do Office 365](https://portal.office.com/), vamos começar a tirar partido do respetivo Centro de Mensagens para comunicar novas funcionalidades e outras notificações. Além disso, ao instalar a aplicação móvel Office 365 Admin complemento, pode receber notificações no seu telemóvel e reencaminhar facilmente mensagens para utilizadores ou para um alias de distribuição.
Vamos começar a utilizar o Centro de Mensagens com a versão de maio para o notificar quando as atualizações estiverem concluídas e incluiremos informações sobre funcionalidades novas e melhoradas do Intune. Inicie sessão no [portal de gestão do Office 365](https://portal.office.com/) e selecione a opção CENTRO DE MENSAGENS no painel de navegação esquerdo para espreitar ainda hoje o Centro de Mensagens.

- **Alterações às contas de Gestores de Inscrição de Dispositivos**. Para melhorar o desempenho e o dimensionamento, o Intune já não mostra **todos** os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel **Os Meus Dispositivos** da aplicação do Portal da Empresa para iOS. Apenas é apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa. O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só pode ser efetuada a partir da consola de administração do Intune. Além disso, o Intune está a descontinuar a utilização de contas DEM com o Programa de registo de dispositivos da Apple ou com a ferramenta Apple Configurator. Ambos os métodos de inscrição já suportam a inscrição sem a ação do utilizador para dispositivos iOS partilhados. Utilize apenas contas DEM quando a inscrição sem a ação do utilizador para dispositivos partilhados não estiver disponível.

### Roteiro da nuvem
Mantenha-se informado sobre os desenvolvimentos futuros do Intune com o [roteiro da Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Depreciação de serviço
- **Aplicações do Visualizador do Intune.** Com o lançamento da nova aplicação de partilha RMS, estamos a remover as seguintes aplicações do Visualizador do Intune, a partir de agosto de 2016:
    - Visualizador AV do Intune
    - Visualizador de PDFs do Intune
    - Visualizador de Imagens do Intune para Android a partir do Google Play

  Em vez de utilizar as aplicações do Visualizador do Intune, recomendamos que utilize a nova aplicação Rights Management (partilha RMS) para Android, o que lhe permite implementar uma aplicação em vez de três aplicações separadas para ver com segurança os ficheiros empresariais em dispositivos Android. Saiba mais sobre a aplicação de partilha RMS (com ligação à documentação).

- **Remoção da Filtragem Personalizada de Grupo de Regras de Notificação.**
As regras de notificações do Intune definem a quem será enviado um alerta de e-mail a partir do Intune. Atualmente, pode configurar regras de notificação para enviar e-mails a todos os utilizadores de dispositivos num grupo de dispositivos do Intune criado por si. A partir de 1 de junho de 2016, a filtragem de grupos criados pelo utilizador já não será suportada.

    Atualmente, para filtrar uma regra de notificação para um grupo que criou a partir da consola de administração do Microsoft Intune, terá de efetuar os seguintes passos:

    Na área de trabalho **Administração**, clique em **Regras de Notificações** > **Criar Nova Regra**

    No passo dois do Assistente para Criar Regra de Notificação, selecione os grupos de dispositivos que a regra irá visar. Este passo, “selecionar grupos de dispositivos”, vai ser removido da Consola do Intune.

    O calendário preliminar para esta alteração é o seguinte:
    - Em junho de 2016, os novos inquilinos deixarão de ver o passo dois do Assistente para Criar Regra de Notificação. Os inquilinos existentes não serão afetados.
    - Por volta de agosto de 2016, alguns inquilinos existentes não verão “selecionar grupos de dispositivos” no assistente.
    - Por volta de outubro de 2016, esperamos que nenhum inquilino veja “selecionar grupos de dispositivos” no assistente.


- **Alterações ao suporte para a aplicação do Portal da Empresa para iOS**. Nos próximos meses, existirá uma atualização para a aplicação do Portal da Empresa do Microsoft Intune para iOS que só irá suportar dispositivos que executem o iOS 8.0 ou posterior. Os utilizadores não poderão inscrever novos dispositivos que executem versões anteriores ao iOS 8.0. Os dispositivos inscritos que executem versões anteriores ao iOS 8.0 continuarão a ser geridos e, durante um período de tempo limitado, será possível continuar a utilizar a aplicação do Portal da Empresa. No entanto, os dispositivos devem ter o iOS 8.0 ou posterior para aceder às versões mais recentes da aplicação do Portal da Empresa. Aconselhamo-lo a notificar os utilizadores para atualizarem para o iOS 8.0 ou posterior, de modo a tirarem o máximo partido das novas funcionalidades do Intune.  


## Abril de 2016
Todas estas funcionalidades também são suportadas em clientes híbridos (Configuration Manager com o Intune).
### Gestão de aplicações
- **Conformidade de utilizadores MAM.**
Agora, pode ver o [estado](monitor-mobile-app-management-policies-with-Microsoft-Intune.md) das suas políticas de gestão de aplicações para qualquer utilizador no inquilino do Azure Active Directory (AAD). Isto inclui:
   - Dispositivos
   - Aplicações no dispositivo

   Valores de estado:

   **Com entrada dada**: indica que a política foi implementada para o utilizador, e a aplicação foi utilizada no contexto profissional, e recebeu com êxito a política.

    **Sem entrada dada:** indica que a política foi implementada para o utilizador, mas a aplicação não foi utilizada no contexto profissional desde então.


- **Controlos de MAM para impedir a sincronização de contactos do Outlook (Android).**
Uma nova definição está disponível para a [gestão de aplicações móveis](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) sem inscrição de dispositivos. Esta definição permite impedir que uma aplicação sincronize contactos com o livro de endereços nativo em dispositivos Android. Quando esta definição estiver ativada, as aplicações visadas já não poderão guardar contactos no livro de endereços nativo. Quando esta definição estiver desativada, as aplicações visadas poderão guardar contactos no livro de endereços nativo. Quando [elimina remotamente os dados de um dispositivo ou aplicação](wipe-managed-company-app-data-with-Microsoft-Intune.md), os contactos que já tenham sido guardados no livro de endereços nativo serão removidos. Esta nova definição é suportada inicialmente pela aplicação Outlook em dispositivos Android.

### Gestão de dispositivos
- **Identificação de números de telefone para dispositivos pertencentes à empresa.** Os telefones que são classificados como "Empresa" estão agora identificados com o respetivo número de telefone completo quando, por exemplo, executa um relatório de inventário de dispositivos móveis. Os números de telefone BYOD continuam a ser mascarados com ****, com apenas os 4 últimos dígitos apresentados.


### Atualizações ao portal da empresa
**Aplicação Portal da Empresa para Android** Os utilizadores que não inscreveram o seu dispositivo no Intune e que não tenham o certificado correto instalado não poderão iniciar sessão na aplicação Portal da Empresa para Android e verão a mensagem “Não é possível inscrever-se porque o dispositivo tem um certificado necessário em falta”. A mensagem inclui uma ligação "How to resolve this" na qual os utilizadores podem tocar para ver instruções para instalar o certificado. Para ver os passos que os utilizadores finais têm de seguir para resolver o problema, consulte [O dispositivo tem um certificado necessário em falta](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**Aplicação Portal da Empresa para iOS** Foi adicionado suporte para a ação “puxe para atualizar”, para atualizar o conteúdo do ecrã principal, que inclui as aplicações listadas, os dispositivos listados e as informações de contacto de TI. A ação «puxe para atualizar» não verifica se existem informações de conformidade ou de política, o que pode ser efetuado selecionando o mosaico relativo ao seu dispositivo atual e tocando no botão **Sincronizar**.

**Aplicação Portal da Empresa para Windows 10 Mobile e Windows Phone 8.1** Quando os utilizadores finais estiverem a instalar aplicações de linha de negócio, irão ver agora uma experiência melhorada de instalação de aplicações. Se a instalação da aplicação estiver a demorar muito tempo, os utilizadores podem sincronizar manualmente os respetivos dispositivos para forçar a continuação do processo de sincronização. Para consultar as instruções do utilizador final, consulte [Sincronizar o dispositivo manualmente para acelerar a instalação de aplicações](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Site do Portal da Empresa** Quando os utilizadores do Windows 10 Mobile e Windows Phone 8.1 estiverem a instalar aplicações de linha de negócio, irão ver agora os seguintes estados novos, que fornecem mais detalhes sobre o estado da instalação:

* **A aguardar sincronização do dispositivo** – o utilizador tocou em "Instalar" e o dispositivo tenta agora sincronizar com a infraestrutura do Intune. A sincronização é necessária para que a instalação possa ser concluída. A mensagem "A aguardar sincronização do dispositivo" é também uma ligação na qual os utilizadores podem tocar para ver [instruções](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) sobre como sincronizar manualmente o dispositivo com o Intune se o processo de sincronização estiver a demorar muito tempo ou ficar parado.
* **A transferir** – o pedido de transferência do utilizador está a ser processado e o dispositivo está a transferir e a instalar a aplicação.

Antes de estes estados terem sido adicionados, os utilizadores ficavam confusos se a instalação de uma aplicação demorava muito tempo, porque viam apenas um estado "A instalar", o qual podia permanecer no ecrã durante horas. Adicionar os novos estados significa que, em vez de contactar o suporte, os utilizadores podem agora tocar na ligação "A aguardar sincronização do dispositivo" e seguir as instruções para forçar a continuação do processo de sincronização.


## Março de 2016
### Novidades a partir de 29 de Março de 2016
Com exceção da atualização à política de configuração geral do Windows 10, todas as funcionalidades lançadas em 29 de março de 2016 também são suportadas em clientes híbridos (Configuration Manager integrado no Intune). O suporte híbrido da atualização da política de configuração geral do Windows 10 estará disponível em breve. Tenha em atenção que algumas destas funcionalidades podem necessitar da versão mais recente do Configuration Manager.

### Gestão de aplicações
- **Controlos de MAM para impedir a sincronização de contactos do Outlook (iOS).** Uma nova definição está disponível para a gestão de aplicações móveis sem inscrição de dispositivos. Esta definição permite impedir que uma aplicação sincronize contactos com o livro de endereços nativo em dispositivos iOS. Quando esta definição estiver ativada, a aplicação já não poderá guardar contactos no livro de endereços nativo. Quando esta definição estiver desativada, a aplicação poderá guardar contactos no livro de endereços nativo. Quando apaga seletivamente os dados de um dispositivo, todos os contactos que já tenham sido guardados no livro de endereços nativo serão removidos. Esta nova definição é suportada pela aplicação Outlook em dispositivos iOS. Para mais detalhes acerca desta e de outras definições, consulte [Criar e implementar políticas de MAM](https://technet.microsoft.com/en-us/library/dn292747.aspx).

### Controlo de acesso
- **O Skype para Empresas Online suporta o acesso condicional.** Pode definir uma política de acesso condicional para o Skype para Empresas Online, para que apenas dispositivos iOS e Android geridos e conformes possam aceder ao mesmo. Aos utilizadores finais que tentarem iniciar sessão na aplicação Skype para Empresas para dispositivos móveis em dispositivos iOS e Android será pedido que se inscrevam primeiro no Intune e que corrijam quaisquer problemas de não conformidade para que o início de sessão possa ser concluído. Para mais detalhes, consulte [Gerir o acesso ao Skype para Empresas Online](https://technet.microsoft.com/en-us/library/mt695297.aspx).

### Gestão de dispositivos
- **Suporte do Intune para iOS 9.3.** Na segunda-feira, 21 de março, a Apple anunciou a disponibilidade do iOS 9.3. Estivemos a trabalhar intensamente para garantir que o Microsoft Intune é compatível com a versão mais recente do sistema operativo móvel da Apple, e [temos o prazer de anunciar que o Intune suporta a gestão de dispositivos iOS 9.3](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/).

  Todas as funcionalidades existentes do Intune atualmente disponíveis para gerir dispositivos iOS continuarão a funcionar de forma totalmente integrada quando os utilizadores atualizarem os seus dispositivos para iOS 9.3. Além disso, o iOS 9.3 também é suportado atualmente para clientes híbridos (Configuration Manager integrado no Intune).

- **A política de configuração geral do Windows 10 contém agora definições para gerir o Windows Defender em PCs Windows 10 inscritos.** Para detalhes, consulte [Definições de política de configuração do Windows 10 no Microsoft Intune](https://technet.microsoft.com/en-us/library/mt404697.aspx).


### Portal da empresa

- **Pacotes de aplicações do Windows disponíveis diretamente a partir do site do Portal da Empresa.** Os utilizadores de PCs Windows 8, Windows 8.1 e Windows RT podem agora instalar pacotes de aplicações do Windows (com a extensão .appx) diretamente a partir do site do Portal da Empresa. Anteriormente, era necessário implementar, ou os utilizadores tinham de instalar, a aplicação Portal da Empresa nos respetivos dispositivos para instalar aplicações.

- **Os utilizadores podem bloquear remotamente o seu dispositivo a partir do site do Portal da Empresa.** Foi adicionada uma nova opção de bloqueio remoto ao site do Portal da Empresa para permitir que os utilizadores bloqueiem remotamente o seu dispositivo a partir do Portal, em caso de perda ou roubo do dispositivo. Consulte as [instruções do utilizador final](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock). A tabela seguinte lista o suporte de plataforma do Bloqueio Remoto para o Intune autónomo e o Intune com o Configuration Manager.

|Plataforma | Detalhes do suporte|
|---------|----------------|
|Android |Suportado|
|iOS |Suportado|
|Windows 10 Mobile |Suportado apenas se o telemóvel tiver um código de acesso definido|
|Windows 10 Desktop |Não suportado|
|Windows Phone 8.1 |Suportado apenas se o telemóvel tiver um código de acesso definido|
|Windows Phone 8.0 |Não suportado|
|PC (Windows 8.0 e anterior) |Não suportado|
|PC (Windows 8.1) |Não suportado|

### Novidades a partir de 10 de março de 2016

### Gestão de aplicações

- **Tirar partido da funcionalidade de gestão "Open-in" do iOS para dispositivos inscritos numa solução MDM de terceiros** Pode utilizar o fornecedor de gestão de dispositivos móveis (MDM) de terceiros para tirar partido da funcionalidade de gestão "Open-in" do iOS. Pode configurar as restrições nas definições do perfil de configuração e implementar a aplicação, utilizando [Gerir a transferência de dados entre aplicações iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).

     Esta abordagem tem duas vantagens principais:

     1. Os utilizadores são obrigados a iniciar sessão com a respetiva conta profissional antes de terem acesso a quaisquer dados empresariais a partir de Serviços Cloud ou de outras aplicações. Isto garante que as políticas de gestão de aplicações móveis (MAM) estão implementadas quando aceder aos dados.

     2. Os perfis de e-mail gerido e outras aplicações geridas implementadas através de uma solução MDM de terceiros podem partilhar ficheiros e dados com aplicações que tenham políticas MAM do Intune.

- **Gerir a aplicação Microsoft Outlook com políticas de MAM para dispositivos que não estão inscritos no Intune** Agora, já pode gerir a aplicação Microsoft Outlook em dispositivos que não estão inscritos no Intune com a política de gestão de aplicações móveis do Intune. A aplicação Microsoft Outlook atualizada com as capacidades MAM está disponível para dispositivos [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8) e [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook). Utilize as instruções do tópico [Criar e implementar políticas de gestão de aplicações móveis](https://technet.microsoft.com/library/mt627829.aspx) para criar uma política MAM.  


- **As políticas de configuração de aplicações móveis dão-lhe uma maior flexibilidade para especificar detalhes de utilizador para aplicações iOS** Pode fornecer as definições de utilizador que poderão ser necessárias a uma aplicação iOS quando for aberta. Por exemplo, pode fornecer uma porta de rede ou um nome de utilizador. Para detalhes, consulte [Configurar aplicações com políticas de configuração de aplicações móveis no Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md).


- **Implementar o Adobe Reader para Microsoft Intune em dispositivos iOS geridos pelo Intune na sua empresa** A aplicação Adobe Reader para iOS pode agora ser gerida em dispositivos inscritos com a política de gestão de aplicações móveis do Intune.

- **Garantir que os clips Web são abertos no browser gerido** Pode implementar clips Web direcionados, que só podem ser abertos com o browser gerido em dispositivos iOS e Android. Por exemplo, pode implementar hiperligações para recursos da empresa através do Portal da Empresa e quando os utilizadores navegarem para as hiperligações, estas abrem diretamente no browser gerido, onde podem ser protegidas pela política MAM. Para detalhes, consulte [Implementar aplicações](deploy-apps.md).


- **Localizar, gerir e distribuir aplicações da Loja Windows para Empresas para dispositivos Windows 10 a partir da consola do administrador do Intune** O suporte da Loja Windows para Empresas está disponível no Intune para o ajudar a localizar, gerir e distribuir aplicações para os dispositivos Windows 10 que estiver a gerir. A Loja Windows para Empresas permite-lhe gerir o processo de implementação e monitorização destas aplicações na consola do administrador do Intune — a mesma consola que utiliza para gerir as suas outras aplicações. Especificamente, a Loja Windows para Empresas gere o conteúdo e o licenciamento de "aplicações licenciadas online". Para detalhes, consulte [Gerir aplicações compradas na Loja Windows para Empresas](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md).


### Gestão de dispositivos
- **Distribuição de certificados PFX para dispositivos iOS** Os administradores do Intune podem criar e implementar certificados PFX iOS para Wi-Fi, e-mail e autenticação VPN em dispositivos iOS. Esta funcionalidade já se encontra disponível para dispositivos Android e Windows 10. Para detalhes, consulte [Permitir o acesso a recursos da empresa através de perfis de certificados](secure-resource-access-with-certificate-profiles.md).


- **Aplicar aplicações e políticas a diferentes grupos de dispositivos com base na seleção da categoria de utilizador** Os administradores do Intune podem agora definir categorias de dispositivo personalizadas para os utilizadores selecionarem durante a inscrição. Por exemplo, os administradores poderão querer que os utilizadores especifiquem se estão a inscrever um dispositivo utilizado para "Caixa registadora", "Camião de entregas" ou "Sala de inventário". A categoria selecionada fará com que o dispositivo passe a ser membro de um grupo de dispositivos do Intune, que pode ser utilizado para implementar diferentes aplicações e políticas no dispositivo inscrito. Para detalhes, consulte [Categorizar os dispositivos com o mapeamento de grupo de dispositivos](categorize-devices-with-device-group-mapping-in-microsoft-intune.md).

### Alterações e atualizações do Portal da Empresa da Microsoft
As seguintes alterações foram efetuadas no Portal da Empresa nesta versão:

**Aplicação do Portal da Empresa para Android**

* Quando os seus utilizadores iniciarem uma aplicação gerida pela gestão de aplicações móveis (MAM), verão uma mensagem a indicar que a aplicação é gerida pela empresa. Os utilizadores podem agora tocar numa hiperligação "Mais Informações" para obterem [mais informações](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps) sobre “aplicações geridas”. Também podem tocar em "Não voltar a mostrar" para que a mensagem deixe de aparecer quando iniciarem a aplicação.
* Foram adicionados novos ecrãs para orientar os utilizadores ao longo do processo de inscrição e fornecer mais informações sobre a razão pela qual os utilizadores devem efetuar a inscrição e o que os administradores de TI podem e não podem ver nos seus dispositivos inscritos. Consulte as [instruções de inscrição](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc) para obter mais informações.
* As mensagens de erro de inscrição são agora apresentadas na aplicação Portal da Empresa. Anteriormente, estas mensagens eram apresentados no site do Portal da Empresa. Esta alteração significa que todas as mensagens de erro são agora apresentadas apenas num local em vez de dois locais diferentes.


**Aplicação Portal da Empresa para iOS**
* Quando os seus utilizadores iniciarem uma aplicação gerida pela gestão de aplicações móveis (MAM), verão uma mensagem a indicar que a aplicação é gerida pela empresa. Os utilizadores podem agora tocar numa hiperligação "Mais Informações" para obterem [mais informações](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps) sobre “aplicações geridas”. Também podem tocar em "Não voltar a mostrar" para que a mensagem deixe de aparecer quando iniciarem a aplicação.
* Foram adicionados novos ecrãs para orientar os utilizadores ao longo do processo de inscrição e fornecer mais informações sobre a razão pela qual os utilizadores devem efetuar a inscrição e o que os administradores de TI podem e não podem ver nos seus dispositivos inscritos. Consulte as [instruções de inscrição](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device) para obter mais informações.
* As mensagens de erro de inscrição são agora apresentadas na aplicação Portal da Empresa. Anteriormente, estas mensagens eram apresentados no site do Portal da Empresa. Esta alteração significa que todas as mensagens de erro são agora apresentadas apenas num local em vez de dois locais diferentes.




## Fevereiro de 2016
### Alterações e atualizações do Portal da Empresa da Microsoft

As seguintes alterações foram efetuadas no Portal da Empresa nesta versão:

#### Aplicação do Portal da Empresa para Android
- Foram adicionados novos ecrãs para orientar os utilizadores ao longo do processo de inscrição e fornecer mais informações sobre a razão pela qual os utilizadores devem efetuar a inscrição e o que os administradores de TI podem e não podem ver nos seus dispositivos inscritos. Consulte as [instruções de inscrição](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc) para obter mais informações.
- As mensagens de erro de inscrição são agora apresentadas na aplicação Portal da Empresa. Anteriormente, estas mensagens eram apresentados no site do Portal da Empresa. Esta alteração significa que todas as mensagens de erro são agora apresentadas apenas num local em vez de dois locais diferentes.

#### Aplicação Portal da Empresa para iOS
 - Foram adicionados novos ecrãs para orientar os utilizadores ao longo do processo de inscrição e fornecer mais informações sobre a razão pela qual os utilizadores devem efetuar a inscrição e o que os administradores de TI podem e não podem ver nos seus dispositivos inscritos. Consulte as [instruções de inscrição](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device) para obter mais informações.

 - As mensagens de erro de inscrição são agora apresentadas na aplicação Portal da Empresa. Anteriormente, estas mensagens eram apresentados no site do Portal da Empresa. Esta alteração significa que todas as mensagens de erro são agora apresentadas apenas num local em vez de dois locais diferentes.


## Janeiro de 2016

### Tirar partido das funcionalidades do Windows 10
* **Acesso condicional com Serviço de Atestado de Estado de Funcionamento** Os administradores do Intune podem agora ver o estado do Atestado de Estado de Funcionamento do Dispositivo Windows 10 na consola de administração do Intune. O Device Health Attestation permite ao administrador garantir que os computadores cliente têm configurações fidedignas de BIOS, TPM e software de arranque. Para suportar o atestado de estado de funcionamento do dispositivo, os dispositivos cliente têm de ter o Windows 10 com o TPM 2 ativado. O Device Health Attestation apresenta o número de dispositivos ativados para cada o seguinte:
    * Antimalware de início antecipado
    * BitLocker
    * Arranque Seguro
    * Integridade de Código

    Leia o artigo [Introdução às políticas de conformidade de dispositivos para o Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md) para obter mais detalhes sobre a definição de estado de funcionamento do dispositivo, pontos de dados recolhidos e o relatório de atestado de estado de funcionamento. O tópico [Detalhes do serviço HAS](https://msdn.microsoft.com/en-us/library/dn934876.aspx) explica o serviço em profundidade.

* **Política Passport for Work e gestão de certificados do Windows 10** Com o Intune, é possível efetuar a [integração com o Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), que é um método de início de sessão alternativo para Windows 10 que utiliza o Active Directory ou uma conta do Azure Active Directory para substituir uma palavra-passe, um smart card ou um smart card virtual. O Passport permite utilizar um gesto de utilizador para iniciar sessão, em vez de uma palavra-passe. Um gesto de utilizador pode ser um PIN simples, uma autenticação biométrica, como o Windows Hello, ou um dispositivo externo, como um leitor de impressões digitais.

* **VPN para aplicações específicas** Pode selecionar aplicações que ligam automaticamente à sua rede empresarial através de VPN. Crie a lista de aplicações quando configurar o perfil VPN, conforme descrito no tópico Ajudar os utilizadores a estabelecer uma ligação com o respetivo trabalho através de perfis da VPN com o Microsoft Intune.

* **Suporte de Eliminação Completa de Dados do Windows 10** Agora, pode emitir uma eliminação completa remota de dados de dispositivos de ambiente de trabalho Windows 10 inscritos no Intune, através da consola de administração do Intune. A eliminação completa de dados do Windows 10 efetua uma reposição de fábrica do dispositivo.


### Atualização do Apple Volume Purchase Program (VPP)
O Intune pode agora ajudá-lo a [gerir as aplicações compradas através do Apple Volume Purchase Program (VPP) for Business](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md). Isto inclui sincronizar as informações de licença entre a Apple e o Intune, e controlar a quantidade de cópias de cada aplicação que implementou.

### Utilizar números IMEI para identificar dispositivos pertencentes à empresa
Agora, pode [importar números de identidade internacional do equipamento móvel (IMEI)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) para plataformas de dispositivos móveis que tenham um número IMEI para ajudar a identificar os dispositivos móveis pertencentes à empresa. Depois de inscritos no Intune, os dispositivos com números IMEI importados são etiquetados como Empresa, o que pode ser utilizado na aplicação de políticas diferentes das aplicadas a dispositivos de propriedade pessoal.

### Mais aplicações são agora compatíveis com as políticas MAM do Intune
Mais aplicações de parceiros da Microsoft são agora compatíveis com as políticas de gestão de aplicações móveis (MAM) do Intune (para dispositivos geridos pelo Intune):
* Box for EMM (da Box Inc) – apenas iOS
* Adobe Reader (da Adobe) – apenas Android
* Foxit PDF Reader (da Foxit Corporation) – iOS e Android


### O suporte do IE9 termina em janeiro
A partir de fevereiro de 2016, o Internet Explorer 9 já não será suportado como browser oficial para aceder ao site do portal da empresa do Microsoft Intune, ao portal de contas do Intune e à consola de administração do Intune. Terá de migrar para o Internet Explorer 10 ou posterior.


>[!div class="step-by-step"]

>[&larr; **Novidades do Intune**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Aug16_HO3-->


