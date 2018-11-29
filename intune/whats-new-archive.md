---
title: Novidades nos meses anteriores do Microsoft Intune – Azure | Microsoft Docs
titlesuffix: ''
description: Veja os anúncios mais antigos na página Novidades do Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 09cd1177157897886631f804cd335ae78562a233
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182147"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Novidades do Microsoft Intune – meses anteriores

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="march-2018"></a>Março de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Alertas de aplicações de linha de negócio (LOB) prestes a expirar para o Microsoft Intune <!-- 748789 -->

No portal do Azure, o Intune irá alertá-lo para as aplicações de linha de negócio do iOS que estão prestes a expirar. Após o carregamento de uma nova versão da aplicação de linha de negócio do iOS, o Intune remove a notificação de expiração da lista de aplicações. Esta notificação de expiração só estará ativa para as aplicações de linha de negócio do iOS carregadas recentemente. Será apresentado um aviso 30 dias antes de o perfil de aprovisionamento de aplicações LOB do iOS expirar. Quando o perfil expirar, o estado do alerta será alterado para Expirado.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Personalizar os seus temas do Portal da Empresa com códigos hexadecimais <!--1049561 -->

Pode personalizar a cor do tema nas aplicações do Portal da Empresa com códigos hexadecimais. Ao introduzir o seu código hexadecimal, o Intune determina a cor do texto que fornece o maior nível de contraste entre a cor do texto e a cor de fundo. Pode pré-visualizar a cor do texto e o logótipo da empresa relativamente à cor em **Aplicações do cliente** > **Portal da Empresa**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Incluir e excluir a atribuição de aplicações com base nos grupos do Android Enterprise <!-- 1813081 -->

O Android Enterprise (anteriormente conhecido como Android for Work) suporta incluir e excluir grupos, mas não suporta os grupos incorporados **Todos os Utilizadores** e **Todos os Dispositivos** pré-criados. Para obter mais informações, veja [Incluir e excluir atribuições de aplicações no Microsoft Intune](apps-inc-exl-assignments.md).


### <a name="device-management"></a>Gestão de dispositivos

### <a name="export-all-devices-into-csv-files-in-ie-microsoft-edge-or-chrome----2258071---"></a>Exportar todos os dispositivos para ficheiros CSV no IE, Microsoft Edge ou Chrome <!-- 2258071 -->
Em **Dispositivos** > **Todos os dispositivos**, pode **Exportar** os dispositivos para uma lista com formatação CSV. Os utilizadores do Internet Explorer (IE) com mais de 10 000 dispositivos podem exportar os seus dispositivos com êxito para múltiplos ficheiros. Cada ficheiro contém um máximo de 10 000 dispositivos.

Os utilizadores do Microsoft Edge e Chrome com mais de 30 000 dispositivos podem exportar os seus dispositivos com êxito para múltiplos ficheiros. Cada ficheiro contém um máximo de 30 000 dispositivos.

O artigo [Gerir dispositivos](device-management.md) fornece mais detalhes sobre o que pode fazer com os dispositivos que gere.

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

Para obter mais informações sobre estes canais, veja [Manage Insider Preview Builds](https://insider.windows.com/for-business-organization-admin/) (Gerir Compilações do Insider Preview).   
Para obter mais informações sobre a criação de canais de implementação no Intune, veja [Gerir atualizações de software no Intune](windows-update-for-business-configure.md).

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

### <a name="intune-apps"></a>Aplicações do Intune

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Os sites do Azure Active Directory podem exigir a aplicação Intune Managed Browser e o suporte do Início de Sessão Único do Managed Browser (Pré-visualização Pública) <!-- 710595 -->

Com o Azure Active Directory (Azure AD), pode restringir o acesso a sites em dispositivos móveis na aplicação Intune Managed Browser. No Managed Browser, os dados dos sites permanecerão protegidos e separados dos dados pessoais dos utilizadores finais. Além disso, o Managed Browser suporta as funcionalidades de Início de Sessão Único para sites protegidos pelo Azure AD. Iniciar sessão no Managed Browser ou utilizá-lo num dispositivo com outra aplicação gerida pelo Intune permite que o Managed Browser aceda a sites empresariais protegidos pelo Azure AD sem que o utilizador tenha de introduzir as suas credenciais. Esta funcionalidade aplica-se a sites como o Outlook Web Access (OWA) e o SharePoint Online, bem como a outros sites empresariais como recursos de intranet acedidos através do Proxy de Aplicações do Azure. Para obter informações adicionais, veja [Access controls in Azure Active Directory conditional access](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls) (Controlos de acesso no acesso condicional do Azure Active Directory).

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Atualizações visuais da aplicação Portal da Empresa para Android <!--976944 -->

Atualizámos a aplicação Portal da Empresa para Android para seguir as diretrizes de [Conceção do Material](https://material.io/) do Android. Pode ver as imagens dos novos ícones no artigo [Novidades na IU da aplicação](whats-new-app-ui.md).

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>Registo no Portal da Empresa melhorado <!-- 1874230 eeready-->
Os utilizadores que inscreverem um dispositivo através do Portal da Empresa com a compilação 1703 e posteriores do Windows 10 poderão concluir o primeiro passo de inscrição sem sair da aplicação.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>O HoloLens e o SurfaceHub são agora apresentados em listas de dispositivos <!--1725868 -->
Incluímos suporte adicional para mostrar dispositivos HoloLens e SurfaceHub inscritos no Intune na aplicação Portal da Empresa para Android.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>Personalizar categorias de livros para eBooks do programa comprado em volume (VPP) <!-- 1488911 -->
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

## <a name="february-2018"></a>Fevereiro de 2018

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Suporte do Intune para várias contas do DEP da Apple/Apple School Manager <!-- 747685 -->

O Intune agora suporta a inscrição de dispositivos com até 100 contas diferentes do [Programa de Inscrição de Dispositivos (DEP) da Apple](device-enrollment-program-enroll-ios.md) ou do [Apple School Manager](apple-school-manager-set-up-ios.md). Cada token carregado pode ser gerido separadamente para dispositivos e perfis de inscrição. Um perfil de inscrição diferente pode ser automaticamente atribuído por token do DEP/School Manager carregado. Se forem carregados vários tokens do School Manager, só um poderá ser partilhado com a School Data Sync da Microsoft de cada vez.

Após a migração, as Graph APIs beta e os scripts publicados para gerir o DEP da Apple ou o ASM através do Graph deixarão de funcionar. Estão em desenvolvimento novas Graph APIs beta e serão lançadas após a migração.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Ver restrições de inscrição por utilizador <!-- 1634444 eeready wnready -->
No painel **Resolução de problemas**, pode agora ver as [restrições de inscrição](enrollment-restrictions-set.md) de cada utilizador ao selecionar **Restrições de inscrição** na lista **Atribuições**.

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

#### <a name="new-settings-for-the-microsoft-edge-browser---1469166---"></a>Novas definições no browser Microsoft Edge <!--1469166 -->
Estão agora disponíveis [duas novas definições](device-restrictions-windows-10.md#microsoft-edge-browser) de privacidade para os dispositivos com o browser Microsoft Edge: **Caminho para o ficheiro de favoritos** e **Alterações aos Favoritos**.

### <a name="app-management"></a>Gestão de aplicações

#### <a name="protocol-exceptions-for-applications---1035509---"></a>Exceções de protocolo para aplicações <!--1035509 -->

Agora pode criar exceções para a política de transferência de dados da Gestão de Aplicações Móveis (MAM) do Intune para abrir determinadas aplicações não geridas. Estas aplicações têm de ser consideradas fidedignas pelas TI. Além das exceções que criar, a transferência de dados ainda será restrita a aplicações geridas pelo Intune quando a sua política de transferência de dados estiver definida para **apenas aplicações geridas**. Pode criar as restrições ao utilizar protocolos (iOS) ou pacotes (Android).

Por exemplo, pode adicionar o pacote WebEx como uma exceção à política de transferência de dados da MAM. Isto permite que as ligações WebEx numa mensagem de e-mail do Outlook gerido sejam abertas diretamente na aplicação WebEx. A transferência de dados será restrita noutras aplicações não geridas. Para obter mais informações, veja [Data transfer policy exceptions for apps](app-protection-policies-exception.md) (Exceções da política de transferência de dados).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Dados encriptados da Windows Information Protection (WIP) nos resultados da pesquisa do Windows<!-- 1469193 -->
Uma definição na política do Windows Information Protection (WIP) agora permite-lhe controlar se os dados encriptados pelo WIP são incluídos nos resultados da pesquisa do Windows. Pode definir esta opção de política de proteção de aplicações ao selecionar **Permitir que o Indexador do Windows Search procure itens encriptados** nas **Definições avançadas** da política do Windows Information Protection. A política de proteção de aplicações tem de ser definida para a plataforma do *Windows 10* e a política de aplicação **Estado da inscrição** tem de ser definida para **Com inscrição**. Para obter mais informações, veja [Permitir que o Indexador do Windows Search procure itens encriptados](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Configurar uma aplicação móvel MSI de atualização automática <!-- 1740840 -->
Pode configurar uma aplicação MSI móvel de atualização automática conhecida para ignorar o processo de verificação da versão. Esta funcionalidade é útil para evitar que ocorra uma condição race. Por exemplo, este tipo de condição race poderia ocorrer quando a aplicação de atualização automática por parte do programador também é atualizada pelo Intune. Ambos podem tentar impor uma versão da aplicação no cliente Windows, o que pode criar um conflito. Para estas aplicações MSI atualizadas automaticamente, pode configurar a definição **Ignorar versão da aplicação** no painel **Informações da aplicação**. Quando esta opção está definida para **Sim**, o Microsoft Intune irá ignorar a versão da aplicação instalada no cliente Windows.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Conjuntos relacionados de licenças de aplicações suportadas no Intune <!-- 1864117 -->
O Intune no portal do Azure agora suporta conjuntos relacionados de licenças de aplicações como um único item de aplicação na IU. Além disso, todas as aplicações com Licença Offline sincronizadas a partir da Microsoft Store para Empresas serão consolidadas numa única entrada de aplicação e todos os detalhes de implementação dos pacotes individuais serão migrados para uma única entrada. Para ver conjuntos relacionados de licenças de aplicações no portal do Azure, selecione **Licenças de aplicação** no painel **Aplicações do cliente**.

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

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Suporte para aplicações offline na Loja Microsoft para Empresas <!--1222672-->
As aplicações offline que comprou na Microsoft Store para Empresas são agora sincronizadas com o portal do Azure. Pode implementar estas aplicações em grupos de dispositivos ou de utilizadores. As aplicações offline são instaladas pelo Intune, não pela loja.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Impedir os utilizadores de adicionarem ou removerem contas manualmente no perfil de trabalho <!-- 1728700 -->

Ao implementar a aplicação Gmail num perfil do Android for Work, agora pode impedir os utilizadores finais de adicionarem ou removerem contas manualmente no perfil de trabalho através da definição **Adicionar e remover contas** no perfil Restrições do dispositivo Android for Work.


## <a name="january-2018"></a>Janeiro de 2018

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

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Nova funcionalidade para a ação "Resolver" para dispositivos Android <!--1583480-->

A aplicação Portal da Empresa para Android irá expandir a ação "Resolver" de **Atualizar definições do dispositivo** para também resolver [problemas de encriptação de dispositivos](/intune-user-help/encrypt-your-device-android).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Bloqueio remoto disponível na aplicação Portal da Empresa para Windows 10 <!--676506-->
Agora os utilizadores finais podem bloquear remotamente os seus dispositivos a partir da aplicação Portal da Empresa para Windows 10. Isto não será apresentado no dispositivo local que estejam a utilizar atualmente.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Resolução de problemas de conformidade mais fácil na aplicação do Portal da Empresa para Windows 10 <!--676546-->
Os utilizadores finais com dispositivos Windows poderão tocar no motivo de não conformidade na aplicação Portal da Empresa. Sempre que possível, esta ação irá reencaminhá-lo para a localização correta na aplicação de definições para resolver o problema.

## <a name="december-2017"></a>Dezembro de 2017

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="new-automatic-redeployment-setting----1469168---"></a>Nova definição de reimplementação automática <!-- 1469168 -->
A definição **Reimplementação automática** permite aos utilizadores com direitos administrativos eliminar todos os dados do utilizador e as definições através de **CTRL + Win + R** no ecrã de bloqueio do dispositivo. O dispositivo é automaticamente reconfigurado e reinscrito na gestão. Esta definição encontra-se em Windows 10 > Restrições do dispositivo > Geral > Reimplementação automática. Para obter mais detalhes, veja [Definições de restrição de dispositivos Windows 10 no Intune](device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Suporte para edições de origem adicionais na política de atualização de edição do Windows 10<!-- 903672,  1119689 -->
Agora, pode utilizar a política de atualização de edição do Windows 10 para atualizar a partir de edições do Windows 10 adicionais (Windows 10 Pro, Windows 10 Pro for Education, Windows 10 Cloud e etc.). Antes desta versão, os caminhos de atualização de edição suportados eram mais limitados. Para obter detalhes, veja [Como configurar atualizações de edição do Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Novas definições do perfil de configuração do dispositivo do Centro de Segurança do Windows Defender (WDSC) <!-- 1335507 -->

O Intune adiciona uma nova secção de definições do perfil de configuração do dispositivo na Endpoint Protection com o nome **Centro de Segurança do Windows Defender**. Os administradores de TI podem configurar quais os pilares do Centro de Segurança do Windows Defender a que os utilizadores finais podem aceder. Se um administrador de TI ocultar um pilar na aplicação do Centro de Segurança do Windows Defender, nenhuma das notificações relacionadas com o pilar oculto serão apresentadas no dispositivo do utilizador.

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

   - **e-mail**

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

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>O Intune suporta as aplicações negadas do Windows Information Protection (WIP) <!-- 1479103 -->
Pode especificar aplicações negadas no Intune. Se uma aplicação for negada, não poderá aceder a informações empresariais, ao contrário do que acontece com a lista de aplicações permitidas. Para obter mais informações, veja [Recommended deny list for Windows Information Protection (Lista de negações recomendadas para o Windows Information Protection)](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection).


## <a name="november-2017"></a>Novembro de 2017

### <a name="troubleshoot-enrollment-issues-----746324---"></a>Resolução de problemas de inscrição <!-- 746324 -->

A área de trabalho **Resolução de Problemas** agora apresenta os problemas de inscrição de utilizadores. Os detalhes acerca do problema e os passos de remediação sugeridos podem ajudar os administradores e os operadores de suporte técnico a resolver problemas. Existem determinados problemas de inscrição que não são detetados e é possível que não existam sugestões de remediação para alguns erros.

### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restrições de inscrição atribuídas a grupos <!-- 747598 -->

Enquanto administrador do Intune, agora pode [criar restrições de inscrição personalizadas de Tipo de Dispositivo e Limite de Dispositivo para grupos de utilizadores](enrollment-restrictions-set.md).

O portal do Azure do Intune permite-lhe criar até 25 instâncias de cada tipo de restrição, que podem depois ser atribuídas a grupos de utilizadores. As restrições atribuídas a grupos substituem as restrições predefinidas.

Todas as instâncias de um tipo de restrição são mantidas numa lista estritamente ordenada. Esta ordem define um valor de prioridade para a resolução do conflito. Um utilizador afetado por mais do que uma instância de restrição só é restringido pela instância com o valor de prioridade mais elevada. Pode alterar a prioridade de uma determinada instância ao arrastá-la para uma posição diferente na lista.

Esta funcionalidade será lançada com a migração das definições do Android for Work do menu de inscrição do Android for Work para o menu Restrições de Inscrição. Como esta migração pode demorar vários dias, poderão ser atualizadas outras partes da sua conta no lançamento de novembro antes da ativação da atribuição de grupos nas Restrições de Inscrição.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Suporte para múltiplos conectores do Serviço de Inscrição de Dispositivos de Rede (NDES) <!-- 1528104 -->

O NDES permite a execução de dispositivos móveis sem credenciais de domínio para obter certificados com base no protocolo SCEP (Simple Certificate Enrollment Protocol).
Com esta atualização, são suportados múltiplos conectores do NDES.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Gerir dispositivos Android for Work de forma independente dos dispositivos Android <!-- 1490731 EEready-->

O Intune suporta a gestão de inscrição de dispositivos Android for Work de forma independente da plataforma Android. Estas definições são geridas em **Inscrição de Dispositivos** > **Restrições de inscrição** > **Restrições de Tipos de Dispositivos**. (Estavam anteriormente localizadas em **Inscrição de Dispositivos** > **Inscrição do Android for Work** > **Definições de Inscrição do Android for Work**.)

Por predefinição, as definições dos dispositivos Android for Work são as mesmas que as definições dos seus dispositivos Android. No entanto, depois de alterar as definições do Android for Work, este já não será o caso.

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

### <a name="google-play-protect-support-on-android----908720---"></a>Suporte ao Google Play Protect no Android<!-- 908720 -->

Com o lançamento do Android Oreo, a Google apresenta um conjunto de funcionalidades de segurança chamado Google Play Protect, que permite que os utilizadores e as organizações executem imagens Android e aplicações seguras. O Intune agora suporta funcionalidades do Google Play Protect, incluindo o atestado remoto SafetyNet. Os administradores podem definir os requisitos da política de conformidade que são necessários para o Google Play Protect ser configurado e funcionar corretamente.
A definição **Atestado do dispositivo SafetyNet** requer que o dispositivo para estabelecer ligação com um serviço do Google verifique se o dispositivo está a funcionar e se não está comprometido. Os administradores também podem especificar uma definição de perfil de configuração do Android For Work que exija que as aplicações instaladas sejam verificadas pelos serviços do Google Play. O acesso condicional pode impedir que os utilizadores acedam a recursos da empresa caso o dispositivo não esteja em conformidade com os requisitos do Google Play Protect.

- Saiba [Como criar uma política de conformidade de dispositivos para ativar o Google Play Protect](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect).

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocolo de texto autorizado a partir de Aplicações geridas <!-- 1414050  -->

As aplicações geridas pelo SDK da Aplicação Intune podem enviar mensagens SMS.


### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>O relatório de instalação da aplicação foi atualizado para incluir o estado Instalação Pendente <!-- 1249446 -->  

O relatório **Estado de instalação de aplicação** acessível para cada aplicação através da lista **Aplicação** na carga de trabalho **Aplicações do cliente** contém uma contagem de **Instalações Pendentes** para Utilizadores e Dispositivos.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API do inventário de aplicações para iOS 11 para a Deteção de Ameaças para Dispositivos Móveis <!-- 1391759 -->

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

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>Migrar utilizadores e dispositivos da MDM híbrida para o Intune autónomo <!-- 1463747 wnready -->
Estão agora disponíveis novos processos e ferramentas para migrar utilizadores e os respetivos dispositivos da MDM híbrida para o Intune no portal do Azure, que lhe permitem efetuar as seguintes tarefas:
- Copiar políticas e perfis da consola do Configuration Manager para o Intune no portal do Azure
- Mover um subconjunto de utilizadores para o Intune no portal do Azure enquanto mantém os restantes na MDM híbrida
- Migrar dispositivos para o Intune no portal do Azure sem precisar de voltar a inscrevê-los

Para obter detalhes, veja [Migrate hybrid MDM users and devices to Intune standalone (Migrar os dispositivos e utilizadores da MDM híbrida para o Intune autónomo)](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Suporte de elevada disponibilidade do conector do Exchange no local <!-- 676614 -->
Depois de o conector do Exchange criar uma ligação ao Exchange através da CAS especificada, o conector terá a capacidade de detetar outras CASs. Se a CAS principal ficar indisponível, o conector realizará a ativação pós-falha de outra CAS, se disponível, até a CAS principal ficar disponível. Para obter mais informações, veja [Suporte de elevada disponibilidade do conector do Exchange no local](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support).

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Reiniciar dispositivos iOS remotamente (apenas supervisionado) <!-- 1424595 -->

Agora pode acionar o reinício de um dispositivo supervisionado com o iOS 10.3 ou superior ao utilizar uma ação de dispositivo. Para obter mais informações sobre como utilizar a ação de reinício de dispositivos, veja [Reiniciar remotamente dispositivos com o Intune](device-restart.md).

> [!Note]
> Este comando necessita de um dispositivo supervisionado e do direito de acesso **Bloqueio do Dispositivo**. O dispositivo é reiniciado imediatamente. Os dispositivos iOS bloqueados por código de acesso não voltarão a ligar-se a uma rede Wi-Fi após o reinício. Após o reinício, estes dispositivos poderão não conseguir comunicar com o servidor.

### <a name="single-sign-on-support-for-ios----1333645---"></a>Suporte de Início de Sessão Único para iOS <!-- 1333645 -->  

Pode utilizar o Início de Sessão Único para utilizadores do iOS. As aplicações iOS que estão codificadas para procurar as credenciais dos utilizadores no payload de Início de Sessão Único são compatíveis com esta atualização de configuração do payload. Também pode utilizar o UPN e o ID de Dispositivo do Intune para configurar o Nome Principal e o Realm. Para obter detalhes, veja [Configure Intune for iOS device single sign-on (Configurar o Intune para o início de sessão único em dispositivos iOS)](sso-ios.md).

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Adicionar "Encontrar iPhone" para dispositivos pessoais <!--1427287-->
Agora pode ver se os dispositivos iOS têm o Bloqueio de Ativação ativado. Esta funcionalidade estava anteriormente disponível no portal clássico do Intune.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Bloquear remotamente dispositivos macOS geridos com o Intune <!-- 1437691 -->

Pode bloquear um dispositivo macOS perdido e definir um PIN de recuperação de 6 dígitos. Se estiver bloqueado, o painel **Descrição geral do dispositivos** apresenta o PIN até que seja enviada outra ação de dispositivo.

Para obter mais informações, veja [Bloquear remotamente dispositivos geridos com o Intune](device-remote-lock.md).

### <a name="new-scep-profile-details-supported----1559808---"></a>Suporte para novos detalhes do perfil SCEP <!-- 1559808 -->

Agora, os administradores podem configurar definições adicionais ao criar um perfil SCEP em plataformas Windows, iOS, macOS e Android.  Os administradores podem definir o IMEI, o número de série ou o nome comum, incluindo o e-mail, no formato do nome do requerente.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset----1588489---"></a>Reter dados durante uma reposição de fábrica <!--1588489 -->
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


### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Atribuições de cadência de atualização do Windows 10 são apresentadas <!-- 1621837 -->
Durante a **Resolução de problemas** do utilizador que está a ver, pode ver todas as atribuições de cadências de atualização do Windows 10.  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Definições da frequência de relatórios de Proteção Avançada Contra Ameaças do Windows Defender <!-- 1455974  -->
O serviço de Proteção Avançada Contra Ameaças do Windows Defender (WDATP) permite aos administradores gerir a frequência de relatórios dos dispositivos geridos. Com a nova opção **Acelerar a frequência do relatório de telemetria**, o WDATP recolhe os dados e avalia os riscos com mais frequência. A predefinição dos relatórios otimiza a velocidade e o desempenho. O aumento da frequência de relatórios pode ser útil para dispositivos de alto risco. Poderá encontrar esta definição no perfil **Windows Defender ATP** nas **Configurações do dispositivo**.

### <a name="audit-updates----1412961---"></a>Atualizações de auditoria <!-- 1412961 -->  
A auditoria do Intune fornece um registo das operações de alteração relacionadas com o Intune.  Todas as operações de criação, atualização, eliminação e realização de tarefas remotas são registadas e retidas durante um ano.  O portal do Azure fornece uma vista dos dados de auditoria dos últimos 30 dias em cada carga de trabalho e podem ser filtrados.  A Graph API correspondente permite a obtenção dos dados de auditoria armazenados do último ano.

A Auditoria está localizada no grupo **MONITORIZAÇÃO**. Existe um item de menu **Registos de Auditoria** para cada carga de trabalho.

### <a name="company-portal-app-for-macos-is-available---1541700--"></a>A aplicação Portal da Empresa para macOS está disponível <!--1541700-->
O Portal da Empresa do Intune no macOS tem uma experiência atualizada, a qual foi otimizada para apresentar corretamente todas as informações e notificações de conformidade que os utilizadores precisam para todos os dispositivos inscritos. Além disso, após implementar o Portal da Empresa do Intune num dispositivo, o Microsoft AutoUpdate para macOS fornecerá as atualizações. Pode transferir o novo Portal da Empresa do Intune para macOS ao iniciar sessão no site do Portal da Empresa do Intune a partir de um dispositivo macOS.

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>O Microsoft Planner faz agora parte da lista de gestão de aplicações móveis (MAM) de aplicações aprovadas <!-- 1248473 -->
A aplicação Microsoft Planner para iOS e Android faz agora parte das aplicações aprovadas para a gestão de aplicações móveis (MAM). A aplicação pode ser configurada através do painel Proteção de Aplicações do Intune no portal do Azure para todos os inquilinos.
- Saiba mais sobre a [Lista MAM de aplicações aprovadas](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>Frequência de atualização dos requisitos de VPN por Aplicação em dispositivos iOS <!-- 1547061 -->  
Os administradores podem agora remover os requisitos de VPN por Aplicação para as aplicações em dispositivos iOS; os dispositivos afetados serão removidos após a próxima entrada do Intune, o que geralmente ocorre num espaço de 15 minutos.  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Suporte para o pacote de gestão do System Center Operations Manager do conector do Exchange <!-- 885457 -->
O pacote de gestão do System Center Operations Manager (SCOM) do conector do Exchange está agora disponível para ajudá-lo a analisar os registos do conector do Exchange. Esta funcionalidade disponibiliza maneiras diferentes de monitorizar o serviço quando precisar de resolver problemas.

### <a name="co-management-for-windows-10-devices-----1243445---"></a>Cogestão para dispositivos Windows 10 <!-- 1243445 -->
A cogestão é uma solução que proporciona a transição de uma gestão tradicional para uma moderna, além de permitir que faça essa transição de forma faseada. Na sua génese, a cogestão é uma solução em que os dispositivos Windows 10 são geridos simultaneamente pelo Configuration Manager e pelo Microsoft Intune, além de estar associada ao Active Directory (AD) e ao Azure Active Directory (Azure AD).  Esta configuração proporciona-lhe uma forma de modernizar a gestão com ao longo do tempo e ao ritmo mais adequado para a sua organização, caso não consiga efetuar a mudança de uma só vez.  

### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Restringir a Inscrição do Windows por versão do SO <!-- 245498 -->
Enquanto administrador do Intune, pode especificar uma versão mínima e máxima do Windows 10 para a inscrição de dispositivos. Pode definir estas restrições no painel **Configurações da Plataforma**.

O Intune irá continuar a suportar a inscrição de telemóveis e PCs com o Windows 8.1. No entanto, apenas as versões do Windows 10 podem ser definidas com os limites mínimo e máximo. Para permitir a inscrição de dispositivos com o Windows 8.1, deixe o limite mínimo em branco.

### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Alertas para dispositivos Windows AutoPilot não atribuídos  <!-- 1631236 -->
Está disponível um novo alerta para dispositivos Windows AutoPilot não atribuídos na página **Microsoft Intune** > **Inscrição de dispositivos** > **Descrição geral**. Este alerta mostra o número de dispositivos do programa AutoPilot que não têm perfis de implementação do AutoPilot atribuídos. Utilize as informações no alerta para criar perfis e atribui-los aos dispositivos não atribuídos. Quando clica no alerta, é-lhe apresentada uma lista completa dos dispositivos Windows AutoPilot e informações detalhadas sobre os mesmos. Para obter mais informações, veja [Inscrever dispositivos Windows com o programa de implementação do Windows AutoPilot](https://docs.microsoft.com/intune/enrollment-autopilot).


### <a name="refresh-button-for-devices-list-------1333581---"></a>Botão de atualização da lista Dispositivos    <!-- 1333581 -->
Como a lista Dispositivos não atualiza automaticamente, pode utilizar o novo botão Atualizar para atualizar os dispositivos que são apresentados na lista.

### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Suporte para a Autoridade de Certificação (AC) da Symantec Cloud <!-- 1333638 -->    
O Intune agora suporta a AC da Symantec Cloud, que permite ao Intune Certificate Connector emitir certificados PKCS a partir da AC da Symantec Cloud para os dispositivos geridos pelo Intune. Se já estiver a utilizar o Intune Certificate Connector com a Autoridade de Certificação (AC) da Microsoft, pode utilizar a configuração existente do Intune Certificate Connector para incluir o suporte à AC da Symantec.

### <a name="new-items-added-to-device-inventory-----1404455---"></a>Novos itens adicionados ao inventário de dispositivos   <!--1404455 -->
Estão agora disponíveis os seguintes novos itens no [inventário de dispositivos inscritos](device-inventory.md):

- Endereço MAC Wi-Fi
- Espaço de armazenamento total
- Espaço livre total
- MEID
- Operadora subscritora

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Definir o acesso a aplicações através de uma atualização de segurança mínima para Android no dispositivo <!-- 1278463 -->   
Um administrador pode definir a atualização de segurança mínima para Android que tem de ser instalada no dispositivo, de modo a obter acesso a uma aplicação gerida numa conta gerida.

> [!Note]  
> Esta funcionalidade apenas restringe atualizações de segurança lançadas pela Google em dispositivos Android 6.0+.

### <a name="app-conditional-launch-support----1193313---"></a>Suporte para execução condicional de aplicações <!-- 1193313 -->
Os administradores de TI já podem definir um requisito através do portal de administração do Azure para impor um código de acesso em vez de um PIN numérico através da gestão de aplicações móveis (MAM) quando a aplicações é executada. Caso esteja configurado, é pedido ao utilizador que defina e utilize um código de acesso antes de poder aceder a aplicações otimizadas para a MAM. Os código de acesso são definidos como um PIN numérico com, pelo menos, um caráter especial ou letras em maiúsculas/minúsculas. Esta versão do Intune irá ativar esta funcionalidade **apenas no iOS**. O Intune suporta um código de acesso de forma semelhante a um PIN numérico: a aplicação define um comprimento mínimo e permite sequências e carateres repetidos. Esta funcionalidade requer que a participação de aplicações (por exemplo, WXP, Outlook, Managed Browser, Yammer) integre o SDK da Aplicação Intune com o código desta funcionalidade para que as definições do código de acesso sejam impostas nas aplicações visadas.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Número da Versão de Aplicação para aplicações de linha de negócio no relatório de estado de instalação do dispositivo <!-- 1233999 -->
Com esta versão, o relatório de estado de instalação do Dispositivo apresenta o número da versão de aplicação das aplicações de linha de negócio para iOS e Android. Pode utilizar estas informações para resolver problemas nas suas aplicações ou localizar dispositivos que estão a ser executados com versões desatualizadas da aplicação.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Agora, os administradores podem configurar as definições de Firewall num dispositivo através de um perfil de configuração de dispositivo <!-- 951708 -->   
Os administradores podem ativar a firewall para os dispositivos, bem como configurar vários protocolos para redes de domínio privadas e públicas.  Poderá encontrar estas definições de firewall no perfil "Proteção de ponto final".

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>O Windows Defender Application Guard ajuda a proteger os dispositivos de sites não fidedignos, consoante as definições da sua organização <!-- 958257 -->   
Os administradores podem definir sites como "fidedigno" ou "empresarial" através de um fluxo do Windows Information Protection ou do novo perfil "Limite de rede" nas configurações dos dispositivos. Se forem acedidos com o Microsoft Edge, todos os sites que não estiverem indicados no limite de rede fidedigno de um dispositivo com o Windows 10 de 64 bits serão abertos num browser num computador virtual Hyper-V.

Poderá encontrar o Application Guard nos perfis de configuração de dispositivos, no perfil "Proteção de ponto final". A partir daí, os administradores podem configurar a interação entre o browser virtualizado e o computador anfitrião, sites fidedignos e não fidedignos e os dados de armazenamento gerados no browser virtualizado. Para utilizar o Application Guard num dispositivo, é necessário configurar primeiro um limite de rede. É importante definir apenas um limite de rede para um dispositivo.  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>O Controlo de Aplicações do Windows Defender no Windows 10 Enterprise fornece um modo para confiar apenas em aplicações autorizadas <!-- 1031096 -->    
Com milhares de novos ficheiros maliciosos a serem criados todos os dias, a deteção com base em assinatura de antivírus para combater software maligno poderá deixar de ser uma defesa adequada contra novos ataques. Com o Controlo de Aplicações do Windows Defender no Windows 10 Enterprise, pode alterar a configuração do dispositivo de um modo em que as aplicações são fidedignas, a menos que sejam bloqueadas por um antivírus ou por outra solução de segurança, para um modo em que o sistema operativo confia apenas nas aplicações autorizadas pela sua empresa. A atribuição de fidedignidade a aplicações é feita no Controlo de Aplicações do Windows Defender.

Com o Intune, pode configurar as políticas de controlo de aplicações no modo "apenas auditoria" ou no modo de imposição. As aplicações não são bloqueadas ao serem executadas no modo "apenas auditoria". O modo "apenas auditoria" regista todos os eventos nos registos do cliente local. Também pode configurar se pretende que apenas os componentes Windows e as aplicações da Microsoft Store tenham permissão para serem executados ou se pretende permitir a execução de aplicações adicionais com boa reputação, conforme definido pelo Gráfico de Segurança Inteligente.

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>O Windows Defender Exploit Guard é um novo conjunto de funcionalidades de prevenção de intrusões para o Windows 10 <!-- 1063615 -->   
O Windows Defender Exploit Guard inclui regras personalizadas para reduzir a exploração de aplicações, impede ameaças de macros e scripts, bloqueia automaticamente ligações de rede a endereço IP com baixa reputação e ajuda a proteger os dados de ransomware e ameaças desconhecidas. O Windows Defender Exploit Guard consiste nos seguintes componentes:

- A **Redução da Superfície de Ataque (ASR)** fornece regras que lhe permitem impedir ameaças de macros, scripts e e-mail.
- O **Acesso a Pastas Controladas** bloqueia automaticamente o acesso a conteúdos de pastas protegidas.
- O **Filtro de Rede** bloqueia a ligação de saída de qualquer aplicação para um IP/domínio com baixa reputação
- A **Exploit Protection** fornece restrições de memória, fluxo de controlos e de políticas que podem ser utilizadas para proteger um aplicação de exploits.

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Gerir scripts do PowerShell no Intune para dispositivos Windows 10 <!-- 790537 -->

A extensão de gestão do Intune permite-lhe carregar scripts do PowerShell no Intune para executar em dispositivos Windows 10. A extensão complementa as funcionalidades de gestão de dispositivos móveis (MDM) do Windows 10 e facilita a sua transição para a gestão moderna. Para obter detalhes, veja [Manage PowerShell scripts in Intune for Windows 10 devices (Gerir scripts do PowerShell no Intune para dispositivos Windows 10)](intune-management-extension.md).

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Novas definições de restrição de dispositivos para Windows 10      <!-- 1308850 -->
-    Mensagens (apenas para telemóveis) – desativar mensagens de teste ou MMS
-    Palavra-passe – definições para ativar o sistema FIPS e utilizar dispositivos secundários Windows Hello para efeitos de autenticação 
-    Apresentação – definições para ativar ou desativar o Dimensionamento de GDI para aplicações legadas

### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Restrições de dispositivos Windows 10 no modo de local público <!-- 1308872 -->   
Pode restringir os utilizadores de dispositivos Windows 10 ao modo de local público, que os limita a um conjunto de aplicações predefinidas.  Para fazê-lo, crie um perfil de restrição de dispositivos Windows 10 e configure as definições do modo de local público.

O modo de local público suporta dois modos: **quiosque de uma aplicação** (permite que um utilizador execute apenas uma aplicação) ou **quiosque de várias aplicações** (concede acesso a um conjunto de aplicações).  Defina a conta de utilizador e o nome do dispositivo, o qual determina as aplicações suportadas).  Quando o utilizador tiver sessão iniciada, este será limitado às aplicações definidas.  Para saber mais, veja [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp). 

O modo de local público necessita que:

- O Intune seja a autoridade MDM.
- As aplicações já estejam instaladas no dispositivo alvo.
- O dispositivo esteja [devidamente aprovisionado](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Novo perfil de configuração de dispositivos para a criação de limites de rede <!-- 1311967 -->   
Está agora disponível um novo perfil de configuração de dispositivos denominado **Limite de rede** nos perfis de configuração de dispositivos. Utilize este perfil para definir os recursos online que pretende que sejam considerados como empresariais e fidedignos. Tem de definir um limite de rede para um dispositivo *antes* de as funcionalidades como o Windows Defender Application Guard e o Windows Information Protection poderem ser utilizadas no dispositivo. É importante definir apenas um limite de rede para cada dispositivo.

Pode definir os recursos do Enterprise Cloud, intervalos de endereços IP e servidores proxy internos que pretende que sejam considerados fidedignos. Assim que o definir, o limite de rede pode ser utilizado por outras funcionalidades, tais como o Windows Defender Application Guard e o Windows Information Protection.

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Duas definições adicionais do Antivírus do Windows Defender <!-- 1338409 -->  
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

### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Adição da VPN do Citrix para dispositivos Windows 10 <!-- 1512457 -->  
Pode configurar a VPN do Citrix nos respetivos dispositivos Windows 10. Pode selecionar a VPN do Citrix na lista *Selecione um tipo de ligação* no painel **VPN Base** ao configurar uma VPN para o Windows 10 e posterior.

> [!Note]
> A configuração do Citrix existia para os sistemas iOS e Android.

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>As ligações Wi-Fi suportam chaves pré-partilhadas no iOS <!-- 1550823 -->
Os clientes podem configurar perfis de Wi-Fi para utilizar chaves pré-partilhadas (PSK) para ligações Pessoais WPA/WPA2 em dispositivos iOS. Estes perfis são enviados via push para o dispositivo do utilizador quando o dispositivo está inscrito no Intune.

Quando o perfil tiver sido enviado para o dispositivo, o passo seguinte depende da configuração do perfil.  Se estiver definido para ligar automaticamente, assim o faz quando a rede se tornar necessária.  Quando o perfil está definido para ligar manualmente, o utilizador tem de ativar a ligação manualmente.  

### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Acesso a registos de aplicações geridas para iOS <!-- 1469920 -->
Agora, os utilizadores finais com o Managed Browser instalado podem ver o estado da gestão de todas as aplicações publicadas da Microsoft e enviar registos para resolver os problemas das respetivas aplicações iOS geridas.

Para saber como ativar o modo de resolução de problemas num Managed Browser num dispositivo iOS, veja [How to access to managed app logs using the Managed Browser on iOS (Como aceder a registos de aplicações geridas com o Managed Browser no iOS)](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Melhorias no fluxo de trabalho da configuração de dispositivos no Portal da Empresa para iOS na versão 2.9.0 <!-- 1417174 -->

O fluxo de trabalho da configuração de dispositivos foi melhorado na aplicação Portal da Empresa para iOS. O tipo de linguagem é mais simples. Além disso, combinámos os ecrãs sempre que possível. A linguagem é agora mais adaptada à sua empresa, ao utilizar o nome da sua empresa no texto de configuração. Pode ver este fluxo de trabalho atualizado em  [novidades na página da IU para aplicações](whats-new-app-ui.md).


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>A entidade User contém dados de utilizador no modelo de dados do Armazém de Dados <!-- 1544273 -->
A primeira versão do modelo de dados do Armazém de Dados do Intune continha apenas dados de histórico recentes do Intune. Os criadores de relatórios não conseguiam capturar o estado atual de um utilizador. Nesta atualização, a **entidade User** é preenchida com os dados de utilizador mais recentes.


## <a name="october-2017"></a>Outubro de 2017

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>O número da versão da aplicação de linha de negócio para iOS e Android está visível <!-- 1380712 -->

As aplicações no Intune apresentam agora o número da versão de aplicações de linha de negócio para iOS e Android. O número é apresentado no portal do Azure na lista de aplicações e no painel de descrição geral da aplicação. Os utilizadores finais podem ver o número da aplicação na aplicação Portal da Empresa e no portal Web.

__Número da versão completo__ – O número da versão completo identifica uma versão específica da aplicação. O número é apresentado como _Versão_(_Compilação_), por exemplo, 2.2(2.2.17560800).

O número da versão completo tem dois componentes:

 - **Versão**  
   O número da versão é o número da versão legível por humanos da aplicação. Este número é utilizado pelos utilizadores finais para identificar diferentes versões da aplicação.

 - **Número de Compilação**  
    O número de compilação é um número interno que pode ser utilizado para detetar aplicações e gerir a aplicação de forma programática. O número de compilação refere-se a uma iteração da aplicação que faz referência a alterações no código.

Saiba mais sobre os números de versão e o desenvolvimento de aplicações de linha de negócio em [Introdução ao SDK da Aplicação Microsoft Intune](app-sdk-get-started.md#line-of-business-app-version-numbers).

### <a name="device-and-app-management-integration----677972---"></a>Integração da gestão de dispositivos e aplicações <!-- 677972 -->   
Agora que tanto a gestão de dispositivos móveis (MDM) do Intune como a gestão de aplicações móveis (MAM) se encontram acessíveis no portal do Azure, o Intune iniciou a integração da experiência de administradores de TI em torno da gestão de aplicações e dispositivos. Estas alterações foram concebidas de modo a simplificar a sua experiência de gestão de dispositivos e aplicações.

Saiba mais sobre as alterações de MDM e MAM anunciadas no [blogue da equipa de suporte do Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Novos alertas de inscrição para dispositivos da Apple <!-- 1471790 -->
A página de descrição geral para inscrição apresentará alertas úteis para os administradores de TI sobre a gestão de dispositivos da Apple. Os alertas serão apresentados na página Descrição Geral quando o certificado push de MDM da Apple estiver prestes a expirar ou já tiver expirado, quando o token do Programa de Registo de Aparelho estiver prestes a expirar ou já tiver expirado e quando existirem dispositivos não atribuídos no Programa de Registo de Aparelho.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>Substituição do token de suporte para a configuração de aplicações sem inscrição de dispositivos <!-- 1080364 -->

Pode utilizar tokens para valores dinâmicos em configurações da aplicação para aplicações em dispositivos que não estejam inscritos. Para obter mais informações, veja [Adicionar políticas de configuração da aplicação para aplicações geridas sem inscrição de dispositivos](app-configuration-policies-managed-app.md).

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Atualizações à aplicação Portal da Empresa para Windows 10 <!--1299474-->
A página Definições na aplicação Portal da Empresa para Windows 10 foi atualizada para tornar as definições e as ações do utilizador em causa mais consistentes em todas as definições. Também foi atualizada para corresponder ao esquema de outras aplicações do Windows. Pode encontrar imagens antes/depois na página [novidades na página da IU para aplicações](whats-new-app-ui.md).

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>Informe os utilizadores finais acerca das informações do dispositivo que podem ser vistas para dispositivos Windows 10 <!--1337920-->
Adicionámos o **Tipo de Propriedade** ao ecrã Detalhes do Dispositivo na aplicação Portal da Empresa para Windows 10. Isto permite que os utilizadores obtenham mais informações sobre privacidade diretamente a partir desta página, através da documentação de utilizador final do Intune. Também poderão localizar estas informações no ecrã **Acerca de**.

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Pedidos de comentários sobre a aplicação Portal da Empresa para Android<!--1165249-->
A aplicação Portal da Empresa para Android solicita agora comentários aos utilizadores finais. Este feedback é enviado diretamente para a Microsoft e proporciona aos utilizadores finais a oportunidade de reverem a aplicação na Google Play Store pública. Os comentários não são obrigatórios e podem ser dispensados facilmente para os utilizadores poderem continuar a utilizar a aplicação.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Ajudar os utilizadores a resolver problemas com a aplicação Portal da Empresa para Android <!-- 1573324, 1573150, 1558616, 1564878 -->

A aplicação Portal da Empresa para Android adicionou instruções para ajudar os utilizadores finais a compreender e, sempre que possível, a resolver autonomamente novos casos de utilização.
- Os utilizadores finais serão encaminhados para o [portal do Azure Active Directory](https://account.activedirectory.windowsazure.com/r/#/profile) para remover um dispositivo se tiverem atingido o número máximo de dispositivos que estão autorizados a adicionar.
- Os utilizadores finais recebem uma lista de passos a seguir para os ajudar a [corrigir erros de ativação em dispositivos Samsung Knox](https://go.microsoft.com/fwlink/?linkid=859718) ou a [desativar o modo de poupança de energia](/intune-user-help/power-saving-mode-android). Se nenhuma dessas soluções resolver o problema, forneceremos uma explicação sobre como [enviar registos para a Microsoft](/intune-user-help/send-logs-to-microsoft-android).

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Nova ação "Resolver" disponível para dispositivos Android <!-- 1583480 -->

A aplicação Portal da Empresa para Android está a introduzir a ação "Resolver" na página _Atualizar definições do dispositivo_. A seleção desta opção levará o utilizador diretamente para a definição que está a fazer com que o dispositivo não esteja em conformidade. A aplicação Portal da Empresa para Android suporta atualmente esta ação para as definições de [código de acesso do dispositivo](/intune-user-help/set-your-pin-or-password-android), [depuração de USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) e [Origens Desconhecidas](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Indicador de progresso da configuração do dispositivo no Portal da Empresa para Android <!-- 1565657 -->
A aplicação Portal da Empresa para Android mostra um indicador de progresso da configuração do dispositivo quando um utilizador está a inscrever o dispositivo. O indicador mostra novos estados, a começar por “A configurar o dispositivo…”, seguido de “A registar o dispositivo…”, “A concluir o registo do dispositivo...” e “A concluir a configuração do dispositivo...”.

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Suporte para a autenticação baseada em certificados no Portal da Empresa para iOS <!--1029830-->
Adicionámos o suporte para a autenticação baseada em certificados (CBA) na aplicação Portal da Empresa para iOS. Os utilizadores com CBA devem introduzir o seu nome de utilizador e, em seguida, tocar na ligação "Iniciar sessão com um certificado". A CBA já é suportada na aplicação Portal da Empresa para Android e Windows. Pode obter mais informações na página [Iniciar sessão na aplicação Portal da Empresa](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>As aplicações que estão disponíveis com ou sem inscrição podem agora ser instaladas sem qualquer pedido de inscrição. <!-- 1334712 -->

As aplicações da empresa que foram disponibilizadas com ou sem inscrição na aplicação Portal da Empresa para Android já podem ser instaladas sem qualquer pedido de inscrição.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune----747617---"></a>Suporte do Programa Windows AutoPilot Deployment no Microsoft Intune  <!-- 747617  -->
Agora pode utilizar o Microsoft Intune com o Programa Windows AutoPilot Deployment para permitir que os utilizadores aprovisionem os respetivos dispositivos da empresa sem envolver o departamento de TI. Pode personalizar a configuração inicial (OOBE) e guiar os utilizadores para associarem os respetivos dispositivos ao Azure AD e inscrevê-los no Intune. Ao trabalharem em conjunto, o Microsoft Intune e o Windows AutoPilot eliminam a necessidade de implementar, manter e gerir imagens de sistema operativo. Para obter detalhes, veja [Enroll Windows devices using Windows AutoPilot Deployment Program (Inscrever dispositivos Windows com o Programa Windows AutoPilot Deployment)](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="quick-start-for-device-enrollment----1425655---"></a>Guia de introdução da inscrição de dispositivos  <!-- 1425655 --> 
O guia de introdução está disponível em **Inscrição de dispositivos** e fornece uma tabela de referência para gerir plataformas e configurar o processo de inscrição. Uma breve descrição de cada item e as ligações para documentos com instruções passo a passo fornecem documentos úteis para simplificar a introdução.

### <a name="device-categorization----1427491---"></a>Categorização de dispositivos <!-- 1427491 -->
O gráfico da plataforma de dispositivos inscritos do painel **Dispositivos > Descrição Geral** organiza os dispositivos por plataforma, incluindo Android, iOS, macOS, Windows e Windows Mobile.  Os dispositivos com outros sistemas operativos são agrupados em "Outro".  Isto inclui dispositivos fabricados pela Blackberry, NOKIA, entre outros.  

Para saber quais são os dispositivos afetados no seu inquilino, selecione **Gerir > Todos os dispositivos** e, em seguida, utilize o **Filtro** para limitar o campo **SO**.

### <a name="zimperium---new-mobile-threat-defense-partner-----954681---"></a>Zimperium – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis   <!-- 954681 -->  
Pode controlar o acesso aos recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Zimperium, uma solução de Defesa Contra Ameaças para Dispositivos Móveis que está integrada com o Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Como funciona a integração com o Intune
O risco é avaliado com base na telemetria recolhida dos dispositivos a executar o Zimperium. Pode configurar políticas de acesso condicional de EMS baseadas na avaliação de riscos do Zimperium, que é ativada através de políticas de conformidade do dispositivo do Intune, as quais pode utilizar para permitir ou impedir que os dispositivos não conformes acedam aos recursos empresariais com base em ameaças detetadas.

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Novas definições para o perfil de restrição de dispositivos Windows 10 <!--- 978575, 1308849, -->  
Estamos a adicionar novas definições ao perfil de restrição de dispositivos com o Windows 10 na categoria Windows Defender SmartScreen.

Para obter detalhes sobre o perfil de restrição de dispositivos com o Windows 10, veja [Windows 10 and later device restriction settings (Definições de restrição de dispositivos com o Windows 10 e posterior)]( device-restrictions-windows-10.md).

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Suporte remoto para dispositivos Windows e Windows Mobile  <!-- 1070473 -->  
O Intune pode utilizar o software [TeamViewer](https://www.teamviewer.com), comprado separadamente, para lhe permitir disponibilizar assistência remota aos utilizadores com o Windows e dispositivos Windows Mobile.

### <a name="scan-devices-with-windows-defender----1280988-1280990---"></a>Analisar dispositivos com o Windows Defender <!-- 1280988  1280990   -->
Pode executar uma **Análise rápida**, **Análise completa** e **Atualizar assinaturas** com o Antivírus do Windows Defender em dispositivos Windows 10 geridos. No painel de descrição geral do dispositivo, escolha a ação a executar no dispositivo. Ser-lhe-á pedido para confirmar a ação antes do comando ser enviado para o dispositivo. 

**Análise rápida**: uma análise rápida analisa as localizações onde se inicia o registo do software maligno, tais como chaves do registo e pastas de arranque conhecidas do Windows. Uma análise rápida demora cerca de cinco minutos. Combinada com a definição **Proteção em tempo real sempre ativada**, que analisa os ficheiros quando são abertos, quando são fechados e sempre que um utilizador navega para uma pasta, a análise rápida ajuda a fornecer proteção contra software maligno que poderá estar no sistema ou no kernel. Os utilizadores veem os resultados da análise nos dispositivos ao terminar. 

**Análise completa**: pode ser útil uma análise completa em dispositivos que encontraram uma ameaça de software maligno para identificar se existem componentes inativos que requerem uma limpeza mais detalhada- É também útil para executar análises a pedido. Uma análise completa pode demorar cerca de uma hora. Os utilizadores veem os resultados da análise nos dispositivos ao terminar. 

**Atualizar assinaturas**: o comando de atualização de assinaturas atualiza as definições e as assinaturas do software maligno do Windows Defender Antivirus. Este comando ajuda a garantir que o Windows Defender Antivirus é eficaz na deteção de software maligno. Esta funcionalidade destina-se apenas a dispositivos Windows 10, com ligação à Internet dos dispositivos pendente. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>O botão Ativar/Desativar é removido da página Autoridade de Certificação do Intune do portal do Azure no Intune <!-- 1400455 -->
 Vamos eliminar um passo extra na configuração do Certificate Connector no Intune. Neste momento, pode transferir o Certificate Connector e, em seguida, ativá-lo na consola do Intune. No entanto, se desativar o conector na consola do Intune, este continuará a emitir certificados.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
A partir de outubro, o botão Ativar/Desativar deixará de ser apresentado na página Autoridade de Certificação no portal do Azure. A funcionalidade do conector permanece igual. Os certificados continuam a ser implementados nos dispositivos inscritos no Intune. Pode continuar a transferir e instalar o Certificate Connector. Para interromper a emissão de certificados, desinstale o Certificate Connector em vez de o desativar.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Se tiver o Certificate Connector desativado, deve desinstalá-lo.

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Novas definições para o perfil de restrição de dispositivos Windows 10 Team <!--- 1308838 -->
Nesta versão, adicionámos muitas definições novas ao perfil de restrição de dispositivos Windows 10 Team para ajudar a controlar os dispositivos Surface Hub.

Para obter mais informações sobre este perfil, veja [Definições de restrição de dispositivos Windows 10 Team](device-restrictions-windows-10-teams.md).

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time----1333292---"></a>Impedir que os utilizadores de dispositivos Android alterem a data e hora dos dispositivos  <!-- 1333292 -->
Pode utilizar uma [política de dispositivo personalizada do Android](custom-settings-android.md) para impedir que os utilizadores de dispositivos Android alterem a data e a hora do dispositivo.

Para tal, configure uma política personalizada do Android com a definição URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange. Defina esta opção como **TRUE**e, em seguida, atribua-a aos grupos necessários.

### <a name="bitlocker-device-configuration---1397398---"></a>Configuração do dispositivo BitLocker <!-- 1397398 -->
A opção **Encriptação Windows > Definições Base** inclui uma nova definição **Aviso para a encriptação de outro disco**, que permitirá desativar o [pedido de aviso](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) para a encriptação de outro disco que poderá estar em utilização no dispositivo do utilizador.  A mensagem de aviso necessita de consentimento do utilizador final para configurar o BitLocker no dispositivo e bloqueia a configuração do BitLocker até confirmação do utilizador final.  A nova definição desativa o aviso do utilizador final.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>As aplicações do Volume Purchase Program for Business irão sincronizar com o seu Inquilino do Intune <!-- 800882 -->  
Os programadores de terceiros podem distribuir em privado aplicações aos membros autorizados do Volume Purchase Program (VPP) for Business especificados no iTunes Connect. Estes membros do VPP for Business podem iniciar sessão na Loja de Aplicações do Volume Purchase Program e comprar as suas aplicações.

Com esta versão, as aplicações do VPP for Business compradas pelo utilizador final começarão a sincronizar com os respetivos inquilinos do Intune.

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Selecionar a loja do país da Apple para sincronizar aplicações VPP <!-- 1332311 -->  
Pode configurar o Volume Purchase Program (VPP) ao carregar o token VPP. O Intune sincroniza as aplicações VPP para todas as regiões a partir da loja do país do VPP especificada.

> [!NOTE]  
> Atualmente, o Intune só sincroniza as aplicações VPP a partir da loja do país do VPP que corresponda à região do Intune na qual foi criado o inquilino do Intune.


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Bloquear ações de copiar e colar entre perfis de trabalho e pessoais no Android for Work <!-- 1098994 -->
Com esta versão, pode configurar o perfil de trabalho do Android for Work para bloquear as ações de copiar e colar entre aplicações pessoais e de trabalho. Pode encontrar esta nova definição no perfil **Restrições do dispositivo** da Plataforma **Android for Work** em **Definições do perfil de trabalho**.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Criar aplicações iOS limitadas a Lojas de Aplicações da Apple regionais específicas <!-- 1281692 -->
Poderá especificar a região do país durante a criação de uma aplicação gerida pela Loja de Aplicações da Apple.

> [!Note]  
> Atualmente, só pode criar aplicações geridas pela Apple App Store que estejam presentes na loja dos E.U.A.

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Atualizar o utilizador do VPP para iOS e as aplicações licenciadas de dispositivos <!-- 1305564 -->  
Poderá configurar o token VPP para iOS para atualizar todas as aplicações compradas para esse token através do serviço Intune. O Intune vai detetar as atualizações de aplicações VPP no interior da loja de aplicações e emiti-las automaticamente para o dispositivo quando este entra.

Para obter passos para configurar um token VPP e ativar as atualizações automáticas, veja [Como gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune] (/intune/vpp-apps-ios).


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Coleção de entidades de associação de dispositivos do utilizador adicionada ao modelo de dados do Armazém de Dados do Intune <!-- 1187917 -->
Agora pode criar relatórios e visualizações de dados com as informações de associação de dispositivos do utilizador que associam o utilizador às coleções de dispositivos de entidades. Pode aceder ao modelo de dados através do ficheiro do Power BI (PBIX) obtido na página do Intune do Armazém de Dados, através do ponto final do OData ou ao desenvolver um cliente personalizado.

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Rever a conformidade das políticas das cadências de atualização do Windows 10 <!-- 1067886 -->
Poderá consultar um relatório das políticas das cadências de atualização do Windows 10 em Atualizações de software > Por estado de implementação da cadência de atualização. O relatório das políticas inclui o estado de implementação das cadências de atualização configuradas. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions----1352223---"></a>Novo relatório que indica os dispositivos iOS com versões mais antigas do iOS   <!-- 1352223 -->
O relatório **Dispositivos iOS desatualizados** está disponível na área de trabalho **Atualizações de software**. No relatório, poderá ver uma lista dos dispositivos iOS supervisionados que foram abrangidos por uma política de atualização iOS com atualizações disponíveis. Pode ver o estado com o motivo pelo qual cada um dos dispositivos não foi atualizado automaticamente. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting----1475003---"></a>Ver as atribuições de políticas de proteção de aplicações para resolução de problemas <!--  1475003 -->
Nesta versão futura, a opção **Política de proteção de aplicações** será adicionada a **Atribuições**, na lista pendente disponível no painel de resolução de problemas. Agora, pode selecionar as políticas de proteção de aplicações para ver as políticas de proteção de aplicações que foram atribuídas aos utilizadores selecionados.



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Melhorias no fluxo de trabalho da configuração de dispositivos no Portal da Empresa <!--1490692-->
Melhorámos o fluxo de trabalho da configuração de dispositivos na aplicação Portal da Empresa para Android. O tipo de linguagem é mais simples e específico para a sua empresa. Além disso, combinámos os ecrãs sempre que possível. Pode ver estas melhorias na página [Novidades na IU da aplicação](whats-new-app-ui.md#week-of-october-2-2017).

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Orientação melhorada no pedido de acesso aos contactos em dispositivos Android <!--1484985-->

A aplicação Portal da Empresa para Android exige frequentemente que o utilizador final aceite as permissões de Contactos. Se um utilizador final recusar este acesso, verá agora uma notificação na aplicação que o alerta para o conceder para acesso condicional. 

### <a name="secure-startup-remediation-for-android---1490712--"></a>Remediação de arranque seguro para Android <!--1490712-->

Os utilizadores finais com dispositivos Android poderão tocar no motivo de não conformidade na aplicação Portal da Empresa. Sempre que possível, esta ação irá reencaminhá-lo para a localização correta na aplicação de definições para resolver o problema. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Notificações push adicionais para utilizadores finais na aplicação Portal da Empresa para Android Oreo <!--1475932-->

Os utilizadores finais receberão notificações adicionais a indicar quando a aplicação Portal da Empresa para Android Oreo está a efetuar tarefas em segundo plano, como a obtenção de políticas do serviço do Intune. Isto aumenta a transparência para os utilizadores finais sobre quando o Portal da Empresa está a efetuar tarefas administrativas nos respetivos dispositivos. Isto faz parte da [otimização geral da IU do Portal da Empresa](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) para a aplicação Portal da Empresa para Android Oreo. 

Existem mais otimizações para novos elementos da IU que estão ativadas no Android Oreo.  Os utilizadores finais receberão notificações adicionais a indicar quando o Portal da Empresa está a efetuar tarefas em segundo plano, como a obtenção de políticas do serviço do Intune.  Isto aumenta a transparência para os utilizadores finais sobre quando o Portal da Empresa está a efetuar tarefas administrativas no dispositivo.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Novo comportamentos para a aplicação Portal da Empresa para Android com perfis de trabalho <!-- 1485783 -->

Quando inscreve um dispositivo Android for Work num perfil de trabalho, é a aplicação Portal da Empresa no perfil de trabalho que executa as tarefas de gestão no dispositivo. 

Se estiver a utilizar uma aplicação ativada para MAM no perfil pessoal, a aplicação Portal da Empresa para Android já não terá qualquer utilidade. Para melhorar a experiência do perfil de trabalho, o Intune ocultará automaticamente a aplicação Portal da Empresa depois de inscrever com sucesso o perfil de trabalho.

A aplicação Portal da Empresa para Android pode ser ativada em qualquer altura no perfil pessoal. para tal, navegue para o [Portal da Empresa na Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) e toque em **Ativar**.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Mudança do Portal da Empresa para Windows 8.1 e do Windows Phone 8.1 para modo de suporte <!--1428681-->

A partir de outubro de 2017, as aplicações Portal da Empresa para Windows 8.1 e o Windows Phone 8.1 irão passar para o modo de suporte, o que significa que as aplicações e os cenários existentes, tais como inscrição e conformidade, continuarão a ter suporte nestas plataformas. Estas aplicações continuarão a estar disponíveis para transferência através dos canais de lançamento existentes, tais como a Loja Microsoft. 

Quando estiverem no modo de suporte, estas aplicações receberão apenas atualizações de segurança críticas. Não haverá quaisquer atualizações ou funcionalidades adicionais para estas aplicações. Para obter novas funcionalidades, recomendamos que atualize os dispositivos para Windows 10 ou Windows 10 Mobile. 


### <a name="block-unsupported-samsung-knox-device-enrollment----1490695---"></a>Bloquear a inscrição de dispositivos Samsung Knox não suportados   <!-- 1490695 -->

A aplicação Portal da Empresa apenas tenta inscrever dispositivos Samsung Knox suportados. Para evitar erros de ativação Knox que impeçam a inscrição MDM, a tentativa de inscrição do dispositivo só será realizada se o dispositivo aparecer na [lista de dispositivos publicados pela Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Os dispositivos Samsung poderão ter números de modelo compatíveis ou não com o Knox. Verifique a compatibilidade com o Knox junto do revendedor do seu dispositivo antes da compra e implementação. Poderá encontrar a lista completa de dispositivos verificados nas [Definições da política para Android e Samsung Knox Standard](/intune/supported-devices-browsers.md#intune-supported-web-browsers).

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>Fim do suporte para Android 4.3 e anterior <!-- 1171126, 1326920 -->
As aplicações geridas e a aplicação Portal da Empresa para Android precisarão do Android 4.4 e superior para aceder a recursos empresariais. Até dezembro, todos os dispositivos inscritos serão retirados à força, resultando na perda do acesso aos recursos empresariais. Se estiver a utilizar políticas de proteção de aplicações sem MDM, as aplicações não receberão atualizações e a qualidade da experiência irá diminuir ao longo do tempo.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>Informe os utilizadores finais acerca das informações do dispositivo que podem ser vistas em dispositivos inscritos <!--1165314-->
Iremos adicionar o **Tipo de Propriedade** ao ecrã Detalhes do Dispositivo em todas as aplicações Portal da Empresa. Isto permitirá aos utilizadores saber mais sobre a privacidade diretamente a partir do artigo [Que informações pode a sua empresa ver?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune). Isto será implementado em todas as aplicações Portal da Empresa brevemente. Anunciámos esta funcionalidade para iOS em [setembro](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017).

## <a name="september-2017"></a>Setembro de 2017

### <a name="intune-supports-ios-11---1428975--"></a>O Intune suporta o iOS 11 <!--1428975-->
O Intune suporta o iOS 11. Isto foi anteriormente anunciado no [blogue de Suporte do Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

### <a name="end-of-support-for-ios-80----1164477---"></a>Fim do suporte para iOS 8.0 <!-- 1164477 -->
As aplicações geridas e a aplicação Portal da Empresa para iOS precisarão do iOS 9.0 e superior para aceder aos recursos empresariais. Os dispositivos que não forem atualizados antes de setembro deixarão de poder aceder ao Portal da Empresa ou a essas aplicações. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Ação de atualizar adicionada à aplicação Portal da Empresa para Windows 10 <!--1132468-->
A aplicação Portal da Empresa para Windows 10 permite aos utilizadores atualizar os dados na aplicação, ao pedir para atualizar ou, em computadores, ao premir F5.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Informe os utilizadores finais acerca das informações do dispositivo que podem ser vistas para iOS <!--739894-->

Adicionámos o   **Tipo de Propriedade** ao ecrã Detalhes do Dispositivo na aplicação Portal da Empresa para iOS. Isto permite que os utilizadores obtenham mais informações sobre privacidade diretamente a partir desta página, através da documentação de utilizador final do Intune. Também poderão localizar estas informações no ecrã Acerca de.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Permitir que os utilizadores finais acedam à aplicação Portal da Empresa para Android sem inscrição <!---1169910--->

Em breve, os utilizadores finais não terão de inscrever os dispositivos para aceder à aplicação Portal da Empresa para Android. Os utilizadores finais em organizações que utilizam Políticas de Proteção de Aplicações deixarão de receber pedidos para inscrever os dispositivos quando abrem a aplicação Portal da Empresa. Os utilizadores finais também poderão instalar aplicações a partir do Portal da Empresa sem inscrever o dispositivo. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Linguagem de compreensão mais fácil na aplicação Portal da Empresa para Android <!---1396349--->  

O texto do processo de inscrição da aplicação Portal da Empresa para Android foi simplificado para facilitar a inscrição dos utilizadores finais. Se tiver documentação de inscrição personalizada, deve atualizá-la para refletir os novos ecrãs. Poderá encontrar imagens de exemplo na nossa página de [Atualização da IU para aplicações de utilizadores finais do Intune](whats-new-app-ui.md#week-of-september-11-2017).

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Aplicação Portal da Empresa do Windows 10 adicionada à política de permissão do Windows Information Protection <!-- 677129 -->

A aplicação Portal da Empresa do Windows 10 foi atualizada para suportar o Windows Information Protection (WIP). A aplicação pode ser adicionada à política de permissão do WIP. Com esta alteração, a aplicação já não tem de ser adicionada à lista **Excluídas**.


## <a name="august-2017"></a>Agosto de 2017

### <a name="improvements-to-device-overview----1404453---"></a>Melhorias na descrição geral do dispositivo <!-- 1404453 -->  
As melhorias na descrição geral do dispositivo apresentam agora os dispositivos inscritos, mas excluem os dispositivos geridos pelo Exchange ActiveSync. Os dispositivos do Exchange ActiveSync não têm as mesmas opções de gestão que os dispositivos inscritos. Para ver o número de dispositivos inscritos e o número de dispositivos inscritos por plataforma, no Intune, no portal do Azure, aceda a **Dispositivos** > **Descrição Geral**.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Melhorias no inventário de dispositivos recolhido pelo Intune
<!-- 961134, 1104426, 1281327, 1333543 --> Neste lançamento, fizemos as seguintes melhorias às informações do inventário recolhido pelos dispositivos que gere:
 
-   Em dispositivos Android, pode agora adicionar uma coluna ao inventário do dispositivo que mostra o nível de atualização mais recente para cada dispositivo. Adicione a coluna **Nível de atualização de segurança** à sua lista de dispositivos para ver isto.
-   Quando filtrar a vista do dispositivo, agora pode filtrar dispositivos pela sua data de inscrição. Por exemplo, pode apresentar apenas dispositivos que foram inscritos após uma data especificada por si.
-   Melhorámos o filtro utilizado pelo item **Data do Último Registo**.
-   Na lista de dispositivos, agora pode ver o número de telemóvel dos dispositivos pertencentes à empresa.
Além disso, pode utilizar o painel de filtros para procurar dispositivos por número de telemóvel.

Para obter mais detalhes sobre o inventário de dispositivos, veja [Como ver o inventário de dispositivos do Intune](device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Suporte de acesso condicional para dispositivos macOS 
<!-- 720172 --> Agora pode definir uma política de acesso condicional que exige que os dispositivos Mac estejam inscritos no Intune e em conformidade com as políticas de conformidade do dispositivo. Por exemplo, os utilizadores podem transferir a aplicação Portal da Empresa do Intune para macOS e inscrever os dispositivos Mac no Intune. O Intune avalia se o dispositivo Mac está ou não em conformidade com os requisitos, tal como o PIN, versão do SO e Integridade do Sistema.

- Saiba mais sobre o [suporte de acesso condicional para dispositivos macOS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>A aplicação Portal da Empresa para macOS está em pré-visualização pública <!---1484796--->
A aplicação Portal da Empresa para macOS está agora disponível como parte da pré-visualização pública para acesso condicional no Enterprise Mobility + Security. Esta versão suporta o macOS 10.11 e posterior. Obtenha-a em [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### <a name="new-device-restriction-settings-for-windows-10"></a>Novas definições de restrição de dispositivos para Windows 10    
<!--1063965, 1308850  --> Nesta versão, adicionámos novas definições ao [perfil de restrição de dispositivos com o Windows 10](/intune/device-restrictions-windows-10) nas seguintes categorias:

-   Windows Defender SmartScreen
-   Loja de aplicações

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Atualizações ao perfil de dispositivo de proteção de ponto final do Windows 10 para as definições do BitLocker
<!--1459533 -->     Nesta versão, fizemos as seguintes melhorias à forma como as definições do BitLocker funcionam num perfil de dispositivo de proteção de ponto final do Windows 10:
 
-   Em **Definições de unidades de SO do BitLocker**, na definição **BitLocker com chip do TPM não compatível**, selecionar **Bloquear** fazia anteriormente com que o BitLocker fosse permitido. Corrigimos isto para que o BitLocker seja bloqueado quando a opção é selecionada.
-   Em **Definições de unidades de SO do BitLocker**, na definição **Agente de recuperação de dados baseada em certificados**, pode agora bloquear explicitamente o agente de recuperação de dados baseada em certificados. No entanto, por predefinição, o agente é permitido.
-   Em **Definições de unidades de dados fixas do BitLocker**, na definição **Agente de recuperação de dados**, pode agora bloquear explicitamente o agente de recuperação de dados.
Para obter mais informações, veja [Endpoint protection settings for Windows 10 and later (Definições de proteção de ponto final para o Windows 10 e versões posteriores)](endpoint-protection-windows-10.md).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nova experiência de início de sessão para utilizadores do Portal da Empresa para Android e das Políticas de Proteção de Aplicações <!-- 621669 -->
Os utilizadores finais podem agora procurar aplicações, gerir dispositivos e ver informações de contacto de TI com a aplicação Portal da Empresa para Android sem inscrever os respetivos dispositivos Android. Além disso, se um utilizador final já utilizar uma aplicação protegida por Políticas de Proteção de Aplicações do Intune e iniciar o Portal da Empresa para Android, deixará de receber um pedido para inscrever o dispositivo.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Nova definição para ativar e desativar a otimização da bateria na aplicação Portal da Empresa para Android <!--1405990-->
A página **Definições** na aplicação Portal da Empresa para Android tem uma nova definição para permitir aos utilizadores desativar facilmente a otimização da bateria para as aplicações Microsoft Authenticator e Portal da Empresa. O nome da aplicação apresentado na definição irá variar consoante a aplicação que gere a conta profissional. Recomendamos que os utilizadores desativem a otimização da bateria para melhorar o desempenho das aplicações de trabalho que sincronizam e-mails e dados. 

### <a name="multi-identity-support-for-onenote-for-ios----1234281---"></a>Suporte de várias identidades do OneNote para iOS      <!-- 1234281 -->
Os utilizadores finais podem agora utilizar contas diferentes (profissionais e pessoais) com o Microsoft OneNote para iOS. As políticas de proteção de aplicações podem ser aplicadas a dados empresariais em blocos de notas de trabalho sem afetar os blocos de notas pessoais. Por exemplo, uma política pode permitir que um utilizador encontre informações em blocos de notas de trabalho, mas impedir que o utilizador copie e cole dados empresariais do bloco de notas de trabalho num bloco de notas pessoal.
 
- Saiba mais sobre as aplicações que suportam a [proteção de aplicações e várias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) com o Intune.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Novas definições para permitir e bloquear aplicações em dispositivos Samsung Knox Standard
<!-- 1305423 822899-->  
Neste lançamento, estamos a adicionar novas [definições de restrição de dispositivos](device-restrictions-android.md) que lhe permitem especificar as seguintes listas de aplicações:
 
- Aplicações que os utilizadores têm permissão para instalar
- Aplicações que os utilizadores não têm permissão para executar
- Aplicações que estão ocultadas do utilizador no dispositivo  
Pode especificar a aplicação pelo URL, nome do pacote ou da lista de aplicações que gere.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Nova ligação da IU da política de acesso condicional com base na aplicação Azure AD do Intune
<!-- 1016201 --> Os administradores de TI podem agora definir políticas condicionais com base nas aplicações através da nova IU da política de acesso condicional na carga de trabalho do Azure AD. Por enquanto, o acesso condicional com base nas aplicações na secção Proteção de Aplicações do Intune no portal do Azure permanecerá no local e será imposto lado a lado. Também existe uma ligação útil para a nova IU da política de acesso condicional na carga de trabalho do Intune.

- Saiba mais sobre o [acesso condicional com base na aplicação no Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).



## <a name="july-2017"></a>Julho de 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version-----1333256-1245463----"></a>Restringir a inscrição de dispositivos Android e iOS pela versão do SO  <!--- 1333256,  1245463 --->
O Intune suporta agora a restrição da inscrição do iOS e Android pelo número da versão do sistema operativo. Em **Restrição do Tipo de Dispositivo**, o administrador de TI poderá definir uma configuração de plataforma para restringir a inscrição entre o valor do sistema operativo mínimo e o máximo. As versões do sistema operativo Android têm de ser especificadas como Major.Minor.Build.Rev, em que Minor, Build e Rev são opcionais. As versões iOS têm de ser especificadas como Major.Minor.Build em que Minor e Build são opcionais. Saiba mais sobre as [restrições de inscrição de dispositivos](enrollment-restrictions-set.md).

>[!NOTE]
>Não restringe a inscrição através dos programas de inscrição da Apple ou do Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment-----1333272-1333275-1245709---"></a>Restringir a inscrição de dispositivos pessoais Android, iOS e macOS  <!--- 1333272,  1333275, 1245709 --->
O Intune pode restringir a inscrição de dispositivos pessoais ao criar uma lista de permissões de números IMEI de dispositivos empresariais. O Intune expandiu esta funcionalidade para iOS, Android e macOS através de números de série de dispositivos. Ao carregar os números de série para o Intune, pode pré-declarar os dispositivos como pertencentes à empresa. Através das restrições de inscrição, pode bloquear dispositivos pessoais (BYOD) e permitir a inscrição apenas para dispositivos pertencentes à empresa. Saiba mais sobre as [restrições de inscrição de dispositivos](enrollment-restrictions-set.md).

Para importar números de série, aceda a **Inscrição de dispositivos** > **Identificadores de dispositivo da empresa** e clique em **Adicionar** . Em seguida, carregue um ficheiro .CSV (nenhum cabeçalho, duas colunas para o número de série e detalhes como números IMEI).  Para restringir dispositivos pessoais, aceda a **Inscrição do dispositivo** > **Restrições de inscrição**. Em **Restrições de Tipos de Dispositivos**, selecione **Predefinição** e, em seguida, selecione **Configurações de Plataformas**. Pode **Permitir** ou **Bloquear** dispositivos pessoais para iOS, Android e macOS. 


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Nova ação de dispositivo para forçar os dispositivos a sincronizar com o Intune <!-- 711369 -->
Nesta versão, adicionámos uma nova ação de dispositivo que força o dispositivo selecionado a dar entrada imediatamente no Intune. Quando um dispositivo dá entrada, recebe imediatamente todas as ações ou políticas pendentes que foram atribuídas ao mesmo.  Esta ação pode ajudá-lo a validar e resolver imediatamente problemas de políticas que atribuiu, sem esperar pela próxima entrada agendada.
Para obter detalhes, veja [Sincronizar dispositivos](device-sync.md)

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de software disponíveis mais recentes <!-- 777100 -->
Encontra-se disponível uma nova política a partir da área de trabalho Atualizações de software, onde pode forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de software disponíveis mais recentes. Para obter mais detalhes, veja [Configurar as políticas de atualização do iOS](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner----954651-1172027---"></a>Check Point SandBlast Mobile – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis  <!-- 954651, 1172027 -->
Pode controlar o acesso a recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo CheckPoint SandBlast Mobile, uma solução de defesa contra ameaças para dispositivos móveis que está integrada com o Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Como funciona a integração com o Intune?
O risco é avaliado com base na telemetria recolhida dos dispositivos que executam o CheckPoint SandBlast Mobile. Pode configurar políticas de acesso condicional de EMS com base na avaliação de riscos do CheckPoint SandBlast Mobile ativada através de políticas de conformidade do dispositivo do Intune. Pode permitir ou bloquear o acesso dos dispositivos que não estejam em conformidade aos recursos empresariais, com base nas ameaças detetadas.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>Implementar uma aplicação como disponível na Loja Microsoft para Empresas <!-- 748101 -->
Com esta versão, os administradores podem atribuir a Loja Microsoft para Empresas como disponível. Quando é definida como disponível, os utilizadores finais podem instalar a aplicação a partir da aplicação ou site do Portal da Empresa sem serem redirecionados para a Loja Microsoft.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>Atualização da IU do site do Portal da Empresa <!--1313244 part 1-->
Fizemos várias alterações à IU do [site do Portal da Empresa](https://portal.manage.microsoft.com) para melhorar a experiência do utilizador final.

- __Melhorias aos mosaicos das aplicações__: os ícones das aplicações são agora apresentados com um fundo gerado automaticamente com base na cor dominante do ícone (caso seja possível detetar uma). Quando aplicável, este fundo vem substituir o limite cinzento que era apresentado nos mosaicos das aplicações.

    O site do Portal da Empresa apresentará ícones grandes sempre que possível numa próxima versão. Recomendamos que os administradores de TI publiquem aplicações com ícones de alta resolução com o tamanho mínimo de 120 x 120 píxeis. 

- __Alterações de navegação__: os itens da barra de navegação foram movidos para o menu de opções no canto superior esquerdo. A página Categorias foi removida. Os utilizadores podem agora filtrar conteúdos por categoria enquanto navegam.

- __Atualização das Aplicações em Destaque:__ adicionámos ao site uma página dedicada em que os utilizadores podem procurar aplicações que optou por destacar e otimizámos a IU da secção Destaques na home page.

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>Suporte para iBooks no site do Portal da Empresa <!--1231841-->
Adicionámos uma página dedicada ao site do Portal da Empresa que permite aos utilizadores procurar e transferir iBooks. 


### <a name="additional-help-desk-troubleshooting-details-----applies-to-1263399-1326964-1341642----"></a>Detalhes adicionais sobre a resolução de problemas para o suporte técnico<!---  Applies to 1263399, 1326964, 1341642 --->
O Intune atualizou o ecrã de resolução de problemas e acrescentou mais informações para a equipa de administradores e suporte técnico. Agora pode ver uma tabela **Atribuições**, que resume todas as atribuições do utilizador com base na associação a grupos. Esta lista inclui:
- Aplicações móveis
- Políticas de conformidade
- Perfis de configuração

Para além disso, a tabela **Dispositivos** agora inclui as colunas **Tipo de associação Azure AD** e **Em conformidade com o Azure AD**. Para obter mais informações, veja [Ajudar os utilizadores na resolução de problemas](help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Armazém de Dados do Intune (Pré-visualização Pública)
O Armazém de Dados do Intune copia dados diariamente para fornecer uma apresentação do histórico do seu inquilino. Pode aceder a dados através de um ficheiro do Power BI (PBIX), de uma ligação OData compatível com várias ferramentas de análise ou ao interagir com a API REST. Para obter mais informações, veja [Utilizar o Armazém de Dados do Intune](reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Modos claro e escuro disponíveis para a aplicação Portal da Empresa para Windows 10 <!---676547--->
Os utilizadores finais poderão personalizar o modo de cor da aplicação Portal da Empresa para Windows 10. O utilizador pode fazer a alteração na secção Definições da aplicação Portal da Empresa. A alteração será apresentada após o utilizador reiniciar a aplicação. Para a versão 1607 e posterior do Windows 10, o modo de aplicação será predefinido para a definição do sistema. Para a versão 1511 e anterior do Windows 10, o modo de aplicação será predefinido para o modo claro.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Permitir que os utilizadores finais marquem o grupo de dispositivos na aplicação Portal da Empresa para Windows 10 <!---807046-->
Os utilizadores finais podem agora selecionar o grupo a que o dispositivo pertence ao marcá-lo diretamente na aplicação Portal da Empresa para Windows 10.



## <a name="june-2017"></a>Junho de 2017

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Novo acesso de administração baseada em funções para administradores do Intune <!-- 1099990 -->  
Uma nova função de administrador de acesso condicional está a ser adicionada para ver, criar, modificar e eliminar as políticas de Acesso Condicional do Azure AD. Anteriormente, apenas os administradores globais e os administradores de segurança tinham essa permissão. Pode ser concedida esta permissão de função aos administradores do Intune para que tenham acesso às políticas de acesso condicional.


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>Marcar dispositivos da empresa com um número de série <!-- 1215070 -->  
Agora, o Intune suporta o carregamento de números de série Android, Mac OS e iOS como Identificadores de Dispositivo da Empresa. Neste momento, não pode utilizar números de série para bloquear a inscrição de dispositivos pessoais, porque os números de série não são verificados durante a inscrição. O bloqueio de dispositivos pessoais pelo número de série será lançado em breve.


### <a name="new-remote-actions-for-ios-devices----854689---"></a>Novas ações remotas para dispositivos iOS <!-- 854689 -->
Nesta versão, adicionámos duas novas ações de dispositivo remoto para dispositivos iPad partilhados que fazem a gestão da aplicação Sala de Aula da Apple:

-   [Terminar a sessão do utilizador atual](device-logout-user.md) – termina a sessão do utilizador atual do dispositivo iOS que selecionar.
-   [Remover utilizador](device-remove-user.md) – elimina o utilizador que selecionar da cache local num dispositivo iOS.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>Suporte para iPads partilhados com a aplicação Sala de Aula para iOS<!-- 1044681 -->
Nesta versão, expandimos o suporte da gestão da aplicação Sala de Aula para iOS para incluir alunos que iniciem sessão em iPads partilhados com o respetivo ID Apple gerido.


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Alterações às aplicações incorporadas do Intune <!-- 1332306 -->
Anteriormente, o Intune continha várias aplicações incorporadas que podia atribuir rapidamente. Com base no seu feedback, removemos esta lista e já não verá as aplicações incorporadas.
No entanto, se já tiver atribuído aplicações incorporadas, as mesmas continuarão visíveis na lista de aplicações. Pode continuar a atribuir estas aplicações conforme necessário.
Numa versão posterior, planeamos adicionar um método mais simples para selecionar e atribuir aplicações incorporadas a partir do portal do Azure.

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Instalação mais fácil das aplicações do Office 365 <!--- 1121362 --->
O novo tipo de aplicação do **Office 365 ProPlus** faz com que seja mais fácil atribuir aplicações do Office 365 ProPlus 2016 aos dispositivos que está a gerir que executem a versão mais recente do Windows 10. Além disso, também pode instalar o Microsoft Project e o Microsoft Visio, se tiver licenças dos mesmos. As aplicações que pretende são agrupadas e apresentadas como uma aplicação na lista de aplicações na consola do Intune.
Para obter mais informações, veja [Como adicionar aplicações do Office 365 para Windows 10](apps-add-office365.md).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>Suporte para aplicações offline na Loja Microsoft para Empresas <!--- 777044 --->
As aplicações offline compradas na Loja Microsoft para Empresas serão agora sincronizadas com o portal do Azure. Poderá então implementar essas aplicações para grupos de dispositivos ou grupos de utilizadores. As aplicações offline são instaladas pelo Intune e não pela loja.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>O Microsoft Teams faz agora parte da lista de aplicações aprovadas para acesso condicional com base em aplicações <!-- 1257019 -->
A aplicação Microsoft Teams para iOS e Android faz agora parte das aplicações aprovadas para políticas de acesso condicional com base em aplicações para o Exchange e o SharePoint Online. A aplicação pode ser configurada através do painel de Proteção de Aplicações do Intune no portal do Azure para todos os inquilinos que utilizam atualmente o acesso condicional com base em aplicações.

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Managed Browser e integração do proxy de aplicações <!-- 1287310 -->
O Intune Managed Browser pode agora ser integrado com o serviço do Proxy de Aplicações do Azure AD para permitir aos utilizadores acederem a sites internos mesmo quando trabalham remotamente. Basta que os utilizadores do browser entrem no URL do site como fariam normalmente e o Managed Browser encaminha o pedido através do gateway Web do proxy de aplicações. Para obter mais informações, veja [Manage Internet access using managed browser policies (Gerir o acesso à Internet através de políticas de browser gerido)](app-configuration-managed-browser.md).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Novas definições de configuração de aplicações para o Intune Managed Browser<!-- 682951 -->
Nesta versão, adicionámos mais configurações à aplicação Intune Managed Browser para iOS e Android. Agora, pode utilizar uma política de configuração de aplicações para configurar a página inicial predefinida e os marcadores para o browser.
Para obter mais informações, veja [Manage Internet access using managed browser policies (Gerir o acesso à Internet através de políticas de browser gerido)](app-configuration-managed-browser.md)

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Definições do BitLocker para Windows 10 <!-- 951707 -->
Agora, pode configurar as definições do BitLocker para dispositivos Windows 10 com um novo perfil de dispositivo do Intune. Por exemplo, pode exigir que os dispositivos sejam encriptados e também pode configurar definições adicionais que são aplicadas quando o BitLocker está ativado.
Para obter mais informações, veja [Endpoint protection settings for Windows 10 and later (Definições de proteção de ponto final para o Windows 10 e versões posteriores)](endpoint-protection-windows-10.md).

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Novas definições para o perfil de restrição de dispositivos Windows 10 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
Nesta versão, adicionámos novas definições ao perfil de restrição de dispositivos Windows 10 nas seguintes categorias:

-  Windows Defender
-  Rede móvel e conectividade
-  Experiência de ecrã bloqueado
-  Privacidade
-  Procura
-  Destaque do Windows
-  Browser Microsoft Edge

Para obter mais informações sobre as definições do Windows 10, veja [Windows 10 and later device restriction settings (Definições de restrição de dispositivos Windows 10)](device-restrictions-windows-10.md).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>A aplicação Portal da Empresa para Android tem agora uma nova experiência de utilizador final para Políticas de Proteção de Aplicações <!--1305217-->
Com base no feedback dos clientes, modificámos a aplicação Portal da Empresa para Android para apresentar o botão **Aceder a Conteúdos da Empresa**. O objetivo é evitar que os utilizadores finais passem desnecessariamente pelo processo de inscrição quando apenas precisarem de acesso a aplicações que suportem Políticas de Proteção de Aplicações, uma funcionalidade da gestão de aplicações móveis do Intune. Pode ver estas alterações na página [Novidades na IU da aplicação](whats-new-app-ui.md).

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nova ação de menu para remover facilmente o Portal da Empresa <!--1164569-->
Com base nos comentários dos utilizadores, a aplicação Portal da Empresa para Android adicionou uma nova ação de menu para iniciar a remoção do Portal da Empresa do seu dispositivo. Esta ação remove o dispositivo da gestão do Intune para que a aplicação possa ser removida do dispositivo pelo utilizador. Pode ver estas alterações na página [Novidades na IU da aplicação](whats-new-app-ui.md) e na [Documentação do utilizador final do Android](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Melhorias na sincronização da aplicação com a Atualização para Criativos do Windows 10 <!--676505-->
A aplicação Portal da Empresa para Windows 10 iniciará agora automaticamente uma sincronização para pedidos de instalação de aplicações para dispositivos com a Atualização para Criativos do Windows 10 (versão 1703). Tal reduzirá o problema da interrupção da instalação de aplicações durante o estado “Sincronização Pendente”. Além disso, os utilizadores poderão iniciar manualmente uma sincronização a partir da própria aplicação. Pode ver estas alterações na página [Novidades na IU da aplicação](whats-new-app-ui.md).

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nova experiência orientada para o Portal da Empresa do Windows 10 <!---1058938--->
A aplicação Portal da Empresa para Windows 10 vai incluir uma experiência de instruções orientada do Intune para dispositivos que não foram identificados ou inscritos. A nova experiência disponibiliza instruções passo a passo que orientam o utilizador no registo do Azure Active Directory (obrigatório para as funcionalidades de Acesso Condicional) e na inscrição MDM (obrigatória para as funcionalidades de gestão de dispositivos). A experiência guiada estará acessível na página inicial do Portal da Empresa. Os utilizadores podem continuar a utilizar a aplicação se não concluírem o registo e a inscrição, mas terão funcionalidades limitadas.

Esta atualização só é visível em dispositivos com a Atualização de Aniversário do Windows 10 (compilação 1607) ou superior. Pode ver estas alterações na página [Novidades na IU da aplicação](whats-new-app-ui.md).


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>As consolas de administração do Microsoft Intune e do Acesso Condicional estão geralmente disponíveis
Estamos a anunciar a disponibilidade geral do novo Intune na consola de administração do portal do Azure e na consola de administração do Acesso Condicional. Através do Intune no portal do Azure, agora pode gerir todas as capacidades de MAM e MDM do Intune numa experiência de administração consolidada e tirar partido do agrupamento e do direcionamento do Azure AD. O acesso condicional no Azure junta capacidades avançadas no Azure AD e no Intune numa única consola unificada. E, a partir de uma experiência administrativa, a migração para a plataforma do Azure permite que utilize browsers modernos.

O Intune agora está visível sem a etiqueta **pré-visualização** no portal do Azure em portal.azure.com.

Não é necessária nenhuma ação para os clientes existentes no momento, exceto se tiver recebido uma de várias mensagens no centro de mensagens a pedir para tomar uma ação para que possamos migrar os seus grupos. Também pode ter recebido um aviso do centro de mensagens a informar que a migração está a demorar mais tempo devido a erros do nosso lado. Continuaremos a trabalhar diligentemente para migrar qualquer cliente afetado.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Melhorias dos mosaicos de aplicação na aplicação Portal da Empresa para iOS
Atualizamos a estrutura dos mosaicos de aplicação na home page para refletir a cor corporativa que definiu para o Portal da Empresa. Para mais obter informações, veja [Novidades na IU da aplicação](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Seletor de conta agora disponível para a aplicação Portal da Empresa para iOS
Os utilizadores de dispositivos iOS podem ver o nosso novo seletor de conta ao iniciar sessão no Portal da Empresa se utilizarem a conta profissional ou escolar para iniciar sessão noutras aplicações da Microsoft. Para mais obter informações, veja [Novidades na IU da aplicação](whats-new-app-ui.md).

## <a name="may-2017"></a>Maio de 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Alterar a sua autoridade MDM sem anular a inscrição dos dispositivos geridos <!--1103950-->
Pode agora alterar a autoridade MDM sem ter de contactar o Suporte da Microsoft e sem ter de anular a inscrição e inscrever novamente os seus dispositivos geridos existentes. Na consola do Gestor de Configuração, pode [alterar a sua autoridade MDM](/sccm/mdm/deploy-use/change-mdm-authority) com a opção Definir para o Gestor de Configuração (híbrido) para o Microsoft Intune (autónomo) ou vice-versa.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Notificação melhorada para os PINs de arranque do Samsung Knox <!--1087143-->
Quando os utilizadores finais têm de definir um PIN de arranque em dispositivos Samsung Knox para ficarem em conformidade com a encriptação, a notificação apresentada aos utilizadores finais vai colocá-los no local exato na aplicação Definições quando toca na notificação.  Anteriormente, a notificação enviava o utilizador final para o ecrã de alteração da palavra-passe.

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>Suporte do Gestor de Escola da Apple (ASM) com iPad partilhado <!-- 748864, 770395-->

O Intune suporta agora a utilização do Gestor de Escola da Apple (ASM) em vez do Programa de Inscrição de Dispositivos Apple para fornecer uma inscrição inicial de dispositivos iOS. A integração do ASM é necessária para utilizar a aplicação Sala de Aula para iPads Partilhados e para ativar a sincronização de dados do ASM no Azure Active Directory através da School Data Sync (SDS) da Microsoft. Para obter mais informações, veja [Ativar a inscrição do dispositivo iOS com o Gestor de Escola da Apple](apple-school-manager-set-up-ios.md).

> [!NOTE]
> A configuração de iPads Partilhados para trabalhar com a aplicação Sala de Aula requer configurações do iOS Education no Azure que ainda não estão disponíveis.  Esta funcionalidade será adicionada em breve.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>Fornecer assistência remota em dispositivos Android através do TeamViewer <!-- 675418 -->

O Intune pode agora utilizar o software [TeamViewer](https://www.teamviewer.com), adquirido separadamente, para lhe permitir disponibilizar assistência remota aos seus utilizadores com dispositivos Android. Para obter mais informações, veja [Fornecer assistência remota em dispositivos Android geridos no Intune](device-profile-android-teamviewer.md).

### <a name="app-management"></a>Gestão de aplicações

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>Novas condições de políticas de proteção de aplicações para MAM <!-- 679864 -->

Agora pode definir um requisito para a MAM sem utilizadores de inscrição que impõe as seguintes políticas:

- Versão mínima da aplicação
- Versão mínima do sistema operativo
- Versão mínima do SDK da Aplicação Intune da aplicação de destino (apenas iOS)

Esta funcionalidade está disponível no Android e no iOS. O Intune suporta a imposição da versão mínima para versões de plataformas de SO, versões de aplicações e SDK da Aplicação Intune. No iOS, as aplicações com o SDK integrado podem também definir a imposição de uma versão mínima ao nível do SDK. O utilizador não poderá aceder à aplicação de destino se não forem cumpridos os requisitos mínimos através da política de proteção de aplicações nos três níveis diferentes mencionados acima. Neste momento, o utilizador pode remover a conta (para aplicações de várias identidades), fechar a aplicação ou atualizar a versão do SO ou da aplicação.

Também pode configurar definições adicionais para fornecer uma notificação sem bloqueios que recomenda uma atualização da versão do SO ou da aplicação. Esta notificação pode ser fechada e a aplicação pode ser utilizada normalmente.

Para obter mais informações, veja [Definições de políticas de proteção de aplicações iOS](app-protection-policy-settings-ios.md) e [Definições de políticas de proteção de aplicações Android](app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Configurar as configurações de aplicações para Android for Work <!-- 621621 -->
Algumas aplicações Android da loja suportam opções de configuração geridas que permitem a um administrador de TI controlar o modo como uma aplicação é executada no perfil de trabalho. Com o Intune, agora pode ver as configurações suportadas por uma aplicação e configurá-las a partir do portal do Azure com um estruturador de configuração ou um editor de JSON. Para obter mais informações, veja [Use app configurations for Android for Work (Utilizar configurações de aplicações para Android for Work)](app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>Nova capacidade de configuração de aplicações para MAM sem inscrição <!-- 677969 -->
Agora pode criar políticas de configuração de aplicações através do MAM sem canal de inscrição. Esta funcionalidade é equivalente às políticas de configuração de aplicações disponíveis na configuração de aplicações de gestão de dispositivos móveis (MDM). Para obter um exemplo de configuração de aplicações através do MAM sem inscrição, veja [Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Configurar listas de URLs permitidos e bloqueados para o Managed Browser <!-- 682960 -->
Agora pode configurar uma lista de domínios e URLs permitidos e bloqueados para o Intune Managed Browser utilizando definições de configuração de aplicações no portal do Azure. Estas definições podem ser configuradas independentemente de estarem a ser utilizadas num dispositivo gerido ou não gerido. Para obter mais informações, veja [Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>Vista do suporte técnico da política de proteção de aplicações <!-- 1069473 -->
Os utilizadores do Suporte Técnico de TI agora podem verificar o estado da licença do utilizador e o estado da política de proteção de aplicações atribuído aos utilizadores no painel Resolução de Problemas. Para obter detalhes, veja [Resolução de Problemas](./help-desk-operators.md).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="control-website-visits-on-ios-devices----723832---"></a>Controlar visitas de sites em dispositivos iOS <!-- 723832 -->
Agora pode controlar os sites que os utilizadores dos dispositivos iOS podem visitar através de um destes métodos:

- Adicionar URLs permitidos e bloqueados através do filtro de conteúdo Web incorporado da Apple.

- Permitir o acesso apenas a sites específicos no browser Safari. São criados marcadores no Safari para cada site que especificar.

Para obter mais informações, veja [Definições de filtros de conteúdo Web para dispositivos iOS](web-content-filter-settings-ios.md).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Permissões pré-configuradas de dispositivos para aplicações Android for Work <!-- 621614 -->
Para aplicações implementadas para perfis de trabalho de dispositivos Android for Work, pode agora configurar o estado das permissões para aplicações individuais.  Por predefinição, as aplicações Android que requerem permissões de dispositivos, tal como o acesso à localização ou à câmara do dispositivo, solicitarão aos utilizadores que aceitem ou recusem as permissões.  Por exemplo, se uma aplicação utilizar o microfone do dispositivo, o utilizador final ser solicitado a conceder permissão à aplicação para utilizar o microfone. Esta funcionalidade permite-lhe definir permissões em nome do utilizador final.  Pode configurar permissões para a) recusar automaticamente sem notificar o utilizador, b) aprovar automaticamente sem notificar o utilizador ou c) avisar o utilizador para aceitar ou recusar. Para obter mais informações, veja [Definições de restrição de dispositivos Android for Work no Microsoft Intune](device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Definir um PIN específico de cada aplicação para dispositivos Android for Work <!-- 728976, 1102534 -->
Os dispositivos Android 7.0 e superior com um perfil de trabalho gerido como um dispositivo Android for Work permitem ao administrador definir uma política de código de acesso aplicada apenas a aplicações no perfil de trabalho.  As opções incluem:

- Definir apenas uma política de código de acesso para todos os dispositivos – este é o código de acesso que o utilizador tem de utilizar para desbloquear os dispositivos completos.
- Definir apenas uma política de código de acesso do perfil de trabalho – será pedido aos utilizadores que introduzam um código de acesso sempre que qualquer aplicação no perfil de trabalho for aberta.
- Definir uma política de perfil de trabalho e de dispositivo – o administrador de TI tem a opção de definir uma política de código de acesso do dispositivo e uma política de código de acesso do perfil de trabalho com diferentes níveis de segurança (por exemplo, um PIN de quatro dígitos para desbloquear o dispositivo, mas um PIN de seis dígitos para abrir qualquer aplicação de trabalho).

Para obter mais informações, veja [Definições de restrição de dispositivos Android for Work no Microsoft Intune](device-restrictions-android-for-work.md).

> [!NOTE]
> Esta opção só está disponível para o Android 7.0 e superior.  Por predefinição, o utilizador final pode utilizar os dois PINs definidos separadamente ou pode optar por combinar os dois PINs definidos no mais forte dos dois.

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Novas definições para dispositivos Windows 10 <!-- 978585 -->
Adicionámos novas [Definições de restrição de dispositivos Windows](device-restrictions-windows-10.md) que controlam funcionalidades como ligação sem fios, deteção de dispositivos, mudança de tarefas e mensagens de erro do cartão SIM.

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>Atualizações à configuração do certificado <!-- 918991 and 823198 -->
Ao criar um perfil de certificado SCEP, para <strong>Formato de nome do requerente</strong>, a opção <strong>Personalizado</strong> está disponível para dispositivos iOS, Android e Windows. Antes desta atualização, o campo <strong>Personalizado</strong> estava disponível apenas para dispositivos iOS. Para obter mais informações, veja [Criar um perfil de certificado SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile).

Ao criar um perfil de certificado PKCS, para **Nome alternativo do requerente**, o **atributo Personalizado do Azure AD** está disponível. A opção **Departamento** está disponível quando seleciona o **atributo Personalizado do Azure AD**. Para obter mais informações, veja [criar um perfil de certificado PKCS](certficates-pfx-configure.md#create-a-pkcs-certificate-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Configurar várias aplicações que podem ser executadas quando um dispositivo Android está no modo de quiosque <!-- 662059 -->
Quando um dispositivo Android estava no modo de quiosque, podia apenas configurar anteriormente uma aplicação com permissão para ser executada. Agora pode configurar várias aplicações ao utilizar a ID da aplicação, o URL da loja ou ao selecionar uma aplicação Android que já gere. Para obter mais informações, veja [Definições do modo de quiosque](device-restrictions-android.md#kiosk).



## <a name="april-2017"></a>Abril de 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Suporte para gerir a aplicação Sala de Aula da Apple
Já pode gerir a aplicação Sala de Aula do iOS nos dispositivos iPad. Configure a aplicação Sala de Aula no iPad dos professores com os dados corretos da turma e dos estudantes e, em seguida, configure os iPads dos estudantes registados numa turma para que possa controlá-los através da aplicação.
Para obter detalhes, veja [Configure iOS education settings (Configurar as definições de educação do iOS)](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Suporte para opções de configuração gerida para aplicações Android <!-- 621621 -->
As aplicações Android na Play Store que suportam opções de configuração gerida podem agora ser configuradas pelo Intune.  Esta funcionalidade permite às TI ver a lista de valores de configuração suportados por uma aplicação e disponibiliza IU de primeira classe assistida para lhes permitir configurar os valores.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Nova política para PINs complexos em Android <!-- 722069 -->
Pode agora definir um tipo de [palavra-passe](device-restrictions-android.md#password) obrigatório de Numérica complexa num perfil de dispositivo Android para dispositivos com o Android 5.0 e superior.  Utilize esta definição para impedir que os utilizadores dos dispositivos criem um PIN que contenha números repetidos ou consecutivos, como 1111 ou 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Suporte adicional para dispositivos Android for Work
- **Gerir definições de palavra-passe e perfil de trabalho** <!-- 612808 -->

  Esta nova política de restrição para dispositivos Android for Work permite-lhe agora gerir as definições de palavra-passe e perfil de trabalho em dispositivos Android for Work geridos por si.

- **Permitir a partilha de dados entre perfis de trabalho e pessoais** <!-- 1045102 -->

Este perfil de restrição para dispositivos Android for Work tem agora novas opções para o ajudar a configurar a partilha de dados entre perfis de trabalho e perfis pessoais.

- **Restringir as ações de copiar e colar entre perfis de trabalho e pessoais** <!-- 1046094 -->

  Um novo perfil de dispositivo personalizado para dispositivos Android for Work permite-lhe agora decidir se as ações de copiar e colar entre aplicações de trabalho e pessoais são permitidas.

Para obter mais informações, veja [Restrições de dispositivos para Android for Work](device-restrictions-android-for-work.md).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Atribuir aplicações LOB a dispositivos iOS e Android <!-- 1057568 -->
Agora pode atribuir aplicações de linha de negócio (LOB) para [iOS](lob-apps-ios.md) (ficheiros .ipa) e [Android](lob-apps-android.md) (ficheiros .apk) a utilizadores ou dispositivos.


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Novas políticas de dispositivos para iOS <!-- 723774, 723815, 723826, 723830 -->
- **Aplicações no Ecrã principal** – controla as aplicações que os utilizadores veem no [Ecrã principal do dispositivo iOS](home-screen-settings-ios.md). Esta política altera o esquema do ecrã principal, mas não implementa aplicações.

- **Ligações a dispositivos AirPrint** – controla os [dispositivos AirPrint](air-print-settings-ios-macos.md) (impressoras de rede) aos quais os utilizadores finais do dispositivo iOS se podem ligar.

- **Ligações a dispositivos AirPlay** – controla os [dispositivos AirPlay](airplay-settings-ios.md) (como a Apple TV) aos quais os utilizadores finais do dispositivo iOS se podem ligar.

- **Mensagem de ecrã de bloqueio personalizada** – configura uma mensagem personalizada que os utilizadores verão no ecrã de bloqueio do dispositivo iOS, que substitui a mensagem de ecrã de bloqueio predefinida. Para mais informações, veja [Ativar o modo perdido em dispositivos iOS](device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Restringir notificações push para aplicações para iOS <!-- 723767 -->
Num perfil de restrição para dispositivos do Intune, pode agora configurar as seguintes [definições de notificação](app-notification-settings-ios.md) para dispositivos iOS:

- Ativar ou desativar notificações por completo para uma aplicação específica.
- Ativar ou desativar notificações para uma aplicação específica na central de notificações.
- Especificar o tipo de alerta: **Nenhum**, **Faixa** ou **Aviso Modal**.
- Especificar se são permitidos emblemas para esta aplicação.
- Especificar se são permitidos sons de notificação.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Configurar que aplicações iOS são executadas em modo de aplicação única autónomo <!-- 737837 -->
Pode agora utilizar um perfil de dispositivo do Intune para configurar os dispositivos iOS para executar aplicações específicas no [modo de aplicação única autónomo](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only). Quando este modo está configurado e a aplicação é executada, o dispositivo é bloqueado para que possa apenas executar essa aplicação. Um exemplo desta funcionalidade é quando configura uma aplicação que permite aos utilizadores fazer um teste no dispositivo. Quando as ações da aplicação forem concluídas ou quando remover esta política, o dispositivo regressa ao estado de funcionamento normal.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Configurar domínios de confiança para navegação Web e de e-mail em dispositivos iOS <!-- 723765 -->
Para um perfil de restrição para dispositivos iOS, pode agora configurar as seguintes [definições de domínio](device-restrictions-ios.md#domains):

- **Domínios de e-mail não marcados** – e-mails que o utilizador envia ou recebe que não correspondam aos domínios que especifica aqui serão marcados como não sendo de confiança.

- **Domínios Web geridos** – os documentos transferidos a partir dos URLs que especificar aqui serão considerados como geridos (apenas para Safari).  

- **Domínios de preenchimento automático da palavra-passe do Safari** – os utilizadores podem guardar palavras-passe no Safari apenas de URLs que correspondam aos padrões que especificar aqui. Para utilizar esta definição, o dispositivo tem de estar no modo supervisionado e não configurado para múltiplos utilizadores. (iOS 9.3 e superior)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>Aplicações do VPP disponíveis no Portal da Empresa para iOS <!-- 748782 -->
Pode agora atribuir aos utilizadores finais aplicações iOS compradas em grandes volumes (VPP) como instalações no modo **Disponível**. Os utilizadores finais precisarão de uma conta da Apple Store para instalar a aplicação.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Sincronizar eBooks a partir da Apple VPP Store <!-- 800878 -->
Agora pode [sincronizar livros](vpp-apps-ios.md) que tenha comprado na loja do Apple Volume Purchase Program com o Intune e atribuí-los aos utilizadores.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Gestão de vários utilizadores em dispositivos Samsung Knox Standard <!-- 971988 -->
Os dispositivos com o Samsung Knox Standard agora suportam a [gestão de vários utilizadores](android-enroll.md) do Intune. Isto significa que os utilizadores finais podem iniciar e terminar sessão no dispositivo com as credenciais do Azure Active Directory e o dispositivo será gerido centralmente quer esteja a ser utilizado ou não.  Quando os utilizadores finais iniciam sessão, têm acesso às aplicações e obtêm as políticas aplicadas às mesmas. Quando os utilizadores terminam sessão, todos os dados das aplicações são limpos.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Definições de restrição adicionais para dispositivos Windows <!-- 818566 -->
Adicionamos suporte para mais [definições de restrição para dispositivos Windows](device-restrictions-windows-10.md), tais como suporte adicional para o browser Edge, personalização do ecrã de bloqueio do dispositivo, personalizações do menu Iniciar, imagens de fundo definidas por pesquisas do Destaque do Windows e definição de proxy.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Suporte para múltiplos utilizadores da Atualização para Criativos do Windows 10 <!-- 822547 -->
Adicionamos suporte para a [gestão de vários utilizadores](windows-enroll.md) para dispositivos a executar a Atualização para Criativos do Windows 10 e que estejam associados ao domínio do Azure Active Directory. Tal significa que, quando outros utilizadores padrão iniciarem sessão no dispositivo com as credenciais do Azure AD, receberão as aplicações e as políticas atribuídas aos seus nomes de utilizador. Atualmente, os utilizadores não podem utilizar o Portal da Empresa para cenários de self-service, tais como instalar aplicações.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start para PCs com Windows 10 <!-- 1004830 -->
Está agora disponível uma [ação de dispositivo Fresh Start](device-fresh-start.md) para PCs com Windows 10.  Ao executar esta ação, as aplicações instaladas no PC são removidas e o PC é automaticamente atualizado para a versão mais recente do Windows. Esta ação pode ajudar a remover aplicações OEM que vêm frequentemente pré-instaladas num PC novo. Pode configurar se os dados de utilizador são retidos ao efetuar esta ação.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Caminhos de atualização do Windows 10 adicionais<!-- 903672 -->
Agora, pode criar uma [política de atualização de edição para atualizar os dispositivos](edition-upgrade-configure-windows-10.md) para as seguintes edições do Windows 10 adicionais:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Inscrever dispositivos Windows 10 em volume <!-- 747607 -->
Agora, pode juntar-se a um grande número de dispositivos que executam a atualização para Criativos do Windows 10 para o Azure Active Directory e o Intune com o Windows Configuration Designer (WCD). Para ativar a [inscrição na MDM em massa](windows-bulk-enroll.md) para o seu inquilino do Azure AD, crie um pacote de aprovisionamento que associe dispositivos ao seu inquilino do Azure AD através do Windows Configuration Designer e aplique o pacote aos dispositivos pertencentes à empresa que pretende inscrever e gerir em massa. Assim que o pacote for aplicado aos dispositivos, estes são associados ao Azure AD, inscritos no Intune e estarão prontos para os seus utilizadores do Azure AD iniciarem sessão.  Os utilizadores do Azure AD são utilizadores padrão nestes dispositivos e obtêm as políticas atribuídas e as aplicações necessárias. Os cenários Self-service e Portal da Empresa não são atualmente suportados.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Novas definições de MAM para PIN e localizações de armazenamento gerido <!-- 581122, 736644 -->
Estão agora disponíveis duas novas definições de aplicações para o ajudar em cenários de MAM (gestão de aplicações móveis):

- **Desativar o PIN da aplicação quando o PIN do dispositivo for gerido** – deteta se está presente um PIN no dispositivo inscrito e, caso esteja, ignora o PIN da aplicação acionado pelas políticas de proteção da aplicação. Esta definição permitirá reduzir o número de pedidos de PIN quando os utilizadores abrirem uma aplicação com MAM ativada num dispositivo inscrito. Esta funcionalidade está disponível para Android e iOS.

- **Selecionar em que serviços de armazenamento podem ser guardados os dados empresariais** – permite-lhe especificar as localizações de armazenamento onde podem ser guardados dados empresariais. Os utilizadores podem guardar nos serviços de localização de armazenamento selecionados, o que significa que todos os que não estiverem listados serão bloqueados.

  Lista dos serviços de localização de armazenamento:

  - OneDrive para Empresas
  - SharePoint Online
  - Armazenamento local

### <a name="help-desk-troubleshooting-portal----907448---"></a>Portal de resolução de problemas de suporte técnico <!-- 907448 -->
O novo [portal de resolução de problemas](help-desk-operators.md) permite aos operadores de suporte técnico e aos administradores do Intune verem os utilizadores e os seus dispositivos e executar tarefas para resolver problemas técnicos do Intune.

## <a name="march-2017"></a>Março de 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Suporte para o Modo Perdido no iOS <!--431695-->
Para os dispositivos iOS 9.3 e posteriores, o Intune adicionou o suporte para o **Modo Perdido**. Agora, pode bloquear um dispositivo para impedir toda a utilização e apresentar um número de telefone de contacto e uma mensagem no ecrã de bloqueio do dispositivo.

O utilizador final só poderá desbloquear o dispositivo quando um administrador desativar o Modo Perdido. Quando o Modo Perdido está ativado, pode utilizar a ação **Localizar dispositivo** para apresentar a localização geográfica do dispositivo num mapa na consola do Intune.

O dispositivo tem de ser um dispositivo iOS pertencente à empresa, inscrito através do DEP, que esteja no modo supervisionado.

Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](device-management.md)?

### <a name="improvements-to-device-actions-report---677150--"></a>Melhorias ao relatório de Ações de Dispositivos<!--677150-->
Melhoramos o relatório de Ações de Dispositivos para um melhor desempenho. Além disso, agora pode filtrar o relatório por estado. Por exemplo, pode filtrar o relatório para mostrar apenas as ações de dispositivo que foram concluídas.

### <a name="custom-app-categories---748805--"></a>Categorias de aplicações personalizadas <!--748805-->
Agora pode criar, editar e atribuir categorias às aplicações que adicionar ao Intune. Atualmente, as categorias só podem ser especificadas em inglês.
Veja [Como adicionar uma aplicação ao Intune](apps-add.md).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Atribuir aplicações de LOB a utilizadores com dispositivos não inscritos <!--748823-->
Agora pode atribuir aplicações de linha de negócio da loja aos utilizadores, quer os respetivos dispositivos estejam ou não inscritos no Intune. Se o dispositivo do utilizador não estiver inscrito no Intune, o utilizador terá de aceder ao site do Portal da Empresa para o instalar, em vez da aplicação Portal da Empresa.

### <a name="new-compliance-reports---846671--"></a>Novos relatórios de conformidade <!--846671-->
Tem agora relatórios de conformidade que lhe dão a postura de conformidade dos dispositivos na sua empresa e lhe permitem rapidamente resolver problemas relacionados com a conformidade encontrados pelos utilizadores. Pode ver informações sobre o

- Estado de conformidade geral dos dispositivos
- Estado de conformidade de uma definição individual
- Estado de conformidade de uma política individual

Também pode utilizar estes relatórios para desagregar um dispositivo individual e ver as definições e políticas específicas que afetam esse dispositivo.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acesso direto aos cenários de inscrição da Apple <!--951869-->
Para as contas do Intune criadas depois de janeiro de 2017, o Intune ativou o acesso direto aos cenários de inscrição da Apple através da carga de trabalho Inscrever Dispositivos no portal do Azure. Anteriormente, a pré-visualização da inscrição da Apple apenas estava acessível a partir de ligações no portal do Azure. As contas do Intune criadas antes de Janeiro de 2017 precisam de uma única migração antes de estas funcionalidades ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder à pré-visualização.


## <a name="february-2017"></a>Fevereiro de 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Capacidade para restringir a inscrição de dispositivos móveis<!--747600, 795782-->
O Intune está a adicionar novas restrições de inscrição que controlam as plataformas de dispositivos móveis autorizadas a inscrever. O Intune separa plataformas de dispositivos móveis como iOS, macOS, Android, Windows e Windows Mobile.

* A restrição da inscrição de dispositivos móveis não restringe a inscrição do cliente de PC.  
* Existe uma opção adicional para bloquear a inscrição de dispositivos pessoais apenas para iOS e Android.

O Intune marca todos os novos dispositivos como pessoais, a menos que o administrador de TI os marque como pertencentes à empresa, conforme explicado [neste artigo](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Ver todas as ações em dispositivos geridos <!--677150-->
Um novo relatório __Ações de Dispositivos__ mostra quem efetuou ações remotas como a reposição de dados de fábrica em dispositivos e o estado dessas ações. Veja [O que é a gestão de dispositivos?](device-management.md)

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Os dispositivos não geridos podem aceder a aplicações atribuídas <!--664691-->
Como parte das alterações de estrutura no site do Portal da Empresa, os utilizadores de iOS e Android poderão instalar aplicações atribuídas a eles próprios como "disponíveis sem inscrição" nos seus dispositivos não geridos. Com as suas credenciais do Intune, os utilizadores poderão iniciar sessão no site do Portal da Empresa e ver as listas de aplicações atribuídas a eles próprios. Os pacotes de aplicações das aplicações "disponíveis sem inscrição" estão disponíveis para transferência através do site do Portal da Empresa. As aplicações que requerem inscrição para instalação não são afetadas por esta alteração, uma vez que será solicitado aos utilizadores que inscrevam o seu dispositivo se quiserem instalar essas aplicações.

### <a name="custom-app-categories---748805--"></a>Categorias de aplicações personalizadas <!--748805-->
Agora pode criar, editar e atribuir categorias às aplicações que adicionar ao Intune. Atualmente, as categorias só podem ser especificadas em inglês.
Veja [Como adicionar uma aplicação ao Intune](apps-add.md).

### <a name="display-device-categories---814654--"></a>Mostrar categorias dos dispositivos <!--814654-->
Agora pode ver a categoria do dispositivo como uma coluna na lista de dispositivos. Também pode editar a categoria a partir da secção de propriedades do painel de propriedades do dispositivo. Veja [Como adicionar uma aplicação ao Intune](apps-add.md).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Configurar definições do Windows Update para Empresas <!--776716-->

O Windows como um Serviço é a nova forma de disponibilizar atualizações para o Windows 10. A partir do Windows 10, todas as novas Atualizações de Funcionalidades e Atualizações de Qualidade irão conter o conteúdo de todas as atualizações anteriores. Tal significa que, desde que instale a atualização mais recente, sabe que os dispositivos Windows 10 estão completamente atualizados. Ao contrário das versões anteriores do Windows, agora tem de instalar toda a atualização em vez de parte de uma atualização.

Ao utilizar o Windows Update para Empresas, pode simplificar a experiência de gestão de atualizações para não ter de aprovar atualizações individuais para grupos de dispositivos. Pode continuar a gerir o risco nos seus ambientes ao configurar uma estratégia de implementação de atualizações e o Windows Update irá garantir que as atualizações são instaladas no momento certo. O Microsoft Intune permite configurar definições de atualizações nos dispositivos e dá-lhe a capacidade de diferir a instalação de atualizações. O Intune não armazena as atualizações, mas apenas a atribuição da política de atualização. Os dispositivos acedem ao Windows Update diretamente para obterem as atualizações. Utilize o Intune para configurar e gerir **anéis de atualização do Windows 10**. Um anel de atualização contém um grupo de definições que configuram quando e como as atualizações do Windows 10 são instaladas. Para obter detalhes, veja [Configure Windows Update for Business settings (Configurar definições do Windows Update para Empresas)](windows-update-for-business-configure.md).
