---
title: "Edição antecipada"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d4bcabc4d1af4554a3e3bea875be45f9376b4ef7
ms.sourcegitcommit: b982f9d50da4f958fb0c48c56ba46c8ef71500c4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2018
---
# <a name="the-early-edition-for-microsoft-intune---february-2018"></a>Edição antecipada do Microsoft Intune – fevereiro de 2018

A **edição antecipada** oferece uma lista de funcionalidades disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida numa base limitada e está sujeita a alterações. Não partilhe estas informações fora da sua empresa. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu contacto do grupo de produtos da Microsoft se tiver dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

> [!Note]
>As seguintes alterações estão em desenvolvimento para o Intune. Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->

## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure


<!-- 1802 start -->


### <a name="app-protection-policies-----679615---"></a>Políticas de Proteção de Aplicações <!-- 679615 -->
As Políticas de Proteção de Aplicações do Intune permitirão criar políticas predefinidas globais para ativar rapidamente a proteção em todos os utilizadores em todo o inquilino.

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Suporte do Intune para várias contas do DEP da Apple/Apple School Manager <!-- 747685 -->

O Intune suportará a inscrição de dispositivos de um máximo de 100 contas diferentes do Programa de Inscrição de Dispositivos (DEP) da Apple ou do Apple School Manager. Cada token carregado pode ser gerido separadamente para dispositivos e perfis de inscrição. Um perfil de inscrição diferente pode ser automaticamente atribuído por token do DEP/School Manager carregado. Se forem carregados vários tokens do School Manager, só um poderá ser partilhado com a School Data Sync da Microsoft de cada vez.

Após a migração, as Graph APIs beta e os scripts publicados para gerir o DEP da Apple ou o ASM através do Graph deixarão de funcionar. Estão em desenvolvimento novas Graph APIs beta e serão lançadas após a migração.

### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Relatórios de estado da ameaça e estado de funcionamento do Windows Defender <!--854704 -->

Compreender o funcionamento e o estado do Windows Defender é fundamental para gerir PCs Windows.  O Intune adicionará novos relatórios e ações ao estado e funcionamento do agente do Windows Defender. Ao utilizar um relatório de agregação de estados na carga de trabalho Conformidade do Dispositivo, poderá ver que dispositivos precisam do seguinte:

- atualização de assinatura
- reinício
- intervenção manual
- análise completa
- outros estados de agente a precisar de intervenção

Em alguns casos, podem ser tomadas outras medidas de remediação remotamente, como acionar uma atualização de assinatura.  O relatório também indica o número de PCs que estão registados como **Limpar**.

Um relatório de agregação para cada categoria de estado indica os PCs individuais que precisam de atenção ou os que estão registados como **Limpar**.

### <a name="protocol-exceptions-for-applications---1035509-eeready--"></a>Exceções de protocolo para aplicações <!--1035509 eeready-->

Poderá criar exceções à política de transferência de dados da Gestão de Aplicações Móveis do Intune (MAM) para abrir determinadas aplicações não geridas. Estas aplicações têm de ser consideradas fidedignas pelas TI. Além das exceções que criar, a transferência de dados será restrita a aplicações geridas pelo Intune quando a sua política de transferência de dados estiver definida para **apenas aplicações geridas**. Pode criar as restrições ao utilizar protocolos (iOS) ou pacotes (Android).

Por exemplo, pode adicionar o pacote WebEx como uma exceção à política de transferência de dados da MAM. Isto permite que as ligações WebEx numa mensagem de e-mail do Outlook gerido sejam abertas diretamente na aplicação WebEx. A transferência de dados será restrita noutras aplicações não geridas.

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561-eeready--"></a>Personalizar os seus temas do Portal da Empresa com códigos hexadecimais <!--1049561 eeready-->

Poderá personalizar a cor do tema nas aplicações do Portal da Empresa com códigos hexadecimais. Ao introduzir o seu código hexadecimal, o Intune irá determinar a cor do texto que fornece o maior nível de contraste entre a cor do texto e a cor de fundo segundo os [padrões do WCAG 2.0](http://www.w3.org/TR/WCAG20). Pode pré-visualizar a cor do texto e o logótipo da empresa relativamente à cor em **Aplicações móveis** > **Portal da Empresa**. 

### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963---"></a>Selecionar as categorias de dispositivos através das definições de Acesso Profissional ou Escolar<!-- 1058963 --> 
Se tiver ativado o [mapeamento do grupo de dispositivos](https://docs.microsoft.com/en-us/intune/device-group-mapping), será pedido aos utilizadores no Windows 10 que selecionem uma categoria de dispositivos após a inscrição através do botão **Ligar** em **Definições** > **Contas** > **Acesso profissional ou escolar** ou durante a configuração inicial.

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>Novas definições do Windows Defender Credential Guard foram adicionadas às definições de proteção de ponto final <!--1102252 --> 

As novas definições do [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) serão adicionadas a **Configuração de dispositivos** > **Perfis** > **Proteção de ponto final**. Serão adicionadas as seguintes definições: 

- Nível de Segurança da Plataforma: especifique se o Nível de Segurança da Plataforma está ativado no próximo reinício. A segurança baseada em virtualização necessita do Arranque Seguro. Opcionalmente, a segurança baseada em virtualização pode ser ativada com a utilização de proteções de acesso direto à memória (DMA). As proteções de DMA necessitam de suporte de hardware e serão ativadas apenas em dispositivos configurados corretamente.
- Segurança Baseada em Virtualização: especifique se a segurança baseada em virtualização está ativada no próximo reinício. 
- Windows Defender Credential Guard: ative o Credential Guard com a segurança baseada em virtualização para ajudar a proteger as credenciais no próximo reinício quando o Nível de Segurança da Plataforma com o Arranque Seguro e a Segurança Baseada em Virtualização estiverem ativados. As opções disponíveis incluem **Desativada**, **Ativada com bloqueio UEFI**, **Ativada sem bloqueio** e **Não configurado**. 
  - A opção "Desativada" desativa o Credential Guard remotamente se este tiver sido ativado antes através da opção "Ativada sem bloqueio".

  - A opção "Ativada com bloqueio UEFI" garante que o Credential Guard não pode ser desativado com a chave de registo ou através da utilização da Política de Grupo. Para desativar o Credential Guard após a utilização desta definição, terá de definir a Política de Grupo para "Desativada" e remover a funcionalidade de segurança de cada computador, com um utilizador fisicamente presente, para limpar a configuração persistente na UEFI. Enquanto a configuração da UEFI persistir, o Credential Guard estará ativado.

  - A opção "Ativada sem bloqueio" permite que o Credential Guard seja desativado remotamente através da utilização da Política de Grupo. Os dispositivos que utilizam esta definição têm de ter, pelo menos, o Windows 10 (Versão 1511).

  - A opção "Não Configurado" deixa a definição de política indefinida. A Política de Grupo não escreve a definição de política no registo, pelo que não tem qualquer impacto nos computadores ou utilizadores. Se existir uma definição atual no registo, não será modificada.

### <a name="synchronize-and-deploy-sparsely-bundled-windows-store-for-business-apps---1222672---"></a>Sincronizar e implementar aplicações agregadas dispersamente da Microsoft Store para Empresas <!--1222672 -->
As aplicações offline compradas a partir da Microsoft Store para Empresas serão sincronizadas com o portal do Intune. Poderá então implementar essas aplicações em grupos de dispositivos ou grupos de utilizadores. As aplicações offline são instaladas pelo Intune e não pela loja.

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Repor palavras-passe de dispositivos Android O <!-- 1238299 -->
Poderá repor as palavras-passe de dispositivos Android O inscritos. Quando envia um pedido "Repor palavra-passe" para um dispositivo Android O, este define uma nova palavra-passe de desbloqueio de dispositivo ou um desafio de perfil gerido para o utilizador atual. A palavra-passe ou o desafio é enviado consoante o dispositivo tiver um proprietário de perfil ou proprietário de dispositivo e entra em vigor imediatamente.

### <a name="local-device-security-option-settings----1251887---"></a>Definições da opção de segurança do dispositivo local <!-- 1251887 -->
Poderá ativar definições de segurança em dispositivos Windows 10 com as novas definições da Opção de Segurança do Dispositivo Local. Estas definições encontram-se na categoria Endpoint Protection durante a criação de uma política de configuração de dispositivo Windows 10.

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Novas definições de impressora para perfis de educação <!-- 1308900 -->

Para os perfis de educação, as novas definições estarão disponíveis na categoria **Impressoras**: **Impressoras**, **Impressora predefinida**, **Adicionar novas impressoras**. 

### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Novas definições de privacidade para restrições do dispositivo <!--1308926 -->

Estarão disponíveis duas novas definições de privacidade para os dispositivos:

- **Publicar as atividades do utilizador**: defina esta opção para **Bloquear** para impedir que as experiências e a deteção de recursos utilizados recentemente sejam partilhadas no comutador de tarefas.

- **Apenas atividades locais**: defina esta opção para **Bloquear** para impedir que as experiências e a deteção de recursos utilizados recentemente sejam partilhadas no comutador de tarefas com base na atividade local.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Suporte do Portal da Empresa do macOS para inscrições que utilizam o Gestor de Inscrições de Dispositivos <!-- 1352411 -->

Os utilizadores poderão utilizar o Gestor de Inscrições de Dispositivos ao efetuar inscrições com o Portal da Empresa do macOS.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Novas definições no browser Edge <!--1469166 -->

Estarão disponíveis duas novas definições para dispositivos com o browser Edge: **Caminho para o ficheiro de favoritos** e **Alterações aos Favoritos**. 

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Dados encriptados da Windows Information Protection (WIP) nos resultados da pesquisa do Windows<!-- 1469193 -->

Uma nova definição na política da Windows Information Protection (WIP) vai permitir-lhe controlar se os dados encriptados da WIP estão incluídos nos resultados da pesquisa do Windows.

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Suporte de aplicações de linha de negócio (LOB) para macOS <!-- 1473977 -->
O Intune irá oferecer a possibilidade de instalar aplicações LOB no macOS. As aplicações LOB são aplicações em que pode fornecer o ficheiro de instalação e utilizar o Intune para instalar a aplicação no dispositivo. Como parte do suporte de aplicações LOB para macOS, tem de utilizar a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para macOS para processar previamente as aplicações de linha de negócio (LOB) para macOS.

### <a name="configure-resource-account-settings-for-surface-hubs----1475674---"></a>Configurar definições de contas de recurso para Surface Hubs <!-- 1475674 -->

Poderá configurar remotamente definições de contas de recurso para Surface Hubs.

A conta de recurso é utilizada por um Surface Hub para efetuar a autenticação com o Skype/Exchange para que possa participar numa reunião. Poderá querer criar uma conta de recurso exclusiva para que o Surface Hub seja apresentado na reunião como a sala de conferência. Por exemplo, uma conta de recurso como **Sala de Conferência B41/6233**.

> [!NOTE]
> - Se deixar campos em branco, irá substituir atributos configurados anteriormente no dispositivo.
>
> - As propriedades da Conta de Recurso podem ser alteradas de forma dinâmica no Surface Hub. Por exemplo, caso a rotação da palavra-passe esteja ativada. Por isso, é possível que os valores na consola do Azure demorem algum tempo a refletir a realidade no dispositivo. 
>
>   Para perceber o que está configurado atualmente no Surface Hub, as informações da Conta de Recurso podem ser incluídas no inventário de hardware (que já tem um intervalo de 7 dias) ou como propriedades só de leitura. Para melhorar a precisão após ser efetuada uma ação remota, pode obter o estado dos parâmetros imediatamente após a execução da ação para atualizar a conta/os parâmetros no Surface Hub.

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

### <a name="see-enrollment-restrictions-per-user----1634444---"></a>Ver restrições de inscrição por utilizador <!-- 1634444 -->
No painel Resolução de Problemas, poderá ver as restrições de inscrição que estão em vigor para cada utilizador.

### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Configurar uma aplicação móvel MSI de atualização automática <!-- 1740840 -->
Poderá configurar uma aplicação móvel MSI de atualização automática para ignorar o processo de verificação da versão. Esta funcionalidade é útil para evitar que ocorra uma condição race. Por exemplo, isto pode ocorrer quando uma aplicação está a ser atualizada automaticamente pelo programador de aplicações e pelo Intune ao mesmo tempo. Ambos podem tentar impor uma versão da aplicação no cliente do Windows, o que pode criar um conflito.

### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133---"></a>Adições às definições de políticas de conformidade da Segurança do Sistema do Windows 10 e posterior <!--1704133 -->

Estarão disponíveis adições às definições de conformidade do Windows 10, incluindo a exigência de Firewall e Antivírus do Windows Defender.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Incluir e excluir a atribuição de aplicações com base nos grupos do Android Enterprise <!-- 1813081 -->
Durante a atribuição de aplicações e após selecionar um tipo de atribuição, o Android Enterprise (anteriormente conhecido como Android for Work) irá suportar a funcionalidade de exclusão.


### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Conjuntos relacionados de licenças de aplicações suportadas no Intune <!-- 1864117 -->
O Intune no portal do Azure irá suportar conjuntos relacionados de licenças de aplicações suportadas como um único item de aplicação na IU. Além disso, todas as aplicações com Licença Offline sincronizadas a partir da Microsoft Store para Empresas serão consolidadas numa única entrada de aplicação e todos os detalhes de implementação dos pacotes individuais serão migrados para uma única entrada. Para ver conjuntos relacionados de licenças de aplicações no portal do Azure, selecione **Licenças de aplicações** no painel **Aplicações móveis**.

<!-- the following are present prior to 1802 -->

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>Nova opção para a autenticação do utilizador na inscrição em massa da Apple<!-- 747625 -->
O Intune dar-lhe-á a opção para autenticar dispositivos através da aplicação Portal da Empresa para os seguintes métodos de inscrição:

- Programa de Inscrição de Dispositivos da Apple
- Gestor Escolar da Apple
- Inscrição no Apple Configurator

Ao utilizar a opção do Portal da Empresa, a autenticação multifator do Azure Active Directory pode ser imposta sem bloquear estes métodos de inscrição.

Quando utilizar a opção do Portal da empresa, o Intune ignora a autenticação do utilizador no Assistente de Configuração iOS para a inscrição de afinidade do utilizador. Tal significa que o dispositivo está inscrito inicialmente como um dispositivo sem utilizador e, como tal, não receberá configurações ou políticas de grupos de utilizadores. Receberá apenas configurações e políticas para grupos de dispositivos. No entanto, o Intune instalará automaticamente a aplicação Portal da Empresa no Dispositivo. O primeiro utilizador a abrir e a iniciar sessão na aplicação Portal da Empresa será associado ao dispositivo no Intune. Neste momento, o utilizador receberá configurações e políticas dos grupos de utilizadores. A associação do utilizador não pode ser alterada sem a reinscrição.

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Suporte do Intune para várias contas do DEP da Apple/Apple School Manager <!-- 747685 -->
O Intune suportará a inscrição de dispositivos de um máximo de 100 contas diferentes do Programa de Inscrição de Dispositivos (DEP) da Apple ou do Apple School Manager. Cada token carregado pode ser gerido separadamente para dispositivos e perfis de inscrição. Um perfil de inscrição diferente pode ser automaticamente atribuído por token do DEP/School Manager carregado. Se forem carregados vários tokens do School Manager, só um poderá ser partilhado com a School Data Sync da Microsoft de cada vez.

Após a migração, as Graph APIs beta e os scripts publicados para gerir o DEP da Apple ou o ASM através do Graph deixarão de funcionar. Estão em desenvolvimento novas Graph APIs beta e serão lançadas após a migração.

### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963---"></a>Selecionar as categorias de dispositivos através das definições de Acesso Profissional ou Escolar<!-- 1058963 -->
Se tiver ativado o [mapeamento do grupo de dispositivos](https://docs.microsoft.com/en-us/intune/device-group-mapping), será pedido aos utilizadores no Windows 10 que selecionem uma categoria de dispositivos após a inscrição através do botão **Ligar** em **Definições** > **Contas** > **Acesso profissional ou escolar** ou durante a configuração inicial.

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Filtrar políticas de conformidade em dispositivos nos grupos de dispositivos <!--1307012 -->

Será capaz de filtrar políticas de conformidade de destino para os utilizadores nos grupos de utilizadores. Será capaz de filtrar políticas de conformidade para os dispositivos nos grupos de dispositivos.

### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Incluir e excluir a atribuição de aplicações com base nos grupos <!-- 1406920 -->

Durante a atribuição de aplicações e, depois de selecionar um tipo de atribuição, poderá selecionar os grupos a incluir, bem como os grupos a excluir.

### <a name="remote-erase-command-support----1438084---"></a>Suporte do comando “Apagar” remoto <!-- 1438084 -->

Os administradores poderão emitir um comando Apagar remotamente.

> [!IMPORTANT]
> O comando apagar não pode ser invertido e deve ser utilizado com cuidado.

O comando apagar remove todos os dados, incluindo o sistema operativo, de um dispositivo. Esta operação também remove o dispositivo da gestão do Intune. Nenhum aviso é apresentado ao utilizador e a eliminação ocorre imediatamente após a emissão do comando.

Poderá configurar um PIN de recuperação de 6 dígitos. Este PIN pode servir para desbloquear o dispositivo apagado, altura em que irá iniciar a reinstalação do sistema operativo. Depois de a eliminação começar, o PIN é apresentado numa barra de estado no painel de descrição geral do dispositivo no Intune. O PIN será mantido enquanto a eliminação estiver em curso. Depois de concluída a eliminação, o dispositivo desaparece totalmente da gestão do Intune. Não se esqueça de registar o PIN de recuperação para que quem estiver a restaurar o dispositivo o possa utilizar.

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Dados encriptados da Windows Information Protection (WIP) nos resultados da pesquisa do Windows<!-- 1469193 -->

Uma nova definição na política da Windows Information Protection (WIP) vai permitir-lhe controlar se os dados encriptados da WIP estão incluídos nos resultados da pesquisa do Windows.

### <a name="website-learning-mode----1631908---"></a>Modo de Aprendizagem do Site<!-- 1631908 -->

O Intune vai introduzir uma extensão do Modo de aprendizagem da Windows Information Protection (WIP). Além de ver informações sobre as aplicações com a WIP, poderá ver um resumo dos dispositivos que partilharam dados de trabalho com os sites. Com estas informações, pode determinar os sites que devem ser adicionados às políticas WIP dos grupos e dos utilizadores.

### <a name="updates-to-compliance-emails---1637547---"></a>Atualizações em e-mails de conformidade <!--1637547 -->

Quando um e-mail é enviado para comunicar um dispositivo não conforme, serão incluídos detalhes sobre o dispositivo não conforme. O seguinte artigo será atualizado para indicar este facto: [ações automáticas de não conformidade](#actions-for-noncompliance).

###  <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Alertas para tokens expirados e tokens que irão expirar em breve <!-- 1639263 -->
A página de descrição geral mostrará alertas para tokens expirados e tokens que irão expirar em breve. Ao clicar num alerta com um único token, acederá à página de detalhes do token.  Se clicar num alerta com vários tokens, acederá a uma lista de todos os tokens com o estado deles. Os administradores devem renovar os tokens antes da data de expiração.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Impressão remota através de uma rede segura <!-- 1709994  -->
As soluções de impressão móveis sem fios da PrinterOn irão permitir aos utilizadores imprimir remotamente a partir de qualquer lugar e em qualquer altura através de uma rede segura. A PrinterOn será integrada com o SDK da Aplicação Intune para iOS e Android. Conseguirá filtrar políticas de proteção de aplicações para esta aplicação através do painel **Políticas de proteção de aplicações** do Intune na consola de administração. Os utilizadores finais conseguirão transferir a aplicação “PrinterOn para Microsoft” através da Play Store ou do iTunes para utilizar no seu ecossistema do Intune.

### <a name="approve-the-company-portal-app-for-android-for-work---1797090---"></a>Aprovar a aplicação do Portal da Empresa para o Android for Work <!--1797090 -->
Se a sua organização utilizar o Android for Work, terá de aprovar manualmente a aplicação Portal da Empresa para Android para continuar a receber atualizações automáticas da Google Play Store gerida.

### <a name="faceid-on-ios-devices----1807377---"></a>Face ID nos dispositivos iOS <!-- 1807377 -->
As políticas de proteção de aplicações do Intune suportam agora uma definição que controla o Face ID nos dispositivos iOS. Esta definição destina-se a dispositivos que suportam a funcionalidade Face ID (atualmente apenas no iPhone X). Esta definição está separada dos controlos do Touch ID atualmente suportados. As organizações têm a capacidade de escolher se vão confiar no Face ID como um pedido de PIN válido e como uma alternativa aos controlos do Touch ID.

### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>Microsoft Graph API para o Intune – Disponibilidade Geral <!-- 1833289 -->
As APIs do Intune no Microsoft Graph irão conceder acesso programático aos dados e aos métodos para automatizar as ações administrativas do serviço do Intune.  Com a **Disponibilidade Geral** destas APIs, os clientes, os parceiros e os programadores conseguirão tirar partido das APIs para as integrar em soluções internas ou comerciais que exijam ou estejam relacionadas com o suporte do Intune ou outros serviços Microsoft disponíveis através do Microsoft Graph.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Políticas de Proteção de Aplicações <!-- 679615 -->
As Políticas de Proteção de Aplicações do Intune permitirão criar políticas predefinidas globais para ativar rapidamente a proteção em todos os utilizadores em todo o inquilino.

### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Revogar aplicações Programa Comprado em Volume para iOS <!-- 820863 -->
Para um determinado dispositivo que tenha uma ou mais aplicações Programa Comprado em Volume (VPP) para iOS, será capaz de revogar a licença de aplicação baseada em dispositivos associados do dispositivo. Revogar a licença de uma aplicação não desinstala a aplicação VPP relacionada do dispositivo. Para desinstalar uma aplicação VPP, tem de alterar a ação de atribuição para **Desinstalar**. Para obter mais informações, veja [Como gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune](vpp-apps-ios.md).

### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Revogar licenças para um token de Programa Comprado em Volume para iOS<!-- 820870 -->
Será capaz de revogar a licença de todas as aplicações Programa Comprado em Volume (VPP) para iOS para um determinado Token VPP.

### <a name="new-ios-device-action------1244701---"></a>Nova ação do dispositivo iOS <!-- 1244701 -->
Pode encerrar os dispositivos iOS 10.3 supervisionados. Esta ação encerra o dispositivo imediatamente sem avisar o utilizador final. A ação **Encerrar (apenas os supervisionados)** encontra-se nas propriedades do dispositivo ao selecionar um dispositivo na carga de trabalho **Dispositivo**.

### <a name="intune-provides-the-account-move-operation-----1573558-1579830---"></a>O Intune disponibiliza a operação Mover Conta <!-- 1573558, 1579830 -->
A operação **Mover Conta** migra um inquilino de uma Unidade de Escala do Azure (ASU) para outra. A operação **Mover Conta** pode ser utilizada para os cenários iniciados pelo cliente, quando telefona para a equipa de suporte do Intune para a pedir, e também pode ser um cenário impulsionado pela Microsoft onde a Microsoft tem de fazer ajustes ao serviço no back-end. Durante a operação **Mover Conta**, o inquilino entra no modo só de leitura (ROM). As operações do serviço, como inscrever, mudar o nome de dispositivos e atualizar o estado de conformidade, falharão durante o período do ROM.



<!-- the following are present prior to 1712 -->
### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Atribuir aplicações móveis do Office 365 a dispositivos iOS e Android ao utilizar o tipo de aplicação incorporada <!-- 1332318 -->
O tipo de aplicação **Incorporada** permite-lhe criar e atribuir aplicações do Office 365 mais facilmente aos dispositivos iOS e Android que está a gerir. Estas aplicações incluem aplicações do O365, tais como o Word, Excel, PowerPoint e OneDrive. Pode atribuir aplicações específicas ao tipo de aplicação e editar a configuração de informações da aplicação.

### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>A resolução de conflitos de atribuição mudou para as aplicações da loja iOS <!-- 1480316 -->
Os utilizadores finais poderão reparar numa alteração quanto à disponibilidade das aplicações da loja iOS. Atualmente, uma aplicação que tenha sido atribuída a dois grupos com um conflito entre **Necessário e Disponível** e **Não Aplicável** é resolvida para **Necessário e Disponível**. Com a alteração, uma aplicação com este conflito é resolvida para **Não Aplicável**.

A alteração diz respeito à confusão gerada quando uma aplicação é atribuída a múltiplos grupos com intenções diferentes no que diz respeito às aplicações.

Se pretender ter a sua aplicação disponível no Portal dos Técnicos de Informação e no Portal da Empresa antes do lançamento do serviço em novembro, tem duas opções:

1. Remova a atribuição **Não Aplicável** do seu grupo.
2. Crie um novo grupo que não inclua os membros com a intenção **Necessário e Disponível** atribuída e atribua a intenção **Não Aplicável** a esse grupo.

Para obter mais informações, veja [Como atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md).

> [!Note]
> Após o lançamento, deixará de poder ver ou modificar as atribuições de aplicação da Gestão de Dispositivos Móveis (MDM) na consola clássica do Intune. No entanto, pode utilizar a consola do Azure ou a Graph API do Intune para fazer as suas atribuições de aplicações.

### <a name="configure-an-ios-app-pin----1586774---"></a>Configurar um PIN da aplicação para iOS <!-- 1586774 -->
Em breve poderá exigir um PIN para aplicações específicas para iOS. Pode configurar a data de expiração em dias e a obrigatoriedade de introdução de PIN através do portal do Azure. Quando for necessário, um utilizador terá de definir e utilizar um PIN novo para ter acesso a uma aplicação iOS. Apenas as aplicações iOS que têm ativada a proteção de aplicações com o SDK da Aplicação Intune suportarão esta funcionalidade.

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>Atualização da experiência de utilizador da aplicação Portal da Empresa para iOS <!--1412866-->

Vamos lançar uma atualização importante da experiência de utilizador para a aplicação Portal da Empresa para iOS. A atualização consiste numa reestruturação visual completa, que inclui aspeto e funcionalidade mais modernos com usabilidade e acessibilidade melhoradas. Todas as funcionalidades atuais do Portal da Empresa para iOS serão mantidas.

Estamos a oferecer uma versão de pré-lançamento da aplicação Portal da Empresa para iOS atualizada através do programa TestFlight da Apple para que a utilize e forneça feedback. Inscreva-se em https://aka.ms/intune_ios_cp_testflight para obter acesso ao TestFlight. 

![imagens de amostra da nova aplicação portal da empresa para iOS](./media/ios-cp-app-redesign-1801-teaser.png)

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Os sites do Azure Active Directory podem exigir a aplicação Intune Managed Browser e o suporte do Início de Sessão Único do Managed Browser (Pré-visualização Pública) <!-- 710595 -->   
Com o Azure Active Directory (Azure AD), poderá restringir o acesso a sites em dispositivos móveis na aplicação Intune Managed Browser. No Managed Browser, os dados dos sites permanecerão protegidos e separados dos dados pessoais dos utilizadores finais. Além disso, o Managed Browser suporta as funcionalidades de Início de Sessão Único para sites protegidos pelo Azure AD. Iniciar sessão no Managed Browser ou utilizá-lo num dispositivo com outra aplicação gerida pelo Intune permite que o Managed Browser aceda a sites empresariais protegidos pelo Azure AD sem que o utilizador tenha de introduzir as suas credenciais. Esta funcionalidade aplica-se a sites como o Outlook Web Access (OWA) e o SharePoint Online, bem como a outros sites empresariais como recursos de intranet acedidos através do Proxy de Aplicações do Azure.

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Redirecionar utilizadores do macOS para a nova aplicação Portal da Empresa <!--1380728-->   
Quando um utilizador final inicia sessão no site do Portal da Empresa para inscrever o seu dispositivo macOS, este será direcionado para transferir a nova aplicação Portal da Empresa para macOS para concluir o processo. Isto ocorre nos dispositivos macOS que utilizam o OS X El Capitan 10.11 ou posterior. 


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Suporte do Intune Managed Browser para iOS e Android <!-- 1374196 -->
A partir de outubro de 2017, a aplicação Intune Managed Browser no Android irá suportar apenas dispositivos a executar o Android 4.4 e posterior. A aplicação Intune Managed Browser no iOS irá suportar apenas dispositivos a executar o iOS 9.0 e posterior. As versões anteriores do Android e iOS poderão continuar a utilizar o Managed Browser, mas não poderão instalar novas versões da aplicação e poderão não conseguir aceder a todas as funcionalidades da aplicação. Aconselhamos que atualize estes dispositivos para uma versão do sistema operativo suportada.

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensagem de erro melhorada para quando um utilizador atinge o número máximo de dispositivos que é permitido inscrever <!-- 1270370 -->
Em vez de uma mensagem de erro genérica, os utilizadores finais com dispositivos Android verão uma mensagem de erro amigável acionável: “Inscreveu o número máximo de dispositivos permitidos pelo administrador de TI. Remova um dispositivo inscrito ou peça ajuda ao seu administrador de TI."



## <a name="notices"></a>Avisos

Neste momento, não existem avisos ativos.



### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.


