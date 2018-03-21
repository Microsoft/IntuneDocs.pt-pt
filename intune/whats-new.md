---
title: Novidades do Microsoft Intune
titlesuffix: 
description: Descobrir as novidades do Intune no portal do Azure
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 01/02/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 513164a1f734fddb6ac66fcaffdc2fb885a4659a
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/09/2018
---
# <a name="whats-new-in-microsoft-intune"></a>Novidades do Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Saiba mais sobre as novidades todas as semanas no Microsoft Intune. Pode também descobrir quais são as [alterações futuras](#whats-coming), os [avisos importantes](#notices) sobre o serviço e as informações sobre [versões anteriores](whats-new-archive.md).

> [!Note]
> Para obter informações sobre novas funcionalidades na gestão de dispositivos móveis (MDM) híbrida, veja a nossa [página Hybrid What’s New (Novidades nas Implementações Híbridas)](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   


## <a name="week-of-february-19-2018"></a>Semana de 19 de fevereiro de 2018
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Suporte do Intune para várias contas do DEP da Apple/Apple School Manager <!-- 747685 -->
 
O Intune agora suporta a inscrição de dispositivos com até 100 contas diferentes do Programa de Inscrição de Dispositivos (DEP) da Apple ou do Apple School Manager. Cada token carregado pode ser gerido separadamente para dispositivos e perfis de inscrição. Um perfil de inscrição diferente pode ser automaticamente atribuído por token do DEP/School Manager carregado. Se forem carregados vários tokens do School Manager, só um poderá ser partilhado com a School Data Sync da Microsoft de cada vez.

Após a migração, as Graph APIs beta e os scripts publicados para gerir o DEP da Apple ou o ASM através do Graph deixarão de funcionar. Estão em desenvolvimento novas Graph APIs beta e serão lançadas após a migração.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Ver restrições de inscrição por utilizador <!-- 1634444 eeready wnready -->
No painel **Resolução de problemas**, pode agora ver as restrições de inscrição de cada utilizador ao selecionar **Restrições de inscrição** na lista **Atribuições**.

### <a name="device-management"></a>Gestão de dispositivos
#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Relatórios de estado da ameaça e estado de funcionamento do Windows Defender <!--854704 -->

Compreender o funcionamento e o estado do Windows Defender é fundamental para gerir PCs Windows.  Com esta atualização, o Intune adiciona novos relatórios e ações ao estado e estado de funcionamento do agente Windows Defender. Através de um relatório de roll up do estado na carga de trabalho de Conformidade do Dispositivo, pode ver os dispositivos que necessitam de:
- atualização de assinatura
- Reiniciar
- intervenção manual
- análise completa
- outros estados de agente a precisar de intervenção

Um relatório de agregação para cada categoria de estado indica os PCs individuais que precisam de atenção ou os que estão registados como **Limpar**.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Novas definições de privacidade para restrições do dispositivo <!--1308926 -->
Estão agora disponíveis duas novas definições de privacidade para os dispositivos:
- **Publicar as atividades do utilizador**: defina esta opção para **Bloquear** para impedir que as experiências e a deteção de recursos utilizados recentemente sejam partilhadas no comutador de tarefas.
- **Apenas atividades locais**: defina esta opção para **Bloquear** para impedir que as experiências e a deteção de recursos utilizados recentemente sejam partilhadas no comutador de tarefas com base na atividade local.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Novas definições no browser Edge <!--1469166 -->
Estão agora disponíveis duas novas definições de privacidade para os dispositivos com o browser Edge: **Caminho para o ficheiro de favoritos** e **Alterações aos Favoritos**. 

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

A conta de recurso é utilizada por um Surface Hub para efetuar a autenticação com o Skype/Exchange para que possa participar numa reunião. Poderá querer criar uma conta de recurso exclusiva para que o Surface Hub seja apresentado na reunião como a sala de conferência. Por exemplo, uma conta de recurso como **Sala de Conferência B41/6233**.

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

|Nome da definição  |Opções da definição  |Descrição  |
|---------|---------|---------|
|Proteção de pastas (já implementada)|Não configurado, Ativar, Apenas auditoria (já implementada)<br><br> **Novidade**<br>Bloquear modificação do disco, Auditar modificação do disco|
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

Os clientes que utilizam o conector do NDES no local para entregar certificados aos dispositivos podem agora configurar vários conectores num único inquilino.

Esta nova capacidade suporta o seguinte cenário:

- **Elevada disponibilidade**

Cada conector do NDES obtém os pedidos de certificados do Intune.  Se um conector do NDES ficar offline, o outro conector poderá continuar a processar pedidos.

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>Nome do requerente do cliente pode utilizar a variável AAD_DEVICE_ID <!-- 1468599 -->

Quando cria um perfil de certificado SCEP no Intune, agora, pode utilizar a variável AAD_DEVICE_ID ao criar o nome do requerente personalizado.   Quando o certificado é solicitado através deste perfil SCEP, a variável é substituída pelo ID de dispositivo do AAD do dispositivo que faz o pedido de certificado.


### <a name="device-management"></a>Gestão de dispositivos

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Gerir dispositivos macOS inscritos com Jamf através do motor de conformidade de dispositivo do Intune <!-- 1592747 -->
Agora, pode utilizar o Jamf para enviar informações sobre o estado do dispositivo macOS ao Intune que, em seguida, avaliará a conformidade com as políticas definidas na consola do Intune. Com base no estado de conformidade do dispositivo, bem como outras condições (como a localização, risco do utilizador, etc.), o acesso condicional estabelecerá a conformidade dos dispositivos macOS que tentem aceder a aplicações na nuvem e no local ligadas com o Azure Active Directory, incluindo o Office 365. Saiba mais sobre como [configurar a integração do Jamf](conditional-access-integrate-jamf.md) e [impor a conformidade para dispositivos geridos pelo Jamf](conditional-access-assign-jamf.md).

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

#### <a name="end-user-messaging-for-accounts---1573558-for-1712--"></a>Mensagens do utilizador final relativas às contas <!--1573558 for 1712-->

Os utilizadores do site do Portal da Empresa serão impedidos de realizar ações que necessitem de acesso de escrita ao inquilino. Estes utilizadores verão mensagens de erro adequadas a explicar que as suas contas estão em manutenção. Em breve, serão feitas algumas alterações semelhantes às aplicações do Portal da Empresa para Android, iOS, macOS e Windows. Pode ver este erro na página [novidades na IU da aplicação](whats-new-app-ui.md).



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


## <a name="week-of-november-27-2017"></a>Semana de 27 de novembro de 2017

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="troubleshoot-enrollment-issues-----746324---"></a>Resolução de problemas de inscrição <!-- 746324 -->

A área de trabalho **Resolução de Problemas** agora apresenta os problemas de inscrição de utilizadores. Os detalhes acerca do problema e os passos de remediação sugeridos podem ajudar os administradores e os operadores de suporte técnico a resolver problemas. Existem determinados problemas de inscrição que não são detetados e é possível que não existam sugestões de remediação para alguns erros.

#### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restrições de inscrição atribuídas a grupos <!-- 747598 -->

Enquanto administrador do Intune, agora pode [criar restrições de inscrição personalizadas de Tipo de Dispositivo e Limite de Dispositivo para grupos de utilizadores](enrollment-restrictions-set.md).

O portal do Azure do Intune permite-lhe criar até 25 instâncias de cada tipo de restrição, que podem depois ser atribuídas a grupos de utilizadores. As restrições atribuídas a grupos substituem as restrições predefinidas.

Todas as instâncias de um tipo de restrição são mantidas numa lista estritamente ordenada. Esta ordem define um valor de prioridade para a resolução do conflito. Um utilizador afetado por mais do que uma instância de restrição só é restringido pela instância com o valor de prioridade mais elevada. Pode alterar a prioridade de uma determinada instância ao arrastá-la para uma posição diferente na lista.

Esta funcionalidade será lançada com a migração das definições do Android for Work do menu de inscrição do Android for Work para o menu Restrições de Inscrição. Como esta migração pode demorar vários dias, poderão ser atualizadas outras partes da sua conta no lançamento de novembro antes da ativação da atribuição de grupos nas Restrições de Inscrição.

#### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Suporte para múltiplos conectores do Serviço de Inscrição de Dispositivos de Rede (NDES) <!-- 1528104 -->

O NDES permite a execução de dispositivos móveis sem credenciais de domínio para obter certificados com base no protocolo SCEP (Simple Certificate Enrollment Protocol).
Com esta atualização, são suportados múltiplos conectores do NDES.

#### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Gerir dispositivos Android for Work de forma independente dos dispositivos Android <!-- 1490731 EEready-->

**Nota**: as seguintes alterações começarão a ser implementadas com a atualização de novembro, mas a execução na sua conta poderá demorar algum tempo. Receberá uma notificação de confirmação no portal do Office 365 quando estas alterações entrarem em vigor na sua conta. Após a implementação, terá opções de capacidade de gestão adicionais. Não existirão alterações à experiência do utilizador final durante a implementação.

O Intune suporta a gestão de inscrição de dispositivos Android for Work de forma independente da plataforma Android. Estas definições são geridas em **Inscrição de Dispositivos** > **Restrições de inscrição** > **Restrições de Tipos de Dispositivos**. (Estavam anteriormente localizadas em **Inscrição de Dispositivos** > **Inscrição do Android for Work** > **Definições de Inscrição do Android for Work**.)

Por predefinição, as definições dos dispositivos Android for Work são as mesmas que as definições dos seus dispositivos Android. No entanto, depois de alterar as definições do Android for Work, este já não será o caso.

Se bloquear a inscrição pessoal do Android for Work, só será possível inscrever dispositivos Android empresariais como Android for Work.

Ao trabalhar com as novas definições, tenha em conta o seguinte:

##### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Se nunca tiver integrado a inscrição do Android for Work

A nova plataforma do Android for Work está bloqueada nas Restrições de Tipos de Dispositivos predefinidas. Depois de integrar a funcionalidade, pode permitir que os dispositivos sejam inscritos com o Android for Work. Para tal, altere a predefinição ou crie uma nova Restrição de Tipo de Dispositivo para substituir a Restrição de Tipo de Dispositivo predefinida.

##### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Se já tiver integrado a inscrição do Android for Work

Se já a tiver integrado, a sua situação depende da definição que escolher:

| Definição | Estado do Android for Work em Restrição de Tipo de Dispositivo predefinida | Notas |
| --- | --- | --- |
| **Gerir todos os dispositivos como Android** | Bloqueado | Todos os dispositivos Android têm de ser inscritos sem o Android for Work. |
| **Gerir dispositivos suportados como Android for Work** | Permitido | Todos os dispositivos Android que suportam o Android for Work têm de ser inscritos com o Android for Work. |
| **Gerir dispositivos suportados para utilizadores apenas nestes grupos como Android for Work** | Bloqueado | Foi criada uma política de Restrição de Tipo de Dispositivo separada para substituir a predefinição. Esta política define os grupos que selecionou anteriormente para permitir a inscrição do Android for Work. Os utilizadores nos grupos selecionados continuarão a poder inscrever os seus dispositivos Android for Work. Todos os outros utilizadores não efetuam a inscrição com o Android for Work. |

Em todos os casos, mantém-se o seu regulamento pretendido. Não é necessária nenhuma ação da sua parte para manter a permissão global ou por grupo do Android for Work no seu ambiente.

### <a name="app-management"></a>Gestão de aplicações

#### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>O relatório de instalação da aplicação foi atualizado para incluir o estado Instalação Pendente <!-- 1249446 -->  

O relatório **Estado de instalação de aplicação** acessível para cada aplicação através da lista **Aplicação** na carga de trabalho **Aplicações móveis** contém uma contagem de **Instalações Pendentes** para Utilizadores e Dispositivos.

#### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API do inventário de aplicações para iOS 11 para a Deteção de Ameaças para Dispositivos Móveis <!-- 1391759 -->

O Intune recolhe informações do inventário de aplicações de dispositivos pessoais e empresariais e disponibiliza-as aos fornecedores de Deteção de Ameaças para Dispositivos Móveis (MTD), como o Lookout for Work. Pode recolher o inventário de aplicações dos utilizadores de dispositivos com o iOS 11 ou uma versão superior.

**Inventário de aplicações**  
Os inventários de dispositivos iOS pessoais ou empresariais com o iOS 11 ou uma versão superior são enviados para o seu fornecedor de serviços de MTD. Os dados no inventário de aplicações incluem:

 - ID da Aplicação
 - Versão da Aplicação
 - Versão Abreviada da Aplicação
 - Nome da Aplicação
 - Tamanho da Coleção de Pacotes de Aplicação
 - Tamanho Dinâmico da Aplicação
 - A aplicação é ou não validada
 - A aplicação é ou não gerida


### <a name="device-management"></a>Gestão de dispositivos

#### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>Migrar utilizadores e dispositivos da MDM híbrida para o Intune autónomo <!-- 1463747 wnready -->
Estão agora disponíveis novos processos e ferramentas para migrar utilizadores e os respetivos dispositivos da MDM híbrida para o Intune no portal do Azure, que lhe permitem efetuar as seguintes tarefas:
- Copiar políticas e perfis da consola do Configuration Manager para o Intune no portal do Azure
- Mover um subconjunto de utilizadores para o Intune no portal do Azure enquanto mantém os restantes na MDM híbrida
- Migrar dispositivos para o Intune no portal do Azure sem precisar de voltar a inscrevê-los

Para obter detalhes, veja [Migrate hybrid MDM users and devices to Intune standalone (Migrar os dispositivos e utilizadores da MDM híbrida para o Intune autónomo)](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

#### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Suporte de elevada disponibilidade do conector do Exchange no local <!-- 676614 -->
Depois de o conector do Exchange criar uma ligação ao Exchange através da CAS especificada, o conector terá a capacidade de detetar outras CASs. Se a CAS principal ficar indisponível, o conector realizará a ativação pós-falha de outra CAS, se disponível, até a CAS principal ficar disponível. Para obter mais informações, veja [Suporte de elevada disponibilidade do conector do Exchange no local](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support).

#### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Reiniciar dispositivos iOS remotamente (apenas supervisionado) <!-- 1424595 -->

Agora pode acionar o reinício de um dispositivo supervisionado com o iOS 10.3 ou superior ao utilizar uma ação de dispositivo. Para obter mais informações sobre como utilizar a ação de reinício de dispositivos, veja [Reiniciar remotamente dispositivos com o Intune](device-restart.md).

> [!Note]
> Este comando necessita de um dispositivo supervisionado e do direito de acesso **Bloqueio do Dispositivo**. O dispositivo é reiniciado imediatamente. Os dispositivos iOS bloqueados por código de acesso não voltarão a ligar-se a uma rede Wi-Fi após o reinício. Após o reinício, estes dispositivos poderão não conseguir comunicar com o servidor.

#### <a name="single-sign-on-support-for-ios----1333645---"></a>Suporte de Início de Sessão Único para iOS <!-- 1333645 -->  

Pode utilizar o Início de Sessão Único para utilizadores do iOS. As aplicações iOS que estão codificadas para procurar as credenciais dos utilizadores no payload de Início de Sessão Único são compatíveis com esta atualização de configuração do payload. Também pode utilizar o UPN e o ID de Dispositivo do Intune para configurar o Nome Principal e o Realm. Para obter detalhes, veja [Configure Intune for iOS device single sign-on (Configurar o Intune para o início de sessão único em dispositivos iOS)](sso-ios.md).

#### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Adicionar "Encontrar iPhone" para dispositivos pessoais <!--1427287-->
Agora pode ver se os dispositivos iOS têm o Bloqueio de Ativação ativado. Esta funcionalidade estava anteriormente disponível no portal clássico do Intune.


#### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Bloquear remotamente dispositivos macOS geridos com o Intune <!-- 1437691 -->

Pode bloquear um dispositivo macOS perdido e definir um PIN de recuperação de 6 dígitos. Se estiver bloqueado, o painel **Descrição geral do dispositivos** apresenta o PIN até que seja enviada outra ação de dispositivo.

Para obter mais informações, veja [Bloquear remotamente dispositivos geridos com o Intune](device-remote-lock.md).

#### <a name="new-scep-profile-details-supported----1559808---"></a>Suporte para novos detalhes do perfil SCEP <!-- 1559808 -->

Agora, os administradores podem configurar definições adicionais ao criar um perfil SCEP em plataformas Windows, iOS, macOS e Android.  Os administradores podem definir o IMEI, o número de série ou o nome comum, incluindo o e-mail, no formato do nome do requerente.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

#### <a name="retain-data-during-a-factory-reset----1588489---"></a>Reter dados durante uma reposição de fábrica <!--1588489 -->
Quando repõe uma versão 1709 ou posterior do Windows 10 para as definições de fábrica, fica disponível uma nova capacidade. Os administradores podem especificar se a inscrição de dispositivos e outros dados aprovisionados são retidos num dispositivo através de uma reposição de fábrica.

Os seguintes dados são retidos através de uma reposição de fábrica:
- Contas de utilizador associadas ao dispositivo
- Estado da máquina (associação a um domínio, associado ao Azure Active Directory)
- Inscrição na MDM
- Aplicações OEM instaladas (aplicações Win32 e da loja)
- Perfil de utilizador
- Dados de utilizador fora do perfil de utilizador
- Início de sessão automático de utilizador

Os seguintes dados não são retidos:
- Ficheiros do utilizador
- Aplicações instaladas pelo utilizador (aplicações Win32 e da loja)
- Definições do dispositivo não predefinidas

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas
#### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Atribuições de cadência de atualização do Windows 10 são apresentadas <!-- 1621837 -->
Durante a **Resolução de problemas** do utilizador que está a ver, pode ver todas as atribuições de cadências de atualização do Windows 10.  

#### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Definições da frequência de relatórios de Proteção Avançada Contra Ameaças do Windows Defender <!-- 1455974  -->
O serviço de Proteção Avançada Contra Ameaças do Windows Defender (WDATP) permite aos administradores gerir a frequência de relatórios dos dispositivos geridos. Com a nova opção **Acelerar a frequência do relatório de telemetria**, o WDATP recolhe os dados e avalia os riscos com mais frequência. A predefinição dos relatórios otimiza a velocidade e o desempenho. O aumento da frequência de relatórios pode ser útil para dispositivos de alto risco. Poderá encontrar esta definição no perfil **Windows Defender ATP** nas **Configurações do dispositivo**.

#### <a name="audit-updates----1412961---"></a>Atualizações de auditoria <!-- 1412961 -->  
A auditoria do Intune fornece um registo das operações de alteração relacionadas com o Intune.  Todas as operações de criação, atualização, eliminação e realização de tarefas remotas são registadas e retidas durante um ano.  O portal do Azure fornece uma vista dos dados de auditoria dos últimos 30 dias em cada carga de trabalho e podem ser filtrados.  A Graph API correspondente permite a obtenção dos dados de auditoria armazenados do último ano.

A Auditoria está localizada no grupo **MONITORIZAÇÃO**. Existe um item de menu **Registos de Auditoria** para cada carga de trabalho.




## <a name="week-of-november-20-2017"></a>Semana de 20 de novembro de 2017

### <a name="app-management"></a>Gestão de aplicações

#### <a name="google-play-protect-support-on-android----908720---"></a>Suporte ao Google Play Protect no Android<!-- 908720 -->

Com o lançamento do Android Oreo, a Google apresenta um conjunto de funcionalidades de segurança chamado Google Play Protect, que permite que os utilizadores e as organizações executem imagens Android e aplicações seguras. O Intune agora suporta funcionalidades do Google Play Protect, incluindo o atestado remoto SafetyNet. Os administradores podem definir os requisitos da política de conformidade que são necessários para o Google Play Protect ser configurado e funcionar corretamente.
A definição **Atestado do dispositivo SafetyNet** requer que o dispositivo para estabelecer ligação com um serviço do Google verifique se o dispositivo está a funcionar e se não está comprometido. Os administradores também podem especificar uma definição de perfil de configuração do Android For Work que exija que as aplicações instaladas sejam verificadas pelos serviços do Google Play. O acesso condicional pode impedir que os utilizadores acedam a recursos da empresa caso o dispositivo não esteja em conformidade com os requisitos do Google Play Protect.

- Saiba [Como criar uma política de conformidade de dispositivos para ativar o Google Play Protect](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect).

#### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocolo de texto autorizado a partir de Aplicações geridas <!-- 1414050  -->

As aplicações geridas pelo SDK da Aplicação Intune podem enviar mensagens SMS.

## <a name="week-of-november-13-2017"></a>Semana de 13 de novembro de 2017

### <a name="intune-apps"></a>Aplicações do Intune
#### <a name="company-portal-app-for-macos-is-available---1541700--"></a>A aplicação Portal da Empresa para macOS está disponível <!--1541700-->
O Portal da Empresa do Intune no macOS tem uma experiência atualizada, a qual foi otimizada para apresentar corretamente todas as informações e notificações de conformidade que os utilizadores precisam para todos os dispositivos inscritos. Além disso, após implementar o Portal da Empresa do Intune num dispositivo, o Microsoft AutoUpdate para macOS fornecerá as atualizações. Pode transferir o novo Portal da Empresa do Intune para macOS ao iniciar sessão no site do Portal da Empresa do Intune a partir de um dispositivo macOS.

#### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>O Microsoft Planner faz agora parte da lista de gestão de aplicações móveis (MAM) de aplicações aprovadas <!-- 1248473 -->
A aplicação Microsoft Planner para iOS e Android faz agora parte das aplicações aprovadas para a gestão de aplicações móveis (MAM). A aplicação pode ser configurada através do painel Proteção de Aplicações do Intune no portal do Azure para todos os inquilinos.
- Saiba mais sobre a [Lista MAM de aplicações aprovadas](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

#### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>Frequência de atualização dos requisitos de VPN por Aplicação em dispositivos iOS <!-- 1547061 -->  
Os administradores podem agora remover os requisitos de VPN por Aplicação para as aplicações em dispositivos iOS; os dispositivos afetados serão removidos após a próxima entrada do Intune, o que geralmente ocorre num espaço de 15 minutos.  

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas
#### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Suporte para o pacote de gestão do System Center Operations Manager do conector do Exchange <!-- 885457 -->
O pacote de gestão do System Center Operations Manager (SCOM) do conector do Exchange está agora disponível para ajudá-lo a analisar os registos do conector do Exchange. Esta funcionalidade disponibiliza maneiras diferentes de monitorizar o serviço quando precisar de resolver problemas.

## <a name="week-of-november-6-2017"></a>Semana de 6 de novembro de 2017

### <a name="device-enrollment"></a>Inscrição de dispositivos
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>Cogestão para dispositivos Windows 10 <!-- 1243445 -->
A cogestão é uma solução que proporciona a transição de uma gestão tradicional para uma moderna, além de permitir que faça essa transição de forma faseada. Na sua génese, a cogestão é uma solução em que os dispositivos Windows 10 são geridos simultaneamente pelo Configuration Manager e pelo Microsoft Intune, além de estar associada ao Active Directory (AD) e ao Azure Active Directory (Azure AD).  Esta configuração proporciona-lhe uma forma de modernizar a gestão com ao longo do tempo e ao ritmo mais adequado para a sua organização, caso não consiga efetuar a mudança de uma só vez.  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Restringir a Inscrição do Windows por versão do SO <!-- 245498 -->
Enquanto administrador do Intune, pode especificar uma versão mínima e máxima do Windows 10 para a inscrição de dispositivos. Pode definir estas restrições no painel **Configurações da Plataforma**.

O Intune irá continuar a suportar a inscrição de telemóveis e PCs com o Windows 8.1. No entanto, apenas as versões do Windows 10 podem ser definidas com os limites mínimo e máximo. Para permitir a inscrição de dispositivos com o Windows 8.1, deixe o limite mínimo em branco.

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Alertas para dispositivos Windows AutoPilot não atribuídos  <!-- 1631236 -->
Está disponível um novo alerta para dispositivos Windows AutoPilot não atribuídos na página **Microsoft Intune** > **Inscrição de dispositivos** > **Descrição geral**. Este alerta mostra o número de dispositivos do programa AutoPilot que não têm perfis de implementação do AutoPilot atribuídos. Utilize as informações no alerta para criar perfis e atribui-los aos dispositivos não atribuídos. Quando clica no alerta, é-lhe apresentada uma lista completa dos dispositivos Windows AutoPilot e informações detalhadas sobre os mesmos. Para obter mais informações, veja [Inscrever dispositivos Windows com o programa de implementação do Windows AutoPilot](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="refresh-button-for-devices-list-------1333581---"></a>Botão de atualização da lista Dispositivos    <!-- 1333581 -->
Como a lista Dispositivos não atualiza automaticamente, pode utilizar o novo botão Atualizar para atualizar os dispositivos que são apresentados na lista.

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Suporte para a Autoridade de Certificação (AC) da Symantec Cloud <!-- 1333638 -->    
O Intune agora suporta a AC da Symantec Cloud, que permite ao Intune Certificate Connector emitir certificados PKCS a partir da AC da Symantec Cloud para os dispositivos geridos pelo Intune. Se já estiver a utilizar o Intune Certificate Connector com a Autoridade de Certificação (AC) da Microsoft, pode utilizar a configuração existente do Intune Certificate Connector para incluir o suporte à AC da Symantec.

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>Novos itens adicionados ao inventário de dispositivos   <!--1404455 -->
Estão agora disponíveis os seguintes novos itens no [inventário de dispositivos inscritos](device-inventory.md):

- Endereço MAC Wi-Fi
- Espaço de armazenamento total
- Espaço livre total
- MEID
- Operadora subscritora


### <a name="app-management"></a>Gestão de aplicações
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Definir o acesso a aplicações através de uma atualização de segurança mínima para Android no dispositivo <!-- 1278463 -->   
Um administrador pode definir a atualização de segurança mínima para Android que tem de ser instalada no dispositivo, de modo a obter acesso a uma aplicação gerida numa conta gerida.

> [!Note]  
> Esta funcionalidade apenas restringe atualizações de segurança lançadas pela Google em dispositivos Android 6.0+.

#### <a name="app-conditional-launch-support----1193313---"></a>Suporte para execução condicional de aplicações <!-- 1193313 -->
Os administradores de TI já podem definir um requisito através do portal de administração do Azure para impor um código de acesso em vez de um PIN numérico através da gestão de aplicações móveis (MAM) quando a aplicações é executada. Caso esteja configurado, é pedido ao utilizador que defina e utilize um código de acesso antes de poder aceder a aplicações otimizadas para a MAM. Os código de acesso são definidos como um PIN numérico com, pelo menos, um caráter especial ou letras em maiúsculas/minúsculas. Esta versão do Intune irá ativar esta funcionalidade **apenas no iOS**. O Intune suporta um código de acesso de forma semelhante a um PIN numérico: a aplicação define um comprimento mínimo e permite sequências e carateres repetidos. Esta funcionalidade requer que a participação de aplicações (por exemplo, WXP, Outlook, Managed Browser, Yammer) integre o SDK da Aplicação Intune com o código desta funcionalidade para que as definições do código de acesso sejam impostas nas aplicações visadas.

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Número da Versão de Aplicação para aplicações de linha de negócio no relatório de estado de instalação do dispositivo <!-- 1233999 -->
Com esta versão, o relatório de estado de instalação do Dispositivo apresenta o número da versão de aplicação das aplicações de linha de negócio para iOS e Android. Pode utilizar estas informações para resolver problemas nas suas aplicações ou localizar dispositivos que estão a ser executados com versões desatualizadas da aplicação.


### <a name="device-configuration"></a>Configuração do dispositivo
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Agora, os administradores podem configurar as definições de Firewall num dispositivo através de um perfil de configuração de dispositivo <!-- 951708 -->   
Os administradores podem ativar a firewall para os dispositivos, bem como configurar vários protocolos para redes de domínio privadas e públicas.  Poderá encontrar estas definições de firewall no perfil "Proteção de ponto final".

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>O Windows Defender Application Guard ajuda a proteger os dispositivos de sites não fidedignos, consoante as definições da sua organização <!-- 958257 -->   
Os administradores podem definir sites como "fidedigno" ou "empresarial" através de um fluxo do Windows Information Protection ou do novo perfil "Limite de rede" nas configurações dos dispositivos. Se forem acedidos com o Microsoft Edge, todos os sites que não estiverem indicados no limite de rede fidedigno de um dispositivo com o Windows 10 de 64 bits serão abertos num browser num computador virtual Hyper-V.

Poderá encontrar o Application Guard nos perfis de configuração de dispositivos, no perfil "Proteção de ponto final". A partir daí, os administradores podem configurar a interação entre o browser virtualizado e o computador anfitrião, sites fidedignos e não fidedignos e os dados de armazenamento gerados no browser virtualizado. Para utilizar o Application Guard num dispositivo, é necessário configurar primeiro um limite de rede. É importante definir apenas um limite de rede para um dispositivo.  

#### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>O Controlo de Aplicações do Windows Defender no Windows 10 Enterprise fornece um modo para confiar apenas em aplicações autorizadas <!-- 1031096 -->    
Com milhares de novos ficheiros maliciosos a serem criados todos os dias, a deteção com base em assinatura de antivírus para combater software maligno poderá deixar de ser uma defesa adequada contra novos ataques. Com o Controlo de Aplicações do Windows Defender no Windows 10 Enterprise, pode alterar a configuração do dispositivo de um modo em que as aplicações são fidedignas, a menos que sejam bloqueadas por um antivírus ou por outra solução de segurança, para um modo em que o sistema operativo confia apenas nas aplicações autorizadas pela sua empresa. A atribuição de fidedignidade a aplicações é feita no Controlo de Aplicações do Windows Defender.

Com o Intune, pode configurar as políticas de controlo de aplicações no modo "apenas auditoria" ou no modo de imposição. As aplicações não são bloqueadas ao serem executadas no modo "apenas auditoria". O modo "apenas auditoria" regista todos os eventos nos registos do cliente local. Também pode configurar se pretende que apenas os componentes Windows e as aplicações da Microsoft Store tenham permissão para serem executados ou se pretende permitir a execução de aplicações adicionais com boa reputação, conforme definido pelo Gráfico de Segurança Inteligente.

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>O Windows Defender Exploit Guard é um novo conjunto de funcionalidades de prevenção de intrusões para o Windows 10 <!-- 1063615 -->   
O Windows Defender Exploit Guard inclui regras personalizadas para reduzir a exploração de aplicações, impede ameaças de macros e scripts, bloqueia automaticamente ligações de rede a endereço IP com baixa reputação e ajuda a proteger os dados de ransomware e ameaças desconhecidas. O Windows Defender Exploit Guard consiste nos seguintes componentes:

- A **Redução da Superfície de Ataque (ASR)** fornece regras que lhe permitem impedir ameaças de macros, scripts e e-mail.
- O **Acesso a Pastas Controladas** bloqueia automaticamente o acesso a conteúdos de pastas protegidas.
- O **Filtro de Rede** bloqueia a ligação de saída de qualquer aplicação para um IP/domínio com baixa reputação
- A **Exploit Protection** fornece restrições de memória, fluxo de controlos e de políticas que podem ser utilizadas para proteger um aplicação de exploits.


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Gerir scripts do PowerShell no Intune para dispositivos Windows 10 <!-- 790537 -->

A extensão de gestão do Intune permite-lhe carregar scripts do PowerShell no Intune para executar em dispositivos Windows 10. A extensão complementa as funcionalidades de gestão de dispositivos móveis (MDM) do Windows 10 e facilita a sua transição para a gestão moderna. Para obter detalhes, veja [Manage PowerShell scripts in Intune for Windows 10 devices (Gerir scripts do PowerShell no Intune para dispositivos Windows 10)](intune-management-extension.md).

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Novas definições de restrição de dispositivos para Windows 10      <!-- 1308850 -->
-    Mensagens (apenas para telemóveis) – desativar mensagens de teste ou MMS
-    Palavra-passe – definições para ativar o sistema FIPS e utilizar dispositivos secundários Windows Hello para efeitos de autenticação 
-    Apresentação – definições para ativar ou desativar o Dimensionamento de GDI para aplicações legadas

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Restrições de dispositivos Windows 10 no modo de local público <!-- 1308872 -->   
Pode restringir os utilizadores de dispositivos Windows 10 ao modo de local público, que os limita a um conjunto de aplicações predefinidas.  Para fazê-lo, crie um perfil de restrição de dispositivos Windows 10 e configure as definições do modo de local público.

O modo de local público suporta dois modos: **quiosque de uma aplicação** (permite que um utilizador execute apenas uma aplicação) ou **quiosque de várias aplicações** (concede acesso a um conjunto de aplicações).  Defina a conta de utilizador e o nome do dispositivo, o qual determina as aplicações suportadas).  Quando o utilizador tiver sessão iniciada, este será limitado às aplicações definidas.  Para saber mais, veja [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp). 

O modo de local público necessita que:

- O Intune seja a autoridade MDM.
- As aplicações já estejam instaladas no dispositivo alvo.
- O dispositivo esteja [devidamente aprovisionado](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Novo perfil de configuração de dispositivos para a criação de limites de rede <!-- 1311967 -->   
Está agora disponível um novo perfil de configuração de dispositivos denominado **Limite de rede** nos perfis de configuração de dispositivos. Utilize este perfil para definir os recursos online que pretende que sejam considerados como empresariais e fidedignos. Tem de definir um limite de rede para um dispositivo *antes* de as funcionalidades como o Windows Defender Application Guard e o Windows Information Protection poderem ser utilizadas no dispositivo. É importante definir apenas um limite de rede para cada dispositivo.

Pode definir os recursos do Enterprise Cloud, intervalos de endereços IP e servidores proxy internos que pretende que sejam considerados fidedignos. Assim que o definir, o limite de rede pode ser utilizado por outras funcionalidades, tais como o Windows Defender Application Guard e o Windows Information Protection.

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Duas definições adicionais do Antivírus do Windows Defender <!-- 1338409 -->  
**Nível de bloqueio de ficheiros**

| | |
|---|---|
| Não Configurado | A definição **Não Configurado** utiliza o nível de bloqueio predefinido do Antivírus do Windows Defender e oferece um sistema de deteção avançado sem aumentar o risco de detetar ficheiros legítimos. |
| Alto | A opção**Alto** aplica um nível de deteção elevado.
| Alto +  | A opção **Alto +** proporciona o nível de deteção Alto com medidas adicionais de proteção que podem afetar o desempenho do cliente.
| Tolerância zero  | A opção **Tolerância zero** bloqueia todos os executáveis desconhecidos. |

Embora seja pouco provável, mudar para o nível **Alto** pode fazer com que alguns ficheiros legítimos sejam detetados.
Recomendamos que mude o Nível de bloqueio de ficheiros para o valor predefinido **Não configurado**.

**Prolongamento do tempo limite para a análise de ficheiros pela cloud**  

| | |
|--|--|
| Número de segundos (0-50) | Especifique o período de tempo máximo em que o Antivírus do Windows Defender deve bloquear um ficheiro enquanto aguarda por um resultado da cloud. O período predefinido é de 10 segundos: o tempo adicional que for especificado aqui (até um máximo de 50 segundos) será adicionado a esses 10 segundos. Na maioria dos casos, a pesquisa demora muito menos tempo do que o tempo máximo permitido. Alargar o período de tempo permite que a cloud investigue ficheiros suspeitos de forma mais minuciosa. Recomendamos que ative esta definição e especifique, no mínimo, um aumento de 20 segundos adicionais. |

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Adição da VPN do Citrix para dispositivos Windows 10 <!-- 1512457 -->  
Pode configurar a VPN do Citrix nos respetivos dispositivos Windows 10. Pode selecionar a VPN do Citrix na lista *Selecione um tipo de ligação* no painel **VPN Base** ao configurar uma VPN para o Windows 10 e posterior.

> [!Note]
> A configuração do Citrix existia para os sistemas iOS e Android.

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>As ligações Wi-Fi suportam chaves pré-partilhadas no iOS <!-- 1550823 -->
Os clientes podem configurar perfis de Wi-Fi para utilizar chaves pré-partilhadas (PSK) para ligações Pessoais WPA/WPA2 em dispositivos iOS. Estes perfis são enviados via push para o dispositivo do utilizador quando o dispositivo está inscrito no Intune.

Quando o perfil tiver sido enviado para o dispositivo, o passo seguinte depende da configuração do perfil.  Se estiver definido para ligar automaticamente, assim o faz quando a rede se tornar necessária.  Quando o perfil está definido para ligar manualmente, o utilizador tem de ativar a ligação manualmente.  

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Acesso a registos de aplicações geridas para iOS <!-- 1469920 -->
Agora, os utilizadores finais com o Managed Browser instalado podem ver o estado da gestão de todas as aplicações publicadas da Microsoft e enviar registos para resolver os problemas das respetivas aplicações iOS geridas.

Para saber como ativar o modo de resolução de problemas num Managed Browser num dispositivo iOS, veja [How to access to managed app logs using the Managed Browser on iOS (Como aceder a registos de aplicações geridas com o Managed Browser no iOS)](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Melhorias no fluxo de trabalho da configuração de dispositivos no Portal da Empresa para iOS na versão 2.9.0 <!-- 1417174 -->

O fluxo de trabalho da configuração de dispositivos foi melhorado na aplicação Portal da Empresa para iOS. O tipo de linguagem é mais simples. Além disso, combinámos os ecrãs sempre que possível. A linguagem é agora mais adaptada à sua empresa, ao utilizar o nome da sua empresa no texto de configuração. Pode ver este fluxo de trabalho atualizado em  [novidades na página da IU para aplicações](whats-new-app-ui.md).

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>A entidade User contém dados de utilizador no modelo de dados do Armazém de Dados <!-- 1544273 -->
A primeira versão do modelo de dados do Armazém de Dados do Intune continha apenas dados de histórico recentes do Intune. Os criadores de relatórios não conseguiam capturar o estado atual de um utilizador. Nesta atualização, a **entidade User** é preenchida com os dados de utilizador mais recentes.


## <a name="notices"></a>Avisos


### <a name="coming-soon-workflow-updates-to-intune-administration-ui"></a>Brevemente: atualizações do fluxo de trabalho à IU da Administração do Intune

O Intune está a atualizar a experiência de administração na versão de serviço de março. Não precisa de tomar medidas, mas queríamos que tivesse conhecimento deste facto, de acordo com o compromisso da Microsoft para com a transparência. Quando a gestão de dispositivos Android ou Apple está ativada, o Intune envia informações de dispositivos e utilizadores para serem integradas com estes serviços de terceiros para gerirem os respetivos dispositivos. A experiência da IU de administração melhorada que iremos introduzir na versão de serviço de março fornecerá mais transparência relativamente aos dados que são partilhados. Estas alterações à IU não afetarão o utilizador final.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?

Os cenários que irão acrescentar uma janela de consentimento para partilhar dados incluem:
- Ao ativar o Android for Work 
- Ao ativar e carregar certificados Push de MDM da Apple 
- Ao ativar qualquer dos serviços da Apple, tal como o Programa de Registo de Aparelho, o School Manager e o Programa de Compras em Volume

Em cada caso, o consentimento está estritamente relacionado com a execução de um serviço de gestão de dispositivos móveis, tal como confirmar que um Administrador de TI autorizou a inscrição de dispositivos Google ou Apple. Está disponível aqui documentação que aborda que informações serão partilhadas quando o novo fluxo de trabalho for disponibilizado:
- [Dados que o Intune envia para a Google](data-intune-sends-to-google.md)
- [Dados que o Intune envia para a Apple](data-intune-sends-to-apple.md)

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?

Não tem de realizar nenhuma preparação para esta mudança, visto que são pequenas atualizações à IU do fluxo de trabalho. Para obter mais informações sobre a conformidade com o GDPR por parte da Microsoft, aceda ao Centro de Confiança, que é acessível a partir da ligação Informações Adicionais.



### <a name="plan-for-change-update-where-you-configure-your-app-protection-policies"></a>Planear a Alteração: Atualização do Local de Configuração das Políticas da Proteção de Aplicações

A partir de março de 2018, iremos redirecioná-lo temporariamente do painel do serviço Proteção de Aplicações do Intune no portal do Azure para o painel Aplicação móvel no Intune no portal do Azure. Tenha em atenção que todas as suas políticas de proteção de aplicações já se encontram no painel Aplicação móvel no Intune, em Configuração de aplicações. Em vez de aceder à Proteção de Aplicações do Intune, acederá simplesmente ao Intune. Em abril, deixaremos de redirecionar e removeremos o painel do serviço Proteção de Aplicações do Intune por completo. É apenas uma repetição das opções incorporadas no Intune. 

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Esta alteração afetará os clientes autónomos e os clientes híbridos (Intune com o Configuration Manager) do Intune. Esta integração irá ajudar a simplificar a sua administração da gestão da cloud. Agora terá apenas um painel para aceder no Azure – o painel do Intune – para gerir grupos, políticas, aplicações e qualquer gestão de dispositivos móveis.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Adicione o Intune como um favorito em vez do painel do serviço Proteção de Aplicações do Intune e certifique-se de que está familiarizado com o fluxo de trabalho da Política de proteção de aplicações no painel Aplicação móvel no Intune. Iremos redirecionar os utilizadores durante um breve período de tempo e, em seguida, remover o painel Proteção de Aplicações. Tenha em conta que todas as políticas da Proteção de Aplicações já se encontram no Intune e pode modificar qualquer uma das suas políticas de acesso condicional ao seguir esta documentação: [https://aka.ms/azuread_ca](https://aka.ms/azuread_ca).

**Informações Adicionais**: [https://aka.ms/intuneapppolicy](https://aka.ms/intuneapppolicy)

### <a name="updated-new-security-enhancements-in-the-intune-service-----1637539---"></a>Atualização: novas melhorias de segurança no serviço do Intune  <!-- 1637539 -->   

Estamos a implementar melhorias de segurança no serviço do Intune. Como parte desta alteração, com a atualização de março ao serviço do Intune, estará disponível um botão na consola do Azure para ativar ou desativar esta funcionalidade de segurança. Quando a funcionalidade estiver ativada, os dispositivos sem política de conformidade atribuída serão marcados como "não conforme".

**Clientes híbridos**: não implementaremos esta alteração para clientes híbridos neste momento. Não terá de tomar nenhuma medida. Contudo, recomendamos que se certifique de que os seus dispositivos têm pelo menos uma política de conformidade atribuída.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?

Quando começarmos a implementar esta alteração na atualização de março, esta funcionalidade irá afetá-lo consoante já tenha políticas de conformidade atribuídas ou não.

- Se for um inquilino novo ou existente e não tiver políticas de conformidade atribuídas aos seus dispositivos, o botão estará automaticamente definido para **em conformidade**. A funcionalidade estará desativada por predefinição na consola. O utilizador final não será afetado.
- Se for um inquilino existente e tiver dispositivos com políticas de conformidade atribuídas, o botão estará automaticamente definido para "não conforme". A funcionalidade estará ativada por predefinição, quando a atualização de março for implementada. 

Se utilizar políticas de conformidade com Acesso Condicional (AC) e tiver a funcionalidade ativada, os dispositivos sem pelo menos uma política de conformidade atribuída serão bloqueados pela AC. Os utilizadores finais associados a estes dispositivos, que tinham anteriormente permissão de acesso ao e-mail, perderão o acesso a menos que atribua pelo menos uma política de conformidade a todos os dispositivos.   
 
#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?  

Se utiliza o Acesso Condicional, recomendamos que tenha esta funcionalidade ativada e que deixe o botão definido para **Não conforme**. Para evitar perder o acesso ao e-mail por parte dos seus utilizadores finais, certifique-se de que todos os seus dispositivos têm pelo menos uma política de conformidade atribuída. Eis algumas alterações que iremos fazer para o ajudar nesta tarefa:   

- Introduzimos um relatório denominado **Dispositivos sem política de conformidade** no portal do Intune, que pode utilizar para identificar todos os dispositivos no seu ambiente que não têm uma política de conformidade atribuída. 
- Existe uma opção **Todos os Utilizadores** para facilitar a atribuição de uma política de conformidade a todos os utilizadores.

Se optar por deixar o botão desativado, não é necessária mais nenhuma ação da sua parte.

**Informações Adicionais**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>Planear a Alteração: alteração no suporte do plug-in Cordova do SDK da Aplicação Microsoft Intune
O Intune irá descontinuar o suporte do [plug-in Cordova do SDK da Aplicação Microsoft Intune](app-sdk-cordova.md) no dia 1 de maio de 2018. Recomendamos que utilize a Ferramenta de Encapsulamento de Aplicações do Intune como alternativa para preparar as suas aplicações baseadas em Cordova para gestão e disponibilidade no Intune. Quando esta alteração entrar em vigor, o plug-in Cordova do SDK da Aplicação Microsoft Intune já não será gerido nem receberá atualizações. Os programadores de aplicações não poderão utilizar este plug-in. O Intune planeia continuar a suportar as aplicações criadas com Cordova. Contudo, as aplicações criadas com o plug-in Cordova do SDK da Aplicação Microsoft Intune terão as funcionalidades reduzidas no Intune. Após serem encapsuladas com a Ferramenta de Encapsulamento de Aplicações do Intune, as aplicações podem ser implementadas para os utilizadores finais como aconteceria normalmente. Para as aplicações Android baseadas em Cordova lançadas na Google Play Store:
- Serão pedidas credenciais aos utilizadores finais para receberem a política do Intune quando as aplicações forem iniciadas pela primeira vez.
- As aplicações deverão ser lançadas na loja de aplicações especificamente para os utilizadores do Intune, por exemplo "Aplicação Contoso para Intune". 

Para obter mais informações sobre a Ferramenta de Encapsulamento de Aplicações, veja [Ferramenta de Encapsulamento de Aplicações para iOS](app-wrapper-prepare-ios.md) e [Ferramenta de Encapsulamento de Aplicações para Android](app-wrapper-prepare-android.md). Caso tenha perguntas ou se depare com problemas, contacte [msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com). 

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Planear a Alteração: Utilizar agora o Intune no Azure para a sua gestão da MDM <!-- 1227338 -->
Há mais de um ano, anunciámos a [pré-visualização pública do Intune no Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) e, há seis meses, lançámos a [disponibilidade geral da nova experiência de administrador](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/) para o Intune. A partir de 31 de agosto de 2018, vamos desativar a gestão de dispositivos móveis (MDM) na consola Silverlight clássica para os clientes que utilizam o Intune autónomo. No seu lugar, pode utilizar o [Intune no Azure](https://aka.ms/Intune_on_Azure) para as suas necessidades de MDM. Se continua a utilizar a consola clássica para a MDM, pare e familiarize-se com o Intune no Azure. Não esperamos nenhum impacto no utilizador final com esta alteração. A gestão clássica do PC irá permanecer no Silverlight. Pode saber mais sobre esta alteração e como ela o afeta [aqui](https://aka.ms/Intune_on_Azure_mdm).


### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Gerir dispositivos Android for Work de forma independente dos dispositivos Android <!-- 1490731 EEready-->    
**Nota**: as seguintes alterações começarão a ser implementadas com a atualização de novembro, mas a execução na sua conta poderá demorar algum tempo. Receberá uma notificação de confirmação no portal do Office 365 quando estas alterações entrarem em vigor na sua conta. Após a implementação, terá opções de capacidade de gestão adicionais. Não existirão alterações à experiência do utilizador final durante a implementação.

O Intune suporta a gestão de inscrição de dispositivos Android for Work de forma independente da plataforma Android. Estas definições são geridas em **Inscrição de Dispositivos** > **Restrições de inscrição** > **Restrições de Tipos de Dispositivos**. (Estavam anteriormente localizadas em **Inscrição de Dispositivos** > **Inscrição do Android for Work** > **Definições de Inscrição do Android for Work**.)

Por predefinição, as definições dos dispositivos Android for Work serão as mesmas que as definições dos seus dispositivos Android. No entanto, depois de alterar as definições do Android for Work, este já não será o caso.

Se bloquear a inscrição pessoal do Android for Work, só será possível inscrever dispositivos Android empresariais como Android for Work.

Ao trabalhar com as novas definições, tenha em conta o seguinte:

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

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acesso direto aos cenários de inscrição da Apple <!--951869-->
Para as contas do Intune criadas depois de janeiro de 2017, o Intune ativou o acesso direto aos cenários de inscrição da Apple através da carga de trabalho Inscrever Dispositivos no portal do Azure. Anteriormente, a pré-visualização da inscrição da Apple apenas estava acessível a partir de ligações no portal do Intune clássico. As contas do Intune criadas antes de janeiro de 2017 precisam de uma única migração antes de estas funcionalidades ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder ao portal do Azure.

## <a name="whats-coming"></a>Novidades futuras

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>Atualização da experiência de utilizador da aplicação Portal da Empresa para iOS <!--1412866-->

Vamos lançar uma atualização importante da experiência de utilizador para a aplicação Portal da Empresa para iOS. A atualização consiste numa reestruturação visual completa, que inclui aspeto e funcionalidade mais modernos com usabilidade e acessibilidade melhoradas. Todas as funcionalidades atuais do Portal da Empresa para iOS serão mantidas.

Estamos a oferecer uma versão de pré-lançamento da aplicação Portal da Empresa para iOS atualizada através do programa TestFlight da Apple para que a utilize e forneça feedback. Inscreva-se em https://aka.ms/intune_ios_cp_testflight para obter acesso ao TestFlight.

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>A Apple passará a exigir atualizações para a Segurança de Transporte de Aplicações <!--748318-->
A Apple anunciou que irá impor requisitos específicos para a Segurança de Transporte de Aplicações (ATS). A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Esta alteração irá afetar os clientes do Intune que utilizam as aplicações do Portal da Empresa para iOS.

Disponibilizamos uma versão da aplicação do Portal da Empresa para iOS através do programa TestFlight da Apple que impõe os novos requisitos da ATS. Se gostaria de a experimentar para testar a sua conformidade com a ATS, envie um e-mail para <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app"> CompanyPortalBeta@microsoft.com </a> com o seu nome próprio, apelido, endereço de e-mail e o nome da empresa. Consulte o nosso [blogue de suporte do Intune](https://aka.ms/compportalats) para obter mais detalhes.

## <a name="see-also"></a>Consulte também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novidades na IU do Portal da Empresa](whats-new-app-ui.md)
* [Novidades nos meses anteriores](whats-new-archive.md)
